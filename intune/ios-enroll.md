---
title: Escolher como inscrever dispositivos Windows no Intune
titleSuffix: Intune on Azure
description: "Saiba como configurar a inscrição de dispositivos Windows no Microsoft Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrever dispositivos iOS no Intune

O Intune ativa a gestão de dispositivos móveis (MDM) de iPads e iPhones para conceder aos utilizadores acesso a aplicações e ao e-mail da empresa.

Enquanto administrador do Intune, pode ativar a inscrição para dispositivos iOS. Pode permitir que os utilizadores inscrevam dispositivos pessoais. Este processo é conhecido como inscrição BYOD (Bring Your Own Device). Também pode ativar a inscrição de dispositivos pertencentes à empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Pré-requisitos para a inscrição de dispositivos iOS
Antes de poder ativar dispositivos iOS, conclua os seguintes passos:
- [Configurar o Intune](setup-steps.md) – estes passos irão configurar a sua infraestrutura do Intune, em particular as inscrições de dispositivos que exigem que [defina a autoridade MDM](mdm-authority-set.md).
- [Obter um Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md) - a Apple exige um certificado para ativar a gestão de dispositivos iOS e macOS.

Quando estes pré-requisitos forem cumpridos, os utilizadores podem instalar a aplicação Portal da Empresa para inscrever os respetivos dispositivos pessoais iOS ou o administrador pode configurar a gestão de dispositivos iOS pertencentes à empresa. Os administradores também podem atribuir [gestores de inscrição de dispositivos](device-enrollment-manager-enroll.md), os quais podem inscrever vários dispositivos com uma única conta de gestão. O Intune suporta os seguintes métodos de inscrição de dispositivos iOS pertencentes à empresa:

## <a name="device-enrollment-program"></a>Programa de Inscrição de Dispositivos
As organizações podem adquirir dispositivos iOS através do Programa de Inscrição de Dispositivos (DEP) da Apple. O DEP permite-lhe implementar um perfil de inscrição através de uma ligação sem fios para incluir os dispositivos na gestão. Saiba mais sobre o [Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Gestor Escolar da Apple
O Gestor Escolar da Apple é um programa de compra e inscrição de dispositivos da Apple para escolas. À semelhança do DEP, pode implementar um perfil para inscrever dispositivos para gestão. Saiba mais sobre o [Gestor Escolar da Apple](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Pode inscrever dispositivos iOS com o Apple Configurator num computador Mac. Para preparar os dispositivos, deve ligá-los via USB e instalar um perfil de inscrição. Pode inscrever dispositivos com o Apple Configurator de duas formas:
- Inscrição com o Assistente de Configuração – realiza a reposição de fábrica do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.
- Inscrição direta – não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos sem afinidade de utilizador.

Saiba mais sobre a [inscrição no Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
