---
title: "Repor dispositivos Windows 10 com o Microsoft Intune – Azure | Microsoft Docs"
description: "Utilize a funcionalidade Começar do Zero para remover ou desinstalar aplicações em PCs com Windows 10 com o Microsoft Intune, incluindo aplicações pré-instaladas de OEMs. Também é possível manter os conteúdos da pasta raiz do utilizador através da definição \"se os dados de utilizador forem retidos\"."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d17c9dc11791f32f0c2c1e7faa88966c112fc6a5
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/09/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utilizar a funcionalidade Começar do Zero para repor dispositivos Windows 10 com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação de dispositivo **Começar do Zero** remove as aplicações instaladas em PCs com a versão Atualização para Criativos do Windows 10. Em seguida, atualiza automaticamente o PC para a versão mais recente do Windows.

Esta ação ajuda a remover aplicações que vêm geralmente pré-instaladas (OEM) num PC novo. Para manter os conteúdos da pasta raiz de um utilizador e apenas remover as aplicações e definições, utilize a definição `if user data is retained`.

> [!IMPORTANT]
> A funcionalidade Começar do Zero anula a inscrição do dispositivo no Intune, mas o mesmo continua associado ao Azure Active Directory.

## <a name="use-fresh-start"></a>Utilizar a funcionalidade Começar do Zero

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** e, em seguida, selecione **Todos os dispositivos**.
4. A partir da lista de dispositivos que gere, selecione um computador com Windows 10 e, em seguida, selecione **Começar do Zero**.

## <a name="next-steps"></a>Próximos passos

Para ver o estado desta ação, selecione **Ações do dispositivo** (**Microsoft Intune** > **Dispositivos**).