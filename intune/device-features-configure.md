---
title: Criar um perfil de dispositivo iOS ou macOS com o Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou criar um iOS ou macOS, perfil de dispositivo e, em seguida, configure as definições do AirPrint, layout do ecrã principal, notificações de aplicações, dispositivos partilhados, o início de sessão único e definições de filtro de conteúdo web no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4542a65afa87668702620a1b50443c9844692a87
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831280"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Adicionar definições de funcionalidades de dispositivos iOS ou macOS no Intune

O Intune inclui muitas funcionalidades e definições que ajudam os administradores a controlam os dispositivos iOS e macOS. Por exemplo, os administradores podem:

- Permitir aos utilizadores acesso a impressoras com o AirPrint na sua rede
- Adicionar aplicações e pastas para o ecrã principal, incluindo a adição de novas páginas
- Escolha se e como são apresentadas notificações da aplicação
- Configurar o ecrã de bloqueio para mostrar uma mensagem ou a etiqueta de recursos, especialmente para dispositivos partilhados
- Dar aos usuários uma única início de sessão experiência seguro para partilhar as credenciais entre aplicações
- Sites de filtro que utilizar uma linguagem para adultos e permitir ou bloquear sites da web específicos

Estas funcionalidades estão disponíveis no Intune e são configuráveis pelo administrador. O Intune utiliza "perfis de configuração" para criar e personalizar estas definições para as necessidades da sua organização. Depois de adicionar esses recursos num perfil, pode, em seguida, enviar por push ou implementar o perfil para dispositivos iOS e macOS na sua organização.

Este artigo mostra-lhe como criar um perfil de configuração do dispositivo. Também pode ver todas as definições disponíveis para [iOS](ios-device-features-settings.md) e [macOS](macos-device-features-settings.md) dispositivos.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione a plataforma:
        - **iOS**
        - **macOS**
    - **Tipo de perfil**: Selecione **funcionalidades do dispositivo**.
    - **Definições**: Introduza as definições que pretende configurar. Para obter uma lista de todas as definições e o que fazer, consulte:

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. Assim que terminar, selecione **OK** e **Criar** para guardar as suas alterações.

O perfil é criado e apresentado na lista. Não se esqueça [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

## <a name="next-steps"></a>Passos Seguintes

Depois do perfil é criado, está pronto para ser atribuído. Em seguida, [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

Ver todas as definições de funcionalidade do dispositivo para [iOS](ios-device-features-settings.md) e [macOS](macos-device-features-settings.md) dispositivos.