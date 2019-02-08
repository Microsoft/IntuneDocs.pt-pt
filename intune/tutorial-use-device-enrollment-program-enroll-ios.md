---
title: Tutorial – utilizar o programa de inscrição de dispositivos para inscrever dispositivos iOS no Intune
titleSuffix: Microsoft Intune
description: Neste tutorial, vai configurar da Apple DEP para inscrever dispositivos iOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/30/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17258ce2bd671dba091fa7206e599858e5ec7a93
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841543"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>Tutorial: Utilizar o programa de inscrição de dispositivos para inscrever dispositivos iOS no Intune
Programa de inscrição de dispositivos de (DEP da Apple) simplifica a inscrição de dispositivos. Com o Microsoft Intune e o DEP, os dispositivos são inscritos automaticamente na primeira vez que o usuário ativa o dispositivo. Portanto pode enviar dispositivos para muitos usuários sem ter de configurar individualmente cada dispositivo. 

Neste tutorial, ficará a saber como:
> [!div class="checklist"]
> * Obter um token DEP da Apple
> * Criar um grupo de dispositivos do Autopilot
> * Criar um perfil de implementação do Autopilot
> * Atribuir um perfil de implementação do Autopilot ao grupo de dispositivos
> * Distribuir dispositivos Windows pelos utilizadores

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Dispositivos adquiridos através do [Programa de Inscrição de Dispositivos da Apple](http://deploy.apple.com)
- Definir o [autoridade de gestão de dispositivos móveis](mdm-authority-set.md)
- Obter um [certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obter um token DEP da Apple
Antes de inscrever dispositivos iOS com o DEP, precisa de um ficheiro de token (. pem) do DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos DEP que são propriedade da sua empresa. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Pode utilizar o portal de DEP da Apple para criar um token DEP. Também pode utilizar o portal de DEP para atribuir dispositivos ao Intune para gestão.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do Programa de Inscrição** > **Adicionar**.

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.

4. Selecione **Criar um token para o Programa de Registo de Aparelho da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o Apple ID da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.

5.  No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**.

4. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.

5. Para **nome do servidor MDM**, introduza *TestMDMServer* e, em seguida, escolha **seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome ou URL do servidor do Microsoft Intune.

6. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Aceda a **programas de implementação** > **programa de inscrição de dispositivos** > **gerir dispositivos**.
7. Sob **selecionar dispositivos por**, escolha **número de série**. <!--ask Tiffany about this-->

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

9. Para referência futura, no Intune no portal do Azure, forneça o ID Apple utilizado para criar este token.

    ![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

10. Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. 

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple
Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos DEP. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.

2. Selecione o token que acabou de instalar, escolha **perfis** > **criar perfil**.

3. Sob **criar perfil**, introduza *TestDEPProfile* para **nome** e *teste de DEP para dispositivos iOS* para **descrição** . Os utilizadores não verão estes detalhes.

4. Para **afinidade de utilizador**, escolha **inscrever com afinidade de utilizador**. Esta opção destina-se a dispositivos que pertencem aos utilizadores que pretendem utilizar o Portal da empresa para serviços como a instalação de aplicações.

5. Escolher **não** sob **autenticar no Portal da empresa em vez do Assistente de configuração do Apple**.

6. Escolher **definições de gestão de dispositivos** e escolha **não** sob **supervisionado**. Dispositivos supervisionados dão-lhe mais opções de gestão, mas não usá-lo para efeitos deste tutorial.

7. Escolha **OK**.

8. Escolher **personalização do Assistente de configuração** e introduza *departamento Tutorial* para **nome do departamento**. Esta cadeia é que os utilizadores veem quando estes tocam **sobre a configuração** durante a ativação do dispositivo.

9. Sob **telefone do departamento**, introduza um número de telefone. Este número é apresentado quando os utilizadores tocam no **precisa de ajuda** botão durante a ativação.

10. Pode **mostrar** ou **ocultar** uma variedade de ecrãs durante a ativação do dispositivo. Para efeitos deste tutorial, defina **código de acesso** ao **mostrar** e todas as outras para **ocultar**.

11. Selecione **OK** > **Criar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos

Agora, pode ver quais os dispositivos que estão atribuídos a este token.

1. No Intune no portal do Azure, selecione **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token no a lista > **dispositivos** > **sincronização**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Atribuir um perfil de inscrição para dispositivos iOS

Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los.

1. No Intune no portal do Azure, selecione **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha o seu token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos > **Atribuir**.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Definiu até o gerenciamento e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a sua inscrição de dispositivos do DEP. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador.

## <a name="clean-up-resources"></a>Limpar recursos

Se não quiser mais usar dispositivos Autopilot, pode eliminá-los.

- Se os dispositivos estiverem inscritos no Intune, primeiro tem de [eliminá-los do portal do Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>Passos Seguintes

Pode encontrar mais informações sobre outras opções disponíveis para inscrever dispositivos iOS.

> [!div class="nextstepaction"]
> [Artigo de inscrição de DEP do iOS aprofundada](device-enrollment-program-enroll-ios.md)
