---
title: Remover dados empresariais em dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Remova dados empresariais num dispositivo ou faça uma reposição de dados de fábrica num dispositivo Android, Android for Work, iOS, macOS ou Windows com o Microsoft Intune. Além disso, elimine um dispositivo do Azure Active Directory.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bb191f33133b85613f491220c970947b9e55b79f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Remover dispositivos através da reposição de fábrica ou da remoção de dados da empresa

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode remover do Intune os dispositivos que já não são necessários, que estão a ser reaproveitados ou que estão em falta. Pode fazê-lo ao utilizar as ações **Remover dados da empresa** ou **Reposição de dados de fábrica**. Os utilizadores também podem emitir um comando remoto a partir do Portal da Empresa do Intune para dispositivos pessoais inscritos no Intune.

> [!NOTE]
> Antes de remover um utilizador do Azure Active Directory (Azure AD), utilize as ações **Reposição de dados de fábrica** ou **Remover dados da empresa** para todos os dispositivos associados a esse utilizador. Se remover utilizadores que têm dispositivos geridos a partir do Azure AD, o Intune deixará de conseguir efetuar uma reposição de dados fábrica ou remoções de dados da empresa nesses dispositivos.

## <a name="factory-reset"></a>Reposição de fábrica

A ação **Reposição de dados de fábrica** restaura um dispositivo para as predefinições de fábrica. Uma reposição de dados de fábrica restaura todos os dados e definições da empresa e do utilizador. O dispositivo é removido da gestão do Intune. Uma reposição de dados de fábrica é útil para repor um dispositivo antes de o atribuir a um novo utilizador ou em caso de perda ou roubo do dispositivo. Tenha atenção ao selecionar a **Reposição de dados de fábrica**. Não é possível recuperar os dados no dispositivo.

### <a name="factory-reset-a-device"></a>Efetuar uma reposição de dados de fábrica num dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Dispositivos** > **Todos os dispositivos**.
4. Selecione o nome do dispositivo em que pretende efetuar a reposição de dados de fábrica.
5. No painel que mostra o nome do dispositivo, selecione **Reposição de dados de fábrica**.
6. Para a versão 1709 ou posterior do Windows 10, também tem a opção **Reter estado de inscrição e conta de utilizador**. 
    
    |Dados retidos durante uma reposição de dados de fábrica|Não retido|
    | -------------|------------|
    |Contas de utilizador associadas ao dispositivo|Ficheiros do utilizador|
    |Estado da máquina \(associação a um domínio, associado ao Azure AD)| Aplicações instaladas pelo utilizador \(aplicações Win32 e da loja)|
    |Inscrição da gestão de dispositivos móveis (MDM)|Definições do dispositivo não predefinidas|
    |Aplicações OEM instaladas \(aplicações Win32 e da loja)||
    |Perfil de utilizador||
    |Dados de utilizador fora do perfil de utilizador||
    |Início de sessão automático de utilizador|| 
    
         
7. Selecione **Sim** para confirmar a reposição de dados de fábrica.

Se o dispositivo estiver ativado e ligado, a ação **Reposição de dados de fábrica** propaga a todos os tipos de dispositivo em menos de 15 minutos.

## <a name="remove-company-data"></a>Remover dados da empresa

A ação **Remover dados da empresa** remove os dados de aplicações geridas (quando aplicável), definições e perfis de e-mail atribuídos através do Intune. A ação **Remover dados da empresa** mantém os dados pessoais do utilizador no dispositivo. O dispositivo é removido da gestão do Intune. 

As seguintes tabelas descrevem os dados que são removidos e o efeito da ação **Remover dados da empresa** nos dados que permanecem no dispositivo após uma remoção dos dados da empresa.

### <a name="ios"></a>iOS

|Tipo de dados|iOS|
|-------------|-------|
|Aplicações da empresa e dados associados instalados pelo Intune|As aplicações são desinstaladas. Os dados da aplicação da empresa são removidos.<br /><br />Os dados de aplicações da Microsoft que utilizam a gestão de aplicações móveis são removidos. A aplicação não é removida.|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|
|Definições de perfil de certificado|Os certificados são removidos e revogados.|
|Agente de gestão|O perfil de gestão é removido.|
|E-mail|Os perfis de e-mail aprovisionados através do Intune são removidos. O e-mail em cache no dispositivo é eliminado.|
|Outlook|Os e-mails recebidos pela aplicação Microsoft Outlook para iOS são removidos. Isto exige que a aplicação móvel do Outlook seja implementada primeiro como uma aplicação Necessária para os utilizadores de iOS.|
|Anulação da associação ao Azure AD|O registo do Azure AD é removido.|
|Contactos |Os contactos sincronizados diretamente da aplicação com o livro de endereços nativo são removidos. Não é possível remover contactos sincronizados do livro de endereços nativo com outra origem externa. <br /> <br />Atualmente, apenas a aplicação Outlook é suportada.

### <a name="android"></a>Android

