---
title: "Configurar o Windows Information Protection – Intune"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para gerir o Windows Information Protection."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f233672c-7d9b-4554-af1f-92c001a1a3c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 66be6716df38d868e8247131b49ffb50fc48e60b
ms.openlocfilehash: 84fb6c275995fc43226adbda5fc5c40344d6eb09
ms.lasthandoff: 04/15/2017


---

# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Como configurar o Windows Information Protection no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Com o aumento do número de dispositivos pertencentes aos empregados nas empresas, há também um maior risco de fuga de dados acidental através de aplicações e serviços, como o e-mail, as redes sociais e a cloud pública, que estão fora do controlo da empresa. Por exemplo, quando um empregado envia as imagens de um projeto mais recentes a partir da conta de e-mail pessoal dele, copia e cola informações sobre produtos num tweet ou guarda um relatório de vendas em curso no armazenamento na cloud pública.

O **Windows Information Protection** ajuda a proteger desta potencial fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger aplicações e dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os empregados utilizem no trabalho, sem que seja necessário fazer alterações ao seu ambiente ou a outras aplicações.

Esta política do Intune gere a lista de aplicações que o Windows Information Protection gere, as localizações da rede empresarial, o nível de proteção e as definições de encriptação.

>[!NOTE]
> Para utilizar a aplicação Portal da Empresa do Windows 10 com o Windows Information Protection, tem de adicionar a aplicação Portal da Empresa no modo de **Isento** do Windows Information Protection. 

### <a name="next-steps"></a>Próximos passos
Para mais informações, consulte [Proteger os dados empresariais com o Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

