---
title: Segurança e compartilhamento de dados no Intune
titleSuffix: Microsoft Intune
description: Saiba como os dados pessoais são protegidos e compartilhados no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53480b7a2e008af46f4f8929cc6321e10b042b33
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306753"
---
# <a name="data-security-and-sharing-in-intune"></a>Segurança e compartilhamento de dados no Intune


## <a name="data-security"></a>Segurança dos dados

Microsoft Intune é um componente fundamental da oferta de serviço de nuvem do Microsoft Enterprise Mobility e Security Suite. Para dar suporte à [estratégia de governança de dados](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx), todos os serviços de nuvem da Microsoft são desenvolvidos com as metodologias de [privacidade](https://www.microsoft.com/en-us/trustcenter/privacy) e [segurança](https://www.microsoft.com/en-us/trustcenter/security/) da Microsoft.  

Microsoft Intune segue as mesmas medidas técnicas e organizacionais que as equipes de serviço Microsoft Azure usam para proteger contra processos de violação de dados.

Para obter mais informações, consulte o [portal de confiança do serviço](https://www.microsoft.com/en-us/TrustCenter/stp).

O Intune usa técnicas de minimização de dados, como

- Aggregation
- coleta de dados opcional para alguns recursos
- dados feitos menos precisos ou confidenciais

O Intune também usa técnicas como RBAC e segurança JiT para incidentes de suporte para garantir a proteção de dados por padrão. 

### <a name="data-breach-reporting"></a>Relatório de violação de dados

Quando um incidente de segurança reportable do cliente (CRSI) é identificado, os clientes são notificados. Esse processo inclui o trabalho com a equipe do Microsoft O365 para comunicar notificações de violação para quaisquer clientes do Microsoft O365 usando o Intune.

## <a name="data-sharing"></a>Compartilhamento de dados

Quando os administradores de locatários ativam determinadas funcionalidades (como a Apple Programa de registro de dispositivos), Microsoft Intune Obtém o consentimento do administrador para compartilhar dados com as terceiras partes apropriadas. Nesses casos, o Intune pode compartilhar dados pessoais com:

- Terceiros atuando como agentes da Microsoft.
- Terceiros que não atuam como agentes da Microsoft, mas somente quando os administradores de locatários concedem explicitamente permissão do Intune para fazer isso.

Todas as terceiros que atuam como agentes da Microsoft são incluídas na [lista subcontratados dos serviços online](https://aka.ms/Online_Serv_Subcontractor_List).

O compartilhamento de dados com essas entidades é feito para auxiliar o cliente e o suporte técnico, manutenção do serviço e outras operações.

O contrato de um locatário com o terceiro rege os dados pessoais do Intune mantidos no serviço de terceiros. Ele também concede ao Intune a permissão para transmitir dados para o serviço de terceiros.  

Para obter informações sobre os dados compartilhados com certos terceiros, consulte os seguintes artigos:
- [Dados enviados pelo Intune à Apple](data-intune-sends-to-apple.md)
- [Dados enviados pelo Intune ao Google](data-intune-sends-to-google.md)
- [Dados enviados pela Apple ao Intune](data-apple-sends-to-intune.md)
- [Dados enviados pelo Google ao Intune](data-google-sends-to-intune.md)
- [O data JAMF pro envia ao Intune](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>Compartilhamento de dados System Center Configuration Manager

Microsoft Intune não compartilha nenhum dado com o System Center Configuration Manager. System Center Configuration Manager é um produto local implantado, gerenciado e operado diretamente pelo cliente. Os dados de diagnóstico e de uso coletados pelo Configuration Manager são apenas para melhorar a experiência de instalação, a qualidade e a segurança de versões futuras.

Para saber mais, consulte [dados de diagnóstico e de uso para o SCCM](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). 


## <a name="next-steps"></a>Passos seguintes

Descubra como [Exibir e corrigir](privacy-data-view-correct.md) dados pessoais no Intune.
