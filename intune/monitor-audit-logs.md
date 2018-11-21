---
title: Registos de auditoria para atividades do Microsoft Intune
description: Saiba como rever os registos de auditoria que registam as atividades do Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.openlocfilehash: d9ecfa44e2619e5e123c9e8af169b6a8a95ee466
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183898"
---
# <a name="audit-logs-for-intune-activities"></a>Registos de auditoria para atividades do Intune
Os registos de auditoria proporcionam um registo das atividades que geram uma alteração no Microsoft Intune. As tarefas remotas ou as ações Criar, Atualizar (editar), Eliminar e Atribuir geram eventos de auditoria que poderá rever. Pode rever os registos de auditoria da maioria das cargas de trabalho do Intune. A auditoria é ativada por predefinição para todos os clientes e não pode ser desativada. Os eventos de auditoria começaram a ser registados na data de lançamento de funcionalidades de dezembro de 2017. Os eventos anteriores a essa data não estão disponíveis.

## <a name="who-can-access-the-data"></a>Quem pode aceder aos dados?
Os utilizadores com as seguintes permissões podem rever os registos de auditoria:
- Administrador Global
- Administrador de Serviços do Intune
- Administradores atribuídos a uma função do Intune com as permissões **Dados de auditoria** - **Leitura**

## <a name="audit-logs-for-intune-workloads"></a>Registos de auditoria das cargas de trabalho do Intune
Pode rever os registos de auditoria no grupo Monitorização de cada carga de trabalho do Intune.  
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione a carga de trabalho para a qual pretende rever os relatórios de auditoria, por exemplo, **Dispositivos**.
4. No grupo **Monitorização** da carga de trabalho, escolha **Registos de auditoria**.

## <a name="review-audit-events"></a>Rever eventos de auditoria
![Registos de auditoria](./media/monitor-audit-logs.png "Registos de auditoria")

Um registo de auditoria tem uma vista de lista predefinida que mostra os seguintes itens:    

- data e hora da ocorrência
- Iniciado por (Ator)
- Nome da Aplicação
- Atividade
- Destino(s)
- Categoria
- Estado

Ao clicar num item na vista de lista, obtém todos os detalhes disponíveis sobre o mesmo.

![Registos de auditoria](./media/monitor-audit-log-detail.png "Registos de auditoria")

> [!Note]    
> A secção **Iniciado por (Ator)** nos detalhes do registo de auditoria apresenta informações sobre quem realizou a atividade e o local onde foi realizada. Por exemplo, se realizar a atividade no Intune no portal do Azure, a **Aplicação** indica sempre a **extensão do portal do Microsoft Intune** e o **ID da Aplicação** utiliza sempre o mesmo GUID. 
>    
> A secção **Destino(s)** pode indicar vários destinos e as propriedades que foram alteradas.  


## <a name="filter-audit-events"></a>Filtrar eventos de auditoria
Cada carga de trabalho tem um item de menu que filtra previamente a categoria de eventos de auditoria associados a esse painel. Uma opção de filtro em separado permite-lhe mudar para diferentes categorias e para os detalhes da ação do evento dentro dessa categoria. Pode pesquisar por UPN (por exemplo, o utilizador que realizou a ação). Um filtro de intervalo de datas permite opções de 24 horas, 7 dias ou 30 dias. Por predefinição, são apresentados os últimos 30 dias de eventos de auditoria.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utilizar a Graph API para obter eventos de auditoria
Para obter mais informações sobre como utilizar a Graph API para obter até um ano de eventos de auditoria, veja [Listar auditEvents](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list).