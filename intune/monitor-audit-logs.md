---
title: Auditar alterações e eventos no Microsoft Intune – Azure | Documentos da Microsoft
description: Saiba como rever os registos de auditoria que registam as atividades do Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d01b1f745450785209bf289be5b6e36ac65cc2d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046311"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Utilize registos de auditoria para controlar e monitorizar os eventos no Microsoft Intune

Registos de auditoria incluem um registo de atividades que geram uma alteração no Microsoft Intune. Criar, atualizar (editar), eliminar, atribuir e ações remotas todos os criam eventos de auditoria que os administradores podem rever para a maioria das cargas de trabalho do Intune. Por predefinição, a auditoria está ativada para todos os clientes. Não pode ser desativada.

> [!NOTE]
> Auditar eventos de comecei a gravar sobre a versão da funcionalidade de Dezembro de 2017. Eventos anteriores não estão disponíveis.

## <a name="who-can-access-the-data"></a>Quem pode aceder aos dados?

Os utilizadores com as seguintes permissões podem rever os registos de auditoria:

- Administrador Global
- Administrador de Serviços do Intune
- Administradores atribuídos a uma função do Intune com as permissões **Dados de auditoria** - **Leitura**

## <a name="audit-logs-for-intune-workloads"></a>Registos de auditoria das cargas de trabalho do Intune

Pode rever os registos de auditoria no grupo de monitorização para cada carga de trabalho do Intune:

1. No [portal do Azure](https://portal.azure.com/), selecione **Todos os serviços** > filtre o **Intune** > selecione  **Intune**.
2. Escolha a carga de trabalho que pretende rever os registos de auditoria. Por exemplo, seleccione **dispositivos**.
3. Sob **monitorização**, escolha **registos de auditoria**.

## <a name="route-logs-to-azure-monitor"></a>Registos de rota para o Azure Monitor

Registos de auditoria e registos operacionais também podem ser encaminhados para o Azure Monitor. Na **registos de auditoria**, selecione **exportar definições de dados**:

![Exportar dados de registo para o Azure monitor ao selecionar as definições de exportação de dados no Intune](./media/audit-logs-export-data-settings.png)

Para obter mais informações sobre esta funcionalidade, consulte [enviar dados de registo para o armazenamento, os hubs de eventos ou do log analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Rever eventos de auditoria

![Escolha os registos de auditoria no Intune para ver as ações e datas quando os eventos aconteceram](./media/monitor-audit-logs.png "registos de auditoria")

Um registo de auditoria tem uma vista de lista predefinida que mostra os seguintes itens:

- Data e hora da ocorrência
- Iniciado por (Ator)
- Nome da Aplicação
- Atividade
- Destino(s)
- Category
- Estado

Para ver informações mais específicas sobre um evento, selecione um item na lista:

![Obtenha informações mais específicas sobre quem fez o que na auditoria inicia sessão no Intune](./media/monitor-audit-log-detail.png "detalhes do registo de auditoria")

> [!NOTE]
> **Iniciado por (ator)** inclui informações sobre quem executou a tarefa e, em que foi executado. Por exemplo, se executar a atividade no Intune no portal do Azure, em seguida, **aplicativo** indica sempre **extensão de portal do Microsoft Intune** e o **ID da aplicação** sempre utiliza o mesmo GUID.
> 
> O **destino (s)** seção apresenta uma lista de vários destinos e as propriedades que foram alteradas.  

## <a name="filter-audit-events"></a>Filtrar eventos de auditoria

Cada carga de trabalho tem um item de menu que filtra previamente a categoria de eventos de auditoria associados a esse painel. Uma opção de filtro em separado permite-lhe mudar para diferentes categorias e para os detalhes da ação do evento dentro dessa categoria. Pode pesquisar por UPN, por exemplo, o utilizador que realizou a ação. Um filtro de intervalo de datas permite opções de 24 horas, 7 dias ou 30 dias. Por predefinição, são apresentados os últimos 30 dias de eventos de auditoria.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utilizar a Graph API para obter eventos de auditoria

Para obter detalhes sobre como utilizar a graph API para obter até um ano de eventos de auditoria, veja [listar auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Passos Seguintes

[Enviar dados de registo para o armazenamento, os hubs de eventos ou do log analytics](review-logs-using-azure-monitor.md).

[Rever registos de proteção de aplicações de cliente](app-protection-policy-settings-log.md).
