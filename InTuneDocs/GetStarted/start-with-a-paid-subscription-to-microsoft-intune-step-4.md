---
# required metadata

title: Gerir licenças do Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gerir licenças do Intune
Antes de os utilizadores poderem iniciar sessão para utilizar o serviço ou inscrever os dispositivos para gestão, têm de ter uma licença para a subscrição do Intune. Quando têm uma licença, os utilizadores passam a ser membros do grupo de utilizadores do [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]. Esse grupo inclui todos os utilizadores com uma licença para usar a subscrição. Cada licença de utilizador suporta a inscrição até 5 dispositivos

## Como são atribuídas as licenças do Intune
Quando as contas de utilizador são sincronizadas a partir do Active Directory no local ou adicionadas manualmente à subscrição de serviços na nuvem através do portal de contas, não lhes é atribuída automaticamente uma licença do Intune. Em vez disso, posteriormente, um administrador inquilino do Intune tem de editar a conta de utilizador para atribuir uma licença ao utilizador a partir do portal de contas.

Quando a sua subscrição partilha o Azure AD com outros serviços na nuvem associados à subscrição, também tem acesso aos utilizadores que foram adicionados a esses serviços. Estes utilizadores não possuem uma licença para o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] até que a atribua a cada um deles.

> [!TIP]
> Se a opção de atribuir ou revogar uma licença do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] estiver desativada, a subscrição pode incluir opções de licenciamento em volume, como as que estão disponíveis ao utilizar o [Enterprise Mobility Suite](https://www.microsoft.com/en-us/server-cloud/enterprise-mobility/overview.aspx). Para obter informações sobre como atribuir ou revogar licenças, consulte a documentação das opções de licenciamento.

## Atribuir uma licença de utilizador do Intune

Utiliza o **[!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]** para adicionar manualmente utilizadores baseados na nuvem e atribuir licenças às contas de utilizador baseadas na nuvem e às contas sincronizadas a partir do Active Directory no local para o Azure AD.

1.  Inicie sessão no portal de contas do Intune com as suas credenciais de administrador inquilino.

2.  Selecione a conta de utilizador à qual pretende atribuir uma licença de utilizador do Intune e ative a caixa de verificação **Microsoft Intune** nas propriedades da conta de utilizador.

3.  A conta de utilizador será agora adicionada ao grupo de utilizadores do Microsoft Intune que atribui as permissões de utilizador para utilizar o serviço e inscrever os respetivos dispositivos para gestão.

### Utilizar o PowerShell para gerir seletivamente licenças de utilizador do EMS
As organizações que utilizam o Enterprise Mobility Suite (EMS) da Microsoft podem ter utilizadores que apenas necessitam do Azure Active Directory Premium ou dos serviços do Intune no pacote EMS. Pode atribuir um ou um subconjunto de serviços utilizando [cmdlets do PowerShell do Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx) 

Para atribuir seletivamente licenças de utilizador para serviços do EMS, abra o PowerShell como administrador num computador com o [Módulo Azure Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) instalado. Pode instalar o PowerShell num computador local ou num servidor do ADFS.

Tem de criar uma nova definição de SKU de licença que se aplique apenas aos planos de serviço pretendidos. Para tal, desative os planos que não pretende aplicar. Por exemplo, pode criar uma definição de SKU de licença que não atribua uma licença do Intune. Para ver uma lista dos serviços disponíveis, escreva:
 
    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus 

Pode executar o comando seguinte para excluir o plano de serviço do Intune. Pode utilizar o mesmo método para expandir para um grupo de segurança completo ou pode utilizar filtros mais granulares. 

Exemplo 1

    Connect-MsolService 
        
    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS 
    

Criar um novo utilizador na linha de comandos e atribuir uma licença de EMS sem ativar a parte do Intune da licença:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

Verificar com:

    Connect-MsolService 
    
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
 
Exemplo 2
 
    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![Desativar a parte do Intune da licença de EMS para um utilizador a quem já foi atribuída uma licença:](./media/posh-addlic-verify.png)

### Verificar com:
PoSH-AddLic-Verify Passos seguintes
>Parabéns!

>Acabou de concluir o passo 4 do *Guia de introdução do Intune*  


<!--HONumber=May16_HO2-->


