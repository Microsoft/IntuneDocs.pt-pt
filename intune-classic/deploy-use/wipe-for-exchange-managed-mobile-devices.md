---
title: "Eliminação de dispositivos móveis geridos pelo Exchange"
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
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 31c5707424e582c9e86d8a271e4c03d5668c315c
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Exchange-managed mobile devices

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Microsoft Intune permite-lhe apagar ou repor dispositivos móveis que são geridos através do Exchange ActiveSync (EAS) com o Intune Exchange Connector. A tabela seguinte descreve as funcionalidades de eliminação disponibilizadas através do Exchange ActiveSync:

|Tipo de eliminação|Windows 8.1 e Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|Eliminação completa|Remove a conta de correio e o correio em cache.|Reposição de fábrica.|Reposição de fábrica.|
|Eliminação seletiva/e-mail|Remove a conta de e-mail.|Não suportada.|Não suportada.|
|Eliminação seletiva/políticas|A imposição de política foi eliminada, mas as definições não foram alteradas|A imposição de política foi removida, mas as definições não foram alteradas.|A imposição de política foi eliminada, mas as definições não foram alteradas.|
