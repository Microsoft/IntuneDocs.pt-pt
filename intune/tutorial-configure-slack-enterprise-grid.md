---
title: Tutorial - configurar o Slack para utilizar o Intune para a configuração de aplicações e de EMM
titleSuffix: Microsoft Intune
description: Neste tutorial, configurará Slack para utilizar o Intune para a configuração de EMM e a aplicação.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 06/11/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da6c9b544d86c9c4b09c061c0f1500ed8612a047
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530703"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Tutorial: Configurar o Slack para utilizar o Intune para a configuração de aplicações e de EMM

Slack é uma aplicação de colaboração que pode utilizar com o Microsoft Intune.   

Neste tutorial, irá:
> [!div class="checklist"]
> - Definir o Intune como o fornecedor de gestão de mobilidade empresarial (EMM) na sua grelha de Enterprise do Slack. Poderá limitar o acesso a áreas de trabalho do seu plano de grade para dispositivos geridos pelo Intune.
> - Crie políticas de configuração de aplicação para gerir o Slack para a aplicação EMM no iOS e a aplicação Slack para dispositivos de perfil de trabalho Android.
> - Criar políticas de conformidade para definir as condições Android de dispositivos do Intune e dispositivos iOS têm de cumprir para ser considerado conforme.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:
- Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Subscrição do Intune ([avaliação gratuita](free-trial-sign-up.md))

Também precisará de um [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) plano.

## <a name="configure-your-slack-enterprise-grid-plan"></a>Configurar o seu plano de grade de Enterprise do Slack
Ativar EMM para o seu plano de grade do Slack Enterprise seguindo [instruções do Slack](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) e [ligar o Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) como fornecedor de identidade (IDP) do seu plano de grade.

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune
Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) enquanto Administrador Global ou Administrador de Serviços do Intune. Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Configurar o Slack para EMM em dispositivos iOS
Adicionar a aplicação iOS Slack para EMM ao seu inquilino do Intune e criar uma política de configuração de aplicações para permitir que os utilizadores de iOS de sua organização aceder a Slack com o Intune como um provedor EMM.

### <a name="add-slack-for-emm-to-intune"></a>Adicionar Slack para EMM ao Intune
Adicionar Slack para EMM de como uma aplicação iOS gerida no Intune e atribuir a seus usuários Slack. As aplicações são específicas da plataforma, por isso terá de adicionar uma aplicação do Intune separada para os seus utilizadores Slack em dispositivos Android.
1. No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar**.
2. Em tipo de aplicação, selecione **Store app - iOS**.
3. Selecione **Procurar na App Store**. Introduza o termo de pesquisa "Slack para EMM" e selecione a aplicação.
4. Selecione **informações da aplicação** e configurar todas as alterações como quiser.
5. Selecione **Adicionar**.
6. Na barra de pesquisa, introduza "Slack para EMM" e selecione a aplicação que acabou de adicionar.
7. A partir de gerir, selecione **atribuições**.
8. Selecione **adicionar grupo**. Dependendo do que escolheu seja afetado quando ativou EMM para Slack, em **tipo de atribuição** pode ser útil selecionar:
    -  **Disponível para dispositivos inscritos** se escolheu "Todos os membros (inclusive convidados)" ou
    -  **Disponível com ou sem inscrição** se escolheu "Todos os membros (excluindo convidados)" ou "Opcional".
