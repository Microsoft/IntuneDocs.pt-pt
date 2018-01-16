---
title: Reiniciar remotamente dispositivos com o Intune
titlesuffix: Azure portal
description: "Saiba como reiniciar remotamente dispositivos com a ação de dispositivos reiniciar.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7177616d654ca9af0b7e7276a1a4b5453117f36c
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/12/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Reiniciar remotamente dispositivos com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Reiniciar** provoca o reinício do dispositivo que escolheu. O proprietário do dispositivo não é automaticamente notificado relativamente ao reinício, por isso, poderá perder trabalho.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado no Windows 8.1 e posterior
- Windows Phone – suportado no Windows Phone 8.1 e posterior
- iOS – suportado

    > [!Note]  
    > Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.
- macOS – não suportado
- Android – não suportado

## <a name="how-to-restart-a-device"></a>Como reiniciar um dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Reiniciar**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
