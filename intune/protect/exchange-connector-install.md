---
title: Configurar um conector do Exchange Microsoft Intune
titleSuffix: Microsoft Intune
description: Use o Intune Exchange Connector local para gerenciar o acesso do dispositivo às caixas de correio do Exchange com base no registro do Intune e no EAS (Exchange ActiveSync).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30b5debc6e1ab113a08d8930f96f6cbc9bf12b48
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509530"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Configurar o Intune Exchange Connector local
Para ajudar a proteger o acesso ao Exchange, o Intune conta com um componente local que é conhecido como o conector do Exchange Microsoft Intune. Esse conector também é chamado de *conector local do Exchange ActiveSync* em alguns locais do console do Intune. 

As informações neste artigo podem ajudá-lo a instalar e monitorar o Intune Exchange Connector. Você pode usar o conector com suas [políticas de acesso condicional](conditional-access-exchange-create.md) para permitir ou bloquear o acesso às suas caixas de correio locais do Exchange. 

O conector é instalado e executado em seu hardware local. Ele descobre os dispositivos que se conectam ao Exchange, comunicando as informações do dispositivo ao serviço do Intune. O conector permite ou bloqueia dispositivos com base no fato de os dispositivos estarem registrados e em conformidade. Essas comunicações usam o protocolo HTTPS.

Quando um dispositivo tenta acessar o Exchange Server local, o Exchange Connector mapeia registros do Exchange ActiveSync (EAS) no Exchange Server para registros do Intune para verificar se o dispositivo está registrado no Intune e está em conformidade com as políticas do dispositivo. Dependendo das políticas de acesso condicional, o dispositivo poderá ser permitido ou bloqueado. Para obter mais informações, consulte [quais são as maneiras comuns de usar o acesso condicional com o Intune?](conditional-access-intune-common-ways-use.md)

As operações de *descoberta* e de *permissão e bloqueio* são feitas usando cmdlets padrão do Exchange PowerShell. Essas operações usam a conta de serviço que é fornecida quando o Exchange Connector é instalado inicialmente. 

O Intune dá suporte à instalação de vários conectores do Exchange do Intune por assinatura. Se você tiver mais de uma organização do Exchange local, poderá configurar um conector separado para cada uma. No entanto, apenas um conector pode ser instalado para cada organização do Exchange.  

Siga estas etapas gerais para configurar uma conexão que habilita o Intune a se comunicar com o Exchange Server local:

1. Baixe o conector local no portal do Intune.
2. Instale e configure o Exchange Connector num computador na organização do Exchange no local.
3. Valide a ligação ao Exchange.
4. Repita essas etapas para cada organização do Exchange adicional que você deseja conectar ao Intune.

## <a name="intune-exchange-connector-requirements"></a>Requisitos do Intune Exchange Connector

Para se conectar ao Exchange, você precisa de uma conta que tenha uma licença do Intune que o conector possa usar. Você especifica a conta ao instalar o conector do.  

A tabela a seguir lista os requisitos para o computador no qual você instala o Intune Exchange Connector.  

