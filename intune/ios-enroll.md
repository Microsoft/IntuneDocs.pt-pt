---
title: Escolher como inscrever dispositivos Windows no Intune
titlesuffix: Azure portal
description: "Saiba como configurar a inscrição de dispositivos Windows no Microsoft Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 307f4b8d5ba27ce8136569e0c58711f9b1364d93
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrever dispositivos iOS no Intune

O Intune ativa a gestão de dispositivos móveis (MDM) de iPads e iPhones para conceder aos utilizadores acesso a aplicações e ao e-mail da empresa.

Enquanto administrador do Intune, pode ativar a inscrição para dispositivos iOS. Pode permitir que os utilizadores inscrevam dispositivos pessoais. Este processo é conhecido como inscrição BYOD (Bring Your Own Device). Também pode ativar a inscrição de dispositivos pertencentes à empresa.

## <a name="prerequisites-for-ios-enrollment"></a>Pré-requisitos para a inscrição de dispositivos iOS
Antes de poder ativar dispositivos iOS, conclua os seguintes passos:
- [Configurar o Intune](setup-steps.md) – estes passos irão configurar a sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md).
- [Obter um Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md) - a Apple exige um certificado para ativar a gestão de dispositivos iOS e macOS.

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS propriedade do utilizador (BYOD)

Pode permitir que os seus utilizadores inscrevam os respetivos dispositivos pessoais na gestão do Intune. Chama-se a isto "bring your own device (traga o seu próprio dispositivo)", ou BYOD. Após concluir os pré-requisitos e atribuir licenças aos utilizadores, estes podem transferir a aplicação Portal da Empresa para iOS a partir da App Store e seguir as instruções da inscrição na aplicação.

## <a name="company-owned-ios-devices"></a>Dispositivos iOS pertencentes à empresa
Para as organizações que compram dispositivos para os respetivos utilizadores, o Intune suporta os seguintes métodos de inscrição de dispositivos iOS pertencentes à empresa:

- Programa de Registo de Aparelho (DEP) da Apple
- Gestor Escolar da Apple
- Inscrição do Assistente de Configuração do Apple Configurator
- Inscrição direta no Apple Configurator

Também pode inscrever os dispositivos iOS pertencentes à empresa com uma conta de [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programa de Inscrição de Dispositivos
As organizações podem adquirir dispositivos iOS através do Programa de Inscrição de Dispositivos (DEP) da Apple. O DEP permite-lhe implementar um perfil de inscrição através de uma ligação sem fios para incluir os dispositivos na gestão. Saiba mais sobre o [Programa de Inscrição de Dispositivos](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Gestor Escolar da Apple
O Gestor Escolar da Apple é um programa de compra e inscrição de dispositivos da Apple para escolas. À semelhança do DEP, pode implementar um perfil para inscrever dispositivos para gestão. Saiba mais sobre o [Gestor Escolar da Apple](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Pode inscrever dispositivos iOS com o Apple Configurator num computador Mac. Para preparar os dispositivos, deve ligá-los via USB e instalar um perfil de inscrição. Pode inscrever dispositivos com o Apple Configurator de duas formas:
- Inscrição com o Assistente de Configuração – realiza a reposição de fábrica do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.
- Inscrição direta – não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos sem afinidade de utilizador.

Saiba mais sobre a [inscrição no Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
