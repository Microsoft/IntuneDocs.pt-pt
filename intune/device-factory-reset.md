---
title: "Repor dispositivos para definições de fábrica com o Intune"
titleSuffix: Intune on Azure
description: "Saiba como repor os dispositivos que gere com o Intune para as definições de fábrica.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 44f69179f76c8d5eeca1594485ca3a9c1b036188
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/09/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>Repor dispositivos geridos com o Intune para definições de fábrica


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A **Reposição de fábrica** repõe um dispositivo para as suas predefinições. O dispositivo deixará de ser gerido pelo Intune e os dados pessoais e da empresa serão removidos. Não pode anular esta ação.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado no Windows 8.1 e posterior (não são suportados dispositivos geridos pelo EAS)
- Windows Phone – suportado
- iOS – suportado
- macOS – não suportado
- Android – suportado (o Android for Work não é suportado)

## <a name="how-to-reset-a-device-to-factory-settings"></a>Como repor um dispositivo para as definições de fábrica

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Reposição de fábrica**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.

