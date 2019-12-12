---
title: Configurações de linhas de base de segurança do Intune para proteção avançada contra ameaças do Microsoft defender
titleSuffix: Microsoft Intune
description: Configurações de linha de base de segurança com suporte do Intune para gerenciar a proteção avançada contra ameaças do Microsoft defender
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85d0b28de6c133ece5116dd78b1646f497ff2f6b
ms.sourcegitcommit: 0a85af9d584709ecc29062f91645a4c47a61ebb9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2019
ms.locfileid: "74882330"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Configurações de linha de base de proteção avançada contra ameaças do Microsoft defender para Intune

Exiba as configurações de linha de base da proteção avançada contra ameaças do Microsoft defender (anteriormente conhecida como proteção avançada contra ameaças do Windows Defender) com suporte pelo Microsoft Intune. Os padrões de linha de base de proteção contra ameaças avançadas (ATP) representam a configuração recomendada para ATP e podem não corresponder os padrões de linha de base para outras linhas de base de segurança.  

A linha de base de proteção avançada contra ameaças do Microsoft defender está disponível quando seu ambiente atende aos pré-requisitos para usar a [proteção avançada contra ameaças do Microsoft defender](advanced-threat-protection.md#prerequisites). 

Essa linha de base é otimizada para dispositivos físicos e não é recomendada no momento para uso em VMs (máquinas virtuais) ou pontos de extremidade de VDI. Determinadas configurações de linha de base podem afetar sessões interativas remotas em ambientes virtualizados. Para obter mais informações, consulte [aumentar a conformidade com a linha de base de segurança do Microsoft defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) na documentação do Windows.

## <a name="application-guard"></a>Proteção de aplicativo  
Para obter mais informações, consulte [WINDOWSDEFENDERAPPLICATIONGUARD CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) na documentação do Windows.  

Ao usar o Microsoft Edge, o Microsoft defender Application Guard protege seu ambiente de sites que não são confiáveis para sua organização. Quando os usuários visitam sites que não estão listados em seu limite de rede isolado, os sites são abertos em uma sessão de navegação virtual do Hyper-V. Sites confiáveis são definidos por um limite de rede.  

- Configurações de - do **Application Guard** */AllowWindowsDefenderApplicationGuard*  
  Selecione *Sim* para ativar esse recurso, que abre sites não confiáveis em um contêiner de navegação virtualizado do Hyper-V. Quando definido como *não configurado*, qualquer site (confiável e não confiável) é aberto no dispositivo e não em um contêiner virtualizado.  

  **Padrão**: Sim
 
  - **Conteúdo externo em sites corporativos** - *configurações/BlockNonEnterpriseContent*  
    Selecione *Sim* para bloquear o carregamento de conteúdo de sites não aprovados. Quando definido como *não configurado*, os sites que não são corporativos podem abrir no dispositivo. 
 
    **Padrão**: Sim

  - **Comportamento da área de transferência** - *configurações/ClipboardSettings*  
    Escolha quais ações de copiar e colar são permitidas entre o computador local e o navegador virtual do Application Guard.  As opções incluem:
    - Não Configurado  
    - Bloquear copiar e colar entre PC e navegador-bloquear ambos. Os dados não podem ser transferidos entre o PC e o navegador virtual.  
    - Permitir copiar e colar do navegador para o PC somente-os dados não podem transferir do PC para o navegador virtual.
    - Permitir copiar e colar do PC para o navegador somente-os dados não podem transferir do navegador virtual para o PC host.
    - Permitir copiar e colar entre PC e navegador-nenhum bloco para conteúdo existe.  

    **Padrão**: bloquear cópia e colar entre PC e navegador  

- **Política de isolamento de rede do Windows – nomes de domínio de rede corporativa**  
  Para obter mais informações, consulte [Policy CSP-NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) na documentação do Windows.
  
  Especifique uma lista de recursos da empresa como domínios, intervalos de endereços IP e limites de rede hospedados na nuvem que o Application Guard trata como sites corporativos.  

  **Padrão**: SecurityCenter.Windows.com

## <a name="application-reputation"></a>Reputação do aplicativo  

Para obter mais informações, consulte [CSP da política-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.

- **Bloquear a execução de arquivos não verificados**  
    Impedir que o usuário execute arquivos não verificados. Quando definido como *não configurado*, os funcionários podem ignorar os avisos do SmartScreen e executar arquivos mal-intencionados. Defina como *Sim* para que os funcionários não possam ignorar avisos do SmartScreen e executar arquivos mal-intencionados.  
  
    **Padrão**: Sim

- **Exigir SmartScreen para aplicativos e arquivos**  
  Defina como *Sim* para habilitar o SmartScreen para Windows.  

  **Padrão**: Sim

## <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque  

- **Tipo de processo filho de lançamento de aplicativos do Office**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – quando definido como *Bloquear*, os aplicativos do Office não poderão criar processos filho. Os aplicativos do Office incluem Word, Excel, PowerPoint, OneNote e Access. A criação de um processo filho é um comportamento típico de malware, especialmente para ataques baseados em macro que tentam usar aplicativos do Office para iniciar ou baixar executáveis mal-intencionados.  

  **Padrão**: bloquear

- **Tipo de execução de conteúdo baixado por script**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – especifique um nível de detecção para aplicativos potencialmente indesejados que são baixados ou tentam ser instalados.  

  **Padrão**: bloquear 

- **Impedir tipo de roubo de credencial**  
  Defina como *habilitar* para [proteger as credenciais de domínio derivadas com o Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard). O Microsoft defender Credential Guard usa segurança baseada em virtualização para isolar segredos para que somente o software de sistema privilegiado possa acessá-los. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, tal como Ataques PtH ou PtT. O Microsoft defender Credential Guard impede esses ataques ao proteger os hashes de senha NTLM, tíquetes de concessão de permissão Kerberos e credenciais armazenadas por aplicativos como credenciais de domínio.  

  **Padrão**: habilitar

- **Execução de conteúdo de email**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – quando definido como *Bloquear*, essa regra impede que os seguintes tipos de arquivo sejam executados ou iniciados de um email visto no Microsoft Outlook ou webmail (como gmail.com ou Outlook.com):  

  - Arquivos executáveis (como. exe,. dll ou. SCR)  
  - Arquivos de script (como um arquivo PowerShell. PS, VisualBasic. vbs ou JavaScript. js)  
  - Arquivos mortos de script  

  **Padrão**: bloquear

- **Lançamento do Adobe Reader em um processo filho**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – *habilite* essa regra para impedir que o Adobe Reader crie um processo filho. Por meio de engenharia social ou explorações, o malware pode baixar e iniciar cargas adicionais e dividir o Adobe Reader.  

  **Padrão**: habilitar

- **Script de código de macro ofuscado**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – malware e outras ameaças podem tentar ofuscar ou ocultar seu código mal-intencionado em alguns arquivos de script. Essa regra impede que os scripts que parecem estar ofuscados sejam executados.  
    
  **Padrão**: bloquear

- **Processo USB não confiável**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – quando definido para *Bloquear*, não assinados ou arquivos executáveis não confiáveis de unidades removíveis USB e os cartões SD não podem ser executados.

  Os arquivos executáveis incluem:
  - Arquivos executáveis (como. exe,. dll ou. SCR)
  - Arquivos de script (como um arquivo PowerShell. PS, VisualBasic. vbs ou JavaScript. js)  

  **Padrão**: bloquear

- **Outros aplicativos do Office injeção de processo**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) -quando definido como *Bloquear*, os aplicativos do Office, incluindo o Word, o Excel, o PowerPoint e o OneNote, não podem injetar código em outros processos. A injeção de código é normalmente usada por malware para executar código mal-intencionado em uma tentativa de ocultar a atividade de mecanismos de verificação antivírus.  

  **Padrão**: bloquear

- **Código de macro do Office permitir importações Win32**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – quando definido como *Bloquear*, essa regra tenta bloquear os arquivos do Office que contêm o código de macro que pode importar as DLLs do Win32. Os arquivos do Office incluem Word, Excel, PowerPoint e OneNote. O malware pode usar o código de macro em arquivos do Office para importar e carregar as DLLs do Win32, que são usadas para fazer chamadas à API para permitir infecções adicionais em todo o sistema.  

  **Padrão**: bloquear

- **Aplicativos de comunicação do Office são iniciados em um processo filho**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – quando definido como *habilitar*, essa regra impede que o Outlook Crie processos filho. Ao bloquear a criação de um processo filho, essa regra protege contra ataques de engenharia social e impede que o código de exploração abusando uma vulnerabilidade no Outlook.  

  **Padrão**: habilitar

- **Criação ou inicialização de conteúdo executável de aplicativos do Office**  
  [Regra de redução da superfície de ataque](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – quando definido como *Bloquear*, os aplicativos do Office não podem criar conteúdo executável. Os aplicativos do Office incluem Word, Excel, PowerPoint, OneNote e Access.  

  Essa regra destina-se a comportamentos típicos usados por Complementos suspeitos e mal-intencionados e scripts (extensões) que criam ou iniciam arquivos executáveis. Essa é uma técnica típica de malware. As extensões são impedidas de serem usadas pelos aplicativos do Office. Normalmente, essas extensões usam o Windows Scripting Host (arquivos. WSH) para executar scripts que automatizam determinadas tarefas ou fornecem recursos de complemento criados pelo usuário.

  **Padrão**: bloquear

## <a name="bitlocker"></a>BitLocker  

Para obter mais informações, o [BitLocker política de grupo configurações](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) na documentação do Windows.  

- **Criptografar dispositivos**  
  Selecione *Sim* para habilitar a criptografia de dispositivo do BitLocker. Dependendo do hardware do dispositivo e da versão do Windows, os usuários do dispositivo podem ser solicitados a confirmar se não há criptografia de terceiros no dispositivo. Ativar a criptografia do Windows enquanto a criptografia de terceiros estiver ativa tornará o dispositivo instável.  

   **Padrão**: Sim

- **Política de unidade removível do armário de bits**  
  Os valores dessa política determinam a força da codificação que o BitLocker usa para a criptografia de unidades removíveis. As empresas controlam o nível de criptografia para maior segurança (o AES-256 é mais seguro do que o AES-128). Se você selecionar *Sim* para habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada. 

  Para política de unidade removível de armário de bits, defina as seguintes configurações:

  - **Exigir criptografia para acesso de gravação**  
    **Padrão**: Sim

  - **Método de criptografia**  
    **Padrão**: AES 128bit CBC

- **Criptografar cartão de armazenamento (somente dispositivos móveis)** Selecionar *Sim* irá criptografar a placa de armazenamento do dispositivo móvel.  

   **Padrão**: Sim

- **Política de unidade fixa do armário de bits**  
  Os valores dessa política determinam a força da codificação que o BitLocker usa para a criptografia de unidades fixas. As empresas podem controlar o nível de criptografia para aumentar a segurança (o AES-256 é mais seguro do que o AES-128). Se você habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada.

  Para política de unidade fixa do armário de bits, defina as seguintes configurações:

  - **Exigir criptografia para acesso de gravação**  
    **Padrão**: Sim

  - **Método de criptografia**  
    **Padrão**: AES 128bit XTS

- **Política de unidade do sistema do armário de bits**  
  Os valores dessa política determinam a força da codificação que o BitLocker usa para a criptografia da unidade do sistema. As empresas podem querer controlar o nível de criptografia para aumentar a segurança (o AES-256 é mais seguro do que o AES-128). Se você habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada.  

  Para a política de unidade do sistema do armário de bits, defina as seguintes configurações:  

  - **Método de criptografia**  
    **Padrão**: AES 128bit XTS

## <a name="device-control"></a>Controle de dispositivo  

- **Verificar unidades removíveis durante uma verificação completa**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) -quando definido como *Sim*, o defender verifica se há software mal-intencionado e indesejado em unidades removíveis, como unidades flash, durante uma verificação completa. O defender antivírus examina todos os arquivos em dispositivos USB antes que os arquivos no dispositivo USB possam ser executados.

  Configuração relacionada nesta lista: *defender/AllowFullScanOnMappedNetworkDrives*  

  **Padrão**: Sim

- **Enumeração de dispositivos externos incompatíveis com a proteção de kernel DMA**  
   Consulte *DmaGuard/DeviceEnumerationPolicy* no [CSP da política-DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  Essa política fornece segurança adicional em relação a dispositivos compatíveis com DMA externo. Ele permite mais controle sobre a enumeração de dispositivos compatíveis com DMA externo que são incompatíveis com isolamento de memória de dispositivo DMA e área restrita.

  Essa política só entra em vigor quando há suporte para a proteção do kernel DMA e ela é habilitada pelo firmware do sistema. A proteção de kernel DMA é um recurso de plataforma que não pode ser controlado pela política ou pelo usuário de um dispositivo. Ele deve ser suportado pelo sistema no momento da fabricação. 

  Para verificar se o sistema dá suporte à proteção de kernel DMA, execute MSINFO32. exe no sistema e examine o campo *proteção de DMA do kernel* na página Resumo.  

  As opções incluem: 
  - *Dispositivo padrão* -após a entrada ou desbloqueio de tela, os dispositivos com remapeamento de DMA drivers compatíveis podem ser enumerados a qualquer momento. Dispositivos com remapeamento de DMA drivers incompatíveis só serão enumerados depois que o usuário desbloquear a tela
  - *Permitir todos* -todos os dispositivos PCIe com capacidade para DMA externos serão enumerados a qualquer momento
  - *Bloquear todos os* dispositivos com remapeamento de DMA os drivers compatíveis têm permissão para enumerar a qualquer momento. Dispositivos com remapeamento de DMA drivers incompatíveis nunca terão permissão para iniciar e executar DMA a qualquer momento.

  **Padrão**: dispositivo padrão

- **Instalação de dispositivo de hardware por identificadores de dispositivo**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) -com essa política, você especifica uma lista de plug and Play IDs de hardware e IDs compatíveis para dispositivos que o Windows é impedido de instalar. Essa configuração de política tem precedência sobre qualquer outra configuração de diretiva que permita que o Windows instale um dispositivo. Se você habilitar essa configuração de política (definida para *bloquear a instalação do dispositivo de hardware*), o Windows será impedido de instalar um dispositivo cuja ID de hardware ou ID compatível apareça na lista que você criar. Se você habilitar essa configuração de política em um servidor de área de trabalho remota, a política afetará o redirecionamento dos dispositivos especificados de um cliente de área de trabalho remota para o servidor de área de trabalho remota. Se você desabilitar ou não definir essa configuração de política (definida para *permitir a instalação do dispositivo de hardware*), os dispositivos poderão instalar e atualizar conforme permitido ou impedido por outras configurações de política.  

  **Padrão**: bloquear a instalação do dispositivo de hardware  

  Quando *Bloquear instalação de dispositivo de hardware* estiver selecionado, as configurações a seguir estarão disponíveis.
  - **Remover dispositivos de hardware correspondentes**  
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por identificadores de dispositivo* está definida para *bloquear a instalação do dispositivo de hardware*.  

    **Padrão**: Sim

  - **Identificadores de dispositivo de hardware que são bloqueados**  
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por identificadores de dispositivo* está definida para *bloquear a instalação do dispositivo de hardware*. Para definir essa configuração, expanda a opção, selecione **+ Adicionar**e especifique o identificador de dispositivo de hardware que você deseja bloquear.  

    **Padrão**: PCI \ CC_0C0A

- **Bloquear o acesso direto à memória**  
  [Dataprotection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) -Use essa configuração de política para bloquear o DMA (acesso direto à memória) para todas as portas de downstream PCI conectadas a quente em um dispositivo, até que um usuário faça logon no Windows. Quando um usuário fizer logon, o Windows enumerará os dispositivos PCI conectados às portas PCI plug-host. Toda vez que o usuário bloqueia a máquina, o DMA é bloqueado em portas PCI de plugue a quente sem dispositivos filhos até que o usuário faça logon novamente. Os dispositivos que já foram enumerados quando o computador foi desbloqueado continuarão funcionando até serem desconectados. 

  Essa configuração de política só é imposta quando o BitLocker ou a criptografia de dispositivo está habilitada.  

  **Padrão**: Sim


- **Instalação de dispositivo de hardware por classes de instalação**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) -com essa política, você pode especificar uma lista de identificadores exclusivos (GUIDs) de classe de instalação de dispositivo para drivers de dispositivo que o Windows é impedido de instalar. Essa configuração de política tem precedência sobre qualquer outra configuração de diretiva que permita que o Windows instale um dispositivo. Se você habilitar essa configuração de política (definida para *bloquear a instalação do dispositivo de hardware*), o Windows será impedido de instalar ou atualizar drivers de dispositivo cujos GUIDs de classe de instalação do dispositivo apareçam na lista que você criar. Se você habilitar essa configuração de política em um servidor de área de trabalho remota, a configuração de política afetará o redirecionamento dos dispositivos especificados de um cliente de área de trabalho remota para o servidor de área de trabalho remota. Se você desabilitar ou não definir essa configuração de política (definida para *permitir a instalação do dispositivo de hardware*), o Windows poderá instalar e atualizar dispositivos conforme permitido ou impedido por outras configurações de política.  

  **Padrão**: bloquear a instalação do dispositivo de hardware

  Quando *Bloquear instalação de dispositivo de hardware* estiver selecionado, as configurações a seguir estarão disponíveis.  

  - **Remover dispositivos de hardware correspondentes**  
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por classes de instalação* está definida para *bloquear a instalação do dispositivo de hardware*.  
 
    **Padrão**: Sim  

  - **Identificadores de dispositivo de hardware que são bloqueados**  
    Essa configuração está disponível somente quando a instalação do dispositivo de hardware por classes de instalação está definida para bloquear a instalação do dispositivo de hardware. Para definir essa configuração, expanda a opção, selecione **+ Adicionar**e especifique o identificador de dispositivo de hardware que você deseja bloquear.  
 
    **Padrão**: {d48179be-ec20-11D1-b6b8-00c04fa372a7}

