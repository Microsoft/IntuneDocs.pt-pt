---
title: Utilizar autoridades de certificação de terceiros com o SCEP no Microsoft Intune – Azure | Microsoft Docs
description: No Microsoft Intune, pode adicionar autoridades de certificação de terceiros ou um fornecedor para emitir certificados para dispositivos móveis com o protocolo SCEP. Nesta descrição geral, uma aplicação do Azure Active Directory (Azure AD) fornece permissões ao Microsoft Intune para validar certificados. Em seguida, utilize o ID da aplicação, a chave de autenticação e o ID do inquilino da aplicação do AAD para configurar o servidor do SCEP para emitir certificados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee5a39ee8a146fbc6a85a9f4438b8e14a408a735
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321731"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Adicionar autoridades de certificação parceiras no Intune com o SCEP

No Microsoft Intune, podem ser adicionadas autoridades de certificação (AC) de terceiros. Estas ACs podem fornecer certificados para dispositivos móveis com o protocolo SCEP (Simple Certificate Enrollment Protocol). Esta funcionalidade pode emitir novos certificados e renovar certificados em dispositivos Windows, iOS, Android e macOS.

Existem duas partes para utilizar esta funcionalidade: API open source e tarefas de administrador do Intune.

**Parte 1 – utilizar uma API open source**  
A Microsoft criou uma API que se integra com o Intune para validar certificados, enviar notificações de êxito ou falha e utilizar SSL, especificamente SSL socket factory, para comunicar com o Intune.

A API está disponível para transferência no [Repositório do GitHub público da API do SCEP no Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) e pode utilizá-la nas suas soluções. Utilize esta API com servidores do SCEP de terceiros para executar a validação do desafio personalizado no Intune antes de fornecer um certificado a um dispositivo.

A secção [Integração com a solução de gestão do SCEP no Intune](scep-libraries-apis.md) fornece mais detalhes sobre como utilizar a API, os seus métodos e como testar a solução que criar.

**Parte 2 – criar a aplicação e o perfil**  
Ao utilizar uma aplicação do Azure Active Directory (Azure AD), pode delegar direitos ao Intune para processar pedidos de SCEP provenientes de dispositivos. A aplicação do Azure AD inclui o ID da aplicação e os valores de chave de autenticação que são utilizados na solução de API criada pelo programador. Os administradores podem criar e implementar perfis de certificados de SCEP com o Intune. Também pode ver relatórios sobre o estado de implementação nos dispositivos.

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

Certifique-se de que tem as permissões obrigatórias para registar uma aplicação do Azure AD. A secção [Permissões obrigatórias](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) indica os passos.

**Passo 1: criar uma aplicação do Azure AD**

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Azure Active Directory** > **Registos das aplicações** > **Novo registo de aplicação**.
3. Introduza um nome ou URL de início de sessão. Selecione **Aplicação Web/API** no tipo de aplicação.
4. Selecione **Criar**.

O artigo [Integrar aplicações com o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) inclui algumas orientações sobre como criar uma aplicação, incluindo sugestões sobre o URL e o nome.

**Passo 2: conceder permissões**

Depois de criar a sua aplicação, conceda à API do Microsoft Intune as permissões obrigatórias:

1. Na aplicação do Azure AD, abra as **Definições** > **Permissões Obrigatórias**.  
2. Selecione **Adicionar** > **Selecionar uma API** > selecione **API do Microsoft Intune** > **Selecionar**.
3. Em **Selecionar permissões**, selecione **Validação do desafio SCEP** > **Selecionar**.
4. Selecione **Concluído** para guardar as alterações.

**Passo 3: obter o ID da aplicação e a chave de autenticação**

Em seguida, obtenha o ID e os valores de chave da sua aplicação do Azure AD. São necessários os seguintes valores:

- ID da Aplicação
- Chave de Autenticação
- ID de inquilino

**Para obter o ID da aplicação e a chave de autenticação**:

1. No Azure AD, selecione a sua nova aplicação (**Registos das aplicações**).
2. Copie o **ID da Aplicação** e armazene-o no código da sua aplicação.
3. Em seguida, gere uma chave de autenticação. Na sua aplicação do Azure AD, abra as **Definições** > **Chaves**.
4. Em **Palavras-passe**, introduza uma descrição e escolha a duração da chave. **Guarde** as suas alterações. Copie e guarde o valor apresentado.

    > [!IMPORTANT]
    > Copie e guarde esta chave imediatamente, pois não será apresentada novamente. Este valor de chave é necessário com a implementação da autoridade de certificação de terceiros. Certifique-se de que revê a documentação de orientação para saber como configurar o ID da Aplicação, a Chave de Autenticação e o ID do Inquilino.

O **ID do Inquilino** é o texto de domínio após o sinal @ na sua conta. Por exemplo, se a sua conta for `admin@name.onmicrosoft.com`, o ID do inquilino é **nome.onmicrosoft.com**.

A secção [Obter o ID da aplicação e a chave de autenticação](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key) indica os passos para obter estes valores e fornece mais detalhes sobre as aplicações do Azure AD.

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurar e implementar um perfil de certificado SCEP
Enquanto administrador, crie um perfil de certificado SCEP para direcionar para utilizadores ou dispositivos. Em seguida, atribua o perfil.

- [Criar um perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Atribuir o perfil de certificado](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Remover certificados

Quando anula a inscrição ou apaga os dados do dispositivo, os certificados são removidos. Os certificados não são revogados.

## <a name="third-party-certification-authority-partners"></a>Parceiros de autoridades de certificação de terceiros
As seguintes autoridades de certificação de terceiros suportam o Intune:

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)

Se for uma autoridade de certificação de terceiros interessada em integrar o seu produto com o Intune, reveja a documentação de orientação da API:

- [Repositório do GitHub da API do SCEP no Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)

## <a name="see-also"></a>Consulte também

- [Configurar perfis de certificado](certificates-scep-configure.md)
- [Repositório do GitHub da API do SCEP no Intune](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Documentação de orientação da API do SCEP no Intune para ACs de terceiros](scep-libraries-apis.md)
