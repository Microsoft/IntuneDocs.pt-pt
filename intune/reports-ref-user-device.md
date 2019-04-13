---
title: Associação de Dispositivos do Utilizador – Armazém de Dados do Intune
titleSuffix: Microsoft Intune
description: A entidade de UserDeviceAssociation contém associações de dispositivo do utilizador na sua organização.
keywords: Armazém de Dados do Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ae5ee7a33ca069853201c553e461d9e36c9bbdb
ms.sourcegitcommit: af2512a1342d8037a96a61c8cc2c63e107913733
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59533517"
---
# <a name="reference-for-user-device-association-entity"></a>Referência para a entidade Associação de Dispositivo do Utilizador

A entidade **UserDeviceAssociation** contém associações de dispositivos do utilizador na sua organização.

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        Name        |                                           Descrição                                            |        Exemplo         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Identificador exclusivo do utilizador no armazém de dados. (Chave de substituição).               |          123           |
|     DeviceKey      |                      Identificador exclusivo do dispositivo no armazém de dados.                      |          123           |
| CreatedDateTimeUTC |           Data e hora em que a associação de dispositivos do utilizador foi criada. Utiliza o formato UTC.           | 11/23/2016 12:00:00 AM |
|     IsDeleted      | Indica que o utilizador anulou a inscrição desse dispositivo e essa associação já não está atualizada. |       Verdadeiro/Falso       |
|  EndedDateTimeUTC  |              Data e hora em UTC em que a propriedade IsDeleted foi alterada para <strong>True</strong>.               | 23/06/2017 12:00:00 |

## <a name="next-steps"></a>Passos Seguintes

- Saiba mais sobre o [armazém de dados do Intune](reports-nav-create-intune-reports.md).
