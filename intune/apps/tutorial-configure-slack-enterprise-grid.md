---
title: Tutorial - Configure Slack para usar Intune para emm e configuração de app
titleSuffix: Microsoft Intune
description: Neste tutorial, irá configurar o Slack para utilizar o Intune para a configuração de EMM e app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f5045e78eaca19e5a78468c7c4b6698e4e1a5019
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511553"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Tutorial: Configure A folga para usar Intune para configuração de EMM e app

Slack é uma aplicação de colaboração que pode usar com o Microsoft Intune.   

Neste tutorial, irá:
> [!div class="checklist"]
> - Defina intune como o fornecedor de Gestão da Mobilidade Empresarial (EMM) na sua Rede Empresarial Slack. Poderá limitar o acesso aos espaços de trabalho do seu plano Grid para dispositivos geridos por Intune.
> - Crie políticas de configuração de aplicações para gerir a aplicação Slack para EMM no iOS/iPadOS e na aplicação Slack para dispositivos de perfil de trabalho Android.
> - Crie políticas de conformidade de dispositivos Intune para definir as condições que os dispositivos Android e iOS/iPadOS devem cumprir para serem considerados conformes.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:
- Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Subscrição inoportuna[(teste gratuito)](../fundamentals/free-trial-sign-up.md)

Também vai precisar de um plano [slack Enterprise Grid.](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-)

## <a name="configure-your-slack-enterprise-grid-plan"></a>Configure o seu plano de grelha de empresa slack
Ligue o EMM para o seu plano Slack Enterprise Grid seguindo [as instruções da Slack](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) e ligue o [Azure Ative Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) como fornecedor de identidade do seu plano grid (IDP).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune
Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) como administrador global ou administrador de serviço intune. Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Configurar a folga para emm em dispositivos iOS
Adicione a aplicação iOS/iPadOS Slack for EMM ao seu inquilino Intune e crie uma política de configuração de aplicações para permitir aos utilizadores de iOS/iPadOS das suas organizações aceder em Slack com Intune como fornecedor em MEm.

### <a name="add-slack-for-emm-to-intune"></a>Adicione folga para emm ao Intune
Adicione slack para EMM como uma aplicação gerida para iOS/iPadOS em Intune e atribua os seus utilizadores Slack. As aplicações são específicas da plataforma, pelo que precisa de adicionar uma aplicação Intune separada para os seus utilizadores Slack em dispositivos Android.
1. No centro de administração, selecione **Apps** > **Todas as aplicações** > **Adicionar**.
2. No **tipo app,** selecione a aplicação da loja **iOS.**
3. Selecione **Procurar na App Store**. Introduza o termo de pesquisa "Slack for EMM" e selecione a aplicação. Clique em **Selecionar** no painel **search the App Store.**
4. Selecione **informações da App** e configure quaisquer alterações conforme entender. Selecione **OK** para definir as informações da sua aplicação.
5. Clique em **Adicionar**.
6. Selecione **Atribuições**.
7. Clique em **Adicionar grupo**. Dependendo de quem escolheu para ser afetado quando ligou o EMM para Slack, ao abrigo do **tipo de Atribuição** poderá desejar selecionar:
    - **Disponível para dispositivos matriculados** se escolher "Todos os membros (incluindo convidados)" OU
    - **Disponível com ou sem inscrição** se escolher "Todos os membros (excluindo os hóspedes)" ou "Opcional".
