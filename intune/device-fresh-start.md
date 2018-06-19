---
title: Repor dispositivos Windows 10 com o Microsoft Intune – Azure | Microsoft Docs
description: Utilize a funcionalidade Começar do Zero para remover ou desinstalar aplicações de PCs com Windows 10 com o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5658bf2e1ee250ef9fd405b3f7ec1772b166f338
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021001"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utilizar a funcionalidade Começar do Zero para repor dispositivos Windows 10 com o Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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