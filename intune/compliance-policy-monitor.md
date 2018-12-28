---
title: Monitorizar as políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o dashboard de conformidade do dispositivo para monitorizar a conformidade global de dispositivos, ver relatórios e ver a conformidade do dispositivo por política e por definição.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fd401875e1a98690d9673243b28b48347e4c6183
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642817"
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorizar as políticas de conformidade do Dispositivo do Intune

Os relatórios de conformidade ajudam a analisar a conformidade de dispositivos e a resolver problemas relacionados com a conformidade na sua organização. Estes relatórios permitem ver informações sobre:

- Os estados de conformidade geral dos dispositivos
- O estado de conformidade de uma definição individual
- O estado de conformidade de uma política individual
- Abrir dispositivos individuais para ver as definições e políticas específicas que afetam o dispositivo

## <a name="open-the-compliance-dashboard"></a>Abrir o dashboard de conformidade

Abra o **dashboard de conformidade do Dispositivo do Intune**:

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.

2. Selecione **Conformidade do dispositivo** > **Descrição Geral**. É aberto o **Dashboard de conformidade do dispositivo**.

> [!IMPORTANT]
> Os dispositivos têm de ser inscritos no Intune para receberem políticas de conformidade do dispositivo.

## <a name="dashboard-overview"></a>Descrição geral do dashboard

Quando o dashboard é aberto, obtém uma descrição geral com todos os relatórios de conformidade. Nestes relatórios, pode ver e verificar o seguinte:

- Conformidade geral do dispositivo
- Conformidade do dispositivo por política
- Conformidade do dispositivo por definição
- Estado da proteção do dispositivo
- Estado do agente de ameaça

![Imagem do dashboard que mostra o dashboard de conformidade do dispositivo e os diferentes relatórios](./media/compliance-policy-monitor/idc-1.png)

À medida que analisar este relatório em profundidade, também poderá ver todas as definições e políticas de conformidade específicas que se aplicam a um determinado dispositivo, incluindo o estado de conformidade de cada definição.

### <a name="device-compliance-status-report"></a>Relatório do estado de conformidade do dispositivo

O gráfico mostra os estados de conformidade de todos os dispositivos inscritos no Intune. Os Estados de conformidade do dispositivo são mantidos em duas bases de dados diferentes: Intune e Azure Active Directory. 

