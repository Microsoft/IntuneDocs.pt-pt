---
title: Definições dos dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Add, configure, or create settings on iOS devices to restrict features, including setting password requirements, control the locked screen, use built-in apps, add restricted or approved apps, handle bluetooth devices, connect to the cloud for backup and storage, enable kiosk mode, add domains, and control how users interact with the Safari web browser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6fde277e16043662420864adcc0458e3dccad308
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465649"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>iOS and iPadOS device settings to allow or restrict features using Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

This article lists and describes the different settings you can control on iOS and iPadOS devices. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos iOS.

> [!TIP]
> These settings use Apple's MDM settings. For more information on these settings, see [Apple's mobile device management settings](https://support.apple.com/guide/mdm/welcome/web) (opens Apple's web site).

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> These settings apply to different enrollment types, with some settings applying to all enrollment options. For more information on the different enrollment types, see [iOS enrollment](../ios-enroll.md).

## <a name="general"></a>Geral

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Share usage data**: Choose **Block** to prevent the device from sending diagnostic and usage data to Apple. **Não configurado** (predefinição) permite que estes dados sejam enviados.

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device. In iOS 9.0 and newer, it also blocks screen recordings. **Não configurado** (predefinição) permite ao utilizador capturar o conteúdo do ecrã como uma imagem ou um vídeo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Untrusted TLS certificates**: Choose **Block** to prevent untrusted Transport Layer Security (TLS) certificates on the device. **Não configurado** (predefinição) permite os certificados TLS.
- **Allow over-the-air PKI updates**: **Allow** lets your users  receive software updates without connecting their devices to a computer.
- **Limit ad tracking**: Choose **Limit** to disable the device advertising identifier. **Não configurado** (predefinição) mantém-no ativado.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Diagnostics submission settings modification**: **Block** prevents the user from changing the diagnostic submission and app analytics settings in **Diagnostics and Usage** (device Settings). **Não configurado** (predefinição) permite ao utilizador alterar estas definições do dispositivo.

  To use this setting, set the **Share usage data** setting to **Block**.

  Esta funcionalidade aplica-se a:  
  - iOS 9.3.2 and newer

- **Remote screen observation by Classroom app**: Choose **Block** to prevent the Classroom app from remotely viewing the screen on the device. **Não configurado** (predefinição) permite que a aplicação Classroom da Apple veja o ecrã.

  To use this setting, set the **Screen capture** setting to **Block**.

  Esta funcionalidade aplica-se a:  
  - iOS 9.3 and newer

- **Unprompted screen observation by Classroom app**: If set to **Allow**, teachers can silently observe the screen of students iOS devices using the Classroom app without the students' knowledge. Os dispositivos de estudantes inscritos numa turma através da aplicação Classroom concedem automaticamente permissão ao professor do curso. **Não configurado** (predefinição) impede esta funcionalidade.

  To use this setting, set the **Screen capture** setting to **Block**.

- **Enterprise app trust**: Choose **Block** to remove the **Trust Enterprise Developer** button in Settings > General > Profiles & Device Management on the device. **Não configurado** (predefinição) permite que o utilizador opte por confiar nas aplicações que não são transferidas da App Store.
- **Account modification**: When set to **Block**, the user can't update the device-specific settings from the iOS settings app. Por exemplo, o utilizador não pode criar contas novas no dispositivo nem alterar o nome de utilizador ou a palavra-passe. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade também se aplica às definições acessíveis na aplicação de definições do iOS, tais como o Correio, Contactos, Calendário, Twitter e outros. A funcionalidade não se aplica a aplicações com definições da conta que não sejam configuráveis na aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.

- **Screen time**: Choose **Block** to prevent users from setting their own restrictions in Screen Time (device settings). **Não configurado** permite que o utilizador configure as restrições do dispositivo (por exemplo, as restrições de acesso ou as restrições de conteúdo e de privacidade) no dispositivo.

  O nome desta definição foi mudado em **Ativar restrições nas definições do dispositivo**. Impacto desta alteração:  
  
  - iOS 11.4.1 and earlier: **Block** prevents end users from setting their own restrictions in the device settings. The behavior is the same; and there are no changes for end users.
  - iOS 12.0 and newer: **Block** prevents end users from setting their own **Screen Time** in the device settings (Settings > General > Screen Time), including content and privacy restrictions. Os dispositivos atualizados para o iOS 12.0 deixam apresentar o separador de restrições nas definições do dispositivo (Definições > Geral > Gestão de Dispositivos > Perfil de Gestão > Restrições). Estas definições estão em **Tempo do Ecrã**.
  
- **Use of the erase all content and settings option on the device**: Choose **Block** so users can't use the erase all content and settings option on the device. **Não configurado** (predefinição) concede aos utilizadores acesso a estas definições.
- **Device name modification**: Choose **Block** so the device name can't be changed. **Não configurado** (predefinição) permite ao utilizador alterar o nome do dispositivo.
- **Notification settings modification**: Choose **Block** so the notification settings can't be changed. **Não configurado** (predefinição) permite ao utilizador alterar as definições de notificação do dispositivo.
- **Wallpaper modification**: **Block** prevents the wallpaper from being changed. **Não configurado** (predefinição) permite ao utilizador alterar a imagem de fundo no dispositivo.
- **Enterprise app trust settings modification**: **Block** prevents the user from changing the enterprise app trust settings on supervised devices. **Não configurado** (predefinição) permite que o utilizador confie nas aplicações que não são transferidas da App Store.
- **Configuration profile changes**: **Block** prevents configuration profile changes on the device. **Não configurado** (predefinição) permite que o utilizador instale perfis de configuração.
- **Activation Lock**: Choose **Allow** to enable Activation Lock on supervised iOS devices. O Bloqueio de Ativação dificulta que um dispositivo perdido ou roubado seja reativado.
- **Block app removal**: Choose **Block** to prevent users from removing apps. **Não configurado** (predefinição) permite que os utilizadores removam aplicações do dispositivo.
- **Blocks USB Restricted mode**: Choose **Block** to disable USB Restricted mode on supervised devices. USB Restricted mode prevents USB accessories from exchanging data with a device that's locked for over an hour. **Não configurado** (predefinição) permite o modo USB Restrito.
- **Force automatic date and time**: **Require** forces supervised devices to set the Date & Time automatically. O fuso horário do dispositivo é atualizado quando o dispositivo está ligado à rede móvel ou ao Wi-Fi com os serviços de localização ativados.
- **Require students to request permission to leave Classroom course**: **Require** forces students enrolled in an unmanaged course using the Classroom app to request permission from the teacher to leave the course. **Não configurado** (predefinição) não força o estudante a pedir permissão.

  Esta funcionalidade aplica-se a:  
  - iOS 11.3 and newer

- **Allow Classroom to lock to an app and lock the device without prompting**: **Enable** allows teacher to lock apps or lock the device using the Classroom app without prompting the student. Bloquear aplicações significa que o dispositivo pode apenas aceder às aplicações especificadas pelo professor. **Não configurado** (predefinição) impede que os professores bloqueiem aplicações ou dispositivos através da aplicação Classroom sem avisar o estudante.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 and newer

- **Automatically join Classroom classes without prompting**: **Enable** automatically allows students to join a class that is in the Classroom app without prompting the teacher. **Não configurado** (predefinição) aviso o professor que os estudantes querem aderir a uma turma da aplicação Classroom.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 and newer

- **Block VPN creation**: **Block** prevents users from creating VPN configuration settings. **Não configurado** (predefinição) deixa que os utilizadores criem VPNs no dispositivo.
- **Modifying eSIM settings**: **Block** prevents users from removing or adding a cellular plan to the eSIM on the device. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade aplica-se a:  
  - iOS 12.1 and newer

- **Defer software updates**: When set to **Not configured** (default), software updates are shown on the device as Apple releases them. Por exemplo, se uma atualização do iOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Delay visibility of software updates**: Enter a value from 0-90 days. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se iOS 12.a estiver disponível a **1 de janeiro** e a opção **Adiar visibilidade** estiver definida como **5 dias**, a iOS 12.a não será mostrado como uma atualização disponível nos dispositivos do utilizador final. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta definição aplica-se a:  
    - iOS 11.3 and newer

## <a name="password"></a>Palavra-passe

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Password**: **Require** the end user to enter a password to access the device. **Not configured** (default) allows users to access the device without entering a password.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

> [!IMPORTANT]
> On user-enrolled devices, if you configure any password setting, then the **Simple passwords** settings is automatically set to **Block**, and a 6 digit PIN is enforced.
>
> For example, you configure the **Password expiration** setting, and push this policy to user-enrolled devices. On the devices, the following happens:
>
> - The **Password expiration** setting is ignored.
> - Simple passwords, such as `1111` or `1234`, aren't allowed.
> - A 6 digit pin is enforced.

- **Simple passwords**: Choose **Block** to require more complex passwords. **Não configurado** permite palavras-passe simples, tais como `0000` e `1234`.

- **Required password type**: Choose the type of password your organization require. As opções são:
  - **Predefinição do dispositivo**
  - **Numérico**
  - **Alfanumérico**
- **Number of non-alphanumeric characters in password**: Enter the number of symbol characters, such as `#` or `@`, that must be included in the password.

- **Minimum password length**: Enter the minimum length a user must enter, between 4 and 14 characters. On user enrolled devices, enter a length between 4 and 6 characters.
  
  > [!NOTE]
  > For devices that are user enrolled, users can set a PIN greater than 6 digits. But, no more than 6 digits are enforced on the device. For example, an administrator sets the minimum length to `8`. On user-enrolled devices, users are only required to set a 6 digit PIN. Intune doesn't force a PIN greater than 6 digits on user-enrolled devices.

- **Number of sign-in failures before wiping device**: Enter the number of failed sign-ins to allow before the device is wiped (between 4-11).
  
  iOS has built-in security that can impact this setting. For example, iOS may delay triggering the policy depending on the number of sign in failures. It may also consider repeatedly entering the same passcode as one attempt. Apple's [iOS security guide](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (opens Apple's web site) is a good resource, and provides more specific details on passcodes.
  
