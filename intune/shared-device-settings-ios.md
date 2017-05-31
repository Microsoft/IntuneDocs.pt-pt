---
title: "Definições de configuração de dispositivos partilhados do Intune para iOS"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba as definições do Intune que pode utilizar para apresentar as informações no ecrã de bloqueio do dispositivo iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6a2aba8b2f062a3e06d517a572992b84fd977514
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Definições de configuração de Dispositivos Partilhados para apresentar mensagens no ecrã de bloqueio do dispositivo iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

As definições de configuração de dispositivos partilhados permitem-lhe especificar o texto opcional apresentado no ecrã de bloqueio e na janela de início de sessão (por exemplo, uma mensagem “Se perdido, devolver a” e Informações da Etiqueta de Recursos). 

>[!IMPORTANT]
> Esta capacidade é suportada em dispositivos supervisionados com iOS 9.3 e posterior.

1. No painel **Funcionalidades do dispositivo**, escolha **Configuração de Dispositivos Partilhados (apenas supervisionado)**.
2. No painel **Configuração de Dispositivos Partilhados (apenas supervisionado)**, configure as seguintes opções:
    - **Informações da etiqueta de recursos** – introduza informações sobre a etiqueta de recursos do dispositivo. Por exemplo: **Propriedade da Contoso Corp**. As informações introduzidas serão aplicadas a todos os dispositivos aos quais atribuir este perfil.
    - **Nota de rodapé do ecrã de bloqueio** –introduza uma nota que possa ajudar a obter o dispositivo devolvido em caso de perda ou roubo. Por exemplo: **se for encontrado, ligue para o “número”**.
3. Quando tiver terminado, escolha **OK** até regressar ao painel **Criar Perfil** e, em seguida, escolha **Criar**. 

