---
title: Ativar o Lookout MTP no Intune
description: "Ative o Lookout Mobile Threat Protection na consola de administração do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f34697140a287d41203d1bad5df59250f07d08ce
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="enable-lookout-mtd-connection-in-the-intune-classic-portal"></a>Ativar a ligação do Lookout MTD no portal clássico do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para ativar a ligação da Defesa Contra Ameaças para Dispositivos Móveis (MTP) do Lookout no Intune, já deve ter configurado o Conetor do Intune na consola do Lookout.  Se ainda não o fez, deve [Configurar a sua subscrição da Defesa Contra Ameaças para Dispositivos Móveis do Lookout](setup-your-lookout-mtd-subscription.md).

Para ativar a ligação Lookout MTP no Intune, na página **Administração**, na [Consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Integração de Serviço de Terceiros**. Selecione **Estado do Lookout** e ative a opção **Sincronização com MTP** utilizando o botão de alternar.

![captura de ecrã da página de sincronização do Lookout com o botão de alternar realçado](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> **Tem** de configurar a aplicação Lookout for Work antes de criar as regras de política de conformidade e configurar o acesso condicional. Isto garante que a aplicação está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

Este passo conclui a configuração da integração do Lookout e do Intune na consola do administrador do Intune.  Os próximos passos para implementar esta solução envolvem implementar a política das [aplicações Lookout for Work](/intune-classic/deploy-use/device-threat-protection-policy).


## <a name="next-steps"></a>Passos seguintes
[Configurar a aplicação Lookout for Work ](/intune-classic/deploy-use/device-threat-protection-apps)
