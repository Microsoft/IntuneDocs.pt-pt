---
title: "Configurar o Skycure para utilizar o início de sessão único do Azure AD com o Intune"
titlesuffix: Azure portal
description: "Configurar o Skycure para utilizar o início de sessão único do Azure AD com o Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0466ac4-4942-4c4c-b8af-996b597c701d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 93e7f1a21c9badb3cc3ccdf02432267b271e6e94
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Configurar o Skycure para utilizar o Início de Sessão Único (SSO) do Azure Active Directory

O SSO do Azure AD é utilizado quando integra o Intune com o Skycure. Veja a seguir as vantagens principais:

-   Os **administradores** podem utilizar as mesmas credenciais sem terem de as escrever novamente sempre que iniciam e terminam sessão nos portais Microsoft (Intune, Azure) e na consola de Gestão do Skycure.

-   Os **utilizadores finais** podem utilizar as mesmas credenciais do Azure AD sem terem de as escrever novamente sempre que iniciam e terminam sessão nas aplicações Skycure.

Seguem-se os passos para integrar o Skycure com o Início de Sessão Único (SSO) do Azure Active Directory.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Para obter o ID de Inquilino do Azure Active Directory

Precisa de obter o ID de Inquilino do Azure AD.

1.  Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as suas credenciais.

2.  Para ver o **Dashboard**, escolha **Azure Active Directory**.

    ![Dashboard do Azure AD](./media/skycure-sso-1.png)

3.  Quando o painel do **Azure Active Directory** for apresentado, escolha **Propriedades**.

    ![Painel Propriedades do Azure AD](./media/skycure-sso-2.png)

4.  Clique no **ícone Copiar**, no **ID de Diretório do Inquilino**, no painel **Propriedades do Azure Active Directory**.

5. Cole o valor ID de Diretório copiado num ficheiro de texto para que possa utilizá-lo mais tarde. O valor ID de Diretório será preciso mais tarde no processo de integração do Skycure e do Intune.

    ![Dashboard do Azure AD](./media/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Permitir que o Skycure comunique com o Azure Active Directory

1.  Introduza o URL abaixo no seu browser. Em vez de **DIRECTORY_ID**, introduza o ID de Inquilino do Azure Active Directory anteriormente copiado para o ficheiro de texto.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Tem de iniciar sessão com as suas credenciais do Azure Active Directory. Clique em **Aceito** para continuar.

![Página de início de sessão do Azure AD](./media/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Criar um Grupo de segurança do Azure AD para o Skycure (opcional)

Pode querer criar um grupo de utilizadores dedicado que contenha os utilizadores que executam o Skycure (por exemplo, Utilizadores do Skycure). Esta ação pode ser útil ao analisar a atividade do Skycure através dos relatórios.

-   Saiba mais sobre [como criar um grupo e adicionar membros no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> Também pode utilizar um grupo de segurança do Azure AD existente.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Configurar a conta do Azure AD para integrar o Intune com o Skycure

1.  Na [Consola de Gestão do Skycure](https://aad.skycure.com/), introduza o ID de Inquilino do Azure Active Directory previamente guardado no ficheiro de texto.

![Campo ID de Inquilino do Azure AD da consola de Gestão do Skycure](./media/skycure-sso-5.png)

> [!IMPORTANT] 
> O Skycure valida se o ID de Inquilino do Azure AD existe ao consultar o Azure AD e, assim que o Skycure o localizar, o administrador pode avançar para o próximo passo, que é a Configuração básica.

## <a name="next-steps"></a>Próximos passos

[Transferir a política de configuração de aplicações iOS do Skycure](skycure-ios-app-configuration-policy-download.md)
