---
title: Definições de linhas de base de segurança do Intune para a proteção de ameaças avançada do Microsoft Defender
titleSuffix: Microsoft Intune
description: Definições de linha de base de segurança suportadas pelo Intune para gerir a proteção de ameaças avançada do Microsoft Defender
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 837442f93bbac2c5eb19b3c433c91f91aa38a17e
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197535"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Definições de linha de base de proteção do Microsoft Defender avançada contra ameaças para o Intune

Ver as definições de linha de base do Microsoft Defender proteção avançada contra ameaças (anteriormente conhecido como Windows Defender proteção avançada contra ameaças) que são suportadas pelo Microsoft Intune. As predefinições de linha de base da proteção avançada de ameaças (ATP) representam a configuração recomendada para ATP e podem não corresponder aos padrões de linha de base para outras linhas de base de segurança.  

  Linha de base da Microsoft Defender proteção avançada contra ameaças está disponível quando o seu ambiente cumpre os pré-requisitos de utilização [a proteção de ameaças avançada do Microsoft Defender](advanced-threat-protection.md#prerequisites)).




> [!NOTE]  
> As definições de linha de base do ATP estão no **pré-visualização**. Enquanto está em pré-visualização, a lista de definições disponíveis e a ordem em que este conteúdo apresenta essas definições, pode não corresponder aos que estão disponíveis no portal.  
>
> Quando as definições de linha de base do modo de pré-visualização, este conteúdo será atualizado para refletir a lista atual de definições de linha de base de segurança que o Intune suporta.

## <a name="application-guard"></a>Application Guard  
Para obter mais informações, consulte [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) na documentação do Windows.  

Ao utilizar o Microsoft Edge, o Microsoft Defender Application Guard protege o seu ambiente de sites que não são consideradas fidedignas pela sua organização. Quando os utilizadores visitam sites que não estão listados no seu limite de rede isolada, os sites abertos numa sessão de navegação virtual do Hyper-V. Sites fidedignos são definidos por um limite de rede.  

- **Application Guard** - *Settings/AllowWindowsDefenderApplicationGuard*  
  Selecione *Sim* para ativar esta funcionalidade, o que abre sites não fidedignos num contentor de navegação virtualizado Hyper-V. Quando definido como *não configurado*, qualquer site (fidedignos e não fidedignas) abre-se no dispositivo e não num contêiner virtualizado.  

  **Predefinido**: Sim
 
  - **Conteúdo externo em sites de empresa** - *definições/BlockNonEnterpriseContent*  
    Selecione *Sim* para bloquear o conteúdo de sites não aprovados sejam carregados. Quando definido como *não configurado*, sites de não empresariais, podem abrir no dispositivo. 
 
    **Predefinido**: Sim

  - **Comportamento de área de transferência** - *definições/ClipboardSettings*  
    Escolha que ações de copiar e colar são permitidas entre o PC local e o browser virtual do Application Guard.  As opções incluem:
    - *Não configurado*  
    - *Bloquear ambos* -não é possível de transferência de dados entre o PC e o browser virtual.  
    - *Anfitrião de bloco para contentor* -não é possível de transferência de dados do PC no virtual browser.
    - *Contentor de bloco para anfitrião* -dados não é possível transferir a partir do virtual browser para o anfitrião de PC.
    - *Bloquear nenhum* – não bloquear o conteúdo de existência.  

    **Predefinido**: Bloquear ambos  

- **Política de isolamento de rede do Windows – nomes de domínio de rede empresarial**  
  Para obter mais informações, consulte [CSP de política - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) na documentação do Windows.
  
  Especifique uma lista de recursos empresariais como domínios, intervalos de endereços IP e os limites de rede que estão alojados na cloud que o Application Guard trata como sites de empresa.  

  **Predefinido**: securitycenter.windows.com

## <a name="application-reputation"></a>Reputação de aplicação  

Para obter mais informações, consulte [CSP de política - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.

- **Bloquear a execução de ficheiros não verificados**  
    Impedir o utilizador de executar ficheiros não verificados. Quando definido como *não configurado*, os funcionários podem ignorar avisos do SmartScreen e executar ficheiros maliciosos. Defina como *Sim* para que os funcionários não é possível ignorar os avisos do SmartScreen e executar ficheiros maliciosos.  
  
    **Predefinido**: Sim

- **Exigir o SmartScreen para aplicações e ficheiros**  
  Defina como *Sim* para ativar o SmartScreen para Windows.  

  **Predefinido**: Sim

## <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque  

- **Tipo de processo filho de lançamento de aplicações do Office**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – quando definido como *bloco*, aplicações do Office não têm permissão para criar processos de subordinados. Aplicações do Office incluem Word, Excel, PowerPoint, OneNote e acesso. Criação de um processo filho é um comportamento típico de malware, especialmente para ataques baseados na macro que tentam utilizar aplicações do Office para iniciar ou transferir executáveis mal-intencionados.  

  **Predefinido**: Bloquear

- **Script transferido o tipo de execução do payload**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – especificar um nível de deteção de aplicações potencialmente indesejadas que transferir ou tentar instalar.  

  **Predefinido**: Bloquear 

- **Impedir que o tipo de roubo de credenciais**  
  Defina como *ativar* para [derivado de proteger as credenciais de domínio com o Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard). Windows Defender Credential Guard utiliza segurança baseada em virtualização para isolar segredos, permitindo apenas software de sistema com privilégios possam acessá-los. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, tal como Ataques PtH ou PtT. Windows Defender Credential Guard impede estes ataques protegendo os hashes de palavra-passe NTLM, permissão de concessão de permissões Kerberos e as credenciais armazenadas por aplicações como credenciais de domínio.  

  **Predefinido**: Ativar

- **Tipo de execução de conteúdo de e-mail**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – quando definido como *bloco*, este blocos de regra tipos sejam executados ou iniciados a partir de uma mensagem de e-mail vista no Microsoft Outlook ou webmail (como Gmail.com ou Outlook.com) de ficheiros do seguinte:  

  - Ficheiros executáveis (por exemplo, .exe,. dll ou. scr)  
  - Arquivos de script (por exemplo, um .ps do PowerShell, VisualBasic. vbs ou arquivo do JavaScript. js)  
  - Ficheiros de arquivo de script  

  **Predefinido**: Bloquear

- **Lançamento de leitor Adobe num processo filho**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *ativar* esta regra para bloquear o Adobe Reader desde a criação de um processo filho. Por meio de engenharia social ou explorações, malware pode transferir e iniciar payloads adicionais e sair Adobe Reader.  

  **Predefinido**: Ativar

- **Tipo de código de macro de oculto de script**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – software maligno e outras ameaças podem tentar ofuscar ou ocultar o respetivo código malicioso em alguns arquivos de script. Esta regra impede que os scripts que parecem estar ocultado a execução.  
    
  **Predefinido**: Bloquear

- **Tipo de processo USB não fidedigno**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – quando definido como *bloco*, ficheiros do executável não assinado ou não fidedigno de unidades amovíveis de USB e cartões SD não podem ser executado.

  Ficheiros executáveis incluem:
  - Ficheiros executáveis (por exemplo, .exe,. dll ou. scr)
  - Arquivos de script (por exemplo, um .ps do PowerShell, VisualBasic. vbs ou arquivo do JavaScript. js)  

  **Predefinido**: Bloquear

- **Aplicações do Office outros processam o tipo de injeção**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) -quando definido como *bloco*, aplicações do Office, incluindo o Word, Excel, PowerPoint e OneNote, não podem injetar código noutros processos. Injeção de código é normalmente utilizada por software maligno para executar código malicioso numa tentativa de ocultar a atividade de mecanismos de verificação de antivírus.  

  **Predefinido**: Bloquear

- **Código de macro do Office que tipo de importações do Win32**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) -quando definido como *bloco*, esta regra tenta bloquear ficheiros do Office que contêm código de macro que pode importar as Win32 DLLs. Ficheiros do Office incluem Word, Excel, PowerPoint e OneNote. Software maligno pode utilizar o código de macro ficheiros do Office para importar e carregar DLLs Win32, que depois são usados para fazer chamadas de API para permitir a infecção em todo o sistema.  

  **Predefinido**: Bloquear

