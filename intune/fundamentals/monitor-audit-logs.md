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
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991986"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Usar logs de auditoria para acompanhar e monitorar eventos no Microsoft Intune

Os logs de auditoria incluem um registro de atividades que geram uma alteração no Microsoft Intune. Criar, atualizar (editar), excluir, atribuir e ações remotas criam eventos de auditoria que os administradores podem examinar para a maioria das cargas de trabalho do Intune. Por padrão, a auditoria está habilitada para todos os clientes. Não pode ser desativado.

> [!NOTE]
> Eventos de auditoria começaram a gravação na versão do recurso de dezembro de 2017. Os eventos anteriores não estão disponíveis.

## <a name="who-can-access-the-data"></a>Quem pode aceder aos dados?

Os utilizadores com as seguintes permissões podem rever os registos de auditoria:

- Administrador Global
- Administrador de Serviços do Intune
- Administradores atribuídos a uma função do Intune com as permissões **Dados de auditoria** - **Leitura**

## <a name="audit-logs-for-intune-workloads"></a>Registos de auditoria das cargas de trabalho do Intune

Você pode examinar os logs de auditoria no grupo de monitoramento para cada carga de trabalho do Intune:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Administração de locatário** > **logs de auditoria**.
3. Para filtrar os resultados, selecione **Filtrar** e refine os resultados usando as opções a seguir.
    - **Categoria**: como **conformidade**, **dispositivo**e **função**.
    - **Atividade**: as opções listadas aqui são restritas pela opção escolhida em **categoria**.
    - **Intervalo de datas**: você pode escolher os logs para o mês, a semana ou o dia anterior.
4. Escolha **Aplicar**.
4. Selecione um item na lista para ver os detalhes da atividade.

## <a name="route-logs-to-azure-monitor"></a>Rotear logs para Azure Monitor

Os logs de auditoria e os logs operacionais também podem ser roteados para Azure Monitor. Em **logs de auditoria**, selecione **exportar configurações de dados**:

![Exportar dados de log para o Azure monitor selecionando configurações de dados de exportação no Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> Para obter mais informações sobre esse recurso e revisar os pré-requisitos para usá-lo, consulte [enviar dados de log para armazenamento, hubs de eventos ou log Analytics](review-logs-using-azure-monitor.md).

> [!NOTE]
> **Iniciado por (ator)** inclui informações sobre quem executou a tarefa e onde ela foi executada. Por exemplo, se você executar a atividade no Intune na portal do Azure, o **aplicativo** sempre listará **Microsoft Intune extensão do portal** e a **ID do aplicativo** sempre usará o mesmo GUID.
>
> A seção **destino (s)** lista vários destinos e as propriedades que foram alteradas.  

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utilizar a Graph API para obter eventos de auditoria

Para obter detalhes sobre como usar a API do Graph para obter até um ano de eventos de auditoria, consulte [list auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Próximos passos

[Enviar dados de log para armazenamento, hubs de eventos ou log Analytics](review-logs-using-azure-monitor.md).

[Examine os logs de proteção do aplicativo cliente](../apps/app-protection-policy-settings-log.md).
