---
title: Configure Email settings for iOS devices in Microsoft Intune - Azure | Microsoft Docs
description: See a list of all the email settings you can configure and add to iOS devices in Microsoft Intune, including using Exchange servers, and getting attributes from Azure Active Directory. You can also enable SSL, authenticate users with certificates or username/password, and synchronize email on iOS devices using device configuration profiles in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73de0ac94ff02e43fe73ca6357f6008ba71e3b93
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390825"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Add e-mail settings for iOS devices in Microsoft Intune

In Microsoft Intune, you can create and configure email to connect to an email server, choose how users authenticate, use S/MIME for encryption, and more.

This article lists and describes all the email settings available for devices running iOS. You can create a device configuration profile to push or deploy these email settings to your iOS devices.

## <a name="before-you-begin"></a>Antes de começar

[Create a device configuration profile](../email-settings-configure.md).

> [!NOTE]
> These settings are available for all enrollment types. For more information on the enrollment types, see [iOS enrollment](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Exchange ActiveSync account settings

- **Servidor de e-mail**: introduza o nome de anfitrião do seu servidor Exchange.
- **Nome da conta**: introduza o nome a apresentar da conta de e-mail. Este nome será apresentado nos dispositivos dos utilizadores.
- **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (AAD). O Intune gera de forma dinâmica o nome de utilizador utilizado por este perfil. As opções são:
  - **Nome Principal de Utilizador**: obtém o nome, como `user1` ou `user1@contoso.com`.
  - **Endereço SMTP primário**: obtém o nome no formato de endereço de e-mail, como `user1@contoso.com`
  - **Nome da Conta SAM**: precisa do domínio, como `domain\user1`. Introduza também:  
    - **Origem de nome de domínio do utilizador**: selecione **AAD** (Azure Active Directory) ou **Personalizado**.
      - **AAD**: Get the attributes from Azure AD. Introduza também:
        - **User domain name attribute from AAD**: Choose to get the **Full domain name** (`contoso.com`) or the **NetBIOS name** (`contoso`) attribute of the user.

      - **Custom**: Get the attributes from a custom domain name. Introduza também:
        - **Custom domain name to use**: Enter a value that Intune uses for the domain name, such as `contoso.com` or `contoso`.

- **Atributo de endereço de e-mail do AAD**: selecione como é gerado o endereço de e-mail do utilizador. As opções são:
  - **User principal name**: Use the full principal name as the email address, such as `user1@contoso.com` or `user1`.
  - **Primary SMTP address**: Use the primary SMTP address to sign in to Exchange, such as `user1@contoso.com`.
- **Authentication method**: Choose how users to authenticate to the email server. As opções são:
  - **Certificate**: Select a client SCEP or PKCS certificate profile you previously created to authenticate the Exchange connection. This option provides the most secure and seamless experience for your users.
  - **Username and Password**: Users are prompted to enter their user name and password.
  - **Derived credential**: Use a certificate that’s derived from a user’s smart card. For more information, see [Use derived credentials in Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > A autenticação multifator do Azure não é suportada.
  
- **SSL**: **Ativar** resulta na utilização da comunicação SSL (Secure Sockets Layer) ao enviar e-mails, ao receber e-mails e ao comunicar com o servidor Exchange.
- **OAuth**: **Ativar** resulta na utilização da comunicação Open Authorization (OAuth) ao enviar e-mails, ao receber e-mails e ao comunicar com o Exchange. Se o seu servidor OAuth utilizar a autenticação de certificados, selecione **Certificado** como **Método de autenticação** e inclua o certificado juntamente com o perfil. Caso contrário, selecione **Nome de utilizador e palavra-passe** como **Método de autenticação**. Quando utilizar o OAuth, certifique-se de que:

  - Confirma que sua solução de e-mail suporta OAuth antes de direcionar este perfil para os seus utilizadores. O Office 365 Exchange Online suporta OAuth. O Exchange no Local e outras soluções de parceiro ou de terceiros poderão não suportar OAuth. É possível configurar o Exchange no Local para Autenticação Moderna (veja a mensagem de blogue [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) [Apresentamos a Autenticação Moderna Híbrida para o Exchange no Local]).

    Se o perfil de e-mail utilizar o OAuth e o serviço de e-mail não o suportar, a opção **Reintroduzir a palavra-passe** parecerá não funcionar. Por exemplo, não acontece nada quando o utilizador seleciona **Reintroduzir a palavra-passe** nas definições de dispositivos da Apple.

  - Quando o OAuth está ativado, os utilizadores finais têm uma experiência diferente de início de sessão no e-mail através de "Autenticação moderna" que suporta autenticação multifator (MFA). 

  - Algumas organizações desativam a funcionalidade que permite que os utilizadores finais utilizem o [acesso de gestão personalizada à aplicação](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Neste cenário, o início de sessão através de Autenticação Moderna poderá falhar até que um Administrador crie a aplicação empresarial "Contas iOS" e conceda acesso à aplicação no Azure AD aos utilizadores.

    A ação predefinida é a adição de uma aplicação através da funcionalidade do [Painel de Acesso da Aplicação](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **Adicionar Aplicação** **sem a aprovação empresarial**. Para obter mais informações, veja [Atribuir utilizadores a Aplicações](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quando ativar o OAuth, ocorrerá o seguinte:  
  > 1. Será emitido um novo perfil para os dispositivos já visados.
  > 2. Será novamente pedido aos utilizadores finais que introduzam as respetivas credenciais.

## <a name="exchange-activesync-profile-configuration"></a>Exchange ActiveSync profile configuration

> [!IMPORTANT]
> Configuring these settings deploys a new profile to the device, even when an existing email profile is updated to include these settings. Users are prompted to enter their Exchange ActiveSync account password. These settings take affect when the password is entered.

- **Exchange data to sync**: When using Exchange ActiveSync, choose the Exchange services that are synced on the device: Calendar, Contacts, Reminders, Notes, and Email. As opções são:
  - **All data** (default): Sync is enabled for all services.
  - **Email only**: Sync is enabled for Email only. Sync is disabled for the other services.
  - **Calendar only**: Sync is enabled for Calendar only. Sync is disabled for the other services.
  - **Calendar and Contacts only**: Sync is enabled for Calendar and Contacts only. Sync is disabled for the other services.
  - **Contacts only**: Sync is enabled for Contacts only. Sync is disabled for the other services.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer

- **Allow users to change sync settings**: Choose if users can change the Exchange ActiveSync settings for the Exchange services on the device: Calendar, Contacts, Reminders, Notes, and Email. As opções são:

  - **Yes** (default): Users can change the sync behavior of all services. Choosing **Yes** allows changes to *all* services.
  - **No**: Users can't change the sync settings of all the services. Choosing **No** blocks changes to *all* services.

  > [!TIP]
  > If you configured the **Exchange data to sync** setting to sync only some services, we recommend selecting **No** for this setting. Choosing **No** prevents users from changing the Exchange service that's synced.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer

## <a name="exchange-activesync-email-settings"></a>Exchange ActiveSync email settings

- **S/MIME**: S/MIME uses email certificates that provide extra security to your email communications by signing, encrypting, and decrypting. When you use S/MIME with an email message, you confirm the authenticity of the sender, and the integrity and confidentiality of the message.

  As opções são:

  - **Disable S/MIME** (default): Doesn't use an S/MIME email certificate to sign, encrypt, or decrypt emails.
  - **Enable S/MIME**: Allows users to sign and/or encrypt email in the iOS native mail application. Introduza também:

    - **S/MIME signing enabled**: **Disable** (default) doesn't allow users to digitally sign the message. **Enable** allows users to digitally sign outgoing email for the account you entered. Signing helps users who receive messages be certain that the message came from the specific sender, and not from someone pretending to be the sender.
      - **Allow user to change setting**: **Enable** allows users to change the signing options. **Disable** (default) prevents users from changing the signing, and forces users to use the signing you configured.
      - **Signing certificate type**: Your options:
        - **Not configured**: Intune doesn't update or change this setting.
        - **None**: As an administrator, you don't force a specific certificate. Select this option so users can choose their own certificate.
        - **Derived credential**: Use a certificate that’s derived from a user’s smart card. For more information, see [Use derived credentials in Microsoft Intune](../protect/derived-credentials.md).
        - **Certificates**: Select an existing PKCS or SCEP certificate profile that's used for signing email messages.
      - **Allow user to change setting**: **Enable** allows users to change the signing certificate. **Disable** (default) prevents users from changing the signing certificate, and forces users to use the certificate you configured.

        Esta funcionalidade aplica-se a:  
        - iOS 12 and newer
        - iPadOS 12 and newer

    - **Encrypt by default**: **Enable** encrypts all messages as the default behavior. **Disable** (default) doesn't encrypt all messages as the default behavior.
      - **Allow user to change setting**: **Enable** allows users to change the default encryption behavior. **Disable** prevents users from changing the encryption default behavior, and forces users to use the encryption you configured.

        Esta funcionalidade aplica-se a:  
        - iOS 12 and newer
        - iPadOS 12 and newer

    - **Force per-message encryption**: Per-message encryption allows users to choose which emails are encrypted before being sent.

      **Enable** shows the per-message encryption option when creating a new email. Users can then choose to opt-in or opt-out of per-message encryption. If the **Encrypt by default** setting is also enabled, enabling per-message encryption allows users to opt out of encryption per message.

      **Disable** (default) prevents the per-message encryption option from showing. If the **Encrypt by default** setting is also disabled, enabling per-message encryption allows users to opt in to encryption per message.

      - **Encryption certificate type**: Your options:
        - **Not configured**: Intune doesn't update or change this setting.
        - **None**: As an administrator, you don't force a specific certificate. Select this option so users can choose their own certificate.
        - **Derived credential**: Use a certificate that’s derived from a user’s smart card. For more information, see [Use derived credentials in Microsoft Intune](../protect/derived-credentials.md).
        - **Certificates**: Select an existing PKCS or SCEP certificate profile that's used for signing email messages.
      - **Allow user to change setting**: **Enable** allow users to change the encryption certificate. **Disable** (default) prevents users from changing the encryption certificate, and forces users to use the certificate you configured.

        Esta funcionalidade aplica-se a:  
        - iOS 12 and newer
        - iPadOS 12 and newer

- **Quantidade de e-mails a sincronizar**: selecione o número de dias de e-mails que pretende sincronizar. Em alternativa, selecione **Ilimitada** para sincronizar todos os e-mails disponíveis.
- **Allow messages to be moved to other email accounts**: **Enable** (default) allows users to move email messages between different accounts the users configured on their devices.
- **Allow email to be sent from third-party applications**: **Enable** (default) allows users to select this profile as the default account for sending email. que as aplicações de terceiros abram o e-mail na aplicação de e-mail nativa, por exemplo, para anexar ficheiros ao e-mail.
- **Synchronize recently used email addresses**: **Enable** (default) allows users to synchronize the list of email addresses that have been recently used on the device with the server.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).

Configure email settings on [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md), and [Windows Phone 8.1](email-settings-windows-phone-8-1.md) devices.
