---
title: Gerir alertas | Microsoft Intune
description: "Utilize a área de trabalho Alertas para avaliar o estado de funcionamento geral dos dispositivos na sua organização."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pbala
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9a124663a80bb477d0312faa0fb43e4457ba8246
ms.openlocfilehash: 54dd8c6bae6c02e7dde3582b439d106261bc490b


---

# Gerir alertas no Microsoft Intune
Utilize a área de trabalho **Alertas** na consola de administração do Intune para avaliar o estado de funcionamento geral dos dispositivos na sua organização e identificar problemas.

#### Para ver alertas ativos

1.  Na consola de administração do Intune, efetue um dos seguintes procedimentos:

    -   **Para apresentar informações gerais sobre alertas**, incluindo os três alertas principais e o número total de alertas ativos, clique em **Descrição Geral do Sistema**. Pode clicar nas ligações nestes alertas para desagregar para obter informações mais detalhadas.

    -   **Para apresentar dados de resumo para alertas**, clique em **Alertas &gt; Descrição Geral**. Na página **Descrição Geral dos Alertas**, a área **Resumo do Tipo de Alerta** apresenta um resumo dos alertas. Os alertas críticos são apresentados primeiro. Pode clicar nas ligações nestes alertas para desagregar para obter informações mais detalhadas.

        > [!NOTE]
        > Em alguns casos, um tipo de alerta pode ser apresentado mais do que uma vez na lista **Resumo do Tipo de Alerta**.
        >
        > Por exemplo, as seguintes instâncias do tipo de alerta Espaço Livre em Disco Lógico podem aparecer na lista:
        >
        > -   Espaço Livre em Disco Lógico 3
        > -   Espaço Livre em Disco Lógico 2
        >
        > Este comportamento ocorre quando o mesmo tipo de alerta é gerado para dispositivos que estão a executar sistemas operativos diferentes. No exemplo, a primeira instância do tipo de alerta Espaço Livre em Disco Lógico, Espaço Livre em Disco Lógico 3, pode ter sido gerado por computadores com o Windows® 7. A segunda instância do tipo de alerta Espaço Livre em Disco Lógico pode ter sido gerado por computadores com o Windows Vista®.

    -   **Para apresentar todos os alertas ativos**, clique em **Alertas &gt; Todos os Alertas**. A página **Alertas** apresenta uma lista de todos os alertas ativos com as seguintes colunas:

        1.  **Nome** - o nome do tipo de alerta que gerou o alerta.

        2.  **Origem** - uma ligação para a origem do alerta. Se o limiar de apresentação do tipo de alerta estiver definido como **Apresentar Tudo**, esta ligação apresenta um único dispositivo. Se o limiar de apresentação do tipo de alerta estiver definido como um valor, esta ligação apresenta uma lista de cada dispositivo que é afetado por este alerta.

        3.  **Última Atualização** - Indica a hora em que o alerta foi modificado pela última vez. Se um alerta estiver fechado, será apresentada a hora em que o alerta foi fechado.

        4.  **Gravidade** - Indica a gravidade do alerta

## Ver Alertas do Quadro de Avisos
Os alertas do quadro de avisos fornecem anúncios de serviço importantes como uma atualização, manutenção e indisponibilidade futura do serviço. Utilize este procedimento para ver e gerir alertas do quadro de avisos.

#### Para ver e gerir alertas do quadro de avisos

1.  Na consola de administração do Intune, clique em **Descrição Geral do Sistema**.

2.  Se existirem anúncios do serviço importantes, estes são apresentados na área **Quadro de Avisos**.

3.  Se pretende exportar um alerta do quadro de avisos para um ficheiro de valores separados por vírgulas (.csv) ou ficheiro HTML, na consola de administração do Intune, clique em **Alertas &gt; Todos os Alertas &gt; Avisos**. Selecione um aviso, clique no ícone exportar lista e, em seguida, siga as instruções.

## Rever Estados do Intune
Na área de trabalho **Descrição Geral do Sistema**, consulte os resumos do Estado do Sistema para Endpoint Protection, Updates, Agent Health, Policy e Software, para o ajudar a identificar e a atribuir prioridades a problemas que necessitam da sua atenção imediata. Uma ligação para o resumo **Estado do Serviço** também é fornecida nas mensagens de erro quando o sistema é interrompido. Um resumo do **Estado do Serviço** mostra os detalhes do problema em cada localização e mostra sempre a hora da última atualização.

#### Para ver o estado da sua subscrição

1.  Na consola de administração do Intune, clique em **Descrição Geral do Sistema**.

2.  Na área **Estado do Sistema**, pode examinar o estado dos vários componentes do Microsoft Intune. Muitos dos itens contêm ligações que permitem desagregar para obter mais informações. Por exemplo, em **Endpoint Protection**, selecionar o número de instâncias irá apresentar a área de trabalho **Endpoint Protection** com uma lista do software maligno que foi detetado. Selecionar o número de dispositivos irá apresentar a área de trabalho **Grupos** com uma lista de dispositivos nos quais foi detetado software maligno.

## Fechar e Reativar Alertas
Os alertas do Intune permanecem ativos até que um dos seguintes eventos ocorra:

-   O problema que causou a criação do alerta foi resolvido.

-   O alerta foi fechado manualmente.

-   Passaram 5 dias desde que o alerta foi gerado. Após 45 dias, o alerta expira e é fechado automaticamente.

Os alertas que são marcados como fechados são eliminados permanentemente após 90 dias.

#### Para fechar um alerta manualmente

1.  Na consola de administração do Intune, efetue um dos seguintes procedimentos:

    1.  **Para fechar um alerta a partir da lista de Alertas** – Clique em **Alertas &gt; Todos os Alertas**. Selecione um alerta e, em seguida, clique em **Fechar Alerta**.

    2.  **Para fechar um alerta para um dispositivo específico** – Clique em **Grupos &gt; Todos os Dispositivos**. Selecione um dispositivo e clique em **Ver Propriedades**. Em seguida, no separador **Alertas**, selecione um alerta e clique em **Fechar Alerta**.

    3.  **Para fechar um alerta do quadro de avisos** - Clique em **Descrição Geral do Sistema**. Clique no **X** junto ao alerta do quadro de avisos.

#### Para ver e reativar alertas fechados

1.  Na consola de administração do Intune, clique em **Alertas &gt; Todos os Alertas**.

2.  Na lista **Filtros**, clique em **Fechados**.

    Os nomes e as informações adicionais sobre os alertas são apresentados no painel de lista de gestão. Os detalhes sobre o alerta selecionado são apresentados no painel de pré-visualização.

3.  Para reativar o alerta selecionado, clique em **Reativar Alerta**.

### Consulte também
[Seja notificado através de alertas do Microsoft Intune](get-notified-by-alerts.md)



<!--HONumber=Jul16_HO4-->


