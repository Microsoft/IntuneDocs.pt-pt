---
title: "Como atribuir aplicações a grupos"
titlesuffix: Azure portal
description: "Depois de adicionar uma aplicação ao Intune, deve atribuí-la a grupos de utilizadores ou dispositivos.\""
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc4732043153662ac83beac950d53246caff1b94
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Como atribuir aplicações a grupos com o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Depois de adicionar uma aplicação ao Intune, pode atribui-la a utilizadores e dispositivos.

As aplicações podem ser atribuídas a dispositivos, independentemente de estes serem geridos pelo Intune. Utilize a tabela seguinte para compreender melhor as várias opções para atribuir as aplicações a utilizadores e a dispositivos:

||||
|-|-|-|-|
|&nbsp;|Dispositivos inscritos com o Intune|Dispositivos não inscritos com o Intune|
|Atribuir a utilizadores|Sim|Sim|
|Atribuir a dispositivos|Sim|Não|
|Atribuir aplicações encapsuladas ou aplicações que incorporem o SDK do Intune (para políticas de proteção de aplicações)|Sim|Sim|
|Atribuir aplicações como Disponíveis|Sim|Sim|
|Atribuir aplicações como Obrigatórias|Sim|Não|
|Desinstalar aplicações|Sim|Não|
|Os utilizadores finais instalam as aplicações disponíveis a partir da aplicação Portal da Empresa|Sim|Não|
|Os utilizadores finais instalam as aplicações disponíveis a partir do Portal da Empresa baseado na Web|Sim|Sim|

> [!NOTE]
> Atualmente, pode atribuir aplicações iOS e Android (tanto de linha empresarial como compradas na loja) a dispositivos que não estão inscritos no Intune.

## <a name="how-to-assign-an-app"></a>Como atribuir uma aplicação

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1. Na carga de trabalho **Aplicações Móveis**, escolha **Gerir** > **Aplicações**.
2. No painel da lista de aplicações, clique na aplicação que quer atribuir.
3. No painel <*nome da aplicação*> – **Descrição geral**, escolha **Gerir** > **Atribuições**.
4. Escolha **Selecionar Grupos** e, no painel **Selecionar grupos**, escolha os grupos do Azure AD aos quais pretende atribuir a aplicação.
5. Para cada aplicação que escolher, selecione um **tipo de atribuição** para a aplicação em:
    - **Disponível** – Os utilizadores instalam a aplicação a partir do site ou da aplicação Portal da Empresa.
    - **Não Aplicável** – A aplicação não é instalada nem apresentada no Portal da Empresa.
    - **Obrigatório** – A aplicação é instalada em dispositivos nos grupos selecionados.
    - **Desinstalar** – A aplicação é desinstalada dos dispositivos nos grupos selecionados.
    - **Disponível com ou sem inscrição** – Atribua esta aplicação a grupos de utilizadores cujos dispositivos não estão inscritos no Intune.
6. **Apenas para aplicações iOS** – se tiver criado um perfil VPN de iOS que contenha definições de VPN por aplicação, pode selecioná-lo em **VPN**. Quando a aplicação for executada, a ligação VPN será aberta. Para obter mais informações, veja [Definições VPN para dispositivos iOS](vpn-settings-ios.md).
6. Assim que tiver terminado, escolha **Guardar**.

A aplicação está agora atribuída aos grupos que selecionou.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Como são resolvidos conflitos entre objetivos de aplicações

Por vezes, a mesma aplicação é atribuída a múltiplos grupos, mas com objetivos diferentes. Nestes casos, utilize esta tabela para compreender o objetivo resultante.

||||
|-|-|-|
|Objetivo do grupo 1|Objetivo do grupo 2|Objetivo resultante|
|Utilizador – Necessário|Utilizador – Disponível|Necessário e Disponível|
|Utilizador – Necessário|Utilizador – Não Disponível|Necessário|
|Utilizador – Necessário|Utilizador – Desinstalar|Necessário|
|Utilizador – Disponível|Utilizador – Não Disponível|Não disponível|
|Utilizador – Disponível|Utilizador – Desinstalar|Desinstalar|
|Utilizador – Não Disponível|Utilizador – Desinstalar|Desinstalar
|Utilizador – Necessário|Dispositivo – Necessário|Ambos existem, o Gateway trata do objetivo Necessário 
|Utilizador – Necessário|Dispositivo – Desinstalar|Ambos existem, o Gateway resolve o objetivo Necessário 
|Utilizador – Disponível|Dispositivo – Necessário|Ambos existem, o Gateway resolve o objetivo Necessário (Necessário e Disponível)
|Utilizador – Disponível|Dispositivo – Desinstalar|Ambos existem, o Gateway resolve o objetivo Disponível.<br>A aplicação é apresentada no Portal da Empresa.<br>Se a aplicação já estiver instalada (como aplicação necessária com o objetivo anterior), será desinstalada.<br>No entanto, se o utilizador clicar em Instalar a partir do portal da empresa e, em seguida, a aplicação for instalada e desinstalada, o objetivo não será cumprido.|
|Utilizador – Não Disponível|Dispositivo – Necessário|Necessário|
|Utilizador – Não Disponível|Dispositivo – Desinstalar|Desinstalar|
|Utilizador – Desinstalar|Dispositivo – Necessário|Ambos existem, o Gateway resolve o objetivo Necessário|
|Utilizador – Desinstalar|Dispositivo – Desinstalar|Ambos existem, o Gateway resolve o objetivo Desinstalar|
|Dispositivo – Necessário|Dispositivo – Desinstalar|Necessário|
|Utilizador – Necessário e Disponível|Utilizador – Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Utilizador – Desinstalar|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Utilizador – Não Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Dispositivo – Necessário|Ambos existem, Necessário e Disponível
|Utilizador – Necessário e Disponível|Dispositivo – Não Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Dispositivo – Desinstalar|Ambos existem, o Gateway resolve o objetivo Necessário. Necessário + Disponível
|Utilizador – Não Disponível|Dispositivo – Não Disponível|Não disponível|
|Utilizador – Disponível|Dispositivo – Não Disponível|Disponível|
|Utilizador – Necessário|Dispositivo – Não Disponível|Necessário|
|Utilizador – Disponível sem inscrição|Utilizador – Necessário e Disponível|Necessário e Disponível
|Utilizador – Disponível sem inscrição|Utilizador – Necessário|Necessário
|Utilizador – Disponível sem inscrição|Utilizador – Não Disponível|Não disponível
|Utilizador – Disponível sem inscrição|Utilizador – Disponível|Disponível|
|Utilizador – Disponível sem inscrição|Dispositivo – Necessário|Necessário e Disponível sem inscrição|
|Utilizador – Disponível sem inscrição|Dispositivo – Não Disponível|Disponível sem inscrição|
|Utilizador – Disponível sem inscrição|Dispositivo – Desinstalar|Desinstalar e Disponível sem inscrição.<br>Se o utilizador não tiver instalado a aplicação a partir do portal da empresa, o objetivo Desinstalação é cumprido.<br>Se o utilizador instalar a aplicação a partir do portal da empresa, a instalação é priorizada em relação à desinstalação.|

>[!NOTE]
>Apenas para aplicações da loja iOS geridas: quando as adiciona ao Intune e as atribui como Necessário, estas aplicações são criadas automaticamente com os objetivos Necessário e Disponível.

## <a name="next-steps"></a>Próximos passos

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.