## <a name="endpoint-detection-and-response"></a>Detecção e resposta de ponto de extremidade  
Para obter mais informações, consulte [WINDOWSADVANCEDTHREATPROTECTION CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) na documentação do Windows.  

- **Agilizar a frequência de relatório de telemetria** - *configuração/TelemetryReportingFrequency*

  Acelere a frequência de relatórios de telemetria da proteção avançada contra ameaças do Microsoft defender.  

  **Padrão**: Sim

- **Compartilhamento de amostra para todos os arquivos** - *Configuration/SampleSharing* 

  Retorna ou define o parâmetro de configuração de compartilhamento de exemplo de proteção avançada contra ameaças do Microsoft defender.  

  **Padrão**: Sim

## <a name="exploit-protection"></a>Proteção contra Exploit  

- **Exploração de XML de proteção**  
  Para obter mais informações, consulte [importar, exportar e implantar configurações de proteção de exploração](/windows/security/threat-protection/microsoft-defender-atp/import-export-exploit-protection-emet-xml) na documentação do Windows.  

  Permite que o administrador de ti envie uma configuração que representa o sistema desejado e as opções de mitigação de aplicativo para todos os dispositivos na organização. A configuração é representada por um XML. 

  O Exploit Protection se aplica ajuda a proteger dispositivos contra malware que usam explorações para disseminar e infectar. Você usa o aplicativo de segurança do Windows ou o PowerShell para criar um conjunto de atenuações (conhecido como uma configuração). Você pode exportar essa configuração como um arquivo XML e compartilhá-la com vários computadores na sua rede para que todos tenham o mesmo conjunto de configurações de mitigação.
 
  Você também pode converter e importar um arquivo XML de configuração do EMET existente em um XML de configuração do Exploit Protection.

