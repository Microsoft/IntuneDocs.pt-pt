---
title: Resolução de problemas do conector do Exchange
description: Resolução de problemas relacionados com o conector do Exchange no local do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 54e014adbdea3330028be0455fdcf7bd1ade6586
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231343"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Resolução de problemas do conector do Exchange no local do Intune

Este artigo descreve como resolver problemas relacionados com o conector do Exchange no local do Intune.

## <a name="steps-for-checking-the-connector-configuration"></a>Passos para verificar a configuração do conector 

Verifique a [configuração do conector do Exchange no local do Intune](exchange-connector-install.md) para se certificar de que o conector está corretamente configurado. Abaixo estão descritos alguns problemas comuns. Após fazer as correções necessárias, veja se o problema ficou resolvido.

 - Na caixa de diálogo do Microsoft Intune Exchange Connector, certifique-se de que especificou uma conta de utilizador com as permissões adequadas para executar os [cmdlets do Windows PowerShell Exchange necessários](exchange-connector-install.md#exchange-cmdlet-requirements).
- Ative as notificações e especifique uma conta de notificação.
 - Quando configurar o Exchange Connector, especifique um Servidor de Acesso de Cliente (CAS) que seja o mais parecido possível com o servidor que aloja o conector do Exchange. A latência de comunicação entre os CAS e o conector do Exchange pode resultar em atrasos de deteção de dispositivo, especialmente ao utilizar o Exchange Online Dedicado.
 - Um utilizador com um dispositivo inscrito recentemente pode sofrer um atraso na obtenção de acesso até que o conector do Exchange sincronize com o CAS do Exchange. Uma sincronização completa é realizada uma vez ao dia e uma sincronização (rápida) delta ocorre várias vezes ao dia.  Pode [forçar manualmente uma sincronização rápida ou uma sincronização completa](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) para minimizar atrasos.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Dispositivo do Exchange ActiveSync não detetado a partir do Exchange
[Monitorize a atividade do conector do Exchange](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) para ver se o conector do Exchange está a sincronizar com o servidor Exchange. Se uma sincronização rápida ou uma sincronização completa foi concluída com êxito desde que o dispositivo foi associado, pode verificar a existência de outros possíveis problemas, que se encontram listados abaixo. Se não tiver sido efetuada uma sincronização, recolha os registos de sincronização e anexe-os a um pedido de suporte.

 - Se um utilizador não tiver uma licença do Intune, o conector do Exchange não irá detetar os respetivos dispositivos.
 - Se o endereço SMTP principal de um utilizador for diferente do respetivo UPN no Azure Active Directory (Azure AD), o Exchange Connector não detetará dispositivos para esse utilizador. Corrija o endereço SMTP principal para resolver o problema.
 - Se tiver servidores de caixa de correio do Exchange 2010 e do Exchange 2013 no seu ambiente, recomendamos apontar o conector do Exchange para um CAS do Exchange 2013. Caso contrário, se o conector do Exchange estiver configurado para comunicar com um CAS do Exchange 2010, o conector do Exchange não irá detetar os dispositivos dos utilizadores do Exchange 2013. 
- Para ambientes do Exchange Online Dedicado, tem de apontar o conector do Exchange para um CAS do Exchange 2013 (não um CAS do Exchange 2010) no ambiente dedicado durante a configuração inicial, já que o conector só irá comunicar com este CAS ao executar os cmdlets do Powershell.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Utilizar o Powershell para obter mais dados sobre problemas do Exchange Connector
- Para obter uma lista de todos os dispositivos móveis para uma caixa de correio, utilize Get-ActiveSyncDeviceStatistics -mailbox mbx
- Para obter uma lista de endereços SMTP para uma caixa de correio, utilize Get-Mailbox -Identity user | select emailaddresses | fl
- Para obter informações detalhadas acerca do estado de acesso de um dispositivo, utilize Get-CASMailbox <upn> | fl

### <a name="next-steps"></a>Próximos passos
Se estas informações não o ajudarem, também pode [obter suporte para o Microsoft Intune](get-support.md).
