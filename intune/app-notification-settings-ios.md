---
title: "Criar notificações da aplicação para dispositivos iOS – Microsoft Intune – Azure | Microsoft Docs"
description: "Adicione ou crie notificações da aplicação para dispositivos iOS no Microsoft Intune. Escolha as aplicações pretendidas para enviar notificações, configure as definições de notificações no ecrã de bloqueio, ative o som, selecione o tipo de alerta e adicione um distintivo."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 018a04bd674e4f270ed2e356c08825ab1d5878da
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Configurar as definições de notificações das aplicações em dispositivos iOS no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Configure a forma como as aplicações instaladas num dispositivo iOS enviam notificações. Estas definições suportam dispositivos supervisionados com o iOS 9.3 e posterior.

## <a name="add-the-app-notification"></a>Adicionar a notificação de aplicação

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. No seu perfil iOS ou macOS, selecione **Funcionalidades do dispositivo**. O tópico [Funcionalidades do dispositivo iOS ou macOS](device-features-configure.md) apresenta a lista de passos para criar um perfil.
3. Selecione **Notificações da Aplicação (apenas supervisionado)** e, em seguida, selecione **Adicionar**: ![adicionar notificação da aplicação no perfil iOS ou macOS no Intune](./media/ios-macos-app-notifications.png)
4. Introduza as seguintes propriedades:

  - **ID da coleção de pacotes de aplicação**: introduza o **ID da coleção de pacotes de aplicação** da aplicação que pretende configurar. Para obter ajuda, veja **Referência de ID da coleção de pacotes para aplicações iOS incorporadas** (neste artigo).
  - **Nome da aplicação** – introduza o nome da aplicação que pretende configurar. Este nome não é apresentado no dispositivo e é utilizado para o ajudar a identificar a aplicação na lista.
  - **Publicador** – introduza o publicador da aplicação que pretende configurar. O nome do publicador não é apresentado no dispositivo e é utilizado apenas para o ajudar a identificar a aplicação na lista.
  - **Notificações**: ative ou desative o envio de notificações da aplicação para o dispositivo. Se desativar esta definição, as seguintes definições também serão desativadas.
    - **Mostrar no Centro de Notificações** – ative esta definição para permitir que a aplicação mostre notificações no Centro de Notificações do dispositivo.
    - **Mostrar no Ecrã de Bloqueio** – ative esta definição para ver as notificações da aplicação no ecrã de bloqueio do dispositivo.
    - **Tipo de alerta** – selecione o tipo de notificação que quer quando o dispositivo é desbloqueado em:
      - **Nenhum** – não são apresentadas notificações.
      - **Faixa** – é apresentada uma faixa brevemente a mostrar a notificação.
      - **Modal** – a notificação é apresentada e o utilizador tem de a dispensar manualmente para poder continuar a utilizar o dispositivo.
    - **Distintivo no ícone da aplicação** – ative esta definição para adicionar um distintivo ao ícone da aplicação para indicar que a mesma enviou uma notificação.
    - **Sons** – ative esta definição para reproduzir um som quando for recebida uma notificação.

5. Continue a adicionar aplicações, conforme necessário. Quando terminar de adicionar as aplicações, selecione **OK**.
6. Selecione **Criar** para guardar o seu perfil.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referência de ID do pacote para aplicações iOS incorporadas

A seguinte lista mostra o ID da coleção de pacotes de algumas aplicações iOS comuns incorporadas. Para localizar o ID da coleção de pacotes de outras aplicações, recomenda-se contactar o fabricante do software.

|||
|-|-|
|Nome da aplicação|ID do Pacote|
|App Store|com.apple.AppStore|
|Calculadora|com.apple.calculator|
|Calendário|com.apple.mobilecal|
|Câmara|com.apple.camera|
|Relógio|com.apple.mobiletimer|
|Bússola|com.apple.compass|
|Contactos|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Encontrar Amigos|com.apple.mobileme.fmf1|
|Localizar iPhone|com.apple.mobileme.fmip1|
|Centro de Jogos|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Estado de Funcionamento|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Correio|com.apple.mobilemail|
|Mapas|com.apple.Maps|
|Mensagens|com.apple.MobileSMS|
|Música|com.apple.Music|
|Notícias|com.apple.news|
|Notas|com.apple.mobilenotes|
|Números|com.apple.Numbers|
|Páginas|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Fotografias|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Lembretes|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Definições|com.apple.Preferences|
|Bolsa|com.apple.stocks|
|Sugestões|com.apple.tips|
|Vídeos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Wallet|com.apple.Passbook|
|Watch|com.apple.Bridge|
|Meteorologia|com.apple.weather|

## <a name="next-steps"></a>Próximos passos

Atribua o perfil do dispositivo aos grupos que selecionar. O tópico [Como atribuir perfis de dispositivo](device-profile-assign.md) apresenta a lista de passos.