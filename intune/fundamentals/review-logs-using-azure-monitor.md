---
title: Rotear logs para Azure Monitor usando o Microsoft Intune-Azure | Microsoft Docs
description: Use as configurações de diagnóstico para enviar logs de auditoria e logs operacionais no Microsoft Intune para a conta de armazenamento do Azure, os hubs de eventos ou o log Analytics. Escolha por quanto tempo deseja manter os dados e veja alguns custos estimados para locatários de tamanho diferentes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
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
ms.openlocfilehash: 66acf4d8b88097c3262f44493ab72b3900781eed
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504975"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Enviar dados de log para armazenamento, hubs de eventos ou log Analytics no Intune (versão prévia)

O Microsoft Intune inclui logs internos que fornecem informações sobre seu ambiente:

- **Os logs de auditoria** mostram detalhes sobre diferentes eventos ou tarefas que ocorrem no Intune.
- **Os logs operacionais (versão prévia)** mostram detalhes sobre os usuários e dispositivos que foram registrados com êxito (ou com falha) e detalhes sobre dispositivos não compatíveis.
- **Os logs organizacionais de conformidade do dispositivo (versão prévia)** mostram um relatório organizacional para conformidade do dispositivo no Intune e detalhes sobre dispositivos sem conformidade.

Esses logs também podem ser enviados para Azure Monitor serviços, incluindo contas de armazenamento, hubs de eventos e log Analytics. Especificamente, você pode:

* Arquive logs do Intune em uma conta de armazenamento do Azure para manter os dados ou arquivar por um tempo definido.
* Transmita logs do Intune para um hub de eventos do Azure para análise usando ferramentas de SIEM (gerenciamento de eventos e informações de segurança) populares, como Splunk e QRadar.
* Integre os logs do Intune com suas próprias soluções de log personalizadas transmitindo-os para um hub de eventos.
* Envie logs do Intune para Log Analytics para permitir visualizações avançadas, monitoramento e alertas nos dados conectados.

Esses recursos fazem parte das **configurações de diagnóstico** no Intune.

Este artigo mostra como usar **as configurações de diagnóstico** para enviar dados de log para diferentes serviços, fornece exemplos e estimativas de custos e responde a algumas perguntas comuns. Depois de habilitar esse recurso, os logs serão roteados para o serviço de Azure Monitor que você escolher.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar esta funcionalidade, precisa de:

