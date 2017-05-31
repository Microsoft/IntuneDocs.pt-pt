---
title: "Definir termos e condições no Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Defina os termos e condições que os utilizadores veem no Portal da Empresa do Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d53e91e24988d1bc71ff8df425f0d82e0fc43b58
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="ensure-users-accept-company-terms-for-access"></a>Certifique-se de que os utilizadores aceitam os termos da empresa para o acesso

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Como administrador do Intune, pode optar por exigir que os utilizadores aceitem os termos e condições da sua empresa antes de poderem utilizar o Portal da Empresa para inscrever os respetivos dispositivos e aceder a recursos da empresa, como aplicações e e-mail. A configuração dos termos e condições é opcional.

Pode criar vários conjuntos de termos e atribuí-los a diferentes grupos, tal como para suportar outros idiomas.

## <a name="create-terms-and-conditions"></a>Criar termos e condições
Conclua estes passos para criar os termos e condições. O nome a apresentar e a descrição são para utilização administrativa enquanto as propriedades dos termos são apresentadas aos utilizadores no Portal da Empresa.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrição de dispositivos** e, em seguida, escolha **Termos e Condições**.

3. Selecione **Criar**.
![Captura de ecrã do portal do Intune que mostra o botão Criar para os termos e condições](media/terms-create-terms.png)

4. No painel expandido, especifique as seguintes informações:

   - **Nome a apresentar**: o nome relativo aos termos no portal do Intune. Os utilizadores não veem este nome.

   - **Descrição**: detalhes opcionais que o ajudam a identificar este conjunto de termos no Portal do Azure.

5. Selecione a seta junto a Definir termos de utilização para a abrir o painel Termos e Condições e, em seguida, introduza as seguintes informações:

   ![Captura de ecrã do ecrã de aceitação dos termos e condições do utilizador final com um resumo dos termos](./media/terms-summary-create.png)

   - **Título**: o título que os utilizadores veem no Portal da Empresa.

   - **Resumo dos Termos**: texto que explica o que significa se os utilizadores aceitarem os termos. Por exemplo, “Ao inscrever o dispositivo, aceita os termos de utilização definidos pela Contoso. Leia atentamente os termos antes de continuar”.

   - **Termos e Condições**: os termos e condições que os utilizadores veem e devem aceitar ou rejeitar.

6. Selecione **Ok** e, em seguida, selecione **Criar**.

## <a name="assign-terms-and-conditions"></a>Atribuir termos e condições

Pode atribuir termos e condições a grupos de utilizadores que devem aceitá-los antes de utilizar o Portal da Empresa.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrição de dispositivos** e, em seguida, escolha **Termos e Condições**.

3. Na lista de termos e condições, selecione os termos que pretende atribuir e, em seguida, selecione **Grupos Atribuídos**.
![Captura de ecrã do painel Atribuir Grupo do portal do Intune a mostrar os botões Selecionar Grupo e Selecionar para a atribuição dos termos e condições](media/terms-assign-groups.png)

4. Clique no botão **Selecionar Grupo** e, no painel **Selecionar Grupos**, selecione os grupos aos quais pretende atribuir os termos e, em seguida, clique em **Selecionar**.

5. No painel **Grupos Atribuídos**, clique em **Guardar**.  Os termos e condições estão agora atribuídos aos utilizadores nos grupos selecionados. Será pedido aos utilizadores que aceitem os termos da próxima vez que acederem ao portal da empresa.

   ![Captura de ecrã do ecrã de aceitação dos termos e condições do utilizador final com um resumo dos termos](./media/terms-summary-accept.png)

## <a name="monitor-a-terms-and-conditions"></a>Monitorizar os termos e condições

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**. No painel Intune, escolha **Inscrição de dispositivos** e, em seguida, escolha **Termos e Condições**.
2. Na lista de termos e condições, selecione os termos nos quais pretende ver a aceitação e, em seguida, selecione **Estados de Aceitação**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Trabalhar com múltiplas versões de termos e condições
Pode editar os seus termos e condições e gerir as respetivas versões. Recomendamos que aumente o número da versão e solicite a aceitação sempre que efetua alterações significativas nos seus termos e condições. Mantenha o número da versão atual se, por exemplo, estiver a corrigir erros de digitação ou a alterar a formatação.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrição de dispositivos**, depois, **Termos e Condições**, selecione os termos e condições que pretende modificar e, em seguida, selecione **Propriedades**.

4. No painel **Propriedades**, selecione **Termos e Condições** e, em seguida, modifique o **Título**, **Resumo dos Termos** e **Termos e Condições**, conforme necessário. Se as alterações que efetuou tornam necessário aos utilizadores aceitar novamente os novos termos, clique em **Exigir que os utilizadores voltem a aceitar e incrementar o número de versão**

4.  Selecione **OK** e, em seguida, selecione **Guardar**.

