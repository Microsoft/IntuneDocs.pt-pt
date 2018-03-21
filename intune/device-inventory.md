---
title: "Ver os seus dispositivos com o Microsoft Intune – Azure | Microsoft Docs"
description: "Veja os detalhes do seu dispositivo, incluindo sistemas operativos, espaço de armazenamento, fabrico e modelo e mais. Obtenha uma lista de aplicações instaladas, verifique as políticas de conformidade, configure o TeamViewer e mais com o Microsoft Intune no Azure. Semelhante a ver o inventário dos dispositivos que gere."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 934ba0853f8bee851f7027580c276a9fff911b7f
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="see-device-details-in-intune"></a>Consultar os detalhes do dispositivo no Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A funcionalidade **Dispositivos** fornece detalhes adicionais para os dispositivos que gere, incluindo o respetivo hardware e as aplicações instaladas. 

Este artigo mostra como ver todos os seus dispositivos e as respetivas propriedades no portal do Azure.

## <a name="view-your-device-details"></a>Ver os detalhes do seu dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos**. Em Dispositivos, tem várias opções:

  - **Descrição geral** – Obtenha informações sobre os dispositivos que inscreveu e os sistemas operativos executados em cada dispositivo.
  - **Gerir** – para ver uma lista de todos os dispositivos que gere, selecione **Todos os dispositivos** ou **Dispositivos do Azure AD**.
    Selecione um dos dispositivos na lista. Este passo abre a **Descrição geral** do <*nome de dispositivo*> , onde pode selecionar o seguinte:
    - **Descrição geral** – veja o nome do dispositivo, o proprietário, se é um dispositivo BYOD (Bring Your Own Device), quando entrou e mais detalhes
    - **Hardware** – veja qual o espaço de armazenamento livre, o modelo e fabricante e mais detalhes sobre o dispositivo
    - **Aplicações detetadas** – apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo
    - **Conformidade do dispositivo** – apresenta o estado de todas as políticas de conformidade que foram atribuídas ao dispositivo
    - **Configuração do dispositivo** – apresenta o estado de conformidade de todas as políticas de configuração do dispositivo que estão atribuídas ao mesmo
- **Monitorizar** – selecione **Ações do dispositivo** para ver uma lista das ações do dispositivo que são realizadas nos dispositivos que gere e o estado atual dos mesmos. **Registos de auditoria** – mostra o estado de diferentes tarefas.
- **Configuração** > **Conector do TeamViewer** – configure a administração remota em dispositivos que utilizam o software TeamViewer. Para obter detalhes, veja [Fornecer assistência remota para dispositivos Android geridos pelo Intune](device-profile-android-teamviewer.md).

O Intune recolhe uma lista de aplicações apenas nos dispositivos pertencentes à empresa. As aplicações não são verificadas nos dispositivos pessoais. Para PCs com o Windows 10, apenas é apresentada a lista de aplicações modernas em dispositivos pertencentes à empresa. O Intune não recolhe informações de aplicações Win32 no dispositivo. Consoante a utilização da operadora pelos dispositivos, nem todas as aplicações podem ser recolhidas.

## <a name="next-steps"></a>Próximos passos
Veja o que mais pode fazer para [gerir os seus dispositivos](device-management.md) com o Intune.
