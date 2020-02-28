---
title: Reiniciar dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Reiniciar os dispositivos Windows e iOS/iPadOS utilizando o Microsoft Intune no portal Azure utilizando a ação remota Restart.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6312a71ecd341bf52057af4d3fb7c1b796b89d1
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781982"
---
# <a name="remotely-restart-devices-with-intune"></a>Reiniciar remotamente dispositivos com o Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A ação do dispositivo **Restart** faz com que o dispositivo que escolher seja reiniciado (dentro de 5 minutos). O proprietário do dispositivo não é automaticamente notificado relativamente ao reinício e poderá perder trabalho.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado no Windows 8.1 e posterior
- Windows Phone – suportado no Windows Phone 8.1 e posterior
- Dispositivos de quiosque Android - Suportado no Android 7.0 e mais tarde
- iOS/iPadOS - Suportado

    > [!Note]  
    > Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS/iPadOS bloqueados por código sem acesso não voltam a juntar-se a uma rede Wi-Fi após o reinício. Após o reinício, o dispositivo poderá não conseguir comunicar com o servidor.
- macOS – não suportado
- Dispositivos Android e dispositivos com perfil de trabalho do Android – não suportado

## <a name="restart-a-device"></a>Reiniciar um dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Dispositivos** > **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo > **Restart** > **Yes**.

## <a name="next-steps"></a>Próximos passos

- Para ver o estado da ação **Reiniciar** do dispositivo, selecione **Dispositivos** > **Ações do dispositivo**.
