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
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 428b4040eb0d91b7fe32fcf71842ce5bd1910013
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713216"
---
# <a name="erase-all-data-from-a-macos-device"></a>Apagar todos os dados de um dispositivo macOS

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pode apagar todos os dados de um dispositivo macOS, incluindo o sistema operativo. O dispositivo também será removido da gestão do Intune. O utilizador final não receberá qualquer aviso.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **todos os dispositivos** > escolha o dispositivo que você deseja apagar.
![Captura de ecrã](./media/device-erase/choosedevice.png)
2. Clique em **Mais** > **Apagar** > forneça um número de 6 dígitos para o **PIN de Recuperação**. Este é o PIN que tem de dar ao utilizador para que possa reinstalar o sistema operativo no respetivo dispositivo. Certifique-se de que anota este PIN, porque o mesmo deixará de ser visível assim que a ação de apagamento for concluída.
![Captura de ecrã](./media/device-erase/providepin.png)
3. Clique em **OK** para apagar o dispositivo.
