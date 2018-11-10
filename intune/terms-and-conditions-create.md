---
title: Definir termos e condições no Microsoft Intune
titlesuffix: ''
description: Defina os termos e condições que os utilizadores veem no Portal da Empresa do Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f480feae1e1df95567023614744c80ec392e86cb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236429"
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Gerir os termos e condições da sua empresa para o acesso dos utilizadores

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enquanto administrador do Intune, pode exigir que os utilizadores aceitem os termos e condições da sua empresa antes de utilizarem o Portal da Empresa para:
- inscrever dispositivos
- aceder a recursos como aplicações e e-mail da empresa.
A configuração dos termos e condições é opcional.

Pode criar vários conjuntos de termos e atribuí-los a diferentes grupos, tal como para suportar outros idiomas.

Existem duas formas de criar os termos e condições da sua empresa:
- com o Intune, conforme descrito neste artigo.
- com a [funcionalidade termos de utilização do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou). Para saber que método é melhor para si, veja a mensagem de blogue [Choosing the right Terms solution for your organization blog post](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) (Escolher a solução de Termos correta para a sua organização). 

## <a name="create-terms-and-conditions"></a>Criar termos e condições
Conclua estes passos para criar os termos e condições. O nome a apresentar e a descrição são para utilização administrativa enquanto as propriedades dos termos são apresentadas aos utilizadores no Portal da Empresa.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Inscrição de dispositivos** > **Termos e Condições**.
2. Selecione **Criar**.
![Captura de ecrã do portal do Azure a mostrar o botão Criar dos termos e condições](media/terms-create-terms.png)
3. No painel expandido, especifique as seguintes informações:

   - **Nome a apresentar**: o nome relativo aos termos no portal do Azure. Os utilizadores não veem este nome.

   - **Descrição**: detalhes opcionais que ajudam a identificar este conjunto de termos no Portal do Azure.

4. Selecione a seta junto a **Definir termos de utilização** para abrir o painel Termos e Condições e, em seguida, introduza as seguintes informações:

   ![Captura de ecrã a mostrar o ecrã de aceitação dos termos e condições do utilizador final, com um resumo dos termos](./media/terms-summary-create.png)

   - **Título**: o nome dos termos que os utilizadores veem no Portal da Empresa acima do **Resumo**.
   - **Resumo dos Termos**: texto que explica o que significa quando os utilizadores aceitam os termos. Por exemplo, "Ao inscrever o dispositivo, aceita os termos de utilização definidos pela Contoso. Leia atentamente os termos antes de continuar”.
   - **Termos e Condições**: os termos e condições que os utilizadores veem e devem aceitar ou rejeitar.

5. Selecione **OK** > **Criar**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Ver como os termos são apresentados para os utilizadores
O exemplo a seguir mostra o **Título** e o **Resumo de Termos** na consola de administração e no Portal da Empresa.

![Captura de ecrã do Título e do Resumo dos Termos na consola de administração e no Portal da Empresa.](./media/terms-summary-terms.png)

O exemplo a seguir mostra os termos e as condições na consola de administração e no Portal da Empresa.

![Captura de ecrã dos termos e das condições na consola de administração e no Portal da Empresa.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Atribuir termos e condições

Pode atribuir termos e condições a grupos de utilizadores que devem aceitá-los antes de utilizar o Portal da Empresa.

1. No portal do Azure, escolha **Inscrição de dispositivos** e, em seguida, **Termos e Condições**.
2. Na lista de termos e condições, selecione os termos que pretende atribuir > **Gerir** > **Atribuições**.
![Captura de ecrã do painel Atribuir Grupo do portal do Azure a mostrar os botões Selecionar Grupo e Selecionar para a atribuição dos termos e condições](media/terms-assign-groups.png)
3. Selecione a opção **Selecionar grupos para incluir** > selecione os grupos aos quais pretende atribuir os termos > **Selecionar**. Não pode atribuir Termos e Condições aos grupos dinâmicos.
4. No painel **Grupos Atribuídos**, selecione **Guardar**.  Os termos e condições estão agora atribuídos aos utilizadores nos grupos selecionados. Será pedido aos utilizadores que aceitem os termos da próxima vez que acederem ao portal da empresa. Os termos e condições só precisam de ser aceites uma vez. Os utilizadores com vários dispositivos não precisam de aceitar em cada dispositivo.


## <a name="monitor-terms-and-conditions"></a>Monitorizar os termos e as condições

1. No portal do Azure, selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**. 
1. No painel Intune, selecione **Inscrição de dispositivos** > **Termos e Condições**.
2. Na lista de termos e condições, selecione os termos cuja aceitação pretende ver > **Relatórios de Aceitação**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabalhar com múltiplas versões de termos e condições
Pode editar os seus termos e condições e gerir as respetivas versões. Sempre que fizer uma alteração significativa aos seus termos e condições, deve:
- aumentar o número da versão.
- exigir que os utilizadores aceitem os novos termos e condições. Mantenha o número da versão atual se, por exemplo, estiver a corrigir erros de digitação ou alterar a formatação.

1. No portal do Azure, selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, selecione **Inscrição de dispositivos** > **Termos e Condições** > selecione os termos e condições que pretende modificar > **Propriedades**.

4. No painel **Propriedades**, selecione **Termos e Condições** e, em seguida, modifique o **Título**, **Resumo dos Termos** e **Termos e Condições**, conforme necessário. Se os utilizadores tiverem de voltar a aceitar os novos termos devido às alterações que fez, selecione **Exigir que os utilizadores voltem a aceitar e incrementem o número da versão para**

4.  Selecione **OK** > **Guardar**.

Os utilizadores só precisam de aceitar os termos e as condições atualizados uma vez. Os utilizadores com vários dispositivos não precisam de aceitar os termos e condições em cada dispositivo.
