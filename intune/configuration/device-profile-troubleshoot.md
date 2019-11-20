---
title: Resolução de problemas de perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Common questions and answers with device policies and profiles, including profile changes not applied to users or devices, how long it takes for new policies to be pushed to devices, which settings are applied when there are multiple policies, what happens when a profile is deleted or removed, and more with Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a1177a37ddbfa7f760339c4ad0cd7773d670540
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199195"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Common questions, issues, and resolutions with device policies and profiles in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Get answers to common questions when working with device profiles and policies in Intune. This article also lists the check-in time intervals, provides more detains on conflicts, and more.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que razão um utilizador não obtém um novo perfil quando altera uma palavra-passe ou frase de acesso num perfil de Wi-Fi existente?

Suponhamos que cria um perfil de Wi-Fi empresarial, implementa o perfil num grupo, altera a palavra-passe e guarda o perfil. Quando o perfil é alterado, alguns utilizadores podem não receber o novo perfil.

Para mitigar este problema, configure o Wi-Fi de convidado. Se o Wi-Fi empresarial falhar, os utilizadores podem ligar-se ao Wi-Fi de convidado. Certifique-se de que ativa todas as definições de ligação automática. Implemente o perfil de Wi-Fi convidado para todos os utilizadores.

Algumas recomendações adicionais:  

- If the Wi-Fi network you're connecting to uses a password or passphrase, make sure you can connect to the Wi-Fi router directly. Pode testar com um dispositivo iOS.
- Depois de se ligar com êxito ao ponto final do Wi-Fi (router do Wi-Fi), tenha em atenção o SSID e a credencial utilizados (este valor será a palavra-passe ou a frase de acesso).
- Introduza o SSID e a credencial (palavra-passe ou frase de acesso) no campo Chave Pré-partilhada. 
- Implemente num grupo de teste com um número de utilizadores limitado, preferencialmente apenas a equipa de TI. 
- Sincronize o seu dispositivo iOS com o Intune. Inscreva-o caso ainda não o tenha feito. 
- Tente ligar-se novamente ao mesmo ponto final do Wi-Fi (como mencionado no primeiro passo).
- Implemente em grupos maiores e, por fim, em todos os utilizadores esperados na sua organização. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>How long does it take for devices to get a policy, profile, or app after they are assigned?

Intune notifies the device to check in with the Intune service. The notification times vary, including immediately up to a few hours. These notification times also vary between platforms.

If a device doesn't check in to get the policy or profile after the first notification, Intune makes three more attempts. An offline device, such as turned off, or not connected to a network, may not receive the notifications. In this case, the device gets the policy or profile on its next scheduled check-in with the Intune service, which is **estimated** at:

| Platform | Ciclo de atualização|
| --- | --- |
| iOS | About every 8 hours |
| macOS | About every 8 hours |
| Android | About every 8 hours |
| PCs com o Windows 10 inscritos como dispositivos | About every 8 hours |
| Windows Phone | About every 8 hours |
| Windows 8.1 | About every 8 hours |

If the device recently enrolled, the compliance and configuration check-in runs more frequently, which is **estimated** at:

| Platform | Frequência |
| --- | --- |
| iOS | Every 15 minutes for 1 hour, and then around every 8 hours |  
| macOS | Every 15 minutes for 1 hour, and then around every 8 hours | 
| Android | Every 3 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 
| PCs com o Windows 10 inscritos como dispositivos | Every 3 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 
| Windows Phone | Every 5 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 
| Windows 8.1 | Every 5 minutes for 15 minutes, then every 15 minutes for 2 hours, and then around every 8 hours | 

At any time, users can open the Company Portal app, **Settings** > **Sync** to immediately check for policy or profile updates.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?

There are different actions that trigger a notification, such as when a policy, profile, or app is assigned (or unassigned), updated, deleted, and so on. These action times vary between platforms.

Devices check in with Intune when they receive a notification to check in, or during the scheduled check-in. When you target a device or user with an action, such as lock, passcode reset, app, profile or policy assignment, then Intune immediately notifies the device to check in to receive these updates.

Other changes, such as revising the contact information in the Company Portal app, don't cause an immediate notification to devices.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se forem atribuídas várias políticas ao mesmo utilizador ou dispositivo, como posso saber que definições serão aplicadas?