- **Bloquear a substituição da proteção contra exploração**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – defina como *Sim* para impedir que os usuários façam alterações na área de configurações da proteção de exploração na central de segurança do Microsoft defender. Se você desabilitar ou não definir essa configuração, os usuários locais poderão fazer alterações na área de configurações do Exploit Protection.  
  **Padrão**: Sim  

## <a name="microsoft-defender-antivirus"></a>Microsoft defender antivírus  

Para obter mais informações, consulte [Policy CSP-defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.

- **Verificar scripts carregados nos navegadores da Web da Microsoft**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – defina como *Sim* para permitir a funcionalidade de verificação de script do Microsoft defender.  

  **Padrão**: Sim

- **Examinar mensagens de email recebidas**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – defina como *Sim* para permitir que o Microsoft defender Verifique o email.  

  **Padrão**: Sim

- **Consentimento de envio de exemplo do defender**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) -verifica o nível de consentimento do usuário no Microsoft defender para enviar dados. Se o consentimento necessário já tiver sido concedido, o Microsoft defender os enviará. Se não (e se o usuário tiver especificado nunca perguntar), a interface do usuário será iniciada para solicitar o consentimento do usuário (quando a *proteção fornecida pela nuvem* estiver definida como *Sim*) antes de enviar dados.  

  **Padrão**: enviar amostras seguras automaticamente