- **Lançamento de aplicações do Office communication num processo filho**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – quando definido como *ativar*, esta regra impede que o Outlook de criação de processos subordinados. Ao bloquear a criação de um processo filho, esta regra protege contra ataques de engenharia social e impede que o código de exploração abuso de uma vulnerabilidade no Outlook.  

  **Predefinido**: Ativar

- **Office aplicações executável criação ou lançamento tipo de conteúdo**  
  [Regra de redução da superfície de ataque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – quando definido como *bloco*, aplicações do Office não é possível criar conteúdo executável. Aplicações do Office incluem Word, Excel, PowerPoint, OneNote e acesso.  

  Esta regra destina-se comportamentos comuns utilizados por suplementos suspeitos e maliciosos e scripts (extensões), que criam ou iniciar ficheiros executáveis. Essa é uma técnica de malware típico. As extensões são bloqueadas sejam utilizados pelas aplicações do Office. Normalmente, estas extensões usar o Windows Scripting Host (.wsh ficheiros) para executar scripts que automatizar determinadas tarefas ou fornecer funcionalidades de suplemento criados pelo utilizador.

  **Predefinido**: Bloquear

## <a name="bitlocker"></a>BitLocker  

Para obter mais informações, [definições de política de grupo de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) na documentação do Windows.  

- **Encriptar dispositivos**  
  Selecione *Sim* para ativar a encriptação de dispositivo de disco BitLocker. Dependendo do hardware do dispositivo e a versão do Windows, os utilizadores de dispositivos poderão ser-lhe pedidos para confirmar que não existe nenhuma encriptação de terceiros no dispositivo. Ativar a encriptação do Windows enquanto a encriptação de terceiros está ativa processará o dispositivo instável.  

   **Predefinido**: Sim

- **Pouco cacifo unidade amovível política**  
  Os valores para esta política de determinam a força da cifra que utiliza o BitLocker para a encriptação de unidades amovíveis. As empresas a controlam o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se selecionou *Sim* para ativar esta definição, que pode configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada. 

  Para a política de unidade amovível cacifo de Bit, configure as seguintes definições:

    - **Exigir encriptação de acesso de escrita**  
      **Predefinido**: Sim

    - **Método de encriptação**  
      **Predefinido**: AES 128bit CBC

- **Cacifo de bit fixo de política de unidade**  
  Os valores para esta política de determinam a força da cifra que utiliza o BitLocker para a encriptação de unidades fixas. As empresas podem controlar o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se ativar esta definição, pode configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada.

  Para o cacifo de Bit fixo de política de unidade, configure as seguintes definições:

    - **Exigir encriptação de acesso de escrita**  
      **Predefinido**: Sim

    - **Método de encriptação**  
      **Predefinido**: AES de 128 bits XTS

- **Política de unidade de sistema do bit locker**  
  Os valores para esta política de determinam a força da cifra que utiliza o BitLocker para a encriptação de unidade do sistema. As empresas podem querer controlar o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se ativar esta definição, pode configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada.  

  Para a política de unidade de sistema de cacifo de Bit, configure as seguintes definições:  

  - **Método de encriptação**  
    **Predefinido**: AES de 128 bits XTS

## <a name="device-control"></a>Controle de dispositivo  

- **Analisar unidades amovíveis durante uma análise completa**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) -quando definido como *Sim*, Defender verifica a existência de software mal-intencionado e indesejado em unidades amovíveis, como unidades flash, durante uma análise completa. Antivírus do Defender analisa todos os ficheiros em dispositivos USB, antes de podem executar ficheiros no dispositivo USB.

  Configuração relacionada nesta lista: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **Predefinido**: Sim

