---
title: Auditar alterações e eventos no Microsoft Intune-Azure | Microsoft Docs
description: Saiba como rever os registos de auditoria que registam as atividades do Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4be1755a07e6ec304edb7bceba8041d5b58263e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510001"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Usar logs de auditoria para acompanhar e monitorar eventos no Microsoft Intune

Os logs de auditoria incluem um registro de atividades que geram uma alteração no Microsoft Intune. Criar, atualizar (editar), excluir, atribuir e ações remotas criam eventos de auditoria que os administradores podem examinar para a maioria das cargas de trabalho do Intune. Por padrão, a auditoria está habilitada para todos os clientes. Ele não pode ser desabilitado.

> [!NOTE]
> Eventos de auditoria começaram a gravação na versão do recurso de dezembro de 2017. Os eventos anteriores não estão disponíveis.

## <a name="who-can-access-the-data"></a>Quem pode aceder aos dados?

Os utilizadores com as seguintes permissões podem rever os registos de auditoria:

- Administrador Global
- Administrador de Serviços do Intune
- Administradores atribuídos a uma função do Intune com as permissões **Dados de auditoria** - **Leitura**

## <a name="audit-logs-for-intune-workloads"></a>Registos de auditoria das cargas de trabalho do Intune

Você pode examinar os logs de auditoria no grupo de monitoramento para cada carga de trabalho do Intune:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Escolha a carga de trabalho que você deseja examinar os logs de auditoria. Por exemplo, selecione **dispositivos**.
3. Em **monitoramento**, escolha **logs de auditoria**.

## <a name="route-logs-to-azure-monitor"></a>Rotear logs para Azure Monitor

Os logs de auditoria e os logs operacionais também podem ser roteados para Azure Monitor. Em **logs de auditoria**, selecione **exportar configurações de dados**:

![Exportar dados de log para o Azure monitor selecionando configurações de dados de exportação no Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

Para obter mais informações sobre esse recurso, consulte [enviar dados de log para armazenamento, hubs de eventos ou log Analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Rever eventos de auditoria

![Escolha logs de auditoria no Intune para ver as ações e datas em que os eventos ocorreram](./media/monitor-audit-logs/monitor-audit-logs.png "Logs de auditoria")

Um registo de auditoria tem uma vista de lista predefinida que mostra os seguintes itens:

- Data e hora da ocorrência
- Iniciado por (Ator)
- Nome do aplicativo
- Atividade
- Destino(s)
- Category
- Estado

Para ver informações mais específicas sobre um evento, selecione um item na lista:

![Obter informações mais específicas sobre quem fez o que nos logs de auditoria no Intune](./media/monitor-audit-logs/monitor-audit-log-detail.png "Detalhes do log de auditoria")

> [!NOTE]
> **Iniciado por (ator)** inclui informações sobre quem executou a tarefa e onde ela foi executada. Por exemplo, se você executar a atividade no Intune na portal do Azure, o **aplicativo** sempre listará **Microsoft Intune extensão do portal** e a **ID do aplicativo** sempre usará o mesmo GUID.
> 
> A seção **destino (s)** lista vários destinos e as propriedades que foram alteradas.  

## <a name="filter-audit-events"></a>Filtrar eventos de auditoria

Cada carga de trabalho tem um item de menu que filtra previamente a categoria de eventos de auditoria associados a esse painel. Uma opção de filtro em separado permite-lhe mudar para diferentes categorias e para os detalhes da ação do evento dentro dessa categoria. Você pode pesquisar por UPN, como o usuário que fez a ação. Um filtro de intervalo de datas permite opções de 24 horas, 7 dias ou 30 dias. Por padrão, os últimos 30 dias de eventos de auditoria são mostrados.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utilizar a Graph API para obter eventos de auditoria

Para obter detalhes sobre como usar a API do Graph para obter até um ano de eventos de auditoria, consulte [list auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Próximos passos

[Enviar dados de log para armazenamento, hubs de eventos ou log Analytics](review-logs-using-azure-monitor.md).

[Examine os logs de proteção do aplicativo cliente](../apps/app-protection-policy-settings-log.md).
