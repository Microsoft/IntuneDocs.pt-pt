---
title: "Ver o inventário de dispositivos do Intune"
titleSuffix: Intune on Azure
description: "Saiba como ver os dispositivos que gere com o Intune e compreender o respetivo hardware e aplicações instaladas.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3618c5ee0b4a7ff0e7b6a4d6ed58f77a2af0ba66
ms.sourcegitcommit: fb17b59f4aa2b994b149fcc6d32520f74b0de6a5
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/12/2017
---
# <a name="how-to-view-intune-device-inventory"></a>Como ver o inventário de dispositivos do Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A carga de trabalho **Dispositivos** fornece informações sobre os dispositivos que gere, incluindo as respetivas capacidades de hardware, e as aplicações instaladas nos mesmos. 

Para ver o inventário de dispositivos:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.

Agora, selecione uma das seguintes opções:

- **Descrição geral** – Obtenha informações sobre os dispositivos que inscreveu e os sistemas operativos executados em cada dispositivo.
- **Gerir** – Escolha **Todos os Dispositivos** para ver uma lista de todos os dispositivos que gere.
    Selecione um desses dispositivos na lista para abrir o painel <*nome do dispositivo*> **Descrição Geral**, onde pode selecionar uma das opções:
    - **Descrição Geral** – veja as informações gerais do dispositivo, incluindo o respetivo nome, o proprietário, se é um dispositivo BYOD, quando foi efetuado o registo e mais.
    ![Descrição geral do dispositivo](./media/device-overview.png)
    - **Hardware** – veja informações mais detalhadas sobre o dispositivo, incluindo o espaço de armazenamento livre, o modelo e fabricante e mais.
    ![Inventário do hardware do dispositivo gerido](./media/hardware-inventory.png)
    - **Aplicações detetadas** – apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo.
    ![Nó das aplicações detetadas](./media/detected-applications.png)
    


    - **Conformidade do dispositivo** – apresenta o estado de conformidade de todas as políticas de conformidade que foram atribuídas ao dispositivo.
    - **Configuração do dispositivo** – apresenta o estado de conformidade de todas as políticas de configuração do dispositivo que foram atribuídas ao mesmo.
- **Monitorizar** – selecione **Ações do Dispositivo** para ver uma lista das ações do dispositivo que foram realizadas nos dispositivos que gere e o estado atual dos mesmos.
- **Configuração** > **Conector do TeamViewer** – permite-lhe configurar a administração remota em dispositivos que utilizam o software TeamViewer. Para obter detalhes, veja [Fornecer assistência remota para dispositivos Android geridos pelo Intune](/intune/device-profile-android-teamviewer).

>[!NOTE]
> O Intune recolhe o inventário de aplicações apenas nos dispositivos pertencentes à empresa. As aplicações não são inventariadas em dispositivos pessoais. Para PCs com o Windows 10, apenas é recolhido o inventário de aplicações modernas em dispositivos pertencentes à empresa. O Intune não recolhe informações de aplicações Win32 no dispositivo.
