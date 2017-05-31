---
title: "Implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS | Documentos da Microsoft"
description: "Implemente aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS na consola clássica do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 19c8ca7bbfe19649585d63ce2c0c96a8f57b3739
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Antes de começar

-   Os passos abaixo têm de ser realizados na [consola clássica do Intune](https://manage.microsoft.com/).

-   Utilize a mesma conta do Azure AD anteriormente configurada na consola de Gestão do Skycure, que deve ser a mesma conta utilizada para iniciar sessão na consola clássica do Intune.

-   Verifique se está familiarizado com o processo de:

    -   [Implementar uma aplicação com o Intune](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Implementar uma política de configuração de aplicações iOS](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Para implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS

1.  Na consola clássica do Intune, escolha **Aplicações** &gt; **Aplicações** para ver a lista de aplicações que pode gerir.

2.  Selecione as seguintes aplicações:

    a.  Microsoft Authenticator

    b.  Aplicação Skycure para Android

    c.  Aplicação Skycure para iOS

       ![Todas as aplicações a implementar na consola clássica do Intune](../media/mtp/skycure-deploy-app-1.png)

3.  Escolha **Gerir Implementações**, selecione o grupo de segurança do Azure AD que tenha os utilizadores do Skycure e clique em **Seguinte**.

4.  Na página **Ação de Implementação**, selecione a opção **Instalação Obrigatória** na lista pendente **Aprovação** e clique em **Seguinte**.

    ![Ação de Implementação da consola clássica do Intune](../media/mtp/skycure-deploy-app-2.png)

5.  Na página **Perfil VPN**, selecione a opção **Nenhuma** na lista pendente **Política VPN** e clique em **Seguinte**.

6.  Na página **Configuração da Aplicação Móvel**, selecione a Política de Configuração de Aplicações iOS que criou anteriormente na lista pendente **Política de Configuração de Aplicações** e clique em **Concluir**.

    ![Configuração de aplicações móveis na consola clássica do Intune](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>Próximos passos

[Configurar a integração do Skycure com o Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