- **Enumeração de dispositivos externos incompatíveis com a proteção do DMA de Kernel**  
   Ver *DmaGuard/DeviceEnumerationPolicy* no [política CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  Esta política fornece segurança adicional para dispositivos compatíveis com o DMA externos. Ele permite que mais controlo sobre a enumeração de DMA compatível com dispositivos externos que são incompatíveis com o isolamento de memória do dispositivo DMA e áreas de segurança.

  Esta política só tem efeito quando a proteção do DMA de Kernel é suportada e ativada pelo firmware do sistema. Proteção de DMA de kernel é uma funcionalidade de plataforma que não pode ser controlada por política ou pelo utilizador de um dispositivo. Ele precisa ser suportado pelo sistema no momento da produção. 

  Para verificar se o sistema suporta a proteção do DMA de Kernel, execute MSINFO32.exe no sistema e reveja os *Kernel DMA proteção* campo na página de resumo.  

  As opções incluem: 
  - *Predefinição do dispositivo* – após iniciar sessão ou desbloquear o ecrã, dispositivos com o DMA remapear os controladores compatíveis têm permissão para enumerar em qualquer altura. Dispositivos com o DMA controladores incompatíveis o remapeamento só serão enumerados depois do usuário desbloqueia a tela
  - *Permitir que todos os* -todos os externos DMA com capacidade de dispositivos PCIe serão enumerados em qualquer altura
  - *Bloquear todos* -os dispositivos com o DMA remapear os controladores compatíveis têm permissão para enumerar em qualquer altura. Dispositivos com o DMA remapeamento controladores incompatíveis nunca terá permissão para iniciar e executar o DMA em qualquer altura.

  **Predefinido**: Predefinição do dispositivo

- **Instalação de dispositivo de hardware por identificadores de dispositivo**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) -com esta política, é especificar uma lista de IDs de hardware Plug and Play e identificações compatíveis com dispositivos que o Windows é impedidos de instalar. Esta definição de política tem precedência sobre qualquer outra definição de política que permite que o Windows instalar um dispositivo. Se ativar esta definição de política (definido como *bloqueia a instalação de dispositivo de hardware*), Windows é impedidos de instalar um dispositivo cujo ID de hardware ou identificação compatível aparece na lista de criar. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a política afeta o redirecionamento dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desabilitar ou não configurar esta definição de política (definido como *permitir a instalação de dispositivo de hardware*), dispositivos podem instalar e atualizar como permitido ou impedido por outras configurações de diretiva.  

  **Predefinido**: Instalação de dispositivo de hardware de bloco  

  Quando *bloqueia a instalação de dispositivo de hardware* é selecionado, as seguintes definições estão disponíveis.
  - **Remover dispositivos de hardware correspondente**  
    Esta definição só está disponível quando *instalação de dispositivo de Hardware por identificadores de dispositivo* está definida como *bloqueia a instalação de dispositivo de hardware*.  

    **Predefinido**: *Nenhuma configuração predefinida*

  - **Identificadores de dispositivo de hardware que estão bloqueados**  
    Esta definição só está disponível quando *instalação de dispositivo de Hardware por identificadores de dispositivo* está definida como *bloqueia a instalação de dispositivo de hardware*. Para configurar esta definição, expanda a opção, selecione **+ adicionar**, e, em seguida, especifique o identificador de dispositivo de hardware que pretende bloquear.  

    **Predefinido**: *Não existem dispositivos estão bloqueados*  

