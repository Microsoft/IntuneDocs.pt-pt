---
title: Conector do Exchange para o Exchange Online | Documentos da Microsoft
description: "Ligue o Intune ao serviço do Exchange do Office 365 para suportar a gestão de dispositivos móveis (MDM) do Exchange Active Sync."
keywords: 
author: andredm7
ms.author: andredm
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
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: b322f368637e39da1ab10b41dd724859fb49e1f2


---

# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>Configurar o conector de serviços do Intune para o Exchange Online

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize estas informações para ligar o Microsoft Intune e o Exchange Online ou o novo serviço do Exchange Online Dedicado. Para determinar se o seu ambiente do Exchange Online Dedicado é a versão **nova** ou **legada**, contacte o seu gestor de conta. O Intune apenas suporta uma ligação de conector do Exchange de qualquer tipo por subscrição.

## <a name="service-to-service-connector-requirements"></a>Requisitos do Conector de Serviços
O **Conector de Serviços** suporta apenas o Exchange Online ou o Exchange Online Dedicado e não possui requisitos para infraestruturas no local.

|Requisito|Mais informações|
|---------------|--------------------|
|Exchange Online configurado e em execução|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autoridade de gestão de dispositivos móveis| [Definir o Microsoft Intune como a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Versão do Microsoft Exchange|Exchange Online ou o novo serviço do Exchange Online Dedicado|
|Sincronização do Active Directory|Antes de poder utilizar o Conector do Intune, tem de [configurar a sincronização do Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory.|

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Tem de criar uma conta de utilizador do Exchange Online utilizada pelo Exchange Connector do Intune. A conta tem de ter permissão para utilizar a consola de administração do Intune e para executar os seguintes cmdlets do Windows PowerShell Exchange necessários:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurar o Conector de Serviços

1. Abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com) com uma conta de utilizador que tenha direitos e permissões de administrador do Exchange relativamente aos cmdlets [descritos anteriormente](#exchange-cmdlet-requirements). O Microsoft Intune utiliza o endereço de e-mail do utilizador que tem atualmente sessão iniciada para configurar a ligação.

2.  No painel de atalhos da área de trabalho, selecione **ADMIN (Administrador)**>**Mobile Device Management (Gestão de Dispositivos Móveis)** > **Microsoft Exchange** > **Set Up Exchange Connection (Configurar Ligação do Exchange)**.
![Página Configurar conector de serviços](../media/intunesa5cservicetoserviceconnector.png)

3.  Na página **Set Up Exchange Connection (Configurar a Ligação ao Exchange)**, escolha **Set Up Service to Service Connector (Configurar o Conector de Serviços)**.


O Conector de Serviços configura e sincroniza automaticamente o seu Exchange Online ou o novo ambiente do Exchange Online Dedicado.

## <a name="validate-your-exchange-connection"></a>Validar a sua ligação ao Exchange

Após ter configurado o Conector do Exchange com êxito, aceda à [consola de administração do Microsoft Intune](http://manage.microsoft.com). Selecione **Admin (Administrador)**> **Mobile Device Management (Gestão de Dispositivos Móveis)** > **Microsoft Exchange**. Em seguida, confirme que os detalhes que forneceu são apresentados em **Exchange Connection Information (Informações de Ligação do Exchange)**.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.



<!--HONumber=Dec16_HO2-->


