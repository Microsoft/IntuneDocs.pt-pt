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
ms.openlocfilehash: 0a2ebf91efb35ecd46607baffc47abbe73c5fc5c
ms.sourcegitcommit: 2bce5e43956b6a5244a518caa618f97f93b4f727
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68467485"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Configurar o Exchange Connector local do Intune no Microsoft Intune
As informações neste artigo o ajudarão a instalar e monitorar o Exchange Active Sync Connector local para o Intune.  Use o Exchange Connector local do Intune com suas políticas de [acesso condicional para permitir ou bloquear o acesso às suas caixas de correio locais do Exchange](conditional-access-exchange-create.md). 

Quando um dispositivo tenta acessar seu Exchange local, o Exchange Connector mapeia os registros de Exchange Active Sync (EAS) no Exchange Server para registros do Intune para verificar o registro do dispositivo com o Intune e a conformidade com as políticas de conformidade do dispositivo. Dependendo de suas políticas de acesso condicional, o dispositivo pode ter acesso permitido ou bloqueado. Para obter mais informações, consulte [quais são as maneiras comuns de usar o acesso condicional com o Intune?](conditional-access-intune-common-ways-use.md)

O Intune dá suporte à instalação de vários conectores locais do Exchange por assinatura. Se você tiver mais de uma organização do Exchange local, poderá configurar um conector separado para cada uma. No entanto, apenas um conector pode ser instalado para usar cada organização individual do Exchange. 

A seguir estão as etapas gerais para configurar uma conexão que habilita o Intune a se comunicar com o Exchange Server local:

1. Baixe o Exchange Connector local do Intune no portal do Intune.
2. Instale e configure o Exchange Connector num computador na organização do Exchange no local.
3. Valide a ligação ao Exchange.
4. Repita essas etapas para cada organização do Exchange adicional que você deseja conectar ao Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisitos do Exchange Connector no local do Intune
Você precisará de uma conta com uma licença do Intune que possa ser usada pelo conector para se conectar ao Exchange. A conta é especificada quando você instala o conector do.  

A seguinte tabela descreve os requisitos do computador onde irá instalar o Exchange Connector no local.  

|  Requisito  |   Mais informações     |
|---------------|------------------------|
|  Sistemas operativos        | O Intune suporta o Exchange Connector no local num computador com qualquer edição do Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />Não há suporte para o conector em nenhuma instalação Server Core.  |
| Microsoft Exchange          | Os conectores no local necessitam do Microsoft Exchange 2010 SP3 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração <strong>nova</strong> ou <strong>legada</strong>, contacte o seu gestor de conta. |
| Autoridade de gestão de dispositivos móveis           | [Definir o Intune como a autoridade de gestão de dispositivos móveis](mdm-authority-set.md). |
| Hardware              | O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco. |
|  Sincronização do Active Directory             | Antes de poder utilizar o conector para ligar o Intune ao seu Exchange Server, tem de [configurar a sincronização do Active Directory](users-add.md), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory. |
| Software adicional         | O computador que aloja o conector tem de ter uma instalação completa do Microsoft .NET Framework 4.5 e do Windows PowerShell 2.0. |
| Rede               | O computador em que instalar o conector tem de estar num domínio que tenha uma relação de fidedignidade com o domínio que aloja o seu Exchange Server.<br /><br />O computador requer configurações que lhe permitam aceder ao serviço Intune através de firewalls e servidores proxy pelas Portas 80 e 443. Os domínios que são utilizados pelo Intune incluem manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Crie uma conta de usuário Active Directory que será usada pelo Exchange Connector local. A conta tem de ter permissão para executar os seguintes cmdlets necessários do Windows PowerShell do Exchange:


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

2. Acesse o **Intune** > **Exchange Access**  

3. Em **instalação**, escolha **conector local do Exchange ActiveSync**e, em seguida, selecione **Adicionar**.

