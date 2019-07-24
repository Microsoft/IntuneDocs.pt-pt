---
title: APIs do Graph para configurar dispositivos no Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Consulte uma lista de todas as entidades de API do Graph com o CSP do Windows e o URI de deslocamento correspondentes em dispositivos Windows 10 e mais recentes usados ao configurar dispositivos no Microsoft Intune. Consulte a API de correspondência e o CSP para PCs compartilhados, Endpoint Protection, proteção avançada contra ameaças do Microsoft defender, proteção de identidade, equipes do Windows 10, quiosque e Windows Update para empresas.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9db6be9c61455056f7ad32a9dba3fa6be9f6f5c3
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427273"
---
# <a name="graph-apis-and-matching-windows-10-csps-used-in-intune"></a>APIs de grafo e CSPs correspondentes do Windows 10 usados no Intune

Microsoft Intune usa as [entidades de API do Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview) (abre outro site de documentos) para configurar dispositivos (**configuração de dispositivo**do**Intune** > ) executando o Windows 10 e posterior. O API do Graph usa CSPs (provedores de serviços de configuração) para ler, definir, alterar e/ou excluir definições de configuração em dispositivos.

Esta lista se aplica a:

- Windows 10 e posterior

Este artigo lista as entidades de grafo e seus CSPs e URIs de deslocamento correspondentes do Windows 10.

Essas informações são úteis para uma variedade de cenários. Por exemplo, consulte o que é usado pelo Intune, consulte configurações para incluir em configurações de OMA-URI personalizadas e assim por diante. 

## <a name="windows-10-csps"></a>Windows 10 CSPs

