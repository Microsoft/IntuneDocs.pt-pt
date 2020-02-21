---
title: Monitorizar as políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o dashboard de conformidade do dispositivo para monitorizar a conformidade global de dispositivos, ver relatórios e ver a conformidade do dispositivo por política e por definição.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 128f615a9551c31e6b0e0de4f1d269083874bf48
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515123"
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorizar as políticas de conformidade do Dispositivo do Intune

Os relatórios de conformidade ajudam a analisar a conformidade de dispositivos e a resolver problemas relacionados com a conformidade na sua organização. Estes relatórios permitem ver informações sobre:

- Os estados de conformidade geral dos dispositivos
- O estado de conformidade de uma definição individual
- O estado de conformidade de uma política individual
- Abrir dispositivos individuais para ver as definições e políticas específicas que afetam o dispositivo

## <a name="open-the-compliance-dashboard"></a>Abrir o dashboard de conformidade

Abra o **dashboard de conformidade do Dispositivo do Intune**:

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **visão geral** > separador de **conformidade.**

> [!IMPORTANT]
> Os dispositivos têm de ser inscritos no Intune para receberem políticas de conformidade do dispositivo.

## <a name="dashboard-overview"></a>Descrição geral do dashboard

Quando o dashboard é aberto, obtém uma descrição geral com todos os relatórios de conformidade. Nestes relatórios, pode ver e verificar o seguinte:

- Conformidade geral do dispositivo
- Conformidade do dispositivo por política
- Conformidade do dispositivo por definição
- Estado do agente de ameaça
- Estado da proteção do dispositivo

![Imagem do dashboard que mostra o dashboard de conformidade do dispositivo e os diferentes relatórios](./media/compliance-policy-monitor/idc-1.png)

À medida que analisar este relatório em profundidade, também poderá ver todas as definições e políticas de conformidade específicas que se aplicam a um determinado dispositivo, incluindo o estado de conformidade de cada definição.

### <a name="device-compliance-status"></a>Estado de conformidade do dispositivo

O gráfico de conformidade do **dispositivo** mostra os estados de conformidade de todos os dispositivos matriculados intune. Os estados de conformidade do dispositivo são mantidos em duas bases de dados diferentes: Intune e Azure Active Directory.

