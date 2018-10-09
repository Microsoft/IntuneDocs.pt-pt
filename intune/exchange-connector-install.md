---
title: Configurar o Exchange Connector no local no Microsoft Intune
titleSuffix: ''
description: Utilize o Exchange Connector no local para gerir o acesso de dispositivos a caixas de correio do Exchange com base na inscrição no Intune e no Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e12ab106b44d217d7e7b4b1a466fd5b12a9fb528
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231836"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configurar o Exchange Connector do Intune no local no Microsoft Intune no Azure

Num ambiente do Exchange Server no local, pode ser utilizado o acesso condicional do Intune para permitir ou bloquear o acesso às caixas de correio do Exchange no local. Utilize os conectores no local do Exchange Active Sync para ligar o Intune às suas organizações do Exchange e configurar o acesso condicional do Intune, juntamente com as políticas de conformidade do dispositivo. Assim, quando um dispositivo tentar estabelecer ligação ao Exchange, o Intune determinará se o dispositivo está inscrito no Intune e está em conformidade. Para determinar quais os dispositivos inscritos no Intune, o Exchange Connector no local efetua o mapeamento dos registos do Exchange Active Sync (EAS) no Exchange Server aos registos do Intune. Para obter mais informações sobre como funciona, veja [Quais são as formas comuns de utilizar o acesso condicional com o Intune?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> O Intune suporta múltiplos Exchange Connectors no local por subscrição. Se tiver mais do que uma organização do Exchange no local, pode configurar um conector separado para cada organização do Exchange.

Para configurar uma ligação que permita ao Microsoft Intune comunicar com o Exchange Server no local, eis os passos gerais:

1.  Transfira o Exchange Connector no local do Intune a partir do portal do Azure.
2.  Instale e configure o Exchange Connector num computador na organização do Exchange no local.
3.  Valide a ligação ao Exchange.
4. Repita estes passos para cada organização do Exchange que pretenda ligar ao Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisitos do Exchange Connector no local do Intune
A seguinte tabela descreve os requisitos do computador onde irá instalar o Exchange Connector no local.


|            Requisito             |                                                                                                                                                                                                        Mais informações                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Sistemas operativos          |                                                               O Intune suporta o Exchange Connector no local num computador com qualquer edição do Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />O conector não é suportado em nenhuma instalação Server Core.                                                                |
|         Microsoft Exchange         |                                                                           Os conectores no local necessitam do Microsoft Exchange 2010 SP1 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração <strong>nova</strong> ou <strong>legada</strong>, contacte o seu gestor de conta.                                                                           |
| Autoridade de gestão de dispositivos móveis |                                                                                                                              [Definir o Intune como a autoridade de gestão de dispositivos móveis](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).                                                                                                                               |
|              Hardware              |                                                                                                                                                     O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco.                                                                                                                                                      |
|  Sincronização do Active Directory  |                                                                                      Antes de poder utilizar o conector para ligar o Intune ao seu Exchange Server, tem de [configurar a sincronização do Active Directory](users-add.md), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory.                                                                                      |
|        Software adicional         |                                                                                                                                           O computador que aloja o conector tem de ter uma instalação completa do Microsoft .NET Framework 4.5 e do Windows PowerShell 2.0.                                                                                                                                           |
|              Rede               | O computador em que instalar o conector tem de estar num domínio que tenha uma relação de fidedignidade com o domínio que aloja o seu Exchange Server.<br /><br />O computador requer configurações que lhe permitam aceder ao serviço Intune através de firewalls e servidores proxy pelas Portas 80 e 443. Os domínios que são utilizados pelo Intune incluem manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Tem de criar uma conta de utilizador do Active Directory que é utilizada pelo Exchange Connector do Intune. A conta tem de ter permissão para executar os seguintes cmdlets necessários do Windows PowerShell do Exchange:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Transferir o pacote de instalação de software do Exchange Connector no local

1. Num sistema operativo Windows Server suportado para o Exchange Connector no local, abra o [portal do Azure](http://portal.azure.com) e inicie sessão com uma conta de utilizador que seja administrador no servidor do Exchange no local e tenha uma licença para utilizar o Exchange Server.

2. Selecione **Todos os serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Selecione **Intune** e, quando o Dashboard do Intune for apresentado, selecione **Acesso no local**.

4. Em **Configuração**, selecione **Conectores do Exchange ActiveSync** e, em seguida, selecione **Transferir o conector no local**.

5.  O Exchange Connector no local encontra-se numa pasta comprimida (.zip) que pode ser aberta ou guardada. Na caixa de diálogo **Transferência de Ficheiros**, escolha **Guardar**, para armazenar a pasta comprimida numa localização segura.

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

   5. Nos campos **Utilizador (Domínio\utilizador)** e **Palavra-passe**, introduza as credenciais necessárias para se ligar ao seu servidor do Exchange.

   6.  Forneça as credenciais necessárias para enviar notificações para a caixa de correio do Exchange Server de um utilizador. Este utilizador pode ficar dedicado apenas às notificações. O utilizador de notificações necessita de uma caixa de correio do Exchange para poder enviar notificações por e-mail. Pode configurar estas notificações com políticas de acesso condicional no Intune.  

       Certifique-se de que o serviço de Deteção Automática e os Serviços Web Exchange são configurados no Servidor de Acesso de Cliente do Exchange. Para mais informações, consulte o artigo [servidor de Acesso de Cliente](https://technet.microsoft.com/library/dd298114.aspx).

   7.  No campo **Palavra-passe**, forneça a palavra-passe desta conta para permitir que o Intune aceda ao Exchange Server.

   8. Escolha **Ligar**.

   > [!NOTE]
   > Podem ser necessários alguns minutos para que a ligação seja configurada.

Durante a configuração, o Exchange Connector armazena as suas definições de proxy para ativar o acesso à Internet. Se as suas definições de proxy forem alteradas, terá de reconfigurar o Exchange Connector para aplicar as definições de proxy atualizadas ao Exchange Connector.

Quando o Exchange Connector configurar a ligação, os dispositivos móveis que estão associados a utilizadores geridos no Exchange são automaticamente sincronizados e adicionados ao Exchange Connector. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se instalou o Exchange Connector no local e, a determinada altura, eliminou a ligação ao Exchange, terá de desinstalar o Exchange Connector no local do computador em que foi instalado.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para várias organizações do Exchange
O Intune suporta múltiplos Exchange Connectors no local por subscrição. Para um inquilino com várias organizações do Exchange, pode configurar um conector para cada organização do Exchange. Transfira a pasta .zip uma vez e, em seguida, para cada organização do Exchange, siga os passos na secção anterior para extrair e executar o programa de configuração num servidor da organização.

As funcionalidades de elevada disponibilidade, monitorização e sincronização manual descritas nas secções seguintes são suportadas para cada organização do Exchange ligada ao Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Suporte de elevada disponibilidade do Exchange Connector no local 
Depois de o Exchange Connector criar uma ligação ao Exchange através da CAS especificada, o conector tem a capacidade de detetar outras CASs. Se a CAS principal ficar indisponível, o conector realizará a ativação pós-falha para outra CAS, se disponível, até a CAS principal ficar disponível. Por predefinição, esta funcionalidade está ativada. Pode desativar esta funcionalidade através do seguinte procedimento:
1. No servidor onde está instalado o Exchange Connector, aceda a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Altere &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; para &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para desativar a funcionalidade.    


## <a name="monitor-the-exchange-connector-activity"></a>Monitorizar a atividade do conector do Exchange

Após a configuração com êxito dos Exchange Connectors, pode ver o estado das ligações e a última tentativa de sincronização efetuada com êxito. Para validar as ligações ao Exchange Connector:

1. No Dashboard do Intune, escolha **Acesso no local**.
2. Em **Configuração**, selecione **Conectores do Exchange ActiveSync** para verificar o estado da ligação para cada Exchange Connector.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.

### <a name="system-center-operations-manager-scom-management-pack"></a>Pacote de gestão do System Center Operations Manager (SCOM)

A partir da versão 1710 do Intune, pode utilizar o [pacote de gestão do SCOM para o conector do Exchange e o Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Este pacote de gestão proporciona-lhe várias formas de monitorizar o conector do Exchange quando precisar de resolver problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forçar manualmente uma sincronização rápida ou uma sincronização completa
Um Exchange Connector no local sincroniza automaticamente o EAS e os registos de dispositivos do Intune, de forma regular. Se o estado de conformidade de um dispositivo for alterado, o processo de sincronização automática atualiza regularmente os registos para que o acesso do dispositivo possa ser bloqueado ou permitido em conformidade.

   - **Sincronização rápida** ocorre regularmente, várias vezes ao dia. Uma sincronização rápida obtém informações do dispositivo para utilizadores direcionados ao acesso condicional do Exchange no local e com licença do Intune que foram alterados desde a última sincronização.

   - **Sincronização completa** ocorre uma vez por dia, por predefinição. Uma sincronização completa obtém informações do dispositivo para todos os utilizadores direcionados ao acesso condicional do Exchange no local e com licença do Intune. Uma sincronização completa obtém também informações do servidor do Exchange e garante que a configuração especificada pelo Intune no portal do Azure está atualizada no servidor do Exchange. 

Pode forçar a execução de uma sincronização por parte do conector ao utilizar as opções de **Sincronização Rápida** ou **Sincronização Completa** no dashboard do Intune com os seguintes passos:

   1. No dashboard do Intune, selecione **Acesso no local**.
   2. Em **Configuração**, selecione **Conectores do Exchange Active Sync**.
   3. Selecione o conector que pretende sincronizar e, em seguida, selecione **Sincronização Rápida** ou **Sincronização Completa**.

## <a name="next-steps"></a>Próximos passos
[Criar uma política de acesso condicional para o Exchange no Local](conditional-access-exchange-create.md)
