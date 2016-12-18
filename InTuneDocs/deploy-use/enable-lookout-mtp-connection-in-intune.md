---
title: Ativar o Lookout MTP no Intune | Microsoft Intune
description: "Ative o Lookout Mobile Threat Protection na consola de administração do Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 1bef6c15387309e1b36bc85758ca699acd54fdd0


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Ativar a ligação Lookout MTP na consola de administração do Intune
Este tópico mostra-lhe como ativar a ligação Lookout MTP no Intune. Antes de efetuar este passo, já deverá ter o Conector do Intune configurado na consola do Lookout.  Se ainda não o fez, efetue os passos descritos em [Set up your subscription with Lookout mobile threat protection (Configurar a sua subscrição com o Lookout Mobile Threat Protection – em inglês)](set-up-your-subscription-with-lookout-mtp.md).

Para ativar a ligação Lookout MTP no Intune, na página **Administração**, na [Consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Integração de Serviço de Terceiros**. Selecione **Estado do Lookout** e ative a opção **Sincronização com MTP** utilizando o botão de alternar.

![captura de ecrã da página de sincronização do Lookout com o botão de alternar realçado](../media/mtp/lookout-intune-synchronization.png)

Este passo conclui a configuração da integração do Lookout e do Intune na consola do administrador do Intune.  Os próximos passos para implementar esta solução envolvem a implementação da [aplicação Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) e a configuração da política de [conformidade](enable-device-threat-protection-rule-in-compliance-policy.md).

>[!IMPORTANT]
> **Tem** de configurar a aplicação Lookout for Work antes de criar as regras de política de conformidade e configurar o acesso condicional. Isto garante que a aplicação está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.
## <a name="next-steps"></a>Próximos passos
[Configurar a aplicação Lookout for Work ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Dec16_HO2-->


