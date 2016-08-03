---
title: "Especificar os números IMEI | Microsoft Intune"
description: "O Microsoft Intune permite aos administradores importar números IMEI para plataformas de dispositivos móveis para ajudar a identificar os dispositivos móveis pertencentes à empresa"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 4e2092182dbda4523c19afeabc34aa0166962c40


---

# Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)
O Microsoft Intune permite que os administradores importem números de identidade internacional do equipamento móvel (IMEI) para plataformas de dispositivos móveis com números IMEI para ajudar a identificar os dispositivos móveis pertencentes à empresa. Quando inscritos no Intune, os dispositivos com números IMEI importados podem ser visualizados em **Grupos** > **Descrição Geral** > **Todos os Dispositivos**. O **Grupo de dispositivos** lista os dispositivos apresentados com números IMEI importados como **Empresa** na coluna **Propriedade**.

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



<!--HONumber=Jul16_HO4-->


