---
title: "Repor um código de acesso de dispositivo com o Intune"
titlesuffix: Azure portal
description: "Saiba como repor um código de acesso em dispositivos que gere com o Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0446db40b829e92b681294ecc497a2c475480fac
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>Repor o código de acesso em dispositivos geridos pelo Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação **Remover código de acesso** gera um novo código de acesso para o dispositivo, que é apresentado no painel **Descrição Geral** do <*nome do dispositivo*> .

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – suportado no Windows Phone 8.1 para a Atualização para Criativos do Windows 10 não associada ao Azure AD. Atualização para Criativos do Windows 10 e posterior
- iOS – suportado
- macOS – não suportado
- Android – suportado em versões do Android anteriores ao Android 7. O Android for Work não é suportado.

## <a name="how-to-reset-a-passcode"></a>Como repor um código de acesso

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione um dispositivo e, em seguida, selecione a ação remota de dispositivos **Remover código de acesso**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
