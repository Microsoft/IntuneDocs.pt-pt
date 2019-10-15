---
title: Tutorial – proteger email do Exchange Online em dispositivos gerenciados
titleSuffix: Microsoft Intune
description: Saiba como proteger o Exchange Online com as políticas de conformidade do iOS Intune e o acesso condicional do Azure AD para exigir dispositivos gerenciados e o aplicativo Outlook.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c20c0c1543cd8fcbf7345a02295486aaaa6ddcea
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306876"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Tutorial: proteger o email do Exchange Online em dispositivos gerenciados
Saiba mais sobre como usar políticas de conformidade do dispositivo com acesso condicional para garantir que os dispositivos iOS possam acessar o email do Exchange Online somente se eles forem gerenciados pelo Intune e usando um aplicativo de email aprovado. 

Neste tutorial, ficará a saber como: 
> [!div class="checklist"]
> * Crie uma política de conformidade de dispositivo iOS do Intune para definir as condições que um dispositivo deve atender para ser considerado em conformidade.
> * Crie uma política de acesso condicional do Azure Active Directory (AD do Azure) que exija que os dispositivos iOS se registrem no Intune, cumpram as políticas do Intune e use o aplicativo móvel do Outlook aprovado para acessar o email do Exchange Online.

Se você não tiver uma assinatura do Intune, [Inscreva-se para uma conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Você precisará de um locatário de teste com as seguintes assinaturas para este tutorial:
  - Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - Assinatura comercial do Office 365 que inclui o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))
