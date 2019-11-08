---
title: Criar perfil de dispositivo de extensões de kernel macOS com o Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Adicione ou crie um perfil de dispositivo macOS e, em seguida, configure extensões de kernel para permitir substituição do usuário, adicionar identificador de equipe e um grupo e um identificador de equipe em Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e69f1b11833da0906aaf831f8bb82b04241e442f
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755180"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Adicionar extensões de kernel macOS no Intune

Em dispositivos macOS, você pode adicionar recursos no nível do kernel. Esses recursos acessam partes do sistema operacional que programas regulares não podem acessar. Sua organização pode ter necessidades ou requisitos específicos que não estão disponíveis em um aplicativo, um recurso de dispositivo e assim por diante. 

Para adicionar extensões de kernel que sempre têm permissão para carregar em seus dispositivos, adicione "extensões de kernel" (KEXT) em Microsoft Intune e, em seguida, implante essas extensões em seus dispositivos.

Por exemplo, você tem um programa de verificação de vírus que verifica o seu dispositivo em busca de conteúdo mal-intencionado. Você pode adicionar a extensão do kernel do programa de verificação de vírus como uma extensão de kernel permitida no Intune. Em seguida, "atribua" a extensão aos dispositivos macOS.

Com esse recurso, os administradores podem permitir que os usuários substituam as extensões do kernel, adicionem identificadores de equipe e adicionem extensões de kernel específicas no Intune.

Esta funcionalidade aplica-se a:

- macOS 10.13.2 e posterior

Para usar esse recurso, os dispositivos devem ser:

- Registrado no Intune usando a DEP (Programa de registro de dispositivos da Apple). [Registrar dispositivos MacOS automaticamente](../enrollment/device-enrollment-program-enroll-macos.md) tem mais informações.

  OU

- Registrado no Intune com "registro aprovado pelo usuário" (termo da Apple). [Preparar para alterações em extensões de kernel no MacOS High Sierra](https://support.apple.com/en-us/HT208019) (abre o site da Apple) tem mais informações.

O Intune usa "perfis de configuração" para criar e personalizar essas configurações para as necessidades da sua organização. Depois de adicionar esses recursos em um perfil, você pode enviar por Push ou implantar o perfil para dispositivos macOS em sua organização.

Este artigo mostra como criar um perfil de configuração de dispositivo usando extensões de kernel no Intune.

> [!TIP]
> Para obter mais informações sobre extensões de kernel, consulte [visão geral da extensão do kernel](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (abre o site da Apple).

## <a name="what-you-need-to-know"></a>O que tem de saber

- Extensões de kernel herdadas não assinadas podem ser adicionadas.
- Certifique-se de inserir o identificador de equipe correto e a ID do pacote da extensão do kernel. O Intune não valida os valores inseridos. Se você inserir informações erradas, a extensão não funcionará no dispositivo.

> [!NOTE]
> A Apple lançou informações sobre assinatura e notarization para todos os softwares. No macOS 10.14.5 e mais recentes, as extensões de kernel implantadas por meio do Intune não precisam atender à política de notarization da Apple.
>
> Para obter informações sobre essa política de notarization e quaisquer atualizações ou alterações, consulte os seguintes recursos:
>
> - [Notarizing seu aplicativo antes da distribuição](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (abre o site da Apple) 
> - [Preparar-se para alterações nas extensões de kernel no MacOS High Sierra](https://support.apple.com/en-us/HT208019) (abre o site da Apple)

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **MacOS**
    - **Tipo de perfil**: selecione **extensões**.
    - **Configurações**: Insira as configurações que você deseja configurar. Para obter uma lista de todas as configurações e o que elas fazem, consulte:

        - [macOS](kernel-extensions-settings-macos.md)

4. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e mostrado na lista. Certifique-se de [atribuir o perfil](../device-profile-assign.md) e [monitorar seu status](../device-profile-monitor.md).

## <a name="next-steps"></a>Próximos passos

Depois que o perfil é criado, ele está pronto para ser atribuído. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).