|  Requisito  |   Mais informações     |
|---------------|------------------------|
|  Operating systems        | O Intune dá suporte ao Intune Exchange Connector em um computador que executa qualquer edição do Windows Server 2008 SP2 64-bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />Não há suporte para o conector em nenhuma instalação Server Core.  |
| Microsoft Exchange          | Os conectores no local necessitam do Microsoft Exchange 2010 SP3 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração *nova* ou *legada*, contacte o seu gestor de conta. |
| Autoridade de gestão de dispositivos móveis           | [Definir o Intune como a autoridade de gestão de dispositivos móveis](../fundamentals/mdm-authority-set.md). |
| Hardware              | O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco. |
|  Sincronização do Active Directory             | Antes de usar o conector para conectar o Intune ao seu Exchange Server, [configure Active Directory sincronização](../fundamentals/users-add.md). Os usuários e grupos de segurança locais devem ser sincronizados com sua instância do Azure Active Directory. |
| Software adicional         | O computador que hospeda o conector deve ter uma instalação completa do Microsoft .NET Framework 4,5 e do Windows PowerShell 2,0. |
| Rede               | O computador no qual você instala o conector deve estar em um domínio que tenha uma relação de confiança com o domínio que hospeda o Exchange Server.<br /><br />Configure o computador para permitir que ele acesse o serviço do Intune por meio de firewalls e servidores proxy nas portas 80 e 443. O Intune usa estes domínios: <br> -manage.microsoft.com <br> @no__t -0\*manage.microsoft.com<br> @no__t -0\*.manage.microsoft.com <br><br> O Intune Exchange Connector se comunica com os seguintes serviços: <br> -Serviço do Intune: porta HTTPS 443 <br> -Servidor de acesso para cliente do Exchange (CAS): porta do serviço WinRM 443<br> -Descoberta automática do Exchange 443<br> -Serviços Web do Exchange (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Crie uma conta de usuário Active Directory para o Intune Exchange Connector. A conta deve ter permissão para executar os seguintes cmdlets do Windows PowerShell Exchange:  

- `Get-ActiveSyncOrganizationSettings`, `Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`, `Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`, `Set-ActiveSyncMailboxPolicy`, `New-ActiveSyncMailboxPolicy`, `Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`, `Set-ActiveSyncDeviceAccessRule`, `New-ActiveSyncDeviceAccessRule`, `Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`, `Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>Baixar o pacote de instalação

1. Em um servidor Windows que pode dar suporte ao Intune Exchange Connector, entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Use uma conta que seja um administrador no Exchange Server local e que tenha uma licença para usar o Exchange Server.

2. Acesse **Intune** > **acesso ao Exchange**.  

3. Em **instalação**, escolha **conector local do Exchange ActiveSync** e, em seguida, selecione **Adicionar**.

4. Na página **Adicionar conector** , selecione **baixar o conector local**. O Intune Exchange Connector está em uma pasta compactada (. zip) que pode ser aberta ou salva. Na caixa de diálogo **download de arquivo** , escolha **salvar** para armazenar a pasta compactada em um local seguro.


## <a name="install-and-configure-the-intune-exchange-connector"></a>Instalar e configurar o Intune Exchange Connector

Siga estas etapas para instalar o Intune Exchange Connector. Se você tiver várias organizações do Exchange, repita as etapas para cada conector do Exchange que você deseja configurar.

1. Em um sistema operacional com suporte para o Intune Exchange Connector, extraia os arquivos em **Exchange_Connector_Setup. zip** para um local seguro.
   > [!IMPORTANT]
   > Não renomeie ou mova os arquivos que estão na pasta *Exchange_Connector_Setup* Essas alterações podem fazer com que a instalação do conector falhe.

2. Depois que os arquivos forem extraídos, abra a pasta extraída e clique duas vezes em **Exchange_Connector_Setup. exe** para instalar o conector.

   > [!IMPORTANT]
   > Se a pasta de destino não for um local seguro, exclua o arquivo de certificado *MicrosoftIntune. accountcert* ao concluir a instalação de seus conectores locais.

3. Na caixa de diálogo **Microsoft Intune Exchange Connector**, selecione **Microsoft Exchange Server no local** ou **Microsoft Exchange Server alojado**.

   ![Imagem que mostra onde pode escolher o tipo de Exchange Server](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Para um servidor do Exchange no local, forneça o nome do servidor ou o nome de domínio completamente qualificado do servidor do Exchange que aloja a função **Servidor de Acesso de Cliente**.

   Para um servidor do Exchange alojado, forneça o endereço do servidor do Exchange. Para localizar o URL do servidor do Exchange alojado:

   1. Abra o Outlook para Office 365.

   2. Escolha o ícone **?** no canto superior esquerdo e, em seguida, selecione **sobre**.

   3. Localize o valor do **Servidor POP Externo**.

   4. Escolha o **Servidor Proxy** para especificar as definições do servidor proxy do seu servidor do Exchange alojado.

       1. Selecione **Utilizar um servidor proxy ao sincronizar informações de dispositivos móveis**.

       1. Introduza o **nome do servidor proxy** e o **número de porta** a utilizar para aceder ao servidor.

       1. Se as credenciais do usuário forem necessárias para acessar o servidor proxy, selecione **usar credenciais para se conectar ao servidor proxy**. Em seguida, introduza o **domínio\utilizador** e a **palavra-passe**.

       1. Escolha **OK**.

4. Nos campos **User (domínio \ usuário)** e **password** , insira as credenciais para se conectar ao Exchange Server. A conta especificada deve ter uma licença para usar o Intune. 

5. Forneça credenciais para enviar notificações para a caixa de correio do Exchange Server de um usuário. Este utilizador pode ficar dedicado apenas às notificações. O usuário de notificações precisa de uma caixa de correio do Exchange para enviar notificações por email. Você pode configurar essas notificações usando políticas de acesso condicional no Intune.  

   Verifique se o serviço descoberta automática e os serviços Web do Exchange estão configurados nas CAS do Exchange. Para mais informações, consulte o artigo [servidor de Acesso de Cliente](https://technet.microsoft.com/library/dd298114.aspx).

6. No campo **senha** , forneça a senha dessa conta para habilitar o Intune a acessar o Exchange Server.

   > [!NOTE]
   > A conta usada para entrar no locatário precisa ser pelo menos um administrador de serviços do Intune. Sem essa conta de administrador, você receberá uma falha de conexão com o erro "o servidor remoto retornou um erro: (400) solicitação inadequada".

7. Escolha **Ligar**.

   > [!NOTE]
   > Pode levar alguns minutos para configurar a conexão.

Durante a configuração, o Exchange Connector armazena as configurações de proxy para habilitar o acesso à Internet. Se as configurações de proxy forem alteradas, reconfigure o Exchange Connector para aplicar as configurações de proxy atualizadas ao Exchange Connector.

Depois que o Exchange Connector configura a conexão, os dispositivos móveis associados aos usuários gerenciados pelo Exchange são automaticamente sincronizados e adicionados ao Exchange Connector. Essa sincronização pode levar algum tempo para ser concluída.

> [!NOTE]
> Se você instalar o Intune Exchange Connector e posteriormente precisar excluir a conexão do Exchange, será necessário desinstalar o conector do computador em que ele foi instalado.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para várias organizações do Exchange

O Intune dá suporte a vários conectores do Exchange do Intune por assinatura. Para um locatário que tem várias organizações do Exchange, você pode configurar apenas um conector para cada organização do Exchange. 

Para instalar conectores para se conectar a várias organizações do Exchange, baixe a pasta. zip uma vez. Reutilize esse mesmo download para cada conector que você instalar. Para cada conector adicional, siga as etapas na seção anterior para extrair e executar o programa de instalação em um servidor na organização do Exchange.

Cada organização do Exchange que se conecta ao Intune dá suporte à alta disponibilidade, ao monitoramento e à sincronização manual. As seções a seguir descrevem esses recursos.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Suporte de alta disponibilidade do Intune Exchange Connector local  

Para o conector local, a alta disponibilidade significa que, se as CAS do Exchange que o conector usa se tornarem indisponíveis, o conector poderá mudar para uma CAS diferente para a organização do Exchange. O Exchange Connector em si não dá suporte à alta disponibilidade. Se o conector falhar, não haverá nenhum failover automático. Você deve [instalar um novo conector](#reinstall-the-intune-exchange-connector) para substituir o conector com falha. 

Para fazer failover, o conector usa as CAS especificadas para criar uma conexão bem-sucedida com o Exchange. Em seguida, ele descobre CASs adicionais para a organização do Exchange. Essa descoberta permite que o conector faça failover para outra CAS, se houver uma disponível, até que as CAS primárias se tornem disponíveis. 

Por padrão, a descoberta de CASs adicionais está habilitada. Se você precisar desativar o failover:  
1. No servidor onde o Exchange Connector está instalado, acesse **%*ProgramData*% \ Microsoft\Windows Intune Exchange Connector**. 
2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Altere **\<IsCasFailoverEnabled >*true*\</IsCasFailoverEnabled >** para **\<IsCasFailoverEnabled >*false*\</IsCasFailoverEnabled >** .  
 
## <a name="performance-tune-the-exchange-connector-optional"></a>Ajuste de desempenho do Exchange Connector (opcional)

Quando o Exchange ActiveSync dá suporte a 5.000 ou mais dispositivos, você pode definir uma configuração opcional para melhorar o desempenho do conector. Você melhora o desempenho habilitando o Exchange a usar várias instâncias de um espaço de execução de comando do PowerShell. 

Antes de fazer essa alteração, certifique-se de que a conta usada para executar o Exchange Connector não seja usada para outros fins de gerenciamento do Exchange. Uma conta do Exchange tem um número limitado de espaços de execução e o conector usará a maioria deles. 

O ajuste de desempenho não é adequado para conectores que são executados em hardware mais antigo ou mais lento.  

Para melhorar o desempenho do Exchange Connector: 

1. No servidor em que o conector do está instalado, abra o diretório de instalação do conector.  O local padrão é o *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Edite o arquivo *OnPremisesExchangeConnectorServiceConfiguration. xml*.
3. Localize **EnableParallelCommandSupport** e defina o valor como **true**:  
     
   \<EnableParallelCommandSupport > true @ no__t-1/EnableParallelCommandSupport >
4. Salve o arquivo e reinicie o Microsoft Intune serviço do Exchange Connector.

## <a name="reinstall-the-intune-exchange-connector"></a>Reinstalar o Intune Exchange Connector

Talvez seja necessário reinstalar um Intune Exchange Connector. Como apenas um único conector pode se conectar a cada organização do Exchange, se você instalar um segundo conector para a organização, o novo conector que você instalar substituirá o conector original.

1. Para instalar o novo conector, siga as etapas na seção [instalar e configurar o Exchange Connector](#install-and-configure-the-intune-exchange-connector) . 
2. Quando solicitado, selecione **substituir** para instalar o novo conector.  
   aviso de ![Configuration para substituir um conector @ no__t-1

3. Continue as etapas da seção [instalar e configurar o Intune Exchange Connector](#install-and-configure-the-intune-exchange-connector) e entre no Intune novamente.
4. Na janela final, selecione **fechar** para concluir a instalação.  
   instalação do ![Finish @ no__t-1
 

## <a name="monitor-an-exchange-connector"></a>Monitorar um Exchange Connector

Depois de configurar com êxito o Exchange Connector, você pode exibir o status das conexões e a última tentativa de sincronização bem-sucedida. 

Para validar a conexão do Exchange Connector:

1. No painel do Intune, escolha **Exchange Access**.
2. Selecione **Exchange local Access** para verificar o status da conexão de cada conector do Exchange.

Também pode ver a data e hora da última tentativa de sincronização efetuada com êxito.

A partir da versão 1710 do Intune, você pode usar o [pacote de gerenciamento do System Center Operations Manager para o Exchange Connector e o Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). O pacote de gerenciamento oferece diferentes maneiras de monitorar o Exchange Connector quando você precisa solucionar problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forçar manualmente uma sincronização rápida ou uma sincronização completa

Um Intune Exchange Connector sincroniza automaticamente os registros de dispositivo EAS e Intune regularmente. Se o status de conformidade de um dispositivo for alterado, o processo de sincronização automática atualizará regularmente os registros para que o acesso ao dispositivo possa ser bloqueado ou permitido.

- Uma **sincronização rápida** ocorre regularmente, várias vezes por dia. Uma sincronização rápida recupera informações de dispositivo para usuários do Exchange no local e licenciados para o Intune que são direcionados para acesso condicional e que foram alterados desde a última sincronização.

- Uma **sincronização completa** ocorre uma vez por dia por padrão. Uma sincronização completa recupera informações do dispositivo para todos os usuários do Exchange com licença do Intune e locais que são direcionados para acesso condicional. Uma sincronização completa também recupera informações do Exchange Server e garante que a configuração que o Intune especifica na portal do Azure seja atualizada no Exchange Server. 


Você pode forçar um conector a executar uma sincronização usando as opções **sincronização rápida** ou **sincronização completa** no painel do Intune:

   1. No painel do Intune, escolha **Exchange Access**.
   2. Selecione **Exchange local Access**.
   3. Selecione o conector que pretende sincronizar e, em seguida, selecione **Sincronização Rápida** ou **Sincronização Completa**.

## <a name="next-steps"></a>Próximos passos

Crie uma [política de acesso condicional para servidores Exchange locais](conditional-access-exchange-create.md).
