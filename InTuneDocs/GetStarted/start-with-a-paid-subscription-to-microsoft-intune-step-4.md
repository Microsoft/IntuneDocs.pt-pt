---
title: "Gerir licenças do Intune | Microsoft Intune"
description: "Atribuir licenças a utilizadores na sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 325373a19de96265d3605ef22e633eb60e6be2b3


---

# <a name="manage-intune-licenses"></a>Gerir licenças do Intune
Antes de os utilizadores poderem iniciar sessão para utilizar o serviço do Intune ou inscreverem os respetivos dispositivos para gestão, tem primeiro de atribuir uma licença a cada utilizador para a sua subscrição do Intune ao utilizar o [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

As organizações que utilizam Microsoft Enterprise Mobility + Security (EMS) podem ter utilizadores que apenas necessitam do Azure Active Directory Premium ou dos serviços do Intune no pacote EMS. Pode atribuir um ou um subconjunto de serviços através dos [cmdlets do PowerShell do Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx). Para obter mais informações, consulte [Gerir licenças do Intune através do PowerShell](start-with-a-paid-subscription-to-microsoft-intune-step-4-posh.md).

## <a name="how-intune-licenses-are-assigned"></a>Como são atribuídas as licenças do Intune
Quando as contas de utilizador são sincronizadas a partir do Active Directory no local ou adicionadas manualmente à subscrição de serviços em nuvem através do [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), não lhes é atribuída automaticamente uma licença do Intune. Em vez disso, posteriormente, um administrador inquilino do Intune tem de editar a conta de utilizador para atribuir uma licença ao utilizador a partir do portal do Office 365.

Quando a sua subscrição partilha o Azure AD com outros serviços na nuvem associados à subscrição, também tem acesso aos utilizadores que foram adicionados a esses serviços. Estes utilizadores não possuem uma licença para o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] até que a atribua a cada um deles.

> [!TIP]
> Se a opção de atribuir ou revogar uma licença do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] estiver desativada, a sua subscrição poderá incluir opções de licenciamento em volume, como as que estão disponíveis ao utilizar o [Enterprise Mobility Suite + Security](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx). Para obter informações sobre como atribuir ou revogar licenças, consulte a documentação das opções de licenciamento.

## <a name="assign-an-intune-user-license"></a>Atribuir uma licença de utilizador do Intune

Para adicionar manualmente utilizadores baseados na nuvem e atribuir licenças às contas de utilizador baseadas na nuvem e às contas sincronizadas do Active Directory no local com o Azure AD, é utilizado o [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

1.  Inicie sessão no [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as suas credenciais de administrador inquilino e depois selecione **Pessoas** > **Todos os Utilizadores**.

2.  Selecione a conta de utilizador à qual pretende atribuir uma licença de utilizador do Intune e então selecione ou **Microsoft Intune** (autónome) ou o **Enterprise Mobility Suite**.

3.  A conta de utilizador tem agora as permissões necessárias para utilizar o serviço e inscrever dispositivos para gestão.

> [!NOTE]
> Os utilizadores serão apresentados na consola após terem inscrito um dispositivo.

### <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Utilizar o PowerShell para gerir seletivamente licenças de utilizador do EMS
As organizações que utilizam Microsoft Enterprise Mobility + Security (anteriormente denominado Enterprise Mobility Suite) podem ter utilizadores que apenas necessitam do Azure Active Directory Premium ou dos serviços do Intune no pacote EMS. Pode atribuir um ou um subconjunto de serviços através dos [cmdlets do PowerShell do Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

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


