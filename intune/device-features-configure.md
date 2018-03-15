---
title: "Configurar definições das funcionalidades dos dispositivos no Microsoft Intune"
titleSuffix: 
description: Saiba como utilizar o Microsoft Intune para configurar funcionalidades nos dispositivos que gere.
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>Configurar as definições das funcionalidades dos dispositivos no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As funcionalidades do dispositivo permitem-lhe controlar as funcionalidades nos dispositivos iOS e macOS como configurações de dispositivos partilhados, notificações e AirPrint.

Utilize as informações deste artigo para conhecer as noções básicas sobre como configurar perfis de funcionalidades de dispositivos e, em seguida, leia os artigos adicionais de cada plataforma para saber mais sobre as especificações dos dispositivos.

## <a name="create-a-device-profile-containing-device-feature-settings"></a>Criar um perfil de dispositivo com as definições das funcionalidades de dispositivos

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Na página **Intune**, selecione **Configuração do dispositivo**.
2. Na página **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
3. Na página de perfis, selecione **Criar perfil**.
4. Na página **Criar perfil**, introduza um **Nome** e uma **Descrição** para o perfil de funcionalidades de dispositivos.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições. Atualmente, pode escolher uma das seguintes plataformas para as funcionalidades de dispositivos:
    - **iOS**
    - **macOS**
6. Na lista pendente **Tipo de perfil**,selecione **Funcionalidades de dispositivos**. 
7. As definições que pode configurar diferem consoante a plataforma que escolher. Aceda a um dos seguintes artigos para obter definições detalhadas para cada plataforma:
    - [Definições do AirPrint para iOS e MacOS](air-print-settings-ios-macos.md)
    - [Definições do AirPlay para iOS](airplay-settings-ios.md)
    - [Definições de esquema do ecrã principal para iOS](home-screen-settings-ios.md)
    - [Definições de notificação das aplicações para iOS](app-notification-settings-ios.md)
    - [Definições de configuração de dispositivos partilhados para iOS](shared-device-settings-ios.md)
    - [Configurar o Intune para o Início de Sessão Único em dispositivos iOS](sso-ios.md)
    - [Definições de filtros de conteúdo Web para iOS](web-content-filter-settings-ios.md)

8. Quando tiver terminado, selecione **OK**, regresse à página **Criar perfil** e selecione **Criar**.

O perfil é criado e apresentado na página da lista de perfis.
## <a name="next-steps"></a>Passos seguintes

Se quiser atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).