- **Maximum minutes after screen lock before password is required**<sup>1</sup>: Enter how long the device stays idle before the user must reenter their password. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido. Suportado no iOS 8.0 e em dispositivos mais recentes.

- **Maximum minutes of inactivity until screen locks**<sup>1</sup>: Enter the maximum number of minutes of inactivity allowed on the device until the screen locks.

  **iOS options**:  

  - **Not configured** (Default): Intune doesn't touch this setting.
  - **Immediately**: Screen locks after 30 seconds of inactivity.
  - **1**: Screen locks after 1 minute of inactivity.
  - **2**: Screen locks after 2 minutes of inactivity.
  - **3**: Screen locks after 3 minutes of inactivity.
  - **4**: Screen locks after 4 minutes of inactivity.
  - **5**: Screen locks after 5 minutes of inactivity.
    
  **iPadOS options**:  

  - **Not configured** (Default): Intune doesn't touch this setting.
  - **Immediately**: Screen locks after 2 minutes of inactivity.
  - **2**: Screen locks after 2 minutes of inactivity.
  - **5**: Screen locks after 5 minutes of inactivity.
  - **10**: Screen locks after 10 minutes of inactivity.
  - **15**: Screen locks after 15 minutes of inactivity.

  If a value doesn't apply to iOS or iPadOS, then Apple uses the closest *lowest* value. For example, if you enter `4` minutes, then iPadOS devices use `2` minutes. If you enter `10` minutes, then iOS devices use `5` minutes. This is an Apple limitation.
  
  > [!NOTE]
  > The Intune UI for this setting doesn't separate the iOS and iPadOS supported values. The UI might be updated in a future release.

