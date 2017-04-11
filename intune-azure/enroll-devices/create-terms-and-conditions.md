---
title: "Definir termos e condições no Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: defina os termos e condições que os utilizadores veem no Portal da Empresa do Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 07a42cf8fa10d3223129fbb2932217ff90ac365b
ms.lasthandoff: 02/18/2017

---

# <a name="set-terms-and-conditions"></a>Definir termos e condições 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pode implementar termos e condições do Intune para grupos de utilizadores para explicar como a inscrição, o acesso a recursos de trabalho e a aplicação Portal da Empresa afetam os dispositivos e os utilizadores. Os utilizadores têm de aceitar os termos e condições antes de poderem utilizar o Portal da Empresa para inscrever e aceder ao seu trabalho.

Pode criar e implementar diversas políticas que contêm diferentes termos e condições. Pode também produzir versões dos mesmos termos e condições em idiomas diferentes e, em seguida, implementá-los nos grupos adequados.

**Para criar termos e condições**:

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Termos e Condições**.

3. Selecione **Criar**.

4. No painel **Criar Termos e Condições**, especifique as seguintes informações:

   - **Nome a apresentar**: nome a utilizar para os termos. Os utilizadores veem este nome na aplicação do Portal da Empresa.

   - **Descrição**: detalhes opcionais que o ajudam a identificar a política no portal do Azure.

5. Selecione a seta junto a Definir termos de utilização para a abrir o painel Termos e Condições e, em seguida, introduza as seguintes informações:

   - **Título**: o título que os utilizadores veem no Portal da Empresa.

   - **Resumo dos Termos**: texto que explica o que significa se os utilizadores aceitarem os termos.

   - **Termos e Condições**: a etiqueta legal que os utilizadores veem e devem aceitar ou rejeitar. Por exemplo, “Concordo com os termos e condições”.

6. Selecione **OK**.

