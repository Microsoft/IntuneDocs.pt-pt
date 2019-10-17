---
title: Adicionar e atribuir aplicações de MTD ao Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize o Intune para adicionar aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis), a aplicação Microsoft Authenticator e a política de configuração para iOS no portal do Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
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
ms.openlocfilehash: f5ca8b7c94569861ccc5c4235315a7a57de9d838
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504404"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Adicionar e atribuir aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis) com o Intune  

> [!NOTE] 
> Este artigo se aplica a todos os parceiros de defesa contra ameaças móveis.

Você pode usar o Intune para adicionar e implantar aplicativos de MTD (defesa contra ameaças móveis) para que os usuários finais possam receber notificações quando uma ameaça for identificada em seus dispositivos móveis e receber orientação para corrigir as ameaças.

## <a name="before-you-begin"></a>Antes de começar    
Os passos abaixo têm de ser concluídos no [portal do Azure](https://portal.azure.com/). Verifique se está familiarizado com o processo de:

- [Adicionar uma aplicação no Intune](../apps/apps-add.md).
- [Adicionar uma política de configuração de aplicações iOS no Intune](../apps/app-configuration-policies-use-ios.md).
- [Atribuir uma aplicação com o Intune](../apps/apps-deploy.md).

> [!TIP]
> O Portal da Empresa do Intune funciona como o agente em dispositivos Android para que os usuários possam ter suas identidades verificadas pelo Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Configurar o Microsoft Authenticator para iOS  
Para os dispositivos iOS, precisa do [Microsoft Authenticator ](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) para que a identidade dos utilizadores seja verificada pelo Azure AD. Além disso, você precisa de uma política de configuração de aplicativo iOS que define o aplicativo iOS MTD que você usa com o Intune.

Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Utilize este [URL da loja de aplicações para obter o Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) no **passo 12** na secção **Configurar as informações da aplicação**.

## <a name="configure-mtd-applications"></a>Configurar as aplicações de MTD  
Selecione a secção que corresponde ao seu fornecedor de MTD:

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Vaga](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Configurar as aplicações Lookout for Work  
- **Android**  
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [URL da loja de aplicações da Google para obter o Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) no **passo 7**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [LOOKOUT for Work URL da loja de aplicativos Ios](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) na **etapa 11** para a **URL AppStore**.

- **Aplicação Lookout for Work fora da Apple Store**  
  - Tem de voltar a assinar a aplicação Lookout for Work para iOS. A Lookout faz a distribuição da respetiva aplicação Lookout for Work para iOS fora da iOS App Store. Antes de distribuir a aplicação, tem de voltar a assinar a aplicação com o seu iOS Enterprise Developer Certificate.  
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

    - Carregue o arquivo. ipa reassinado conforme descrito no artigo [adicionar aplicativos LOB do IOS com o Intune](../apps/lob-apps-ios.md) . Também tem de definir a versão mínima do SO para o iOS 8.0 ou versões posteriores.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Configurar as aplicações do Symantec Endpoint Protection Mobile  
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). No **passo 7**, utilize este [URL da loja de aplicações para obter o SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Para o **Sistema operativo mínimo**, selecione **Android 4.0 (Ice Cream Sandwich)** .

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos móveis de setembro](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) na **etapa 11** para a **URL AppStore**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Configurar as aplicações do Check Point SandBlast Mobile  
- **Android**  
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [URL da loja de aplicações Check Point SandBlast Mobile](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) no **passo 7**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos móveis do SandBlast Check Point](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) na **etapa 11** para a **URL do AppStore**.  

### <a name="configure-zimperium-apps"></a>Configurar as aplicações do Zimperium  
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [URL da loja de aplicações para obter o Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) no **passo 7**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos do Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) na **etapa 11** para a **URL do AppStore**.  
 
### <a name="configure-pradeo-apps"></a>Configurar as aplicações do Pradeo  
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [URL da loja de aplicações para obter o Pradeo](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) no **passo 7**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos do Pradeo](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) na **etapa 11** para a **URL do AppStore**.

### <a name="configure-better-mobile-apps"></a>Configurar aplicações do Better Mobile  
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Utilize este [URL da loja de aplicações para obter o Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) no **passo 7**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos do ActiveShield](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) na **etapa 11** para a **URL AppStore**.

