---
title: Quickstart - Criar um perfil de dispositivo de e-mail para dispositivos iOS/iPadOS
titleSuffix: Microsoft Intune
description: Saiba como usar o Microsoft Intune para criar um perfil de dispositivo de e-mail para que os dispositivos iOS/iPadOS possam ligar-se de forma segura ao e-mail da empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af2576c44e0486dbd859a56896db3b7d0ffc6cff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511073"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>Quickstart: Criar um perfil de dispositivo de e-mail para iOS/iPadOS

Neste arranque rápido, você verá como criar um perfil de dispositivo de e-mail para dispositivos iOS/iPadOS. Este perfil especifica as definições necessárias para que a aplicação de e-mail incorporada no dispositivo iOS/iPadOS se conectem ao e-mail da empresa. Os perfis de dispositivo de e-mail ajudam a padronizar as definições em vários dispositivos e permitem que os utilizadores finais acedam ao e-mail da empresa nos respetivos dispositivos pessoais sem precisarem de realizar qualquer configuração. Para salvaguardar ainda mais o seu e-mail, pode utilizar um perfil de e-mail para determinar se os dispositivos estão em conformidade e, em seguida, configurar o Acesso Condicional para permitir apenas dispositivos compatíveis para aceder a emails. Para obter detalhes sobre perfis de e-mail, veja [Como configurar definições de e-mail no Microsoft Intune](email-settings-configure.md).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) como administrador global ou administrador de serviço intune. Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-an-iosipados-email-profile"></a>Criar um perfil de e-mail iOS/iPadOS

1. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

   ![Criar um perfil de e-mail para iOS/iPadOS em Intune](./media/quickstart-email-profile/ios-create-profile.png)

2. Em **Nome**, introduza um nome descritivo para o novo perfil. Neste exemplo, introduza **O iOS necessita de um e-mail de trabalho**.
3. Introduza as seguintes informações de perfil:
    - Para **descrição**, insira Requisito **seleção de dispositivos iOS/iPadOS para utilizar e-mail**de trabalho .
    - Para **plataforma**, selecione **iOS/iPadOS**.
    - Em **Tipo de perfil**, selecione **E-mail**.

        ![Criar um perfil de e-mail para utilização com dispositivos iOS/iPadOS em Intune](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Selecione **Definições** e introduza as definições que se seguem (nas outras definições, deixe as predefinições):
   - **Servidor de e-mail**: neste início rápido, introduza **outlook.office365.com**. Esta definição especifica a localização de Troca (URL) do servidor de e-mail que a aplicação de correio iOS/iPadOS utilizará para se ligar ao e-mail.
   - **Nome da conta**: introduza o **E-Mail da Empresa**.
   - **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera dinamicamente o nome de utilizador para este perfil através deste nome. Neste início rápido, vamos pressupor que pretendemos que o **Nome Principal de Utilizador** seja utilizado como o nome de utilizador do perfil (por exemplo, user1@contoso.com).
   - **Atributo de endereço de e-mail do AAD**: esta definição é o endereço de e-mail do Azure AD que será utilizado para iniciar sessão no Exchange. Neste início rápido, selecione **Nome Principal de Utilizador**.
   - **Método de autenticação**: neste início rápido, selecione **Nome de utilizador e palavra-passe**. (Também pode selecionar **Certificado** se já tiver configurado um certificado para o Intune.)

        ![Criar um perfil de e-mail para uso iOS/iPadOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Selecione **OK** > **Criar**. O novo perfil aparece na lista de perfis com o painel de instrumentos apresentado para que possa monitorizar a forma como o perfil foi atribuído aos dispositivos iOS/iPadOS e aos utilizadores de iOS/iPadOS.
6. Selecione **Atribuições**.
7. Selecione o separador **Incluir** e, em seguida, selecione **Todos os Utilizadores e Todos os Dispositivos**. 
8. Selecione **Guardar**.

## <a name="clean-up-resources"></a>Limpar recursos

Se não tencionar utilizar o perfil que criou em tutoriais ou testes adicionais, pode eliminá-lo agora.

1. No Intune, selecione **Configuração do dispositivo** e, em seguida, selecione **Perfis**.
2. Selecione o perfil de teste que criou, **iOS/iPadOS requer e-mail**de trabalho .
3. Selecione as reticências ( **...** ) que se encontram junto ao perfil e, em seguida, selecione **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Neste arranque rápido, criou um perfil de e-mail para dispositivos iOS/iPadOS. Agora pode utilizar este perfil para determinar se um dispositivo iOS/iPadOS está em conformidade, criando uma política de conformidade que marca como não conforme qualquer dispositivo iOS/iPadOS que não corresponda ao perfil. Para maior proteção, pode criar uma política de Acesso Condicional que bloqueie dispositivos iOS/iPadOS não conformes de aceder a e-mails. Para saber mais sobre as políticas de conformidade de dispositivos, veja [Introdução às políticas de conformidade de dispositivos no Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutorial: Proteger o e-mail do Exchange Online em dispositivos geridos](../tutorial-protect-email-on-enrolled-devices.md)
