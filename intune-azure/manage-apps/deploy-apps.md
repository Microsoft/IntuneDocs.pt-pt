---
title: "Como atribuir aplicações a grupos | Pré-visualização do Azure no Intune | Documentos da Microsoft"
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
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 638ad0d87c19c9e40e96b42d18e5c4342f40a156
ms.lasthandoff: 02/16/2017

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

