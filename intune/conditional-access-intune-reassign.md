---
title: "Migre políticas de acesso condicional do portal clássico do Intune para o novo portal do Azure."
titleSuffix: Intune on Azure
description: "Migre políticas de acesso condicional do portal clássico do Intune para o novo portal do Azure."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2450a878424d8c992a43e8028ba59b7136e1d530
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2017
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-new-azure-portal"></a>Reatribuir políticas de acesso condicional do portal clássico do Intune para o novo portal do Azure

No novo portal do Azure, o acesso condicional oferece suporte para múltiplas políticas por aplicação, assim como mais personalizações.

## <a name="before-you-begin"></a>Antes de começar

Se estiver pronto para mudar para o novo portal do Azure, pode seguir os passos abaixo para reatribuir as políticas de acesso condicional criadas anteriormente no portal clássico do Intune:

- Recolha as políticas de acesso condicional criadas anteriormente no portal clássico do Intune, para saber que definições precisa de reatribuir mais tarde.

- Siga os passos neste tópico para recriar estas políticas no novo portal do Azure.

- Desative as políticas condicionais na consola clássica do Intune assim que tiver verificado que as novas políticas funcionam conforme esperado no novo portal do Azure.
<br /><br />
    - **Antes de desativar** as políticas de acesso condicional no portal clássico do Intune, planeie a forma como irá migrar os utilizadores para a nova política. Existem duas abordagens:
<br /><br />
        - **Utilize o mesmo grupo de inclusão para aplicar políticas criadas no novo portal do Azure e crie um novo grupo de isenção para utilizar com as políticas aplicadas pelo portal clássico do Intune**.
            - Migre gradualmente alguns utilizadores para o grupo de isenção especificado no portal clássico.  Esta ação impede que as políticas direcionadas pelo portal clássico do Intune sejam aplicadas. As políticas criadas e direcionadas para o mesmo grupo de utilizadores no novo portal do Azure são aplicadas para além daquelas aplicadas no portal clássico do Intune. 
<br /><br />
        - **Crie um novo grupo para direcionar as políticas de acesso condicional no novo portal do Azure**. Se escolher esta abordagem, tem de fazer o seguinte:
            - Remova gradualmente os utilizadores de grupos de segurança que têm políticas de acesso condicional direcionadas no portal clássico do Intune.
            - Assim que tiver confirmado que a nova política está a funcionar para estes utilizadores, pode desativar a política no portal clássico do Intune. 
