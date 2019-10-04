---
title: Entender a entrega e o tempo da política de proteção de aplicativo
titleSuffix: Microsoft Intune
description: Conheça as diferentes janelas de implantação para as políticas de proteção de aplicativo para entender quando as alterações devem aparecer em seus dispositivos de usuário final.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9f9b6734dc5a5af320519a5f65442f01d21d66f
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940238"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Entender o tempo de entrega da política de proteção do aplicativo

Conheça as diferentes janelas de implantação para as políticas de proteção de aplicativo para entender quando as alterações devem aparecer em seus dispositivos de usuário final.

## <a name="delivery-timing-summary"></a>Resumo do tempo de entrega

A entrega de política de proteção de aplicativo depende do estado da licença e do registro do serviço do Intune para seus usuários.  

|    Estado do usuário    |    Comportamento de proteção do aplicativo     |    Intervalo de repetição (consulte a observação)    |    Por que isso acontece?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Locatário não integrado    |    Aguarde o próximo intervalo de repetição.  A proteção do aplicativo não está ativa para o usuário.    |    24 horas    |    Ocorre quando você não configura seu locatário para o Intune.    |
|    Usuário não licenciado     |    Aguarde o próximo intervalo de repetição.  A proteção do aplicativo não está ativa para o usuário.     |    12 horas-no entanto, em dispositivos Android, esse intervalo requer o SDK de aplicativo do Intune versão 5.6.0 ou posterior. Caso contrário, para dispositivos Andriod, o intervalo é de 24 horas.   |    Ocorre quando você não licencia o usuário para o Intune.    |
|    O usuário não atribuiu políticas de proteção de aplicativo    |    Aguarde o próximo intervalo de repetição.  A proteção do aplicativo não está ativa para o usuário.    |    12 horas        |    Ocorre quando você não atribui configurações de aplicativo ao usuário.    |
|    Usuário registrado com êxito para o MAM do Intune    |    A proteção do aplicativo é aplicada por configurações de política.    As atualizações ocorrem com base no intervalo de repetição    |    Serviço do Intune definido com base na carga do usuário.    Normalmente, 30 minutos.     |    Ocorre quando o usuário é registrado com êxito com o serviço do Intune para configuração de MAM.    |

> [!NOTE]
> Os intervalos de repetição podem exigir que o uso do aplicativo ativo ocorra, o que significa que o aplicativo é iniciado e em uso.  Se o intervalo de repetição é de 24 horas e o usuário aguarda 48 horas para iniciar o aplicativo, o cliente de proteção de aplicativo tentará novamente às 48 horas.

## <a name="handling-network-connectivity-issues"></a>Lidando com problemas de conectividade de rede

Quando o registro de usuário falha devido a problemas de conectividade de rede, é usado um intervalo de repetição acelerado.  O cliente de proteção de aplicativo tentará novamente em intervalos cada vez mais longos até que o intervalo atinja 60 minutos ou uma conexão bem-sucedida seja feita.  O cliente continuará a tentar novamente a intervalos de 60 minutos até que uma conexão bem-sucedida seja feita. Em seguida, o cliente voltará ao intervalo de repetição padrão com base no estado do usuário.

## <a name="next-steps"></a>Passos seguintes

[Atribuir licenças aos utilizadores para que estes possam inscrever dispositivos no Intune](../fundamentals/licenses-assign.md)