- **Password expiration (days)** : Enter the number of days before the device password must be changed.
- **Prevent reuse of previous passwords**: Enter the number of new passwords that must be used until an old one can be reused.
- **Touch ID and Face ID unlock**: Choose **Block** to prevent using a fingerprint or face to unlock the device. **Not configured** allows the user to unlock the device using these methods.

  Blocking this setting also prevents using FaceID authentication to unlock the device.

  Face ID applies to:  
  - iOS 11.0 and newer

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Passcode modification**: Choose **Block** to stop the passcode from being changed, added, or removed. As alterações às restrições do código de acesso são ignoradas nos dispositivos supervisionados após o bloqueio desta funcionalidade. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.

  - **Touch ID and Face ID modification**: **Block** stops the user from changing, adding, or removing TouchID fingerprints and Face ID. **Not configured** (default) allows the user to update the TouchID fingerprints and Face ID on the device.

    Blocking this setting also stops the user from changing, adding, or removing FaceID authentication.

    Face ID applies to:  
    - iOS 11.0 and newer

- **Block password AutoFill**: Choose **Block** to prevent using the AutoFill Passwords feature on iOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Block password proximity requests**: Choose **Block** so a user’s device doesn't request passwords from nearby devices. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.
- **Block password sharing**: **Block** prevents sharing passwords between devices using AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.
- **Require Touch ID or Face ID authentication for password or credit card information AutoFill**: When set to **Require**, users must authenticate using TouchID or FaceID before passwords or credit card information can be auto filled in Safari and other apps. **Não configurado** (predefinição) permite que os utilizadores controlem esta funcionalidade nas definições do dispositivo.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 and newer
  
