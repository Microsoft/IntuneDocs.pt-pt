---
title: Configure S/MIME with Outlook for iOS in Microsoft Intune
description: Understand S/MIME with Outlook for iOS in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b2f483415d050486ae9979899d9308154a9b131
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74412017"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Configure S/MIME with Outlook for iOS

Secure/Multipurpose Internet Mail Extensions (S/MIME) provides an added layer of security for email sent to and from an Exchange ActiveSync (EAS) account. [Microsoft Outlook](https://aka.ms/omsmime) can utilize S/MIME to allow users to encrypt both outgoing messages and attachments, ensuring that only the intended recipient can read and access message content when using Office 365 accounts. Users can also digitally sign a message, which allows the recipients to both verify the identity of the sender and confirm that the message hasn't been tampered with. This capability is possible by utilizing certificates. For more information, see [Understanding S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> This topic describes how to deploy trusted root certificates via [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Microsoft Endpoint Manager is a single, integrated endpoint management platform for managing all your endpoints. This Microsoft Endpoint Manager admin center integrates ConfigMgr and Microsoft Intune.

## <a name="about-message-encryption"></a>About message encryption
Users can send encrypted message to people in their organization and people outside their organization if they have the public portion of the encryption certificates. Private keys associated with the encryption certificates should always be protected and secured by the recipient of the encrypted message. The private key of the encryption certificate is used to decrypt the message by the recipient.

Encrypted messages can be read only by recipients who have the certificate corresponding to the one that encrypted the message. If you try to send an encrypted message to recipient(s) whose encryption certificate is not available, the app will prompt you to remove these recipients before sending the email.

## <a name="about-digital-signatures"></a>About digital signatures
A digitally signed message reassures the recipient that the message hasn't been tampered with and the identity of the sender is authentic. Recipients can only verify the digital signature if they’re using an email client that supports S/MIME.

## <a name="prerequisites"></a>Pré-requisitos
- Outlook for iOS only supports S/MIME on Office 365 accounts.
- S/MIME must be configured for Office 365. For more information, see [How to configure S/MIME in Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- You must have a Certification Authority that can issue certificates that can be used for signing and encryption.
- Deploy trusted root certificates via Endpoint Manager. For more information, see [Create trusted certificate profiles](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- Encryption certificates must be imported into Endpoint Manager. For more information, see [Configure and use imported PKCS certificates with Intune](~/protect/certificates-imported-pfx-configure.md).
- Install and Configure the PFX Connector for Microsoft Intune. For more information, see [Download, install, and configure the PFX Certificate Connector for Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Devices must be MDM enrolled to receive trusted root and S/MIME certificates automatically from Endpoint Manager.

> [!IMPORTANT]
> You must download and install the updated PFX connector (version 6.1911.11.0 or later) for Microsoft Intune to use S/MIME encryption certificates with Outlook for iOS.

## <a name="smime-support-in-outlook-for-ios"></a>S/MIME Support in Outlook for iOS
Outlook for iOS supports S/MIME signing and encryption of messages using certificates. Many customers have separate signing and encryption certificates, as opposed to having a single certificate that supports both signing and encryption. Signing certificates are generally unique across an individual user’s enrolled devices, while encryption certificates are shared across an individual user’s enrolled devices. Often, users will have used S/MIME for years and will have used different encryption certificates over time as certificates are renewed. Encryption certificate histories, including their private keys, must be present on the user’s device so that email that may have been encrypted with any of those certificates in the past can be read. It is also possible to have a single certificate that supports signing and encryption.

Outlook for iOS supports two ways to deliver certificates to devices so that they can be used for S/MIME:

- **Users** can email S/MIME certificates to themselves and install them from attachments within Outlook for iOS on their mobile devices.
- **Administrators** can import encryption certificate histories from any Certification Authority to Endpoint Manager. Endpoint Manager will then automatically deliver those certificates to any device that the user enrolls. Generally, Simple Certificate Enrollment Protocol (SCEP) is used for signing certificates. With SCEP, the private key is generated and stored on the enrolled device and a unique certificate is delivered to each device that a user enrolls, which can be used for non-repudiation. Administrators import encryption certificate histories for their users to Endpoint Manager, which then delivers all of the user’s encryption certs to any device they enroll. Lastly, Endpoint Manager supports derived credentials for customers who need support for the NIST 800-157 standard. On iOS, the Company Portal is used to retrieve signing and encryption certificates from Intune.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Configuring Outlook for iOS S/MIME in Endpoint Manager
To configure Outlook for iOS S/MIME in Endpoint Manager, including automatically delivering S/MIME certificates that Outlook for iOS can use, use the following steps:

### <a name="add-the-microsoft-outlook-app"></a>Add the Microsoft Outlook app
1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Add the Microsoft Outlook for iOS app from the app store to Endpoint Manager or sync Outlook for iOS from the Apple Volume Purchase Program. For more information, see [Add iOS store apps to Microsoft Intune](~/apps/store-apps-ios.md) or [How to manage iOS and macOS apps purchased through Apple Volume Purchase Program with Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Create the Outlook for iOS S/MIME configuration policy

The following steps allow you to create and configure the Outlook for iOS S/MIME policy in Endpoint Manager. These settings provide automated delivery of the signing and encryption certificates.

1. In [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** > **Apps configuration policies** > **Add**.<br>
The **Add configuration policy** pane will be displayed.
2. Enter the **Name** and **Description** of the configuration policy.
3. Select **Managed devices** as the **Device enrollment type**.
4. Select **iOS/iPadOS** as the **Platform**.
5. Click **Select the required app** to find and associate the Microsoft Outlook for iOS app that you added previously. 
6. Click **Configuration settings** to add configuration settings. 
    - Select **Use configuration designer** next to **Configuration settings format** and accept the default settings. For more information, see [Microsoft Outlook configuration settings](~/apps/app-configuration-policies-outlook.md).
7. Click **S/MIME** to display the **Outlook S/MIME settings**.

    ![Screenshot of Outlook for iOS S/MIME settings](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. Set **Enable S/MIME** to **Yes**.
9. Set **Deploy S/MIME certificates from Intune** to **Yes**.
10. Under **Signing certificates** next to **Certificate profile type**, choose one of the following options:
    - **SCEP** – Creates a certificate that is unique for the device and user that can be used by Microsoft Outlook for signing. For related information, see [Configure infrastructure to support SCEP with Intune](~/protect/certificates-scep-configure.md) and [Create a SCEP certificate profile](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **PKCS imported certificates** – Uses a certificate that is unique to the user, but may be shared across devices and has been imported to Endpoint Manager by the administrator on behalf of the user. The certificate is delivered to any device that a user enrolls. Endpoint Manager will automatically pick the imported certificate that supports signing to deliver to the device the corresponds to the enrolled user.
    - **Derived credentials** – Uses a certificate that is already on the device that can be used for signing. The certificate must be retrieved on the device using the derived credentials flows in Intune.
11. Under **Encryption certificates** next to **Certificate profile type**, choose one of the following options:
    - **PKCS imported certificates** – Delivers any encryption certificates that have been imported to Endpoint Manager by the administrator across any device a user enrolls Endpoint Manager will automatically pick the imported certificate or certificates that support encryption to deliver to the device that corresponds to the enrolled user.
    - **Derived credentials** – Uses a certificate that is already on the device that can be used for signing. The certificate must be retrieved on the device using the derived credentials flows in Intune.
12. Next to **End-user notifications**, choose notify end users by selecting **Company Portal** or **Email** to retrieve S/MIME certificates for Outlook for iOS.

    On iOS, users must use the Company Portal app to retrieve their S/MIME certificates. Endpoint Manager will inform the user that they need to launch the Company Portal to retrieve their S/MIME certificates via the Notifications section of Company Portal, a push notification, and/or an email. Clicking one of the notifications will take the user to a landing page that informs them of progress retrieving the certificates. Once the certificates are retrieved, the user can use S/MIME from within Microsoft Outlook for iOS to sign and encrypt email.
    
    The end-user notifications include the following options:
       - **Company Portal** – If selected, users will receive a push notification on their device, which will take them to the landing page in Company Portal where S/MIME certificates will be retrieved.
        - **Email** – Sends an email to the end user informing them that they need to launch Company Portal to retrieve their S/MIME certificates. If the user is on their enrolled iOS device when they click the link in the email, they will be redirected to the Company Portal to retrieve their certificates.
    
13. Select **Assignments** to assign the app configuration policy to the Azure AD groups. Para obter mais informações, veja [Atribuir aplicações a grupos com o Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Próximos passos

- For more information, see [App configuration policies for Microsoft Intune](app-configuration-policies-overview.md).
