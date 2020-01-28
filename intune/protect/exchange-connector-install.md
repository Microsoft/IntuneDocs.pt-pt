---
title: Criar um conector Microsoft Intune Exchange
titleSuffix: Microsoft Intune
description: Utilize o conector Intune Exchange no local para gerir o acesso do dispositivo às caixas de correio exchange com base na inscrição intune e exchange ActiveSync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
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
ms.openlocfilehash: 7d00fec5efd9caa54c7f481389e3993e9797699c
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755743"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Configurar o conector Intune Exchange no local

Para ajudar a proteger o acesso ao Exchange, intune baseia-se num componente no local conhecido como conector Microsoft Intune Exchange. Este conector também é chamado de *conector* exchange ActiveSync no local em alguns locais da consola Intune.

As informações deste artigo podem ajudá-lo a instalar e monitorizar o conector Intune Exchange. Pode utilizar o conector com as suas [políticas de acesso condicional](conditional-access-exchange-create.md) para permitir ou bloquear o acesso às suas caixas de correio no local.

O conector está instalado e funciona no hardware no local. Descobre dispositivos que se ligam ao Exchange, comunicando informações do dispositivo ao serviço Intune. O conector permite ou bloqueia dispositivos com base no facto de os dispositivos estarem matriculados e em conformidade. Estas comunicações utilizam o protocolo HTTPS.

Quando um dispositivo tenta aceder ao seu servidor de intercâmbio no local, o conector Exchange mapeia registos Exchange ActiveSync (EAS) em Exchange Server para Intune records para garantir que o dispositivo se inscreve com o Intune e cumpre as políticas do seu dispositivo. Dependendo das suas políticas de acesso condicional, o dispositivo pode ser permitido ou bloqueado. Para mais informações, consulte [Quais são as formas comuns de usar o acesso condicional com Intune?](conditional-access-intune-common-ways-use.md)

Tanto *a descoberta* como as operações de permitir e *bloquear* são feitas utilizando cmdlets padrão exchange PowerShell. Estas operações utilizam a conta de serviço fornecida quando o conector Exchange é inicialmente instalado.

Intune suporta a instalação de vários conectores Intune Exchange por subscrição. Se tiver mais do que uma organização de intercâmbio no local, pode configurar um conector separado para cada um. No entanto, apenas um conector pode ser instalado para cada organização exchange.  

Siga estes passos gerais para estabelecer uma ligação que permite à Intune comunicar com o servidor de intercâmbio no local:

1. Descarregue o conector no local a partir do portal Intune.
2. Instale e configure o Exchange Connector num computador na organização do Exchange no local.
3. Valide a ligação ao Exchange.
4. Repita estes passos para cada organização de intercâmbio adicional que pretende ligar ao Intune.

## <a name="intune-exchange-connector-requirements"></a>Requisitos do conector de intercâmbio intune

Para ligar ao Exchange, precisa de uma conta que tenha uma licença Intune que o conector possa utilizar. Especifica a conta quando instala o conector.  

A tabela seguinte enumera os requisitos para o computador no qual instala o conector Intune Exchange.  