<sup>1</sup>Quando configura as definições **Máximo de minutos de inatividade até o ecrã ser bloqueado** e **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor de ambas as definições para **5** minutos, o ecrã desativa automaticamente passados cinco minutos e o dispositivo bloqueia após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, após o utilizador desativar o ecrã, o dispositivo será bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Control Center access while device locked**: Choose **Block** to prevent access to the Control Center app while device is locked. **Not configured** (default) allows users access to the Control Center app when the device is locked.
- **Notifications while device locked**: **Block** prevents access to notifications when the device is locked. **Not configured** (default) allows the user to access the notifications without unlocking the device.
- **Today view while device locked**: **Block** prevents access to the Today view when the device is locked. **Not configured** (default) allows the user to see the Today view when the device is locked.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Wallet notifications while device locked**: **Block** prevents access to the Wallet app when the device is locked. **Not configured** (default) allows the user to access the Wallet app while the device is locked.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Viewing corporate documents in unmanaged apps**: **Block** prevents viewing corporate documents in unmanaged apps. **Not configured** (default) allows corporate documents to be viewed in any app. Por exemplo, quer impedir que os utilizadores guardem os ficheiros da aplicação OneDrive na Dropbox. Configure esta definição como **Bloquear**. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não é permitido guardar.


  > [!NOTE]
  > When this setting is blocked, third party keyboards installed from the App Store are also blocked.

  - **Allow unmanaged apps to read from managed contacts accounts**: When set to **Allow**, unmanaged apps, such as the built-in iOS Contacts app, can read and access contact information from managed apps, including the Outlook mobile app. **Not configured** (default) prevents reading, including removing duplicates, from the built-in Contacts app on the device.  
  
    This setting allows or prevents reading contact information. It doesn't control syncing contacts between the apps.
  
    Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

  For more information about these two settings, and their impact on Outlook for iOS contact export synchronization, see [Support Tip: Use Intune custom profile settings with the iOS Native Contacts App](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Treat AirDrop as an unmanaged destination**: **Require** forces AirDrop to be considered an unmanaged drop target. Impede que as aplicações geridas enviem dados através do Airdrop. 
- **Viewing non-corporate documents in corporate apps**: **Block** prevents viewing non-corporate documents in corporate apps. **Not configured** (default) allows any document to be viewed in corporate managed apps.

  Setting to **Block** also prevents contact export synchronization in Outlook for iOS. For more information, see [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Require iTunes Store password for all purchases**: **Require** the user to enter the Apple ID password for each in-app or ITunes purchase. **Not configured** (default) allows purchases without prompting for a password every time.
- **In-app purchases**: Choose **Block** to prevent in-app purchases from the store. **Not configured** (default) allows store purchases within a running app.
- **Download content from iBook store flagged as 'Erotica'** : Choose **Block** to prevent stops users from downloading media from the iBook store that's tagged as erotica. **Not configured** (default) allows the user to download books with the "Erotica" category.
- **Allow managed apps to write contacts to unmanaged contacts accounts**: When set to **Allow**, managed apps, such as the Outlook mobile app, can save or sync contact information, including business and corporate contacts, to the built-in iOS Contacts app. When set to **Not configured** (default), managed apps can't save or sync contact information to the built-in iOS Contacts app on the device.
  
  Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

- **Ratings region**: Choose the ratings region you want to use for allowed downloads. And then choose the allowed ratings for **Movies**, **TV Shows**, and **Apps**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **App store**: **Block** prevents access to the app store on supervised devices. **Not configured** (default) allows access.

  Starting with iOS 13.0, this setting requires supervised devices.

  - **Installing apps from App Store**: Choose **Block** to block the app store from the device home screen. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Not configured** (default) allows the app store on the home screen.
  - **Automatic app downloads**: Choose **Block** to prevent automatic downloading of apps bought on other devices. Não afeta a atualização das aplicações existentes. **Not configured** (default) allows apps bought on other iOS devices to download on the device.

- **Explicit iTunes music, podcast, or news content**: Choose **Block** to prevent explicit iTunes music, podcast, or news content. **Not configured** (default) allows the device to access content rated as adult from the store. iOS 13 and newer may require supervised only devices. 

  Starting with iOS 13.0, this setting requires supervised devices.

- **Adding Game Center friends**: **Block** prevents users from adding Game Center friends. **Not configured** (default) allows the user to add friends in Game Center.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Game Center**: **Block** the use of the Game Center app. **Not configured** (default) allows using the Game Center app on the device.
- **Multiplayer gaming**: Choose **Block** to prevent multiplayer gaming. **Not configured** (default) allows the user to play multiplayer games on the device.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Access to network drive in Files app**: Using the Server Message Block (SMB) protocol, devices can access files or other resources on a network server. **Disable** prevents accessing files on a network SMB drive. **Not configured** (default) allows access.

  Esta funcionalidade aplica-se a:  
  - iOS and iPadOS 13.0 and newer

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Siri**: **Block** prevents access to Siri. **Not configured** (default) allows using the Siri voice assistant on the device.
  - **Siri while device is locked**: Choose **Block** to prevent access to Siri when the device is locked. **Not configured** (default) allows using the Siri voice assistant on the device when it's locked.

- **Safari fraud warnings**: **Require** fraud warnings to be shown in the web browser on the device. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Spotlight search to return results from internet**: **Block** stops Spotlight from returning any results from an Internet search. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Safari cookies**: Choose how cookies are handled on the device. As opções são:
  - Allow
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual

- **Safari JavaScript**: **Block** prevents Java scripts in the browser from running on the device. **Not configured** (default) allows Java scripts.

- **Safari Pop-ups**: **Block** to disable the pop-up blocker in the web browser. **Not configured** (default) allows the pop-up blocker.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Camera**: Choose **Block** to prevent access to the camera on the device. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.

  Starting with iOS 13.0, this setting requires supervised devices.

  - **FaceTime**: **Block** to prevent access to the FaceTime app. **Not configured** (default) allows access to the FaceTime app on the device.

    Starting with iOS 13.0, this setting requires supervised devices.

- **Siri profanity filter**: **Require** prevents Siri from dictating, or speaking profane language.

  To use this setting, set the **Siri** setting to **Block**.

- **Siri to query user-generated content from the internet**: **Block** prevents Siri from accessing websites to answer questions. **Not configured** (default) allows Siri to access user-generated content from the internet.

  To use this setting, set the **Siri** setting to **Block**.

- **Apple News**: Choose **Block** to prevent access to the Apple News app on the device. **Not configured** (default) allows using the Apple News app.
- **iBooks store**: **Block** prevents access to the iBooks store. **Not configured** (default) allows users to browse and buy books from the iBooks store.
- **Messages app on the device**: **Block** prevents users from using the Messages app for iMessage. If the device supports text messaging, the user can still send and receive text messages using SMS. **Not configured** (default) allows using the Messages app to send and read messages over the internet.
- **Podcasts**: **Block** prevents users using the Podcasts app. **Not configured** (default) allows using the Podcasts app.
- **Music service**: **Block** reverts the Music app to classic mode and disables the Music service. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **iTunes Radio service**: **Block** prevents users from using the iTunes Radio app. **Not configured** (default) allows using the iTunes Radio app.
- **iTunes store**: **Not configured** (default) allows iTunes on the devices. **Block** prevents users from using iTunes on the device. 

  Esta funcionalidade aplica-se a:  
  - iOS 4.0 and newer

- **Find my iPhone**: **Not configured** (default) allows using this Find My app feature to get the approximate location of the device. **Block** prevents this feature in the Find My app. 

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 and iPadOS 13.0 and newer

- **Find my Friends**: **Not configured** (default) allows using this Find My app feature to find family and friends from an Apple device or iCloud.com. **Block** prevents this feature in the Find My app.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 and iPadOS 13.0 and newer

- **Changes to the Find My Friends app settings**: **Block** prevents changes to the Find My Friends app settings. **Not configured** (default) allows the user to change settings for the Find My Friends app.

- **Spotlight search to return results from internet**: **Block** stops Spotlight from returning any results from an Internet search. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Block removal of system apps from device**: Choosing **Block** disables the ability to remove system apps from the device. **Not configured** (default) allows users to remove system apps.

- **Safari**: **Block** using the Safari browser on the device. **Not configured** (default) allows users to use the Safari browser.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Safari Autofill**: **Block** disables the autofill feature in Safari on the device. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.

  Starting with iOS 13.0, this setting requires supervised devices.

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Type of restricted apps list**: Create a list of apps that users aren't allowed to install or use. As opções são:

  - **Not configured** (default): There are no restrictions from Intune. Users have access to apps you assign, and built-in apps.
  - **Prohibited apps**: Apps not managed by Intune that you don't want installed on the device. Users aren't prevented from installing a prohibited app. But if a user installs an app from this list, it's reported in Intune.
  - **Approved apps**: Apps that users are allowed to install. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. But if they do, it's reported in Intune.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o URL do iTunes App Store da aplicação desejada. For example, to add the Microsoft Work Folders app, enter `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` or `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- **Import** a CSV file with details about the app, including the URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Or, **Export** an existing list that includes the restricted apps list in the same format.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps"></a>Mostrar ou ocultar aplicações

Applies to devices running iOS 9.3 or newer.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Type of apps list**: Create a list of apps to show or hide. You can show or hide built-in apps and line-of-business apps. Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT208094). As opções são:

  - **Hidden apps**: Enter a list of apps that are hidden from users. Os utilizadores não podem ver nem abrir estas aplicações.
  
    Apple prevents hiding some native apps. For example, you can't hide the **Settings** or **Wallet** apps on the device. [Delete built-in Apple apps](https://support.apple.com/HT208094) lists the apps that can be hidden.
  
  - **Visible apps**: Enter a list of apps that users can view and launch. Mais nenhuma outra aplicação pode ser vista ou lançada.

- **App URL**: Enter the store app URL of the app you want to show or hide. Por exemplo:

  - To add the Microsoft Work Folders app, enter `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` or `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - To add the Microsoft Word app, enter `https://itunes.apple.com/de/app/microsoft-word/id586447913` or `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.
  
  For more information about locating a Bundle ID, see [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **App Bundle ID**: Enter the app [bundle ID](bundle-ids-built-in-ios-apps.md) of the app you want. You can show or hide built-in apps and line-of-business apps. Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT208094).
- **App name**: Enter the app name of the app you want. You can show or hide built-in apps and line-of-business apps. Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT208094).
- **Publisher**: Enter the publisher of the app you want.

