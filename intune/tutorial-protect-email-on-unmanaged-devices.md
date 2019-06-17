---
title: Tutorial - proteger o e-mail do Exchange Online em dispositivos não geridos
titleSuffix: Microsoft Intune
description: Aprenda a proteger o Exchange Online do Office 365 com políticas de proteção de aplicações do Intune e acesso condicional do Azure AD.
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
ms.openlocfilehash: 624cc72ad9539659e1ce2c8b70f6a6698d5e7ba2
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67046279"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutorial: Proteger o e-mail do Exchange Online em dispositivos não geridos

Saiba como utilizar políticas de proteção de aplicações com acesso condicional para proteger o Exchange Online, mesmo quando os dispositivos não estejam inscritos numa solução de gestão de dispositivos, como o Intune. Neste tutorial, ficará a saber como: 

> [!div class="checklist"]
> * Crie uma política de proteção de aplicações do Intune para a aplicação Outlook. Irá limitar o que o utilizador pode fazer com os dados de aplicação ao impedir "Guardar como" e restringir cortar, copiar e colar ações. 
> * Crie políticas de acesso condicional do Azure Active Directory (Azure AD) que permitem apenas a aplicação Outlook aceder ao e-mail da empresa no Exchange Online. Também é necessária autenticação multifator (MFA) para clientes de autenticação moderna, como o Outlook para iOS e Android.

## <a name="prerequisites"></a>Pré-requisitos
  - Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:
    - Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Subscrição do Intune ([avaliação gratuita](free-trial-sign-up.md))
    - Subscrição do Office 365 Empresas com o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) enquanto Administrador Global ou Administrador de Serviços do Intune. O Intune encontra-se no portal do Azure. Para aceder ao Intune, selecione **Todos os serviços** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Crie a política de proteção de aplicações
Para este tutorial, iremos configurar uma política de proteção de aplicações do Intune para a aplicação Outlook colocar proteções in-loco, ao nível da aplicação. Podemos irá exigir um PIN abrir a aplicação num contexto de trabalho. Vamos também limitar a partilha de dados entre aplicações e impedir que os dados da empresa sejam guardados numa localização pessoal.

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e aceda à **aplicações de cliente** > **políticas de proteção de aplicações** > **criar política**.  
2. Configure a seguinte definição:  
   - **Nome**: Introduza **teste de política de aplicação do Outlook**.  
   - **Descrição**: Introduza **teste de política de aplicação do Outlook**.  
   - **Plataforma**: Selecione **iOS**.  
   - **Direcionar para todos os tipos de aplicação**: Selecione **não**e, em seguida, para **tipos de aplicações**, selecione a caixa de verificação **aplicações em dispositivos não geridos**.  
