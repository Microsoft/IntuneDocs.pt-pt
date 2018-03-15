---
title: "Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs"
description: "Adicione ou configure um perfil de dispositivo no Microsoft Intune, incluindo a seleção do tipo de plataforma e a configuração das definições no portal do Azure"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c40fd13a46a61ec0ee05efba7ece7653f5de90ca
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Criar o perfil
1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** e procure **Microsoft Intune**.

2. No **Microsoft Intune**, selecione **Configuração do dispositivo**, selecione **Perfis** e, em seguida, selecione **Criar Perfil**.

3. Introduza as seguintes propriedades: 

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição**: opcional, mas recomendada. Introduza uma descrição do perfil.
    - **Plataforma**: selecione o tipo de plataforma:  

        - **Android**
        - **Android for Work**
        - **iOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 e posterior**
        - **Windows 10 e posterior**

    - **Tipo de perfil**: selecione o tipo que pretende criar. A lista depende da plataforma que escolher.
    - **Definições**: os seguintes tópicos descrevem as definições para cada tipo de perfil:

        -  [Definições das funcionalidades de dispositivos](device-features-configure.md)
        -  [Definições de restrição de dispositivos](device-restrictions-configure.md)
        -  [Definições de e-mail](email-settings-configure.md)
        -  [Definições de VPN](vpn-settings-configure.md)
        -  [Definições de Wi-Fi](wi-fi-settings-configure.md)
        -  [Definições de atualização da edição do Windows 10](edition-upgrade-configure-windows-10.md)
        -  [Definições de certificado](certificates-configure.md)
        -  [Definições do Windows Information Protection](windows-information-protection-configure.md)
        -  [Definições de educação](education-settings-configure.md)
        -  [Definições personalizadas](custom-settings-configure.md)

    ![Introduza as definições para criar um perfil de dispositivo](./media/create-device-profile.png)

4. Selecione **Criar** quando tiver terminado. 

O perfil é criado e apresentado na lista. Para atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).


## <a name="next-steps"></a>Passos seguintes
Para atribuir perfis de dispositivo, veja [Como atribuir perfis de dispositivo com o Microsoft Intune](device-profile-assign.md).