> [!IMPORTANT]
> Intune segue o agendamento de entrada do dispositivo para todas as avaliações de conformidade no dispositivo. [Saiba mais sobre o agendamento da entrada dispositivo](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Descrições dos diferentes estados de política de conformidade do dispositivo:

- **Em conformidade**: O dispositivo aplicou com êxito um ou mais definições de política de conformidade de dispositivos.

- **Período de tolerância:** O dispositivo é direcionado com um ou mais definições de política de conformidade de dispositivos. Porém, o utilizador ainda não aplicou as políticas. Isto significa que o dispositivo não está em conformidade embora se encontre no período de tolerância definido pelo administrador.

  - Saiba mais sobre [Ações para dispositivos não conformes](actions-for-noncompliance.md).

- **Não avaliado**: Um Estado inicial de dispositivos inscritos recentemente. Outras razões possíveis para este problema de estado:

  - Dispositivos que não são atribuídos uma política de conformidade e não tem um acionador para verificar a conformidade
  - Dispositivos que não se tenham registado, uma vez que a política de conformidade foi atualizado pela última vez.
  - Dispositivos não associados a um utilizador removeu
  - Dispositivos inscritos com uma conta de gestor (DEM) de inscrição de dispositivos

- **Não conforme:** O dispositivo não conseguiu aplicar uma ou mais definições de política de conformidade de dispositivos. ou o utilizador não respeitou as políticas.

- **Dispositivo não sincronizado:** O dispositivo não conseguiu comunicar o estado de política de conformidade do dispositivo porque um dos seguintes motivos:

  - **Desconhecido**: O dispositivo está offline ou não conseguiu comunicar com o Intune ou do Azure AD por outros motivos.

  - **Erro**: O dispositivo não conseguiu comunicar com o Intune e o Azure AD e recebeu uma mensagem de erro com o motivo.

> [!IMPORTANT]
> Os dispositivos que estão inscritos no Intune, mas não visados pelas políticas de conformidade do dispositivo, são incluídos neste relatório sob o registo **Conforme**.

#### <a name="drill-down-for-more-details"></a>Desagregar para obter mais detalhes

No gráfico **Estado de conformidade do dispositivo**, selecione um estado. Por exemplo, selecione o estado **Não conforme**:

![Selecionar o estado não conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

Desta forma, apresenta mais detalhes sobre os dispositivos nesse estado, incluindo a plataforma do sistema operativo, a data da última entrada e mais. 

![Imagem do dashboard que mostra mais detalhes sobre o dispositivo nesse estado específico](./media/compliance-policy-monitor/drill-down-details.png)

Se quiser ver todos os dispositivos pertencentes a um utilizador específico, também pode filtrar o relatório de gráfico ao escrever o e-mail do utilizador.

#### <a name="filter-and-columns"></a>Filtro e colunas

![Selecione o Filtro e Coluna para alterar os resultados no gráfico](./media/compliance-policy-monitor/filter-columns.png)

Quando selecionar o botão **Filtro**, será apresentada a lista de filtros com mais opções, incluindo o estado de conformidade, os dispositivos com jailbreak e mais. **Aplique** o filtro para atualizar os resultados.

Utilize a propriedade **Colunas** para adicionar ou remover colunas do resultado do gráfico. Por exemplo, **Nome principal de utilizador** poderá mostrar o endereço de e-mail registado no dispositivo. **Aplique** as colunas para atualizar os resultados.

#### <a name="device-details"></a>Detalhes do dispositivo

No gráfico, selecione um dispositivo específico e, em seguida, selecione **Conformidade do dispositivo**:

![Selecione um dispositivo específico e, em seguida, Conformidade do Dispositivo para ver as políticas de conformidade aplicadas](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Desta forma, apresenta mais detalhes sobre as definições da política de conformidade aplicadas a esse dispositivo. Quando selecionar a política específica, serão apresentadas todas as definições na política.

### <a name="devices-without-compliance-policy"></a>Dispositivos sem política de conformidade
Em **Conformidade do dispositivo** > **Descrição geral**, o relatório também identifica dispositivos que não tenham políticas de conformidade atribuídas:

![Ver dispositivos sem políticas de conformidade](./media/compliance-policy-monitor/devices-without-policies.png)

Quando selecionar o mosaico, serão apresentados todos os dispositivos que não têm uma política de conformidade. Também são apresentados o utilizador do dispositivo, o estado de implementação da política e o modelo do dispositivo.

#### <a name="what-you-need-to-know"></a>O que tem de saber

- Com a definição de segurança **Marcar os dispositivos sem política de conformidade atribuída como**, é importante identificar os dispositivos que não têm uma política de conformidade. Em seguida, pode atribuir pelo menos uma política de conformidade aos mesmos.

  A definição de segurança é configurável no portal do Intune. Selecione **Conformidade do dispositivo** > **Definições de política de conformidade**. Em seguida, defina **Marcar os dispositivos sem política de conformidade atribuída como** para **Conforme** ou **Não conforme**. 

  Saiba mais sobre esta [melhoria de segurança no serviço Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Os utilizadores com uma política de conformidade de qualquer tipo não são apresentados no relatório, independentemente da plataforma do dispositivo. Por exemplo, se tiver atribuído uma política de conformidade para Windows a um utilizador com um dispositivo Android, o dispositivo não será apresentado no relatório. No entanto, o Intune considera que esse dispositivo Android não está conforme. Para evitar problemas, recomendamos que crie políticas para cada plataforma de dispositivo e que as implemente para todos os utilizadores.

### <a name="per-policy-device-compliance-report"></a>Relatório de conformidade do dispositivo por política

O relatório **Conformidade do dispositivo** > **Conformidade com a política** mostra as políticas e a quantidade de dispositivos que estão conformes e não conformes. 

![Veja uma lista que inclui a política e a quantidade de dispositivos conformes e não conformes dessa política](./media/compliance-policy-monitor/idc-8.png)

Quando seleciona uma política específica, pode ver o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** de cada dispositivo visado por essa política de conformidade.

## <a name="setting-compliance-report"></a>Relatório de conformidade com as definições

O relatório **Conformidade do dispositivo** > **Conformidade da definição** mostra o número total de dispositivos em cada estado de conformidade por definição de conformidade. Apresenta todas as definições de política de conformidade do dispositivo de todas as políticas de conformidade, as plataformas onde as definições de política foram aplicadas e o número de dispositivos não conformes.

![Veja uma lista de todas as definições nas diferentes políticas](./media/compliance-policy-monitor/idc-10.png)

Quando seleciona uma definição específica, pode ver o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** de cada dispositivo visado por essa definição.

> [!NOTE]
> Os dispositivos Windows 10 que estão associados ao Microsoft Azure AD podem mostrar a Conta do Sistema como um utilizador em não conformidade. Este comportamento é esperado e não afeta a conformidade geral do dispositivo. 

## <a name="view-status-of-device-policies"></a>Ver o estado das políticas de dispositivos

Pode verificar os diferentes estados das suas políticas por plataforma. Por exemplo, imaginemos que tem uma política de conformidade do macOS. Quer ver os dispositivos afetados por esta política e saber se existem conflitos ou falhas.

Esta funcionalidade está incluída no relatório de estado do dispositivo:

1. Selecione **Conformidade do dispositivo** > **Políticas**. É apresentada uma lista de políticas, incluindo a plataforma, se a política estiver atribuída, e mais detalhes.
2. Selecione uma política > **Descrição Geral**. Nesta vista, a atribuição de política inclui os seguintes estados:

    - Foi efetuada com êxito: A política é aplicada
    - Erro: Não foi possível aplicar a política. Normalmente, a mensagem é apresentada com um código de erro que direciona para uma explicação. 
    - Conflito: Duas definições são aplicadas ao mesmo dispositivo, e o Intune não é possível classificar o conflito. Um administrador deve rever a situação.
    - Pendente: O dispositivo não for verificado Intune para receber a política ainda. 
    - Não aplicável: O dispositivo não pode receber a política. Por exemplo, a política atualiza uma definição específica para o iOS 11.1, mas o dispositivo está a utilizar o iOS 10. 

3. Para ver detalhes sobre os dispositivos que utilizam esta política, selecione um dos estados. Por exemplo, selecione **Com êxito**. Na janela seguinte, são indicados detalhes dos dispositivos específicos, incluindo o nome do dispositivo e o estado de implementação.

## <a name="how-intune-resolves-policy-conflicts"></a>Como o Intune resolve conflitos de políticas
Se forem aplicadas múltiplas políticas do Intune a um dispositivo, podem ocorrer conflitos de políticas. Se as definições de políticas se sobrepuserem, o Intune utiliza as seguintes regras para resolver eventuais conflitos:

- Se as definições em conflito pertencerem a uma política de configuração do Intune e a uma política de conformidade, as definições da política de conformidade têm prioridade sobre as definições da política de configuração. Isto acontece mesmo que as definições na política de conformidade sejam mais seguras.

- Se tiver implementado múltiplas políticas de conformidade, o Intune utiliza a mais segura destas políticas.
