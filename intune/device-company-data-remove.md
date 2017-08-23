---
title: Remover dados da empresa de dispositivos com o Intune
titleSuffix: Intune on Azure
description: Saiba como remover apenas os dados da empresa de dispositivos que gere com o Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b0cc7d62770057ff9df5a36e6e5df58b29430534
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/09/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Remover dados da empresa de dispositivos geridos com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação do dispositivo **Remover dados da empresa** remove apenas os dados da empresa de dispositivos geridos pelo Intune. Esta ação não remove os dados pessoais do dispositivo. Após a remoção, o dispositivo já não será gerido pelo Intune e deixa de poder aceder a recursos empresariais.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – suportado (não suportado em dispositivos Windows associados ao Azure Active Directory)
- Windows Phone – suportado
- iOS – suportado
- macOS – suportado
- Android – suportado

## <a name="how-to-remove-company-data"></a>Como remover dados da empresa

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Remover dados da empresa**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
