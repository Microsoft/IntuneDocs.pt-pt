---
title: Extinguir ou apagar dados de dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Retire ou limpe um dispositivo num dispositivo Android, Android, iOS/iPadOS, macOS ou dispositivo Windows utilizando o Microsoft Intune. Além disso, elimine um dispositivo do Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62ba66469dfff004c3cd6a60284ec7466e8b9f00
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415521"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Remover dispositivos ao apagar os dados, extinguir ou anular a inscrição do dispositivo de forma manual

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Ao realizar as ações **Extinguir** ou **Limpar**, pode remover do Intune os dispositivos que já não são necessários, que estão a ser reaproveitados ou que estão em falta. Os utilizadores também podem emitir um comando remoto a partir do Portal da Empresa do Intune para dispositivos inscritos no Intune.

> [!NOTE]
> Antes de remover um utilizador do Azure Active Directory (Azure AD), utilize as ações **Limpar** ou **Extinguir** para todos os dispositivos associados a esse utilizador. Se remover utilizadores que têm dispositivos geridos a partir do Azure AD, o Intune deixará de conseguir apagar os dados ou extinguir esses dispositivos.

## <a name="wipe"></a>Eliminação

A ação **Limpar** restaura um dispositivo para as predefinições de fábrica. Os dados do utilizador são mantidos se selecionar a caixa de verificação **Reter estado de inscrição e conta de utilizador**. Caso contrário, todos os dados, aplicações e configurações serão removidos.

|Ação Limpar|**Reter estado de inscrição e conta de utilizador**|Removido da gestão do Intune|Description|
|:-------------:|:------------:|:------------:|------------|
|**Eliminação**| Opção não selecionada | Sim | Apaga todas as contas, dados, políticas de MDM e definições do utilizador. Repõe as definições e estado predefinidos do sistema operativo.|
|**Eliminação**| Opção selecionada | Não | Apaga todas as políticas de MDM. Mantém os dados e as contas do utilizador. Repõe as definições predefinidas do utilizador. Repõe as definições e estado predefinidos do sistema operativo.|


> [!NOTE]
> A ação Wipe não está disponível para dispositivos iOS/iPadOS matriculados com inscrição no utilizador.

A opção **Reter estado de inscrição e conta de utilizador** só está disponível para a versão 1709 ou posterior do Windows 10.

A opção **'Eliminar'** não pode ser contornada a ação de limpeza não pode ser contornada desligando o dispositivo. Uma limpeza protegida continuará a tentar redefinir o dispositivo até ser bem sucedido. Em algumas configurações, esta ação pode deixar o dispositivo incapaz de reiniciar.

As políticas de MDM voltarão a ser aplicadas da próxima vez que o dispositivo estabelecer ligação ao Intune.

Apagar é útil para repor um dispositivo antes de o atribuir a um novo utilizador ou em caso de perda ou roubo do dispositivo. Tenha cuidado quando selecionar a ação **Limpar**. Não é possível recuperar os dados no dispositivo.

### <a name="wiping-a-device"></a>Limpar um dispositivo

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Dispositivos** > **Todos os dispositivos**.
4. Selecione o nome do dispositivo que pretende apagar.
5. No painel que mostra o nome do dispositivo, selecione **Limpar**.
6. Para a versão 1709 do Windows 10 ou mais tarde, também tem o **dispositivo Wipe, mas mantenha o estado de inscrição e a** opção de conta de utilizador associada. 
    
    |Retido durante uma limpeza |Não retido|
    | -------------|------------|
    |Contas de utilizador associadas ao dispositivo|Ficheiros do utilizador|
    |Estado da máquina \(associação a um domínio, associado ao Azure AD)| Aplicações instaladas pelo utilizador \(aplicações Win32 e da loja)|
    |Inscrição da gestão de dispositivos móveis (MDM)|Definições do dispositivo não predefinidas|
    |Aplicações OEM instaladas \(aplicações Win32 e da loja)||
    |Perfil de utilizador||
    |Dados de utilizador fora do perfil de utilizador||
    |Início de sessão automático de utilizador|| 
    
         
7. Para confirmar a limpeza, selecione **Sim**.

Se o dispositivo estiver ativado e ligado, a ação **Limpar** propaga-se a todos os tipos de dispositivo em menos de 15 minutos.

## <a name="retire"></a>Extinguir

