---
title: Criar um perfil de dispositivo iOS ou macOS com o Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil de dispositivo iOS ou macOS e, em seguida, defina as configurações de impressão, layout da tela inicial, notificações de aplicativo, dispositivo compartilhado, logon único e configurações de filtro de conteúdo da Web em Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 272a7303e7d529a4867334cbe05e6df31e6c5683
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755373"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Adicionar definições de funcionalidades de dispositivos iOS ou macOS no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune inclui muitos recursos e configurações que ajudam os administradores a controlar dispositivos iOS e macOS. Por exemplo, os administradores podem:

- Permitir que os usuários acessem impressoras de impressão em sua rede
- Adicionar aplicativos e pastas à tela inicial, incluindo a adição de novas páginas
- Escolha se e como as notificações de aplicativo são mostradas
- Configurar a tela de bloqueio para mostrar uma mensagem ou a marca do ativo, especialmente para dispositivos compartilhados
- Fornecer aos usuários uma experiência de logon único segura para compartilhar credenciais entre aplicativos
- Filtrar sites que usam idioma adulto e permitir ou bloquear sites específicos

O Intune usa "perfis de configuração" para criar e personalizar essas configurações para as necessidades da sua organização. Depois de adicionar esses recursos em um perfil, você envia por Push ou implanta o perfil para dispositivos iOS e macOS em sua organização.

Este artigo descreve os diferentes recursos que você pode configurar e mostra como criar um perfil de configuração de dispositivo. Você também pode ver todas as configurações disponíveis para dispositivos [Ios](ios-device-features-settings.md) e [MacOS](macos-device-features-settings.md) .

## <a name="airprint"></a>AirPrint

O arquivo de impressão é um recurso da Apple que permite que os dispositivos sejam impressos em arquivos em uma rede sem fio. No Intune, você pode adicionar informações de impressão aos dispositivos.

