---
title: Adicionar identificadores IMEI ao Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como adicionar identificadores empresariais (números IMEI) ao Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: e0a853c34c6d38e8fae6f4712ba6c2b767e5d0ba
ms.lasthandoff: 03/22/2017

---

# <a name="add-corporate-identifiers"></a>Adicionar identificadores empresariais

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador de TI, pode criar e importar um ficheiro de valores separados por vírgulas (.csv) que liste os números de Identidade Internacional do Equipamento Móvel (IMEI) para identificar os dispositivos da empresa. Cada número IMEI pode ter detalhes especificados na lista para fins administrativos.

## <a name="create-a-csv-file"></a>Criar um ficheiro .csv
Para criar a lista, crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione o identificador IMEI na coluna da esquerda e os detalhes na coluna da direita. Os detalhes estão limitados a 128 carateres. O limite atual é de 500 linhas por ficheiro .csv.

**Carregar um ficheiro .csv que contenha números de série** – crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5 000 dispositivos ou 5 MB por ficheiro .csv.

|||
|-|-|
|&lt;IMEI n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
|&lt;IMEI n.º 2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**Para adicionar uma lista .csv de identificadores empresariais**

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Identificadores de Dispositivo da Empresa**.

3. Se estiver a importar um ficheiro com novos detalhes que vão substituir os existentes, selecione **Substituir detalhes para os identificadores existentes** para que os novos detalhes substituam os detalhes existentes.

4. Navegue até ao ficheiro CSV do IMEI e selecione **Adicionar**.

> [!IMPORTANT]
> Alguns dispositivos Android têm múltiplos números IMEI. O Intune fará o inventário de um número IMEI por dispositivo. Se importar um número IMEI inventariado pelo Intune, o dispositivo será classificado como um dispositivo pessoal em vez de um dispositivo da empresa. Se importar múltiplos números IMEI de um dispositivo, os números não inventariados irão apresentar o estado de inscrição **Desconhecido**.

Depois de importados, estes dispositivos podem ou não ser inscritos e podem ter um estado de **Inscrito** ou **Não contactado**. **Não contactado** significa que o dispositivo nunca comunicou com o serviço do Intune.

## <a name="delete-a-csv-list"></a>Eliminar uma lista .csv

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Identificadores de Dispositivo da Empresa**.

3. Escolha **Eliminar**.

Para obter especificações detalhadas sobre os Identificadores Internacionais do Equipamento Móvel, veja [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

