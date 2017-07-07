---
title: "Extinguir aplicações"
description: "Saiba como extinguir ou desinstalar aplicações com o Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1851fa03d36ffe42a49fd557cdd0c2c6250726f4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="retire-apps-using-microsoft-intune"></a>Extinguir aplicações com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para extinguir uma aplicação, basta desinstalá-la. Quando implementar e gerir aplicações com o Intune, o processo para desinstalar a aplicação é o mesmo para dispositivos móveis e para PCs Windows. A aplicação tem de suportar o processo de desinstalação para este procedimento ser concluído com êxito.

## <a name="uninstall-an-app"></a>Desinstalar uma aplicação

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Aplicações** &gt; **Aplicações**.

2.  Selecione a aplicação que pretende desinstalar (uma que tenha sido implementada anteriormente) e, em seguida, escolha **Gerir Implementação**.

3.  Na página **Ação de Implementação**, selecione **Desinstalar** a partir da coluna **Aprovação** .

Quando o computador ou dispositivo verificar as aplicações, a aplicação será desinstalada.

### <a name="see-also"></a>Consulte também
[Adicionar aplicações no Microsoft Intune](add-apps.md)
