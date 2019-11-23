---
title: Use Microsoft Defender ATP in Microsoft Intune - Azure | Microsoft Docs
description: Use Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) with Intune, including setup and configuration, onboarding of your Intune devices with ATP, and then use a devices ATP risk assessment with your Intune device compliance and conditional access policies to protect network resources.
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
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8c756ad2df00a97df7289491daf830e584c0045
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410201"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Enforce compliance for Microsoft Defender ATP with Conditional Access in Intune

You can integrate Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) with Microsoft Intune as a Mobile Threat Defense solution. Integration can help you prevent security breaches and limit the impact of breaches within an organization. Microsoft Defender ATP works with devices that run Windows 10 or later.

To be successful, you use the following configurations in concert:

- **Establish a service-to-service connection between Intune and Microsoft Defender ATP**. This connection lets Microsoft Defender ATP collect data about machine risk from Windows 10 devices you manage with Intune.
- **Use a device configuration profile to onboard devices with Microsoft Defender ATP**. You onboard devices to configure them to communicate with Microsoft Defender ATP and to provide data that helps assess their risk level.
- **Use a device compliance policy to set the level of risk you want to allow**. Risk levels are reported by Microsoft Defender ATP. Devices that exceed the allowed risk level are identified as non-compliant.
- **Use a conditional access policy** to block users from accessing corporate resources from devices that are non-compliant.

When you integrate Intune with Microsoft Defender ATP, you can take advantage of ATPs Threat & Vulnerability Management (TVM) and [use Intune to remediate endpoint weakness identified by TVM](atp-manage-vulnerabilities.md).

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Example of using Microsoft Defender ATP with Intune

The following example helps explain how these solutions work together to help protect your organization. For this example, Microsoft Defender ATP and Intune are already integrated.

Consider an event where someone sends a Word attachment with embedded malicious code to a user within your organization.

- O utilizador abre o anexo e ativa o conteúdo.
- É iniciado um ataque de privilégios elevados e o atacante tem direitos de administrador no dispositivo da vítima a partir de um computador remoto.
- O atacante, em seguida, acede remotamente aos outros dispositivos do utilizador. Esta falha de segurança pode afetar toda a organização.

Microsoft Defender ATP can help resolve security events like this scenario.

- In our example, Microsoft Defender ATP detects that the device executed abnormal code, experienced a process privilege escalation, injected malicious code, and issued a suspicious remote shell.
- Based on these actions from the device, Microsoft Defender ATP [classifies the device as high-risk](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity) and includes a detailed report of suspicious activity in the Microsoft Defender Security Center portal.

Because you have an Intune device compliance policy to classify devices with a *Medium* or *High* level of risk as non-compliant, the compromised device is classified as non-compliant. This classification allows your conditional access policy to kick in and block access from that device to your corporate resources.

## <a name="prerequisites"></a>Pré-requisitos

To use Microsoft Defender ATP with Intune, be sure you have the following configured, and ready for use:

- Um inquilino com licença para o Enterprise Mobility + Security E3 e o Windows E5 (ou Microsoft 365 Enterprise E5)
- O ambiente do Microsoft Intune, com dispositivos Windows 10 [geridos pelo Intune](../enrollment/windows-enroll.md) que também estão associados ao Azure AD
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) and access to the Microsoft Defender Security Center (ATP portal)

> [!NOTE]
> Microsoft Defender ATP is not supported with iOS and Android Intune app protection policies.

## <a name="enable-microsoft-defender-atp-in-intune"></a>Enable Microsoft Defender ATP in Intune

The first step you take is to set up the service-to-service connection between Intune and Microsoft Defender ATP. This requires administrative access to both the Microsoft Defender Security Center, and to Intune.

### <a name="to-enable-defender-atp"></a>To enable Defender ATP

