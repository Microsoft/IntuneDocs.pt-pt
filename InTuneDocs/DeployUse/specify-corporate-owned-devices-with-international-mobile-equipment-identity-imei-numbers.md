<<<<<<< HEAD
---
title: "Especificar os números IMEI | Microsoft Intune"
description: "O Microsoft Intune permite aos administradores importar números IMEI para plataformas de dispositivos móveis para ajudar a identificar os dispositivos móveis pertencentes à empresa"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: c6b01a5efc0f60622b95623fd91f192c267ff766
ms.openlocfilehash: 9bd2b4bb676e23712c0a668161b81c4e352bce87

||||||| merged common ancestors
---
title: "Especificar os números IMEI | Microsoft Intune"
description: "O Microsoft Intune permite aos administradores importar números IMEI para plataformas de dispositivos móveis para ajudar a identificar os dispositivos móveis pertencentes à empresa"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: c6b01a5efc0f60622b95623fd91f192c267ff766
ms.openlocfilehash: 9bd2b4bb676e23712c0a668161b81c4e352bce87

=======
---
title: "Especificar os números IMEI | Microsoft Intune"
description: "O Microsoft Intune permite aos administradores importar números IMEI para plataformas de dispositivos móveis para ajudar a identificar os dispositivos móveis pertencentes à empresa"
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 656c93771776fd317f2b8d91bc59125fba1eb0b9
ms.openlocfilehash: 8b19cb740ed34b479fa8c4f5e2c1d13f13cda1f4

>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

---
<<<<<<< HEAD

# Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)
||||||| merged common ancestors

# Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)
=======

# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Especifique os dispositivos da empresa com os números de identidade internacional do equipamento móvel (IMEI)
>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2
O Microsoft Intune permite aos administradores importar números de identidade internacional do equipamento móvel (IMEI) para plataformas de dispositivos móveis com números IMEI para ajudar a identificar os dispositivos móveis pertencentes à empresa. Após a inscrição dos dispositivos no Intune, pode ver os dispositivos cujos números IMEI foram importados em **Grupos** > **Descrição Geral** > **Todos os Dispositivos**. O **Grupo de dispositivos** lista os dispositivos com números IMEI importados como **Empresa** na coluna **Propriedade**.

1. Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), selecione **Grupos**&gt; **Todos os Dispositivos** &gt; **Todos os Dispositivos Pertencentes à Empresa** &gt; **Por IMEI (Todas as plataformas)** e, em seguida, clique em **Adicionar dispositivos…**. Pode adicionar dispositivos de duas formas:

    -   **Carregar um ficheiro .csv que contenha números de série** – crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5 000 dispositivos ou 5 MB por ficheiro .csv.

        |||
        |-|-|
        |&lt;IMEI n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
        |&lt;IMEI n.º 2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|
        Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Adicionar manualmente os detalhes de dispositivos** – introduza o número IMEI e os detalhes de um máximo de 15 dispositivos.

   O campo *Detalhes* é para utilização administrativa. Pode especificar os detalhes para ajudar a identificar o dispositivo na lista de dispositivos pertencentes à empresa listados pelo ID de hardware. Estas informações não são enviadas para o dispositivo, mas irão aparecer na consola do Intune.

2.   Selecione **Seguinte**.
3.  No painel **Rever Dispositivos**, pode confirmar os números IMEI de dispositivos importados. Também pode decidir se quer substituir os **Detalhes** dos números IMEI que serão importados novamente. Pode desmarcar a caixa **Substituir** para manter os Detalhes atuais. Escolha **Concluir** para importar os números IMEI.
4.  Os números IMEI importados e as descrições são adicionadas à lista **Por IMEI (Todas as plataformas)**.

Quando um dispositivo com um número IMEI é inscrito no Intune, normalmente, quando um utilizador instalar a aplicação Portal da Empresa e concluir o processo de inscrição, o dispositivo será marcado como sendo de propriedade da empresa e será apresentado como inscrito no grupo **Dispositivos IMEI**.



<!--HONumber=Nov16_HO3-->


