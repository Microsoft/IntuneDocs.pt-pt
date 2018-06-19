---
title: Utilizar definições personalizadas do dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou criar um perfil para utilizar definições personalizadas para dispositivos Windows, Android e iOS com o Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce7c263435f92a041b93dc5d34ffa912c6fa87fb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021885"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Criar um perfil com definições personalizadas no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Intune poderá não ter todas as definições incorporadas que pretende ou de que precisa. Em alternativa, é recomendável utilizar uma definição disponível noutros perfis de dispositivo. Para adicionar estas definições, crie um perfil de dispositivo e configure o perfil com definições personalizadas do dispositivo.

Este artigo apresenta os passos básicos para criar um perfil com definições personalizadas. Também inclui ligações para saber mais sobre como criar definições personalizadas com plataformas diferentes.

## <a name="custom-settings-on-different-platforms"></a>Definições personalizadas em plataformas diferentes
As definições personalizadas são configuradas de forma diferente para cada plataforma. Por exemplo, para controlar as funcionalidades em dispositivos Android e Windows, pode introduzir valores Open Mobile Alliance Uniform Resource Identifier (OMA-URI). Para dispositivos Apple, pode importar um ficheiro que criou no [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

## <a name="create-the-profile"></a>Criar o perfil

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo**, selecione **Perfis** e, em seguida, selecione **Criar perfil**.
4. Introduza um **Nome** e uma **Descrição** para o perfil personalizado.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo à qual pretende aplicar as definições personalizadas. Pode escolher qualquer uma das seguintes plataformas:

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**

6. Na lista pendente **Tipo de perfil**, escolha **Personalizado**.
7. Consoante a plataforma que escolheu, as definições que pode configurar variam. As seguintes ligações fornecem mais detalhes sobre as definições personalizadas para cada plataforma:

    - [Definições do Android](custom-settings-android.md)
    - [Definições do iOS](custom-settings-ios.md)
    - [Definições do macOS](custom-settings-macos.md)
    - [Definições do Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Definições do Windows 10](custom-settings-windows-10.md)
    - [Definições do Windows Holographic for Business](custom-settings-windows-holographic.md)
    - [Definições do Android for Work](custom-settings-android-for-work.md)

8. Quando tiver terminado, selecione **Criar**.

O perfil será criado e apresentado na lista de perfis. Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
