---
title: Tutorial - Proteja o e-mail online de troca de dispositivos geridos
titleSuffix: Microsoft Intune
description: Aprenda a garantir o Exchange Online com as políticas de conformidade do iOS Intune e o Azure AD Conditional Access para exigir dispositivos geridos e a aplicação Outlook.
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
ms.openlocfilehash: c134eb1fc413a32f2a27034d8c3a993f18f8a9c9
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576265"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Tutorial – Proteger o e-mail do Exchange Online em dispositivos geridos

Saiba utilizar as políticas de conformidade do dispositivo com acesso condicional para garantir que os dispositivos iOS só podem aceder ao email do Exchange Online se forem geridos pela Intune e utilizarem uma aplicação de email aprovada.

Neste tutorial, ficará a saber como:

> [!div class="checklist"]
> * Criar uma política de conformidade de dispositivos iOS do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme.
> * Crie uma política de Acesso Condicional do Diretório Ativo Azure (Azure AD) que exija que os dispositivos iOS se inscrevam no Intune, cumpram as políticas intune e utilizem a aplicação móvel do Outlook aprovada para aceder ao email Exchange Online.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos

Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:

- Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))

- Subscrição do Office 365 Empresas com o Exchange ([avaliação gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

Antes de começar, crie um perfil de dispositivo de teste para dispositivos iOS seguindo os passos em Quickstart: Crie um perfil de dispositivo de [e-mail para iOS/iPadOS](../configuration/quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) como [administrador global](../fundamentals/users-add.md#types-of-administrators) ou administrador de [serviço](../fundamentals/users-add.md#types-of-administrators)intune . Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-the-ios-device-compliance-policy"></a>Criar a política de conformidade dos dispositivos iOS

Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade para dispositivos iOS. As políticas de conformidade são específicas da plataforma, por isso, precisa de uma política de conformidade separada para cada plataforma de dispositivo que queira avaliar.

1. Intune, selecione **Dispositivos** > Políticas de **Conformidade** > **Criar a política**.

2. Para **Nome,** insira o teste de política de **conformidade do iOS**.

3. Para **descrição,** insira o teste de política de **conformidade do iOS**.

4. Para **plataforma**, selecione **iOS/iPadOS**.

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
     > Valores padrão que são acinzentados e itálico são apenas recomendações. Deve substituir valores que são recomendações para configurar uma definição.

   - Para **Tipo de palavra-passe obrigatório**, escolha **Alfanumérico**.

   - Para **Máximo de minutos após o bloqueio de ecrã até ao pedido de palavra-passe**, escolha **Imediatamente**.

   - Para **Expiração da palavra-passe (dias)**, introduza **41**.

   - Para **Número de palavras-passe anteriores para impedir a reutilização**, introduza **5**.
 
   ![Configurar as definições de palavra-passe para a política de conformidade de e-mail](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Selecione **OK** e, em seguida, selecione **OK** novamente.

9. Selecione **Criar**.

## <a name="create-the-conditional-access-policy"></a>Criar a política de acesso condicional

Agora vamos criar uma política de Acesso Condicional que requer que todas as plataformas de dispositivos se inscrevam em Intune e cumpram a nossa política de conformidade intune antes de poderem aceder ao Exchange Online. Também vamos exigir a aplicação Outlook para aceder ao e-mail. As políticas de Acesso Condicional são configuráveis no portal Azure AD ou no portal Intune. Uma vez que já estamos no portal do Intune, vamos criar a política aqui.

1. Intune, selecione **Endpoint security** > **Acesso Condicional** > **Nova política**.

2. Para **Nome**, insira **a política de teste para o Office 365 e-mail**.

3. Em **Atribuições**, selecione **Utilizadores e grupos**. No separador **Incluir**, selecione **Todos os utilizadores** e, em seguida, selecione **Concluído**.

4. Em **Atribuições,** selecione **aplicações ou ações cloud**. Uma vez que queremos proteger o e-mail do Office 365 Exchange Online, vamos selecioná-lo ao seguir estes passos:

   1. No separador **Incluir**, escolha **Selecionar aplicações**.

   2. Clique em **Selecionar**. 

   3. Na lista de aplicações, selecione **Office 365 Exchange Online** e, em seguida, escolha **Selecionar**. 

   4. Selecione **Concluído**.
  
   ![Selecionar a aplicação Office 365 Exchange Online](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. Em **Atribuições**, selecione **Condições** > **Plataformas de dispositivos**.

   1. Em **Configurar**, selecione **Sim**.

   2. No separador **Incluir,** selecione **Qualquer dispositivo**, e, em seguida, selecione **Done**. 

   3. Selecione **Concluído** novamente.

   ![Incluir qualquer dispositivo](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. Em **Atribuições**, selecione **Condições** > **Aplicações do cliente**.

   1. Em **Configurar**, selecione **Sim**.

   2. Neste tutorial, selecione **Aplicações móveis e clientes de ambiente de trabalho** e **Clientes de autenticação moderna** (que se refere às aplicações como o Outlook para iOS e o Outlook para Android). Desmarque todas as outras caixas de verificação.

   3. Selecione **Concluído** e, em seguida, selecione **Concluído** novamente.

   ![Selecione apps e clientes](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. Em **Controlos de acesso**, selecione **Concessão**.

   1. No painel **Concessão**, selecione **Conceder acesso**.

   2. Selecione **Pedir que o dispositivo seja marcado como conforme**.

   3. Selecione **Requer aplicação aprovada do cliente**.

   4. Em **Para vários controlos**, selecione **Exigir todos os controlos selecionados**. Esta definição garantirá que ambos os requisitos que selecionou são impostos quando um dispositivo tentar aceder ao e-mail.

   5. Clique em **Selecionar**.

   ![Selecione controlos](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. Em **Ativar política**, selecione **Ativar**.

   ![Ativar política](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Selecione **Criar**.

## <a name="try-it-out"></a>Experimentar

Com as políticas que criou, qualquer dispositivo iOS que tente iniciar sessão no Office 365 terá de se inscrever no Intune e utilizar a aplicação móvel Outlook para iOS/iPadOS. Para testar este cenário num dispositivo iOS, experimente iniciar sessão no Exchange Online com as credenciais para um utilizador no seu inquilino de teste. Será solicitado a inscrever o dispositivo e a instalar a aplicação móvel do Outlook.

1. Para testar num iPhone, aceda a **Definições** > **Palavras-passe e Contas** > **Adicionar Conta** > **Exchange**.

2. Introduza o endereço de e-mail de um utilizador no inquilino de teste e, em seguida, prima **Seguinte**.

3. Prima **Iniciar Sessão**.

4. Introduza a palavra-passe do utilizador de teste e prima **Iniciar sessão**.

5. É apresentada uma mensagem que indica que o dispositivo tem de ser gerido para aceder ao recurso, juntamente com uma opção para a inscrição.

## <a name="clean-up-resources"></a>Limpar recursos

Quando já não precisar das políticas de teste, poderá removê-las.
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) como administrador global ou administrador de serviço intune.

2. Selecione **Dispositivos** > políticas de **conformidade**.

3. Na lista **Nome da Política**, selecione o menu de contexto (**...**) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **OK** para confirmar.

4. Selecione **segurança endpoint** > **acesso condicional**.

5. Na lista **Nome da Política**, selecione o menu de contexto (**...**) para a sua política de teste e, em seguida, selecione **Eliminar**. Selecione **Sim** para confirmar.

## <a name="next-steps"></a>Próximos passos

Neste tutorial, criou políticas que exigem que os dispositivos iOS se inscrevam no Intune e utilizem a aplicação Outlook para aceder ao e-mail do Exchange Online. Para aprender sobre a utilização do Intune com acesso condicional para proteger outras aplicações e serviços, incluindo clientes Exchange ActiveSync para o Office 365 Exchange Online, consulte [Configurar o Acesso Condicional](conditional-access.md).
