---
title: Entidade IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria da Entidade IntuneManagementExtension das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae99e747f9c0540418c15f24fbe0c27c585f869c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490298"
---
# <a name="reference-for-intune-management-extensions"></a>Referência para extensões de gerenciamento do Intune

A categoria **intuneManagementExtensions** contém entidades para dispositivos móveis que rastreiam informações como:

- Versões de uma IntuneManagementExtension
- Estado da instalação de uma IntuneManagementExtension

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

A entidade **intuneManagementExtensionVersion** lista todas as versões usadas pelo intuneManagementExtensions.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| extensionVersionKey |Identificador exclusivo da versão do intuneManagementExtensions. | 1 |
| extensionVersion |O número da versão de quatro dígitos. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

O **intuneManagementExtensionHealthState** lista todos os Estados de integridade possíveis do intuneManagementExtensions.

| Propriedade  | Description | Exemplo |
|---------|------------|--------|
| extensionStateKey |Identificador exclusivo do estado de funcionamento. | 2 |
| extensãostate |Estado de funcionamento de uma IntuneManagementExtension. | Íntegro |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

O **intuneManagementExtension** lista a integridade do IntuneManagementExtensions em cada dispositivo Windows 10 por dia.
Os dados são mantidos relativamente aos últimos 60 dias. 


|      Propriedade       |                         Description                         | Exemplo |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               Identificador exclusivo da Data.                |   123   |
|      tenantKey      |              Identificador exclusivo do Inquilino.               |   456   |
|      deviceKey      |              Identificador exclusivo do Dispositivo.               |   789   |
| extensionVersionKey | Identificador exclusivo da versão do intuneManagementExtension. |    1    |
|  extensionStateKey  |             Identificador exclusivo do estado de funcionamento.              |    2    |
