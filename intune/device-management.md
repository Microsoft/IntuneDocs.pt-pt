---
title: Gerir dispositivos com o Intune
titleSuffix: Intune on Azure
description: "Saiba como ver os dispositivos que gere com o Intune e como desempenhar várias operações neles.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 08/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b034e144aa43d239874b484acb2a40be12aff7c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de TI, tem de garantir que os dispositivos geridos estão a disponibilizar os recursos de que os seus utilizadores finais precisam para trabalhar a proteger os dados contra riscos.

A carga de trabalho **Dispositivos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos. Para aceder à carga de trabalho:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No **Intune**, selecione **Dispositivos**.
4. Pode ver informações sobre os dispositivos e executar as ações remotas de dispositivos da seguinte forma:
    - **Descrição geral** – um resumo dos dispositivos inscritos que pode gerir.
    - **Todos os dispositivos** – uma lista dos dispositivos inscritos que gere. Selecione **Filtro** ou **Colunas** para refinar as informações apresentadas. Selecione um dispositivo para [ver o inventário de dispositivos](device-inventory.md).
    - **Dispositivos do Azure AD** – uma lista dos dispositivos registados ou associados ao Azure Active Directory (AD). Saiba mais sobre a [gestão de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Ações do dispositivo** – um histórico das ações remotas realizadas em dispositivos, incluindo a ação, o respetivo estado, quem a iniciou e quando.

    ![Monitorizar ações de dispositivos](./media/monitor-device-actions.png)

    - **TeamViewer** – o serviço TeamViewer permite aos utilizadores de dispositivos Android geridos pelo Intune obter assistência remota por parte do administrador de TI. Saiba mais sobre o [TeamViewer](device-profile-android-teamviewer.md).

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
