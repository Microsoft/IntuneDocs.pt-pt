---
title: Configurar o Exchange Connector no local no Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize o Exchange Connector no local para gerir o acesso de dispositivos a caixas de correio do Exchange com base na inscrição no Intune e no Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da828b162e008541cb5cb2b5d15092d0fce417c5
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572541"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Configurar o Exchange connector do Intune no local no Microsoft Intune
As informações neste artigo irão ajudá-lo a instalar e, em seguida, monitorizar o conector do Exchange Active Sync no local para o Intune.  Utilizar o Exchange connector do Intune no local com o seu [políticas de acesso condicional para permitir ou bloquear o acesso ao seu Exchange no local caixas de correio](conditional-access-exchange-create.md). 

Quando um dispositivo tenta aceder ao seu Exchange no local, o conector do Exchange mapeia Exchange Active Sync (EAS) regista no Exchange Server para registos do Intune para verificar a inscrição de dispositivos com o Intune e a conformidade com as políticas de conformidade do dispositivo. Dependendo das suas políticas de acesso condicional, o dispositivo pode ser acesso permitido ou bloqueado. Para obter mais informações, consulte [o que são formas comuns de utilizar o acesso condicional com o Intune?](conditional-access-intune-common-ways-use.md)

O Intune suporta a instalação de múltiplos conectores do Exchange no local por subscrição. Se tiver mais do que uma organização do Exchange no local, pode configurar um conector separado para cada um. No entanto, apenas um conector pode ser instalado para utilização de cada organização do Exchange individual. 

Seguem-se os passos gerais para configurar uma ligação que permite que o Intune para se comunicar com o servidor do Exchange no local:

1. Baixe o Exchange connector no local do Intune no portal do Intune.
2. Instale e configure o Exchange Connector num computador na organização do Exchange no local.
3. Valide a ligação ao Exchange.
4. Repita estes passos para cada organização do Exchange adicional que pretende ligar ao Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisitos do Exchange Connector no local do Intune
Precisará de uma conta com uma licença do Intune que pode ser utilizada pelo conector para estabelecer ligação ao Exchange. A conta é especificada quando instalar o conector.  

A seguinte tabela descreve os requisitos do computador onde irá instalar o Exchange Connector no local.  

|  Requisito  |   Mais informações     |
|---------------|------------------------|
|  Sistemas operativos        | O Intune suporta o Exchange Connector no local num computador com qualquer edição do Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />O conector não é suportado em nenhuma instalação Server Core.  |
| Microsoft Exchange          | Os conectores no local necessitam do Microsoft Exchange 2010 SP3 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração <strong>nova</strong> ou <strong>legada</strong>, contacte o seu gestor de conta. |
| Autoridade de gestão de dispositivos móveis           | [Definir o Intune como a autoridade de gestão de dispositivos móveis](mdm-authority-set.md). |
| Hardware              | O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco. |
|  Sincronização do Active Directory             | Antes de poder utilizar o conector para ligar o Intune ao seu Exchange Server, tem de [configurar a sincronização do Active Directory](users-add.md), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory. |
| Software adicional         | O computador que aloja o conector tem de ter uma instalação completa do Microsoft .NET Framework 4.5 e do Windows PowerShell 2.0. |
| Rede               | O computador em que instalar o conector tem de estar num domínio que tenha uma relação de fidedignidade com o domínio que aloja o seu Exchange Server.<br /><br />O computador requer configurações que lhe permitam aceder ao serviço Intune através de firewalls e servidores proxy pelas Portas 80 e 443. Os domínios que são utilizados pelo Intune incluem manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Crie uma conta de utilizador do Active Directory que será utilizada pelo conector do Exchange no local. A conta tem de ter permissão para executar os seguintes cmdlets necessários do Windows PowerShell do Exchange:


 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-CasMailbox, Set-CasMailbox
 - Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-ActiveSyncDeviceStatistics
 - Get-ActiveSyncDevice
 - Get-ExchangeServer
 - Get-ActiveSyncDeviceClass
 - Get-Recipient
 - Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 - Set-ADServerSettings
 - Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Transferir o pacote de instalação de software do Exchange Connector no local

