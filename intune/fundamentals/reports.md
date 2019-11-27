---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: O Intune fornece tipos de relatórios específicos com exibições focadas que contêm dados consistentes e oportunos.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390935"
---
# <a name="intune-reports"></a>Relatórios do Intune
Microsoft Intune relatórios permite que você monitore de forma mais eficiente e proativa a integridade e a atividade dos pontos de extremidade em sua organização e também fornece outros dados de relatório no Intune. Por exemplo, você poderá ver relatórios sobre a conformidade do dispositivo, integridade do dispositivo e tendências do dispositivo. Além disso, você pode criar relatórios personalizados para obter dados mais específicos. 

> [!NOTE]
> As alterações de relatórios do Intune serão distribuídas gradualmente em um período de tempo para ajudá-lo a se preparar e se adaptar à nova estrutura.

Os tipos de relatório são organizados nas seguintes áreas de foco:
- **Operacional** – fornece dados direcionados a tempo, que ajudam você a se concentrar e tomar medidas. Administradores, especialistas no assunto e assistência técnica acharão esses relatórios mais úteis.
- **Organizacional** – fornece um resumo mais amplo de uma exibição geral, como o estado do gerenciamento de dispositivos. Gerentes e administradores acharão esses relatórios mais úteis.
- **Histórico** -fornece padrões e tendências ao longo de um período de tempo. Gerentes e administradores acharão esses relatórios mais úteis.
- **Especialista** – permite que você use dados brutos para criar seus próprios relatórios personalizados. Os administradores encontrarão esses relatórios mais úteis.

A estrutura de relatórios fornece uma experiência de relatório consistente e mais abrangente. Os relatórios disponíveis fornecem a seguinte funcionalidade:
- **Pesquisar e classificar** – você pode pesquisar e classificar em todas as colunas, independentemente do tamanho do conjunto de um.
- **Paginação de dados** – você pode digitalizar seus dados com base na paginação, seja página por página ou saltando para uma página específica.
- **Desempenho** -você pode gerar e exibir rapidamente relatórios criados a partir de locatários grandes.
- **Exportar** – você pode exportar rapidamente os dados de relatório gerados de locatários grandes.

### <a name="who-can-access-the-data"></a>Quem pode aceder aos dados?

Os usuários com as seguintes permissões podem examinar os logs:

- Administrador Global
- Administrador de Serviços do Intune
- Administradores atribuídos a uma função do Intune com permissões de **leitura**

## <a name="non-compliant-devices-report-operational"></a>Relatório de dispositivos não compatíveis (operacional)
Os dispositivos sem conformidade relatam as superfícies de dados normalmente usadas por funções de assistência técnica ou de administrador para identificar problemas e ajudar a corrigir problemas. Os dados encontrados nesses relatórios são oportunos, chamam comportamento inesperado e devem ser acionáveis. O relatório está disponível junto com a carga de trabalho, tornando o relatório de dispositivos sem conformidade acessível sem sair dos fluxos de trabalho ativos. Este relatório fornece recursos de filtragem, pesquisa, paginação e classificação. Além disso, você pode fazer uma busca detalhada para ajudar a solucionar problemas.

