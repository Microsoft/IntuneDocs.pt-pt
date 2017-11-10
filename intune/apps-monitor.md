---
title: "Como monitorizar informações e atribuições da aplicação"
titlesuffix: Azure portal
description: "Depois de atribuir uma aplicação aos utilizadores ou dispositivos, utilize estas informações para o ajudar a monitorizar o estado.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3736b6d43f5cd3b6c75097a2ceabebffd75f0caa
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Como monitorizar informações e atribuições da aplicação com o Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune fornece várias formas através das quais pode monitorizar as propriedades das aplicações que gere, assim como os respetivos estados das atribuições.

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** + **Intune**.
3. Na carga de trabalho **Aplicações Móveis**, selecione **Aplicações** no grupo **Gerir**.
     
    ![Painel de estado de instalação de aplicações.](./media/monitor-apps.png)
5. Na lista do painel de aplicações, escolha uma aplicação. Em seguida, verá o painel <*nome da aplicação*> **Estado de instalação do dispositivo**.

O relatório de estado de instalação do dispositivo contém as seguintes colunas:

1.  **Nome do Dispositivo** – o nome do tipo de dispositivo.
2.  **Nome do Utilizador** – o nome do utilizador.
3.   **Plataforma** – o sistema operativo instalado no dispositivo.
4.  **Versão** – o número da versão da aplicação.
5.   **Estado** – os estados possíveis para as aplicações são: **Instalado**, **Não Instalado**, **Instalação Pendente** e **Erro**.
6. **Detalhes do Estado** – uma descrição legível do estado da aplicação no dispositivo.
7. **Última Entrada** – a última vez que o dispositivo entrou no Intune.

Depois, selecione uma das seguintes ações para saber mais sobre as suas aplicações e as respetivas atribuições.

## <a name="general"></a>Geral

- **Descrição geral** – fornece uma descrição geral básica da aplicação e informações sobre o estado de qualquer atribuição para essa aplicação. Pode escolher um dos gráficos para abrir os painéis **Estado da instalação do dispositivo** ou **Estado da instalação do utilizador** para obter informações mais detalhadas.

## <a name="manage"></a>Gerir o Endpoint Protection do

- **Propriedades** – permite-lhe ver e alterar as informações sobre a aplicação selecionada. Para obter mais informações sobre as propriedades da aplicação, veja [Como adicionar uma aplicação ao Microsoft Intune](apps-add.md).
- **Atribuições** – fornece informações sobre atribuições para esta aplicação. Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

## <a name="monitor"></a>Monitor

- **Estado da instalação do dispositivo** – fornece informações detalhadas para cada dispositivo ao qual atribuiu a aplicação selecionada, incluindo o nome do dispositivo, sistema operativo, realização do último registo do dispositivo no Intune e o estado da instalação da aplicação.
- **Estado da instalação do utilizador** – fornece informações detalhadas do utilizador ao qual atribuiu a aplicação selecionada, incluindo o número de instalações da aplicação que o utilizador tem em todos os respetivos dispositivos e informações sobre qualquer falha da instalação.