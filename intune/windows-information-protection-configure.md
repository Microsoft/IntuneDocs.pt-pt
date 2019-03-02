---
title: As definições do Windows Information Protection no Microsoft Intune | Microsoft Intune
description: Saiba mais sobre as definições do Microsoft Intune que pode utilizar para gerir o Windows Information Protection.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6a5dea2075def1d7a30fdebc5722c4117a1579f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229637"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Como configurar o Windows Information Protection no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Com o aumento do número de dispositivos pertencentes aos empregados nas empresas, há também um maior risco de fuga de dados acidental através de aplicações e serviços, como o e-mail, as redes sociais e a cloud pública, que estão fora do controlo da empresa. Por exemplo, quando um empregado envia as imagens de um projeto mais recentes a partir da conta de e-mail pessoal dele, copia e cola informações sobre produtos num tweet ou guarda um relatório de vendas em curso no armazenamento na cloud pública.

O **Windows Information Protection** ajuda a proteger desta potencial fuga de dados sem interferir com a experiência do empregado. Também ajuda a proteger aplicações e dados da empresa contra fugas de dados acidentais em dispositivos pertencentes à empresa e em dispositivos pessoais que os empregados utilizem no trabalho, sem que seja necessário fazer alterações ao seu ambiente ou a outras aplicações.

Esta política do Intune gere a lista de aplicações que o Windows Information Protection gere, as localizações da rede empresarial, o nível de proteção e as definições de encriptação.

>[!NOTE]
> Para utilizar a aplicação Portal da Empresa do Windows 10 com o Windows Information Protection, tem de adicionar a aplicação Portal da Empresa no modo de **Isento** do Windows Information Protection. 

## <a name="next-steps"></a>Passos Seguintes
Para obter mais informações, consulte:
-  [Protect your enterprise data using Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip) (Proteger os seus dados empresariais com o Windows Information Protection).
- [Create a Windows Information Protection (WIP) policy using the classic console for Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune) (Criar uma política Windows Information Protection [WIP] através da consola clássica do Microsoft Intune)
- [Create a Windows Information Protection (WIP) policy with MDM using the Azure portal for Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure) (Criar uma política Windows Information Protection [WIP] com MDM através do portal do Azure do Microsoft Intune)
- [Create a Windows Information Protection (WIP) policy with MAM using the Azure portal for Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure) (Criar uma política Windows Information Protection [WIP] com MAM através do portal do Azure do Microsoft Intune)
