---
title: "Repor dispositivos Windows 10 com o Intune"
titlesuffix: Azure portal
description: "Saiba como utilizar a funcionalidade Começar do Zero para repor PCs Windows 10 que executam o Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 181818bf40e569d0354ee5bd661169c529cb3d07
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/12/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utilizar a funcionalidade Começar do Zero para repor dispositivos Windows 10 com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Começar do Zero** remove todas as aplicações que foram instaladas nos PCs a executar a Atualização para Criativos do Windows 10 e, em seguida, atualiza automaticamente os PCs para a versão mais recente do Windows.
Esta ação pode ajudar a remover aplicações (OEM) que vêm frequentemente pré-instaladas em PCs novos. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação. Neste caso, as aplicações e as definições são removidas, mas o conteúdo da pasta Raiz dos utilizadores é mantido.

## <a name="how-to-use-fresh-start"></a>Como utilizar a funcionalidade Começar do Zero

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo com o ambiente de trabalho Windows 10 e, em seguida, escolha a ação remota de dispositivos **Começar do Zero**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.

