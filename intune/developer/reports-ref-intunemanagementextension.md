---
title: Entidade IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria da Entidade IntuneManagementExtension das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70802626c79f11748e81c39afdd8bc8c5d0622b3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730152"
---
# <a name="reference-for-intune-management-extensions"></a>Referência para extensões de gerenciamento do Intune

A categoria **intuneManagementExtensions** contém entidades para dispositivos móveis que rastreiam informações como:

- Versões de uma IntuneManagementExtension
- Estado da instalação de uma IntuneManagementExtension

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

A entidade **intuneManagementExtensionVersion** lista todas as versões usadas pelo intuneManagementExtensions.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| ExtensionVersionKey |Identificador exclusivo da versão do intuneManagementExtensions. | 1 |
| ExtensionVersion |O número da versão de quatro dígitos. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

O **intuneManagementExtensionHealthState** lista todos os Estados de integridade possíveis do intuneManagementExtensions.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| ExtensionStateKey |Identificador exclusivo do estado de funcionamento. | 2 |
| Extensãostate |Estado de funcionamento de uma IntuneManagementExtension. | Bom estado de funcionamento |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

O **intuneManagementExtension** lista a integridade do IntuneManagementExtensions em cada dispositivo Windows 10 por dia.
Os dados são mantidos relativamente aos últimos 60 dias. 


|      Propriedade       |                         Descrição                         | Exemplo |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               Identificador exclusivo da Data.                |   123   |
|      TenantKey      |              Identificador exclusivo do Inquilino.               |   456   |
|      DeviceKey      |              Identificador exclusivo do Dispositivo.               |   789   |
| ExtensionVersionKey | Identificador exclusivo da versão do intuneManagementExtension. |    1    |
|  ExtensionStateKey  |             Identificador exclusivo do estado de funcionamento.              |    2    |

