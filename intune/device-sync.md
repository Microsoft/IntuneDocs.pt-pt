---
title: Sincronizar dispositivos com o Intune
titlesuffix: Azure portal
description: "Saiba como sincronizar dispositivos com o Intune para obter as políticas e ações mais recentes."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3906b567935f026202ccf0e81424a1bb36e376ef
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Sincronizar dispositivos com o Intune para obter as políticas e ações mais recentes


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação **Sincronizar** dispositivo força o dispositivo selecionado a registar-se imediatamente com o Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo.  Esta ação pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado
- Windows Phone – suportado
- iOS – suportado
- macOS – suportado
- Android – suportado

## <a name="how-to-sync-a-device"></a>Como sincronizar um dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota **Sincronizar**.
7. Selecione **Sim** para confirmar a ação.

## <a name="next-steps"></a>Próximos passos

Selecione **Ações do Dispositivo** para ver o estado da ação de sincronização. 
