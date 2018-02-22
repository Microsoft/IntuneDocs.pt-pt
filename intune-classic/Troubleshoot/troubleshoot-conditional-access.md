---
title: Resolver problemas de acesso condicional
description: "O que fazer quando os utilizadores não conseguem obter acesso aos recursos através de acesso condicional do Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5f16e14b32508adf1fc4f3f448f53a7dcad8e137
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2018
---
# <a name="troubleshoot-conditional-access"></a>Resolver problemas de acesso condicional

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Normalmente, um utilizador tenta aceder ao e-mail ou ao SharePoint e recebe uma mensagem para se inscrever. Esse pedido direciona o utilizador para o portal da empresa.

Este tópico descreve o que fazer quando os utilizadores não conseguem obter acesso aos recursos através de acesso condicional do Intune.


## <a name="the-basics-for-success-in-conditional-access"></a>Princípios básicos sobre êxito no acesso condicional

Para que o acesso condicional funcione, é necessário respeitar as seguintes condições:

-   O dispositivo tem de ser gerido pelo Intune
-   O dispositivo tem de ser registado no Azure Active Directory (AAD). Em circunstâncias normais, este registo ocorre automaticamente durante a inscrição do Intune
-   O dispositivo tem de estar em conformidade com as políticas de conformidade do Intune, para o dispositivo e para o utilizador do dispositivo.  Se não existirem políticas de conformidade, a inscrição do Intune é suficiente.
-   O Exchange ActiveSync tem de estar ativado no dispositivo se o utilizador tentar obter correio através do cliente de correio nativo do dispositivo, em vez de através do Outlook.     Isto acontece automaticamente em dispositivos iOS, Windows Phone e Android/KNOX Standard.
-   O Intune Exchange Connector deve estar corretamente configurado. Veja [Resolução de Problemas do Exchange Connector no Microsoft Intune](troubleshoot-exchange-connector.md) para obter mais informações.

Estas condições podem ser visualizadas para cada dispositivo no Portal de Gestão do Azure e no relatório de inventário do dispositivo.

## <a name="enrollment-issues"></a>Problemas de inscrição

 -  O dispositivo não está inscrito, pelo que a inscrição irá resolver o problema.
 -  O utilizador inscreveu o dispositivo, mas a associação à área de trabalho falhou. O utilizador deve atualizar a inscrição no portal da empresa.

## <a name="compliance-issues"></a>Resolver problemas de compatibilidade

 -  O dispositivo não está em conformidade com as políticas do Intune. Os problemas comuns são os requisitos de encriptação e palavra-passe. O utilizador será redirecionado para o portal da empresa, onde pode configurar o respetivo dispositivo para estar em conformidade.
 -  Pode demorar algum tempo para que as informações de compatibilidade sejam registadas num dispositivo. Aguarde alguns minutos e tente novamente.
 -  Para dispositivos com iOS:
     -   Um perfil de e-mail existente criado pelo utilizador irá bloquear a implementação de um perfil do Intune criado pelo administrador. Este é um problema comum, uma vez que os utilizadores do iOS criam um perfil de e-mail e depois fazem a inscrição. O portal da empresa irá informar o utilizador da não conformidade devido ao respetivo perfil de e-mail configurado manualmente e solicitará ao utilizador para remover esse perfil. O utilizador deve remover o respetivo perfil de e-mail, para que o perfil do Intune possa ser implementado. Para evitar este problema, indique aos seus utilizadores para inscreverem-se sem instalar um perfil de e-mail e para permitir que o Intune implemente o perfil.
     -   Um dispositivo iOS pode ficar bloqueado num estado de verificação de conformidade, impedindo que o utilizador inicie outra verificação. Reiniciar o portal da empresa pode corrigir este problema e o estado de conformidade irá refletir o estado do dispositivo no Intune. Após todos os dados terem sido recolhidos a partir de uma sincronização do dispositivo, a verificação de conformidade é rápida, cerca de meio segundo em média.

        Normalmente, a razão pela qual os dispositivos se mantêm neste estado é terem problemas de ligação ao serviço ou de sincronização a demorar muito tempo.  Se o problema persistir em diferentes configurações de rede (dados móveis, Wi-Fi, VPN), após reiniciar o dispositivo e depois de verificar que o SSP está atualizado no dispositivo, contacte o Suporte da Microsoft conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

 - Para dispositivos Android:
    - É possível que certos dispositivos Android pareçam estar encriptados, mas que a aplicação Portal da Empresa reconheça estes dispositivos como não encriptados. 
    
        -   Os dispositivos que se encontrarem neste estado necessitam que o utilizador defina um código de acesso de arranque seguro. O utilizador verá uma notificação de dispositivo da aplicação Portal da Empresa que pede para definir um código de acesso para o dispositivo. Depois de tocar na notificação de dispositivo e confirmar a palavra-passe ou PIN existente, selecione a opção **Require PIN to start device (Exigir PIN para iniciar o dispositivo)** no ecrã **Secure start-up (Arranque seguro)**. Em seguida, toque no botão **Check Compliance (Verificar Conformidade)** do dispositivo na aplicação Portal da Empresa. O dispositivo deverá ser detetado como encriptado agora.
    
        -   Alguns fabricantes de dispositivos encriptam os seus dispositivos através de um PIN predefinido em vez do PIN secreto definido pelo utilizador. O Intune reconhece a encriptação de dispositivos com o PIN predefinido como não sendo segura, dado que este método de encriptação pode colocar os dados do dispositivo em risco de serem acedidos fisicamente por utilizadores mal-intencionados. Se for este o problema, pondere utilizar [políticas de proteção de aplicações](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies).

