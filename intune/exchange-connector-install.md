---
title: Configurar o Exchange Connector para EAS no local com o Intune
titleSuffix: Azure portal
description: "Utilize a ferramenta Connector para permitir a comunicação entre o Intune e o Exchange Server no local"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9650afefc8ba0ba782e95b28feaaf1aaceea8d7f
ms.sourcegitcommit: 06abc5ccc8b868c9ff3ad3f8f62473a87b2da481
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/15/2017
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configurar o Exchange Connector do Intune no local no Microsoft Intune no Azure

Os ambientes do Exchange Server no local podem utilizar o conector do Exchange no local do Intune para gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de os dispositivos estarem ou não inscritos no Intune e estarem ou não conformes com as políticas de conformidade de dispositivos do Intune. O conector do Exchange no local é também responsável pela descoberta de dispositivos móveis que se ligam a Exchange Servers no local, ao sincronizar o registo do Exchange Active Sync (EAS) existente com o Intune.

> [!IMPORTANT]
> O Intune apenas suporta uma ligação do Exchange Connector no local de qualquer tipo por subscrição.

Para configurar uma ligação que permita ao Microsoft Intune comunicar com o Exchange Server no local, precisa de seguir os passos abaixo:

1.  Transfira o Exchange Connector no local do Intune a partir do portal do Azure.
2.  Instale e configure o conector do Exchange no local do Intune.
3.  Valide a ligação ao Exchange.

## <a name="on-premises-exchange-connector-requirements"></a>Requisitos do Exchange Connector no Local
A seguinte tabela descreve os requisitos do computador onde irá instalar o Exchange Connector no Local.

|Requisito|Mais informações|
|---------------|--------------------|
|Sistemas operativos|O Intune suporta o Exchange Connector no Local num computador com qualquer edição do Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012 ou Windows Server 2012 R2.<br /><br />O Connector não é suportado em nenhuma instalação Server Core.|
|Microsoft Exchange|Os Connectors no local requerem o Microsoft Exchange 2010 SP1 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração **nova** ou **legada**, contacte o seu gestor de conta.|
|Autoridade de gestão de dispositivos móveis| [Definir o Intune como a autoridade de gestão de dispositivos móveis](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).|
|Hardware|O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco.|users-add.md
|Sincronização do Active Directory|Antes de poder utilizar o Connector para ligar o Intune ao seu Exchange Server, tem de [configurar a sincronização do Active Directory](users-add.md), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory.|
|Software adicional|O computador que aloja o conector tem de ter uma instalação completa do Microsoft .NET Framework 4.5 e do Windows PowerShell 2.0.|
|Rede|O computador em que instalar o conector tem de estar num domínio que tenha uma relação de fidedignidade com o domínio que aloja o seu Exchange Server.<br /><br />O computador requer configurações que lhe permitam aceder ao serviço Intune através de firewalls e servidores proxy pelas Portas 80 e 443. Os domínios que são utilizados pelo Intune incluem manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com.|


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

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Transferir o pacote de instalação de software do Exchange Connector no Local

