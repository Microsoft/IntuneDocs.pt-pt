---
title: "Definições personalizadas do Intune para dispositivos macOS"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba quais são as definições que pode utilizar num perfil personalizado do macOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 84902bb0e7ea67b388debd8bd7992d396d981a7b
ms.lasthandoff: 02/18/2017


---

# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Definições personalizadas para dispositivos macOS no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize o perfil personalizado do macOS do Microsoft Intune para implementar as definições que criou com a [Ferramenta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) para dispositivos macOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para um perfil personalizado do macOS do Intune e atribuir as definições a utilizadores e dispositivos da sua organização.

Esta capacidade permite-lhe implementar definições do macOS que não são configuráveis com outros tipos de perfis do Intune.


1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](how-to-configure-custom-settings.md) para começar.
2. No painel **Criar Perfil**, especifique o seguinte:

- **Nome do perfil de configuração personalizada** – Indique um nome para a política, o qual será apresentado no dispositivo e no estado do Intune.
- **Ficheiro de perfil de configuração** – Navegue até ao perfil de configuração que criou ao utilizar o Apple Configurator.
Confirme que as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do macOS nos dispositivos nos quais implementou a política personalizada do macOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

O ficheiro que importou será apresentado na área **Conteúdos do ficheiro** do painel.

