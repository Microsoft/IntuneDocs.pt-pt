---
title: "Como os utilizadores de dispositivos Android obtêm as aplicações"
description: "Métodos para disponibilizar aplicações Android aos utilizadores finais"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4f0364750edf2e97e2b621c27fb25bea8e0f537c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Como os utilizadores de dispositivos Android obtêm as aplicações

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Utilize estas informações para saber como e onde é que os seus utilizadores finais de Android podem obter as aplicações que distribuir através do Microsoft Intune. As informações podem variar de acordo com o tipo de dispositivo (dispositivos Android nativos ou dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (não Samsung Knox Standard)

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. É apresentada uma notificação, na qual os utilizadores tocam para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. | Os utilizadores tocam na aplicação no Portal da Empresa e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação.|
| Required apps      | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece.    | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Android Samsung Knox Standard

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. A aplicação é instalada sem intervenção do utilizador adicional. | Os utilizadores tocam na aplicação no Portal da Empresa e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação.|
| Required apps      | A aplicação é instalada sem qualquer intervenção do utilizador.    | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

As aplicações podem ser geridas ou não geridas, conforme descrito abaixo. O processo para tornar as aplicações geridas é igual para todos os tipos de dispositivos Android.

**Aplicações geridas** – são as aplicações que podem ser geridas através das políticas. Aplicações que foram "encapsuladas" pelo Intune ou criadas no Software Development Kit (SDK) da Gestão de Aplicações Móveis (MAM) do Intune. Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

**Aplicações não geridas** – são as aplicações que não podem ser geridas através das políticas. Não foram encapsuladas pelo Intune ou não fazem parte do SDK de MAM do Intune. Não é possível aplicar políticas de aplicação a estas aplicações.

### <a name="see-also"></a>Consulte também
[Adicionar aplicações com o Microsoft Intune](apps-add.md)

[Como os utilizadores de dispositivos iOS obtêm as aplicações](end-user-apps-ios.md)

[Como os utilizadores de dispositivos Windows obtêm as aplicações](end-user-apps-windows.md)