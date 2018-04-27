---
title: Definições personalizadas do Microsoft Intune para dispositivos macOS
titleSuffix: ''
description: Saiba quais são as definições que pode utilizar num perfil personalizado do macOS no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 849bf23429ed689ee995784c3a47a802ba7dbf71
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-macos"></a>Definições do dispositivo personalizadas do Microsoft Intune para dispositivos macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilize o perfil personalizado do macOS do Microsoft Intune para atribuir as definições que criou com a [Ferramenta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) a dispositivos macOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para um perfil personalizado do macOS do Intune e atribuir as definições a utilizadores e dispositivos da sua organização.

Esta capacidade permite-lhe atribuir definições do macOS que não são configuráveis com outros tipos de perfis do Intune.


1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Perfil de Configuração Personalizada**, configure cada uma das seguintes definições:

- **Nome do perfil de configuração personalizado** – forneça um nome para a política conforme apresentado no dispositivo e no estado do Intune.
- **Ficheiro de perfil de configuração** – Navegue até ao perfil de configuração que criou ao utilizar o Apple Configurator.
Confirme que as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do macOS nos dispositivos nos quais atribuiu a política personalizada do macOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

O ficheiro que importou é apresentado na área **Conteúdos do ficheiro** do painel.
