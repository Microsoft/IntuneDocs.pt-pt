---
title: "Repor dispositivos Windows 10 com o Intune"
titlesuffix: Azure portal
description: "Saiba como utilizar a funcionalidade Começar do Zero para repor PCs Windows 10 que executam o Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c45d3e47c90ca7739b3aa6eee1bf31d787a82264
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utilizar a funcionalidade Começar do Zero para repor dispositivos Windows 10 com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Começar do Zero** remove todas as aplicações que foram instaladas nos PCs a executar a Atualização para Criativos do Windows 10 e, em seguida, atualiza automaticamente os PCs para a versão mais recente do Windows.
Esta ação pode ajudar a remover aplicações (OEM) que vêm frequentemente pré-instaladas num PC novo. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação. Neste caso, as aplicações e as definições são removidas, mas o conteúdo da pasta Raiz dos utilizadores é mantido.

## <a name="how-to-use-fresh-start"></a>Como utilizar a funcionalidade Começar do Zero

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo com o ambiente de trabalho Windows 10 e, em seguida, escolha a ação remota de dispositivos **Começar do Zero**.

## <a name="next-steps"></a>Passos seguintes

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos**, selecione **Ações do dispositivo**.

