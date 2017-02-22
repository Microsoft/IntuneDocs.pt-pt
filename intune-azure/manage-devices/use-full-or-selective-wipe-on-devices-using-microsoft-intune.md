---
title: "Eliminação completa ou seletiva em dispositivos com o Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como fazer uma eliminação seletiva de dados da empresa num dispositivo ou fazer uma eliminação completa para uma reposição de fábrica do dispositivo."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 9188f4bb4ea526227ccd9f2029fc9b44cbd4a334


---

# <a name="use-full-or-selective-wipe"></a>Utilizar a eliminação completa ou seletiva 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pode eliminar aplicações e dados a partir dos dispositivos geridos pelo Intune que já não são precisos, que estão a ser reobjetivados ou que desapareceram. Para tal, o Intune fornece as funcionalidades de eliminação completa e eliminação seletiva. Os utilizadores também podem emitir um comando de eliminação remota de dados no dispositivo a partir da aplicação Portal da Empresa do Intune em dispositivos de propriedade privada inscritos no Intune.

  > [!NOTE]
  > Este tópico aborda apenas a eliminação de dispositivos geridos pela gestão de dispositivos móveis do Intune. Também pode utilizar o [portal do Azure](https://portal.azure.com) para [apagar dados da empresa das aplicações](https://docs.microsoft.com/intune/deploy-use/wipe-managed-company-app-data-with-microsoft-intune). Também pode [extinguir computadores geridos com o software de cliente Intune](https://docs.microsoft.com/intune/deploy-use/retire-a-windows-pc-with-microsoft-intune).

## <a name="full-wipe"></a>Eliminação completa

A **Eliminação completa** restaura as predefinições do dispositivo, removendo todos os dados e definições da empresa e do utilizador. O dispositivo é removido do Intune. A eliminação completa é útil para repor um dispositivo antes de o atribuir a um novo utilizador ou em caso de perda ou roubo do dispositivo.  **Seja cuidadoso com a seleção da eliminação completa. Não é possível recuperar os dados no dispositivo**.


> [!Warning]
> A eliminação pode fazer com que os dispositivos Windows 10 RTM (dispositivos anteriores ao Windows 10 versão 1511) com menos de 4 GB de RAM fiquem inacessíveis. Para aceder a um dispositivo Windows 10 que deixou de responder, pode arrancá-lo a partir de uma unidade USB.


**Para fazer uma eliminação completa (reposição de fábrica) de um dispositivo**:

1.  No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.

2.  Escolha o nome do dispositivo cujos dados pretende eliminar.

3.  No painel que mostra o nome do dispositivo, selecione **Reposição de fábrica** e, em seguida, selecione **Sim** para confirmar a eliminação dos dados.

Se o dispositivo estiver ativo e ligado, demora menos de 15 minutos até um comando de eliminação ser propagado em todos os tipos de dispositivo.

### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Para eliminar dispositivos no portal do Azure Active Directory

1.  Navegue para [http://aka.ms/accessaad](http://aka.ms/accessaad) ou escolha **Administração** &gt; **Azure AD** a partir de [https://portal.office.com](https://portal.office.com).

2.  Inicie sessão com o seu ID de Organização através da ligação no lado esquerdo da página.

3.  Se não tiver uma, crie uma Subscrição do Azure. Se tiver uma conta paga (escolha a ligação de subscrição **Registar o Azure Active Directory gratuito**), não deverá ser preciso um cartão de crédito ou um pagamento para esta subscrição.

4.  Selecione **Active Directory** e, em seguida, selecione a sua organização.

5.  Selecione o separador **Utilizadores** .

6.  Selecione o utilizador cujos dispositivos pretende eliminar.

7.  Escolha **Dispositivos**.

8.  Remova os dispositivos conforme adequado, como aqueles que já não estão em utilização ou que têm definições incorretas.


## <a name="selective-wipe"></a>Eliminação seletiva

A **eliminação seletiva** remove os dados da empresa, incluindo os dados de gestão de aplicações móveis (MAM) (onde for aplicável), definições e perfis de e-mail de um dispositivo. A eliminação seletiva mantém os dados pessoais do utilizador no dispositivo. O dispositivo é removido do Intune. As seguintes tabelas descrevem os dados que são removidos e o efeito nos dados que permanecem no dispositivo após uma eliminação seletiva. (As tabelas estão organizadas por plataforma.)

**iOS**

|Tipo de dados|iOS|
|-------------|-------|
|Aplicações da empresa e dados associados instalados pelo Intune|As aplicações são desinstaladas. Os dados da aplicação da empresa são removidos.<br /><br />Os dados de aplicações da Microsoft que utilizam a gestão de aplicações móveis são removidos. A aplicação não é removida.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|
|Definições de perfil de certificado|Os certificados são removidos e revogados.|
|Agente de Gestão|O perfil de gestão é removido.|
|E-mail|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado. Se o Microsoft Exchange estiver alojado no local, os perfis de e-mail e o e-mail em cache não serão removidos.|
|Outlook|Os e-mails recebidos pela aplicação Microsoft Outlook para iOS são removidos.</br>Exceção: se o Exchange estiver alojado no local, o e-mail não será removido.|
|Anulação da associação ao Azure Active Directory (AAD)|O Registo do AAD é removido.|
|Contactos | Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.

**Android**

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
|E-mail|Os e-mails recebidos pela aplicação Microsoft Outlook para Android são removidos.|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|
|Outlook|Os e-mails recebidos pela aplicação Microsoft Outlook para iOS são removidos.</br>Exceção: se o Exchange estiver alojado no local, o e-mail não será removido.|Os e-mails recebidos pela aplicação Microsoft Outlook para iOS são removidos.</br>Exceção: se o Exchange estiver alojado no local, o e-mail não será removido.|
|Anulação da associação ao Azure Active Directory (AAD)|Registo do AAD removido.|Registo do AAD removido.|
|Contactos | Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.|Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.

**Windows**

|Tipo de dados|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicações da empresa e dados associados instalados pelo Intune|Os ficheiros protegidos pelo EFS terão as respetivas chaves revogadas e o utilizador não poderá abrir os ficheiros.|Não remove aplicações da empresa.|As aplicações instaladas originalmente através do portal da empresa são desinstaladas. Os dados da aplicação da empresa são removidos.|As aplicações são desinstaladas e as chaves de sideload são removidas.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidos.|Removidos.|Não suportada.|Removidos.|
|Definições de perfil de certificado|Certificados removidos e revogados.|Certificados removidos e revogados.|Não suportada.|Certificados removidos e revogados.|
|E-mail|Remove o e-mail que tenha o EFS ativado, que inclui a aplicação Correio para e-mail e anexos do Windows.|Não suportada.|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|Remove o e-mail que tenha o EFS ativado, que inclui a aplicação Correio para e-mail e anexos do Windows. Remove as contas de e-mail que tenham sido aprovisionadas pelo Intune.</br>**Exceção**: se o Microsoft Exchange estiver alojado no local, as contas de e-mail não serão removidas.|
|Anulação da associação ao Azure Active Directory (AAD)|Não.|Não.|Registo do AAD removido.|Não aplicável. O Windows 10 não suporta a eliminação seletiva para dispositivos associados ao Azure Active Directory.|

**Para fazer uma eliminação seletiva**:

1.  No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.

2.  Escolha o nome do dispositivo cujos dados pretende eliminar.

3.  No painel que mostra o nome do dispositivo, selecione **Remover dados...** (significa Remover dados da empresa) e, em seguida, selecione **Sim** para confirmar a eliminação dos dados.

Se o dispositivo estiver ativo e ligado, demora menos de 15 minutos até um comando de eliminação ser propagado em todos os tipos de dispositivo.



<!--HONumber=Feb17_HO1-->


