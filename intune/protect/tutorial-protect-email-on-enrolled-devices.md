---
title: Tutorial - Protect Exchange Online email on managed devices
titleSuffix: Microsoft Intune
description: Learn to secure Exchange Online with iOS Intune compliance policies and Azure AD Conditional Access to require managed devices and the Outlook app.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9deee0dca675d7fd95445131ed98ea195972c6ac
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409857"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Tutorial – Proteger o e-mail do Exchange Online em dispositivos geridos

Learn about using device compliance policies with Conditional Access to make sure that iOS devices can access Exchange Online email only if they're managed by Intune and using an approved email app.

Neste tutorial, ficará a saber como:

> [!div class="checklist"]
> * Criar uma política de conformidade de dispositivos iOS do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme.
> * Create an Azure Active Directory (Azure AD) Conditional Access policy that requires iOS devices to enroll in Intune, comply with Intune policies, and use the approved Outlook mobile app to access Exchange Online email.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:

- Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))

- Subscrição do Office 365 Empresas com o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

Antes de começar, crie um perfil de dispositivos de teste para dispositivos iOS ao seguir os passos em [Início Rápido: criar um perfil de dispositivo de e-mail para iOS](../configuration/quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) as a [Global administrator](../fundamentals/users-add.md#types-of-administrators) or an Intune [Service administrator](../fundamentals/users-add.md#types-of-administrators). Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-the-ios-device-compliance-policy"></a>Criar a política de conformidade dos dispositivos iOS

Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade para dispositivos iOS. As políticas de conformidade são específicas da plataforma, por isso, precisa de uma política de conformidade separada para cada plataforma de dispositivo que queira avaliar.

1. In Intune, select **Devices** > **Compliance policies** > **Create policy**.

2. For **Name**, enter **iOS compliance policy test**.

3. For **Description**, enter **iOS compliance policy test**.

4. For **Platform**, select **iOS/iPadOS**.

5. Selecione **Definições** > **E-mail**.

   1. Junto a **Exigir que os dispositivos móveis tenham um perfil de e-mail gerido**, selecione **Exigir**.

   2. Selecione **OK**.

   ![Definir a política de conformidade de e-mail para exigir um perfil de e-mail gerido](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)

6. Selecione **Estado de Funcionamento dos Dispositivos**. Junto a **Dispositivos com jailbreak**, selecione **Bloquear** e, em seguida, selecione **OK**.

7. Selecione **Segurança do Sistema** e entre nas definições da **Palavra-passe**. Para este tutorial, selecione as seguintes definições recomendadas:

   - Para **Palavra-passe obrigatória para desbloquear os dispositivos móveis**, selecione **Exigir**.

   - Para **Palavras-passe simples**, selecione **Bloquear**.

   - Em **Comprimento mínimo da palavra-passe**, introduza **4**.

     > [!TIP]
     > Default values that are grayed out and italicized are only recommendations. You must replace values that are recommendations to configure a setting.

   - Para **Tipo de palavra-passe obrigatório**, escolha **Alfanumérico**.

   - Para **Máximo de minutos após o bloqueio de ecrã até ao pedido de palavra-passe**, escolha **Imediatamente**.

   - Para **Expiração da palavra-passe (dias)** , introduza **41**.

   - Para **Número de palavras-passe anteriores para impedir a reutilização**, introduza **5**.
 
   ![Configurar as definições de palavra-passe para a política de conformidade de e-mail](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Selecione **OK** e, em seguida, selecione **OK** novamente.

9. Selecione **Criar**.

## <a name="create-the-conditional-access-policy"></a>Create the Conditional Access policy

Now we’ll create a Conditional Access policy that requires all device platforms to enroll in Intune and comply with our Intune compliance policy before they can access Exchange Online. Também vamos exigir a aplicação Outlook para aceder ao e-mail. Conditional Access policies are configurable in either the Azure AD portal or the Intune portal. Uma vez que já estamos no portal do Intune, vamos criar a política aqui.

1. In Intune, select **Endpoint security** > **Conditional Access** > **New policy**.

2. For **Name**, enter **Test policy for Office 365 email**.

3. Em **Atribuições**, selecione **Utilizadores e grupos**. No separador **Incluir**, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.

4. Under **Assignments**, select **Cloud apps or actions**. Uma vez que queremos proteger o e-mail do Office 365 Exchange Online, vamos selecioná-lo ao seguir estes passos:

   1. No separador **Incluir**, escolha **Selecionar aplicações**.

   2. Clique em **Selecionar**. 

   3. Na lista de aplicações, selecione **Office 365 Exchange Online** e, em seguida, escolha **Selecionar**. 

   4. Selecione **Concluído**.
  
   ![Selecionar a aplicação Office 365 Exchange Online](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.

   1. Em **Configurar**, selecione **Sim**.

   2. On the **Include** tab, select **Any device**, and then select **Done**. 

   3. Selecione **Concluído** novamente.

   ![Include any device](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. Em **Atribuições**, selecione **Condições** > **Aplicações do cliente**.

   1. Em **Configurar**, selecione **Sim**.

   2. Neste tutorial, selecione **Aplicações móveis e clientes de ambiente de trabalho** e **Clientes de autenticação moderna** (que se refere às aplicações como o Outlook para iOS e o Outlook para Android). Desmarque todas as outras caixas de verificação.

   3. Selecione **Concluído** e, em seguida, selecione **Concluído** novamente.

   ![Select apps and clients](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. Em **Controlos de acesso**, selecione **Concessão**.

   1. No painel **Concessão**, selecione **Conceder acesso**.

   2. Selecione **Pedir que o dispositivo seja marcado como conforme**.

   3. Selecione **Requer aplicação aprovada do cliente**.

   4. Em **Para vários controlos**, selecione **Exigir todos os controlos selecionados**. Esta definição garantirá que ambos os requisitos que selecionou são impostos quando um dispositivo tentar aceder ao e-mail.

   5. Clique em **Selecionar**.

   ![Select conrols](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. Em **Ativar política**, selecione **Ativar**.

   ![Enable policy](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

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
1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) as a Global Administrator or an Intune Service Administrator.

2. Select **Devices** > **Compliance policies**.

3. Na lista **Nome da Política**, selecione o menu de contexto ( **...** ) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **OK** para confirmar.

4. Select **Endpoint security** > **Conditional access**.

5. Na lista **Nome da Política**, selecione o menu de contexto ( **...** ) para a sua política de teste e, em seguida, selecione **Eliminar**. Select **Yes** to confirm.

## <a name="next-steps"></a>Próximos passos

Neste tutorial, criou políticas que exigem que os dispositivos iOS se inscrevam no Intune e utilizem a aplicação Outlook para aceder ao e-mail do Exchange Online. To learn about using Intune with Conditional Access to protect other apps and services, including Exchange ActiveSync clients for Office 365 Exchange Online, see [Set up Conditional Access](conditional-access.md).
