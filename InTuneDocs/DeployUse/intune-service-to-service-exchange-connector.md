---
title: Conector do Exchange para o Exchange Online | Microsoft Intune
description: "Ligue o Intune ao serviço do Exchange do Office 365 para suportar a gestão de dispositivos móveis (MDM) do Exchange Active Sync."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de3296e81c88b3ac04e3ba3f3d3ca222a59df7bd
ms.openlocfilehash: 1aabf820170483eacc83bec5e2b275e84dc07ffd


---

# Configurar o conector de serviços do Intune para o Exchange Online

Utilize estas informações para ligar o serviço Microsoft Intune e Exchange Online ou o novo serviço Dedicado do Exchange Online. Para determinar se o ambiente dedicado do Exchange Online está como **novo** ou **legado**,  contacte o seu gestor de conta. O Intune apenas suporta uma ligação de conector do Exchange de qualquer tipo por subscrição.

## Requisitos para o Conector de serviços
O **Conector de Serviços** suporta apenas o Exchange Online ou o novo Exchange Online Dedicado e não tem requisitos para a infraestrutura no local.

|Requisito|Mais informações|
|---------------|--------------------|
|Exchange Online configurado e em execução|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autoridade de gestão de dispositivos móveis| [Definir a autoridade de gestão de dispositivos móveis como o Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Versão do Microsoft Exchange|Exchange Online ou o novo serviço Exchange Online Dedicado|
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


O Conector de Serviços será automaticamente configurado e sincronizado com o seu ambiente do Exchange Online ou do Exchange Online Dedicado.

## Validar a sua ligação ao Exchange

Após a configuração com êxito do Exchange Connector, na [consola de administração do Microsoft Intune](http://manage.microsoft.com) escolha **Administração** e aceda a **Gestão de Dispositivo Móveis** > **Microsoft Exchange** e confirme que os detalhes que forneceu aparecem em **Informações de Ligação do Exchange**.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.



<!--HONumber=Jul16_HO5-->


