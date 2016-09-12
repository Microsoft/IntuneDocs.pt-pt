---
title: "Como os utilizadores de dispositivos Android obtêm as aplicações | Microsoft Intune"
description: "Métodos para disponibilizar aplicações Android aos utilizadores finais"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 90f50d14fac0e335f3b7c5e0825b0bb243b7a532


---


# Como os utilizadores de dispositivos Android obtêm as aplicações
Utilize estas informações para saber como e onde é que os seus utilizadores finais de Android podem obter as aplicações que distribuir através do Microsoft Intune. Estas informações podem ser diferentes entre os dispositivos Android nativos e os dispositivos Samsung Knox.

## Dispositivos Android nativos (não Samsung Knox)

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. É apresentada uma notificação, na qual os utilizadores tocam para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. | Os utilizadores tocam na aplicação no Portal da Empresa e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação.|
| Required apps      | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece.    | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

## Dispositivos Android Samsung Knox

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. A aplicação é instalada sem intervenção do utilizador adicional. | Os utilizadores tocam na aplicação no Portal da Empresa e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação.|
| Required apps      | A aplicação é instalada sem qualquer intervenção do utilizador.    | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

As aplicações podem ser geridas ou não geridas, conforme descrito abaixo. O processo para tornar as aplicações geridas é igual para todos os tipos de dispositivos Android.

**Aplicações geridas** - aplicações que podem ser geridas através de políticas e que foram "encapsuladas" pelo Intune ou incorporadas no Software Development Kit (SDK) do Intune Mobile Application Management (MAM). Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

**aplicações não geridas** - aplicações que podem ser geridas através de políticas e que não foram encapsuladas pelo Intune ou que não incorporam o SDK do Intune MAM. Não é possível aplicar políticas de aplicação a estas aplicações.

### Consulte também
[Adicionar aplicações com o Microsoft Intune](/intune/deploy-use/add-apps)
[Como os utilizadores de iOS obtêm as aplicações](how-your-ios-users-get-their-apps.md)
[Como os utilizadores do Windows obtêm as aplicações](how-your-windows-users-get-their-apps.md)



<!--HONumber=Jul16_HO4-->


