---
title: Gerir dispositivos com o Intune
titlesuffix: Azure portal
description: "Saiba como ver os dispositivos que gere com o Intune e como desempenhar várias operações neles.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca40eee8a53fa3e8b2610ce414f0037180d4beaf
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A carga de trabalho **Dispositivos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos. Para aceder à carga de trabalho:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. Pode ver informações sobre os dispositivos e executar as ações remotas de dispositivos listadas.

## <a name="available-device-actions"></a>Ações do dispositivo disponíveis
As ações disponíveis dependem da plataforma do dispositivo e da configuração do dispositivo.

- [Ver o inventário de dispositivos](device-inventory.md)
- Execute as ações remotas de dispositivos:
    - [Remover dados da empresa](devices-wipe.md#remove-company-data)
    - [Reposição de fábrica](devices-wipe.md#factory-reset)
    - [Bloqueio remoto](device-remote-lock.md)
    - [Repor código de acesso](device-passcode-reset.md)
    - [Ignorar Bloqueio de Ativação](device-activation-lock-bypass.md) (apenas em iOS)
    - [Começar do Zero](device-fresh-start.md) (apenas no Windows)
    - [Modo perdido](device-lost-mode.md) (apenas em iOS)
    - [Localizar dispositivo](device-locate.md) (apenas em iOS)
    - [Reiniciar](device-restart.md) (apenas no Windows)
    - [Reposição do PIN do Windows 10](device-windows-pin-reset.md)
    - [Controlo remoto do Android](device-profile-android-teamviewer.md)
    - [Sincronizar o dispositivo](device-sync.md)


## <a name="next-steps"></a>Próximos passos

- Selecione **Ações do Dispositivo** para ver o estado das ações efetuadas nos dispositivos que gere.
![Monitorizar ações de dispositivos](./media/monitor-device-actions.png)