Para obter uma lista das configurações que você pode configurar no Intune, confira [impressão no Ios](ios-device-features-settings.md#airprint) e no Microsoft [MacOS](macos-device-features-settings.md#airprint).

Para obter mais informações sobre o impresso, consulte [sobre o esprint](https://support.apple.com/HT201311) no site da Apple.

Aplica-se a:

- iOS 7,0 e mais recente
- iPadOS 13,0 e mais recente
- macOS 10,10 e mais recente

## <a name="app-notifications"></a>Notificações de aplicativo

Escolha como os aplicativos em seus dispositivos iOS e iPad recebem notificações. Por exemplo, no Intune, envie notificações de aplicativo para que elas apareçam no centro de notificações, sejam exibidas na tela de bloqueio ou joguem um som.

Para obter uma lista das configurações que você pode definir no Intune, consulte [notificações de aplicativo no Ios](ios-device-features-settings.md#app-notifications).

Para obter mais informações sobre esse recurso, consulte [notificações](https://developer.apple.com/notifications/) no site da Apple.

Aplica-se a:

- iOS 9,3 e mais recente
- iPadOS 13,0 e mais recente

## <a name="associated-domains"></a>Domínios associados

Os domínios associados permitem que você crie uma relação entre seus domínios, como `contoso.com` e seus aplicativos. Esse recurso permite que você:

- Compartilhe dados e conecte as credenciais entre aplicativos e sites em sua organização.
- Use recursos de aplicativo baseados em seu site, como extensão de aplicativo de logon único, links universais e preenchimento automático de senha.

  Por exemplo, crie um domínio associado para permitir que o preenchimento automático de senha recomende credenciais, como uma senha, para sites associados ao seu aplicativo.

Para obter uma lista das configurações que você pode configurar no Intune, consulte [domínios associados no MacOS](macos-device-features-settings.md#associated-domains).

Para obter mais informações sobre esse recurso, consulte [Configurando os domínios associados de um aplicativo](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) no site da Apple.

Aplica-se a:

- macOS 10,15 e mais recente

## <a name="home-screen-layout"></a>Esquema do ecrã principal

Essas configurações configuram o layout do aplicativo e as pastas nas telas de Dock e Home em dispositivos iOS e iPadOS. É possível:

- Use as configurações de **encaixe** para adicionar aplicativos ou pastas à tela. Por exemplo, mostre o Safari e o aplicativo de email no encaixe do dispositivo.
- Adicione **páginas** que você deseja mostrar na tela inicial e os aplicativos que você deseja mostrar em cada página. Por exemplo, adicione uma página da **contoso** e adicione o aplicativo de configurações nesta página.

Para obter uma lista das configurações que você pode configurar no Intune, consulte [layout da tela inicial no Ios](ios-device-features-settings.md#home-screen-layout).

Aplica-se a:

- iOS 9,3 e mais recente
- iPadOS 13,0 e mais recente

## <a name="lock-screen-message"></a>Mensagem da tela de bloqueio

Use essas configurações para mostrar uma mensagem personalizada ou um texto na janela de entrada e na tela de bloqueio. Por exemplo, você pode inserir um "se perdido, retornar para..." mensagem e mostrar informações de marca do ativo.

Para obter uma lista das configurações que podem ser definidas no Intune, consulte [configurações de mensagem da tela de bloqueio no Ios](ios-device-features-settings.md#lock-screen-message).

Para obter mais informações sobre a mensagem da tela de bloqueio, consulte [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) no site da Apple.

Aplica-se a:

- iOS 9,3 e mais recente
- iPadOS 13,0 e mais recente

## <a name="login-items"></a>Itens de logon

Use esse recurso para escolher os aplicativos, aplicativos personalizados, arquivos e pastas que são abertos quando os usuários entram nos dispositivos. 

Para obter uma lista das configurações que você pode configurar no Intune, consulte [itens de logon no MacOS](macos-device-features-settings.md#login-items).

Aplica-se a:

- macOS 10,13 e mais recente

## <a name="login-window"></a>Janela de logon

Controle a aparência da tela de logon e as funções disponíveis para os usuários antes de entrarem. Por exemplo, adicione uma faixa com uma mensagem personalizada, escolha se o botão de suspensão é mostrado e muito mais.

Para obter uma lista das configurações que você pode configurar no Intune, consulte [janela de logon no MacOS](macos-device-features-settings.md#login-window).

Aplica-se a:

- macOS 10,7 e mais recente

## <a name="single-sign-on"></a>Logon único

A maioria das aplicações de Linha de Negócio (LOB) exige algum nível de autenticação do utilizador para suportar a segurança. Em muitos casos, a autenticação exige que o usuário insira as mesmas credenciais repetidamente. Para melhorar a experiência do usuário, os desenvolvedores podem criar aplicativos que usam SSO (logon único). O uso do logon único reduz o número de vezes que um usuário deve inserir as credenciais.

Para usar o logon único, verifique se você tem:

- Um aplicativo que é codificado para procurar o repositório de credenciais do usuário no logon único no dispositivo.
- O Intune configurado para o início de sessão único em dispositivos iOS.

![Painel Início de Sessão Único](./media/device-features-configure/sso-blade.png)

Para obter uma lista das configurações que você pode configurar no Intune, consulte [logon único no Ios](ios-device-features-settings.md#single-sign-on).

Aplica-se a:

- iOS 7,0 e mais recente
- iPadOS 13,0 e mais recente

## <a name="single-sign-on-app-extension"></a>Extensão do aplicativo de logon único

Essas configurações configuram uma extensão de aplicativo que habilita o SSO (logon único) para seus dispositivos iOS, iPadOS e macOS. A maioria dos aplicativos de LOB (linha de negócios) e sites da organização exigem algum nível de autenticação de usuário segura. Em muitos casos, a autenticação exige que os usuários insiram as mesmas credenciais repetidamente. O SSO fornece aos usuários acesso a aplicativos e sites depois de inserir suas credenciais uma vez. Depois de entrar, os usuários podem acessar aplicativos e sites automaticamente ou usar a ID de face, a ID de toque ou a senha da Apple para obter acesso.

No Intune, use essas configurações para configurar a extensão Kerberos interna da Apple ou para configurar uma extensão de aplicativo SSO criada por sua organização. A extensão do aplicativo SSO manipula a autenticação para seus usuários. Essas configurações definem as extensões de aplicativo SSO do tipo credencial, que são projetadas para fluxos de autenticação de desafio e resposta. Você pode escolher entre uma extensão de credencial específica do Kerberos fornecida pela Apple e uma extensão de credencial genérica.

Para obter uma lista das configurações que você pode configurar no Intune, consulte extensão de [aplicativo de SSO do IOS](ios-device-features-settings.md#single-sign-on-app-extension) e extensão de aplicativo de SSO do [MacOS](macos-device-features-settings.md#single-sign-on-app-extension).

Para obter mais informações sobre como desenvolver uma extensão de aplicativo SSO, Assista ao [SSO corporativo extensível](https://developer.apple.com/videos/play/tech-talks/301) no site da Apple.

> [!NOTE]
> O recurso de **extensão do aplicativo de logon único** é diferente do recurso de **logon único** :
>
> - As configurações de **extensão do aplicativo de logon único** se aplicam ao iPadOS 13,0 (e mais recente) e ao Ios 13,0 (e mais recente). As configurações de **logon único** se aplicam ao iPadOS 13,0 (e mais recente) e Ios 7,0 e mais recentes.
> - Uma **extensão de aplicativo de logon único** manipula a autenticação com o sistema operacional. No **logon único**, um aplicativo específico manipula a autenticação.
> - Ao usar a **extensão de aplicativo de logon único**, os usuários entram em aplicativos e sites silenciosamente, ou com ID facial, Touch ID ou pincode ou senha da Apple. Ao usar o **logon único**, os usuários entram em aplicativos e sites usando outro aplicativo.
>
>    A **extensão do aplicativo de logon único** usa o sistema operacional da Apple para se autenticar. Portanto, ele pode fornecer uma melhor experiência do usuário final.
>
> - Do ponto de vista do desenvolvimento, a **extensão do aplicativo de logon único** pode usar qualquer tipo de autenticação SSO de credencial. Com o **logon único**, você só pode usar a autenticação SSO Kerberos.  

Aplica-se a:

- iOS 13,0 e mais recente
- iPadOS 13,0 e mais recente
- macOS 10,15 e mais recente

## <a name="wallpaper"></a>Papéis

Adicione uma imagem. png,. jpg ou. jpeg personalizada aos dispositivos iOS supervisionados. Por exemplo, use o Intune para adicionar um logotipo da empresa à tela de bloqueio em seus dispositivos.

Para obter uma lista das configurações que você pode configurar no Intune, consulte [papel de parede no Ios](ios-device-features-settings.md#wallpaper).

Aplica-se a:

- iOS
- iPadOS 13,0 e mais recente

## <a name="web-content-filter"></a>Filtro de conteúdo da Web

Essas configurações podem usar o algoritmo de AutoFiltro interno da Apple para avaliar páginas da Web e bloquear conteúdo adulto e idioma adulto. Você também pode criar uma lista de links da Web permitidos e links da Web restritos. Por exemplo, você pode permitir que somente sites `contoso` sejam abertos.

Para obter uma lista das configurações que você pode configurar no Intune, consulte [filtro de conteúdo da Web no Ios](ios-device-features-settings.md#web-content-filter).

Aplica-se a:

- iOS 7,0 e mais recente
- iPadOS 13,0 e mais recente

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome descritivo para a política. Atribua nomes às políticas de forma que possa identificá-las facilmente mais tarde. Por exemplo, um bom nome de política é o **MacOS: configura a tela de logon**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos seus dispositivos. As opções são:  
        - **iOS/iPadOS**
        - **macOS**
    - **Tipo de perfil**: selecione **Funcionalidades do dispositivo**.

4. Consoante a plataforma que escolheu, as definições que pode configurar variam. Escolha sua plataforma para configurações detalhadas:

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e mostrado na lista de perfis. Certifique-se de [atribuir o perfil](device-profile-assign.md) e [monitorar seu status](device-profile-monitor.md).

## <a name="next-steps"></a>Próximos passos

Depois que o perfil é criado, ele está pronto para ser atribuído. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Exiba todas as configurações de recurso de dispositivo para dispositivos [Ios](ios-device-features-settings.md) e [MacOS](macos-device-features-settings.md) .
