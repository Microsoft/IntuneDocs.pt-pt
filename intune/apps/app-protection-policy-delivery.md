---
title: Compreender a entrega e o timing da política de proteção de aplicações
titleSuffix: Microsoft Intune
description: Aprenda as diferentes janelas de implementação para que as políticas de proteção de aplicações compreendam quando as alterações devem aparecer nos seus dispositivos de utilizador final.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: d26721ff27f380917fec7f4d23c0c5524737a4a3
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216161"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Compreender o timing de entrega da política de proteção de aplicações

Aprenda as diferentes janelas de implementação para que as políticas de proteção de aplicações compreendam quando as alterações devem aparecer nos seus dispositivos de utilizador final.

## <a name="delivery-timing-summary"></a>Resumo do prazo de entrega

A entrega da política de proteção de aplicações depende do estado de licença e do registo do serviço Intune para os seus utilizadores.  

|    Estado de Utilizador    |    Comportamento de Proteção de Aplicativos     |    Intervalo de repetição (ver nota)    |    Por que isso acontece?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Inquilino Não Abordo    |    Aguarde o próximo intervalo de repetição.  A Proteção de Aplicações não está ativa para o utilizador.    |    24 horas    |    Ocorre quando não instalou o seu inquilino para o Intune.    |
|    Utilizador não licenciado     |    Aguarde o próximo intervalo de repetição.  A Proteção de Aplicações não está ativa para o utilizador.     |    12 horas - No entanto, em dispositivos Android este intervalo requer a versão 5.6.0 da APP SDK intune. Caso contrário, para os dispositivos Andriod, o intervalo é de 24 horas.   |    Ocorre quando não licenciou o utilizador para o Intune.    |
|    Políticas de proteção de aplicações não atribuídas ao utilizador    |    Aguarde o próximo intervalo de repetição.  A Proteção de Aplicações não está ativa para o utilizador.    |    12 horas        |    Ocorre quando não atribuiu as definições de APP ao utilizador.    |
|    Políticas de proteção de aplicações atribuídas ao utilizador, mas a app não está definida nas Políticas de Proteção de Aplicações   |    Aguarde o próximo intervalo de repetição.  A Proteção de Aplicações não está ativa para o utilizador.    |    12 horas        |    Ocorre quando não adicionou a app à APP.    |
|    Utilizador registado com sucesso para Intune MAM    |    A Proteção de Aplicações é aplicada de acordo com as definições de política.    As atualizações ocorrem com base no intervalo de repetição    |    Serviço Intune definido com base na carga do utilizador.    Normalmente 30 minutos.     |    Ocorre quando o utilizador se registou com sucesso no serviço Intune para a configuração MAM.    |

> [!NOTE]
> Intervalos de repetição podem exigir a utilização ativa da aplicação, o que significa que a aplicação é lançada e em uso.  Se o intervalo de repetição for de 24 horas e o utilizador esperar 48 horas para lançar a aplicação, o cliente de Proteção de Aplicações voltará a tentar às 48 horas.

## <a name="handling-network-connectivity-issues"></a>Lidar com problemas de conectividade da rede

Quando o registo do utilizador falha devido a problemas de conectividade de rede, é utilizado um intervalo de repetição acelerado.  O cliente de Proteção de Aplicações irá voltar a tentar em intervalos cada vez mais longos até que o intervalo atinja 60 minutos ou seja feita uma ligação bem sucedida.  O cliente continuará então a tentar novamente em intervalos de 60 minutos até que seja feita uma ligação bem sucedida. Em seguida, o cliente voltará ao intervalo padrão de repetição com base no estado do utilizador.

## <a name="next-steps"></a>Próximos passos

[Atribuir licenças aos utilizadores para que estes possam inscrever dispositivos no Intune](../fundamentals/licenses-assign.md)

