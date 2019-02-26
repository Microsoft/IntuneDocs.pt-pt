---
title: Entrega de políticas de proteção de aplicações de Undertastand e temporização das atualizações
titleSuffix: Microsoft Intune
description: Saiba as janelas de implementação diferentes de políticas de proteção de aplicações compreender quando alterações devem aparecer nos seus dispositivos de utilizador final.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69cab2f2cda974249eccba90f203b4b06c29806f
ms.sourcegitcommit: a9bb967273e8df7e743c9826948582fda555c02d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56795550"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Compreender o tempo de entrega de política de proteção de aplicações

Saiba as janelas de implementação diferentes de políticas de proteção de aplicações compreender quando alterações devem aparecer nos seus dispositivos de utilizador final.

## <a name="delivery-timing-summary"></a>Resumo de tempo de entrega

Entrega de políticas de proteção de aplicação depende do Estado de licença e o registo de serviço do Intune para os seus utilizadores.  

|    Estado do utilizador    |    Comportamento de proteção de aplicação     |    Intervalo de repetição (ver nota)    |    Por que isso acontece?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Não incluído de inquilino    |    Aguarde o próximo intervalo entre tentativas.  Proteção de aplicações não está ativa para o utilizador.    |    24 horas    |    Ocorre quando não tiver configurado o inquilino do Intune.    |
|    Utilizador não licenciado     |    Aguarde o próximo intervalo entre tentativas.  Proteção de aplicações não está ativa para o utilizador.     |    12 horas – no entanto, em dispositivos Android este intervalo requer o SDK da aplicação Intune versão 5.6.0 ou posterior. Caso contrário, para suportará dispositivos, o intervalo é de 24 horas.   |    Ocorre quando não tiver licenciado o utilizador para o Intune.    |
|    Utilizador não atribuída políticas de proteção de aplicações    |    Aguarde o próximo intervalo entre tentativas.  Proteção de aplicações não está ativa para o utilizador.    |    12 horas        |    Ocorre quando não tiver atribuído as definições da aplicação para o usuário.    |
|    Utilizador registado com êxito para MAM do Intune    |    Proteção de aplicações é aplicada por definições de política.    Atualizações ocorrem com base no intervalo entre tentativas    |    Serviço do Intune definidas com base na carga de utilizador.    Normalmente de 30 minutos.     |    Ocorre quando o utilizador registou com êxito com o serviço do Intune para a configuração de MAM.    |

> [!NOTE]
> Intervalos de repetição podem exigir a utilização da aplicação do Active Directory possa ocorrer, que significa que a aplicação é iniciada e em utilização.  Se o intervalo entre tentativas é de 24 horas e o usuário aguarda 48 horas para iniciar a aplicação, o cliente de proteção de aplicações irá repetir em 48 horas.

## <a name="handling-network-connectivity-issues"></a>Lidar com problemas de conectividade de rede

Quando o registo de utilizador falhar devido a problemas de conectividade de rede é utilizado um intervalo de repetição acelerado.  O cliente de proteção de aplicações será repetida em intervalos de cada vez mais até que o intervalo de atinge os 60 minutos ou é feita uma ligação com êxito.  O cliente, em seguida, irá continuar a repetir em intervalos de 60 minutos, até que seja estabelecida uma ligação com êxito. Em seguida, o cliente será retornado para o intervalo de repetição padrão com base no estado do utilizador.

## <a name="next-steps"></a>Passos Seguintes

[Atribuir licenças aos utilizadores para que eles possam inscrever dispositivos no Intune](licenses-assign.md)