- **Bloquear acesso direto à memória**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) -Utilize esta definição para bloquear o acesso direto à memória (DMA) para todos os hot conectáveis PCI downstream portas num dispositivo, até que um utilizador inicia sessão no Windows de política. Assim que um utilizador inicia sessão, o Windows irão enumerar os dispositivos PCI ligados as portas PCI do host plug. Sempre que o utilizador bloqueia a máquina, DMA está bloqueado nas portas PCI plug frequente sem dispositivos filhos até que o usuário fizer logon novamente. Dispositivos que já foram enumerados quando a máquina foi desbloqueada continuarão a funcionar até que não-conectado. 

  Esta definição de política é imposta apenas quando a encriptação BitLocker ou o dispositivo está ativada.  

  **Predefinido**: Sim


- **Instalação de dispositivo de hardware por classes de instalação**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) – com esta política pode especificar a classe identificadores globais exclusivos (GUIDs) para que o Windows é impedida a instalação de drivers de dispositivo de configuração de uma lista de dispositivos. Esta definição de política tem precedência sobre qualquer outra definição de política que permite que o Windows instalar um dispositivo. Se ativar esta definição de política (definido como *bloqueia a instalação de dispositivo de hardware*), o Windows é impedidos de instalar ou atualizar controladores de dispositivo GUIDs de classe de configuração de cujo dispositivo aparecem na lista que cria. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a definição de política afeta o redirecionamento dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desabilitar ou não configurar esta definição de política (definido como *permitir a instalação de dispositivo de hardware*), podem instalar o Windows e dispositivos de atualização como permitido ou impediam por outras configurações de diretiva.  

  **Predefinido**: Instalação de dispositivo de hardware de bloco

  Quando *bloqueia a instalação de dispositivo de hardware* é selecionado, as seguintes definições estão disponíveis.  

  - **Remover dispositivos de hardware correspondente**  
    Esta definição só está disponível quando *instalação de dispositivo de Hardware por classes de instalação* está definida como *bloqueia a instalação de dispositivo de hardware*.  
 
    **Predefinido**: *Nenhuma configuração predefinida*  

  - **Identificadores de dispositivo de hardware que estão bloqueados**  
    Esta definição está disponível apenas quando a instalação de dispositivo de Hardware por classes de instalação está configurada para bloquear a instalação de dispositivo de hardware. Para configurar esta definição, expanda a opção, selecione **+ adicionar**, e, em seguida, especifique o identificador de dispositivo de hardware que pretende bloquear.  
 
    **Predefinido**: *Não existem dispositivos estão bloqueados*

## <a name="endpoint-detection-and-response"></a>Ponto final deteção e resposta  
Para obter mais informações, consulte [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) na documentação do Windows.  

