---
title: "Inscrever dispositivos macOS no Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como inscrever dispositivos macOS na pré-visualização do Azure no Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Inscrever dispositivos macOS na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador do Intune, pode gerir dispositivos macOS. Por predefinição, o portal do Azure permite aos utilizadores inscrever os dispositivos macOS. Apenas terá de informar os utilizadores para acederem ao [site do Portal da Empresa](http://portal.manage.microsoft.com) e inscreverem o dispositivo macOS. 

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos macOS, tem de cumprir os seguintes pré-requisitos:

- [Configurar domínios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Definir a Autoridade de MDM](set-mdm-authority.md)
- [Criar grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar o Portal da Empresa](/intune-azure/manage-apps/company-portal-app.md)
- Atribuir licenças de utilizador no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Configurar a inscrição de macOS

Por predefinição, o Intune já está configurado para permitir a inscrição de dispositivos macOS. 

Para ver a definição para permitir ou bloquear a inscrição de dispositivos macOS, aceda ao painel do Intune no portal do Azure e escolha **Inscrição** > **Restrições de Inscrição**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indique aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Para obter as instruções de inscrição do utilizador final, veja [Inscrever o dispositivo macOS no Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos). O processo de inscrição informa os utilizadores sobre o que podem esperar e o que os administradores de TI podem e não podem ver nos respetivos dispositivos.

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Utilizar o seu dispositivo iOS ou macOS com o Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