Para adicionar aplicações, pode:

- **Add**: Select to create your list of apps.
- **Import** a CSV file with details about the app, including the URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Or, **Export** to create a list of the restricted apps you added, in the same format.

## <a name="wireless"></a>Sem fios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

Note needed for Data Roaming (Tip or important note to help with customer confusion): This setting will not show up on the targeted device's management profile. That is because this setting is treated as a remote device action, and every time the state of data roaming is changed on the device, it will become blocked again by the Intune service. Even though it is not in the management profile, it is working if it showing as a success from the reporting in the admin console. 
- **Data roaming**: Choose **Block** to prevent data roaming over the cellular network. **Não configurado** (predefinição) permite o roaming de dados quando o dispositivo está numa rede móvel.

  > [!IMPORTANT]
  > This setting is treated as a remote device action. So, this setting isn't shown in the management profile on the device. Every time the data roaming status changes on the device, **Data roaming** is blocked by the Intune service. In Intune, if the reporting status shows a success, then know that it's working, even though the setting isn't shown in the management profile on the device.

- **Global background fetch while roaming**: **Block** prevents using the global background fetch feature when roaming over the cellular network. **Não configurado** (predefinição) permite que o dispositivo obtenha dados, como o e-mail, quando estiver a utilizar o roaming numa rede móvel.
- **Voice dialing**: Choose **Block** to prevent users from using the voice dialing feature on the device. **Não configurado** (predefinição) permite a marcação por voz no dispositivo.
- **Voice roaming**: Choose **Block** to prevent voice roaming over the cellular network. **Não configurado** (predefinição) permite as chamadas em roaming quando o dispositivo está numa rede móvel.
- **Personal Hotspot**: **Block** turns off the personal hotspot on the users' device with every device sync. This setting might not be compatible with some carriers. **Não configurado** (predefinição) mantém a configuração do hotspot pessoal como o conjunto predefinido pelo utilizador.

  > [!IMPORTANT]
  > This setting is treated as a remote device action. So, this setting isn't shown in the management profile on the device. Every time the personal hotspot status changes on the device, **Personal Hotspot** is blocked by the Intune service. In Intune, if the reporting status shows a success, then know that it's working, even though the setting isn't shown in the management profile on the device.

