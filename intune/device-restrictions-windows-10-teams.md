---
title: "Restrições de dispositivos no Intune para dispositivos Windows 10 Team"
titleSuffix: Intune on Azure
description: "Saiba mais sobre as restrições disponíveis para dispositivos Windows 10 Team.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7a5c3eaf3d2b1fc4383282473352124c793b666f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Windows 10 Team no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

- **Ativar ecrã quando alguém entra na sala** – Permite ao dispositivo ser reativado automaticamente quando o sensor deteta alguém na sala.
- **PIN para projeção sem fios** – Especifica se deve introduzir um PIN para poder utilizar as capacidades de projeção sem fios do dispositivo.
- **Projeção sem fios Miracast** – Ative esta opção se quer permitir que o dispositivo Windows 10 Team utilize dispositivos preparados para Miracast para projeção.
- **Informações sobre a reunião apresentadas no ecrã de boas-vindas** – Se ativar esta opção, pode escolher as informações que serão apresentadas no mosaico Reuniões do ecrã Bem-vindo. É possível:
    - **Mostrar apenas organizador e hora**
    - **Mostrar organizador, hora e assunto (assunto oculto para reuniões privadas)**
- **URL da imagem de fundo do ecrã de boas-vindas** – Ative esta definição para apresentar um fundo personalizado no ecrã **Bem-vindo** dos dispositivos Windows 10 Team a partir do URL especificado.<br>A imagem tem de estar no formato PNG e o URL tem de começar por **https://**.
- **Janela de manutenção de atualizações** – Configura a janela quando podem ocorrer atualizações ao dispositivo. Pode configurar a hora de início da janela e a duração (de 1 a 5 horas).
- **Informações Operacionais do Azure** – As Informações Operacionais do Azure, parte do conjunto de aplicações Microsoft Operations Manager, recolhe, armazena e analisa os dados dos ficheiros de registo a partir de dispositivos Windows 10 Team.<br>Para ligar às Informações Operacionais do Azure, tem de especificar um **ID da Área de Trabalho** e uma **Chave da Área de Trabalho**.
