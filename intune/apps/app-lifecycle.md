---
title: Descrição geral do ciclo de vida das aplicações do Microsoft Intune
description: Saiba mais sobre o ciclo de vida das aplicações geridas no Microsoft Intune. O ciclo de vida das aplicações envolve adicionar, implementar, configurar, proteger e extinguir aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 670e5033ddf2a04cd5bd87040d85eef764dca519
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512301"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Descrição geral do ciclo de vida das aplicações no Microsoft Intune

O ciclo de vida das aplicações do Microsoft Intune começa quando uma aplicação é adicionada e avança por fases adicionais até esta ser removida. Ao compreender estas fases, terá os detalhes necessários para começar com a gestão de aplicações em Intune.

![O ciclo de vida da aplicação - Adicionar, implementar, configurar, proteger e reformar- se.](./media/app-lifecycle/app-lifecycle.png "o ciclo de vida da app Intune")

## <a name="add"></a>Adicionar

O primeiro passo na implementação de aplicações consiste em adicionar as aplicações que pretende gerir e atribuir no Intune. Apesar de poder utilizar muitos tipos de aplicações diferentes, os procedimentos básicos são iguais. Com a Intune pode adicionar diferentes tipos de aplicações, incluindo aplicações escritas internamente (linha de negócio), aplicações da loja, apps que estão incorporadas e aplicações na web. Para obter mais informações sobre cada um destes tipos de aplicações, veja [Como adicionar uma aplicação ao Microsoft Intune](apps-add.md).

## <a name="deploy"></a>Implementar

Depois de adicionar a aplicação ao Intune, pode [atribuí-la aos utilizadores e dispositivos que gere](apps-deploy.md). Intune facilita este processo e, após a implementação da aplicação, poderá [monitorizar o sucesso](apps-monitor.md) da implementação a partir do Intune dentro do portal Azure. Além disso, em algumas lojas de aplicações, como a da [Apple](vpp-apps-ios.md) e do [Windows](windows-store-for-business.md), pode comprar licenças de aplicações em volume para a sua empresa. O Intune pode sincronizar os dados com estas lojas para poder implementar e monitorizar a utilização de licenças para estes tipos de aplicações diretamente a partir da consola de administração do Intune.

## <a name="configure"></a>Configurar

Como parte do ciclo de vida das aplicações, são lançadas regularmente novas versões das aplicações. O Intune fornece ferramentas para [atualizar aplicações](apps-add.md) facilmente, que tenha implementado numa versão mais recente. Além disso, pode configurar funcionalidades adicionais para algumas aplicações, por exemplo:

- As políticas de configuração de [aplicações iOS/iPadOS](app-configuration-policies-use-ios.md) fornecem definições para aplicações compatíveis iOS/iPadOS que são utilizadas quando a aplicação é executada. Por exemplo, uma aplicação pode precisar de definições de imagem corporativa específicas ou do nome de um servidor ao qual deve estabelecer ligação.
- [As políticas geridas](app-configuration-managed-browser.md) do navegador ajudam-no a configurar as definições para o [Microsoft Edge](~/apps/apps-supported-intune-apps.md#microsoft-apps), que substitui o navegador do dispositivo predefinido e permite restringir os websites que os seus utilizadores podem visitar.

## <a name="protect"></a>Proteger

O Intune fornece várias formas para ajudar a proteger os dados nas suas aplicações. Os métodos principais são:

- [Acesso Condicional](../protect/conditional-access.md), que controla o acesso a e-mail e outros serviços com base em condições que especifica. As condições incluem tipos de dispositivos ou conformidade com uma [política de conformidade do dispositivo](../protect/device-compliance-get-started.md) que tenha implementado.
- As [Políticas de proteção de aplicações](app-protection-policy.md) funcionam com aplicações individuais para ajudar a proteger os dados da empresa que utilizam. Por exemplo, pode restringir a cópia de dados entre aplicações não geridas e aplicações geridas ou pode impedir a execução das aplicações nos dispositivos com jailbreak ou rooting.

## <a name="retire"></a>Extinguir

Eventualmente, é provável que as aplicações implementadas fiquem desatualizadas e tenham de ser removidas. O Intune facilita a [extinção de aplicações no serviço](../remote-actions/device-management.md).

## <a name="next-steps"></a>Próximos passos

- Saiba mais sobre a [gestão de aplicações no Microsoft Intune](app-management.md)