- Antes de começar, crie um perfil de dispositivo de teste para dispositivos iOS seguindo as etapas em [início rápido: criar um perfil de dispositivo de email para IOS](../configuration/quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Entrar no Intune

Entre no [Intune](https://aka.ms/intuneportal) como um administrador global ou um administrador de serviços do Intune. Se você tiver criado uma assinatura de avaliação do Intune, a conta com a qual você criou a assinatura será o administrador global.

## <a name="create-the-ios-device-compliance-policy"></a>Criar a política de conformidade do dispositivo iOS
Configure uma política de conformidade do dispositivo do Intune para definir as condições que um dispositivo deve atender para ser considerado em conformidade. Para este tutorial, criaremos uma política de conformidade do dispositivo para dispositivos iOS. As políticas de conformidade são específicas da plataforma, portanto, você precisa de uma política de conformidade separada para cada plataforma de dispositivo que você deseja avaliar.

1. No Intune, selecione **conformidade do dispositivo** > **políticas** > **criar política**.
2. Em **nome**, insira **teste de política de conformidade do IOS**. 
3. Em **Descrição**, insira **teste de política de conformidade do IOS**.
4. Em **plataforma**, selecione **Ios**. 
5. Selecione **configurações** > **email**. 
     
    1. Ao lado de exigir que os **dispositivos móveis tenham um perfil de email gerenciado**, selecione **exigir**.
    2. Selecione **OK**.

    ![Definir a política de conformidade de email para exigir um perfil de email gerenciado](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6. Selecione **integridade do dispositivo**. Ao lado de **dispositivos com jailbreak**, selecione **Bloquear**e, em seguida, selecione **OK**.
7. Selecione **segurança do sistema** e insira as configurações de **senha** . Para este tutorial, selecione as seguintes configurações recomendadas:
     
    - Para **exigir uma senha para desbloquear dispositivos móveis**, selecione **exigir**.
    - Para **senhas simples**, selecione **Bloquear**.
    - Para **comprimento mínimo da senha**, digite **4**.
    - Para **tipo de senha necessária**, escolha **alfanumérico**.
    - Para **máximo de minutos após o bloqueio de tela antes que a senha seja necessária**, escolha **imediatamente**.
    - Para **expiração da senha (dias)** , digite **41**.
    - Para o **número de senhas anteriores para evitar a reutilização**, insira **5**.
 
    ![Definir configurações de senha para a política de conformidade de email](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Selecione **OK**e, em seguida, selecione **OK** novamente.
9. Selecione **Criar**.

## <a name="create-the-conditional-access-policy"></a>Criar a política de acesso condicional
Agora, criaremos uma política de acesso condicional que exige que todas as plataformas de dispositivo sejam registradas no Intune e estejam em conformidade com nossa política de conformidade do Intune antes que possam acessar o Exchange Online. Também precisaremos do aplicativo Outlook para acesso ao email. As políticas de acesso condicional são configuráveis no portal do Azure AD ou no portal do Intune. Como já estamos no portal do Intune, vamos criar a política aqui.
1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.
1. Em **nome**, insira **política de teste para email do Office 365**. 
3. Em **atribuições**, selecione **usuários e grupos**. Na guia **incluir** , selecione **todos os usuários**e, em seguida, selecione **concluído**.

4. Em **atribuições**, selecione **aplicativos de nuvem**. Como queremos proteger o email do Office 365 Exchange Online, vamos selecioná-lo seguindo estas etapas:
     
    1. Na guia **incluir** , escolha **selecionar aplicativos**.
    2. Escolha **Selecionar**. 
    3. Na lista de aplicativos, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecionar**. 
    4. Selecione **Done** (Concluído).
  
    ![Selecione o aplicativo Office 365 Exchange Online](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. Em **atribuições**, selecione **condições** > **plataformas de dispositivo**.
     
    1. Em **Configurar**, selecione **Sim**.
    2. Na guia **incluir** , selecione **qualquer dispositivo**e, em seguida, selecione **concluído**. 
    3. Selecione **concluído** novamente.
   
    ![Incluir qualquer dispositivo](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. Em **atribuições**, selecione **condições** > **aplicativos cliente**.
     
    1. Em **Configurar**, selecione **Sim**.
    2. Para este tutorial, selecione **aplicativos móveis e clientes de área de trabalho** e **clientes de autenticação moderna** (que se refere a aplicativos como Outlook para IOS e Outlook para Android). Desmarque todas as outras caixas de seleção.
    3. Selecione **concluído**e, em seguida, selecione **concluído** novamente.
    
    ![Selecionar aplicativos e clientes](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. Em **controles de acesso**, selecione **conceder**. 
     
    1. No painel **conceder** , selecione **conceder acesso**.
    2. Selecione **exigir que o dispositivo seja marcado como compatível**. 
    3. Selecione **exigir aplicativo cliente aprovado**.
    4. Em **para vários controles**, selecione **exigir todos os controles selecionados**. Essa configuração garante que os dois requisitos selecionados sejam aplicados quando um dispositivo tentar acessar o email.
    5. Escolha **Selecionar**.
     
    ![Selecionar conrols](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. Em **Ativar política**, selecione **Ativado**.
     
    ![Habilitar política](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Selecione **Criar**.

## <a name="try-it-out"></a>Experimentar
Com as políticas que você criou, qualquer dispositivo iOS que tentar entrar no email do Office 365 precisará se registrar no Intune e usar o aplicativo móvel do Outlook para iOS. Para testar esse cenário em um dispositivo iOS, tente entrar no Exchange Online usando as credenciais de um usuário em seu locatário de teste. Você será solicitado a registrar o dispositivo e instalar o aplicativo móvel do Outlook.
1. Para testar em um iPhone, vá para **configurações** > **senhas & contas** > **adicionar conta** > **Exchange**.
2. Insira o endereço de email para um usuário em seu locatário de teste e, em seguida, pressione **Avançar**.
3. Pressione **entrar**.
4. Insira a senha do usuário de teste e pressione **entrar**.
5. Uma mensagem aparece dizendo que o dispositivo deve ser gerenciado para acessar o recurso, juntamente com uma opção para registrar. 

## <a name="clean-up-resources"></a>Limpar recursos
Quando as políticas de teste não forem mais necessárias, você poderá removê-las.
1. Entre no [Intune](https://aka.ms/intuneportal) como um administrador global ou um administrador de serviços do Intune.
2. Selecione **conformidade do dispositivo** > **políticas**.
3. Na lista **nome da política** , selecione o menu de contexto ( **...** ) para a política de teste e, em seguida, selecione **excluir**. Selecione **OK** para confirmar.
4. Selecione **acesso condicional** > **políticas**.
5. Na lista **nome da política** , selecione o menu de contexto ( **...** ) para a política de teste e, em seguida, selecione **excluir**. Selecione **Sim** para confirmar.

## <a name="next-steps"></a>Passos seguintes 
Neste tutorial, você criou políticas que exigem dispositivos iOS para registrar no Intune e usar o aplicativo Outlook para acessar o email do Exchange Online. Para saber mais sobre como usar o Intune com acesso condicional para proteger outros aplicativos e serviços, incluindo clientes do Exchange ActiveSync para o Office 365 Exchange Online, consulte [Configurar o acesso condicional](conditional-access.md).
