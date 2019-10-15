---
title: Tutorial – proteger email do Exchange Online em dispositivos não gerenciados
titleSuffix: Microsoft Intune
description: Saiba como proteger o Office 365 Exchange Online com as políticas de proteção de aplicativo do Intune e o acesso condicional do Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/10/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e0a01034bc35ddf8fd8eb1ede5fcf4c942dc735
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306799"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutorial: proteger o email do Exchange Online em dispositivos não gerenciados

Saiba mais sobre como usar políticas de proteção de aplicativo com acesso condicional para proteger o Exchange Online, mesmo quando os dispositivos não são registrados em uma solução de gerenciamento de dispositivo como o Intune. Neste tutorial, ficará a saber como: 

> [!div class="checklist"]
> * Crie uma política de proteção de aplicativo do Intune para o aplicativo Outlook. Você limitará o que o usuário pode fazer com os dados do aplicativo, impedindo "salvar como" e restringir as ações de recortar, copiar e colar. 
> * Criar políticas de acesso condicional do Azure Active Directory (AD do Azure) que permitem que apenas o aplicativo do Outlook acesse o email da empresa no Exchange Online. Você também precisará da MFA (autenticação multifator) para clientes de autenticação modernos, como o Outlook para iOS e Android.

## <a name="prerequisites"></a>Pré-requisitos
- Você precisará de um locatário de teste com as seguintes assinaturas para este tutorial:
  - Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - Assinatura do Intune ([avaliação gratuita](../fundamentals/free-trial-sign-up.md))
  - Assinatura comercial do Office 365 que inclui o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Entrar no Intune

Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) como um administrador global ou um administrador de serviços do Intune. O Intune está localizado na portal do Azure escolhendo **todos os serviços** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Criar a política de proteção do aplicativo
Para este tutorial, vamos configurar uma política de proteção de aplicativo do Intune para o aplicativo do Outlook para colocar as proteções em vigor no nível do aplicativo. Precisaremos de um PIN para abrir o aplicativo em um contexto de trabalho. Também limitaremos o compartilhamento de dados entre aplicativos e evitaremos que os dados da empresa sejam salvos em um local pessoal.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **aplicativos cliente** > **políticas de proteção de aplicativo** > **criar política**.  
2. Defina a seguinte configuração:  
   - **Nome**: Insira o **teste de política de aplicativo do Outlook**.  
   - **Descrição**: Insira o **teste de política de aplicativo do Outlook**.  
   - **Plataforma**: selecione **Ios**.  
   - **Destino para todos os tipos de aplicativo**: selecione **não**e, para **tipos de aplicativo**, marque a caixa de seleção para **aplicativos em dispositivos não gerenciados**.  
