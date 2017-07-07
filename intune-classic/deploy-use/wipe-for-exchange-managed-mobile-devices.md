---
title: "Eliminação de dispositivos móveis geridos pelo Exchange | Documentos da Microsoft"
description: "O Microsoft Intune permite-lhe apagar ou repor dispositivos móveis que são geridos através do Exchange ActiveSync (EAS) com o Intune Exchange Connector"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4b0914ab12456fd3ad5f957d68a59df9de539176
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---


# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Exchange-managed mobile devices

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune permite-lhe apagar ou repor dispositivos móveis que são geridos através do Exchange ActiveSync (EAS) com o Intune Exchange Connector. A tabela seguinte descreve as funcionalidades de eliminação disponibilizadas através do Exchange ActiveSync:

|Tipo de eliminação|Windows 8.1 e Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|Eliminação completa|Remove a conta de correio e o correio em cache.|Reposição de fábrica.|Reposição de fábrica.|
|Eliminação seletiva/e-mail|Remove a conta de e-mail.|Não suportada.|Não suportada.|
|Eliminação seletiva/políticas|A imposição de política foi eliminada, mas as definições não foram alteradas|A imposição de política foi removida, mas as definições não foram alteradas.|A imposição de política foi eliminada, mas as definições não foram alteradas.|
