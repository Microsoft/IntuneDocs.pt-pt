---
title: Configurar Microsoft Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Use o Intune Exchange Connector local para gerenciar o acesso do dispositivo às caixas de correio do Exchange com base no registro e Exchange Active Sync (EAS) do Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/28/2019
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
ms.openlocfilehash: 12c190cad923569e15fd32fe7e5f7f6bd2a45302
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814131"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Configurar o Intune Exchange Connector local
Para ajudar a proteger o acesso ao Exchange, o Intune conta com um componente local que é conhecido como o Microsoft Intune Exchange Connector. Isso também é chamado de *conector local do Exchange ActiveSync* em alguns locais do console do Intune. As informações neste artigo podem ajudá-lo a instalar e monitorar o Intune Exchange Connector, que você usa com suas [políticas de acesso condicional para permitir ou bloquear o acesso às suas caixas de correio locais do Exchange](conditional-access-exchange-create.md). 

O conector é instalado e executado no seu hardware local e é responsável por descobrir dispositivos que se conectam ao Exchange, comunicando informações do dispositivo ao serviço do Intune e permitindo ou bloqueando dispositivos com base em se os dispositivos estão registrados e em conformidade. Essas comunicações são feitas usando o protocolo HTTPS.

Quando um dispositivo tenta acessar seu Exchange local, o Exchange Connector mapeia os registros de Exchange Active Sync (EAS) no Exchange Server para registros do Intune para verificar o registro do dispositivo com o Intune e a conformidade com as políticas de conformidade do dispositivo. Dependendo de suas políticas de acesso condicional, o dispositivo pode ter acesso permitido ou bloqueado. Para obter mais informações, consulte [quais são as maneiras comuns de usar o acesso condicional com o Intune?](conditional-access-intune-common-ways-use.md)

As operações de *descoberta* e de *permissão e bloqueio* são feitas usando cmdlets padrão do Exchange PowerShell. Esses oOperations usam a conta de serviço que é fornecida quando o Exchange Connector é instalado inicialmente. 

O Intune dá suporte à instalação de vários conectores do Exchange do Intune por assinatura. Se você tiver mais de uma organização do Exchange local, poderá configurar um conector separado para cada uma. No entanto, apenas um conector pode ser instalado para uso com cada organização individual do Exchange.  

A seguir estão as etapas gerais para configurar uma conexão que habilita o Intune a se comunicar com o Exchange Server local:

1. Baixe o conector local no portal do Intune.
2. Instale e configure o Exchange Connector num computador na organização do Exchange no local.
3. Valide a ligação ao Exchange.
4. Repita essas etapas para cada organização do Exchange adicional que você deseja conectar ao Intune.

## <a name="intune-exchange-connector-requirements"></a>Requisitos do Intune Exchange Connector

Você precisará de uma conta com uma licença do Intune que possa ser usada pelo conector para se conectar ao Exchange. A conta é especificada quando você instala o conector do.  

A tabela a seguir lista os requisitos para o computador no qual você instala o Intune Exchange Connector.  

|  Requisito  |   Mais informações     |
|---------------|------------------------|
|  Sistemas operativos        | O Intune dá suporte ao Intune Exchange Connector em um computador que executa qualquer edição do Windows Server 2008 SP2 64-bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />Não há suporte para o conector em nenhuma instalação Server Core.  |
| Microsoft Exchange          | Os conectores no local necessitam do Microsoft Exchange 2010 SP3 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração <strong>nova</strong> ou <strong>legada</strong>, contacte o seu gestor de conta. |
| Autoridade de gestão de dispositivos móveis           | [Definir o Intune como a autoridade de gestão de dispositivos móveis](../fundamentals/mdm-authority-set.md). |
| Hardware              | O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco. |
|  Sincronização do Active Directory             | Antes de poder utilizar o conector para ligar o Intune ao seu Exchange Server, tem de [configurar a sincronização do Active Directory](../fundamentals/users-add.md), para que os seus utilizadores e grupos de segurança locais sejam sincronizados com a instância do Azure Active Directory. |
| Software adicional         | O computador que aloja o conector tem de ter uma instalação completa do Microsoft .NET Framework 4.5 e do Windows PowerShell 2.0. |
| Rede               | O computador em que instalar o conector tem de estar num domínio que tenha uma relação de fidedignidade com o domínio que aloja o seu Exchange Server.<br /><br />O computador requer configurações que lhe permitam aceder ao serviço Intune através de firewalls e servidores proxy pelas Portas 80 e 443. Os domínios usados pelo Intune incluem: <br> **-** Manage.Microsoft.com <br> **-** &#42;Manage.Microsoft.com<br> **-** &#42;. Manage.Microsoft.com <br><br> O Intune Exchange Connector se comunica com os seguintes serviços: <br> **-** Serviço do Intune: Porta HTTPS 443 <br> **-** Servidor de acesso para cliente do Exchange (CAS): Porta do serviço WinRM 443<br> **-** Descoberta automática do Exchange 443<br> **-** Serviço de serviços do Exchange (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Crie uma conta de usuário Active Directory que será usada pelo Exchange Connector do Intune. A conta deve ter permissão para executar os seguintes cmdlets do Windows PowerShell Exchange:  

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

