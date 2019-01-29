---
title: Registos de auditoria de rota no monitor do Azure com o Microsoft Intune – Azure | Documentos da Microsoft
description: Utilize as definições de diagnóstico para enviar registos de auditoria e registos operacionais no Microsoft Intune para a conta de armazenamento do Azure, os hubs de eventos ou do log analytics. Escolha o período de tempo pretende manter os dados e ver que alguns custos estimados para os inquilinos de tamanho diferente.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6323eda16ef54df3cb14f9a8dd4f8349e51d1b01
ms.sourcegitcommit: 17f58d35a6bdff3e179662f3731fc74d39144470
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/28/2019
ms.locfileid: "55105158"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Enviar dados de registo para o armazenamento, os hubs de eventos ou do log analytics no Intune (pré-visualização)

O Microsoft Intune inclui os registos incorporados que fornecem informações sobre o seu ambiente. **Registos de auditoria** Mostrar detalhes sobre os diferentes eventos ou tarefas que ocorrem no Intune. **Registos operacionais (pré-visualização)** Mostrar detalhes em utilizadores e dispositivos ou com êxito (ou falha) para se inscrever.

Estes registos também podem ser enviados aos serviços do Azure Monitor, incluindo contas de armazenamento, os hubs de eventos e do log analytics. Especificamente, pode:

* Arquive registos do Intune a uma conta de armazenamento do Azure para manter os dados ou de arquivo para uma hora definida.
* Stream Intune registos para um hub de eventos do Azure para análise com ferramentas populares de informações de segurança e gestão de eventos (SIEM), como Splunk e QRadar.
* Integre registos do Intune com as suas próprias soluções de registo personalizado por transmissão em fluxo para um hub de eventos.
* Envie registos do Intune para o Log Analytics para ativar visualizações ricas, monitorização e os alertas nos dados ligados.

Esses recursos fazem parte do **as definições de diagnóstico** no Intune. 

Este artigo mostra-lhe como utilizar **as definições de diagnóstico** para enviar dados de registo para diferentes serviços, oferece exemplos e estimativas de custos e responde a algumas perguntas comuns.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar esta funcionalidade, terá de:

