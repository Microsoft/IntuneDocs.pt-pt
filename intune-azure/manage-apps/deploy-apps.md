---
title: "Como atribuir aplicações a grupos"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: depois de adicionar uma aplicação ao Intune, deve atribuí-la a grupos de utilizadores ou dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b372d4ee505ca39a4739069e5798918ecde134ea
ms.openlocfilehash: abf45b835d13ef5fe4acb769194542611448504e
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Como atribuir aplicações a grupos com o Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Depois de adicionar uma aplicação ao Intune, vai querer disponibilizá-la para os utilizadores e os dispositivos. Para tal, basta atribuí-la.

As aplicações podem ser atribuídas a dispositivos, independentemente de estes serem geridos pelo Intune. Utilize a tabela seguinte para compreender melhor as várias opções para atribuir as aplicações a utilizadores e a dispositivos:

||||
|-|-|-|-|
|&nbsp;|Dispositivos inscritos com o Intune|Dispositivos não inscritos com o Intune|
|Atribuir a utilizadores|Sim|Sim|
|Atribuir a dispositivos|Sim|Não|
|Atribuir aplicações encapsuladas ou aplicações que incorporem o SDK do Intune (para políticas de proteção de aplicações)|Sim|Sim|
|Atribuir aplicações como Disponíveis|Sim|Sim|
|Atribuir aplicações como Obrigatórias|Sim|Não|
|Desinstalar aplicações|Sim|Sim|
|Os utilizadores finais instalam as aplicações disponíveis a partir da aplicação do Portal da Empresa|Sim|Não|
|Os utilizadores finais instalam as aplicações disponíveis a partir do Portal da Empresa baseado na Web|Sim|Sim|

> [!NOTE]
> Atualmente, pode atribuir aplicações iOS e Android (tanto de linha empresarial como compradas na loja) a dispositivos que não estão inscritos no Intune.

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>Alterações à forma como atribui aplicações a grupos na pré-visualização do Intune

Na pré-visualização do Azure no Intune, deixará de utilizar os grupos do Intune para atribuir aplicações. Em vez disso, passará a utilizar os grupos de segurança do Azure Active Directory (Azure AD). Por este motivo, terá de saber mais sobre as alterações ao funcionamento de atribuição de aplicações, em particular nos casos em que atribuiu aplicações a grupos subordinados do Intune.
O aspeto mais importante a ter em atenção é que o conceito de grupos subordinados não existe no Azure AD. No entanto, alguns grupos poderão conter os mesmos membros. Neste caso, o comportamento entre o Intune clássico e a pré-visualização do Azure no Intune é diferente. A tabela seguinte ilustra isso mesmo:

||||||
|-|-|-|-|-|
|**Intune Clássico (antes da migração do inquilino)**|-|**Intune Azure (após a migração do inquilino estar concluída)**|-|**Mais informações**|
|**Objetivo de implementação de grupos principais**|**Objetivo de implementação de grupos subordinados**|**Objetivo de atribuição resultante para os membros comuns de grupos principais e subordinados anteriores**|**Ação resultante do objetivo de atribuição para os membros do grupo principal**|-|    
|Disponível|Necessário|Necessário e Disponível|Disponível|O objetivo de implementação Necessário e Disponível significa que as aplicações atribuídas como necessárias também podem ser vistas na aplicação Portal da Empresa.
|Não Aplicável|Disponível|Não Aplicável|Não Aplicável|Solução: remova o objetivo de implementação "Não Aplicável" do grupo principal do Intune.
|Necessário|Disponível|Necessário e Disponível|Necessário|-|
|Necessário e Disponível<sup>1</sup>|Disponível|Necessário e Disponível|Necessário e Disponível|-|    
|Necessário|Não Aplicável|Necessário|Necessário|-|    
|Necessário e Disponível|Não Aplicável|Necessário e Disponível|Necessário e Disponível|-|    
|Necessário|Desinstalar|Necessário|Necessário|-|    
|Necessário e Disponível|Desinstalar|Necessário e Disponível|Necessário e Disponível|-|
<sup>1</sup> Apenas para aplicações da loja iOS geridas. Quando as adiciona ao Intune e as implementa como Necessário, estas aplicações são criadas automaticamente com os objetivos Necessário e Disponível.

Pode efetuar as seguintes ações de modo a evitar conflitos de implementação:

1.    Se implementou aplicações em grupos principais e subordinados relacionados do Intune anteriormente, pondere remover essas implementações antes de iniciar a migração do seu inquilino.
2.    Remova os grupos subordinados dos grupos principais e crie um novo grupo com os membros do grupo subordinado antigo. Em seguida, poderá criar uma nova implementação de aplicações para este grupo.
Notas: se o tipo de grupo principal anterior era "Todos os Utilizadores", terá de criar um novo grupo dinâmico que não inclua membros do grupo subordinado.
Terá de efetuar as alterações necessárias aos grupos de utilizadores e dispositivos no [Portal do Azure](https://portal.azure.com/). O [Portal do Azure Clássico](https://manage.windowsazure.com/) só lhe permitirá efetuar alterações a grupos de utilizadores.


## <a name="how-to-assign-an-app"></a>Como atribuir uma aplicação

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Gerir aplicações**.
1. Na carga de trabalho **Gerir Aplicações**, escolha **Gerir** > **Aplicações**.
2. No painel da lista de aplicações, clique na aplicação que quer atribuir.
3. No painel <*nome da aplicação*> – **Descrição geral**, escolha **Gerir** > **Atribuições**.
4. Escolha **Selecionar Grupos** e, no painel **Selecionar grupos**, escolha os grupos do Azure AD aos quais pretende atribuir a aplicação.
5. Para cada aplicação que escolher, selecione um **tipo de atribuição** para a aplicação em:
    - **Disponível** – Os utilizadores instalam a aplicação a partir do site ou da aplicação do Portal da Empresa.
    - **Não Aplicável** – A aplicação não é instalada nem apresentada no Portal da Empresa.
    - **Obrigatório** – A aplicação é instalada em dispositivos nos grupos selecionados.
    - **Desinstalar** – A aplicação é desinstalada dos dispositivos nos grupos selecionados.
    - **Disponível com ou sem inscrição** – Atribua esta aplicação a grupos de utilizadores cujos dispositivos não estão inscritos no Intune. Veja a tabela acima para obter ajuda.
6. Assim que tiver terminado, escolha **Guardar**.

A aplicação está agora atribuída ao grupo que escolheu.

Veja [Como monitorizar aplicações](monitor-apps.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.

