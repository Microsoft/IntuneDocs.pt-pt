---
title: Como os utilizadores de dispositivos Android obtêm as aplicações
description: Métodos para disponibilizar aplicações Android aos utilizadores finais
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 231b30e93a3e56811e1569c32cc1286e02320f0d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514409"
---
# <a name="how-your-android-users-get-their-apps"></a>Como os utilizadores de dispositivos Android obtêm as aplicações

Este artigo ajuda-o a perceber como e onde os utilizadores finais do Android obtêm as aplicações que distribui através do Microsoft Intune. As informações podem variar de acordo com o tipo de dispositivo (dispositivos Android nativos ou dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (não Samsung Knox Standard)

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. É apresentada uma notificação, na qual os utilizadores tocam para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. | Os utilizadores tocam na aplicação no Portal da Empresa e são levados para uma página de aplicações na Play Store. É aqui que iniciam a instalação.|
| Required apps      | Os utilizadores recebem uma notificação, que não podem descartar, indicando que precisam de instalar uma aplicação. Os utilizadores tocam na notificação para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece.    | Os utilizadores recebem uma notificação, que não podem descartar, indicando que precisam de instalar uma aplicação. Os utilizadores tocam na notificação e são levados para uma página de aplicações na Play Store. É aqui que iniciam a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

Os utilizadores finais precisam de permitir a instalação de fontes desconhecidas para instalar [aplicações LOB](../apps/lob-apps-android.md). Esta configuração é normalmente encontrada em dois lugares diferentes:

* **Android 7.1.2 e inferior**: **Definições** > **Segurança** > **Fontes desconhecidas**
* **Android 8.0 e superior**: **Definições** > **Aplicações e notificações** > **Acesso de aplicações especiais** > **Instalar aplicações desconhecidas** > **Portal da Empresa** > **Permitir desta fonte**

Neste caso, a aplicação Portal da Empresa irá informar e orientar o utilizador final consoante a definição adequada. 

## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Android Samsung Knox Standard

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. A aplicação é instalada sem intervenção do utilizador adicional. | Os utilizadores tocam na aplicação no Portal da Empresa e são levados para uma página de aplicações na Play Store. É aqui que iniciam a instalação.|
| Required apps      | A aplicação é instalada sem qualquer intervenção do utilizador.    | Os utilizadores recebem uma notificação, que não podem descartar, indicando que precisam de instalar uma aplicação. Os utilizadores tocam na notificação e são levados para uma página de aplicações na Play Store. É aqui que iniciam a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

As aplicações podem ser geridas ou não geridas, conforme descrito abaixo. O processo para tornar as aplicações geridas é igual para todos os tipos de dispositivos Android.

**Aplicativos geridos** - Estas aplicações são geridas através de políticas. Foram "embrulhados" pela Intune ou construídos com o Intune App SDK. Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

Apps não **geridas** - Estas aplicações não são geridas através de políticas. Não foram embrulhados pela Intune ou não incorporam o Intune App SDK. As políticas de aplicação não podem ser aplicadas a estas aplicações.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Dispositivos zebra com extensões de mobilidade da zebra

Intune usa o conjunto de ferramentas Zebra Mobility Extensions (MX) para instalar silenciosamente aplicações em dispositivos Zebra geridos pelo administrador do dispositivo. Esta funcionalidade permite-lhe implementar e atualizar aplicações em dispositivos Zebra sem a intervenção do utilizador. Se a versão MX do seu dispositivo for 4.2 ou mais antiga, então as aplicações não são instaladas silenciosamente. Para mais informações, consulte [full MX Feature Matrix](http://techdocs.zebra.com/mx/compatibility/) no site da Zebra.

As aplicações LOB implantadas para dispositivos Zebra devem ser instaladas a partir de uma localização pública no dispositivo. O pacote de aplicações .apk pode ser acessível a outras aplicações e serviços que também tenham acesso ao armazenamento público no dispositivo. Normalmente, este acesso é uma pequena janela entre o download da aplicação e no início da instalação. Esta janela pode permitir um ataque de tempo. Por exemplo, um pacote .apk pode ser alterado durante esta janela. Intune minimiza o tempo que a .apk passa em armazenamento público, e não permite que as aplicações não assinadas se instalem. Para ajudar a minimizar o risco de segurança, certifique-se de que os ficheiros .apk que envia não contêm informações sensíveis.

## <a name="see-also"></a>Veja também

[Adicionar aplicações com o Microsoft Intune](../apps/apps-add.md)

[Como os seus utilizadores iOS/iPadOS obtêm as suas aplicações](end-user-apps-ios.md)

[Como os utilizadores de dispositivos Windows obtêm as aplicações](end-user-apps-windows.md)
