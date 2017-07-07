---
title: "Monitorizar implementações de aplicações"
description: "Saiba como monitorizar aplicações implementadas com o Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9255a9cb966ef02aba11e0a6aaf7caf7e808a41c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="monitor-app-deployments-in-microsoft-intune"></a>Monitorizar implementações de aplicações no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>Monitorizar a implementação de uma aplicação
Pode ver as aplicações que gere e o estado de todas as implementações na consola de administração do Intune. <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>Para ver as aplicações que gere e o respetivo estado
Na área de trabalho **Aplicações**, escolha o nó **Aplicações** e, em seguida, escolha **Aplicações**.

É apresentada a lista de aplicações que gere. Pode escolher qualquer aplicação para ver um estado de instalação no painel inferior das janelas da consola. Escolha este estado para ver mais detalhes. Por exemplo, se o estado mostrar **1 utilizador tem este software disponível**, pode escolher a mensagem para ver o nome do utilizador.

> [!TIP]
> Pode utilizar a lista pendente **Filtros** para ver apenas as aplicações que cumprem os critérios que especificar, como as aplicações que não conseguiu instalar ou as que foram implementadas com êxito.
>
> ![Exemplo de filtros de aplicação](./media/app-filters.png)

Além disso, a área de trabalho **Dashboard** mostra uma descrição geral do estado das suas aplicações. Se clicar em qualquer parte da descrição geral, será direcionado para a lista de aplicações.

## <a name="to-view-more-detailed-information-about-an-app"></a>Para ver informações mais detalhadas sobre uma aplicação
Na lista de aplicações, selecione uma aplicação e, em seguida, escolha **Ver Propriedades**.

Na página **Propriedades de Software** da aplicação, escolha um dos seguintes separadores: **Geral** - Mostra informações gerais sobre a aplicação e o estado de instalação da mesma; **Dispositivos** - Mostra os dispositivos que instalaram com êxito a implementação segmentada de uma aplicação; **Utilizadores** - Mostra os utilizadores cujos dispositivos instalaram com êxito a implementação segmentada de uma aplicação.

Como anteriormente, pode utilizar a lista pendente **Filtros** para configurar os valores apresentados em cada um dos separadores.
