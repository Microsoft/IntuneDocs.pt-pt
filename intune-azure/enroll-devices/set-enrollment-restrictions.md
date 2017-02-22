---
title: "Definir restrições de inscrição no Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: restringir a inscrição por plataforma e definir um limite de inscrição de dispositivos no Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pode limitar os tipos de dispositivos que têm permissão para se inscrever no Intune ao especificar as plataformas permitidas. Também pode definir o número máximo de dispositivos que um utilizador está autorizado a inscrever.

## <a name="set-device-type-restrictions"></a>Definir restrições de tipos de dispositivos

1. No portal do Azure, selecione **Mais Serviços**, introduza **Intune** na caixa de texto e, em seguida, selecione **Outros** > **Intune**

2. No painel Intune, selecione **Inscrever dispositivos** e, em seguida, selecione **Restrições de Inscrição**.

3. Em **Restrições de Tipos de Dispositivos**, selecione **Predefinição**.

4. No painel **Todos os Utilizadores**, selecione **Plataformas**.

5. Para as plataformas que têm permissão para se inscrever no Intune, selecione **Permitir**. Para as plataformas cuja inscrição quer bloquear, selecione **Bloquear**.

6. Selecione **Guardar**.

7. Selecione **Configurações de Plataformas**.

8. Opte por Permitir ou Bloquear a inscrição de dispositivos iOS pessoais.

9. Selecione **Guardar**.

## <a name="set-device-limit-restrictions"></a>Definir restrições de limite de dispositivos

1. No painel Intune do portal do Azure, selecione **Inscrever dispositivos** e, em seguida, selecione **Restrições de Inscrição**.

2. Em **Restrições de Limite de Dispositivos**, selecione **Predefinição**.

3. No painel **Todos os Utilizadores**, selecione **Limite de Dispositivos**.

4. Selecione o número máximo de dispositivos que um utilizador pode inscrever e, em seguida, selecione **Guardar**.



<!--HONumber=Feb17_HO1-->


