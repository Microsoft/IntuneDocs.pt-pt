---
title: Criar um perfil de dispositivo iOS ou macOS com o Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil de dispositivo iOS ou macOS e, em seguida, configure as definições do AirPrint, AirPlay, esquema do ecrã principal, notificação das aplicações, dispositivos partilhados, início de sessão único e definições de filtros de conteúdo Web no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2282ba4dd3caf8c71c8624884bc124393ea52d2f
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203098"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Adicionar definições de funcionalidades de dispositivos iOS ou macOS no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As funcionalidades de dispositivos permitem-lhe controlar uma variedade de definições e funcionalidades em dispositivos iOS e macOS, tais como:

- Definições do AirPrint e do AirPlay
- Esquema do ecrã principal
- Notificação das aplicações
- Mensagem de ecrã de bloqueio
- Configuração do início de sessão único
- Filtragem de conteúdos Web

Este artigo mostra-lhe os princípios básicos sobre como configurar perfis de funcionalidades de dispositivos iOS. Em seguida, pode consultar artigos adicionais para configurar definições específicas da plataforma para os seus dispositivos.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
4. Introduza as seguintes propriedades:

   - **Nome**: Introduza um nome descritivo para o novo perfil.
   - **Descrição**: Introduza uma descrição para o perfil. (Esta definição é opcional mas recomendado.)
   - **Plataforma**: Selecione o tipo de plataforma:
     - **iOS**
     - **macOS**
   - **Tipo de perfil**: Selecione **funcionalidades do dispositivo**.
   - **Definições**: As definições dependem da plataforma que escolher. Os seguintes artigos descrevem as definições para cada tipo de perfil:

     - [Definições do AirPrint para iOS e MacOS](air-print-settings-ios-macos.md)
     - [Definições do AirPlay para iOS](airplay-settings-ios.md)
     - [Definições de esquema do ecrã principal para iOS](home-screen-settings-ios.md)
     - [Definições de notificação das aplicações para iOS](app-notification-settings-ios.md)
     - [Definições de mensagem de ecrã de bloqueio para iOS](shared-device-settings-ios.md)
     - [Configurar o Intune para o início de sessão único em dispositivos iOS](sso-ios.md)
     - [Definições de filtros de conteúdo Web para iOS](web-content-filter-settings-ios.md)

5. Assim que terminar, selecione **OK** e **Criar** para guardar as suas alterações.

O perfil é criado e apresentado na lista.

## <a name="next-step"></a>Passo seguinte

Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).