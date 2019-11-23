---
title: Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou configure um perfil de configuração de dispositivos no Microsoft Intune. Select the platform type, configure the settings, add a scope tag.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c4c995322234a4a2486d8e6c5e9efd88f78dd63
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390876"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

Os perfis de dispositivo permitem-lhe adicionar e configurar definições e, em seguida, enviar essas definições para dispositivos na sua organização. Veja [Aplicar definições e funcionalidades aos dispositivos com perfis de dispositivo](device-profiles.md) para obter mais detalhes, incluindo o que pode fazer.

Este artigo:

- Apresenta os passos para criar um perfil.
- Mostra-lhe como adicionar uma etiqueta de âmbito para “filtrar” o perfil.
- Describes applicability rules on Windows 10 devices, and shows you how to create a rule.
- Apresenta os tempos de ciclos de atualização de entrada quando os dispositivos recebem perfis e atualizações de perfis.

## <a name="create-the-profile"></a>Criar o perfil

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Configuration profiles**. You have the following options:

    - **Overview**: Lists the status of your profiles, and provides additional details on the profiles you assigned to users and devices.
    - **Manage**: Create device profiles, upload custom [PowerShell scripts](../apps/intune-management-extension.md) to run within the profile, and add data plans to devices using [eSIM](esim-device-configuration.md).
    - **Monitor**: Check the status of a profile for success or failure, and also view logs on your profiles.
    - **Setup**: Add a SCEP or PFX certificate authority, or enable [Telecom Expense Management](telecom-expenses-monitor.md) in the profile.

