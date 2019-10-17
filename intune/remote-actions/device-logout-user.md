---
title: Terminar a sessão do utilizador num dispositivo iOS
titleSuffix: Microsoft Intune
description: Saiba como terminar a sessão do utilizador atual de um dispositivo iOS com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8336f5b29cd21bb6875285177071542080eb95f3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509450"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Terminar a sessão do utilizador atual em dispositivos iOS geridos pelo Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A ação **Terminar sessão do utilizador atual** termina a sessão do utilizador atual num dispositivo iPad partilhado. 

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – não suportado
- iOS – suportado no iOS 9.3 e posterior (apenas dispositivos iPad partilhados)
- macOS – não suportado
- Android – não suportado

## <a name="how-to-log-out-the-current-user"></a>Como terminar a sessão do utilizador atual

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione um dispositivo iOS e, em seguida, selecione a ação remota de dispositivos **Terminar sessão do utilizador atual**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
