---
title: Add preference file settings to macOS devices in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Add an xml or plist file that includes key information about your app. Use a preference file device configuration profile to change key information in the property list file, and assign it to your macOS devices.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390975"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Add a property list file to macOS devices using Microsoft Intune

Using Microsoft Intune, you can add a property list file (.plist) for macOS devices, or apps on macOS devices.

Esta funcionalidade aplica-se a:

- macOS devices running 10.7 and newer

Property list files typically include information about macOS applications. For more information, see [About Information Property List Files](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (Apple's website) and [Custom payload settings](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

This article lists and describes the different property list file settings you can add to macOS devices. As part of your mobile device management (MDM) solution, use these settings to add the app bundle ID (`com.company.application`), and add its .plist file.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Create the profile](device-profile-create.md).

## <a name="what-you-need-to-know"></a>O que tem de saber

- These settings aren't validated. Be sure to test your changes before assigning the profile to your devices.
- If you’re not sure how to enter an app key, change the setting within the app. Then, review the app's preference file using [Xcode](https://developer.apple.com/xcode/) to see how the setting is configured. Apple recommends removing non-manageable settings using Xcode before importing the file.
- Only some apps work with managed preferences, and might not allow you to manage all settings.
- Be sure you upload property list files that target device channel settings, not user channel settings. Property list files target the entire device.

## <a name="preference-file"></a>Preference file

- **Preference domain name**: Property list files are typically used for web browsers (Microsoft Edge), [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac), and custom apps. When you create a preference domain, a bundle ID is also created. Enter the bundle ID, such as `com.company.application`. For example, enter `com.Contoso.applicationName`, `com.Microsoft.Edge` or `com.microsoft.wdav`.
- **Property list file**: Select the property list file associated with your app. Be sure it's a `.plist` or `.xml` file. For example, upload a `YourApp-Manifest.plist` or `YourApp-Manifest.xml` file.
- **File contents**: The key information in the property list file is shown. If you need to change the key information, open the list file in another editor, and then reupload the file in Intune.

Selecione **OK** > **Criar** para guardar as alterações. The profile is created and shown in the profiles list.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).
