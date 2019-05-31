---
title: Resolver problemas de atualizações de software no Microsoft Intune – Azure | Documentos da Microsoft
description: Resolva problemas de atualizações de software no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee5ed6339efff4b3e32a9c10ac756d7f8bec6260
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402623"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Resolver problemas de atualizações de software no Microsoft Intune

Ajudar a resolver problemas de atualizações de software no Microsoft Intune. Para ver uma lista dos códigos de erro e descrições, aceda a [códigos de erro do Software update agent no Microsoft Intune](software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>Dispositivos do Windows 7 com muitas atualizações substituídas stop, geração de relatórios para o Intune

Os clientes do Microsoft Intune podem ter um ou mais dos sintomas seguintes:

- Dispositivos, de repente, pare de reportar para o Intune.  
- Dispositivos experiência de alta utilização da CPU.
- Aplicações são instaladas lentamente quando instalado através do Intune.
- O Microsoft Intune Center mostra o seguinte erro: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- A consola de administração do Intune > grupos > todos os dispositivos > estado mostra: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Este problema pode ocorrer se tiver sido substituída atualizações (atualizações são substituídas por outra atualização) ainda não foram recusadas durante um período prolongado. Durante determinados processos, como instalar um aplicativo, o Windows verifica que todas as atualizações substituídas em sequência, para que as atualizações e as respetivas sucessoras são mapeadas corretamente. Se a lista de atualizações substituídas ficar demasiado grande, esta tarefa de verificação pode causar a alta utilização da CPU devido a carga de processamento e o tempo necessário. Este problema afeta principalmente dispositivos do Windows 7 devido ao elevado número de atualizações substituídas que estão disponíveis para o Windows 7. Sistemas operativos mais recentes podem não ter tantas atualizações substituídas disponíveis e não pode ser suscetíveis a este problema.

**Resolução**

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **atualizações de Software**.
3. Rejeitar todas as atualizações substituídas que poderão aplicar-se para o Windows 7 ou às aplicações, como o Microsoft Office, que foram instaladas nos clientes afetados.
4. Reinicie os clientes afetados.

Se estiver a executar o Windows 7, certifique-se de que a seguinte atualização é instalada:[3050265 Windows atualizar o cliente para Windows 7: Junho de 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>Passos Seguintes

Obtenha [suportam a ajuda da Microsoft](get-support.md), ou utilize o [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).