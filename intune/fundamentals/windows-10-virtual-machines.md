---
title: Usando máquinas virtuais do Windows 10 com Microsoft Intune
titleSuffix: ''
description: Diretrizes para usar máquinas virtuais do Windows 10 com Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afaf2c8a63bfaed1fdb593baf42c8fa258d7893
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74266336"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Usando máquinas virtuais do Windows 10 com o Intune

O Intune dá suporte ao gerenciamento de máquinas virtuais que executam o Windows 10 Enterprise com certas limitações. O gerenciamento do Intune não depende nem interfere no gerenciamento de área de trabalho virtual do Windows da mesma máquina virtual.

Ao gerenciar VMs do Windows 10 com o Intune, tenha em mente os seguintes pontos:

## <a name="enrollment"></a>Inscrição
- Não recomendamos o gerenciamento de máquinas virtuais de host de sessão sob demanda com o Intune. Cada VM deve ser registrada quando for criada. Além disso, a exclusão regular de VMs deixará os registros de dispositivo órfãos no Intune até que eles sejam [limpos](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules). 
- O modo de autoimplantação do Windows AutoPilot não tem suporte porque requer um Trusted Platform Module (TPM). 
- Não há suporte para o registro de OOBE (experiência inicial pelo uso) em VMs que só podem ser acessadas usando o RDP (como as VMs hospedadas no Azure). Essa restrição significa:
    - Não há suporte para o Azure AutoPilot e o OOBE comercial.
    - Não há suporte para as opções de página de status de registro para políticas de contexto de dispositivo.

## <a name="configuration"></a>Configuração
O Intune não oferece suporte a nenhuma configuração que utilize um gerenciamento de Trusted Platform Module ou de hardware, incluindo:
- [Configurações do BitLocker](../configuration/device-profiles.md#endpoint-protection)
- [Configurações de interface de configuração de firmware do dispositivo](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>Relatórios
O Intune detecta automaticamente as máquinas virtuais e as relata como "máquina virtual" em **dispositivos** > **todos os dispositivos** > escolher um dispositivo > **visão geral** > campo de **modelo** . 

As máquinas virtuais desalocadas podem contribuir para relatórios de dispositivos não compatíveis porque não conseguem [fazer check-in com o serviço do Intune](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retirement"></a>Extinção
Se você só tiver acesso RDP, não use a [ação apagar](../remote-actions/devices-wipe.md#wipe). A ação de apagamento excluirá as configurações de RDP da máquina virtual e impedirá que você se conecte novamente.


