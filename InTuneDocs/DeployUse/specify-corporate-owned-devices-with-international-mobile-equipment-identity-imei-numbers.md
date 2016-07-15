---
title: "Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI) | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 398d93d4e2317d00a2f9d5f89966aaec3b942504
ms.openlocfilehash: af4b87eb8082ee5ff11cd2d42b788ad17b334bcb


---

# Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)
O Microsoft Intune permite que os administradores importem números de identidade internacional do equipamento móvel (IMEI) para plataformas de dispositivos móveis com números IMEI para ajudar a identificar os dispositivos móveis pertencentes à empresa. Quando inscritos no Intune, os dispositivos com números IMEI importados podem ser visualizados em **Grupos** > **Descrição Geral** > **Todos os Dispositivos** > **Dispositivos pré-inscritos empresariais** > **Por IMEI (Todas as plataformas)**.

1. Na [consola de administração do Microsoft Intune](http://manage.microsoft.com) escolha **Grupos**&gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Pertencentes à Empresa** &gt; **Por IMEI (Todas as plataformas)** e, em seguida, clique em **Adicionar dispositivos…**. Pode adicionar dispositivos de duas formas:

    -   **Carregue um ficheiro CSV que contenha números de série** - crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5000 dispositivos ou 5 MB por ficheiro .csv.

        |||
        |-|-|
        |&lt;IMEI N.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
        |&lt;IMEI Nº. 2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|
        Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Adicione manualmente os detalhes de dispositivos** - introduza o número IMEI e os detalhes de até cinco dispositivos

   Os *Detalhes* são para utilização administrativa para que possa identificar o número IMEI associado a um dispositivo. Estas informações não são enviadas para o dispositivo, mas irão aparecer na consola do Intune.

2.   Escolha **Seguinte**.
3.  No painel **Rever Dispositivos**, pode confirmar os números IMEI de dispositivos que são importados. Também pode decidir se pretende substituir os **Detalhes** dos números IMEI ao serem importados novamente. Pode desmarcar a caixa de verificação **Substituir** para manter os Detalhes atuais. Escolha **Concluir** para importar os números IMEI.
4.  Os números IMEI e as descrições acrescentadas são adicionadas à lista **Por IMEI (Todas as plataformas)**.

Quando o dispositivo com esse número IMEI é inscrito, normalmente, quando um utilizador instala a aplicação de Portal da Empresa e conclui o processo de inscrição, o dispositivo será marcado como sendo de propriedade da Empresa e é apresentado como inscrito no grupo **Dispositivos IMEI**.



<!--HONumber=Jun16_HO3-->


