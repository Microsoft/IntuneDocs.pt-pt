---
title: "Como os utilizadores de dispositivos Android obtêm as aplicações"
description: "Métodos para disponibilizar aplicações Android aos utilizadores finais"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fac1ce49584af299face679270dcc43decc4d2f5
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Como os utilizadores de dispositivos Android obtêm as aplicações

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Utilize estas informações para saber como e onde é que os seus utilizadores finais de Android podem obter as aplicações que distribuir através do Microsoft Intune. As informações podem variar de acordo com o tipo de dispositivo (dispositivos Android nativos ou dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (não Samsung Knox Standard)

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. É apresentada uma notificação, na qual os utilizadores tocam para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. | Os utilizadores tocam na aplicação no Portal da Empresa e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação.|
| Required apps      | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece.    | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

Os seus utilizadores finais têm de permitir a instalação a partir de origens desconhecidas para instalar [Aplicações LOB](lob-apps-android.md). Normalmente, estas aplicações encontram-se em dois locais:

* **Android 7.1.2 e inferior**: **Definições** > **Segurança** > **Fontes desconhecidas**
* **Android 8.0 e superior**: **Definições** > **Aplicações e notificações** > **Acesso de aplicações especiais** > **Instalar aplicações desconhecidas** > **Portal da Empresa** > **Permitir desta fonte**

Neste caso, a aplicação Portal da Empresa irá informar e orientar o utilizador final consoante a definição adequada. 


## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Android Samsung Knox Standard

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. A aplicação é instalada sem intervenção do utilizador adicional. | Os utilizadores tocam na aplicação no Portal da Empresa e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação.|
| Required apps      | A aplicação é instalada sem qualquer intervenção do utilizador.    | É apresentada uma notificação aos utilizadores, que não pode ser rejeitada, a indicar que têm de instalar uma aplicação. Os utilizadores tocam na notificação e são encaminhados para uma página da aplicação na Play Store, onde podem iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

As aplicações podem ser geridas ou não geridas, conforme descrito abaixo. O processo para tornar as aplicações geridas é igual para todos os tipos de dispositivos Android.

**Aplicações geridas** – são as aplicações que podem ser geridas através das políticas. Foram "encapsuladas" pelo Intune ou compiladas com o SDK da Aplicação Intune. Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

**Aplicações não geridas** – são as aplicações que não podem ser geridas através das políticas. Não foram encapsuladas pelo Intune ou não fazem parte do SDK da Aplicação Intune. Não é possível aplicar políticas de aplicação a estas aplicações.

### <a name="see-also"></a>Consulte também
[Adicionar aplicações com o Microsoft Intune](apps-add.md)

[Como os utilizadores de dispositivos iOS obtêm as aplicações](end-user-apps-ios.md)

[Como os utilizadores de dispositivos Windows obtêm as aplicações](end-user-apps-windows.md)
