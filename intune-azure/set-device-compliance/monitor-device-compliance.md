---
title: Como monitorizar a compatibilidade do dispositivo
titleSuffix: Intune Azure preview
description: "Pé-visualização do Azure no Intune: saiba como monitorizar a conformidade dos dispositivos."
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
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d59d94aafa71a9891a6746902339255ea7a9ad15
ms.lasthandoff: 02/18/2017


---
# <a name="how-to-monitor-compliance-in-intune-azure-preview"></a>Como monitorizar a conformidade dos dispositivos na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pode ver o resumo do estado dos seus **perfis de conformidade** no painel **Descrição geral**.
Pode clicar interativamente nas tabelas para desagregar os detalhes. Se tiver vários perfis de conformidade configurados, também pode ver o estado de cada política ao aceder ao painel de política e escolher **Relatórios** na secção **Gerir**.  Os detalhes dos relatórios disponíveis para a pré-visualização estão listados abaixo.

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

Pode desagregar cada uma das definições para ver mais informações sobre os perfis nos quais estas definições tenham sido ativadas, bem como o valor configurado da definição.

