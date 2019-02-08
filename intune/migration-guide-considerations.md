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
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6726a9880d3d7ec34e5e0d13a4342710df4b8d5e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836954"
---
# <a name="special-migration-considerations"></a>Considerações especiais sobre a migração

Existem considerações especiais sobre a migração que podem ser aplicáveis, dependendo do ambiente do fornecedor de MDM existente.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Apagar dados para o Programa de Registo de Aparelho (DEP) da Apple

O Programa de Inscrição de Dispositivos (DEP) da Apple define configurações do dispositivo que não podem ser removidas pelo utilizador final. Para manter as funcionalidades da gestão avançada do DEP, o dispositivo tem de voltar ao estado inicial (novo) através da eliminação dos dados do mesmo para a inscrição no Intune.

Para continuar a utilizar o DEP para gerir os dispositivos no Intune, [configure a inscrição de dispositivos iOS com o Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Passos Seguintes

[Fase 2: Campanha de migração](migration-guide-campaign.md)
