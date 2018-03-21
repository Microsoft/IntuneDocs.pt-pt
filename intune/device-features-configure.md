---
title: "Criar um perfil de dispositivo iOS ou macOS com o Microsoft Intune – Azure | Microsoft Docs"
description: "Adicione ou crie um perfil de dispositivo iOS ou macOS e, em seguida, configure as definições do AirPrint, AirPlay, esquema do ecrã principal, notificação das aplicações, dispositivos partilhados, início de sessão único e definições de filtros de conteúdo Web no Microsoft Intune"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3de7d1bccd57da1290987a714416373cbdd2b0d
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Adicionar definições de funcionalidades de dispositivos iOS ou macOS no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As funcionalidades de dispositivos permitem-lhe controlar uma variedade de definições e funcionalidades em dispositivos iOS e macOS, tais como:

- Definições do AirPrint e do AirPlay
- Esquema do ecrã principal
- Notificação das aplicações
- Configuração de dispositivos partilhados
- Configuração do início de sessão único
- Filtragem de conteúdos Web

Este artigo mostra-lhe os princípios básicos sobre como configurar perfis de funcionalidades de dispositivos iOS. Em seguida, pode consultar artigos adicionais para configurar definições específicas da plataforma para os seus dispositivos.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo**, selecione **Perfis** e, em seguida, selecione **Criar perfil**.
4. Introduza as seguintes propriedades:

  - **Nome**: introduza um nome descritivo para o novo perfil.
  - **Descrição**: introduza uma descrição para o perfil (opcional, mas recomendado)
  - **Plataforma**: selecione o seu tipo de plataforma:
    - **iOS**
    - **macOS**
  - **Tipo de perfil**: selecione **Funcionalidades do dispositivo**
  - **Definições**: as definições variam consoante a plataforma selecionada. Os seguintes artigos descrevem as definições para cada tipo de perfil:

    - [Definições do AirPrint para iOS e MacOS](air-print-settings-ios-macos.md)
    - [Definições do AirPlay para iOS](airplay-settings-ios.md)
    - [Definições de esquema do ecrã principal para iOS](home-screen-settings-ios.md)
    - [Definições de notificação das aplicações para iOS](app-notification-settings-ios.md)
    - [Definições de configuração de dispositivos partilhados para iOS](shared-device-settings-ios.md)
    - [Configurar o Intune para o Início de Sessão Único em dispositivos iOS](sso-ios.md)
    - [Definições de filtros de conteúdo Web para iOS](web-content-filter-settings-ios.md)

5. Assim que terminar, selecione **OK** e **Criar** para guardar as suas alterações.

O perfil é criado e apresentado na lista.

## <a name="next-step"></a>Passo seguinte

Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).