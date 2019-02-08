---
title: Monitorizar a conformidade do dispositivo
titlesuffix: Microsoft Intune
description: Saiba como monitorizar a conformidade do dispositivo."
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 534e8316e584259a818130ea9f83c88b44b67fee
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848088"
---
# <a name="monitor-device-compliance-in-intune"></a>Monitorizar a conformidade do dispositivo no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode ver o resumo do estado dos seus **perfis de conformidade** no painel **Descrição geral**.
Pode clicar interativamente nas tabelas para desagregar os detalhes. Se tiver múltiplos perfis de conformidade configurados, pode ver o estado da política no painel de políticas em **Gerir** > **Relatórios**.

##  <a name="device-compliance"></a>Conformidade do dispositivo

A vista resumida do relatório de conformidade do dispositivo lista as informações agregadas sobre o número de dispositivos que estão a enviar relatórios num dos seguintes estados:

- **Em conformidade**: O dispositivo foi avaliado recentemente e está em conformidade com as definições de perfil de conformidade que especificou.
- **Em não conformidades**: O dispositivo foi avaliado e determinado como não conforme.  Se existia um período de tolerância especificado no perfil, o período de tolerância expirou, o que coloca o dispositivo num estado de não conforme.
- **Período de tolerância**: Dispositivo foi avaliado e determinado como não conforme. No entanto, o período de tolerância ainda se aplica antes de o dispositivo ser assinalado como não conforme.

Pode desagregar cada secção para ver mais detalhes sobre os utilizadores e dispositivos individuais.

## <a name="setting-compliance"></a>Conformidade com definições

O relatório de conformidade com as definições disponibiliza os detalhes para cada uma das definições de conformidade, tais como:

- Número de dispositivos não conformes com a definição.
- A plataforma à qual se aplica a definição.

Pode desagregar cada uma das definições para ver mais informações sobre os perfis nos quais estas definições foram ativadas, bem como o valor da definição.
