---
title: Atribuir aplicações a grupos no Microsoft Intune
titlesuffix: ''
description: Saiba como atribuir uma aplicação do Intune para grupos de utilizadores ou dispositivos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99eb2c70994fcb2b6ed116530f4a82d8db7bcb9b
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2018
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Atribuir aplicações a grupos com o Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Depois de adicionar uma aplicação ao Microsoft Intune, pode atribuí-la a utilizadores e dispositivos.

Pode atribuir uma aplicação a um dispositivo quer este seja ou não gerido pelo Intune. 

A tabela seguinte indica as várias opções para atribuir as aplicações a utilizadores e a dispositivos:

||||
|-|-|-|-|
|&nbsp;|**Dispositivos inscritos com o Intune**|**Dispositivos não inscritos com o Intune**|
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
> Atualmente, pode atribuir aplicações iOS e Android (tanto de linha de negócio como compradas na loja) a dispositivos que não estão inscritos no Intune.
>
> Para receber atualizações de aplicações em dispositivos que não estão inscritos no Intune, os utilizadores dos dispositivos têm de navegar até ao Portal da Empresa da organização e instalar as atualizações das aplicações manualmente.

## <a name="to-assign-an-app"></a>Para atribuir uma aplicação

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No menu **Intune**, selecione **Aplicações móveis**.
4. Na secção **Gerir** do menu, selecione **Aplicações**.
5. No painel **Aplicações**, selecione a aplicação que quer atribuir.
6. Na secção **Gerir** do menu, selecione **Atribuições**.
7. Selecione **Adicionar Grupo** para abrir o painel **Adicionar grupo** que está relacionado com a aplicação.
8. Para a aplicação específica, selecione um **tipo de atribuição**:
   - **Disponível para dispositivos inscritos**: os utilizadores instalam a aplicação a partir da aplicação ou site Portal da Empresa.
   - **Disponível com ou sem inscrição**: atribua esta aplicação a grupos de utilizadores cujos dispositivos não estão inscritos no Intune. O tipo **Aplicação Android for Work** não suporta esta opção. 
   - **Obrigatório**: a aplicação é instalada em dispositivos nos grupos selecionados.
   - **Desinstalar**: a aplicação é desinstalada dos dispositivos nos grupos selecionados.

     > [!NOTE]
     > **Apenas para aplicações iOS**: se tiver criado um perfil VPN de iOS que contenha definições de VPN por aplicação, poderá selecionar o perfil VPN em **VPN**. Quando a aplicação for executada, a ligação VPN será aberta. Para obter mais informações, veja [Definições VPN para dispositivos iOS](vpn-settings-ios.md).

9. Selecione **Grupos Incluídos** para selecionar os grupos de utilizadores que são afetados por esta atribuição de aplicações.
10. Escolha **Selecionar** após selecionar um ou mais grupos para incluir.
11. No painel **Atribuir**, selecione **OK** para concluir a seleção de grupos incluídos.
12. Selecione **Excluir Grupos** se quiser excluir grupos de utilizadores de serem afetados por esta atribuição de aplicações.
13. Se tiver optado por excluir grupos, em **Selecionar grupos**, selecione **Selecionar**.
14. No painel **Adicionar grupo**, selecione **OK**.
15. No painel **Atribuições** de aplicações, selecione **Guardar**.

