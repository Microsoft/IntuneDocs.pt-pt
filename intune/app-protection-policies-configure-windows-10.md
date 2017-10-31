---
title: "Preparar-se para configurar políticas de proteção de aplicações para o Windows 10"
titlesuffix: Azure portal
description: "Configurar o fornecedor de gestão de aplicações móveis (MAM) no Azure AD"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d18ef2119ed0f8adc63f6675024c8e694235ee35
ms.sourcegitcommit: 128770ecc820f6ff3c99b15752bce7a58257f1d5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/21/2017
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparar-se para configurar políticas de proteção de aplicações para o Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de criar uma política de proteção de aplicações do Windows 10, tem de ativar a gestão de aplicações móveis (MAM) para o Windows 10 ao configurar o fornecedor de MAM no Azure AD. Esta configuração permite-lhe definir o estado de inscrição quando criar uma nova política do Windows Information Protection (WIP) com o Intune.

> [!NOTE]
> O estado de inscrição pode ser MAM ou gestão de dispositivos móveis (MDM).

## <a name="to-configure-the-mam-provider"></a>Para configurar o fornecedor de MAM

1.  Aceda ao [portal do Azure](https://portal.azure.com/) e inicie sessão com as credenciais do Intune.

2.  No menu à esquerda, escolha **Azure Active Directory**.

    ![Configuração do fornecedor de MAM](./media/mam-provider-sc-1.png)

3.  É apresentado o painel **Azure AD**, escolha **Mobilidade (MDM e MAM)** e, em seguida, clique em **Microsoft Intune**.

    ![Mobilidade de MDM e MAM](./media/mam-provider-sc-1.png)

4.  É apresentado o painel de configuração, escolha primeiro **Restaurar URLs de MAM predefinidos** e, em seguida, configure o seguinte:

    a.  Âmbito do utilizador de MAM: pode utilizar a MAM para proteger dados empresariais num grupo específico de utilizadores que utilizam dispositivos Windows 10 ou todos os utilizadores.

    b.  URL dos termos de utilização da MAM: o URL do ponto final dos termos de licenciamento do serviço MAM. Serve para apresentar o termo do serviço MAM aos utilizadores finais.

    c.  URL de deteção da MAM: este é o URL que os dispositivos procuram quando precisam de aplicar políticas de proteção de aplicações.

    d.  URL de conformidade de MAM:

5.  Depois de configurar estas definições, escolha **Guardar**.

> [!NOTE]
> Os dispositivos com um estado de inscrição MAM têm de estar associados ao Azure AD.

## <a name="next-steps"></a>Passos seguintes

[Criar uma política de proteção de aplicações WIP](windows-information-protection-policy-create.md)