9. Selecione **grupos incluídos** e em disponibilizar esta aplicação disponível a todos os utilizadores, selecione **Sim**.
10. Clique em **OK**e, em seguida, clique em **OK** novamente.
11. Clique em **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Adicionar uma política de configuração de aplicação para Slack para EMM
Adicione uma política de configuração de aplicação para o Slack para EMM iOS. Políticas de configuração de aplicações para dispositivos geridos são específicas da plataforma, por isso terá de adicionar uma política separada para os seus utilizadores Slack em dispositivos Android.
1. No Intune, selecione **aplicações de cliente** > **políticas de configuração de aplicações** > **adicionar**.
2. No nome, introduza o teste de política de configuração de aplicação Slack.
3. Em tipo de inscrição do dispositivo, selecione **dispositivos geridos**.
4. Em plataforma, selecione **iOS**.
5. Selecione **aplicação associada**.
6. Na barra de pesquisa, introduza "Slack para EMM" e selecione a aplicação.
7. Clique em **OK**e, em seguida, selecione **definições de configuração**. 
    -   Para obter informações sobre chaves de configuração e os respetivos valores, consulte a documentação na guia "Técnico" da [página da web do Slack AppConfig](https://www.appconfig.org/company/slack/).
8. Selecione **OK**e, em seguida, selecione **Add**.
9. Na barra de pesquisa, introduza "teste de política de configuração de aplicação Slack" e selecione a política que acabou de adicionar.
10. A partir de gerir, selecione **atribuições**.
11. Em atribuir para, selecione **todos os utilizadores e todos os dispositivos**.
12. Clique em **Guardar**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Opcional) Criar uma política de conformidade do dispositivo iOS
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade para dispositivos iOS. As políticas de conformidade são específicas da plataforma, por isso terá de criar uma política separada para os seus utilizadores Slack em dispositivos Android.
1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. No nome, introduza "teste de política de conformidade de iOS".
3. Na descrição, insira "teste de política de conformidade de iOS".
4. Em plataforma, selecione **iOS**.
5. Selecione **Estado de Funcionamento dos Dispositivos**. Junto a dispositivos com Jailbreak, selecione **bloco**e, em seguida, selecione **OK**.
6. Selecione **segurança do sistema** e introduza as definições de palavra-passe. Para este tutorial, selecione as seguintes definições recomendadas:
    -   Para exigir uma palavra-passe para desbloquear os dispositivos móveis, selecione **requerem**.
    -   Para palavras-passe simples, selecione **bloco**.
    -   Comprimento mínimo da palavra-passe, introduza 4.
    -   Para o tipo de palavra-passe obrigatório, escolha **alfanumérico**.
    -   Para o máximo de minutos após o bloqueio de ecrã antes de é exigida a palavra-passe, escolha **imediatamente**.
    -   Para a expiração de palavra-passe (dias), introduza 41.
    -   Para o número de palavras-passe anteriores para evitar reutilizar, introduza a 5.
7. Clique em **OK**e, em seguida, selecione **OK** novamente.
8. Clique em **Criar**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Configurar o Slack em dispositivos de perfil de trabalho do Android
Adicionar a aplicação Slack Google Play gerido ao seu inquilino do Intune e criar uma política de configuração de aplicação para ativar a Android aos utilizadores sua organização aceder Slack com o Intune como um provedor EMM.

### <a name="add-slack-to-intune"></a>Adicionar Slack ao Intune
Adicione Slack, enquanto um Google geridos reproduzir a aplicação no Intune e atribuir a seus usuários Slack. As aplicações são específicas da plataforma, por isso terá de adicionar uma aplicação do Intune separada para os seus utilizadores Slack em dispositivos iOS.
1. No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar**.
2. Em tipo de aplicação, selecione **Store aplicação – Google Play gerido**.
3. Selecione **Google Play gerido - aprovar**. Introduza o termo de pesquisa "Slack para EMM" e selecione a aplicação.
4. Selecione **aprovar**.
5. Na barra de pesquisa, introduza "Slack" e selecione a aplicação que acabou de adicionar.
6. A partir de gerir, selecione **atribuições**.
7. Selecione **adicionar grupo**. Dependendo do que escolheu seja afetado quando ativou EMM para Slack, em **tipo de atribuição** pode ser útil selecionar:
    -   **Disponível para dispositivos inscritos** se escolheu "Todos os membros (inclusive convidados)" ou
    -   **Disponível com ou sem inscrição** se escolheu "Todos os membros (excluindo convidados)" ou "Opcional".
