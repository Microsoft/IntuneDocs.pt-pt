---
title: Implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS
description: Implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS no portal clássico do Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 45826fbc-6df5-41b2-8e80-d1353f904b43
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dab1818e627a120935b48861a32d516fbaf5fe9a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy"></a>Implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="before-you-begin"></a>Antes de começar

-   Os passos abaixo têm de ser realizados no [portal clássico do Intune](https://manage.microsoft.com/).

-   Utilize a mesma conta do Azure AD anteriormente configurada na Consola de Gestão do Skycure, que deve ser a mesma conta utilizada para iniciar sessão no portal clássico do Intune.

-   Verifique se está familiarizado com o processo de:

    -   [Implementar uma aplicação com o Intune](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Implementar uma política de configuração de aplicações iOS](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-deploy-skycure-apps-microsoft-authenticator-app-and-the-ios-app-configuration-policy"></a>Para implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS

1.  No portal clássico do Intune, escolha **Aplicações** &gt; **Aplicações** para ver a lista de aplicações que pode gerir.

2.  Selecione as seguintes aplicações:

    a.  Microsoft Authenticator

    b.  Aplicação Skycure para Android

    c.  Aplicação Skycure para iOS

       ![Todas as aplicações a implementar no portal clássico do Intune](../media/mtp/skycure-deploy-app-1.png)

3.  Escolha **Gerir Implementações**, selecione o grupo de segurança do Azure AD que tenha os utilizadores do Skycure e clique em **Seguinte**.

4.  Na página **Ação de Implementação**, selecione a opção **Instalação Obrigatória** na lista pendente **Aprovação** e clique em **Seguinte**.

    ![Ação de Implementação do portal clássico do Intune](../media/mtp/skycure-deploy-app-2.png)

5.  Na página **Perfil VPN**, selecione a opção **Nenhuma** na lista pendente **Política VPN** e clique em **Seguinte**.

6.  Na página **Configuração da Aplicação Móvel**, selecione a Política de Configuração de Aplicações iOS que criou anteriormente na lista pendente **Política de Configuração de Aplicações** e clique em **Concluir**.

    ![Configuração de aplicações móveis no portal clássico do Intune](../media/mtp/skycure-deploy-app-3.png)

## <a name="next-steps"></a>Próximos passos

[Configurar a integração do Skycure com o Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)