- **Acelerar a frequência do relatório de telemetria** - *configuração/TelemetryReportingFrequency*  

  Acelere a frequência do relatório de telemetria de proteção do Microsoft Defender avançada contra ameaças.  

  **Predefinido**: Sim

- **Partilha de amostrar para todos os ficheiros** - *configuração/SampleSharing*  

  Devolve ou define o parâmetro de configuração Microsoft Defender Advanced Threat Protection partilha de amostra.  

  **Predefinido**: Sim

## <a name="exploit-protection"></a>Proteção de exploração  

- **Proteção de exploração XML**  
  Para obter mais informações, consulte [importar, exportar e implantar configurações de proteção de exploração ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml) na documentação do Windows.  

  Permite que o administrador de TI produzir uma configuração que representa o sistema pretendido e as opções de atenuação do aplicativo para todos os dispositivos da organização. A configuração é representada por um XML. 

  Proteção de exploração aplica-se ajuda a proteger os dispositivos contra software maligno que utilize explorações para distribuir e infectar. Utilize a aplicação de segurança do Windows ou o PowerShell para criar um conjunto de atenuações (conhecido como configuração). Em seguida, pode exportar esta configuração como um arquivo XML e partilhe-a com várias máquinas na sua rede para que todos eles têm o mesmo conjunto de definições de atenuação.
 
  Também pode converter e importar um arquivo XML de configuração EMET existente para um XML de configuração da proteção de exploração.

- **Substituição de proteção de exploração de bloco**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – definido como *Sim* para impedir que os utilizadores efetuem alterações para a área de definições de proteção de exploração no Centro de segurança do Windows Defender. Se desabilitar ou não configura esta definição, os usuários locais podem fazer alterações na área de definições de proteção de exploração.  
  **Predefinido**: Sim  

- **Acesso a pastas controladas**  
  Ver [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) e [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) 
  
   Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.

  **Predefinido**: Modo de auditoria

## <a name="web-network-protection"></a>Proteção de rede da Web  

- **Tipo de proteção de rede**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) -esta política permite-lhe ativar ou desativar proteção de rede no Windows Defender Exploit Guard. Proteção de rede é uma funcionalidade do Windows Defender Exploit Guard que protege os funcionários com qualquer aplicação de aceder ao atos fraudulentos de phishing, sites que hospedam a exploração e conteúdo malicioso na Internet. Isto inclui a impedir de browsers de terceiros de ligar a sites perigosos.  

  Quando definida como *habilitar* ou *modo de auditoria*, os utilizadores não é possível desativar a proteção de rede e pode utilizar o Centro de segurança do Windows Defender para ver informações sobre as tentativas de ligação.  
 
  - *Ativar* irá bloquear utilizadores e aplicações de se ligar a domínios perigosos.  
  - *Modo de auditoria* não bloqueia utilizadores e aplicações de se ligar a domínios perigosos.  

  Quando definido como *definidas pelo utilizador*, utilizadores e aplicações não são impedidas de se ligar a domínios perigosos e informações sobre ligações não estão disponíveis no Centro de segurança do Windows Defender.  

  **Predefinido**: Modo de auditoria

- **Exigir o SmartScreen para o Microsoft Edge**  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) -Microsoft Edge utiliza o Windows Defender SmartScreen (ativado) para proteger os usuários contra potenciais atos fraudulentos de phishing e software malicioso por predefinição. Por predefinição, esta política está ativada (definida como *Sim*) e quando ativada impede os utilizadores de desativar o Windows Defender SmartScreen.  Quando a política em vigor a partir de um dispositivo for igual a não configurado, os utilizadores podem desativar Windows Defender SmartScreen, que deixa o dispositivo desprotegido.  

  **Predefinido**: Sim
  
- **Bloquear o acesso do site malicioso**  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) -por predefinição, o Microsoft Edge permite aos utilizadores ignorar (ignorar) os avisos do Windows Defender SmartScreen sobre sites potencialmente maliciosos, que permite aos utilizadores continuar para o site. Com esta política ativada (definida como *Sim*), Microsoft Edge impede que os utilizadores ignorem os avisos e bloqueia-los continue para o site.  

  **Predefinido**: Sim

- **Bloquear a transferência de ficheiros não verificados**  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) -por predefinição, o Microsoft Edge permite aos utilizadores ignorar (ignorar) os avisos do Windows Defender SmartScreen sobre ficheiros potencialmente maliciosos, permitindo que os utilizadores continuem a transferir verificados ficheiros. Com esta política ativada (definida como *Sim*), os utilizadores são impedidos de ignorar os avisos e não é possível transferir os ficheiros não verificados.  

  **Predefinido**: Sim

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Windows Defender antivírus [revisão de definições pendentes para esta secção]

