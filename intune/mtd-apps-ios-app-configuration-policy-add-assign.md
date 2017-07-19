---
title: "Adicionar e atribuir aplicações de MTD ao Intune"
titleSuffix: Intune on Azure
description: "Adicionar aplicações de MTD, a aplicação Microsoft Authenticator e a política de configuração para iOS ao Intune no Azure"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7b3fb86648a86b161eadfc071bdacbfd4ea0222f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Adicionar e atribuir aplicações de MTD (Defesa Contra Ameaças para Dispositivos Móveis) com o Intune

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

### <a name="skycure-app-for-android"></a>Aplicação Skycure para Android

- Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](store-apps-android.md). Utilize este [URL da loja de aplicações para obter o Skycure](https://play.google.com/store/apps/details?id=com.skycure.skycure) no **passo 7**.

### <a name="skycure-app-for-ios"></a>Aplicação Skycure para iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações para obter o Skycure](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) no **passo 5** na secção **Configurar as informações da aplicação**.

### <a name="microsoft-authenticator-app-for-ios"></a>Aplicação Microsoft Authenticator para iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações para obter o Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) no **passo 5** na secção **Configurar as informações da aplicação**.

### <a name="lookout-for-work-android-app"></a>Aplicação Lookout for Work para Android

- Veja as instruções para [adicionar aplicações da loja Android ao Microsoft Intune](store-apps-android.md). Utilize este [URL da loja de aplicações da Google para obter o Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) no **passo 7**.

### <a name="lookout-for-work-ios-app"></a>Aplicação Lookout for Work para iOS

- Veja as instruções para [adicionar aplicações da loja iOS ao Microsoft Intune](store-apps-ios.md). Utilize este [URL da loja de aplicações do iOS para obter o Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) no **passo 5** da secção **Configurar as informações da aplicação**.

### <a name="lookout-for-work-app-outside-the-apple-store"></a>Aplicação Lookout for Work fora da Apple Store

Tem de voltar a assinar a aplicação Lookout for Work para iOS. A Lookout faz a distribuição da respetiva aplicação Lookout for Work para iOS fora da iOS App Store. Antes de distribuir a aplicação, tem de voltar a assinar a aplicação com o seu iOS Enterprise Developer Certificate.

Para obter instruções detalhadas sobre como voltar a assinar a aplicação Lookout for Work para iOS, veja [Lookout for Work iOS app re-signing process (Processo de nova assinatura da aplicação Lookout for Work para iOS)](https://personal.support.lookout.com/hc/articles/114094038714) no site do Lookout.

#### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Ativar a autenticação do Azure AD para a aplicação Lookout for Work para iOS

Ative a autenticação do Azure Active Directory para utilizadores iOS do seguinte modo:

1. Aceda ao [portal do Azure](https://portal.sazure.com), inicie sessão com as suas credenciais e, em seguida, navegue para a página da aplicação.
  
2. Adicione a **aplicação Lookout for Work para iOS** como uma **aplicação de cliente nativo**.

3. Substitua o valor **com.lookout.enterprise.onomedasuaempresa** pelo ID de pacote de cliente que selecionou quando assinou o IPA.

4.  Adicione o URI de redirecionamento adicional: **&lt;companyportal://code/>** seguido de uma versão com codificação URL do seu URI de redirecionamento original.

5.  Adicione **Permissões Delegadas** à sua aplicação.

    > [!NOTE] 
    > Veja [Configurar uma aplicação cliente nativa com o Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) para obter mais detalhes.

#### <a name="add-the-lookout-for-work-ipa-file"></a>Adicionar o ficheiro .ipa do Lookout for Work

- Carregue o ficheiro .ipa com uma nova assinatura, conforme descrito no tópico [Adicionar aplicações LOB para iOS com o Intune](lob-apps-ios.md). Também tem de definir a versão mínima do SO para o iOS 8.0 ou versões posteriores.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Para associar a aplicação de MTD a uma política de configuração de aplicações iOS

### <a name="for-skycure"></a>Para o Skycure

-   Utilize a mesma conta do Azure AD anteriormente configurada na consola de Gestão do Skycure, que deve ser a mesma conta utilizada para iniciar sessão na consola clássica do Intune.

-   Tem de ter o ficheiro de integração do Skycure pronto a ser utilizado. Este é o ficheiro .zip transferido anteriormente a partir da consola de Gestão do Skycure, que contém o ficheiro **skycure\_configuration.plist** com os parâmetros da política de configuração de aplicações iOS.

- Veja as instruções sobre como [utilizar políticas de configuração de aplicações do Microsoft Intune para iOS](app-configuration-policies-use-ios.md) para adicionar a política de configuração de aplicações do Skycure para iOS.
    - No passo 8, utilize a opção **Introduzir dados XML**, copie os conteúdos do ficheiro **skycure_configuration.plist** e cole-os no corpo da política de configuração.

Também pode copiar os conteúdos do ficheiro **skycure_configuration.plist** a partir daqui:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-lookout"></a>Para o Lookout

- Crie a política de configuração de aplicações iOS conforme descrito no tópico [Utilizar a política de configuração de aplicações iOS](app-configuration-policies-use-ios.md).

## <a name="to-assign-mtd-apps"></a>Para atribuir aplicações de MTD

- Veja as instruções sobre como [atribuir aplicações a grupos com o Intune](apps-deploy.md).

## <a name="next-steps"></a>Passos seguintes

[Configurar a integração do Skycure com o Intune](skycure-mtd-connector-integration.md)
[Configurar a integração do Skycure com o Intune](lookout-mtd-connector-integration.md)
