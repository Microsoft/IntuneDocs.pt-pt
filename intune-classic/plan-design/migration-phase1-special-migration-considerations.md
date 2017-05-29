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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7e0adb862d8c60805b3b34406e193df5a93be381
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-special-migration-considerations"></a>Fase 1: Considerações especiais sobre a migração

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Existem considerações especiais sobre a migração que poderão ser aplicáveis, dependendo do ambiente do fornecedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Reposição de fábrica do Programa de Inscrição de Dispositivos (DEP) da Apple

O Programa de Inscrição de Dispositivos (DEP) da Apple define configurações do dispositivo que não podem ser removidas pelo utilizador final. Para manter as funcionalidades da gestão avançada do DEP, o dispositivo tem de voltar ao estado inicial (novo) através da reposição de fábrica para a inscrição no Intune.

Para continuar a utilizar o DEP para gerir os dispositivos no Intune:

1.  Integre o [DEP no Intune](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune).

2.  Aceda à sua conta de DEP da Apple e [atribua novamente os números de série dos dispositivos DEP](https://help.apple.com/deployment/business/#/tesf9562af26) do fornecedor de MDM existente para o Intune.

3.  [Sincronize](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) a sua conta DEP com o Intune.

4.  [Crie e atribua](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) perfis de inscrição de DEP adequados aos números de série no Intune.

5.  Realize a reposição de fábrica nos dispositivos (quer remotamente através do seu fornecedor de MDM atual ou manualmente em cada dispositivo).

6.  Distribua os dispositivos pelos utilizadores finais.

## <a name="next-steps"></a>Próximos passos 

[Fase 2: Campanha de migração](/intune-classic/plan-design/migration-phase2-migration-campaign)

