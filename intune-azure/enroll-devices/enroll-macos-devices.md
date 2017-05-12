---
title: Inscrever dispositivos macOS no Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como inscrever dispositivos macOS na pré-visualização do Azure no Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 6fcbeb30fb11b6bc8def3a1c245bff56b3f7cca4
ms.contentlocale: pt-pt
ms.lasthandoff: 05/10/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Inscrever dispositivos macOS na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Intune permite-lhe gerir dispositivos macOS. Para ativar a gestão de dispositivos, os utilizadores têm de inscrever os seus dispositivos ao aceder ao [site do Portal da Empresa](http://portal.manage.microsoft.com) e seguir as instruções. Assim que os dispositivos macOS estiverem a ser geridos, pode [criar definições personalizadas para dispositivos macOS](../configure-devices/custom-for-macos.md). Serão disponibilizadas brevemente funcionalidades adicionais.

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos macOS, tem de cumprir os seguintes pré-requisitos:

- [Configurar domínios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Definir a Autoridade de MDM](set-mdm-authority.md)
- [Criar grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar o Portal da Empresa](../manage-apps/company-portal-app.md)
- Atribuir licenças de utilizador no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Configurar a inscrição de macOS

Por predefinição, o Intune permite a inscrição de dispositivos macOS.

Para impedir a inscrição de dispositivos macOS, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](set-enrollment-restrictions.md#set-device-type-restrictions).

Para definir o máximo de dispositivos que um utilizador pode inscrever, veja [Set device limit restrictions (Definir restrições de limite de dispositivos)](set-enrollment-restrictions.md#set-device-limit-restrictions).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicar aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Terá de indicar aos utilizadores para acederem ao [site do Portal da Empresa](http://portal.manage.microsoft.com) e seguirem as instruções para inscrever os seus dispositivos. Também poderá enviar-lhes uma ligação para os passos de inscrição online: [Inscrever o dispositivo macOS no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos).

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Utilizar o seu dispositivo iOS ou macOS com o Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)

