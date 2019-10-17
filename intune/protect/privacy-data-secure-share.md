---
title: Partilha e segurança de dados no Intune
titleSuffix: Microsoft Intune
description: Saiba como os dados pessoais são protegidos e partilhados no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b17b87462b2c73e265f062c33a06a810e7c58bf8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504341"
---
# <a name="data-security-and-sharing-in-intune"></a>Partilha e segurança de dados no Intune


## <a name="data-security"></a>Segurança de dados

O Microsoft Intune é um componente fundamental da oferta do serviço Microsoft Enterprise Mobility and Security Suite. Para apoiar a [estratégia de governação de dados](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx), todos os serviços cloud da Microsoft são desenvolvidos com metodologias de [Privacidade da Microsoft](https://www.microsoft.com/en-us/trustcenter/privacy) e de [Segurança da Microsoft](https://www.microsoft.com/en-us/trustcenter/security/).  

O Microsoft Intune segue as mesmas medidas técnicas e organizacionais que as equipas de serviço do Microsoft Azure tomam para a proteção contra processos de falha de segurança de dados.

Para obter mais informações, veja o [Portal de Confiança do Serviço](https://www.microsoft.com/en-us/TrustCenter/stp).

O Intune recorre a técnicas de minimização de dados, tais como

- agregação
- recolha de dados opcional para algumas funcionalidades
- dados menos precisos ou sensíveis

O Intune recorre também a técnicas, tais como o RBAC e a segurança JiT em caso de incidentes de suporte, para garantir a Proteção de Dados por Defeito. 

### <a name="data-breach-reporting"></a>Relatórios de falha de segurança de dados

Quando é identificado um Incidente de Segurança Comunicável pelo Cliente (CRSI), os clientes são notificados. Este processo envolve a colaboração com a equipa do Microsoft Office 365 para comunicar a notificação da falha de segurança a todos os clientes do Microsoft Office 365 que utilizam o Intune.

## <a name="data-sharing"></a>Partilha de dados

Quando os administradores de inquilinos ativam determinadas funcionalidades, por exemplo, o Programa de Registo de Aparelho Apple, o Microsoft Intune obtém o consentimento do administrador para partilhar dados com terceiros adequados. Nestes casos, o Intune poderá partilhar dados pessoais com:

- Terceiros que atuem como agentes da Microsoft.
- Terceiros que não atuem como agentes da Microsoft, mas apenas quando os administradores de inquilinos concederem explicitamente permissão ao Intune para o fazer.

Os terceiros que atuem como agentes da Microsoft estão incluídos na [lista de Subcontratantes dos Serviços Online](https://aka.ms/Online_Serv_Subcontractor_List).

Os dados são partilhados com estas entidades para ajudar o cliente e o suporte técnico, a manutenção do serviço e outras operações.

Os dados pessoais constantes no Intune mantidos em serviços de terceiros são regidos por um contrato de inquilino com terceiros. Este contrato também permite que o Intune transmita os dados para os serviços de terceiros.  

Para obter informações sobre os dados partilhados com alguns terceiros, veja os seguintes artigos:
- [Dados que o Intune envia para a Apple](data-intune-sends-to-apple.md)
- [Dados que o Intune envia para a Google](data-intune-sends-to-google.md)
- [Dados que a Apple envia para o Intune](data-apple-sends-to-intune.md)
- [Dados que a Google envia para o Intune](data-google-sends-to-intune.md)
- [O data JAMF pro envia ao Intune](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>Partilha de dados do System Center Configuration Manager

O Microsoft Intune não partilha dados com o System Center Configuration Manager. O System Center Configuration Manager é um produto implementado, gerido e operado no local diretamente pelo cliente. Os diagnósticos e dados de utilização recolhidos pelo Configuration Manager destinam-se apenas a melhorar a experiência de instalação, qualidade e segurança de versões futuras.

Para saber mais, veja [Diagnósticos e dados de utilização do SCCM](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). 


## <a name="next-steps"></a>Próximos passos

Saiba como [ver e corrigir](privacy-data-view-correct.md) dados pessoais no Intune.