- **Cellular usage rules (managed apps only)** : Define the data types that managed apps can use when on cellular networks. As opções são:
  - **Block use of cellular data**: Block using cellular data for **All managed apps** or **Choose specific apps**.
  - **Block use of cellular data when roaming**: Block using cellular data when roaming for **All managed apps** or **Choose specific apps**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Changes to app cellular data usage settings**: Choose **Block** to prevent changes to the app cellular data usage settings. **Não configurado** (predefinição) permite que o utilizador controle quais aplicações podem utilizar os dados via rede móvel.
- **Changes to cellular plan settings**: **Block** prevents users from changing any settings in the cellular plan. **Não configurado** (predefinição) permite que os utilizadores façam alterações.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 and newer

- **User modification of Personal Hotspot**: When set to **Block**, the user can't change the personal hotspot setting. **Not configured** (default) allows end users to enable or disable their personal hotspot.

  If you block this setting and block the **Personal Hotspot** setting, the personal hotspot is turned off.

  Esta funcionalidade aplica-se a:  
  - iOS 12.2 and newer

- **Join Wi-Fi networks only using configuration profiles**: **Require** forces the device to use only Wi-Fi networks set up through Intune configuration profiles. **Não configurado** (predefinição) permite que o dispositivo utilize outras redes Wi-Fi.
- **Wi-Fi always turned on**: When set to **Require**, Wi-Fi stays on in the Settings app. It can't be turned off in Settings or in the Control Center, even when the device is in airplane mode. **Not configured** (default) allows the user to control turning on or turning off Wi-Fi.

  Configuring this setting doesn't prevent users from selecting a Wi-Fi network.

  Esta funcionalidade aplica-se a:  
  - iOS and iPadOS 13.0 and newer

## <a name="connected-devices"></a>Dispositivos Ligados

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Wrist detection for paired Apple watch**: **Require** forces a paired Apple watch to use wrist detection. Quando exigido, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Require AirPlay outgoing requests pairing password**: **Require** a pairing password when the user uses AirPlay to stream content to other Apple devices. **Não configurado** (predefinição) permite que o utilizador transmita conteúdo através do AirPlay sem introduzir uma palavra-passe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **AirDrop**: **Block** prevents using AirDrop on the device. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Apple Watch pairing**: **Block** prevents pairing with an Apple Watch. **Não configurado** (predefinição) permite que o dispositivo seja emparelhado com um Apple Watch.
- **Bluetooth modification**: **Block** stops the end user from changing Bluetooth settings on the device. **Não configurado** (predefinição) permite que o utilizador altere estas definições.
- **Host pairing to control the devices an iOS device can pair with**: **Not configured** (default) allows host pairing to let the administrator control which devices an iOS device can pair with. **Bloquear** impede o emparelhamento de anfitriões.
- **Block AirPrint**: Choose **Block** to prevent using the AirPrint feature on the device. **Não configurado** (predefinição) permite que o utilizador utilize o AirPrint.
  - **Block storage of AirPrint credentials in Keychain**: **Block** prevents using Keychain storage for username and password on the device. **Não configurado** (predefinição) permite o armazenamento do nome de utilizador e da palavra-passe do AirPrint na aplicação Keychain.
  - **Require a trusted TLS certificate for AirPrint**: **Require** forces the device to use trusted certificates for TLS printing communication.
  - **Block iBeacon discovery of AirPrint printers**: **Block** prevents malicious AirPrint Bluetooth beacons from phishing for network traffic. **Não configurado** (predefinição) permite a publicidade de impressoras AirPrint no dispositivo.
- **Block setting up new nearby devices**: **Block** disables the prompt to set up new devices that are nearby. **Não configurado** (predefinição) permite apresentar avisos aos utilizadores para se ligarem a outros dispositivos Apple próximos.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 and newer