|  Requisito  |   Mais informações     |
|---------------|------------------------|
|  Operating systems        | Intune suporta o conector Intune Exchange num computador que executa qualquer edição do Windows Server 2008 SP2 64-bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />O conector não é suportado em nenhuma instalação do Núcleo do Servidor.  |
| Microsoft Exchange          | Os conectores no local necessitam do Microsoft Exchange 2010 SP3 ou posterior, ou o Exchange Online Dedicado legado. Para determinar se o ambiente dedicado do Exchange Online está na configuração *nova* ou *legada*, contacte o seu gestor de conta. |
| Autoridade de gestão de dispositivos móveis           | [Definir o Intune como a autoridade de gestão de dispositivos móveis](../fundamentals/mdm-authority-set.md). |
| Hardware              | O computador onde irá instalar o conector requer uma CPU de 1,6 GHz com 2 GB de RAM e, pelo menos, 10 GB de espaço livre no disco. |
|  Sincronização do Active Directory             | Antes de utilizar o conector para ligar o Intune ao seu servidor De troca, instale a [sincronização do Diretório Ativo](../fundamentals/users-add.md). Os seus utilizadores locais e grupos de segurança devem ser sincronizados com a sua instância de Diretório Ativo Azure. |
| Software adicional         | O computador que acolhe o conector deve ter uma instalação completa da Microsoft .NET Framework 4.5 e do Windows PowerShell 2.0. |
| Rede               | O computador no qual instala o conector deve estar num domínio que tenha uma relação de confiança com o domínio que acolhe o seu servidor De troca.<br /><br />Configure o computador para permitir o acesso ao serviço Intune através de firewalls e servidores proxy através das portas 80 e 443. Intune usa estes domínios: <br> - manage.microsoft.com <br> -  \*  manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> O conector Intune Exchange comunica com os seguintes serviços: <br> - Serviço insinado: porta HTTPS 443 <br> - Servidor de acesso a clientes de troca (CAS): porta de serviço WinRM 443<br> - Trocar Autodiscover 443<br> - Serviços Web de Intercâmbio (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Requisitos de cmdlets do Exchange

Crie uma conta de utilizador de Diretório Ativo para o conector Intune Exchange. A conta deve ter permissão para executar os seguintes cmdlets de Troca de PowerShell do Windows:  

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

## <a name="download-the-installation-package"></a>Descarregue o pacote de instalação

Num servidor Windows que pode suportar o conector Intune Exchange:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).  Use uma conta que é um administrador no servidor de troca no local e que tem uma licença para usar o Exchange Server.

2. Selecione **a administração do Inquilino** > Exchange **access**.

3. Em **Configuração,** escolha **o conector Exchange ActiveSync no local** e, em seguida, selecione **Adicionar**.

   > [!div class="mx-imgBorder"]
   > ![Adicionar um conector On-Preserção De Intercâmbio ActiveSync no local](./media/exchange-connector-install/add-connector.png)

4. Na página **Add Connector,** selecione **Descarregue o conector no local**. O conector Intune Exchange encontra-se numa pasta comprimido (.zip) que pode ser aberta ou guardada. Na caixa de diálogo **de descarregamento** de ficheiros, escolha **guardar** para armazenar a pasta comprimido num local seguro.

## <a name="install-and-configure-the-intune-exchange-connector"></a>Instale e configure o conector Intune Exchange

Siga estes passos para instalar o conector Intune Exchange. Se tiver várias organizações de Intercâmbio, repita os passos para cada conector de Troca que pretende configurar.

1. Num sistema operativo suportado para o conector Intune Exchange, extrai os ficheiros em **Exchange_Connector_Setup.zip** para um local seguro.
   > [!IMPORTANT]
   > Não mude o nome nem desloque os ficheiros que se encontram na pasta *Exchange_Connector_Setup.* Estas alterações provocariam a falha da instalação do conector.

2. Depois de extraídos os ficheiros, abra a pasta extraída e clique duas vezes **Exchange_Connector_Setup.exe** para instalar o cone.

   > [!IMPORTANT]
   > Se a pasta de destino não for uma localização segura, elimine o ficheiro de certificado *MicrosoftIntune.accountcert* quando terminar a instalação dos seus conectores no local.

