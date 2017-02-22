---
title: "Adicionar identificadores IMEI ao Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como adicionar identificadores empresariais (números IMEI) ao Microsoft Intune. "
keywords: 
author: staciebarker
ms.author: stabark
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: e134a6e3ff143dacce1d70ef0ab44ade0722ed57

---

# <a name="add-corporate-identifiers"></a>Adicionar identificadores empresariais

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pode criar uma lista de números de Identidade Internacional de Equipamento Móvel (IMEI) para identificar os seus dispositivos da empresa. Estes dispositivos podem ou não ser inscritos e têm um estado de “Inscrito” ou “Não contactado”. “Não contactado” significa que o dispositivo nunca faz o registo com o serviço do Intune.

Para criar a lista, crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione o identificador IMEI na coluna da esquerda e os detalhes na coluna da direita. O máximo atual para a lista é de 500 linhas.

Num editor de texto, a lista .csv tem um aspeto semelhante ao seguinte:

01 234567 890123,detalhes do dispositivo</br>
02 234567 890123,detalhes do dispositivo

**Para adicionar uma lista .csv de identificadores empresariais**

1. No portal do Azure, escolha **Mais Serviços**, introduza **Intune** na caixa de texto e, em seguida, escolha **Outros** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Identificadores de Dispositivo da Empresa**.

3. Se estiver a importar um ficheiro com novos detalhes que vão substituir os existentes, selecione **Substituir detalhes para os identificadores existentes** para que os novos detalhes substituam os detalhes existentes.

4. Navegue até ao ficheiro CSV do IMEI e selecione **Adicionar**.

**Para eliminar uma lista .csv de identificadores empresariais**

1. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Identificadores de Dispositivo da Empresa**.

2. Escolha **Eliminar**.



<!--HONumber=Feb17_HO1-->


