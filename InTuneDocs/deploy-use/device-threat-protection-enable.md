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
ms.sourcegitcommit: 53862e49c922b75b414fd5aceec3bba2b10299a6
ms.openlocfilehash: 1297522d0f7b52ebe14eb7b938f3458e7308ae27


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Ativar a ligação Lookout MTP na consola de administração do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para ativar a ligação do Lookout Mobile Threat Protection (MTP) no Intune, já deve ter configurado o Conector do Intune na consola do Lookout.  Se ainda não o fez, deve [Configurar a sua subscrição com o Lookout Mobile Threat Protection](set-up-your-subscription-with-lookout-mtp.md).

Para ativar a ligação Lookout MTP no Intune, na página **Administração**, na [Consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Integração de Serviço de Terceiros**. Selecione **Estado do Lookout** e ative a opção **Sincronização com MTP** utilizando o botão de alternar.

![captura de ecrã da página de sincronização do Lookout com o botão de alternar realçado](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> **Tem** de configurar a aplicação Lookout for Work antes de criar as regras de política de conformidade e configurar o acesso condicional. Isto garante que a aplicação está pronta e disponível para os utilizadores finais instalarem antes de poderem aceder ao e-mail ou a outros recursos da empresa.

Este passo conclui a configuração da integração do Lookout e do Intune na consola do administrador do Intune.  Os Passos seguintes para implementar esta solução envolvem a implementação da [aplicação Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) e a configuração da política de [conformidade](enable-device-threat-protection-rule-in-compliance-policy.md).


## <a name="next-steps"></a>Passos seguintes
[Configurar a aplicação Lookout for Work ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Jan17_HO2-->