### <a name="configure-sophos-apps"></a>Configurar aplicativos do Sophos  
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Use esta [URL da loja de aplicativos do Sophos](https://play.google.com/store/apps/details?id=com.sophos.smsec) na **etapa 7**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos do ActiveShield](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) na **etapa 11** para a **URL AppStore**.

### <a name="configure-wandera-apps"></a>Configurar aplicativos do inphonea  
 
- **Android**
  - Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](../apps/store-apps-android.md). Use esta [URL da loja de aplicativos móveis da vaga](https://play.google.com/store/apps/details?id=com.wandera.android) na **etapa 7**. Para o **sistema operacional mínimo**, selecione **Android 5,0**.

- **iOS**
  - Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](../apps/store-apps-ios.md). Use esta [URL da loja de aplicativos móveis](https://itunes.apple.com/app/wandera/id605469330) da busca na **etapa 11** para a **URL do AppStore**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Configurar as aplicações de MTD com uma política de configuração de aplicações iOS  

### <a name="lookout-for-work-app-configuration-policy"></a>Política de configuração da aplicação Lookout for Work  
- Crie a política de configuração de aplicativo iOS conforme descrito no artigo [usando a política de configuração de aplicativo do IOS](../apps/app-configuration-policies-use-ios.md) .

### <a name="sep-mobile-app-configuration-policy"></a>Política de configuração da aplicação SEP Mobile  
- Use a mesma conta do Azure AD configurada anteriormente no [console de gerenciamento do Symantec Endpoint Protection](https://aad.skycure.com), que deve ser a mesma conta usada para entrar no portal clássico do Intune.

- **Baixe** o arquivo de política de configuração de aplicativo do IOS: 
  - Aceda à [consola do Symantec Endpoint Protection Management](https://aad.skycure.com) e inicie sessão com as suas credenciais de administrador.

  - Aceda às **Definições** e, em **Integrações**, escolha **Intune**. Escolha **Seleção da Integração de EMM**. Escolha **Microsoft** e guarde a seleção.

  - Clique na ligação **Ficheiros de configuração de integração** e guarde o ficheiro \*.zip gerado. O ficheiro .zip contém o ficheiro * **.plist** que servirá para criar a política de configuração de aplicações iOS no Intune.

  - Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações do SEP Mobile para iOS.

  - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos do ficheiro * **.plist** e cole-os no corpo da política de configuração.

> [!NOTE]  
> Se não conseguir obter os ficheiros, contacte o [Suporte Empresarial do Symantec Endpoint Protection Mobile](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Política de configuração da aplicação Check Point SandBlast Mobile  
- Veja as instruções para [utilizar as políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações iOS Check Point SandBlast Mobile.
  - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos abaixo e cole-os no corpo da política de configuração.

        <dict><key>MDM</key><string>INTUNE</string></dict>


### <a name="zimperium-app-configuration-policy"></a>Política de configuração da aplicação Zimperium  
- Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração da aplicação Zimperium para iOS.
  - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos abaixo e cole-os no corpo da política de configuração.
 
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

### <a name="pradeo-app-configuration-policy"></a>Política de configuração de aplicativo Pradeo  
Pradeo não dá suporte à política de configuração de aplicativo no iOS.  Em vez disso, para obter um aplicativo configurado, trabalhe com Pradeo para implementar arquivos IPA ou APK personalizados que são pré-configurados com as configurações desejadas.

### <a name="better-mobile-app-configuration-policy"></a>Política de configuração de aplicações do Better Mobile  
- Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações do Better Mobile para iOS.
  - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos abaixo e cole-os no corpo da política de configuração. Substitua o URL `https://client.bmobi.net` pelo URL da consola apropriado.

        <dict>
        <key>better_server_url</key>
        <string>https://client.bmobi.net</string>
        <key>better_udid</key>
        <string>{{aaddeviceid}}</string>
        <key>better_user</key>
        <string>{{userprincipalname}}</string>
        </dict>


### <a name="sophos-mobile-app-configuration-policy"></a>Política de configuração de aplicativo móvel do Sophos  
Crie a política de configuração de aplicativo iOS conforme descrito no artigo [usando a política de configuração de aplicativo do IOS](../apps/app-configuration-policies-use-ios.md) .

### <a name="wandera-app-configuration-policy"></a>Política de configuração de aplicativo do  
Confira as instruções para [usar Microsoft Intune políticas de configuração de aplicativo para IOS](../apps/app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicativo do Ios.
- Na **etapa 8**, use a opção **inserir dados XML**. Entre no portal de entrada de seu RADAR e navegue até **configurações** > **EMM integração** > **push de aplicativo**. Selecione **Intune**e copie o conteúdo abaixo e cole-o no corpo da política de configuração.  

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

## <a name="assign-apps-to-groups"></a>Atribuir aplicações a grupos  
- Este passo aplica-se a todos os parceiros de MTD. Veja as instruções para [atribuir aplicações a grupos com o Intune](../apps/apps-deploy.md).

## <a name="next-steps"></a>Próximos passos  
- [Configurar a política de conformidade de dispositivos da MTD](mtd-device-compliance-policy-create.md)