- **Sistema de Inspeção de Rede (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) -bloqueia o tráfego mal-intencionado detectado por assinaturas no sistema de inspeção de rede (NIS).  
 
  **Padrão**: Sim

- **Intervalo de atualização de assinatura (em horas)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – especifique em horas, com que frequência o dispositivo verifica se há novas atualizações de assinatura do defender.  
 
  **Padrão**: 4

- **Configurar a baixa prioridade da CPU para verificações agendadas**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – quando definido como *Sim*, a prioridade da CPU para verificações é definida como baixa. Quando *não configurado*, nenhuma alteração é feita na prioridade da CPU para verificações agendadas.  

    **Padrão**: Sim

- **Bloqueio do defender na proteção de acesso**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – quando definido como *Sim*, o Microsoft defender na proteção de acesso está habilitado.  

  **Padrão**: Sim

- **Tipo de verificação do sistema a ser executada**  
  Tipo de verificação do [defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) -defender.  

  **Padrão**: verificação rápida

- **Analisar todas as transferências**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) -quando definido como *Sim*, o defender examina todos os arquivos e anexos baixados.  

  **Padrão**: Sim

- **Dias antes da exclusão de malware em quarentena**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) -especifique quantos dias para manter os itens de quarentena no sistema antes que eles sejam automaticamente excluídos. Quando definido como zero, os itens em quarentena nunca são excluídos automaticamente.  

  **Padrão**: 0

