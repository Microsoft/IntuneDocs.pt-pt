---
title: Solucionar problemas de atualizações de software no Microsoft Intune-Azure | Microsoft Docs
description: Resolva problemas de atualizações de software no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ad8d904f72df169eea136c625a2f44d645cafbc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509769"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Resolver problemas de atualizações de software no Microsoft Intune

Ajudar a solucionar problemas de atualização de software no Microsoft Intune. Para ver uma lista de códigos de erro e descrições, vá para [códigos de erro do agente de atualização de software em Microsoft Intune](../protect/software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>Dispositivos Windows 7 com muitas atualizações substituídas param de relatar para o Intune

Microsoft Intune clientes podem apresentar um ou mais dos seguintes sintomas:

- Os dispositivos param repentinamente os relatórios no Intune.  
- Os dispositivos experimentam alta utilização da CPU.
- Os aplicativos são instalados lentamente quando instalados por meio do Intune.
- O Microsoft Intune Center mostra o seguinte erro: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- O console de administração do Intune > grupos > todos os dispositivos > status mostra: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Esse problema pode ocorrer se atualizações substituídas (atualizações são substituídas por outra atualização) não foram recusadas por um período estendido. Durante determinados processos, como a instalação de um aplicativo, o Windows verifica todas as atualizações substituídas em sequência para que as atualizações e seus sucessores sejam mapeados corretamente. Se a lista de atualizações substituídas ficar muito grande, essa tarefa de verificação poderá causar alta utilização da CPU devido à carga de processamento e ao tempo necessário. Esse problema afeta principalmente os dispositivos Windows 7 devido ao grande número de atualizações substituídas que estão disponíveis para o Windows 7. Sistemas operacionais mais recentes podem não ter tantas atualizações substituídas disponíveis e podem não estar suscetíveis a esse problema.

**Resolução**

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **atualizações de software**.
3. Recusar todas as atualizações substituídas que podem se aplicar ao Windows 7 ou a aplicativos, como Microsoft Office, que foram instalados nos clientes afetados.
4. Reinicie os clientes afetados.

Se você estiver executando o Windows 7, verifique se a seguinte atualização está instalada:[3050265 Windows Update Client para Windows 7: junho de 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>Próximos passos

Obtenha [ajuda de suporte da Microsoft](get-support.md)ou use os [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).