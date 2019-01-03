---
title: Como monitorizar políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Monitorize o estado de conformidade das políticas de gestão de aplicações móveis no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c0603b3cfd2b8fbe1d26e782118fb07526849cfa
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816845"
---
# <a name="how-to-monitor-app-protection-policies"></a>Como monitorizar políticas de proteção de aplicações
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Monitorize o estado de conformidade das políticas de gestão de aplicações móveis (MAM) que aplicou aos utilizadores no painel de proteção de aplicações do Intune no [portal do Azure](https://portal.azure.com). Encontre informações sobre os utilizadores afetados pelas políticas de MAM, o estado de conformidade e quaisquer problemas que os utilizadores possam estar a ter.

Existem três locais diferentes para monitorizar o estado de conformidade:

-   Vista de resumo

-   Vista detalhada

-   Vista de relatórios

> [!NOTE]
> Para obter informações sobre como criar políticas de proteção de aplicações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

## <a name="summary-view"></a>Vista de resumo

1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. Na carga de trabalho **Aplicações do cliente**, selecione **Monitorização** > **Estado de proteção de aplicação** para ver a vista de resumo:

![Mosaico de resumo no painel de gestão de aplicações móveis do Intune](./media/app-protection-user-status-summary.png)

-   **Os utilizadores**: O número total de utilizadores na sua empresa que está a utilizar uma aplicação que está associada a uma política num contexto de trabalho.

-   **GERIDO POR POLÍTICA**: O número de utilizadores que utilizaram uma aplicação que têm uma política atribuída no contexto de trabalho.

-   **NENHUMA POLÍTICA**: O número de utilizadores que estão a utilizar uma aplicação que não é abrangida por nenhuma política num contexto de trabalho. Poderá considerar adicionar estes utilizadores à sua política.
    > [!NOTE]
    > Se tiver múltiplas políticas por plataforma, um utilizador só será considerado gerido por políticas quando lhe tiver sido atribuída pelo menos uma política.

- **Utilizadores sinalizados**: O número de utilizadores que estão com problemas. Atualmente, apenas os utilizadores com dispositivos com jailbreak são reportados como **Utilizadores sinalizados**.


## <a name="detailed-view"></a>Vista detalhada
Pode aceder à vista detalhada do resumo ao selecionar os mosaicos **Estado do utilizador** (com base na plataforma de SO do dispositivo) e **Utilizadores sinalizados**.

### <a name="user-status"></a>Estado de utilizador
Pode procurar um único utilizador e ver o estado de conformidade do mesmo. O painel **Relatório da aplicação** mostra as seguintes informações para um utilizador selecionado:
- Dispositivos associados à conta de utilizador

- Aplicações com a política de MAM no dispositivo

- Estado:

  - **Check-in**: A política foi implementada para o utilizador e a aplicação foi utilizada no contexto profissional pelo menos uma vez.

  - **Sem entrada dada**: A política foi implementada para o usuário, mas a aplicação não foi utilizada no contexto profissional desde então.

>[!NOTE]
> Se os utilizadores que procurou não tiverem a política de MAM implementada, verá uma mensagem a informar que não existem políticas de MAM que abranjam esses utilizadores.

Para ver o relatório para um utilizador, siga estes passos:

1.  Para selecionar um utilizador, aceda ao mosaico **Resumo**.

    ![Captura de ecrã do mosaico de resumo de gestão de aplicações móveis do Intune](./media/MAM-reporting-6.png)

2. No painel **Relatório da aplicação** que abrir, selecione **Selecionar utilizador** para procurar um utilizador do Azure Active Directory.

    ![Captura de ecrã da opção selecionar utilizador no painel relatório da aplicação](./media/MAM-reporting-2.png)

3. Selecione o utilizador na lista. Pode ver os detalhes do estado de conformidade do utilizador.

### <a name="flagged-users"></a>Utilizadores sinalizados
A vista detalhada mostra a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma de SO do dispositivo afetado e um carimbo de data/hora.

## <a name="reporting-view"></a>Vista de relatórios

Pode encontrar os mesmos relatórios da vista Detalhada, bem como relatórios adicionais que o ajudam com o estado de conformidade da política de MAM:

![Captura de ecrã a realçar dois relatórios disponíveis no painel Definições](./media/MAM-reporting-7.png)

-   **Relatório de utilizador de proteção de aplicações:** Descreve as mesmas informações que pode ser encontrada no **estado do utilizador** relatório na secção vista detalhada acima.

-   **Relatório de aplicação de proteção de aplicações:** Ele fornece dois Estados de proteção de aplicações diferentes que os administradores podem selecionar antes de gerar o relatório. Os estados podem ser protegidos ou desprotegidos.

    -   Estado do utilizador para atividade MAM gerida (protegido): Este relatório descreve a atividade de cada aplicação MAM gerida, numa base por utilizador.

        -   Mostra todas as aplicações visadas pelas políticas de MAM para cada utilizador e uma discriminação do estado de cada aplicação como registada com políticas de MAM ou como visada por uma política de MAM, mas nunca registada.
<br></br>
    -   Estado do utilizador para atividade MAM não gerida (não protegido): Este relatório descreve a atividade das aplicações ativadas para MAM que não são atualmente geridos, numa base por utilizador. Isto pode acontecer pelos seguintes motivos:

        -   Estas aplicações estão a ser utilizadas por um utilizador ou por uma aplicação que não seja atualmente visada por uma política de MAM.

        -   Todas as aplicações estão registadas, mas não estão a receber políticas de MAM.

![Captura de ecrã de painel relatório aplicação um utilizador com detalhes para 3 aplicações](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Agrupamento de tabelas

Assim que os dados do **Relatório de utilizador de proteção de aplicações** forem apresentados, pode agregar os dados em função do seguinte:

- **Resultado da validação:** Os dados aparecem agrupados por Estado de proteção de aplicações, que pode ser falhado, aviso ou êxito.
- **Nome da aplicação:** Os dados aparecem agrupados por aplicações (o nome real da aplicação) com falha, aviso ou êxito.

## <a name="export-app-protection-activities-to-csv"></a>Exportar atividades de proteção de aplicações para CSV

Pode exportar todas as atividades de políticas de proteção de aplicações para um ficheiro .csv único. Esta funcionalidade pode ser útil para analisar todos os estados de proteção de aplicações comunicados pelos utilizadores.

Siga estes passos para gerar o Relatório de proteção de aplicações:

1. No painel de gestão de aplicações móveis do Intune, selecione **Relatório de proteção de aplicações**.

    ![Captura de ecrã do link de download de proteção de aplicações](./media/app-protection-report-csv-2.png)

2. Escolha Sim para guardar o relatório e, em seguida, escolha Guardar como e selecione a pasta na qual quer guardar o relatório.

    ![Captura de ecrã da caixa de confirmação Guardar relatório](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte também
[Gerir a transferência de dados entre aplicações iOS](data-transfer-between-apps-manage-ios.md)

* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)
