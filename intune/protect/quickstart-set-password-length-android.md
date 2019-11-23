---
title: Quickstart - Password compliance policy for Android devices
titleSuffix: Microsoft Intune
description: In this quickstart, you will use Microsoft Intune to set the length of the password required for Android devices.
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

In this quickstart, you'll use Microsoft Intune to require your workforce's Android users to enter a password of a specific length before access is granted to information on their Android devices.

Uma política de conformidade de dispositivos do Intune especifica as regras e definições que os dispositivos têm de cumprir para serem considerados conformes. You can use compliance policies with Conditional Access to allow or block access to company resources. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade.

> [!IMPORTANT]
> Além das definições da palavra-passe, deve também considerar outras definições de segurança do sistema para proteger a sua força de trabalho. Para obter mais informações, veja [Definições de segurança do sistema](compliance-policy-create-android-for-work.md).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) as a [Global administrator](../fundamentals/users-add.md#types-of-administrators) or an Intune [Service administrator](../fundamentals/users-add.md#types-of-administrators).

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

Create a device compliance policy to require your workforce's Android users to enter a password of a specific length before access is granted to information on their Android devices.

1. In Intune, select **Devices** > **Compliance Policies** > **Create Policy**.

2. Adicione **Conformidade do Android** como o **Nome**. Adicione também uma **Descrição**.

3. Em **Plataforma**, selecione **Android Enterprise**.

4. For **Profile type**, select **Work profile**.

5. Selecione **Definições** > **Segurança do Sistema** para apresentar o painel **Segurança do Sistema** Android.

6. Para **Palavra-passe obrigatória para desbloquear os dispositivos móveis**, selecione **Exigir**.

7. For **Required password type**, select **At least numeric**.

8. For **Minimum password length**, enter **6**.

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. When done, select **OK** > **OK** > **Create** to create the policy.

When you've successfully created the policy, it appears in your list of device complice policies.

## <a name="clean-up-resources"></a>Limpar recursos

Quando já não for necessária, elimine a política. Para tal, selecione a política de conformidade e clique em **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Neste início rápido, utilizou o Intune para criar uma política de conformidade para os dispositivos Android da sua força de trabalho para exigir uma palavra-passe de, pelo menos, seis carateres de comprimento. Para obter mais informações sobre a criação de políticas de conformidade, veja [Introdução às políticas de conformidade de dispositivos no Intune](device-compliance-get-started.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: enviar notificações para dispositivos não conformes](../quickstart-send-notification.md)
