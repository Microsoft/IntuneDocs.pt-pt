---
title: 'Guia de Início Rápido: inscrever o seu dispositivo Windows 10 Desktop no Microsoft Intune'
description: 'Guia de Início Rápido: utilizar o Portal da Empresa para inscrever o seu dispositivo Windows 10 Desktop no Microsoft Intune'
services: microsoft-intune
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 872cbd203a57976bd1bceb83e5fbf95a15721ff4
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292311"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>Início rápido: Inscrever o seu dispositivo Windows 10

Neste guia de início rápido, irá assumir a função de utilizador do Intune e inscrever o seu dispositivo com o Windows 10 no Microsoft Intune. Em seguida, irá regressar ao Intune e confirme que o dispositivo inscrito.

Inscrever os seus dispositivos no Microsoft Intune permite que os dispositivos com o Windows 10 acedam aos dados seguros da sua organização, incluindo o e-mail, ficheiros e outros recursos. Isto aplica-se a computadores com o Windows 10 e a dispositivos móveis com o Windows 10 Mobile. A inscrição dos dispositivos ajuda a proteger o seu acesso e o da sua organização e ajuda a manter os dados de trabalho separados dos seus dados pessoais.

> [!TIP]
> Descubra o que acontece quando [inscreve o seu dispositivo no Intune](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows) e o que isso significa para as [informações no dispositivo](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

- Subscrição do Microsoft Intune – [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).
- Para concluir este guia de início rápido, tem de concluir os passos para [configurar a inscrição automática no Intune](quickstart-setup-auto-enrollment.md).

## <a name="confirm-your-windows-10-desktop-version"></a>Confirmar a versão do Windows 10 Desktop

Antes de inscrever o seu dispositivo Windows 10 Desktop, tem de confirmar a versão do Windows que instalou.

1. Clique com o botão direito do rato no ícone **Iniciar** do Windows e selecione **Definições** para apresentar as opções de Definições do Windows.

   ![Captura de ecrã a mostrar as Definições do Windows – Sistema](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. Selecione **Sistema** > **Acerca de**. 

   ![Captura de ecrã a mostrar as suas definições de sistema](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > Também pode escrever a expressão "Sobre o seu PC" na **barra de pesquisa** e, em seguida, selecionar **Sobre o seu PC**.

3. Na janela **Definições**, verá uma lista com as **especificações do Windows** do seu PC. Nessa lista, localize a **Versão**.

4. Confirme se a **Versão** do Windows 10 é a **1607 ou superior**.

    > [!IMPORTANT]
    > Os passos apresentados neste guia de início rápido aplicam-se à versão **1607 ou superior** do Windows 10. Se a sua versão for a **igual ou inferior à 1511**, prossiga a partir [destes passos](/intune-user-help/enroll-windows-10-device.md).  

## <a name="enroll-windows-10-desktop"></a>Inscrever o Windows 10 Desktop

1. Regresse às Definições do Windows e selecione **Contas**.

   ![Captura de ecrã a mostrar as suas definições de sistema – Contas](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. Selecione **Aceder a profiss./escolar** > **Ligar**.

    ![Selecione Contas, Aceder a profiss./escolar](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. Inicie sessão no Intune com a sua conta profissional ou escolar e, em seguida, selecione **Seguinte**. Se tiver seguido os [criar um utilizador e atribuir uma licença](quickstart-create-user.md) início rápido, pode iniciar sessão com a conta de utilizador que criou.

    > [!NOTE]
    > Se estiver a configurar uma conta ".onmicrosoft.com", a conta de utilizador apresentará o domínio **.onmicrosoft.com** como parte do respetivo endereço. 

   ![Introduza a sua conta escolar ou profissional](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    Verá uma mensagem a indicar que a sua empresa ou escola está a registar o dispositivo.

4. Quando vir o ecrã **Está tudo pronto!** selecione **Concluído**. Terminou.

5. Agora verá a conta adicionada como parte das definições **Aceder a profiss./escolar** no seu Ambiente de Trabalho do Windows.

   ![Captura de ecrã a mostrar a conta recentemente adicionada](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    Se seguiu os passos anteriores, mas continua a não conseguir aceder à conta de e-mail e aos ficheiros profissionais ou escolares, siga os passos em [Passos de resolução de problemas a seguir se vir Acesso profissional ou escolar](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

## <a name="confirm-your-device-enrollment-in-intune"></a>Confirmar a inscrição do dispositivo no Intune

1. Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.
2. Selecione **Dispositivos** para ver os dispositivos inscritos no Intune.
3. Verifique se tem um dispositivo adicional inscrito no Intune.

   ![Captura de ecrã a mostrar dispositivos inscritos no Intune](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>Limpar recursos

Para anular a inscrição do seu dispositivo Windows, veja [Remover o seu dispositivo Windows da gestão](/intune-user-help/unenroll-your-device-from-intune-windows).

## <a name="next-steps"></a>Passos Seguintes

Neste guia de início rápido, aprendeu como inscrever um dispositivo com o Windows 10 no Intune. Pode aprender outras formas de inscrição de dispositivos em todas as plataformas. Para obter mais informações sobre como utilizar dispositivos com o Intune, veja [Utilizar dispositivos geridos para trabalhar](/intune-user-help/use-managed-devices-to-get-work-done).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Definir um comprimento de palavra-passe obrigatório para dispositivos Android](quickstart-set-password-length-android.md)
