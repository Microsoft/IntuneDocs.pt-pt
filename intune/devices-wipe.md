---
title: "Utilizar o Intune para remover dados da empresa ou efetuar uma reposição de fábrica em dispositivos"
titleSuffix: Intune on Azure
description: "Saiba como remover dados da empresa ou efetuar uma reposição de fábrica no dispositivo."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 331ced93f0697f7c76d1356aae32b955602d17a3
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/10/2017
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Remover dispositivos através da reposição de fábrica ou da remoção de dados da empresa

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Pode remover do Intune os dispositivos que já não são necessários, que estão a ser reobjetivados ou que estão em falta. Pode fazê-lo ao emitir um comando **remover dados da empresa** ou **reposição de fábrica**. Os utilizadores também podem emitir um comando remoto a partir do Portal da Empresa do Intune para dispositivos pessoais inscritos no Intune.

> [!NOTE]
> Antes de remover um utilizador do Azure Active Directory, emita um comando **Reposição de fábrica** ou **Remover dados da empresa** para todos os dispositivos associados a esse utilizador. Se remover utilizadores com dispositivos geridos a partir do Azure Active Directory, o Intune deixará de conseguir efetuar reposições de fábrica ou remoções de dados da empresa nesses dispositivos.

## <a name="factory-reset"></a>Reposição de fábrica

A **Reposição de fábrica** restaura as predefinições do dispositivo, removendo todos os dados e definições da empresa e do utilizador. O dispositivo é removido da gestão do Intune. A reposição de fábrica é útil para repor um dispositivo antes de o atribuir a um novo utilizador ou em caso de perda ou roubo do dispositivo. Tenha atenção ao selecionar a reposição de fábrica. Não é possível recuperar os dados no dispositivo.

### <a name="to-factory-reset-a-device"></a>Para efetuar uma reposição de fábrica num dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
4. Selecione o nome do dispositivo em que pretende efetuar a reposição de fábrica.
5. No painel que apresenta o nome do dispositivo, selecione **Reposição de fábrica** e, em seguida, selecione **Sim** para confirmar.

Se o dispositivo estiver ativo e ligado, demora menos de 15 minutos até um comando de reposição de fábrica ser propagado em todos os tipos de dispositivo.

## <a name="remove-company-data"></a>Remover dados da empresa

O comando **remover dados da empresa** remove os dados de aplicações geridas (quando aplicável), definições e perfis de e-mail atribuídos através do Intune. A remoção dos dados da empresa mantém os dados pessoais do utilizador no dispositivo. O dispositivo é removido da gestão do Intune. As seguintes tabelas descrevem os dados que são removidos e o efeito nos dados que permanecem no dispositivo após uma remoção dos dados da empresa.

### <a name="ios"></a>iOS

|Tipo de dados|iOS|
|-------------|-------|
|Aplicações da empresa e dados associados instalados pelo Intune|As aplicações são desinstaladas. Os dados da aplicação da empresa são removidos.<br /><br />Os dados de aplicações da Microsoft que utilizam a gestão de aplicações móveis são removidos. A aplicação não é removida.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|
|Definições de perfil de certificado|Os certificados são removidos e revogados.|
|Agente de Gestão|O perfil de gestão é removido.|
|E-mail|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|
|Outlook|Os e-mails recebidos pela aplicação Microsoft Outlook para iOS são removidos.|
|Anulação da associação ao Azure Active Directory (AAD)|O registo do Azure AD é removido.|
|Contactos | Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível remover contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.

### <a name="android"></a>Android

|Tipo de dados|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|Ligações Web|Removidos.|Removidos.|
|Aplicações não geridas do Google Play|As aplicações e os dados permanecem instalados.|As aplicações e os dados permanecem instalados.|
|Aplicações de linha de negócio não geridas|As aplicações e os dados permanecem instalados.|As aplicações são desinstaladas e, como resultado, os dados locais da aplicação são removidos. Não são removidos dados fora da aplicação (por exemplo, num cartão SD).|
|Aplicações geridas do Google Play|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados, mas não são removidos.|
|Aplicações de linha empresarial geridas|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|
|Definições de perfil de certificado|Certificados revogados mas não removidos.|Certificados removidos e revogados.|
|Agente de Gestão|O privilégio de Administrador de Dispositivos é revogado.|O privilégio de Administrador de Dispositivos é revogado.|
|E-mail|N/D (os perfis de e-mail não são suportados por dispositivos Android)|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|
|Outlook|Os e-mails recebidos pela aplicação Microsoft Outlook para Android são removidos.|Os e-mails recebidos pela aplicação Microsoft Outlook para Android são removidos.|
|Anulação da associação ao Azure Active Directory (AAD)|O Registo do Azure AD é removido.|O Registo do Azure AD é removido.|
|Contactos | Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível remover contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.|Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível remover contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.

