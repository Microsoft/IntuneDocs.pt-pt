---
title: "Restrições de dispositivos no Intune para dispositivos Windows 10 Team"
titlesuffix: Azure portal
description: "Saiba mais sobre as restrições disponíveis para dispositivos Windows 10 Team.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 824e5e24e73c0c4c3b34e9b045d3a85bd7ed643c
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos Windows 10 Team no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="apps-and-experience"></a>Aplicações e experiência

- **Ativar ecrã quando alguém entra na sala** – Permite ao dispositivo ser reativado automaticamente quando o sensor deteta alguém na sala.
- **Informações sobre a reunião apresentadas no ecrã de boas-vindas** – ative esta opção para escolher as informações que são apresentadas no mosaico Reuniões do ecrã de boas-vindas. É possível:
    - **Mostrar apenas organizador e hora**
    - **Mostrar organizador, hora e assunto (assunto oculto para reuniões privadas)**
- **URL da imagem de fundo do ecrã de boas-vindas** – Ative esta definição para apresentar um fundo personalizado no ecrã **Bem-vindo** dos dispositivos Windows 10 Team a partir do URL especificado.<br>A imagem tem de estar no formato PNG e o URL tem de começar por **https://**.

## <a name="azure-operational-insights"></a>Informações operacionais do Azure

- **Informações Operacionais do Azure** – as Informações Operacionais do Azure, parte do conjunto de aplicações Microsoft Operations Manager, recolhe, armazena e analisa os dados dos ficheiros de registo a partir de dispositivos com o Windows 10 Team.
Para ligar às Informações Operacionais do Azure, tem de especificar um **ID da Área de Trabalho** e uma **Chave da Área de Trabalho**.

## <a name="maintenance"></a>Manutenção

- **Janela de manutenção de atualizações** – Configura a janela quando podem ocorrer atualizações ao dispositivo. Pode configurar a **Hora de início** da janela e a **Duração em horas** (de 1 a 5 horas).

## <a name="wireless-projection"></a>Projeção sem fios

- **PIN para projeção sem fios** – Especifica se deve introduzir um PIN para poder utilizar as capacidades de projeção sem fios do dispositivo.
- **Projeção sem fios Miracast** – se quiser permitir que o dispositivo com o Windows 10 Team utilize dispositivos preparados para Miracast para projeção, selecione esta opção.
- **Canal de projeção sem fios Miracast** – selecione o canal Miracast que será utilizado para estabelecer a ligação.


## <a name="next-steps"></a>Próximos passos

Utilize as informações em [Como configurar definições de restrições de dispositivos](device-restrictions-configure.md) para guardar e atribuir o perfil a utilizadores e dispositivos.
