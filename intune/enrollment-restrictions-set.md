---
title: "Definir restrições de inscrição no Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: restringir a inscrição por plataforma e definir um limite de inscrição de dispositivos no Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d99f7ca5b5e96a7ab113a14d36f0fef474411836
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="set-enrollment-restrictions"></a>Definir restrições de inscrição 

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Pode definir os tipos e o número máximo de dispositivos cuja inscrição pretende permitir. No painel Restrições de Inscrição, pode definir:

- As plataformas que é permitido inscrever e se quer bloquear a inscrição de dispositivos Android e iOS pessoais.

- O número máximo de dispositivos que um utilizador tem permissão para inscrever.

## <a name="set-device-type-restrictions"></a>Definir restrições de tipos de dispositivos

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, selecione **Inscrever dispositivos** e, em seguida, selecione **Restrições de Inscrição**.

3. Em **Restrições de Tipos de Dispositivos**, selecione **Predefinição**.

4. No painel **Todos os Utilizadores**, selecione **Plataformas**.

5. Para as plataformas que têm permissão para se inscrever no Intune, selecione **Permitir**. Para as plataformas cuja inscrição quer bloquear, selecione **Bloquear**. Por predefinição, as plataformas estão definidas com a opção **Permitir**. 

    >[!NOTE]
    >Estas definições não se aplicam nem bloqueiam inscrições de dispositivos Windows que utilizam o software de cliente do Intune. Estas definições afetam apenas as inscrições feitas através da gestão de dispositivos móveis. 

6. Selecione **Guardar**.

7. Selecione **Configurações de Plataformas**.

8. Opte por **Permitir** ou **Bloquear** a inscrição de dispositivos iOS e Android pessoais.

9. Selecione **Guardar**.

## <a name="set-device-limit-restrictions"></a>Definir restrições de limite de dispositivos

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, selecione **Inscrever dispositivos** e, em seguida, selecione **Restrições de Inscrição**.

3. Em **Restrições de Limite de Dispositivos**, selecione **Predefinição**.

4. No painel **Todos os Utilizadores**, selecione **Limite de Dispositivos**.

5. Selecione o número máximo de dispositivos que um utilizador pode inscrever e, em seguida, selecione **Guardar**.

