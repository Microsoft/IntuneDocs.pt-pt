---
title: Reiniciar dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Reinicie dispositivos Windows e iOS através do Microsoft Intune no portal do Azure com a ação remota Reiniciar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc9cc03c5ca0243d41990e1aeab1d9bf4a707de8
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229722"
---
# <a name="remotely-restart-devices-with-intune"></a>Reiniciar remotamente dispositivos com o Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Reiniciar** provoca o reinício do dispositivo que escolheu. O proprietário do dispositivo não é automaticamente notificado relativamente ao reinício e poderá perder trabalho.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado no Windows 8.1 e posterior
- Windows Phone – suportado no Windows Phone 8.1 e posterior
- Dispositivos de quiosque Android – suportados no Android 7.0 e posterior
- iOS – suportado

    > [!Note]  
    > Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, o dispositivo poderá não conseguir comunicar com o servidor.
- macOS – não suportado
- Dispositivos Android e dispositivos com perfil de trabalho do Android – não suportado

## <a name="restart-a-device"></a>Reiniciar um dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** > **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo, selecione **Mais** e, em seguida, selecione a ação remota **Reiniciar** do dispositivo.

## <a name="next-steps"></a>Passos Seguintes

- Para ver o estado da ação **Reiniciar** do dispositivo, selecione **Dispositivos** > **Ações do dispositivo**.
