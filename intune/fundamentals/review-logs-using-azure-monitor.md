---
title: Rota logs para O Monitor Azure usando Microsoft Intune - Azure  Microsoft Docs
description: Utilize definições de diagnóstico para enviar registos de auditoria e registos operacionais na Microsoft Intune para a conta de armazenamento Do Azure, centros de eventos ou análise de registo. Escolha quanto tempo pretende manter os dados e veja alguns custos estimados para inquilinos de diferentes tamanhos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 95191d64-9895-4f2e-8c5b-f0e85be086d8
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a9c74281df61fbf81914461286353d49b89a4f9
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510750"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Envie dados de registo para armazenamento, centros de eventos ou análise de registo em Intune (pré-visualização)

O Microsoft Intune inclui registos incorporados que fornecem informações sobre o seu ambiente:

- **Os Registos** de Auditoria mostram um registo de atividades que geram uma mudança no Intune, incluindo criar, atualizar (editar), excluir, atribuir e ações remotas.
- **Os Registos Operacionais (pré-visualização)** mostram detalhes sobre utilizadores e dispositivos que conseguiram (ou falharam) inscrever-se e detalhes sobre dispositivos não conformes.
- **Os registos organizacionais de conformidade do dispositivo (pré-visualização)** mostram um relatório organizacional para a conformidade do dispositivo em Intune e detalhes sobre dispositivos não conformes.

Estes registos também podem ser enviados para os serviços do Monitor Azure, incluindo contas de armazenamento, centros de eventos e análise de registos. Especificamente, pode:

* Archive Intune logs para uma conta de armazenamento Azure para manter os dados, ou arquivar por um tempo definido.
* Stream Intune regista um hub de eventos Azure para análise usando ferramentas populares de Informação de Segurança e Gestão de Eventos (SIEM), tais como Splunk e QRadar.
* Integre os registos Intune com as suas próprias soluções de log personalizadas, transmitindo-as para um centro de eventos.
* Envie registos intune para Log Analytics para permitir visualizações ricas, monitorização e alerta nos dados conectados.

Estas funcionalidades fazem parte das **Definições** de Diagnóstico em Intune.

Este artigo mostra-lhe como usar **as Definições** de Diagnóstico para enviar dados de registo para diferentes serviços, dá exemplos e estimativas de custos, e responde a algumas questões comuns. Assim que ativar esta funcionalidade, os seus registos são encaminhados para o serviço Azure Monitor que escolher.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar esta funcionalidade, precisa de:

* Uma subscrição Azure: Se não tiver uma subscrição Azure, pode [inscrever-se para um teste gratuito](https://azure.microsoft.com/free/).
* Um ambiente Intune da Microsoft (inquilino) em Azure
* Um utilizador que seja administrador **global** ou administrador de **serviço intune** para o inquilino Intune.

Dependendo de onde pretende encaminhar os dados do registo de auditoria, precisa de um dos seguintes serviços:

* Uma [conta de armazenamento Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview) com permissões *ListKeys.* Recomendamos que utilize uma conta de armazenamento geral, e não uma conta de armazenamento de bolhas. Para obter informações sobre preços de armazenamento, consulte a calculadora de preços do [Armazenamento Azure](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Um [evento Azure hubs namespace](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) para integrar com soluções de terceiros.
* Um espaço de trabalho de análise de [registo Azure](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) para enviar registos para Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Enviar registos para o monitor Azure

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **relatórios** > **definições de diagnóstico**. A primeira vez que o abrires, liga-o. Caso contrário, adicione uma definição.

    > [!div class="mx-imgBorder"]
    > ![ligue as definições de Diagnóstico em Intune para enviar registos para o Monitor Azure](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome para as definições de diagnóstico. Esta definição inclui todas as propriedades em que entra. Por exemplo, introduza `Route audit logs to storage account`.
    - **Arquivar numa conta**de armazenamento: Guarde os dados de registo para uma conta de armazenamento Azure. Utilize esta opção se pretender guardar ou arquivar os dados.

        1. Selecione esta opção > **Configure**. 
        2. Escolha uma conta de armazenamento existente na lista > **OK**.

    - **Stream para um centro de eventos**: Transmite os troncos para um centro de eventos Azure. Se pretender análises nos seus dados de registo utilizando ferramentas SIEM, como splunk e QRadar, escolha esta opção.

        1. Selecione esta opção > **Configure**. 
        2. Escolha um espaço de nome e política existentes do hub de eventos da lista > **OK**.

    - **Enviar para Log Analytics**: Envia os dados para a análise de registo do Azure. Se pretender utilizar visualizações, monitorização e alerta para os seus registos, escolha esta opção.

        1. Selecione esta opção > **Configure**. 
        2. Crie um novo espaço de trabalho e insira os detalhes do espaço de trabalho. Ou, escolha um espaço de trabalho existente na lista > **OK**.

            [O espaço de trabalho](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) de análise de registo azure fornece mais detalhes sobre estas configurações.

    - **LOG** > **AuditLogs**: Escolha esta opção para enviar os registos de [auditoria Intune](../monitor-audit-logs.md) para a sua conta de armazenamento, centro de eventos ou análise de registo. Os registos de auditoria mostram o histórico de cada tarefa que gera uma mudança no Intune, incluindo quem o fez e quando.

      Se optar por utilizar uma conta de armazenamento, introduza também quantos dias pretende manter os dados (retenção). Para manter os dados para sempre, detete a **Retenção (dias)** para `0` (zero).

    - **LOG** > **OperacionaIsLogs**: Os registos operacionais (pré-visualização) mostram o sucesso ou falha dos utilizadores e dispositivos que se inscrevem no Intune, bem como detalhes sobre dispositivos não conformes. Escolha esta opção para enviar os registos de inscrição para a sua conta de armazenamento, centro de eventos ou análise de registo.

      Se optar por utilizar uma conta de armazenamento, introduza também quantos dias pretende manter os dados (retenção). Para manter os dados para sempre, detete a **Retenção (dias)** para `0` (zero).

      > [!NOTE]
      > Os registos operacionais estão em pré-visualização. Para fornecer feedback, incluindo informações nos registos operacionais, aceda ao [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    - **LOG** > **DeviceComplianceOrg**: Registos organizacionais de conformidade do dispositivo (pré-visualização) mostram o relatório organizacional de conformidade do dispositivo em Intune e detalhes de dispositivos não conformes. Escolha esta opção para enviar os registos de conformidade para a sua conta de armazenamento, centro de eventos ou análise de registo.

      Se optar por utilizar uma conta de armazenamento, introduza também quantos dias pretende manter os dados (retenção). Para manter os dados para sempre, detete a **Retenção (dias)** para `0` (zero).
 
      > [!NOTE]
      > Os registos organizacionais de conformidade do dispositivo estão em pré-visualização. Para fornecer feedback, incluindo informações no relatório, vá ao [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    Quando terminadas, as definições parecem semelhantes às seguintes definições: 

    > [!div class="mx-imgBorder"]
    > ![Imagem de amostra que envia registos de auditoria Intune para uma conta de armazenamento Azure](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. **Guarde** as suas alterações. A sua configuração está na lista. Uma vez criado, pode alterar as definições selecionando a **definição de Editar** > **Guardar**.

## <a name="use-audit-logs-throughout-intune"></a>Utilize registos de auditoria em toda a Intune

Também pode exportar os registos de auditoria noutras partes do Intune, incluindo inscrição, conformidade, configuração, dispositivos, aplicações de clientes e muito mais.

Para mais informações, consulte Utilize registos de [auditoria para acompanhar e monitorizar os eventos.](monitor-audit-logs.md) Pode escolher para onde enviar os registos de auditoria, conforme descrito no [monitor de envio para o Monitor Azure](#send-logs-to-azure-monitor) (neste artigo).

## <a name="cost-considerations"></a>Considerações de custos

Se já tem uma licença Microsoft Intune, precisa de uma subscrição Azure para configurar a conta de armazenamento e o centro de eventos. A subscrição azure é normalmente gratuita. Mas paga-se para utilizar os recursos do Azure, incluindo a conta de armazenamento para arquivo e o centro de eventos para streaming. A quantidade de dados e os custos variam consoante o tamanho do arrendatário.

### <a name="storage-size-for-activity-logs"></a>Tamanho do armazenamento para registos de atividade

Todos os eventos de registo de auditoria utilizam cerca de 2 KB de armazenamento de dados. Para um inquilino com 100.000 utilizadores, pode ter cerca de 1,5 milhões de eventos por dia. Pode necessitar de cerca de 3 GB de armazenamento de dados por dia. Como os escritos costumam acontecer em lotes de cinco minutos, pode esperar aproximadamente 9.000 operações de escrita por mês.

As tabelas seguintes mostram uma estimativa de custos dependendo do tamanho do inquilino. Inclui também uma conta de armazenamento v2 de uso geral nos EUA ocidentais durante pelo menos um ano de retenção de dados. Para obter uma estimativa do volume de dados que espera para os seus registos, utilize a calculadora de preços de [armazenamento Azure](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Registo de auditoria com 100.000 utilizadores**

| | |
|---|---|
|Eventos por dia| 1,5 milhões|
|Volume estimado de dados por mês| 90 GB|
|Custo estimado por mês (USD)| $1,93|
|Custo estimado por ano (USD)| $23.12|

**Registo de auditoria com 1.000 utilizadores**

| | |
|---|---|
|Eventos por dia| 15,000|
|Volume estimado de dados por mês| 900 MB|
|Custo estimado por mês (USD)| $0,02|
|Custo estimado por ano (USD)| $0,24|

### <a name="event-hub-messages-for-activity-logs"></a>Mensagens de hub de eventos para registos de atividade

Os eventos são normalmente loteados em intervalos de cinco minutos, e enviados como uma única mensagem com todos os eventos dentro desse prazo. Uma mensagem no centro do evento tem um tamanho máximo de 256 KB. Se o tamanho total de todas as mensagens dentro do prazo exceder esse volume, então são enviadas várias mensagens.

Por exemplo, cerca de 18 eventos por segundo costumam acontecer para um grande inquilino de mais de 100.000 utilizadores. Isto equivale a 5.400 eventos a cada cinco minutos (300 segundos x 18 eventos). Os registos de auditoria são de cerca de 2 KB por evento. Isto equivale a 10,8 MB de dados. Então, 43 mensagens são enviadas para o centro do evento nesse intervalo de cinco minutos.

A tabela seguinte contém custos estimados por mês para um centro de eventos básicos no Oeste dos EUA, dependendo do volume de dados do evento. Para obter uma estimativa do volume de dados que espera para os seus registos, utilize a calculadora de preços do [Event Hubs](https://azure.microsoft.com/pricing/details/event-hubs/).

**Registo de auditoria com 100.000 utilizadores**

| | |
|---|---|
|Eventos por segundo| 18|
|Eventos por intervalo de cinco minutos| 5,400|
|Volume por intervalo| 10,8 MB|
|Mensagens por intervalo| 43|
|Mensagens por mês| 371,520|
|Custo estimado por mês (USD)| $10.83|

**Registo de auditoria com 1.000 utilizadores**

| | |
|---|---|
|Eventos por segundo|0.1 |
|Eventos por intervalo de cinco minutos| 52|
|Volume por intervalo|104 KB |
|Mensagens por intervalo|1 |
|Mensagens por mês|8,640 |
|Custo estimado por mês (USD)|$10,80 |

### <a name="log-analytics-cost-considerations"></a>Considerações de custos de Log Analytics

Para rever os custos relacionados com a gestão do espaço de trabalho do Log Analytics, consulte [Gerir o custo controlando](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage)o volume de dados e a retenção no Log Analytics .

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

Obtenha respostas a perguntas frequentes e leia sobre quaisquer questões conhecidas com registos Intune no Monitor Azure.

### <a name="which-logs-are-included"></a>Que troncos estão incluídos?

Os registos de auditoria e os registos operacionais (pré-visualização) estão ambos disponíveis para encaminhamento utilizando esta funcionalidade.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Depois de uma ação, quando os registos correspondentes aparecem no centro do evento?

Os registos normalmente aparecem no seu centro de eventos dentro de alguns minutos após a ação ser realizada. [O que é Azure Event Hubs?](https://docs.microsoft.com/azure/event-hubs/) fornece mais informações.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Depois de uma ação, quando os registos correspondentes aparecem na conta de armazenamento?

Para as contas de armazenamento azure, a latência está em qualquer lugar entre 5 a 15 minutos após o funcionao da ação.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>O que acontece se um Administrador alterar o período de retenção de uma definição de diagnóstico?

A nova política de retenção é aplicada aos registos recolhidos após a alteração. Os registos recolhidos antes da mudança de política não são afetados.

### <a name="how-much-does-it-cost-to-store-my-data"></a>Quanto custa armazenar os meus dados?

Os custos de armazenamento dependem do tamanho dos seus troncos e do período de retenção que escolher. Para obter uma lista dos custos estimados para os inquilinos, que dependem do volume de registo gerado, consulte o tamanho do [Armazenamento para registos](#storage-size-for-activity-logs) de atividade (neste artigo).

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Quanto custa transmitir os meus dados para um centro de eventos?

Os custos de streaming dependem do número de mensagens que recebe por minuto. Para mais detalhes sobre como os custos são calculados e estimativas de custos com base no número de mensagens, consulte [as mensagens do Hub do Evento para registos](#event-hub-messages-for-activity-logs) de atividade (neste artigo).

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Como integrar registos de auditoria intune com o meu sistema SIEM?

Utilize o Monitor Azure com Centros de Eventos para transmitir registos para o seu sistema SIEM. Primeiro, [transmita os troncos para um centro de eventos.](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub) Em seguida, [configure a sua ferramenta SIEM](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) com o centro de eventos configurado. 

### <a name="what-siem-tools-are-currently-supported"></a>Quais as ferramentas SIEM que são atualmente suportadas?

Atualmente, o Azure Monitor é apoiado pela [Splunk,](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk)QRadar e [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (abre um novo website). Para obter mais informações sobre o funcionamento dos conectores, consulte o [Stream Azure monitorizando os dados para um centro](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs)de eventos para consumo por uma ferramenta externa .

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Posso aceder aos dados a partir de um centro de eventos sem usar uma ferramenta SIEM externa?

Sim. Para aceder aos registos da sua aplicação personalizada, pode utilizar a API dos Hubs de [Eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

### <a name="what-data-is-stored"></a>Que dados são armazenados?

Intune não armazena nenhum dado enviado através do oleoduto. Instonize os dados para o oleoduto Azure Monitor, à autoridade do arrendatário. Para mais informações, consulte a [visão geral do Monitor Azure](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Próximos passos

* [Registos de atividade de arquivo numa conta de armazenamento](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Rota logs para um centro de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrar registos de atividade com Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