- **Access to files on USB drive**: Devices can connect and open files on a USB drive. **Disable** prevents device access to the USB drive in the Files app when a USB is connected to the device. Disabling this feature also blocks end users from transferring files onto a USB drive connected to an iPad. **Not configured** (default) allows access to a USB drive in the Files app.

  Esta funcionalidade aplica-se a:  
  - iOS and iPadOS 13.0 and newer

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Word definition lookup**: **Block** prevents user from highlighting a word, and then looking up its definition on the device. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Predictive keyboards**: **Not configured** (default) allows using predictive keyboards to suggest words the user might want. **Bloquear** impede esta funcionalidade.
- **Auto-correction**: **Not configured** (default) allows the device to automatically correct misspelled words. **Bloquear** impede a utilização da correção automática.
- **Keyboard spell-check**: **Not configured** (default) allows using spellchecker on the device. **Bloquear** não permite a verificação ortográfica.
- **Keyboard shortcuts**: **Not configured** (default) allows using keyboard shortcuts on the device. **Bloco** impede o utilizador de utilizar os atalhos de teclado.
- **Dictation**: **Block** stops the user from using voice input to enter text. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **QuickPath**: **Not configured** (default) allows users to use QuickPath, which allows a continuous input on the device's keyboard. Users can type by swiping across the keys to create words. **Block** prevents users from using QuickPath. 

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 and iPadOS 13.0 and newer

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

### <a name="settings-apply-to-all-enrollment-types"></a>Settings apply to: All enrollment types

- **Encrypted backup**: **Require** so device backups must be encrypted.
- **Managed apps sync to cloud**: **Not configured** (default) allows your Intune-manages apps to sync data to the user's iCloud account. **Bloquear** impede esta sincronização de dados com o iCloud.
- **Block Enterprise Book Backup**: Choose **Block** to prevent users from backing up enterprise books. **Not configured** (default) allows users to back up these books.
- **Block enterprise book metadata sync (notes and highlights)** : **Block** prevents syncing notes and highlights in enterprise books. **Not configured** (default) allows the syncing.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Photo stream syncing to iCloud**: **Not configured** (default) lets users enable **My Photo Stream** on their device to sync to iCloud, and have photos available on all the user's devices. **Bloquear** impede a sincronização do fluxo de fotografias com o iCloud. Blocking this feature may cause data loss. 
- **iCloud Photo Library**: Set to **Block** to disable using iCloud photo library to store photos and videos in the cloud. Todas as fotografias que não tiverem sido completamente transferidas da Fototeca em iCloud para o dispositivo serão removidas do dispositivo. **Not configured** (default) allows using the iCloud photo library.
- **Shared photo stream**: Choose **Block** to disable **iCloud Photo Sharing** on the device. **Not configured** (default) allows shared photo streaming.
- **Handoff**: **Not configured** (default) allows users to start work on an iOS device, and then continue the work they started on another iOS or macOS device. **Bloquear** impede esta passagem de informações.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Backup to iCloud**: **Not configured** (default) allows the user to back up the device to iCloud. **Bloquear** impede que o utilizador faça cópias de segurança do dispositivo para o iCloud.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Block iCloud Document sync**: **Not configured** (default) allows document and key-value synchronization to your iCloud storage space. **Bloquear** impede o iCloud de sincronizar documentos e dados.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Block iCloud Keychain sync**: Choose **Block** to disable syncing credentials stored in the Keychain to iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.

  Starting with iOS 13.0, this setting requires supervised devices.

## <a name="autonomous-single-app-mode"></a>Autonomous single app mode

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado. Pode executar apenas essa aplicação. Por exemplo, adicione uma aplicação que permita que os utilizadores façam um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **App name**: Enter the name of the app you want.
- **App Bundle ID**: Enter the [bundle ID](bundle-ids-built-in-ios-apps.md) of the app you want.
- **Add**: Select to create your list of apps.

You can also **Import** a CSV file with the list of app names and their bundle IDs. Ou **Exportar** uma lista existente que inclua as aplicações.

## <a name="kiosk"></a>Modo de Local Público

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **App to run in kiosk mode**: Choose the type of apps you want to run in kiosk mode. As opções são:
  - **Not configured** (default): Kiosk settings aren't applied. O dispositivo não é executado no modo de quiosque.
  - **Store App**: Enter the URL to an app in the iTunes App store.
  - **Managed App**: Choose an app you added to Intune.
  - **Built-In App**: Enter the [bundle ID](bundle-ids-built-in-ios-apps.md) of the built-in app.

- **Assistive touch**: **Require** the Assistive Touch accessibility setting be on the device. Esta funcionalidade ajuda os utilizadores com os gestos no ecrã que podem ser difíceis para eles. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Invert colors**: **Require** the Invert Colors accessibility setting so users with visual impairments can change the display screen. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Mono audio**: **Require** the Mono audio accessibility setting be on the device. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Voice control**: **Require** enables voice control on the device, and allows users to fully control the OS using Siri commands. **Not configured** disables voice control on the device.

  Esta definição aplica-se a:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer
  
  > [!TIP]
  > If you have LOB apps available for your organization, and they're not **Voice Control** ready on day 0 when iOS 13.0 releases, then we recommend you leave this setting as **Not configured**.