## <a name="download-the-intune-exchange-connector-software-installation-package"></a>Baixar o pacote de instalação de software do Intune Exchange Connector

1. Em um servidor Windows que pode dar suporte ao Intune Exchange Connector, entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) com uma conta de usuário que seja um administrador no Exchange Server local e que tenha uma licença para usar o Exchange Server.

2. Acesse o **Intune** > **Exchange Access**  

3. Em **instalação**, escolha **conector local do Exchange ActiveSync**e, em seguida, selecione **Adicionar**.

4. Na página **Adicionar conector** , selecione **baixar o conector local**. O Intune Exchange Connector está em uma pasta compactada (. zip) que pode ser aberta ou salva. Na caixa de diálogo **Transferência de Ficheiros**, escolha **Guardar**, para armazenar a pasta comprimida numa localização segura.


## <a name="install-and-configure-the-intune-exchange-connector"></a>Instalar e configurar o Intune Exchange Connector

Execute as etapas a seguir para instalar o Intune Exchange Connector. Se tiver várias organizações do Exchange, repita estes passos para cada Exchange Connector adicional que pretenda configurar.

1. Em um sistema operacional com suporte para o Intune Exchange Connector, extraia os arquivos em **Exchange_Connector_Setup. zip** para um local seguro.
   > [!IMPORTANT]
   > Não renomeie ou mova os arquivos que estão na pasta Exchange_Connector_Setup Mover ou renomear o conteúdo da pasta fará com que a instalação do conector falhe.

2. Depois que os arquivos forem extraídos, abra a pasta extraída e clique duas vezes em **Exchange_Connector_Setup. exe** para instalar o conector.

   > [!IMPORTANT]
   > Se a pasta de destino não for uma localização segura, deve eliminar o ficheiro de certificado **MicrosoftIntune.accountcert** após a instalação dos conectores no local.

