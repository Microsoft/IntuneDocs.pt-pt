---
title: Remover um utilizador de um dispositivo iOS com o Intune
titlesuffix: Azure portal
description: Saiba como remover um utilizador de um dispositivo iOS partilhado com o Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dd6f4fab1d21d3fd40c3ec6abd4be44cff5212e
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>Remover um utilizador de um dispositivo iOS partilhado com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação **Remover utilizador** elimina um utilizador que selecionar na cache local num dispositivo iPad partilhado que tenha sido configurado para gerir a aplicação Sala de Aula para iOS com um [perfil de educação do iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – não suportado
- iOS – suportado no iOS 9.3 e posterior (apenas dispositivos iPad partilhados)
- macOS – não suportado
- Android – não suportado

## <a name="how-to-remove-a-user"></a>Como remover um utilizador

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, selecione um dispositivo iOS.
6. No painel desse dispositivo, selecione **Utilizadores**.
7. Na lista, clique com o botão direito do rato no utilizador que pretende remover e, em seguida, selecione **Remover utilizador**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
