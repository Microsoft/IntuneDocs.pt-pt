---
title: Adicionar e atribuir aplicações de MTD ao Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize o Intune para adicionar aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis), a aplicação Microsoft Authenticator e a política de configuração para iOS no portal do Azure.
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
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efdb1912fdbb2f28c6859fae4407116173daa99d
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576287"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Adicionar e atribuir aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis) com o Intune

Pode utilizar o Intune para adicionar e implementar aplicações de Defesa de Ameaças Móveis (MTD) para que os utilizadores finais possam receber notificações quando uma ameaça é identificada nos seus dispositivos móveis, e receber orientações para remediar as ameaças.

> [!NOTE]
> Este artigo aplica-se a todos os parceiros de Defesa de Ameaças Móveis.

## <a name="before-you-begin"></a>Antes de começar

Complete os seguintes passos em Intune. Verifique se está familiarizado com o processo de:

- [Adicionar uma aplicação no Intune](../apps/apps-add.md).
- [Adicionar uma política de configuração de aplicações iOS no Intune](../apps/app-configuration-policies-use-ios.md).
- [Atribuir uma aplicação com o Intune](../apps/apps-deploy.md).

> [!TIP]
> O Intune Company Portal funciona como corretor em dispositivos Android para que os utilizadores possam ter as suas identidades verificadas pela Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Configurar o Microsoft Authenticator para iOS

Para os dispositivos iOS, precisa do [Microsoft Authenticator ](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) para que a identidade dos utilizadores seja verificada pelo Azure AD. Além disso, precisa de uma política de configuração de aplicações iOS que define a aplicação iOS MTD que utiliza com o Intune.

Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL da loja de [aplicações Do Autenticador microsoft](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) quando configurar **as informações da App**.

## <a name="configure-mtd-applications"></a>Configurar as aplicações de MTD

Selecione a secção que corresponde ao seu fornecedor de MTD:

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Configurar as aplicações Lookout for Work

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [Lookout para trabalho google app store URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) para o URL **appstore**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações iOS](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) para o URL da **appstore**.

- **Aplicação Lookout for Work fora da Apple Store**
  - Deve voltar a assinar a aplicação Lookout for Work iOS. A Lookout faz a distribuição da respetiva aplicação Lookout for Work para iOS fora da iOS App Store. Antes de distribuir a aplicação, tem de voltar a assinar a aplicação com o seu iOS Enterprise Developer Certificate.  
  - Para obter instruções detalhadas sobre como voltar a assinar a aplicação Lookout for Work para iOS, veja [Lookout for Work iOS app re-signing process (Processo de nova assinatura da aplicação Lookout for Work para iOS)](https://personal.support.lookout.com/hc/articles/114094038714) no site do Lookout.

  - **Ativar a autenticação do Azure AD para os utilizadores da aplicação Lookout for Work para iOS.**

    1. Aceda ao [portal do Azure](https://portal.azure.com), inicie sessão com as suas credenciais e, em seguida, navegue para a página da aplicação.

    2. Adicione a **aplicação Lookout for Work para iOS** como uma **aplicação de cliente nativo**.

    3. Substitua o valor **com.lookout.enterprise.onomedasuaempresa** pelo ID de pacote de cliente que selecionou quando assinou o IPA.

    4. Adicione o URI de redirecionamento adicional: **&lt;companyportal://code/>** seguido de uma versão com codificação URL do seu URI de redirecionamento original.

    5. Adicione **Permissões Delegadas** à sua aplicação.

    > [!NOTE]
    > Veja [Configurar uma aplicação cliente nativa com o Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) para obter mais detalhes.

  - **Adicionar o ficheiro .ipa do Lookout for Work.**

    - Faça upload do ficheiro .ipa re-assinado, conforme descrito nas [aplicações Add iOS LOB com artigo Intune.](../apps/lob-apps-ios.md) Também tem de definir a versão mínima do SO para o iOS 8.0 ou versões posteriores.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Configurar as aplicações do Symantec Endpoint Protection Mobile

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure) para o URL da **Appstore**.  Para o **Sistema operativo mínimo**, selecione **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações SEP Mobile](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) para o URL da **Appstore**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Configurar as aplicações do Check Point SandBlast Mobile

- **Android**  
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações Check Point SandBlast Mobile](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) para o URL da **Appstore**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações Check Point SandBlast Mobile](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) para o URL da **Appstore**.  

### <a name="configure-zimperium-apps"></a>Configurar as aplicações do Zimperium

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) para o URL da **Appstore**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) para o URL da **Appstore**.  
 
### <a name="configure-pradeo-apps"></a>Configurar as aplicações do Pradeo

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações Pradeo](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) para o URL da **Appstore**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações Pradeo](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) para o URL da **Appstore**.

### <a name="configure-better-mobile-apps"></a>Configurar aplicações do Better Mobile

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações Ative Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) para o URL da **Appstore**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações ActiveShield](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) para o URL da **Appstore**.

