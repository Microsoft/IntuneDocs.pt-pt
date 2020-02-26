---
title: Criar o perfil do dispositivo de extensões de kernel macOS com o Microsoft Intune - Azure Microsoft Docs
titleSuffix: ''
description: Adicione ou crie um perfil de dispositivo macOS e, em seguida, configure extensões de kernel para permitir a sobreposição do utilizador, adicione o identificador de equipa e um conjunto e identificador de equipa no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/25/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8a516ce9dda525d5c7a48fcbc2c799471489d0d
ms.sourcegitcommit: ff254acb94df88afc3e3e7b878084052adf40745
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600242"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Adicione extensões de kernel macOS em Intune

> [!NOTE]
> As extensões de kernel macOS estão a ser substituídas por extensões do sistema. Para mais informações, consulte [Dica de Suporte: Utilizar extensões do sistema em vez de extensões de kernel para macOS Catalina 10.15 em Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-using-system-extensions-instead-of-kernel-extensions/ba-p/1191413).

Nos dispositivos macOS, pode adicionar funcionalidades ao nível do núcleo. Estes recursos de acesso a partes do SISTEMA que os programas regulares não podem aceder. A sua organização pode ter necessidades ou requisitos específicos que não estejam disponíveis numa aplicação, uma funcionalidade de dispositivo, e assim por diante. 

Para adicionar extensões de kernel que são sempre autorizadas a carregar nos seus dispositivos, adicione "extensões de kernel" (KEXT) no Microsoft Intune e, em seguida, implemente estas extensões para os seus dispositivos.

Por exemplo, tem um programa de digitalização de vírus que digitaliza o seu dispositivo para obter conteúdo malicioso. Pode adicionar a extensão do núcleo de digitalização do vírus como uma extensão de kernel permitida em Intune. Em seguida, "atribuir" a extensão aos seus dispositivos macOS.

Com esta funcionalidade, os administradores podem permitir que os utilizadores sobreporem extensões de kernel, adicionar identificadores de equipa e adicionar extensões específicas de kernel em Intune.

Esta funcionalidade aplica-se a:

- macOS 10.13.2 e mais tarde

Para utilizar esta funcionalidade, os dispositivos devem ser:

- Matriculado em Intune utilizando o Programa de Inscrição de Dispositivos da Apple (DEP). [Os dispositivos macOS de inscrição automática](../enrollment/device-enrollment-program-enroll-macos.md) têm mais informações.

  OU

- Matriculado em Intune com "inscrição aprovada pelo utilizador" (termo da Apple). [Prepare-se para alterações às extensões de kernel no macOS High Sierra](https://support.apple.com/en-us/HT208019) (abre o site da Apple) tem mais informações.

Intune usa "perfis de configuração" para criar e personalizar estas configurações para as necessidades da sua organização. Depois de adicionar estas funcionalidades num perfil, pode então empurrar ou implementar o perfil para dispositivos macOS na sua organização.

Este artigo mostra-lhe como criar um perfil de configuração do dispositivo utilizando extensões de kernel em Intune.

> [!TIP]
> Para obter mais informações sobre extensões de kernel, consulte a visão geral da [extensão do kernel](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (abre o site da Apple).

## <a name="what-you-need-to-know"></a>O que tem de saber

- Podem ser adicionadas extensões de kernel legado não assinadas.
- Certifique-se de introduzir o identificador de equipa correto e agregar a identificação da extensão do núcleo. Intune não valida os valores que entra. Se introduzir informações erradas, a extensão não funcionará no dispositivo. Um identificador de equipa tem exatamente 10 caracteres alfanuméricos. 

> [!NOTE]
> A Apple divulgou informações sobre a assinatura e a notização de todos os softwares. No macOS 10.14.5 e mais recente, as extensões de kernel implementadas através do Intune não têm de cumprir a política de notização da Apple.
>
> Para obter informações sobre esta política de notariação, e quaisquer atualizações ou alterações, consulte os seguintes recursos:
>
> - [Notar a sua aplicação antes](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) da distribuição (abre o site da Apple) 
> - [Prepare-se para alterações às extensões de kernel no macOS High Sierra](https://support.apple.com/en-us/HT208019) (abre o site da Apple)

## <a name="create-the-profile"></a>Criar o perfil

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **macOS**
    - **Tipo de perfil**: Selecione **extensões**.
    - **Definições**: Introduza as definições que pretende configurar. Para uma lista de todas as configurações, e o que fazem, veja:

        - [macOS](kernel-extensions-settings-macos.md)

4. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e mostrado na lista. Certifique-se de [atribuir o perfil](../device-profile-assign.md) e monitorizar [o seu estado](../device-profile-monitor.md).

## <a name="next-steps"></a>Próximos passos

Depois que o perfil é criado, está pronto para ser atribuído. Em seguida, [atribua o perfil](../device-profile-assign.md) e [monitorize o estado](../device-profile-monitor.md).
