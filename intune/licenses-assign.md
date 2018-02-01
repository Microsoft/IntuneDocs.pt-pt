---
title: "Atribuir licenças do Intune"
description: "Atribuir licenças a utilizadores na sua subscrição do Intune"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b0fe556eaf548d51b35c843ee313264244144f9c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="assign-intune-licenses-to-your-user-accounts"></a>Atribuir licenças do Intune às contas de utilizador

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Quer adicione utilizadores manualmente ou sincronize a partir do Active Directory no local, tem primeiro de atribuir a cada utilizador uma licença do Intune antes de os utilizadores poderem inscrever os respetivos dispositivos no Intune.

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>Atribuir uma licença do Intune no Centro de administração do Office 365

Para adicionar manualmente utilizadores baseados na cloud e atribuir licenças às contas de utilizador baseadas na cloud e às contas sincronizadas do Active Directory no local com o Azure AD, pode utilizar o [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

1.  Inicie sessão no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) com as suas credenciais de administrador inquilino e escolha **Utilizadores** > **Utilizadores Ativos**.

2.  Selecione a conta de utilizador à qual pretende atribuir uma licença de utilizador do Intune e, em seguida, escolha **Licenças de produtos** > **Editar**.

3.  Alterne o **Intune** ou o **Enterprise Mobility + Security** para **Ativado** e escolha **Guardar**.

  ![Imagem da página de atribuição de licenças de Produtos no portal do Office 365.](./media/office-assign-license.png)

4. A conta de utilizador tem agora as permissões que são precisas para utilizar o serviço e inscrever os dispositivos para gestão.

> [!NOTE]
> Os utilizadores apenas serão apresentados na Consola de administração após terem inscrito um dispositivo. Além disso, pode selecionar um grupo de utilizadores para editar ao mesmo tempo, ao selecionar para adicionar ou substituir uma licença para todos os utilizadores selecionados.

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Utilizar o School Data Sync para atribuir licenças aos utilizadores do Intune for Education
Se for uma organização de ensino, poderá utilizar o School Data Sync (SDS) para atribuir licenças do Intune for Education aos utilizadores sincronizados. Basta selecionar a caixa de verificação do Intune for Education quando estiver a configurar o perfil SDS.  

![Imagem da definição do perfil SDS](./media/i4e-sds-profile-setup-setting.png)

Quando atribuir uma licença do Intune for Education, confirme se a licença do Intune A Direct também foi atribuída.

![Imagem da configuração da licença do produto](./media/i4e-set-licenses.png)

Veja esta [descrição geral do School Data Sync](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91?ui=en-US&rs=en-US&ad=US) para saber mais sobre o SDS.

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>Como as licenças de utilizadores e dispositivos afetam o acesso aos serviços
* Cada **utilizador** ao qual atribua uma licença de software de utilizador poderá aceder e utilizar os serviços online e o software relacionado (incluindo o software do System Center) para gerir aplicações e até 15 dispositivos.
* Cada **dispositivo** ao qual atribua uma licença de software de dispositivo poderá aceder e utilizar os serviços online e o software relacionado (incluindo o software do System Center) para utilização por qualquer número de utilizadores.
* Caso um dispositivo seja utilizado por mais de um utilizador, cada um requer uma licença de software de dispositivo ou todos os utilizadores requerem uma licença de software de utilizador.

## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Utilizar o PowerShell para gerir seletivamente licenças de utilizador do EMS
As organizações que utilizam Microsoft Enterprise Mobility + Security (anteriormente denominado Enterprise Mobility Suite) podem ter utilizadores que apenas necessitam do Azure Active Directory Premium ou dos serviços do Intune no pacote EMS. Pode atribuir um ou um subconjunto de serviços através dos [cmdlets do PowerShell do Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Para atribuir seletivamente licenças de utilizador para serviços do EMS, abra o PowerShell como administrador num computador com o [Módulo Azure Active Directory para Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) instalado. Pode instalar o PowerShell num computador local ou num servidor do ADFS.

Tem de criar uma nova definição de SKU de licença que se aplique apenas aos planos de serviço pretendidos. Para tal, desative os planos que não pretende aplicar. Por exemplo, pode criar uma definição de SKU de licença que não atribua uma licença do Intune. Para ver uma lista dos serviços disponíveis, escreva:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Pode executar o comando seguinte para excluir o plano de serviço do Intune. Pode utilizar o mesmo método para expandir para um grupo de segurança completo ou pode utilizar filtros mais granulares.

**Exemplo 1**<br>
Criar um novo utilizador na linha de comandos e atribuir uma licença de EMS sem ativar a parte do Intune da licença:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Verificar com:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Exemplo 2**<br>
Desativar a parte do Intune da licença de EMS para um utilizador a quem já foi atribuída uma licença:

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Verificar com:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)