* Uma subscrição do Azure: Se não tiver uma subscrição do Azure, pode [Inscreva-se numa avaliação gratuita](https://azure.microsoft.com/free/).
* Um ambiente do Microsoft Intune (inquilino) no Azure
* Um utilizador que tem um **Administrador Global** ou **administrador de serviço do Intune** para o inquilino do Intune.

Dependendo de onde pretende encaminhar os dados de registo de auditoria, precisa de um dos seguintes serviços:

* Uma [conta de armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview) com *ListKeys* permissões. Recomendamos que utilize uma conta de armazenamento geral e não uma conta de armazenamento de Blobs. Para obter informações sobre preços de armazenamento, consulte a [Calculadora de preços do armazenamento do Azure](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Uma [espaço de nomes de hubs de eventos do Azure](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) para integrar com soluções de terceiros.
* Uma [área de trabalho do Azure log analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) para enviar registos para o Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Enviar registos para o Azure monitor

1. Na [portal do Azure](https://portal.azure.com/), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Sob **monitorização**, selecione **as definições de diagnóstico**. Na primeira vez que abri-lo, ativá-la:

    ![Ative as definições de diagnóstico no Intune para enviar registos para o Azure Monitor](media/diagnostics-settings-turn-on.png)

3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome para as definições de diagnóstico. Esta definição inclui todas as propriedades que introduzir. Por exemplo, introduza `Route audit logs to storage account`.
    - **Arquivo para uma conta de armazenamento**: Guarda os dados de registo para uma conta de armazenamento do Azure. Utilize esta opção se pretender guardar ou arquivar os dados.

        1. Selecione esta opção > **configurar**. 
        2. Escolha uma conta de armazenamento existente na lista > **OK**.

    - **Stream para um hub de eventos**: Transmite os registos para um hub de eventos do Azure. Se quiser que o serviço de análise nos seus dados de registo através de ferramentas SIEM, como Splunk e QRadar, escolha esta opção.

        1. Selecione esta opção > **configurar**. 
        2. Escolha uma existente espaço de nomes de hub de eventos e a política na lista > **OK**.

    - **Enviar para o Log Analytics**: Envia os dados para o log analytics do Azure. Se pretender utilizar visualizações, monitorização e alertas para os seus registos, escolha esta opção.

        1. Selecione esta opção > **configurar**. 
        2. Criar uma nova área de trabalho e introduza os detalhes da área de trabalho. Em alternativa, escolha uma área de trabalho existente na lista > **OK**.

            [Área de trabalho do Azure log analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) fornece mais detalhes sobre estas definições.

    - **LOG** > **AuditLogs**: Escolha esta opção para enviar a [registos de auditoria do Intune](monitor-audit-logs.md) à sua conta de armazenamento, hub de eventos ou do log analytics. Os registos de auditoria mostram o histórico de cada tarefa que gera uma alteração no Intune, incluindo quem o fez e quando.

      Se optar por utilizar uma conta de armazenamento, em seguida, também de introduzir o número de dias que pretende manter os dados (retenção). Para manter os dados para sempre, defina **retenção (dias)** para `0` (zero).

    - **LOG** > **OperationalLogs**: Registos operacionais (pré-visualização) mostram o sucesso ou fracasso de utilizadores e dispositivos que inscrever no Intune. Escolha esta opção para enviar os registos de inscrição para a sua conta de armazenamento, hub de eventos, ou do log analytics.

      Se optar por utilizar uma conta de armazenamento, em seguida, também de introduzir o número de dias que pretende manter os dados (retenção). Para manter os dados para sempre, defina **retenção (dias)** para `0` (zero).

      > [!NOTE]
      > Registos operacionais estão em pré-visualização. Para fornecer comentários, incluindo informações incluídas nos registos operacionais, aceda a [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback) (abre um novo Web site).

    Quando terminar, as definições de ter um aspeto semelhantes para as seguintes definições: 

    ![Imagem de exemplo que envia registos de auditoria do Intune para uma conta de armazenamento do Azure](media/diagnostics-settings-example.png)

4. **Guarde** as suas alterações. A definição é apresentada na lista. Depois de criado, pode alterar as definições, selecionando **editar a definição** > **guardar**.

## <a name="cost-considerations"></a>Considerações de custos

Se já tiver uma licença do Microsoft Intune, precisa de uma subscrição do Azure para configurar o hub de eventos e de conta de armazenamento. A subscrição do Azure é normalmente gratuita. Mas, paga para utilizar recursos do Azure, incluindo a conta de armazenamento para arquivamento e o hub de eventos para transmissão em fluxo. A quantidade de dados e os custos podem variar consoante o tamanho do inquilino.

### <a name="storage-size-for-activity-logs"></a>Tamanho de armazenamento para registos de atividades

Cada evento de log de auditoria utiliza cerca de 2 KB de armazenamento de dados. Para um inquilino com 100 000 utilizadores, pode ter cerca de 1,5 milhões de eventos por dia. Poderá ter cerca de 3 GB de armazenamento de dados por dia. Uma vez que normalmente ocorrem escritas em lotes de cinco minutos, pode esperar aproximadamente 9,000 operações de escrita por mês.

As tabelas seguintes mostram uma estimativa de custo, dependendo do tamanho do inquilino. Também inclui uma conta de armazenamento para fins gerais v2 na região E.U.A. oeste para, pelo menos, um ano de retenção de dados. Para obter uma estimativa do volume de dados que pretende para os seus registos, utilize o [Calculadora de preços do armazenamento do Azure](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Registo de auditoria com 100 000 utilizadores**

| | |
|---|---|
|Eventos por dia| 1,5 milhões|
|Volume previsto dos dados por mês| 90 GB|
|Custo estimado por mês (USD)| $1.93|
|Custo estimado por ano (USD)| $23.12|

**Registo de auditoria com 1.000 usuários**

| | |
|---|---|
|Eventos por dia| 15,000|
|Volume previsto dos dados por mês| 900 MB|
|Custo estimado por mês (USD)| $0.02|
|Custo estimado por ano (USD)| $0.24|

### <a name="event-hub-messages-for-activity-logs"></a>Mensagens do hub de eventos para os registos de atividade

Os eventos são normalmente em lote em intervalos de cinco minutos e enviados como uma única mensagem com todos os eventos durante esse período de tempo. Uma mensagem no hub de eventos tem um tamanho máximo de 256 KB. Se o tamanho total de todas as mensagens durante o período de tempo exceder esse volume, em seguida, são enviadas várias mensagens.

Por exemplo, cerca de 18 eventos por segundo normalmente ocorrem para um inquilino grandes de mais de 100 000 utilizadores. Tal equivale a 5400 eventos a cada cinco minutos (eventos de 300 segundos x 18). Registos de auditoria são cerca de 2 KB por evento. Tal equivale a 10.8 MB de dados. Então, 43 mensagens são enviadas para o hub de eventos nesse intervalo de cinco minutos.

A tabela seguinte contém os custos estimados por mês para um hub de eventos básico na região E.U.A. oeste, dependendo do volume de dados de eventos. Para obter uma estimativa do volume de dados que pretende para os seus registos, utilize o [Calculadora de preços de Hubs de eventos](https://azure.microsoft.com/pricing/details/event-hubs/).

**Registo de auditoria com 100 000 utilizadores**

| | |
|---|---|
|Eventos por segundo| 18|
|Eventos por intervalo de cinco minutos| 5,400|
|Volume por intervalo| 10.8 MB|
|Mensagens por intervalo| 43|
|Mensagens por mês| 371,520|
|Custo estimado por mês (USD)| $10.83|

**Registo de auditoria com 1.000 usuários**

| | |
|---|---|
|Eventos por segundo|0.1 |
|Eventos por intervalo de cinco minutos| 52|
|Volume por intervalo|104 KB |
|Mensagens por intervalo|1 |
|Mensagens por mês|8,640 |
|Custo estimado por mês (USD)|$10.80 |

### <a name="log-analytics-cost-considerations"></a>Considerações de custos do log Analytics

Para rever os custos relacionados ao gerenciamento de área de trabalho do Log Analytics, consulte [gerir os custos ao controlar o volume de dados e a retenção do Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

Obtenha respostas para perguntas mais frequentes e leia sobre os problemas conhecidos com os registos do Intune no Azure Monitor.

#### <a name="which-logs-are-included"></a>Os registos que estão incluídos?

Registos de auditoria e registos operacionais (pré-visualização) estão disponíveis para utilizar esta funcionalidade de encaminhamento.

#### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Após uma ação, quando os registos correspondentes aparece de evento hub?

Os registos, normalmente, são exibidas no seu hub de eventos dentro de alguns minutos depois da ação é executada. [O que é o Event Hubs do Azure? ](https://docs.microsoft.com/azure/event-hubs/) fornece mais informações.

#### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Após uma ação, quando os registos correspondentes aparece na conta de armazenamento?

Para contas de armazenamento do Azure, a latência for em qualquer lugar de 5 a 15 minutos após a ação de execução.

#### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>O que acontece se um administrador alterar o período de retenção de uma definição de diagnóstico?

A nova política de retenção é aplicada a registos recolhidos após a alteração. Registos recolhidos antes da alteração de política não são afetados.

#### <a name="how-much-does-it-cost-to-store-my-data"></a>Quanto custa para armazenar meus dados?

Os custos de armazenamento dependem do tamanho dos seus registos e o período de retenção que escolher. Para obter uma lista dos custos estimados para os inquilinos, que depende o volume de registo gerado, consulte a [tamanho de armazenamento para registos de atividades](#storage-size-for-activity-logs) (neste artigo).

#### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Quanto custa a transmitir em fluxo meus dados para um hub de eventos?

Os custos de transmissão em fluxo dependem do número de mensagens a que receber por minuto. Para obter detalhes sobre como os custos são calculados e com base no número de mensagens de estimativas de custos, veja [mensagens do hub de eventos para os registos de atividade](#event-hub-messages-for-activity-logs) (neste artigo).

#### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Como posso integrar registos de auditoria do Intune no meu sistema SIEM?

Utilize o Azure Monitor com os Hubs de eventos para transmitir os registos para o seu sistema SIEM. Primeiro, [transmitir os registos para um hub de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Em seguida, [configurar a ferramenta SIEM](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) com o hub de evento configurado. 

#### <a name="what-siem-tools-are-currently-supported"></a>Que ferramentas SIEM atualmente são suportadas?

Atualmente, o Azure Monitor é suportado pelo [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar, e [Sumo lógica](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (abre um novo Web site). Para obter mais informações sobre como funcionam os conectores, consulte [Azure Stream a monitorização dos dados para um hub de eventos para consumo por uma ferramenta externa](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

#### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Posso acessar os dados de um hub de eventos sem usar uma ferramenta externa de SIEM?

Sim. Para aceder aos registos da sua aplicação personalizada, pode utilizar o [API dos Hubs de eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

#### <a name="what-data-is-stored"></a>Que dados são armazenados?

O Intune não armazena todos os dados enviados através do pipeline. Intune encaminha dados para o pipeline do Azure Monitor, na autoridade de inquilino. Para obter mais informações, consulte [descrição geral do Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Passos Seguintes

* [Registos de atividade de arquivo para uma conta de armazenamento](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Registos de atividade de rota para um hub de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrar registos de atividade com o Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
