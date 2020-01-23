---
title: Início Rápido – Configurar a inscrição automática no Intune
description: 'Início Rápido: configurar a inscrição automática para dispositivos Windows 10 no Intune.'
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5cc7cf3661caa2b2640d9370d26402b7702d36b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541073"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Início Rápido: configurar a inscrição automática para dispositivos com o Windows 10

Neste início rápido, vai configurar o Microsoft Intune para inscrever dispositivos automaticamente mediante o início de sessão de utilizadores específicos em dispositivos com o Windows 10.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Subscrição do Microsoft Intune – [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).
- Para concluir este início rápido, tem primeiro de [criar um utilizador](../fundamentals/quickstart-create-user.md) e [criar um grupo](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Entrar no Intune no Microsoft Endpoint Manager

Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) como um administrador global ou um administrador de serviços do Intune. Se criou uma Subscrição de Avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar a inscrição automática de dispositivos Windows 10

Neste exemplo, irá utilizar a inscrição na MDM para que seja possível inscrever automaticamente dispositivos empresariais e BYOD. Irá inscrever-se numa subscrição gratuita do Azure Active Directory Premium.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **todos os serviços** > **M365 Azure Active Directory** > **Azure Active Directory** > **Mobility (MDM e MAM)** .
2. Selecione **Obtenha uma versão de avaliação Premium gratuita para utilizar esta funcionalidade**. Selecionar esta opção irá permitir a inscrição automática através da versão de avaliação Premium gratuita do Azure Active Directory. 

    ![Selecione a versão de avaliação Premium gratuita do Azure Active Directory](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

3. Selecione a opção de versão de avaliação gratuita do **Enterprise Mobility + Security E5**. 
4. Clique em **avaliação gratuita** > **Ativar** a avaliação gratuita.

    ![Selecione a versão de avaliação gratuita do Enterprise Mobility + Security E5](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

    > [!NOTE]
    > Pode levar um minuto para ser ativado. 

3. Selecione **Microsoft Intune** para configurar o Intune. 

    ![Selecione o Microsoft Intune na lista](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Selecione **Alguns** no **âmbito de utilizadores de MDM** para utilizar a inscrição automática MDM para gerir dados empresariais nos dispositivos Windows dos seus colaboradores. A inscrição automática de MDM será configurada para os dispositivos associados a AAD e cenários de BYOD.

    ![Selecione "Alguns" na lista Configurar](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Clique em **Selecionar grupos** > os **testadores da Contoso** > **selecionar** como o grupo atribuído.

    ![Selecione o grupo a inscrever](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Selecione **Alguns** no **Âmbito de Utilizadores de MAM** para gerir dados nos dispositivos da sua força de trabalho.

    ![Selecione o grupo a inscrever](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-06.png)

7. Selecione **Selecionar grupos** > **Técnicos de Teste da Contoso** > **Selecionar** como grupo atribuído. 
8. Utilize os valores predefinidos para os restantes valores de configuração.
9. Escolha **Guardar**.

## <a name="clean-up-resources"></a>Limpar recursos

Para reconfigurar a inscrição automática do Intune, veja [Configurar a inscrição para dispositivos Windows](windows-enroll.md).

## <a name="next-steps"></a>Próximos passos

Neste início rápido, aprendeu a configurar a inscrição automática para dispositivos com o Windows 10. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](device-enrollment.md)

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: inscrever o seu dispositivo com o Windows 10](../quickstart-enroll-windows-device.md)