A ação **Extinguir** remove os dados de aplicações geridas (quando aplicável), definições e perfis de e-mail atribuídos através do Intune. O dispositivo é removido da gestão do Intune. Essa extinção ocorrerá na próxima vez que o dispositivo for registado e receber a ação remota **Extinguir**. O dispositivo ainda aparece em Intune até o dispositivo fazer o check-in. Se pretender remover imediatamente os dispositivos velhos, utilize a [ação Eliminar.](devices-wipe.md#delete-devices-from-the-intune-portal)

A ação **Extinguir** mantém os dados pessoais do utilizador no dispositivo.  

As seguintes tabelas descrevem os dados que são removidos e o efeito da ação **Extinguir** nos dados que permanecem no dispositivo após a remoção dos dados da empresa.

### <a name="ios"></a>iOS

|Tipo de dados|iOS|
|-------------|-------|
|Aplicações da empresa e dados associados instalados pelo Intune|**Apps instaladas utilizando o Portal da Empresa:** Para aplicações que estão fixadas no perfil de gestão, todos os dados da aplicação e as aplicações são removidas. Estas aplicações incluem aplicações originalmente instaladas a partir da App Store e posteriormente geridas como aplicações da empresa, a menos que a aplicação esteja configurada para não ser desinstalada na remoção do dispositivo. <br /><br /> **Aplicações da Microsoft que utilizam a gestão de aplicações móveis e foram instaladas a partir da App Store:** Para aplicações que não são geridas pelo Portal da Empresa, os dados de aplicações da empresa que estão protegidos pela encriptação mobile application management (MAM) dentro da aplicação armazenamento local é removido. Os dados protegidos pela encriptação MAM fora da aplicação permanecem encriptados e inutilizáveis, mas não são removidos. As aplicações pessoais e os dados não são removidos.|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|
|Definições de perfil de certificado|Os certificados são removidos e revogados.|
|Agente de gestão|O perfil de gestão é removido.|
|E-mail|Os perfis de e-mail aprovisionados através do Intune são removidos. O e-mail em cache no dispositivo é eliminado.|
|Anulação da associação ao Azure AD|O registo do Azure AD é removido.|

### <a name="android"></a>Android

|Tipo de dados|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Ligações Web|Removidos.|Removidos.|
|Aplicações não geridas do Google Play|As aplicações e os dados permanecem instalados. <br /> <br />São removidos os dados de aplicações da empresa protegidos pela encriptação de Gestão de Aplicações Móveis (MAM) dentro do armazenamento local de aplicações. Os dados protegidos pela encriptação MAM fora da aplicação permanecem encriptados e inutilizáveis, mas não são removidos. |As aplicações e os dados permanecem instalados. <br /> <br />São removidos os dados de aplicações da empresa protegidos pela encriptação de Gestão de Aplicações Móveis (MAM) dentro do armazenamento local de aplicações. Os dados protegidos pela encriptação MAM fora da aplicação permanecem encriptados e inutilizáveis, mas não são removidos.|
|Aplicações de linha de negócio não geridas|As aplicações e os dados permanecem instalados.|As aplicações são desinstaladas e os dados locais da aplicação são removidos. Não são removidos dados fora da aplicação (por exemplo, num cartão SD).|
|Aplicações geridas do Google Play|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação da Gestão de Aplicações Móveis (MAM) fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados, mas não são removidos.|
|Aplicações de linha de negócios geridas|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (por exemplo, cartão SD) permanecem encriptados e inutilizáveis, mas não são removidos.|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|
|Definições de perfil de certificado|Os certificados são revogados, mas não removidos.|Os certificados são removidos e revogados.|
|Agente de gestão|O privilégio de Administrador de Dispositivos é revogado.|O privilégio de Administrador de Dispositivos é revogado.|
|E-mail|N/D (os perfis de e-mail não são suportados por dispositivos Android)|Os perfis de e-mail aprovisionados através do Intune são removidos. O e-mail em cache no dispositivo é eliminado.|
|Anulação da associação ao Azure AD|O registo do Azure AD é removido.|O registo do Azure AD é removido.|

### <a name="android-work-profile"></a>Perfil de trabalho do Android

Uma remoção dos dados da empresa num dispositivo com perfil de trabalho do Android remove todos os dados, aplicações e definições no perfil de trabalho nesse dispositivo. A gestão do dispositivo através do Intune é desativada. A limpeza não é suportada por perfis de trabalho do Android.

### <a name="android-enterprise-kiosk-devices"></a>Dispositivos de quiosque Android Enterprise

Só pode limpar dispositivos de quiosque. Não é possível extinguir dispositivos de quiosque Android.


### <a name="macos"></a>macOS

|Tipo de dados|macOS|
|-------------|-------|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|
|Definições de perfil de certificado|Os certificados que foram implementados através da MDM são removidos e revogados.|
|Agente de gestão|O perfil de gestão é removido.|
|Outlook|Se o Acesso Condicional estiver ativado, o dispositivo não recebe correio novo.|
|Anulação da associação ao Azure AD|O registo do Azure AD é removido.|

### <a name="windows"></a>Windows

|Tipo de dados|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8.1 e Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicações da empresa e dados associados instalados pelo Intune|As chaves para ficheiros protegidos por EFS são revogadas. O utilizador não consegue abrir os ficheiros.|As aplicações da empresa não são removidas.|As aplicações instaladas originalmente através do Portal da Empresa são desinstaladas. Os dados da aplicação da empresa são removidos.|As aplicações são desinstaladas. As chaves de sideload são removidas.<br>Na versão 1703 do Windows 10 (Atualização para Criativos) e posterior, as aplicações do Office 365 ProPlus não são removidas. As aplicações Win32 instaladas da extensão de gestão do Intune não serão desinstaladas em dispositivos não inscritos. Os administradores podem tirar partido da exclusão de atribuição para não oferecer aplicações Win32 em dispositivos BYOD.|
|Definições|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são impostas. Os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|Não suportada.|Removidos.|
|Definições de perfil de certificado|Os certificados são removidos e revogados.|Os certificados são removidos e revogados.|Não suportada.|Os certificados são removidos e revogados.|
|E-mail|Remove e-mails com o EFS ativado. Isto inclui e-mails e anexos na aplicação Correio para Windows.|Não suportada.|Os perfis de e-mail aprovisionados através do Intune são removidos. O e-mail em cache no dispositivo é eliminado.|Remove e-mails com o EFS ativado. Isto inclui e-mails e anexos na aplicação Correio para Windows. Remove as contas de e-mail que tenham sido aprovisionadas pelo Intune.|
|Anulação da associação ao Azure AD|Não.|Não.|O registo do Azure AD é removido.|O registo do Azure AD é removido.|

> [!NOTE]
> Para dispositivos Windows 10 que se juntem ao Azure AD durante a configuração inicial (OOBE), o comando de aposentadoria removerá todas as contas Azure AD do dispositivo. Siga os passos no [Start your PC em modo seguro](https://support.microsoft.com/en-us/help/12376/windows-10-start-your-pc-in-safe-mode) para iniciar sessão como administrador local e recuperar o acesso aos dados locais do utilizador. 

### <a name="retire"></a>Extinguir

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. No painel **Dispositivos**, selecione **Todos os dispositivos**.
3. Selecione o nome do dispositivo que pretende extinguir.
4. No painel que mostra o nome do dispositivo, selecione **Extinguir**. Para confirmar, selecione **Sim**.

Se o dispositivo estiver ativado e ligado, a ação **Extinguir** propaga-se a todos os tipos de dispositivo em menos de 15 minutos.

## <a name="delete-devices-from-the-intune-portal"></a>Eliminar dispositivos do portal do Intune

Se pretender remover dispositivos do portal do Intune, poderá eliminá-los no painel do dispositivo específico. Da próxima vez que o dispositivo for registado, todos os dados da empresa no mesmo serão removidos.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha **Dispositivos** > **Todos os dispositivos** > escolha os dispositivos que quer eliminar > **Eliminar**.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Eliminar automaticamente dispositivos com regras de limpeza
Pode configurar o Intune de forma a eliminar automaticamente dispositivos que parecem estar inativos, obsoletos ou sem resposta. Estas regras de limpeza monitorizam o inventário do seu dispositivo de forma contínua para que os registos do mesmo se mantenham atualizados. Os dispositivos eliminados desta forma são removidos da gestão do Intune.
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Regras de limpeza do dispositivo** > **Sim**.
3. Nos **dispositivos Delete que não tenham verificado esta** caixa de muitos dias, introduza um número entre 30 e 270.
4. Escolha **Guardar**.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminar dispositivos do portal do Azure Active Directory

Poderá ter de eliminar dispositivos do Azure AD devido a problemas de comunicação ou dispositivos em falta. Pode utilizar a ação **Eliminar** para remover registos de dispositivos do portal do Azure para dispositivos que sabe que são inacessíveis e pouco prováveis de voltar a comunicar com o Azure. A ação **Eliminar** não remove um dispositivo da gestão.

1. Inicie sessão no [Azure Active Directory no portal do Azure](https://aka.ms/accessaad) com as suas credenciais de administrador. Também pode iniciar sessão no [centro de administração do Microsoft 365](https://admin.microsoft.com). A partir do menu, selecione **Centros de administração** > **Azure AD**.
2. Se não tiver uma, crie uma Subscrição do Azure. Isto não deve exigir um cartão de crédito ou pagamento se tiver uma conta paga (selecione a ligação de subscrição **Registar o Azure Active Directory gratuito**).
3. Selecione **Azure Active Directory** e, em seguida, selecione a sua organização.
4. Selecione o separador **Utilizadores** .
5. Selecione o utilizador associado ao dispositivo que pretende eliminar.
6. Selecione **Dispositivos**.
7. Remova os dispositivos conforme adequado. Por exemplo, poderá remover dispositivos que já não estão em utilização ou que têm definições incorretas.

## <a name="retire-an-apple-dep-device-from-intune"></a>Extinguir um dispositivo DEP da Apple no Intune

Se pretender remover completamente um dispositivo DEP da Apple da gestão pelo Intune, siga estes passos:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Extinguir**.
![Captura de ecrã da extinção](./media/devices-wipe/retire.png)
3. Aceda a [deploy.apple.com](http://deploy.apple.com) e procure o dispositivo através do respetivo número de série.
4. No menu **Atribuído a**, selecione **Não atribuído**.

5. Selecione **Reatribuir**.

    ![Captura de ecrã da opção Reatribuir da Apple](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>Começar do Zero

Aplicável aos dispositivos Windows 10. Leia mais sobre [Começar do Zero](device-fresh-start.md).

## <a name="next-steps"></a>Próximos passos

Se pretender reinscrever um dispositivo eliminado, veja [Opções de inscrição](../enrollment/enrollment-options.md).

