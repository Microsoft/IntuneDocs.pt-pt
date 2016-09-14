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
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 899f50cfec9e7c20d2981c077f93e0fccf37dc2b
ms.openlocfilehash: fea9e10de761fa1bacfb87d07ce571d40f8286bc


---
# Escolher como inscrever dispositivos móveis

As respostas a esta série de questões irão ajudá-lo a determinar o melhor método de inscrição para os dispositivos que gere.


## **Como vai gerir os dispositivos iOS partilhados?**

  > [!div class="button"]
  [Inscrição do DEP para iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
  > [!div class="button"]
  [Inscrição Direta para iOS >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)
  > [!div class="button"]
  [Inscrição de DEM >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Programa de registo de dispositivos da Apple (DEP)** - os dispositivos iOS adquiridos ou geridos com o DEP podem ser segmentados com um perfil de inscrição. Da primeira vez que os utilizadores inscrevem os dispositivos, estes transferem o perfil do DEP e são inscritos com o mesmo.

  - **Apple Configurator num Mac** - o Apple Configurator é uma aplicação da Apple que é executada em PCs Mac. Pode ligar os seus dispositivos iOS ao Mac com um cabo USB para instalar um perfil de inscrição nos mesmos. Se puder repor os dispositivos para as definições de fábrica para os inscrever, utilize a inscrição através do Assistente de Configuração. Se não quiser repor os dispositivos para as definições de fábrica, utilize a inscrição direta.

  - **Gestor de Inscrição de Dispositivos** - o gestor de inscrição de dispositivos (DEM) do Intune permite a um gestor ou administrador inscrever vários dispositivos móveis com uma única conta de utilizador. Estes dispositivos não podem ter afinidade do utilizador (ou seja, utilizadores dedicados) e têm de estar inscritos através da instalação e início de sessão na aplicação Portal da Empresa.

  > [!div class="button"]
  [< Anterior](choose-how-to-enroll-devices3.md)



<!--HONumber=Sep16_HO2-->