4. Na página **Adicionar conector** , selecione **baixar o conector local**. O Exchange Connector local está em uma pasta compactada (. zip) que pode ser aberta ou salva. Na caixa de diálogo **Transferência de Ficheiros**, escolha **Guardar**, para armazenar a pasta comprimida numa localização segura.

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

4. Nos campos **Utilizador (Domínio\utilizador)** e **Palavra-passe**, introduza as credenciais necessárias para se ligar ao seu servidor do Exchange. A conta especificada deve ter uma licença para usar o Intune. 

5. Forneça as credenciais necessárias para enviar notificações para a caixa de correio do Exchange Server de um utilizador. Este utilizador pode ficar dedicado apenas às notificações. O usuário de notificações precisa de uma caixa de correio do Exchange para enviar notificações por email. Pode configurar estas notificações com políticas de Acesso Condicional no Intune.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. No campo **Palavra-passe**, forneça a palavra-passe desta conta para permitir que o Intune aceda ao Exchange Server.

7. Escolha **Ligar**.

   > [!NOTE]
   > Podem ser necessários alguns minutos para que a ligação seja configurada.

Durante a configuração, o Exchange Connector armazena as suas definições de proxy para ativar o acesso à Internet. Se as configurações de proxy forem alteradas, você precisará reconfigurar o Exchange Connector para aplicar as configurações de proxy atualizadas ao Exchange Connector.

Quando o Exchange Connector configurar a ligação, os dispositivos móveis que estão associados a utilizadores geridos no Exchange são automaticamente sincronizados e adicionados ao Exchange Connector. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se instalou o Exchange Connector no local e, a determinada altura, eliminou a ligação ao Exchange, terá de desinstalar o Exchange Connector no local do computador em que foi instalado.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para várias organizações do Exchange
O Intune suporta múltiplos Exchange Connectors no local por subscrição. Para um locatário com várias organizações do Exchange, você pode configurar um conector para cada organização do Exchange, mas apenas um único conector para uma única organização. 

Se você instalar conectores para se conectar a várias organizações do Exchange, baixe a pasta. zip uma vez e reutilize o mesmo download para cada conector que você instalar. Para cada conector adicional, siga as etapas na seção anterior para extrair e executar o programa de instalação em um servidor na organização do Exchange.