- **Hora de início da verificação agendada**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – agende uma hora do dia para o defender verificar dispositivos. 
  
  Opção relacionada nesta lista: *defender/ScheduleScanDay*   

  **Padrão**: 2 am

- **Proteção entregue na nuvem**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – quando definido como *Sim*, o Microsoft defender envia informações à Microsoft sobre quaisquer problemas encontrados. A Microsoft analisará essas informações, aprenderá mais sobre problemas que afetam você e outros clientes, além de oferecer soluções aprimoradas.

  Quando essa política é definida como *Sim*, você pode usar o *tipo de consentimento de envio de exemplo do defender* para dar aos usuários o controle sobre o envio de informações do seu dispositivo.  

  **Padrão**: Sim

- **Ação de aplicativo potencialmente indesejado defender**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – o Microsoft defender antivírus pode identificar e bloquear o download e a instalação de *aplicativos potencialmente indesejados* (puas) em pontos de extremidade em sua rede. 
 
  - Quando definido como *Bloquear*, o Microsoft defender bloqueia puas e lista-os em histórico junto com outras ameaças.
  - Quando definido como *auditoria*, o Microsoft defender detecta o puas, mas não os bloqueia. As informações sobre os aplicativos nos quais o Microsoft defender teria feito a ação podem ser encontradas pesquisando eventos que foram criados pelo Microsoft defender na Visualizador de Eventos.  
  - Quando definido como *padrão do dispositivo*, a proteção pua está desativada.  
 
  **Padrão**: bloquear

