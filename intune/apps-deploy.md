---
title: "Como atribuir aplicações a grupos no Microsoft Intune"
titlesuffix: 
description: "Após adicionar uma aplicação ao Microsoft Intune, irá atribuí-la a grupos de utilizadores ou dispositivos."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78a9e9f4af41cdb97efd017eec56e676eda82856
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2018
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
|Receber atualizações de aplicações a partir do Intune|Sim|Não|
|Os utilizadores finais instalam as aplicações disponíveis a partir da aplicação Portal da Empresa|Sim|Não|
|Os utilizadores finais instalam as aplicações disponíveis a partir do Portal da Empresa baseado na Web|Sim|Sim|

> [!NOTE]
> Atualmente, pode atribuir aplicações iOS e Android (tanto de linha empresarial como compradas na loja) a dispositivos que não estão inscritos no Intune.<br></br><br></br>
> Para receber atualizações de aplicações em dispositivos que não estão inscritos no Intune, os utilizadores têm de navegar para a respetiva aplicação Portal da Empresa e instalar as atualizações das aplicações manualmente.

## <a name="how-to-assign-an-app"></a>Como atribuir uma aplicação

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Aplicações móveis**.
1. Na carga de trabalho **Aplicações Móveis**, escolha **Gerir** > **Aplicações**.
2. No painel da lista de aplicações, clique na aplicação que quer atribuir.
3. No painel **Descrição Geral**, selecione **Gerir** > **Atribuições**.
4. Selecione **Adicionar Grupo** e, em seguida, no painel **Adicionar grupo**, selecione grupos do Azure AD a incluir ou excluir da atribuição da aplicação.
5. Para cada aplicação que escolher, selecione um **tipo de atribuição** para a aplicação em:
    - **Disponível para dispositivos inscritos** – os utilizadores instalam a aplicação a partir da aplicação ou site Portal da Empresa.
    - **Disponível com ou sem inscrição** – Atribua esta aplicação a grupos de utilizadores cujos dispositivos não estão inscritos no Intune.
    - **Obrigatório** – A aplicação é instalada em dispositivos nos grupos selecionados.
    - **Desinstalar** – A aplicação é desinstalada dos dispositivos nos grupos selecionados.
6. **Apenas para aplicações iOS** – se tiver criado um perfil VPN de iOS que contenha definições de VPN por aplicação, pode selecioná-lo em **VPN**. Quando a aplicação for executada, a ligação VPN será aberta. Para obter mais informações, veja [Definições VPN para dispositivos iOS](vpn-settings-ios.md).
6. Quando terminar, selecione **OK** e, em seguida, selecione **Guardar**.

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

## <a name="next-steps"></a>Passos seguintes

Veja [Como monitorizar aplicações](apps-monitor.md) para obter informações que o ajudam a monitorizar as atribuições de aplicações.
