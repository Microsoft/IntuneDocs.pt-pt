---
title: Renomear um dispositivo com Microsoft Intune-Azure | Microsoft Docs
description: Renomear um dispositivo usando Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d109529e2c5dafdf8d5b4e0d73191d1715ecd8c
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71304662"
---
# <a name="rename-a-device-in-intune"></a>Renomear um dispositivo no Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação **renomear dispositivo** permite renomear um dispositivo registrado no Intune. O nome do dispositivo é alterado no Intune e no dispositivo.

Você pode renomear os seguintes tipos de dispositivos:
- Janelas de propriedade corporativa 
- supervisionado do iOS
- MacOS 10 de propriedade corporativa

No momento, esse recurso não dá suporte à renomeação de dispositivos Windows do Azure AD híbridos.

## <a name="rename-a-device"></a>Renomear um dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Escolha **dispositivos** > **todos os dispositivos** > escolha um dispositivo > **mais** > **renomear dispositivo**.
4. Na folha **renomear dispositivo** , digite o novo nome na caixa de texto. Você pode usar letras, números e hifens. O nome deve conter pelo menos uma letra ou hífen.
5. Se você quiser reiniciar o dispositivo depois de renomeá-lo, escolha **Sim** avançar para **reiniciar após a renomeação**.
6. Escolha **renomear**.



## <a name="next-steps"></a>Passos seguintes

Para ver o status da ação **renomear** dispositivo, verifique a página **visão geral** do dispositivo.
