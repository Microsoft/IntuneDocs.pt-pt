---
title: Criar perfil de dispositivo de extensões de kernel de macOS com o Microsoft Intune – Azure | Documentos da Microsoft
titleSuffix: ''
description: Adicionar ou criar um macOS perfil de dispositivo e, em seguida, configure as extensões de kernel para permitir a substituição de usuário, adicionar um identificador de equipa e um identificador de pacote e o team no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67404014"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Adicionar extensões de kernel do macOS no Intune

Em dispositivos macOS, pode adicionar funcionalidades ao nível do kernel. Estas funcionalidades acessar partes do sistema operacional que não é possível aceder a programas normais. Sua organização pode ter necessidades específicas ou requisitos que não estão disponíveis numa aplicação, um recurso de dispositivo e assim por diante. 

Para adicionar extensões de kernel que sempre têm permissão para carregar nos seus dispositivos, adicione "extensões de kernel" (KEXT) no Microsoft Intune e, em seguida, implementar essas extensões nos seus dispositivos.

Por exemplo, tem um programa de verificação de vírus que analisa o seu dispositivo relativamente a conteúdo malicioso. Pode adicionar esta extensão de kernel do programa de vírus como uma extensão de kernel permitido no Intune. Em seguida, "atribua" a extensão para os seus dispositivos macOS.

Com esta funcionalidade, os administradores podem permitir aos usuários substituir extensões de kernel, adicionar identificadores de equipe e adicionar extensões de kernel específico no Intune.

Esta funcionalidade aplica-se a:

- macOS 10.13.2 e posterior

Para utilizar esta funcionalidade, tem de ser dispositivos:

- Inscritos no Intune através do programa de inscrição de dispositivos de (DEP da Apple). [Inscrever automaticamente dispositivos macOS](device-enrollment-program-enroll-macos.md) tem mais informações.

  OU

- Inscritos no Intune com "inscrição de utilizadores aprovados" (termo da Apple). [Preparar para alterações para extensões de kernel no macOS High Sierra](https://support.apple.com/en-us/HT208019) (abre o site da Apple) tem mais informações.

O Intune utiliza "perfis de configuração" para criar e personalizar estas definições para as necessidades da sua organização. Depois de adicionar esses recursos num perfil, pode, em seguida, enviar por push ou implementar o perfil para dispositivos macOS na sua organização.

Este artigo mostra-lhe como criar um perfil de configuração de dispositivo usando extensões de kernel no Intune.

> [!TIP]
> Para obter mais informações sobre as extensões de kernel, consulte [descrição geral da extensão de kernel](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (abre o site da Apple).

## <a name="what-you-need-to-know"></a>O que tem de saber

- Extensões de kernel herdado não assinados podem ser adicionadas.
- Certifique-se de que introduza o identificador de equipa correta e ID da extensão do kernel do pacote. Intune não será validado os valores que introduzir. Se introduzir informações erradas, a extensão não funcionará no dispositivo.

> [!NOTE]
> Apple lançadas informações relativas à assinatura e notarization para todos os softwares. No macOS 10.14.5 e kernel mais recente, extensões implementadas através do Intune não têm de cumprir a política de notarization da Apple.
>
> Para obter informações sobre esta política notarization e quaisquer atualizações ou alterações, consulte os seguintes recursos:
>
>  - [Notarizing a sua aplicação antes da distribuição](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (abre o site da Apple) 
>  - [Preparar para alterações para extensões de kernel no macOS High Sierra](https://support.apple.com/en-us/HT208019) (abre o site da Apple)

## <a name="create-the-profile"></a>Criar o perfil

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **macOS**
    - **Tipo de perfil**: Selecione **extensões**.
    - **Definições**: Introduza as definições que pretende configurar. Para obter uma lista de todas as definições e o que fazer, consulte:

        - [macOS](kernel-extensions-settings-macos.md)

4. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e apresentado na lista. Não se esqueça [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

## <a name="next-steps"></a>Passos Seguintes

Depois do perfil é criado, está pronto para ser atribuído. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).
