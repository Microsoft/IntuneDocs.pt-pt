---
title: IOS/iPadOS bundle IDs para aplicações incorporadas no Microsoft Intune - Azure Microsoft Docs
titleSuffix: ''
description: Consulte uma lista dos IDs de pacote para as aplicações incorporadas para iOS e iPadOS. Utilize estes IDs de pacote para permitir explicitamente aplicações em perfis e políticas de configuração do dispositivo no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10c6ea8e3afd7bb1f5a583c0088c72fc155cb0f9
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513304"
---
# <a name="bundle-ids-for-built-in-ios-and-ipados-apps-you-can-use-in-intune"></a>Pacote iDs para aplicações incorporadas para iOS e iPadOS que pode utilizar no Intune

Quando configurar funcionalidades em dispositivos iOS/iPadOS, também pode adicionar as aplicações incorporadas em dispositivos iOS/iPadOS. Este artigo lista os IDs de algumas aplicações comuns incorporadas iOS/iPadOS. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software. Consulte a lista de [IOs/iPadOS](https://support.apple.com/guide/mdm/ios-bundle-ids-mdm90f60c1ce/web) da Apple (abre o site da Apple).

## <a name="bundle-ids"></a>IDs de pacote

| ID do Pacote                   | Nome da Aplicação     | Publicador |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendário     | Apple     |
| com.apple.camera            | Câmara       | Apple     |
| com.apple.mobiletimer       | Relógio        | Apple     |
| com.apple.clips             | Clips        | Apple     |
| com.apple.compass           | Bússola      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Ficheiros        | Apple     |
| com.apple.mobileme.fmf1     | Encontrar Amigos | Apple     |
| com.apple.mobileme.fmip1    | Localizar iPhone  | Apple     |
| com.apple.gamecenter        | Centro de Jogos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Estado de Funcionamento       | Apple     |
| com.apple.Home              | Casa         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Correio         | Apple     |
| com.apple.Maps              | Mapas         | Apple     |
| com.apple.measure           | Medida      | Apple     |
| com.apple.MobileSMS         | Mensagens     | Apple     |
| com.apple.Music             | Música        | Apple     |
| com.apple.news              | Notícias         | Apple     |
| com.apple.mobilenotes       | Notas        | Apple     |
| com.apple.Numbers           | Números      | Apple     |
| com.apple.Pages             | Páginas        | Apple     |
| com.apple.mobilephone       | Telefone        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotografias       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Lembretes    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Definições     | Apple     |
| com.apple.atalhos         | Atalhos    | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Bolsa       | Apple     |
| com.apple.tips              | Sugestões         | Apple     |
| com.apple.tv                | TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Meteorologia      | Apple     |

## <a name="next-steps"></a>Próximos passos

Utilize estes IDs de pacote para configurar [as funcionalidades](ios-device-features-settings.md) do dispositivo e [para permitir ou restringir algumas definições](device-restrictions-ios.md) em dispositivos iOS/iPadOS.
