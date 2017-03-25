---
title: "Monitorizar as políticas de conformidade do dispositivo do Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como monitorizar as políticas de conformidade do dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 503d1dd2-a647-4aea-bf48-55319a3dd8a7
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: f207edab1b6b30d3680164f24d37e55823eec6d3
ms.lasthandoff: 03/15/2017


---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorizar as políticas de conformidade do Dispositivo do Intune

Os relatórios de conformidade ajudam os administradores a analisarem a postura de conformidade dos dispositivos na sua organização e a resolver rapidamente problemas relacionados com a compatibilidade encontrados por utilizadores dentro da organização. Pode ver informações sobre o estado de conformidade geral dos dispositivos, o estado de conformidade de uma definição individual, o estado de conformidade de uma política individual e explorar a fundo os dispositivos individuais para ver as definições e as políticas específicas que afetam o dispositivo.

## <a name="before-you-begin"></a>Antes de começar

Siga os passos abaixo para encontrar o **Dashboard de conformidade do Dispositivo do Intune** no portal do Azure:

1.  Aceda ao [Portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do Intune.

2.  Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3.  Escolha **Intune** &gt; **Conformidade do dispositivo** &gt; **Descrição geral** e, em seguida, o **Dashboard de conformidade do dispositivo** é aberto.

> [!IMPORTANT] 
> Os dispositivos têm de ser inscritos no Intune para receberem políticas de conformidade do dispositivo.

## <a name="device-compliance-dashboard"></a>Dashboard de conformidade do dispositivo

No **Dashboard de conformidade do dispositivo**, pode monitorizar os estados da política de Conformidade do dispositivo, que proporciona relatórios diferentes dentro de mosaicos diferentes que lhe indicam a postura de conformidade dos dispositivos na sua organização. Pode ver os seguintes relatórios:

-   Conformidade do dispositivo global agregada

-   Conformidade do dispositivo por política

-   Conformidade do dispositivo por definição

![Dashboard de conformidade do dispositivo](../media/idc-1.png)

Também pode ver as definições e políticas de conformidade específicas que se aplicam a um dispositivo individual e o estado de conformidade final para cada uma dessas definições no dispositivo.

### <a name="overall-device-compliance-aggregate-report"></a>Relatório da conformidade do dispositivo global agregada

É um gráfico em anel que mostra o estado da conformidade agregada de todos os dispositivos inscritos no Intune. Os estados de conformidade do dispositivo são mantidos em duas bases de dados diferentes, Intune e Azure Active Directory. Veja a seguir mais detalhes sobre os estados da política de conformidade do dispositivo:

-   **Conforme**: o dispositivo aplicou com êxito uma ou mais definições de política de conformidade do dispositivo visadas pelo administrador.

-   **Não conforme:** o dispositivo não conseguiu aplicar uma ou mais definições de política de conformidade do dispositivo visadas pelo administrador ou o utilizador ainda não está a cumprir as políticas visadas pelo administrador.

-   **Período de tolerância:** o dispositivo foi visado pelo administrador com uma ou mais definições de política de conformidade do dispositivo, mas o utilizador ainda não aplicou as políticas, o que significa que o dispositivo não está conforme, mas está no período de tolerância definido pelo administrador.

    -   Saiba mais sobre as Ações para os dispositivos não conformes.

-   **Dispositivos não sincronizados:** o dispositivo não comunicou o seu estado de política de conformidade do dispositivo devido a um dos motivos seguintes:

    -   **Desconhecido**: o dispositivo está offline ou não conseguiu comunicar com o Intune ou o Azure AD por outros motivos.

    -   **Erro**: o dispositivo não conseguiu comunicar com o Intune e o Azure AD e recebeu uma mensagem de erro com o motivo.

> [!IMPORTANT] 
> Os dispositivos que estão inscritos no Intune, mas não visados pelas políticas de conformidade do dispositivo, serão incluídos neste relatório sob o bucket **Conforme**.

#### <a name="drill-down-option"></a>Opção de desagregação

No **Dashboard de conformidade do dispositivo**, se clicar no mosaico Conformidade do dispositivo, pode desagregar o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** específicos para cada dispositivo que foi visado pelas políticas de conformidade do dispositivo.

![Desagregação do dashboard de conformidade do dispositivo](../media/idc-2.png)

Se precisar de mais detalhes sobre um utilizador específico, pode filtrar o relatório de gráfico de Conformidade do dispositivo ao escrever o alias de e-mail do utilizador.

![Utilizador específico do dashboard de conformidade do dispositivo](../media/idc-3.png)

Também pode clicar nos diferentes estados de conformidade no gráfico de Conformidade do dispositivo para ver mais detalhes sobre os estados da política de conformidade dos dispositivos do utilizador.

![Estados diferentes do dashboard de conformidade do dispositivo](../media/idc-4.png)

#### <a name="filter"></a>Filtro

Se clicar no botão **Filtrar**, é apresentada a lista de filtros com as seguintes opções:

-   Modelo

    -   Cadeia da caixa de texto a aceitar a pesquisa gratuita
<br></br>
-   Plataforma

    -   Android

    -   iOS

    -   Mac OS

    -   Windows

    -   Windows Phone

-   Estado

    -   Compatível

    -   Não Conforme

    -   No Período de tolerância

    -   Desconhecido

    -   Erro

Se clicar no botão **Atualizar**, a lista de opções deve fechar-se e os resultados devem ser atualizados de acordo com os critérios do filtro selecionado.

![Botão de atualização de filtro](../media/idc-5.png)

##### <a name="device-details"></a>Detalhes do dispositivo

Ao clicar num dispositivo, abre o **Painel Dispositivos** com o dispositivo selecionado. Este painel apresenta mais detalhes sobre a definição da política de conformidade aplicada a esse dispositivo.

![Dashboard de conformidade do dispositivo](../media/idc-6.png)

Quando clica na definição da política do dispositivo, pode ver que o nome da política de conformidade do dispositivo originou essa definição de conformidade do dispositivo visada pelo administrador.

![Nome da definição de conformidade do dispositivo](../media/idc-7.png)

### <a name="per-policy-device-compliance-report"></a>Relatório de conformidade do dispositivo por política

Este relatório apresenta a vista da política por conformidade e o número total de dispositivos em cada estado de conformidade. O mosaico **Conformidade de política** está disponível no **Dashboard de conformidade do dispositivo** e mostra todas as políticas criadas anteriormente pelo administrador, as plataformas em que a política é aplicada, o número de dispositivos conformes e o número de dispositivos não conformes.

![Relatório de conformidade do dispositivo por política](../media/idc-8.png)

Depois de clicar no mosaico Conformidade de política, clique numa das políticas de conformidade do dispositivo e poderá ver o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** para cada dispositivo que foi visado por essa política de conformidade do dispositivo.

![Mosaico Conformidade de política](../media/idc-9.png)

### <a name="per-setting-device-compliance-report"></a>Relatório de conformidade do dispositivo por definição

Este relatório permite-lhe ver o número total de dispositivos em cada estado de conformidade por definição de conformidade. O mosaico **Conformidade das definições** está disponível no **Dashboard de conformidade do dispositivo** e mostra todas as definições da política de conformidade do dispositivo de todas as políticas de conformidade do dispositivo criadas pelo administrador, as plataformas nas quais as definições de política foram aplicadas e o número de dispositivos não conformes.

![Relatório de conformidade do dispositivo por definição](../media/idc-10.png)

Depois de clicar no mosaico Conformidade das definições, clique numa das definições da política de conformidade do dispositivo para poder ver o **estado de conformidade**, o **alias de e-mail do utilizador**, o **modelo do dispositivo** e a **localização** de cada dispositivo que foi visado por essa definição de política de conformidade do dispositivo.

![Mosaico Conformidade das definições](../media/idc-11.png)
