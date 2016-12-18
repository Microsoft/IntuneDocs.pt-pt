---
title: Exchange Connector para EAS no Local | Microsoft Intune
description: "Utilize a ferramenta Connector para permitir a comunicação entre a consola de administração do Intune e o Exchange Server no Local na MDM do Exchange ActiveSync."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41ff4212-a6f5-4374-8731-631f7560cff1
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d50a5751a5afd987196336e9443dc5a429a283fd
ms.openlocfilehash: 58c5ab6b506695fb5b0f7556dc1deac39580f59b


---

# <a name="install-the-intune-on-premises-exchange-connector"></a>Instalar o Exchange Connector no Local do Intune


Para configurar uma ligação que permite a comunicação entre o Microsoft Intune e o Exchange Server que aloja as caixas de correio dos dispositivos móveis, tem de transferir e configurar o Exchange Connector no Local na consola do administrador do Intune. O Intune apenas suporta uma ligação do Exchange Connector de qualquer tipo por subscrição.

## <a name="on-premises-exchange-connector-requirements"></a>Requisitos do Exchange Connector no Local
A seguinte tabela descreve os requisitos do computador onde irá instalar o Exchange Connector no Local.

|Requisito|Mais informações|
|---------------|--------------------|
|Sistemas operativos|O Intune suporta o Exchange Connector no Local num computador com qualquer edição do Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012 ou Windows Server 2012 R2.<br /><br />O Connector não é suportado em nenhuma instalação Server Core.|
|Microsoft Exchange|Os Connectors no local requerem o Microsoft Exchange 2010 SP1 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração **nova** ou **legada**, contacte o seu gestor de conta.|
|Autoridade de gestão de dispositivos móveis| [Definir o Intune como a autoridade de gestão de dispositivos móveis](prerequisites-for-enrollment.md#step-2-set-mdm-authority).|
|Hardware|O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco.|
|Sincronização do Active Directory|Antes de poder utilizar o Connector para ligar o Intune ao seu Exchange Server, tem de [configurar a sincronização do Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory.|
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

1. Num sistema operativo Windows Server suportado para o Exchange Connector no Local, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com) (http://manage.microsoft.com) com uma conta de utilizador que seja administrador no inquilino do Exchange e que tenha uma licença para utilizar o Exchange Server.
![Abrir Configurar a ligação ao Exchange](../media/ExchangeConnector.gif)

2.  No painel de atalhos da área de trabalho, selecione **Admin**>**Mobile Device Management** > **Microsoft Exchange**>**Setup Exchange Connection**.

3.  Na página **Configurar a Ligação ao Exchange**, escolha **Transferir o Conector No Local**.

4.  O Exchange Connector no Local encontra-se numa pasta comprimida (.zip) que pode ser aberta ou guardada. Na caixa de diálogo **Transferência de Ficheiros**, escolha **Guardar**, para armazenar a pasta comprimida numa localização segura.

> [!IMPORTANT]
> Não mude o nome nem mova os ficheiros dentro da pasta do Exchange Connector no Local. Mover ou mudar o nome dos conteúdos da pasta irá causar a falha da instalação.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Instalar e configurar o Exchange Connector no Local do Intune
Execute os seguintes passos para instalar o Exchange Connector no Local do Intune. O Exchange Connector no Local só pode ser instalado uma vez por cada subscrição do Intune e em apenas um computador. Se tentar configurar um Exchange Connector no Local adicional, a nova ligação substituirá a ligação original.

1.  Num sistema operativo suportado para o Connector no Local, extraia os ficheiros em **Exchange_Connector_Setup.zip** para uma localização segura.

2.  Após a extração dos ficheiros, abra a pasta extraída e faça duplo clique em **Exchange_Connector_Setup.exe** para instalar o Exchange Connector no Local.

    > [!IMPORTANT]
    > Se a pasta de destino não for uma localização segura, deve eliminar o ficheiro de certificado **WindowsIntune.accountcert** após a instalação do Connector no Local.

3.  Na caixa de diálogo **Microsoft Intune Exchange Connector**, selecione **Microsoft Exchange Server no local** ou **Microsoft Exchange Server alojado**.

  ![Escolher o tipo de Exchange Server](../media/IntuneSA1dconfigureExchConnector.png)

  Para um servidor do Exchange no Local, forneça o nome do servidor ou o nome de domínio completamente qualificado do servidor do Exchange que aloja a função **Servidor de Acesso de Cliente**.

  Para um servidor do Exchange alojado, forneça o endereço do servidor do Exchange. Para localizar o URL do servidor do Exchange alojado:

    1. Abra o Outlook Web App para Office 365.

    2. Escolha o ícone **?** no canto superior esquerdo e, em seguida, selecione **Sobre**.

    3. Localize o valor do **Servidor POP Externo** .

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

Podem ser necessários alguns minutos para que a ligação seja configurada.

Durante a configuração, o Exchange Connector armazena as suas definições de proxy para ativar o acesso à Internet. Se as suas definições de proxy forem alteradas, terá de reconfigurar o Exchange Connector para aplicar as definições de proxy atualizadas ao Exchange Connector.

Quando o Exchange Connector configurar a ligação, os dispositivos móveis que estão associados a utilizadores geridos no Exchange Connector são automaticamente sincronizados e adicionados ao Exchange Connector. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se instalou o Exchange Connector no Local e, a determinada altura, eliminou a ligação ao Exchange, terá de desinstalar o Exchange Connector no Local do computador em que foi instalado.

## <a name="validate-the-exchange-connection"></a>Validar a ligação ao Exchange

Após a configuração com êxito do Exchange Connector, pode ver o estado da ligação e a última tentativa de sincronização efetuada com êxito. Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), selecione a área de trabalho **ADMIN**. Em **Mobile Device Management**, selecione **Microsoft Exchange**, e confirme se os detalhes fornecidos são apresentados em **Exchange Connection Information**.


Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.



<!--HONumber=Dec16_HO2-->


