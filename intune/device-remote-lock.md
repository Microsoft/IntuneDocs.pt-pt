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
ms.openlocfilehash: ecd7fa03b35e91b5a77906858fb251348796704d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloquear remotamente dispositivos geridos com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O **Bloqueio remoto** bloqueia o dispositivo selecionado. O proprietário do dispositivo tem de utilizar o código de acesso para desbloqueá-lo. Só pode bloquear remotamente um dispositivo que tenha um PIN ou uma palavra-passe definida.

## <a name="supported-platforms"></a>Plataformas suportadas

O bloqueio remoto é suportado pelas seguintes plataformas:

|Platform|Estado do suporte|
|---|---|
|Android|Sim|
|iOS|Sim|
|macOS|Sim|
|Windows 10|Sim|
|Windows 10 Mobile|Sim|
|Windows Phone|Sim, para Windows Phone 8.1 e posterior|

> [!NOTE]  
> Para dispositivos macOS, defina um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

## <a name="how-to-remote-lock-a-device"></a>Como bloquear remotamente um dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Bloqueio remoto**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