8. Selecione **Grupos Incluídos** e, em **baixo, disponibilize esta aplicação a todos os utilizadores** selecione **Sim**.
9. Clique **ok**, e depois clique **OK** novamente para adicionar o grupo.
10. Clique em **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Adicione uma política de configuração de aplicativos para Slack para EMM
Adicione uma política de configuração de aplicativos para o Slack para emM iOS/iPadOS. As políticas de configuração de aplicações para dispositivos geridos são específicas da plataforma, pelo que é necessário adicionar uma política separada para os seus utilizadores Slack em dispositivos Android.
1. No centro de administração, selecione **Apps** > políticas de **configuração** de apps > **adicionar** > **dispositivos geridos**.
2. Em Nome, introduza o 'Teste de política de configuração da aplicação Slack'.
3. No tipo de inscrição do Dispositivo, confirme que os **dispositivos geridos** estão definidos.
4. Em Plataforma, selecione **iOS**.
5. Selecione **aplicação Associada**.
6. Na barra de pesquisa, introduza "Slack for EMM" e selecione a aplicação.
7. Clique **em OK**, e, em seguida, selecione as **definições de configuração**. 
8. Selecione **OK**, e, em seguida, selecione **Adicionar**.
9. Na barra de pesquisa, introduza "Slack app configuration policy test" e selecione a política que acabou de adicionar.
10. A partir de Gerir, selecione **Atribuições**.
11. Em designado por, selecione **Todos os Utilizadores + Todos os Dispositivos**.
12. Clique em **Guardar**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Opcional) Criar uma política de conformidade com dispositivos iOS
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade de dispositivos para dispositivos iOS/iPadOS. As políticas de conformidade são específicas da plataforma, pelo que precisa de criar uma política separada para os seus utilizadores Slack em dispositivos Android.
1. No centro de administração, selecione **A conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Em Nome, insira "teste de política de conformidade iOS".
3. Em Descrição, insira o "teste de política de conformidade iOS".
4. Em Plataforma, selecione **iOS**.
5. Selecione **Estado de Funcionamento dos Dispositivos**. Ao lado de dispositivos Jailbroken, selecione **Block**, e, em seguida, selecione **OK**.
6. Selecione **A Segurança do Sistema** e introduza as definições de palavra-passe. Para este tutorial, selecione as seguintes definições recomendadas:
    - Para exigir uma palavra-passe para desbloquear dispositivos móveis, selecione **Exigir**.
    - Para palavras-passe simples, selecione **Bloquear**.
    - Para o comprimento mínimo da palavra-passe, introduza 4.
    - Para o tipo de palavra-passe exigido, escolha **Alphanumérico**.
    - Para os minutos máximos após o bloqueio do ecrã antes da palavra-passe ser necessária, escolha **imediatamente**.
    - Para a expiração da palavra-passe (dias), insira 41.
    - Para o número de senhas anteriores para evitar a reutilização, introduza 5.
7. Clique **ok**e, em seguida, selecione **OK** novamente.
8. Clique em **Criar**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Configurar slack em dispositivos de perfil de trabalho Android
Adicione a aplicação Slack Managed Google Play ao seu inquilino Intune e crie uma política de configuração de aplicações para permitir aos utilizadores Android das suas organizações aceder em Slack com Intune como fornecedor de EMM.

### <a name="add-slack-to-intune"></a>Adicione folga ao Intune
Adicione Slack como uma aplicação de jogo gerida da Google em Intune e atribua os seus utilizadores Slack. As aplicações são específicas da plataforma, pelo que precisa de adicionar uma aplicação Intune separada para os seus utilizadores Slack em dispositivos iOS/iPadOS.
1. Intune, selecione **Apps** > **Todas as aplicações** > **Add**.
2. No tipo de App, selecione **app Store – Managed Google Play**.
3. Selecione **Managed Google Play - Approve**. Introduza o termo de pesquisa "Slack for EMM" e selecione a aplicação.
4. Selecione **Aprovar**.
5. Na barra de pesquisa, introduza "Slack" e selecione a aplicação que acabou de adicionar.
6. A partir de Gerir, selecione **Atribuições**.
7. **Selecione Adicionar grupo**. Dependendo de quem escolheu para ser afetado quando ligou o EMM para Slack, ao abrigo do **tipo de Atribuição** poderá desejar selecionar:
    - **Disponível para dispositivos matriculados** se escolher "Todos os membros (incluindo convidados)" OU
    - **Disponível com ou sem inscrição** se escolher "Todos os membros (excluindo os hóspedes)" ou "Opcional".
