---
title: "Definir a autoridade de gestão de dispositivos móveis"
titleSuffix: Intune on Azure
description: "Saiba como definir a autoridade de gestão de dispositivos móveis no Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 449c45e0edcc0d0a33352ba154ad68fa6c4725c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="set-the-mobile-device-management-authority"></a>Definir a autoridade de gestão de dispositivos móveis

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.

As configurações possíveis são:

- **Intune Autónomo** – gestão apenas na cloud, que configura através do portal do Azure. Inclui o conjunto completo das funcionalidades que o Intune oferece. [Defina a autoridade de MDM na consola do Intune](#mdm-authority-set-to-intune).

- **Intune Híbrido** – integração da solução cloud do Intune com o System Center Configuration Manager. Configura o Intune com a consola do Configuration Manager. [Defina a autoridade de MDM no Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestão de Dispositivos Móveis para o Office 365** – integração do Office 365 com a solução cloud do Intune. Configura o Intune a partir do Centro de Administração do Office 365. Inclui um subconjunto das funcionalidades que estão disponíveis com o Intune Autónomo. Defina a autoridade de MDM no Centro de Administração do Office 365.

>[!IMPORTANT]    
No Configuration Manager versão 1610 ou posterior e no Microsoft Intune versão 1705, pode alterar a autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Para obter detalhes, veja [O que fazer se escolher a definição de autoridade MDM errada](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Definir a autoridade de MDM como o Intune

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
  ![Captura de ecrã da carga de trabalho da Resolução de Problemas do Intune com a ligação Selecionar Utilizador](media/set-mdm-auth.png)
2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Descrição Geral**.

3. No painel **Começar a gerir dispositivos**, escolha **Definir a Autoridade de MDM como o Intune**. Uma mensagem indica que definiu com êxito a autoridade de MDM como o Intune.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Limpeza de dispositivos móveis após a expiração do certificado MDM

O certificado MDM é renovado automaticamente quando os dispositivos móveis estão a comunicar com o serviço do Intune. Se os dispositivos móveis forem eliminados ou não conseguirem comunicar com o serviço do Intune durante um determinado período de tempo, o certificado MDM não será renovado. O dispositivo é removido do portal do Azure 180 dias depois da expiração do certificado MDM.