Para obter mais informações, consulte [CSP de política - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.

- **Analisar scripts carregados em browsers da Microsoft**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – definido como *Sim* para permitir a funcionalidade de análise de scripts do Windows Defender.  

  **Predefinido**: Sim

- **Analisar mensagens de correio recebidas**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – definido como *Sim* para permitir que o Windows Defender analisar o e-mail.  

  **Predefinido**: Sim

- **Tipo de consentimento de submissão de exemplo do Defender**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) -nível no Windows Defender para enviar dados de consentimento de verificações para o utilizador. Se já tiver sido concedido o consentimento necessário, o Windows Defender envia-os. Se não for (e se o usuário especificou nunca para perguntar), a interface do Usuário é iniciado para pedir consentimento do utilizador (quando *proteção fornecida pela Cloud* está definida como *Sim*) antes de enviar dados.  

  **Predefinido**: Enviar automaticamente amostras seguras

- **Sistema de inspeção de rede (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) -bloquear tráfego malicioso detetado pelas assinaturas no sistema de inspeção de rede (NIS).  
 
  **Predefinido**: Sim

- **Intervalo de atualização de assinatura (em horas)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – especifique em horas, a frequência com que o dispositivo verifica a existência de novas atualizações de assinatura do Defender.  
 
  **Predefinido**: 4

- **Configurar para análises agendadas de baixa prioridade de CPU**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – quando definido como *Sim*, prioridade de CPU para verificações é definida na opção baixa. Quando *não configurado*, não são efetuadas alterações à prioridade de CPU para análises agendadas.  

    **Predefinido**: Sim

- **Bloco de Defender na proteção de acesso**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – quando definido como *Sim*, Windows Defender na proteção de acesso está ativada.  

  **Predefinido**: Sim

- **Tipo de análise do sistema para executar**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) -tipo de análise de Defender.  

  **Predefinido**: Análise rápida

- **Analisar todas as transferências**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) -quando definido como *Sim*, o Defender analisa todos os ficheiros transferidos e anexos.  

  **Predefinido**: Sim

- **Software maligno em quarentena de dias antes de eliminar**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) -especifique o número de dias a quarentena itens no sistema antes de que sendo automaticamente excluído. Quando definido como zero, itens em quarentena automaticamente nunca são eliminados.  

  **Predefinido**: 0

- **Hora de início da análise agendada**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – agendar uma hora do dia para o Defender analise os dispositivos. 
  
  Opção relacionada nesta lista: *Defender/ScheduleScanDay*   

  **Predefinido**: 2 AM

- **Proteção fornecida pela cloud**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – quando definido como *Sim*, o Windows Defender envia informações à Microsoft sobre quaisquer problemas que encontra. Microsoft irá analisar essas informações, obter mais informações sobre problemas que afetam o utilizador e outros clientes e oferecer soluções aprimoradas.

  Quando esta política está definida como *Sim*, pode utilizar *tipo de consentimento de submissão de exemplo de Defender* para dar aos utilizadores controlo sobre o envio de informações do respetivo dispositivo.  

  **Predefinido**: Sim

- **Defender potencialmente indesejado ação da aplicação**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – Windows Defender Antivirus pode identificar e bloquear *potencialmente indesejável aplicativos* (PUAs) de baixar e instalar em pontos finais na sua rede. 
 
  - Quando definido como *bloco*, o Windows Defender bloqueia PUAs e apresenta uma lista no histórico, juntamente com outras ameaças.
  - Quando definido como *auditoria*, Windows defender Deteta PUAs, mas não bloqueia-los. Pode encontrar informações sobre os aplicativos que do Windows Defender executará alguma ação em relação ao procurar por eventos que foram criados pelo Windows Defender de evento Visualizador.  
  - Quando definido como *predefinição do dispositivo*, proteção de PUA está desativada.  
 
  **Predefinido**: Bloquear

- **Cloud de Defender estendido de tempo limite**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) -especifique a quantidade máxima de tempo adicional que o antivírus do Windows Defender deve bloquear um ficheiro enquanto espera por um resultado da cloud. A quantidade de base de tempo de que espera do Windows Defender é de 10 segundos. Qualquer tempo adicional que especificar aqui (até 50 segundos) é adicionado a esses 10 segundos. Na maioria dos casos, a análise demora menos tempo do que o máximo. Alargar o período de tempo permite que a cloud investigue ficheiros suspeitos de forma mais minuciosa.  

  Por predefinição, o valor de hora expandida é 0 (desativado). Intune recomenda que ative esta definição e especifique, pelo menos, 20 segundos adicionais.  
 
  **Predefinido**: 0

