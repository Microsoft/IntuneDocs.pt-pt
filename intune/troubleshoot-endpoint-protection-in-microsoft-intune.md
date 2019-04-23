---
title: Resolver problemas com a proteção de ponto final no Intune – Azure | Microsoft Docs
description: Resolva problemas quando o Endpoint Protection do Microsoft Intune está a ser utilizado.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: troubleshooting
ms.prod: ''
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
ms.openlocfilehash: 8eddf9af16e0218733f1e0445d85ab7e0176ed27
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61504031"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Resolver problemas com o Endpoint Protection no Intune

Utilize as informações para ajudar a resolver problemas ao utilizar a proteção de ponto final. Veja também [Review event logs and error codes to troubleshoot issues with Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus) (Rever registos de eventos e códigos de erro para resolver problemas com o Windows Defender AV).

Se estas informações não o ajudarem, também poderá [obter suporte para o Microsoft Intune](get-support.md).

### <a name="error-messages"></a>Mensagens de erro
Esta secção descreve possíveis causas e soluções para os seguintes erros e avisos.

|Item de estado|Possíveis causas|Possíveis soluções|
|---------------|--------------------|-----------------------|
|**Motor do Endpoint Protection indisponível**|O motor do Intune Endpoint Protection foi danificado ou eliminado.|Se o motor do Endpoint Protection do Intune estiver danificado, pode experimentar atualizar ou reinstalar o software.<br /><br />Para forçar uma atualização imediata, escolha **Atualizar** no software de cliente do Endpoint Protection (que se encontra na barra de tarefas nos computadores geridos).<br /><br />Se não for possível atualizar o motor, tem de reinstalar o motor do Endpoint Protection.<br /><br />Na lista de programas instalados, no Painel de Controlo do computador gerido, localize o **Agente do Endpoint Protection do Microsoft Intune** e, em seguida, desinstale a aplicação.<br /><br />Durante a próxima sincronização de atualizações, o Gestor de Atualizações do Microsoft Online Management deteta o programa em falta e reinstala-o na hora de instalação agendada.|
|**Endpoint Protection desativado**|A proteção de ponto final do Intune foi desativada por um administrador através de um perfil de configuração ou por um utilizador num computador gerido.|Ative a proteção de ponto final. Veja [Adicionar definições de proteção de ponto final no Intune](endpoint-protection-configure.md) ou [Ativar o Windows Defender para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows).|
|**Proteção em tempo real desativada**|A proteção em tempo real foi desativada por um administrador através de um perfil ou por um utilizador num computador gerido.|Ative a proteção de ponto final. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) no Intune ou [Ativar a proteção em tempo real para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows). |
|**Análise de transferências desativada**|A análise de transferências foi desativada por um administrador através de um perfil ou por um utilizador num computador gerido.|Ative a análise. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) no Intune ou [Ativar a proteção em tempo real para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows). |
|**Monitorização da atividade de programas e ficheiros desativada**|A monitorização da atividade de programas e ficheiros foi desativada por um administrador através de um perfil ou por um utilizador num computador gerido.|Ative a atividade dos ficheiros e programas. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) no Intune ou [Ativar a proteção em tempo real para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows). |
|**Monitorização de comportamento desativada**|A monitorização de comportamento foi desativada por um administrador através de um perfil ou por um utilizador num computador gerido.|Ative a monitorização de comportamento. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) no Intune ou [Ativar a proteção em tempo real para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows). |
|**Análise de scripts desativada**|A análise de scripts foi desativada por um administrador através de um perfil ou por um utilizador num computador gerido.|Ative a análise de scripts. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) no Intune ou [Ativar a proteção em tempo real para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows). |
|**Sistema de Inspeção de Rede desativado**|O Sistema de Inspeção de Rede foi desativado por um administrador através de um perfil ou por um utilizador num computador gerido.|Ative o Sistema de Inspeção de Rede (NIS). Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) no Intune ou [Ativar a proteção em tempo real para aceder aos recursos da empresa](/intune-user-help/turn-on-defender-windows). |
|**Definições de software maligno desatualizadas**|O computador pode ter estado desligado da Internet durante um longo período de tempo e as definições de software maligno podem não ter sido atualizadas. Este estado é apresentado quando as definições de software maligno do computador estão desatualizadas há 14 dias ou mais.|Se as definições de malware estiverem desatualizadas, poderá atualizar as definições através do [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Análise completa em atraso**|Não foi concluída nenhuma análise completa nos últimos 14 dias. Esta situação pode ocorrer se o computador for reiniciado durante uma análise completa.|Se uma análise completa estiver em atraso, poderá executar uma análise completa única ou agendar análises completas periódicas. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus). |
|**Análise rápida em atraso**|Não foi concluída nenhuma análise rápida nos últimos 14 dias. Esta situação pode ocorrer se o computador for reiniciado durante uma análise rápida.|Se uma análise rápida estiver em atraso, poderá executar uma análise rápida única ou agendar análises rápidas periódicas. Veja [Antivírus do Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Outra aplicação de Endpoint Protection em execução**|Está a ser executada outra aplicação de Endpoint Protection e o computador está em bom estado de funcionamento.|Por predefinição, se estiver instalada outra aplicação de proteção de ponto final e o Intune detetar essa aplicação, o dispositivo poderá tornar-se instável.|

### <a name="next-steps"></a>Passos Seguintes
Se estas informações não o ajudarem, também poderá [obter suporte para o Microsoft Intune](get-support.md).
