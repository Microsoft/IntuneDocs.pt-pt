---
title: "Definir termos e condições no Microsoft Intune"
titlesuffix: 
description: "Defina os termos e condições que os utilizadores veem no Portal da Empresa do Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8fb386948d14fcbd26cffcd1b531b6ae61e9d669
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Gerir os termos e condições da sua empresa para o acesso dos utilizadores

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador do Intune, pode exigir que os utilizadores aceitem os termos e condições da sua empresa antes de poderem utilizar o Portal da Empresa para inscrever os dispositivos e aceder a recursos como aplicações e e-mail da empresa. A configuração dos termos e condições é opcional.

Pode criar vários conjuntos de termos e atribuí-los a diferentes grupos, tal como para suportar outros idiomas.

## <a name="create-terms-and-conditions"></a>Criar termos e condições
Conclua estes passos para criar os termos e condições. O nome a apresentar e a descrição são para utilização administrativa enquanto as propriedades dos termos são apresentadas aos utilizadores no Portal da Empresa.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Inscrição de dispositivos** e, em seguida, selecione **Termos e Condições**.
2. Selecione **Criar**.
![Captura de ecrã do portal do Azure a mostrar o botão Criar dos termos e condições](media/terms-create-terms.png)
3. No painel expandido, especifique as seguintes informações:

   - **Nome a apresentar**: o nome relativo aos termos no portal do Azure. Os utilizadores não veem este nome.

   - **Descrição**: detalhes opcionais que ajudam a identificar este conjunto de termos no Portal do Azure.

4. Selecione a seta junto a **Definir termos de utilização** para abrir o painel Termos e Condições e, em seguida, introduza as seguintes informações:

   ![Captura de ecrã do ecrã de aceitação dos termos e condições do utilizador final com um resumo dos termos](./media/terms-summary-create.png)

   - **Título**: o nome dos termos que os utilizadores veem no Portal da Empresa acima do **Resumo**.
   - **Resumo dos Termos**: texto que explica o que significa quando os utilizadores aceitam os termos. Por exemplo, “Ao inscrever o dispositivo, aceita os termos de utilização definidos pela Contoso. Leia atentamente os termos antes de continuar”.
   - **Termos e Condições**: os termos e condições que os utilizadores veem e devem aceitar ou rejeitar.

5. Selecione **Ok** e, em seguida, selecione **Criar**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Ver como os termos são apresentados para os utilizadores
O exemplo a seguir mostra o **Título** e o **Resumo de Termos** na consola de administração e no Portal da Empresa.

![Captura de ecrã do Título e do Resumo dos Termos na consola de administração e no Portal da Empresa.](./media/terms-summary-terms.png)

O exemplo a seguir mostra os termos e as condições na consola de administração e no Portal da Empresa.

![Captura de ecrã dos termos e das condições na consola de administração e no Portal da Empresa.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Atribuir termos e condições

Pode atribuir termos e condições a grupos de utilizadores que devem aceitá-los antes de utilizar o Portal da Empresa.

1. No portal do Azure, escolha **Inscrição de dispositivos** e, em seguida, **Termos e Condições**.
2. Na lista de termos e condições, selecione os termos que pretende atribuir e, em seguida, selecione **Gerir** > **Atribuições**.
![Captura de ecrã do painel Atribuir Grupo do portal do Azure a mostrar os botões Selecionar Grupo e Selecionar para a atribuição dos termos e condições](media/terms-assign-groups.png)
3. Clique em **Selecionar grupos para incluir** e selecione os grupos aos quais pretende atribuir os termos e, em seguida, clique em **Selecionar**. Não pode atribuir Termos e Condições aos grupos dinâmicos.
4. No painel **Grupos Atribuídos**, clique em **Guardar**.  Os termos e condições estão agora atribuídos aos utilizadores nos grupos selecionados. Será pedido aos utilizadores que aceitem os termos da próxima vez que acederem ao portal da empresa. Os termos e condições só precisam de ser aceites uma vez. Os utilizadores com vários dispositivos não precisam de aceitar em cada dispositivo.


## <a name="monitor-terms-and-conditions"></a>Monitorizar os termos e as condições

1. No portal do Azure, selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**. 
1. No painel Intune, selecione **Inscrição de dispositivos** e, em seguida, selecione **Termos e Condições**.
2. Na lista de termos e condições, selecione os termos nos quais pretende ver a aceitação e, em seguida, selecione **Relatórios de Aceitação**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabalhar com múltiplas versões de termos e condições
Pode editar os seus termos e condições e gerir as respetivas versões. Recomendamos que aumente o número da versão e solicite a aceitação sempre que efetua alterações significativas nos seus termos e condições. Mantenha o número da versão atual se, por exemplo, estiver a corrigir erros de digitação ou a alterar a formatação.

1. No portal do Azure, selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, selecione **Inscrição de dispositivos**, selecione **Termos e Condições**, selecione os termos e condições que pretende modificar e, em seguida, selecione **Propriedades**.

4. No painel **Propriedades**, selecione **Termos e Condições** e, em seguida, modifique o **Título**, **Resumo dos Termos** e **Termos e Condições**, conforme necessário. Se as alterações que efetuou tornam necessário aos utilizadores aceitar novamente os novos termos, clique em **Exigir que os utilizadores voltem a aceitar e incrementar o número de versão**

4.  Selecione **OK** e, em seguida, selecione **Guardar**.

Os utilizadores só precisam de aceitar os termos e as condições atualizados uma vez. Os utilizadores com vários dispositivos não precisam de aceitar os termos e condições em cada dispositivo.
