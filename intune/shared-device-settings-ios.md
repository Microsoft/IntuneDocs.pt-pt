---
title: "Definições de configuração de dispositivos partilhados do Intune para iOS"
titlesuffix: Azure portal
description: "Saiba as definições do Intune que pode utilizar para apresentar as informações no ecrã de bloqueio do dispositivo iOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5473a280551ab74f781a2de682d7e5922491e98
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Definições de configuração de dispositivos partilhados para apresentar mensagens no ecrã de bloqueio do dispositivo iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As definições de configuração de dispositivos partilhados permitem-lhe especificar o texto opcional que é apresentado na janela de início de sessão e no ecrã de bloqueio. Por exemplo, pode introduzir uma mensagem do tipo "Em Caso de Extravio, Devolver a" e Informações de Etiqueta de Recurso. 

>[!IMPORTANT]
> Esta capacidade é suportada em dispositivos supervisionados com iOS 9.3 e posterior.

## <a name="create-shared-device-settings"></a>Criar definições de dispositivos partilhados

1. No painel **Funcionalidades do dispositivo**, selecione **Configuração de Dispositivos Partilhados (apenas supervisionado)**.
2. No painel **Configuração de Dispositivos Partilhados (apenas supervisionado)**, configure as seguintes definições:
    - **Informações da etiqueta de recursos** – introduza informações sobre a etiqueta de recursos do dispositivo. Por exemplo: **Propriedade da Contoso Corp**. As informações que introduzir serão aplicadas a todos os dispositivos que atribuir a este perfil.
    - **Nota de rodapé do ecrã de bloqueio** – introduza uma nota que possa ajudar à devolução do dispositivo, caso este seja perdido ou extraviado. Por exemplo: **Se encontrar este dispositivo, ligue para o seguinte número: "número"**.
3. Quando tiver terminado, escolha **OK** até regressar ao painel **Criar Perfil** e, em seguida, escolha **Criar**. 


## <a name="next-steps"></a>Próximos passos

Agora pode atribuir o perfil do dispositivo aos grupos que selecionar. Para obter detalhes, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
