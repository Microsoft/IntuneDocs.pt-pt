---
title: "Adicionar e atribuir aplicações de MTD ao Microsoft Intune"
titleSuffix: 
description: "Utilize o Intune para adicionar aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis), a aplicação Microsoft Authenticator e a política de configuração para iOS no portal do Azure."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fc71620fee1b1df907a4027c1c57cd91b53032e
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Adicionar e atribuir aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis) com o Intune

> [!NOTE] 
> Este tópico aplica-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

Pode utilizar o Intune para adicionar e implementar aplicações de MTD, para que os utilizadores finais possam receber notificações quando são identificadas ameaças nos respetivos dispositivos móveis e para receber orientações sobre como remediar essas ameaças.

Para os dispositivos iOS, precisa do [Microsoft Authenticator ](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) para que a identidade dos utilizadores seja verificada pelo Azure AD. Adicionalmente, precisa da política de configuração de aplicações iOS que assinala a aplicação de MTD para iOS a utilizar com o Intune.

> [!TIP]
> O portal da empresa do Intune funciona como o mediador em dispositivos Android para que a identidade dos utilizadores seja verificada pelo Azure AD.

## <a name="before-you-begin"></a>Antes de começar

-   Os passos abaixo têm de ser concluídos no [portal do Azure](https://portal.azure.com/).

-   Verifique se está familiarizado com o processo de:

    -   [Adicionar uma aplicação no Intune](apps-add.md).

    -   [Adicionar uma política de configuração de aplicações iOS no Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

    -   [Atribuir uma aplicação com o Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [ Adicionar uma política de configuração de aplicações iOS](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-apps"></a>Para adicionar aplicações

### <a name="all-mtd-partners"></a>Todos os parceiros MTD

#### <a name="microsoft-authenticator-app-for-ios"></a>Aplicação Microsoft Authenticator para iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações para obter o Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) no **passo 5** na secção **Configurar as informações da aplicação**.

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](store-apps-android.md). Utilize este [URL da loja de aplicações da Google para obter o Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) no **passo 7**.

#### <a name="ios"></a>iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações do iOS para obter o Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) no **passo 5** da secção **Configurar as informações da aplicação**.

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Aplicação Lookout for Work fora da Apple Store

Tem de voltar a assinar a aplicação Lookout for Work para iOS. A Lookout faz a distribuição da respetiva aplicação Lookout for Work para iOS fora da iOS App Store. Antes de distribuir a aplicação, tem de voltar a assinar a aplicação com o seu iOS Enterprise Developer Certificate.

Para obter instruções detalhadas sobre como voltar a assinar a aplicação Lookout for Work para iOS, veja [Lookout for Work iOS app re-signing process (Processo de nova assinatura da aplicação Lookout for Work para iOS)](https://personal.support.lookout.com/hc/articles/114094038714) no site do Lookout.

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Ativar a autenticação do Azure AD para a aplicação Lookout for Work para iOS

Ative a autenticação do Azure Active Directory para utilizadores iOS do seguinte modo:

1. Aceda ao [portal do Azure](https://portal.azure.com), inicie sessão com as suas credenciais e, em seguida, navegue para a página da aplicação.
  
2. Adicione a **aplicação Lookout for Work para iOS** como uma **aplicação de cliente nativo**.

3. Substitua o valor **com.lookout.enterprise.onomedasuaempresa** pelo ID de pacote de cliente que selecionou quando assinou o IPA.

4.  Adicione o URI de redirecionamento adicional: **&lt;companyportal://code/>** seguido de uma versão com codificação URL do seu URI de redirecionamento original.

5.  Adicione **Permissões Delegadas** à sua aplicação.

    > [!NOTE] 
    > Veja [Configurar uma aplicação cliente nativa com o Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) para obter mais detalhes.

##### <a name="add-the-lookout-for-work-ipa-file"></a>Adicionar o ficheiro .ipa do Lookout for Work

- Carregue o ficheiro .ipa com uma nova assinatura, conforme descrito no tópico [Adicionar aplicações LOB para iOS com o Intune](lob-apps-ios.md). Também tem de definir a versão mínima do SO para o iOS 8.0 ou versões posteriores.

### <a name="skycure"></a>Skycure

#### <a name="android"></a>Android

- Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](store-apps-android.md). Utilize este [URL da loja de aplicações para obter o Skycure](https://play.google.com/store/apps/details?id=com.skycure.skycure) no **passo 7**.

#### <a name="ios"></a>iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações para obter o Skycure](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) no **passo 5** na secção **Configurar as informações da aplicação**.

### <a name="check-point-sandblast-mobile"></a>Check Point SandBlast Mobile

#### <a name="android"></a>Android

- Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](store-apps-android.md). Utilize este [URL da loja de aplicações Check Point SandBlast Mobile](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) no **passo 7**.

#### <a name="ios"></a>iOS

- Contacte a [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) para obter a aplicação para iOS. Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md) e, em seguida, utilize o URL da Apple Store no **passo 5**, na secção **Configurar as informações da aplicação**.

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](store-apps-android.md). Utilize este [URL da loja de aplicações para obter o Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) no **passo 7**.

#### <a name="ios"></a>iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações para obter o Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) no **passo 5** na secção **Configurar as informações da aplicação**.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Para associar a aplicação de MTD a uma política de configuração de aplicações iOS

### <a name="for-lookout"></a>Para o Lookout

- Crie a política de configuração de aplicações iOS conforme descrito no tópico [Utilizar a política de configuração de aplicações iOS](app-configuration-policies-use-ios.md).

### <a name="for-skycure"></a>Para o Skycure

-   Utilize a mesma conta do Azure AD anteriormente configurada na [consola de Gestão do Skycure](https://aad.skycure.com), que deve ser a mesma conta utilizada para iniciar sessão no portal clássico do Intune.

-   Tem de **transferir** o ficheiro de política de configuração de aplicações iOS: 
    -   Aceda à [consola de Gestão do Skycure](https://aad.skycure.com) e inicie sessão com as suas credenciais de administrador.
    
    -   Aceda a **Definições** &gt; **Integrações da Gestão de Dispositivos** &gt; **Seleção da Integração de EMM**, escolha **Microsoft Intune** e, em seguida, guarde a sua seleção.
    
    -   Clique na ligação **Ficheiros de configuração de integração** e guarde o ficheiro \*.zip gerado. O ficheiro .zip contém o ficheiro **skycure\_configuration.plist**, que servirá para criar a política de configuração de aplicações iOS no Intune.
    
    -   Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações do Skycure para iOS.
    
    - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos do ficheiro **skycure_configuration.plist** e cole-os no corpo da política de configuração.

Também pode copiar os conteúdos do ficheiro **skycure_configuration.plist** a partir daqui:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-check-point-sandblast-mobile"></a>Para o Check Point SandBlast Mobile

- Veja as instruções para [utilizar as políticas de configuração de aplicações do Microsoft Intune para iOS](app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações iOS Check Point SandBlast Mobile.
    - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos abaixo e cole-os no corpo da política de configuração.

```
<dict><key>MDM</key><string>INTUNE</string></dict>

```

### <a name="for-zimperium"></a>Para o Zimperium

- Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](app-configuration-policies-use-ios.md) para adicionar a política de configuração da aplicação Zimperium para iOS.
    - No **passo 8**, utilize a opção **Introduzir dados XML**, copie os conteúdos abaixo e cole-os no corpo da política de configuração.

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

## <a name="to-assign-apps-all-mtd-partners"></a>Para atribuir aplicações (todos os parceiros MTD)

- Veja as instruções para [atribuir aplicações a grupos com o Intune](apps-deploy.md).

## <a name="next-steps"></a>Próximos passos

- [Adicionar a política de conformidade de dispositivos da MTD](mtd-device-compliance-policy-create.md)
