---
title: Adicionar aplicativos de defesa contra ameaças móveis a dispositivos não registrados
titleSuffix: Microsoft Intune
description: Adicione aplicativos de defesa contra ameaças móveis a dispositivos não registrados por usuários do dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
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
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72795323"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Adicionar aplicativos de defesa contra ameaças móveis a dispositivos não registrados

Por padrão, ao usar políticas de proteção de aplicativo do Intune com defesa contra ameaças móveis, o Intune faz o trabalho de orientar o usuário final em seu dispositivo para instalar e entrar em todos os aplicativos necessários para habilitar as conexões com os serviços relevantes.

Os usuários finais precisam do Microsoft Authenticator (iOS) para registrar seu dispositivo e a defesa contra ameaças móveis (Android e iOS) para receber notificações quando uma ameaça é identificada em seus dispositivos móveis e para receber orientação para corrigir as ameaças.

Opcionalmente, você pode usar o Intune para adicionar e implantar os aplicativos de Microsoft Authenticator e de defesa contra ameaças móveis (MTD) também.

> [!NOTE] 
> Este artigo se aplica a todos os parceiros de defesa contra ameaças móveis que dão suporte a políticas de proteção de aplicativo: melhores dispositivos móveis (Android), Zimperium (iOS), Lookout for Work (Android/iOS).
> 
> Para dispositivos não registrados, você **não precisa de uma política de configuração de aplicativo IOS** que configure o aplicativo de defesa contra ameaças móveis para IOS que você usa com o Intune. Essa é uma diferença importante em comparação com os dispositivos registrados no Intune. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Configurar Microsoft Authenticator para iOS via Intune (opcional)
Ao usar políticas de proteção de aplicativo do Intune com defesa contra ameaças móveis, o Intune orientará o usuário final a instalar, entrar e registrar seu dispositivo com o Microsoft Authenticator (iOS).

No entanto, se desejar disponibilizar o aplicativo para os usuários finais por meio do Portal da Empresa do Intune, consulte as instruções para [adicionar aplicativos da loja do Ios ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos Microsoft Authenticator-Ios](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) ao concluir a seção **configurar informações do aplicativo** . Não se esqueça de [atribuir o aplicativo a grupos com o Intune](../apps/apps-deploy.md) como a etapa final.

> [!NOTE] 
> Para os dispositivos iOS, precisa do [Microsoft Authenticator ](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) para que a identidade dos utilizadores seja verificada pelo Azure AD. O Portal da Empresa do Intune funciona como o agente em dispositivos Android para que os usuários possam ter suas identidades verificadas pelo Azure AD.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Disponibilizando aplicativos de defesa contra ameaças móveis por meio do Intune (opcional)
Ao usar políticas de proteção de aplicativo do Intune com defesa contra ameaças móveis, o Intune orientará o usuário final a instalar e entrar no aplicativo cliente de defesa contra ameaças móveis necessário. 

No entanto, se desejar disponibilizar o aplicativo para os usuários finais por meio do Portal da Empresa do Intune, você poderá seguir as etapas abaixo na [portal do Azure](https://portal.azure.com/). Verifique se está familiarizado com o processo de:

- [Adicionar uma aplicação no Intune](../apps/apps-add.md).
- [Atribuir uma aplicação com o Intune](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Disponibilizando Lookout for Work para os usuários finais
- **Android**  
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Use essa [URL de Lookout for Work Play Store](https://play.google.com/store/apps/details?id=com.lookout.enterprise) ao concluir a seção **configurar informações do aplicativo** .

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos Lookout for Work-Ios](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) ao concluir a seção **configurar informações do aplicativo** .

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

### <a name="making-zimperium-available-to-end-users"></a>Disponibilizando o Zimperium para os usuários finais
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL de loja do Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) ao concluir a seção **configurar informações do aplicativo** .
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Tornando o melhor móvel disponível para os usuários finais 
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Use esta [URL de Play Store de blindagem ativa](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) ao concluir a seção **configurar informações do aplicativo** .
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

- [Habilitar o conector de defesa contra ameaças móveis no Intune para dispositivos não registrados](~/protect/mtd-enable-unenrolled-devices.md)

