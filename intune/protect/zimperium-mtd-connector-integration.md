---
title: Integrar o Zimperium MTD com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Como configurar a solução de Defesa Contra Ameaças (MTD) do Zimperium com o Microsoft Intune para controlar o acesso aos seus recursos empresariais a partir de dispositivos móveis.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ba94a649f9d7b49437d5d97bb621b0b0a94466c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508697"
---
# <a name="integrate-zimperium-with-intune"></a>Integrar o Zimperium com o Intune

Tem de realizar os passos seguintes para integrar a solução de Defesa Contra Ameaças para Dispositivos Móveis do Zimperium com o Intune.

## <a name="before-you-begin"></a>Antes de começar

> [!NOTE]
> Os passos seguintes devem ser realizados na [consola do Zimperium MTD](https://www.zimperium.com/platform).

Antes de iniciar o processo de integração do Zimperium com o Intune, certifique-se de que tem a seguinte subscrição e credenciais:

- Subscrição do Microsoft Intune

- Azure Active Directory as credenciais de administrador global para conceder as seguintes permissões:

  - Iniciar sessão e ler o perfil de utilizador

  - Aceder ao diretório como o utilizador com sessão iniciada

  - Ler dados do diretório

  - Enviar informações do dispositivo para o Intune

- Credenciais do administrador para aceder à consola do Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorização da aplicação Zimperium

O processo de autorização da aplicação Zimperium consiste no seguinte:

- Conceda as permissões de serviço Zimperium para comunicar informações relacionadas ao estado de integridade do dispositivo de volta para o Intune. Para conceder essas permissões, você deve usar credenciais de administrador global. A concessão de permissões é uma operação única. Depois que as permissões são concedidas, as credenciais de administrador global não são necessárias para a operação do dia a dia.

- O Zimperium sincroniza com a associação do Grupo de Inscrição do Azure Active Directory (AD) para preencher a respetiva base de dados do dispositivo.

- Permitir que a consola de administração do Zimperium utilize o Início de Sessão Único (SSO) do Azure AD.

- Permitir que a aplicação Zimperium inicie sessão através do SSO do Azure AD.

Para obter mais informações sobre os aplicativos de consentimento e Azure Active Directory, consulte [solicitar as permissões de um administrador de diretório](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) no artigo Azure Active Directory *permissões e consentimento no ponto de extremidade do Azure Active Directory v 2.0*.


## <a name="to-set-up-zimperium-integration"></a>Para configurar a integração do Zimperium

1. Aceda à [Consola do Zimperium MTD](https://www.zimperium.com/platform) e inicie sessão com as suas credenciais. Para executar o processo de configuração de integração do Zimperium, você deve entrar com um usuário Azure Active Directory que tenha a função de administrador global. Esta operação de configuração única usa os direitos de administrador global para conceder permissão em sua organização para que os aplicativos Zimperium se comuniquem com o Intune. 

2. Selecione **Gestão** a partir do menu esquerdo.

3. Selecione o separador **definições de MDM**.

4. Selecione **Adicionar MDM** e, em seguida, selecione **Microsoft Intune** a partir da lista **Fornecedor de MDM**.

5. Assim que definir o Microsoft Intune como serviço MDM, é apresentada a janela **Configuração do Microsoft Intune**, escolha **Adicionar Azure Active Directory** para cada opção: **Zimperium zConsole** e **Aplicações zIPS para iOS e Android** para autorizar o Zimperium a comunicar com o Intune e o Azure AD através do Início de Sessão Único do Azure AD.

    > [!IMPORTANT]  
    > Você deve adicionar os aplicativos Zimperium zConsole, zIPS iOS e Android para concluir o processo de integração com o Intune.

6. Selecione **Aceitar** para autorizar a aplicação Zimperium a comunicar com o Intune e o Azure Active Directory.

7. Depois de adicionar o **Zimperium zConsole** e os aplicativos **ZIPS Ios e Android** ao Azure AD, adicione os grupos de segurança do Azure AD. Esta adição permite que o Zimperium sincronize o grupo de segurança do Azure AD com o seu serviço.

8. Selecione **Concluir** para guardar a configuração e iniciar a primeira sincronização do grupo de segurança do Azure AD.

9. Saia do console do Zimperium MTD.

## <a name="next-steps"></a>Próximos passos

- [Configurar aplicações do Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)