- **Tempo limite estendido do defender Cloud**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) – especifique a quantidade máxima de tempo adicional que o Microsoft defender antivírus deve bloquear um arquivo enquanto aguarda um resultado da nuvem. A quantidade de tempo de base que o Microsoft defender aguarda é de 10 segundos. Qualquer tempo adicional que você especificar aqui (até 50 segundos) será adicionado a esses 10 segundos. Na maioria dos casos, a verificação leva menos tempo do que o máximo. Alargar o período de tempo permite que a cloud investigue ficheiros suspeitos de forma mais minuciosa.  

  Por padrão, o valor de tempo expandido é 0 (desabilitado). O Intune recomenda que você habilite essa configuração e especifique pelo menos 20 segundos adicionais.  
 
  **Padrão**: 0

- **Analisar ficheiros de arquivo**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – defina como *Sim* para que o Microsoft defender Verifique arquivos mortos.  

  **Padrão**: Sim

- **Agenda de verificação do sistema do defender**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) -agenda em que o defender de dias verifica os dispositivos. 
 
  Opção relacionada nesta lista: *defender/ScheduleScanTime*

  **Padrão**: definido pelo usuário

- **Monitoramento de comportamento**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – defina como *Sim* para ativar a funcionalidade de monitoramento de comportamento do Microsoft defender. Inserido no Windows 10, os sensores de monitoramento de comportamento do Microsoft defender coletam e processam sinais comportamentais do sistema operacional e enviam esses dados de sensor para sua instância privada, isolada e de nuvem do Microsoft defender ATP.  

  **Padrão**: Sim

- **Verificar arquivos abertos de pastas de rede**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – defina como *Sim* para que o Microsoft defender Verifique os arquivos na rede. O usuário não poderá remover o malware detectado de arquivos somente leitura.  

  **Padrão**: Sim

- **Nível de bloco do defender Cloud**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – Use essa política para determinar a agressividade com que o Microsoft defender antivírus está bloqueando e verificando arquivos suspeitos. As opções incluem:

  - Bloqueie de forma alta agressiva arquivos desconhecidos ao mesmo tempo em que otimiza o desempenho do cliente (maior chance de falsos positivos)
  - Blocos de proteção mais altos e agressivos de bloqueio e aplicação de medidas adicionais (podem afetar o desempenho do cliente)
  - Tolerância zero-bloquear todos os arquivos executáveis desconhecidos

  **Padrão**: não configurado

- **Monitoramento em tempo real**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – defina como *Sim* para permitir o monitoramento do Microsoft defender em tempo real.  

  **Padrão**: Sim

- **Limite de uso da CPU durante uma verificação**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – especifique o uso médio máximo de% de CPU que o Microsoft defender pode usar durante uma verificação.  

  **Padrão**: 50

- **Verificar unidades de rede mapeadas durante uma verificação completa**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) -defina como *Sim* para que o Microsoft defender Verifique os arquivos na rede. O usuário não pode remover o malware detectado de arquivos somente leitura,

  Configuração relacionada nesta lista: *defender/AllowScanningNetworkFiles*

  **Padrão**: Sim

- **Bloquear o acesso do usuário final ao defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – defina como *Sim* para bloquear o acesso dos usuários finais à interface do usuário do Microsoft defender em seu dispositivo.  

  **Padrão**: Sim

- **Hora de início da verificação rápida**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) -agende uma hora do dia para o defender executar uma verificação rápida.  

  **Padrão**: 2 am

## <a name="microsoft-defender-firewall"></a>Microsoft defender firewall
Para obter mais informações, consulte [CSP do firewall](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) na documentação do Windows.

- **Tempo ocioso de associação de segurança antes da exclusão** - *MdmStore/Global/SaIdleTime*   
  As associações de segurança são excluídas após o tráfego de rede não ser visto para esse número de segundos.  
  **Padrão**: 300

- **Protocolo FTP** - *MdmStore/Global/DisableStatefulFtp*   
  Bloqueia protocolo FTP com estado (FTP).  
  **Padrão**: Sim

- **Enfileiramento de pacotes** - *MdmStore/Global/EnablePacketQueue*    
  Especifique como o dimensionamento do software no lado de recebimento está habilitado para recebimento criptografado e texto não criptografado para o cenário de gateway de túnel IPsec. Isso garante que a ordem dos pacotes seja preservada.  
  **Padrão**: dispositivo padrão