## <a name="policy-issues"></a>Problemas de políticas

Quando cria uma política de conformidade e associa-a a uma política de e-mail, ambas as políticas têm de ser implementadas para o mesmo utilizador, por isso tenha cuidado quando planear que políticas devem ser implementadas para os grupos. É provável que os utilizadores que tenham apenas uma política aplicada verifiquem que os seus dispositivos não são conformes.


## <a name="exchange-activesync-issues"></a>Problemas do Exchange ActiveSync

### <a name="compliant-android-device-gets-quarantine-notice"></a>Dispositivo Android conforme recebe aviso de quarentena
- Um dispositivo Android inscrito e conforme poderá receber um aviso de quarentena quando tentar aceder a recursos empresariais. Antes de escolher a ligação que indica **Começar**, o utilizador deve certificar-se de que o portal da empresa não estava aberto quando tentou aceder aos recursos. Os utilizadores devem fechar o portal da empresa, tentar aceder de novo aos recursos e, em seguida, selecionar a ligação **Começar**.

### <a name="retired-device-continues-to-have-access"></a>O dispositivo extinto continua a ter acesso.
- Quando utilizar o Exchange Online, um dispositivo extinto pode continuar a ter acesso várias horas depois de ser retirado. Isto acontece porque o Exchange coloca os direitos de acesso à memória cache a cada 6 horas. Considere outros meios de proteger dados em dispositivos extintos neste cenário.

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>O dispositivo está em conformidade e registado no AAD, mas permanece bloqueado
- Por vezes, o aprovisionamento do Exchange ActiveSync ID (EASID) para o AAD está atrasado. Uma causa comum deste problema é a limitação, por isso, aguarde alguns minutos e tente novamente.

### <a name="device-blocked"></a>Dispositivo bloqueado

Um dispositivo pode ser bloqueado no Acesso Condicional sem receber um e-mail de ativação.

- Existe uma regra do Exchange predefinida que bloqueie ou coloque dispositivos em quarentena? Se uma regra predefinida bloquear ou colocar dispositivos em quarentena, os dispositivos não poderão receber o e-mail de ativação do Exchange Connector. Isto é propositado.
- A conta de notificação está configurada corretamente conforme descrito na configuração Básica?
- O dispositivo está presente na consola de administração do Intune como um dispositivo do Exchange ActiveSync? Se não estiver, a deteção de dispositivos pode estar a falhar, provavelmente devido a um problema de sincronização do Exchange Connector. Verifique se o dispositivo do Exchange ActiveSync não foi detetado a partir do Exchange.
- Verifique os registos do Exchange Connector para a atividade de sendemail e procure a existência de erros. Um exemplo do comando a procurar é SendEmail da conta de notificação para useremail.
- Antes do Exchange Connector bloquear o dispositivo, envia o e-mail de ativação. Se o dispositivo estiver offline, poderá não receber o e-mail de ativação. Verifique se o cliente de e-mail do dispositivo tem a obtenção de e-mail através de Push em vez de Poll, uma vez que isto também pode fazer com que o utilizador não receba o e-mail. Mude para Poll e verifique se o dispositivo recebe o e-mail.

## <a name="noncompliant-device-not-blocked"></a>Dispositivo não conforme não bloqueado

Se tiver um dispositivo que não esteja em conformidade mas continue a ter acesso, siga os passos seguintes.

