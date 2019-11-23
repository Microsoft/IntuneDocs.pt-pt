---
title: Integrar o Jamf Pro com o Microsoft Intune para conformidade
titleSuffix: Microsoft Intune
description: Use Microsoft Intune compliance policies with Azure Active Directory Conditional Access to help integrate and secure Jamf-managed devices.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59edb9956ee117e0dbdb9d90a4fd4ef313fd5c66
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390469"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

When your organization uses [Jamf Pro](https://www.jamf.com) to manage macOS devices, you can use Microsoft Intune compliance policies with Azure Active Directory (Azure AD) Conditional Access to ensure devices in your organization are compliant before they can access company resources. This article will help you configure Jamf integration with Intune.

When Jamf Pro integrates with Intune, you can sync the inventory data from macOS devices with Intune, through Azure AD. Intune's compliance engine then analyzes the inventory data to generate a report. Intune's analysis is combined with intelligence about the device user’s Azure AD identity to drive enforcement through Conditional Access. Devices that are compliant with the Conditional Access policies can gain access to protected company resources.

After you configure integration, you'll then [configure Jamf and Intune to enforce compliance with Conditional Access](conditional-access-assign-jamf.md) on devices managed by Jamf.

## <a name="prerequisites"></a>Pré-requisitos

### <a name="products-and-services"></a>Products and services

You need the following to configure Conditional Access with Jamf Pro:

- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- macOS devices with OS X 10.12 Yosemite or later

### <a name="network-ports"></a>Network ports

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
The following ports should be accessible for Jamf and Intune to integrate correctly:

- **Intune**: Port 443
- **Apple**: Ports 2195, 2196, and 5223 (push notifications to Intune)
- **Jamf**: Ports 80 and 5223

To allow APNS to function correctly on the network, you must also enable outgoing connections to, and redirects from:

- the Apple 17.0.0.0/8 block over TCP ports 5223 and 443 from all client networks.
- ports 2195 and 2196 from Jamf Pro servers.  

For more information about these ports, see the following articles:

- [Intune network configuration requirements and bandwidth](../fundamentals/network-bandwidth-use.md).
- [Network Ports Used by Jamf Pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) on jamf.com.
- [TCP and UDP ports used by Apple software products](https://support.apple.com/HT202944) on support.apple.com

## <a name="connect-intune-to-jamf-pro"></a>Connect Intune to Jamf Pro

To connect Intune with Jamf Pro:

1. Create a new application in Azure.
2. Enable Intune to integrate with Jamf Pro.
3. Configure Conditional Access in Jamf Pro.

### <a name="create-an-application-in-azure-active-directory"></a>Create an application in Azure Active Directory

1. In the [Azure portal](https://portal.azure.com), go to **Azure Active Directory** > **App Registrations**, and then select **New registration**.

2. On the **Register an application** page, specify the following details:

   - In the **Name** section, enter a meaningful application name, for example **Jamf Conditional Access**.
   - For the **Supported account types** section, select **Accounts in any organizational directory**.
   - For **Redirect URI**, leave the default of Web, and then specify the URL for your Jamf Pro instance.

3. Select **Register** to create the application and to open the **Overview** page for the new app.

4. On the app **Overview** page, copy the **Application (client) ID** value and record it for later use. You'll need this value in later procedures.

5. Select **Certificates & secrets** under **Manage**. Select the **New client secret** button. Enter a value in **Description**, select any option for **Expires** and choose **Add**.

   > [!IMPORTANT]
   > Before you leave this page, copy the value for the client secret and record it for later use. You will need this value in later procedures. This value isn’t available again, without recreating the app registration.

6. Select **API permissions** under **Manage**. Select the existing permissions and then select **Remove permission** to delete those permissions. Removal of all existing permissions is necessary as you’ll add a new permission, and the application only works if it has the single required permission.

7. To assign a new permission, select **Add a permission**. On the **Request API permissions** page, select **Intune**, and then select **Application permissions**. Select only the check box for **update_device_attributes**.

   Select **Add permission** to save this configuration.

8. On the **API permissions** page, select **Grant admin consent for _\<your tenant>_** , and then select **Yes**.  After the app is registered successfully, the API permissions should appear as follows:

   ![Successful permissions](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   The app registration process in Azure AD is complete.

    > [!NOTE]
    > If the client secret expires, you must create a new client secret in Azure and then update the Conditional Access data in Jamf Pro. Azure allows you to have both the old secret and new key active to prevent service disruptions.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Tenant administration** > **Connectors and tokens** > **Partner device management**.

3. Enable the *Compliance Connector for Jamf* by pasting the Application ID you saved during the previous procedure into the **Specify the Azure Active Directory App ID for Jamf** field.

4. Selecione **Guardar**.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. Activate the connection in the Jamf Pro console:

   1. Open the Jamf Pro console and navigate to **Global Management** > **Conditional Access**. Click the **Edit** button on the **macOS Intune Integration** tab.
   2. Select the check box for **Enable Intune Integration for macOS**.
   3. Provide the required information about your Azure tenant, including **Location**, **Domain name**, the **Application ID**, and the value for the *client secret* that you saved when you created the app in Azure AD.
   4. Selecione **Guardar**. Jamf Pro tests your settings and verifies your success.

   Return to the **Partner device management** page in Intune to complete the configuration.

2. In Intune, go to the **Partner device management** page. Under **Connector Settings** configure groups for assignment:

   - Select **Include** and specify which User groups you want to target for macOS enrollment with Jamf.
   - Use **Exclude** to select groups of Users that won’t enroll with Jamf and instead will enroll their Macs directly with Intune.

   *Exclude* overrides *Include*, which means any device that is in both groups is excluded from Jamf and directed to enroll with Intune.

   >[!NOTE]
   > This method of including and excluding user groups affects the enrollment experience of the user. Any user with a Mac thats already enrolled in either Jamf or Intune who is then targeted to enroll with the other MDM must unenroll their device and then re-enroll it with the new MDM before management of the device works properly.

3. Select **Evaluate** to determine how many devices will be enrolled with Jamf, based on your group configurations.

4. Select **Save** when you’re ready to apply the configuration.

5. To proceed, you will next need to use [Jamf to deploy the Company Portal for Mac](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) so that users can register their devices to Intune.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

After you configure integration between Intune and Jamf, you need to [apply compliance policies to Jamf-managed devices](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Disconnect Jamf Pro and Intune

If you no longer use Jamf Pro to manage Macs in your organization and want users to be managed by Intune, you must remove the connection between Jamf Pro and Intune. Remove the connection by using the Jamf Pro console.

1. In Jamf Pro, go to **Global Management** > **Conditional Access**. On the **macOS Intune Integration** tab, select **Edit**.

2. Clear the **Enable Intune Integration for macOS** check box.

3. Selecione **Guardar**. Jamf Pro sends your configuration to Intune and the integration will be terminated.

4. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Select **Tenant administration** > **Connectors and tokens** > **Partner device management** to verify that the status is now **Terminated**.

   > [!NOTE]
   > Your organization's Mac devices will be removed at the date (3 months) shown in your console.

## <a name="next-steps"></a>Próximos passos

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)
- [Data Jamf sends to Intune](data-jamf-sends-to-intune.md)
