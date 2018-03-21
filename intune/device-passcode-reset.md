---
title: "Repor códigos de acesso de dispositivos com o Microsoft Intune – Azure | Microsoft Docs"
description: "Remova ou reponha o código de acesso com a ação Remover código de acesso nos dispositivos dos quais faça a gestão ou monitorização com o Intune."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f23a79bbe72d12750ef642226aefd1e11dcac24
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Repor ou remover um código de acesso do dispositivo no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para criar um novo código de acesso para um dispositivo, utilize a ação **Remover código de acesso**.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows Phone 8.1 à Atualização para Criativos do Windows 10 não associada ao Azure AD e Atualização para Criativos do Windows 10 e posterior
- iOS
- Versões do Android anteriores ao Android 7

Esta funcionalidade **não** é suportada para os seguintes sistemas:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Repor um código de acesso

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo, selecione **...Mais** e, em seguida, selecione a ação remota de dispositivos **Remover código de acesso**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, em **Dispositivos**, selecione **Ações do dispositivo**.