3. Selecione **aplicativos**. Na lista de aplicativos, selecione **Outlook**e, em seguida, escolha **selecionar**.
4. Selecione **configurações** para abrir o painel configurações. 
5. No painel configurações, selecione **proteção de dados**. No painel proteção de dados, abaixo *transferência de dados*, defina as seguintes configurações para este tutorial:

   - Para **enviar dados da org para outros aplicativos**, selecione **nenhum**.  
   - Para **receber dados de outros aplicativos**, selecione **nenhum**.  
   - Para **salvar cópias dos dados da organização**, selecione **Bloquear**.  
   - Para **restringir recortar, copiar e colar entre outros aplicativos**, selecione **bloqueado**. 
   - Deixe todas as outras configurações com seus valores padrão. 
   
   ![Selecione as configurações de realocação de dados da política de proteção de aplicativo do Outlook](./media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   Selecione **OK** para retornar ao painel configurações.  

6. Selecione **requisitos de acesso** e defina as seguintes configurações:  

   - Para **PIN para acesso**, selecione **exigir**.
   - Para **credenciais de conta corporativa ou de estudante para acesso**, selecione **exigir**.
   - Deixe todas as outras configurações com seus valores padrão.
 
    ![Selecione as ações de acesso à política de proteção de aplicativo do Outlook](./media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

    Selecione **OK** para retornar ao painel configurações.  

7. No painel configurações, selecione **OK**e, em seguida, no painel criar política, selecione **criar**.

A política de proteção de aplicativo para o Outlook é criada. Em seguida, você configurará o acesso condicional para exigir que os dispositivos usem o aplicativo Outlook.

## <a name="create-conditional-access-policies"></a>Criar políticas de acesso condicional
Agora, criaremos duas políticas de acesso condicional para abranger todas as plataformas de dispositivo.  

- A primeira política exigirá que os clientes de autenticação modernos usem o aplicativo Outlook aprovado e a MFA (autenticação multifator). Os clientes de autenticação moderna incluem o Outlook para iOS e o Outlook para Android.  

- A segunda política exigirá que os clientes do Exchange ActiveSync usem o aplicativo Outlook aprovado. (Atualmente, Exchange Active Sync não dá suporte a condições diferentes da plataforma de dispositivo). Você pode configurar políticas de acesso condicional no portal do Azure AD ou no portal do Intune. Como já estamos no portal do Intune, vamos criar a política aqui.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Criar uma política de MFA para clientes de autenticação moderna  

1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.  

2. Para **nome**, insira **a política de teste para clientes de autenticação modernos**.  

3. Em **atribuições**, selecione **usuários e grupos**. Na guia **incluir** , selecione **todos os usuários**e, em seguida, selecione **concluído**.

4. Em **atribuições**, selecione **aplicativos de nuvem ou ações**. Como queremos proteger o email do Office 365 Exchange Online, vamos selecioná-lo seguindo estas etapas:  
     
   1. Na guia **incluir** , escolha **selecionar aplicativos**.  
   2. Escolha **Selecionar**.  
   3. Na lista de aplicativos, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecionar**.  
   4. Selecione **concluído** para retornar ao painel nova política.  
  
   ![Selecione o aplicativo Office 365 Exchange Online](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5. Em **atribuições**, selecione **condições** > **plataformas de dispositivo**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Na guia **incluir** , selecione **qualquer dispositivo**.  
   3. Selecione **Done** (Concluído).  
   
6. No painel **condições** , selecione **aplicativos cliente**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Selecione **aplicativos móveis e clientes de área de trabalho** e **clientes de autenticação modernos**.  
   3. Desmarque as outras caixas de seleção.  
   4. Selecione **concluído** > **feito** para retornar ao painel nova política.  

   ![Selecionar aplicativos móveis e clientes](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7. Em **controles de acesso**, selecione **conceder**. 
     
   1. No painel **conceder** , selecione **conceder acesso**.
   2. Selecione **exigir autenticação multifator**.
   3. Selecione **exigir aplicativo cliente aprovado**.
   4. Em **para vários controles**, selecione **exigir todos os controles selecionados**. Essa configuração garante que os dois requisitos selecionados sejam aplicados quando um dispositivo tentar acessar o email.
   5. Escolha **Selecionar**.
     
   ![Selecionar controles](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

7. Em **habilitar política**, selecione **ativado**e, em seguida, selecione **criar**.  
     
    ![Criar política](./media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

A política de acesso condicional para clientes de autenticação moderna é criada. Agora você pode criar uma política para clientes Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Criar uma política para clientes de Exchange Active Sync  
1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.  
2. Para **nome**, insira a **política de teste para clientes EAS**.  
3. Em **atribuições**, selecione **usuários e grupos**.  
4. Na guia *incluir* , selecione **todos os usuários**e, em seguida, selecione **concluído**.  

5. Em **atribuições**, selecione **aplicativos de nuvem ou ações**. Selecione email do Office 365 Exchange Online com estas etapas:  
   1. Na guia *incluir* , escolha **selecionar aplicativos**.  
   2. Escolha **Selecionar**.  
   3. Na lista de *aplicativos*, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecionar**e, em seguida, **concluído**.  
  
6. Em **atribuições**, selecione **condições** > **plataformas de dispositivo**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Na guia **incluir** , selecione **qualquer dispositivo**e, em seguida, selecione **concluído**.  

7. No painel **condições** , selecione **aplicativos cliente**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Selecione **aplicativos móveis e clientes de desktop**.  
   3. Selecione **clientes do Exchange ActiveSync** e **aplique a política somente às plataformas com suporte**.  
   4. Desmarque todas as outras caixas de seleção.  
   5. Selecione **concluído**e, em seguida, selecione **concluído** novamente.  
    
   ![Aplicar a plataformas com suporte](./media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

7. Em **controles de acesso**, selecione **conceder**.  
   1. No painel **conceder** , selecione **conceder acesso**.  
   2. Selecione **exigir aplicativo cliente aprovado**. Desmarque todas as outras caixas de seleção.  
   3. Escolha **Selecionar**.  
     
   ![Exigir aplicativo cliente aprovado](./media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)  

8. Em **Ativar política**, selecione **Ativado**.  

9. Selecione **Criar**.  

Suas políticas de proteção de aplicativo e acesso condicional estão agora em vigor e prontos para teste.  

## <a name="try-it-out"></a>Experimentar  
Com as políticas que você criou, os dispositivos precisarão se registrar no Intune e usar o aplicativo móvel do Outlook para acessar o email do Office 365. Para testar esse cenário em um dispositivo iOS, tente entrar no Exchange Online usando as credenciais de um usuário em seu locatário de teste.  
1. Para testar em um iPhone, vá para **configurações** > **senhas & contas** > **adicionar conta** > **Exchange**.  
2. Insira o endereço de email para um usuário em seu locatário de teste e, em seguida, pressione **Avançar**.  
3. Pressione **entrar**.  
4. Insira a senha do usuário de teste e pressione **entrar**.  
5. A mensagem **mais informações é necessária** , o que significa que você está sendo solicitado a configurar o MFA. Vá em frente e configure um método de verificação adicional.  
6. Em seguida, você verá uma mensagem dizendo que está tentando abrir esse recurso com um aplicativo que não está aprovado pelo departamento de ti. A mensagem significa que você está sendo impedido de usar o aplicativo de email nativo. Cancele a entrada.  
7. Abra o aplicativo Outlook e selecione **configurações** > **adicionar conta** > **adicionar conta de email**.  
8. Insira o endereço de email para um usuário em seu locatário de teste e, em seguida, pressione **Avançar**.  
9. Pressione **entrar com o Office 365**. Você será solicitado a fornecer autenticação e registro adicionais. Depois de entrar, você pode testar ações como recortar, copiar, colar e "salvar como".  

## <a name="clean-up-resources"></a>Limpar recursos  
Quando as políticas de teste não forem mais necessárias, você poderá removê-las.  
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) como um administrador global ou um administrador de serviços do Intune.  
2. Selecione **conformidade do dispositivo** > **políticas**.  
3. Na lista **nome da política** , selecione o menu de contexto ( **...** ) para a política de teste e, em seguida, selecione **excluir**. Selecione **OK** para confirmar.  
4. Selecione **acesso condicional** > **políticas**.  
5. Na lista **nome da política** , selecione o menu de contexto ( **...** ) para cada uma das políticas de teste e, em seguida, selecione **excluir**. Selecione **Sim** para confirmar.  

## <a name="next-steps"></a>Passos seguintes  
Neste tutorial, você criou políticas de proteção de aplicativo para limitar o que o usuário pode fazer com o aplicativo Outlook e criou políticas de acesso condicional para exigir o aplicativo Outlook e exigir MFA para clientes de autenticação modernos. Para saber mais sobre como usar o Intune com acesso condicional para proteger outros aplicativos e serviços, consulte [Configurar o acesso condicional](conditional-access.md).