You only need to enable Defender ATP a single time per tenant.

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Endpoint security** > **Microsoft Defender ATP**, and then select **Open the Microsoft Defender Security Center**.

   ![Select to open the Microsoft Defender Security Center](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. In **Microsoft Defender Security Center**:
    1. Selecione **Definições** > **Funcionalidades avançadas**.
    2. Em **Ligação do Microsoft Intune**, escolha **Ligado**:

        ![Ativar a ligação ao Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Selecione **Guardar preferências**.

4. Return to **Microsoft Defender ATP** in the Microsoft Endpoint Manager Admin Center. Under **MDM Compliance Policy Settings**, set **Connect Windows devices version 10.0.15063 and above to Microsoft Defender ATP** to **On**.

5. Selecione **Guardar**.

> [!TIP]
> When you integrate a new application to Intune Mobile Threat Defense and enable the connection to Intune, Intune creates a classic conditional access policy in Azure Active Directory. Each MTD app you integrate, including [Defender ATP](advanced-threat-protection.md) or any of our additional [MTD partners](mobile-threat-defense.md#mobile-threat-defense-partners), creates a new classic conditional access policy. These policies can be ignored, but should not be edited, deleted, or disabled.
>
> If the classic policy is deleted, you will need to delete the connection to Intune that was responsible for its creation, and then set it up again. This recreates the classic policy. Its not supported to migrate classic policies for MTD apps to the new policy type for conditional access.
>
> Classic conditional access policies for MTD apps:
>
> - Are used by Intune MTD to require that devices are registered in Azure AD so that they have a device ID before communicating to MTD partners. The ID is required so that devices and can successfully report their status to Intune.
> - Have no effect on any other Cloud apps or Resources.
> - Are distinct from conditional access policies you might create to help manage MTD.
> - By default, don’t interact with other conditional access policies you use for evaluation.
>
> To view classic conditional access policies, in [Azure](https://portal.azure.com/#home), go to **Azure Active Directory** > **Conditional Access** > **Classic policies**.

## <a name="onboard-devices-by-using-a-configuration-profile"></a>Onboard devices by using a configuration profile

After you establish the service-to-service connection between Intune and Microsoft Defender ATP, you onboard your Intune managed devices to ATP so that data about their risk level can be collected and used. To onboard devices, you use a device configuration profile for Microsoft Defender ATP.

When you established the connection to Microsoft Defender ATP, Intune received a Microsoft Defender ATP onboarding configuration package from Microsoft Defender ATP. This package is deployed to devices with the device configuration profile. The configuration package configures devices to communicate with [Microsoft Defender ATP services](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) to scan files, detect threats, and report the risk to Microsoft Defender ATP.

After you onboard a device using configuration package, you don't need to do it again. Também pode carregar dispositivos através de uma [política de grupo ou o System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="create-the-device-configuration-profile"></a>Create the device configuration profile

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration profiles** > **Create profile**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e versões posteriores**
5. For **Profile type**, select **Microsoft Defender ATP (Windows 10 Desktop)** .
6. Configure as definições:

   - **Microsoft Defender ATP client configuration package type**: Select **Onboard** to add the configuration package to the profile. Selecione **Descarregar** para remover o pacote de configuração do perfil.
  
     > [!NOTE]
     > If you've properly established a connection with Microsoft Defender ATP, Intune will automatically **Onboard** the configuration profile for you, and the **Microsoft Defender ATP client configuration package type** setting will not be available.
  
   - **Sample sharing for all files**: **Enable** allows samples to be collected, and shared with Microsoft Defender ATP. For example, if you see a suspicious file, you can submit it to Microsoft Defender ATP for deep analysis. **Not configured** doesn't share any samples to Microsoft Defender ATP.
   - **Expedite telemetry reporting frequency**: For devices that are at high risk, **Enable** this setting so it reports telemetry to the Microsoft Defender ATP service more frequently.

     [Onboard Windows 10 machines using System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) has more details on these Microsoft Defender ATP settings.

7. Selecione **OK** e **Criar** para guardar as alterações. O perfil será criado.
8. [Assign the device configuration profile](../configuration/device-profile-assign.md) to devices you want to assess with Microsoft Defender ATP.

## <a name="create-and-assign-the-compliance-policy"></a>Create and assign the compliance policy

The compliance policy determines the level of risk that you consider as acceptable for a device.

### <a name="create-the-compliance-policy"></a>Criar a política de conformidade

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Compliance policies** > **Create policy**.
3. Introduza um **Nome** e uma **Descrição**.
4. Em **Plataforma**, selecione **Windows 10 e posterior**.
5. Under **Settings**, select **Microsoft Defender ATP**.
6. Set **Require the device to be at or under the machine risk score** to your preferred level.

   Threat level classifications are [determined by Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Seguro**: este é o nível mais seguro. The device can't have any existing threats and still access company resources. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme. (Microsoft Defender ATP users the value *Secure*.)
   - **Baixo**: o dispositivo estará em conformidade se só existirem ameaças de nível baixo. Devices with medium or high threat levels aren't compliant.
   - **Médio**: o dispositivo estará conforme se as ameaças encontradas no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
   - **High**: This level is the least secure and allows all threat levels. So devices that with high, medium, or low threat levels are considered compliant.

7. Selecione **OK** e **Criar** para guardar as alterações (e criar o perfil).
8. [Assign the device compliance policy](create-compliance-policy.md#assign-the-policy) to applicable groups.

## <a name="create-a-conditional-access-policy"></a>Create a Conditional Access policy

The Conditional Access policy blocks access to resources for devices that exceed the threat level you set in your compliance policy. You can block access from the device to corporate resources, such as SharePoint or Exchange Online.

> [!TIP]
> O Acesso Condicional é uma tecnologia do Azure Active Directory (Azure AD). The Conditional Access node accessed from the Microsoft Endpoint Manager Admin Center is the same node as accessed from *Azure AD*.

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Endpoint security** > **Conditional Access** > **New policy**.

3. Introduza um **Nome** para a política e selecione **Utilizadores e grupos**. Utilize as opções Incluir ou Excluir para adicionar os grupos à política e selecione **Concluído**.

4. Selecione **Aplicações na cloud** e escolha as aplicações que quer proteger. Por exemplo, escolha **Selecionar aplicações** e selecione **Office 365 SharePoint Online** e **Office 365 Exchange Online**.

   Selecione **Concluído** para guardar as alterações.

5. Selecione **Condições** > **Aplicações do cliente** para aplicar a política a aplicações e browsers. Por exemplo, selecione **Sim** e, em seguida, ative **Browser** e **Aplicações móveis e clientes de ambiente de trabalho**.

   Selecione **Concluído** para guardar as alterações.

6. Select **Grant** to apply Conditional Access based on device compliance. Por exemplo, selecione **Conceder acesso** > **Pedir que o dispositivo seja marcado como conforme**.

    Escolha **Selecionar** para guardar as alterações.

7. Selecione **Ativar política** e, em seguida, **Criar** para guardar as alterações.

## <a name="monitor-device-compliance"></a>Monitorizar a conformidade do dispositivo

Next, monitor the state of devices that have the Microsoft Defender ATP compliance policy.

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Monitor** > **Policy compliance**.

3. Find your Microsoft Defender ATP policy in the list, and see which devices are compliant or noncompliant.

You can also use the *operational* report for noncompliant devices from the same location:

1. Select **Devices** > **Monitor** > **Noncompliant devices**.

For more information about reports, see [Intune reports](../fundamentals/reports.md).

## <a name="view-onboarding-status"></a>View onboarding status

To view the onboarding status of all Intune-managed Windows 10 devices, you can go to **Device compliance** > **Microsoft Defender ATP**. From this page, you can also initiate the creation of a device configuration profile for onboarding more devices to Microsoft Defender ATP.

## <a name="next-steps"></a>Próximos passos

[Microsoft Defender ATP Conditional Access](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)

[Microsoft Defender ATP risk dashboard](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)

[Use security tasks with ATPs Vulnerability Management to remediate issues on devices](atp-manage-vulnerabilities.md).

[Introdução às políticas de conformidade de dispositivos](device-compliance-get-started.md)