- **Analisar ficheiros de arquivo**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – definido como *Sim* ter o Windows Defender verificar arquivos mortos.  

  **Predefinido**: Sim

- **Agendamento da análise de sistema do Defender**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) -agenda no qual dia Defender analisa os dispositivos. 
 
  Opção relacionada nesta lista: *Defender/ScheduleScanTime*

  **Predefinido**: definido pelo utilizador

- **Monitorização de comportamento**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – definido como *Sim* para ativar a funcionalidade de monitorização de comportamento do Windows Defender. Incorporado no Windows 10, sensores de monitorização de comportamento do Windows Defender recolhem e processam sinais comportamentais do sistema operacional e enviam estes dados de sensor a sua instância de cloud privada, isolados, do Microsoft Defender ATP.  

  **Predefinido**: Sim

- **Analisar ficheiros abertos a partir de pastas de rede**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – definido como *Sim* ter o Windows Defender analise ficheiros em rede. O utilizador não será capaz de remover software maligno detetado a partir de ficheiros só de leitura.  

  **Predefinido**: Sim

- **Nível de bloco de nuvem do Defender**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – Utilize esta política para determinar a agressividade antivírus do Windows Defender está no bloqueio e a análise de ficheiros suspeitos. As opções incluem:

  - Alto - agressivamente bloquear arquivos desconhecidos durante a otimização de desempenho do cliente (chance maior de falsos positivos)
  - Alta plus - agressivamente bloco desconhecido de ficheiros e aplicar medidas de proteção adicional (poderá afetar o desempenho do cliente)
  - Tolerância zero – bloquear todos os ficheiros executáveis desconhecidos

  **Predefinido**: Não Configurado

- **Monitorização em tempo real**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – definido como *Sim* para permitir a monitorização do Windows Defender em tempo real.  

  **Predefinido**: Sim

- **Limite de utilização da CPU durante uma análise**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – especifique a CPU média máxima % de utilização que pode utilizar o Windows Defender durante uma análise.  

  **Predefinido**: 50

- **Analisar unidades de rede mapeadas durante uma análise completa**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) -definido como *Sim* ter o Windows Defender analise ficheiros em rede. O utilizador não é possível remover software maligno detetado a partir dos ficheiros só de leitura,

  Configuração relacionada nesta lista: *Defender/AllowScanningNetworkFiles*

  **Predefinido**: Sim

- **Bloquear o acesso de utilizador final ao Defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – definido como *Sim* para impedir o acesso de utilizadores finais para a interface do Usuário do Windows Defender no respetivo dispositivo.  

  **Predefinido**: Sim

- **Hora de início da análise rápida**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) -agendar uma hora do dia para Defender a executar uma análise rápida.  

  **Predefinido**: 2 AM

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender
Para obter mais informações, consulte [Firewall CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) na documentação do Windows.

- **Tempo de inatividade de associação de segurança antes da eliminação** - *MdmStore/Global/SaIdleTime*   
  As associações de segurança são eliminadas quando o tráfego de rede não é visualizado para este número de segundos.  
  **Predefinido**: 300

- **Protocolo de transferência de ficheiros** - *MdmStore/Global/DisableStatefulFtp*   
  Blocos com monitoração de estado protocolo FTP (File Transfer).  
  **Predefinido**: Sim

- **Pacotes de colocação** - *MdmStore/Global/EnablePacketQueue*    
  Especifique como o dimensionamento para o software do lado da receção está ativado para a receção encriptada e limpar o reencaminhamento de texto para o cenário de gateway de túnel IPsec. Isto garante que o pedido de pacote é preservado.  
  **Predefinido**: Predefinição do dispositivo

- **Domínio do perfil de firewall** - *FirewallRules/FirewallRuleName/perfis*  
  Especifica os perfis ao qual pertence a regra: Domain, Private, Public. Este valor representa o perfil para redes que estão ligados a domínios.  

  Definições disponíveis:  
  - **Respostas unicast às difusões multicast necessários**  
    **Predefinido**: Sim

  - **Regras de aplicação autorizada da diretiva de grupo intercaladas**  
    **Predefinido**: Sim

  - **Notificações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Regras de portas globais da política de grupo intercaladas**  
    **Predefinido**: Sim

  - **Modo invisível bloqueado**  
    **Predefinido**: Sim

  - **Firewall ativada**  
    **Predefinido**: Permitido

  - **Regras de segurança de ligação da política de grupo não intercaladas**  
    **Predefinido**: Sim

  - **Regras de política da política de grupo não intercaladas**  
    **Predefinido**: Sim

