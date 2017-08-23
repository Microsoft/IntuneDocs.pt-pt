---
title: Gerir dispositivos com o Intune
titleSuffix: Intune on Azure
description: "Saiba como ver os dispositivos que gere com o Intune e como desempenhar várias operações neles.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A carga de trabalho **Dispositivos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos. Para aceder à carga de trabalho:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. Agora pode efetuar as ações do dispositivo remoto listadas. As ações disponíveis dependem da plataforma do dispositivo e da configuração do dispositivo:

## <a name="available-device-actions"></a>Ações do dispositivo disponíveis

- [Ver o inventário de dispositivos](device-inventory.md)
- Execute as ações remotas de dispositivos:
    - [Remover dados da empresa](device-company-data-remove.md) 
    - [Reposição de fábrica](device-factory-reset.md)
    - [Bloqueio remoto](device-remote-lock.md)
    - [Repor código de acesso](device-passcode-reset.md)
    - [Ignorar Bloqueio de Ativação](device-activation-lock-bypass.md)
    - [Começar do Zero](device-fresh-start.md)
    - [Modo perdido](device-lost-mode.md)
    - [Localizar dispositivo](device-locate.md)
    - [Reiniciar](device-restart.md)
    - [Reposição do PIN do Windows 10](device-windows-pin-reset.md)
    - [Controlo remoto do Android](device-profile-android-teamviewer.md)
    - [Sincronizar o dispositivo](device-sync.md)


## <a name="next-steps"></a>Próximos passos

- Selecione **Ações do Dispositivo** para ver o estado das ações efetuadas nos dispositivos que gere. 
![Monitorizar ações de dispositivos](./media/monitor-device-actions.png)
