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
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3b903c8d21b678bb86d9e6474dbe52a9caaaf74
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503608"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutorial: proteger o email do Exchange Online em dispositivos não gerenciados

Saiba mais sobre como usar políticas de proteção de aplicativo com acesso condicional para proteger o Exchange Online, mesmo quando os dispositivos não são registrados em uma solução de gerenciamento de dispositivo como o Intune. Neste tutorial, ficará a saber como: 

> [!div class="checklist"]
> * Crie uma política de proteção de aplicativo do Intune para o aplicativo Outlook. Você limitará o que o usuário pode fazer com os dados do aplicativo, impedindo "salvar como" e restringir as ações de recortar, copiar e colar. 
> * Criar políticas de acesso condicional do Azure Active Directory (AD do Azure) que permitem que apenas o aplicativo do Outlook acesse o email da empresa no Exchange Online. Você também precisará da MFA (autenticação multifator) para clientes de autenticação modernos, como o Outlook para iOS e Android.

## <a name="prerequisites"></a>Pré-requisitos
- Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:
  - Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - Assinatura do Intune ([avaliação gratuita](../fundamentals/free-trial-sign-up.md))
  - Subscrição do Office 365 Empresas com o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) enquanto Administrador Global ou Administrador de Serviços do Intune. O Intune encontra-se no portal do Azure. Para aceder ao Intune, selecione **Todos os serviços** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Criar a política de proteção do aplicativo
Para este tutorial, vamos configurar uma política de proteção de aplicativo do Intune para o aplicativo do Outlook para colocar as proteções em vigor no nível do aplicativo. Precisaremos de um PIN para abrir o aplicativo em um contexto de trabalho. Também limitaremos o compartilhamento de dados entre aplicativos e evitaremos que os dados da empresa sejam salvos em um local pessoal.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **aplicativos cliente** > **políticas de proteção de aplicativo** > **criar política**.  
2. Configure a seguinte definição:  
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

- A segunda política exigirá que os clientes do Exchange ActiveSync usem o aplicativo Outlook aprovado. (Atualmente, Exchange Active Sync não dá suporte a condições diferentes da plataforma de dispositivo). Você pode configurar políticas de acesso condicional no portal do Azure AD ou no portal do Intune. Uma vez que já estamos no portal do Intune, vamos criar a política aqui.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Criar uma política de MFA para clientes de autenticação moderna  

1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.  

2. Para **nome**, insira **a política de teste para clientes de autenticação modernos**.  

3. Em **Atribuições**, selecione **Utilizadores e grupos**. No separador **Incluir**, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.

