---
title: Definições de configuração de dispositivos partilhados do Microsoft Intune para iOS
titlesuffix: ''
description: Saiba que definições do Microsoft Intune pode utilizar para apresentar informações no ecrã de bloqueio do dispositivo iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 638b4b3ebc83917faae0d34ec407b8ad47b4a4fb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183388"
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Definições de configuração de dispositivos partilhados para apresentar mensagens no ecrã de bloqueio do dispositivo iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe que definições do Microsoft Intune pode utilizar para apresentar informações no ecrã de bloqueio do dispositivo iOS.

As definições de configuração de dispositivos partilhados permitem-lhe especificar o texto opcional que é apresentado na janela de início de sessão e no ecrã de bloqueio. Por exemplo, pode introduzir uma mensagem do tipo "Em Caso de Extravio, Devolver a" e Informações de Etiqueta de Recurso. 

>[!IMPORTANT]
> Esta capacidade é suportada em dispositivos supervisionados com iOS 9.3 e posterior.

## <a name="create-shared-device-settings"></a>Criar definições de dispositivos partilhados

1. A partir do [Intune no Portal do Azure](https://portal.azure.com), navegue para [**Funcionalidades do dispositivo** na área de configuração do dispositivo](device-features-configure.md). 
1. No painel **Funcionalidades do dispositivo**, selecione **Configuração de Dispositivos Partilhados (apenas supervisionado)**.
2. No painel **Configuração de Dispositivos Partilhados (apenas supervisionado)**, configure as seguintes definições:
    - **Informações da etiqueta de recursos** – introduza informações sobre a etiqueta de recursos do dispositivo. Por exemplo: **Propriedade da Contoso Corp**. As informações que introduzir serão aplicadas a todos os dispositivos que atribuir a este perfil.
    - **Nota de rodapé do ecrã de bloqueio** – introduza uma nota que possa ajudar à devolução do dispositivo, caso este seja perdido ou extraviado. Por exemplo: **Se encontrar este dispositivo, ligue para o seguinte número: "número"**.
3. Quando tiver terminado, selecione **OK** até regressar ao painel **Criar perfil** e, em seguida, selecione **Criar**. 


## <a name="next-steps"></a>Passos Seguintes

Agora pode atribuir o perfil do dispositivo aos grupos que selecionar. Para obter detalhes, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
