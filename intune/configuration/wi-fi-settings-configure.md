---
title: Criar um perfil Wi-Fi para os dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Veja os passos para criar um perfil de configuração dos dispositivos de Wi-Fi no Microsoft Intune. Crie perfis para Android, Android Enterprise, quiosque Android, iOS, iPadOS, macOS, Windows 10 e mais recente, e Windows Holographic para Negócios. Utilize estes perfis para criar uma ligação Wi-Fi para utilizar certificados, escolher um tipo de EAP, selecionar um método de autenticação, ativar um proxy e mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3110998970eeaf654ab57397ec827090a4103f34
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512335"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Adicionar e utilizar definições de Wi-Fi nos seus dispositivos no Microsoft Intune

O Wi-Fi é uma rede sem fios que é usada por muitos dispositivos móveis para obter acesso à rede. O Microsoft Intune inclui configurações wi-fi incorporadas que podem ser implementadas para utilizadores e dispositivos na sua organização. Este grupo de configurações chama-se "perfil", podendo ser atribuído a diferentes utilizadores e grupos. Uma vez atribuídos, os seus utilizadores têm acesso à rede Wi-Fi da sua organização sem a configurarem por si mesmos.

Por exemplo, instale uma nova rede Wi-Fi com o nome Contoso Wi-Fi. Em seguida, pretende configurar todos os dispositivos iOS/iPadOS para se ligar a esta rede. Eis o processo:

1. Crie um perfil Wi-Fi que inclua as definições que se ligam à rede sem fios Contoso Wi-Fi.
2. Atribuir o perfil a um grupo que inclua todos os utilizadores de dispositivos iOS/iPadOS.
3. Os utilizadores encontrarão a nova rede Contoso Wi-Fi na lista de redes sem fios do dispositivo deles. Podem, em seguida, ligar-se à rede através do método de autenticação à sua escolha.

Este artigo lista os passos para criar um perfil Wi-Fi. Também inclui links que descrevem as diferentes configurações para cada plataforma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos suportadas

Os perfis de Wi-Fi suportam as seguintes plataformas de dispositivos:

- Android 4 e mais recente
- Android Enterprise e quiosque
- iOS 8.0 e mais recente
- iPadOS 13.0 e mais recente
- macOS X 10.11 e mais recente
- Windows 10 e mais recente, Windows 10 Mobile e Windows Holographic para Negócios

> [!NOTE]
> Nos dispositivos que executam o Windows 8.1, pode importar uma configuração de Wi-Fi que tenha sido exportada anteriormente a partir de outro dispositivo.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é **perfil Wi-Fi para toda a empresa**.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolha a plataforma dos seus dispositivos. As opções são:

      - **Android**
      - **Android Enterprise**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 8.1 e posterior**
      - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **Wi-Fi**.

      > [!TIP]
      >
      > - Para dispositivos **Android Enterprise** que funcionam como um dispositivo dedicado (quiosque), escolha o proprietário do **Dispositivo apenas** > **Wi-Fi**.
      > - Para **Windows 8.1 e posterior**, pode escolher **Importação de Wi-Fi**. Esta opção permite-lhe importar definições de Wi-Fi como um ficheiro XML que exportou anteriormente a partir de um dispositivo diferente.

4. Algumas das definições de Wi-Fi são diferentes para cada plataforma. Para ver as definições para uma plataforma específica, escolha a sua plataforma:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise](wi-fi-settings-android-enterprise.md), incluindo dispositivos dedicados
    - [iOS/iPadOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 e posterior](wi-fi-settings-windows.md)
    - [Windows 8.1 e posterior](wi-fi-settings-import-windows-8-1.md), incluindo o Windows Holographic for Business

5. Quando terminar, selecione **Criar perfil** > **Criar**.

O perfil é criado e mostrado na lista de perfis **(configuração** do dispositivo > **Perfis).**

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md) e [monitorize o seu estado.](device-profile-monitor.md). .

[Problemas perfis Wi-Fi em Intune](troubleshoot-wi-fi-profiles.md).