4. Em **atribuições**, selecione **aplicativos de nuvem ou ações**. Uma vez que queremos proteger o e-mail do Office 365 Exchange Online, vamos selecioná-lo ao seguir estes passos:  
     
   1. No separador **Incluir**, escolha **Selecionar aplicações**.  
   2. Clique em **Selecionar**.  
   3. Na lista de aplicativos, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecionar**.  
   4. Selecione **concluído** para retornar ao painel nova política.  
  
   ![Selecionar a aplicação Office 365 Exchange Online](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Na guia **incluir** , selecione **qualquer dispositivo**.  
   3. Selecione **Concluído**.  
   
6. No painel **condições** , selecione **aplicativos cliente**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Selecione **aplicativos móveis e clientes de área de trabalho** e **clientes de autenticação modernos**.  
   3. Desmarque as outras caixas de seleção.  
   4. Selecione **concluído** > **feito** para retornar ao painel nova política.  

   ![Selecionar aplicativos móveis e clientes](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7. Em **Controlos de acesso**, selecione **Concessão**. 
     
   1. No painel **Concessão**, selecione **Conceder acesso**.
   2. Selecione **exigir autenticação multifator**.
   3. Selecione **Requer aplicação aprovada do cliente**.
   4. Em **Para vários controlos**, selecione **Exigir todos os controlos selecionados**. Esta definição garantirá que ambos os requisitos que selecionou são impostos quando um dispositivo tentar aceder ao e-mail.
   5. Clique em **Selecionar**.
     
   ![Selecionar controles](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

7. Em **habilitar política**, selecione **ativado**e, em seguida, selecione **criar**.  
     
    ![Criar política](./media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

A política de acesso condicional para clientes de autenticação moderna é criada. Agora você pode criar uma política para clientes Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Criar uma política para clientes de Exchange Active Sync  
1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.  
2. Para **nome**, insira a **política de teste para clientes EAS**.  
3. Em **Atribuições**, selecione **Utilizadores e grupos**.  
4. No separador *Incluir*, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.  

5. Em **atribuições**, selecione **aplicativos de nuvem ou ações**. Selecione email do Office 365 Exchange Online com estas etapas:  
   1. No separador *Incluir*, escolha **Selecionar aplicações**.  
   2. Clique em **Selecionar**.  
   3. Na lista de *aplicativos*, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecionar**e, em seguida, **concluído**.  
  
6. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Na guia **incluir** , selecione **qualquer dispositivo**e, em seguida, selecione **concluído**.  

7. No painel **condições** , selecione **aplicativos cliente**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Selecione **aplicativos móveis e clientes de desktop**.  
   3. Selecione **clientes do Exchange ActiveSync** e **aplique a política somente às plataformas com suporte**.  
   4. Desmarque todas as outras caixas de verificação.  
   5. Selecione **Concluído** e, em seguida, selecione **Concluído** novamente.  
    
   ![Aplicar a plataformas com suporte](./media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

7. Em **Controlos de acesso**, selecione **Concessão**.  
   1. No painel **Concessão**, selecione **Conceder acesso**.  
   2. Selecione **Requer aplicação aprovada do cliente**. Desmarque todas as outras caixas de verificação.  
   3. Clique em **Selecionar**.  
     
   ![Exigir aplicativo cliente aprovado](./media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)  

8. Em **Ativar política**, selecione **Ativar**.  

9. Selecione **Criar**.  

Suas políticas de proteção de aplicativo e acesso condicional estão agora em vigor e prontos para teste.  

## <a name="try-it-out"></a>Experimentar  
Com as políticas que você criou, os dispositivos precisarão se registrar no Intune e usar o aplicativo móvel do Outlook para acessar o email do Office 365. Para testar este cenário num dispositivo iOS, experimente iniciar sessão no Exchange Online com as credenciais para um utilizador no seu inquilino de teste.  
1. Para testar num iPhone, aceda a **Definições** > **Palavras-passe e Contas** > **Adicionar Conta** > **Exchange**.  
2. Introduza o endereço de e-mail de um utilizador no inquilino de teste e, em seguida, prima **Seguinte**.  
3. Prima **Iniciar Sessão**.  
4. Introduza a palavra-passe do utilizador de teste e prima **Iniciar sessão**.  
5. A mensagem **mais informações é necessária** , o que significa que você está sendo solicitado a configurar o MFA. Vá em frente e configure um método de verificação adicional.  
6. Em seguida, você verá uma mensagem dizendo que está tentando abrir esse recurso com um aplicativo que não está aprovado pelo departamento de ti. A mensagem significa que você está sendo impedido de usar o aplicativo de email nativo. Cancele a entrada.  
7. Abra o aplicativo Outlook e selecione **configurações** > **adicionar conta** > **adicionar conta de email**.  
8. Introduza o endereço de e-mail de um utilizador no inquilino de teste e, em seguida, prima **Seguinte**.  
9. Pressione **entrar com o Office 365**. Você será solicitado a fornecer autenticação e registro adicionais. Depois de entrar, você pode testar ações como recortar, copiar, colar e "salvar como".  

## <a name="clean-up-resources"></a>Limpar recursos  
Quando já não precisar das políticas de teste, poderá removê-las.  
1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) enquanto Administrador Global ou Administrador de Serviços do Intune.  
2. Selecione **Conformidade do Dispositivo** > **Políticas**.  
3. Na lista **Nome da Política**, selecione o menu de contexto ( **...** ) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **OK** para confirmar.  
4. Selecione **Acesso Condicional** > **Políticas**.  
5. Na lista **nome da política** , selecione o menu de contexto ( **...** ) para cada uma das políticas de teste e, em seguida, selecione **excluir**. Selecione **Sim** para confirmar.  

## <a name="next-steps"></a>Próximos passos  
Neste tutorial, você criou políticas de proteção de aplicativo para limitar o que o usuário pode fazer com o aplicativo Outlook e criou políticas de acesso condicional para exigir o aplicativo Outlook e exigir MFA para clientes de autenticação modernos. Para saber mais sobre como usar o Intune com acesso condicional para proteger outros aplicativos e serviços, consulte [Configurar o acesso condicional](conditional-access.md).