Para obter mais informações sobre os provedores de serviço de configuração do Windows 10, consulte a [referência do provedor de serviços de configuração](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (abre outro site de documentos).

## <a name="graph-api-properties-to-csp-mapping"></a>API do Graph Propriedades ao mapeamento do CSP

A lista a seguir mostra a maioria das entidades de API do Graph usadas pelo Microsoft Intune para a configuração de dispositivo do Windows 10. Ele também mostra o CSP do Windows 10 correspondente e o URI de deslocamento.

Para ver as versões do Windows 10 as APIs a seguir se aplicam, use a [referência do provedor de serviços de configuração](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) do Windows 10 (abre outro site de documentos).

### <a name="editionupgradeconfigurationlicense"></a>EditionUpgradeConfiguration.License 
**CSP**:./Device/Vendor/MSFT/WindowsLicensing  
**URI de deslocamento**:/UpgradeEditionWithLicense

### <a name="editionupgradeconfigurationlicensetype"></a>EditionUpgradeConfiguration.LicenseType 
**CSP**:./Device/Vendor/MSFT/WindowsLicensing  
**URI de deslocamento**:/LicenseKeyType

### <a name="editionupgradeconfigurationproductkey"></a>EditionUpgradeConfiguration.ProductKey 
**CSP**:./Device/Vendor/MSFT/WindowsLicensing  
**URI de deslocamento**:/UpgradeEditionWithProductKey

### <a name="editionupgradeconfigurationwindowssmode"></a>EditionUpgradeConfiguration.WindowsSMode 
**CSP**:./Device/Vendor/MSFT/WindowsLicensing  
**URI de deslocamento**:/SMode/SwitchingPolicy

### <a name="sharedpcconfigurationaccountmanagerpolicy"></a>SharedPCConfiguration.AccountManagerPolicy 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /DeletionPolicy, /DiskLevelCaching, /InactiveThreshold, /DiskLevelDeletion

### <a name="sharedpcconfigurationaccountmanagerpolicy-windows-holographic-for-business-edition-targeted-devices"></a>SharedPCConfiguration. AccountManagerPolicy (dispositivos Windows Holographic for Business Edition direcionados) 
**CSP**: ./Vendor/MSFT/AccountManagement  
**Offset URI**: /DeletionPolicy, /StorageCapacityStartDeletion, /StorageCapacityStopDeletion, /ProfileInactivityThreshold

### <a name="sharedpcconfigurationallowedaccounts"></a>SharedPCConfiguration.AllowedAccounts 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/AccountModel

### <a name="sharedpcconfigurationallowlocalstorage"></a>SharedPCConfiguration.AllowLocalStorage 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/RestrictLocalStorage

### <a name="sharedpcconfigurationdisableaccountmanager"></a>SharedPCConfiguration.DisableAccountManager 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/EnableAccountManager

### <a name="sharedpcconfigurationdisableedupolicies"></a>SharedPCConfiguration.DisableEduPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/SetEduPolicies

### <a name="sharedpcconfigurationdisablepowerpolicies"></a>SharedPCConfiguration.DisablePowerPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/SetPowerPolicies

### <a name="sharedpcconfigurationdisablesigninonresume"></a>SharedPCConfiguration.DisableSignInOnResume 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/SignInOnResume

### <a name="sharedpcconfigurationenabled"></a>SharedPCConfiguration.Enabled 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/EnableSharedPCMode

### <a name="sharedpcconfigurationidletimebeforesleepinseconds"></a>SharedPCConfiguration.IdleTimeBeforeSleepInSeconds 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/InactiveThreshold

### <a name="sharedpcconfigurationkioskappdisplayname"></a>SharedPCConfiguration.KioskAppDisplayName 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/KioskModeUserTileDisplayText

### <a name="sharedpcconfigurationkioskappusermodelid"></a>SharedPCConfiguration.KioskAppUserModelId 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/KioskModeAUMID

### <a name="sharedpcconfigurationlocalstorage"></a>SharedPCConfiguration.LocalStorage 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/RestrictLocalStorage

### <a name="sharedpcconfigurationmaintenancestarttime"></a>SharedPCConfiguration.MaintenanceStartTime 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/MaintenanceStartTime

### <a name="sharedpcconfigurationsetaccountmanager"></a>SharedPCConfiguration.SetAccountManager
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/EnableAccountManager

### <a name="sharedpcconfigurationsetedupolicies"></a>SharedPCConfiguration.SetEduPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/SetEduPolicies

### <a name="sharedpcconfigurationsetpowerpolicies"></a>SharedPCConfiguration.SetPowerPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/SetPowerPolicies

### <a name="sharedpcconfigurationsigninonresume"></a>SharedPCConfiguration.SignInOnResume 
**CSP**: ./Vendor/MSFT/SharedPC  
**URI de deslocamento**:/SignInOnResume

### <a name="windows10endpointconfigurationsmartscreenblockoverrideforfiles"></a>Windows10endpointconfiguration.smartScreenBlockOverrideForFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/SmartScreen/PreventOverrideForFilesInShell

### <a name="windows10endpointprotectionconfigurationapplicationguardallowfilesaveonhost"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowFileSaveOnHost 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/SaveFilesToHost

### <a name="windows10endpointprotectionconfigurationapplicationguardallowpersistence"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPersistence 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/AllowPersistence

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttolocalprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToLocalPrinters 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttonetworkprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToNetworkPrinters 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttopdf"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToPDF 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttoxps"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToXPS 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/PrintingSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardallowvirtualgpu"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowVirtualGPU 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/AllowVirtualGPU

### <a name="windows10endpointprotectionconfigurationapplicationguardblockclipboardsharing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockClipboardSharing 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/ClipboardSettings

### <a name="windows10endpointprotectionconfigurationapplicationguardblockfiletransfer"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockFileTransfer 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/ClipboardFileType

### <a name="windows10endpointprotectionconfigurationapplicationguardblocknonenterprisecontent"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockNonEnterpriseContent 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/BlockNonEnterpriseContent

### <a name="windows10endpointprotectionconfigurationapplicationguardenabled"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardEnabled 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Settings/AllowWindowsDefenderApplicationGuard

### <a name="windows10endpointprotectionconfigurationapplicationguardforceauditing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardForceAuditing 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**URI de deslocamento**:/Audit/AuditApplicationGuard

### <a name="windows10endpointprotectionconfigurationbitlockerallowstandarduserencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerAllowStandardUserEncryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/AllowStandardUserEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerdisablewarningforotherdiskencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerDisableWarningForOtherDiskEncryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/AllowWarningForOtherDiskEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerenablestoragecardencryptiononmobile"></a>Windows10EndpointProtectionConfiguration.BitLockerEnableStorageCardEncryptionOnMobile 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/RequireStorageCardEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerencryptdevice"></a>Windows10EndpointProtectionConfiguration.BitLockerEncryptDevice 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/RequireDeviceEncryption

### <a name="windows10endpointprotectionconfigurationbitlockerfixeddrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerFixedDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/EncryptionMethodByDriveType,/FixedDrivesRequireEncryption,/FixedDrivesRecoveryOptions

### <a name="windows10endpointprotectionconfigurationbitlockerremovabledrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerRemovableDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/EncryptionMethodByDriveType,/RemovableDrivesRequireEncryption

### <a name="windows10endpointprotectionconfigurationbitlockersystemdrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerSystemDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**URI de deslocamento**:/EncryptionMethodByDriveType,/SystemDrivesRequireStartupAuthentication,/SystemDrivesMinimumPINLength,/SystemDrivesRecoveryMessage,/SystemDrivesRecoveryOptions

### <a name="windows10endpointprotectionconfigurationclientconnectionencryptionlevel"></a>windows10endpointprotectionconfiguration.clientConnectionEncryptionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteDesktopServices/ClientConnectionEncryptionLevel

### <a name="windows10endpointprotectionconfigurationconfiguresmbv1clientdriver"></a>windows10endpointprotectionconfiguration.configureSMBV1ClientDriver 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/ConfigureSMBV1ClientDriver

### <a name="windows10endpointprotectionconfigurationconnectivitydownloadingofprintdriversoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityDownloadingOfPrintDriversOverHttp 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/DisableDownloadingOfPrintDriversOverHTTP

### <a name="windows10endpointprotectionconfigurationconnectivityhardeneduncpaths"></a>Windows10EndpointProtectionConfiguration.ConnectivityHardenedUncPaths 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/HardenedUNCPaths

### <a name="windows10endpointprotectionconfigurationconnectivityinternetdownloadforwebpublishingandonlineorderingwizards"></a>Windows10EndpointProtectionConfiguration.ConnectivityInternetDownloadForWebPublishingAndOnlineOrderingWizards 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/DisableInternetDownloadForWebPublishingAndOnlineOrderingWizards

### <a name="windows10endpointprotectionconfigurationconnectivityprintingoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityPrintingOverHttp 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/DiablePrintingOverHTTP

### <a name="windows10endpointprotectionconfigurationcredentialsuienumerateadministrators"></a>Windows10EndpointProtectionConfiguration.CredentialsUIEnumerateAdministrators 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/CredentialsUI/EnumerateAdministrators

### <a name="windows10endpointprotectionconfigurationdefenderadditionalguardedfolders"></a>Windows10EndpointProtectionConfiguration.DefenderAdditionalGuardedFolders 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/defender/ControlledFolderAccessProtectedFolders

### <a name="windows10endpointprotectionconfigurationdefenderadvancedransomewareprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderAdvancedRansomewareProtectionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderattacksurfacereductionexcludedpaths"></a>Windows10EndpointProtectionConfiguration.DefenderAttackSurfaceReductionExcludedPaths 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionOnlyExclusions

### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecution"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecution 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowEmailScanning

### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecutionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxml"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXml 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/ExploitGuard/ExploitProtectionSettings

### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxmlfilename"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXmlFileName 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ExploitGuard/ExploitProtectionSettings

### <a name="windows10endpointprotectionconfigurationdefenderguardedfoldersallowedapppaths"></a>Windows10EndpointProtectionConfiguration.DefenderGuardedFoldersAllowedAppPaths 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/defender/ControlledFolderAccessAllowedApplications

### <a name="windows10endpointprotectionconfigurationdefenderguardmyfolderstype"></a>Windows10EndpointProtectionConfiguration.DefenderGuardMyFoldersType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/EnableControlledFolderAccess

### <a name="windows10endpointprotectionconfigurationdefendernetworkprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderNetworkProtectionType 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/defender/EnableNetworkProtection

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunch"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunch 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunchtype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunchType
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocess"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcessType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjection"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjectionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType 

### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32imports"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32Imports 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32importstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32ImportsType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderpreventcredentialstealingtype"></a>Windows10EndpointProtectionConfiguration.DefenderPreventCredentialStealingType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderprocesscreation"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreation 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderprocesscreationtype"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreationType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderprotectagainstpotentiallyunwantedapplications"></a>Windows10EndpointProtectionConfiguration.DefenderProtectAgainstPotentiallyUnwantedApplications 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/TurnOnWindowsDefenderProtectionAgainstPotentiallyUnwantedApplications

### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecution"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecution 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecutionType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocode"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocodetype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCodeType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterblockexploitprotectionoverride"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterBlockExploitProtectionOverride 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableaccountui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAccountUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/DisableAccountProtectionUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableappbrowserui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAppBrowserUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/DisableAppBrowserUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablefamilyui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableFamilyUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/DisableFamilyUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablehealthui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableHealthUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/DisableHealthUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablenetworkui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableNetworkUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/DisableNetworkUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablesecurebootui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableSecureBootUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/HideSecureBoot

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisabletroubleshootingui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableTroubleshootingUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/HideTPMTroubleshooting

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablevirusui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableVirusUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/DisableVirusUI

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpemail"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpEmail 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/email

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpphone"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpPhone 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/Phone

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpurl"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpURL 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/URL

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenteritcontactdisplay"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterITContactDisplay 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/WindowsDefenderSecurityCenter/EnableCustomizedToasts,/WindowsDefenderSecurityCenter/EnableInAppCustomization

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenternotificationsfromapp"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterNotificationsFromApp 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/HideWindowsSecurityNotificationAreaControl

### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterorganizationdisplayname"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterOrganizationDisplayName 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsDefenderSecurityCenter/CompanyName

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutable"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutable 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutabletype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutableType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocess"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AttackSurfaceReductionRules

### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcessType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ATTACKSURFACEREDUCTIONRULES (CSP/configuração requer Propriedades de grafo: Windows10endpointprotection/Configuration. defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection/ Configuration. defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration. defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection/ Configuration. defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration. defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration. defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration. defenderEmailContentExecutionType, windows10endpointprotection/Configuration. defenderPreventCredentialStealingType, windows10endpointprotection/ Configuration. defenderUntrustedUSBProcessType

### <a name="windows10endpointprotectionconfigurationdeviceguardenablesecurebootwithdma"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableSecureBootWithDMA 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceGuard/RequirePlatformSecurityFeatures

### <a name="windows10endpointprotectionconfigurationdeviceguardenablevirtualizationbasedsecurity"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableVirtualizationBasedSecurity 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/DeviceGuard/EnableVirtualizationBasedSecurity

### <a name="windows10endpointprotectionconfigurationdeviceguardlaunchsystemguard"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLaunchSystemGuard 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceGuard/ConfigureSystemGuardLaunch

### <a name="windows10endpointprotectionconfigurationdeviceguardlocalsystemauthoritycredentialguardsettings"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLocalSystemAuthorityCredentialGuardSettings 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceGuard/LsaCfgFlags

### <a name="windows10endpointprotectionconfigurationdmaguarddeviceenumerationpolicy"></a>Windows10EndpointProtectionConfiguration.DmaGuardDeviceEnumerationPolicy 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DmaGuard/DeviceEnumerationPolicy

### <a name="windows10endpointprotectionconfigurationeventlogserviceapplicationlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceApplicationLogMaximumFileSizeInKb 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/EventLogService/SpecifyMaximumFileSizeApplicationLog

### <a name="windows10endpointprotectionconfigurationeventlogservicesecuritylogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSecurityLogMaximumFileSizeInKb 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/EventLogService/SpecifyMaximumFileSizeSecurityLog

### <a name="windows10endpointprotectionconfigurationeventlogservicesystemlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSystemLogMaximumFileSizeInKb 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/EventLogService/SpecifyMaximumFileSizeSystemLog

### <a name="windows10endpointprotectionconfigurationexplorerdataexecutionprevention"></a>Windows10EndpointProtectionConfiguration.ExplorerDataExecutionPrevention 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/FileExplorer/TurnOffDataExecutionPreventionForExplorer

### <a name="windows10endpointprotectionconfigurationexplorerheapterminationoncorruption"></a>Windows10EndpointProtectionConfiguration.ExplorerHeapTerminationOnCorruption 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/FileExplorer/TurnOffHeapTerminationOnCorruption

### <a name="windows10endpointprotectionconfigurationfirewallblockstatefulftp"></a>Windows10EndpointProtectionConfiguration.FirewallBlockStatefulFTP 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/DisableStatefulFtp

### <a name="windows10endpointprotectionconfigurationfirewallcertificaterevocationlistcheckmethod"></a>Windows10EndpointProtectionConfiguration.FirewallCertificateRevocationListCheckMethod 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/CRLcheck

### <a name="windows10endpointprotectionconfigurationfirewallidletimeoutforsecurityassociationinseconds"></a>Windows10EndpointProtectionConfiguration.FirewallIdleTimeoutForSecurityAssociationInSeconds 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/SaIdleTime

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowdhcp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowDHCP 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowicmp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowICMP 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowneighbordiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowNeighborDiscovery 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowrouterdiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowRouterDiscovery 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/IPsecExempt

### <a name="windows10endpointprotectionconfigurationfirewallmergekeyingmodulesettings"></a>Windows10EndpointProtectionConfiguration.FirewallMergeKeyingModuleSettings 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/OpportunisticallyMatchAuthSetPerKM

### <a name="windows10endpointprotectionconfigurationfirewallpacketqueueingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPacketQueueingMethod 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/EnablePacketQueue

### <a name="windows10endpointprotectionconfigurationfirewallpresharedkeyencodingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPreSharedKeyEncodingMethod 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/global/PresharedKeyEncoding

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomain"></a>Windows10EndpointProtectionConfiguration.FirewallProfileDomain 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/EnableFirewall,/DisableStealthMode,/shielded,/DisableUnicastResponsesToMulticastBroadcast,/DisableInboundNotifications,/AuthAppsAllowUserPrefMerge,/GlobalPortsAllowUserPrefMerge,/AllowLocalPolicyMerge,/ Outboundaction,/DefaultInboundAction,/DisableStealthModeIpsecSecuredPacketExemption,/AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/domainprofile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/domainprofile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/domainprofile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofiledomainoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.outboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/domainprofile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivate"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePrivate 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/EnableFirewall,/DisableStealthMode,/shielded,/DisableUnicastResponsesToMulticastBroadcast,/DisableInboundNotifications,/AuthAppsAllowUserPrefMerge,/GlobalPortsAllowUserPrefMerge,/AllowLocalPolicyMerge,/ Outboundaction,/DefaultInboundAction,/DisableStealthModeIpsecSecuredPacketExemption,/AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivatefirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.firewallEnabled 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/PrivateProfile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/PrivateProfile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/PrivateProfile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.outboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/PrivateProfile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublic"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePublic 
**CSP**:./Vendor/MSFT/firewall  
**URI de deslocamento**:/EnableFirewall,/DisableStealthMode,/shielded,/DisableUnicastResponsesToMulticastBroadcast,/DisableInboundNotifications,/AuthAppsAllowUserPrefMerge,/GlobalPortsAllowUserPrefMerge,/AllowLocalPolicyMerge,/ Outboundaction,/DefaultInboundAction,/DisableStealthModeIpsecSecuredPacketExemption,/AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicconnectionsecurityrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.connectionSecurityRulesFromGroupPolicyMerged 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/publicprofile/AllowLocalIpsecPolicyMerge

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicfirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.firewallEnabled 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/publicprofile/EnableFirewall

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/publicprofile/DefaultInboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundNotificationsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/publicprofile/DisableInboundNotifications

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.outboundConnectionsBlocked 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/publicprofile/DefaultOutboundAction

### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicpolicyrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.policyRulesFromGroupPolicyMerged 
**CSP**:./Device/Vendor/MSFT/firewall  
**URI de deslocamento**:/MdmStore/publicprofile/AllowLocalPolicyMerge

### <a name="windows10endpointprotectionconfigurationlanmanagerauthenticationlevel"></a>Windows10EndpointProtectionConfiguration.LanManagerAuthenticationLevel 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkSecurity LANManagerAuthenticationLevel

### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationdisableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationDisableInsecureGuestLogons 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/LanmanWorkstation/EnableInsecureGuestLogons

### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationenableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationEnableInsecureGuestLogons 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/LanmanWorkstation/EnableInsecureGuestLogons

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratoraccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorAccountName 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts RenameAdministratorAccount

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratorelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorElevationPromptBehavior
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl BehaviorOfTheElevationPromptForAdministrators

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowanonymousenumerationofsamaccountsandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowAnonymousEnumerationOfSAMAccountsAndShares 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkAccess DoNotAllowAnonymousEnumerationOfSamAccountsAndShares

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowpku2uauthenticationrequests"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowPKU2UAuthenticationRequests 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkSecurity AllowPKU2UAuthenticationRequests

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanager"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkAccess RestrictClientsAllowedToMakeRemoteCallsToSAM

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanagerhelperbool"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManagerHelperBool 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkAccess RestrictClientsAllowedToMakeRemoteCallsToSAM

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowsystemtobeshutdownwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowSystemToBeShutDownWithoutHavingToLogOn 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/Shutdown AllowSystemToBeShutDownWithoutHavingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationElevation 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl AllowUIAccessApplicationsToPromptForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationsforsecurelocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationsForSecureLocations 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowundockwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUndockWithoutHavingToLogon 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/Devices AllowUndockWithoutHavingToLogon

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockmicrosoftaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockMicrosoftAccounts 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts BlockMicrosoftAccounts

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremotelogonwithblankpassword"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteLogonWithBlankPassword 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremoteopticaldriveaccess"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteOpticalDriveAccess 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/Devices RestrictCDROMAccessToLocallyLoggedOnUserOnly

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockusersinstallingprinterdrivers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockUsersInstallingPrinterDrivers 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/Devices PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclearvirtualmemorypagefile"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClearVirtualMemoryPageFile 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/Shutdown ClearVirtualMemoryPageFile

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientDigitallySignCommunicationsAlways 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient DigitallySignCommunicationsAlways

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientsendunencryptedpasswordtothirdpartysmbservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientSendUnencryptedPasswordToThirdPartySMBServers 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient SendUnencryptedPasswordToThirdPartySMBServers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdetectapplicationinstallationsandpromptforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDetectApplicationInstallationsAndPromptForElevation 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl DetectApplicationInstallationsAndPromptForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableAdministratorAccount 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts EnableAdministratorAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableclientdigitallysigncommunicationsifserveragrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableClientDigitallySignCommunicationsIfServerAgrees 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient DigitallySignCommunicationsIfServerAgrees

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableGuestAccount 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts EnableGuestAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsAlways 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer DigitallySignCommunicationsAlways

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsifclientagrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsIfClientAgrees 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer DigitallySignCommunicationsIfClientAgrees

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotallowanonymousenumerationofsamaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotAllowAnonymousEnumerationOfSAMAccounts 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkAccess DoNotAllowAnonymousEnumerationOfSAMAccounts

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotrequirectrlaltdel"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotRequireCtrlAltDel 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon DoNotRequireCTRLALTDEL

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotstorelanmanagerhashvalueonnextpasswordchange"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotStoreLANManagerHashValueOnNextPasswordChange 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkSecurity DoNotStoreLANManagerHashValueOnNextPasswordChange

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableAdministratorAccount 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts EnableAdministratorAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableGuestAccount 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts EnableGuestAccountStatus

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsformatandejectofremovablemediaalloweduser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsFormatAndEjectOfRemovableMediaAllowedUser 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/Devices AllowedToFormatAndEjectRemovableMedia

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsguestaccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsGuestAccountName 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/accounts RenameGuestAccount

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshidelastsignedinuser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideLastSignedInUser 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon DoNotDisplayLastSignedIn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshideusernameatsignin"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideUsernameAtSignIn 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon DoNotDisplayUsernameAtSignIn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationdisplayedonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationDisplayedOnLockScreen 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon DisplayUserInformationWhenTheSessionIsLocked

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationshownonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationShownOnLockScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon DisplayUserInformationWhenTheSessionIsLocked

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetext"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageText 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon MessageTextForUsersAttemptingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetitle"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageTitle 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon MessageTitleForUsersAttemptingToLogOn

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimit"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimit 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon MachineInactivityLimit

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimitinminutes"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimitInMinutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon MachineInactivityLimit

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedclients"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedClients 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkSecurity MinimumSessionSecurityForNTLMSSPBasedClients

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedServers 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkSecurity MinimumSessionSecurityForNTLMSSPBasedServers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsonlyelevatesignedexecutables"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsOnlyElevateSignedExecutables 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl OnlyElevateExecutableFilesThatAreSignedAndValidated

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsrestrictanonymousaccesstonamedpipesandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsRestrictAnonymousAccessToNamedPipesAndShares 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/NetworkAccess RestrictAnonymousAccessToNamedPipesAndShares

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionssmartcardremovalbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSmartCardRemovalBehavior 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/InteractiveLogon SmartCardRemovalBehavior

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsstandarduserelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsStandardUserElevationPromptBehavior 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl BehaviorOfTheElevationPromptForStandardUsers

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsswitchtosecuredesktopwhenpromptingforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSwitchToSecureDesktopWhenPromptingForElevation 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl SwitchToTheSecureDesktopWhenPromptingForElevation

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmode"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl UseAdminApprovalMode

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmodeforadministrators"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalModeForAdministrators 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl RunAllAdministratorsInAdminApprovalMode

### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsvirtualizefileandregistrywritefailurestoperuserlocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsVirtualizeFileAndRegistryWriteFailuresToPerUserLocations 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:\_/config/LocalPoliciesSecurityOptions/userAccountControl VirtualizeFileAndRegistryWriteFailuresToPerUserLocations

### <a name="windows10endpointprotectionconfigurationnetworkicmpredirectsoverrideospfgeneratedroutes"></a>Windows10EndpointProtectionConfiguration.NetworkIcmpRedirectsOverrideOspfGeneratedRoutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSLegacy/AllowICMPRedirectsToOverrideOSPFGeneratedRoutes

### <a name="windows10endpointprotectionconfigurationnetworkignorenetbiosnamereleaserequestsexceptfromwinsservers"></a>Windows10EndpointProtectionConfiguration.NetworkIgnoreNetBiosNameReleaseRequestsExceptFromWinsServers 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSLegacy/AllowTheComputerToIgnoreNetBIOSNameReleaseRequestsExceptFromWINSServers

### <a name="windows10endpointprotectionconfigurationnetworkipsourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpSourceRoutingProtectionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSLegacy/IPSourceRoutingProtectionLevel

### <a name="windows10endpointprotectionconfigurationnetworkipv6sourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpV6SourceRoutingProtectionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSLegacy/IPv6SourceRoutingProtectionLevel

### <a name="windows10endpointprotectionconfigurationpasswordpinlogon"></a>Windows10EndpointProtectionConfiguration.PasswordPinLogOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/CredentialProviders/AllowPINLogon

### <a name="windows10endpointprotectionconfigurationpowershellshellscriptblocklogging"></a>Windows10EndpointProtectionConfiguration.PowerShellShellScriptBlockLogging 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsPowerShell/TurnOnPowerShellScriptBlockLogging

### <a name="windows10endpointprotectionconfigurationremoteassistancesolicitedsetting"></a>Windows10EndpointProtectionConfiguration.RemoteAssistanceSolicitedSetting 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/HardenedUNCPaths

### <a name="windows10endpointprotectionconfigurationremotedesktopservicesclientconnectionencryptionlevel"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesClientConnectionEncryptionLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteDesktopServices/ClientConnectionEncryptionLevel

### <a name="windows10endpointprotectionconfigurationremotedesktopservicesdriveredirection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesDriveRedirection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteDesktopServices/DoNotAllowDriveRedirection

### <a name="windows10endpointprotectionconfigurationremotedesktopservicespasswordsaving"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPasswordSaving 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteDesktopServices/DoNotAllowPasswordSaving

### <a name="windows10endpointprotectionconfigurationremotedesktopservicespromptforpassworduponconnection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPromptForPasswordUponConnection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteDesktopServices/PromptForPasswordUponConnection

### <a name="windows10endpointprotectionconfigurationremotedesktopservicessecurerpccommunication"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesSecureRpcCommunication 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteDesktopServices/RequireSecureRPCCommunication

### <a name="windows10endpointprotectionconfigurationremotehostdelegationofnonexportablecredentials"></a>Windows10EndpointProtectionConfiguration.RemoteHostDelegationOfNonExportableCredentials 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/CredentialsDelegation/RemoteHostAllowsDelegationOfNonExportableCredentials

### <a name="windows10endpointprotectionconfigurationremotemanagementclientbasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientBasicAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_cliente/config/RemoteManagement/AllowBasicAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementclientdigestauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientDigestAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteManagement/DisallowDigestAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementclientunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientUnencryptedTraffic 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_cliente/config/RemoteManagement/AllowUnencryptedTraffic

### <a name="windows10endpointprotectionconfigurationremotemanagementservicebasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceBasicAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_serviço/config/RemoteManagement/AllowBasicAuthentication

### <a name="windows10endpointprotectionconfigurationremotemanagementservicestoringrunascredentials"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceStoringRunAsCredentials 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteManagement/DisallowStoringOfRunAsCredentials

### <a name="windows10endpointprotectionconfigurationremotemanagementserviceunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceUnencryptedTraffic 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:\_serviço/config/RemoteManagement/AllowUnencryptedTraffic

### <a name="windows10endpointprotectionconfigurationrpcunauthenticatedclientoptions"></a>Windows10EndpointProtectionConfiguration.RpcUnauthenticatedClientOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteProcedureCall/RestrictUnauthenticatedRPCClients

### <a name="windows10endpointprotectionconfigurationsecurityguideapplyuacrestrictionstolocalaccountsonnetworklogon"></a>Windows10EndpointProtectionConfiguration.SecurityGuideApplyUacRestrictionsToLocalAccountsOnNetworkLogon 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/ApplyUACRestrictionsToLocalAccountsOnNetworkLogon

### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1clientdriverstartconfiguration"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1ClientDriverStartConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/ConfigureSMBV1ClientDriver

### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1server"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1Server 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/ConfigureSMBV1Server

### <a name="windows10endpointprotectionconfigurationsecurityguidestructuredexceptionhandlingoverwriteprotection"></a>Windows10EndpointProtectionConfiguration.SecurityGuideStructuredExceptionHandlingOverwriteProtection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/EnableStructuredExceptionHandlingOverwriteProtection

### <a name="windows10endpointprotectionconfigurationsecurityguidewdigestauthentication"></a>Windows10EndpointProtectionConfiguration.SecurityGuideWDigestAuthentication 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/MSSecurityGuide/WDigestAuthentication

### <a name="windows10endpointprotectionconfigurationsmartscreenblockoverrideforfiles"></a>Windows10EndpointProtectionConfiguration.SmartScreenBlockOverrideForFiles 
**CSP**:./Device/VENDOR/MSFT/Policy **offset URI**:/config/DeviceGuard/RequirePlatformSecurityFeatures

### <a name="windows10endpointprotectionconfigurationsmartscreenenableinshell"></a>Windows10EndpointProtectionConfiguration.SmartScreenEnableInShell 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/SmartScreen/EnableSmartScreenInShell

### <a name="windows10endpointprotectionconfigurationsolicitedremoteassistance"></a>windows10endpointprotectionconfiguration.solicitedRemoteAssistance 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/RemoteAssistance/SolicitedRemoteAssistance

### <a name="windows10endpointprotectionconfigurationuserrightsaccesscredentialmanagerastrustedcaller"></a>Windows10EndpointProtectionConfiguration.UserRightsAccessCredentialManagerAsTrustedCaller 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/AccessCredentialManagerAsTrustedCaller

### <a name="windows10endpointprotectionconfigurationuserrightsaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/AccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsactaspartoftheoperatingsystem"></a>Windows10EndpointProtectionConfiguration.userRightsActAsPartOfTheOperatingSystem 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ActAsPartOfTheOperatingSystem

### <a name="windows10endpointprotectionconfigurationuserrightsallowaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsAllowAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/AccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsbackupdata"></a>Windows10EndpointProtectionConfiguration.UserRightsBackupData 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/BackupFilesAndDirectories

### <a name="windows10endpointprotectionconfigurationuserrightsblockaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsBlockAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/DenyAccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightschangesystemtime"></a>Windows10EndpointProtectionConfiguration.UserRightsChangeSystemTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ChangeSystemTime

### <a name="windows10endpointprotectionconfigurationuserrightscreateglobalobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateGlobalObjects 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/CreateGlobalObjects

### <a name="windows10endpointprotectionconfigurationuserrightscreatepagefile"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePageFile 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/CreatePageFile

### <a name="windows10endpointprotectionconfigurationuserrightscreatepermanentsharedobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePermanentSharedObjects 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/CreatePermanentSharedObjects

### <a name="windows10endpointprotectionconfigurationuserrightscreatesymboliclinks"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateSymbolicLinks 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/CreateSymbolicLinks

### <a name="windows10endpointprotectionconfigurationuserrightscreatetoken"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateToken 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/CreateToken

### <a name="windows10endpointprotectionconfigurationuserrightsdebugprograms"></a>Windows10EndpointProtectionConfiguration.UserRightsDebugPrograms 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/DebugPrograms

### <a name="windows10endpointprotectionconfigurationuserrightsdelegation"></a>Windows10EndpointProtectionConfiguration.UserRightsDelegation 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/EnableDelegation

### <a name="windows10endpointprotectionconfigurationuserrightsdenyaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsDenyAccessFromNetwork 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/DenyAccessFromNetwork

### <a name="windows10endpointprotectionconfigurationuserrightsgeneratesecurityaudits"></a>Windows10EndpointProtectionConfiguration.UserRightsGenerateSecurityAudits 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/GenerateSecurityAudits

### <a name="windows10endpointprotectionconfigurationuserrightsimpersonateclient"></a>Windows10EndpointProtectionConfiguration.UserRightsImpersonateClient 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ImpersonateClient

### <a name="windows10endpointprotectionconfigurationuserrightsincreaseschedulingpriority"></a>Windows10EndpointProtectionConfiguration.UserRightsIncreaseSchedulingPriority 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/IncreaseSchedulingPriority

### <a name="windows10endpointprotectionconfigurationuserrightsloadunloaddrivers"></a>Windows10EndpointProtectionConfiguration.UserRightsLoadUnloadDrivers 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/LoadUnloadDeviceDrivers

### <a name="windows10endpointprotectionconfigurationuserrightslocallogon"></a>Windows10EndpointProtectionConfiguration.UserRightsLocalLogOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/AllowLocalLogOn

### <a name="windows10endpointprotectionconfigurationuserrightslockmemory"></a>Windows10EndpointProtectionConfiguration.UserRightsLockMemory 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/LockMemory

### <a name="windows10endpointprotectionconfigurationuserrightsmanageauditingandsecuritylogs"></a>Windows10EndpointProtectionConfiguration.UserRightsManageAuditingAndSecurityLogs 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ManageAuditingAndSecurityLog

### <a name="windows10endpointprotectionconfigurationuserrightsmanagevolumes"></a>Windows10EndpointProtectionConfiguration.UserRightsManageVolumes 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ManageVolume

### <a name="windows10endpointprotectionconfigurationuserrightsmodifyfirmwareenvironment"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyFirmwareEnvironment 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ModifyFirmwareEnvironment

### <a name="windows10endpointprotectionconfigurationuserrightsmodifyobjectlabels"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyObjectLabels 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ModifyObjectLabel

### <a name="windows10endpointprotectionconfigurationuserrightsprofilesingleprocess"></a>Windows10EndpointProtectionConfiguration.UserRightsProfileSingleProcess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/ProfileSingleProcess

### <a name="windows10endpointprotectionconfigurationuserrightsregisterprocessasservice"></a>Windows10EndpointProtectionConfiguration.UserRightsRegisterProcessAsService 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/DenyLocalLogOn

### <a name="windows10endpointprotectionconfigurationuserrightsremotedesktopserviceslogon"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteDesktopServicesLogOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/DenyRemoteDesktopServicesLogOn

### <a name="windows10endpointprotectionconfigurationuserrightsremoteshutdown"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteShutdown 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/RemoteShutdown

### <a name="windows10endpointprotectionconfigurationuserrightsrestoredata"></a>Windows10EndpointProtectionConfiguration.UserRightsRestoreData 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/RestoreFilesAndDirectories

### <a name="windows10endpointprotectionconfigurationuserrightstakeownership"></a>Windows10EndpointProtectionConfiguration.UserRightsTakeOwnership 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/UserRights/TakeOwnership

### <a name="windows10endpointprotectionconfigurationwindowsconnectionmanagerconnectiontonondomainnetworks"></a>Windows10EndpointProtectionConfiguration.WindowsConnectionManagerConnectionToNonDomainNetworks 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsConnectionManager/ProhitConnectionToNonDomainNetworksWhenConnectedToDomainAuthenticatedNetwork

### <a name="windows10endpointprotectionconfigurationwindowslogonsigninlastinteractiveuseraftersysteminitiatedrestart"></a>Windows10EndpointProtectionConfiguration.WindowsLogOnSignInLastInteractiveUserAfterSystemInitiatedRestart 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsLogon/SignInLastInteractiveUserAutomaticallyAfterASystemInitiatedRestart

### <a name="windows10endpointprotectionconfigurationxboxservicesaccessorymanagementservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesAccessoryManagementServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxservicesenablexboxgamesavetask"></a>Windows10EndpointProtectionConfiguration.XboxServicesEnableXboxGameSaveTask 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/TaskScheduler/EnableXboxGameSaveTask

### <a name="windows10endpointprotectionconfigurationxboxservicesliveauthmanagerservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveAuthManagerServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxserviceslivegamesaveservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveGameSaveServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**Offset URI**: /Config/SystemServices/XboxServicesLiveGameSaveServiceStartupMode

### <a name="windows10endpointprotectionconfigurationxboxserviceslivenetworkingservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveNetworkingServiceStartupMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode

### <a name="windows10enterprisemodernappmanagementconfigurationuninstallbuiltinapps"></a>Windows10EnterpriseModernAppManagementConfiguration.UninstallBuiltInApps
**CSP**: N/A API do Graph apenas chamar **URI de deslocamento**: N/r API do Graph somente chamada

### <a name="windows10generalconfigurationaccountsblockaddingnonmicrosoftaccountemail"></a>Windows10GeneralConfiguration.AccountsBlockAddingNonMicrosoftAccountEmail 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/accounts/AllowAddingNonMicrosoftAccountsManually

### <a name="windows10generalconfigurationantitheftmodeblocked"></a>Windows10GeneralConfiguration.AntiTheftModeBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Security/AntiTheftMode

### <a name="windows10generalconfigurationappmanagementmsiallowusercontroloverinstall"></a>Windows10GeneralConfiguration.AppManagementMSIAllowUserControlOverInstall 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/MSIAllowUserControlOverInstall

### <a name="windows10generalconfigurationappmanagementmsialwaysinstallwithelevatedprivileges"></a>Windows10GeneralConfiguration.AppManagementMSIAlwaysInstallWithElevatedPrivileges 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges

### <a name="windows10generalconfigurationappsallowtrustedappssideloading"></a>Windows10GeneralConfiguration.AppsAllowTrustedAppsSideloading 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/AllowAllTrustedApps

### <a name="windows10generalconfigurationappsblockwindowsstoreoriginatedapps"></a>Windows10GeneralConfiguration.AppsBlockWindowsStoreOriginatedApps 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/DisableStoreOriginatedApps

### <a name="windows10generalconfigurationappsmicrosoftaccountsoptional"></a>Windows10GeneralConfiguration.AppsMicrosoftAccountsOptional 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/AppRuntime/AllowMicrosoftAccountsToBeOptional

### <a name="windows10generalconfigurationassignedaccessmultimodeprofiles"></a>Windows10GeneralConfiguration.AssignedAccessMultiModeProfiles 
**CSP**: ./Device/Vendor/MSFT/AssignedAccess  
**URI de deslocamento**:/configuração

### <a name="windows10generalconfigurationassignedaccesssinglemodeappusermodelid"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeAppUserModelId 
**CSP**: ./Device/Vendor/MSFT/AssignedAccess  
**URI de deslocamento**:/configuração

### <a name="windows10generalconfigurationassignedaccesssinglemodeusername"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeUserName 
**CSP**: ./Device/Vendor/MSFT/AssignedAccess  
**URI de deslocamento**:/configuração

### <a name="windows10generalconfigurationauthenticationallowfidodevice"></a>Windows10GeneralConfiguration.AuthenticationAllowFIDODevice 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Authentication/AllowFidoDeviceSignon

### <a name="windows10generalconfigurationauthenticationallowsecondarydevice"></a>Windows10GeneralConfiguration.AuthenticationAllowSecondaryDevice 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Authentication/AllowSecondaryAuthenticationDevice

### <a name="windows10generalconfigurationauthenticationpreferredazureadtenantdomainname"></a>Windows10GeneralConfiguration.AuthenticationPreferredAzureADTenantDomainName 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Authentication/PreferredAadTenantDomainName

### <a name="windows10generalconfigurationauthenticationwebsignin"></a>Windows10GeneralConfiguration.AuthenticationWebSignIn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Authentication/EnableWebSignIn

### <a name="windows10generalconfigurationautoplaydefaultautorunbehavior"></a>Windows10GeneralConfiguration.AutoPlayDefaultAutoRunBehavior 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Autoplay/SetDefaultAutoRunBehavior

### <a name="windows10generalconfigurationautoplayfornonvolumedevices"></a>Windows10GeneralConfiguration.AutoPlayForNonVolumeDevices 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Autoplay/DisallowAutoplayForNonVolumeDevices

### <a name="windows10generalconfigurationautoplaymode"></a>Windows10GeneralConfiguration.AutoPlayMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Autoplay/TurnOffAutoPlay

### <a name="windows10generalconfigurationbluetoothallowedservices"></a>Windows10GeneralConfiguration.BluetoothAllowedServices 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Bluetooth/ServicesAllowedList

### <a name="windows10generalconfigurationbluetoothblockadvertising"></a>Windows10GeneralConfiguration.BluetoothBlockAdvertising 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Bluetooth/AllowAdvertising

### <a name="windows10generalconfigurationbluetoothblockdiscoverablemode"></a>Windows10GeneralConfiguration.BluetoothBlockDiscoverableMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Bluetooth/AllowDiscoverableMode

### <a name="windows10generalconfigurationbluetoothblocked"></a>Windows10GeneralConfiguration.BluetoothBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowBluetooth

### <a name="windows10generalconfigurationbluetoothblockprepairing"></a>Windows10GeneralConfiguration.BluetoothBlockPrePairing 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Bluetooth/AllowPrepairing

### <a name="windows10generalconfigurationbluetoothblockpromptedproximalconnections"></a>Windows10GeneralConfiguration.BluetoothBlockPromptedProximalConnections 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Bluetooth/AllowPromptedProximalConnections

### <a name="windows10generalconfigurationbluetoothdevicename"></a>Windows10GeneralConfiguration.BluetoothDeviceName 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Bluetooth/LocalDeviceName

### <a name="windows10generalconfigurationbootstartdriverinitialization"></a>windows10generalconfiguration.bootStartDriverInitialization 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/BootStartDriverInitialization

### <a name="windows10generalconfigurationcamerablocked"></a>Windows10GeneralConfiguration.CameraBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Camera/AllowCamera

### <a name="windows10generalconfigurationcellularblockdatawhenroaming"></a>Windows10GeneralConfiguration.CellularBlockDataWhenRoaming 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowCellularDataRoaming

### <a name="windows10generalconfigurationcellularblockvpn"></a>Windows10GeneralConfiguration.CellularBlockVpn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowVPNOverCellular

### <a name="windows10generalconfigurationcellularblockvpnwhenroaming"></a>Windows10GeneralConfiguration.CellularBlockVpnWhenRoaming 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowVPNRoamingOverCellular

### <a name="windows10generalconfigurationcellulardata"></a>Windows10GeneralConfiguration.CellularData 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowCellularData

### <a name="windows10generalconfigurationcertificatesblockmanualrootcertificateinstallation"></a>Windows10GeneralConfiguration.CertificatesBlockManualRootCertificateInstallation 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Security/AllowManualRootCertificateInstallation

### <a name="windows10generalconfigurationconnecteddevicesserviceblocked"></a>Windows10GeneralConfiguration.ConnectedDevicesServiceBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowConnectedDevices

### <a name="windows10generalconfigurationcopypasteblocked"></a>Windows10GeneralConfiguration.CopyPasteBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowCopyPaste

### <a name="windows10generalconfigurationcortanablocked"></a>Windows10GeneralConfiguration.CortanaBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/AboveLock/AllowCortanaAboveLock

### <a name="windows10generalconfigurationcryptographyallowfipsalgorithmpolicy"></a>Windows10GeneralConfiguration.CryptographyAllowFipsAlgorithmPolicy 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Cryptography/AllowFipsAlgorithmPolicy

### <a name="windows10generalconfigurationdataprotectionblockdirectmemoryaccess"></a>Windows10GeneralConfiguration.DataProtectionBlockDirectMemoryAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/dataprotection/AllowDirectMemoryAccess

### <a name="windows10generalconfigurationdefenderblockenduseraccess"></a>Windows10GeneralConfiguration.DefenderBlockEndUserAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowUserUIAccess

### <a name="windows10generalconfigurationdefenderblockonaccessprotection"></a>Windows10GeneralConfiguration.DefenderBlockOnAccessProtection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowOnAccessProtection

### <a name="windows10generalconfigurationdefendercloudblocklevel"></a>Windows10GeneralConfiguration.DefenderCloudBlockLevel 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/CloudBlockLevel

### <a name="windows10generalconfigurationdefendercloudextendedtimeout"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeout 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/CloudExtendedTimeout

### <a name="windows10generalconfigurationdefendercloudextendedtimeoutinseconds"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeoutInSeconds 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/CloudExtendedTimeout

### <a name="windows10generalconfigurationdefenderdaysbeforedeletingquarantinedmalware"></a>Windows10GeneralConfiguration.DefenderDaysBeforeDeletingQuarantinedMalware 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/DaysToRetainCleanedMalware

### <a name="windows10generalconfigurationdefenderdetectedmalwareactions"></a>Windows10GeneralConfiguration.DefenderDetectedMalwareActions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ThreatSeverityDefaultAction

### <a name="windows10generalconfigurationdefenderfileextensionstoexclude"></a>Windows10GeneralConfiguration.DefenderFileExtensionsToExclude 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ExcludedExtensions

### <a name="windows10generalconfigurationdefenderfilesandfolderstoexclude"></a>Windows10GeneralConfiguration.DefenderFilesAndFoldersToExclude 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ExcludedPaths

### <a name="windows10generalconfigurationdefendermonitorfileactivity"></a>Windows10GeneralConfiguration.DefenderMonitorFileActivity 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowRealtimeMonitoring

### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappaction"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppAction 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/PUAProtection

### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappactionsetting"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppActionSetting 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/PUAProtection

### <a name="windows10generalconfigurationdefenderprocessestoexclude"></a>Windows10GeneralConfiguration.DefenderProcessesToExclude 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ExcludedProcesses

### <a name="windows10generalconfigurationdefenderpromptforsamplesubmission"></a>Windows10GeneralConfiguration.DefenderPromptForSampleSubmission 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/SubmitSamplesConsent

### <a name="windows10generalconfigurationdefenderrequirebehaviormonitoring"></a>Windows10GeneralConfiguration.DefenderRequireBehaviorMonitoring 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowBehaviorMonitoring

### <a name="windows10generalconfigurationdefenderrequirecloudprotection"></a>Windows10GeneralConfiguration.DefenderRequireCloudProtection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowCloudProtection

### <a name="windows10generalconfigurationdefenderrequirenetworkinspectionsystem"></a>Windows10GeneralConfiguration.DefenderRequireNetworkInspectionSystem 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowIntrusionPreventionSystem

### <a name="windows10generalconfigurationdefenderrequirerealtimemonitoring"></a>Windows10GeneralConfiguration.DefenderRequireRealTimeMonitoring 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowRealtimeMonitoring

### <a name="windows10generalconfigurationdefenderscanarchivefiles"></a>Windows10GeneralConfiguration.DefenderScanArchiveFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowArchiveScanning

### <a name="windows10generalconfigurationdefenderscandownloads"></a>Windows10GeneralConfiguration.DefenderScanDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowIOAVProtection

### <a name="windows10generalconfigurationdefenderscanincomingmail"></a>Windows10GeneralConfiguration.DefenderScanIncomingMail 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowScanningNetworkFiles

### <a name="windows10generalconfigurationdefenderscanmappednetworkdrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanMappedNetworkDrivesDuringFullScan 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowFullScanOnMappedNetworkDrives

### <a name="windows10generalconfigurationdefenderscanmaxcpu"></a>Windows10GeneralConfiguration.DefenderScanMaxCpu 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AvgCPULoadFactor

### <a name="windows10generalconfigurationdefenderscannetworkfiles"></a>Windows10GeneralConfiguration.DefenderScanNetworkFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowScanningNetworkFiles

### <a name="windows10generalconfigurationdefenderscanremovabledrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanRemovableDrivesDuringFullScan 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowFullScanRemovableDriveScanning

### <a name="windows10generalconfigurationdefenderscanscriptsloadedininternetexplorer"></a>Windows10GeneralConfiguration.DefenderScanScriptsLoadedInInternetExplorer 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/AllowScriptScanning

### <a name="windows10generalconfigurationdefenderscantype"></a>Windows10GeneralConfiguration.DefenderScanType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ScanParameter

### <a name="windows10generalconfigurationdefenderscheduledquickscantime"></a>Windows10GeneralConfiguration.DefenderScheduledQuickScanTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ScheduleQuickScanTime

### <a name="windows10generalconfigurationdefenderscheduledscantime"></a>Windows10GeneralConfiguration.DefenderScheduledScanTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ScheduleScanTime

### <a name="windows10generalconfigurationdefenderschedulescanday"></a>Windows10GeneralConfiguration.DefenderScheduleScanDay 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ScheduleScanDay

### <a name="windows10generalconfigurationdefendersignatureupdateintervalinhours"></a>Windows10GeneralConfiguration.DefenderSignatureUpdateIntervalInHours 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/SignatureUpdateInterval

### <a name="windows10generalconfigurationdefendersubmitsamplesconsenttype"></a>Windows10GeneralConfiguration.DefenderSubmitSamplesConsentType 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/SubmitSamplesConsent

### <a name="windows10generalconfigurationdefendersystemscanschedule"></a>Windows10GeneralConfiguration.DefenderSystemScanSchedule 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/defender/ScheduleScanDay

### <a name="windows10generalconfigurationdeveloperunlocksetting"></a>Windows10GeneralConfiguration.DeveloperUnlockSetting 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/AllowDeveloperUnlock

### <a name="windows10generalconfigurationdevicemanagementblockfactoryresetonmobile"></a>Windows10GeneralConfiguration.DeviceManagementBlockFactoryResetOnMobile 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/AllowUserToResetPhone

### <a name="windows10generalconfigurationdevicemanagementblockmanualunenroll"></a>Windows10GeneralConfiguration.DeviceManagementBlockManualUnenroll 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowManualMDMUnenrollment

### <a name="windows10generalconfigurationdiagnosticsdatasubmissionmode"></a>Windows10GeneralConfiguration.DiagnosticsDataSubmissionMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/AllowTelemetry

### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedoff"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOff 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/display/TurnOffGdiDPIScalingForApps

### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedon"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/display/TurnOnGdiDPIScalingForApps

### <a name="windows10generalconfigurationedgeallowstartpagesmodification"></a>Windows10GeneralConfiguration.EdgeAllowStartPagesModification 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/HomePages

### <a name="windows10generalconfigurationedgeblockaccesstoaboutflags"></a>Windows10GeneralConfiguration.EdgeBlockAccessToAboutFlags 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventAccessToAboutFlagsInMicrosoftEdge

### <a name="windows10generalconfigurationedgeblockaddressbardropdown"></a>Windows10GeneralConfiguration.EdgeBlockAddressBarDropdown 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowAddressBarDropdown

### <a name="windows10generalconfigurationedgeblockautofill"></a>Windows10GeneralConfiguration.EdgeBlockAutofill 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowAutofill

### <a name="windows10generalconfigurationedgeblockcompatibilitylist"></a>Windows10GeneralConfiguration.EdgeBlockCompatibilityList 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowMicrosoftCompatibilityList

### <a name="windows10generalconfigurationedgeblockdevelopertools"></a>Windows10GeneralConfiguration.EdgeBlockDeveloperTools 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowDeveloperTools

### <a name="windows10generalconfigurationedgeblocked"></a>Windows10GeneralConfiguration.EdgeBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowBrowser

### <a name="windows10generalconfigurationedgeblockeditfavorites"></a>Windows10GeneralConfiguration.EdgeBlockEditFavorites 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/LockdownFavorites

### <a name="windows10generalconfigurationedgeblockextensions"></a>Windows10GeneralConfiguration.EdgeBlockExtensions 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowExtensions

### <a name="windows10generalconfigurationedgeblockfullscreenmode"></a>Windows10GeneralConfiguration.EdgeBlockFullScreenMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowFullScreenMode

### <a name="windows10generalconfigurationedgeblockinprivatebrowsing"></a>Windows10GeneralConfiguration.EdgeBlockInPrivateBrowsing 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowInPrivate

### <a name="windows10generalconfigurationedgeblocklivetiledatacollection"></a>Windows10GeneralConfiguration.EdgeBlockLiveTileDataCollection 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventLiveTileDataCollection

### <a name="windows10generalconfigurationedgeblockpasswordmanager"></a>Windows10GeneralConfiguration.EdgeBlockPasswordManager 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowPasswordManager

### <a name="windows10generalconfigurationedgeblockpopups"></a>Windows10GeneralConfiguration.EdgeBlockPopups 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowPopups

### <a name="windows10generalconfigurationedgeblockprelaunch"></a>Windows10GeneralConfiguration.EdgeBlockPrelaunch 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowPrelaunch

### <a name="windows10generalconfigurationedgeblockprinting"></a>Windows10GeneralConfiguration.EdgeBlockPrinting 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowPrinting

### <a name="windows10generalconfigurationedgeblocksavinghistory"></a>Windows10GeneralConfiguration.EdgeBlockSavingHistory 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowSavingHistory

### <a name="windows10generalconfigurationedgeblocksearchsuggestions"></a>Windows10GeneralConfiguration.EdgeBlockSearchSuggestions 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowSearchSuggestionsinAddressBar

### <a name="windows10generalconfigurationedgeblocksendingdonottrackheader"></a>Windows10GeneralConfiguration.EdgeBlockSendingDoNotTrackHeader 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowDoNotTrack

### <a name="windows10generalconfigurationedgeblocksendingintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeBlockSendingIntranetTrafficToInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SendIntranetTraffictoInternetExplorer

### <a name="windows10generalconfigurationedgeblocksideloadingextensions"></a>Windows10GeneralConfiguration.EdgeBlockSideloadingExtensions 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowSideloadingOfExtensions

### <a name="windows10generalconfigurationedgeblocktabpreloading"></a>Windows10GeneralConfiguration.EdgeBlockTabPreloading 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowTabPreloading

### <a name="windows10generalconfigurationedgeblockwebcontentonnewtabpage"></a>Windows10GeneralConfiguration.EdgeBlockWebContentOnNewTabPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowWebContentOnNewTabPage

### <a name="windows10generalconfigurationedgeclearbrowsingdataonexit"></a>Windows10GeneralConfiguration.EdgeClearBrowsingDataOnExit 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ClearBrowsingDataOnExit

### <a name="windows10generalconfigurationedgecookiepolicy"></a>Windows10GeneralConfiguration.EdgeCookiePolicy 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowCookies

### <a name="windows10generalconfigurationedgedisablefirstrunpage"></a>Windows10GeneralConfiguration.EdgeDisableFirstRunPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventFirstRunPage

### <a name="windows10generalconfigurationedgeenterprisemodesitelistlocation"></a>Windows10GeneralConfiguration.EdgeEnterpriseModeSiteListLocation 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/EnterpriseSiteListServiceUrl

### <a name="windows10generalconfigurationedgefavoritesbarvisibility"></a>Windows10GeneralConfiguration.EdgeFavoritesBarVisibility 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ConfigureFavoritesBar

### <a name="windows10generalconfigurationedgefavoriteslistlocation"></a>Windows10GeneralConfiguration.EdgeFavoritesListLocation 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ProvisionFavorites

### <a name="windows10generalconfigurationedgefirstrunurl"></a>Windows10GeneralConfiguration.EdgeFirstRunUrl 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/FirstRunURL

### <a name="windows10generalconfigurationedgehomebuttonconfiguration"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SetHomeButtonURL

### <a name="windows10generalconfigurationedgehomebuttonconfigurationenabled"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfigurationEnabled 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ConfigureHomeButton

### <a name="windows10generalconfigurationedgehomepageurls"></a>Windows10GeneralConfiguration.EdgeHomepageUrls 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SetHomeButtonURL

### <a name="windows10generalconfigurationedgenewtabpageurl"></a>Windows10GeneralConfiguration.EdgeNewTabPageURL 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SetNewTabPageURL

### <a name="windows10generalconfigurationedgeopenswith"></a>Windows10GeneralConfiguration.EdgeOpensWith 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ConfigureOpenMicrosoftEdgeWith

### <a name="windows10generalconfigurationedgepreventcertificateerroroverride"></a>Windows10GeneralConfiguration.EdgePreventCertificateErrorOverride 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventCertErrorOverrides

### <a name="windows10generalconfigurationedgerequiresmartscreen"></a>Windows10GeneralConfiguration.EdgeRequireSmartScreen 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/AllowSmartScreen

### <a name="windows10generalconfigurationedgesearchengine"></a>Windows10GeneralConfiguration.EdgeSearchEngine 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SetDefaultSearchEngine

### <a name="windows10generalconfigurationedgesendintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeSendIntranetTrafficToInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SendIntranetTraffictoInternetExplorer

### <a name="windows10generalconfigurationedgeshowmessagewhenopeninginternetexplorersites"></a>Windows10GeneralConfiguration.EdgeShowMessageWhenOpeningInternetExplorerSites 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ShowMessageWhenOpeningSitesInInternetExplorer

### <a name="windows10generalconfigurationedgesyncfavoriteswithinternetexplorer"></a>Windows10GeneralConfiguration.EdgeSyncFavoritesWithInternetExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/SyncFavoritesBetweenIEAndMicrosoftEdge

### <a name="windows10generalconfigurationedgetelemetryformicrosoft365analytics"></a>Windows10GeneralConfiguration.EdgeTelemetryForMicrosoft365Analytics 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ConfigureTelemetryForMicrosoft365Analytics

### <a name="windows10generalconfigurationenableautomaticredeployment"></a>Windows10GeneralConfiguration.EnableAutomaticRedeployment 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/CredentialProviders/DisableAutomaticReDeploymentCredentials

### <a name="windows10generalconfigurationenterprisecloudprintdiscoveryendpoint"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryEndPoint 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint

### <a name="windows10generalconfigurationenterprisecloudprintdiscoverymaxlimit"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryMaxLimit 
**CSP**:./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit

### <a name="windows10generalconfigurationenterprisecloudprintmopriadiscoveryresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintMopriaDiscoveryResourceIdentifier 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/EnterpriseCloudPrint/MopriaDiscoveryResourceId

### <a name="windows10generalconfigurationenterprisecloudprintoauthauthority"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthAuthority 
**CSP**:./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

### <a name="windows10generalconfigurationenterprisecloudprintoauthclientidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthClientIdentifier 
**CSP**:./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

### <a name="windows10generalconfigurationenterprisecloudprintresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintResourceIdentifier 
**CSP**:./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrintResourceId

### <a name="windows10generalconfigurationexperienceblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.ExperienceBlockConsumerSpecificFeatures 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsConsumerFeatures

### <a name="windows10generalconfigurationexperienceblockdevicediscovery"></a>Windows10GeneralConfiguration.ExperienceBlockDeviceDiscovery 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowDeviceDiscovery

### <a name="windows10generalconfigurationexperienceblockerrordialogwhennosim"></a>Windows10GeneralConfiguration.ExperienceBlockErrorDialogWhenNoSIM 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowSIMErrorDialogPromptWhenNoSIM

### <a name="windows10generalconfigurationexperienceblocktaskswitcher"></a>Windows10GeneralConfiguration.ExperienceBlockTaskSwitcher 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowTaskSwitcher

### <a name="windows10generalconfigurationexperienceblockwindowsspotlight"></a>Windows10GeneralConfiguration.ExperienceBlockWindowsSpotlight 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsSpotlight

### <a name="windows10generalconfigurationexperiencedonotsyncbrowsersettings"></a>Windows10GeneralConfiguration.ExperienceDoNotSyncBrowserSettings 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/DoNotSyncBrowserSettings

### <a name="windows10generalconfigurationgamedvrblocked"></a>Windows10GeneralConfiguration.GameDvrBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/AllowGameDVR

### <a name="windows10generalconfigurationhardwaredeviceinstallationbydeviceidentifiers"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationByDeviceIdentifiers 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

### <a name="windows10generalconfigurationhardwaredeviceinstallationbysetupclasses"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationBySetupClasses 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

### <a name="windows10generalconfigurationinkworkspaceaccess"></a>Windows10GeneralConfiguration.InkWorkspaceAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsInkWorkspace/AllowWindowsInkWorkspace

### <a name="windows10generalconfigurationinkworkspaceaccessstate"></a>Windows10GeneralConfiguration.InkWorkspaceAccessState 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsInkWorkspace/AllowWindowsInkWorkspace

### <a name="windows10generalconfigurationinkworkspaceblocksuggestedapps"></a>Windows10GeneralConfiguration.InkWorkspaceBlockSuggestedApps 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace

### <a name="windows10generalconfigurationinternetexploreractivexcontrolsinprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerActiveXControlsInProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DoNotAllowActiveXControlsInProtectedMode

### <a name="windows10generalconfigurationinternetexplorerautocomplete"></a>Windows10GeneralConfiguration.InternetExplorerAutoComplete 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/AllowAutoComplete

### <a name="windows10generalconfigurationinternetexplorerblockoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerBlockOutdatedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DoNotBlockOutdatedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarnings"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarnings 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableBypassOfSmartScreenWarnings

### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarningsaboutuncommonfiles"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarningsAboutUncommonFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableBypassOfSmartScreenWarningsAboutUncommonFiles

### <a name="windows10generalconfigurationinternetexplorercertificateaddressmismatchwarning"></a>Windows10GeneralConfiguration.InternetExplorerCertificateAddressMismatchWarning 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/AllowCertificateAddressMismatchWarning

### <a name="windows10generalconfigurationinternetexplorercheckservercertificaterevocation"></a>Windows10GeneralConfiguration.InternetExplorerCheckServerCertificateRevocation 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/CheckServerCertificateRevocation

### <a name="windows10generalconfigurationinternetexplorerchecksignaturesondownloadedprograms"></a>Windows10GeneralConfiguration.InternetExplorerCheckSignaturesOnDownloadedPrograms 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/CheckSignaturesOnDownloadedPrograms

### <a name="windows10generalconfigurationinternetexplorercrashdetection"></a>Windows10GeneralConfiguration.InternetExplorerCrashDetection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableCrashDetection

### <a name="windows10generalconfigurationinternetexplorerdisableprocessesinenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerDisableProcessesInEnhancedProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableProcessesInEnhancedProtectedMode

### <a name="windows10generalconfigurationinternetexplorerdownloadenclosures"></a>Windows10GeneralConfiguration.InternetExplorerDownloadEnclosures 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableEnclosureDownloading

### <a name="windows10generalconfigurationinternetexplorerencryptionsupport"></a>Windows10GeneralConfiguration.InternetExplorerEncryptionSupport 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableEncryptionSupport

### <a name="windows10generalconfigurationinternetexplorerenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerEnhancedProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/AllowEnhancedProtectedMode

### <a name="windows10generalconfigurationinternetexplorerfallbacktossl3"></a>Windows10GeneralConfiguration.InternetExplorerFallbackToSsl3 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/AllowFallbackToSSL3

### <a name="windows10generalconfigurationinternetexplorerignorecertificateerrors"></a>Windows10GeneralConfiguration.InternetExplorerIgnoreCertificateErrors 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableIgnoringCertificateErrors

### <a name="windows10generalconfigurationinternetexplorerincludeallnetworkpaths"></a>Windows10GeneralConfiguration.InternetExplorerIncludeAllNetworkPaths 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/IncludeAllNetworkPaths

### <a name="windows10generalconfigurationinternetexplorerinternetzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAccessToDataSources 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowAccessToDataSources

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowVBScriptToRun 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowVBScriptToRunInInternetExplorer

### <a name="windows10generalconfigurationinternetexplorerinternetzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAutomaticPromptForFileDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowAutomaticPromptingForFileDownloads

### <a name="windows10generalconfigurationinternetexplorerinternetzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCopyAndPasteViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowCopyPasteViaScript

### <a name="windows10generalconfigurationinternetexplorerinternetzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCrossSiteScriptingFilter 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneEnableCrossSiteScriptingFilter

### <a name="windows10generalconfigurationinternetexplorerinternetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDotNetFrameworkReliantComponents 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowNETFrameworkReliantComponents

### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadSignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneDownloadSignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadUnsignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneDownloadUnsignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragAndDropOrCopyAndPasteFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowDragAndDropCopyAndPasteFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneIncludeLocalPathWhenUploadingFilesToServer

### <a name="windows10generalconfigurationinternetexplorerinternetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneJavaPermissions


### <a name="windows10generalconfigurationinternetexplorerinternetzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneLaunchingApplicationsAndFilesInIFRAME

### <a name="windows10generalconfigurationinternetexplorerinternetzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLessPrivilegedSites 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowLessPrivilegedSites

### <a name="windows10generalconfigurationinternetexplorerinternetzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLoadingOfXamlFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowLoadingOfXAMLFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLogonOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneLogonOptions

### <a name="windows10generalconfigurationinternetexplorerinternetzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneNavigateWindowsAndFrames

### <a name="windows10generalconfigurationinternetexplorerinternetzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerInternetZonePopupBlocker 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneUsePopupBlocker

### <a name="windows10generalconfigurationinternetexplorerinternetzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneEnableProtectedMode

### <a name="windows10generalconfigurationinternetexplorerinternetzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptingOfWebBrowserControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowScriptingOfInternetExplorerWebBrowserControls

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptInitiatedWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowScriptInitiatedWindows

### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptlets 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowScriptlets

### <a name="windows10generalconfigurationinternetexplorerinternetzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneShowSecurityWarningForPotentiallyUnsafeFiles

### <a name="windows10generalconfigurationinternetexplorerinternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerinternetzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUpdatesToStatusBarViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowUpdatesToStatusBarViaScript

### <a name="windows10generalconfigurationinternetexplorerinternetzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUserDataPersistence 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/InternetZoneAllowUserDataPersistence

### <a name="windows10generalconfigurationinternetexplorerintranetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/IntranetZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerintranetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/IntranetZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/IntranetZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LocalMachineZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddowninternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownInternetZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LockedDownInternetZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerlockeddownintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownIntranetZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LockedDownIntranetJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownLocalMachineZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LockedDownLocalMachineZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LockedDownRestrictedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LockedDownRestrictedSitesZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerlockeddowntrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownTrustedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/LockedDownTrustedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerpreventmanagingsmartscreenfilter"></a>Windows10GeneralConfiguration.InternetExplorerPreventManagingSmartScreenFilter 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/PreventManagingSmartScreenFilter

### <a name="windows10generalconfigurationinternetexplorerpreventperuserinstallationofactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerPreventPerUserInstallationOfActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/PreventPerUserInstallationOfActiveXControls

### <a name="windows10generalconfigurationinternetexplorerprocessesconsistentmimehandling"></a>Windows10GeneralConfiguration.InternetExplorerProcessesConsistentMimeHandling 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/ConsistentMimeHandlingInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesmimesniffingsafetyfeature"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMimeSniffingSafetyFeature 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/MimeSniffingSafetyFeatureInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesmkprotocolsecurityrestriction"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMKProtocolSecurityRestriction 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/MKProtocolSecurityRestrictionInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesnotificationbar"></a>Windows10GeneralConfiguration.InternetExplorerProcessesNotificationBar 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/NotificationBarInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesprotectionfromzoneelevation"></a>Windows10GeneralConfiguration.InternetExplorerProcessesProtectionFromZoneElevation 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/ProtectionFromZoneElevationInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictactivexinstall"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictActiveXInstall 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictActiveXInstallInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictfiledownload"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictFileDownload 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictFileDownloadInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerprocessesscriptedwindowsecurityrestrictions"></a>Windows10GeneralConfiguration.InternetExplorerProcessesScriptedWindowSecurityRestrictions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/ScriptedWindowSecurityRestrictionsInternetExplorerProcesses

### <a name="windows10generalconfigurationinternetexplorerremoverunthistimebuttonforoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRemoveRunThisTimeButtonForOutdatedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RemoveRunThisTimeButtonForOutdatedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAccessToDataSources 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowAccessToDataSources

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneactivescripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneActiveScripting 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowActiveScripting

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowVBScriptToRun 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowVBScriptToRunInInternetExplorer

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAutomaticPromptForFileDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowAutomaticPromptingForFileDownloads

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonebinaryandscriptbehaviors"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneBinaryAndScriptBehaviors 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowBinaryAndScriptBehaviors

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCopyAndPasteViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowCopyPasteViaScript

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCrossSiteScriptingFilter 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneEnableCrossSiteScriptingFilter

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDotNetFrameworkReliantComponents 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowNETFrameworkReliantComponents

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadSignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneDownloadSignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadUnsignedActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneDownloadUnsignedActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragAndDropOrCopyAndPasteFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowDragAndDropCopyAndPasteFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonefiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneFileDownloads 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowFileDownloads

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneIncludeLocalPathWhenUploadingFilesToServer

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneLaunchingApplicationsAndFilesInIFRAME

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLessPrivilegedSites 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowLessPrivilegedSites

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLoadingOfXamlFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowLoadingOfXAMLFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLogonOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneLogonOptions

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonemetarefresh"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneMetaRefresh 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowMETAREFRESH

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneNavigateWindowsAndFrames

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZonePopupBlocker 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneUsePopupBlocker

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneProtectedMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneTurnOnProtectedMode

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerunactivexcontrolsandplugins"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunActiveXControlsAndPlugins 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneRunActiveXControlsAndPlugins

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptactivexcontrolsmarkedsafeforscripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptActiveXControlsMarkedSafeForScripting 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneScriptActiveXControlsMarkedSafeForScripting

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofjavaapplets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfJavaApplets 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneScriptingOfJavaApplets

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfWebBrowserControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowScriptingOfInternetExplorerWebBrowserControls

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptInitiatedWindows 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowScriptInitiatedWindows

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptlets 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowScriptlets

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneShowSecurityWarningForPotentiallyUnsafeFiles

### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSmartScreen 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowSmartScreenIE

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUpdatesToStatusBarViaScript 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowUpdatesToStatusBarViaScript

### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUserDataPersistence 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/RestrictedSitesZoneAllowUserDataPersistence

### <a name="windows10generalconfigurationinternetexplorersecuritysettingscheck"></a>Windows10GeneralConfiguration.InternetExplorerSecuritySettingsCheck 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DisableSecuritySettingsCheck

### <a name="windows10generalconfigurationinternetexplorersecurityzonesuseonlymachinesettings"></a>Windows10GeneralConfiguration.InternetExplorerSecurityZonesUseOnlyMachineSettings 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/SecurityZonesUseOnlyMachineSettings

### <a name="windows10generalconfigurationinternetexplorersoftwarewhensignatureisinvalid"></a>Windows10GeneralConfiguration.InternetExplorerSoftwareWhenSignatureIsInvalid 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/AllowSoftwareWhenSignatureIsInvalid

### <a name="windows10generalconfigurationinternetexplorertrustedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**:./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/TrustedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

### <a name="windows10generalconfigurationinternetexplorertrustedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/TrustedSitesZoneInitializeAndScriptActiveXControls

### <a name="windows10generalconfigurationinternetexplorertrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneJavaPermissions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/TrustedSitesZoneJavaPermissions

### <a name="windows10generalconfigurationinternetexploreruseactivexinstallerservice"></a>Windows10GeneralConfiguration.InternetExplorerUseActiveXInstallerService 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/SpecifyUseOfActiveXInstallerService

### <a name="windows10generalconfigurationinternetexplorerusersaddingsites"></a>Windows10GeneralConfiguration.InternetExplorerUsersAddingSites 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DoNotAllowUsersToAddSites

### <a name="windows10generalconfigurationinternetexploreruserschangingpolicies"></a>Windows10GeneralConfiguration.InternetExplorerUsersChangingPolicies 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/InternetExplorer/DoNotAllowUsersToChangePolicies

### <a name="windows10generalconfigurationinternetsharingblocked"></a>Windows10GeneralConfiguration.InternetSharingBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WiFi/AllowInternetSharing

### <a name="windows10generalconfigurationlocationservicesblocked"></a>Windows10GeneralConfiguration.LocationServicesBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/AllowLocation

### <a name="windows10generalconfigurationlockscreenallowtimeoutconfiguration"></a>Windows10GeneralConfiguration.LockScreenAllowTimeoutConfiguration 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/AllowScreenTimeoutWhileLockedUser/config

### <a name="windows10generalconfigurationlockscreenblockactioncenternotifications"></a>Windows10GeneralConfiguration.LockScreenBlockActionCenterNotifications 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/AboveLock/AllowActionCenterNotifications

### <a name="windows10generalconfigurationlockscreenblockcortana"></a>Windows10GeneralConfiguration.LockScreenBlockCortana 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/AboveLock/AllowCortanaAboveLock

### <a name="windows10generalconfigurationlockscreenblocktoastnotifications"></a>Windows10GeneralConfiguration.LockScreenBlockToastNotifications 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/AboveLock/AllowToasts

### <a name="windows10generalconfigurationlockscreencamera"></a>Windows10GeneralConfiguration.LockScreenCamera 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/PreventEnablingLockScreenCamera

### <a name="windows10generalconfigurationlockscreenhidenetworkselectionui"></a>Windows10GeneralConfiguration.LockScreenHideNetworkSelectionUI 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsLogon/DontDisplayNetworkSelectionUI

### <a name="windows10generalconfigurationlockscreenslideshow"></a>Windows10GeneralConfiguration.LockScreenSlideShow 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/PreventLockScreenSlideShow

### <a name="windows10generalconfigurationlockscreentimeoutinseconds"></a>Windows10GeneralConfiguration.LockScreenTimeoutInSeconds 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/ScreenTimeoutWhileLocked

### <a name="windows10generalconfigurationlogonblockfastuserswitching"></a>Windows10GeneralConfiguration.LogonBlockFastUserSwitching 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsLogon/HideFastUserSwitching

### <a name="windows10generalconfigurationmessagingblockmms"></a>Windows10GeneralConfiguration.MessagingBlockMMS 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Messaging/AllowMMS

### <a name="windows10generalconfigurationmessagingblockrichcommunicationservices"></a>Windows10GeneralConfiguration.MessagingBlockRichCommunicationServices 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Messaging/AllowRCS

### <a name="windows10generalconfigurationmessagingblocksync"></a>Windows10GeneralConfiguration.MessagingBlockSync 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Messaging/AllowMessageSync

### <a name="windows10generalconfigurationmicrosoftaccountblocked"></a>Windows10GeneralConfiguration.MicrosoftAccountBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/accounts/AllowMicrosoftAccountConnection

### <a name="windows10generalconfigurationmicrosoftaccountblocksettingssync"></a>Windows10GeneralConfiguration.MicrosoftAccountBlockSettingsSync 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowSyncMySettings

### <a name="windows10generalconfigurationmicrosoftaccountsigninassistantsettings"></a>Windows10GeneralConfiguration.MicrosoftAccountSignInAssistantSettings 
**CSP**:./Device/Vendor/MSFT/accounts  
**URI de deslocamento**:/AllowMicrosoftAccountSignInAssistant

### <a name="windows10generalconfigurationnetworkproxyapplysettingsdevicewide"></a>Windows10GeneralConfiguration.NetworkProxyApplySettingsDeviceWide 
**CSP**:./Device/Vendor/MSFT/NetworkProxy  
**URI de deslocamento**:/ProxySettingsPerUser

### <a name="windows10generalconfigurationnetworkproxyautomaticconfigurationurl"></a>Windows10GeneralConfiguration.NetworkProxyAutomaticConfigurationUrl 
**CSP**:./Device/Vendor/MSFT/NetworkProxy  
**URI de deslocamento**:/SetupScriptUrl

### <a name="windows10generalconfigurationnetworkproxydisableautodetect"></a>Windows10GeneralConfiguration.NetworkProxyDisableAutoDetect 
**CSP**:./Device/Vendor/MSFT/NetworkProxy  
**URI de deslocamento**:/AutoDetect

### <a name="windows10generalconfigurationnetworkproxyserver"></a>Windows10GeneralConfiguration.NetworkProxyServer 
**CSP**:./Vendor/MSFT/NetworkProxy  
**URI de deslocamento**:/ProxyAddress,/Exceptions e/UseProxyForLocalAddresses

### <a name="windows10generalconfigurationnfcblocked"></a>Windows10GeneralConfiguration.NfcBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowNFC

### <a name="windows10generalconfigurationonedrivedisablefilesync"></a>Windows10GeneralConfiguration.OneDriveDisableFileSync 
**CSP**:./Vendor/MSFT/Policy  
**Offset URI**: /Config/System/DisableOneDriveFileSync

### <a name="windows10generalconfigurationpasswordblocksimple"></a>Windows10GeneralConfiguration.PasswordBlockSimple 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/AllowSimpleDevicePassword

### <a name="windows10generalconfigurationpasswordexpirationdays"></a>Windows10GeneralConfiguration.PasswordExpirationDays 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/DevicePasswordExpiration

### <a name="windows10generalconfigurationpasswordminimumageindays"></a>Windows10GeneralConfiguration.PasswordMinimumAgeInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/MinimumPasswordAge

### <a name="windows10generalconfigurationpasswordminimumcharactersetcount"></a>Windows10GeneralConfiguration.PasswordMinimumCharacterSetCount 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/MinDevicePasswordComplexCharacters

### <a name="windows10generalconfigurationpasswordminimumlength"></a>Windows10GeneralConfiguration.PasswordMinimumLength 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/MinDevicePasswordLength

### <a name="windows10generalconfigurationpasswordminutesofinactivitybeforescreentimeout"></a>Windows10GeneralConfiguration.PasswordMinutesOfInactivityBeforeScreenTimeout 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/MaxInactivityTimeDeviceLock

### <a name="windows10generalconfigurationpasswordpreviouspasswordblockcount"></a>Windows10GeneralConfiguration.PasswordPreviousPasswordBlockCount 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/DevicePasswordHistory

### <a name="windows10generalconfigurationpasswordrequired"></a>Windows10GeneralConfiguration.PasswordRequired 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/DevicePasswordEnabled

### <a name="windows10generalconfigurationpasswordrequiredtype"></a>Windows10GeneralConfiguration.PasswordRequiredType 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/AlphanumericDevicePasswordRequired

### <a name="windows10generalconfigurationpasswordrequirewhenresumefromidlestate"></a>Windows10GeneralConfiguration.PasswordRequireWhenResumeFromIdleState 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/AllowIdleReturnWithoutPassword

### <a name="windows10generalconfigurationpasswordsigninfailurecountbeforefactoryreset"></a>Windows10GeneralConfiguration.PasswordSignInFailureCountBeforeFactoryReset 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceLock/MaxDevicePasswordFailedAttempts

### <a name="windows10generalconfigurationpersonalizationdesktopimageurl"></a>Windows10GeneralConfiguration.PersonalizationDesktopImageUrl 
**CSP**:./Device/Vendor/MSFT/Personalization  
**URI de deslocamento**:/DesktopImageUrl

### <a name="windows10generalconfigurationpersonalizationlockscreenimageurl"></a>Windows10GeneralConfiguration.PersonalizationLockScreenImageUrl 
**CSP**:./Device/Vendor/MSFT/Personalization  
**URI de deslocamento**:/LockScreenImageUrl

### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhileonbattery"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhileOnBattery 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Power/RequirePasswordWhenComputerWakesOnBattery

### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhilepluggedin"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhilePluggedIn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Power/RequirePasswordWhenComputerWakesPluggedIn

### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhileonbattery"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhileOnBattery 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Power/AllowStandbyStatesWhenSleepingOnBattery

### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhilepluggedin"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhilePluggedIn 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Power/AllowStandbyWhenSleepingPluggedIn

### <a name="windows10generalconfigurationpreventinstallationofmatchingdeviceids"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceIDs 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

### <a name="windows10generalconfigurationpreventinstallationofmatchingdevicesetupclasses"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceSetupClasses 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

### <a name="windows10generalconfigurationprinterblockaddition"></a>Windows10GeneralConfiguration.PrinterBlockAddition 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Education/PreventAddingNewPrinters

### <a name="windows10generalconfigurationprinterdefaultname"></a>Windows10GeneralConfiguration.PrinterDefaultName 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Education/DefaultPrinterName

### <a name="windows10generalconfigurationprinternames"></a>Windows10GeneralConfiguration.PrinterNames 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Education/PrinterNames

### <a name="windows10generalconfigurationprivacyadvertisingid"></a>Windows10GeneralConfiguration.PrivacyAdvertisingId 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Privacy/DisableAdvertisingID

### <a name="windows10generalconfigurationprivacyautoacceptpairingandconsentprompts"></a>Windows10GeneralConfiguration.PrivacyAutoAcceptPairingAndConsentPrompts 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Privacy/AllowAutoAcceptPairingAndPrivacyConsentPrompts

### <a name="windows10generalconfigurationprivacyblockactivityfeed"></a>Windows10GeneralConfiguration.PrivacyBlockActivityFeed 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Privacy/EnableActivityFeed

### <a name="windows10generalconfigurationprivacyblockinputpersonalization"></a>Windows10GeneralConfiguration.PrivacyBlockInputPersonalization 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Privacy/AllowInputPersonalization

### <a name="windows10generalconfigurationprivacyblockpublishuseractivities"></a>Windows10GeneralConfiguration.PrivacyBlockPublishUserActivities 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Privacy/PublishUserActivities

### <a name="windows10generalconfigurationsafesearchfilter"></a>Windows10GeneralConfiguration.SafeSearchFilter 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/SafeSearchPermissions

### <a name="windows10generalconfigurationscreencaptureblocked"></a>Windows10GeneralConfiguration.ScreenCaptureBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowScreenCapture

### <a name="windows10generalconfigurationsearchblockdiacritics"></a>Windows10GeneralConfiguration.SearchBlockDiacritics 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/AllowUsingDiacritics

### <a name="windows10generalconfigurationsearchblockwebresults"></a>Windows10GeneralConfiguration.SearchBlockWebResults 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/DoNotUseWebResults

### <a name="windows10generalconfigurationsearchdisableautolanguagedetection"></a>Windows10GeneralConfiguration.SearchDisableAutoLanguageDetection 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/AlwaysUseAutoLangDetection

### <a name="windows10generalconfigurationsearchdisableindexerbackoff"></a>Windows10GeneralConfiguration.SearchDisableIndexerBackoff 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/DisableBackoff

### <a name="windows10generalconfigurationsearchdisableindexingencrypteditems"></a>Windows10GeneralConfiguration.SearchDisableIndexingEncryptedItems 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/AllowIndexingEncryptedStoresOrItems

### <a name="windows10generalconfigurationsearchdisableindexingremovabledrive"></a>Windows10GeneralConfiguration.SearchDisableIndexingRemovableDrive 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/DisableRemovableDriveIndexing

### <a name="windows10generalconfigurationsearchdisablelocation"></a>Windows10GeneralConfiguration.SearchDisableLocation 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/AllowSearchToUseLocation

### <a name="windows10generalconfigurationsearchdisableuselocation"></a>Windows10GeneralConfiguration.SearchDisableUseLocation 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/AllowSearchToUseLocation

### <a name="windows10generalconfigurationsearchenableautomaticindexsizemanangement"></a>Windows10GeneralConfiguration.SearchEnableAutomaticIndexSizeManangement 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/PreventIndexingLowDiskSpaceMB

### <a name="windows10generalconfigurationsearchenableremotequeries"></a>Windows10GeneralConfiguration.SearchEnableRemoteQueries 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Search/PreventRemoteQueries

### <a name="windows10generalconfigurationsecurityblockazureadjoineddevicesautoencryption"></a>Windows10GeneralConfiguration.SecurityBlockAzureADJoinedDevicesAutoEncryption 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices

### <a name="windows10generalconfigurationsettingsblockaccountspage"></a>Windows10GeneralConfiguration.SettingsBlockAccountsPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockaddprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockAddProvisioningPackage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Security/AllowAddProvisioningPackage

### <a name="windows10generalconfigurationsettingsblockappspage"></a>Windows10GeneralConfiguration.SettingsBlockAppsPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockchangelanguage"></a>Windows10GeneralConfiguration.SettingsBlockChangeLanguage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/AllowLanguage

### <a name="windows10generalconfigurationsettingsblockchangepowersleep"></a>Windows10GeneralConfiguration.SettingsBlockChangePowerSleep 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/AllowPowerSleep

### <a name="windows10generalconfigurationsettingsblockchangeregion"></a>Windows10GeneralConfiguration.SettingsBlockChangeRegion 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/AllowRegion

### <a name="windows10generalconfigurationsettingsblockchangesystemtime"></a>Windows10GeneralConfiguration.SettingsBlockChangeSystemTime 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/AllowDateTime

### <a name="windows10generalconfigurationsettingsblockdevicespage"></a>Windows10GeneralConfiguration.SettingsBlockDevicesPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockeaseofaccesspage"></a>Windows10GeneralConfiguration.SettingsBlockEaseOfAccessPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockeditdevicename"></a>Windows10GeneralConfiguration.SettingsBlockEditDeviceName 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/AllowEditDeviceName

### <a name="windows10generalconfigurationsettingsblockgamingpage"></a>Windows10GeneralConfiguration.SettingsBlockGamingPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblocknetworkinternetpage"></a>Windows10GeneralConfiguration.SettingsBlockNetworkInternetPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockpersonalizationpage"></a>Windows10GeneralConfiguration.SettingsBlockPersonalizationPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockprivacypage"></a>Windows10GeneralConfiguration.SettingsBlockPrivacyPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockremoveprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockRemoveProvisioningPackage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Security/AllowRemoveProvisioningPackage

### <a name="windows10generalconfigurationsettingsblocksystempage"></a>Windows10GeneralConfiguration.SettingsBlockSystemPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblocktimelanguagepage"></a>Windows10GeneralConfiguration.SettingsBlockTimeLanguagePage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationsettingsblockupdatesecuritypage"></a>Windows10GeneralConfiguration.SettingsBlockUpdateSecurityPage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Settings/PageVisibilityList

### <a name="windows10generalconfigurationshareduserappdataallowed"></a>Windows10GeneralConfiguration.SharedUserAppDataAllowed 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/AllowSharedUserAppData

### <a name="windows10generalconfigurationsmartscreenblockpromptoverride"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverride 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventSmartScreenPromptOverride

### <a name="windows10generalconfigurationsmartscreenblockpromptoverrideforfiles"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverrideForFiles 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventSmartScreenPromptOverrideForFiles

### <a name="windows10generalconfigurationsmartscreenenableappinstallcontrol"></a>Windows10GeneralConfiguration.SmartScreenEnableAppInstallControl 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/SmartScreen/EnableAppInstallControl

### <a name="windows10generalconfigurationstartblockunpinningappsfromtaskbar"></a>Windows10GeneralConfiguration.StartBlockUnpinningAppsFromTaskbar 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/NoPinningToTaskbar

### <a name="windows10generalconfigurationstartmenuapplistvisibility"></a>Windows10GeneralConfiguration.StartMenuAppListVisibility 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideAppList

### <a name="windows10generalconfigurationstartmenuhidechangeaccountsettings"></a>Windows10GeneralConfiguration.StartMenuHideChangeAccountSettings 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideChangeAccountSettings

### <a name="windows10generalconfigurationstartmenuhidefrequentlyusedapps"></a>Windows10GeneralConfiguration.StartMenuHideFrequentlyUsedApps 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideFrequentlyUsedApps

### <a name="windows10generalconfigurationstartmenuhidehibernate"></a>Windows10GeneralConfiguration.StartMenuHideHibernate 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideHibernate

### <a name="windows10generalconfigurationstartmenuhidelock"></a>Windows10GeneralConfiguration.StartMenuHideLock 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideLock

### <a name="windows10generalconfigurationstartmenuhidepowerbutton"></a>Windows10GeneralConfiguration.StartMenuHidePowerButton 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HidePowerButton

### <a name="windows10generalconfigurationstartmenuhiderecentjumplists"></a>Windows10GeneralConfiguration.StartMenuHideRecentJumpLists 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideRecentJumplists

### <a name="windows10generalconfigurationstartmenuhiderecentlyaddedapps"></a>Windows10GeneralConfiguration.StartMenuHideRecentlyAddedApps 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideRecentlyAddedApps

### <a name="windows10generalconfigurationstartmenuhiderestartoptions"></a>Windows10GeneralConfiguration.StartMenuHideRestartOptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideRestart

### <a name="windows10generalconfigurationstartmenuhideshutdown"></a>Windows10GeneralConfiguration.StartMenuHideShutDown 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideShutDown

### <a name="windows10generalconfigurationstartmenuhidesignout"></a>Windows10GeneralConfiguration.StartMenuHideSignOut 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideSignOut

### <a name="windows10generalconfigurationstartmenuhidesleep"></a>Windows10GeneralConfiguration.StartMenuHideSleep 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideSleep

### <a name="windows10generalconfigurationstartmenuhideswitchaccount"></a>Windows10GeneralConfiguration.StartMenuHideSwitchAccount 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideSwitchAccount

### <a name="windows10generalconfigurationstartmenuhideusertile"></a>Windows10GeneralConfiguration.StartMenuHideUserTile 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/HideUserTile

### <a name="windows10generalconfigurationstartmenulayoutedgeassetsxml"></a>Windows10GeneralConfiguration.StartMenuLayoutEdgeAssetsXml 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/ImportEdgeAssets

### <a name="windows10generalconfigurationstartmenulayoutxml"></a>Windows10GeneralConfiguration.StartMenuLayoutXml 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/StartLayout

### <a name="windows10generalconfigurationstartmenumode"></a>Windows10GeneralConfiguration.StartMenuMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/ForceStartSize

### <a name="windows10generalconfigurationstartmenupinnedfolderdocuments"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDocuments 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderDocuments

### <a name="windows10generalconfigurationstartmenupinnedfolderdownloads"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDownloads 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderDownloads

### <a name="windows10generalconfigurationstartmenupinnedfolderfileexplorer"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderFileExplorer 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderFileExplorer

### <a name="windows10generalconfigurationstartmenupinnedfolderhomegroup"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderHomeGroup 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderHomeGroup

### <a name="windows10generalconfigurationstartmenupinnedfoldermusic"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderMusic 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderMusic

### <a name="windows10generalconfigurationstartmenupinnedfoldernetwork"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderNetwork 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderNetwork

### <a name="windows10generalconfigurationstartmenupinnedfolderpersonalfolder"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPersonalFolder 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderPersonalFolder

### <a name="windows10generalconfigurationstartmenupinnedfolderpictures"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPictures 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderPictures

### <a name="windows10generalconfigurationstartmenupinnedfoldersettings"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderSettings 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderSettings

### <a name="windows10generalconfigurationstartmenupinnedfoldervideos"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderVideos 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Start/AllowPinnedFolderVideos

### <a name="windows10generalconfigurationstorageblockremovablestorage"></a>Windows10GeneralConfiguration.StorageBlockRemovableStorage 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/AllowStorageCard

### <a name="windows10generalconfigurationstoragerequiremobiledeviceencryption"></a>Windows10GeneralConfiguration.StorageRequireMobileDeviceEncryption 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Security/RequireDeviceEncryption

### <a name="windows10generalconfigurationstoragerestrictappdatatosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppDataToSystemVolume 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/RestrictAppDataToSystemVolume

### <a name="windows10generalconfigurationstoragerestrictappinstalltosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppInstallToSystemVolume 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/RestrictAppToSystemVolume

### <a name="windows10generalconfigurationsystembootstartdriverinitialization"></a>Windows10GeneralConfiguration.SystemBootStartDriverInitialization 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/BootStartDriverInitialization

### <a name="windows10generalconfigurationsystemtelemetryproxyserver"></a>Windows10GeneralConfiguration.SystemTelemetryProxyServer 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/System/TelemetryProxy

### <a name="windows10generalconfigurationtaskmanagerblockendtask"></a>Windows10GeneralConfiguration.TaskManagerBlockEndTask 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/taskmanager/AllowEndTask

### <a name="windows10generalconfigurationtenantlockdownrequirenetworkduringoutofboxexperience"></a>Windows10GeneralConfiguration.TenantLockdownRequireNetworkDuringOutOfBoxExperience 
**CSP**: ./Vendor/MSFT/TenantLockdown  
**URI de deslocamento**:/RequireNetworkInOOBE

### <a name="windows10generalconfigurationusbblocked"></a>Windows10GeneralConfiguration.UsbBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Connectivity/AllowUSBConnection

### <a name="windows10generalconfigurationvoicerecordingblocked"></a>Windows10GeneralConfiguration.VoiceRecordingBlocked 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowVoiceRecording

### <a name="windows10generalconfigurationwebrtcblocklocalhostipaddress"></a>Windows10GeneralConfiguration.WebRtcBlockLocalhostIpAddress 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/PreventUsingLocalHostIPAddressForWebRTC

### <a name="windows10generalconfigurationwifiblockautomaticconnecthotspots"></a>Windows10GeneralConfiguration.WiFiBlockAutomaticConnectHotspots 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WiFi/AllowAutoConnectToWiFiSenseHotspots

### <a name="windows10generalconfigurationwifiblocked"></a>Windows10GeneralConfiguration.WiFiBlocked 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WiFi/AllowWiFi

### <a name="windows10generalconfigurationwifiblockmanualconfiguration"></a>Windows10GeneralConfiguration.WiFiBlockManualConfiguration 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WiFi/AllowManualWiFi/Configuration

### <a name="windows10generalconfigurationwifiscaninterval"></a>Windows10GeneralConfiguration.WiFiScanInterval 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WiFi/WLANScanMode

### <a name="windows10generalconfigurationwindowslogonlocalusersondomainjoinedcomputers"></a>Windows10GeneralConfiguration.WindowsLogOnLocalUsersOnDomainJoinedComputers 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WindowsLogon/EnumerateLocalUsersOnDomainJoinedComputers

### <a name="windows10generalconfigurationwindowsspotlightblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockConsumerSpecificFeatures 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsConsumerFeatures

### <a name="windows10generalconfigurationwindowsspotlightblocked"></a>Windows10GeneralConfiguration.WindowsSpotlightBlocked 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsSpotlight

### <a name="windows10generalconfigurationwindowsspotlightblockonactioncenter"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockOnActionCenter 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsSpotlightOnActionCenter

### <a name="windows10generalconfigurationwindowsspotlightblocktailoredexperiences"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockTailoredExperiences 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowTailoredExperiencesWithDiagnosticData

### <a name="windows10generalconfigurationwindowsspotlightblockthirdpartynotifications"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockThirdPartyNotifications 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowThirdPartySuggestionsInWindowsSpotlight

### <a name="windows10generalconfigurationwindowsspotlightblockwelcomeexperience"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWelcomeExperience 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsSpotlightWindowsWelcomeExperience

### <a name="windows10generalconfigurationwindowsspotlightblockwindowstips"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWindowsTips 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/AllowWindowsTips

### <a name="windows10generalconfigurationwindowsspotlightconfigureonlockscreen"></a>Windows10GeneralConfiguration.WindowsSpotlightConfigureOnLockScreen 
**CSP**:./User/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Experience/ConfigureWindowsSpotlightOnLockScreen

### <a name="windows10generalconfigurationwindowsstoreblockautoupdate"></a>Windows10GeneralConfiguration.WindowsStoreBlockAutoUpdate 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/AllowAppStoreAutoUpdate

### <a name="windows10generalconfigurationwindowsstoreblocked"></a>Windows10GeneralConfiguration.WindowsStoreBlocked 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/AllowStore

### <a name="windows10generalconfigurationwindowsstoreenableprivatestoreonly"></a>Windows10GeneralConfiguration.WindowsStoreEnablePrivateStoreOnly 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ApplicationManagement/RequirePrivateStoreOnly

### <a name="windows10generalconfigurationwirelessdisplayblockprojectiontothisdevice"></a>Windows10GeneralConfiguration.WirelessDisplayBlockProjectionToThisDevice 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WirelessDisplay/AllowProjectionToPC

### <a name="windows10generalconfigurationwirelessdisplayblockuserinputfromreceiver"></a>Windows10GeneralConfiguration.WirelessDisplayBlockUserInputFromReceiver 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WirelessDisplay/AllowUserInputFromWirelessDisplayReceiver

### <a name="windows10generalconfigurationwirelessdisplayrequirepinforpairing"></a>Windows10GeneralConfiguration.WirelessDisplayRequirePinForPairing 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/WirelessDisplay/RequirePINForPairing

### <a name="windows10networkboundaryconfigurationwindowsnetworkisolationpolicy"></a>Windows10NetworkBoundaryConfiguration.WindowsNetworkIsolationPolicy 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/NetworkIsolation/EnterpriseCloudResources,/config/NetworkIsolation/EnterpriseIPRange,/config/NetworkIsolation/EnterpriseIPRangesAreAuthoritative,/config/NetworkIsolation/ EnterpriseInternalProxyServers, /Config/NetworkIsolation/EnterpriseNetworkDomainNames, /Config/NetworkIsolation/EnterpriseProxyServers, /Config/NetworkIsolation/EnterpriseProxyServersAreAuthoritative, /Config/NetworkIsolation/ NeutralResources

### <a name="windows10policyoverrideconfigurationprefermdmovergrouppolicy"></a>Windows10PolicyOverrideConfiguration.PreferMdmOverGroupPolicy 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/ControlPolicyConflict/MDMWinsOverGP

### <a name="windows10secureassessmentconfigurationallowprinting"></a>Windows10SecureAssessmentConfiguration.AllowPrinting 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**URI de deslocamento**:/RequirePrinting

### <a name="windows10secureassessmentconfigurationallowscreencapture"></a>Windows10SecureAssessmentConfiguration.AllowScreenCapture 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**URI de deslocamento**:/AllowScreenMonitoring

### <a name="windows10secureassessmentconfigurationallowtextsuggestion"></a>Windows10SecureAssessmentConfiguration.AllowTextSuggestion 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**URI de deslocamento**:/AllowTextSuggestions

### <a name="windows10secureassessmentconfigurationconfigurationaccount"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccount 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**URI de deslocamento**:/TesterAccount

### <a name="windows10secureassessmentconfigurationconfigurationaccounttype"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccountType 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**URI de deslocamento**:/TesterAccount

### <a name="windows10secureassessmentconfigurationlaunchuri"></a>Windows10SecureAssessmentConfiguration.LaunchUri 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**URI de deslocamento**:/LaunchURI

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsblocktelemetry"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsBlockTelemetry 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/MOMAgent/WorkspaceID e/MOMAgent/WorkspaceKey

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspaceid"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceId 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/MOMAgent/WorkspaceID

### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspacekey"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceKey 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/MOMAgent/WorkspaceKey

### <a name="windows10teamgeneralconfigurationconnectappblockautolaunch"></a>Windows10TeamGeneralConfiguration.ConnectAppBlockAutoLaunch 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/Connect/AutoLaunch

### <a name="windows10teamgeneralconfigurationdeviceaccountblockexchangeservices"></a>Windows10TeamGeneralConfiguration.DeviceAccountBlockExchangeServices 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/DeviceAccount/email

### <a name="windows10teamgeneralconfigurationdeviceaccountemailaddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountEmailAddress 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/DeviceAccount/email

### <a name="windows10teamgeneralconfigurationdeviceaccountexchangeserveraddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountExchangeServerAddress 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/DeviceAccount/ExchangeServer

### <a name="windows10teamgeneralconfigurationdeviceaccountrequirepasswordrotation"></a>Windows10TeamGeneralConfiguration.DeviceAccountRequirePasswordRotation 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/DeviceAccount/PasswordRotationEnabled

### <a name="windows10teamgeneralconfigurationdeviceaccountsessioninitiationprotocoladdress"></a>Windows10TeamGeneralConfiguration.DeviceAccountSessionInitiationProtocolAddress 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/DeviceAccount/SipAddress

### <a name="windows10teamgeneralconfigurationmaintenancewindowblocked"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowBlocked 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/MaintenanceHoursSimple/hours/Duration e/MaintenanceHoursSimple/hours/StartTime

### <a name="windows10teamgeneralconfigurationmaintenancewindowdurationinhours"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowDurationInHours 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/MaintenanceHoursSimple/hours/Duration

### <a name="windows10teamgeneralconfigurationmaintenancewindowstarttime"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowStartTime 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/MaintenanceHoursSimple/hours/StartTime

### <a name="windows10teamgeneralconfigurationmiracastblocked"></a>Windows10TeamGeneralConfiguration.MiracastBlocked 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/WirelessProjection/Enabled

### <a name="windows10teamgeneralconfigurationmiracastchannel"></a>Windows10TeamGeneralConfiguration.MiracastChannel 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/WirelessProjection/Channel

### <a name="windows10teamgeneralconfigurationmiracastrequirepin"></a>Windows10TeamGeneralConfiguration.MiracastRequirePin 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/WirelessProjection/PINRequired

### <a name="windows10teamgeneralconfigurationsettingsblockmymeetingsandfiles"></a>Windows10TeamGeneralConfiguration.SettingsBlockMyMeetingsAndFiles 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/DoNotShowMyMeetingsAndFiles

### <a name="windows10teamgeneralconfigurationsettingsblocksessionresume"></a>Windows10TeamGeneralConfiguration.SettingsBlockSessionResume 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/AllowSessionResume

### <a name="windows10teamgeneralconfigurationsettingsblocksigninsuggestions"></a>Windows10TeamGeneralConfiguration.SettingsBlockSigninSuggestions 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/DisableSigninSuggestions

### <a name="windows10teamgeneralconfigurationsettingsdefaultvolume"></a>Windows10TeamGeneralConfiguration.SettingsDefaultVolume 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/DefaultVolume

### <a name="windows10teamgeneralconfigurationsettingsscreentimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsScreenTimeoutInMinutes 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/ScreenTimeout

### <a name="windows10teamgeneralconfigurationsettingssessiontimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSessionTimeoutInMinutes 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/SessionTimeout

### <a name="windows10teamgeneralconfigurationsettingssleeptimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSleepTimeoutInMinutes 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/Properties/SleepTimeout

### <a name="windows10teamgeneralconfigurationwelcomescreenbackgroundimageurl"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBackgroundImageUrl 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/Welcome/CurrentBackgroundPath

### <a name="windows10teamgeneralconfigurationwelcomescreenblockautomaticwakeup"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBlockAutomaticWakeUp 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/Welcome/AutoWakeScreen

### <a name="windows10teamgeneralconfigurationwelcomescreenmeetinginformation"></a>Windows10TeamGeneralConfiguration.WelcomeScreenMeetingInformation 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**URI de deslocamento**:/InBoxApps/Welcome/MeetingInfoOption

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI de deslocamento**:/Offboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingFilename
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI de deslocamento**:/Offboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI de deslocamento**:/Onboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingFilename 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI de deslocamento**:/Onboarding 

### <a name="windowsdefenderadvancedthreatprotectionconfigurationallowsamplesharing"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AllowSampleSharing 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI de deslocamento**:/Configuration/SampleSharing

### <a name="windowsdefenderadvancedthreatprotectionconfigurationenableexpeditedtelemetryreporting"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.EnableExpeditedTelemetryReporting 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**URI de deslocamento**:/Configuration/TelemetryReportingFrequency

### <a name="windowsdeliveryoptimizationconfigurationdeliveryoptimizationmode"></a>WindowsDeliveryOptimizationConfiguration.DeliveryOptimizationMode 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeliveryOptimization/DODownloadMode

### <a name="windowsidentityprotectionconfigurationenhancedantispoofingforfacialfeaturesenabled"></a>WindowsIdentityProtectionConfiguration.EnhancedAntiSpoofingForFacialFeaturesEnabled 
**CSP**:./Device/Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/Biometrics/FacialFeaturesUseEnhancedAntiSpoofing

### <a name="windowsidentityprotectionconfigurationpinexpirationindays"></a>WindowsIdentityProtectionConfiguration.PinExpirationInDays 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/Expiration

### <a name="windowsidentityprotectionconfigurationpinlowercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinLowercaseCharactersUsage 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/LowercaseLetters

### <a name="windowsidentityprotectionconfigurationpinmaximumlength"></a>WindowsIdentityProtectionConfiguration.PinMaximumLength 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/MaximumPINLength

### <a name="windowsidentityprotectionconfigurationpinminimumlength"></a>WindowsIdentityProtectionConfiguration.PinMinimumLength 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/MinimumPINLength

### <a name="windowsidentityprotectionconfigurationpinpreviousblockcount"></a>WindowsIdentityProtectionConfiguration.PinPreviousBlockCount 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/History

### <a name="windowsidentityprotectionconfigurationpinrecoveryenabled"></a>WindowsIdentityProtectionConfiguration.PinRecoveryEnabled 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/EnablePinRecovery

### <a name="windowsidentityprotectionconfigurationpinspecialcharactersusage"></a>WindowsIdentityProtectionConfiguration.PinSpecialCharactersUsage 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/SpecialCharacters

### <a name="windowsidentityprotectionconfigurationpinuppercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinUppercaseCharactersUsage
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/PINComplexity/UppercaseLetters

### <a name="windowsidentityprotectionconfigurationsecuritydevicerequired"></a>WindowsIdentityProtectionConfiguration.SecurityDeviceRequired 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/RequireSecurityDevice

### <a name="windowsidentityprotectionconfigurationunlockwithbiometricsenabled"></a>WindowsIdentityProtectionConfiguration.UnlockWithBiometricsEnabled 
**CSP**:./Device/Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/Biometrics/UseBiometrics

### <a name="windowsidentityprotectionconfigurationusecertificatesforonpremisesauthenabled"></a>WindowsIdentityProtectionConfiguration.UseCertificatesForOnPremisesAuthEnabled 
**CSP**:./Device/Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/UseCertificateForOnPremAuth

### <a name="windowsidentityprotectionconfigurationwindowshelloforbusinessblocked"></a>WindowsIdentityProtectionConfiguration.WindowsHelloForBusinessBlocked 
**CSP**:./Vendor/MSFT/PassportForWork  
**URI de deslocamento**:/{AADTenantId}/Policies/UsePassportForWork

### <a name="windowskioskconfigurationedgekioskenablepublicbrowsing"></a>WindowsKioskConfiguration.EdgeKioskEnablePublicBrowsing 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ConfigureKioskMode

### <a name="windowskioskconfigurationedgekioskresetafteridletimeinminutes"></a>WindowsKioskConfiguration.EdgeKioskResetAfterIdleTimeInMinutes 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Browser/ConfigureKioskResetAfterIdleTimeout

### <a name="windowskioskconfigurationkioskbrowserblockedurlexceptions"></a>WindowsKioskConfiguration.KioskBrowserBlockedUrlExceptions 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/BlockedUrlExceptions

### <a name="windowskioskconfigurationkioskbrowserblockedurls"></a>WindowsKioskConfiguration.KioskBrowserBlockedURLs 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/BlockedUrls

### <a name="windowskioskconfigurationkioskbrowserdefaulturl"></a>WindowsKioskConfiguration.KioskBrowserDefaultUrl 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/DefaultUrl

### <a name="windowskioskconfigurationkioskbrowserenableendsessionbutton"></a>WindowsKioskConfiguration.KioskBrowserEnableEndSessionButton 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/EnableEndSessionButton

### <a name="windowskioskconfigurationkioskbrowserenablehomebutton"></a>WindowsKioskConfiguration.KioskBrowserEnableHomeButton 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/EnableHomeButton

### <a name="windowskioskconfigurationkioskbrowserenablenavigationbuttons"></a>WindowsKioskConfiguration.KioskBrowserEnableNavigationButtons 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/EnableNavigationButtons

### <a name="windowskioskconfigurationkioskbrowserrestartonidletimeinminutes"></a>WindowsKioskConfiguration.KioskBrowserRestartOnIdleTimeInMinutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/KioskBrowser/KioskBrowserRestartOnIdleTimeInMinutes

### <a name="windowsupdateforbusinessconfigurationautomaticupdatemode"></a>WindowsUpdateForBusinessConfiguration.AutomaticUpdateMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/AllowAutoUpdate

### <a name="windowsupdateforbusinessconfigurationautorestartnotificationdismissal"></a>WindowsUpdateForBusinessConfiguration.AutoRestartNotificationDismissal 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/AutoRestartRequiredNotificationDismissal

### <a name="windowsupdateforbusinessconfigurationbusinessreadyupdatesonly"></a>WindowsUpdateForBusinessConfiguration.BusinessReadyUpdatesOnly 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/BranchReadinessLevel

### <a name="windowsupdateforbusinessconfigurationdeliveryoptimizationmode"></a>WindowsUpdateForBusinessConfiguration.DeliveryOptimizationMode 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/DeliveryOptimization/DODownloadMode

### <a name="windowsupdateforbusinessconfigurationdriversexcluded"></a>WindowsUpdateForBusinessConfiguration.DriversExcluded 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/ExcludeWUDriversInQualityUpdate

### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineForFeatureUpdatesInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/EngagedRestartDeadlineForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/EngagedRestartDeadline

### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleForFeatureUpdatesInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/EngagedRestartSnoozeScheduleForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/EngagedRestartSnoozeSchedule

### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleForFeatureUpdatesInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/EngagedRestartTransitionScheduleForFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/EngagedRestartTransitionSchedule

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesDeferralPeriodInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/DeferFeatureUpdatesPeriodInDays

### <a name="windowsupdateforbusinessconfigurationfeatureupdatespaused"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPaused 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/PauseFeatureUpdates

### <a name="windowsupdateforbusinessconfigurationfeatureupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPauseStartDateTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/PauseFeatureUpdatesStartTime

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackStartDateTime
**CSP**: N/A-API do Graph apenas **URI de deslocamento**: Somente API do Graph N/A

### <a name="windowsupdateforbusinessconfigurationfeatureupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesWillBeRolledBack 
**CSP**: N/A-API do Graph apenas **URI de deslocamento**: Somente API do Graph N/A

### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackwindowindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackWindowInDays
**CSP**: N/A-API do Graph apenas **URI de deslocamento**: Somente API do Graph N/A

### <a name="windowsupdateforbusinessconfigurationinstallationschedule"></a>WindowsUpdateForBusinessConfiguration.InstallationSchedule
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/Update/ActiveHoursStart, /Config/Update/ActiveHoursEnd, /Config/Update/ScheduledInstallDay,  /Config/Update/ScheduledInstallTime

### <a name="windowsupdateforbusinessconfigurationmicrosoftupdateserviceallowed"></a>WindowsUpdateForBusinessConfiguration.MicrosoftUpdateServiceAllowed 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/AllowMUUpdateService

### <a name="windowsupdateforbusinessconfigurationpreviewbuildsetting"></a>WindowsUpdateForBusinessConfiguration.PreviewBuildSetting 
**CSP**:./Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/ManagePreviewBuilds

### <a name="windowsupdateforbusinessconfigurationqualityupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesDeferralPeriodInDays 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/DeferQualityUpdatesPeriodInDays

### <a name="windowsupdateforbusinessconfigurationqualityupdatespaused"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPaused 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/PauseQualityUpdates

### <a name="windowsupdateforbusinessconfigurationqualityupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPauseStartDateTime 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/PauseQualityUpdatesStartTime

### <a name="windowsupdateforbusinessconfigurationqualityupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesRollbackStartDateTime
**CSP**: N/A-API do Graph apenas **URI de deslocamento**: Somente API do Graph N/A

### <a name="windowsupdateforbusinessconfigurationqualityupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesWillBeRolledBack 
**CSP**: N/A-API do Graph apenas **URI de deslocamento**: Somente API do Graph N/A

### <a name="windowsupdateforbusinessconfigurationscheduleimminentrestartwarninginminutes"></a>WindowsUpdateForBusinessConfiguration.ScheduleImminentRestartWarningInMinutes 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/ScheduleImminentRestartWarning

### <a name="windowsupdateforbusinessconfigurationschedulerestartwarninginhours"></a>WindowsUpdateForBusinessConfiguration.ScheduleRestartWarningInHours 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/ScheduleRestartWarning

### <a name="windowsupdateforbusinessconfigurationskipchecksbeforerestart"></a>WindowsUpdateForBusinessConfiguration.SkipChecksBeforeRestart 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/SetEDURestart

### <a name="windowsupdateforbusinessconfigurationupdateweeks"></a>WindowsUpdateForBusinessConfiguration.UpdateWeeks 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/ScheduledInstallEveryWeek,/config/Update/ScheduledInstallFirstWeek,/config/Update/ScheduledInstallFourthWeek,/config/Update/ScheduledInstallSecondWeek,/config/Update/ScheduledInstallThirdWeek

### <a name="windowsupdateforbusinessconfigurationuserpauseaccess"></a>WindowsUpdateForBusinessConfiguration.UserPauseAccess 
**CSP**:./Device/Vendor/MSFT/Policy  
**URI de deslocamento**:/config/Update/SetDisablePauseUXAccess


## <a name="next-steps"></a>Passos seguintes

- [Visão geral da configuração do dispositivo](device-profiles.md)
- [Referência do provedor de serviços de configuração](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (abre outro site de documentos)