3. Selecione **aplicações**. Na lista de aplicações, selecione **Outlook**e, em seguida, escolha **selecione**.
4. Selecione **definições** para abrir o painel de definições. 
5. No painel de definições, selecione **proteção de dados**. No painel de proteção de dados, abaixo *transferência de dados*, configure as seguintes definições para este tutorial:

   - Para **Org enviar dados para outras aplicações**, selecione **nenhum**.  
   - Para **receba dados de outras aplicações**, selecione **nenhum**.  
   - Para **guardar cópias dos dados da organização**, selecione **bloco**.  
   - Para **restringir operações cortar, copiar e colar entre as outras aplicações**, selecione **bloqueado**. 
   - Deixe todas as outras definições com os valores padrão. 
   
   ![Selecione as definições de reposicionamento de dados de política do Outlook app protection](media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   Selecione **OK** para regressar ao painel de definições.  

6. Selecione **os requisitos de acesso** e, em seguida, configure as seguintes definições:  

   - Para **PIN para aceder à**, selecione **exigir**.
   - Para **profissional ou escolar, credenciais de acesso da conta**, selecione **exigir**.
   - Deixe todas as outras definições com os valores padrão.
 
    ![Selecione as ações de acesso de política de proteção de aplicações de Outlook](media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

    Selecione **OK** para regressar ao painel de definições.  

7.  No painel de definições, selecione **OK**e, em seguida, no painel de política de criar, selecione **criar**.

É criada a política de proteção de aplicações do Outlook. Em seguida, definirá o acesso condicional para exigir que os dispositivos para utilizar a aplicação Outlook.

## <a name="create-conditional-access-policies"></a>Criar políticas de acesso condicional
Agora, vamos criar duas políticas de acesso condicional para cobrir todas as plataformas de dispositivos.  

- A primeira diretiva irá exigir que os clientes de autenticação moderna utilizem o aprovados Outlook aplicação e multi-factor authentication (MFA). Os clientes de autenticação modernos incluem o Outlook para iOS e o Outlook para Android.  

- A segunda política irá exigir que os clientes do Exchange ActiveSync utilizarem a aplicação aprovada do Outlook. (Atualmente, o Exchange Active Sync não suporta condições que não seja a plataforma do dispositivo). Pode configurar políticas de acesso condicional no portal do Azure AD ou no portal do Intune. Uma vez que já estamos no portal do Intune, vamos criar a política aqui.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Crie uma política MFA para os clientes de autenticação moderna  

1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.  

2. Para **Name**, introduza **testar a política para os clientes de autenticação moderna**.  

3. Em **Atribuições**, selecione **Utilizadores e grupos**. No separador **Incluir**, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.

4. Sob **atribuições**, selecione **Cloud aplicações ou ações**. Uma vez que queremos proteger o e-mail do Office 365 Exchange Online, vamos selecioná-lo ao seguir estes passos:  
     
   1. No separador **Incluir**, escolha **Selecionar aplicações**.  
   2. Escolha **Selecionar**.  
   3. Na lista de aplicações, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecione**.  
   4. Selecione **feito** para voltar para o novo painel de política.  
  
   ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Sobre o **inclusão** separador, selecione **qualquer dispositivo**.  
   3. Selecione **Done** (Concluído).  
   
6. Sobre o **condições** painel, selecione **aplicações de cliente**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Selecione **aplicações móveis e clientes de ambiente de trabalho** e **clientes de autenticação moderna**.  
   3. Desmarque as caixas de verificação.  
   4. Selecione **feito** > **feito** para voltar para o novo painel de política.  

   ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7. Em **Controlos de acesso**, selecione **Concessão**. 
     
   1. No painel **Concessão**, selecione **Conceder acesso**.
   2. Selecione **exigir autenticação multifator**.
   3. Selecione **Requer aplicação aprovada do cliente**.
   4. Em **Para vários controlos**, selecione **Exigir todos os controlos selecionados**. Esta definição garantirá que ambos os requisitos que selecionou são impostos quando um dispositivo tentar aceder ao e-mail.
   5. Escolha **Selecionar**.
     
   ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

7. Sob **ativar política**, selecione **no**e, em seguida, selecione **criar**.  
     
    ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

É criada a política de acesso condicional para clientes de autenticação moderna. Agora, pode criar uma política para os clientes do Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Criar uma política para os clientes do Exchange Active Sync  
1. No Intune, selecione **acesso condicional** > **políticas** > **nova política**.  
2. Para **Name**, introduza **testar a política para clientes EAS**.  
3. Em **Atribuições**, selecione **Utilizadores e grupos**.  
4. No separador *Incluir*, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.  

5. Sob **atribuições**, selecione **Cloud aplicações ou ações**. Selecione o e-mail do Office 365 Exchange Online com estes passos:  
   1. No separador *Incluir*, escolha **Selecionar aplicações**.  
   2. Escolha **Selecionar**.  
   3. Na lista de *aplicativos*, selecione **Office 365 Exchange Online**e, em seguida, escolha **selecione**e, em seguida **feito**.  
  
6. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Sobre o **inclusão** separador, selecione **todos os dispositivos**e, em seguida, selecione **feito**.  

7. Sobre o **condições** painel, selecione **aplicações de cliente**.  
   1. Em **Configurar**, selecione **Sim**.  
   2. Selecione **aplicações móveis e clientes de ambiente de trabalho**.  
   3. Selecione **clientes do Exchange ActiveSync** e **aplicar política apenas a plataformas suportadas**.  
   4. Desmarque todas as outras caixas de verificação.  
   5. Selecione **Concluído** e, em seguida, selecione **Concluído** novamente.  
    
   ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

7. Em **Controlos de acesso**, selecione **Concessão**.  
   1. No painel **Concessão**, selecione **Conceder acesso**.  
   2. Selecione **Requer aplicação aprovada do cliente**. Desmarque todas as outras caixas de verificação.  
   3. Escolha **Selecionar**.  
     
   ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)  

8. Em **Ativar política**, selecione **Ativar**.  

9. Selecione **Criar**.  

O acesso condicional e políticas de proteção de aplicações estão em vigor e está preparado para testar.  

## <a name="try-it-out"></a>Experimentar  
Com as políticas que criou, dispositivos terá de se inscrever no Intune e utilizar a aplicação móvel do Outlook para aceder ao e-mail do Office 365. Para testar este cenário num dispositivo iOS, experimente iniciar sessão no Exchange Online com as credenciais para um utilizador no seu inquilino de teste.  
1. Para testar num iPhone, aceda a **Definições** > **Palavras-passe e Contas** > **Adicionar Conta** > **Exchange**.  
2. Introduza o endereço de e-mail de um utilizador no inquilino de teste e, em seguida, prima **Seguinte**.  
3. Prima **Iniciar Sessão**.  
4. Introduza a palavra-passe do utilizador de teste e prima **Iniciar sessão**.  
5. A mensagem **são necessárias mais informações** for apresentada, que significa que está a ser-lhe pedido para configurar a MFA. Vá em frente e configurar um método de verificação adicional.  
6. Em seguida verá uma mensagem que diz que está a tentar abrir este recurso com uma aplicação que não está aprovada pelo seu departamento de TI. A mensagem significa que está a ser impedido de utilizar a aplicação de e-mail nativo. Cancele o início de sessão.  
7. Abra o Outlook e selecione **configurações** > **adicionar conta** > **adicionar conta de E-Mail**.  
8. Introduza o endereço de e-mail de um utilizador no inquilino de teste e, em seguida, prima **Seguinte**.  
9. Prima **iniciar sessão com o Office 365**. Será solicitado para autenticação adicional e o Registro. Depois de iniciar sessão, pode testar ações como cortar, copiar, colar e "Guardar como".  

## <a name="clean-up-resources"></a>Limpar recursos  
Quando já não precisar das políticas de teste, poderá removê-las.  
1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) enquanto Administrador Global ou Administrador de Serviços do Intune.  
2. Selecione **Conformidade do Dispositivo** > **Políticas**.  
3. Na lista **Nome da Política**, selecione o menu de contexto ( **...** ) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **OK** para confirmar.  
4. Selecione **Acesso Condicional** > **Políticas**.  
5. Na **nome da política** , selecione o menu de contexto ( **...** ) para cada uma das suas políticas de teste e, em seguida, selecione **eliminar**. Selecione **Sim** para confirmar.  

 ## <a name="next-steps"></a>Passos Seguintes  
Neste tutorial, criou as políticas de proteção de aplicações para limitar o que o utilizador pode fazer com o Outlook e criou as políticas de acesso condicional para exigir a aplicação do Outlook e exigir a MFA para os clientes de autenticação moderna. Para saber mais sobre como utilizar o Intune com o acesso condicional para proteger a outras aplicações e serviços, veja [configurar o acesso condicional](conditional-access.md).