- **Perfil público da firewall** - *FirewallRules/FirewallRuleName/perfis*  
  Especifica os perfis ao qual pertence a regra: Domain, Private, Public. Este valor representa o perfil para redes públicas. Estas redes são classificadas como públicas pelos administradores do host de servidor. A classificação aparece na primeira vez que o anfitrião se conecta à rede. Normalmente, estas redes são em aeroportos e cafés e outros locais públicos, onde os elementos de rede na rede ou o administrador de rede não fidedignos.  

  Definições disponíveis:

  - **Ligações de entrada bloqueadas**  
    **Predefinido**: Sim 

  - **Respostas unicast às difusões multicast necessários**  
    **Predefinido**: Sim  

  - **Modo Furtivo necessários**  
    **Predefinido**: Sim 
 
  - **Ligações de saída necessárias**  
    **Predefinido**: Sim  

  - **Regras de aplicação autorizada da diretiva de grupo intercaladas**  
    **Predefinido**: Sim  

  - **Notificações de entrada bloqueadas**  
    **Predefinido**: Sim  

  - **Regras de portas globais da política de grupo intercaladas**  
    **Predefinido**: Sim

  - **Modo invisível bloqueado**  
    **Predefinido**: Sim

  - **Firewall ativada**  
    **Predefinido**: Permitido  

  - **Regras de segurança de ligação da política de grupo não intercaladas**  
    **Predefinido**: Sim  

  - **Tráfego de entrada necessário**  
    **Predefinido**: Sim

  - **Regras de política da política de grupo não intercaladas**  
    **Predefinido**: Sim  

- **Firewall perfil privado** - *FirewallRules/FirewallRuleName/perfis*  
  Especifica os perfis ao qual pertence a regra: Domain, Private, Public. Este valor representa o perfil para redes privadas.  

  Definições disponíveis: 

  - **Ligações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Respostas unicast às difusões multicast necessários**  
    **Predefinido**: Sim

  - **Modo Furtivo necessários**  
    **Predefinido**: Sim

  - **Ligações de saída necessárias**  
    **Predefinido**: Sim

  - **Notificações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Regras de portas globais da política de grupo intercaladas**  
    **Predefinido**: Sim

  - **Modo invisível bloqueado**  
    **Predefinido**: Sim  

  - **Firewall ativada**  
    **Predefinido**: Permitido

  - **Regras de aplicação autorizada da diretiva de grupo não intercaladas**  
    **Predefinido**: Sim

  - **Regras de segurança de ligação da política de grupo não intercaladas**  
    **Predefinido**: Sim

  - **Tráfego de entrada necessário**  
    **Predefinido**: Sim

  - **Regras de política da política de grupo não intercaladas**  
    **Predefinido**: Sim  

- **Pré de firewall partilhada o método de codificação de chave**  
  **Predefinido**: UTF8

- **Verificação de lista de revogação de certificado**  
  **Predefinido**: Predefinição do dispositivo

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas  

Para obter mais informações, consulte [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) na documentação do Windows.

- **Configurar o Windows Hello para empresas** - *TenantId/políticas/UsePassportForWork*    
  Windows Hello para empresas é um método alternativo para iniciar sessão no Windows, substituindo as palavras-passe, Smart Cards e Smart Cards virtuais.  

  Se ativar ou não configurar esta definição de política, o dispositivo Aprovisiona Windows Hello para empresas. Se desativar esta definição de política, o dispositivo não Aprovisiona o Windows Hello para empresas para qualquer utilizador.

  O Intune não suporta desativar Hello do Windows. Em vez disso, pode configurar uma política para ativar o Windows Hello para empresas (Sim) ou não configurar o Windows Hello diretamente (não configurado). Quando não configurada, um dispositivo pode receber a configuração através de outra diretiva, o que pode ativar ou desativar esta funcionalidade.  

  **Predefinido**: Sim  

- **Exigir minúsculas no PIN** - *TenantId/políticas/PINComplexity/LowercaseLetters*  
  **Predefinido**: Permitido  

- **Exigir carateres especiais no PIN** - *TenantId/políticas/PINComplexity/SpecialCharacters*  
  **Predefinido**: Permitido  

- **Exigir maiúsculas no PIN** - *TenantId/políticas/PINComplexity/UppercaseLetters*   
  **Predefinido**: Permitido  