- Reveja os grupos de Destino e Exclusão. Se um utilizador não estiver no grupo de destino certo ou estiver no grupo de exclusão, não será bloqueado. Apenas os dispositivos de utilizadores num grupo de Destino são verificados relativamente à conformidade.
- Certifique-se de que o dispositivo está a ser detetado. O Exchange Connector está a apontar para um CAS do Exchange 2010 enquanto o utilizador está num servidor do Exchange 2013? Neste caso, se a regra do Exchange predefinida for Permitir, mesmo que o utilizador esteja no grupo de Destino, o Intune não pode ter conhecimento da ligação do dispositivo ao Exchange.
- Verifique o estado de Existência/Acesso do Dispositivo no Exchange:
    - Utilize este cmdlet do PowerShell para obter uma lista de todos os dispositivos móveis para uma caixa de correio: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Se o dispositivo não estiver listado, é porque não está a aceder ao Exchange.
    - Se o dispositivo estiver listado, utilize o cmdlet Get-CASmailbox -identity:’upn’ | fl para obter informações detalhadas sobre o respetivo estado de acesso e fornecer essas informações ao Suporte da Microsoft.

## <a name="before-you-open-a-support-ticket"></a>Antes de abrir um pedido de suporte
Se estes procedimentos não resolverem o problema, o Suporte da Microsoft pode pedir-lhe determinadas informações, como os registos de caixa de correio do OWA ou os registos do Exchange Connector.

### <a name="collecting-owa-mailbox-logs"></a>Recolher registos de caixa de correio do OWA

1. Inicie sessão através do OWA e escolha o símbolo de definições (engrenagem) junto ao seu nome no canto superior direito.
2. Selecione **Opções**
3. Selecione **Telemóvel** (poderá ser **Dispositivos Móveis**) na coluna no lado esquerdo.
4. No menu superior, selecione **Dispositivos Móveis**.
5. Escolha o seu dispositivo da lista e, em seguida, escolha **Iniciar o registo**.
6. Quando for solicitado, selecione **Sim** na caixa de diálogo de pop-up.
7. Execute a ação que causou o problema, para que possa reproduzi-la.
8. Aguarde 1 a 2 minutos e depois volte para a lista telefónica no OWA. Certifique-se de que o seu telemóvel está selecionado na lista e, no menu superior, escolha **Obter Registo**.
9. Deverá receber um e-mail enviado por si com um anexo. Quando abre um pedido de suporte, forneça o conteúdo do e-mail ao Suporte da Microsoft.

### <a name="exchange-connector-logs"></a>Registos do Exchange Connector

#### <a name="general-log-information"></a>Informações gerais de registo
Para ver que registos do Exchange Connector utilizam a [Ferramenta Visualizador de Rastreio do Servidor](ferramenta visualizador de rastreio do servidor (https://msdn.microsoft.com/library/ms732023(v=vs.110).aspx'). Esta ferramenta requer que transfira o SDK do Windows Server.

>[!NOTE]
>Os registos estão localizados em C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs. Os registos estão contidos numa série de 30 ficheiros de registo com início em *Connector0.log* e fim em *Connector29.log*. Os registos passam de um para outro após terem sido acumulados 10 MB de dados num registo. Depois de os registos chegarem a Connector29, vão recomeçar novamente em Connector0, substituindo os ficheiros de registo anteriores.

#### <a name="locating-sync-logs"></a>Localizar registos de sincronização

-    Localize uma sincronização completa nos registos ao procurar **full sync**. O início de uma sincronização completa estará marcado pelo seguinte texto:

    'Handling command: Getting the mobile device list without a time filter (full sync) for <number> users`

    O fim do registo de uma sincronização completa tem o seguinte aspeto:

    Getting the mobile device list without a time filter (full sync) for 4 users completed successfully. Details: Inventory command result - Devices synced: 0 Command ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected','

-   Localize uma sincronização (delta) rápida nos registos ao procurar **quick sync**.

##### <a name="exceptions-in-get-next-command"></a>Exceções no comando Get next
Consulte os registos do Exchange Connector para obter as exceções no **comando Get next** e forneça-as ao Suporte da Microsoft.

#### <a name="verbose-logging"></a>Registo verboso

Para ativar o registo verboso:

1.  Abra o ficheiro de configuração de rastreio do Exchange Connector. O ficheiro está localizado em: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml.
2.  Localize o TraceSourceLine com a seguinte chave: OnPremisesExchangeConnectorService
3.  Altere o valor do nó **SourceLevel** de **Warning ActivityTracing** (predefinição) para **Verbose ActivityTracing**, conforme mostrado abaixo.

    <TraceSourceLine> <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key> <Value xsi:type="TraceSource"> <SourceLevel>Todos</SourceLevel> <Listeners> <Listener> <ListenerType>CircularTraceListener</ListenerType> <SourceLevel>Verbose ActivityTracing</SourceLevel> <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes> <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName> <FileQuota>30</FileQuota> </Listener> </Listeners> </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>Próximos passos
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
