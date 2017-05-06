---
title: "Preparar-se para configurar políticas de proteção de aplicações para o Windows 10 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Configurar o fornecedor de gestão de aplicações móveis (MAM) no Azure AD"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 7cd202384eeb17f5ff5a2812fe87a2fffabe6eb0
ms.lasthandoff: 04/27/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparar-se para configurar políticas de proteção de aplicações para o Windows 10

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de criar uma política de proteção de aplicações do Windows 10, tem de ativar a gestão de aplicações móveis (MAM) para o Windows 10 ao configurar o fornecedor de MAM no Azure AD. Esta configuração permite-lhe definir o estado de inscrição quando criar uma nova política do Windows Information Protection (WIP) com o Intune.

> [!NOTE]
> O estado de inscrição pode ser MAM ou gestão de dispositivos móveis (MDM).

## <a name="to-configure-the-mam-provider"></a>Para configurar o fornecedor de MAM

1.  Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

2.  No menu à esquerda, escolha **Azure Active Directory**.

    ![Configuração do fornecedor de MAM](../media/AppManagement/mam-provider-sc-1.png)

3.  É apresentado o painel **Azure AD**, escolha **Mobilidade (MDM e MAM)** e, em seguida, clique em **Microsoft Intune**.

    ![Mobilidade de MDM e MAM](../media/AppManagement/mam-provider-sc-1.png)

4.  É apresentado o painel de configuração, escolha primeiro **Restaurar URLs de MAM predefinidos** e, em seguida, configure o seguinte:

    a.  Âmbito do utilizador de MAM: pode utilizar a MAM para proteger dados empresariais num grupo específico de utilizadores que utilizam dispositivos Windows 10 ou todos os utilizadores.

    b.  URL dos termos de utilização da MAM: o URL do ponto final dos termos de licenciamento do serviço MAM. Serve para apresentar o termo do serviço MAM aos utilizadores finais.

    c.  URL de deteção da MAM: este é o URL que os dispositivos procuram quando precisam de aplicar políticas de proteção de aplicações.

    d.  URL de conformidade de MAM:

5.  Depois de configurar estas definições, escolha **Guardar**.

## <a name="next-steps"></a>Próximos passos

[Criar uma política de proteção de aplicações WIP](https://docs.microsoft.com/intune-azure/manage-apps/create-windows-information-protection-policy-with-intune)

