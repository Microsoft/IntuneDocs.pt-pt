---
title: "Repor dispositivos Windows 10 com o Intune"
titleSuffix: Intune on Azure
description: "Saiba como utilizar o Fresh Start para repor PCs Windows 10 que executam o Intune.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 590472c0ab9f0103d72730b8ab01dc324c852a7a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utilizar o Fresh Start para repor dispositivos Windows 10 com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivos **Fresh Start** remove todas as aplicações que foram instaladas nos PCs a executar a Atualização para Criativos do Windows 10 e, em seguida, atualiza automaticamente os PCs para a versão mais recente do Windows.
Esta ação pode ajudar a remover aplicações (OEM) que vêm frequentemente pré-instaladas em PCs novos. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação. Neste caso, as aplicações e as definições são removidas, mas o conteúdo da pasta Raiz dos utilizadores é mantido.

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo com o ambiente de trabalho Windows 10 e, em seguida, escolha a ação remota de dispositivos **Fresh Start**.

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.

