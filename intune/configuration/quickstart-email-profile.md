---
title: Início Rápido – criar um perfil de dispositivo de e-mail para iOS
titleSuffix: Microsoft Intune
description: Saiba como pode utilizar o Microsoft Intune para criar um perfil de dispositivo de e-mail de modo que os dispositivos iOS possam estabelecer uma ligação segura ao e-mail da empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ad26077c00bf4ad4350ebd9ee124d61a69b324
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730548"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Início rápido: Criar um perfil de dispositivo de email para iOS

Neste início rápido, verá como pode criar um perfil de dispositivo de e-mail para dispositivos iOS. Este perfil especifica as definições que são necessárias para a aplicação de e-mail incorporada no dispositivo iOS estabelecer ligação ao e-mail da empresa. Os perfis de dispositivo de e-mail ajudam a padronizar as definições em vários dispositivos e permitem que os utilizadores finais acedam ao e-mail da empresa nos respetivos dispositivos pessoais sem precisarem de realizar qualquer configuração. Para proteger ainda mais seu email, você pode usar um perfil de email para determinar se os dispositivos estão em conformidade e, em seguida, configurar o acesso condicional para permitir que somente dispositivos em conformidade acessem o email. Para obter detalhes sobre perfis de e-mail, veja [Como configurar definições de e-mail no Microsoft Intune](email-settings-configure.md).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune. Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-an-ios-email-profile"></a>Criar um perfil de e-mail para iOS
1. No Intune, selecione **Configuração do dispositivo** e, em seguida, selecione **Perfis**.
2. Selecione **Criar Perfil**.
   
   ![Criar um perfil de e-mail para iOS](./media/quickstart-email-profile/ios-create-profile.png)

3. Em **Nome**, introduza um nome descritivo para o novo perfil. Neste exemplo, introduza **O iOS necessita de um e-mail de trabalho**.
4. Introduza as seguintes informações de perfil:
   - Em **Descrição**, introduza **Exigir que os dispositivos iOS utilizem o e-mail de trabalho**.
   - Em **Plataforma**, selecione **iOS**.
   - Em **Tipo de perfil**, selecione **E-mail**.
    
     ![Criar um perfil de email para usar com o iOS](./media/quickstart-email-profile/ios-email-profile-name.png)

5. Selecione **Definições** e introduza as definições que se seguem (nas outras definições, deixe as predefinições):
   - **Servidor de email**: Para este guia de início rápido, insira **Outlook.office365.com**. Esta definição especifica a localização do Exchange (URL) do servidor de e-mail que a aplicação de correio do iOS utilizará para estabelecer ligação ao e-mail.
   - **Nome da conta**: Insira o **email da empresa**.
   - **Atributo de nome de usuário do AAD**: Esse nome é o atributo que o Intune obtém de Azure Active Directory (Azure AD). O Intune gera dinamicamente o nome de utilizador para este perfil através deste nome. Neste início rápido, vamos pressupor que pretendemos que o **Nome Principal de Utilizador** seja utilizado como o nome de utilizador do perfil (por exemplo, user1@contoso.com).
   - **Atributo de endereço de email do AAD**: Essa configuração é o endereço de email do Azure AD que será usado para entrar no Exchange. Neste início rápido, selecione **Nome Principal de Utilizador**.
   - **Método de autenticação**: Para este guia de início rápido, selecione **nome de usuário e senha**. (Também pode selecionar **Certificado** se já tiver configurado um certificado para o Intune.)
    
     ![Criar um perfil de email para uso do iOS](./media/quickstart-email-profile/ios-email-profile.png)

6. Selecione **OK**.
7. Selecione **Criar**. O novo perfil aparece na lista de perfis com o dashboard apresentado para que possa monitorizar a forma como o perfil foi atribuído a dispositivos iOS e a utilizadores do iOS.
8. Selecione **Atribuições**.
9. Selecione o separador **Incluir** e, em seguida, selecione **Todos os Utilizadores e Todos os Dispositivos**. 
10. Selecione **Guardar**.

## <a name="clean-up-resources"></a>Limpar recursos
Se não tencionar utilizar o perfil que criou em tutoriais ou testes adicionais, pode eliminá-lo agora.
1. No Intune, selecione **Configuração do dispositivo** e, em seguida, selecione **Perfis**.
2. Selecione o perfil de teste que criou (**O iOS necessita de um e-mail de trabalho**).
3. Selecione as reticências ( **...** ) que se encontram junto ao perfil e, em seguida, selecione **Eliminar**.

## <a name="next-steps"></a>Passos seguintes

Neste início rápido, criou um perfil de e-mail para dispositivos iOS. Agora pode utilizar este perfil para determinar se um dispositivo iOS está em conformidade ao criar uma política de conformidade que assinale como não conformes todos os dispositivos iOS que não correspondam ao perfil. Para maior proteção, você pode criar uma política de acesso condicional que impede que dispositivos iOS não compatíveis acessem email. Para saber mais sobre as políticas de conformidade de dispositivos, veja [Introdução às políticas de conformidade de dispositivos no Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Destina Proteger email do Exchange Online em dispositivos gerenciados @ no__t-0
