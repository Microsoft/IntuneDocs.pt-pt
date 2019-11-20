---
title: Create Mobile Threat Defense (MTD) app protection policy with Intune
titleSuffix: Microsoft Intune
description: Create Mobile Threat Defense (MTD) app protection policy with Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48dc7de86965741d8ed42bd5a5f29f72ae66d4f3
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188504"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Create Mobile Threat Defense app protection policy with Intune

Intune with Mobile Threat Defense (MTD) helps you detect threats and assess risk on mobile devices. You can create an Intune app protection policy that assesses risk to determine if the device is allowed to access corporate data or not.


> [!NOTE]
> This article applies to all Mobile Threat Defense partners that support app protection policies:
>
> - Better Mobile (Android)
> - Zimperium (iOS)
> - Lookout for Work (Android, iOS).

## <a name="before-you-begin"></a>Antes de começar

Como parte da configuração da MTD, na consola do parceiro MTD, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. You now need to set the Mobile Threat Defense level in the Intune app protection policy.

Prerequisites for app protection policy with MTD:

- Set up MTD integration with Intune. Without this integration, the MTD app protection policy will have no effect.

## <a name="to-create-an-mtd-app-protection-policy"></a>To create an MTD app protection policy

Use the procedure to [create an Application protection policy for either iOS/iPadOS or Android](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps), and use the following information on the *Apps*, *Conditional launch*, and *Assignments* pages:

- **Apps**: Select the app for the Mobile Threat Defense partner you use.
- **Conditional launch**:  Below *Device conditions*, use the drop-down box to select **Max allowed device threat level**.

  Options for the threat level **Value**:

  - **Seguro**: este é o nível mais seguro. The device can't have any threats present and still access company resources. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.
  - **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
  - **Elevado**: este é o nível menos seguro. This allows all threat levels and uses Mobile Threat Defense for reporting purposes only. É necessário que os dispositivos tenham a aplicação de MTD ativada com esta definição.

  Options for **Action**:

  - **Block access**
  - **Wipe data**

- **Assignments**: Assign the policy to groups of users.  The devices used by the group’s members are evaluated for access to corporate data on targeted apps via Intune app protection.


## <a name="next-steps"></a>Próximos passos  

- Learn more about [Mobile Threat Defense](~/protect/mobile-threat-defense.md) in Microsoft Intune.