> [!IMPORTANT]
> O Intune segue o agendamento de registo do dispositivo para todas as avaliações de conformidade no dispositivo. [Saiba mais sobre o agendamento de registo do dispositivo](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Descrições dos diferentes estados de política de conformidade do dispositivo:

- **Conforme**: o dispositivo aplicou com êxito uma ou mais definições de política de conformidade do dispositivo.

- **Período de tolerância**: o dispositivo é visado com uma ou mais definições de política de conformidade do dispositivo. Porém, o utilizador ainda não aplicou as políticas. Isto significa que o dispositivo não está em conformidade embora se encontre no período de tolerância definido pelo administrador.

  - Saiba mais sobre [Ações para dispositivos não conformes](actions-for-noncompliance.md).

- **Não avaliado**: um estado inicial de dispositivos recentemente inscritos Outras razões possíveis para este estado incluem:

  - Dispositivos que não são atribuídos uma política de conformidade e não têm um gatilho para verificar a conformidade
  - Dispositivos que não fizeram check-in desde que a política de conformidade foi atualizada pela última vez
  - Dispositivos não associados a um utilizador específico, tais como:
    - dispositivos iOS/iPadOS adquiridos através do Programa de Inscrição de Dispositivos da Apple (DEP) que não têm afinidade do utilizador
    - Quiosque Android ou dispositivos android enterprise dedicados
  - Dispositivos matriculados com uma conta de gestor de inscrição de dispositivos (DEM)

- **Não conforme**: o dispositivo não aplicou com êxito uma ou mais definições de política de conformidade do dispositivo ou o utilizador não respeitou as políticas.

- **Dispositivo não sincronizado:** o dispositivo não comunicou o seu estado de política de conformidade do dispositivo devido a um dos motivos seguintes:

  - **Desconhecido**: o dispositivo está offline ou não conseguiu comunicar com o Intune ou o Azure AD por outros motivos.

  - **Erro**: o dispositivo não conseguiu comunicar com o Intune e o Azure AD e recebeu uma mensagem de erro com o motivo.

> [!IMPORTANT]
> Os dispositivos que estão inscritos no Intune, mas não visados pelas políticas de conformidade do dispositivo, são incluídos neste relatório sob o registo **Conforme**.

#### <a name="drill-down-for-more-details"></a>Desagregar para obter mais detalhes

No gráfico **Estado de conformidade do dispositivo**, selecione um estado. Por exemplo, selecione o estado **Não conforme**:

![Selecionar o estado não conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

Esta ação abre a janela de conformidade do **Dispositivo** e exibe dispositivos num gráfico de **estado do Dispositivo.** O gráfico mostra-lhe mais detalhes sobre os dispositivos nesse estado, incluindo plataforma do sistema operativo, última data de check-in, e muito mais.
![imagem do Dashboard mostra mais detalhes sobre o dispositivo nesse estado específico](./media/compliance-policy-monitor/drill-down-details.png)

Se quiser ver todos os dispositivos pertencentes a um utilizador específico, também pode filtrar o relatório de gráfico ao escrever o e-mail do utilizador.

#### <a name="filter-and-columns"></a>Filtro e colunas

![Selecione o Filtro e Coluna para alterar os resultados no gráfico](./media/compliance-policy-monitor/filter-columns.png)

Quando seleciona o botão **Filter,** o fly-out do filtro abre com mais opções, incluindo o estado **de Conformidade,** dispositivos **Jailbroken** e muito mais. **Aplique** o filtro para atualizar os resultados.

Utilize a propriedade **Colunas** para adicionar ou remover colunas do resultado do gráfico. Por exemplo, **Nome principal de utilizador** poderá mostrar o endereço de e-mail registado no dispositivo. **Aplique** as colunas para atualizar os resultados.

#### <a name="device-details"></a>Detalhes do dispositivo

Na ficha de detalhes do **Dispositivo,** selecione um dispositivo específico e, em seguida, selecione a **conformidade do Dispositivo:**

![Selecione um dispositivo específico e, em seguida, Conformidade do Dispositivo para ver as políticas de conformidade aplicadas](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Intune apresenta mais detalhes sobre as definições da política de conformidade do dispositivo aplicadas nesse dispositivo. Quando selecionar a política específica, serão apresentadas todas as definições na política.

### <a name="devices-without-compliance"></a>Dispositivos sem conformidade

Na página de *compliance,* junto ao gráfico de conformidade da *Política,* pode selecionar os **Dispositivos sem** a política de conformidade para visualizar informações sobre dispositivos que não tenham quaisquer políticas de conformidade atribuídas:

![Ver dispositivos sem políticas de conformidade](./media/compliance-policy-monitor/devices-without-policies.png)

Quando selecionar o mosaico, serão apresentados todos os dispositivos que não têm uma política de conformidade. Também são apresentados o utilizador do dispositivo, o estado de implementação da política e o modelo do dispositivo.

#### <a name="what-you-need-to-know"></a>O que tem de saber

- Com a definição de segurança **Marcar os dispositivos sem política de conformidade atribuída como**, é importante identificar os dispositivos que não têm uma política de conformidade. Em seguida, pode atribuir pelo menos uma política de conformidade aos mesmos.

  A definição de segurança é configurável no portal do Intune. Para **dispositivos** > políticas de **conformidade** > **definições**de política de conformidade . Em seguida, defina **Marcar os dispositivos sem política de conformidade atribuída como** para **Conforme** ou **Não conforme**.

  Saiba mais sobre esta [melhoria de segurança no serviço Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Os utilizadores com uma política de conformidade de qualquer tipo não são apresentados no relatório, independentemente da plataforma do dispositivo. Por exemplo, se tiver atribuído uma política de conformidade para Windows a um utilizador com um dispositivo Android, o dispositivo não será apresentado no relatório. No entanto, o Intune considera que esse dispositivo Android não está conforme. Para evitar problemas, recomendamos que crie políticas para cada plataforma de dispositivo e que as implemente para todos os utilizadores.

### <a name="per-policy-device-compliance"></a>Conformidade do dispositivo por política

O gráfico de **conformidade da Política** mostra-lhe as políticas e quantos dispositivos são conformes e não conformes.

![Veja uma lista que inclui a política e a quantidade de dispositivos conformes e não conformes dessa política](./media/compliance-policy-monitor/idc-8.png)

### <a name="setting-compliance"></a>Conformidade com definições

O gráfico de conformidade de **Definição** mostra-lhe todas as definições de política de conformidade do dispositivo de todas as políticas de conformidade, as plataformas as definições de política são aplicadas e o número de dispositivos não conformes.

![Veja uma lista de todas as definições nas diferentes políticas](./media/compliance-policy-monitor/idc-10.png)

## <a name="view-compliance-reports"></a>Ver relatórios de conformidade

Além de utilizar as tabelas sobre o estado de *Conformidade,* pode ir ao **Reports** > **conformidade com**o Dispositivo .

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **Monitor**, e depois a partir de baixo **A conformidade** selecione o relatório que pretende ver. Alguns dos relatórios de conformidade disponíveis incluem:

   - Conformidade do dispositivo
   - Dispositivos não conformes
   - Dispositivos sem política de conformidade
   - Conformidade com definições
   - Conformidade com a política
   - Relatório de atesta de saúde do Windows
   - Estado do agente de ameaça

Para mais informações sobre relatórios, consulte [relatórios Intune](../fundamentals/reports.md)

## <a name="view-status-of-device-policies"></a>Ver o estado das políticas de dispositivos

Pode verificar os diferentes estados das suas políticas por plataforma. Por exemplo, imaginemos que tem uma política de conformidade do macOS. Quer ver os dispositivos afetados por esta política e saber se existem conflitos ou falhas.

Esta funcionalidade está incluída no relatório de estado do dispositivo:

1. Selecione **Dispositivos** > políticas de **conformidade** > **Políticas**. É apresentada uma lista de políticas, incluindo a plataforma, se a política estiver atribuída, e mais detalhes.
2. Selecione uma política > **Descrição Geral**. Nesta vista, a atribuição de política inclui os seguintes estados:

    - **Sucesso**: A política é aplicada
    - **Erro**: A apólice não se aplica. Normalmente, a mensagem é apresentada com um código de erro que direciona para uma explicação.
    - **Conflito**: Duas configurações são aplicadas no mesmo dispositivo, e Intune não pode resolver o conflito. Um administrador deve rever a situação.
    - **Pendente**: O dispositivo ainda não fez o check-in com a Intune para receber a apólice.
    - **Não aplicável:** O dispositivo não pode receber a apólice. Por exemplo, a política atualiza uma definição específica para o iOS 11.1, mas o dispositivo está a utilizar o iOS 10.

3. Para ver detalhes sobre os dispositivos que utilizam esta política, selecione um dos estados. Por exemplo, selecione **Com êxito**. Na janela seguinte, são indicados detalhes dos dispositivos específicos, incluindo o nome do dispositivo e o estado de implementação.

## <a name="how-intune-resolves-policy-conflicts"></a>Como o Intune resolve conflitos de políticas

Se forem aplicadas múltiplas políticas do Intune a um dispositivo, podem ocorrer conflitos de políticas. Se as definições de políticas se sobrepuserem, o Intune utiliza as seguintes regras para resolver eventuais conflitos:

- Se as definições em conflito pertencerem a uma política de configuração do Intune e a uma política de conformidade, as definições da política de conformidade têm prioridade sobre as definições da política de configuração. Isto acontece mesmo que as definições na política de conformidade sejam mais seguras.

- Se tiver implementado múltiplas políticas de conformidade, o Intune utiliza a mais segura destas políticas.

## <a name="next-steps"></a>Próximos passos

[Visão geral das políticas de conformidade](device-compliance-get-started.md)
