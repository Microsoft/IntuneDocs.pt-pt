---
title: Tutorial – Proteger o e-mail do Exchange Online em dispositivos geridos pelo Intune
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
ms.openlocfilehash: a5a355c82455e135319b7683756eb0ef5c032876
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882371"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Destina Proteger email do Exchange Online em dispositivos gerenciados
Saiba mais sobre como usar políticas de conformidade do dispositivo com acesso condicional para garantir que os dispositivos iOS possam acessar o email do Exchange Online somente se eles forem gerenciados pelo Intune e usando um aplicativo de email aprovado. 

Neste tutorial, ficará a saber como: 
> [!div class="checklist"]
> * Criar uma política de conformidade de dispositivos iOS do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme.
> * Crie uma política de acesso condicional do Azure Active Directory (AD do Azure) que exija que os dispositivos iOS se registrem no Intune, cumpram as políticas do Intune e use o aplicativo móvel do Outlook aprovado para acessar o email do Exchange Online.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
- Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:
  - Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - Subscrição do Office 365 Empresas com o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))
- Antes de começar, crie um perfil de dispositivo de teste para dispositivos IOS seguindo as etapas [em início rápido: Crie um perfil de dispositivo de email](quickstart-email-profile.md)para Ios.

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune. Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-the-ios-device-compliance-policy"></a>Criar a política de conformidade dos dispositivos iOS
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade para dispositivos iOS. As políticas de conformidade são específicas da plataforma, por isso, precisa de uma política de conformidade separada para cada plataforma de dispositivo que queira avaliar.

