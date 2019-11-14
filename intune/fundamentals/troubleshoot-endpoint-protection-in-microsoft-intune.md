---
title: Mensagens comuns do Endpoint Protection no Microsoft Intune-Azure | Microsoft Docs
description: Consulte mensagens comuns e a solução possível ao usar e solucionar problemas do Endpoint Protection e do Microsoft defender no Microsoft Intune.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 819586a923f5c0f3a81a6d59c4a3895898182f6b
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059162"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problemas do Endpoint Protection e soluções possíveis no Microsoft Intune

Este artigo lista e descreve as possíveis causas e soluções para alguns erros e avisos. Use as informações para ajudar a resolver problemas ao usar o Endpoint Protection.

## <a name="microsoft-defender-error-codes"></a>Códigos de erro do Microsoft defender

Examine os logs de eventos e os códigos de erro para [solucionar problemas com o Microsoft defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Erros comuns do Intune e possíveis resoluções

### <a name="endpoint-protection-engine-unavailable"></a>Motor do Endpoint Protection indisponível

**Causa potencial**: o mecanismo do Endpoint Protection do Intune foi corrompido ou excluído.

**Soluções possíveis**:

- Se o Endpoint Protection estiver corrompido ou não for atualizado, atualize ou reinstale o programa.
- Forçar uma atualização imediata. No programa cliente do Endpoint Protection (possivelmente na barra de tarefas), escolha **Atualizar**.
- No painel de controle > programas, selecione **Microsoft Intune Endpoint Protection agente**. Desinstale o aplicativo.
- Durante a próxima sincronização de atualizações, o Gestor de Atualizações do Microsoft Online Management deteta o programa em falta e reinstala-o na hora de instalação agendada.

### <a name="features-are-disabled"></a>Os recursos estão desabilitados

Você pode receber uma mensagem informando que alguns recursos estão desabilitados. Essas mensagens podem acontecer se o Intune Endpoint Protection ou o Microsoft defender for desabilitado por um administrador usando um perfil de configuração. Ou, ele é desabilitado por um usuário final no dispositivo. Mensagens possíveis:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Soluções possíveis**: habilite esses recursos. Para obter diretrizes, consulte:

- [Adicionar configurações do Endpoint Protection](../protect/endpoint-protection-configure.md)
- [Microsoft defender antivírus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [Usuários finais: Ative a proteção em tempo real para acessar os recursos da empresa](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>Definições de software maligno desatualizadas

Esse status mostra quando as definições de malware no dispositivo estão desatualizadas em 14 dias ou mais. Por exemplo, a mensagem pode mostrar se o dispositivo está desconectado da Internet ou se as definições de malware estão desatualizadas.

**Soluções possíveis**: se as definições de malware estiverem desatualizadas, atualize as definições usando o [Microsoft defender antivírus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Verificação completa vencida ou verificação rápida vencida

Uma verificação completa ou verificação rápida não foi concluída por 14 dias. Esse cenário pode acontecer se o dispositivo for reiniciado durante uma verificação completa.

**Soluções possíveis**: se uma verificação estiver atrasada, você poderá executar uma verificação única ou agendar verificações recorrentes. Consulte [Microsoft defender antivírus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>Outra aplicação de Endpoint Protection em execução

Outro aplicativo de proteção de ponto de extremidade está em execução e o dispositivo está íntegro.

**Soluções possíveis**: se outro aplicativo de proteção de ponto de extremidade estiver instalado e o Intune detectar esse aplicativo, o dispositivo poderá ficar instável.

## <a name="next-steps"></a>Próximos passos

Obtenha [ajuda de suporte da Microsoft](get-support.md)ou use os [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
