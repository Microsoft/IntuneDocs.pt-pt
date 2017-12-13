---
title: Bloquear remotamente dispositivos geridos com o Intune
titlesuffix: Azure portal
description: Saiba como utilizar o Intune para bloquear remotamente dispositivos que gere."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8905b97a5912010a2516788a8da66441fc6f89ae
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloquear remotamente dispositivos geridos com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O **Bloqueio remoto** bloqueia o dispositivo selecionado. O proprietário do dispositivo tem de utilizar o código de acesso para desbloqueá-lo. Só pode bloquear remotamente um dispositivo que tenha um PIN ou uma palavra-passe definida.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – suportado no Windows Phone 8.1 e posterior
- iOS – suportado
- macOS – suportado

    > [!Note]  
    > Defina um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral dos dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.
- Android – suportado

## <a name="how-to-remote-lock-a-device"></a>Como bloquear remotamente um dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota de dispositivos **Bloqueio remoto**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