### <a name="android-for-work"></a>Android for Work

Uma remoção dos dados da empresa num dispositivo Android for Work remove todos os dados, aplicações e definições no perfil de trabalho nesse dispositivo. Esta ação extingue o dispositivo da gestão com o Intune. A reposição de fábrica não é suportada para Android for Work.

### <a name="windows"></a>Windows

|Tipo de dados|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicações da empresa e dados associados instalados pelo Intune|Os ficheiros protegidos pelo EFS terão as respetivas chaves revogadas e o utilizador não poderá abrir os ficheiros.|Não remove aplicações da empresa.|As aplicações instaladas originalmente através do portal da empresa são desinstaladas. Os dados da aplicação da empresa são removidos.|As aplicações são desinstaladas e as chaves de sideload são removidas.<br>Na versão 1703 do Windows 10 (Atualização para Criativos) e posterior, as aplicações do Office 365 ProPlus não são removidas.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|Não suportada.|Removidos.|
|Definições de perfil de certificado|Certificados removidos e revogados.|Certificados removidos e revogados.|Não suportada.|Certificados removidos e revogados.|
|E-mail|Remove o e-mail que tenha o EFS ativado, que inclui a aplicação Correio para e-mail e anexos do Windows.|Não suportada.|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|Remove o e-mail que tenha o EFS ativado, que inclui a aplicação Correio para e-mail e anexos do Windows. Remove as contas de e-mail que tenham sido aprovisionadas pelo Intune.|
|Anulação da associação ao Azure Active Directory (AAD)|Não.|Não.|O Registo do Azure AD é removido.|Não aplicável. O Windows 10 não suporta a remoção de dados da empresa para dispositivos associados ao Azure Active Directory.|

### <a name="to-remove-company-data"></a>Para remover dados da empresa

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
4. Selecione o nome do dispositivo do qual pretende remover os dados da empresa.
5. No painel que apresenta o nome do dispositivo, selecione **Remover dados da empresa** e, em seguida, selecione **Sim** para confirmar.

Se o dispositivo estiver ativo e ligado, demora menos de 15 minutos até um comando de remoção de dados ser propagado em todos os tipos de dispositivo.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminar dispositivos do portal do Azure Active Directory

Devido a problemas de comunicação ou dispositivos em falta, poderá ter de eliminar dispositivos do Azure Active Directory (AAD). O comando eliminar não remove um dispositivo da gestão. No entanto, pode utilizar o comando **Eliminar** para remover registos de dispositivos da consola do Azure que saiba que são inacessíveis e pouco prováveis de voltar a comunicar com o Azure.

1.  Inicie sessão no [Azure Active Directory no portal do Azure](http://aka.ms/accessaad) com as suas credenciais de administrador. Também pode iniciar sessão no [portal do Office 365](https://portal.office.com) e, em seguida, selecionar **Administrador** &gt; **Azure AD** através da ligação no lado esquerdo da página.
3.  Se não tiver uma, crie uma Subscrição do Azure. Se tiver uma conta paga (escolha a ligação de subscrição **Registar o Azure Active Directory gratuito**), não deverá ser preciso um cartão de crédito ou um pagamento para esta subscrição.
4.  Selecione **Active Directory** e, em seguida, selecione a sua organização.
5.  Selecione o separador **Utilizadores** .
6.  Selecione o utilizador cujos dispositivos pretende eliminar.
7.  Escolha **Dispositivos**.
8.  Remova os dispositivos conforme adequado, como aqueles que já não estão em utilização ou que têm definições incorretas.