1. Num sistema operativo Windows Server suportado para o Exchange Connector no Local, abra o [portal do Azure](http://portal.azure.com) e inicie sessão com uma conta de utilizador que seja administrador no servidor do Exchange no local e tenha uma licença para utilizar o Exchange Server.

2. Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

3. Escolha **Intune**, quando o Dashboard do Intune for apresentado, escolha **Acesso no local**.

4. No painel **Acesso no local – Conector do Exchange ActiveSync**, na secção **Configurar**, escolha **Transferir o conector no local**.

5.  O Exchange Connector no Local encontra-se numa pasta comprimida (.zip) que pode ser aberta ou guardada. Na caixa de diálogo **Transferência de Ficheiros**, escolha **Guardar**, para armazenar a pasta comprimida numa localização segura.

    > [!IMPORTANT]
    > Não mude o nome nem mova os ficheiros dentro da pasta do Exchange Connector no local. Mover ou mudar o nome dos conteúdos da pasta fará com que a instalação do Exchange Connector falhe.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Instalar e configurar o Exchange Connector no Local do Intune
Execute os seguintes passos para instalar o Exchange Connector no Local do Intune. O Exchange Connector no Local só pode ser instalado uma vez por cada subscrição do Intune e em apenas um computador. Se tentar configurar um Exchange Connector no Local adicional, a nova ligação substituirá a ligação original.

1.  Num sistema operativo suportado para o Connector no Local, extraia os ficheiros em **Exchange_Connector_Setup.zip** para uma localização segura.

2.  Após a extração dos ficheiros, abra a pasta extraída e faça duplo clique em **Exchange_Connector_Setup.exe** para instalar o Exchange Connector no Local.

    > [!IMPORTANT]
    > Se a pasta de destino não for uma localização segura, deve eliminar o ficheiro de certificado **WindowsIntune.accountcert** após a instalação do Connector no Local.

3.  Na caixa de diálogo **Microsoft Intune Exchange Connector**, selecione **Microsoft Exchange Server no local** ou **Microsoft Exchange Server alojado**.

  ![Escolher o tipo de Exchange Server](./media/intune-sa-exchange-connector-config.png)

  Para um servidor do Exchange no Local, forneça o nome do servidor ou o nome de domínio completamente qualificado do servidor do Exchange que aloja a função **Servidor de Acesso de Cliente**.

  Para um servidor do Exchange alojado, forneça o endereço do servidor do Exchange. Para localizar o URL do servidor do Exchange alojado:

    1. Abra o Outlook Web App para Office 365.

    2. Escolha o ícone **?** no canto superior esquerdo e, em seguida, selecione **Sobre**.

    3. Localize o valor do **Servidor POP Externo**.

    4. Escolha o **Servidor Proxy** para especificar as definições do servidor proxy do seu servidor do Exchange alojado.
        1. Selecione **Utilizar um servidor proxy ao sincronizar informações de dispositivos móveis**.

        2. Introduza o **nome do servidor proxy** e o **número de porta** a utilizar para aceder ao servidor.

        3. Se for necessário fornecer as credenciais de utilizador para aceder ao servidor proxy, selecione **Utilizar as credenciais para se ligar ao servidor proxy**. Em seguida, introduza o **domínio\utilizador** e a **palavra-passe**.

        4. Escolha **OK**.

    5. Nos campos **Utilizador (Domínio\utilizador)** e **Palavra-passe**, introduza as credenciais necessárias para se ligar ao seu servidor do Exchange.

    6.  Forneça as credenciais administrativas necessárias para enviar notificações para a caixa de correio do Exchange Server de um utilizador. Pode configurar estas notificações com políticas de Acesso Condicional no Intune.

        Certifique-se de que o serviço de Deteção Automática e os Serviços Web Exchange são configurados no Servidor de Acesso de Cliente do Exchange. Para mais informações, consulte o artigo [servidor de Acesso de Cliente](https://technet.microsoft.com/library/dd298114.aspx).

    7.  No campo **Palavra-passe**, forneça a palavra-passe desta conta para permitir que o Intune aceda ao Exchange Server.

    8. Escolha **Ligar**.

    > [!NOTE]
    > Podem ser necessários alguns minutos para que a ligação seja configurada.

Durante a configuração, o Exchange Connector armazena as suas definições de proxy para ativar o acesso à Internet. Se as suas definições de proxy forem alteradas, terá de reconfigurar o Exchange Connector para aplicar as definições de proxy atualizadas ao Exchange Connector.

Quando o Exchange Connector configurar a ligação, os dispositivos móveis que estão associados a utilizadores geridos no Exchange Connector são automaticamente sincronizados e adicionados ao Exchange Connector. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se instalou o Exchange Connector no Local e, a determinada altura, eliminou a ligação ao Exchange, terá de desinstalar o Exchange Connector no Local do computador em que foi instalado.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Suporte de elevada disponibilidade do Exchange Connector no local 
Depois de o Exchange Connector criar uma ligação ao Exchange através da CAS especificada, o conector tem a capacidade de detetar outras CASs. Se a CAS principal ficar indisponível, o conector realizará a ativação pós-falha para outra CAS, se disponível, até a CAS principal ficar disponível. Por predefinição, esta funcionalidade está ativada. Pode desativar esta funcionalidade através do seguinte procedimento:
1. No servidor onde está instalado o Exchange Connector, aceda a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Altere &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; para &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para desativar a funcionalidade.    


## <a name="monitor-the-exchange-connector-activity"></a>Monitorizar a atividade do conector do Exchange

Após a configuração com êxito do Exchange Connector, pode ver o estado da ligação e a última tentativa de sincronização efetuada com êxito. Para validar a ligação ao Exchange Connector:

1. No Dashboard do Intune, escolha **Acesso no local**.
2. Em **Gerir**, selecione **Acesso do Exchange no local** para verificar o estado da ligação.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.

### <a name="system-center-operations-manager-scom-management-pack"></a>Pacote de gestão do System Center Operations Manager (SCOM)

A partir da versão 1710 do Intune, pode utilizar o [pacote de gestão do SCOM para o conector do Exchange e o Intune](https://www.microsoft.com/en-us/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Este pacote de gestão proporciona-lhe várias formas de monitorizar o conector do Exchange quando precisar de resolver problemas.

## <a name="next-steps"></a>Próximos passos
[Criar uma política de acesso condicional para o Exchange no Local](conditional-access-exchange-create.md)
