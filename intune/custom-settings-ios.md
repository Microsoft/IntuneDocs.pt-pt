---
title: "Definições personalizadas do Intune para dispositivos iOS"
titleSuffix: Azure portal
description: "Saiba quais são as definições que pode utilizar num perfil personalizado do iOS.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f7dfb69b8e837229eac9a4cdd68316a7559441f4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="microsoft-intune-custom-settings-for-ios-devices"></a>Definições personalizadas do Microsoft Intune para dispositivos iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize o perfil personalizado do iOS do Microsoft Intune para atribuir as definições que criou com a [Ferramenta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) a dispositivos iOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para um perfil personalizado do iOS do Intune e atribuir as definições a utilizadores e dispositivos da sua organização.

Esta capacidade permite-lhe atribuir definições do iOS que não são configuráveis com outros tipos de perfis do Intune.


1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. No painel **Criar Perfil**, especifique o seguinte:

- **Nome do perfil de configuração personalizada** – Indique um nome para a política, o qual será apresentado no dispositivo e no estado do Intune.
- **Ficheiro de perfil de configuração** – Navegue até ao perfil de configuração que criou ao utilizar o Apple Configurator.
Confirme se as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do iOS nos dispositivos aos quais atribuiu a política personalizada do iOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

O ficheiro que importou será apresentado na área **Conteúdos do ficheiro** do painel.
