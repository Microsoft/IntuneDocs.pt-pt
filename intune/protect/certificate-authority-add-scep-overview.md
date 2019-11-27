---
title: Usar autoridades de certificação (CA) de terceiros com o SCEP no Microsoft Intune-Azure | Microsoft Docs
description: No Microsoft Intune, você pode adicionar um fornecedor ou uma autoridade de certificação (CA) de terceiros para emitir certificados para dispositivos móveis usando o protocolo SCEP. Nesta descrição geral, uma aplicação do Azure Active Directory (Azure AD) fornece permissões ao Microsoft Intune para validar certificados. Em seguida, utilize o ID da aplicação, a chave de autenticação e o ID do inquilino da aplicação do AAD para configurar o servidor do SCEP para emitir certificados.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9454353ec4f8291d4d8c0001cc977838ecec787b
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540806"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adicionar autoridades de certificação parceiras no Intune com o SCEP

Use autoridades de certificação (CA) de terceiros com o Intune. CAs de terceiros podem provisionar dispositivos móveis com certificados novos ou renovados usando o protocolo SCEP (SCEP) e podem dar suporte a dispositivos Windows, iOS, Android e macOS.

Existem duas partes para utilizar esta funcionalidade: API open source e tarefas de administrador do Intune.

**Parte 1 – utilizar uma API open source**  
A Microsoft criou uma API para integração com o Intune. Embora a API você possa validar certificados, enviar notificações de êxito ou falha e usar SSL, especificamente a Factory de soquete SSL, para se comunicar com o Intune.

A API está disponível para transferência no [Repositório do GitHub público da API do SCEP no Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) e pode utilizá-la nas suas soluções. Use essa API com servidores de SCEP de terceiros para executar a validação de desafio personalizada no Intune antes que o SCEP provisione um certificado para um dispositivo.

A secção [Integração com a solução de gestão do SCEP no Intune](scep-libraries-apis.md) fornece mais detalhes sobre como utilizar a API, os seus métodos e como testar a solução que criar.

**Parte 2 – criar a aplicação e o perfil**  
Ao utilizar uma aplicação do Azure Active Directory (Azure AD), pode delegar direitos ao Intune para processar pedidos de SCEP provenientes de dispositivos. A aplicação do Azure AD inclui o ID da aplicação e os valores de chave de autenticação que são utilizados na solução de API criada pelo programador. Em seguida, os administradores criam e implantam perfis de certificados SCEP usando o Intune e podem exibir relatórios sobre o status da implantação nos dispositivos.

Este artigo fornece uma descrição geral desta funcionalidade a partir da perspetiva do administrador, incluindo como criar a aplicação do Azure AD.

## <a name="overview"></a>Overview

As etapas a seguir fornecem uma visão geral do uso do SCEP para certificados no Intune:

1. No Intune, um administrador cria um perfil de certificado SCEP e, em seguida, direciona o perfil para utilizadores ou dispositivos.
2. O dispositivo é registado no Intune.
3. O Intune cria um desafio SCEP exclusivo. Também adiciona outras informações de verificação de integridade, tal como o assunto e o SAN esperado.
4. O Intune encripta e assina as informações de verificação de integridade e o desafio e, em seguida, envia estas informações para o dispositivo com o pedido de SCEP.
5. O dispositivo gera um pedido de assinatura do certificado (CSR) e o par de chaves pública/privada no dispositivo com base no perfil de certificado SCEP que é emitido pelo Intune.
6. O CSR e o desafio encriptado/assinado são enviados para o ponto final do servidor do SCEP de terceiros.
7. O servidor do SCEP envia o CSR e o desafio para o Intune. Em seguida, o Intune valida a assinatura, desencripta o payload e compara o CSR às informações de verificação de integridade.
8. O Intune envia de volta uma resposta para o servidor do SCEP e indica se a validação do desafio ocorreu com êxito.  
9. Se o desafio for verificado com êxito, o servidor do SCEP emite o certificado para o dispositivo.

O seguinte diagrama mostra um fluxo detalhado da integração do SCEP de terceiros com o Intune:

> [!div class="mx-imgBorder"]
> ![como a autoridade de certificação SCEP de terceiros se integra com Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurar a integração de autoridades de certificação de terceiros

### <a name="validate-third-party-certification-authority"></a>Validar autoridades de certificação de terceiros

Antes de integrar as autoridades de certificação de terceiros com o Intune, confirme se a autoridade de certificação que está a utilizar suporta o Intune. A secção [Parceiros de autoridades de certificação de terceiros](#third-party-certification-authority-partners) (neste artigo) inclui uma lista. Também pode verificar a documentação de orientação da autoridade de certificação para obter mais informações. A autoridade de certificação pode incluir instruções de configuração específicas à respetiva implementação.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizar a comunicação entre a AC e o Intune

Para permitir que um servidor do SCEP de terceiros execute a validação do desafio personalizado com o Intune, crie uma aplicação no Azure AD. Esta aplicação fornece direitos delegados ao Intune para validar pedidos de SCEP.

Certifique-se de que tem as permissões obrigatórias para registar uma aplicação do Azure AD. Consulte [as permissões necessárias](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions), na documentação do Azure AD.

#### <a name="create-an-application-in-azure-active-directory"></a>Criar um aplicativo no Azure Active Directory  

1. Na [portal do Azure](https://portal.azure.com), acesse **Azure Active Directory** > **registros de aplicativo**e, em seguida, selecione **novo registro**.  

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

8. Na página **solicitar permissões de API** , selecione **Intune**e, em seguida, selecione **permissões de aplicativo**. Marque a caixa de seleção para **scep_challenge_provider** (validação de desafio SCEP).  

   Selecione **adicionar permissões** para salvar essa configuração.  

9. Permaneça na página **permissões de API** e selecione **conceder consentimento de administrador para a Microsoft**e, em seguida, selecione **Sim**.  
   
   O processo de registro do aplicativo no Azure AD foi concluído.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implementar um perfil de certificado SCEP
Enquanto administrador, crie um perfil de certificado SCEP para direcionar para utilizadores ou dispositivos. Em seguida, atribua o perfil.

- [Criar um perfil de certificado SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [Atribuir o perfil de certificado](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Remover certificados

Quando anula a inscrição ou apaga os dados do dispositivo, os certificados são removidos. Os certificados não são revogados.

## <a name="third-party-certification-authority-partners"></a>Parceiros de autoridades de certificação de terceiros
As seguintes autoridades de certificação de terceiros suportam o Intune:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [Versão open source do GitHub do EJBCA](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Se for uma autoridade de certificação de terceiros interessada em integrar o seu produto com o Intune, reveja a documentação de orientação da API:

- [Repositório do GitHub da API do SCEP no Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)

## <a name="see-also"></a>Consulte também

- [Configurar perfis de certificado](certificates-scep-configure.md)
- [Repositório do GitHub da API do SCEP no Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)