- **VoiceOver**: **Require** the VoiceOver accessibility setting be on the device to read text on the screen out loud. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Zoom**: **Require** the Zoom setting be on the device to let users use touch to zoom in on the screen. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Auto lock**: **Block** prevents automatic locking of the device. **Not configured** allows this feature.
- **Ringer switch**: **Block** disables the ringer (mute) switch on the device. **Not configured** allows this feature.
- **Screen rotation**: **Block** prevents changing the screen orientation when the user rotates the device. **Not configured** allows this feature.
- **Screen sleep button**: Choose **Block** to disable the screen sleep wake button on the device. **Not configured** allows this feature.
- **Touch**: **Block** disables the touchscreen on the device. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Volume buttons**: **Block** prevents using the volume buttons on the device. **Not configured** allows the volume buttons.
- **Assistive touch control**: **Allow** let users use the assistive touch function. **Não configurado** desativa esta funcionalidade.
- **Invert colors control**: **Allow** invert color changes to let users adjust the invert colors function. **Não configurado** desativa esta funcionalidade.
- **Speak on selected text**: **Allow** the Speak Selection accessibility settings be on the device. Esta funcionalidade lê em voz alta o texto que o utilizador seleciona. **Não configurado** desativa esta funcionalidade.
- **Voice control modification**: **Allow** users to change the state of voice control on their devices. **Not configured** blocks users from changing the state of voice control on their devices.

  Esta definição aplica-se a:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer

- **VoiceOver control**: **Allow** voiceover changes to let users update the VoiceOver function, such as how fast on-screen text is read out loud. **Não configurado** impede as alterações ao VoiceOver.
- **Zoom control**: **Allow** zoom changes by the user. **Não configurado** impede as alterações ao zoom.

> [!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Consulte o guia da Apple sobre a utilização da ferramenta Apple Configurator.
> Se a aplicação iOS que introduziu for instalada após a atribuição do perfil, o dispositivo só entrará em modo de quiosque após ser reiniciado.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Unmarked email domains** > **Email Domain URL**: Add one or more URLs to the list. Quando os utilizadores finais receberem um e-mail de um domínio diferentes dos introduzidos, o e-mail será marcado como não fidedigno na aplicação de E-mail do iOS.

- **Domínios Web geridos** > **URL do Domínio Web**: adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzidos, estes serão considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Settings apply to: Automated device enrollment (supervised)

- **Safari password autofill domains** > **Domain URL**: Add one or more URLs to the list. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. This setting applies only to the Safari browser, and devices in supervised mode. If you don't enter any URLs, then passwords can be saved from all web sites.

  Esta definição aplica-se a:  
  - iOS 9.3 and newer

## <a name="settings-that-require-supervised-mode"></a>Definições que exigem o modo supervisionado

O modo supervisionado do iOS só pode ser ativado durante a configuração inicial de dispositivos através do Programa de Registo de Aparelho da Apple ou com o Apple Configurator. Depois de ativar o modo supervisionado, o Intune pode configurar um dispositivo com a seguinte funcionalidade:

- Bloqueio de Aplicação (Modo de Aplicação Única) 
- Proxy HTTP Global 
- Ignorar Bloqueio de Ativação 
- Modo de Aplicação Única Autónomo 
- Filtro de Conteúdo Web 
- Definição de fundo e ecrã de bloqueio 
- Push da Aplicação Silencioso 
- VPN Sempre Ativada 
- Permitir exclusivamente a instalação de aplicações geridas 
- iBookstore 
- iMessages 
- Centro de Jogos 
- AirDrop 
- AirPlay 
- Emparelhamento de anfitrião 
- Sincronização de Nuvem 
- Pesquisa Spotlight 
- Handoff 
- Apagar dispositivo 
- Restrições da IU 
- Instalação dos perfis de configuração pela IU 
- Notícias 
- Keyboard shortcuts 
- Modificações do código de acesso 
- Alterações do nome do dispositivo 
- Transferências automáticas de aplicações 
- Alterações à confiança na aplicação de empresa 
- Apple Music 
- Mail Drop 
- Emparelhar com o Apple Watch 

> [!NOTE]
> A Apple confirmou que determinadas definições serão mudadas para o modo apenas supervisionado em 2019. Recomendamos que tenha isto em consideração ao utilizar estas definições em vez de aguardar que a Apple efetue a migração para o modo apenas supervisionado:
>
> - Instalação da aplicação por utilizadores finais
> - Remoção de aplicações
> - FaceTime
> - Safari
> - iTunes
> - Conteúdos explícitos
> - Documentos e dados do iCloud
> - Multiplayer gaming
> - Adicionar amigos do Game Center
> - Siri

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [macOS](device-restrictions-macos.md).
