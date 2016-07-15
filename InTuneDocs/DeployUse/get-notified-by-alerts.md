---
title: "Ser notificado através de alertas | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 396ea714-0433-4bd5-a934-8d0b477f28e4
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e929a95d95b71e22d46e124f1a423af7046b0539
ms.openlocfilehash: f1dd166b7b1278003ac8785b8be07c29396dfe8c


---

# Seja notificado através de alertas do Microsoft Intune
Os alertas mantêm-no a par do que está a acontecer no Microsoft Intune.

Por exemplo, os alertas podem notificá-lo sobre os seguintes eventos:

-   Um problema com o Exchange Connector que afeta a gestão de dispositivos móveis

-   Foi encontrado software maligno num computador

-   Foi detetado um conflito entre duas políticas do Intune


## Como funcionam os alertas
Os alertas são gerados com base nos **tipos de alerta**, um conjunto de regras pré-configuradas incorporadas no Intune. Por exemplo, o tipo de alerta **Armazenamento na nuvem tem 10% de espaço livre ou menos** alerta-o se estiver a ficar sem espaço para armazenar as suas aplicações na nuvem. Pode ativar ou desativar e configurar as propriedades para cada tipo de alerta. Por exemplo, utilizando o tipo de alerta acima, pode configurar:

-   **Estado:** Se este tipo de alerta está ativado ou desativado

-   **Gravidade:** Qual é a gravidade deste alerta?


|Gravidade|Detalhes|
|--------|-------|
    |![Alerta crítico](../media/Critical-Alert.jpg)|Indica um problema grave que deve investigar logo que possível, por exemplo, quando tenha sido detetado software maligno num computador.|
    |![Alerta de aviso](../media/Warning-Alert.jpg)|Indica um problema que não é atualmente grave, mas pode tornar-se grave se não atuar, por exemplo, atualizações de segurança que aguardem instalação.|
    |![Alerta informativo](../media/Informational-Alert.jpg)|Indica informações que não são críticas para as suas operações, por exemplo, uma nova versão do Exchange Connector disponível.|

Outros tipos de alerta poderão conter outros itens que pode configurar, como a percentagem de dispositivos que têm de ser afetados por um problema antes de o alerta ser gerado.

**Quando os critérios de um tipo de alerta são cumpridos, é gerado um alerta que é apresentado na consola de administração do Intune.**

Além disso, pode configurar o Intune para notificá-lo por e-mail quando é gerado um alerta.

## Configurar alertas
Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Administração** &gt; **Alertas e Notificações** e, em seguida, escolha uma das seguintes tarefas de configuração:

|Tarefa|Descrição|
|--------|---------------|
|**Tipos de Alerta**|Escolha o tipo de alerta que pretende configurar e, em seguida, efetue um dos seguintes procedimentos:<br /><br />Escolha **Configurar**. Na caixa de diálogo **Configurar Tipo de Alerta**, configure as definições que pretende e escolha **OK**.<br /><br />**Ative** ou **Desative** o alerta.<br /><br />Expanda o nó **Tipos de Alerta** e escolha uma categoria para ver apenas os tipos de alerta dessa categoria.|
|**Destinatários**|Escolha **Adicionar** para adicionar um novo endereço de e-mail que irá receber as notificações de e-mail que configurar.<br /><br />Também pode **Editar** ou **Eliminar** destinatários existentes.<br /><br />Para receber notificações, tem de adicionar também este endereço de e-mail como um destinatário em **Regras de Notificação**.|
|**Regras de Notificação**|Configura regras que definem a quem será enviado um alerta de e-mail. Pode:<br /><br />**Escolher uma regra existente** - escolha uma regra e, em seguida, escolha **Selecionar Destinatários**. Em seguida, pode selecionar todos os destinatários que irão receber um e-mail quando é gerado um alerta que cumpre esta regra.<br /><br />**Criar uma nova regra** - Introduza um nome para a regra, selecione as categorias de alerta e a gravidade do alerta aplicáveis às regras, selecione os grupos de dispositivos aos quais se aplica a regra e selecione os utilizadores que irão receber um e-mail quando for gerado um alerta.<br /><br />Também pode **Ativar**, **Desativar**, **Editar**ou **Eliminar** uma regra existente.|

## Trabalhar com alertas
Utilize as opções seguintes para o ajudar a trabalhar com alertas a partir da consola de administração do Intune.

|Opção|Descrição|
|----------|---------------|
|**Ver alertas ativos**|Escolha um dos seguintes:<br /><br />**Ver um resumo dos alertas** - Na área de trabalho **Dashboard**, os erros principais são apresentados no painel de Alertas. Escolha o painel para ver informações mais detalhadas.<br /><br />Além disso, pode ver um resumo dos alertas na página de **Descrição Geral** da área de trabalho dos **Alertas** .<br /><br />**Ver todos os alertas** - na área de trabalho **Alertas**, escolha **Todos os Alertas**.|
|**Ver avisos**|Escolha um dos seguintes:<br /><br />Na área de trabalho **Dashboard**, escolha **Avisos**.<br /><br />Na área de trabalho **Alertas**, escolha **Todos os Alertas** &gt; **Avisos**.|
|**Fechar um alerta**|Na lista de alertas, selecione o alerta a fechar e, em seguida, escolha **Fechar Alerta**.<br /><br />Os alertas fechados são eliminados definitivamente após 90 dias.|
|**Reativar um alerta fechado**|Na lista de alertas, defina o menu pendente **Filtros** como **Fechados**.<br /><br />Na lista de alertas fechados, selecione aquele que quer reativar e escolha **Reativar Alerta**.|
Os alertas do Intune permanecem ativos até que:

-   O problema que originou o alerta seja resolvido

-   O alerta seja fechado manualmente

-   passem 45 dias desde que o alerta foi gerado

> [!TIP]
> Se for gerado o mesmo alerta por dispositivos com sistemas operativos diferentes, poderá ver várias versões do mesmo alerta na lista de alertas.

### Consulte também
[Monitorização e relatórios com o Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


