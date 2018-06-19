---
title: Considerações especiais sobre a migração
titlesuffix: Microsoft Intune
description: Este artigo fornece considerações especiais sobre a migração antes de iniciar uma campanha de migração para o Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: bd59cf3a4764cc66d0e7d1f47e69c2ff93352387
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2018
ms.locfileid: "29925986"
---
# <a name="special-migration-considerations"></a>Considerações especiais sobre a migração

Existem considerações especiais sobre a migração que podem ser aplicáveis, dependendo do ambiente do fornecedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Reposição de fábrica do Programa de Inscrição de Dispositivos (DEP) da Apple

O Programa de Inscrição de Dispositivos (DEP) da Apple define configurações do dispositivo que não podem ser removidas pelo utilizador final. Para manter as funcionalidades da gestão avançada do DEP, o dispositivo tem de voltar ao estado inicial (novo) através da reposição de fábrica para a inscrição no Intune.

Para continuar a utilizar o DEP para gerir os dispositivos no Intune, [configure a inscrição de dispositivos iOS com o Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Próximos passos

[Fase 2: campanha de migração](migration-guide-campaign.md)
