---
title: Reiniciar dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Reiniciar os dispositivos Windows e iOS/iPadOS utilizando o Microsoft Intune no portal Azure utilizando a ação remota Restart.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
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
ms.openlocfilehash: 54fa0f796e96a2487793197cbbbe548fd8490856
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415624"
---
# <a name="remotely-restart-devices-with-intune"></a>Reiniciar remotamente dispositivos com o Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A ação do dispositivo **Restart** faz com que o dispositivo que escolher seja reiniciado (dentro de 5 minutos). O proprietário do dispositivo não é automaticamente notificado relativamente ao reinício e poderá perder trabalho.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado no Windows 8.1 e posterior
- Windows Phone – suportado no Windows Phone 8.1 e posterior
- Dispositivos Android quiosque-com suporte no Android 7,0 e posterior
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
