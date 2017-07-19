---
title: Gerir dispositivos com o Intune
titleSuffix: Intune on Azure
description: "Saiba como ver os dispositivos que gere com o Intune e como desempenhar várias operações neles.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A carga de trabalho **Dispositivos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos. Para aceder à carga de trabalho:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.

Agora, pode efetuar as seguintes ações:

- [Ver o inventário de dispositivos](device-inventory.md)
- Execute as ações remotas de dispositivos:
    - [Remover dados da empresa](device-company-data-remove.md) 
    - [Reposição de fábrica](device-factory-reset.md)
    - [Bloqueio remoto](device-remote-lock.md)
    - [Repor código de acesso](device-passcode-reset.md)
    - [Ignorar Bloqueio de Ativação](device-activation-lock-bypass.md)
    - [Fresh Start](device-fresh-start.md)
    - [Modo perdido](device-lost-mode.md)
    - [Localizar dispositivo](device-locate.md)
    - [Reiniciar](device-restart.md)
    - [Reposição do PIN do Windows 10](device-windows-pin-reset.md)
    - [Controlo remoto do Android](device-profile-android-teamviewer.md)


## <a name="support-for-each-device-action"></a>Suporte para cada ação do dispositivo

Utilize a seguinte tabela para compreender as plataformas de dispositivos que são suportadas por cada ação.

|||||||
|-|-|-|-|-|-|
|Ação do dispositivo|Windows|Windows Phone|iOS|macOS|Android|
|**Remover dados da empresa**|Sim|Sim|Sim|Sim|Sim|
|**Reposição de fábrica**|Windows 8.1 e posterior (dispositivos não geridos pelo EAS)|Sim|Sim|Não|O Android for Work não é suportado|
|**Eliminar**|Sim|Sim|Sim|Sim|Sim|
|**Bloqueio remoto**|Não|Windows Phone 8.1 e posterior|Sim|Não|Sim|
|**Repor código de acesso**|Não|Windows Phone 8.1 à Atualização para Criativos do Windows 10 não associada ao Azure AD. Atualização para Criativos do Windows 10 e posterior – todos|Sim|Não|Anterior ao Android 7. O Android for Work não é suportado|
|**Novo código de acesso** (para dispositivos Windows 10)|Não|Atualização para Criadores do Windows 10 e posterior (associada ao Azure AD)|Não|Não|O Android for Work não é suportado|
|**Ignorar Bloqueio de Ativação**|Não|Não|Apenas dispositivos da empresa|Não|Não|
|**Modo perdido**|Não|Não|Dispositivos iOS 9.3 e posterior, supervisionados e pertencentes à empresa|Não|Não|
|**Localizar dispositivo**|Não|Não|iOS 9.3 e posterior em modo perdido, supervisionado e pertencente à empresa|Não|Não|
|**Terminar a sessão do utilizador atual**|Não|Não|iOS 9.3 e posterior (apenas dispositivos iPad partilhados)|Não|Não|
|**Reiniciar**|Windows 8.1 e posterior|Windows Phone 8.1 e posterior|Não|Não|Não|
|**Fresh Start**|Atualização para Criativos do Windows 10 e posterior|Não|Não|Não|Não|
|**Nova sessão de Assistência Remota**|Não|Não|Não|Não|Sim|
|**Remover utilizador**|Não|Não|iOS 9.3 e posterior (apenas dispositivos iPad partilhados)|Não|Não|

## <a name="next-steps"></a>Passos seguintes

- Selecione **Ações do Dispositivo** para ver o estado das ações efetuadas nos dispositivos que gere. 
![Monitorizar ações de dispositivos](./media/monitor-device-actions.png)