---
title: Migrar o acesso condicional para o portal do Azure | Microsoft Intune
description: Reatribua as políticas de acesso condicional que criou anteriormente no portal clássico do Intune ao portal do Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f8800eea75afb51af94a250e96fa577f6ecb231
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389596"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Reatribuir políticas de acesso condicional do portal clássico do Intune para o portal do Azure

No novo portal do Azure, o acesso condicional oferece suporte para múltiplas políticas por aplicação, assim como mais personalizações. Se tiver criado anteriormente políticas de acesso condicional no portal clássico do Intune, pode migrá-las para o portal do Azure. 

## <a name="before-you-begin"></a>Antes de começar

Se estiver pronto para mudar para o portal do Azure, siga os passos neste tópico para reatribuir as políticas de acesso condicional criadas anteriormente no portal clássico do Intune:

- Reúna as políticas de acesso condicional criadas anteriormente para saber que definições precisa de reatribuir mais tarde.

- Siga os passos neste tópico para recriar estas políticas no portal do Azure.

- Desative as políticas condicionais no portal clássico do Intune após ter verificado que as novas políticas funcionam conforme esperado no portal do Azure.
<br /><br />
    - **Antes de desativar** as políticas de acesso condicional no portal clássico do Intune, planeie a forma como irá migrar os utilizadores para a nova política. Existem duas abordagens:
<br /><br />
        - **Utilize o mesmo grupo de inclusão para aplicar políticas criadas no portal do Azure e crie um novo grupo de isenção para utilizar com as políticas aplicadas pelo portal clássico do Intune**.
            - Migre gradualmente alguns utilizadores para o grupo de isenção especificado no portal clássico. Esta ação impede que as políticas direcionadas pelo portal clássico do Intune sejam aplicadas. As políticas criadas e direcionadas para o mesmo grupo de utilizadores no portal do Azure são aplicadas para além das aplicadas no portal clássico do Intune. 
<br /><br />
        - **Crie um novo grupo para direcionar as políticas de acesso condicional no portal do Azure**. Se escolher esta abordagem, tem de fazer o seguinte:
            - Remova gradualmente os utilizadores dos grupos de segurança que têm políticas de acesso condicional direcionadas aos mesmos no portal clássico do Intune.
            - Após confirmar que a nova política está a funcionar para estes utilizadores, pode desativar a política no portal clássico do Intune. 
<br /><br />
- Se tiver as suas definições de política de acesso condicional configuradas para utilizar o Exchange Active Sync (EAS) no portal clássico do Intune, veja as [instruções neste tópico](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) para **reatribuir as definições de política de acesso condicional do EAS no portal do Azure**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Para verificar as suas políticas de acesso condicional com base no dispositivo no portal clássico do Intune