<br /><br />
- Se tiver definições de política de acesso condicional configuradas para utilizar o Exchange Active Sync (EAS) no portal clássico do Intune, veja as [instruções neste tópico](#to-reassign-intune-device-based-conditional-access-policies-for-eas-clients) para **reatribuir as definições de política de acesso condicional do EAS no novo portal do Azure**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Para verificar as suas políticas de acesso condicional com base no dispositivo no portal clássico do Intune

1.  Aceda ao [portal clássico do Intune](https://manage.microsoft.com) e inicie sessão com as suas credenciais.

2.  Selecione **Política** no menu à esquerda.

3.  Selecione **Acesso condicional** e, em seguida, selecione o serviço cloud da Microsoft (Exchange Online, SharePoint Online, etc.) para o qual criou uma política de acesso condicional.

4.  Anote as suas definições de acesso condicional e utilize estas notas como referência para criar as mesmas políticas de acesso condicional no novo portal do Azure.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Políticas de acesso condicional com base no dispositivo e na aplicação a trabalharem em conjunto

O painel **Proteção de Aplicações do Intune** no novo portal do Azure permite que os administradores definam regras condicionais com base na aplicação para que apenas as aplicações que suportam as políticas de proteção de aplicações do Intune tenham permissão para aceder aos recursos empresariais. Pode optar por sobrepor estas políticas de acesso condicional com base na aplicação através de políticas de acesso condicional com base no dispositivo. Consoante queira combinar políticas condicionais com base na aplicação e com base no dispositivo (lógico E) ou fornecer uma opção (lógico OU). Se os seus requisitos de política de acesso condicional forem:

- Exigir um dispositivo em conformidade **E** utilizar a aplicação aprovada.
    - Deve definir a sua política de acesso condicional através do [painel Acesso condicional ao Azure AD](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e do [painel Proteção de Aplicações do Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Exigir um dispositivo em conformidade **OU** utilizar a aplicação aprovada.
    - Deve definir a sua política de acesso condicional através do [portal clássico do Intune](https://manage.microsoft.com) e do [painel Proteção de Aplicações do Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Este tópico fornece capturas de ecrã que comparam a experiência do utilizador no portal clássico do Intune e no novo portal do Azure.

## <a name="to-re-assign-intune-device-based-conditional-access-policies"></a>Para reatribuir políticas de acesso condicional com base no dispositivo do Intune

1. Aceda a [Acesso condicional no novo portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sessão com as suas credenciais.

2. Selecione **Nova política**.

3. Forneça um nome para a política.

4. Selecione **Utilizadores e grupos**, na secção **Atribuições**, para direcionar a nova política de acesso condicional.
    
    ![Comparação entre a IU dos grupos de utilizadores no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Se tiver selecionado todos os utilizadores no portal clássico do Intune, inclua Todos os utilizadores. O mesmo se aplica aos grupos. Se tiver grupos selecionados, tem de selecionar a opção **selecionar utilizadores individuais e grupos** para incluir esses grupos. Além disso, se tiver selecionado a opção **Grupos isentos** no portal clássico do Intune, tem de excluir esses grupos selecionados no novo portal do Azure.

5. Após selecionar o seu grupo, clique em **Selecionar** e em **Concluído**.

6. Selecione **Aplicações na cloud**, na secção **Atribuições**.

7. No painel **Aplicações na cloud**, selecione **Selecionar aplicações**.

8. Selecione a aplicação a que pretende aplicar a nova política de acesso condicional, clique em **Selecionar**.

9. Clique em **Concluído**.

    ![Comparação entre a IU da aplicação na cloud no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-3.png)

    > [!TIP] 
    > Se tiver múltiplas aplicações com a mesma política, pode considerar consolidá-las numa única política no novo portal do Azure.

10. Selecione **Condições**, na secção **Atribuições**.

11. No painel **Condições**, selecione **Plataformas de dispositivos** e, em seguida, selecione as plataformas de dispositivos aplicáveis.

12. Assim que terminar de escolher as plataformas de dispositivos, clique em **Concluído** duas vezes.

    ![Comparação entre a IU da plataforma de dispositivo no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-4.png)

    > [!TIP] 
    > Se tiver escolhido plataformas individuais no portal clássico do Intune, selecione as plataformas individuais no novo portal do Azure.

    > [!NOTE] 
    > Pode especificar as opções de conformidade ou associação a um domínio para o Windows mais tarde.

13. Selecione **Condições**, na secção **Atribuições**.

14. No painel **Condições**, selecione **Aplicações cliente** e, em seguida, selecione a aplicação cliente aplicável.

15. Quando terminar de selecionar a aplicação cliente, clique em **Concluído** duas vezes.

    ![Comparação entre a IU das aplicações cliente no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-6.png)

16. Se tiver escolhido as definições do browser no portal clássico do Intune, selecione **Browser** e **Aplicações móveis e clientes de ambiente de trabalho** no novo portal do Azure. No caso de não ter escolhido as definições do browser no portal clássico do Intune, selecione apenas **Aplicações móveis e clientes de ambiente de trabalho**. 

17. Selecione **Conceder**, na secção **Controlos de acesso**.

18. Selecione **Pedir que o dispositivo seja marcado como compatível** em **Conceder Controlos de Acesso** e, em seguida, clique em **Selecionar**.

19. Se tiver uma política para exigir dispositivos Windows associados a um domínio e também permitir dispositivos Windows em conformidade e inscritos no Intune, selecione **Requerer dispositivo associado ao domínio** e **Pedir que o dispositivo seja marcado como compatível**, juntamente com **Exigir um dos controlos selecionados**.

20. Se não permitir dispositivos Windows em conformidade e inscritos no Intune, exclua a política do Windows da política atual e, em seguida, crie uma política separada com a opção **Plataformas de dispositivos** definida para **Windows**, inclua outras condições conforme definido acima e selecione **Requerer dispositivo associado ao domínio** em **Conceder Controlos de Acesso**.

21. Ative o botão de alternar **Ativar política** no painel de política de acesso condicional **Novo** e, em seguida, clique em **Criar**.

    ![Comparação entre a IU da ativação de política de acesso condicional no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-11.png)

## <a name="to-reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Para reatribuir políticas de acesso condicional com base no dispositivo do Intune para clientes EAS

Se tiver configurado as definições do Exchange Active Sync (EAS) como parte de uma política do Exchange Online no portal clássico do Intune, tem de criar uma segunda política de acesso condicional no novo portal do Azure.

1. Aceda a [Acesso condicional no novo portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sessão com as suas credenciais.

2. Selecione **Nova política**.

3. Forneça um nome para a política.

4. Selecione **Utilizadores e grupos**, na secção **Atribuições**, para direcionar a nova política de acesso condicional.

    ![Comparação entre a IU dos grupos de utilizadores no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Se tiver selecionado todos os utilizadores no portal clássico do Intune, inclua Todos os utilizadores. O mesmo se aplica aos grupos. Se tiver grupos selecionados, tem de selecionar a opção **selecionar utilizadores individuais e grupos** para incluir esses grupos. Além disso, se tiver selecionado a opção **Grupos isentos** no portal clássico do Intune, tem de excluir esses grupos selecionados no novo portal do Azure.

5. Após selecionar o seu grupo, clique em **Selecionar** e em **Concluído**.

6. Selecione **Aplicações na cloud**, na secção **Atribuições**.

7. No painel **Aplicações na cloud**, clique em **Aplicações selecionadas**, selecione **Exchange Online**, clique em **Selecionar** e, em seguida, clique em **Concluído**.

    ![Comparação entre a IU das aplicações na cloud no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > As políticas de acesso condicional para clientes EAS não podem incluir outras aplicações na cloud.

8. No painel **Condições**, selecione **Aplicações cliente** e, em seguida, selecione a aplicação cliente aplicável. Se tiver optado por bloquear clientes que não sejam suportados pelo Intune, utilize a opção **Aplicar política apenas a plataformas suportadas**.

    ![Comparação entre a IU das aplicações cliente no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-15.png)

9. Quando terminar de selecionar a aplicação cliente, clique em **Concluído** duas vezes.

10. Selecione **Conceder**, na secção **Controlos de acesso**.

11. Selecione **Pedir que o dispositivo seja marcado como compatível** em **Conceder Controlos de Acesso** e, em seguida, clique em **Selecionar**.

    ![Comparação entre a IU da concessão de acesso no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-16.png)

12. Ative o botão de alternar **Ativar política** no painel de política de acesso condicional **Novo** e, em seguida, clique em **Criar**.

    ![Comparação entre a IU da ativação de política de acesso condicional no portal clássico do Intune e no novo portal do Azure](./media/reassign-ca-17.png)

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Desativar políticas de acesso condicional do portal clássico do Intune
### <a name="before-you-start"></a>Antes de começar

Assim que reatribuir as suas políticas de acesso condicional no novo portal do Azure, é importante desativar gradualmente as políticas de acesso condicional criadas anteriormente no portal clássico do Intune. Além disso, poderá ter de utilizar o mesmo grupo de segurança para aplicar as políticas de acesso condicional criadas no novo portal do Azure

- Consulte a secção [antes de começar](#before-you-begin) no início deste tópico antes de desativar as suas políticas de acesso condicional no portal clássico do Intune.

### <a name="to-disable-the-conditional-access-policies"></a>Para desativar as políticas de acesso condicional

1.  Aceda ao [portal clássico do Intune](https://manage.microsoft.com) e inicie sessão com as suas credenciais.

2.  Selecione **Política** no menu à esquerda.

3.  Selecione **Acesso condicional** e, em seguida, selecione o serviço cloud da Microsoft (Exchange Online, SharePoint Online, etc.) para o qual criou uma política de acesso condicional.

4.  Desmarque a opção **Ativar política de acesso condicional** e, em seguida, clique em **Guardar**.

    ![Desativar políticas de acesso condicional do portal clássico do Intune](./media/reassign-ca-18.png)

## <a name="see-also"></a>Consulte também

- [Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
- [Acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)
- [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)