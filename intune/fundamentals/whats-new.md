---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2b1cd79db8757995518e5622b5320077c7c4864
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409803"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. You can also find [important notices](#notices), [past releases](whats-new-archive.md), and information about [how Intune service updates are released](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> Each [monthly update](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) may take up to three days to rollout and will be in the following order:
>
> - Day 1: Asia Pacific (APAC)
> - Day 2: Europe, Middle East, Africa (EMEA)
> - Day 3: North America
>
> É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.
>
> Check the [In development page](in-development.md) for a list of upcoming features in a release.

**RSS feed**: Get notified when this page is updated by copying and pasting the following URL into your feed reader: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-november-18-2019"></a>Week of November 18, 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="smime-support-with-microsoft-outlook-for-ios---2669398-idready---"></a>S/MIME support with Microsoft Outlook for iOS<!-- 2669398 idready -->
Intune supports delivering S/MIME signing and encryption certificates that can be used with Outlook for iOS on iOS devices. For more information, see [Configure S/MIME for Outlook for iOS](~/apps/app-configuration-policies-outlook-smime.md).

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>UI update when selectively wiping app data<!-- 4102028 -->
The UI to selectively wipe app data in Intune has been updated. UI changes include:
- A simplified experience by using a wizard-style format condensed within one pane.
- An update to the create flow to include assignments.
- A summarized page of all things set when viewing properties, prior to creating a new policy or when editing a property. Also, when editing properties, the summary will only show a list of items from the category of properties being edited.