1.  Aceda ao [portal clássico do Intune](https://manage.microsoft.com) e inicie sessão com as suas credenciais.

2.  Selecione **Política** no menu à esquerda.

3.  Selecione **Acesso condicional** e, em seguida, selecione o serviço cloud da Microsoft (por exemplo, Exchange Online ou SharePoint Online) para o qual criou uma política de acesso condicional.

4.  Anote as suas definições de acesso condicional e utilize estas notas como referência quando criar as mesmas políticas de acesso condicional no portal do Azure.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Políticas de acesso condicional com base no dispositivo e na aplicação a trabalharem em conjunto

O painel **Proteção de Aplicações do Intune** no portal do Azure permite que os administradores definam regras condicionais com base na aplicação para que apenas as aplicações que suportam as políticas de proteção de aplicações do Intune tenham permissão para aceder aos recursos empresariais. Pode optar por sobrepor estas políticas de acesso condicional com base na aplicação através de políticas de acesso condicional com base no dispositivo. Pode combinar as políticas condicionais com base na aplicação e no dispositivo (E lógico) ou pode fornecer qualquer uma das opções (OU lógico). Se os seus requisitos de política de acesso condicional forem para:

- Exigir um dispositivo em conformidade **E** utilizar a aplicação aprovada.
    - Deve definir a sua política de acesso condicional através do [painel Acesso condicional ao Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e do [painel Proteção de Aplicações do Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Exigir um dispositivo em conformidade **OU** utilizar a aplicação aprovada.
    - Deve definir a sua política de acesso condicional através do [portal clássico do Intune](https://manage.microsoft.com) e do [painel Proteção de Aplicações do Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Este tópico fornece capturas de ecrã que comparam a experiência do utilizador no portal clássico do Intune e no portal do Azure.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Reatribuir políticas de acesso condicional com base no dispositivo do Intune

1. Aceda a [Acesso condicional no portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sessão com as suas credenciais.

2. Selecione **Nova política**.

3. Forneça um nome para a política.

4. Na **secção Atribuições**, selecione **Utilizadores e grupos** para direcionar a nova política de acesso condicional.
    
    ![Nesse grupo de utilizadores compara da interface do Usuário entre os portais do Azure do Intune e de imagem](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > A seleção que fizer no portal do Azure deve corresponder à seleção feita no portal clássico. Por exemplo, se tiver selecionado todos os utilizadores no portal clássico do Intune, selecione **Todos os utilizadores** no portal do Azure. Além disso, se tiver selecionado a opção **Grupos isentos** no portal clássico do Intune, tem de excluir esses grupos selecionados no portal do Azure.

5. Após escolher o seu grupo, clique em **Selecionar** e, em seguida, clique em **Concluído**.

6. Na secção **Atribuições**, selecione **Aplicações na cloud**.

7. No painel **Aplicações na cloud**, selecione **Selecionar aplicações**.

8. Selecione a aplicação a que pretende aplicar a nova política de acesso condicional e clique em **Selecionar**.

9. Clique em **Concluído**.

    ![Imagem de uma comparação de interface do Usuário de aplicação na cloud entre os portais do Azure e o Intune](./media/reassign-ca-3.png)

    > [!TIP] 
    > Se tiver múltiplas aplicações com a mesma política, pondere consolidá-las numa única política no portal do Azure.

10. Na secção **Atribuições**, selecione **Condições**.

11. No painel **Condições**, selecione **Plataformas de dispositivos** e, em seguida, selecione as plataformas de dispositivos aplicáveis.

12. Quando terminar de selecionar as plataformas de dispositivos, clique em **Concluído** duas vezes.

    ![Imagem que compara a plataforma de dispositivo da interface do Usuário de portais do Intune e o Azure](./media/reassign-ca-4.png)

    > [!TIP] 
    > Se tiver selecionado plataformas individuais no portal clássico do Intune, selecione as plataformas individuais no portal do Azure.

    > [!NOTE] 
    > Pode especificar as opções de conformidade ou associação a um domínio para o Windows mais tarde.

13. Na secção **Atribuições**, selecione **Condições**.

14. No painel **Condições**, selecione **Aplicações cliente** e, em seguida, selecione a aplicação cliente aplicável.

15. Após selecionar a aplicação cliente, clique em **Concluído** duas vezes.

    ![Imagem que compara as aplicações de cliente da interface do Usuário entre os portais do Azure e o Intune](./media/reassign-ca-6.png)

16. Se tiver escolhido as definições do browser no portal clássico do Intune, selecione **Browser** e **Aplicações móveis e clientes de ambiente de trabalho** no portal do Azure. No caso de não ter escolhido as definições do browser no portal clássico do Intune, selecione apenas **Aplicações móveis e clientes de ambiente de trabalho**. 

17. Na secção **Controlos de acesso**, selecione **Conceder**.

18. Em **Conceder Controlos de Acesso**, selecione **Pedir que o dispositivo seja marcado como compatível** e, em seguida, clique em **Selecionar**.

19. Se tiver uma política para exigir dispositivos Windows associados a um domínio e também permitir dispositivos Windows em conformidade e inscritos no Intune, selecione **Requerer dispositivo associado ao domínio** e **Pedir que o dispositivo seja marcado como compatível**, juntamente com **Exigir um dos controlos selecionados**.

20. Se não permitir dispositivos Windows em conformidade e inscritos no Intune, exclua a política do Windows da política atual. Em seguida, crie uma política separada com a opção **Plataformas de dispositivos** definida para **Windows**, inclua outras condições conforme definido acima e selecione **Requerer dispositivo associado ao domínio** em **Conceder Controlos de Acesso**.

21. No painel de política de acesso condicional **Novo**, ative o botão **Ativar política** e, em seguida, clique em **Criar**.

    ![Comparar ativar política de acesso condicional da interface do Usuário entre o Intune e do Azure](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Reatribuir políticas de acesso condicional com base no dispositivo do Intune para clientes EAS

Se tiver configurado as definições do Exchange Active Sync como parte de uma política do Exchange Online no portal clássico do Intune, tem de criar uma segunda política de acesso condicional no portal do Azure.

1. Aceda a [Acesso condicional no portal do Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e inicie sessão com as suas credenciais.

2. Selecione **Nova política**.

3. Forneça um nome para a política.

4. Na secção **Atribuições**, selecione **Utilizadores e grupos** para direcionar a nova política de acesso condicional.

    ![Imagem que mostra uma comparação de interface do Usuário do grupo de utilizadores entre os portais do Azure e o Intune](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > A seleção que fizer no portal do Azure deve corresponder à seleção feita no portal do Intune. Por exemplo, se tiver selecionado todos os utilizadores no portal clássico do Intune, selecione **Todos os utilizadores** no portal do Azure. Além disso, se tiver selecionado a opção **Grupos isentos** no portal clássico do Intune, tem de excluir esses grupos selecionados no portal do Azure.

5. Após escolher o seu grupo, clique em **Selecionar** e, em seguida, clique em **Concluído**.

6. Na secção **Atribuições**, selecione **Aplicações na cloud**.

7. No painel **Aplicações na cloud**, clique em **Selecionar aplicações** e selecione **Exchange Online**. Em seguida, clique em **Selecionar** e **Concluído**.

    ![Imagem de uma comparação de interface do Usuário de aplicações na Cloud entre os portais do Azure e o Intune](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > As políticas de acesso condicional para clientes EAS não podem incluir outras aplicações na cloud.

8. No painel **Condições**, selecione **Aplicações cliente** e, em seguida, selecione a aplicação cliente aplicável. Se tiver optado por bloquear clientes que não sejam suportados pelo Intune, utilize a opção **Aplicar política apenas a plataformas suportadas**.

    ![Imagem que mostra um cliente comparação da IU de aplicações entre os portais do Azure e o Intune](./media/reassign-ca-15.png)

9. Após selecionar a aplicação cliente, clique em **Concluído** duas vezes.

10. Na secção **Controlos de acesso**, selecione **Conceder**.

11. Em **Conceder Controlos de Acesso**, selecione **Pedir que o dispositivo seja marcado como compatível** e, em seguida, clique em **Selecionar**.

    ![Imagem que compara a concessão de acesso da interface do Usuário entre os portais do Azure e o Intune](./media/reassign-ca-16.png)

12. No painel de política de acesso condicional **Novo**, ative o botão **Ativar política** e, em seguida, clique em **Criar**.

    ![Comparação de política de acesso condicional de ativação da interface do Usuário entre o Intune e do Azure](./media/reassign-ca-17.png)

> [!NOTE]
> Se configurar **Plataformas de dispositivos**, guardar a política irá falhar com o erro "A configuração de política não é suportada". O Exchange ActiveSync não consegue identificar a plataforma a ser utilizada pelo dispositivo de ligação. Por conseguinte, a configuração de plataformas de dispositivos específicas não é suportada quando criar uma política para dispositivos do Exchange ActiveSync.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Desativar políticas de acesso condicional do portal clássico do Intune

Assim que reatribuir as suas políticas de acesso condicional no portal do Azure, é importante desativar gradualmente as políticas de acesso condicional criadas anteriormente no portal clássico do Intune. Além disso, poderá ter de utilizar o mesmo grupo de segurança para aplicar as políticas de acesso condicional criadas no portal do Azure.

> [!NOTE]
> Antes de desativar as suas políticas de acesso condicional no portal clássico do Intune, veja a secção [Antes de começar](#before-you-begin) no início deste tópico.

### <a name="to-disable-the-conditional-access-policies"></a>Para desativar as políticas de acesso condicional

1.  Aceda ao [portal clássico do Intune](https://manage.microsoft.com) e inicie sessão com as suas credenciais.

2.  Selecione **Política** no menu à esquerda.

3.  Selecione **Acesso condicional** e, em seguida, selecione o serviço cloud da Microsoft (por exemplo, Exchange Online ou SharePoint Online) para o qual criou uma política de acesso condicional.

4.  Desmarque a opção **Ativar política de acesso condicional** e, em seguida, clique em **Guardar**.

    ![Imagem de desativar políticas de acesso condicional no portal clássico do Intune](./media/reassign-ca-18.png)

## <a name="see-also"></a>Consulte também

- [Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
- [acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)
- [Acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
