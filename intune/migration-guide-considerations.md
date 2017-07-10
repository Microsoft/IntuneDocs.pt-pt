---
title: "Considerações especiais sobre a migração"
description: "O objetivo deste artigo é proporcionar considerações especiais sobre a migração ao cliente antes de este começar uma campanha de migração."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="special-migration-considerations"></a>Considerações especiais sobre a migração

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Existem considerações especiais sobre a migração que poderão ser aplicáveis, dependendo do ambiente do fornecedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Reposição de fábrica do Programa de Inscrição de Dispositivos (DEP) da Apple

O Programa de Inscrição de Dispositivos (DEP) da Apple define configurações do dispositivo que não podem ser removidas pelo utilizador final. Para manter as funcionalidades da gestão avançada do DEP, o dispositivo tem de voltar ao estado inicial (novo) através da reposição de fábrica para a inscrição no Intune.

Para continuar a utilizar o DEP para gerir os dispositivos no Intune, [configure a inscrição de dispositivos iOS com o Programa de Inscrição de Dispositivos](/intune/device-enrollment-program-enroll-ios).


## <a name="next-steps"></a>Próximos passos 

[Fase 2: Campanha de migração](migration-guide-campaign.md)
