---
title: Mudar o nome de um dispositivo Windows com o Microsoft Intune – Azure | Documentos da Microsoft
description: Mudar o nome de um dispositivo Windows com o Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fdd5a19d46cd6081e5671ddd84e29bf7db2ef538
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57398958"
---
# <a name="rename-a-windows-device-in-intune"></a>Mudar o nome de um dispositivo Windows no Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O **mudança de nome de dispositivo** ação permite-lhe mudar o nome de um dispositivo Windows pertencentes à empresa, que está inscrito no Intune. Isto altera o nome do dispositivo no Intune, bem como no dispositivo. 


## <a name="rename-a-device"></a>Mudar o nome de um dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Escolher **todos os serviços**, filtre por **Intune**e escolha **Microsoft Intune**.
3. Escolher **dispositivos** > **todos os dispositivos** > Escolha um dispositivo de Windows > **mais** > **mudança de nome de dispositivo**.
4. Na **mudança de nome de dispositivo** painel, escreva o novo nome na caixa de texto. Pode utilizar letras, números e hífenes. O nome tem de conter pelo menos uma letra ou um hífen.
5. Se pretender reiniciar o dispositivo depois de alterar o seu nome, escolha **Sim** junto a **Resart após a mudança de nome**.
6. Escolher **mudar o nome**.



## <a name="next-steps"></a>Passos Seguintes

Para ver o estado do **mudar o nome** ação de dispositivo, verifique o **descrição geral** página para o dispositivo.