3. Na caixa de diálogo **Microsoft Intune Exchange Connector**, selecione **Microsoft Exchange Server no local** ou **Microsoft Exchange Server alojado**.

   ![Imagem que mostra onde pode escolher o tipo de Exchange Server](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Para um servidor do Exchange no local, forneça o nome do servidor ou o nome de domínio completamente qualificado do servidor do Exchange que aloja a função **Servidor de Acesso de Cliente**.

   Para um servidor do Exchange alojado, forneça o endereço do servidor do Exchange. Para localizar o URL do servidor do Exchange alojado:

   1. Open Outlook para o Office 365.

   2. Escolha o ícone **?** ícone no canto superior esquerdo e, em seguida, selecione **Cerca**de .

   3. Localize o valor do **Servidor POP Externo**.

   4. Escolha o **Servidor Proxy** para especificar as definições do servidor proxy do seu servidor do Exchange alojado.

       1. Selecione **Utilizar um servidor proxy ao sincronizar informações de dispositivos móveis**.

       1. Introduza o **nome do servidor proxy** e o **número de porta** a utilizar para aceder ao servidor.

       1. Se forem necessárias credenciais de utilizador para aceder ao servidor proxy, selecione **Use credenciais para se ligar ao servidor proxy**. Em seguida, introduza o **domínio\utilizador** e a **palavra-passe**.

       1. Escolha **OK**.

4. Nos campos **User (domain\user)** e **Password,** introduza credenciais para se ligar ao seu servidor De Troca. A conta que especifica deve ter uma licença para usar o Intune.

5. Forneça credenciais para enviar notificações para a caixa de correio do Exchange Server de um utilizador. Este utilizador pode ficar dedicado apenas às notificações. O utilizador das notificações precisa de uma caixa de correio de troca para enviar notificações por e-mail. Pode configurar estas notificações utilizando políticas de acesso condicional em Intune.

   Certifique-se de que o serviço Autodiscover e os Serviços Web de Troca estão configurados no Exchange CAS. Para mais informações, consulte o artigo [servidor de Acesso de Cliente](https://technet.microsoft.com/library/dd298114.aspx).

6. No campo **Password,** forneça a palavra-passe para esta conta para permitir ao Intune aceder ao servidor 'Exchange'.

   > [!NOTE]
   > A conta que usa para assinar com o inquilino precisa de ser pelo menos um administrador de serviço intune. Sem esta conta de administrador, obterá uma ligação falhada com o erro "O servidor remoto devolveu um erro: (400) Pedido Mau".

7. Escolha **Ligar**.

   > [!NOTE]
   > Pode levar alguns minutos para configurar a ligação.

Durante a configuração, o conector Exchange armazena as definições de procuração para permitir o acesso à internet. Se as definições de procuração mudarem, reconfigure o conector De Troca para aplicar as definições de proxy atualizadas no conector De Troca.

Após o conector Exchange configurar a ligação, os dispositivos móveis que estão associados aos utilizadores geridos pelo Exchange são automaticamente sincronizados e adicionados ao conector Exchange. Esta sincronização poderá demorar algum tempo.

> [!NOTE]
> Se instalar o conector Intune Exchange e, mais tarde, tiver de eliminar a ligação Exchange, tem de desinstalar o conector do computador onde foi instalado.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Instalar conectores para várias organizações do Exchange

Intune suporta vários conectores Intune Exchange por subscrição. Para um inquilino que tem várias organizações de Intercâmbio, você pode configurar apenas um conector para cada organização Exchange.

Para instalar conectores para se ligar a várias organizações de Intercâmbio, descarregue a pasta .zip uma vez. Reutilize o mesmo download para cada conector que instale. Para cada conector adicional, siga os passos na secção anterior para extrair e executar o programa de configuração num servidor da organização Exchange.

Cada organização de Intercâmbio que se conecta ao Intune suporta alta disponibilidade, monitorização e sincronização manual. As seguintes secções descrevem estas características.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>No local, o conector Intune Exchange suporte de alta disponibilidade  

Para o conector no local, a elevada disponibilidade significa que se o EXCHANGE CAS que o conector utiliza ficar indisponível, o conector pode mudar para um CAS diferente para essa organização Exchange. O conector Exchange em si não suporta alta disponibilidade. Se o conector falhar, não haverá falha automática e tem de [instalar um novo conector](#reinstall-the-intune-exchange-connector) para substituir o conector falhado.

Para falhar, o conector utiliza o CAS especificado para criar uma ligação bem sucedida ao Exchange. Em seguida, descobre CASs adicionais para aquela organização exchange. Esta descoberta permite que o conector falhe em outro CAS se um estiver disponível, até que o CAS primário esteja disponível.

Por padrão, a descoberta de CASs adicionais está ativada. Se precisar desligar o failover:

1. No servidor onde o conector Exchange está instalado, vá a **%*ProgramData*%\Microsoft\Windows Intune Exchange Connector**.

2. Através de um editor de texto, abra **OnPremisesExchangeConnectorServiceConfiguration.xml**.

3. Change **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** to **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** .

## <a name="performance-tune-the-exchange-connector-optional"></a>Melodia de desempenho do conector De troca (opcional)

Quando o Exchange ActiveSync suporta 5.000 ou mais dispositivos, pode configurar uma definição opcional para melhorar o desempenho do conector. Melhora o desempenho, permitindo que o Exchange utilize várias instâncias de um espaço de comando PowerShell.

Antes de efetuar esta alteração, certifique-se de que a conta que utiliza para executar o conector Exchange não é utilizada para outros fins de gestão do Exchange. Uma conta Exchange tem um número limitado de espaços de execução, e o conector irá usar a maioria deles.

A afinação de desempenho não é adequada para conectores que funcionam em hardware mais antigo ou mais lento.

Para melhorar o desempenho do conector De troca:

1. No servidor onde o conector instalou, abra o diretório de instalação do conector.  A localização predefinida é *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*.

2. Editar o ficheiro *OnPremisesExchangeConnectorServiceConfiguration.xml*.

3. Localizar suporte de **comando sem paralelo** e definir o valor para **verdadeiro:**

   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>

4. Guarde o ficheiro e, em seguida, reinicie o serviço de conector Microsoft Intune Exchange.

## <a name="reinstall-the-intune-exchange-connector"></a>Reinstalar o conector Intune Exchange

Pode ser necessário reinstalar um conector Intune Exchange. Uma vez que apenas um único conector pode ligar-se a cada organização exchange, se instalar um segundo conector para a organização, o novo conector que instala substitui o conector original.

1. Para instalar o novo conector, siga os passos na secção de instalação e configure a secção de [conector De Troca.](#install-and-configure-the-intune-exchange-connector)

2. Quando for solicitado, **selecione Substitua** para instalar o novo conector.
   ![aviso de configuração para substituir um](./media/exchange-connector-install/prompt-to-replace.png) de conector

3. Continue os passos da [secção de conector Intune Exchange e](#install-and-configure-the-intune-exchange-connector) volte a iniciar o intune.

4. Na janela final, selecione **Feche** para completar a instalação.
   ![completo](./media/exchange-connector-install/successful-reinstall.png) de configuração

## <a name="monitor-an-exchange-connector"></a>Monitorize um conector de intercâmbio

Depois de configurar com sucesso o conector Exchange, pode visualizar o estado das ligações e a última tentativa de sincronização bem sucedida:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > Exchange **access**.

3. Selecione **o conector**no local do Exchange ActiveSync e, em seguida, selecione o conector que pretende ver.

4. A consola apresenta detalhes para o conector que seleciona, onde pode ver o **Estado** e a data e hora da última sincronização bem sucedida.

Além do estado na consola, pode utilizar o pacote de gestão do [System Center Operations Manager para o conector Exchange e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). O pacote de gestão oferece diferentes formas de monitorizar o conector Exchange quando precisa de resolver problemas.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forçar manualmente uma sincronização rápida ou uma sincronização completa

Um conector Intune Exchange sincroniza automaticamente os registos do dispositivo EAS e Intune regularmente. Se o estado de conformidade de um dispositivo mudar, o processo de sincronização automática atualiza regularmente os registos para que o acesso ao dispositivo possa ser bloqueado ou permitido.

- Uma **sincronização rápida** ocorre regularmente, várias vezes ao dia. Uma sincronização rápida recupera informações do dispositivo para utilizadores de intercâmbio licenciados e no local licenciados pela Intune que são direcionados para acesso condicional e que mudaram desde a última sincronização.

- Uma **sincronização completa** ocorre uma vez por dia por padrão. Um sincronismo completo recupera informações do dispositivo para todos os utilizadores de intercâmbio licenciados e no local que são direcionados para acesso condicional. Uma sincronização completa também recupera informações do Exchange Server e garante que a configuração que intune especifica no portal Azure é atualizada no servidor Detroca.

Pode forçar um conector a executar uma sincronização utilizando as opções **Quick Sync** ou **Full Sync** no painel de instrumentos Intune:

   1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

   2. Selecione **a administração do Inquilino** > trocar **acesso** >  trocar o **conector ActiveSync no local**.

   3. Selecione o conector que pretende sincronizar e, em seguida, escolha Quick Sync ou Full Sync.

   > [!div class="mx-imgBorder"]
   > ![Exemplo de imagens dos detalhes do conector](./media/exchange-connector-install/connector-details.png)

## <a name="next-steps"></a>Próximos passos

Criar uma [política de acesso condicional para servidores de intercâmbio no local](conditional-access-exchange-create.md).
