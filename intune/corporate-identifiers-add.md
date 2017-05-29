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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 25414cd42159d1c3e09b80d236ccb12f0df5662a
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="add-corporate-identifiers"></a>Adicionar identificadores empresariais

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Como administrador de TI, pode criar e importar um ficheiro de valores separados por vírgulas (.csv) que liste os números de Identidade Internacional do Equipamento Móvel (IMEI) para identificar os dispositivos da empresa. Cada número IMEI pode ter detalhes especificados na lista para fins administrativos.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

## <a name="add-corporate-identifiers"></a>Adicionar identificadores empresariais
Para criar a lista, crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione o identificador IMEI na coluna da esquerda e os detalhes na coluna da direita. Os detalhes estão limitados a 128 carateres e destinam-se apenas a utilização administrativa. Os detalhes não são apresentados no dispositivo. O limite atual é de 500 linhas por ficheiro .csv.

**Carregar um ficheiro .csv que contenha números de série** – crie uma lista de valores separados por vírgulas (.csv) de duas colunas sem cabeçalho, limitada até 5 000 dispositivos ou 5 MB por ficheiro .csv. 

|||
|-|-|
|&lt;IMEI n.º 1&gt;|&lt;Detalhes do Dispositivo n.º 1&gt;|
|&lt;IMEI n.º 2&gt;|&lt;Detalhes do Dispositivo n.º 2&gt;|

Se visualizar este ficheiro .csv num editor de texto, este é apresentado como:

```
01234567890123,device details
02234567890123,device details
```


> [!IMPORTANT]
> Alguns dispositivos Android têm múltiplos números IMEI. O Intune fará o inventário de um número IMEI por dispositivo. Se importar um número IMEI inventariado pelo Intune, o dispositivo será classificado como um dispositivo pessoal em vez de um dispositivo da empresa. Se importar múltiplos números IMEI de um dispositivo, os números não inventariados irão apresentar o estado de inscrição **Desconhecido**.

**Para adicionar uma lista .csv de identificadores empresariais**

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel do Intune, selecione **Inscrição de dispositivos** > **Restrições de Inscrição**, **Identificadores de Dispositivo da Empresa** e, em seguida, clique em **Adicionar**.

3. No painel **Adicionar Identificadores**, especifique o tipo de identificador, **IMEI**. Pode especificar se os números importados anteriormente devem **Substituir os detalhes por identificadores existentes**.  

4. Clique no ícone de pasta e especifique o caminho para a lista que pretende importar. Navegue até ao ficheiro CSV do IMEI e selecione **Adicionar**.

Depois de importados, estes dispositivos podem ou não ser inscritos e podem ter um estado de **Inscrito** ou **Não contactado**. **Não contactado** significa que o dispositivo nunca comunicou com o serviço do Intune.

## <a name="delete--corporate-identifiers"></a>Eliminar identificadores empresariais

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel do Intune, selecione **Inscrição de dispositivos** > **Restrições de Inscrição**, **Identificadores de Dispositivo da Empresa** e, em seguida, selecione **Eliminar**.

3. No painel **Eliminar Identificadores**, navegue para o ficheiro .csv com os IDs de dispositivo a eliminar e, em seguida, clique em **Eliminar**.

## <a name="imei-specifications"></a>Especificações do IMEI
Para obter especificações detalhadas sobre os Identificadores Internacionais do Equipamento Móvel, veja [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

