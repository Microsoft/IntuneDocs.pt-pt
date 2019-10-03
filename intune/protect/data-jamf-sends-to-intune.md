---
title: O data JAMF pro envia ao Intune
titleSuffix: Microsoft Intune
description: Examine a lista de dados que o JAMF pro envia para Microsoft Intune ao integrar o JAMF pro para gerenciar Macs com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 449e799dfc0531958c1578179cf07440d348ecf8
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71813940"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Dados que o Jamf Pro envia para o Intune

Quando você usa o [JAMF pro](https://www.jamf.com) para gerenciar seus Macs de usuários finais com o Intune, o JAMF pro captura informações de inventário sobre dispositivos MacOS gerenciados. 

## <a name="data"></a>Data  
Para obter a lista de dados que o JAMF pro compartilha com o Intune, consulte [Appendix: Informações de inventário compartilhadas com Microsoft Intune @ no__t-0 na documentação técnica do JAMF pro. 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>Passos seguintes
Obtenha informações sobre como [remover um dispositivo gerido por Jamf na documentação do Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Também pode enviar um pedido de suporte para o [suporte do Jamf](https://www.jamf.com/support/) para obter ajuda adicional. 