Você pode exibir o relatório de **dispositivos não compatíveis** usando as seguintes etapas:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **conformidade do dispositivo** > **dispositivos não compatíveis**.

    ![Relatório de dispositivo não compatível](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>Relatório de conformidade do dispositivo (organizacional)
Os relatórios de conformidade do dispositivo devem ser amplos por natureza e fornecer uma exibição de relatório mais tradicional de dados para identificar métricas agregadas. Este relatório foi projetado para funcionar com grandes conjuntos de altos para obter uma imagem completa de conformidade do dispositivo. Por exemplo, o relatório de conformidade do dispositivo para conformidade do dispositivo mostra todos os Estados de conformidade para que os dispositivos forneçam uma visão mais ampla dos dados, independentemente do tamanho do DataSet. Este relatório mostra a divisão completa de registros, além de uma visualização prática de métricas agregadas. Esse relatório pode ser gerado aplicando-se filtros e selecionando o botão "gerar relatório". Isso atualizará os dados para mostrar o estado mais recente com a capacidade de exibir os registros individuais que compõem os dados agregados. Como a maioria dos relatórios na nova estrutura, esses registros podem ser classificados e pesquisados para se concentrar nas informações de que você precisa. 

Para ver um relatório gerado de estado do dispositivo, você pode usar as seguintes etapas:
1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **relatórios** para exibir o resumo dos relatórios.
3. Selecione **Conformidade do dispositivo**.
4. Selecione os filtros **status de conformidade**, **so**e **Propriedade** para refinar o relatório.
5. Clique em **gerar relatório** (ou **gerar novamente**) para recuperar os dados atuais.

    ![Relatório de conformidade do dispositivo](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Este relatório de **conformidade do dispositivo** fornece um carimbo de data/hora de quando o relatório foi gerado pela última vez. 

Para obter informações relacionadas, consulte [impor a conformidade para o Microsoft defender ATP com acesso condicional no Intune](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Resumo de relatórios 

O relatório de conformidade do dispositivo está disponível como o relatório de resumo na carga de trabalho **relatórios** . Use as etapas a seguir para exibir o relatório de conformidade do dispositivo:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **relatórios** para exibir o resumo dos relatórios.

    ![Resumo de relatórios do Intune](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Relatório de tendências de conformidade do dispositivo (histórico)
Os relatórios de tendência de conformidade do dispositivo têm maior probabilidade de serem usados por administradores e arquitetos para identificar tendências de longo prazo para a conformidade do dispositivo. Os dados agregados são exibidos durante um período de tempo e são úteis para tomar decisões futuras de investimento, conduzir melhorias de processo ou solicitar investigação em qualquer anomalia. Os filtros também podem ser aplicados para ver tendências específicas. Os dados fornecidos por esse relatório são um instantâneo do estado atual do locatário (quase em tempo real). 

Um relatório de tendência de conformidade do dispositivo para as tendências de conformidade do dispositivo pode mostrar a tendência de Estados de conformidade do dispositivo durante um período de tempo. Você pode identificar onde os picos de conformidade ocorreram e concentrar seu tempo e esforço de acordo.

Você pode exibir o relatório de **tendências** usando as seguintes etapas:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **relatórios** > **tendências** para exibir a conformidade do dispositivo em uma tendência de 60 dias.

    ![Relatório de tendências do Intune](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Relatórios de integração do Azure Monitor (especialista)
Você pode personalizar seus próprios relatórios para obter os dados desejados. Os dados em seus relatórios estarão, opcionalmente, disponíveis por meio de [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) usando [log Analytics](reports.md#log-analytics) e [Azure monitor pastas de trabalho](reports.md#workbooks). Essas soluções permitem que você crie consultas personalizadas, configure alertas e faça com que os painéis mostrem os dados de conformidade do dispositivo da maneira desejada. Além disso, você pode manter os logs de atividade em sua conta de armazenamento do Azure, integrá-los aos relatórios usando [as ferramentas Siem (gerenciamento de eventos e informações de segurança)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)e correlacionar os relatórios aos logs de atividade do Azure AD. Azure Monitor pastas de trabalho podem ser usadas, além de importar painéis para necessidades de relatórios personalizados.

> [!NOTE]
> A funcionalidade de relatório complexa requer uma assinatura do Azure.

Um relatório de especialista de exemplo corelacionaria dados de propriedade de dispositivo com dados de registro de plataforma em um relatório personalizado. Em seguida, esse relatório personalizado pode ser exibido em um painel existente no portal de Azure Active Directory.

Você pode criar e exibir relatórios personalizados usando as seguintes etapas:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **relatórios** > **configurações de diagnóstico** adicionar uma [configuração de diagnóstico](reports.md#diagnostic-settings).

    ![Resumo de relatórios do Intune](./media/intune-reports/intune-reports-04.png)

3. Clique em **Adicionar configuração de diagnóstico** para exibir o painel **configurações de diagnóstico** . 
4. Adicione um **nome** para as configurações de diagnóstico. 
5. Selecione as configurações **Enviar para log Analytics** e **DeviceComplianceOrg** .

    ![Resumo de relatórios do Intune](./media/intune-reports/intune-reports-04a.png)

6. Clique em **Guardar**.
7. Em seguida, selecione **log Analytics** para criar e executar uma nova consulta de log usando [log Analytics](reports.md#log-analytics).

   ![Consulta de Log Analytics log](./media/intune-reports/intune-reports-05.png)

8. Selecione **pastas de trabalho** para criar ou abrir um relatório interativo usando [pastas de trabalho Azure monitor](reports.md#workbooks).

   ![Pastas de trabalho-relatórios interativos](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Definições de diagnóstico
Cada recurso do Azure requer sua própria configuração de diagnóstico. A configuração de diagnóstico define o seguinte para um recurso:

- Categorias de logs e dados de métrica enviados aos destinos definidos na configuração. As categorias disponíveis irão variar para diferentes tipos de recursos.
- Um ou mais destinos para enviar os logs. Os destinos atuais incluem Log Analytics espaço de trabalho, hubs de eventos e armazenamento do Azure.
- Política de retenção para dados armazenados no armazenamento do Azure.

Uma única configuração de diagnóstico pode definir um de cada um dos destinos. Se você quiser enviar dados para mais de um tipo de destino específico (por exemplo, dois espaços de trabalho de Log Analytics diferentes), crie várias configurações. Cada recurso pode ter até 5 configurações de diagnóstico.

Para obter mais informações, sobre configurações de diagnóstico, consulte [criar configuração de diagnóstico para coletar logs e métricas de plataforma no Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Log Analytics
Log Analytics é a principal ferramenta na portal do Azure para escrever consultas de log e analisar interativamente os resultados das consultas. Mesmo que uma consulta de log seja usada em outro lugar na Azure Monitor, você normalmente escreverá e testará a consulta primeiro usando Log Analytics. Para obter detalhes sobre como usar Log Analytics e criar consultas de log, consulte [visão geral das consultas de log no Azure monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Pastas
As pastas de trabalho combinam texto, consultas de análise, métricas do Azure e parâmetros em relatórios interativos sofisticados. As pastas de trabalho são editáveis por outros membros da equipe que têm acesso aos mesmos recursos do Azure. Para obter mais informações sobre pastas de trabalho, consulte [Azure monitor pastas de trabalho](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). Além disso, você pode trabalhar com os modelos de pasta de trabalho e contribuir com eles. Para obter mais informações, consulte [Azure monitor modelos de pasta de trabalho](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>Passos Seguintes

Saiba mais sobre as seguintes tecnologias:
- [Estrutura de relatórios de Microsoft Intune de blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [O que é Log Analytics?](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Consultas de log](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Introdução ao Log Analytics no Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure Monitor pastas de trabalho](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [Ferramentas de SIEM (gerenciamento de informações e eventos de segurança)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
