---
title: Remover um utilizador de um dispositivo iOS com o Microsoft Intune
titleSuffix: ''
description: Saiba como remover um utilizador de um dispositivo iOS partilhado com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713164"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Remover um utilizador de um dispositivo iOS partilhado


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

A ação **Remover utilizador** elimina um utilizador selecionado da cache local num dispositivo iPad partilhado. O dispositivo iPad tem de estar configurado para gerir a aplicação Sala de Aula do iOS com o [perfil de educação do iOS](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – não suportado
- iOS – suportado no iOS 9.3 e posterior (apenas dispositivos iPad partilhados)
- macOS – não suportado
- Android – não suportado

## <a name="remove-a-user"></a>Remover um utilizador

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Todos os dispositivos**.
3. Na lista de dispositivos que gere, selecione um dispositivo iOS.
4. No painel do dispositivo, selecione **Utilizadores**.
5. Na lista, clique com o botão direito do rato no utilizador que pretende remover e, em seguida, selecione **Remover utilizador**.

## <a name="next-steps"></a>Próximos passos

- Para ver o estado da ação **Remover utilizador**, selecione **Dispositivos** > **Ações do dispositivo**.
