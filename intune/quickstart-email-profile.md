---
title: Início Rápido – criar um perfil de dispositivo de e-mail para iOS
titlesuffix: Microsoft Intune
description: Saiba como pode utilizar o Microsoft Intune para criar um perfil de dispositivo de e-mail de modo que os dispositivos iOS possam estabelecer uma ligação segura ao e-mail da empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 21dda51d2ddde74f07fcc173c5a4dd2a13c9c8b8
ms.sourcegitcommit: 5e5004a31207e75e54504d74548735c048676a03
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51225752"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Guia de Início Rápido: criar um perfil de dispositivo de e-mail para iOS

Neste início rápido, verá como pode criar um perfil de dispositivo de e-mail para dispositivos iOS. Este perfil especifica as definições que são necessárias para a aplicação de e-mail incorporada no dispositivo iOS estabelecer ligação ao e-mail da empresa. Os perfis de dispositivo de e-mail ajudam a padronizar as definições em vários dispositivos e permitem que os utilizadores finais acedam ao e-mail da empresa nos respetivos dispositivos pessoais sem precisarem de realizar qualquer configuração. Para salvaguardar ainda mais o seu e-mail, pode utilizar um perfil de e-mail para determinar se os dispositivos estão em conformidade e, em seguida, para configurar o acesso condicional de modo permitir que apenas os dispositivos conformes acedam ao e-mail. Para obter detalhes sobre perfis de e-mail, veja [Como configurar definições de e-mail no Microsoft Intune](email-settings-configure.md).

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune. O Intune encontra-se no portal do Azure. Para aceder ao Intune, selecione **Todos os serviços** > **Intune**.

## <a name="create-an-ios-email-profile"></a>Criar um perfil de e-mail para iOS
1. No Intune, selecione **Configuração do dispositivo** e, em seguida, selecione **Perfis**.
2. Selecione **Criar Perfil**.
   
   ![Criar um perfil de e-mail para iOS](media/quickstart-email-profile/ios-create-profile.png)

3. Em **Nome**, introduza um nome descritivo para o novo perfil. Neste exemplo, introduza **O iOS necessita de um e-mail de trabalho**.
4. Introduza as seguintes informações de perfil:
   - Em **Descrição**, introduza **Exigir que os dispositivos iOS utilizem o e-mail de trabalho**.
   - Em **Plataforma**, selecione **iOS**.
   - Em **Tipo de perfil**, selecione **E-mail**.
    
     ![Criar um perfil de e-mail para iOS](media/quickstart-email-profile/ios-email-profile-name.png)

5. Selecione **Definições** e introduza as definições que se seguem (nas outras definições, deixe as predefinições):
   - **Servidor de e-mail**: neste início rápido, introduza **outlook.office365.com**. Esta definição especifica a localização do Exchange (URL) do servidor de e-mail que a aplicação de correio do iOS utilizará para estabelecer ligação ao e-mail.
   - **Nome da conta**: introduza o **E-Mail da Empresa**.
   - **Atributo de nome de utilizador do AAD**: este nome é o atributo que o Intune obtém do Azure Active Directory (Azure AD). O Intune gera dinamicamente o nome de utilizador para este perfil através deste nome. Neste início rápido, vamos pressupor que pretendemos que o **Nome Principal de Utilizador** seja utilizado como o nome de utilizador do perfil (por exemplo, user1@contoso.com).
   - **Atributo de endereço de e-mail do AAD**: esta definição é o endereço de e-mail do Azure AD que será utilizado para iniciar sessão no Exchange. Neste início rápido, selecione **Nome Principal de Utilizador**.
   - **Método de autenticação**: neste início rápido, selecione **Nome de utilizador e palavra-passe**. (Também pode selecionar **Certificado** se já tiver configurado um certificado para o Intune.)
    
     ![Criar um perfil de e-mail para iOS](media/quickstart-email-profile/ios-email-profile.png)

6. Selecione **OK**.
7. Selecione **Criar**. O novo perfil aparece na lista de perfis com o dashboard apresentado para que possa monitorizar a forma como o perfil foi atribuído a dispositivos iOS e a utilizadores do iOS.
8. Selecione **Atribuições**.
9. Selecione o separador **Incluir** e, em seguida, selecione **Todos os Utilizadores e Todos os Dispositivos**. 
10. Selecione **Guardar**.

## <a name="clean-up-resources"></a>Limpar recursos
Se não tencionar utilizar o perfil que criou em tutoriais ou testes adicionais, pode eliminá-lo agora.
1. No Intune, selecione **Configuração do dispositivo** e, em seguida, selecione **Perfis**.
2. Selecione o perfil de teste que criou (**O iOS necessita de um e-mail de trabalho**).
3. Selecione as reticências (**...**) que se encontram junto ao perfil e, em seguida, selecione **Eliminar**.

## <a name="next-steps"></a>Próximos passos

Neste início rápido, criou um perfil de e-mail para dispositivos iOS. Agora pode utilizar este perfil para determinar se um dispositivo iOS está em conformidade ao criar uma política de conformidade que assinale como não conformes todos os dispositivos iOS que não correspondam ao perfil. Para obter uma maior proteção, pode criar uma política de acesso condicional que impeça o acesso dos dispositivos iOS não conformes ao e-mail. Para saber mais sobre as políticas de conformidade de dispositivos, veja [Introdução às políticas de conformidade de dispositivos no Intune](device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutorial: Proteger o e-mail do Exchange Online em dispositivos geridos](tutorial-protect-email-on-enrolled-devices.md)
