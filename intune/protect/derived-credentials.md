---
title: Usar credenciais derivadas para dispositivos móveis no Microsoft Intune-Azure | Microsoft Docs
description: Use credenciais derivadas em dispositivos móveis como um método de autenticação para VPN do Intune, email, perfis de Wi-Fi, aplicativos e S/MIME e criptografia. As credenciais derivadas são uma implementação das diretrizes do NIST para a publicação especial 800-157.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4d0772f9a0afce0607d0193bfb82ea6bd22709d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73445321"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Usar credenciais derivadas no Microsoft Intune

*Este artigo se aplica a dispositivos que executam o iOS*

Em um ambiente em que os cartões inteligentes são necessários para autenticação ou criptografia e assinatura, agora você pode usar o Intune para provisionar dispositivos móveis com um certificado derivado do cartão inteligente de um usuário. Esse certificado é chamado de uma *credencial derivada*. O Intune [dá suporte a vários emissores de credencial derivados](#supported-issuers), embora você possa usar apenas um único emissor por locatário por vez.

As credenciais derivadas são uma implementação das diretrizes do National Institute of Standards and Technology (NIST) para as credenciais de PIV (verificação de identidade pessoal) derivadas como parte da publicação especial (SP) 800-157.

**Com a implementação do Intune**:

- O administrador do Intune configura seu locatário para trabalhar com um emissor de credencial derivada com suporte. Você não precisa definir configurações específicas do Intune no sistema do emissor da credencial derivada.

- O administrador do Intune especifica a **credencial derivada** como o *método de autenticação* para os seguintes objetos:

  - Tipos de perfil comuns como Wi-Fi, VPN e email, que inclui o aplicativo de email nativo do iOS

  - Autenticação de aplicativo

  - Assinatura e criptografia S/MIME

- Os usuários obtêm uma credencial derivada usando seu cartão inteligente em um computador para se autenticarem no emissor de credencial derivada. O emissor então emite para o dispositivo móvel um certificado que é derivado de seu cartão inteligente.

- Depois que o dispositivo recebe a credencial derivada, ele é usado para autenticação e para assinatura S/MIME e criptografia quando os aplicativos ou perfis de acesso a recursos exigem a credencial derivada. 

## <a name="prerequisites"></a>Pré-requisitos

Examine as seguintes informações antes de configurar seu locatário para usar credenciais derivadas.

### <a name="supported-platforms"></a>Plataformas suportadas

O Intune dá suporte a credenciais derivadas nas seguintes plataformas de sistema operacional:

- iOS/iPadOS

### <a name="supported-issuers"></a>Emissores com suporte

O Intune dá suporte a um emissor de credencial derivada único por locatário. Você pode configurar o Intune para trabalhar com os seguintes emissores:

- **Disa purebred**: https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercedam**: https://www.intercede.com/

Para obter detalhes importantes sobre como usar os diferentes emissores, consulte as diretrizes para esse emissor<!-- , including the issuers end-user workflow-->. Para obter mais informações, consulte [Plan for Derived Credentials](#plan-for-derived-credentials) neste artigo.

> [!IMPORTANT]  
> Se você excluir um emissor de credencial derivado do seu locatário, as credenciais derivadas que foram configuradas por meio desse emissor deixarão de funcionar.
>
> Consulte [alterar o emissor de credenciais derivadas](#change-the-derived-credential-issuer) mais adiante neste artigo.

### <a name="company-portal-app"></a>Aplicação Portal da Empresa

Planeje implantar o aplicativo Portal da Empresa do Intune em dispositivos que serão registrados para uma credencial derivada. Os usuários do dispositivo usam o aplicativo Portal da Empresa para iniciar o processo de registro de credenciais.

Para dispositivos iOS, consulte [adicionar aplicativos da loja do Ios ao Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Planejar as credenciais derivadas

Entenda as considerações a seguir antes de configurar um emissor de credencial derivado.

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) examine a documentação do emissor de credencial derivada escolhido  

Antes de configurar um emissor, examine a documentação do emissor para entender como o sistema fornece credenciais derivadas para dispositivos.

Dependendo do emissor escolhido, talvez você precise que a equipe esteja disponível no momento do registro para ajudar os usuários a concluir o processo. Você também deve examinar suas configurações atuais do Intune para garantir que elas não bloqueiem o acesso necessário para que os dispositivos ou usuários concluam a solicitação de credenciais.

Por exemplo, você pode usar o acesso condicional para bloquear o acesso ao email para dispositivos sem conformidade. Se você depender de notificações por email para informar ao usuário para iniciar o processo de registro de credenciais derivadas, os usuários poderão não receber essas instruções até que estejam em conformidade com a política.

Da mesma forma, alguns fluxos de trabalho de solicitação de credenciais derivadas exigem o uso da câmera do dispositivo para verificar um código QR na tela. Esse código vincula esse dispositivo à solicitação de autenticação que ocorreu no emissor de credencial derivada com as credenciais de cartão inteligente do usuário. Se as políticas de configuração de dispositivo bloquearem o uso da câmera, o usuário não poderá concluir a solicitação de registro de credencial derivada.

Informações gerais:

- Você só pode configurar um único emissor por locatário por vez e esse emissor está disponível para todos os usuários e dispositivos com suporte em seu locatário.

- Os usuários não serão notificados de que devem se registrar para as credenciais derivadas até que você as direcione com uma política que exija credenciais derivadas.

- A notificação pode ser por meio de notificação de aplicativo para o Portal da Empresa, por email ou ambos. Se você optar por usar notificações por email e usar o acesso condicional habilitado, os usuários poderão não receber a notificação por email se o dispositivo não estiver em conformidade.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) examine o fluxo de trabalho do usuário final para o emissor escolhido

A seguir estão as principais considerações para cada parceiro com suporte.  Familiarize-se com essas informações para garantir que suas políticas e configurações do Intune não bloqueiem usuários e dispositivos de concluir o registro com êxito para uma credencial derivada desse emissor.

#### <a name="disa-purebred"></a>DISA purebred

Examine o [fluxo de trabalho do usuário para Disa purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Os principais requisitos para esse fluxo de trabalho incluem:

- Os usuários precisam de acesso a um computador ou quiosque, onde podem usar seu cartão inteligente para se autenticarem no emissor.

- Os dispositivos que serão registrados para uma credencial derivada devem instalar o aplicativo Portal da Empresa do Intune.

- Use o Intune para [implantar o aplicativo Disa purebred](#deploy-the-disa-purebred-app) em dispositivos que serão registrados para uma credencial derivada. Esse aplicativo deve ser implantado por meio do Intune para que seja gerenciado e, em seguida, pode trabalhar com o aplicativo Portal da Empresa do Intune. Este aplicativo é usado por usuários do dispositivo para concluir a solicitação de credencial derivada.

- O aplicativo DISA purebred requer uma [VPN por aplicativo](../configuration/vpn-settings-configure.md) para garantir que o aplicativo possa acessar Disa purebred durante o registro para a credencial derivada.

- Os usuários do dispositivo devem trabalhar com um agente ao vivo durante o processo de registro. Durante o registro, são fornecidas senhas de uso único de tempo limitado ao usuário à medida que eles passam pelo processo de registro.

Para obter informações sobre como obter e configurar o aplicativo DISA purebred, consulte [implantar o aplicativo Disa purebred](#deploy-the-disa-purebred-app) mais adiante neste artigo.

#### <a name="entrust-datacard"></a>Entrust Datacard

Examine o [fluxo de trabalho do usuário para Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard). Os principais requisitos para esse fluxo de trabalho incluem:

- Os usuários precisam de acesso a um computador ou quiosque, onde podem usar seu cartão inteligente para se autenticarem no emissor.

- Os dispositivos que serão registrados para uma credencial derivada devem instalar o aplicativo Portal da Empresa do Intune.

- Uso de uma câmera de dispositivo para digitalizar um código QR que vincula a solicitação de autenticação à solicitação de credencial derivada do dispositivo móvel.

#### <a name="intercede"></a>Intercedam

Examine o [fluxo de trabalho do usuário para intercedam](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Os principais requisitos para esse fluxo de trabalho incluem:

- Os usuários precisam de acesso a um computador ou quiosque, onde podem usar seu cartão inteligente para se autenticarem no emissor.

- Os dispositivos que serão registrados para uma credencial derivada devem instalar o aplicativo Portal da Empresa do Intune.

- Uso de uma câmera de dispositivo para digitalizar um código QR que vincula a solicitação de autenticação à solicitação de credencial derivada do dispositivo móvel.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) implantar um certificado raiz confiável em dispositivos

Um certificado raiz confiável é usado com credenciais derivadas para verificar se a cadeia de certificados de credencial derivada é válida e confiável. Mesmo quando não é referenciado diretamente pela política, um certificado raiz confiável é necessário. Consulte [configurar um perfil de certificado para seus dispositivos no Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) fornecer instruções do usuário final sobre como obter a credencial derivada

Crie e forneça orientações para os usuários sobre como iniciar o processo de registro de credenciais derivadas e para navegar pelo fluxo de trabalho de registro de credenciais derivadas para o emissor escolhido.

Recomendamos que você forneça uma URL que hospedará suas diretrizes. Você especifica essa URL ao configurar o emissor de credencial derivada para seu locatário e essa URL é disponibilizada no aplicativo Portal da Empresa. Se você não especificar sua própria URL, o Intune fornecerá um link para detalhes genéricos. Esses detalhes não podem abranger todos os cenários e podem não ser precisos para o seu ambiente.

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) implantar políticas do Intune que exigem credenciais derivadas

Crie novas políticas ou edite as políticas existentes para usar credenciais derivadas. As credenciais derivadas substituem outros métodos de autenticação para autenticação de aplicativo, Wi-Fi, VPN, email e assinatura S/MIME e criptografia.

Evite a necessidade de usar uma credencial derivada para acessar um processo que você usará como parte do processo para obter a credencial derivada, pois isso pode impedir que os usuários concluam a solicitação.

## <a name="set-up-a-derived-credential-issuer"></a>Configurar um emissor de credencial derivada

Antes de criar políticas que exigem o uso de uma credencial derivada, configure um emissor de credencial no console do Intune. Um emissor de credencial derivado é uma configuração de todo o locatário. Os locatários dão suporte a apenas um único emissor por vez.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) and go to **Device Configuration** > **Derived Credentials**.

   ![Configurar credenciais derivadas no console](./media/derived-credentials/configure-provider.png)

2. Especifique um **nome de exibição** amigável para a política de emissor de credencial derivada.  Esse nome não é mostrado para os usuários do dispositivo.

3. Para **emissor de credencial derivada**, selecione o emissor de credencial derivada que você escolheu para seu locatário:
   - DISA purebred
   - Entrust Datacard
   - Intercedam  

4. Especifique uma **URL de ajuda de credencial derivada** para fornecer um link para um local que inclui instruções personalizadas para ajudar os usuários a obter credenciais derivadas para sua organização. As instruções devem ser específicas à sua organização e ao fluxo de trabalho necessário para obter uma credencial do emissor escolhido. O link aparece no aplicativo Portal da Empresa e deve ser acessível a partir do dispositivo.

   Se você não especificar sua própria URL, o Intune fornecerá um link para detalhes genéricos que não podem abranger todos os cenários. Essa orientação genérica pode não ser precisa para o seu ambiente.

5. Selecione uma ou mais opções para **tipo de notificação**. Os tipos de notificação são os métodos que você usa para informar os usuários sobre os seguintes cenários:

   - Enroll a device with an issuer to get a new derived credential.
   - Get a new derived credential when the current credential is close to expiration.
   - Use a derived credential with a policy for Wi-Fi, VPN, email, or app authentication, and for S/MIME signing and encryption.

6. When ready, select **Save** to complete configuration of the derived credential issuer.

After you save the configuration, you can make changes to all fields except for the *Derived credential issuer*.  To change the issuer, see [Change the derived credential issuer](#change-the-derived-credential-issuer).

## <a name="deploy-the-disa-purebred-app"></a>Deploy the DISA Purebred app

*This section applies only when you use DISA Purebred*.

To use **DISA Purebred** as your derived credential issuer for Intune, you must get the DISA Purebred app and then use Intune to deploy the app to devices. Device users use the app on their device to request the derived credential from DISA Purebred.

In addition to the deploying the app with Intune, configure an Intune per-app VPN for the DISA Purebred application.

**Complete the following tasks**:
  
1. Download the [DISA Purebred application](https://cyber.mil/pki-pke/purebred/).
2. Deploy the DISA Purebred application in Intune.  See [Add an iOS line-of-business app to Microsoft Intune](../apps/lob-apps-ios.md).
3. [Create a per-app VPN](../configuration/vpn-settings-configure.md) for the DISA Purebred application.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Use derived credentials for authentication and S/MIME signing and encryption

You can specify **Derived credential** for the following profile types and purposes:

- [Aplicações](#use-derived-credentials-for-app-authentication)
- [E-mail](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME signing and encryption](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  For Wi-Fi profiles, *Authentication method* is available only when the **EAP type** is set to one of the following values:
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Use derived credentials for app authentication

Use derived credentials for certificate-based authentication to web sites and applications. To deliver a derived credential for app authentication, do the following steps in the Intune console:  

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) and go to **Device Configuration** > **Profiles** and select **Create Profile**.

2. Enter a friendly name for the profile under **Name**.

3. Em **Plataforma**, selecione **iOS**.

4. For **Profile type**, select **Derived credential**.

5. Select **OK** and then click **Create**.

6. Select **Assignments** to choose which groups should receive the policy.
 
Users receive the app or email notification depending on the settings you specified when you set up the derived credential issuer. The notification informs the user to launch the Company Portal so that the derived credential policies can be processed.

## <a name="renew-a-derived-credential"></a>Renew a derived credential

Derived credentials can't be extended or renewed. Instead, users must use the credential request workflow to request a new derived credential for their device.

If you configure one or more methods for **Notification type**, Intune automatically notifies users when the current derived credential reaches 80% of its life span. The notification directs users to go through the credential request process to get a new derived credential.

After a device receives a new derived credential, policies that use derived credentials redeploy to that device.


## <a name="change-the-derived-credential-issuer"></a>Change the derived credential issuer

At the tenant level, you can change your credential issuer, although only one issuer is supported for a tenant at a time.

After you change the issuer, users are prompted to get a new derived credential from the new issuer. They must do so before they can use a derived credential for authentication.

### <a name="change-the-issuer-for-your-tenant"></a>Change the issuer for your tenant

> [!IMPORTANT]  
> If you delete an issuer and immediately reconfigure that same issuer, you must still update profiles and devices to use derived credentials from that issuer. Derived credentials that were obtained before you delete the issuer are no longer valid.

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) and go to **Device Configuration** > **Derived Credentials**.

2. Select **Delete** to remove the current derived credential issuer.

3. Configure a new issuer.

### <a name="update-profiles-that-use-derived-credentials"></a>Update profiles that use derived credentials

After you delete an issuer and then add a new one, edit each profile that uses derived credentials. This rule applies even if you restore the previous issuer. Any edit of the profile will trigger an update, including a simple edit to the profile *Description*.

### <a name="update-derived-credentials-on-devices"></a>Update derived credentials on devices

After you delete an issuer and then add a new one, device users must request a new derived credential. This rule applies even when you add the same issuer that you removed. O processo para solicitar a nova credencial derivada é o mesmo para registrar um novo dispositivo ou renovar uma credencial existente.

## <a name="next-steps"></a>Próximos passos

[Criar perfis de configuração de dispositivo](../configuration/device-profile-create.md)