- **Domínio do perfil de Firewall** - *FirewallRules/FirewallRuleName/perfis*  
  Especifica os perfis aos quais a regra pertence: domínio, privado, público. Esse valor representa o perfil para redes que estão conectadas a domínios.  

  Configurações disponíveis:  
  - **Respostas unicast para difusões multicast necessárias**  
    **Padrão**: Sim

  - **Regras de aplicativo autorizado da política de grupo mescladas**  
    **Padrão**: Sim

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Regras de porta global da política de grupo mesclada**  
    **Padrão**: Sim

  - **Modo furtivo bloqueado**  
    **Padrão**: Sim

  - **Firewall habilitado**  
    **Padrão**: permitido

  - **Regras de segurança de conexão da política de grupo não mescladas**  
    **Padrão**: Sim

  - **Regras de política da política de grupo não mesclada**  
    **Padrão**: Sim

- **Perfil de Firewall** - *FirewallRules/FirewallRuleName/perfis*  
  Especifica os perfis aos quais a regra pertence: domínio, privado, público. Esse valor representa o perfil para redes públicas. Essas redes são classificadas como públicas pelos administradores no host do servidor. A classificação ocorre na primeira vez que o host se conecta à rede. Normalmente, essas redes estão em aeroportos, cafeterias e outros locais públicos onde os colegas na rede ou o administrador de rede não são confiáveis.  

  Configurações disponíveis:

  - **Conexões de entrada bloqueadas**  
    **Padrão**: Sim 

  - **Respostas unicast para difusões multicast necessárias**  
    **Padrão**: Sim  

  - **Modo furtivo necessário**  
    **Padrão**: Sim 
 
  - **Conexões de saída necessárias**  
    **Padrão**: Sim  

  - **Regras de aplicativo autorizado da política de grupo mescladas**  
    **Padrão**: Sim  

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim  

  - **Regras de porta global da política de grupo mesclada**  
    **Padrão**: Sim

  - **Modo furtivo bloqueado**  
    **Padrão**: Sim

  - **Firewall habilitado**  
    **Padrão**: permitido  

  - **Regras de segurança de conexão da política de grupo não mescladas**  
    **Padrão**: Sim  

  - **Tráfego de entrada necessário**  
    **Padrão**: Sim

  - **Regras de política da política de grupo não mesclada**  
    **Padrão**: Sim  

- **Perfil de firewall particular** - *FirewallRules/FirewallRuleName/perfis*  
  Especifica os perfis aos quais a regra pertence: domínio, privado, público. Esse valor representa o perfil para redes privadas.  

  Configurações disponíveis: 

  - **Conexões de entrada bloqueadas**  
    **Padrão**: Sim

  - **Respostas unicast para difusões multicast necessárias**  
    **Padrão**: Sim

  - **Modo furtivo necessário**  
    **Padrão**: Sim

  - **Conexões de saída necessárias**  
    **Padrão**: Sim

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Regras de porta global da política de grupo mesclada**  
    **Padrão**: Sim

  - **Modo furtivo bloqueado**  
    **Padrão**: Sim  

  - **Firewall habilitado**  
    **Padrão**: permitido

  - **Regras de aplicativo autorizado da política de grupo não mescladas**  
    **Padrão**: Sim

  - **Regras de segurança de conexão da política de grupo não mescladas**  
    **Padrão**: Sim

  - **Tráfego de entrada necessário**  
    **Padrão**: Sim

  - **Regras de política da política de grupo não mesclada**  
    **Padrão**: Sim  

- **Método de codificação de chave pré-compartilhada do firewall**  
  **Padrão**: UTF8

- **Verificação da lista de certificados revogados**  
  **Padrão**: dispositivo padrão

## <a name="web--network-protection"></a>Proteção de rede & Web  

- **Tipo de proteção de rede**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) -essa política permite ativar ou desativar a proteção de rede no Microsoft defender Exploit Guard. A proteção de rede é um recurso do Microsoft defender Exploit Guard que protege os funcionários que usam qualquer aplicativo de acessar golpes de phishing, sites de Hospedagem de exploração e conteúdo mal-intencionado na Internet. Isso inclui impedir que navegadores de terceiros se conectem a sites perigosos.  

  Quando definido como *habilitar* ou *modo de auditoria*, os usuários não podem desativar a proteção de rede e você pode usar a central de segurança do Microsoft defender para exibir informações sobre tentativas de conexão.  
 
  - *Habilitar* impedirá que os usuários e aplicativos se conectem a domínios perigosos.  
  - O *modo de auditoria* não impede que os usuários e aplicativos se conectem a domínios perigosos.  

  Quando definido como *definido pelo usuário*, os usuários e aplicativos não são impedidos de se conectar a domínios perigosos e as informações sobre conexões não estão disponíveis na central de segurança do Microsoft defender.  

  **Padrão**: modo de auditoria