|Tipo de dados|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Ligações Web|Removidos.|Removidos.|
|Aplicações não geridas do Google Play|As aplicações e os dados permanecem instalados.|As aplicações e os dados permanecem instalados.|
|Aplicações de linha de negócio não geridas|As aplicações e os dados permanecem instalados.|As aplicações são desinstaladas e os dados locais da aplicação são removidos. Não são removidos dados fora da aplicação (por exemplo, num cartão SD).|
|Aplicações geridas do Google Play|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação da Gestão de Aplicações Móveis (MAM) fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados, mas não são removidos.|
|Aplicações de linha de negócios geridas|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|
|Definições de perfil de certificado|Os certificados são revogados, mas não removidos.|Os certificados são removidos e revogados.|
|Agente de gestão|O privilégio de Administrador de Dispositivos é revogado.|O privilégio de Administrador de Dispositivos é revogado.|
|E-mail|N/D (os perfis de e-mail não são suportados por dispositivos Android)|Os perfis de e-mail aprovisionados através do Intune são removidos. O e-mail em cache no dispositivo é eliminado.|
|Outlook|Os e-mails recebidos pela aplicação Outlook para Android são removidos, mas apenas se o Outlook estiver protegido por políticas de MAM. Caso contrário, o Outlook não é apagado se a inscrição do dispositivo for anulada.|Os e-mails recebidos pela aplicação Outlook para Android são removidos, mas apenas se o Outlook estiver protegido por políticas de MAM. Caso contrário, o Outlook não é apagado se a inscrição do dispositivo for anulada.|
|Anulação da associação ao Azure AD|O registo do Azure AD é removido.|O registo do Azure AD é removido.|
|Contactos |Os contactos sincronizados diretamente da aplicação com o livro de endereços nativo são removidos. Não é possível remover contactos sincronizados do livro de endereços nativo com outra origem externa. <br /> <br />Atualmente, apenas a aplicação Outlook é suportada.|Os contactos sincronizados diretamente da aplicação com o livro de endereços nativo são removidos. Não é possível remover contactos sincronizados do livro de endereços nativo com outra origem externa. <br /> <br />Atualmente, apenas a aplicação Outlook é suportada.

### <a name="android-for-work"></a>Android for Work

Uma remoção dos dados da empresa num dispositivo Android for Work remove todos os dados, aplicações e definições no perfil de trabalho nesse dispositivo. A gestão do dispositivo através do Intune é desativada. A reposição de fábrica não é suportada para Android for Work.


### <a name="macos"></a>macOS

|Tipo de dados|macOS|
|-------------|-------|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|
|Definições de perfil de certificado|Os certificados que foram implementados através da MDM são removidos e revogados.|
|Agente de gestão|O perfil de gestão é removido.|
|Outlook|Se o acesso condicional estiver ativado, o dispositivo deixará de receber correio novo.|
|Anulação da associação ao Azure AD|O registo do Azure AD é removido.|

### <a name="windows"></a>Windows

|Tipo de dados|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8.1 e Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicações da empresa e dados associados instalados pelo Intune|As chaves para ficheiros protegidos por EFS são revogadas. O utilizador não consegue abrir os ficheiros.|As aplicações da empresa não são removidas.|As aplicações instaladas originalmente através do Portal da Empresa são desinstaladas. Os dados da aplicação da empresa são removidos.|As aplicações são desinstaladas. As chaves de sideload são removidas.<br>Na versão 1703 do Windows 10 (Atualização para Criativos) e posterior, as aplicações do Office 365 ProPlus não são removidas.|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|Não suportada.|Removidos.|
|Definições de perfil de certificado|Os certificados são removidos e revogados.|Os certificados são removidos e revogados.|Não suportada.|Os certificados são removidos e revogados.|
|E-mail|Remove e-mails com o EFS ativado. Isto inclui e-mails e anexos na aplicação Correio para Windows.|Não suportada.|Os perfis de e-mail aprovisionados através do Intune são removidos. O e-mail em cache no dispositivo é eliminado.|Remove e-mails com o EFS ativado. Isto inclui e-mails e anexos na aplicação Correio para Windows. Remove as contas de e-mail que tenham sido aprovisionadas pelo Intune.|
|Anulação da associação ao Azure AD|Não.|Não.|O registo do Azure AD é removido.|Não aplicável. No Windows 10, não pode remover dados da empresa para dispositivos associados ao Azure AD.|

### <a name="remove-company-data"></a>Remover dados da empresa

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Dispositivos**, selecione **Todos os dispositivos**.
4. Selecione o nome do dispositivo do qual pretende remover os dados da empresa.
5. No painel que mostra o nome do dispositivo, selecione **Remover dados da empresa**. Para confirmar, selecione **Sim**.

Se o dispositivo estiver ativado e ligado, a ação **Remover dados da empresa** propaga a todos os tipos de dispositivo em menos de 15 minutos.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminar dispositivos do portal do Azure Active Directory

Poderá ter de eliminar dispositivos do Azure AD devido a problemas de comunicação ou dispositivos em falta. Pode utilizar a ação **Eliminar** para remover registos de dispositivos do portal do Azure para dispositivos que sabe que são inacessíveis e pouco prováveis de voltar a comunicar com o Azure. A ação **Eliminar** não remove um dispositivo da gestão.

1.  Inicie sessão no [Azure Active Directory no portal do Azure](http://aka.ms/accessaad) com as suas credenciais de administrador. Também pode iniciar sessão no [portal do Office 365](https://portal.office.com). A partir do menu, selecione **Centros de administração** > **Azure AD**.
2.  Se não tiver uma, crie uma Subscrição do Azure. Isto não deve exigir um cartão de crédito ou pagamento se tiver uma conta paga (selecione a ligação de subscrição **Registar o Azure Active Directory gratuito**).
3.  Selecione **Azure Active Directory** e, em seguida, selecione a sua organização.
4.  Selecione o separador **Utilizadores** .
5. Selecione o utilizador associado ao dispositivo que pretende eliminar.
6.  Selecione **Dispositivos**.
7.  Remova os dispositivos conforme adequado. Por exemplo, poderá remover dispositivos que já não estão em utilização ou que têm definições incorretas.
