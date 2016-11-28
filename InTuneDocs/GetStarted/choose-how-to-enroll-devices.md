---
title: "Escolher como inscrever dispositivos móveis | Microsoft Intune"
description: "Decidir como inscrever dispositivos móveis no Intune respondendo a algumas perguntas simples"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: a563105aafb447c6e009cca09645e630709ff72d
ms.openlocfilehash: 143f77bde09648a233ff09e9740668191a50cb1e


---

# <a name="choose-how-to-enroll-mobile-devices"></a>Escolher como inscrever dispositivos móveis

As respostas às seguintes perguntas ajudam-no a determinar o melhor método de inscrição para os dispositivos que gere.

## <a name="do-employees-bring-their-own-devices-or-are-devices-provided-by-your-organization"></a>**Os funcionários utilizam os respetivos dispositivos ou os fornecidos pela sua organização?**

  - **Dispositivos pertencentes ao utilizador** – inscrição "Bring Your Own Device" (BYOD)
  - **Dispositivos pertencentes à empresa** – inscrição COD

> [!div class="button"]
[Inscrição BYOD >](#what-byod-devices-can-your-users-enroll)   
> [!div class="button"]
[Inscrição COD >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## <a name="what-byod-devices-can-your-users-enroll"></a>**Que dispositivos BYOD podem os seus utilizadores inscrever?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile e Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [PCs Windows](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## <a name="are-your-company-owned-devices-shared-or-do-they-have-dedicated-users"></a>**Os dispositivos pertencentes à empresa são partilhados ou têm utilizadores dedicados?**

> [!div class="button"]
[Partilhados >](#what-operating-system-are-your-shared-devices-running)   [Dedicados >](#how-will-you-manage-dedicated-ios-devices)


## <a name="what-operating-system-are-your-shared-devices-running"></a>**Qual é o sistema operativo dos dispositivos partilhados?**

> [!div class="button"]
[Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## <a name="how-will-you-manage-shared-ios-devices"></a>**Como irá gerir os dispositivos iOS partilhados?**

> [!div class="button"]
[Inscrição de DEP para iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Inscrição direta para iOS >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [Inscrição de DEM >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Programa de Registo de Dispositivos da Apple (DEP)** – os dispositivos iOS adquiridos ou geridos com o DEP podem ser associados a um perfil de inscrição. Da primeira vez que os utilizadores ligam os dispositivos, estes transferem o perfil do DEP e são inscritos com o mesmo.

  - **Apple Configurator num Mac** – o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a opção de inscrição através do Assistente de Configuração. Se não quiser repor os dispositivos para as definições de fábrica, utilize a opção de inscrição Direta.

  - **Gestor de inscrição de dispositivos (Intune)** – o gestor de inscrição de dispositivos (DEM) do Intune permite a um gestor ou administrador inscrever vários dispositivos móveis com uma única conta de utilizador. Estes dispositivos não podem ter utilizadores dedicados (afinidade de utilizadores) e têm de ser inscritos através da instalação e início de sessão na aplicação Portal da Empresa.

## <a name="how-will-you-manage-dedicated-ios-devices"></a>**Como irá gerir os dispositivos iOS dedicados?**

> [!div class="button"]
[DEP para iOS](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Assistente de Configuração de iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Etiqueta com IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Pode inscrever dispositivos pertencentes à empresa com utilizadores dedicados através das seguintes formas:

  - **Programa de Registo de Dispositivos da Apple (DEP)** – os dispositivos iOS adquiridos ou geridos com o DEP podem ser associados a um perfil de inscrição. Da primeira vez que os utilizadores ligarem os dispositivos, estes transferem o perfil do DEP e são inscritos com o Intune.

  - **Apple Configurator num Mac** – o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a opção de inscrição através do Assistente de Configuração.

  - **Etiqueta com o número IMEI** – ao importar os números de identidade internacional do equipamento móvel (IMEI) dos dispositivos pertencentes à empresa, pode marcá-los como tal no Intune. Os utilizadores podem, em seguida, inscrever os dispositivos deles como dispositivos pessoais através da instalação do Portal da Empresa, para aceder aos recursos da empresa, como e-mail, aplicações e dados.



<!--HONumber=Nov16_HO4-->


