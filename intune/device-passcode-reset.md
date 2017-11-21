---
title: "Repor e remover códigos de acesso de dispositivo com o Intune"
titlesuffix: Azure portal
description: "Saiba como repor e remover o código de acesso nos dispositivos que gere com o Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dfa94d11f978bbe4d23b6672423c849e1f061986
ms.sourcegitcommit: 474a24ba67f6bf4f00268bf9e4eba52331a6b82d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2017
---
# <a name="reset-and-remove-the-passcode-on-intune-managed-devices"></a>Repor e remover o código de acesso nos dispositivos geridos pelo Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Os termos *remover* e *repor* são utilizados alternadamente neste artigo.

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