3. Select **Create profile**. Introduza as seguintes propriedades:

   - **Name**: Enter a descriptive name for the profile. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é **Perfil de e-mail WP para toda a empresa**.
   - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Platform**: Choose the platform of your devices. As opções são:  

       - **Android**
       - **Android Enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

   - **Profile type**: Select the type of settings you want to create. A lista apresentada depende da **plataforma** que escolher.
   - **Settings**: The following articles describe the settings for each profile type:

       - [Modelos administrativos](administrative-templates-windows.md)
       - [Personalizar](../custom-settings-configure.md)
       - [Otimização da entrega](../delivery-optimization-windows.md)
       - [Funcionalidades do dispositivo](../device-features-configure.md)
       - [Restrições de dispositivos](device-restrictions-configure.md)
       - [Atualização da edição e alteração do modo ](edition-upgrade-configure-windows-10.md)
       - [Educação](education-settings-configure.md)
       - [Email](email-settings-configure.md)
       - [Proteção de ponto final](../protect/endpoint-protection-configure.md)
       - [Proteção de identidade](../protect/identity-protection-configure.md)  
       - [Modo de Quiosque](kiosk-settings.md)
       - [Certificado PKCS](../protect/certficates-pfx-configure.md)
       - [PKCS imported certificate](../protect/certificates-imported-pfx-configure.md)
       - [Preference file](preference-file-settings-macos.md)
       - [Certificado SCEP](../protect/certificates-scep-configure.md)
       - [Certificado fidedigno](../protect/certificates-configure.md)
       - [Políticas de atualização](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     For example, if you select **iOS/iPadOS** for the platform, your profile type options look similar to the following profile:

     ![Criar um perfil iOS no Intune](./media/device-profile-create/create-device-profile.png)

4. Quando terminar, selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e apresentado na lista.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

Depois de adicionar as definições, também pode adicionar uma etiqueta de âmbito ao perfil. As etiquetas de âmbito são uma ótima forma de atribuir e filtrar políticas para grupos específicos, tais como RH ou Todos os funcionários dos EUA.

Para obter mais informações sobre etiquetas de âmbito e o que pode fazer, veja [Utilizar RBAC e etiquetas de âmbito para TI distribuídas](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Adicionar etiqueta de âmbito

1. Selecionar **Âmbito (Etiquetas)** .
2. Selecione **Adicionar** para criar uma nova etiqueta de âmbito. Em alternativa, selecione uma etiqueta de âmbito existente na lista.
3. Selecione **OK** para guardar as alterações.

## <a name="applicability-rules"></a>Applicability rules

Applies to:

- Windows 10 e posterior

Applicability rules allow administrators to target devices in a group that meet specific criteria. For example, you create a device restrictions profile that applies to the **All Windows 10 devices** group. And, you only want the profile assigned to devices running Windows 10 Enterprise.

To do this task, create an **applicability rule**. These rules are great for the following scenarios:

- You use Windows 10 Education (EDU). At Bellows College, you want to target all Windows 10 EDU devices between RS3 and RS4.
- You want to target all users in Human Resources at Contoso, but only want Windows 10 Professional or Enterprise devices.

To approach these scenarios, you:

- Create a devices group that includes all devices at Bellows College. In the profile, add an applicability rule so it applies if the OS minimum version is `16299` and the maximum version is `17134`. Assign this profile to the Bellows College devices group.

  When it's assigned, the profile applies to devices between the minimum and maximum versions you enter. For devices that aren't between the minimum and maximum versions you enter, their status shows as **Not applicable**.

- Create a users group that includes all users in Human Resources (HR) at Contoso. In the profile, add an applicability rule so it applies to devices running Windows 10 Professional or Enterprise. Assign this profile to the HR users group.

  When it's assigned, the profile applies to devices running Windows 10 Professional or Enterprise. For devices that aren't running these editions, their status shows as **Not applicable**.

- If there are two profiles with the exact same settings, then the profile without an applicability rule is applied. 

  For example, ProfileA targets the Windows 10 devices group, enables BitLocker, and doesn’t have an applicability rule. ProfileB targets the same Windows 10 devices group, enables BitLocker, and has an applicability rule to only apply the profile to Windows 10 Enterprise.

  When both profiles are assigned, ProfileA is applied because it doesn’t have an applicability rule. 

When you assign the profile to the groups, the applicability rules act as a filter, and only target the devices that meet your criteria.

### <a name="add-a-rule"></a>Add a rule

1. Select **Applicability Rules**. You can choose the **Rule**, **Property**, and **OS edition**:

    ![Add an applicability rule to a device configuration profile in Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. In **Rule**, choose if you want to include or exclude users or groups. As opções são:

    - **Assign profile if**: Includes users or groups that meet the criteria you enter.
    - **Don't assign profile if**: Excludes users or groups that meet the criteria you enter.

3. In **Property**, choose your filter. As opções são: 

    - **OS edition**: In the list, check the Windows 10 editions you want to include (or exclude) in your rule.
    - **OS version**: Enter the **min** and **max** Windows 10 version numbers of you want to include (or exclude) in your rule. Both values are required.

      For example, you can enter `10.0.16299.0` (RS3 or 1709) for minimum version and `10.0.17134.0` (RS4 or 1803) for maximum version. Or, you can be more granular and enter `10.0.16299.001` for minimum version and `10.0.17134.319` for maximum version.

4. Select **Add** to save your changes.

## <a name="refresh-cycle-times"></a>Tempos de ciclos de atualização

Intune uses different refresh cycles to check for updates to configuration profiles. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) lists the estimated refresh times.

Em qualquer altura, os utilizadores podem abrir a aplicação do Portal da Empresa e sincronizar o dispositivo para verificarem imediatamente se existem as atualizações de perfis.

## <a name="recommendations"></a>Recomendações

When creating profiles, consider the following recommendations:

- Name your policies so you know what they are, and what they do. All [compliance policies](../protect/create-compliance-policy.md) and [configuration profiles](../configuration/device-profile-create.md) have an optional **Description** property. In **Description**, be specific and include information so others know what the policy does.

  Some configuration profile examples include:

  **Profile name**: Admin template - OneDrive configuration profile for all Windows 10 users  
  **Profile description**: OneDrive admin template profile that includes the minimum and base settings for all Windows 10 users. Created by user@contoso.com to prevent users from sharing organizational data to personal OneDrive accounts.

  **Profile name**: VPN profile for all iOS users  
  **Profile description**: VPN profile that includes the minimum and base settings for all iOS users to connect to Contoso VPN. Created by user@contoso.com so users automatically authenticate to VPN, instead of prompting users for their username and password.

- Create your profile by its task, such as configure Microsoft Edge settings, enable Microsoft Defender anti-virus settings, block iOS jailbroken devices, and so on.

- Create profiles that apply to specific groups, such as Marketing, Sales, IT Administrators, or by location or school system.

- Separate user policies from device policies.

  For example, [Administrative Templates in Intune](administrative-templates-windows.md) have hundreds of ADMX settings. These template shows if a settings applies to users or devices. When creating admin templates, assign your users settings to a users group, and assign your device settings to a devices group.

  The following image shows an example of a setting that can apply to users and/or apply to devices:

  ![Intune admin template that applies to user and devices](./media/device-profile-create/setting-applies-to-user-and-device.png)

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