1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Em **Nome**, introduza **Teste de política de conformidade do iOS**. 
3. Em **Descrição**, introduza **Teste de política de conformidade do iOS**.
4. Em **Plataforma**, selecione **iOS**. 
5. Selecione **Definições** > **E-mail**. 
     
    1. Junto a **Exigir que os dispositivos móveis tenham um perfil de e-mail gerido**, selecione **Exigir**.
    2. Selecione **OK**.

    ![Definir a política de conformidade de e-mail para exigir um perfil de e-mail gerido](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6. Selecione **Estado de Funcionamento dos Dispositivos**. Junto a **Dispositivos com jailbreak**, selecione **Bloquear** e, em seguida, selecione **OK**.
7. Selecione **Segurança do Sistema** e entre nas definições da **Palavra-passe**. Para este tutorial, selecione as seguintes definições recomendadas:
     
    - Para **Palavra-passe obrigatória para desbloquear os dispositivos móveis**, selecione **Exigir**.
    - Para **Palavras-passe simples**, selecione **Bloquear**.
    - Em **Comprimento mínimo da palavra-passe**, introduza **4**.
    - Para **Tipo de palavra-passe obrigatório**, escolha **Alfanumérico**.
    - Para **Máximo de minutos após o bloqueio de ecrã até ao pedido de palavra-passe**, escolha **Imediatamente**.
    - Para **Expiração da palavra-passe (dias)** , introduza **41**.
    - Para **Número de palavras-passe anteriores para impedir a reutilização**, introduza **5**.
 
    ![Configurar as definições de palavra-passe para a política de conformidade de e-mail](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Selecione **OK** e, em seguida, selecione **OK** novamente.
9. Selecione **Criar**.

## <a name="create-the-conditional-access-policy"></a>Criar a política de acesso condicional
Agora, criaremos uma política de acesso condicional que exige que todas as plataformas de dispositivo sejam registradas no Intune e estejam em conformidade com nossa política de conformidade do Intune antes que possam acessar o Exchange Online. Também vamos exigir a aplicação Outlook para aceder ao e-mail. As políticas de acesso condicional são configuráveis no portal do Azure AD ou no portal do Intune. Uma vez que já estamos no portal do Intune, vamos criar a política aqui.
1. No Intune, selecione**políticas** > de **acesso** > condicional**nova política**.
1. Em **Nome**, introduza **Política de teste para o e-mail do Office 365**. 
3. Em **Atribuições**, selecione **Utilizadores e grupos**. No separador **Incluir**, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.

4. Em **Atribuições**, selecione **Aplicações na Cloud**. Uma vez que queremos proteger o e-mail do Office 365 Exchange Online, vamos selecioná-lo ao seguir estes passos:
     
    1. No separador **Incluir**, escolha **Selecionar aplicações**.
    2. Escolha **Selecionar**. 
    3. Na lista de aplicações, selecione **Office 365 Exchange Online** e, em seguida, escolha **Selecionar**. 
    4. Selecione **Done** (Concluído).
  
    ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.
     
    1. Em **Configurar**, selecione **Sim**.
    2. Na guia **incluir** , selecione **qualquer dispositivo**e, em seguida, selecione **concluído**. 
    3. Selecione **Concluído** novamente.
   
    ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. Em **Atribuições**, selecione **Condições** > **Aplicações do cliente**.
     
    1. Em **Configurar**, selecione **Sim**.
    2. Neste tutorial, selecione **Aplicações móveis e clientes de ambiente de trabalho** e **Clientes de autenticação moderna** (que se refere às aplicações como o Outlook para iOS e o Outlook para Android). Desmarque todas as outras caixas de verificação.
    3. Selecione **Concluído** e, em seguida, selecione **Concluído** novamente.
    
    ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. Em **Controlos de acesso**, selecione **Concessão**. 
     
    1. No painel **Concessão**, selecione **Conceder acesso**.
    2. Selecione **Pedir que o dispositivo seja marcado como conforme**. 
    3. Selecione **Requer aplicação aprovada do cliente**.
    4. Em **Para vários controlos**, selecione **Exigir todos os controlos selecionados**. Esta definição garantirá que ambos os requisitos que selecionou são impostos quando um dispositivo tentar aceder ao e-mail.
    5. Escolha **Selecionar**.
     
    ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. Em **Ativar política**, selecione **Ativar**.
     
    ![Selecionar a aplicação Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Selecione **Criar**.

## <a name="try-it-out"></a>Experimentar
Com as políticas que criou, todos os dispositivos iOS que tentarem iniciar sessão no e-mail do Office 365 terão de se inscrever no Intune e utilizar a aplicação móvel do Outlook para iOS. Para testar este cenário num dispositivo iOS, experimente iniciar sessão no Exchange Online com as credenciais para um utilizador no seu inquilino de teste. Será solicitado a inscrever o dispositivo e a instalar a aplicação móvel do Outlook.
1. Para testar num iPhone, aceda a **Definições** > **Palavras-passe e Contas** > **Adicionar Conta** > **Exchange**.
2. Introduza o endereço de e-mail de um utilizador no inquilino de teste e, em seguida, prima **Seguinte**.
3. Prima **Iniciar Sessão**.
4. Introduza a palavra-passe do utilizador de teste e prima **Iniciar sessão**.
5. É apresentada uma mensagem que indica que o dispositivo tem de ser gerido para aceder ao recurso, juntamente com uma opção para a inscrição. 

## <a name="clean-up-resources"></a>Limpar recursos
Quando já não precisar das políticas de teste, poderá removê-las.
1. Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune.
2. Selecione **Conformidade do Dispositivo** > **Políticas**.
3. Na lista **Nome da Política**, selecione o menu de contexto ( **...** ) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **OK** para confirmar.
4. Selecione **Acesso Condicional** > **Políticas**.
5. Na lista **Nome da Política**, selecione o menu de contexto ( **...** ) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **Sim** para confirmar.

## <a name="next-steps"></a>Passos seguintes 
Neste tutorial, criou políticas que exigem que os dispositivos iOS se inscrevam no Intune e utilizem a aplicação Outlook para aceder ao e-mail do Exchange Online. Para saber mais sobre como usar o Intune com acesso condicional para proteger outros aplicativos e serviços, incluindo clientes do Exchange ActiveSync para o Office 365 Exchange Online, consulte [Configurar o acesso condicional](conditional-access.md).
