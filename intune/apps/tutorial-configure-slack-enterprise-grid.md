---
title: Tutorial-configurar a margem de atraso para usar o Intune para EMM e a configuração de aplicativo
titleSuffix: Microsoft Intune
description: Neste tutorial, você configurará a margem de atraso para usar o Intune para EMM e a configuração do aplicativo.
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
ms.openlocfilehash: a3b01c1444b44e3f5c66fc129f78f321c9c9f5aa
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563404"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Tutorial: configurar a margem de atraso para usar o Intune para EMM e a configuração de aplicativo

A margem de atraso é um aplicativo de colaboração que você pode usar com Microsoft Intune.   

Neste tutorial, você vai:
> [!div class="checklist"]
> - Defina o Intune como o provedor de gerenciamento de mobilidade empresarial (EMM) em sua grade empresarial de margem de atraso. Você poderá limitar o acesso aos espaços de trabalho do seu plano de grade para dispositivos gerenciados do Intune.
> - Crie políticas de configuração de aplicativo para gerenciar a margem de atraso do aplicativo EMM no iOS e o aplicativo de margem de atraso para dispositivos de perfil de trabalho do Android.
> - Crie políticas de conformidade do dispositivo do Intune para definir as condições que os dispositivos Android e iOS devem atender para serem considerados em conformidade.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Precisará de um inquilino de teste com as seguintes subscrições para este tutorial:
- Azure Active Directory Premium ([avaliação gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Assinatura do Intune ([avaliação gratuita](../fundamentals/free-trial-sign-up.md))

Você também precisará de um plano de [grade empresarial de margem de atraso](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) .

## <a name="configure-your-slack-enterprise-grid-plan"></a>Configurar seu plano de grade empresarial de margem de atraso
Ative o EMM para seu plano de grade empresarial de margem de atraso seguindo [as instruções da margem de atraso](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) e [Conecte Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) como o IDP (provedor de identidade do seu plano de grade).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune
Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) enquanto Administrador Global ou Administrador de Serviços do Intune. Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Configurar a margem de atraso do EMM em dispositivos iOS
Adicione a margem de atraso do aplicativo iOS para EMM ao seu locatário do Intune e crie uma política de configuração de aplicativo para permitir que os usuários do iOS de sua organização acessem a margem de atraso com o Intune como um provedor do EMM.

### <a name="add-slack-for-emm-to-intune"></a>Adicionar margem de atraso para EMM no Intune
Adicione a margem de atraso do EMM como um aplicativo iOS gerenciado no Intune e atribua seus usuários de margem de atraso. Os aplicativos são específicos da plataforma, portanto, você precisa adicionar um aplicativo do Intune separado para seus usuários de margem de atraso em dispositivos Android.
1. No Intune, selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
2. Em tipo de aplicativo, selecione **Store app-IOS**.
3. Selecione **Procurar na App Store**. Insira o termo de pesquisa "margem de atraso para EMM" e selecione o aplicativo.
4. Selecione **informações do aplicativo** e configure as alterações como desejar.
5. Selecione **Adicionar**.
6. Na barra de pesquisa, insira "margem de atraso para EMM" e selecione o aplicativo que você acabou de adicionar.
7. Em gerenciar, selecione **atribuições**.
8. Selecione **Adicionar grupo**. Dependendo de quem você optou por ser afetado ao ativar o EMM para a margem de atraso, em **tipo de atribuição** , talvez você queira selecionar:
    - **Disponível para dispositivos registrados** se você escolher "todos os membros (incluindo convidados)" ou
    - **Disponível com ou sem registro** se você escolher "todos os membros (exceto convidados)" ou "opcional".
9. Selecione **grupos incluídos** e, em tornar este aplicativo disponível para todos os usuários, selecione **Sim**.
10. Clique em **OK**e em **OK** novamente.
11. Clique em **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Adicionar uma política de configuração de aplicativo para a margem de atraso do EMM
Adicione uma política de configuração de aplicativo para a margem de atraso do EMM iOS. As políticas de configuração de aplicativo para dispositivos gerenciados são específicas da plataforma, portanto, você precisa adicionar uma política separada para seus usuários de margem de atraso em dispositivos Android.
1. No Intune, selecione **aplicativos** > **políticas de configuração de aplicativo** > **Adicionar**.
2. Em nome, digite margem de atraso configuração do aplicativo teste de política.
3. Em tipo de registro do dispositivo, selecione **dispositivos gerenciados**.
4. Em plataforma, selecione **Ios**.
5. Selecione **aplicativo associado**.
6. Na barra de pesquisa, insira "margem de atraso para EMM" e selecione o aplicativo.
7. Clique em **OK**e, em seguida, selecione **definições de configuração**. 
8. Selecione **OK**e, em seguida, selecione **Adicionar**.
9. Na barra de pesquisa, insira "teste de política de configuração de aplicativo de margem de atraso" e selecione a política que você acabou de adicionar.
10. Em gerenciar, selecione **atribuições**.
11. Em atribuir a, selecione **todos os usuários + todos os dispositivos**.
12. Clique em **Guardar**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>Adicional Criar uma política de conformidade do dispositivo iOS
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, vamos criar uma política de conformidade para dispositivos iOS. As políticas de conformidade são específicas da plataforma, portanto, você precisa criar uma política separada para seus usuários de margem de atraso em dispositivos Android.
1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Em nome, insira "teste de política de conformidade do iOS".
3. Em descrição, insira "teste de política de conformidade do iOS".
4. Em plataforma, selecione **Ios**.
5. Selecione **Estado de Funcionamento dos Dispositivos**. Ao lado de dispositivos com jailbreak, selecione **Bloquear**e, em seguida, selecione **OK**.
6. Selecione **segurança do sistema** e insira as configurações de senha. Para este tutorial, selecione as seguintes definições recomendadas:
    - Para exigir uma senha para desbloquear dispositivos móveis, selecione **exigir**.
    - Para senhas simples, selecione **Bloquear**.
    - Para comprimento mínimo da senha, digite 4.
    - Para tipo de senha necessária, escolha **alfanumérico**.
    - Para máximo de minutos após o bloqueio de tela antes que a senha seja necessária, escolha **imediatamente**.
    - Para expiração da senha (dias), digite 41.
    - Para o número de senhas anteriores para evitar a reutilização, insira 5.
7. Clique em **OK**e selecione **OK** novamente.
8. Clique em **Criar**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Configurar a margem de atraso em dispositivos de perfil de trabalho do Android
Adicione a margem de atraso gerenciada Google Play aplicativo ao seu locatário do Intune e crie uma política de configuração de aplicativo para permitir que os usuários do Android da sua organização acessem a margem de atraso com o Intune como um provedor do EMM.

### <a name="add-slack-to-intune"></a>Adicionar margem de atraso ao Intune
Adicione a margem de atraso como um aplicativo gerenciado do Google Play no Intune e atribua seus usuários de margem de atraso. Os aplicativos são específicos da plataforma, portanto, você precisa adicionar um aplicativo do Intune separado para seus usuários de margem de atraso em dispositivos iOS.
1. No Intune, selecione **aplicativos** > **todos os aplicativos** > **Adicionar**.
2. Em tipo de aplicativo, selecione **armazenar aplicativo – Google Play gerenciado**.
3. Selecione **Google Play gerenciado-aprovar**. Insira o termo de pesquisa "margem de atraso para EMM" e selecione o aplicativo.
4. Selecione **aprovar**.
5. Na barra de pesquisa, insira "margem de atraso" e selecione o aplicativo que você acabou de adicionar.
6. Em gerenciar, selecione **atribuições**.
7. Selecione **Adicionar grupo**. Dependendo de quem você optou por ser afetado ao ativar o EMM para a margem de atraso, em **tipo de atribuição** , talvez você queira selecionar:
    - **Disponível para dispositivos registrados** se você escolher "todos os membros (incluindo convidados)" ou
    - **Disponível com ou sem registro** se você escolher "todos os membros (exceto convidados)" ou "opcional".
8. Selecione grupos incluídos e, em tornar este aplicativo disponível para todos os usuários, selecione **Sim**.
9. Clique em **OK**e em **OK** novamente.
10. Clique em **Guardar**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Adicionar uma política de configuração de aplicativo para a margem de atraso
Adicione uma política de configuração de aplicativo para a margem de atraso. As políticas de configuração de aplicativo para dispositivos gerenciados são específicas da plataforma, portanto, você precisa adicionar uma política separada para seus usuários de margem de atraso em dispositivos iOS.
1. No Intune, selecione **aplicativos** > **políticas de configuração de aplicativo** > **Adicionar**.
2. Em nome, digite margem de atraso configuração do aplicativo teste de política.
3. Em tipo de registro do dispositivo, selecione **dispositivos gerenciados**.
4. Em plataforma, selecione **Android**.
5. Selecione **aplicativo associado**.
6. Na barra de pesquisa, insira "margem de atraso" e selecione o aplicativo.
7. Selecione **OK**e, em seguida, selecione **definições de configuração**.
    - Para obter informações sobre chaves de configuração e seus valores, consulte a documentação na guia "técnico" da [página da Web do AppConfig da margem de atraso](https://www.appconfig.org/company/slack/).
8. Clique em **OK**e, em seguida, selecione **Adicionar**.
9. Na barra de pesquisa, insira "teste de política de configuração de aplicativo de margem de atraso" e selecione a política que você acabou de adicionar.
10. Em gerenciar, selecione **atribuições**.
11. Em atribuir a, selecione **todos os usuários + todos os dispositivos**.
12. Clique em **Guardar**.

### <a name="optional-create-an-android-device-compliance-policy"></a>Adicional Criar uma política de conformidade do dispositivo Android
Crie uma política de conformidade de dispositivos do Intune para definir as condições que um dispositivo tem de cumprir para ser considerado conforme. Para este tutorial, criaremos uma política de conformidade do dispositivo para dispositivos Android. As políticas de conformidade são específicas da plataforma, portanto, você precisa criar uma política separada para seus usuários de margem de atraso em dispositivos iOS.
1. No Intune, selecione **Conformidade do dispositivo** > **Políticas** > **Criar Política**.
2. Em nome, insira "teste de política de conformidade do Android".
3. Em descrição, insira "teste de política de conformidade do Android".
4. Em plataforma, selecione **Android Enterprise**.
5. Em tipo de perfil, selecione **perfil de trabalho**.
6. Selecione **Estado de Funcionamento dos Dispositivos**. Ao lado de dispositivos com raiz, selecione **Bloquear**e, em seguida, selecione **OK**.
7. Selecione **segurança do sistema** e insira **as configurações de senha**. Para este tutorial, selecione as seguintes definições recomendadas:
    - Para exigir uma senha para desbloquear dispositivos móveis, selecione **exigir**.
    - Para tipo de senha necessária, selecione **pelo menos alfanumérico**.
    - Para comprimento mínimo da senha, digite 4.
    - Para máximo de minutos após o bloqueio de tela antes que a senha seja necessária, escolha **15 minutos**.
    - Para expiração da senha (dias), digite 41.
    - Para o número de senhas anteriores para evitar a reutilização, insira 5.
8. Clique em **OK**e em **OK** novamente.
9. Clique em **Criar**.

## <a name="launch-slack"></a>Lançar margem de atraso

Com as políticas que você acabou de criar, todos os dispositivos de perfil de trabalho iOS ou Android que tentarem entrar em um de seus espaços de trabalho precisarão ser registrados no Intune. Para testar esse cenário, tente iniciar a margem de atraso para EMM em um dispositivo iOS registrado pelo Intune ou iniciar a margem de atraso em um dispositivo de perfil de trabalho do Android registrado no Intune. 

## <a name="next-steps"></a>Próximos passos

Neste tutorial:
- Você define o Intune como o provedor de gerenciamento de mobilidade empresarial (EMM) em sua grade empresarial de margem de atraso. 
- Você criou políticas de configuração de aplicativo para gerenciar a margem de atraso para o aplicativo EMM no iOS e o aplicativo de margem de atraso para dispositivos de perfil de trabalho do Android.
- Você criou as políticas de conformidade do dispositivo do Intune para definir as condições que os dispositivos Android e iOS devem atender para serem considerados em conformidade.

Para saber mais sobre as políticas de configuração de aplicativo, consulte [políticas de configuração de aplicativo para Microsoft Intune](app-configuration-policies-overview.md). Para saber mais sobre as políticas de conformidade do dispositivo, consulte [definir regras em dispositivos para permitir o acesso a recursos em sua organização usando o Intune](../protect/device-compliance-get-started.md).
