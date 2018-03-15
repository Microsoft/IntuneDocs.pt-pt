---
title: "Ver o inventário de dispositivos do Intune"
titlesuffix: Azure portal
description: "Saiba como ver os dispositivos que gere com o Intune e compreender o respetivo hardware e aplicações instaladas.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772e2b1380626384d618e653b90b31a1f421eb72
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-view-intune-device-inventory"></a>Como ver o inventário de dispositivos do Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A carga de trabalho **Dispositivos** fornece informações sobre os dispositivos que gere, incluindo as respetivas capacidades de hardware, e as aplicações instaladas nos mesmos. 

Para ver o inventário de dispositivos:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, escolha **Dispositivos**.

Agora, selecione uma das seguintes opções:

- **Descrição geral** – obtenha informações sobre os dispositivos que inscreveu e os sistemas operativos executados em cada dispositivo.
- **Gerir** – selecione **Todos os dispositivos** para ver uma lista de todos os dispositivos que gere.
    Selecione um desses dispositivos na lista para abrir o painel <*nome do dispositivo*> **Descrição Geral**, onde pode selecionar uma das opções:
    - **Descrição Geral** – veja as informações gerais do dispositivo, incluindo o respetivo nome, o proprietário, se é um dispositivo BYOD, quando foi efetuado o registo e mais.
    - **Hardware** – veja informações mais detalhadas sobre o dispositivo, incluindo o espaço de armazenamento livre, o modelo e fabricante e mais.
    - **Aplicações detetadas** – apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo.
    - **Conformidade do dispositivo** – apresenta o estado de conformidade de todas as políticas de conformidade que foram atribuídas ao dispositivo.
    - **Configuração do dispositivo** – apresenta o estado de conformidade de todas as políticas de configuração do dispositivo que foram atribuídas ao mesmo.
- **Monitorizar** – selecione **Ações do dispositivo** para ver uma lista das ações do dispositivo que foram realizadas nos dispositivos que gere e o estado atual dos mesmos.
- **Configuração** > **Conector do TeamViewer** – permite-lhe configurar a administração remota em dispositivos que utilizam o software TeamViewer. Para obter detalhes, veja [Fornecer assistência remota para dispositivos Android geridos pelo Intune](/intune/device-profile-android-teamviewer).

O Intune recolhe o inventário de aplicações apenas nos dispositivos pertencentes à empresa. As aplicações não são inventariadas em dispositivos pessoais. Para PCs com o Windows 10, apenas é recolhido o inventário de aplicações modernas em dispositivos pertencentes à empresa. O Intune não recolhe informações de aplicações Win32 no dispositivo. Consoante a operadora que utilizar nos dispositivos, alguns itens de inventário poderão não ser recolhidos.
