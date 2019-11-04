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
ms.openlocfilehash: 40e8dd8409f70a70934684c56ed9e9729f4ebf0f
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414593"
---
# <a name="how-your-android-users-get-their-apps"></a>Como os utilizadores de dispositivos Android obtêm as aplicações

Este artigo ajuda você a entender como e onde os usuários finais do Android obtêm os aplicativos que você distribui por meio de Microsoft Intune. As informações podem variar de acordo com o tipo de dispositivo (dispositivos Android nativos ou dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (não Samsung Knox Standard)

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. É apresentada uma notificação, na qual os utilizadores tocam para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. | Os usuários tocam o aplicativo na Portal da Empresa e são levados para uma página de aplicativo no Play Store. É aqui que eles iniciam a instalação.|
| Required apps      | Os usuários são mostrados uma notificação, que não podem ser descartados, indicando que eles precisam instalar um aplicativo. Os utilizadores tocam na notificação para iniciar a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece.    | Os usuários são mostrados uma notificação, que não podem ser descartados, indicando que eles precisam instalar um aplicativo. Os usuários tocam na notificação e são levados para uma página de aplicativo no Play Store. É aqui que eles iniciam a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

Os usuários finais precisam permitir a instalação de fontes desconhecidas para instalar [aplicativos LOB](../apps/lob-apps-android.md). Essa configuração normalmente é encontrada em dois locais diferentes:

* **Android 7.1.2 e inferior**: **Definições** > **Segurança** > **Fontes desconhecidas**
* **Android 8.0 e superior**: **Definições** > **Aplicações e notificações** > **Acesso de aplicações especiais** > **Instalar aplicações desconhecidas** > **Portal da Empresa** > **Permitir desta fonte**

Neste caso, a aplicação Portal da Empresa irá informar e orientar o utilizador final consoante a definição adequada. 

## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Android Samsung Knox Standard

| Tipo de aplicação | Aplicações de linha de negócio (LOB) | Aplicações da Play Store  |
| ------------- |-------------| -----|
| Aplicações disponíveis      | Os utilizadores tocam em **instalar** no Portal da Empresa. A aplicação é instalada sem intervenção do utilizador adicional. | Os usuários tocam o aplicativo na Portal da Empresa e são levados para uma página de aplicativo no Play Store. É aqui que eles iniciam a instalação.|
| Required apps      | A aplicação é instalada sem qualquer intervenção do utilizador.    | Os usuários são mostrados uma notificação, que não podem ser descartados, indicando que eles precisam instalar um aplicativo. Os usuários tocam na notificação e são levados para uma página de aplicativo no Play Store. É aqui que eles iniciam a instalação. Depois de a instalação ter sido concluída com êxito, a notificação desaparece. |

As aplicações podem ser geridas ou não geridas, conforme descrito abaixo. O processo para tornar as aplicações geridas é igual para todos os tipos de dispositivos Android.

**Aplicativos gerenciados** -esses aplicativos são gerenciados por meio de políticas. Elas foram "encapsuladas" pelo Intune ou compiladas com o SDK de aplicativos do Intune. Estas aplicações podem ser geridas pelo Intune e podem ser aplicadas políticas de aplicação às mesmas.

**Aplicativos não gerenciados** -esses aplicativos não são gerenciados por meio de políticas. Eles não foram encapsulados pelo Intune ou não incorporam o SDK de aplicativos do Intune. As políticas de aplicativo não podem ser aplicadas a esses aplicativos.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Dispositivos pretas com extensões de mobilidade pretas

O Intune usa o kit de ferramentas do pretas Mobility Extensions (MX) para instalar silenciosamente aplicativos em dispositivos pretas gerenciados pelo administrador do dispositivo. Esse recurso permite implantar e atualizar aplicativos em dispositivos pretas sem a intervenção do usuário. Se a versão MX em seu dispositivo for 4,2 ou mais antiga, os aplicativos não serão instalados silenciosamente. Para obter mais informações, consulte [Full MX Feature Matrix](http://techdocs.zebra.com/mx/compatibility/) no site da pretas.

Os aplicativos LOB implantados em dispositivos pretas devem ser instalados de um local público no dispositivo. O pacote do aplicativo. apk pode ser acessível a outros aplicativos e serviços que também tenham acesso ao armazenamento público no dispositivo. Normalmente, esse acesso é uma pequena janela entre a conclusão do download do aplicativo e no início da instalação. Essa janela pode permitir um ataque de tempo. Por exemplo, um pacote. apk poderia ser alterado durante esta janela. O Intune minimiza a quantidade de tempo que o. apk gasta no armazenamento público e não permite que aplicativos não assinados sejam instalados. Para ajudar a minimizar o risco de segurança, certifique-se de que os arquivos. apk carregados não contenham informações confidenciais.

## <a name="see-also"></a>Consulte também

[Adicionar aplicações com o Microsoft Intune](../apps/apps-add.md)

[Como os utilizadores de dispositivos iOS obtêm as aplicações](end-user-apps-ios.md)

[Como os utilizadores de dispositivos Windows obtêm as aplicações](end-user-apps-windows.md)
