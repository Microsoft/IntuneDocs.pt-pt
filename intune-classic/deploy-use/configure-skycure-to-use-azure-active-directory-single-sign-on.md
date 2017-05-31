---
title: "Configurar o Skycure para utilizar o Início de Sessão Único do Azure Active Directory | Documentos da Microsoft"
description: "Configurar o Skycure para utilizar o Início de Sessão Único (SSO) do Azure Active Directory"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 34d5d359-5c7c-4225-a205-8ce890b6f890
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: bf4cf8441a0ff53abf3f7830f0cdd955a4317fb0
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Configurar o Skycure para utilizar o Início de Sessão Único (SSO) do Azure Active Directory

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O SSO do Azure AD é utilizado quando integra o Intune com o Skycure. Veja a seguir as vantagens principais:

-   Os **administradores** podem utilizar as mesmas credenciais sem terem de as escrever novamente sempre que iniciam e terminam sessão nos portais Microsoft (Intune, Azure) e na consola de Gestão do Skycure.

-   Os **utilizadores finais** podem utilizar as mesmas credenciais do Azure AD sem terem de as escrever novamente sempre que iniciam e terminam sessão nas aplicações Skycure.

Seguem-se os passos para integrar o Skycure com o Início de Sessão Único (SSO) do Azure Active Directory.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Para obter o ID de Inquilino do Azure Active Directory

Precisa de obter o ID de Inquilino do Azure AD.

1.  Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as suas credenciais.

2.  Para ver o **Dashboard**, escolha **Azure Active Directory**.

![Dashboard do Azure AD](../media/mtp/skycure-sso-1.png)

1.  Quando o painel do **Azure Active Directory** for apresentado, escolha **Propriedades**.

![Painel Propriedades do Azure AD](../media/mtp/skycure-sso-2.png)

1.  Clique no **ícone Copiar**, no **ID de Diretório do Inquilino**, no painel **Propriedades do Azure Active Directory**.

> Cole o valor ID de Diretório copiado num ficheiro de texto para que possa utilizá-lo mais tarde. O valor ID de Diretório será preciso mais tarde no processo de integração do Skycure e do Intune.

![Dashboard do Azure AD](../media/mtp/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Permitir que o Skycure comunique com o Azure Active Directory

1.  Introduza o URL abaixo no seu browser. Em vez de **DIRECTORY_ID**, introduza o ID de Inquilino do Azure Active Directory anteriormente copiado para o ficheiro de texto.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Tem de iniciar sessão com as suas credenciais do Azure Active Directory. Clique em **Aceito** para continuar.

![Página de início de sessão do Azure AD](../media/mtp/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Criar um Grupo de segurança do Azure AD para o Skycure (opcional)

Pode querer criar um grupo de utilizadores dedicado que contenha os utilizadores que executam o Skycure (por exemplo, Utilizadores do Skycure). Esta ação pode ser útil ao analisar a atividade do Skycure através dos relatórios.

-   Saiba mais sobre [como criar um grupo e adicionar membros no Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> Também pode utilizar um grupo de segurança do Azure AD existente.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Configurar a conta do Azure AD para integrar o Intune com o Skycure

1.  Na [Consola de Gestão do Skycure](https://aad.skycure.com/), introduza o ID de Inquilino do Azure Active Directory previamente guardado no ficheiro de texto.

![Campo ID de Inquilino do Azure AD da consola de Gestão do Skycure](../media/mtp/skycure-sso-5.png)

> [!IMPORTANT] 
> O Skycure valida se o ID de Inquilino do Azure AD existe ao consultar o Azure AD e, assim que o Skycure o localizar, o administrador pode avançar para o próximo passo, que é a Configuração básica.

## <a name="next-steps"></a>Próximos passos

[Transferir a política de configuração de aplicações iOS do Skycure](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

