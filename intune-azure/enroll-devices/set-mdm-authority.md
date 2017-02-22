---
title: "Definir a autoridade de gestão de dispositivos móveis | Pé-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pé-visualização do Azure no Intune: saiba como definir a autoridade de gestão de dispositivos móveis no Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 3c0de501c172484f036aa2d812f0c40fcfa1d93f

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

1. No portal do Azure, escolha **Mais Serviços**, introduza **Intune** na caixa de texto e, em seguida, escolha **Outros** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Descrição geral**.

3. No painel **Começar a gerir dispositivos**, escolha **Definir a Autoridade de MDM como o Intune**. Uma mensagem indica que definiu com êxito a autoridade de MDM como o Intune.



<!--HONumber=Feb17_HO1-->