### <a name="configure-sophos-apps"></a>Configure aplicativos Sophos

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações Sophos](https://play.google.com/store/apps/details?id=com.sophos.smsec) para o URL da **Appstore**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações ActiveShield](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) para o URL da **Appstore**.

### <a name="configure-wandera-apps"></a>Configure aplicativos Wandera

- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este URL de loja de [aplicações Wandera Mobile](https://play.google.com/store/apps/details?id=com.wandera.android) para o URL da **Appstore**. Para **sistema operativo mínimo,** selecione **Android 5.0**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este URL de loja de [aplicações Wandera Mobile](https://itunes.apple.com/app/wandera/id605469330) para o URL da **Appstore**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Configurar as aplicações de MTD com uma política de configuração de aplicações iOS

### <a name="lookout-for-work-app-configuration-policy"></a>Política de configuração da aplicação Lookout for Work

Crie a política de configuração de aplicações iOS, tal como descrito no artigo de política de configuração de [aplicações iOS.](../apps/app-configuration-policies-use-ios.md)

### <a name="sep-mobile-app-configuration-policy"></a>Política de configuração da aplicação SEP Mobile

Utilize a mesma conta Azure AD previamente configurada na [consola Symantec Endpoint Protection Management](https://aad.skycure.com), que deve ser a mesma conta utilizada para iniciar sessão no Intune.

- **Descarregue** o ficheiro de política de configuração de aplicações iOS:
  - Aceda à [consola do Symantec Endpoint Protection Management](https://aad.skycure.com) e inicie sessão com as suas credenciais de administrador.

  - Aceda às **Definições** e, em **Integrações**, escolha **Intune**. Escolha **Seleção da Integração de EMM**. Escolha **Microsoft** e guarde a seleção.

  - Clique na ligação **Ficheiros de configuração de integração** e guarde o ficheiro \*.zip gerado. O ficheiro .zip contém o ficheiro ***.plist** que servirá para criar a política de configuração de aplicações iOS no Intune.

  - Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações do SEP Mobile para iOS.

    - Para configurações de **configuração,** selecione **dados XML,** copie o conteúdo do ficheiro ***.plist** e cole o seu conteúdo no corpo da política de configuração.

> [!NOTE]
> Se não conseguir obter os ficheiros, contacte o [Suporte Empresarial do Symantec Endpoint Protection Mobile](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Política de configuração da aplicação Check Point SandBlast Mobile

Veja as instruções para [utilizar as políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações iOS Check Point SandBlast Mobile.

- Para configurações de **configuração,** selecione **dados XML,** copie o conteúdo seguinte e cole-o no corpo da política de configuração.

  `<dict><key>MDM</key><string>INTUNE</string></dict>`


### <a name="zimperium-app-configuration-policy"></a>Política de configuração da aplicação Zimperium

Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração da aplicação Zimperium para iOS.

- Para configurações de **configuração,** selecione **dados XML,** copie o conteúdo seguinte e cole-o no corpo da política de configuração.

   ```
   <dict>
   <key>provider</key><string>Intune</string>
   <key>userprincipalname</key><string>{{userprincipalname}}</string>
   <key>deviceid</key>
   <string>{{deviceid}}</string>
   <key>serialnumber</key>
   <string>{{serialnumber}}</string>
   <key>udidlast4digits</key>
   <string>{{udidlast4digits}}</string>
   </dict>
   ```

### <a name="pradeo-app-configuration-policy"></a>Política de configuração de aplicativos pradeo

Pradeo não suporta a política de configuração de aplicações no iOS/iPadOS.  Em vez disso, para obter uma aplicação configurada, trabalhe com pradeo para implementar ficheiros IPA ou APK personalizados que sejam reconfigurados com as definições que deseja.

### <a name="better-mobile-app-configuration-policy"></a>Política de configuração de aplicações do Better Mobile

Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações do Better Mobile para iOS.

- Para configurações de **configuração,** selecione **dados XML,** copie o conteúdo seguinte e cole-o no corpo da política de configuração. Substitua o URL `https://client.bmobi.net` pelo URL da consola apropriado.

   ```
    <dict>
   <key>better_server_url</key>
   <string>https://client.bmobi.net</string>
   <key>better_udid</key>
   <string>{{aaddeviceid}}</string>
   <key>better_user</key>
   <string>{{userprincipalname}}</string>
   </dict>
   ```

### <a name="sophos-mobile-app-configuration-policy"></a>Política de configuração de aplicativos Sophos Mobile

Crie a política de configuração de aplicações iOS, tal como descrito no artigo de política de configuração de [aplicações iOS.](../apps/app-configuration-policies-use-ios.md)

### <a name="wandera-app-configuration-policy"></a>Política de configuração de aplicativos Wandera

Consulte as instruções para utilizar as políticas de configuração da [aplicação Microsoft Intune para o iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração da aplicação Wandera iOS.

- Para configurações de **configuração,** selecione **os dados Do XML**.

Inscreva-se no portal RADAR Wandera e navegue em **Definições** > **Integração EMM** > Impulso de **Aplicação**. Selecione **Intune**, e, em seguida, copie o conteúdo abaixo e cole-o no corpo da política de configuração.  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>
  ```

## <a name="assign-apps-to-groups"></a>Atribuir aplicações a grupos

Este passo aplica-se a todos os parceiros de MTD. Veja as instruções para [atribuir aplicações a grupos com o Intune](../apps/apps-deploy.md).

## <a name="next-steps"></a>Próximos passos

- [Configurar a política de conformidade de dispositivos da MTD](mtd-device-compliance-policy-create.md)
