---
title: "Resolução de Problemas do Exchange Connector | Microsoft Intune"
description: "Resolução de problemas relacionados com o Intune Exchange Connector."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b16c19c95384655e170c199597dd6bd31afb90d
ms.openlocfilehash: 04ac69a30f6c1d91fe755f9720fbc2adc51745f7


---

# Instalar o Exchange Conector
Este tópico descreve como resolver problemas que possam estar relacionados com o Intune Exchange Connector.

## Passos para verificar a configuração do Connector 

Verifique a configuração do Exchange Connector e, em seguida, veja se o problema foi resolvido.

- Certifique-se de que especifica uma conta de notificação na configuração inicial do Exchange Connector.
- A conta de serviço de Exchange Connector deve ter as permissões adequadas para executar os cmdlets do PowerShell utilizados pelo Exchange Connector.
- Quando configurar o Exchange Connector, especifique um Servidor de Acesso de Cliente (CAS) que seja mais o parecido possível com o servidor que aloja o Exchange Connector. A latência de comunicação entre os CAS e o Exchange Connector pode resultar em atrasos de deteção de dispositivo, especialmente ao utilizar o Office 365 dedicado.
- Tenha em atenção de que existe um desfasamento de tempo entre as sincronizações do Exchange Connector com as do Exchange CAS. Uma sincronização completa é realizada uma vez ao dia e uma sincronização (rápida) delta a cada duas horas. Existe uma probabilidade de que um utilizador com um dispositivo inscrito recentemente um experiencie um atraso na obtenção de acesso.
- 
## Dispositivo do Exchange ActiveSync não detetado a partir do Exchange
Verifique se o Exchange Connector está a sincronizar com o servidor Exchange . Para tal, localize os registos para uma sincronização completa ou uma sincronização delta. Ver Registos do Exchange Connector. Se uma sincronização completa ou uma sincronização tiver sido concluída com êxito uma vez que o dispositivo esteja associado, isto foi eliminado como origem do problema. Se não tiver sido efetuada uma sincronização, recolha os registos de sincronização e anexe-os ao pedido de suporte.

- Se um utilizador não tiver uma licença do Intune, o Exchange Connector não irá detetar os respetivos dispositivos.
- Se o endereço SMTP Principal de um utilizador for diferente do respetivo UPN no AAD, o Exchange Connector não detetará quaisquer dispositivos para o utilizador do Intune/AAD. Corrigir o endereço SMTP principal.
- Se o CAS com o que o Exchange Connector comunica durante um ciclo de deteção for um CAS do Exchange 2010 e tiver tanto os servidores de caixa de correio do Exchange 2010 e 2013, o Exchange Conector não irá detetar os dispositivos dos utilizadores no Exchange 2013. Para resolver este problema, configure o Exchange Connector para apontar para um CAS do Exchange 2013.  Apesar deste problema preocupar principalmente as topologias dedicada ao O365, como melhor prática, recomendamos apontar para um CAS do Exchange 2013 nas outras topologias.
- Para ambientes dedicados ao Exchange (O365 dedicado), deve apontar o Exchange Connector para uma CAS do Exchange 2013 (não do 2010) no ambiente dedicado durante a configuração inicial, já que apenas irá comunicar com este CAS ao executar os cmdlets do Powershell.


## Utilizar o Powershell para obter mais dados sobre problemas do Exchange Connector
- Para obter uma lista de todos os dispositivos móveis para uma caixa de correio utilize Get-ActiveSyncDeviceStatistics -mailbox mbx
- Para obter uma lista de endereços SMTP para uma caixa de correio utilize Obter caixa de correio -Utilizador de identidade | selecione emailaddresses | fl.
- Para obter informações detalhadas acerca do estado de acesso a um dispositivo utilize Get-CASMailbox <upn> | fl

### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Aug16_HO1-->

