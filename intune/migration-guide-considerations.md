---
title: "Considerações especiais sobre a migração"
description: "Este artigo fornece considerações especiais sobre a migração antes de iniciar uma campanha de migração."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 7ff1180275fddc7f0d6ef957c4680d7c34ad471e
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/12/2017
---
# <a name="special-migration-considerations"></a>Considerações especiais sobre a migração

Existem considerações especiais sobre a migração que podem ser aplicáveis, dependendo do ambiente do fornecedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Reposição de fábrica do Programa de Inscrição de Dispositivos (DEP) da Apple

O Programa de Inscrição de Dispositivos (DEP) da Apple define configurações do dispositivo que não podem ser removidas pelo utilizador final. Para manter as funcionalidades da gestão avançada do DEP, o dispositivo tem de voltar ao estado inicial (novo) através da reposição de fábrica para a inscrição no Intune.

Para continuar a utilizar o DEP para gerir os dispositivos no Intune, [configure a inscrição de dispositivos iOS com o Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Passos seguintes

[Fase 2: Campanha de migração](migration-guide-campaign.md)
