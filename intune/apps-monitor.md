---
title: "Como monitorizar informações e atribuições da aplicação | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: depois de atribuir uma aplicação aos utilizadores ou dispositivos, utilize estas informações para o ajudar a monitorizar o estado."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7c39c904cd2a7bd20525d9072067c6e484b4437a
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Como monitorizar informações e atribuições da aplicação com o Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

O Intune fornece várias formas através das quais pode monitorizar as propriedades das aplicações que gere, assim como os respetivos estados das atribuições.

1. Na carga de trabalho **Aplicações Móveis**, escolha **Gerir** > **Aplicações**.
2. No painel da lista de aplicações, escolha a aplicação da qual pretende ver informações. Em seguida, verá o painel <*nome da aplicação*> **Estado da instalação do dispositivo**: ![painel do estado da instalação de aplicações.](./media/monitor-apps.png)

Depois, selecione uma das seguintes ações para saber mais sobre as suas aplicações e as respetivas atribuições.

## <a name="general"></a>Geral

- **Descrição geral** – fornece uma descrição geral básica da aplicação e informações sobre o estado de qualquer atribuição para essa aplicação. Pode escolher um dos gráficos para abrir os painéis **Estado da instalação do dispositivo** ou **Estado da instalação do utilizador** para obter informações mais detalhadas.

## <a name="manage"></a>Gerir o Endpoint Protection do

- **Propriedades** – permite-lhe ver e alterar as informações sobre a aplicação selecionada. Para obter mais informações sobre as propriedades da aplicação, veja [Como adicionar uma aplicação ao Microsoft Intune](apps-add.md).
- **Atribuições** – fornece informações sobre atribuições para esta aplicação. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

## <a name="monitor"></a>Monitor

- **Estado da instalação do dispositivo** – fornece informações detalhadas para cada dispositivo ao qual atribuiu a aplicação selecionada, incluindo o nome do dispositivo, sistema operativo, realização do último registo do dispositivo no Intune e o estado da instalação da aplicação.
- **Estado da instalação do utilizador** – fornece informações detalhadas do utilizador ao qual atribuiu a aplicação selecionada, incluindo o número de instalações da aplicação que o utilizador tem em todos os respetivos dispositivos e informações sobre qualquer falha da instalação.