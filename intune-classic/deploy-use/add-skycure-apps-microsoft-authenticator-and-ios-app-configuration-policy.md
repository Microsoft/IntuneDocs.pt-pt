---
title: "Adicionar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS"
description: "Adicionar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS no portal clássico do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 018d26f4-4a75-4e27-bb04-54f54106cb2f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6d762e1aed998642db66908549b2d15d54601aed
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="add-skycure-apps-microsoft-authenticator-app-and-ios-configuration-policy"></a>Adicionar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração para iOS

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Tem de utilizar o Intune para adicionar e implementar as aplicações do Skycure, para que os utilizadores finais possam receber notificações quando são identificadas ameaças nos dispositivos móveis deles e para receber orientações sobre como remediar essas ameaças.

Além disso, precisa do [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to), para que as identidades dos utilizadores possam ser verificadas pelo Azure AD, e da política de configuração de aplicações iOS, que indica à aplicação iOS do Skycure para utilizar o Intune e o Início de Sessão Único (SSO) do Azure AD, de modo a que os utilizadores não tenham de escrever o nome de utilizador e a palavra-passe sempre que iniciarem sessão na aplicação do Skycure.

## <a name="before-you-begin"></a>Antes de começar

-   Os passos abaixo têm de ser realizados no [portal clássico do Intune](https://manage.microsoft.com/).

-   Utilize a mesma conta do Azure AD anteriormente configurada na Consola de Gestão do Skycure, que deve ser a mesma conta utilizada para iniciar sessão no portal clássico do Intune.

-   Tem de ter o ficheiro de integração do Skycure pronto a ser utilizado. Este é o ficheiro .zip transferido anteriormente a partir da consola de Gestão do Skycure, que contém o ficheiro **skycure\_configuration.plist** com os parâmetros da política de configuração de aplicações iOS.

-   Verifique se está familiarizado com o processo de:

    -   [Adicionar uma aplicação no Intune](/intune-classic/deploy-use/add-apps).

    -   [Adicionar uma política de configuração de aplicações iOS no Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-the-skycure-app-for-android"></a>Para adicionar a aplicação Skycure para Android

1.  No portal clássico do Intune, escolha **Aplicações** &gt; **Adicionar Aplicações** para iniciar o Intune Software Publisher e clique em **Seguinte**.

2.  Na página **Configuração do software**, escolha **Ligação externa** cole o [URL da aplicação Skycure para Android](https://play.google.com/store/apps/details?id=com.skycure.skycure) em **Especificar o URL**.

    ![Especificar o URL do Intune Software Publisher](../media/mtp/skycure-add-apps-1.png)

3.  Na página **Descrição do software**, introduza o **Publicador**, o **Nome** e a **Descrição**, selecione a opção **Apresentar esta aplicação como uma aplicação em destaque e realçá-la no portal da empresa** e clique em **Seguinte**.

    ![Descrição do Software Intune Software Publisher](../media/mtp/skycure-add-apps-2.png)

4.  Clique em **Carregar** e em **Fechar**.

## <a name="to-add-the-skycure-app-for-ios"></a>Para adicionar a aplicação Skycure para iOS

1.  No portal clássico do Intune, escolha **Aplicações** &gt; **Adicionar Aplicações** para iniciar o Intune Software Publisher e clique em **Seguinte**.

2.  Na página **Configuração do software**, escolha **Aplicação iOS gerida da App Store** e, em seguida, cole o [URL da aplicação Skycure para iOS](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) em **Especificar o URL**.

    ![Aplicação iOS gerida do Intune Software Publisher](../media/mtp/skycure-add-apps-3.png)

3.  Na página **Descrição do software**, introduza o **Publicador**, o **Nome** e a **Descrição**, selecione a opção **Apresentar esta aplicação como uma aplicação em destaque e realçá-la no portal da empresa** e clique em **Seguinte**.

    ![Opções do Intune Software Publisher](../media/mtp/skycure-add-apps-4.png)

4.  Na página **Requisitos**, selecione a opção **Qualquer**, em **Tipo de dispositivo móvel**, e clique em **Seguinte**.

5.  Clique em **Carregar** e em **Fechar**.

## <a name="to-add-the-microsoft-authenticator-app-for-ios"></a>Para adicionar a aplicação Microsoft Authenticator para iOS

1.  No portal clássico do Intune, escolha **Aplicações** &gt; **Adicionar Aplicações** para iniciar o Intune Software Publisher e clique em **Seguinte**.

2.  Na página **Configuração do software**, escolha **Aplicação iOS gerida da App Store** e, em seguida, cole o [URL da aplicação Microsoft Authenticator para iOS](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) em **Especificar o URL**.

    ![Aplicação iOS gerida do Intune Software Publisher 2](../media/mtp/skycure-add-apps-5.png)

3.  Na página **Descrição do software**, introduza o **Publicador**, o **Nome** e a **Descrição**, selecione a opção **Apresentar esta aplicação como uma aplicação em destaque e realçá-la no portal da empresa** e clique em **Seguinte**.

    ![Aplicação iOS gerida do Intune Software Publisher 3](../media/mtp/skycure-add-apps-6.png)

4.  Na página **Requisitos**, selecione a opção **Qualquer**, em **Tipo de dispositivo móvel**, e clique em **Seguinte**.

5.  Clique em **Carregar** e em **Fechar**.

## <a name="to-add-the-skycure-ios-app-configuration-policy"></a>Para adicionar a política de configuração de aplicações iOS do Skycure

1.  No portal clássico do Intune, escolha **Política** &gt; **Descrição Geral &gt; Adicionar Política**.

2.  Na lista de políticas, expanda **iOS**, escolha **Política de Configuração de Aplicações Móveis (iOS 8.0 e posterior)** e, em seguida, escolha **Criar Política**.

    ![Política de configuração de aplicações iOS](../media/mtp/skycure-add-apps-7.png)

3.  Na secção **Geral**, da página **Criar Política**, indique um nome e uma descrição opcional para a política de configuração de aplicações iOS.

    a.  Abra o ficheiro **skycure\_configuration.plist** com um editor de texto, tal como o bloco de notas, copie o conteúdo e cole-o no corpo da **Política de Configuração de Aplicações Móveis**, escolha **Validar** e, em seguida, escolha **Guardar Política**.

       ![Política de configuração de aplicações iOS 2](../media/mtp/skycure-add-apps-8.png)

## <a name="next-steps"></a>Próximos passos

[Implementar aplicações do Skycure, a aplicação Microsoft Authenticator e a política de configuração de aplicações iOS](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)