- **Exigir SmartScreen para o Microsoft Edge**  
  O [navegador/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) -Microsoft Edge usa o Microsoft defender SmartScreen (ativado) para proteger os usuários contra possíveis golpes de phishing e softwares mal-intencionados por padrão. Por padrão, essa política está habilitada (definida como *Sim*) e, quando habilitada, impede que os usuários desliguem o Microsoft defender SmartScreen.  Quando a política efetiva de um dispositivo é igual a não configurado, os usuários podem desativar o Microsoft defender SmartScreen, o que deixa o dispositivo desprotegido.  

  **Padrão**: Sim
  
- **Bloquear acesso a sites mal-intencionados**  
  [Navegador/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) -por padrão, o Microsoft Edge permite que os usuários ignorem (ignoram) os avisos do Microsoft defender SmartScreen sobre sites potencialmente mal-intencionados, permitindo que os usuários continuem no site. Com essa política habilitada (definida como *Sim*), o Microsoft Edge impede que os usuários ignorem os avisos e os bloqueia de continuar para o site.  

  **Padrão**: Sim

- **Bloquear download de arquivo não verificado**  
  [Navegador/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) -por padrão, o Microsoft Edge permite que os usuários ignorem (ignoram) os avisos do Microsoft defender SmartScreen sobre arquivos potencialmente mal-intencionados, permitindo que eles continuem baixando arquivos não verificados. Com essa política habilitada (definida como *Sim*), os usuários são impedidos de ignorar os avisos e não podem baixar arquivos não verificados.  

  **Padrão**: Sim

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas  

Para obter mais informações, consulte [PASSPORTFORWORK CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) na documentação do Windows.

- **Configurar o Windows Hello para empresas** - *Tenantid/Policies/UsePassportForWork*    
  O Windows Hello para empresas é um método alternativo para entrar no Windows, substituindo senhas, cartões inteligentes e cartões inteligentes virtuais.  


  > [!IMPORTANT]
  > As opções dessa configuração são revertidas de seu significado implícito. Embora seja invertido, um valor de *Sim* não habilita o Windows Hello e, em vez disso, é tratado como *não configurado*. Quando essa configuração é definida como *não configurado*, o Windows Hello é habilitado em dispositivos que recebem essa linha de base.
  >
  > As descrições a seguir foram revisadas para refletir esse comportamento. A reversão das configurações será corrigida em uma atualização futura para essa linha de base de segurança.

  - Quando definido como *não configurado*, o Windows Hello é habilitado e o dispositivo provisiona o Windows Hello para empresas.
  - Quando definido como *Sim*, a linha de base não afeta a configuração de política do dispositivo. Isso significa que, se o Windows Hello para empresas estiver desabilitado em um dispositivo, ele permanecerá desabilitado. Se estiver habilitado, ele permanecerá habilitado.
  <!-- expected behavior 
  - When set to *Yes*, you  enable this policy and the device provisions Windows Hello for Business.  
  - When set to *Not configured*, the baseline does not affect the policy setting of the device. This means that if Windows Hello for Business is disabled on a device, it remains disabled. If its enabled, it remains enabled. 
  -->

  Não é possível desabilitar o Windows Hello para empresas por meio desta linha de base. Você pode desabilitar o Windows Hello para empresas ao configurar o [registro do Windows](windows-hello.md)ou como parte de um perfil de configuração do dispositivo para a proteção de [identidade](identity-protection-configure.md).  

O Windows Hello para empresas é um método alternativo para entrar no Windows, substituindo senhas, cartões inteligentes e cartões inteligentes virtuais.  

  Se você habilitar ou não definir essa configuração de política, o dispositivo provisionará o Windows Hello para empresas. Se você desabilitar essa configuração de política, o dispositivo não provisionará o Windows Hello para empresas para qualquer usuário.

  O Intune não dá suporte à desabilitação do Windows Hello. Em vez disso, você pode configurar a política para habilitar o Windows Hello para empresas (Sim) ou não configurar o Windows Hello diretamente (não configurado). Quando não configurado, um dispositivo pode receber a configuração por meio de outra política, o que pode habilitar ou desabilitar esse recurso.  

  **Padrão**: Sim  

- **Exigir letras minúsculas no PIN** - *Tenantid/Policies/PINComplexity/LowercaseLetters*  
  **Padrão**: permitido  

- **Exigir caracteres especiais no PIN** - *Tenantid/Policies/PINComplexity/SpecialCharacters*  
  **Padrão**: permitido  

- **Exigir letras maiúsculas no PIN** - *Tenantid/Policies/PINComplexity/UppercaseLetters*   
  **Padrão**: permitido  

