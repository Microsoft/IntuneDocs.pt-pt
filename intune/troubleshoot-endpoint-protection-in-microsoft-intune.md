---
title: Mensagens de proteção de ponto final comum no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver mensagens comuns e solução possível quando a utilizar e resolução de problemas de proteção de ponto final e o Windows Defender no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4f749ab85d283ed9743d227476f8229dc1cf7c3
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402650"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problemas do Endpoint protection e as possíveis soluções no Microsoft Intune

Este artigo apresenta e descreve possíveis causas e soluções para alguns erros e avisos. Utilize as informações para ajudar a resolver problemas quando utilizar o endpoint protection.

## <a name="windows-defender-error-codes"></a>Códigos de erro do Windows Defender

Reveja os registos de eventos e códigos de erro para [resolver problemas com o Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Erros comuns do Intune e as possíveis resoluções

#### <a name="endpoint-protection-engine-unavailable"></a>Motor do Endpoint Protection indisponível

**Causa potencial**: O motor do Intune Endpoint Protection foi danificado ou eliminado.

**Possíveis soluções**:

- Se o endpoint protection está danificado ou não de atualização, em seguida, atualizar ou reinstalar um programa.
- Força uma atualização imediata. No programa cliente de endpoint protection (possivelmente sob a barra de tarefas), escolha **atualização**.
- No painel de controlo > programas, selecione **agente do Endpoint Protection do Microsoft Intune**. Desinstale a aplicação.
- Durante a próxima sincronização de atualizações, o Gestor de Atualizações do Microsoft Online Management deteta o programa em falta e reinstala-o na hora de instalação agendada.

#### <a name="features-are-disabled"></a>Funcionalidades são desativadas

Poderá receber uma mensagem que algumas funcionalidades estão desativadas. Essas mensagens podem acontecer se o endpoint protection do Intune ou o Windows Defender está desabilitado por um administrador através de um perfil de configuração. Em alternativa, está desativada por um utilizador final no dispositivo. Mensagens de possíveis:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Possíveis soluções**: Ative estas funcionalidades. Para obter orientações, veja:

- [Adicionar definições do endpoint protection](endpoint-protection-configure.md)
- [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus)
- [Utilizadores finais: Ativar a proteção em tempo real para aceder a recursos da empresa em](/intune-user-help/turn-on-defender-windows)

#### <a name="malware-definitions-out-of-date"></a>Definições de software maligno desatualizadas

Este estado é apresentado quando as definições de malware no dispositivo estão Desatualizadas há 14 dias ou mais. Por exemplo, a mensagem pode mostrar se o dispositivo está desligado da Internet ou as definições de malware estão Desatualizadas.

**Possíveis soluções**: Se as definições de software maligno estiverem Desatualizadas, atualizá-las a usando [antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).

#### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Análise completa em atraso ou análise rápida em atraso

Uma análise completa ou uma análise rápida não concluídas nos últimos 14 dias. Este cenário poderá ocorrer se o dispositivo for reiniciado durante uma análise completa.

**Possíveis soluções**: Se tiver uma análise em atraso, pode executar uma única análise ou agendar análises periódicas. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).

#### <a name="another-endpoint-protection-application-running"></a>Outra aplicação de Endpoint Protection em execução

Outra aplicação de endpoint protection está em execução e o dispositivo está em bom estado.

**Possíveis soluções**: Se estiver instalada outra aplicação de proteção de ponto final e o Intune Deteta essa aplicação, o dispositivo pode tornar-se instável.

## <a name="next-steps"></a>Passos Seguintes

Obtenha [suportam a ajuda da Microsoft](get-support.md), ou utilize o [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
