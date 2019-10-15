---
title: Usar autoridades de certificação (CA) de terceiros com o SCEP no Microsoft Intune-Azure | Microsoft Docs
description: No Microsoft Intune, você pode adicionar um fornecedor ou uma autoridade de certificação (CA) de terceiros para emitir certificados para dispositivos móveis usando o protocolo SCEP. Nesta visão geral, um aplicativo Azure Active Directory (Azure AD) fornece permissões de Microsoft Intune para validar certificados. Em seguida, use a ID do aplicativo, a chave de autenticação e a ID do locatário do aplicativo do AAD na instalação do servidor de SCEP para emitir certificados.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b82124fe8f6da7116c8333e293f219d7c667f9c
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310909"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adicionar autoridade de certificação de parceiro no Intune usando o SCEP

Use autoridades de certificação (CA) de terceiros com o Intune. CAs de terceiros podem provisionar dispositivos móveis com certificados novos ou renovados usando o protocolo SCEP (SCEP) e podem dar suporte a dispositivos Windows, iOS, Android e macOS.

Há duas partes para usar esse recurso: API de software livre e as tarefas de administrador do Intune.

**Parte 1-usar uma API de código-fonte aberto**  
A Microsoft criou uma API para integração com o Intune. Embora a API você possa validar certificados, enviar notificações de êxito ou falha e usar SSL, especificamente a Factory de soquete SSL, para se comunicar com o Intune.

A API está disponível no [repositório GitHub público da API SCEP do Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) para você baixar e usar em suas soluções. Use essa API com servidores de SCEP de terceiros para executar a validação de desafio personalizada no Intune antes que o SCEP provisione um certificado para um dispositivo.

[Integrar com a solução de gerenciamento de SCEP do Intune](scep-libraries-apis.md) fornece mais detalhes sobre como usar a API, seus métodos e testar a solução que você cria.

**Parte 2-criar o aplicativo e o perfil**  
Usando um aplicativo Azure Active Directory (Azure AD), você pode delegar direitos ao Intune para lidar com solicitações SCEP provenientes de dispositivos. O aplicativo Azure AD inclui a ID do aplicativo e os valores de chave de autenticação que são usados na solução de API que o desenvolvedor cria. Em seguida, os administradores criam e implantam perfis de certificados SCEP usando o Intune e podem exibir relatórios sobre o status da implantação nos dispositivos.

Este artigo fornece uma visão geral desse recurso de uma perspectiva de administrador, incluindo a criação do aplicativo do Azure AD.

## <a name="overview"></a>Visão geral

As etapas a seguir fornecem uma visão geral do uso do SCEP para certificados no Intune:

1. No Intune, um administrador cria um perfil de certificado SCEP e, em seguida, direciona o perfil para usuários ou dispositivos.
2. O dispositivo faz check-in no Intune.
3. O Intune cria um desafio SCEP exclusivo. Ele também adiciona informações adicionais de verificação de integridade, como o que o assunto esperado e a SAN devem ser.
4. O Intune criptografa e assina as informações de desafio e de verificação de integridade e, em seguida, envia essas informações ao dispositivo com a solicitação SCEP.
5. O dispositivo gera uma solicitação de assinatura de certificado (CSR) e um par de chaves pública/privada no dispositivo com base no perfil de certificado SCEP enviado por push do Intune.
6. O CSR e o desafio criptografado/assinado são enviados para o ponto de extremidade do servidor SCEP de terceiros.
7. O servidor SCEP envia o CSR e o desafio para o Intune. Em seguida, o Intune valida a assinatura, descriptografa a carga e compara o CSR com as informações de verificação de integridade.
8. O Intune envia de volta uma resposta para o servidor de SCEP e indica se a validação do desafio foi bem-sucedida ou não.  
9. Se o desafio for verificado com êxito, o servidor de SCEP emitirá o certificado para o dispositivo.

O diagrama a seguir mostra um fluxo detalhado de integração de SCEP de terceiros com o Intune:

![Como o SCEP da autoridade de certificação de terceiros se integra ao Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurar integração de CA de terceiros

### <a name="validate-third-party-certification-authority"></a>Validar autoridade de certificação de terceiros

Antes de integrar as autoridades de certificação de terceiros ao Intune, confirme se a AC que você está usando oferece suporte ao Intune. [Parceiros de autoridade de certificação de terceiros](#third-party-certification-authority-partners) (neste artigo) incluem uma lista. Você também pode verificar as diretrizes da autoridade de certificação para obter mais informações. A autoridade de certificação pode incluir instruções de instalação específicas à sua implementação.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizar a comunicação entre a AC e o Intune

Para permitir que um servidor de SCEP de terceiros execute a validação de desafio personalizada com o Intune, crie um aplicativo no Azure AD. Este aplicativo concede direitos delegados ao Intune para validar solicitações SCEP.

Verifique se você tem as permissões necessárias para registrar um aplicativo do Azure AD. Consulte [as permissões necessárias](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions), na documentação do Azure AD.

#### <a name="create-an-application-in-azure-active-directory"></a>Criar uma Aplicação no Azure Active Directory  

1. Na [portal do Azure](https://portal.azure.com), acesse **Azure Active Directory** **registros do aplicativo** >  e, em seguida, selecione **novo registro**.  

2. Na página **registrar um aplicativo** , especifique os seguintes detalhes:  
   - Na seção **nome** , insira um nome de aplicativo significativo.  
   - Para a seção **tipos de conta com suporte** , selecione **contas em qualquer diretório organizacional**.  
   - Para **URI de redirecionamento**, deixe o padrão da Web e, em seguida, ESPECIFIQUE a URL de logon para o servidor SCEP de terceiros.  

3. Selecione **registrar** para criar o aplicativo e abrir a página Visão geral do novo aplicativo.  

4. Na página **visão geral** do aplicativo, copie o valor da **ID do aplicativo (cliente)** e registre-o para uso posterior. Você precisará desse valor mais tarde.  

5. No painel de navegação do aplicativo, acesse **certificados & segredos** em **gerenciar**. Selecione o botão **novo segredo do cliente** . Insira um valor em descrição, selecione qualquer opção para **expirar**e escolha **Adicionar** para gerar um *valor* para o segredo do cliente. 
   > [!IMPORTANT]  
   > Antes de sair dessa página, copie o valor do segredo do cliente e registre-o para uso posterior com sua implementação de autoridade de certificação de terceiros. Esse valor não é mostrado novamente. Certifique-se de examinar as diretrizes para sua autoridade de certificação de terceiros sobre como desejam a ID do aplicativo, a chave de autenticação e a ID do locatário configurados.  

6. Registre sua **ID de locatário**. A ID do locatário é o texto do domínio após o sinal @ em sua conta. Por exemplo, se sua conta for *admin@name.onmicrosoft.com* , sua ID de locatário será **Name.onmicrosoft.com**.  

7. No painel de navegação do aplicativo, acesse **permissões de API** em **gerenciar**e, em seguida, selecione **Adicionar uma permissão**.  

8. Na página **solicitar permissões de API** , selecione **Intune**e, em seguida, selecione **permissões de aplicativo**. Marque a caixa de seleção **scep_challenge_provider** (validação de desafio SCEP).  

   Selecione **adicionar permissões** para salvar essa configuração.  

9. Permaneça na página **permissões de API** e selecione **conceder consentimento de administrador para a Microsoft**e, em seguida, selecione **Sim**.  
   
   O processo de registro do aplicativo no Azure AD foi concluído.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implantar um perfil de certificado SCEP
Como administrador, crie um perfil de certificado SCEP para ser direcionado a usuários ou dispositivos. Em seguida, atribua o perfil.

- [Criar um perfil de certificado SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [Atribuir o perfil de certificado](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Removendo certificados

Quando você cancela o registro ou apaga o dispositivo, os certificados são removidos. Os certificados não são revogados.

## <a name="third-party-certification-authority-partners"></a>Parceiros de autoridade de certificação de terceiros
As seguintes autoridades de certificação de terceiros dão suporte ao Intune:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [Versão de código-fonte aberto do EJBCA GitHub](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Se você for uma CA de terceiros interessada em integrar seu produto com o Intune, examine as diretrizes da API:

- [Repositório GitHub da API SCEP do Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Diretrizes da API SCEP do Intune para CAs de terceiros](scep-libraries-apis.md)

## <a name="see-also"></a>Ver também

- [Configurar perfis de certificado](certificates-scep-configure.md)
- [Repositório GitHub da API SCEP do Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Diretrizes da API SCEP do Intune para CAs de terceiros](scep-libraries-apis.md)
