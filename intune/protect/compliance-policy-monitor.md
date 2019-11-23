---
title: Monitorizar as políticas de conformidade de dispositivos no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o dashboard de conformidade do dispositivo para monitorizar a conformidade global de dispositivos, ver relatórios e ver a conformidade do dispositivo por política e por definição.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/14/2019
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
ms.openlocfilehash: 844e93f3a063ae43342d2967cbd544f3ec425c21
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410149"
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorizar as políticas de conformidade do Dispositivo do Intune

Os relatórios de conformidade ajudam a analisar a conformidade de dispositivos e a resolver problemas relacionados com a conformidade na sua organização. Estes relatórios permitem ver informações sobre:

- Os estados de conformidade geral dos dispositivos
- O estado de conformidade de uma definição individual
- O estado de conformidade de uma política individual
- Abrir dispositivos individuais para ver as definições e políticas específicas que afetam o dispositivo

## <a name="open-the-compliance-dashboard"></a>Abrir o dashboard de conformidade

Abra o **dashboard de conformidade do Dispositivo do Intune**:

1. Sign in to [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Selecione **Conformidade do dispositivo** > **Descrição Geral**. É aberto o **Dashboard de conformidade do dispositivo**.

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

### <a name="device-compliance-status"></a>Device compliance status

The **Device compliance status** chart shows the compliance states for all Intune enrolled devices. Os estados de conformidade do dispositivo são mantidos em duas bases de dados diferentes: Intune e Azure Active Directory.

> [!IMPORTANT]
> O Intune segue o agendamento de registo do dispositivo para todas as avaliações de conformidade no dispositivo. [Saiba mais sobre o agendamento de registo do dispositivo](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Descrições dos diferentes estados de política de conformidade do dispositivo:

- **Conforme**: o dispositivo aplicou com êxito uma ou mais definições de política de conformidade do dispositivo.

- **Período de tolerância**: o dispositivo é visado com uma ou mais definições de política de conformidade do dispositivo. Porém, o utilizador ainda não aplicou as políticas. Isto significa que o dispositivo não está em conformidade embora se encontre no período de tolerância definido pelo administrador.

  - Saiba mais sobre [Ações para dispositivos não conformes](actions-for-noncompliance.md).

- **Não avaliado**: um estado inicial de dispositivos recentemente inscritos Other possible reasons for this state include:

  - Devices that aren't assigned a compliance policy and don't have a trigger to check for compliance
  - Devices that haven't checked in since the compliance policy was last updated
  - Devices not associated to a specific user, such as:
    - iOS devices purchased through Apple's Device Enrollment Program (DEP) that don't have user affinity
    - Android kiosk or Android Enterprise dedicated devices
  - Devices enrolled with a device enrollment manager (DEM) account

- **Não conforme**: o dispositivo não aplicou com êxito uma ou mais definições de política de conformidade do dispositivo ou o utilizador não respeitou as políticas.

- **Dispositivo não sincronizado:** o dispositivo não comunicou o seu estado de política de conformidade do dispositivo devido a um dos motivos seguintes:

  - **Desconhecido**: o dispositivo está offline ou não conseguiu comunicar com o Intune ou o Azure AD por outros motivos.

  - **Erro**: o dispositivo não conseguiu comunicar com o Intune e o Azure AD e recebeu uma mensagem de erro com o motivo.

> [!IMPORTANT]
> Os dispositivos que estão inscritos no Intune, mas não visados pelas políticas de conformidade do dispositivo, são incluídos neste relatório sob o registo **Conforme**.

#### <a name="drill-down-for-more-details"></a>Desagregar para obter mais detalhes

No gráfico **Estado de conformidade do dispositivo**, selecione um estado. Por exemplo, selecione o estado **Não conforme**:

![Selecionar o estado não conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

That action opens the **Device compliance** window, and displays devices in a **Device status** chart. The chart shows you more details on the devices in that state, including operating system platform, last check-in date, and more. 

![Imagem do dashboard que mostra mais detalhes sobre o dispositivo nesse estado específico](./media/compliance-policy-monitor/drill-down-details.png)

Se quiser ver todos os dispositivos pertencentes a um utilizador específico, também pode filtrar o relatório de gráfico ao escrever o e-mail do utilizador.

#### <a name="filter-and-columns"></a>Filtro e colunas

![Selecione o Filtro e Coluna para alterar os resultados no gráfico](./media/compliance-policy-monitor/filter-columns.png)

When you select the **Filter** button, the filter fly-out opens with more options, including the **Compliance** state, **Jailbroken** devices, and more. **Aplique** o filtro para atualizar os resultados.

Utilize a propriedade **Colunas** para adicionar ou remover colunas do resultado do gráfico. Por exemplo, **Nome principal de utilizador** poderá mostrar o endereço de e-mail registado no dispositivo. **Aplique** as colunas para atualizar os resultados.

#### <a name="device-details"></a>Detalhes do dispositivo

In the **Device details** chart, select a specific device, and then select **Device compliance**:

![Selecione um dispositivo específico e, em seguida, Conformidade do Dispositivo para ver as políticas de conformidade aplicadas](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Intune displays more details on the device compliance policy settings applied on that device. Quando selecionar a política específica, serão apresentadas todas as definições na política.

### <a name="devices-without-compliance"></a>Devices without compliance

On the *Compliance status* page, next to the *Policy compliance* chart, you can select the **Devices without compliance policy** tile to view information about devices that don't have any compliance policies assigned:

![Ver dispositivos sem políticas de conformidade](./media/compliance-policy-monitor/devices-without-policies.png)

Quando selecionar o mosaico, serão apresentados todos os dispositivos que não têm uma política de conformidade. Também são apresentados o utilizador do dispositivo, o estado de implementação da política e o modelo do dispositivo.

#### <a name="what-you-need-to-know"></a>O que tem de saber

- Com a definição de segurança **Marcar os dispositivos sem política de conformidade atribuída como**, é importante identificar os dispositivos que não têm uma política de conformidade. Em seguida, pode atribuir pelo menos uma política de conformidade aos mesmos.

  A definição de segurança é configurável no portal do Intune. To to **Devices** > **Compliance policies** > **Compliance policy settings**. Em seguida, defina **Marcar os dispositivos sem política de conformidade atribuída como** para **Conforme** ou **Não conforme**. 

  Saiba mais sobre esta [melhoria de segurança no serviço Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Os utilizadores com uma política de conformidade de qualquer tipo não são apresentados no relatório, independentemente da plataforma do dispositivo. Por exemplo, se tiver atribuído uma política de conformidade para Windows a um utilizador com um dispositivo Android, o dispositivo não será apresentado no relatório. No entanto, o Intune considera que esse dispositivo Android não está conforme. Para evitar problemas, recomendamos que crie políticas para cada plataforma de dispositivo e que as implemente para todos os utilizadores.

### <a name="per-policy-device-compliance"></a>Conformidade do dispositivo por política

The **Policy compliance** chart shows you the policies, and how many devices are compliant and noncompliant. 

![Veja uma lista que inclui a política e a quantidade de dispositivos conformes e não conformes dessa política](./media/compliance-policy-monitor/idc-8.png)

### <a name="setting-compliance"></a>Conformidade com definições

The **Setting compliance** chart shows you all device compliance policy settings from all compliance policies, the platforms the policy settings are applied, and the number of noncompliant devices.

![Veja uma lista de todas as definições nas diferentes políticas](./media/compliance-policy-monitor/idc-10.png)

> [!NOTE]
> A policy can be assigned to a device, and a user on that same device. In some scenarios, a device may sync before the user signs in, such as when the device reboots. Compliance may evaluate this user, and show the device as non compliant. This behavior may also show the System Account as a non-compliant user.
>
> This is a known issue with multi-user Windows 10 devices. Any changes or updates on this behavior are announced in [in development](../fundamentals/in-development.md) and/or [what's new](../fundamentals/whats-new.md).

## <a name="view-compliance-reports"></a>View compliance reports

In addition to using the charts on *Compliance status*, you can view compliance reports from the *Monitor* page of the Admin Center.

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Monitor**, and then from below **Compliance** select the report you want to view. Some of the available compliance reports include:

   - Conformidade do dispositivo
   - Noncompliant devices
   - Dispositivos sem política de conformidade
   - Conformidade com definições
   - Policy compliance
   - Windows health attestation report
   - Estado do agente de ameaça

For more information about reports, see [Intune reports](../fundamentals/reports.md)

## <a name="view-status-of-device-policies"></a>Ver o estado das políticas de dispositivos

Pode verificar os diferentes estados das suas políticas por plataforma. Por exemplo, imaginemos que tem uma política de conformidade do macOS. Quer ver os dispositivos afetados por esta política e saber se existem conflitos ou falhas.

Esta funcionalidade está incluída no relatório de estado do dispositivo:

1. Select **Devices** > **Compliance policies** > **Policies**. É apresentada uma lista de políticas, incluindo a plataforma, se a política estiver atribuída, e mais detalhes.
2. Selecione uma política > **Descrição Geral**. Nesta vista, a atribuição de política inclui os seguintes estados:

    - **Succeeded**: Policy is applied
    - **Error**: The policy failed to apply. Normalmente, a mensagem é apresentada com um código de erro que direciona para uma explicação. 
    - **Conflict**: Two settings are applied to the same device, and Intune can't sort out the conflict. Um administrador deve rever a situação.
    - **Pending**: The device hasn’t checked in with Intune to receive the policy yet. 
    - **Not applicable**: The device can't receive the policy. Por exemplo, a política atualiza uma definição específica para o iOS 11.1, mas o dispositivo está a utilizar o iOS 10. 

3. Para ver detalhes sobre os dispositivos que utilizam esta política, selecione um dos estados. Por exemplo, selecione **Com êxito**. Na janela seguinte, são indicados detalhes dos dispositivos específicos, incluindo o nome do dispositivo e o estado de implementação.

## <a name="how-intune-resolves-policy-conflicts"></a>Como o Intune resolve conflitos de políticas
Se forem aplicadas múltiplas políticas do Intune a um dispositivo, podem ocorrer conflitos de políticas. Se as definições de políticas se sobrepuserem, o Intune utiliza as seguintes regras para resolver eventuais conflitos:

- Se as definições em conflito pertencerem a uma política de configuração do Intune e a uma política de conformidade, as definições da política de conformidade têm prioridade sobre as definições da política de configuração. Isto acontece mesmo que as definições na política de conformidade sejam mais seguras.

- Se tiver implementado múltiplas políticas de conformidade, o Intune utiliza a mais segura destas políticas.