1. Num sistema operativo Windows Server suportado para o Exchange Connector no local, abra o [portal do Azure](https://portal.azure.com) e inicie sessão com uma conta de utilizador que seja administrador no servidor do Exchange no local e tenha uma licença para utilizar o Exchange Server.

2. Aceda a **Intune** > **acesso ao Exchange**  

3. Sob **programa de configuração**, escolha **ActiveSync do Exchange connector no local**e, em seguida, selecione **Add**.

4. Sobre o **adicionar conector** página, selecione **transferir o conector no local**. O conector do Exchange no local é numa pasta comprimida (. zip) que pode ser aberta ou guardada. Na caixa de diálogo **Transferência de Ficheiros**, escolha **Guardar**, para armazenar a pasta comprimida numa localização segura.

    > [!IMPORTANT]
    > Não mude o nome nem mova os ficheiros dentro da pasta do Exchange Connector no local. Mover ou mudar o nome dos conteúdos da pasta fará com que a instalação do Exchange Connector falhe.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Instalar e configurar o Exchange Connector no local do Intune
Execute os seguintes passos para instalar o Exchange Connector no local do Intune. Se tiver várias organizações do Exchange, repita estes passos para cada Exchange Connector adicional que pretenda configurar.

1. Num sistema operativo suportado para o Exchange Connector no local, extraia os ficheiros em **Exchange_Connector_Setup.zip** para uma localização segura.

2. Após a extração dos ficheiros, abra a pasta extraída e faça duplo clique em **Exchange_Connector_Setup.exe** para instalar o Exchange Connector no local.

   > [!IMPORTANT]
   > Se a pasta de destino não for uma localização segura, deve eliminar o ficheiro de certificado **MicrosoftIntune.accountcert** após a instalação dos conectores no local.

3. Na caixa de diálogo **Microsoft Intune Exchange Connector**, selecione **Microsoft Exchange Server no local** ou **Microsoft Exchange Server alojado**.

   ![Imagem que mostra onde pode escolher o tipo de Exchange Server](./media/intune-sa-exchange-connector-config.png)

   Para um servidor do Exchange no local, forneça o nome do servidor ou o nome de domínio completamente qualificado do servidor do Exchange que aloja a função **Servidor de Acesso de Cliente**.

   Para um servidor do Exchange alojado, forneça o endereço do servidor do Exchange. Para localizar o URL do servidor do Exchange alojado:

   1. Abra o Outlook na Web para o Office 365.

   2. Escolha o ícone **?** no canto superior esquerdo e, em seguida, selecione **Sobre**.

   3. Localize o valor do **Servidor POP Externo**.

   4. Escolha o **Servidor Proxy** para especificar as definições do servidor proxy do seu servidor do Exchange alojado.
       1. Selecione **Utilizar um servidor proxy ao sincronizar informações de dispositivos móveis**.

       2. Introduza o **nome do servidor proxy** e o **número de porta** a utilizar para aceder ao servidor.

       3. Se for necessário fornecer as credenciais de utilizador para aceder ao servidor proxy, selecione **Utilizar as credenciais para se ligar ao servidor proxy**. Em seguida, introduza o **domínio\utilizador** e a **palavra-passe**.

       4. Escolha **OK**.

4. Nos campos **Utilizador (Domínio\utilizador)** e **Palavra-passe**, introduza as credenciais necessárias para se ligar ao seu servidor do Exchange. A conta que especificar tem de ter uma licença para utilizar o Intune. 

5. Forneça as credenciais necessárias para enviar notificações para a caixa de correio do Exchange Server de um utilizador. Este utilizador pode ficar dedicado apenas às notificações. O utilizador de notificações necessita de uma caixa de correio do Exchange para enviar notificações por e-mail. Pode configurar estas notificações com políticas de Acesso Condicional no Intune.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. No campo **Palavra-passe**, forneça a palavra-passe desta conta para permitir que o Intune aceda ao Exchange Server.

7. Escolha **Ligar**.

   > [!NOTE]
   > Podem ser necessários alguns minutos para que a ligação seja configurada.

Durante a configuração, o Exchange Connector armazena as suas definições de proxy para ativar o acesso à Internet. Se alterar as definições de proxy, terá de reconfigurar o Exchange connector para aplicar as definições de proxy atualizadas ao Exchange connector.

Quando o Exchange Connector configurar a ligação, os dispositivos móveis que estão associados a utilizadores geridos no Exchange são automaticamente sincronizados e adicionados ao Exchange Connector. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se instalou o Exchange Connector no local e, a determinada altura, eliminou a ligação ao Exchange, terá de desinstalar o Exchange Connector no local do computador em que foi instalado.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para várias organizações do Exchange
O Intune suporta múltiplos Exchange Connectors no local por subscrição. Para um inquilino com múltiplas organizações do Exchange, pode configurar um conector para cada organização do Exchange, mas apenas um único conector para qualquer organização único. 

Se instalará conectores para ligar a várias organizações do Exchange, transfira a pasta. zip, uma vez e, em seguida, reutilizá-lo mesmo transferir para cada conector que instalar. Para cada conector adicional, siga os passos na secção anterior para extrair e executar o programa de configuração num servidor na organização do Exchange.

A elevada disponibilidade, monitorização e sincronização manual funcionalidades descritas nas seções a seguir são suportadas para cada organização do Exchange liga-se ao Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Suporte de elevada disponibilidade do Exchange Connector no local 
Elevada disponibilidade para o meio de conector de Exchange no local que deve o Exchange acesso servidor cliente (CAS) que o conector utiliza fique indisponível, o conector pode mudar para utilizar uma ACs diferentes para essa organização do Exchange. O conector do Exchange em si não suporta elevada disponibilidade. Se o conector falha, não existe nenhuma ativação pós-falha automática e tem de substituir esse conector pela [instalar um novo conector](#reinstall-the-on-premises-exchange-connector). 

Para realizar a ativação pós-falha, depois que o conector cria uma ligação com êxito ao Exchange através da CAS especificada, o conector Deteta CASs adicionais para essa organização do Exchange. Conhecimento de CASs adicionais permite que o conector para ativação pós-falha para outra CAS, se estiver disponível, até a CAS principal ficar disponível. Por predefinição, a deteção de CASs adicionais está ativada. Pode desativar a ativação pós-falha utilizando o seguinte procedimento:  
1. No servidor onde está instalado o Exchange connector, aceda a %*ProgramData*%\Microsoft\Windows Exchange Connector do Intune. 
2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Altere &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; para &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para desativar a funcionalidade.    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>Reinstalar o conector do Exchange no local
Poderá ter de reinstalar um conector do Exchange. Uma vez que um único conector é suportado para ligar a cada organização do Exchange, se instalar um segundo conector para uma organização, o novo conector que instalar substitui o conector do original.

1. Utilize os passos da [instalar e configurar o Exchange connector do Intune no local](#install-and-configure-the-intune-on-premises-exchange-connector) para iniciar a instalação do novo conector. 
2. Quando lhe for pedido, selecione **substitua** para instalar o novo conector.  
   ![Linha de comandos de configuração para substituir um conector](./media/exchange-connector-install/prompt-to-replace.png)

3. Continue a utilizar os passos do procedimento anterior de formulário e iniciar sessão novamente no Intune.
4. Quando apresentado com a tela final, selecione **fechar** para concluir a instalação.  
   ![Concluir a configuração](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Monitorizar a atividade do conector do Exchange

Depois de configurar o conector do Exchange com êxito, pode ver o estado de ligações e a última tentativa de sincronização efetuada com êxito. Para validar a ligação de conector do Exchange:

1. No Dashboard do Intune, escolha **acesso ao Exchange**.
2. Selecione **Exchange no local acesso** para verificar o estado da ligação para cada conector do Exchange.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.
--> 

### <a name="system-center-operations-manager-management-pack"></a>Pacote de gestão do System Center Operations Manager

A partir da versão 1710 do Intune, pode utilizar o [pacote de gestão do Operations Manager para o conector do Exchange e o Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Utilizar o pacote de gestão dá-lhe várias formas de monitorizar o conector do Exchange quando precisar de resolver problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forçar manualmente uma sincronização rápida ou uma sincronização completa
Um conector do Exchange no local sincroniza automaticamente os registos de dispositivos EAS e o Intune regularmente. Se o estado de conformidade de um dispositivo for alterada, o processo de sincronização automática atualiza regularmente os registos para que o acesso do dispositivo pode ser bloqueado ou permitido.

   - **Sincronização rápida** ocorre regularmente, várias vezes ao dia. Uma sincronização rápida obtém informações do dispositivo para a licença do Intune e os utilizadores visados de acesso condicional do Exchange, que foram alterados desde a última sincronização no local.

   - **Sincronização completa** ocorre uma vez por dia, por predefinição. Uma sincronização completa obtém informações do dispositivo para todos os licenciados do Intune e os utilizadores visados de acesso condicional do Exchange no local. Uma sincronização completa obtém também informações do servidor do Exchange e garante que a configuração especificada pelo Intune no portal do Azure está atualizada no servidor do Exchange. 


Pode forçar a execução de uma sincronização por parte do conector ao utilizar as opções de **Sincronização Rápida** ou **Sincronização Completa** no dashboard do Intune com os seguintes passos:

   1. No dashboard do Intune, escolha **acesso ao Exchange**.
   2. Selecione **Exchange no local acesso**.
   3. Selecione o conector que pretende sincronizar e, em seguida, selecione **Sincronização Rápida** ou **Sincronização Completa**.

## <a name="next-steps"></a>Passos Seguintes
[Criar uma política de acesso condicional para o Exchange no local](conditional-access-exchange-create.md)
