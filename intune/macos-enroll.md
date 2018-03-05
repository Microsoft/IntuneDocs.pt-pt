---
title: Inscrever dispositivos macOS no Intune
titlesuffix: Azure portal
description: "Saiba como inscrever dispositivos Mac OS no Intune.\""
keywords: 
author: ErikjeMS
ms.author: erikje
nmanager: dougeby
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f896ebd51f989c0e441043d320247946cdb8997b
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-macos-devices-in-intune"></a>Inscrever dispositivos macOS no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune permite-lhe gerir dispositivos macOS. Para ativar a gestão de dispositivos, os utilizadores têm de inscrever os seus dispositivos ao aceder ao [site do Portal da Empresa](http://portal.manage.microsoft.com) e seguir as instruções. Assim que os dispositivos macOS estiverem a ser geridos, pode [criar definições personalizadas para dispositivos macOS](custom-settings-macos.md). Serão disponibilizadas brevemente funcionalidades adicionais.

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos macOS, tem de cumprir os seguintes pré-requisitos:

- [Configurar domínios](custom-domain-name-configure.md)
- [Definir a Autoridade de MDM](mdm-authority-set.md)
- [Criar grupos](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar o Portal da Empresa](company-portal-app.md)
- Atribuir licenças de utilizador no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>Configurar a inscrição de macOS

Por predefinição, o Intune permite a inscrição de dispositivos macOS.

Para impedir a inscrição de dispositivos macOS, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicar aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Indique aos utilizadores finais para acederem ao [site do Portal da Empresa](http://portal.manage.microsoft.com) e seguirem as instruções para inscrever os dispositivos. Também poderá enviar-lhes uma ligação para os passos de inscrição online: [Inscrever o dispositivo macOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](end-user-educate.md)
- [Utilizar o dispositivo macOS com o Intune](/intune-user-help/using-your-macos-device-with-intune)
