---
title: Entidade IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Tópico de referência para a categoria da Entidade IntuneManagementExtension das coleções de entidades na API do Armazém de Dados do Intune.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea55c92fb3254b6e610bec1074e35d9d9c32cd18
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798005"
---
# <a name="reference-for-intune-management-extension"></a>Referência para a Extensão de Gestão do Intune

A categoria **IntuneManagementExtension** contém entidades para dispositivos móveis que controlam informações como:

  -  Versões de uma IntuneManagementExtension
  -  Estado da instalação de uma IntuneManagementExtension

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

A entidade **IntuneManagementExtensionVersion** apresenta todas as versões utilizadas pela IntuneManagementExtension.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| ExtensionVersionKey |Identificador exclusivo da versão da IntuneManagementExtension. | 1 |
| ExtensionVersion |O número da versão de quatro dígitos. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

O **IntuneManagementExtensionHealthState** apresenta todos os estados de funcionamento possíveis da IntuneManagementExtension.

| Propriedade  | Descrição | Exemplo |
|---------|------------|--------|
| ExtensionStateKey |Identificador exclusivo do estado de funcionamento. | 2 |
| ExtensionState |Estado de funcionamento de uma IntuneManagementExtension. | Bom estado de funcionamento |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

A **IntuneManagementExtension** apresenta o estado de funcionamento da IntuneManagementExtension em cada dispositivo Windows 10 por dia.
Os dados são mantidos relativamente aos últimos 60 dias. 


|      Propriedade       |                         Descrição                         | Exemplo |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Identificador exclusivo da Data.                |   123   |
|      TenantKey      |              Identificador exclusivo do Inquilino.               |   456   |
|      DeviceKey      |              Identificador exclusivo do Dispositivo.               |   789   |
| ExtensionVersionKey | Identificador exclusivo da versão da IntuneManagementExtension. |    1    |
|  ExtensionStateKey  |             Identificador exclusivo do estado de funcionamento.              |    2    |

