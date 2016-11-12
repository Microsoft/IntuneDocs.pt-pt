---
title: "Portal do Azure para políticas de MAM | Microsoft Intune"
description: "Crie políticas de gestão de aplicações móveis com o portal do Azure. As políticas que criar aqui podem ser aplicadas aos dispositivos com ou sem inscrição no Intune."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9eb7e79bee2bc36dffab97ffdb6f665218bc739e
ms.openlocfilehash: 0acef421f179ebf922ec8af71ba336e3e5f96bd2


---

# Portal do Azure para políticas de MAM do Microsoft Intune
## Utilizar o portal do Azure
O portal do Azure permite criar e gerir políticas de gestão de aplicações móveis (MAM).

O portal do Azure suporta a criação de políticas de MAM para:
- Aplicações em execução em dispositivos **inscritos e geridos no Intune**.
- Aplicações em execução em dispositivos que **não estão inscritos** em nenhuma solução de MDM.
- Aplicações em execução em dispositivos que estão **inscritos numa solução de MDM de terceiros**.

>[!IMPORTANT]

> Se estiver a utilizar a consola de administração do Intune para gerir os seus dispositivos, pode criar uma política MAM que suporte aplicações para dispositivos inscritos no Intune através da [consola de administração do Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Poderá não ver todas as definições de política de MAM na consola de administração do Intune. O portal do Azure é a nova consola de administração para a criação de políticas de MAM. Se criar políticas de MAM na consola de administração do Intune e no portal do Azure, a política no portal do Azure é aplicada às aplicações e implementada nos utilizadores.

## Iniciar sessão no portal do Azure e personalizar a página inicial

1.  Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Captura de ecrã da página de início de sessão do portal do Azure](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Depois de iniciar sessão, verá a página **Dashboard**. A página **Dashboard** pode ser personalizada.

    ![Captura de ecrã do dashboard do portal do Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  No menu **Procurar**, localize **Intune**.![ Captura de ecrã do menu Procurar com o Intune realçado](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Escolha **Intune** > **Gestão de aplicações móveis do Intune** > **Definições**.

    ![Captura de ecrã do painel de gestão de aplicações móveis do Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Para afixar um painel à página **Início**, escolha o ícone de pin no painel **Gestão de aplicações móveis do Intune**.

    ![Captura de ecrã do painel de gestão de aplicações móveis do Intune com o ícone de afixação realçado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de ecrã do dashboard com o mosaico do Intune afixado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Passos seguintes
[Configurar políticas de gestão de aplicações móveis](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


