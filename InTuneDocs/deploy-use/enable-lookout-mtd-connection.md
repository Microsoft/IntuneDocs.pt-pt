---
title: Ativar o Lookout MTP no Intune | Documentos da Microsoft
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
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d42fa20a3bc6b6f4a74dd0872aae25cfb33067b9
ms.openlocfilehash: d2a10a0e14d9b0b4d2e3f8e2715b47d984e5aa66
ms.lasthandoff: 03/21/2017


---

# <a name="enable-lookout-mtd-connection-in-the-intune-classic-console"></a>Ativar a ligação da MTP do Lookout na consola clássica do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para ativar a ligação da Defesa Contra Ameaças para Dispositivos Móveis (MTP) do Lookout no Intune, já deve ter configurado o Conetor do Intune na consola do Lookout.  Se ainda não o fez, deve [Configurar a sua subscrição da Defesa Contra Ameaças para Dispositivos Móveis do Lookout](set-up-your-subscription-with-lookout-mtp.md).

Para ativar a ligação Lookout MTP no Intune, na página **Administração**, na [Consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Integração de Serviço de Terceiros**. Selecione **Estado do Lookout** e ative a opção **Sincronização com MTP** utilizando o botão de alternar.

![captura de ecrã da página de sincronização do Lookout com o botão de alternar realçado](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> **Tem** de configurar a aplicação Lookout for Work antes de criar as regras de política de conformidade e configurar o acesso condicional. Isto garante que a aplicação está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

Este passo conclui a configuração da integração do Lookout e do Intune na consola do administrador do Intune.  Os Passos seguintes para implementar esta solução envolvem a implementação da [aplicação Lookout for Work](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps) e a configuração da política de [conformidade](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-policy).


## <a name="next-steps"></a>Passos seguintes
[Configurar a aplicação Lookout for Work ](https://docs.microsoft.com/intune/deploy-use/device-threat-protection-apps)

