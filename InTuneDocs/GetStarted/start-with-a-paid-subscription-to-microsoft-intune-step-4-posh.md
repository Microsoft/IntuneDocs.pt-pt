---
title: "Gerir licenças do Intune através do PowerShell | Microsoft Intune"
description: "Gerir licenças do Intune através do PowerShell"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: aac4e230c3670cf27c57b063afac12b604abf53c


---

# Gerir licenças do Intune através do PowerShell
Antes de os utilizadores poderem iniciar sessão para utilizar o serviço do Intune ou inscreverem os respetivos dispositivos para gestão, tem primeiro de atribuir a cada utilizador uma licença para a sua subscrição do Intune, conforme descrito em [Gerir licenças do Intune](start-with-a-paid-subscription-to-microsoft-intune-step-4.md). Contudo, as organizações que utilizam o Enterprise Mobility Suite (EMS) da Microsoft podem ter utilizadores que apenas necessitem do Azure Active Directory Premium ou dos serviços do Intune no pacote EMS. Pode atribuir um ou um subconjunto de serviços através dos [cmdlets do PowerShell do Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Para atribuir seletivamente licenças de utilizador para serviços do EMS, abra o PowerShell como administrador num computador com o [Módulo Azure Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) instalado. Pode instalar o PowerShell num computador local ou num servidor do ADFS.

Tem de criar uma nova definição de SKU de licença que se aplique apenas aos planos de serviço pretendidos. Para tal, desative os planos que não pretende aplicar. Por exemplo, pode criar uma definição de SKU de licença que não atribua uma licença do Intune. Para ver uma lista dos serviços disponíveis, escreva:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Pode executar o comando seguinte para excluir o plano de serviço do Intune. Pode utilizar o mesmo método para expandir para um grupo de segurança completo ou pode utilizar filtros mais granulares.

**Exemplo 1** Crie um novo utilizador na linha de comandos e atribua uma licença de EMS sem ativar a parte do Intune da licença:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Verificar com:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Exemplo 2** Desative a parte do Intune da licença de EMS para um utilizador a quem já foi atribuída uma licença:

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

Verificar com:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### Passos seguintes
Parabéns! Acabou de concluir o passo 4 do *Guia de introdução do Intune*.
>[!div class="step-by-step"]

>[&larr; **Sincronizar utilizadores com o Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Organizar utilizadores e dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Jul16_HO4-->


