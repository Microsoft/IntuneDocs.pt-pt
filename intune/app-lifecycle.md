---
title: "Descrição geral do ciclo de vida das aplicações do Intune"
description: "Saiba mais sobre o ciclo de vida das aplicações geridas do Intune, desde que são adicionadas até acabarem por ser extintas."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 87bd0ceed846052444e4dac4366e3a0304b1452c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="overview-of-the-app-lifecycle"></a>Descrição geral do ciclo de vida das aplicações

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

O ciclo de vida das aplicações do Intune começa quando uma aplicação é adicionada e avança por fases adicionais até ser removida.

![Ciclo de vida das aplicações](./media/app-lifecycle.png "ciclo de vida das aplicações do Intune")

## <a name="add"></a>Adicionar

O primeiro passo na implementação de aplicações consiste em adicionar as aplicações que pretende gerir e atribuir no Intune. Apesar de poder utilizar muitos tipos de aplicações diferentes, os procedimentos básicos são iguais. Com o Intune, pode adicionar aplicações para [dispositivos inscritos](apps-add.md) ([Portal clássico](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)) ou [PCs Windows que gere com o software de cliente Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune).

## <a name="deploy"></a>Implementar

Depois de adicionar a aplicação ao Intune, pode [atribuí-la aos utilizadores e dispositivos que gere](apps-deploy.md) ([Portal clássico](/intune-classic/deploy-use/deploy-apps)). O Intune facilita este processo e, após a implementação da aplicação, pode [monitorizar o êxito](apps-monitor.md) ([Portal clássico](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)) da implementação a partir da consola de administração do Intune. Além disso, em algumas lojas de aplicações, como as da [Apple](vpp-apps-ios.md) ([Portal clássico](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)) e do [Windows](windows-store-for-business.md) ([Portal clássico](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)), pode comprar licenças de aplicações em volume para a sua empresa. O Intune pode sincronizar os dados com estas lojas para poder implementar e monitorizar a utilização de licenças para estes tipos de aplicações diretamente a partir da consola de administração do Intune.

## <a name="configure"></a>Configurar

Como parte do ciclo de vida das aplicações, são lançadas regularmente novas versões das aplicações. O Intune fornece ferramentas para [atualizar aplicações](apps-add.md) ([Portal clássico](/intune-classic/deploy-use/update-apps-using-microsoft-intune)) facilmente, que tenha implementado numa versão mais recente. Além disso, pode configurar funcionalidades adicionais para algumas aplicações, por exemplo:
- As [políticas de configuração de aplicações iOS](app-configuration-policies-use-ios.md) ([Portal clássico](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)) fornecem definições para aplicações iOS compatíveis utilizadas quando a aplicação é executada. Por exemplo, uma aplicação pode necessitar de definições de imagem corporativa específicas ou do nome de um servidor ao qual ligar.
- As [políticas de browser gerido](app-configuration-managed-browser.md) ([Portal clássico](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)) ajudam a configurar as definições do Intune Managed Browser, que substitui o browser do dispositivo predefinido e permite restringir os sites que os utilizadores podem visitar.

## <a name="protect"></a>Proteger

O Intune fornece várias formas para ajudar a proteger os dados nas suas aplicações. Os métodos principais são:
- O [acesso condicional](conditional-access.md) ([Portal clássico](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)) controla o acesso ao e-mail e a outros serviços com base nas condições especificadas. As condições incluem tipos de dispositivos ou conformidade com uma [política de conformidade do dispositivo](device-compliance.md) ([Portal clássico](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)) que tenha implementado.
- As [políticas de proteção de dispositivos](app-protection-policy.md) ([Portal clássico](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) funcionam com aplicações individuais para ajudar a proteger os dados da empresa que utilizam. Por exemplo, pode restringir a cópia de dados entre aplicações não geridas e aplicações geridas ou pode impedir a execução das aplicações nos dispositivos com jailbreak ou rooting.

## <a name="retire"></a>Extinguir

Eventualmente, é provável que as aplicações implementadas fiquem desatualizadas e tenham de ser removidas. O Intune facilita a [extinção de aplicações no serviço](device-management.md) ([Portal clássico](/intune-classic/deploy-use/retire-apps-using-microsoft-intune)).
