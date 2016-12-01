<<<<<<< HEAD
---
title: "Gerir licenças do Intune através do PowerShell | Microsoft Intune"
description: "Gerir licenças do Intune através do PowerShell"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8f99159079002b9e44dd1ba328b0f2fc079770d8
ms.openlocfilehash: 9a3e28cad00f99035b18182a33c24bcb714cca19

||||||| merged common ancestors
---
title: "Gerir licenças do Intune através do PowerShell | Microsoft Intune"
description: "Gerir licenças do Intune através do PowerShell"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8f99159079002b9e44dd1ba328b0f2fc079770d8
ms.openlocfilehash: 9a3e28cad00f99035b18182a33c24bcb714cca19

=======
---
title: "Gerir licenças do Intune através do PowerShell | Microsoft Intune"
description: "Gerir licenças do Intune através do PowerShell"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 8f0786bc821c4a93e5f1ff4bf3d693dd6d59ca8e

>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

---
<<<<<<< HEAD

# Gerir licenças do Intune através do PowerShell
||||||| merged common ancestors

# Gerir licenças do Intune através do PowerShell
=======

# <a name="manage-intune-licenses-using-powershell"></a>Gerir licenças do Intune através do PowerShell
>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2
Antes de os utilizadores poderem iniciar sessão para utilizar o serviço do Intune ou inscreverem os respetivos dispositivos para gestão, tem primeiro de atribuir a cada utilizador uma licença para a sua subscrição do Intune, conforme descrito em [Gerir licenças do Intune](start-with-a-paid-subscription-to-microsoft-intune-step-4.md). Contudo, as organizações que utilizam o Microsoft Enterprise Mobility + Security podem ter utilizadores que apenas necessitam do Azure Active Directory Premium ou dos serviços do Intune no pacote EMS. Pode atribuir um ou um subconjunto de serviços através dos [cmdlets do PowerShell do Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

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

### <a name="next-steps"></a>Passos seguintes
Parabéns! Acabou de concluir o passo 4 do *Guia de introdução do Intune*.
>[!div class="step-by-step"]

>[&larr; **Sincronizar utilizadores com o Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Organizar utilizadores e dispositivos** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Nov16_HO4-->


