---
title: Como monitorizar a compatibilidade do dispositivo
titleSuffix: Intune on Azure
description: Saiba como monitorizar a conformidade do dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f18bfa7fb045dbad4ab785c2c8e1bc13fc439db
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-monitor-device-compliance-in-intune"></a>Como monitorizar a conformidade do dispositivo no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode ver o resumo do estado dos seus **perfis de conformidade** no painel **Descrição geral**.
Pode clicar interativamente nas tabelas para desagregar os detalhes. Se tiver vários perfis de conformidade configurados, também pode ver o estado de cada política ao aceder ao painel de política e escolher **Relatórios** na secção **Gerir**.  Os detalhes dos relatórios disponíveis estão listados abaixo.

##  <a name="device-compliance"></a>Conformidade do dispositivo

A vista resumida do relatório de conformidade do dispositivo começa com a apresentação das informações agregadas sobre o número de dispositivos que estão a enviar relatórios como um dos seguintes:

- **Conformidade**: o dispositivo foi avaliado quanto à compatibilidade recentemente e foi determinado como estando em conformidade com as definições do perfil de conformidade que especificou.
- **Não conforme**: o dispositivo foi avaliado e determinado como não conforme.  Se existia um período de tolerância especificado no perfil, o período de tolerância expirou, o que coloca o dispositivo num estado de não conforme.
- **Período de tolerância**: o dispositivo foi avaliado e determinado como não conforme. No entanto, o período de tolerância ainda se aplica antes de o dispositivo ser de facto assinalado como não conforme.

Pode desagregar cada secção para ver mais detalhes sobre os utilizadores e dispositivos individuais.

## <a name="setting-compliance"></a>Conformidade com definições

O relatório de conformidade com definições disponibiliza os detalhes para cada uma das definições de conformidade, tais como:

- Número de dispositivos não conformes com a definição.
- A plataforma à qual se aplica a definição.

Pode desagregar cada uma das definições para ver mais informações sobre os perfis nos quais estas definições foram ativadas, bem como o valor da definição.
