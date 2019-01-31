---
title: Repor dispositivos Windows 10 com o Microsoft Intune – Azure | Microsoft Docs
description: Utilize a funcionalidade Começar do Zero para remover ou desinstalar aplicações de PCs com Windows 10 com o Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1eb1e671cc16196974cb15cdc785ba7d99fa8f46
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303417"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utilizar a funcionalidade Começar do Zero para repor dispositivos Windows 10 com o Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação de dispositivo **Começar do Zero** remove todas as aplicações instaladas num PC com a versão 1703 ou posterior do Windows 10. A funcionalidade Começar do Zero ajuda a remover aplicações que vêm geralmente pré-instaladas (OEM) num PC novo.  

1. Inicie sessão no [portal do Azure](https://portal.azure.com) e aceda a > **Microsoft Intune** > **Dispositivos** > **Todos os dispositivos**.
2. Na lista dos dispositivos que gere, selecione um computador com o Windows 10.
3. Clique em **Começar de Novo**. 
4. Selecione **Manter os dados de utilizador neste dispositivo** para:
   * Manter o dispositivo associado ao Azure AD
    * Dispositivo é inscrito na gestão de dispositivos móveis novamente quando quando um Azure Active Directory ativada o utilizador inicia sessão no dispositivo.
    * Manter os conteúdos da pasta Raiz do utilizador do dispositivo e remover as aplicações e definições  
  > [!IMPORTANT]
 > Se não mantiver os dados do utilizador, o dispositivo será restaurado para o estado de configuração inicial. Dispositivos BYOD irão anular a inscrição do Azure AD e gestão de dispositivos móveis.
 > Dispositivos do Azure AD associado serão inscritos para gestão de dispositivos móveis novamente quando um Azure Active Directory ativada o utilizador inicia sessão no dispositivo.
 
5. Clique em **OK**.   
6. Para ver o estado desta ação, volte a **Dispositivos** e clique em **Ações do dispositivo**.  
