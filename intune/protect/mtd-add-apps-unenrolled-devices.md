---
title: Adicione aplicativos de defesa de ameaças móveis a dispositivos não matriculados
titleSuffix: Microsoft Intune
description: Adicione aplicações de Defesa de Ameaças Móveis a dispositivos não matriculados pelos utilizadores do dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/24/2020
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
ms.openlocfilehash: a0d1574599b9e514d4bb0289b88ad3c55cc24d15
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782249"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Adicione aplicativos de defesa de ameaças móveis a dispositivos não matriculados

Por predefinição, ao utilizar as políticas de proteção de aplicações Intune com a Mobile Threat Defense, a Intune faz o trabalho de orientar o utilizador final no seu dispositivo para instalar e iniciar sessão em todas as aplicações necessárias para ativar as ligações com os serviços relevantes.

Os utilizadores finais precisam que o Autenticador da Microsoft (iOS) registe o seu dispositivo, e a Mobile Threat Defense (tanto Android como iOS) receba notificações quando uma ameaça é identificada nos seus dispositivos móveis, e para receber orientações para remediar as ameaças.

Opcionalmente, pode utilizar o Intune para adicionar e implementar as aplicações do Autenticador Microsoft e da Defesa de Ameaças Móveis (MTD).

> [!NOTE]
> Este artigo aplica-se a todos os parceiros de Defesa de Ameaças Móveis que apoiam políticas de proteção de aplicações:
>
> - Melhor Móvel (Android,iOS/iPadOS)
> - Zimperium (Android,iOS/iPadOS)
> - Procura de trabalho (Android,iOS/iPadOS)
>
> Para dispositivos não matriculados, não precisa de uma política de configuração de **aplicações iOS** que configura a Defesa de Ameaças Móveis para aplicação iOS que utiliza com o Intune. Esta é uma diferença fundamental em comparação com os dispositivos matriculados intune.

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Configure o Autenticador microsoft para iOS via Intune (opcional)

Ao utilizar as políticas de proteção de aplicações Intune com a Mobile Threat Defense, a Intune irá orientar o utilizador final para instalar, iniciar sessão e registar o seu dispositivo com o Autenticador Microsoft (iOS).

No entanto, caso deseje disponibilizar a aplicação aos utilizadores finais através do Portal da Empresa Intune, consulte as instruções para adicionar aplicações da [loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este [Microsoft Authenticator - iOS App Store URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) ao concluir a secção de informações da **aplicação Configure.** Não se esqueça de [atribuir app a grupos com Intune](../apps/apps-deploy.md) como o passo final.

> [!NOTE]
> Para os dispositivos iOS, precisa do [Microsoft Authenticator ](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) para que a identidade dos utilizadores seja verificada pelo Azure AD. O Intune Company Portal funciona como corretor em dispositivos Android para que os utilizadores possam ter as suas identidades verificadas pela Azure AD.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Disponibilizar aplicações de Defesa de Ameaças Móveis via Intune (opcional)

Ao utilizar as políticas de proteção de aplicações Intune com a Mobile Threat Defense, a Intune irá orientar o utilizador final a instalar e iniciar sessão na aplicação de clientes mobile threat defense necessária.

No entanto, caso deseje disponibilizar a app aos utilizadores finais através do Portal da Empresa Intune, pode seguir os passos abaixo no [portal Azure.](https://portal.azure.com/) Verifique se está familiarizado com o processo de:

- [Adicionar uma aplicação no Intune](../apps/apps-add.md).
- [Atribuir uma aplicação com o Intune](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Disponibilizar o Lookout for Work para os utilizadores finais

- **Android**  
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [Lookout for Work - Play Store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) ao concluir a secção de informações da **aplicação Configure.**

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este [Lookout for Work - iOS App Store URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) ao concluir a secção de informações da **aplicação Configure.**

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>Disponibilizar zimperium aos utilizadores finais

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) ao concluir a secção de informações da **aplicação Configure.**
- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este [Zimperium - App Store URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) ao concluir a secção de informações da **aplicação Configure.**

<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Disponibilizar melhor móvel aos utilizadores finais

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [Ative Shield - Play Store URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) ao concluir a secção de informações da **aplicação Configure.**

<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>Próximos passos

- [Ativar o conector de defesa de ameaças móveis em Intune para dispositivos não matriculados](~/protect/mtd-enable-unenrolled-devices.md)