3. Na caixa de diálogo **Microsoft Intune Exchange Connector**, selecione **Microsoft Exchange Server no local** ou **Microsoft Exchange Server alojado**.

   ![Imagem que mostra onde pode escolher o tipo de Exchange Server](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

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

   Certifique-se de que o serviço de Deteção Automática e os Serviços Web Exchange são configurados no Servidor de Acesso de Cliente do Exchange. Para mais informações, consulte o artigo [servidor de Acesso de Cliente](https://technet.microsoft.com/library/dd298114.aspx).

6. No campo **Palavra-passe**, forneça a palavra-passe desta conta para permitir que o Intune aceda ao Exchange Server.

   > [!NOTE]
   > Para que a conexão seja bem-sucedida, a conta que você usa para entrar no locatário precisa ter pelo menos o administrador de serviços do Intune. Sem ele, você receberá uma falha na conexão com o erro: "O servidor remoto retornou um erro: (400) solicitação inadequada ".

7. Escolha **Ligar**.

   > [!NOTE]
   > Podem ser necessários alguns minutos para que a ligação seja configurada.

Durante a configuração, o Exchange Connector armazena as suas definições de proxy para ativar o acesso à Internet. Se as configurações de proxy forem alteradas, reconfigure o Exchange Connector para aplicar as configurações de proxy atualizadas ao Exchange Connector.

Quando o Exchange Connector configurar a ligação, os dispositivos móveis que estão associados a utilizadores geridos no Exchange são automaticamente sincronizados e adicionados ao Exchange Connector. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se você tiver instalado o Intune Exchange Connector e, em algum momento, excluir a conexão do Exchange, será necessário desinstalar o conector do computador no qual ele foi instalado.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para várias organizações do Exchange

O Intune dá suporte a vários conectores do Exchange do Intune por assinatura. Para um locatário com várias organizações do Exchange, você pode configurar um conector para cada organização do Exchange, mas apenas um único conector para uma única organização. 

Se você instalar conectores para se conectar a várias organizações do Exchange, baixe a pasta. zip uma vez e reutilize o mesmo download para cada conector que você instalar. Para cada conector adicional, siga as etapas na seção anterior para extrair e executar o programa de instalação em um servidor na organização do Exchange.

Os recursos de alta disponibilidade, monitoramento e sincronização manual descritos nas seções a seguir têm suporte para cada organização do Exchange que se conecta ao Intune.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Suporte de alta disponibilidade do Intune Exchange Connector local 

Alta disponibilidade para o conector local significa que o servidor de acesso para cliente do Exchange (CAS) que o conector usa se torna indisponível, o conector pode alternar para usar uma CAS diferente para a organização do Exchange. O Exchange Connector em si não dá suporte à alta disponibilidade. Se o conector falhar, não haverá failover automático e você deverá substituir esse conector [instalando um novo conector](#reinstall-the-intune-exchange-connector). 

Para realizar o failover, depois que o conector cria uma conexão bem-sucedida com o Exchange usando a CAS especificada, o conector descobre CASs adicionais para a organização do Exchange. O conhecimento de CASs adicionais permite que o conector para failover para outra CAS, se houver um disponível, até que as CAS primárias se tornem disponíveis. Por padrão, a descoberta de CASs adicionais está habilitada. Você pode desativar o failover usando o seguinte procedimento:  
1. No servidor onde o Exchange Connector está instalado, vá para%*ProgramData*% \ Microsoft\Windows Intune Exchange Connector. 
2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Altere &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; para &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; para desativar a funcionalidade.  
 
## <a name="optional-performance-tuning-for-the-exchange-connector"></a>Ajuste de desempenho opcional para o Exchange Connector  

Quando você dá suporte a 5.000 ou mais dispositivos com o Exchange ActiveSync, é possível definir uma configuração opcional para melhorar o desempenho do conector. O aumento do desempenho é atingido ao habilitar o Exchange a usar várias instâncias de um espaço de execução de comando do PowerShell. 

Antes de fazer essa alteração, certifique-se de que a conta usada para executar o Exchange Connector não seja usada para outros fins de gerenciamento do Exchange. Isso ocorre porque o Exchange tem um número limitado de espaços de execução por conta, sendo que a maioria deles é usada pelo conector. 

Essa alteração de desempenho não é adequada para conectores que são executados em hardware mais antigo ou mais lento.  

1. No servidor onde o conector está instalado, abra o diretório de instalação de conectores.  O local padrão é o *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Edite o arquivo *OnPremisesExchangeConnectorServiceConfiguration. xml*.
3. Localize **EnableParallelCommandSupport** e defina o valor como **true**:  
     
   \<EnableParallelCommandSupport > true\</EnableParallelCommandSupport >
4. Salve o arquivo e reinicie o Microsoft Intune serviço do Exchange Connector.

## <a name="reinstall-the-intune-exchange-connector"></a>Reinstalar o Intune Exchange Connector

Talvez seja necessário reinstalar um Intune Exchange Connector. Como um único conector tem suporte para se conectar a cada organização do Exchange, se você instalar um segundo conector para uma organização, o novo conector que você instalar substituirá o conector original.

1. Use as etapas em [instalar e configurar o Intune Exchange Connector](#install-and-configure-the-intune-exchange-connector) para iniciar a instalação do novo conector. 
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

Um Intune Exchange Connector sincroniza automaticamente os registros de dispositivo EAS e Intune regularmente. Se o status de conformidade de um dispositivo for alterado, o processo de sincronização automática atualizará regularmente os registros para que o acesso ao dispositivo possa ser bloqueado ou permitido.

- **Sincronização rápida** ocorre regularmente, várias vezes ao dia. Uma sincronização rápida recupera informações de dispositivo para usuários de acesso condicional do Exchange com licença e local do Intune que foram alterados desde a última sincronização.

- **Sincronização completa** ocorre uma vez por dia, por predefinição. Uma sincronização completa recupera informações do dispositivo para todos os usuários de acesso condicional do Exchange com licença do Intune e locais. Uma sincronização completa também recupera informações do Exchange Server e garante que a configuração especificada pelo Intune no portal do Azure atualizações no Exchange Server. 


Pode forçar a execução de uma sincronização por parte do conector ao utilizar as opções de **Sincronização Rápida** ou **Sincronização Completa** no dashboard do Intune com os seguintes passos:

   1. No painel do Intune, escolha **Exchange Access**.
   2. Selecione **Exchange local Access**.
   3. Selecione o conector que pretende sincronizar e, em seguida, selecione **Sincronização Rápida** ou **Sincronização Completa**.

## <a name="next-steps"></a>Passos seguintes

[Criar uma política de acesso condicional para o Exchange local](conditional-access-exchange-create.md)
