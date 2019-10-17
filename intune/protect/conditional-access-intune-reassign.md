---
title: Migrar acesso condicional para portal do Azure
titleSuffix: Microsoft Intune
description: Reatribua as políticas de acesso condicional que você criou anteriormente no portal clássico do Intune para a portal do Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03b228795d7601647c57ea86b5adf7576b669c45
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504576"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Reatribuir políticas de acesso condicional do portal clássico do Intune para o portal do Azure

A partir do novo portal do Azure, o acesso condicional oferece suporte para várias políticas por aplicativo, juntamente com mais personalização. Se você já tiver criado políticas de acesso condicional no portal clássico do Intune, poderá migrá-las para o portal do Azure. 

## <a name="before-you-begin"></a>Antes de começar

Se você estiver pronto para mover para a portal do Azure, siga as etapas neste tópico para reatribuir as políticas de acesso condicional criadas anteriormente no portal clássico do Intune:

- Reúna as políticas de acesso condicional criadas anteriormente, para que você saiba quais configurações precisará reatribuir mais tarde.

- Siga os passos neste tópico para recriar estas políticas no portal do Azure.

- Desative as políticas condicionais no portal clássico do Intune após ter verificado que as novas políticas funcionam conforme esperado no portal do Azure.
<br /><br />
  - **Antes de desabilitar** as políticas de acesso condicional no portal clássico do Intune, planeje como você moverá os usuários para a nova política. Existem duas abordagens:
<br /><br />
    - **Utilize o mesmo grupo de inclusão para aplicar políticas criadas no portal do Azure e crie um novo grupo de isenção para utilizar com as políticas aplicadas pelo portal clássico do Intune**.
      - Migre gradualmente alguns utilizadores para o grupo de isenção especificado no portal clássico. Esta ação impede que as políticas direcionadas pelo portal clássico do Intune sejam aplicadas. As políticas criadas e direcionadas para o mesmo grupo de utilizadores no portal do Azure são aplicadas para além das aplicadas no portal clássico do Intune. 
<br /><br />
    - **Crie um novo grupo para direcionar as políticas de acesso condicional no portal do Azure**. Se escolher esta abordagem, tem de fazer o seguinte:
      - Remova gradualmente os usuários dos grupos de segurança que têm políticas de acesso condicional direcionadas para eles no portal clássico do Intune.
      - Após confirmar que a nova política está a funcionar para estes utilizadores, pode desativar a política no portal clássico do Intune. 
<br /><br />
- Se você tiver suas configurações de política de acesso condicional configuradas para usar o EAS (Exchange ActiveSync) no portal clássico do Intune, consulte as [instruções neste tópico](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) para **reatribuir as configurações da política de acesso condicional do EAS no portal do Azure**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Para verificar as políticas de acesso condicional com base no dispositivo no portal clássico do Intune

