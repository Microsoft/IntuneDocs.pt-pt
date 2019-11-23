---
title: Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Microsoft Intune
titleSuffix: Microsoft Intune
description: Ative o conector entre o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis (MTD) e o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c041941db583542f704477fe2d5389a58007ed0f
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409753"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Ativar o conector da Defesa Contra Ameaças para Dispositivos Móveis no Intune

> [!NOTE]
> Este tópico aplica-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

Durante a configuração da Defesa Contra Ameaças para Dispositivos Móveis (MTD), configurou uma política para classificar ameaças na sua consola do parceiro MTD e criou a política de conformidade de dispositivos no Intune. If you've already configured the Intune connector in the MTD partner console, you can now enable the MTD connection for MTD partner applications.

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Classic conditional access policies for MTD apps

When you integrate a new application to Intune Mobile Threat Defense and enable the connection to Intune, Intune creates a classic conditional access policy in Azure Active Directory. Each MTD app you integrate, including [Defender ATP](advanced-threat-protection.md) or any of our additional [MTD partners](mobile-threat-defense.md#mobile-threat-defense-partners), creates a new classic conditional access policy. These policies can be ignored, but shouldn't be edited, deleted, or disabled.

If the classic policy is deleted, you'll need to delete the connection to Intune that was responsible for its creation, and then set it up again. This process recreates the classic policy. It's not supported to migrate classic policies for MTD apps to the new policy type for conditional access.

Classic conditional access policies for MTD apps:

- Are used by Intune MTD to require that devices are registered in Azure AD so that they have a device ID before communicating to MTD partners. The ID is required so that devices and can successfully report their status to Intune.

- Have no effect on any other Cloud apps or Resources.

- Are distinct from conditional access policies you might create to help manage MTD.

- By default, don’t interact with other conditional access policies you use for evaluation.

To view classic conditional access policies, in [Azure](https://portal.azure.com/#home), go to **Azure Active Directory** > **Conditional Access** > **Classic policies**.

## <a name="to-enable-the-mobile-threat-defense-connector"></a>To enable the Mobile Threat Defense connector

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Tenant administration** > **Connectors and tokens** > **Mobile Threat Defense**.

3. On the **Mobile Threat Defense** pane, select **Add**.

4. For **Mobile Threat Defense connector to setup**, select your MTD solution from the drop-down list.

5. Ative as opções de alternância de acordo com os requisitos da sua organização. As opções de alternância visíveis variam consoante o parceiro MTD.  For example, the following image shows the options that are available for Symantec Endpoint Protection:

   ![Configuração da MTD do Intune no portal do Azure](./media/mtd-connector-enable/enable-mtd-connector-1.png)

## <a name="mobile-threat-defense-toggle-options"></a>Mobile Threat Defense toggle options

You can decide which Mobile Threat Defense toggle options you need to enable according to your organization's requirements. Not all of the following options are supported by all Mobile Thread Defense partners:

**MDM Compliance Policy Settings**

- **Connect Android devices of version _\<supported versions>_ to _\<MTD partner name>_** : When you enable this option, you can have Android 4.1+ devices reporting security risk back to Intune.

- **Connect iOS devices version _\<supported versions>_ to _\<MTD partner name>_** : When you enable this option, you can have iOS 8.0+ devices reporting security risk back to Intune.

- **Ativar Sincronização de Aplicações para Dispositivos iOS**: permite que o parceiro de Defesa Contra Ameaças para Dispositivos Móveis peça metadados de aplicações iOS a partir do Intune para utilizar para fins de análise de ameaças.

- **Bloquear versões do SO não suportadas**: bloquear se o dispositivo estiver a executar um sistema operativo inferior à versão mínima suportada.

**App Protection Policy Settings**

- **Connect Android devices of version *\<supported versions>* to *\<MTD partner name>* for app protection policy evaluation**: When you enable this option, app protection policies using the Device Threat Level rule will evaluate devices including data from this connector.

- **Connect iOS devices version *\<supported versions>* to *\<MTD partner name>* for app protection policy evaluation**: When you enable this option, app protection policies using the Device Threat Level rule will evaluate devices including data from this connector.

To learn more about using Mobile Threat Defense connectors for Intune App Protection Policy evaluation, see [Set up Mobile Threat Defense for unenrolled devices](~/protect/mtd-enable-unenrolled-devices.md).

**Common Shared Settings**

- **Número de dias até o parceiro ficar não responsivo**: número de dias de inatividade antes de o Intune considerar o parceiro como não responsivo devido a perda da ligação. O Intune ignora o estado de conformidade para parceiros MTD não responsivos.

> [!IMPORTANT]
> When possible, we recommend that you add and assign the MTD apps before creating the device compliance and the Conditional Access policy rules. This helps ensures that the MTD app is ready and available for end users to install before they can get access to email or other company resources.

> [!TIP]
> Pode ver o **Estado da ligação** e a hora da **Última sincronização** entre o Intune e o parceiro MTD no painel de Defesa Contra Ameaças para Dispositivos Móveis.
