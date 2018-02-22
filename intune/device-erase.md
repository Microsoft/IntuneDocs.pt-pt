---
title: Apagar um dispositivo macOS
titlesuffix: Azure portal
description: Saiba como apagar todos os dados, incluindo o sistema operativo, de um dispositivo macOS.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81f328004863e812b706174e74a9b74d0bdf80b6
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2018
---
# <a name="erase-all-data-from-a-macos-device"></a>Apagar todos os dados de um dispositivo macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode apagar todos os dados de um dispositivo macOS, incluindo o sistema operativo. O dispositivo também será removido da gestão do Intune. O utilizador final não receberá qualquer aviso.

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo que pretende apagar.
![Captura de ecrã](./media/device-erase/choosedevice.png)
2. Clique em **Mais** > **Apagar** > forneça um número de 6 dígitos para o **PIN de Recuperação**. Este é o PIN que tem de dar ao utilizador para que possa reinstalar o sistema operativo no respetivo dispositivo. Certifique-se de que anota este PIN, porque o mesmo deixará de ser visível assim que a ação de apagamento for concluída.
![Captura de ecrã](./media/device-erase/providepin.png)
3. Clique em **OK** para apagar o dispositivo.