8. Selecione grupos incluídas e em disponibilizar esta aplicação para todos os utilizadores selecione **Sim**.
9. Clique em **OK**e, em seguida, clique em **OK** novamente.
10. Clique em **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Adicionar uma política de configuração de aplicação para Slack
Adicione uma política de configuração de aplicação para o Slack. Políticas de configuração de aplicações para dispositivos geridos são específicas da plataforma, por isso terá de adicionar uma política separada para os seus utilizadores Slack em dispositivos iOS.
1. No Intune, selecione **aplicações de cliente** > **políticas de configuração de aplicações** > **adicionar**.
2. No nome, introduza o teste de política de configuração de aplicação Slack.
3. Em tipo de inscrição do dispositivo, selecione **dispositivos geridos**.
4. Em plataforma, selecione **Android**.
5. Selecione **aplicação associada**.
6. Na barra de pesquisa, introduza "Slack" e selecione a aplicação.
7. Selecione **OK**e, em seguida, selecione **definições de configuração**.
    -   Para obter informações sobre chaves de configuração e os respetivos valores, consulte a documentação na guia "Técnico" da [página da web do Slack AppConfig](https://www.appconfig.org/company/slack/).
8. Clique em **OK**e, em seguida, selecione **Add**.
9. Na barra de pesquisa, introduza "teste de política de configuração de aplicação Slack" e selecione a política que acabou de adicionar.
10. A partir de gerir, selecione **atribuições**.
11. Em atribuir para, selecione **todos os utilizadores e todos os dispositivos**.
12. Clique em **Guardar**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Opcional) Criar uma política de conformidade do dispositivo Android
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade para dispositivos Android. As políticas de conformidade são específicas da plataforma, por isso terá de criar uma política separada para os seus utilizadores Slack em dispositivos iOS.
1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. No nome, introduza "teste de política de conformidade do Android".
3. Na descrição, insira "teste de política de conformidade do Android".
4. Em plataforma, selecione **Android Enterprise**.
5. Em tipo de perfil, selecione **perfil de trabalho**.
6. Selecione **Estado de Funcionamento dos Dispositivos**. Junto a dispositivos com raiz, selecione **bloco**e, em seguida, selecione **OK**.
7. Selecione **segurança do sistema** e introduza **definições de palavra-passe**. Para este tutorial, selecione as seguintes definições recomendadas:
    -   Para exigir uma palavra-passe para desbloquear os dispositivos móveis, selecione **requerem**.
    -   Para o tipo de palavra-passe obrigatório, selecione **, pelo menos, de alfanuméricos**.
    -   Comprimento mínimo da palavra-passe, introduza 4.
    -   Para o máximo de minutos após o bloqueio de ecrã antes de é exigida a palavra-passe, escolha **15 minutos**.
    -   Para a expiração de palavra-passe (dias), introduza 41.
    -   Para o número de palavras-passe anteriores para evitar reutilizar, introduza a 5.
8. Clique em **OK**e, em seguida, clique em **OK** novamente.
9. Clique em **Criar**.

## <a name="launch-slack"></a>Inicie o Slack

Com as políticas que acabou de criar, qualquer iOS ou Android, dispositivos de perfil de trabalho que tentarem iniciar sessão a uma das suas áreas de trabalho terá de ser inscritos no Intune. Para testar este cenário, tente iniciar o Slack para EMM num dispositivo de iOS inscritos no Intune ou Slack lançamento num dispositivo de perfil de trabalho Android inscritos no Intune. 

## <a name="next-steps"></a>Passos Seguintes

Neste tutorial:
- Definir o Intune como o fornecedor de gestão de mobilidade empresarial (EMM) na sua grelha de Enterprise do Slack. 
- Criar políticas de configuração de aplicação para gerir o Slack para a aplicação EMM no iOS e a aplicação Slack para dispositivos de perfil de trabalho Android.
- Que dispositivos do Intune criou as políticas de conformidade para definir as condições de Android e dispositivos iOS têm de cumprir para ser considerado conforme.

Para saber mais sobre as políticas de configuração de aplicações, veja [políticas de configuração de aplicações do Microsoft Intune](app-configuration-policies-overview.md). Para saber mais sobre as políticas de conformidade de dispositivos, veja [definir regras em dispositivos para permitir o acesso a recursos na sua organização utilizar o Intune](device-compliance-get-started.md).