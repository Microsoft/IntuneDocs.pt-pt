---
title: Descrição geral do ciclo de vida das aplicações do Microsoft Intune
description: Saiba mais sobre o ciclo de vida das aplicações geridas no Microsoft Intune. O ciclo de vida das aplicações envolve adicionar, implementar, configurar, proteger e extinguir aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: apps
ms.openlocfilehash: 69bf4b1dc85a8a17312fe78b6a17564a8a6ff642
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Descrição geral do ciclo de vida das aplicações no Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

O ciclo de vida das aplicações do Microsoft Intune começa quando uma aplicação é adicionada e avança por fases adicionais até esta ser removida. Ao compreender estas fases, terá os detalhes de que precisa para começar a gerir aplicações no Intune.

![Ciclo de vida das aplicações](./media/app-lifecycle.png "ciclo de vida das aplicações do Intune")

## <a name="add"></a>Adicionar

O primeiro passo na implementação de aplicações consiste em adicionar as aplicações que pretende gerir e atribuir no Intune. Apesar de poder utilizar muitos tipos de aplicações diferentes, os procedimentos básicos são iguais. Com o Intune, pode adicionar diferentes tipos de aplicações, incluindo aplicações escritas internamente (linha de negócio), aplicações da loja, aplicações incorporadas e aplicações na Web. Para obter mais informações sobre cada um destes tipos de aplicações, veja [Como adicionar uma aplicação ao Microsoft Intune](apps-add.md). 

## <a name="deploy"></a>Implementar

Depois de adicionar a aplicação ao Intune, pode [atribuí-la aos utilizadores e dispositivos que gere](apps-deploy.md). O Intune facilita este processo e, após a implementação da aplicação, pode [monitorizar o êxito](apps-monitor.md) da implementação a partir do Intune no portal do Azure. Além disso, em algumas lojas de aplicações, como a da [Apple](vpp-apps-ios.md) e do [Windows](windows-store-for-business.md), pode comprar licenças de aplicações em volume para a sua empresa. O Intune pode sincronizar os dados com estas lojas para poder implementar e monitorizar a utilização de licenças para estes tipos de aplicações diretamente a partir da consola de administração do Intune.

## <a name="configure"></a>Configurar

Como parte do ciclo de vida das aplicações, são lançadas regularmente novas versões das aplicações. O Intune fornece ferramentas para [atualizar aplicações](apps-add.md) facilmente, que tenha implementado numa versão mais recente. Além disso, pode configurar funcionalidades adicionais para algumas aplicações, por exemplo:
- As [políticas de configuração de aplicações iOS](app-configuration-policies-use-ios.md) fornecem definições para aplicações iOS compatíveis utilizadas quando a aplicação é executada. Por exemplo, uma aplicação pode precisar de definições de imagem corporativa específicas ou do nome de um servidor ao qual deve estabelecer ligação.
- As [políticas de browser gerido](app-configuration-managed-browser.md) ajudam a configurar as definições para o Intune Managed Browser, que substitui o browser do dispositivo predefinido e permite restringir os sites que os utilizadores podem visitar.

## <a name="protect"></a>Proteger

O Intune fornece várias formas para ajudar a proteger os dados nas suas aplicações. Os métodos principais são:
- O [Acesso condicional](conditional-access.md), que controla o acesso ao e-mail e a outros serviços com base nas condições especificadas. As condições incluem tipos de dispositivos ou conformidade com uma [política de conformidade do dispositivo](device-compliance.md) que tenha implementado.
- As [Políticas de proteção de aplicações](app-protection-policy.md) funcionam com aplicações individuais para ajudar a proteger os dados da empresa que utilizam. Por exemplo, pode restringir a cópia de dados entre aplicações não geridas e aplicações geridas ou pode impedir a execução das aplicações nos dispositivos com jailbreak ou rooting.

## <a name="retire"></a>Extinguir

Eventualmente, é provável que as aplicações implementadas fiquem desatualizadas e tenham de ser removidas. O Intune facilita a [extinção de aplicações no serviço](device-management.md).

## <a name="next-steps"></a>Próximos passos:

- Saiba mais sobre a [gestão de aplicações no Microsoft Intune](app-management.md)