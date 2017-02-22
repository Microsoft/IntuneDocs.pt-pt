---
title: "Definições personalizadas do Intune para dispositivos iOS | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba quais são as definições que pode utilizar num perfil personalizado do iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: cfccdbf34437c5ab23cefba5307c53c60573ddb0


---

# <a name="intune-custom-settings-for-ios-devices-in-intune-azure-preview"></a>Definições personalizadas do Intune para dispositivos iOS na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize o perfil personalizado do iOS do Microsoft Intune para implementar as definições que criou com a [Ferramenta Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) para dispositivos iOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para um perfil personalizado do iOS do Intune e atribuir as definições a utilizadores e dispositivos da sua organização.

Esta capacidade permite-lhe implementar definições do iOS que não são configuráveis com outros tipos de perfis do Intune.


1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](how-to-configure-custom-settings.md) para começar.
2. No painel **Criar Perfil**, especifique o seguinte:

- **Nome do perfil de configuração personalizada** – Indique um nome para a política, o qual será apresentado no dispositivo e no estado do Intune.
- **Ficheiro de perfil de configuração** – Navegue até ao perfil de configuração que criou ao utilizar o Apple Configurator.
Certifique-se de que as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do iOS nos dispositivos nos quais implementou a política personalizada do iOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).

O ficheiro que importou será apresentado na área **Conteúdos do ficheiro** do painel.



<!--HONumber=Feb17_HO1-->


