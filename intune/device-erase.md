---
title: Apagar um dispositivo macOS
titleSuffix: Microsoft Intune
description: Saiba como apagar todos os dados, incluindo o sistema operativo, de um dispositivo macOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d4203f559fc9c5f66a9b9317040c0123aecb1940
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237006"
---
# <a name="erase-all-data-from-a-macos-device"></a>Apagar todos os dados de um dispositivo macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode apagar todos os dados de um dispositivo macOS, incluindo o sistema operativo. O dispositivo também será removido da gestão do Intune. O utilizador final não receberá qualquer aviso.

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo que pretende apagar.
![Captura de ecrã](./media/device-erase/choosedevice.png)
2. Clique em **Mais** > **Apagar** > forneça um número de 6 dígitos para o **PIN de Recuperação**. Este é o PIN que tem de dar ao utilizador para que possa reinstalar o sistema operativo no respetivo dispositivo. Certifique-se de que anota este PIN, porque o mesmo deixará de ser visível assim que a ação de apagamento for concluída.
![Captura de ecrã](./media/device-erase/providepin.png)
3. Clique em **OK** para apagar o dispositivo.
