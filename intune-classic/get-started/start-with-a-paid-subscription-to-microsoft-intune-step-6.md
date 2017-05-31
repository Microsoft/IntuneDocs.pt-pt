---
title: "Implementar políticas e aplicações | Documentos da Microsoft"
description: "Pode ativar as definições de política e implementar aplicações que serão aplicadas assim que os dispositivos são inscritos na gestão."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 90ca67757367f89a7c1a0eebea70f107eb279378
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="create-policies-and-publish-apps"></a>Criar políticas e publicar aplicações

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico informa os administradores do Intune sobre como podem criar políticas e publicar aplicações que possam implementar em dispositivos geridos.

Antes de começar a inscrição de aplicações no Intune, pode ativar as definições de política e as aplicações que serão implementadas assim que esses dispositivos fiquem disponíveis para gestão. As políticas do Intune disponibilizam definições que o ajudam a controlar as definições de segurança nos dispositivos móveis, a gerir as definições de Endpoint Protection e Firewall do Windows de computadores e a implementar aplicações. Pode configurar a política, adicionar aplicações e implementar essas aplicações para que os dispositivos recebem as definições e aplicações assim que se inscrevam no Intune.

As políticas e aplicações são específicas da plataforma.

## <a name="manage-device-settings"></a>Gerir definições do dispositivo

 As definições de política do dispositivo são configuradas e geridas por plataforma. As ligações seguintes fornecem listas de definições disponíveis para as respetivas plataformas:

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android e Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 /intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows Team](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [PCs Windows com o cliente de software do Intune](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Pode saber mais sobre como [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Adicionar e implementar aplicações

Pode adicionar aplicações ao Intune e, em seguida, implementá-las em dispositivos geridos de duas formas:
- **Instalação obrigatória** – As aplicações instalam automaticamente a aplicação para os dispositivos geridos
- **Instalação disponível** – As aplicações são apresentadas no Portal da Empresa do Intune para que os utilizadores possam escolher se pretendem instalá-las nos seus dispositivos

### <a name="add-apps"></a>Adicionar aplicações

Primeiro, torne as aplicações disponíveis no Intune através de um dos seguintes métodos:
- [Adicionar aplicações a dispositivos inscritos](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Adicionar aplicações a PCs do cliente de software do Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Implementar aplicações

Agora que a aplicação está disponível no Intune, pode implementá-la em dispositivos geridos:
- [Implementar aplicações em dispositivos](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Implementar aplicações compradas em volume:
    - [iOS – Programa comprado em volume](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Loja Windows para Empresas](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    Depois de ter configurado as aplicações para implementação, pode [configurar aplicações](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Organizar utilizadores e dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**Personalizar o Portal da Empresa**  &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  

