---
title: Associação de Dispositivos do Utilizador – Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: A entidade UserDeviceAssociation contém associações de dispositivo de usuário em sua organização.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 423e401f5f03aa6ea359e421e28b4b2c4243b590
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505683"
---
# <a name="reference-for-user-device-association-entity"></a>Referência para a entidade Associação de Dispositivo do Utilizador

A entidade **userDeviceAssociation** contém associações de dispositivo de usuário em sua organização.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Nome        |                                           Description                                            |        Exemplo         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              Identificador exclusivo do utilizador no armazém de dados. (Chave de substituição).               |          123           |
|     deviceKey      |                      Identificador exclusivo do dispositivo no armazém de dados.                      |          123           |
| createdDateTimeUTC |           Data e hora em que a associação de dispositivos do utilizador foi criada. Utiliza o formato UTC.           | 11/23/2016 12:00:00 AM |
|     isDeleted      | Indica que o utilizador anulou a inscrição desse dispositivo e essa associação já não está atualizada. |       True/False       |
|  endedDateTimeUTC  |              Data e hora em UTC em que a propriedade IsDeleted foi alterada para <strong>True</strong>.               | 23/06/2017 12:00:00 |

## <a name="next-steps"></a>Próximos passos

- Saiba mais sobre o [data warehouse do Intune](../reports-nav-create-intune-reports.md).
