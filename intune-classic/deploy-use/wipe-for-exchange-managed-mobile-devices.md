---
title: Eliminação de dispositivos móveis geridos pelo Exchange
description: O Microsoft Intune permite-lhe apagar ou repor dispositivos móveis que são geridos através do Exchange ActiveSync (EAS) com o Intune Exchange Connector
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Exchange-managed mobile devices

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

O Microsoft Intune permite-lhe apagar ou repor dispositivos móveis que são geridos através do Exchange ActiveSync (EAS) com o Intune Exchange Connector. A tabela seguinte descreve as funcionalidades de eliminação disponibilizadas através do Exchange ActiveSync:


|      Tipo de eliminação       |              Windows 8.1 e Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        Eliminação completa        |          Remove a conta de correio e o correio em cache.           |                      Reposição de fábrica.                       |                      Reposição de fábrica.                       |
|  Eliminação seletiva/e-mail   |                  Remove a conta de e-mail.                  |                       Não suportada.                       |                      Não suportada.                       |
| Eliminação seletiva/políticas | A imposição de política foi eliminada, mas as definições não foram alteradas | A imposição de política foi removida, mas as definições não foram alteradas. | A imposição de política foi eliminada, mas as definições não foram alteradas. |

