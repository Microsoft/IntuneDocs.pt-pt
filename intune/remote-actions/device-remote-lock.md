---
title: Bloquear dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Utilize a ação Bloqueio remoto no Microsoft Intune para bloquear um dispositivo protegido por um PIN ou palavra-passe.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bce5a89ecc49952f5c21536c429e9cd3309b13c3
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712276"
---
# <a name="remotely-lock-devices-with-intune"></a>Bloquear remotamente dispositivos com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A ação **Bloqueio remoto** bloqueia o dispositivo. Para desbloquear o dispositivo, o proprietário do dispositivo introduz o código de acesso. Pode bloquear remotamente dispositivos que tenham um PIN ou uma palavra-passe definida. Os dispositivos que não tenham um PIN ou palavra-passe não podem ser bloqueados remotamente.

## <a name="supported-platforms"></a>Plataformas suportadas

O **Bloqueio remoto** é suportado pelas seguintes plataformas:

- Android
- Dispositivos de quiosque Android Enterprise
- Dispositivos com perfil de trabalho do Android Enterprise
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 e posterior

O **Bloqueio remoto** não é suportado para:
- Computadores com o Windows 10

> [!NOTE]
> Para dispositivos macOS, defina um PIN de recuperação de 6 dígitos. Se o dispositivo estiver bloqueado, a **Descrição geral do dispositivo** apresenta o PIN até que seja enviada outra ação de dispositivo.

## <a name="remote-lock-a-device"></a>Bloquear remotamente um dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Dispositivos** > **Todos os dispositivos**.
4. Na lista de dispositivos, selecione um dispositivo e, em seguida, selecione a ação **Bloqueio remoto**.

## <a name="next-steps"></a>Próximos passos

- Para ver o estado desta ação, selecione **Microsoft Intune** > **Dispositivos** > **Ações do dispositivo**. 
- Para obter mais ações que podem ajudá-lo a gerir os seus dispositivos, veja [Ações disponíveis](device-management.md).