* Uma assinatura do Azure: se você não tiver uma assinatura do Azure, poderá se [inscrever para obter uma avaliação gratuita](https://azure.microsoft.com/free/).
* Um ambiente de Microsoft Intune (locatário) no Azure
* Um usuário que é um **administrador global** ou **administrador de serviços do Intune** para o locatário do Intune.

Dependendo de onde você deseja rotear os dados do log de auditoria, você precisa de um dos seguintes serviços:

* Uma [conta de armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview) com permissões *ListKeys* . Recomendamos que você use uma conta de armazenamento geral e não uma conta de armazenamento de BLOBs. Para obter informações sobre os preços de armazenamento, veja a [Calculadora de preços do Armazenamento do Azure](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Um [namespace de hubs de eventos do Azure](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) para integrar a soluções de terceiros.
* Um [espaço de trabalho do Azure log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) para enviar logs para log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Enviar logs para o Azure monitor

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Em **monitoramento**, selecione **configurações de diagnóstico**. Na primeira vez que você abri-lo, ative-o. Caso contrário, adicione uma configuração.

    ![Ativar as configurações de diagnóstico no Intune para enviar logs para Azure Monitor](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. Introduza as seguintes propriedades:

    - **Nome**: Insira um nome para as configurações de diagnóstico. Essa configuração inclui todas as propriedades que você inserir. Por exemplo, introduza `Route audit logs to storage account`.
    - **Arquivar em uma conta de armazenamento**: salva os dados de log em uma conta de armazenamento do Azure. Use esta opção se desejar salvar ou arquivar os dados.

        1. Selecione esta opção > **Configurar**. 
        2. Escolha uma conta de armazenamento existente na lista > **OK**.

    - **Transmitir para um hub de eventos**: transmite os logs para um hub de eventos do Azure. Se você quiser análise nos dados de log usando ferramentas SIEM, como Splunk e QRadar, escolha essa opção.

        1. Selecione esta opção > **Configurar**. 
        2. Escolha um namespace do hub de eventos existente e uma política da lista > **OK**.

    - **Enviar para log Analytics**: envia os dados para o log Analytics do Azure. Se você quiser usar visualizações, monitoramento e alertas para seus logs, escolha essa opção.

        1. Selecione esta opção > **Configurar**. 
        2. Crie um novo espaço de trabalho e insira os detalhes do espaço de trabalho. Ou escolha um espaço de trabalho existente na lista > **OK**.

            O [espaço de trabalho do Azure log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) fornece mais detalhes sobre essas configurações.

    - **LOG** > **AuditLogs**: escolha esta opção para enviar os [logs de auditoria do Intune](../monitor-audit-logs.md) para sua conta de armazenamento, Hub de eventos ou log Analytics. Os logs de auditoria mostram o histórico de cada tarefa que gera uma alteração no Intune, incluindo quem fez e quando.

      Se você optar por usar uma conta de armazenamento, insira também o número de dias que deseja manter os dados (retenção). Para manter os dados para sempre, defina a **retenção (dias)** para `0` (zero).

    - **LOG** > **OperationalLogs**: os logs operacionais (visualização) mostram o êxito ou a falha de usuários e dispositivos que se registram no Intune, bem como detalhes sobre dispositivos sem conformidade. Escolha esta opção para enviar os logs de registro para sua conta de armazenamento, Hub de eventos ou log Analytics.

      Se você optar por usar uma conta de armazenamento, insira também o número de dias que deseja manter os dados (retenção). Para manter os dados para sempre, defina a **retenção (dias)** para `0` (zero).

      > [!NOTE]
      > Os logs operacionais estão em versão prévia. Para fornecer comentários, incluindo informações nos logs operacionais, vá para [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    - **LOG** > **DeviceComplianceOrg**: os logs organizacionais de conformidade do dispositivo (versão prévia) mostram o relatório organizacional para conformidade do dispositivo no Intune e detalhes de dispositivos não compatíveis. Escolha esta opção para enviar os logs de conformidade para sua conta de armazenamento, Hub de eventos ou log Analytics.

      Se você optar por usar uma conta de armazenamento, insira também o número de dias que deseja manter os dados (retenção). Para manter os dados para sempre, defina a **retenção (dias)** para `0` (zero).
 
      > [!NOTE]
      > Os logs organizacionais de conformidade do dispositivo estão em versão prévia. Para fornecer comentários, incluindo informações no relatório, vá para [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    Quando terminar, suas configurações são semelhantes às seguintes configurações: 

    ![Imagem de exemplo que envia logs de auditoria do Intune para uma conta de armazenamento do Azure](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. **Guarde** as suas alterações. Sua configuração é mostrada na lista. Após a criação, você pode alterar as configurações selecionando **Editar configuração** > **salvar**.

## <a name="use-audit-logs-throughout-intune"></a>Usar logs de auditoria em todo o Intune

Você também pode exportar os logs de auditoria em outras partes do Intune, incluindo registro, conformidade, configuração, dispositivos, aplicativos cliente e muito mais.

Por exemplo, para exportar os logs de auditoria ao usar a conformidade do dispositivo:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione monitor de **conformidade do dispositivo** > **monitorar** > **logs de auditoria**:

    ![Escolha os logs de auditoria para rotear dados do Intune para Azure Monitor armazenamento, hubs de eventos ou análises](./media/review-logs-using-azure-monitor/audit-logs-under-monitor-in-compliance.png)

3. Selecione **exportar configurações de dados**. Se ele não estiver habilitado, você poderá ativar **as configurações de diagnóstico**. Você também pode escolher para onde enviar os logs, conforme descrito em [enviar logs para o Azure monitor](#send-logs-to-azure-monitor) (neste artigo).

## <a name="cost-considerations"></a>Considerações de custos

Se você já tiver uma licença Microsoft Intune, precisará de uma assinatura do Azure para configurar a conta de armazenamento e o Hub de eventos. A assinatura do Azure normalmente é gratuita. Mas você paga para usar os recursos do Azure, incluindo a conta de armazenamento para arquivamento e o Hub de eventos para streaming. A quantidade de dados e os custos variam dependendo do tamanho do locatário.

### <a name="storage-size-for-activity-logs"></a>Tamanho de armazenamento para registos de atividades

Cada evento de registo de auditoria consome cerca de 2 KB de armazenamento de dados. Para um locatário com 100.000 usuários, você pode ter cerca de 1,5 milhões eventos por dia. Talvez seja necessário cerca de 3 GB de armazenamento de dados por dia. Como as gravações normalmente acontecem em lotes de cinco minutos, você pode esperar aproximadamente 9.000 operações de gravação por mês.

As tabelas a seguir mostram uma estimativa de custo, dependendo do tamanho do locatário. Ele também inclui uma conta de armazenamento de uso geral V2 no oeste dos EUA por pelo menos um ano de retenção de dados. Para obter uma estimativa do volume de dados que você espera para seus logs, use a [calculadora de preços do armazenamento do Azure](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Log de auditoria com 100.000 usuários**

| | |
|---|---|
|Eventos por dia| 1,5 milhões|
|Volume estimado de dados por mês| 90 GB|
|Custo estimado por mês (USD)| $1,93|
|Custo estimado por ano (USD)| $23,12|

**Log de auditoria com 1.000 usuários**

| | |
|---|---|
|Eventos por dia| 15,000|
|Volume estimado de dados por mês| 900 MB|
|Custo estimado por mês (USD)| $0,02|
|Custo estimado por ano (USD)| $0,24|

### <a name="event-hub-messages-for-activity-logs"></a>Mensagens do hub de eventos para os registos de atividades

Em geral, os eventos são enviados em lotes em intervalos de cinco minutos e enviado como uma única mensagem com todos os eventos dentro desse período. Uma mensagem no Hub de eventos tem um tamanho máximo de 256 KB. Se o tamanho total de todas as mensagens dentro do período exceder esse volume, então várias mensagens serão enviadas.

Por exemplo, cerca de 18 eventos por segundo geralmente acontecem para um locatário grande de mais de 100.000 usuários. Isso equivale a 5.400 eventos a cada cinco minutos (300 segundos x 18 eventos). Os logs de auditoria são cerca de 2 KB por evento. Isso equivale a 10,8 MB de dados. Portanto, 43 mensagens são enviadas para o Hub de eventos nesse intervalo de cinco minutos.

A tabela seguinte contém os custos estimados por mês para um hub de eventos básico nos E.U.A. Oeste, consoante o volume de dados de eventos. Para obter uma estimativa do volume de dados que você espera para seus logs, use a [calculadora de preços dos hubs de eventos](https://azure.microsoft.com/pricing/details/event-hubs/).

**Log de auditoria com 100.000 usuários**

| | |
|---|---|
|Eventos por segundo| 18|
|Eventos por intervalo de cinco minutos| 5400|
|Volume por intervalo| 10,8 MB|
|Mensagens por intervalo| 43|
|Mensagens por mês| 371 520|
|Custo estimado por mês (USD)| $10,83|

**Log de auditoria com 1.000 usuários**

| | |
|---|---|
|Eventos por segundo|0.1 |
|Eventos por intervalo de cinco minutos| 52|
|Volume por intervalo|104 KB |
|Mensagens por intervalo|1 |
|Mensagens por mês|8640 |
|Custo estimado por mês (USD)|10,80 $ |

### <a name="log-analytics-cost-considerations"></a>Log Analytics considerações de custo

Para examinar os custos relacionados ao gerenciamento do espaço de trabalho Log Analytics, consulte [gerenciar custos controlando o volume de dados e a retenção em log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

Obtenha respostas para perguntas frequentes e leia sobre quaisquer problemas conhecidos com os logs do Intune em Azure Monitor.

### <a name="which-logs-are-included"></a>Quais logs estão incluídos?

Os logs de auditoria e os logs operacionais (visualização) estão disponíveis para roteamento usando esse recurso.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Após uma ação, quando os logs correspondentes aparecem no Hub de eventos?

Os logs normalmente aparecem no Hub de eventos em vários minutos após a execução da ação. [O que são hubs de eventos do Azure?](https://docs.microsoft.com/azure/event-hubs/) fornece mais informações.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Após uma ação, quando os logs correspondentes aparecem na conta de armazenamento?

Para contas de armazenamento do Azure, a latência é de 5 a 15 minutos após a execução da ação.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>O que acontece se um administrador altera o período de retenção de uma configuração de diagnóstico?

A nova política de retenção é aplicada aos logs coletados após a alteração. Os logs coletados antes da alteração da política não são afetados.

### <a name="how-much-does-it-cost-to-store-my-data"></a>Quanto custa armazenar meus dados?

Os custos de armazenamento dependem do tamanho dos seus logs e do período de retenção que você escolher. Para obter uma lista dos custos estimados para locatários, que dependem do volume de log gerado, consulte o [tamanho do armazenamento para logs de atividade](#storage-size-for-activity-logs) (neste artigo).

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Quanto custa transmitir meus dados para um hub de eventos?

Os custos de streaming dependem do número de mensagens recebidas por minuto. Para obter detalhes sobre como os custos são calculados e estimativas de custo com base no número de mensagens, consulte [mensagens do hub de eventos para logs de atividades](#event-hub-messages-for-activity-logs) (neste artigo).

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Como fazer integrar os logs de auditoria do Intune ao meu sistema SIEM?

Utilize o Azure Monitor com os Hubs de Eventos para transmitir os registos para o seu sistema SIEM. Primeiro, [transmita os logs para um hub de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Em seguida, [configure sua ferramenta Siem](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) com o Hub de eventos configurado. 

### <a name="what-siem-tools-are-currently-supported"></a>Quais ferramentas de SIEM têm suporte atualmente?

Atualmente, Azure Monitor é suportada por [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar e a [lógica do resumo](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (abre um novo site). Para obter mais informações sobre como funcionam os conectores, veja [Stream Azure monitoring data to an event hub for consumption by an external tool](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) (Transmitir em fluxo dados de monitorização do Azure para um hub de eventos, para consumo por uma ferramenta externa).

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Posso acessar os dados de um hub de eventos sem usar uma ferramenta SIEM externa?

Sim. Pode utilizar a [API dos Hub de Eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph) para aceder aos registos da sua aplicação personalizada.

### <a name="what-data-is-stored"></a>Quais dados são armazenados?

O Intune não armazena nenhum dado enviado por meio do pipeline. O Intune roteia dados para o pipeline de Azure Monitor, na autoridade do locatário. Para obter mais informações, consulte [Azure monitor visão geral](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Próximos passos

* [Arquivar registos de atividades numa conta de armazenamento](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Encaminhar registos de atividades para um hub de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrar logs de atividade com Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
