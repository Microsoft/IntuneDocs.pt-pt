---
title: "Definir a autoridade de gestão de dispositivos móveis"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como definir a autoridade de gestão de dispositivos móveis no Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9d7a1a934188f0a40553d3c6b8b567ba8f6af034
ms.lasthandoff: 02/18/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Definir a autoridade de gestão de dispositivos móveis 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A definição da autoridade de gestão de dispositivos móveis determina como gerir os seus dispositivos. As configurações possíveis são:

- **Intune Autónomo** – gestão apenas na cloud, que configura através do portal do Azure. Inclui o conjunto completo das funcionalidades que o Intune oferece.

- **Intune Híbrido** – integração da solução cloud do Intune com o System Center Configuration Manager. Configura o Intune com a consola do Configuration Manager.

- **Gestão de Dispositivos Móveis para o Office 365** – integração do Office 365 com a solução cloud do Intune. Configura o Intune a partir do Centro de Administração do Office 365. Inclui um subconjunto das funcionalidades que estão disponíveis com o Intune Autónomo.

>[!IMPORTANT]
>Depois de definir a autoridade de gestão de dispositivos móveis, tem de contactar o [Suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) para alterá-la. Por isso, faça a sua escolha com atenção.

**Para definir a autoridade de gestão de dispositivos móveis:**

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Descrição geral**.

3. No painel **Começar a gerir dispositivos**, escolha **Definir a Autoridade de MDM como o Intune**. Uma mensagem indica que definiu com êxito a autoridade de MDM como o Intune.

