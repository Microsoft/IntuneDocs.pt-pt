---
title: "Bloquear dispositivos com o Microsoft Intune – Azure | Microsoft Docs"
description: "Utilize a ação Bloqueio Remoto no Microsoft Intune para bloquear um dispositivo protegido por um PIN ou palavra-passe."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59a55de54a5a18f5fd1080fefa15c0e4801a1456
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="remotely-lock-devices-with-intune"></a>Bloquear remotamente dispositivos com o Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O **Bloqueio remoto** bloqueia o dispositivo. Para desbloqueá-lo, o proprietário do dispositivo introduz o código de acesso. Pode bloquear remotamente dispositivos que tenham um PIN ou uma palavra-passe definida. Os dispositivos que não tenham um PIN ou código de acesso não podem ser bloqueados remotamente.

## <a name="supported-platforms"></a>Plataformas suportadas

O bloqueio remoto é suportado pelas seguintes plataformas:

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 e posterior

O bloqueio remoto **não** é suportado em:
- Computadores com o Windows 10

> [!NOTE]
> Para dispositivos macOS, defina um PIN de recuperação de 6 dígitos. Se estiver bloqueado, a **Descrição geral do dispositivo** apresenta o PIN até que seja enviada outra ação de dispositivo.

## <a name="remote-lock-a-device"></a>Bloquear remotamente um dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. Na lista de dispositivos, selecione um dispositivo e, em seguida, selecione a ação **Bloqueio remoto**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado desta ação, abra as **Ações do dispositivo** (Microsoft Intune > Dispositivos). Veja [Ações disponíveis](device-management.md) para obter mais ações que o irão ajudar a gerir os seus dispositivos.