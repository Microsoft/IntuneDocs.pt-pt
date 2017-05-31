---
title: "Definir a autoridade de gestão de dispositivos móveis"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como definir a autoridade de gestão de dispositivos móveis no Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Definir a autoridade de gestão de dispositivos móveis

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Como administrador de TI, tem de definir uma autoridade de MDM antes de os utilizadores poderem inscrever dispositivos para gestão.

As configurações possíveis são:

- **Intune Autónomo** – gestão apenas na cloud, que configura através do portal do Azure. Inclui o conjunto completo das funcionalidades que o Intune oferece. [Defina a autoridade de MDM na consola do Intune](#mdm-authority-set-to-intune).

- **Intune Híbrido** – integração da solução cloud do Intune com o System Center Configuration Manager. Configura o Intune com a consola do Configuration Manager. [Defina a autoridade de MDM no Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestão de Dispositivos Móveis para o Office 365** – integração do Office 365 com a solução cloud do Intune. Configura o Intune a partir do Centro de Administração do Office 365. Inclui um subconjunto das funcionalidades que estão disponíveis com o Intune Autónomo. Defina a autoridade de MDM no Centro de Administração do Office 365.

>[!IMPORTANT]
>Depois de definir a autoridade de gestão de dispositivos móveis, tem de contactar o [Suporte da Microsoft](https://docs.microsoft.com/intune-classic/troubleshoot/get-support) para alterá-la. Por isso, faça a sua escolha com atenção.

## <a name="set-mdm-authority-to-intune"></a>Definir a autoridade de MDM como o Intune

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
  ![Captura de ecrã da carga de trabalho da Resolução de Problemas do Intune com a ligação Selecionar Utilizador](media/set-mdm-auth.png)
2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Descrição Geral**.

3. No painel **Começar a gerir dispositivos**, escolha **Definir a Autoridade de MDM como o Intune**. Uma mensagem indica que definiu com êxito a autoridade de MDM como o Intune.