1. Aceda ao [portal clássico do Intune](https://manage.microsoft.com) e inicie sessão com as suas credenciais.

2. Selecione **Política** no menu à esquerda.

3. Escolha **acesso condicional**e, em seguida, selecione o serviço de nuvem da Microsoft (por exemplo, Exchange Online ou SharePoint Online) para o qual você criou uma política de acesso condicional.

4. Anote suas configurações de acesso condicional e faça referência a elas ao criar as mesmas políticas de acesso condicional no portal do Azure.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Políticas de acesso condicional com base no aplicativo e no dispositivo trabalhando juntas

O painel **Proteção de Aplicações do Intune** no portal do Azure permite que os administradores definam regras condicionais com base na aplicação para que apenas as aplicações que suportam as políticas de proteção de aplicações do Intune tenham permissão para aceder aos recursos empresariais. Você pode optar por sobrepor essas políticas de acesso condicional com base no aplicativo usando políticas de acesso condicional com base no dispositivo. Pode combinar as políticas condicionais com base na aplicação e no dispositivo (E lógico) ou pode fornecer qualquer uma das opções (OU lógico). Se seus requisitos de política de acesso condicional forem:

- Exigir um dispositivo em conformidade **E** utilizar a aplicação aprovada.
  - Você deve definir sua política de acesso condicional usando a [folha acesso condicional Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e a [folha proteção de aplicativo do Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Exigir um dispositivo em conformidade **OU** utilizar a aplicação aprovada.
  - Você deve definir sua política de acesso condicional usando o [portal clássico do Intune](https://manage.microsoft.com) e a [folha proteção de aplicativo do Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Este tópico fornece capturas de ecrã que comparam a experiência do utilizador no portal clássico do Intune e no portal do Azure.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Reatribuir políticas de acesso condicional com base no dispositivo do Intune

1. Acesse [o acesso condicional no portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)e entre com suas credenciais.

2. Selecione **Nova política**.

3. Forneça um nome para a política.

4. Na **seção atribuições**, escolha **usuários e grupos** para direcionar a nova política de acesso condicional.

    ![Imagem que compara a interface do usuário do grupo de usuários entre os portais do Intune e do Azure](./media/conditional-access-intune-reassign/reassign-ca-1.png)

    > [!IMPORTANT] 
    > A seleção que fizer no portal do Azure deve corresponder à seleção feita no portal clássico. Por exemplo, se tiver selecionado todos os utilizadores no portal clássico do Intune, selecione **Todos os utilizadores** no portal do Azure. Além disso, se tiver selecionado a opção **Grupos isentos** no portal clássico do Intune, tem de excluir esses grupos selecionados no portal do Azure.

5. Após escolher o seu grupo, clique em **Selecionar** e, em seguida, clique em **Concluído**.

6. Na secção **Atribuições**, selecione **Aplicações na cloud**.

7. No painel **Aplicações na cloud**, selecione **Selecionar aplicações**.

8. Escolha o aplicativo ao qual você deseja aplicar a nova política de acesso condicional e clique em **selecionar**.

9. Clique em **Concluído**.

    ![Imagem de uma comparação de interface do usuário de aplicativo de nuvem entre os portais do Intune e do Azure](./media/conditional-access-intune-reassign/reassign-ca-3.png)

    > [!TIP] 
    > Se tiver múltiplas aplicações com a mesma política, pondere consolidá-las numa única política no portal do Azure.

10. Na secção **Atribuições**, selecione **Condições**.

11. No painel **Condições**, selecione **Plataformas de dispositivos** e, em seguida, selecione as plataformas de dispositivos aplicáveis.

12. Quando terminar de selecionar as plataformas de dispositivos, clique em **Concluído** duas vezes.

    ![Imagem que compara a interface do usuário da plataforma de dispositivo dos portais do Intune e do Azure](./media/conditional-access-intune-reassign/reassign-ca-4.png)

    > [!TIP] 
    > Se tiver selecionado plataformas individuais no portal clássico do Intune, selecione as plataformas individuais no portal do Azure.

    > [!NOTE] 
    > Pode especificar as opções de conformidade ou associação a um domínio para o Windows mais tarde.

13. Na secção **Atribuições**, selecione **Condições**.

14. No painel **Condições**, selecione **Aplicações cliente** e, em seguida, selecione a aplicação cliente aplicável.

15. Após selecionar a aplicação cliente, clique em **Concluído** duas vezes.

    ![Imagem que compara a interface do usuário de aplicativos cliente entre os portais do Intune e do Azure](./media/conditional-access-intune-reassign/reassign-ca-6.png)

16. Se tiver escolhido as definições do browser no portal clássico do Intune, selecione **Browser** e **Aplicações móveis e clientes de ambiente de trabalho** no portal do Azure. No caso de não ter escolhido as definições do browser no portal clássico do Intune, selecione apenas **Aplicações móveis e clientes de ambiente de trabalho**. 

17. Na secção **Controlos de acesso**, selecione **Conceder**.

18. Em **Conceder Controlos de Acesso**, selecione **Pedir que o dispositivo seja marcado como compatível** e, em seguida, clique em **Selecionar**.

19. Se tiver uma política para exigir dispositivos Windows associados a um domínio e também permitir dispositivos Windows em conformidade e inscritos no Intune, selecione **Requerer dispositivo associado ao domínio** e **Pedir que o dispositivo seja marcado como compatível**, juntamente com **Exigir um dos controlos selecionados**.

20. Se não permitir dispositivos Windows em conformidade e inscritos no Intune, exclua a política do Windows da política atual. Em seguida, crie uma política separada com a opção **Plataformas de dispositivos** definida para **Windows**, inclua outras condições conforme definido acima e selecione **Requerer dispositivo associado ao domínio** em **Conceder Controlos de Acesso**.

21. Na folha **nova** política de acesso condicional, ative a alternância **habilitar política** e, em seguida, clique em **criar**.

    ![Comparar habilitar interface do usuário de política de acesso condicional entre o Intune e o Azure](./media/conditional-access-intune-reassign/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Reatribuir políticas de acesso condicional com base no dispositivo do Intune para clientes EAS

Se você tiver configurado as configurações do Exchange ActiveSync como parte de uma política do Exchange Online no portal clássico do Intune, será necessário criar uma segunda política de acesso condicional no portal do Azure.

1. Acesse [o acesso condicional no portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)e entre com suas credenciais.

2. Selecione **Nova política**.

3. Forneça um nome para a política.

4. Na seção **atribuições** , escolha **usuários e grupos** para direcionar a nova política de acesso condicional.

    ![Imagem mostrando uma comparação de interface do usuário do grupo de usuários entre os portais do Azure e do Intune](./media/conditional-access-intune-reassign/reassign-ca-12.png)

    > [!IMPORTANT] 
    > A seleção que fizer no portal do Azure deve corresponder à seleção feita no portal do Intune. Por exemplo, se tiver selecionado todos os utilizadores no portal clássico do Intune, selecione **Todos os utilizadores** no portal do Azure. Além disso, se tiver selecionado a opção **Grupos isentos** no portal clássico do Intune, tem de excluir esses grupos selecionados no portal do Azure.

5. Após escolher o seu grupo, clique em **Selecionar** e, em seguida, clique em **Concluído**.

6. Na secção **Atribuições**, selecione **Aplicações na cloud**.

7. No painel **Aplicações na cloud**, clique em **Selecionar aplicações** e selecione **Exchange Online**. Em seguida, clique em **Selecionar** e **Concluído**.

    ![Imagem de uma comparação de interface do usuário de aplicativos de nuvem entre os portais do Intune e do Azure](./media/conditional-access-intune-reassign/reassign-ca-14.png)

    > [!IMPORTANT] 
    > As políticas de acesso condicional para clientes EAS não podem incluir outras aplicações na cloud.

8. No painel **Condições**, selecione **Aplicações cliente** e, em seguida, selecione a aplicação cliente aplicável. Se tiver optado por bloquear clientes que não sejam suportados pelo Intune, utilize a opção **Aplicar política apenas a plataformas suportadas**.

    ![Imagem mostrando uma comparação de interface do usuário de aplicativos cliente entre os portais do Azure e do Intune](./media/conditional-access-intune-reassign/reassign-ca-15.png)

9. Após selecionar a aplicação cliente, clique em **Concluído** duas vezes.

10. Na secção **Controlos de acesso**, selecione **Conceder**.

11. Em **Conceder Controlos de Acesso**, selecione **Pedir que o dispositivo seja marcado como compatível** e, em seguida, clique em **Selecionar**.

    ![Imagem que compara a concessão de interface do usuário de acesso entre os portais do Intune e do Azure](./media/conditional-access-intune-reassign/reassign-ca-16.png)

12. Na folha **nova** política de acesso condicional, ative a alternância **habilitar política** e, em seguida, clique em **criar**.

    ![Comparação da interface do usuário habilitar política de acesso condicional entre o Intune e o Azure](./media/conditional-access-intune-reassign/reassign-ca-17.png)

> [!NOTE]
> Se configurar **Plataformas de dispositivos**, guardar a política irá falhar com o erro "A configuração de política não é suportada". O Exchange ActiveSync não consegue identificar a plataforma a ser utilizada pelo dispositivo de ligação. Por conseguinte, a configuração de plataformas de dispositivos específicas não é suportada quando criar uma política para dispositivos do Exchange ActiveSync.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Desabilitar políticas de acesso condicional no portal clássico do Intune

Depois de ter reatribuído suas políticas de acesso condicional no portal do Azure, é importante desabilitar gradualmente as políticas de acesso condicional criadas anteriormente no portal clássico do Intune. Além disso, talvez seja necessário usar o mesmo grupo de segurança para aplicar as políticas de acesso condicional criadas no portal do Azure.

> [!NOTE]
> Antes de desabilitar suas políticas de acesso condicional no portal clássico do Intune, consulte a seção [antes de começar](#before-you-begin) no início deste tópico.

### <a name="to-disable-the-conditional-access-policies"></a>Para desabilitar as políticas de acesso condicional

Como o MDM foi removido do portal clássico do Intune, o seguinte link foi fornecido para exibir/desabilitar estas políticas clássicas:

[https://portal.azure.com/?microsoft_aad_iam_classicPolicyDontHide=true#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/ClassicPolicies](https://portal.azure.com/?microsoft_aad_iam_classicPolicyDontHide=true#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/ClassicPolicies)

## <a name="see-also"></a>Consulte também

- [Maneiras comuns de usar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
- [Acesso condicional baseado em aplicativo com o Intune](app-based-conditional-access-intune.md)
- [Acesso Condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