A aplicação está agora atribuída aos grupos que selecionou. Para obter mais informações sobre como incluir e excluir atribuições de aplicações, veja [Incluir e excluir atribuições de aplicações](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Como são resolvidos conflitos entre objetivos de aplicações

Por vezes, a mesma aplicação é atribuída a múltiplos grupos, mas com intenções diferentes. As informações na tabela seguinte podem ajudar a compreender a intenção resultante quando ocorre o seguinte:

||||
|-|-|-|
|**Intenção do grupo 1**|**Intenção do grupo 2**|**Intenção resultante**|
|Utilizador – Necessário|Utilizador – Disponível|Necessário e Disponível|
|Utilizador – Necessário|Utilizador – Não Disponível|Necessário|
|Utilizador – Necessário|Utilizador – Desinstalar|Necessário|
|Utilizador – Disponível|Utilizador – Não Disponível|Não disponível|
|Utilizador – Disponível|Utilizador – Desinstalar|Desinstalar|
|Utilizador – Não Disponível|Utilizador – Desinstalar|Desinstalar
|Utilizador – Necessário|Dispositivo – Necessário|Ambas existem, o Gateway trata da intenção Necessário
|Utilizador – Necessário|Dispositivo – Desinstalar|Ambas existem, o Gateway resolve a intenção Necessário
|Utilizador – Disponível|Dispositivo – Necessário|Ambas existem, o Gateway resolve a intenção Necessário (Necessário e Disponível)
|Utilizador – Disponível|Dispositivo – Desinstalar|Ambas existem, o Gateway resolve a intenção Disponível.<br><br>A aplicação é apresentada no Portal da Empresa.<br><br>Se a aplicação já estiver instalada (como aplicação necessária com a intenção anterior), será desinstalada.<br><br>Se o utilizador selecionar **Instalar a partir do Portal da Empresa**, a aplicação será instalada e a intenção de desinstalação não será cumprida.|
|Utilizador – Não Disponível|Dispositivo – Necessário|Necessário|
|Utilizador – Não Disponível|Dispositivo – Desinstalar|Desinstalar|
|Utilizador – Desinstalar|Dispositivo – Necessário|Ambas existem, o Gateway resolve a intenção Necessário|
|Utilizador – Desinstalar|Dispositivo – Desinstalar|Ambos existem, o Gateway resolve o objetivo Desinstalar|
|Dispositivo – Necessário|Dispositivo – Desinstalar|Necessário|
|Utilizador – Necessário e Disponível|Utilizador – Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Utilizador – Desinstalar|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Utilizador – Não Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Dispositivo – Necessário|Ambas existem, Necessário e Disponível
|Utilizador – Necessário e Disponível|Dispositivo – Não Disponível|Necessário e Disponível|
|Utilizador – Necessário e Disponível|Dispositivo – Desinstalar|Ambas existem, o Gateway resolve a intenção Necessário (Necessário e Disponível)
|Utilizador – Não Disponível|Dispositivo – Não Disponível|Não disponível|
|Utilizador – Disponível|Dispositivo – Não Disponível|Disponível|
|Utilizador – Necessário|Dispositivo – Não Disponível|Necessário|
|Utilizador – Disponível sem inscrição|Utilizador – Necessário e Disponível|Necessário e Disponível
|Utilizador – Disponível sem inscrição|Utilizador – Necessário|Necessário
|Utilizador – Disponível sem inscrição|Utilizador – Não Disponível|Não disponível
|Utilizador – Disponível sem inscrição|Utilizador – Disponível|Disponível|
|Utilizador – Disponível sem inscrição|Dispositivo – Necessário|Necessário e Disponível sem inscrição|
|Utilizador – Disponível sem inscrição|Dispositivo – Não Disponível|Disponível sem inscrição|
|Utilizador – Disponível sem inscrição|Dispositivo – Desinstalar|Desinstalar e Disponível sem inscrição.<br><br>Se o utilizador não tiver instalado a aplicação a partir do Portal da Empresa, a desinstalação é cumprida.<br><br>Se o utilizador instalar a aplicação a partir do Portal da Empresa, a instalação terá prioridade sobre a desinstalação.|

> [!NOTE]
> Apenas para aplicações da loja iOS geridas: quando adiciona estas aplicações ao Microsoft Intune e as atribui como **Necessário**, estas aplicações são criadas automaticamente com as intenções **Necessário** e **Disponível**.

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre a monitorização de atribuições de aplicações, veja [Como monitorizar aplicações](apps-monitor.md).
