---
title: Apagar um dispositivo macOS
titleSuffix: Microsoft Intune
description: Saiba como apagar todos os dados, incluindo o sistema operativo, de um dispositivo macOS.
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
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 446c88dabb070c42e47e2bb2d2ac87d6acecdedc
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781958"
---
# <a name="erase-all-data-from-a-macos-device"></a>Apagar todos os dados de um dispositivo macOS

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pode apagar todos os dados de um dispositivo macOS, incluindo o sistema operativo. O dispositivo também será removido da gestão do Intune. O utilizador final não receberá qualquer aviso.

1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **Todos os dispositivos** > escolha o dispositivo que pretende apagar.
2. Clique em **Mais** > **Apagar** > forneça um número de 6 dígitos para o **PIN de Recuperação**. Este é o PIN que tem de dar ao utilizador para que possa reinstalar o sistema operativo no respetivo dispositivo. Certifique-se de que anota este PIN, porque o mesmo deixará de ser visível assim que a ação de apagamento for concluída.
![Captura de ecrã](./media/device-erase/providepin.png)
3. Clique em **OK** para apagar o dispositivo.
