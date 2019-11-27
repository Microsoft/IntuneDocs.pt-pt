---
title: Guia de início rápido-política de conformidade de senha para dispositivos Android
titleSuffix: Microsoft Intune
description: Neste guia de início rápido, você usará Microsoft Intune para definir o comprimento da senha necessária para dispositivos Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409764"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Guia de Início Rápido: criar uma política de conformidade de palavra-passe para dispositivos Android

Neste guia de início rápido, você usará Microsoft Intune para exigir que os usuários do Android da força de equipe insiram uma senha de um comprimento específico antes que o acesso seja concedido às informações em seus dispositivos Android.

Uma política de conformidade de dispositivos do Intune especifica as regras e definições que os dispositivos têm de cumprir para serem considerados conformes. Você pode usar políticas de conformidade com acesso condicional para permitir ou bloquear o acesso aos recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade.

> [!IMPORTANT]
> Além das definições da palavra-passe, deve também considerar outras definições de segurança do sistema para proteger a sua força de trabalho. Para obter mais informações, veja [Definições de segurança do sistema](compliance-policy-create-android-for-work.md).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) como um [administrador global](../fundamentals/users-add.md#types-of-administrators) ou um [administrador de serviços](../fundamentals/users-add.md#types-of-administrators)do Intune.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

Crie uma política de conformidade do dispositivo para exigir que os usuários do Android da força de usuário insiram uma senha de um comprimento específico antes que o acesso seja concedido às informações em seus dispositivos Android.

1. No Intune, selecione **dispositivos** > **políticas de conformidade** > **criar política**.

2. Adicione **Conformidade do Android** como o **Nome**. Adicione também uma **Descrição**.

3. Em **Plataforma**, selecione **Android Enterprise**.

4. Para **tipo de perfil**, selecione **perfil de trabalho**.

5. Selecione **Definições** > **Segurança do Sistema** para apresentar o painel **Segurança do Sistema** Android.

6. Para **Palavra-passe obrigatória para desbloquear os dispositivos móveis**, selecione **Exigir**.

7. Para **tipo de senha necessária**, selecione **pelo menos numérico**.

8. Para **comprimento mínimo da senha**, digite **6**.

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. Quando terminar, selecione **ok** > **OK** > **criar** para criar a política.

Quando você criou a política com êxito, ela aparece na lista de políticas de dispositivo complice.

## <a name="clean-up-resources"></a>Limpar recursos

Quando já não for necessária, elimine a política. Para tal, selecione a política de conformidade e clique em **Eliminar**.

## <a name="next-steps"></a>Passos Seguintes

Neste início rápido, utilizou o Intune para criar uma política de conformidade para os dispositivos Android da sua força de trabalho para exigir uma palavra-passe de, pelo menos, seis carateres de comprimento. Para obter mais informações sobre a criação de políticas de conformidade, veja [Introdução às políticas de conformidade de dispositivos no Intune](device-compliance-get-started.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: enviar notificações para dispositivos não conformes](../quickstart-send-notification.md)
