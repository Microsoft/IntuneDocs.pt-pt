---
title: Portal do Azure para políticas de MAM
description: Crie políticas de gestão de aplicações móveis com o portal do Azure. As políticas que criar aqui podem ser aplicadas aos dispositivos com ou sem inscrição no Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 10/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2e3e71f52979f6285a14c5cc4fe26ea912cb3a42
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="azure-portal-for-intune-app-protection-policies"></a>Portal do Azure para políticas de proteção de aplicações do Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O portal do Azure é utilizado para criar e gerir políticas de proteção de aplicações para:

- Aplicações em execução em dispositivos **inscritos e geridos no Intune**.

- Aplicações em execução em dispositivos que **não estão inscritos** em nenhuma solução de MDM.
- Aplicações em execução em dispositivos que estão **inscritos numa solução de MDM de terceiros**.

> [!IMPORTANT]
> O portal do Azure é a nova consola de administração para criar políticas de proteção de aplicações, mas também pode criar uma política de proteção de aplicações que suporte aplicações para dispositivos inscritos no Intune ao utilizar a [consola de administração do Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) para cenários MDM.
> 
> Poderá não ver todas as definições de políticas de proteção de aplicações disponíveis na consola de administração do Intune. Além disso, se criar políticas de proteção de aplicações na consola de administração do Intune e no portal do Azure, as políticas criadas no portal do Azure irão substituir as que tiverem sido criadas na consola de administração do Intune. Neste cenário, as políticas de proteção de aplicações do portal do Azure serão aplicadas às aplicações e implementadas para os utilizadores.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Iniciar sessão no portal do Azure e personalizar a página inicial

1.  Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do Intune.

    ![Captura de ecrã da página de início de sessão do portal do Azure](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Depois de iniciar sessão com êxito, verá o **Dashboard**. A página **Dashboard** pode ser personalizada.

    ![Captura de ecrã do dashboard do portal do Azure](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

    ![Captura de ecrã do menu Procurar com o Intune realçado](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  Selecione **Intune App Protection** > **Gestão de aplicações móveis do Intune** > **Todas as Definições**.

    ![Captura de ecrã do painel de gestão de aplicações móveis do Intune](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (Opcional): Para afixar um painel à página **Início**, pode utilizar a opção **afixar** no painel. Clique no ícone de afixação no **painel de gestão de aplicações móveis do Intune** para o afixar à página **Início**.

    ![Captura de ecrã do painel de gestão de aplicações móveis do Intune com o ícone de afixação realçado](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Captura de ecrã do dashboard com o mosaico do Intune afixado](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>Próximos passos
[Preparar-se para configurar políticas de proteção de aplicações](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
