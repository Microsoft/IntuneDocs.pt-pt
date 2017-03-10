---
title: Gerir dispositivos com o Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como ver os dispositivos que gere com o Intune e desempenhar várias operações nos mesmos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d5d7b87f58604b93ba3b65d5d264a0a5e3743d45
ms.lasthandoff: 02/18/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune? 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A carga de trabalho **Dispositivos e grupos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos. Para aceder à carga de trabalho:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos e Grupos**.

    ![Carga de trabalho Dispositivos e grupos](./media/devices-and-groups-workload.png)

Agora, escolha uma das seguintes opções:

- **Descrição geral** – Obtenha informações sobre os dispositivos que inscreveu e os sistemas operativos executados em cada dispositivo.
- **Gerir** – Escolha **Todos os Dispositivos** para ver uma lista de todos os dispositivos que gere.
    Selecione um desses dispositivos na lista para abrir o painel <*nome do dispositivo*> **Descrição Geral**, onde pode selecionar uma das opções:
    - **Descrição Geral** – Veja as informações gerais do dispositivo, incluindo informações sobre o nome, o proprietário, se é um dispositivo BYOD, quando foi registado pela última vez e muito mais. Além disso, pode realizar as seguintes ações remotas no dispositivo (nem todas as ações são suportadas por todas as plataformas de dispositivos):
        - **Remover dados da empresa** – Remove apenas os dados da empresa geridos pelo Intune. Não remove os dados pessoais do dispositivo. O dispositivo deixará de ser gerido pelo Intune e já não poderá aceder aos recursos da empresa (não suportado para dispositivos Windows que estejam associados ao Azure Active Directory).
        - **Reposição de fábrica** – Repõe as predefinições do dispositivo. O dispositivo deixará de ser gerido pelo Intune e os dados pessoais e da empresa são removidos. Não pode anular esta ação.
        - **Bloqueio remoto** – Bloqueia o dispositivo. O proprietário do dispositivo tem de utilizar o código de acesso para desbloqueá-lo. Só pode bloquear remotamente um dispositivo que tenha um PIN ou uma palavra-passe definida.
        - **Repor código de acesso** – Gera um novo código de acesso para o dispositivo, que será apresentado no painel <*nome do dispositivo*> **Descrição Geral**.
        - **Ignorar Bloqueio de Ativação** – Esta opção removerá o bloqueio de ativação de um dispositivo iOS sem o Apple ID e a palavra-passe do utilizador. Depois de ignorar o bloqueio de ativação, o dispositivo ativa novamente o bloqueio de ativação quando a aplicação Encontrar o Meu iPhone é iniciada. Ignore o bloqueio de ativação apenas se tiver acesso físico ao dispositivo.
        - **Modo perdido** – Se um dispositivo tiver sido roubado, poderá ativar o modo perdido. Esta opção permite-lhe especificar uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo.
        - **Reiniciar** – Faz com que o dispositivo seja reiniciado. O proprietário do dispositivo não é automaticamente notificado relativamente ao reinício, por isso, poderá perder trabalho.
        ![Descrição geral do dispositivo](http://i.imgur.com/4Rx4VXm.png)
        
    - **Hardware** – Veja informações mais detalhadas sobre o dispositivo, incluindo o espaço de armazenamento livre, o modelo e fabricante, entre outros.
    ![Inventário do hardware do dispositivo gerido](./media/hardware-inventory.png)
    - **Aplicações Detetadas** – Apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo.
    ![Nó de aplicações detetadas](./media/detected-applications.png)
- **Monitorizar** – Escolha **Ações do Dispositivo** para ver uma lista das ações do dispositivo que foram realizadas nos dispositivos que gere e o estado atual dessas ações.
![Monitorizar ações de dispositivos](./media/monitor-device-actions.png)

