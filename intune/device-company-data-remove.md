---
title: Remover dados da empresa de dispositivos com o Intune
titleSuffix: Intune on Azure
description: Saiba como remover apenas os dados da empresa de dispositivos que gere com o Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Remover dados da empresa de dispositivos geridos com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A opção **Remover dados da empresa** remove apenas os dados da empresa de dispositivos geridos pelo Intune. Não remove os dados pessoais do dispositivo. O dispositivo deixará de ser gerido pelo Intune e já não poderá aceder aos recursos da empresa (não suportado para dispositivos Windows que estejam associados ao Azure Active Directory).

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Remover dados da empresa**.

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
