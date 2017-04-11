---
title: "Considerações especiais sobre a migração | Documentos da Microsoft"
description: "O objetivo deste artigo é proporcionar considerações especiais sobre a migração ao cliente antes de este começar uma campanha de migração."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 634e84312fa1a93eb85bf70e1593ca11359b72ff
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-special-migration-considerations"></a>Fase 1: Considerações especiais sobre a migração

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Existem considerações especiais sobre a migração que poderão ser aplicáveis, dependendo do ambiente do fornecedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Reposição de fábrica do Programa de Inscrição de Dispositivos (DEP) da Apple

O Programa de Inscrição de Dispositivos (DEP) da Apple define configurações do dispositivo que não podem ser removidas pelo utilizador final. Para manter as funcionalidades da gestão avançada do DEP, o dispositivo tem de voltar ao estado inicial (novo) através da reposição de fábrica para a inscrição no Intune.

Para continuar a utilizar o DEP para gerir os dispositivos no Intune:

1.  Integre o [DEP no Intune](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune).

2.  Aceda à sua conta de DEP da Apple e [atribua novamente os números de série dos dispositivos DEP](https://help.apple.com/deployment/business/#/tesf9562af26) do fornecedor de MDM existente para o Intune.

3.  [Sincronize](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) a sua conta DEP com o Intune.

4.  [Crie e atribua](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) perfis de inscrição de DEP adequados aos números de série no Intune.

5.  Realize a reposição de fábrica nos dispositivos (quer remotamente através do seu fornecedor de MDM atual ou manualmente em cada dispositivo).

6.  Distribua os dispositivos pelos utilizadores finais.

## <a name="next-steps"></a>Próximos passos 

[Fase 2: Campanha de migração](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

