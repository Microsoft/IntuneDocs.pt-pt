---
title: Encrypt devices with the platforms supported encryption method
titleSuffix: Microsoft Intune
description: Encrypt devices with built-in encryption methods like BitLocker or FileVault, and manage the recovery keys for those encrypted devices from within the Intune portal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 13d6a2b9cdc8596c7f5cf81218377754e9412be1
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390310"
---
# <a name="use-device-encryption-with-intune"></a>Use device Encryption with Intune

Use Intune to manage a devices built-in disk or drive encryption to protect data on your devices.

Configure disk encryption as part of a device configuration profile for endpoint protection. The following platforms and encryption technologies are supported by Intune:

- macOS: FileVault
- Windows 10 and later: BitLocker

Intune also provides a built-in [encryption report](encryption-monitor.md) that presents details about the encryption status of devices, across all your managed devices.

## <a name="filevault-encryption-for-macos"></a>FileVault encryption for macOS

Use Intune to configure FileVault disk encryption on devices that run macOS. Then, use the Intune encryption report to view encryption details for those devices and to manage recovery keys for FileVault encrypted devices.

FileVault is a whole-disk encryption program that is included with macOS. You can use Intune to configure FileVault on devices that run **macOS 10.13 or later**.

To configure FileVault, create a [device configuration profile](../configuration/device-profile-create.md) for endpoint protection for the macOS platform. FileVault settings are one of the available settings categories for macOS endpoint protection.

After you create a policy to encrypt devices with FileVault, the policy is applied to devices in two stages. First, the device is prepared to enable Intune to retrieve and back up the recovery key. This is referred to as escrow. After the key is escrowed, the disk encryption can start.

![FileVault settings](./media/encrypt-devices/filevault-settings.png)

For details about the FileVault setting you can manage with Intune, see [FileVault](endpoint-protection-macos.md#filevault) in the Intune article for macOS endpoint protection settings.

### <a name="how-to-configure-macos-filevault"></a>How to configure macOS FileVault

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Configuration profiles** > **Create profile**.

3. Set the following options:

   - Platform: macOS
   - Profile type: Endpoint protection

4. Select **Settings** > **FileVault**.

5. For *FileVault*, select **Enable**.

6. For *Recovery key type*, only **Personal key** is supported.

   Consider adding a message to help guide end-users on how to retrieve the recovery key for their device. This information can be useful for your end-users when you use the setting for Personal recovery key rotation, which can automatically generate a new recovery key for a device periodically.

   For example: To retrieve a lost or recently rotated recovery key, sign in to the Intune Company Portal website from any device. In the portal, go to *Devices* and select the device that has FileVault enabled, and then select *Get recovery key*. The current recovery key is displayed.

7. Configure the remaining [FileVault settings](endpoint-protection-macos.md#filevault) to meet your business needs, and then select **OK**.

   > [!IMPORTANT]
   > There is a known issue when the setting **Disable prompt at sign out** is set to *Enable*. When set to *Enable*, the setting for **Number of times allowed to bypass** must be set to a value and must not be set as *Not configured*. If set to *Not configured*, the profile fails on the device. In this scenario the device reports it's **Profile State Summary** as **Error** with no further details.
   >
   > When **Disable prompt at sign out** is set to *Not configured*, **Number of times allowed to bypass** can be *Not configured* or have a value.
   >
   > This issue will be resolved in a future update.

8. Complete configuration of additional settings, and then save the profile.  

### <a name="manage-filevault"></a>Manage FileVault

After Intune encrypts a macOS device with FileVault, you can view and manage the FileVault recovery keys when you view the Intune [encryption report](encryption-monitor.md).

After Intune encrypts a macOS device with FileVault, you can view that device's personal recovery key from the web Company Portal on any device. Once in the web Company Portal, choose the encrypted macOS device, and then choose to "Get recovery key" as a remote device action.

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker encryption for Windows 10

Use Intune to configure BitLocker Drive Encryption on devices that run Windows 10. Then, use the Intune encryption report to view encryption details for those devices. You can also access important information for BitLocker from your devices, as found in Azure Active Directory (Azure AD).

BitLocker is available on devices that run **Windows 10 or later**.

Configure BitLocker when you create a [device configuration profile](../configuration/device-profile-create.md) for endpoint protection for the Windows 10 or later platform. BitLocker settings are in the Windows Encryption settings category for Windows 10 endpoint protection.

![BitLocker settings](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>How to configure Windows 10 BitLocker

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Configuration profiles** > **Create profile**.

3. Set the following options:

   - Platform: Windows 10 and later
   - Profile type: Endpoint protection

4. Select **Settings** > **Windows Encryption**.

5. Configure settings for BitLocker to meet your business needs, and then select **OK**.

6. Complete configuration of additional settings, and then save the profile.

### <a name="manage-bitlocker"></a>Manage BitLocker

After Intune encrypts a Windows 10 device with BitLocker, you can view and retrieve BitLocker recovery keys when you view the Intune [encryption report](encryption-monitor.md).

### <a name="rotate-bitlocker-recovery-keys"></a>Rotate BitLocker recovery keys

You can use an Intune device action to remotely rotate the BitLocker recovery key of a device that runs Windows 10 version 1909 or later.

#### <a name="prerequisites"></a>Pré-requisitos

Devices must meet the following prerequisites to support rotation of the BitLocker recovery key:

- Devices must run Windows 10 version 1909 or later

- Azure AD-joined and Hybrid-joined devices must have support for key rotation enabled:

  - **Client-driven recovery password rotation**

  This setting is found under *Windows Encryption* as part of a device configuration policy for Windows 10 Endpoint Protection.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>To rotate the BitLocker recovery key

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **Todos os dispositivos**.

3. In the list of devices that you manage, select a device, select **More**, and then select the **BitLocker key rotation** device remote action.

## <a name="next-steps"></a>Próximos passos

Create [a device compliance](compliance-policy-create-windows.md) policy.

Use the encryption report, to manage:

- [BitLocker recovery keys](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault recovery keys](encryption-monitor.md#filevault-recovery-keys)

Review the encryption settings you can configure with Intune for:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
