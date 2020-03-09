---
title: Utilize autoridades de certificação de terceiros (CA) com SCEP no Microsoft Intune - Azure  Microsoft Docs
description: No Microsoft Intune, pode adicionar um fornecedor ou autoridade de certificados de terceiros (CA) para emitir certificados a dispositivos móveis utilizando o protocolo SCEP. Nesta descrição geral, uma aplicação do Azure Active Directory (Azure AD) fornece permissões ao Microsoft Intune para validar certificados. Em seguida, utilize o ID da aplicação, a chave de autenticação e o ID do inquilino da aplicação do AAD para configurar o servidor do SCEP para emitir certificados.
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
ms.openlocfilehash: 85aac54a81d81dc138dd12612db183aae839b72b
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78370045"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adicionar autoridades de certificação parceiras no Intune com o SCEP

Utilize autoridades de certificação de terceiros (CA) com Intune. Os CAs de terceiros podem fornecer dispositivos móveis com certificados novos ou renovados utilizando o Protocolo de Inscrição de Certificados Simples (SCEP), e podem suportar dispositivos Windows, iOS/iPadOS, Android e macOS.

Existem duas partes para utilizar esta funcionalidade: API open source e tarefas de administrador do Intune.

**Parte 1 – utilizar uma API open source**  
A Microsoft criou uma API para integrar com o Intune. Embora a API possa validar certificados, enviar notificações de sucesso ou falha, e utilizar a SSL, especificamente a fábrica de tomadas SSL, para comunicar com a Intune.

A API está disponível para transferência no [Repositório do GitHub público da API do SCEP no Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) e pode utilizá-la nas suas soluções. Utilize este API com servidores SCEP de terceiros para executar validação personalizada do desafio contra intune antes de o SCEP fornecer um certificado a um dispositivo.

A secção [Integração com a solução de gestão do SCEP no Intune](scep-libraries-apis.md) fornece mais detalhes sobre como utilizar a API, os seus métodos e como testar a solução que criar.

**Parte 2 – criar a aplicação e o perfil**  
Ao utilizar uma aplicação do Azure Active Directory (Azure AD), pode delegar direitos ao Intune para processar pedidos de SCEP provenientes de dispositivos. A aplicação do Azure AD inclui o ID da aplicação e os valores de chave de autenticação que são utilizados na solução de API criada pelo programador. Os administradores criam e então perfis de certificados SCEP utilizando o Intune e podem visualizar relatórios sobre o estado de implementação nos dispositivos.

Este artigo fornece uma descrição geral desta funcionalidade a partir da perspetiva do administrador, incluindo como criar a aplicação do Azure AD.

## <a name="overview"></a>Descrição geral

Os seguintes passos fornecem uma visão geral da utilização do SCEP para certificados em Intune:

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
> ![Como a autoridade de certificação de terceiros sCEP integra com a Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurar a integração de autoridades de certificação de terceiros

### <a name="validate-third-party-certification-authority"></a>Validar autoridades de certificação de terceiros

Antes de integrar as autoridades de certificação de terceiros com o Intune, confirme se a autoridade de certificação que está a utilizar suporta o Intune. A secção [Parceiros de autoridades de certificação de terceiros](#third-party-certification-authority-partners) (neste artigo) inclui uma lista. Também pode verificar a documentação de orientação da autoridade de certificação para obter mais informações. A autoridade de certificação pode incluir instruções de configuração específicas à respetiva implementação.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizar a comunicação entre a AC e o Intune

Para permitir que um servidor do SCEP de terceiros execute a validação do desafio personalizado com o Intune, crie uma aplicação no Azure AD. Esta aplicação fornece direitos delegados ao Intune para validar pedidos de SCEP.

Certifique-se de que tem as permissões obrigatórias para registar uma aplicação do Azure AD. Consulte [as permissões necessárias,](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions)na documentação da AD Azure.

#### <a name="create-an-application-in-azure-active-directory"></a>Criar uma aplicação no Diretório Ativo azure  

1. No [portal Azure,](https://portal.azure.com)vá ao **Azure Ative Directory** > Registos de **Aplicações,** e depois selecione **Nova inscrição.**  

2. No **Registo de uma** página de candidatura, especifique os seguintes detalhes:  
   - Na secção **Nome,** introduza um nome de aplicação significativo.  
   - Para a secção de tipos de **conta suportada,** selecione **Contas em qualquer diretório organizacional**.  
   - Para **redirecionar o URI,** deixe o padrão da Web e, em seguida, especifique o URL de entrada para o servidor SCEP de terceiros.  

3. Selecione **Register** para criar a aplicação e para abrir a página 'Visão Geral' para a nova aplicação.  

4. Na página de **visão geral** da aplicação, copie o valor de ID **da Aplicação (cliente)** e grave-o para posterior utilização. Vai precisar deste valor mais tarde.  

5. No painel de navegação para a app, vá a **Certificados e segredos** no **âmbito do Manage**. Selecione o botão secreto do **novo cliente.** Introduza um valor em Descrição, selecione qualquer opção para **Expirações,** e depois escolha **Adicionar** para gerar um *valor* para o segredo do cliente. 
   > [!IMPORTANT]  
   > Antes de sair desta página, copie o valor para o segredo do cliente e grave-o para posterior utilização com a sua implementação de AC de terceiros. Este valor não é mostrado novamente. Certifique-se de rever as orientações para o seu CA de terceiros sobre como eles querem o ID de aplicação, chave de autenticação e ID do inquilino configurado.  

6. Grave a sua **identificação do inquilino.** O ID do Inquilino é o texto de domínio após o sinal de @na sua conta. Por exemplo, se a sua conta for *admin@name.onmicrosoft.com,* então a sua identificação do inquilino é **name.onmicrosoft.com**.  

7. No painel de navegação da aplicação, vá a **permissões API** ao abrigo **do Manage**, e, em seguida, selecione Adicionar **uma permissão**.  

8. Na página de **permissões Solicitar API,** selecione **Intune**, e, em seguida, selecione **permissões**de Pedido . Selecione a caixa de verificação para **scep_challenge_provider** (validação do desafio SCEP).  

   Selecione **Adicionar permissões** para salvar esta configuração.  

9. Permaneça na página de **permissões da API** e selecione o consentimento do **administrador grant para**a Microsoft , e depois selecione **Sim**.  
   
   O processo de registo da aplicação em Azure AD está completo.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implementar um perfil de certificado SCEP
Enquanto administrador, crie um perfil de certificado SCEP para direcionar para utilizadores ou dispositivos. Em seguida, atribua o perfil.

- [Criar um perfil de certificado SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [Atribuir o perfil de certificado](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Remover certificados

Quando anula a inscrição ou apaga os dados do dispositivo, os certificados são removidos. Os certificados não são revogados.

## <a name="third-party-certification-authority-partners"></a>Parceiros de autoridades de certificação de terceiros
As seguintes autoridades de certificação de terceiros suportam o Intune:

- [Entrust Datacard](https://go.entrustdatacard.com/pki/intune/)
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

## <a name="see-also"></a>Veja também

- [Configurar perfis de certificado](certificates-scep-configure.md)
- [Repositório do GitHub da API do SCEP no Intune](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)
