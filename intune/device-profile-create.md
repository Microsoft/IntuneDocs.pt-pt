---
title: Criar perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou configure um perfil de dispositivo no Microsoft Intune, incluindo a seleção do tipo de plataforma e a configuração das definições no portal do Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6bc6f5d2f32ff060eb2eec568b0048628ad0e09c
ms.sourcegitcommit: 349ab913932547b4a7491181f0aff092f109b87b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303860"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Criar um perfil de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Criar o perfil
1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** e procure **Microsoft Intune**.

2. No **Microsoft Intune**, selecione **Configuração do dispositivo** e selecione **Perfis**. Em seguida, selecione **Criar Perfil**.

3. Introduza as seguintes propriedades:

   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil. (Isto é opcional, mas recomendado.)
   - **Plataforma**: selecione o tipo de plataforma:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e posterior**
       - **Windows 10 e posterior**

   - **Tipo de perfil**: selecione o tipo que pretende criar. A lista depende da plataforma que escolher.
   - **Definições**: os seguintes tópicos descrevem as definições para cada tipo de perfil:

       -  [Funcionalidades do dispositivo](device-features-configure.md)
       -  [Restrições de dispositivos](device-restrictions-configure.md)
       -  [Proteção de ponto final](endpoint-protection-configure.md)
       -  [Proteção de identidade](identity-protection-configure.md)  
       -  [Modo de Quiosque](kiosk-settings.md)
       -  [e-mail](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  Education for [Windows 10](education-settings-configure.md) e [iOS](wi-fi-settings-ios.md)
       -  [Atualização de edição do Windows 10](edition-upgrade-configure-windows-10.md)
       -  [Políticas de atualização do iOS](software-updates-ios.md)
       -  [Certificados](certificates-configure.md)
       -  [Windows Information Protection](windows-information-protection-configure.md)
       -  [Personalizar](custom-settings-configure.md)

     ![Captura de ecrã de Criar perfil](./media/create-device-profile.png)

4. Selecione **Criar** quando tiver terminado.

O perfil é criado e apresentado na lista.

## <a name="next-steps"></a>Passos Seguintes
[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
