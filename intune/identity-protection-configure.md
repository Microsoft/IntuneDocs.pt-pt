---
title: Utilizar um PIN para iniciar sessão em dispositivos Windows 10 com o Microsoft Intune – Azure | Documentos da Microsoft
description: Utilize o Windows Hello para empresas para permitir que os utilizadores iniciem sessão em dispositivos através de um PIN, uma impressão digital e muito mais. Criar um perfil de configuração de proteção de identidade no Intune para dispositivos Windows 10 com estas definições e atribuir o perfil a grupos de utilizadores e grupos de dispositivos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d52c140a8cf408955d8a8d4cbce6038349b5b66b
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57395812"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Utilizar o Windows Hello para empresas em dispositivos Windows 10 com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows Hello para empresas é um método para iniciar sessão dispositivos Windows, substituindo as palavras-passe, smart cards e smart cards virtuais. O Intune inclui definições incorporadas para que os administradores podem configurar e utilizar o Windows Hello para empresas. Por exemplo, pode utilizar estas definições para:

- Ativar Windows Hello para empresas para dispositivos e utilizadores
- Definir requisitos de PIN do dispositivo, incluindo um comprimento mínimo ou máximo do PIN
- Permitir que os gestos, como uma impressão digital, o que os utilizadores podem (ou não é possível utilizar) para iniciar sessão nos dispositivos

Esta funcionalidade aplica-se a dispositivos que executem:

- Windows 10 e posterior
- Windows 10 Mobile
- Windows Holographic for Business

O Intune utiliza "perfis de configuração" para criar e personalizar estas definições para as necessidades da sua organização. Depois de adicionar esses recursos num perfil, push ou implementar estas definições em utilizadores e grupos de dispositivos na sua organização.

Este artigo mostra-lhe como criar um perfil de configuração do dispositivo. Para obter uma lista de todas as definições, e o que fazer, consulte [definições do dispositivo Windows 10 para ativar o Windows Hello para empresas](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Criar o perfil de dispositivo

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **Windows 10 e posterior**. O Windows Hello para Empresas só é suportado em dispositivos com o Windows 10 e versões posteriores.
    - **Tipo de perfil**: Selecione **Identity protection**.
    - **Configurar o Windows Hello para empresas**: Escolha como pretende configurar o Windows Hello para empresas. As opções são:

        - **Não configurado**: [Aprovisiona Windows Hello para empresas](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) no dispositivo. Quando atribuir perfis de proteção de identidade apenas a utilizadores, o contexto do dispositivo assume a predefinição **Não configurado**.
        - **Desativado**: Se não quiser utilizar o Windows Hello para empresas, selecione esta opção. Esta opção desativa o Windows Hello para empresas para todos os utilizadores.
        - **Ativado**: Escolha esta opção para [aprovisionar]((https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning))e configurar o Windows Hello para empresas no Intune. Introduza as definições que pretende configurar. Para obter uma lista de todas as definições e o que fazer, consulte:

            - [Definições do dispositivo Windows 10 para ativar o Windows Hello para empresas](identity-protection-windows-settings.md)

4. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e apresentado na lista de perfis. Em seguida, [atribuir](device-profile-assign.md) este perfil a grupos de utilizadores e dispositivos para atender às suas necessidades.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->

## <a name="next-steps"></a>Passos Seguintes

- Ver uma lista de todos os [as definições e o que fazem](identity-protection-windows-settings.md).
- [Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
