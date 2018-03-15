---
title: Bloquear remotamente dispositivos geridos com o Intune
titlesuffix: Azure portal
description: Saiba como utilizar o Intune para bloquear remotamente dispositivos que gere."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a8f3c93507cde4363570a9a39f8b3b1f69c07df
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloquear remotamente dispositivos geridos com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O **Bloqueio remoto** bloqueia o dispositivo selecionado. O proprietário do dispositivo tem de utilizar o código de acesso para desbloqueá-lo. Só pode bloquear remotamente um dispositivo que tenha um PIN ou uma palavra-passe definida.

## <a name="supported-platforms"></a>Plataformas suportadas

O bloqueio remoto é suportado pelas seguintes plataformas:

|Plataforma|Estado do suporte|
|---|---|
|Android|Sim|
|iOS|Sim|
|macOS|Sim|
|Computadores com o Windows 10|Não|
|Windows 10 Mobile|Sim|
|Windows Phone|Sim, para Windows Phone 8.1 e posterior|

> [!NOTE]  
> Para dispositivos macOS, defina um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivo** apresenta o PIN até que seja enviada outra ação de dispositivo.

## <a name="how-to-remote-lock-a-device"></a>Como bloquear remotamente um dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Bloqueio remoto**.

## <a name="next-steps"></a>Passos seguintes

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos**, selecione **Ações do dispositivo**.
