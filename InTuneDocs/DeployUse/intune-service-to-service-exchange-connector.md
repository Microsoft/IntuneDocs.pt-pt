---
title: Configurar o Exchange Connector do Microsoft Intune para o Exchange alojado | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: 6cfc532cba2f53034c4c3ef0c2df3d6c1e6e7841


---

# Configurar o conector de serviços do Intune para o Exchange Online

Utilize estas informações para ligar o serviço Microsoft Intune e Exchange Online alojado pelo Office 365.

## Requisitos para o Conector de serviços
O **Conector de Serviços** suporta apenas o Exchange alojado e não tem requisitos para a infraestrutura no local.

|Requisito|Mais informações|
|---------------|--------------------|
|Exchange alojado configurado e em execução|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autoridade de gestão de dispositivos móveis| [Definir a autoridade de gestão de dispositivos móveis como o Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Versão do Microsoft Exchange|É necessário ter uma subscrição do Office 365 com um inquilino do Exchange Server 2013 ou posterior. Desde que o inquilino seja o Exchange Server 2013 ou posterior, o conector suporta o Exchange Server 2010 nesse mesmo ambiente.|
|Sincronização do Active Directory|Antes de poder utilizar o Conector do Intune, tem de [configurar a sincronização do Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory.|

### Requisitos de cmdlets do Exchange

Tem de criar uma conta de utilizador do Exchange Online utilizada pelo Exchange Connector do Intune. A conta tem de ter permissão para utilizar a consola de administração do Intune e executar os seguintes cmdlets do Exchange do Windows PowerShell necessários:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Configurar o conector de serviços

1. Abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com) com uma conta de utilizador com direitos de administrador do Exchange e permissões para os cmdlets [acima](#exchange-cmdlet-requirements). O Microsoft Intune utiliza o endereço de e-mail do utilizador atualmente com sessão iniciada para configurar a ligação.

2.  No painel de atalhos da área de trabalho, escolha **ADMIN**, aceda a **Gestão de Dispositivos Móveis** > **Microsoft Exchange** > **Configurar Ligação ao Exchange**.
![Página Configurar conector de serviços](../media/intunesa5cservicetoserviceconnector.png)

3.  Na página **Configurar a Ligação ao Exchange**, escolha **Configurar o Conector de Serviços**.


O Conector de Serviços será automaticamente configurado e sincronizado com o seu ambiente do Exchange alojado.

## Validar a sua ligação ao Exchange

Após a configuração com êxito do Exchange Connector, na consola de administração do Intune, escolha a área de trabalho **ADMIN** e aceda a **Gestão de Dispositivos Móveis** > **Microsoft Exchange** e confirme se os detalhes fornecidos são apresentados em **Informações da Ligação ao Exchange**.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.



<!--HONumber=Jun16_HO4-->