8. Selecione Grupos Incluídos e, em baixo, disponibilize esta aplicação a todos os utilizadores selecione **Sim**.
9. Clique **OK**e, em seguida, clique **OK** novamente.
10. Clique em **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Adicione uma política de configuração de aplicativos para Slack
Adicione uma política de configuração de aplicativos para Slack. As políticas de configuração de aplicações para dispositivos geridos são específicas da plataforma, pelo que é necessário adicionar uma política separada para os seus utilizadores Slack em dispositivos iOS/iPadOS.
1. Intune, selecione **Apps** > políticas de **configuração** de apps > **adicionar**.
2. Em Nome, introduza o teste de configuração da aplicação Slack.
3. No tipo de inscrição do Dispositivo, selecione **dispositivos geridos**.
4. Na Plataforma, selecione **Android.**
5. Selecione **aplicação Associada**.
6. Na barra de pesquisa, introduza "Slack" e selecione a aplicação.
7. Selecione **OK**, e, em seguida, selecione **as definições**de configuração .
    - Para obter informações sobre as chaves de configuração e os seus valores, consulte a documentação no separador "Técnico" [da página web appConfig da Slack](https://www.appconfig.org/company/slack/).
8. Clique **em OK,** e depois selecione **Adicionar**.
9. Na barra de pesquisa, introduza "Slack app configuration policy test" e selecione a política que acabou de adicionar.
10. A partir de Gerir, selecione **Atribuições**.
11. Em designado por, selecione **Todos os Utilizadores + Todos os Dispositivos**.
12. Clique em **Guardar**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Opcional) Criar uma política de conformidade com dispositivos Android
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade de dispositivos Android. As políticas de conformidade são específicas da plataforma, pelo que é necessário criar uma política separada para os seus utilizadores Slack em dispositivos iOS/iPadOS.
1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Em Nome, introduza "Teste de política de conformidade Android".
3. Em Descrição, insira "Teste de política de conformidade Android".
4. Em Platform, selecione **Android Enterprise**.
5. No tipo de perfil, selecione **Perfil de trabalho**.
6. Selecione **Estado de Funcionamento dos Dispositivos**. Ao lado dos dispositivos Enraizados, selecione **Bloco**, e, em seguida, selecione **OK**.
7. Selecione **A Segurança do Sistema** e introduza as **definições de palavra-passe**. Para este tutorial, selecione as seguintes definições recomendadas:
    - Para exigir uma palavra-passe para desbloquear dispositivos móveis, selecione **Exigir**.
    - Para o tipo de palavra-passe necessário, selecione **Pelo menos alfanumérico**.
    - Para o comprimento mínimo da palavra-passe, introduza 4.
    - Para os minutos máximos após o bloqueio do ecrã antes da palavra-passe ser necessária, escolha **15 Minutos**.
    - Para a expiração da palavra-passe (dias), insira 41.
    - Para o número de senhas anteriores para evitar a reutilização, introduza 5.
8. Clique **OK**e, em seguida, clique **OK** novamente.
9. Clique em **Criar**.

## <a name="launch-slack"></a>Lançar Folga

Com as políticas que acaba de criar, quaisquer dispositivos de perfil de trabalho iOS/iPadOS ou Android que tentem iniciar sessão num dos seus espaços de trabalho terão de ser inscritos intune. Para testar este cenário, tente lançar Slack para EMM num dispositivo intune iOS/iPadOS ou lançar Slack num dispositivo de perfil de trabalho Android matriculado no Intune. 

## <a name="next-steps"></a>Próximos passos

Neste tutorial:
- Definiu o Intune como o fornecedor de Gestão de Mobilidade Empresarial (EMM) na sua Rede Empresarial Slack. 
- Criou políticas de configuração de aplicações para gerir a aplicação Slack for EMM no iOS/iPadOS e na aplicação Slack para dispositivos de perfil de trabalho Android.
- Criou políticas de conformidade com dispositivos Intune para definir as condições que os dispositivos Android e iOS/iPadOS devem cumprir para serem considerados conformes.

Para saber mais sobre as políticas de configuração de apps, consulte as políticas de configuração de [Aplicativos para o Microsoft Intune](app-configuration-policies-overview.md). Para saber mais sobre as políticas de conformidade do dispositivo, consulte [as regras definidas sobre dispositivos para permitir o acesso aos recursos na sua organização utilizando o Intune](../protect/device-compliance-get-started.md).
