---
title: Monitorizar a conformidade do dispositivo
titlesuffix: Microsoft Intune
description: Saiba como monitorizar a conformidade do dispositivo."
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b363e074b1b0652a81d56c68e28cf11220adfa56
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="monitor-device-compliance-in-intune"></a>Monitorizar a conformidade do dispositivo no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode ver o resumo do estado dos seus **perfis de conformidade** no painel **Descrição geral**.
Pode clicar interativamente nas tabelas para desagregar os detalhes. Se tiver múltiplos perfis de conformidade configurados, pode ver o estado da política no painel de políticas em **Gerir** > **Relatórios**.

##  <a name="device-compliance"></a>Conformidade do dispositivo

A vista resumida do relatório de conformidade do dispositivo lista as informações agregadas sobre o número de dispositivos que estão a enviar relatórios num dos seguintes estados:

- **Conforme**: o dispositivo foi avaliado recentemente e está em conformidade com as definições de conformidade do perfil que especificou.
- **Não conforme**: o dispositivo foi avaliado e determinado como não conforme.  Se existia um período de tolerância especificado no perfil, o período de tolerância expirou, o que coloca o dispositivo num estado de não conforme.
- **Período de tolerância**: o dispositivo foi avaliado e determinado como não conforme. No entanto, o período de tolerância ainda se aplica antes de o dispositivo ser assinalado como não conforme.

Pode desagregar cada secção para ver mais detalhes sobre os utilizadores e dispositivos individuais.

## <a name="setting-compliance"></a>Conformidade com definições

O relatório de conformidade com as definições disponibiliza os detalhes para cada uma das definições de conformidade, tais como:

- Número de dispositivos não conformes com a definição.
- A plataforma à qual se aplica a definição.

Pode desagregar cada uma das definições para ver mais informações sobre os perfis nos quais estas definições foram ativadas, bem como o valor da definição.