Para obter mais informações, veja [Como eliminar apenas dados empresariais de aplicações geridas pelo Intune](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS and iPadOS third party keyboard support<!-- 4922950 -->
In March, 2019, we announced the removal of support for the iOS App protection policy setting "Third party keyboards". The feature is returning to Intune with both iOS and iPadOS support. To enable this setting, visit the **Data protection** tab of a new or existing iOS/iPadOS app protection policy and find the **Third party keyboards** setting under **Data Transfer**.

The behavior of this policy setting differs slightly from the previous implementation. In multi-identity apps using SDK version 12.0.16 and later, targeted by app protection policies with this setting configured to **Block**, end-users will be unable to opt for third party keyboards in both their organization and personal accounts. Apps using SDK versions 12.0.12 and earlier will continue to exhibit the behavior documented in our blog post title, [Known issue: Third party keyboards are not blocked in iOS for personal accounts](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Target macOS user groups to require Jamf management<!-- 4061739  --> 
You can target specific groups of users that will get their [macOS devices managed by Jamf](../protect/conditional-access-integrate-jamf.md). This enables you apply the Jamf compliance integration to a subset of macOS devices while other devices are managed by Intune. If you are already using the Jamf integration, All Users will be targeted for the integration by default.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>New Exchange ActiveSync settings when creating an Email device configuration profile on iOS devices<!-- 4892824   --> 
On iOS/iPadOS devices, you can configure email connectivity in a device configuration profile (**Device configuration** > **Profiles** > **Create profile** > **iOS/iPadOS** for platform > **Email** for profile type). 

There are new Exchange ActiveSync settings available, including:
- **Exchange data to sync**: Choose the Exchange services to sync (or block syncing) for Calendar, Contacts, Reminders, Notes, and Email.
- **Allow users to change sync settings**: Allow (or block) users to change the sync settings for these services on their devices.  

For more information on these setting, go to [Email profile settings for iOS devices in Intune](../configuration/email-settings-ios.md). 

Applies to:
- iOS 13.0 and newer
- iPadOS 13.0 and newer

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Prevent users from adding personal Google accounts to Android Enterprise fully managed and dedicated devices<!-- 5353228   -->
On Android Enterprise fully managed and dedicated devices, there's a new setting that prevent users from creating personal Google accounts (**Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Device Owner Only > Device Restrictions** for profile type > **Users and Accounts settings** > **Personal Google Accounts**).

To see the settings you can configure, go to [Android Enterprise device settings to allow or restrict features using Intune](../configuration/device-restrictions-android-for-work.md).

Applies to:
- Android Enterprise fully managed devices
- Android Enterprise dedicated devices

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Server-side logging for Siri commands setting is removed in iOS/iPadOS device restrictions profile <!-- 5468501   -->
On iOS and iPadOS devices, the **Server-side logging for Siri commands** setting is removed from the Microsoft Endpoint Manager admin console (**Device configuration** > **Profiles** > **Create profile** > **iOS/iPadOS** for platform > **Device restrictions** for profile type > **Built-in apps**). 

This setting has no effect on devices. To remove the setting from existing profiles, open the profile, make any change, and then save the profile. The profile is updated, and the setting is deleted from devices.

To see all the settings you can configure, see [iOS and iPadOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-ios.md).

Applies to:
- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 feature updates (public preview)<!-- 2384877 -->
You can now deploy [Windows 10 feature updates](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) to Windows 10 devices. Windows 10 feature updates are a new software update policy that sets the version of Windows 10 that you want devices to install and remain at. You can use this new policy type along with your existing Windows 10 update rings.

Devices that receive Windows 10 feature updates policy will install the specified version of Windows, and then remain at that version until the policy is edited or removed. Devices that run a later version of Windows remain at their current version. Devices that are held at a specific version of Windows can still install quality and security updates for that version from Windows 10 update rings.

This new type of policy begins rolling out to tenants this week. If this policy isn't available for your tenant yet, it will be soon.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Add and change key information in plist files for macOS applications<!-- 4736278 -->
On macOS devices, you can now create a device configuration profile that uploads a property list file (.plist) associated with an app or with the device (**Devices** > **Configuration profiles** > **Create profile** > **macOS** for platform > **Preference File** for profile type).

Only some apps support managed preferences, and these apps might not allow you to manage all settings. Be sure to upload a property list file that configures device channel settings, not user channel settings.

For more information on this feature, see [Add a property list file to macOS devices using Microsoft Intune](../configuration/preference-file-settings-macos.md).

Applies to:
- macOS devices running 10.7 and newer

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-deployment-reports---3856172---"></a>Windows Autopilot deployment reports<!-- 3856172 -->
A new report details each device deployed through Windows Autopilot. For more information, see [Autopilot deployment report](../enrollment/enrollment-autopilot.md#autopilot-deployments-report). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Edit device name value for Autopilot devices<!-- 2640074 -->
You can edit the Device Name value for Azure AD Joined Autopilot devices.  For more information, see [Edit Autopilot device attributes](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Edit Group Tag value for Autopilot devices<!-- 4816775   -->
You can edit the Group Tag value for Autopilot devices. For more information, see [Edit Autopilot device attributes](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="updated-support-experience---5012398---"></a>Updated support experience<!-- 5012398 -->

Starting today, an updated and streamlined in-console experience for [getting help and support for Intune](get-support.md) is rolling out to tenants. If this new experience isn't available for you yet, it will be soon.

We've improved the in-console search and feedback for common issues, and the workflow you use to contact support. When opening a support issue, you'll see real-time estimates for when you can expect a callback or email reply, and Premier and Unified support customers can easily specify a severity for their issue, to help get support faster.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Improved Intune reporting experience (public preview) <!-- 3791418 -->
Intune now provides an improved reporting experience, including new report types, better report organization, more focused views, improved report functionality, as well as more consistent and timely data. New report types focus on the following:
- **Operational** - Provides fresh records with a negative health focus. 
- **Organizational** - Provides an broader summary of the overall state.
- **Historical** - Provides patterns and trends over a period of time.
- **Specialist** - Allows you to use raw data to create your own custom reports.

The first set of new reports focuses on device compliance. For more information, see [Blog - Microsoft Intune reporting framework](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) and [Intune reports](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Duplicate custom or built-in roles <!-- 1081938   -->
You can now copy built-in and custom roles. For more information, see [Copy a role](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>New permissions for school administrator role <!-- 5621805  -->  
Two new permissions, **Assign profile** and **Sync device**, have been added to the school administrator role > **Permissions** > **Enrollment programs**. The sync profile permission lets group admins sync Windows Autopilot devices. The assign profile permission lets them delete user-initiated Apple enrollment profiles. It also gives them permission to manage Autopilot device assignments and Autopilot deployment profile assignments. For a list of all school administrator/group admin permissions, see [Assign group admins](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Segurança

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker key rotation<!-- 2564951  -->
You can use an Intune device action to remotely [rotate BitLocker recovery keys](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)  for managed devices that run Windows version 1909 or later. To qualify to have recovery keys rotated, devices must be configured to support recovery key rotation.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Updates to dedicated device enrollment to support SCEP device certificate deployment <!-- 5198878  -->
Intune now supports SCEP device certificate deployment to Android Enterprise dedicated devices for certificate-based access to Wi-Fi profiles. The Microsoft Intune app must be present on the device for deployment to work. As a result, we've updated the enrollment experience for Android Enterprise dedicated devices. New enrollments still start the same (with QR, NFC, Zero-touch, or device identifier) but now have a step that requires users to install the Intune app. Existing devices will start getting the app automatically installed on a rolling basis.

#### <a name="intune-support-for-azure-ad-business-to-business-collaboration--5670211----"></a>Intune support for Azure AD business-to-business collaboration<!--5670211  -->
Intune supports Azure Active Directory (Azure AD) business-to-business (B2B) collaboration. Azure AD B2B collaboration lets you securely share your company's applications and services with guest users from any other organization, while maintaining control over your own corporate data. This functionality also provides auditing capabilities of B2B guest users. For more information, see [What is guest user access in Azure Active Directory B2B?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)

<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Week of November 11, 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>Improved macOS enrollment experience in Company Portal <!-- 5074349 WNready -->  
The Company Portal for macOS enrollment experience has a simpler enrollment process that aligns more closely with the Company Portal for iOS enrollment experience. Device users now see:  

* A sleeker user interface.  
* An improved enrollment checklist.  
* Clearer instructions about how to enroll their devices.  
* Improved troubleshooting options.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Web apps launched from the Windows Company Portal app<!-- 5030972 -->
End-users can now launch web apps directly from the Windows Company Portal app. End-users can select the web app and then choose the option **Open in browser**. The published web URL is opened directly in a web browser. This functionality will be rolled out over the next week. For more information about Web apps, see [Add web apps to Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950-wnready---"></a>New assignment type column in Company Portal for Windows 10 <!-- 5459950 WNready -->
The Company Portal > **Installed Apps** > **Assignment type** column has been renamed to **Required by your organization**.  Under that column, users will see a **Yes** or **No** value to indicate that an app is either required or made optional by their organization. These changes were made because device users were confused about the concept of available apps. Your users can find more information about installing apps from Company Portal in [Install and share apps on your device](/intune-user-help/install-apps-cpapp-windows). For more  information about configuring the Company Portal app for your users, see [How to configure the Microsoft Intune Company Portal app](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Week of November 4, 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Security baselines are supported on Microsoft Azure Government<!-- 4062552 -->

Instances of  Intune that are hosted on *Microsoft Azure Government* can now use [security baselines](../protect/security-baselines.md) to help you secure and protect your users and devices.

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>Week of October 28, 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Improved checklist design in Company Portal app for Android<!-- 5550857 -->  
The setup checklist in the Company Portal app for Android has been updated with a lightweight design and new icons. The changes align with the recent updates made to the Company Portal app for iOS. For a side-by-side comparison of the changes, see [What's new in the app UI](whats-new-app-ui.md). For a look at the updated enrollment steps, see [Enroll with Android work profile](/intune-user-help/enroll-device-android-work-profile) and [Enroll your Android device](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Win32 apps on Windows 10 S mode devices<!-- 3747604 --> 
You can install and run Win32 apps on Windows 10 S mode managed devices. To do this, you can create one or more supplemental policies for S mode using the Windows Defender Application Control (WDAC) PowerShell tools. Sign the supplemental policies with the Device Guard Signing Portal and then upload and distribute the policies via Intune. In Intune, you will find this capability by selecting **Client apps** > **Windows 10 S supplemental policies**. For more information, see [Enable Win32 apps on S mode devices](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Set Win32 app availability based on a date and time<!-- 3510685 -->
As an admin, you can configure the start time and deadline time for a required Win32 app. At the start time, Intune management extension will start the app content download and cache it. The app will be installed at the deadline time. For available apps, start time will dictate when the app is visible in Company Portal. For more information, see [Intune Win32 app management](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Require device restart based on grace period after Win32 app install<!-- 3136567 -->
You can require that a device must restart after a Win32 app successfully installs. For more information, see [Win32 app management - Configure app installation details](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Dark Mode for iOS Company Portal<!-- 4911422 -->
Dark Mode is available for the iOS Company Portal. Users can download company apps, manage their devices, and get IT support in the color scheme of their choice based on device settings. The iOS Company Portal will automatically match the end user's device settings for dark or light mode. For more information, see [Introducing dark mode on Microsoft Intune Company Portal for iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). For more information about the iOS Company Portal, see [How to configure the Microsoft Intune Company Portal app](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android Company Portal enforced minimum app version<!-- 2378776 -->
By using the **Min Company Portal version** setting of an app protection policy, you can specify a specific minimum defined version of the Company Portal that is enforced on an end user device. This conditional launch setting allows you to **Block access**, **Wipe data**, or **Warn** as possible actions when the value is not met. The possible formats for this value follows the pattern *[Major].[Minor]* , *[Major].[Minor].[Build]* , or *[Major].[Minor].[Build].[Revision]* .

The **Min Company Portal version** setting, if configured, will affect any end user who gets version 5.0.4560.0 of the Company Portal and any future versions of the Company Portal. This setting will have no effect on users using a version of Company Portal that is older than the version that this feature is released with. End users using app auto-updates on their device will likely not see any dialogs from this feature, given that they will likely be on the latest Company Portal version. This setting is Android only with app protection for enrolled and unenrolled devices. For more information, see [Android app protection policy settings - Conditional launch](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365 Device Management

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introducing Endpoint Security node in Microsoft 365 Device Management<!-- 5630102 -->

**Endpoint Security** node is now generally available in Microsoft 365 Device Management specialist workspace at https://devicemanagement.microsoft.com, which groups together the capabilities to secure endpoints such as:

- Security Baselines:  Pre-configured group of settings that help you apply known group of settings and default values that are recommended by Microsoft.

- Security Tasks: Take advantage of Microsoft Defender ATPs Threat and Vulnerability Management (TVM) and use Intune to remediate endpoint weaknesses.

- Microsoft Defender ATP: Integrated Microsoft Defender Advanced Threat Protection (ATP) to help prevent security breaches.

These settings will continue to be accessible from other applicable nodes such as devices, and current configured state will be the same no matter where you access and enable these capabilities.

For more information about these improvements, see the [Intune Customer Success blog post](https://aka.ms/Endpoint_security_node) on the Microsoft Tech Community web site.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune supports iOS 11 and later<!-- 4665324  -->

Intune enrollment and Company Portal now support iOS versions 11 and later. Older versions aren't supported.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge baseline (Preview)<!--  3787164  -->

We've added a security baseline Preview for [Microsoft Edge settings](../protect/security-baseline-settings-edge.md). 

<!-- ########################## -->
## <a name="week-of-october-21-2019"></a>Week of October 21, 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 Device Management

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Improved administration experience in Microsoft 365 Device Management<!-- 5551239 -->

A refreshed and streamlined administration experience is now generally available in the Microsoft 365 Device Management specialist workspace at [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com), including:

- **Updated navigation**: You will find a simplified 1st level navigation that logically groups features.
- **New platform filters**: You can select a single platform, which shows only the policies and apps for the selected platform, on the Devices and Apps pages.
- **A new home page**: Quickly see service health, state of your tenant, news, etc. on the new home page.

For more information about these improvements, see the [Enterprise Mobility + Security blog post](https://go.microsoft.com/fwlink/?linkid=2109094) on the Microsoft Tech Community web site.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Add Mobile Threat Defense apps to unenrolled devices<!-- 3005337 -->
You can create an Intune app protection policy that may block, or selectively wipe the users corporate data based on the health of a device. The health of the device is determined using your chosen Mobile Threat Defense (MTD) solution. This capability exists today with Intune enrolled devices as a device compliance setting. With this new feature, we extend the threat detection from an Mobile Threat Defense vendor to function on unenrolled devices. On Android, this feature requires the latest Company Portal on the device. On iOS, this feature will be available for use when apps integrate the latest Intune SDK (v 12.0.15+). We'll update the What's New topic when the first app adopts the latest Intune SDK. The remaining apps will become available on a rolling basis. For more information, see [Create Mobile Threat Defense app protection policy with Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>New device firmware configuration interface profile for Windows 10 and later devices (public preview)<!-- 2266073  -->

On Windows 10 and later, you can create a device configuration profile to control settings and features (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform). In this update, there's a new device firmware configuration interface profile type that allows Intune to manage UEFI (BIOS) settings.

For more information on this feature, see [Use DFCI profiles on Windows devices in Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Applies to:
- Windows 10 RS5 (1809) and newer on supported firmware

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Toggle to only show Enrollment Status Page on devices provisioned by out-of-box experience (OOBE)<!--3959566-->
You can now choose to only show the Enrollment Status Page on devices provisioned by Autopilot OOBE.

To see the new toggle, choose **Intune** > **Device enrollment** > **Windows enrollment** > **Enrollment Status Page** > **Create Profile** > **Settings** > **Only show page to devices provisioned by out-of-box experience (OOBE)** .


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Week of October 14, 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Available Google Play app reporting for Android work profiles<!-- 3041956   -->
For available app installs on Android Enterprise work profile, dedicated, and fully managed devices you can view app installation status as well as the installed version of managed Google Play apps. For more information, see [How to monitor app protection policies](~/apps/app-protection-policies-monitor.md), [Manage Android work profile devices with Intune](~/enrollment/android-enterprise-overview.md) and [Managed Google Play app type](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge version 77 and later for Windows 10 and macOS (public preview)<!-- 3872025, 4678761  -->
Microsoft Edge version 77 and later will be available to deploy to PCs running Windows 10 and macOS. 

The public preview offers **Dev** and **Beta** channels for Windows 10 and a **Beta** channel for macOS. The deployment is in English (EN) only, however end users can change the display language in the browser under **Settings** > **Languages**. Microsoft Edge is a Win32 app installed in system context and on like architectures (x86 app on x86 OS, and x64 app on x64 OS). In addition, automatic updates of the browser is **On** by default, and Microsoft Edge cannot be uninstalled. For more information, see [Add Microsoft Edge for Windows 10 to Microsoft Intune](~/apps/apps-windows-edge.md) and [Microsoft Edge documentation](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Update to app protection UI and iOS app provisioning UI<!-- 4102027, 4102029   -->
The UI to create and edit app protection policies and iOS app provisioning profiles in Intune has been updated. UI changes include:
- A simplified experience by using a wizard-style format condensed within one blade. 
- An update to the create flow to include assignments.
- A summarized page of all things set when viewing properties, prior to creating a new policy or when editing a property. Also, when editing properties, the summary will only show a list of items from the category of properties being edited.

For more information, see [How to create and assign app protection policies](~/apps/app-protection-policies.md) and [Use iOS app provisioning profiles](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Intune guided scenarios<!-- 4850318, 4831296, 3610611  -->
Intune now provides guided scenarios to help you complete a specific task or set of tasks within Intune. A guided scenario is a customized series of steps (workflow) centered around one end-to-end use-case. Common scenarios are defined based on the role an admin, user, or device plays in your organization. These workflows typically require a collection of carefully orchestrated profiles, settings, applications, and security controls to provide the best user experience and security. New guided scenarios include:
- [Deploy Microsoft Edge for Mobile](~/fundamentals/guided-scenarios-edge.md)
- [Secure Microsoft Office mobile apps](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Cloud-managed Modern Desktop](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

For more information, see [Intune guided scenarios overview](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Additional app configuration variable available<!-- 4969237   -->
When creating an app configuration policy, you can include the `AAD Device ID` configuration variable as part of your configuration settings. In Intune, select **Client apps** > **App configuration policies** > **Add**. Enter your configuration policy details and select **Configuration settings** to view the **Configuration settings** blade. For more information, see [App configuration policies for managed Android Enterprise devices - Use the configuration designer](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Create groups of management objects called policy sets<!-- 3762880  -->
Policy sets allow you to create a bundle of references to already existing management entities that need to be identified, targeted, and monitored as a single conceptual unit. Policy sets do not replace existing concepts or objects. You can continue to assign individual objects in Intune and you can reference individual objects as part of a policy set. Therefore, any changes to those individual objects will be reflected in the Policy set.  In Intune, you will select **Policy sets** > **Create** to create a new Policy set. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>UI update for creating and editing Windows 10 Update Rings<!-- 4099089         -->
We’ve updated the UI experience for [creating and editing Windows 10 Update Rings](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) for Intune. Changes to UI include:  
- A wizard-style format condensed into a single console blade, which does away with the blade sprawl seen previously as you configure update rings.   
- The revised workflow includes Assignments, before completing the initial configuration of the ring.
- A summary page you can use to review all the configurations you made, before saving and deploying a new update ring. When editing an update ring, the summary shows only the list of items set within the category of properties you edited.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>UI update for creating and editing iOS software update policy<!-- 4099090       --> 
We’ve updated the UI experience for [creating](../protect/software-updates-ios.md#configure-the-policy) and [editing](../protect/software-updates-ios.md#edit-a-policy) iOS software update policies for Intune.  Changes to UI include:  
- A wizard-style format condensed into a single console blade, which does away with the blade sprawl seen previously as you configure update policies.   
- The revised workflow includes Assignments, before completing the initial configuration of the policy.
- A summary page you can use to review all the configurations you made, before saving and deploying a new policy. When editing a policy, the summary shows only the list of items set within the category of properties you edited.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Engaged restart settings are removed from Windows Update rings<!--  4464404   WNReady   -->
As previously announced, Intune's Windows 10 Update rings now [support settings for deadlines](../protect/windows-update-settings.md) and no longer support *Engaged restart*. Settings for *Engaged restart* are no longer available when you configure or manage Update rings in Intune.  

This change aligns with recent [Windows servicing changes](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) and on devices that run Windows 10 1903 or later, *deadlines* supersede configurations for *engaged restart*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Prevent installation of apps from Unknown Sources on Android Enterprise work profile devices<!-- 4760025   -->
On Android Enterprise work profile devices, users can't ever install apps apps from unknown sources. In this update, there's a new setting - **Prevent app installations from unknown sources in the personal profile**. By default, this setting prevents users from side-loading apps from unknown sources into the personal profile on the device.

To see the setting you can configure, go to [Android Enterprise device settings to allow or restrict features using Intune](../configuration/device-restrictions-android-for-work.md).

Applies to:
- Android Enterprise work profile

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Create a global HTTP proxy on Android Enterprise device owner devices<!-- 4816339   -->
On Android Enterprise devices, you can configure a global HTTP Proxy to meet your organization’s web browsing standards (**Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Device owner > Device restrictions** for profile type > **Connectivity**). Once configured, all HTTP traffic will use this proxy.

To configure this feature, and see all the settings you configure, go to [Android Enterprise device settings to allow or restrict features using Intune](../configuration/device-restrictions-android-for-work.md).

Applies to:
- Android Enterprise device owner

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Connect automatically setting is removed in Wi-Fi profiles on Android device administrator and Android Enterprise<!-- 5021055   -->
On Android device administrator and Android Enterprise devices, you can create a Wi-Fi profile to configure different settings (**Device configuration** > **Profiles** > **Create profile** > **Android device administrator** or **Android Enterprise** for platform > **Wi-Fi** for profile type). In this update, the **Connect automatically** setting is removed, as it's [not support by Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

If you use this setting in a Wi-Fi profile, you may have noticed that **Connect automatically** doesn't work. You don't need to take any action, but be aware this setting is removed in the Intune user interface.

To see the current settings, go to [Android Wi-Fi settings](../configuration/wi-fi-settings-android.md) or [Android Enterprise Wi-Fi settings](../configuration/wi-fi-settings-android-enterprise.md).

Applies to:
- Android device administrator 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>New device configuration settings for supervised iOS and iPadOS devices<!-- 5199328   -->
On iOS and iPadOS devices, you can create a profile to restrict features and settings on devices (**Device configuration** > **Profiles** > **Create profile** > **iOS/iPadOS** for platform > **Device restrictions** for profile type). In this update, there are new settings you can control: 
- Access to network drive in Files app  
- Access to USB drive in Files app 
- Wi-Fi always turned on 

To see these settings, go to [iOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-ios.md).

Applies to:
- iOS 13.0 and newer
- iPadOS 13.0 and newer

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Specify which Android device operating system versions enroll with work profile or device administrator enrollment<!-- 4350697   -->
Using Intune device type restrictions, you can use the device's OS version to specify which user devices will use Android Enterprise work profile enrollment or Android device administrator enrollment.  For more information, see [Set enrollment restrictions](../enrollment/enrollment-restrictions-set.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>New restrictions for renaming Windows devices<!-- 3478938  -->
When renaming a Windows device, you must follow new rules:
- 15 characters or less (must be less than or equal to 63 bytes, not including trailing NULL)
- Not null or an empty string
- Allowed ASCII: Letters (a-z, A-Z), numbers (0-9), and hyphens
- Allowed Unicode: characters >= 0x80, must be valid UTF8, must be IDN-mappable (that is, RtlIdnToNameprepUnicode succeeds; see RFC 3492)
- Names must not contain only numbers
- No spaces in the name
- Disallowed characters: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 For more information, see [Rename a device in Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>New Android report on Devices overview page<!-- 4924364 -->
A new report to the Devices overview page displays how many Android devices have been enrolled in each device management solution. This chart shows work profile, fully managed, dedicated, and device administrator enrolled device counts. To see the report, choose **Intune** > **Devices** > **Overview**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>PKCS certificates for macOS<!-- 1333650       -->
You can now [use PKCS certificates with macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). You can select the PKCS certificate as a profile type for macOS, and deploy user and device certificates that have [customized subject and subject alternative name fields](../protect/certficates-pfx-configure.md#subject-name-format-for-macos).  

PKCS certificate for macOS also support a new setting, _Allow All Apps Access_. With this setting you can enable all associated apps access to the private key of the certificate.  For more information about this setting, see the Apple documentation at https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Derived Credentials to provision iOS mobile devices with certificates<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune supports use of [derived credentials](../protect/derived-credentials.md) as an authentication method and for S/MIME signing and encryption for iOS devices. Derived credentials are an implementation of the *National Institute of Standards and Technology (NIST) 800-157* standard for deploying certificates to devices.  

Derived credentials rely on the use of a Personal Identity Verification (PIV) or Common Access Card (CAC) card, like a smart card. To get a derived credential for their mobile device, users start in the Company Portal app and follow an enrollment workflow that is unique to the provider you use.  Common to all providers is the requirement to use a smart card on a computer to authenticate to the derived credential provider. That provider then issues a certificate to the device that's derived from the user’s smart card.  

Intune supports the following derived credential providers:
- DISA Purebred
- Entrust Datacard
- Intercede

You use derived credentials as the authentication method for device configuration profiles for VPN, Wi-Fi, and email. You can also use them for app authentication, and S/MIME signing and encryption.  

For more information about the standard, see [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) at www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Use Graph API to specify a on-premises User Principal Name as a variable for SCEP certificates<!--  5437939        -->  
When you use the [Intune Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0), you can specify onPremisesUserPrincipalName as a variable for the Subject Alternative Name (SAN) for SCEP certificates.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Week of September 23, 2019

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>iOS User Enrollment in Preview<!-- 4817900 -->
Apple's iOS 13.1 release includes User Enrollment, a new form of lightweight management for iOS devices. It can be used in place of Device Enrollment or Automated Device Enrollment (formerly Device Enrollment Program) for personally-owned devices. Intune's Preview is supporting this feature set by letting you:

- Target User Enrollment to user groups.
- Give end users the ability to select between lighter User Enrollment or stronger Device Enrollment when they enroll their devices.

Starting on 9/24/2019 with the release of iOS 13.1, we're in the process of rolling out these updates to all customers and expect to be completed by the end of next week.
Applies to:

iOS 13.1 and later

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Intune support for iPadOS and iOS 13.1 devices<!--5439574-->
Intune now supports managing both iPadOS and iOS 13.1 devices. Para obter mais informações, veja [esta mensagem do blogue](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Week of September 16, 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Managed Google Play private LOB apps<!-- 1464182  -->
Intune now allows IT admins to publish private Android LOB apps to Managed Google Play via an iframe embedded in the Intune console.  Previously, IT admins needed to publish LOB apps directly to Google's Play publishing console, which required several steps and was time consuming. This new feature allows for easy publishing of LOB apps with a minimal set of steps, without needing to leave the Intune console.  Admins will no longer need to manually register as a developer with Google, and will no longer need to pay the Google $25 registration fee.  Any of the Android Enterprise management scenarios that use Managed Google Play can take advantage of this feature (work profile, dedicated, fully managed, and non-enrolled devices). From Intune, select **Client apps** > **Apps** > **Add**. Then, select **Managed Google Play** from the **App type** list. For more information about Managed Google Play apps, see [Add Managed Google Play apps to Android Enterprise devices with Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows Company Portal experience<!-- 1473353, 3598357 -->
The Windows Company Portal is being updated. You will be able to use multiple filters on the Apps page within the Windows Company Portal. The Device Details page is also being updated with an improved user experience. We are in the process of rolling out these updates to all customers and expect to be completed by the end of next week.

#### <a name="macos-support-for-web-apps---3174427---"></a>macOS support for web apps<!-- 3174427 -->
Web apps, which allow you to add a shortcut to a URL on the web, can be installed to the Dock using the macOS Company Portal. End users can access the **Install** action from the app details page for a web app in the macOS Company Portal. For more information about the **Web link** app type, see [Add apps to Microsoft Intune](../apps/apps-add.md) and [Add web apps to Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>macOS support for VPP apps<!-- 3173501  -->
macOS apps, purchased using Apple Business Manager, are displayed in the console when Apple VPP tokens are synced in Intune. You can assign, revoke and reassign device and user-based licenses for groups using the Intune console. Microsoft Intune helps you manage VPP apps purchased for use at your company by:

- Comunicar informações sobre a licença a partir da App Store.
- Controlar o número de licenças que utilizou.
- Helping you prevent installation of more copies of the app than you own.

For more information about Intune and VPP, see [Manage volume-purchased apps and books with Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>Managed Google Play iframe support<!-- 2871756  -->
Intune now provides support for adding and managing web links directly in the  Intune console via the Managed Google Play iframe.  This lets IT admins submit a URL and icon graphic, and then deploy those links to devices just like regular Android apps. Any of the Android Enterprise management scenarios that use Managed Google Play can take advantage of this feature (work profile, dedicated, fully managed, and non-enrolled devices). From Intune, select **Client apps** > **Apps** > **Add**. Then, select **Managed Google Play** from the **App type** list. For more information about Managed Google Play apps, see [Add Managed Google Play apps to Android Enterprise devices with Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Silently install Android LOB apps on Zebra devices<!-- 4252734  -->
When installing Android line-of-business (LOB) apps on [Zebra devices](../configuration/android-zebra-mx-overview.md), rather than being prompted to both download and install the LOB app, you will be able to install the app silently. In Intune, select **Client apps** > **Apps** > **Add**. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**. For more information, see [Add an Android line-of-business app to Microsoft Intune](../apps/lob-apps-android.md).

Currently, after the LOB app is downloaded, a **download success** notification will appear on the user's device. The notification can only be dismissed by tapping **Clear All** in the notification shade. This notification issue will be fixed in an upcoming release, and the installation will be completely silent with no visual indicators.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Read and write Graph API operations for Intune apps<!-- 5031704  -->
Applications can call the Intune Graph API with both read and write operations using app identity without user credentials. For more information about accessing the Microsoft Graph API for Intune, see [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Protected data sharing and encryption for Intune App SDK for iOS<!-- 3586942  -->
The Intune App SDK for iOS will use 256-bit encryption keys when encryption is enabled by App Protection Policies. All apps will need to have a SDK version 8.1.1 to allow protected data sharing.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Support for IKEv2 VPN profiles for iOS<!-- 1943438   -->
In this update, you can create VPN profiles for the iOS native VPN client using the IKEv2 protocol. IKEv2 is a new connection type in **Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **VPN** for profile type > **Connection Type**.

These VPN profiles configure the native VPN client, so no VPN client apps are installed or pushed to managed devices. This feature requires devices be enrolled in Intune (MDM enrollment).

To see the current VPN settings you can configure, go to [Configure VPN settings on iOS devices](../configuration/vpn-settings-ios.md).

Applies to:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Device features, device restrictions, and extension profiles for iOS and macOS settings are shown by enrollment type<!-- 4886161   -->

In Intune, you create profiles for iOS and macOS devices (**Device configuration** > **Profiles** > **Create profile** > **iOS** or **macOS** for platform > **Device features**, **Device restrictions**, or **Extensions** for profile type). 

In this update, the available settings in the Intune portal are categorized by the enrollment type they apply to:

- iOS
  - User enrollment
  - Inscrição de dispositivos
  - Automated device enrollment (supervised)
  - All enrollment types

- macOS
  - User approved
  - Inscrição de dispositivos
  - Automated device enrollment
  - All enrollment types

Applies to:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>New voice control settings for supervised iOS devices running in kiosk mode<!-- 4892835   -->
In Intune, you can create policies to run supervised iOS devices as a kiosk, or dedicated device (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **Kiosk**).

In this update, there are new settings you can control:
- **Voice control**: Enables Voice Control on the device while in kiosk mode.
- **Modification of voice control**: Allow users to change the Voice Control setting on the device while in kiosk mode.

To see the current settings, go to [iOS Kiosk settings](../configuration/device-restrictions-ios.md#kiosk).

Applies to:
- iOS 13.0 and later

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Use single sign-on for apps and websites on your iOS and macOS devices<!-- 4893175   -->
In this update, there are some new single sign-on settings for iOS and macOS devices (**Device configuration** > **Profiles** > **Create profile** > **iOS** or **macOS** for platform > **Device features** for profile type).

Use these settings to configure a single sign-on experience, especially for apps and websites that use Kerberos authentication. You can choose between a generic credential single sign-on app extension, and Apple's built-in Kerberos extension.

To see the current device features you can configure, go to [iOS device features](../configuration/ios-device-features-settings.md) and [macOS device features](../configuration/macos-device-features-settings.md).

Applies to:
- iOS 13.0 and newer
- macOS 10.15 and newer

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associate domains to apps on macOS 10.15+ devices<!-- 4898079   -->
On macOS devices, you can configure different features, and push these features to your devices using a policy (**Device configuration** > **Profiles** > **Create profile** > **macOS** for platform > **Device features** for profile type). In this update, you can associate domains to your apps. This feature helps share credentials with websites related to your app, and can be used with Apple’s single sign-on extension, universal links, and password autofill. 

To see the current features you can configure, go to [macOS device feature settings in Intune](../configuration/macos-device-features-settings.md).

Applies to:
- macOS 10.15 and newer

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Use "iTunes" and "apps" in the iTunes App store URL when showing or hiding apps on iOS supervised devices<!-- 4928474   --> 
In Intune, you can create policies to show or hide apps on your supervised iOS devices (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **Show or hide apps**). 

You can enter the iTunes App store URL, such as `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. In this update, both `apps` and `itunes` can be used in the URL, such as:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

For more information on these settings, see [Show or hide apps](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Applies to:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Windows 10 compliance policy password type values are clearer and match CSP<!-- 5138985 -->
On Windows 10 devices, you can create a compliance policy that requires specific password features (**Device compliance** > **Policies** > **Create policy** > **Windows 10 and later** for platform > **System Security**). In this update:
- The **Password type** values are clearer, and updated to match the [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- The **Password expiration (days)** setting is updated to allow values from 1-730 days. 

For more information on Windows 10 compliance settings, see [Windows 10 and later settings to mark devices as compliant or not compliant](../protect/compliance-policy-create-windows.md). 

Applies to:
- Windows 10 e posterior

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Updated UI for configuring Microsoft Exchange on-premises access<!-- 4092920 -->  
We've updated the console where you [configure access Microsoft Exchange on-premises access](../protect/conditional-access-exchange-create.md). All of the configurations for Exchange on-premises access are now available on the same pane of the console where you *Enable Exchange on-premises access control*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Allow or restrict adding app widgets to the home screen on Android Enterprise work profile devices<!-- 1109650  --> 
On Android Enterprise devices, you can configure features in the work profile (**Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Work profile only > Device restrictions** for profile type). In this update, you can allow users to add widgets exposed by work profile apps to the device home screen.

To see the settings you can configure, go to [Android Enterprise device settings to allow or restrict features using Intune](../configuration/device-restrictions-android-for-work.md).

Applies to:
- Android Enterprise work profile

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>New tenants will default away from Android device administrator management<!-- 4869790   -->
Android's device administrator capabilities have been superseded by Android Enterprise. Therefore, we recommend using Android Enterprise for new enrollments instead. In a future update, new tenants will need to complete the following prerequisite steps in Android enrollment to use device administrator management: Go to **Intune** > **Device enrollment** > **Android enrollment** > **Personal and corporate-owned devices with device administration privileges** > **Use device administrator to manage devices**.

Existing tenants will experience no change in their environments.

For more information about Android device administrator in Intune, see [Android device administrator enrollment](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>List of DEP devices associated with a profile<!-- 5012045 idmiss -->
You can now see a paged list of Apple Automated Device Enrollment Program (DEP) devices that are associated with a profile. You can search the list from any page in the list. To see the list, go to **Intune** > **Device enrollment** > **Apple enrollment** > **Enrollment program tokens** > choose a token > **Profiles** > choose a profile > **Assigned devices** (under **Monitor**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>More Android Fully Managed support<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
We've added the following support for Android Fully Managed devices:

- SCEP certificates for fully managed Android are available for cert authentication on devices managed as Device Owner. SCEP certificates are already supported on Work Profile devices.  With SCEP certificates for Device Owner, you will be able to: <!-- 5227935 -->
    - create SCEP profile under DO section of Android Enterprise
    - link SCEP certificates to DO Wi-Fi profile for authentication
    - link SCEP certificates to DO VPN profiles for authentication
    - link SCEP certificates to DO Email profiles for authentication (via AppConfig)
- System apps are supported on Android Enterprise devices. In Intune, add an Android Enterprise system app by selecting **Client apps** > **Apps** > **Add**. In the **App type** list, select **Android Enterprise system app**. For more information, see [Add Android Enterprise system apps to Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- In **Device compliance** > **Android Enterprise** > **Device Owner**, you can create a compliance policy that sets the Google SafetyNet attestation level.   <!-- 4631425 -->
- On Android Enterprise fully managed devices, the mobile threat defense providers is supported. In **Device compliance** > **Android Enterprise** > **Device Owner**, you can choose an acceptable threat level. <!-- 4631440 --> [Android Enterprise settings to mark devices as compliant or not compliant using Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) lists the current settings.
- On Android Enterprise fully managed devices, the Microsoft Launcher app can now be configured via app configuration policies to allow a standardized end-user experience on the fully managed device. The Microsoft Launcher app can be used to personalize your Android device. Using the app along with a Microsoft account or work/school account, you can access your calendar, documents, and recent activities in your personalized feed. <!-- 5334044 -->

With this update we are happy to announce that Intune support for Android Enterprise Fully Managed is now generally available.

Applies to:

- Android Enterprise fully managed devices

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Send custom notifications to a single device<!-- 4928910 -->
You can now select a single device, and then use a remote device action to [send a custom notification to only that device](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Wipe and Passcode Reset actions aren't available for iOS devices that are enrolled by using User Enrollment<!-- 4950491 -->
User Enrollment is a new type of Apple device enrollment. When you enroll devices using User Enrollment, the Wipe and Passcode Reset remote actions won't be available for such devices.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune support for iOS 13 and macOS Catalina devices<!-- 4665317 -->
Intune now supports managing both iOS 13 and macOS Catalina devices.
For more information see the [Microsoft Intune Support for iOS 13 and iPadOS blog post](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>BitLocker support for client-driven recovery password rotation<!--  3444125 -->
Use Intune Endpoint Protection settings to configure [Client-driven recovery password rotation](../protect/endpoint-protection-windows-10.md#windows-encryption) for BitLocker on devices that run Windows version 1909 or later.

This setting initiates a client-driven recovery password refresh after an OS drive recovery (either by using bootmgr or WinRE) and recovery password unlock on a Fixed data drive. This setting refreshes the specific recovery password that was used, and other unused passwords on the volume remain unchanged. For more information see the BitLocker CSP documentation for [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Tamper Protection for Windows Defender Antivirus<!-- 4705448        -->
Use Intune to manage *Tamper Protection* for Windows Defender Antivirus. You’ll find the [setting for Tamper Protection](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) in the Microsoft Defender Security Center group when you use device configuration profiles for Windows 10 endpoint protection. You can set Tamper Protection to *Enabled* to turn on Temper Protection restrictions, set *Disabled* to turn them off, or set*Not configured* to leave a devices current configuration in place.  

For more information about Tamper Protection, see [Prevent security settings changes with tamper protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) in the Windows documentation.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Advanced settings for Windows Defender Firewall are now generally available<!--  5317392       -->  
The [Windows Defender custom firewall rules for endpoint protection](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), which you configure as part of a device configuration profile, are out of public preview and are generally available (GA).  You can use these rules to specify inbound and outbound behavior to applications, network addresses, and ports. These rules were released in July as a public preview. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>Scope tags now support Terms of Use policies<!-- 2358863 idmiss -->
You can now assign [scope tags](scope-tags.md) to Terms of Use policies. To do so, go to **Intune** > **Device enrollment** > **Terms and conditions** > choose an item in the list > **Properties** > **Scope tags** > choose a scope tag.

## <a name="week-of-september-9-2019"></a>Week of September 9, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Updates to Microsoft Intune app<!-- 4997846 -->
The Microsoft Intune app for Android has been updated with the following improvements:
- Updated and improved the layout to include bottom navigation for the most important actions.
- Added an additional page that shows the user's profile.
- Added the display of actionable notifications in the app for the user, such as the need to update their device settings.
- Added the display of custom push notifications, aligning the app with the support recently added in the Company Portal app for iOS and Android. For more information, see [Send custom notifications in Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>For iOS devices, customize the enrollment process privacy screen of the Company Portal<!-- 4394993 -->
Using Markdown, you can customize the Company Portal's privacy screen that end users see during iOS enrollment. Specifically, you'll be able to customize the list of things that your organization can't see or do on the device. For more information, see [How to configure the Intune Company Portal app](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Week of September 2, 2019

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune user interface update – Tenant Status dashboard<!-- 5273210  -->
The user interface for the Tenant Status dashboard has been updated to align with Azure user interface styles. For more information, see  [Tenant status](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Week of August 26, 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Configure Microsoft Edge settings using administrative templates for Windows 10 and newer<!-- 5228061 -->

On Windows 10 and newer devices, you can create administrative templates to configure group policy settings in Intune. In this update, you can configure settings that apply to Microsoft Edge version 77 and newer.

To learn more about administrative templates, see [Use Windows 10 templates to configure group policy settings in Intune](../configuration/administrative-templates-windows.md).

Applies to:

- Windows 10 and newer (Windows RS4+)

## <a name="week-of-august-12-2019"></a>Week of August 12, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Control iOS app uninstall behavior at device unenrollment<!-- 3504144   -->
Admins can manage whether an app is removed or retained on a device when the device is unenrolled at a user or device group level. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Categorize Microsoft Store for Business apps<!-- 3926922 -->
You can categorize Microsoft Store for Business apps. To do so, choose **Intune** > **Client apps** > **Apps** > Select a Microsoft Store for Business app > **App Information** > **Category**. On the drop-down menu, assign a category.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Customized notifications for Microsoft Intune app users<!-- 4843354  -->
The Microsoft Intune app for Android now supports the display of custom push notifications, aligning it with the support recently added in the Company Portal apps for iOS and Android. For more information, see [Send custom notifications in Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>New features for Android Enterprise dedicated devices in multi-app mode<!-- 3755304 3041943 3041946   -->

In Intune, you can control features and settings in a kiosk-style experience on your Android Enterprise dedicated devices (**Device configuration** > **Profiles** > **Create profile** > **Android Enterprise** for platform > **Device Owner only, Device restrictions** for profile type).

In this update, the following features are being added:

- **Dedicated devices** > **Multi-app**: The **Virtual home button** can be shown by swiping up on the device, or floating on the screen so users can move it.
- **Dedicated devices** > **Multi-app**: **Flashlight access** allows users to use the flashlight. 
- **Dedicated devices** > **Multi-app**: **Media volume control** allows users to control the device's media volume using a slider. 
- **Dedicated devices** > **Multi-app**:  **Enable a screensaver**, upload a custom image, and control when the screensaver is shown.

To see the current settings, go to [Android Enterprise device settings to allow or restrict features using Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Applies to:

- Android Enterprise dedicated devices

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>New app and configuration profiles for Android Enterprise fully managed devices<!-- 3574215 3574238 3574235 3574232   -->
Using profiles, you can configure settings that apply VPN, email, and Wi-Fi settings to your Android Enterprise device owner (fully managed) devices. In this update, you can:

- Use [app configuration policies](../apps/app-configuration-policies-use-android.md) to deploy Outlook, Gmail, and Nine Work email settings.
- Use device configuration profiles to deploy [trusted root certificate settings](../protect/certificates-configure.md).
- Use device configuration profiles to deploy [VPN](../configuration/vpn-settings-android-enterprise.md) and [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) settings.

> [!IMPORTANT]
> With this feature, users authenticate with their username and password for VPN, Wi-Fi, and e-mail profiles. Currently, certificate-based authentication isn't available.

Applies to:  
- Android Enterprise device owner (fully managed)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Control the apps, files, documents, and folders that open when users sign in to macOS devices<!--3914202   -->
You can enable and configure features on macOS devices (**Device configuration** > **Profiles** > **Create profile** > **macOS** for platform > **Device features** for profile type). 

In this update, there's a new Login Items setting to control which apps, files, documents, and folders open when a user signs in to the enrolled device. 

To see the current settings, go to [macOS device feature settings in Intune](../configuration/macos-device-features-settings.md).

Applies to:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Deadlines replace Engaged restart settings for Windows Update rings<!-- 4464404        -->
To align with recent [Windows servicing changes](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), Intune's Windows 10 Update rings now [support settings for deadlines](../protect/windows-update-settings.md). *Deadlines* determine when a device installs feature and security updates.  On devices that run Windows 10 1903 or later, *deadlines* supersede configurations for *engaged restart*.  In the future, *deadlines* will supersede *engaged restart* on earlier versions of Windows 10 as well.  

When you don’t’ configure *deadlines*, devices continue to use their *engaged restart* settings, however Intune will deprecate support for engaged restart settings in a future update.  

Plan to use *deadlines* for all your Windows 10 devices. After settings for *deadlines* are in place, you can change your Intune configurations for *engaged restart* to be Not configured. When set to Not configured, Intune stops managing those settings on devices but doesn’t remove the last configurations for the setting from the device. Therefore, the last configurations that were set for *engaged restart* remain active and in use on devices until those settings are modified by a method other than Intune. Later, when the devices version of Windows changes or when Intune support for *deadlines* expands to the devices Windows version, the device will begin to use the new settings, which are already in place.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Support for multiple Microsoft Intune Certificate Connectors<!--   4704642      -->
Intune now supports install and use of multiple [Microsoft Intune Certificate Connectors for PKCS operations](../protect/certficates-pfx-configure.md). This change supports load balancing and high availability of the connector. Each connector instance can process certificate requests from Intune.  If one connector is unavailable, other connectors continue to process requests.

To use multiple connectors, you don’t need to upgrade to the latest version of the connector software.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>New settings, and changes to existing settings to restrict features on iOS and macOS devices<!-- 4867699 4867709   -->
You can create profiles to restrict settings on devices running iOS and macOS (**Device configuration** > **Profiles** > **Create profile** > **iOS** or **macOS** for platform type > **Device restrictions**). This update includes the following features:

- On **macOS** > **Device restrictions** > **Cloud and storage**, use the new **Handoff** setting to block users from starting work on one macOS device, and continue working on another macOS or iOS device.

  To see the current settings, go to [macOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-macos.md).

- On **iOS** > **Device restrictions**, there are a few changes:

  - **Built-in apps** > **Find my iPhone (supervised only)** : New setting that blocks this feature in the Find My app feature. 
  - **Built-in apps** > **Find my Friends (supervised only)** : New setting that blocks this feature in the Find My app feature. 
  - **Wireless** > **Modification of Wi-Fi state (supervised only)** : New setting that prevents users from turning on or turning off Wi-Fi on the device.
  - **Keyboard and Dictionary** > **QuickPath (supervised only)** : New setting that blocks the QuickPath feature.
  - **Cloud and storage**: **Activity continuation** is renamed to **Handoff**.

  To see the current settings, go to [iOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-ios.md).

Applies to:  
- macOS 10.15 and newer
- iOS 13 and newer

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Some unsupervised iOS device restrictions will become supervised-only with the iOS 13.0 release<!-- 4867809   -->
In this update, some settings apply to supervised-only devices with the iOS 13.0 release. If these settings are configured and assigned to unsupervised devices prior to the iOS 13.0 release, the settings are still applied to those unsupervised devices. They also still apply after the devices upgrade to iOS 13.0. These restrictions are removed on unsupervised devices that are backed up and restored.

These settings include:

- App Store, Visualização de Documentos, Jogos
  - Loja de aplicações
  - Explicit iTunes, music, podcast, or news content
  - Adding Game Center friends
  - Multiplayer gaming
- Aplicações Incorporadas
  - Câmara
    - FaceTime
  - Safari
    - Autofill
- Cloud e Armazenamento
  - Backup to iCloud
  - Block iCloud Document sync
  - Block iCloud Keychain sync

To see the current settings, go to [iOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-ios.md).

Applies to:  
- iOS 13.0 and newer

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Improved device status for macOS FileVault encryption<!-- 4944983         -->
We've updated several of the [device status messages](../protect/encryption-monitor.md#device-encryption-status) for FileVault encryption on macOS devices.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Some Windows Defender Antivirus scan settings in the reporting show a Failed status<!-- 5119229 -->
In Intune, you can create policies to use Windows Defender Antivirus to scan your Windows 10 devices (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Device restrictions** for profile type > **Windows Defender Antivirus**). The **Time to perform a daily quick scan** and **Type of system scan to perform** reporting shows a failed status, when it’s actually a success status. 

In this update, this behavior is fixed. So, the **Time to perform a daily quick scan** and **Type of system scan to perform** settings shows a success status when the scans complete successfully, and show a failed status when the settings fail to apply.

For more information on the Windows Defender Antivirus settings, see [Windows 10 (and newer) device settings to allow or restrict features using Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="default-scope-tags---3702875----"></a>Default scope tags<!-- 3702875  -->
A new built-in default scope tag is now available. All un-tagged Intune objects that support scope tags are automatically assigned to the default scope tag. The **Default** scope tag is added to all existing role assignments to maintain parity with the admin experience today. If you don't want an admin to see Intune objects with the default scope tag, remove the default scope tag from the role assignment. This feature is similar to the security scopes feature in System Center Configuration Manager. For more information, see [Use RBAC and scope tags to for distributed IT](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android enrollment device administrator support<!-- 4869749   -->
The Android device administrator enrollment option has been added to the Android enrollment page (**Intune** > **Device enrollment** > **Android enrollment**). Android device administrator will still be enabled by default for all tenants.  For more information, see [Android device administrator enrollment](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Skip more screens in Setup Assistant <!--4877451  -->
You can set Device Enrollment Program profiles to skip the following Setup Assistant screens:
- Para iOS
    - Appearance
    - Express Language
    - Preferred Language
    - Device to Device Migration
- For macOS
    - Screen Time
    - Touch ID Setup

For more information about Setup Assistant customization, see [Create an Apple enrollment profile for iOS ](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) and [Create an Apple enrollment profile for macOS ](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Add a user column to the Autopilot device CSV upload process<!-- 3823054 -->
You can now add a user column to the CSV upload for Autopilot devices. This lets you bulk assign users at the time you import the CSV. For more information, see [Enroll Windows devices in Intune by using the Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Configure automatic device clean-up time limit down to 30 days<!--4231059  -->
You can set the automatic device clean-up time limit as short as 30 days (instead of previous limit of 90 days) after the last sign-in. To do so, go to **Intune** > **Devices** > **Setup** > **Device Clean Up Rules**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Build number included on Android device Hardware page<!-- 4461910   -->
A new entry on the Hardware page for each Android device includes the device's operating system build number. For more information, see [View device details in Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Week of August 5, 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies is a supported OEM for OEMConfig on Android Enterprise devices<!-- 4843713 -->

In Intune, you can create device configuration profiles, and apply settings to Android Enterprise devices using OEMConfig (**Device configuration** > **Profiles** > **Create profile** > **Android enterprise** for platform > **OEMConfig** for profile type).

In this update, Zebra Technologies is a supported original equipment manufacturer (OEM) for OEMConfig. For more information on OEMConfig, see [Use and manage Android Enterprise devices with OEMConfig](../configuration/android-oem-configuration-overview.md).

Applies to:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Week of July 22, 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Customized notifications for users and groups<!-- 16766574          -->
Send custom push notifications from the Company Portal application to users on iOS and Android devices that you manage with Intune. These mobile push notifications are highly customizable with free text and can be used for any purpose. You can target them to different user groups in your organization. For more information, see [custom notifications](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Google's Device Policy Controller app<!-- 3041950  -->
The Managed Home Screen app now provides access to Google's Android Device Policy app. The Managed Home Screen app is a custom launcher used for devices enrolled in Intune as Android Enterprise (AE) dedicated devices using multi-app kiosk mode. You can access the Android Device Policy app, or guide users to the Android Device Policy app, for support and debug purposes. This launching capability is available at the time the device enrolls and locks into Managed Home Screen. No additional installations are needed to use this functionality.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Outlook protection settings for iOS and Android devices<!-- 3212619 -->
You can now configure both general app and data protection configuration settings for Outlook for iOS and Android using simple Intune admin controls without device enrollment. The general app config settings provide parity with the settings administrators can enable when managing Outlook for iOS and Android on enrolled devices. For more information about Outlook settings, see [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Use "applicability rules" when creating Windows 10 device configuration profiles <!-- 2549910 eeready   idstaged -->

You create Windows 10 device configuration profiles (**Device configuration** > **Profiles** > **Create profile** > **Windows 10** for platform > **Applicability rules**). In this update, you can create an **applicability rule** so the profile only applies to a specific edition or specific version. For example, you create a profile that enables some BitLocker settings. Once you add the profile, use an applicability rule so the profile only applies to devices running Windows 10 Enterprise.

To add an applicability rule, see [Applicability rules](../configuration/device-profile-create.md#applicability-rules).

Aplica-se a: Windows 10 e posterior

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Use tokens to add device-specific information in custom profiles for iOS and macOS devices<!-- 3330008  -->
You can use custom profiles on iOS and macOS devices to configure settings and features not built in to Intune (**Device configuration** > **Profiles** > **Create profile** > **iOS** or **macOS** for platform > **Custom** for profile type). In this update, you can add tokens to your `.mobileconfig` files to add device-specific information. For example, you can add `Serial Number: {{serialnumber}}` to your configuration file to show the serial number of the device.

To create a custom profile, see [iOS custom settings](../configuration/custom-settings-ios.md) or [macOS custom settings](../configuration/custom-settings-macos.md).

Applies to:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>New configuration designer when creating an OEMConfig profile for Android Enterprise<!-- 3712769   -->
In Intune, you can create a device configuration profile that uses an OEMConfig app (Device Configuration > Profiles > Create profile > Android enterprise for platform > OEMConfig for profile type). When you do this, a JSON editor opens with a template and values for you to change. 

This update includes a Configuration Designer with an improved user experience that shows details embedded in the app, including titles, descriptions, and more. The JSON editor is still available, and shows any changes you make in the Configuration Designer.

To see the current settings, go to [Use and manage Android Enterprise devices with OEMConfig](../configuration/android-oem-configuration-overview.md).

Applies to: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Updated UI for configuring Windows Hello<!-- 4089576            -->
We've updated the console where you [configure Intune to use Windows Hello for Business](../protect/windows-hello.md). All of the configuration settings are now available on the same pane of the console where you enable support for Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
The Intune PowerShell SDK, which provides support for the Intune API through Microsoft Graph, has been updated to version 6.1907.1.0. The SDK now supports the following:
- Works with Azure Automation.
- Supports app-only auth read operations. 
- Supports friendly shortened names as aliases.
- Conforms to PowerShell naming conventions. Specifically, the `PSCredential` parameter (on the `Connect-MSGraph` cmdlet) has been renamed to `Credential`.
- Supports manually specifying the value of the `Content-Type` header when using the `Invoke-MSGraphRequest` cmdlet.

For more information, see [PowerShell SDK for Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Updates for Enrollment Restrictions<!-- 2871968 -->
Enrollment Restrictions for new tenants have been updated so that Android Enterprise work profiles are allowed by default. Existing tenants will experience no change. To use Android Enterprise work profiles, you still need to [connect your Intune account to your Managed Google Play account](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>UI updates for Apple enrollment and enrollment restrictions<!--4089575, 4089579  -->
Both of the following processes use a wizard-style user interface:
- Apple device enrollment. For more information, see [Automatically enroll iOS devices with Apple's Device Enrollment Program](../enrollment/device-enrollment-program-enroll-ios.md).
- Enrollment restriction creation. For more information, see [Set enrollment restrictions](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Handling pre-configuration of corporate device identifiers for Android Q devices<!-- 4711509  idmiss -->
In Android Q (v10), Google will remove the ability for MDM agents on legacy-managed (device administrator) Android devices to collect device identifier information.  Intune has a feature that enables IT admins to [pre-configure a list of device serial numbers or IMEIs](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) in order to automatically tag these devices as corporate-owned. This feature won't work for Android Q devices that are device admin-managed.  Regardless of whether the serial number or IMEI for the device is uploaded, it will always be considered to be personal during Intune enrollment.  You can manually switch ownership to corporate after enrollment.  This affects new enrollments only, and existing enrolled devices are not affected.  Android devices managed with work profiles are not affected by this change and will continue working as they do today.  Additionally, Android Q devices enrolled as device administrator will no longer be able to report serial number or IMEI in the Intune console as device properties.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Icons have changed for Android Enterprise enrollments (work profile, dedicated devices, and fully managed devices)<!-- 4977730 -->
The icons for Android Enterprise enrollment profiles have changed. To see the new icons, go to **Intune** > **Enrollment** > **Android enrollment** > look under **Enrollment profiles**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Windows Diagnostic Data collection change<!-- 4113859 -->
The default value for diagnostic data collection has changed for devices running Windows 10, version 1903 and later. Starting with Windows 10 1903, diagnostic data collection is enabled by default. Windows diagnostic data is vital technical data from Windows devices about the device and how Windows and related software are performing. For more information, see [Configure Windows diagnostic data in your organization](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Autopilot devices are also opted into “Full” telemetry unless otherwise set in the Autopilot profile with [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="improve-device-location---3855417----"></a>Improve device location<!-- 3855417  -->
You can zoom in to the exact coordinates of a device using the **Locate device** action. For more information about locating lost iOS devices, see [Find lost iOS devices](../remote-actions/device-locate.md).

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Advanced settings for Windows Defender Firewall  (public preview)<!--  1311949     -->  
Use Intune to manage [custom firewall rules as part of a device configuration profile](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) for endpoint protection on Windows 10. Rules can specify inbound and outbound behavior to applications, network addresses, and ports. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Updated UI for managing security baselines<!-- 4091125     -->
We've updated the [create and edit experience](../protect/security-baselines.md#create-the-profile) in the Intune console for our security baselines. Changes include:

A simpler wizard-style format that's been condensed to a single blade. within one blade. This new design does away with blade sprawl that requires IT Pros to drill down into several separate panes.  
You can now create Assignments as part of the create and edit experience, instead of having to return later to assign baselines. We've added a summarization of settings you can view prior to creating a new baseline and when editing an existing one. When editing, the summary only shows the list of items set within the one category of properties being edited.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Week of July 15, 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Managed Home Screen and Managed Settings icons<!-- 4918107 -->
The Managed Home Screen app icon and the **Managed Settings** icon have been updated. The Managed Home Screen app is only used by devices enrolled in Intune as Android Enterprise (AE) dedicated devices and running in multi-app kiosk mode. For more information about the Managed Home Screen app, see [Configure the Microsoft Managed Home Screen app for Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Device Policy on Android Enterprise dedicated devices<!-- 4918136 -->
You can access the Android Device Policy application from the Managed Home Screen app's debug screen. The Managed Home Screen app is only used by devices enrolled in Intune as Android Enterprise (AE) dedicated devices and running in multi-app kiosk mode. For more information, see [Configure the Microsoft Managed Home Screen app for Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>iOS Company Portal updates<!-- 3902931 -->
Your company name on iOS app management prompts will replace the current "i.manage.microsoft.com" text. For instance, users will see their company name instead of "i.manage.microsoft.com" when users attempt to install an iOS app from the Company Portal or when users allow management of the app. This will be rolled out to all customers over the next few days.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Manage FileVault for macOS<!--  3858502 + 4557986 + 1210104  -->
You can use Intune to [manage FileVault key encryption for macOS devices](../protect/encrypt-devices.md). To encrypt devices, you use an endpoint protection device configuration profile.

Our support for FileVault includes encrypting unencrypted devices, escrow of a devices personal recovery key, automatic or manual rotation of personal encryption keys, and key retrieval for your corporate devices. End users can also use the Company Portal website to get the personal recovery key for their encrypted devices.

We've also expanded the encryption report to include [information about FileVault](../protect/encryption-monitor.md) along-side information for BitLocker, so you can view all your device encryption details in one place.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows Autopilot reset removes the device's primary user<!-- 4156123 -->
When Autopilot reset is used on a device, the device's primary user will be removed. The next user who signs in after the reset will be set as the primary user. This feature will be rolled out to all customers over the next few days.

## <a name="week-of-july-8-2019"></a>Week of July 8, 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>New Office, Windows, and OneDrive settings in Windows 10 administrative templates <!-- 3510695 -->

You can create Administrative templates in Intune that mimic on-premises group policy management (**Device management** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Administrative template** for profile type).

This update includes more Office, Windows, and OneDrive settings you can add to your templates. With these new settings, you can now configure over 2500 settings that are 100% cloud-based.

To learn more about this feature, see [Use Windows 10 templates to configure group policy settings in Intune](../configuration/administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

## <a name="week-of-july-1-2019"></a>Week of July 1, 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD and APP on Android Enterprise devices<!-- 3574267 -->
When onboarding fully managed Android Enterprise devices, users will now register with Azure Active Directory (AAD) during the initial setup of their new or factory reset device. Previously for a fully managed device, after setup was complete, the user had to manually launch the Microsoft Intune app to start AAD registration. Now when the user lands on the device home page after initial setup, the device is both enrolled and registered.

In addition to the AAD updates, Intune app protection policies (APP) are now supported on fully managed Android Enterprise devices. This functionality will become available as we roll it out. For more information, see [Add Managed Google Play apps to Android Enterprise devices with Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Week of June 24, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Configure which browser is allowed to link to organization data<!-- 3145939 -->
Intune App Protection Policies (APP) on Android and iOS devices now allow you to transfer Org web links to a specific browser beyond the Intune Managed Browser or Microsoft Edge.  For more about APP, see [What are app protection policies?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>All apps page identifies online/offline Microsoft Store for Business apps<!--4089647 -->
The **All apps** page now includes labeling to identify Microsoft Store for Business (MSFB) apps as online or offline apps. Each MSFB app now includes a suffix for **Online** or **Offline**. The app details page also includes **License Type** and **Supports device context installation** (offline licensed  apps only) information.

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Company Portal app on Windows shared devices<!--4393553 -->
Users can now access the Company Portal app on Windows shared devices. End users will see a **Shared** label on the device tile. This applies to the Windows Company Portal app version 10.3.45609.0 and later.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>View all installed apps from new Company Portal web page<!-- 4224326 -->
The Company Portal website's new **Installed Apps** page lists all managed apps (both required and available) that are installed on a user's devices. In addition to assignment type, users can see the app's publisher, date published, and current installation status. If you haven't made any apps required or available to your users, they'll see a message explaining that no company apps have been installed. To see the new page on the web, go to the [Company Portal website](https://portal.manage.microsoft.com) and click **Installed Apps**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>New view lets app users see all managed apps installed on device<!-- 2352913 -->  
The Company Portal app for Windows now lists all managed apps (both required and available) that are installed on a user's device. Users can also see attempted and pending app installations, and their current statuses. If you haven't made apps required or available to your users, they'll see a message explaining that no company apps have been installed. To see the new view, go to the Company Portal navigation pane and select **Apps** > **Installed Apps**.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Configure settings for kernel extensions on macOS devices<!-- 2043024 -->
On macOS devices, you can create a device configuration profile (**Device configuration** > **Profiles** > **Create profile** > choose **macOS** for platform). This update includes a new group of settings that let you configure and use kernel extensions on your devices. You can add specific extensions, or allow all extensions from a specific partner or developer.

To learn more about this feature, see [kernel extensions overview](../configuration/kernel-extensions-overview-macos.md) and [kernel extension settings](../configuration/kernel-extensions-settings-macos.md).

Applies to: macOS 10.13.2 and later

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Apps from the store only setting for Windows 10 devices includes more configuration options<!-- 2697002 -->
When you create a device restrictions profile for Windows devices, you can use the **Apps from the store only** setting so users only install apps from the Windows App Store (**Device configuration** > **Profiles** > **Create profile** > **Windows 10 and later** for platform > **Device restrictions** for profile type). In this update, this setting is expanded to support more options.

To see the new setting, go to [Windows 10 (and newer) device settings to allow or restrict features](../configuration/device-restrictions-windows-10.md#app-store).

Aplica-se a: Windows 10 e posterior

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Deploy multiple Zebra mobility extensions device profiles to a device, same user group, or same devices group<!-- 4089955 -->
In Intune, you can use Zebra mobility extensions (MX) in a device configuration profile to customize settings for Zebra devices that aren't built into Intune. Currently, you can deploy one profile to a single device. In this update, you can deploy multiple profiles to:
- The same user group
- The same devices group
- A single device

[Use and manage Zebra devices with Zebra Mobility Extensions in Microsoft Intune](../configuration/android-zebra-mx-overview.md) shows how to use MX in Intune.

Applies to: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Some kiosk settings on iOS devices are set using "Block", replacing "Allow"<!-- 4404075  -->
When you create a device restrictions profile on iOS devices (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **Kiosk**), you set the **Auto lock**, **Ringer switch**, **Screen rotation**, **Screen sleep button**, and **Volume buttons**.

In this update, the values are **Block** (blocks the feature) and **Not configured** (allows the feature). To see the settings, go to [iOS device settings to allow or restrict features](../configuration/device-restrictions-ios.md#kiosk).

Aplica-se a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Use Face ID for password authentication on iOS devices<!-- 4490704 -->
When you create a device restrictions profile for iOS devices, you can use a fingerprint for a password. In this update, the fingerprint password settings also allow facial recognition (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **Password**). As a result, the following settings changed:

- **Fingerprint unlock** is now **Touch ID and Face ID unlock**.
- **Fingerprint modification (supervised only)** is now **Touch ID and Face ID modification (supervised only)** .

Face ID is available in iOS 11.0 and later. To see the settings, go to [iOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-ios.md#password).

Aplica-se a: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Restricting gaming and app store features on iOS devices is now dependent on ratings region<!-- 4593948 -->
On iOS devices, you can allow or restrict features related to gaming, the app store, and viewing documents (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **App Store, Doc Viewing, Gaming**). You can also choose the Ratings region, such as the United States.

In this update, the **Apps** feature is moved to be a child to **Ratings region**, and is dependent on **Ratings region**. To see the settings, go to [iOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Windows Autopilot support for Hybrid Azure AD Join<!-- 4809146-->
Windows Autopilot for existing devices now supports Hybrid Azure AD Join (in addition to the existing Azure AD Join support). Applies to Windows 10 version 1809 and above devices. For more information, see [ Windows Autopilot for existing devices](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>See the security patch level for Android devices<!-- 4461911 -->
You can now see the security patch level for Android devices. To do so, choose **Intune** > **Devices** > **All devices** > choose a device > **Hardware**.
The patch level is listed in the **Operating System** section.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Assign scope tags to all managed devices in a security group<!-- 3173810 -->
You can now assign scope tags to a security group and all devices in the security group will also be associated with those scope tags. All devices in these groups will also be assigned the scope tag. The scope tags set with this feature will overwrite the scope tags set with the current device scope tags flow. For more information, see [Use RBAC and scope tags for distributed IT](scope-tags.md).

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="use-keyword-search-with-security-baselines------"></a>Use keyword search with Security Baselines<!--  -->
When you create or edit [Security Baseline profiles](../protect/security-baselines.md#create-the-profile), you can specify keywords in the new *Search* bar to filter the available groups of settings to those that contain your search criteria.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>The Security Baselines feature is now generally available<!-- 3785395 -->
The **Security Baselines** feature is out of preview and is now generally available (GA).  This means the feature is ready for use in production. However, the individual baseline templates can remain in preview and are evaluated and released to GA on their own schedules.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>The MDM Security Baseline template is now generally available<!-- 3794072, 4217151,  3534649 -->
The MDM Security Baseline template has moved out of preview and is now generally available (GA). The GA template is identified as **MDM Security Baseline for May 2019**.  This is a new template and not an upgrade from the preview version.  As a new template, you’ll need to review the [settings it contains](../protect/security-baseline-settings-mdm.md), and then create new profiles to deploy the template to your device. Other security baseline templates can remain in preview. For a list of available baselines, see [Available security baselines](../protect/security-baselines.md#available-security-baselines).  

In addition to being a new template, the *MDM Security Baseline for May 2019* template includes the two settings that we recently announced in our In Development article:  
- Above Lock: Voice activate apps from a locked screen  
- DeviceGuard: Use virtualization-based security (VBS) at the next reboot of devices.  

The *MDM Security Baseline for May 2019* also includes the addition of several new settings, the removal of others, and a revision of the default value of one setting. For a detailed list of the changes from Preview to GA, see **What’s changed in the new template**.

#### <a name="security-baseline-versioning---3194322---"></a>Security baseline versioning<!-- 3194322 -->
Security baselines for Intune support versioning. With this support, as new versions of each security baseline are released, you can update your existing security baseline profiles to use the newer baseline version without having to recreate and deploy a new baseline from scratch. Additionally, in the Intune console you can view information about each baseline like the number of individual profiles you have that use the baseline, how many of the different baseline versions your profiles use, and when the latest release of a specific security baseline was.  For more information, see **Security Baselines**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>The Use security keys for sign-in setting has moved<!-- 4501151 -->
The device configuration setting for identity protection named **Use security keys for sign-in** is no longer found as a sub-setting of *Configure Windows Hello for Business*. It's now a top-level setting that is always available, even when you don't enable use of Windows Hello for Business. For more information, see [Identity protection](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>New permissions for assigned group admins<!-- 4504437   -->
Intune's built-in School Administrator role now has create, read, update, and delete (CRUD) permissions for Managed Apps. This update means that if you're assigned as a group admin in Intune for Education, you can now create, view, update, and delete the iOS MDM Push Certificate, iOS MDM server tokens, and iOS VPP tokens along with [all of the existing permissions you have](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). To take any of these actions, go to **Tenant settings** > **iOS Device Management**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Applications can use the Graph API to call read operations without user credentials<!-- 4655885 -->
Applications can call Intune Graph API read operations with app identity without user credentials. For more information about accessing the Microsoft Graph API for Intune, see [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Apply scope tags to Microsoft Store for Business apps<!-- 4392555 -->
You can now apply scope tags to Microsoft Store for Business apps. For more information about scope tags, see [Use role-based access control (RBAC) and scope tags for distributed IT](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Week of June 17, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-features-in-microsoft-intune-app"></a>New features in Microsoft Intune app
We’ve added new features to the Microsoft Intune app (preview) for Android. Users on fully managed Android devices can now:  

* View and manage the devices they've enrolled through the Intune Company Portal or Microsoft Intune app.
* Contact their organization for support.
* Send their feedback to Microsoft.
* View terms and conditions, if set by their organization.

## <a name="week-of-june-10-2019"></a>Week of June 10, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>New sample apps showing Intune SDK integration available on GitHub<!-- 2653471 -->
The msintuneappsdk GitHub account has added new sample applications for iOS (Swift), Android, Xamarin.iOS, Xamarin Forms, and Xamarin.Android. These apps are meant to supplement our existing documentation and provide demonstrations of how to integrate the Intune APP SDK into your own mobile apps. If you are an app developer that needs additional Intune SDK guidance, see the following linked samples:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - A native iOS (Swift) instant messaging app that uses the Azure Active Directory Authentication Library (ADAL) for brokered authentication.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - A native Android todo list app that uses ADAL for brokered authentication.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - A Xamarin.Android todo list app that uses ADAL for brokered authentication, this repository also has the Xamarin.Forms app.
- [Xamarin.iOS sample app](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - A barebones Xamarin.iOS sample app.

## <a name="week-of-may-27-2019"></a>Week of May 27, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Reporting for potentially harmful apps on Android devices<!-- 4223162 -->
Intune now provides additional reporting information about potentially harmful apps on Android devices. 

## <a name="week-of-may-20-2019"></a>Week of May 20, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="windows-company-portal-app---3316993---"></a>Aplicação do Portal da Empresa do Windows<!-- 3316993 -->
The Windows Company Portal app will now have a new page labeled **Devices**. The **Devices** page will show end users all of their enrolled devices. Users will see this change in the Company Portal when they use version 10.3.4291.0 and later. For information about the configuring the Company Portal, see [How to configure the Microsoft Intune Company Portal app](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot device OrderID attribute name changed to Group Tag <!-- 4659453 -->

To make it more intuitive, the **OrderID** attribute name on Autopilot devices has been changed to **Group Tag**. When using CSVs to upload Autopilot device information, you must use Group Tag as the column header, not OrderID.  

## <a name="week-of-may-13-2019"></a>Week of May 13, 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Intune policies update authentication method and Company Portal app installation<!-- 1927359  -->
On devices already enrolled via Setup Assistant through one of Apple’s corporate device enrollment methods, Intune will no longer support the Company Portal when it is manually installed by end users from the app store. This change is only relevant when you authenticate with Apple Setup Assistant during enrollment. This change also only affects iOS devices enrolled through:  
* Apple configurator

* Apple Business Manager

* Gestor Escolar da Apple

* Apple Device Enrollment Program (DEP)

If users install the Company Portal app from the App store, and then try to enroll these devices through it, they will receive an error. These devices will be expected to only use the Company Portal when it's been pushed, automatically, by Intune during enrollment. Enrollment profiles in Intune in the Azure portal will be updated so that you can specify how devices authenticate and if they receive the Company Portal app. If you want your DEP device users to have the Company Portal, you will need to specify your preferences in an enrollment profile. 

In addition, the **Identify your device** screen in the iOS Company Portal is being removed. Therefore, admins who want to enable Conditional Access or deploy company apps must update the DEP enrollment profile. This requirement only applies if the DEP enrollment is authenticated with Setup Assistant. In that case, you must push the Company Portal onto the device. To do so, choose **Intune** > **Device enrollment** > **Apple enrollment** > **Enrollment program tokens** > choose a token > **Profiles** > choose a profile > **Properties** > set **Install Company Portal** to **Yes**.

To install the Company Portal on already-enrolled DEP devices, you will need to go to Intune > Client apps, and push it as a managed app with app configuration policies. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Configure how end users update a line-of-business (LOB) app using an app protection policy<!-- 3568384 -->
You can now configure where your end users can get an updated version of a line-of-business (LOB) app. End users will see this feature in the **min app version** conditional launch dialog, which will prompt end users to update to a minimum version of the LOB app. You must provide these update details as part of your LOB app protection policy (APP). This feature is available on iOS and Android. On iOS, this feature requires the app to be integrated (or wrapped using the wrapping tool) with the Intune SDK for iOS v. 10.0.7 or above. On Android, this feature would require the latest Company Portal. To configure how an end user updates a LOB app, the app needs a managed app configuration policy sent to it with the key, `com.microsoft.intune.myappstore`. The value sent will define which store the end user will download the app from. If the app is deployed via the Company Portal, the value must be `CompanyPortal`. For any other store, you must enter a complete URL.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune management extension PowerShell scripts<!-- 3734186  -->
You can configure PowerShell scripts to run with the user’s admin privileges on the device. For more information, see [Use PowerShell scripts on Windows 10 devices in Intune](../apps/intune-management-extension.md) and [Win32 app management](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Android Enterprise app management<!-- 4459905 -->
To make it easier for IT admins to configure and use Android Enterprise management, Intune will automatically add four common Android Enterprise related apps to the Intune admin console. The four Android Enterprise apps are the following apps:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Used for Android Enterprise fully managed scenarios.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Helps you sign in to your accounts if you use two-factor verification.
- **[Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Used for App Protection Policies (APP) and Android Enterprise work profile scenarios.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Used for Android Enterprise dedicated/kiosk scenarios.

Previously, IT admins would need to manually find and approve these apps in the [Managed Google Play store](https://play.google.com/store/apps) as part of setup. This change removes those previously manual steps to make it easier and faster for customers to use Android Enterprise management.

Admins will see these four apps automatically added to their Intune apps list at the time that they first connect their Intune tenant to managed Google Play. For more information, see [Connect your Intune account to your Managed Google Play account](../enrollment/connect-intune-android-enterprise.md). For tenants that have already connected their tenant or who already use Android Enterprise, there is nothing admins need to do. Those four apps will automatically show up within 7 days of the completion of the May 2019 service rollout.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Updated PFX Certificate Connector for Microsoft Intune<!-- 1533038 -->
We’ve released an update for the [PFX Certificate Connector for Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) that addresses an issue where existing PFX certificates continue to be reprocessed, which causes the connector to stop processing new requests.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Intune security tasks for Defender ATP (In public preview)<!-- 3208597 -->
In public preview, you can use Intune to manage [security tasks for Microsoft Defender Advanced Threat Protection (ATP)](../protect/atp-manage-vulnerabilities.md). This integration with ATP and adds a risk-based approach to discover, prioritize, and remediate endpoint vulnerabilities and misconfigurations, while reducing the time between discovery to mitigation.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Check for a TPM chipset in a Windows 10 device compliance policy<!-- 3617671   idstaged-->
Many Windows 10 and later devices have Trusted Platform Module (TPM) chipsets. This update includes a new compliance setting that checks the TPM chip version on the device.

[Windows 10 and later compliance policy settings](../protect/compliance-policy-create-windows.md#device-security) describes this setting.

Aplica-se a: Windows 10 e posterior

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Prevent end users from modifying their Personal HotSpot and disable Siri server logging on iOS devices<!-- 4097904   -->  
You create a device restrictions profile on iOS device (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type). This update includes new settings you can configure:

- **Built-in Apps**: Server-side logging for Siri commands
- **Wireless**: User modification of Personal Hotspot (supervised only)

To see these settings, go to [built-in app settings for iOS](../configuration/device-restrictions-ios.md#built-in-apps) and [wireless settings for iOS](../configuration/device-restrictions-ios.md#wireless).

Applies to: iOS 12.2 and newer

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>New classroom app device restriction settings for macOS devices<!-- 4097905   --> 
You can create device configuration profiles for macOS devices (**Device configuration** > **Profiles** > **Create profile** > **macOS** for platform > **Device restrictions** for profile type). This update includes new classroom app settings, the option to block screenshots, and the option to disable the iCloud Photo Library.

To see the current settings, go to [macOS device settings to allow or restrict features using Intune](../configuration/device-restrictions-macos.md).

Applies to: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>The iOS Password to access app store setting is renamed<!-- 4557891  -->
The **Password to access app store** setting is renamed to **Require iTunes Store password for all purchases** (**Device configuration** > **Profiles** > **Create profile** > **iOS** for platform > **Device restrictions** for profile type > **App store, Doc viewing, and Gaming**).

To see the available settings, go to [App Store, Doc Viewing, Gaming iOS settings](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender Advanced Threat Protection  baseline  (Preview)<!--  3754134 -->
We've added a security baseline Preview for [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md) settings. This baseline is available when your environment meets the prerequisites for using [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows Enrollment Status Page (ESP) is now generally available<!-- 3605348 -->
The Enrollment Status Page is now out of preview. For more information, see [Set up an enrollment status page](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune user interface update - Autopilot enrollment profile creation<!-- 4593669 -->
The user interface for creating an Autopilot enrollment profile has been updated to align with Azure user interface styles. For more information, see [Create an Autopilot enrollment profile](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Moving forward, additional Intune scenarios will be updated to this new UI style.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Enable Autopilot Reset for all Windows devices<!-- 4225665 -->
Autopilot Reset now works for all Windows devices, even those not configured to use the Enrollment Status Page. If an enrollment status page wasn't configured for the device during initial device enrollment, the device will go straight to the desktop after sign-in. It might take up to eight hours to sync and appear compliant in Intune. For more information, see [Reset devices with remote Windows Autopilot Reset](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Exact IMEI format not required when searching All devices<!--30407680 -->
You won't need to include spaces in IMEI numbers when you search **All devices**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Deleting a device in the Apple portal will be reflected in the Intune portal<!--2489996 -->
If a device is deleted from Apple's Device Enrollment Program or Apple Business Manager portals, the device will automatically be deleted from Intune during the next sync.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>The Enrollment Status Page now tracks Win32 apps<!-- 2714451 -->
This only applies to devices running Windows 10 version 1903 and above. For more information, see [Set up an enrollment status page](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Reset and wipe devices in bulk by using the Graph API<!-- 3295288 -->
You can now reset and wipe up to 100 devices in bulk using the Graph API.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>The Encryption report is out of Public Preview<!-- 4587546      -->
The [report for BitLocker and device encryption](../protect/encryption-monitor.md) is now generally available, and no longer part of the public preview.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Outlook signature and biometric settings for  iOS and Android devices<!-- 4050557 -->
You can now specify if the default signature is enabled in Outlook on iOS and Android devices. Additionally, you can choose to allow users to change the biometric setting in Outlook on iOS.

## <a name="week-of-may-6-2019"></a>Week of May 6, 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Network Access Control (NAC) support for F5 Access for iOS devices<!-- 4500808 -->

F5 released an update to BIG-IP 13 that allows NAC functionality for F5 Access on iOS in Intune. To use this feature:

- Update BIG-IP to 13.1.1.5 refresh. BIG-IP 14 isn't supported.
- Integrate BIG-IP with Intune for NAC. Steps in [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Check the **Enable Network Access Control (NAC)** setting in the VPN profile in Intune.

To see the available setting, go to [Configure VPN settings on iOS devices](../configuration/vpn-settings-ios.md).

Aplica-se a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Updated PFX Certificate Connector for Microsoft Intune<!-- doc-vso 1521237  -->  
We’ve released an update for the [PFX Certificate Connector for Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) that drops the polling interval from 5 minutes to 30 seconds.




## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