Os recursos de alta disponibilidade, monitoramento e sincronização manual descritos nas seções a seguir têm suporte para cada organização do Exchange que se conecta ao Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Suporte de elevada disponibilidade do Exchange Connector no local 
A alta disponibilidade para o Exchange Connector local significa que o servidor de acesso para cliente do Exchange (CAS) que o conector usa se torna indisponível, o conector pode alternar para usar uma CAS diferente para a organização do Exchange. O Exchange Connector em si não dá suporte à alta disponibilidade. Se o conector falhar, não haverá failover automático e você deverá substituir esse conector instalando [um novo conector](#reinstall-the-on-premises-exchange-connector). 

Para realizar o failover, depois que o conector cria uma conexão bem-sucedida com o Exchange usando a CAS especificada, o conector descobre CASs adicionais para a organização do Exchange. O conhecimento de CASs adicionais permite que o conector para failover para outra CAS, se houver um disponível, até que as CAS primárias se tornem disponíveis. Por padrão, a descoberta de CASs adicionais está habilitada. Você pode desativar o failover usando o seguinte procedimento:  
1. No servidor onde o Exchange Connector está instalado, vá para%*ProgramData*% \ Microsoft\Windows Intune Exchange Connector. 
2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Altere &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; para &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para desativar a funcionalidade.  
 
## <a name="optional-performance-tuning-for-the-exchange-connector"></a>Ajuste de desempenho opcional para o Exchange Connector  

Quando você dá suporte a 5.000 ou mais dispositivos com o Exchange ActiveSync, é possível definir uma configuração opcional para melhorar o desempenho do conector. O aumento do desempenho é atingido ao habilitar o Exchange a usar várias instâncias de um espaço de execução de comando do PowerShell. 

Antes de fazer essa alteração, certifique-se de que a conta usada para executar o Exchange Connector não seja usada para outros fins de gerenciamento do Exchange. Isso ocorre porque o Exchange tem um número limitado de espaços de execução por conta, e a maioria deles será usada pelo conector. 

Essa alteração de desempenho não é adequada para conectores que são executados em hardware mais antigo ou mais lento.  

1. No servidor onde o conector está instalado, abra o diretório de instalação de conectores.  O local padrão é o *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Edite o arquivo *OnPremisesExchangeConnectorServiceConfiguration. xml*.
3. Localize **EnableParallelCommandSupport** e defina o valor como **true**:  
     
   \<EnableParallelCommandSupport > true\</EnableParallelCommandSupport >
4. Salve o arquivo e reinicie o Microsoft Intune serviço do Exchange Connector.

## <a name="reinstall-the-on-premises-exchange-connector"></a>Reinstalar o Exchange Connector local
Talvez seja necessário reinstalar um Exchange Connector. Como um único conector tem suporte para se conectar a cada organização do Exchange, se você instalar um segundo conector para uma organização, o novo conector que você instalar substituirá o conector original.

1. Use as etapas em [instalar e configurar o conector do Exchange local do Intune](#install-and-configure-the-intune-on-premises-exchange-connector) para iniciar a instalação do novo conector. 
2. Quando solicitado, selecione **substituir** para instalar o novo conector.  
   ![Prompt de configuração para substituir um conector](./media/exchange-connector-install/prompt-to-replace.png)

3. Continue usando as etapas do procedimento anterior e faça logon no Intune novamente.
4. Quando a tela final for exibida, selecione **fechar** para concluir a instalação.  
   ![Concluir a instalação](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Monitorizar a atividade do conector do Exchange

Depois de configurar com êxito o Exchange Connector, você pode exibir o status das conexões e a última tentativa de sincronização bem-sucedida. Para validar a conexão do Exchange Connector:

1. No painel do Intune, escolha **Exchange Access**.
2. Selecione **Exchange local Access** para verificar o status da conexão de cada conector do Exchange.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.
--> 

### <a name="system-center-operations-manager-management-pack"></a>Pacote de gerenciamento do System Center Operations Manager

A partir da versão 1710 do Intune, você pode usar o [pacote de gerenciamento do Operations Manager para o Exchange Connector e o Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). O uso do pacote de gerenciamento oferece diferentes maneiras de monitorar o Exchange Connector quando você precisa solucionar problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forçar manualmente uma sincronização rápida ou uma sincronização completa
Um conector do Exchange local sincroniza automaticamente os registros de dispositivo EAS e Intune regularmente. Se o status de conformidade de um dispositivo for alterado, o processo de sincronização automática atualizará regularmente os registros para que o acesso ao dispositivo possa ser bloqueado ou permitido.

- **Sincronização rápida** ocorre regularmente, várias vezes ao dia. Uma sincronização rápida recupera informações de dispositivo para usuários de acesso condicional do Exchange com licença e local do Intune que foram alterados desde a última sincronização.

- **Sincronização completa** ocorre uma vez por dia, por predefinição. Uma sincronização completa recupera informações do dispositivo para todos os usuários de acesso condicional do Exchange com licença do Intune e locais. Uma sincronização completa obtém também informações do servidor do Exchange e garante que a configuração especificada pelo Intune no portal do Azure está atualizada no servidor do Exchange. 


Pode forçar a execução de uma sincronização por parte do conector ao utilizar as opções de **Sincronização Rápida** ou **Sincronização Completa** no dashboard do Intune com os seguintes passos:

   1. No painel do Intune, escolha **Exchange Access**.
   2. Selecione **Exchange local Access**.
   3. Selecione o conector que pretende sincronizar e, em seguida, selecione **Sincronização Rápida** ou **Sincronização Completa**.

## <a name="next-steps"></a>Passos Seguintes
[Criar uma política de acesso condicional para o Exchange local](conditional-access-exchange-create.md)
