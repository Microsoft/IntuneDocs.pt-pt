---
title: Terminar a sessão do utilizador num dispositivo iOS
titlesuffix: Microsoft Intune
description: Saiba como terminar a sessão do utilizador atual de um dispositivo iOS com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 223906d37159ba4081f5a5c055392321ac02e0ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020627"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Terminar a sessão do utilizador atual em dispositivos iOS geridos pelo Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação **Terminar sessão do utilizador atual** termina a sessão do utilizador atual num dispositivo iPad partilhado configurado para gerir a aplicação Classroom para iOS com um [perfil de educação do iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows – não suportado
- Windows Phone – não suportado
- iOS – suportado no iOS 9.3 e posterior (apenas dispositivos iPad partilhados)
- macOS – não suportado
- Android – não suportado

## <a name="how-to-logout-the-current-user"></a>Como terminar a sessão do utilizador atual

1.  Inicie sessão no portal do Azure.
2.  Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3.  No painel **Intune**, escolha **Dispositivos**.
4.  No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5.  Na lista de dispositivos que gere, selecione um dispositivo iOS e, em seguida, selecione a ação remota de dispositivos **Terminar sessão do utilizador atual**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado da ação que acabou de realizar, no painel **Dispositivos e grupos**, escolha **Ações de Dispositivos**.