When two or more policies are assigned to the same user or device, then the setting that applies happens at the individual setting level:

- Compliance policy settings always have precedence over configuration profile settings.

- If a compliance policy evaluates against the same setting in another compliance policy, then the most restrictive compliance policy setting applies.

- If a configuration policy setting conflicts with a setting in another configuration policy, this conflict is shown in Intune. Deve resolver estes conflitos manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicações estão em conflito entre si? Qual delas é aplicada na aplicação?

Conflict values are the most restrictive settings available in an app protection policy *except* for the number entry fields, such as PIN attempts before reset. The number entry fields are set the same as the values, as if you created a MAM policy using the recommended settings option.

Conflicts happen when two profile settings are the same. Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar. Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

A policy is deployed to the app and takes effect. A second policy is deployed. In this scenario, the first policy takes precedence, and stays applied. The second policy shows a conflict. If both are applied at the same time, meaning that there isn't preceding policy, then both are in conflict. As definições em conflito são definidas para os valores mais restritivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando políticas personalizadas do iOS entram em conflito?

O Intune não avalia o payload dos ficheiros do Apple Configurator nem de políticas OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizadas. Serve apenas como o mecanismo de entrega.

When you assign a custom policy, confirm that the configured settings don't conflict with compliance, configuration, or other custom policies. If a custom policy and its settings conflict, then the settings are applied randomly.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é eliminado ou deixa de ser aplicável?

When you delete a profile, or you remove a device from a group that has the profile, then the profile and settings are removed from the device as described:

- Perfis de Wi-Fi, VPN, certificado e e-mail: estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de perfil:  

  - **Windows and Android devices**: Settings aren't removed from the device
  - **Dispositivos Windows Phone 8.1**: as definições seguintes são removidas:  
  
    - Palavra-passe obrigatória para desbloquear os dispositivos móveis
    - Permitir palavras-passe simples
    - Comprimento mínimo da palavra-passe
    - Tipo obrigatório de palavra-passe
    - Expiração da palavra-passe (dias)
    - Memorizar histórico de palavras-passe
    - Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado
    - Minutos de inatividade antes da palavra-passe ser exigida
    - Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres
    - Permitir câmara
    - Encriptação obrigatória no dispositivo móvel
    - Permitir armazenamento amovível
    - Permitir browser
    - Permitir loja de aplicações
    - Permitir captura de ecrã
    - Permitir geolocalização
    - Permitir conta Microsoft
    - Permitir copiar e colar
    - Permitir tethering Wi-Fi
    - Permitir ligação automática a hotspots Wi-Fi
    - Permitir relatórios de hotspots Wi-Fi
    - Permitir a limpeza
    - Permitir Bluetooth
    - Permitir NFC
    - Permitir Wi-Fi

  - **iOS**: todas as definições são removidas, exceto:
  
    - Permitir chamadas em roaming
    - Permitir roaming de dados
    - Permitir sincronização automática em roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Alterei um perfil de restrição de dispositivos, mas as alterações ainda não foram aplicadas

Once set, Windows Phone devices don't allow security policies set using MDM or EAS to be reduced in security. For example, you set a **Minimum number of character password** to 8. You try to reduce it to 4. The more restrictive profile is already applied to the device.

To change the profile to a less secure value, then reset security policies. For example, in Windows 8.1, on the desktop, swipe in from right > select **Settings** > **Control Panel**. Selecione a miniaplicação **Contas de Utilizador** . In the left-hand navigation menu, there's a **Reset Security Policies** link (toward the bottom). Selecione-a e, em seguida, selecione **Repor Políticas**.

Other MDM devices, such as Android, Windows Phone 8.1 and later, iOS, and Windows 10 may need to be retired, and re-enrolled in to Intune to apply a less restrictive profile.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Some settings in a Windows 10 profile return "Not Applicable"

Some settings on Windows 10 devices may show as "Not Applicable". When this happens, that specific setting isn't supported on the version or edition of Windows running on the device. This message can occur for the following reasons:

- The setting is only available for newer versions of Windows, and not the current operating system (OS) version on the device.
- The setting is only available for specific Windows editions or specific SKUs, such as Home, Professional, Enterprise, and Education.

To learn more about the version and SKU requirements for the different settings, see the [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Próximos passos

Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
