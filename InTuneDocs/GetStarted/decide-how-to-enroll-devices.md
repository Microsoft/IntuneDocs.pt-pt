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
ms.assetid: 178df739-d3b9-43cb-8440-c5c110b1276b
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 90a26e1008a8e0800b07940c11a8adcd00cbb241
ms.openlocfilehash: becbaa195dc3fde6bc0a0edb0916c75a4d07c017


---

# Escolher como inscrever dispositivos móveis

A inscrição de dispositivos móveis é o processo pelo qual smartphones, tablets e PCs são adicionados à gestão pelo Microsoft Intune. Como administrador, tem de determinar o melhor método para inscrever os dispositivos com base no seguinte:

 -  Propriedade (pessoal ou pertencente à empresa)
 -  Utilização (partilhado ou pessoal)
 -  Plataforma (iOS, Android, Windows Phone, PC Windows, PC Mac)

As respostas às questões que se seguem irão ajudá-lo a determinar o melhor método de inscrição para os dispositivos que gere.

## **Os empregados utilizam os respetivos dispositivos ou os fornecidos pela sua organização?**

  - **Dispositivos pertencentes ao utilizador** - inscrição "BYOD" (Bring your own device) – os utilizadores podem instalar a aplicação do Portal da Empresa do Intune nos dispositivos deles e, depois, inscrevê-los, obtendo acesso aos recursos da empresa como e-mail, aplicações da empresa, dados da empresa e suporte.  

  - **Dispositivos pertencentes à empresa** - é possível inscrever dispositivos pertencentes à empresa (COD) de diversas formas, consoante as necessidades da organização e os tipos de dispositivos geridos.

> [!div class="button"]
[Inscrição BYOD>](#what-byod-devices-can-your-users-enroll)   [Inscrição COD >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## **Que dispositivos BYOD podem inscrever os seus utilizadores?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile e Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [PCs Windows](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## **Os dispositivos pertencentes à empresa são partilhados ou têm utilizadores dedicados?**

- **Dispositivos pertencentes à empresa partilhados** - estes dispositivos não têm um único utilizador e, normalmente, não estão configurados para aceder ao e-mail. Alguns exemplos incluem dispositivos de local público ou dispositivos orientados para tarefas e que os utilizadores recolhem quando precisam dos mesmos e, depois, devolvem. Os métodos de inscrição recomendados dependem da plataforma dos dispositivos.

- **Utilizadores Dedicados** - os dispositivos pertencentes à empresa atribuídos a utilizadores individuais têm de ser monitorizados como ativos da empresa e permitir, simultaneamente, aos utilizadores aceder a e-mail e dados como dispositivos pessoais. Os métodos de inscrição recomendados dependem da plataforma dos dispositivos.

> [!div class="button"]
[Partilhados >](#what-operating-system-are-your-shared-devices-running)   [Dedicados >](#how-will-you-manage-dedicated-ios-devices)


## **Qual é o sistema operativo dos dispositivos partilhados?**

  > [!div class="button"]
  [Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## **Como vai gerir os dispositivos iOS partilhados?**

- **Programa de registo de dispositivos da Apple (DEP)** - os dispositivos iOS adquiridos ou geridos com o DEP podem ser segmentados com um perfil de inscrição. Da primeira vez que os utilizadores inscrevem os dispositivos, estes transferem o perfil do DEP e são inscritos com o mesmo.

- **Apple Configurator num Mac** - o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração. Se não quiser repor os dispositivos para as definições de fábrica, utilize a inscrição direta.

- **Gestor de Inscrição de Dispositivos** - o gestor de inscrição de dispositivos (DEM) do Intune permite a um gestor ou administrador inscrever vários dispositivos móveis com uma única conta de utilizador. Estes dispositivos não podem ter afinidade do utilizador (ou seja, utilizadores dedicados) e têm de estar inscritos através da instalação e início de sessão na aplicação Portal da Empresa.

  > [!div class="button"]
  [Inscrição de DEP para iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Inscrição direta para iOS >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [Inscrição de DEM >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

## **Como vai gerir os dispositivos iOS dedicados?**

Pode inscrever dispositivos pertencentes à empresa com utilizadores dedicados através das seguintes formas:

- **Programa de registo de dispositivos da Apple (DEP)** - os dispositivos iOS adquiridos ou geridos com o DEP podem ser segmentados com um perfil de inscrição. Da primeira vez que os utilizadores inscrevem os dispositivos, estes transferem o perfil do DEP e são inscritos com o Intune.

- **Apple Configurator num Mac** - o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração.

- **Etiqueta com o número IMEI** - ao importar os números de identidade internacional do equipamento móvel (IMEI) dos dispositivos pertencentes à empresa, pode marcá-los como tal no Intune. Os utilizadores podem, em seguida, inscrever os dispositivos deles como dispositivos pessoais através da instalação do Portal da Empresa para aceder aos recursos da empresa, como e-mail, aplicações e dados.

  > [!div class="button"]
  [Etiqueta com IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [DEP para iOs](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Assistente de Configuração de iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Etiqueta com IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Aug16_HO2-->


