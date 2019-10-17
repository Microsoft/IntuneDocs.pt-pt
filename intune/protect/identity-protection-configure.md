---
title: Usar um PIN para entrar em dispositivos Windows 10 usando o Microsoft Intune-Azure | Microsoft Docs
description: Use o Windows Hello para empresas para permitir que os usuários entrem em dispositivos usando um PIN, uma impressão digital e muito mais. Crie um perfil de configuração de proteção de identidade no Intune para dispositivos Windows 10 com essas configurações e atribua o perfil a grupos de usuários e grupos de dispositivos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 333b94bf3226c99ed50c4b433f4b477814b8e4bb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509541"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Use o Windows Hello para empresas em dispositivos Windows 10 com Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Windows Hello para empresas é um método para entrar em dispositivos Windows, substituindo senhas, cartões inteligentes e cartões inteligentes virtuais. O Intune inclui configurações internas para que os administradores possam configurar e usar o Windows Hello para empresas. Por exemplo, você pode usar essas configurações para:

- Habilitar o Windows Hello para empresas para dispositivos e usuários
- Definir requisitos de PIN do dispositivo, incluindo um comprimento mínimo ou máximo do PIN
- Permitir gestos, como uma impressão digital, que os usuários podem (ou não podem usar) para entrar em dispositivos

Esta funcionalidade aplica-se a dispositivos que executem:

- Windows 10 e posterior
- Windows 10 Mobile
- Windows Holographic for Business

O Intune usa "perfis de configuração" para criar e personalizar essas configurações para as necessidades da sua organização. Depois de adicionar esses recursos em um perfil, envie por Push ou implante essas configurações para grupos de usuários e dispositivos em sua organização.

Este artigo mostra como criar um perfil de configuração de dispositivo. Para obter uma lista de todas as configurações e o que elas fazem, consulte [configurações do dispositivo Windows 10 para habilitar o Windows Hello para empresas](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Criar o perfil do dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Windows 10 e posterior**. O Windows Hello para Empresas só é suportado em dispositivos com o Windows 10 e versões posteriores.
    - **Tipo de perfil**: selecione **proteção de identidade**.
    - **Configurar o Windows Hello para empresas**: escolha como você deseja configurar o Windows Hello para empresas. As opções são:

        - **Não configurado**: [provisiona o Windows Hello para empresas](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) no dispositivo. Quando atribuir perfis de proteção de identidade apenas a utilizadores, o contexto do dispositivo assume a predefinição **Não configurado**.
        - **Desabilitado**: se você não quiser usar o Windows Hello para empresas, selecione esta opção. Essa opção desabilita o Windows Hello para empresas para todos os usuários.
        - **Habilitado**: escolha esta opção para [provisionar](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)e definir as configurações do Windows Hello para empresas no Intune. Insira as configurações que você deseja configurar. Para obter uma lista de todas as configurações e o que elas fazem, consulte:

            - [Configurações do dispositivo Windows 10 para habilitar o Windows Hello para empresas](identity-protection-windows-settings.md)

4. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e aparece na lista de perfis. Em seguida, [atribua](../configuration/device-profile-assign.md) esse perfil aos grupos de usuários e dispositivos para atender às suas necessidades.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>Próximos passos

- Veja uma lista de todas as [configurações e o que elas fazem](identity-protection-windows-settings.md).
- [Atribua o perfil](../configuration/device-profile-assign.md) e [monitorize o respetivo estado](../configuration/device-profile-monitor.md).
