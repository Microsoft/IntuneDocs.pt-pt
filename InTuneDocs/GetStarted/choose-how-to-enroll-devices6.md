---
title: "Escolher como inscrever dispositivos móveis | Microsoft Intune"
description: "Decidir como inscrever dispositivos móveis no Intune respondendo a algumas perguntas simples"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: a5f80058e004f119acc9a918123c897b72b71314
ms.openlocfilehash: ecc6834b18d7906633bf1a029f5d63a4432c4989


---
# Escolher como inscrever dispositivos móveis

As respostas a esta série de questões irão ajudá-lo a determinar o melhor método de inscrição para os dispositivos que gere.

## **Como vai gerir os dispositivos dedicados pertencentes à empresa?**

  > [!div class="button"]
[iOS DEP >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)<br>[Assistente de Configuração de iOS >](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)<br>[Identificar com IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Pode inscrever dispositivos pertencentes à empresa com utilizadores dedicados através das seguintes formas:

  - **Programa de registo de dispositivos da Apple (DEP)** - os dispositivos iOS adquiridos ou geridos com o DEP podem ser segmentados com um perfil de inscrição. Da primeira vez que os utilizadores inscrevem os dispositivos, estes transferem o perfil do DEP e são inscritos com o Intune.

  - **Apple Configurator num Mac** - o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração.

  - **Etiqueta com o número IMEI** - ao importar os números de identidade internacional do equipamento móvel (IMEI) dos dispositivos pertencentes à empresa, pode marcá-los como tal no Intune. Esta é a única forma de identificar dispositivos dedicados (“utilizador único”) do Windows e Android como pertencentes à empresa. Os dispositivos iOS que não vão ser inscritos no programa de inscrição de dispositivos da Apple ou no Apple Configurator também podem ser etiquetados com um número IMEI. Após declarar previamente o dispositivo para que seja etiquetado como “corporativo”, pode distribuir os dispositivos para os utilizadores. Os utilizadores podem, em seguida, inscrever os respetivos dispositivos como dispositivos dedicados através da instalação do Portal da Empresa para aceder aos recursos da empresa, como e-mail, aplicações e dados.

  > [!div class="button"]
  [< Anterior](choose-how-to-enroll-devices3.md)



<!--HONumber=Aug16_HO5-->


