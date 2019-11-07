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
ms.openlocfilehash: fdb23916319b06fb4d85b913209d1ac9e007d551
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713169"
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

1. Entre no [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e selecione **dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione um dispositivo iOS e, em seguida, selecione a ação remota de dispositivos **Terminar sessão do utilizador atual**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
