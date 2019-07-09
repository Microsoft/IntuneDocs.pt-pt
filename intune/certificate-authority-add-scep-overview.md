---
title: Utilizar autoridades de certificação (AC) com o SCEP no Microsoft Intune – Azure | Documentos da Microsoft
description: No Microsoft Intune, pode adicionar um fornecedor ou de terceiros autoridade de certificação (AC) para emitir certificados para dispositivos móveis utilizando o protocolo SCEP. Nesta descrição geral, uma aplicação do Azure Active Directory (Azure AD) fornece permissões ao Microsoft Intune para validar certificados. Em seguida, utilize o ID da aplicação, a chave de autenticação e o ID do inquilino da aplicação do AAD para configurar o servidor do SCEP para emitir certificados.
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
ms.openlocfilehash: 0c5ddb32502aa15f6eaf8f5866772ecd32e970d4
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648443"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adicionar autoridades de certificação parceiras no Intune com o SCEP

Utilize autoridades de certificação (AC) com o Intune. CAs de terceiros pode aprovisionar dispositivos móveis com o novos ou renovados certificados utilizando o protocolo de inscrição de certificados (SCEP) simples e pode oferecer suporte a dispositivos Windows, iOS, Android e macOS.

Existem duas partes para utilizar esta funcionalidade: API open source e tarefas de administrador do Intune.

**Parte 1 – utilizar uma API open source**  
A Microsoft criou uma API para integrar com o Intune. Embora a API pode validar certificados, enviar notificações de êxito ou falha e utilizar SSL, especificamente factory de soquete SSL, para comunicar com o Intune.

A API está disponível para transferência no [Repositório do GitHub público da API do SCEP no Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) e pode utilizá-la nas suas soluções. Utilize esta API com servidores do SCEP de terceiros para executar de validação do desafio personalizadas no Intune, antes de SCEP aprovisiona um certificado num dispositivo.

A secção [Integração com a solução de gestão do SCEP no Intune](scep-libraries-apis.md) fornece mais detalhes sobre como utilizar a API, os seus métodos e como testar a solução que criar.

**Parte 2 – criar a aplicação e o perfil**  
Ao utilizar uma aplicação do Azure Active Directory (Azure AD), pode delegar direitos ao Intune para processar pedidos de SCEP provenientes de dispositivos. A aplicação do Azure AD inclui o ID da aplicação e os valores de chave de autenticação que são utilizados na solução de API criada pelo programador. Os administradores, em seguida, criar e implementar perfis de certificados SCEP com o Intune e podem exibir relatórios sobre o estado de implementação nos dispositivos.

Este artigo fornece uma descrição geral desta funcionalidade a partir da perspetiva do administrador, incluindo como criar a aplicação do Azure AD.

## <a name="overview"></a>Descrição geral

Os seguintes passos fornecem uma descrição geral de como emitir certificados do SCEP no Intune:

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

![Como é que o SCEP da autoridade de certificação de terceiros se integra com o Microsoft Intune](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurar a integração de autoridades de certificação de terceiros

### <a name="validate-third-party-certification-authority"></a>Validar autoridades de certificação de terceiros

Antes de integrar as autoridades de certificação de terceiros com o Intune, confirme se a autoridade de certificação que está a utilizar suporta o Intune. A secção [Parceiros de autoridades de certificação de terceiros](#third-party-certification-authority-partners) (neste artigo) inclui uma lista. Também pode verificar a documentação de orientação da autoridade de certificação para obter mais informações. A autoridade de certificação pode incluir instruções de configuração específicas à respetiva implementação.

### <a name="authorize-communication-between-ca-and-intune"></a>Autorizar a comunicação entre a AC e o Intune

Para permitir que um servidor do SCEP de terceiros execute a validação do desafio personalizado com o Intune, crie uma aplicação no Azure AD. Esta aplicação fornece direitos delegados ao Intune para validar pedidos de SCEP.

Certifique-se de que tem as permissões obrigatórias para registar uma aplicação do Azure AD. Ver [permissões obrigatórias](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions), na documentação do Azure AD.

#### <a name="create-an-application-in-azure-active-directory"></a>Criar uma aplicação no Azure Active Directory  

1. No [portal do Azure](https://portal.azure.com), aceda à **Azure Active Directory** > **registos das aplicações**e, em seguida, selecione **novo registo**.  

2. Sobre o **registar uma aplicação** , especifique os seguintes detalhes:  
   - Na **nome** , digite um nome de aplicação significativo.  
   - Para o **tipos de conta suportados** secção, selecione **contas em qualquer diretório organizacional**.  
   - Para **URI de redirecionamento**, deixe a predefinição da Web e, em seguida, especifique o URL de início de sessão para o servidor do SCEP de terceiros.  

3. Selecione **registar** para criar a aplicação e para abrir a página de descrição geral da nova aplicação.  

4. Na aplicação **descrição geral** página, copie a **ID de aplicação (cliente)** valor e registe-a para utilização posterior. Precisará desse valor mais tarde.  

5. No painel de navegação para a aplicação, aceda a **certificados e segredos** sob **gerir**. Selecione o **novo segredo do cliente** botão. Introduza um valor na descrição, selecione qualquer opção para **Expires**e, em seguida e escolha **Add** para gerar um *valor* para o segredo do cliente. 
   > [!IMPORTANT]  
   > Antes de sair desta página, copie o valor para o segredo do cliente e registe-a para utilização posterior com a implementação de AC de terceiros. Este valor não é apresentado novamente. Certifique-se de que reveja as orientações para a AC de terceiros em como pretendem o ID da aplicação, a chave de autenticação e o ID do inquilino configurado.  

6. Registo sua **ID de inquilino**. O ID de inquilino é o texto de domínio após o @ início de sessão na sua conta. Por exemplo, se a sua conta está *admin@name.onmicrosoft.com* , em seguida, o seu ID de inquilino é **name.onmicrosoft.com**.  

7. No painel de navegação para a aplicação, aceda a **permissões de API** sob **gerir**e, em seguida, selecione **adicionar uma permissão**.  

8. Sobre o **permissões de pedido de API** página, selecione **Intune**e, em seguida, selecione **permissões de aplicação**. Selecione a caixa de verificação **scep_challenge_provider** (validação do desafio SCEP).  

   Selecione **adicionar permissões** para guardar esta configuração.  

9. Manter-se no **permissões de API** página e selecione **conceder autorização de administrador para a Microsoft**e, em seguida, selecione **Sim**.  
   
   O processo de registo de aplicação no Azure AD foi concluído.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implementar um perfil de certificado SCEP
Enquanto administrador, crie um perfil de certificado SCEP para direcionar para utilizadores ou dispositivos. Em seguida, atribua o perfil.

- [Criar um perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Atribuir o perfil de certificado](certificates-scep-configure.md#assign-the-certificate-profile)

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
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Se for uma autoridade de certificação de terceiros interessada em integrar o seu produto com o Intune, reveja a documentação de orientação da API:

- [Repositório do GitHub da API do SCEP no Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)

## <a name="see-also"></a>Consulte também

- [Configurar perfis de certificado](certificates-scep-configure.md)
- [Repositório do GitHub da API do SCEP no Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)
