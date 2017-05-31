---
title: "Definições de notificação de aplicações do Intune para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba as definições que pode utilizar para controlar as notificações das aplicações nos dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c64167275a2628c6a3a4e899e00c25df4c10b06b
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="intune-app-notifications-settings-for-ios-devices"></a>Definições de notificações de aplicações do Intune para dispositivos iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Permite-lhe configurar a forma como as aplicações instaladas num dispositivo enviam notificações. Esta definição suporta dispositivos supervisionados que executam o iOS 9.3 e posterior.

## <a name="configure-settings"></a>Configurar definições

1. No painel **Funcionalidades do dispositivo**, escolha **Notificações de Aplicações (apenas supervisionado)**.
2. No painel **Notificações de Aplicações**, escolha **Adicionar** e, em seguida, configure os seguintes valores:
    - **ID do pacote de aplicações** – introduza o **ID do Pacote de Aplicações** da aplicação que pretende configurar. Para obter ajuda, veja **Referência de ID do pacote para aplicações iOS incorporadas** mais adiante neste tópico.
    - **Nome da aplicação** – introduza o nome da aplicação que pretende configurar. O nome não é apresentado no dispositivo e serve para o ajudar a identificar a aplicação na lista.
    - **Publicador** – introduza o publicador da aplicação que pretende configurar. O nome não é apresentado no dispositivo e serve para o ajudar a identificar a aplicação na lista.
    - **Notificações** – ative ou desative o envio de notificações da aplicação para o dispositivo. Se desativar esta definição, as seguintes definições também serão desativadas.
        - **Mostrar na Central de Notificações** – ative para permitir que a aplicação mostre as notificações na Central de Notificações do dispositivo.
        - **Mostrar no Ecrã de Bloqueio** – ative para ver as notificações da aplicação no ecrã de bloqueio do dispositivo.
        - **Tipo de alerta** – selecione o tipo de notificação que quer quando o dispositivo é desbloqueado em:
            - **Nenhum** – não são apresentadas notificações.
            - **Faixa** – é apresentada uma faixa brevemente a mostrar a notificação.
            - **Modal** – a notificação é apresentada e o utilizador tem de a dispensar manualmente para poder continuar a utilizar o dispositivo.
        - **Destaque no ícone da aplicação** – ative esta opção para adicionar um destaque ao ícone da aplicação para indicar que a aplicação enviou uma notificação.
        - **Sons** – ative para reproduzir um som quando uma notificação é entregue.
3. Continue a adicionar aplicações, conforme necessário. Quando terminar, escolha **OK**.
4. Escolha **OK** até regressar ao painel **Criar Perfil** e, em seguida, escolha **Criar**. 


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referência de ID do pacote para aplicações iOS incorporadas

Esta lista mostra o ID do pacote de algumas aplicações iOS comuns incorporadas. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software. 

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
