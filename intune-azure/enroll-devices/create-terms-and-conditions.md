---
title: "Definir termos e condições no Microsoft Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: defina os termos e condições que os utilizadores veem no Portal da Empresa do Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: f7d6ebc9d71a077492ab615a3bc5397e092b1deb
ms.lasthandoff: 02/15/2017

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

