---
title: Definições de linhas de base de segurança do Windows para o Intune
titleSuffix: Microsoft Intune
description: Definições de linha de base de segurança do Windows suportadas pelo Intune
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/05/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67938f8697002f94f275f953510d1b0f4864a3fa
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507160"
---
# <a name="windows-security-baseline-settings-for-intune"></a>Definições da linha de base de segurança do Windows para o Intune  

Ver os [definições de linha de base de segurança do Windows](security-baselines.md) que são suportadas pelo Microsoft Intune.  

> [!NOTE]  
> As definições de linha de base de segurança do Windows estão em pré-visualização. Enquanto está em pré-visualização, a lista de definições disponíveis e a ordem em que este conteúdo apresenta essas definições, irão variar consoante o que está disponível no portal.  
>  
> Quando as definições de linha de base do modo de pré-visualização, este conteúdo será atualizado com a lista de pré-visualização de definições de linha de base de segurança que o Intune suporta.  

## <a name="above-lock"></a>Acima de bloqueio  
Para obter mais informações, consulte [CSP de política - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) na documentação do Windows.  

- **Exibição de bloco de notificações do sistema**  
  Esta definição de política permite-lhe impedir que as notificações de aplicações de aparecer no ecrã de bloqueio. Se ativar esta definição de política, não existem notificações da aplicação são apresentadas no ecrã de bloqueio. Se desabilitar ou não configura esta definição de política, os usuários podem escolher quais as aplicações apresentar as notificações no ecrã de bloqueio.
  
  **Predefinido**: Sim  

## <a name="app-runtime"></a>Tempo de execução da aplicação    
Para obter mais informações, consulte [CSP de política - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) na documentação do Windows.  

- **Contas Microsoft opcionais para aplicações da Windows Store**  
  Esta definição de política permite-lhe controlar se as contas Microsoft são opcionais para aplicações da Windows Store que requerem uma conta para iniciar sessão. Esta política afeta apenas as aplicações do Windows Store que o suportam. Se ativar esta definição de política, aplicações da Windows Store que exigem, normalmente, uma conta Microsoft para iniciar sessão permitirá aos utilizadores iniciar sessão com uma conta da empresa em vez disso. Se desabilitar ou não configura esta definição de política, os utilizadores devem iniciar sessão com uma conta Microsoft.  
  
  **Predefinido**: Enabled  

## <a name="application-management"></a>Gestão de aplicações   
Para obter mais informações, consulte [CSP de política - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) na documentação do Windows.  

- **Bloquear o gravador de jogo (apenas ambiente de trabalho)**  
  Configura se é permitida a gravação e a difusão de jogos.
  
  **Predefinido**: Sim  

## <a name="auto-play"></a>Reprodução automática   
Para obter mais informações, consulte [CSP de política - reprodução automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) na documentação do Windows.  

- **Comportamento de execução de automática de padrão de reprodução automática**  
  Esta definição afeta o comportamento predefinido para comandos de execução automática. Comandos de execução automática são armazenados em arquivos Autorun. inf e podem iniciar programas de instalação ou outras rotinas. Quando *ativado*, os administradores podem alterar o comportamento de execução automática do padrão num dispositivo que executa o Windows Vista ou posterior. Comportamento pode ser definido como: a) completamente desativar comandos de execução automática ou b) reverter para o comportamento do anteriores ao Windows Vista de automaticamente executar o comando de execução automática. Quando definido como *desativada* ou *não configurada*, os dispositivos que executam o Windows Vista ou posterior perguntar ao usuário sobre um comando de execução automática deve ser executado.
  
  **Predefinido**: Não executar  
  
- **Modo de reprodução automática**  
  Esta definição de política permite-lhe desativar a funcionalidade de reprodução automática. Reprodução automática começa a leitura de uma unidade assim que insira o suporte de dados na unidade. Como resultado, o ficheiro de configuração de programas e a música no suporte de dados de áudio começar imediatamente. Antes do Windows XP SP2, a reprodução automática está desativada por predefinição em unidades amovíveis, como a unidade de disquete (mas não a unidade de CD-ROM) e em unidades de rede. A partir do Windows XP SP2, o reprodução automática está ativada-se para unidades amovíveis, incluindo unidades Zip e alguns dispositivos de armazenamento em massa USB. Se ativar esta definição de política, reprodução automática está desativada em CD-ROM e unidades de mídia removível ou desativado em todas as unidades. Esta definição de política Desabilita a reprodução automática em tipos adicionais de unidades. Não é possível utilizar esta definição para ativar a reprodução automática em unidades em que está desativada por predefinição. Se desabilitar ou não configura esta definição de política, reprodução automática está ativada. Nota: Esta definição de política é apresentada nas pastas a configuração do computador e a configuração do usuário. Se as definições de política entrarem em conflito, a definição de política na configuração do computador tem precedência sobre a definição de política na configuração de utilizador.
  
  **Predefinido**: Desativado

- **Bloquear a reprodução automática para dispositivos não volume**  
  Esta definição de política não permite reprodução automática para dispositivos do MTP, como câmeras ou telefones. Se ativar esta definição de política, reprodução automática não é permitida para dispositivos do MTP, como câmeras ou telefones. Se desabilitar ou não configura esta definição de política, reprodução automática está ativada para dispositivos não volume.
  
  **Predefinido**: Enabled  

## <a name="bitlocker"></a>BitLocker    
Para obter mais informações, consulte [CSP de política - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) na documentação do Windows.  

- **Pouco cacifo unidade amovível política**  
  Esta definição de política é utilizada para controlar o método de encriptação e a força de cifras. Os valores desta política determinam a força da cifra que utiliza o BitLocker para a encriptação. As empresas podem querer controlar o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se ativar esta definição, poderá configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada.

  Para a política de unidade amovível cacifo de Bit, configure as seguintes definições:

    - **Exigir encriptação de acesso de escrita**  
      **Predefinido**: Sim  
  
    - **Método de encriptação**  
      **Predefinido**: AES 256bit CBC  

- **Cacifo de bit fixo de política de unidade**  
  Esta definição de política é utilizada para controlar o método de encriptação e a força de cifras. Os valores desta política determinam a força da cifra que utiliza o BitLocker para a encriptação. As empresas podem querer controlar o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se ativar esta definição, pode configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada.  
 
   Para o cacifo de Bit fixo de política de unidade, configure as seguintes definições: 
   - **Método de encriptação**
     **predefinido**: AES de 256 bits XTS  

- **Política de unidade de sistema do bit locker**  
  Esta definição de política é utilizada para controlar o método de encriptação e a força de cifras. Os valores desta política determinam a força da cifra que utiliza o BitLocker para a encriptação. As empresas podem querer controlar o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se ativar esta definição, pode configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada.  

   Para a política de unidade de sistema de cacifo de Bit, configure as seguintes definições:
  - **Método de encriptação**  
    **Predefinido**: AES de 256 bits XTS  

## <a name="browser"></a>Browser  
Para obter mais informações, consulte [CSP de política - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) na documentação do Windows.  

- **Exigir o SmartScreen para o Microsoft Edge**  
  Microsoft Edge utiliza o Windows Defender SmartScreen (ativado) para proteger os usuários contra potenciais atos fraudulentos de phishing e software malicioso por predefinição. Além disso, por predefinição, os utilizadores não é possível desativar (desative) Windows Defender SmartScreen. Ativar esta política se desligar o Windows Defender SmartScreen e impedir que os utilizadores ativá-la. Não configure esta política para permitir que os utilizadores que optar por ativar ou desativar a defender de Windows SmartScreen.  
  
  **Predefinido**: Sim  
  
- **Bloquear o acesso do site malicioso**  
  Por predefinição, o Microsoft Edge permite aos utilizadores ignorar (ignorar) os avisos do Windows Defender SmartScreen sobre sites potencialmente maliciosos, permitindo-lhes continuar para o site. Com esta política, pode configurar Microsoft Edge para impedir que os utilizadores ignorem os avisos do utilizador, bloqueando-los continue para o site.
  
  **Predefinido**: Sim  
  
- **Transferência de ficheiros de verificados de bloco** por predefinição, o Microsoft Edge permite aos utilizadores ignorar (ignorar) os avisos do Windows Defender SmartScreen sobre ficheiros potencialmente maliciosos, permitindo que os utilizadores continuem a transferir os ficheiros não verificados. Ativar esta política impede os utilizadores ignorem os avisos,-los a bloquear a transferência dos ficheiros não verificados.
  
  **Predefinido**: Sim  
  
- **Gestor de palavra-passe de bloco**  
  Por predefinição, Microsoft Edge utiliza o Gestor de palavra-passe automaticamente, permitindo que os usuários a palavras-passe manager localmente. A desativar esta política restringe o Microsoft Edge de utilizando o Gestor de palavra-passe. Não configure esta política se pretender permitir que os utilizadores que optar por guardar e gerir palavras-passe localmente utilizando o Gestor de palavra-passe.
  
  **Predefinido**: Sim  
  
- **Impedir as substituições de erro de certificado**  
  Esta definição de política impede que o utilizador a ignorar erros de certificado de Secure Sockets Layer/Transport Layer Security (SSL/TLS) que interrompem a navegação (como "expirada", "revogado" ou erros de "erro de correspondência do nome") no Internet Explorer. Se ativar esta definição de política, o utilizador não é possível continuar a navegar. Se desabilitar ou não configura esta definição de política, o utilizador pode optar por ignorar erros de certificado e continuar a navegar.
  
  **Predefinido**: Sim  

## <a name="connectivity"></a>Conectividade  
Para obter mais informações, consulte [CSP de política - conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) na documentação do Windows.  

- **Transferência de Internet de bloco para web de publicação e ordenação online assistentes**  
  Esta definição de política especifica se o Windows devem transferir uma lista de fornecedores para a web de publicação e ordenação online assistentes. Estes assistentes permitem que os utilizadores selecionarem uma lista de empresas que fornecem serviços como o armazenamento online e impressão photographic. Por predefinição, o Windows apresenta fornecedores transferidos a partir de um site do Windows para além de fornecedores especificado no registo. Se ativar esta definição de política, o Windows não transferir fornecedores e apenas os fornecedores de serviços que estão em cache no visor de registo local. Se desabilitar ou não configura esta definição de política, uma lista de fornecedores transfere quando o utilizador utiliza a web de publicação ou pedidos online assistentes. Para obter mais informações que inclui detalhes sobre a especificação de fornecedores de serviços no Registro, consulte a documentação para a web de publicação e ordenação online assistentes.  
  
  **Predefinido**: Enabled  

- **Bloquear o download dos controladores de impressão por HTTP**  
  Esta definição de política especifica se pretende permitir que este cliente transferir pacotes de controladores de impressão por HTTP. Para configurar a impressão de HTTP, drivers de caixa de entrada não tem de ser transferidos através de HTTP. Nota: Esta definição de política não impede que o cliente de impressão para impressoras na Intranet ou na Internet através de HTTP. Apenas proíbe a transferência de controladores que ainda não estiverem instalados localmente. Se ativar esta definição de política, os controladores de impressão não pode ser transferido através de HTTP. Se desabilitar ou não configura esta definição de política, os utilizadores podem transferir controladores de impressão por HTTP.
  
  **Predefinido**: Enabled  

## <a name="credentials-delegation"></a>Delegação de credenciais  
Para obter mais informações, consulte [CSP de política - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) na documentação do Windows.  

- **Delegação de anfitrião remoto de credenciais não exportável**  
  Anfitrião remoto permite que a delegação de credenciais não exportável. Ao utilizar a delegação de credenciais, os dispositivos fornecem uma versão exportável de credenciais para o anfitrião remoto, que expõe os utilizadores ao risco de roubo de credenciais contra invasores no anfitrião remoto. Se ativar esta definição de política, o anfitrião suporta o modo Admin restrito ou de Credential Guard remoto. Se desabilitar ou não configura esta definição de política, administração restrito e o modo de Credential Guard remoto não são suportados. Usuário sempre precisará passar as credenciais para o anfitrião.  

  
  **Predefinido**: Enabled  

## <a name="credentials-ui"></a>Credenciais da interface do Usuário  
Para obter mais informações, consulte [CSP de política - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) na documentação do Windows.  

- **Enumerar os administradores** esta política de definição de controles se as contas de administrador da tela quando um utilizador tenta elevar um aplicativo em execução. Por predefinição, as contas de administrador não são apresentadas quando o utilizador tenta elevar um aplicativo em execução. Se ativar esta definição de política, todas as contas de administrador local no PC apresentam para que o utilizador possa escolher um e introduza a palavra-passe correta. Se desativar esta definição de política, os usuários sempre terão de escreva um nome de utilizador e palavra-passe para elevar.  

  
  **Predefinido**: Desativado  

## <a name="data-protection"></a>Proteção de dados  
Para obter mais informações, consulte [CSP de política - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) na documentação do Windows.  

- **Bloquear acesso direto à memória**  
  Esta definição de política permite-lhe bloquear o acesso direto à memória (DMA) para todos os hot conectáveis PCI downstream portas até que um utilizador inicia sessão no Windows. Assim que um utilizador inicia sessão, o Windows irão enumerar os dispositivos PCI ligados as portas PCI do host plug. Sempre que o utilizador bloqueia a máquina, DMA está bloqueado nas portas PCI plug frequente sem dispositivos filhos até que o usuário fizer logon novamente. Dispositivos que já foram enumerados quando a máquina foi desbloqueada continuarão a funcionar até que não-conectado. Esta definição de política é imposta apenas quando a encriptação BitLocker ou o dispositivo está ativada.
  
  
  **Predefinido**: Sim  

## <a name="device-guard"></a>O Device Guard  
Para obter mais informações, consulte [CSP de política - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) na documentação do Windows.  

- **Credential Guard**  
  Esta definição permite aos utilizadores ativar o Credential Guard com a segurança baseada em virtualização para ajudar a proteger as credenciais no próximo reinício.
   
  **Predefinido**: Ativar com bloqueio UEFI 

- **Ativar a virtualização com base em segurança**  </br>
  Ativa a virtualização de segurança baseada em (VBS) no próximo reinício. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.
  
  **Predefinido**: Sim  

<!-- not yet available 
- **Enable secure boot with DMA**  
  Among the commands that follow, you can choose settings for Secure Boot and Secure Boot with DMA. In most situations, we recommend that you choose Secure Boot. This option provides Secure Boot with as much protection as is supported by a given computer’s hardware. A computer with input/output memory management units (IOMMUs) will have Secure Boot with DMA protection. A computer without IOMMUs will simply have Secure Boot enabled. In contrast, with Secure Boot with DMA, the setting will enable Secure Boot—and VBS itself—only on a computer that supports DMA, that is, a computer with IOMMUs. With this setting, any computer without IOMMUs won't have VBS or HVCI protection, although it can still have WDAC enabled.
  
  
  **Default**: Yes  
  -->
- **Inicie a proteção do sistema**    
  **Predefinido**: Enabled  

## <a name="device-installation"></a>Instalação de dispositivo  
Para obter mais informações, consulte [CSP de política - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) na documentação do Windows.  

- **Instalação de dispositivo de hardware por identificadores de dispositivo**  
  Esta definição de política permite-lhe especificar uma lista de IDs de hardware Plug and Play e identificações compatíveis com dispositivos que o Windows é impedidos de instalar. Esta definição de política tem precedência sobre qualquer outra definição de política que permite que o Windows instalar um dispositivo. Se ativar esta definição de política, o Windows é impedidos de instalar um dispositivo cujo hardware identificação compatível ou ID é apresentado na lista que cria. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a definição de política afeta o redirecionamento dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desabilitar ou não configura esta definição de política, os dispositivos podem instalar e atualizar como permitido ou impedido por outras configurações de diretiva.
  
  **Predefinido**: Instalação de dispositivo de hardware de bloco  

    Quando *bloqueia a instalação de dispositivo de hardware* é selecionado, as seguintes definições estão disponíveis.
  
    - **Remover dispositivos de hardware correspondente**   
    Esta definição só está disponível quando *instalação de dispositivo de Hardware por identificadores de dispositivo* está definida como *bloqueia a instalação de dispositivo de hardware*.
      
      **Predefinido**: Sim
  
    - **Identificadores de dispositivo de hardware que estão bloqueados**  
       Esta definição só está disponível quando *instalação de dispositivo de Hardware por identificadores de dispositivo* está definida como *bloqueia a instalação de dispositivo de hardware*.
      
      **Predefinido**: Sim  
  
- **Instalação de dispositivo de hardware por classes de instalação**  
  Esta definição de política permite-lhe especificar uma lista de dispositivos configuração classe identificadores globalmente exclusivos (GUIDs) para os controladores de dispositivo que o Windows é impedidos de instalar. Esta definição de política tem precedência sobre qualquer outra definição de política que permite que o Windows instalar um dispositivo. Se ativar esta definição de política, o Windows é impedidos de instalar ou atualizar drivers de dispositivo cujo classe de instalação do dispositivo GUIDs aparecem na lista de criar. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a definição de política afeta o redirecionamento dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desabilitar ou não configura esta definição de política, podem instalar o Windows e dispositivos de atualização como permitido ou impediam por outras configurações de diretiva.
  
  **Predefinido**: Instalação de dispositivo de hardware de bloco  

    Quando *bloqueia a instalação de dispositivo de hardware* é selecionado, as seguintes definições estão disponíveis.
    - **Remover dispositivos de hardware correspondente**    
    Esta definição só está disponível quando *instalação de dispositivo de Hardware por classes de instalação* está definida como *bloqueia a instalação de dispositivo de hardware*.  

      **Predefinido**: *Nenhuma configuração predefinida*  
  
    - **Identificadores de dispositivo de hardware que estão bloqueados**  
      Esta definição só está disponível quando *instalação de dispositivo de Hardware por classes de instalação* está definida como *bloqueia a instalação de dispositivo de hardware*.
      
      **Predefinido**: *Nenhuma configuração predefinida*  

## <a name="device-lock"></a>Bloqueio do dispositivo  
Para obter mais informações, consulte [CSP de política - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) na documentação do Windows.  

- **Impedir a utilização da câmara**  
  Desativa o comutador de estado do bloqueio ecrã câmara nas definições do PC e impede que uma câmera que está a ser invocado no ecrã de bloqueio. Por predefinição, os utilizadores podem permitir a invocação de uma câmera disponível no ecrã de bloqueio. Se ativar esta definição, os utilizadores já não poderão ativar ou desativar o acesso de câmera de ecrã de bloqueio em definições do PC e a câmara não pode ser invocada no ecrã de bloqueio. 
  
  **Predefinido**: Enabled  

- **Exigir palavra-passe**  
  Especifica se o bloqueio do dispositivo está ativado.
  
  **Predefinido**: Sim  
  
    Quando *exigir palavra-passe* está definida como *Sim*, as seguintes definições estão disponíveis.

    - **Contagem de conjunto de caracteres de mínimo de palavra-passe**  
      O número de tipos de elementos complexos (letras maiúsculas e minúsculas, números e pontuação) necessários para um PIN ou palavra-passe forte. PIN impõe o seguinte comportamento para computadores e dispositivos móveis: 1 - dígitos apenas 2 - dígitos e letras minúsculas são necessárias 3 - dígitos, letras minúsculas, e têm de letras maiúsculas. Não é suportado em contas do ambiente de trabalho Microsoft e contas de domínio. 4 - dígitos, letras minúsculas, letras maiúsculas e carateres especiais são necessários. Não é suportado no desktop. O valor predefinido é 1. 
      
      **Predefinido**: 3  
  
    - **Número de falhas de início de sessão antes de eliminar os dados do dispositivo**  
      O número de falhas de autenticação permitidas antes do dispositivo é apagado. Um valor de 0 desativa a funcionalidade de limpeza do dispositivo.
        
      **Predefinido**: 10  
  
    - **Expiração da Palavra-passe (dias)**  
      A definição de política de idade de palavra-passe máximo determina a forma como há muito tempo (em dias) que uma palavra-passe pode ser utilizada antes do sistema exige que o utilizador para alterá-lo. Pode definir palavras-passe para expirar após um número de dias entre 1 e 999, ou pode especificar que as palavras-passe nunca expirem ao definir o número de dias para 0. Se a idade de palavra-passe de máximo é entre 1 e 999 dias, a idade mínima da palavra-passe tem de ser inferior a idade máxima da palavra-passe. Se a idade de palavra-passe máximo for definida como 0, a idade de palavra-passe mínimo pode ser qualquer valor entre 0 e 998 dias.
      
      **Predefinido**: 60  
  
    - **Tipo obrigatório de palavra-passe**  
      Determina o tipo de PIN ou palavra-passe necessária.
      
      **Predefinido**: Alfanumérico  
  
    - **Comprimento mínimo da palavra-passe**  
      A definição de política de comprimento de palavra-passe mínima determina o menor número de carateres que podem tornar uma palavra-passe para uma conta de utilizador. Pode definir um valor entre 1 e 14 carateres, ou pode estabelecer que nenhuma palavra-passe é necessária para definir o número de carateres como 0.
      
      **Predefinido**: 8  
  
    - **Bloquear palavras-passe simples**  
      Especifica se os PINs ou palavras-passe como "1111" ou "1234" são permitidas. Para a área de trabalho, este também controla o uso de senhas com imagem.
      
      **Predefinido**: Sim  
        *Uma definição de Sim impede a utilização de palavras-passe simples.* 

  - **Impedir a reutilização de palavras-passe anteriores**  
    Especifica quantas palavras-passe podem ser armazenadas no histórico de que não pode ser utilizado. O valor inclui a palavra-passe do utilizador atual. Por exemplo, com uma definição de *1* o utilizador não é possível reutilizar a palavra-passe atual ao escolher uma nova palavra-passe. Uma definição de *5* significa que um utilizador não é possível definir a palavra-passe nova para a palavra-passe atual ou qualquer uma das suas palavras-passe anteriores quatro.
    
    **Predefinido**: 24  

- **Impedir a apresentação de diapositivos**  
  Desativa as definições de apresentação de slides do ecrã de bloqueio em definições do PC e impede que uma apresentação de diapositivos reproduzindo no ecrã de bloqueio. Por predefinição, os utilizadores podem ativar uma apresentação de slides que será executado depois que a máquina de bloqueio. Se ativar esta definição, os utilizadores não é possível modificar as definições de apresentação de slides nas definições do PC, e não de slides pode começar.
  
    **Predefinido**: Enabled  
    *Uma definição de ativado impede que o slide mostra a execução.* 

- **Idade mínima da palavra-passe em dias**  
  A definição de política de idade de palavra-passe mínima determina o período de tempo (em dias) que uma palavra-passe tem de ser utilizada antes do utilizador pode alterá-lo. Pode definir um valor entre 1 e 998 dias, ou pode permitir que as alterações de palavra-passe imediatamente ao definir o número de dias para 0. A idade mínima da palavra-passe tem de ser inferior a idade de palavra-passe máximo, a menos que a idade máxima da palavra-passe está definida como 0, que indica que as palavras-passe nunca expira. Se a idade máxima da palavra-passe é definida como 0, a idade mínima da palavra-passe pode ser definida para qualquer valor entre 0 e 998.
  
    **Predefinido**: 1  

## <a name="event-log-service"></a>Serviço de registo de eventos  
Para obter mais informações, consulte [CSP de política - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) na documentação do Windows.  

- **Tamanho máximo do ficheiro de registo de segurança no artigo BDC**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho do ficheiro de registo máximo para ser entre 1 megabyte (1024 quilobytes) e 2 terabytes (quilobytes 2147483647) em incrementos de kilobytes. Se desabilitar ou não configura esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local usando a caixa de diálogo de propriedades de registo e é assumida como predefinição para 20 megabytes.
  
   **Predefinido**: 196608  

- **Tamanho máximo do ficheiro de registo de sistema no artigo BDC**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho do ficheiro de registo máximo para ser entre 1 megabyte (1024 quilobytes) e 2 terabytes (quilobytes 2147483647) em incrementos de kilobytes. Se desabilitar ou não configura esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local usando a caixa de diálogo de propriedades de registo e é assumida como predefinição para 20 megabytes.
  
  **Predefinido**: 32768  

- **Tamanho máximo do ficheiro de registo de aplicação no artigo BDC**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho do ficheiro de registo máximo para ser entre 1 megabyte (1024 quilobytes) e 2 terabytes (quilobytes 2147483647) em incrementos de kilobytes. Se desabilitar ou não configura esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local usando a caixa de diálogo de propriedades de registo e é assumida como predefinição para 20 megabytes.
  
  **Predefinido**: 32768  

## <a name="experience"></a>Experiência  
Para obter mais informações, consulte [CSP de política - experiência](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) na documentação do Windows.  

- **Bloquear destaque do Windows**  
  Permite que os administradores de TI desativar todos os Windows funcionalidades de destaque - destaque do Windows no funcionalidades do consumidor do bloqueio ecrã, dicas do Windows, Microsoft e outras funcionalidades relacionadas.
  
  **Predefinido**: Sim  

  Quando *destaque do Windows bloquear* está definida como *Sim*, as seguintes definições estão disponíveis.
  
  - **Bloquear as sugestões de terceiros no destaque do Windows**  
    Especifica se a permitir sugestões de aplicações e conteúdos do software de terceiros publicadores no Windows em destaque funcionalidades como o destaque do ecrã de bloqueio, aplicações sugeridas no menu Iniciar e dicas do Windows. Utilizadores ainda poderão ver sugestões de funcionalidades, aplicações e serviços Microsoft.
      
    **Predefinido**: Sim  
   - **Bloquear recursos específicos do consumidor**  
      Permite que os administradores de TI ativem experiências normalmente destinadas a consumidores apenas, tais como sugestões de início, notificações de associação, instalação de aplicações pós-OOBE, e mosaicos de redirecionamento.
      
     **Predefinido**: Sim  


## <a name="exploit-guard"></a>Exploit Guard  
Para obter mais informações, consulte [CSP de política - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) na documentação do Windows.  

- **Proteção de exploração XML**  
  Permite que o administrador de TI produzir uma configuração que representa o sistema pretendido e as opções de atenuação do aplicativo para todos os dispositivos da organização. A configuração é representada por um XML. Exploit protection ajuda a proteger os dispositivos contra software maligno que utilize explorações para distribuir e infectar. Utilize a aplicação de segurança do Windows ou o PowerShell para criar um conjunto de atenuações (conhecido como configuração). Em seguida, pode exportar esta configuração como um arquivo XML e partilhe-a com várias máquinas na sua rede para que todos eles têm o mesmo conjunto de definições de atenuação. Também pode converter e importar um arquivo XML de configuração EMET existente para um XML de configuração da proteção de exploração.
  
  **Predefinido**: *Xml de exemplo é fornecido* 
 
## <a name="file-explorer"></a>Explorador de Ficheiros  
Para obter mais informações, consulte [CSP de política - Explorador de ficheiros](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) na documentação do Windows.  

- **Prevenção de execução de dados de bloco**  
  Desabilitar a prevenção de execução de dados pode permitir que determinados aplicativos herdados de plug-ins a funcionar sem terminação Explorer.
  
  **Predefinido**: Desativado  
   
- **Terminação de área dinâmica para dados de bloco em Corrupção**  
  Desativar a terminação de área dinâmica para dados em corrupção pode permitir que determinados aplicativos herdados de plug-ins a funcionar sem terminação Explorer imediatamente, embora Explorer pode ainda terminar inesperadamente mais tarde.
  
  **Predefinido**: Desativado  
    

## <a name="internet-explorer"></a>Internet Explorer  
Para obter mais informações, consulte [CSP de política - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) na documentação do Windows.  
<!-- not yet available 
- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Disabled  
  
- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Disable  
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Disable  
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: Disabled  
 -->
- **Acesso da zona de internet do Internet Explorer para origens de dados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer pode acessar dados de outra zona de segurança com o Microsoft XML Parser (MSXML) ou ActiveX Data Objects (ADO). Se ativar esta definição de política, os utilizadores podem carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que uma página carregar na zona que utiliza o MSXML ou o ADO para acessar dados de outro site na zona. Se desativar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se não configurar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona.
  
  **Predefinido**: Desativar  
  
- **Zona restrita do Internet Explorer arrastar o conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão na mesma janela. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores não é possível alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta definição de política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores não é possível alterar esta definição na caixa de diálogo Opções da Internet.
  
  **Predefinido**: Desativado
  
- **Aviso de erro de correspondência do endereço de certificado do Internet Explorer**  
  Esta definição de política permite-lhe ativar o aviso de segurança de erro de correspondência de endereço do certificado. Quando esta definição de política é ativada, o usuário é avisado quando visita Web sites HTTP Secure (HTTPS) que presentes certificados emitidos para um endereço de outro Web site. Este aviso ajuda a impedir ataques de falsificação. Se ativar esta definição de política, o certificado endereço erro de correspondência de aviso sempre será exibido. Se desabilitar ou não configura esta definição de política, o usuário pode escolher se o aviso de erro de correspondência do endereço de certificado é apresentado (ao utilizar a página avançada no painel de controlo da Internet).
  
  **Predefinido**: Enabled 
  
- **Zona restrita do Internet Explorer menos sites com privilégios**  
  Esta definição de política permite-lhe gerir se sites da Web de zonas com menos privilégios, tais como sites da Internet, pode navegar para esta zona. Se ativar esta definição de política, Web sites de zonas com menos privilégios pode abrir novas janelas no ou navegue para esta zona. A zona de segurança serão executados sem a camada adicional de segurança que é fornecida pela proteção da funcionalidade de segurança de elevação de zona. Se selecionar a linha de comandos na caixa de lista pendente, é emitido um aviso ao utilizador que potencialmente perigoso navegação está prestes a ocorrer. Se desativar esta definição de política, é impedida a navegação possivelmente prejudicial. A funcionalidade de segurança do Internet Explorer está nesta zona conforme definido pela proteção de controlo de recursos de elevação de zona. Se não configurar esta definição de política, são impedidas as navegações possivelmente prejudiciais. A funcionalidade de segurança do Internet Explorer está nesta zona conforme definido pela proteção de controlo de recursos de elevação de zona.
  
  **Predefinido**: Desativar  
  
- **Downloads do Internet Explorer zona restritas automática linha de comandos para o ficheiro**  
  Esta definição de política determina se é pedido aos utilizadores para as transferências de ficheiros não iniciada pelo utilizador. Independentemente desta definição, os utilizadores irão receber caixas de diálogo de download de arquivo para downloads iniciada pelo utilizador. Se ativar esta definição, os utilizadores irão receber uma caixa de diálogo de download de arquivo para tentativas de transferência automática. Se desabilitar ou não configura esta definição, as transferências de ficheiros que não são iniciados pelo usuário são bloqueadas e os utilizadores verão a barra de notificação, em vez da caixa de diálogo de download do arquivo. Os utilizadores podem, em seguida, clicar a barra de notificação para permitir que o pedido de transferência de ficheiros.
  
  **Predefinido**: Desativado
  
- **Componentes da habilitação de .NET Framework zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que não são assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados não assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados não assinados. Se desativar esta definição de política, o Internet Explorer não irá executar componentes gerenciados não assinados. Se não configurar esta definição de política, o Internet Explorer será executado componentes gerenciados não assinados.
  
  **Predefinido**: Desativar 
  
- **Permitir que a zona de internet de Internet Explorer apenas aprovados domínios para usar controles do ActiveX tdc**  
  Esta definição de política controla se o utilizador pode executar o controle TDC ActiveX nos Web sites. Se ativar esta definição de política, o controle TDC ActiveX não será executado de Web sites nesta zona. Se desativar esta definição de política, o controle de TDC Active X será executado de todos os sites desta zona.
  
  **Predefinido**: Enabled 
  
- **Script de zona do Internet Explorer restrito iniciadas pelo windows**  
  Esta definição de política permite-lhe gerir restrições para janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Se ativar esta definição de política, não se aplicam a segurança de restrições do Windows nesta zona. A zona de segurança é executado sem a camada de segurança fornecida por esta funcionalidade adicional. Se desativar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows. Se não configurar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows.
  
  **Predefinido**: Desativado 
  
- **Zona de internet do Internet Explorer incluir o caminho local, ao carregar ficheiros para o servidor**  
  Esta definição de política controla se as informações de caminho local são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se as informações de caminho local são enviadas, algumas informações podem inadvertidamente reveladas para o servidor. Por exemplo, os arquivos enviados a partir do ambiente de trabalho do usuário podem conter o nome de utilizador como parte do caminho. Se ativar esta definição de política, informações de caminho são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se desativar esta definição de política, informações de caminho são removidas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se não configurar esta definição de política, o usuário pode escolher se as informações de caminho são enviadas quando eles carregam um ficheiro através de um formulário HTML. Por predefinição, são enviadas informações de caminho.
  
  **Predefinido**: Desativado 
  
- **Internet Explorer desativar processos no modo protegido avançado**  
  Esta definição de política determina se Internet Explorer 11 utiliza os processos de 64 bits (para maior segurança) ou processos de 32 bits (para maior compatibilidade) quando em execução no modo protegido avançado em versões de 64 bits do Windows. Importante: Alguns controles ActiveX e barras de ferramentas poderão não estar disponíveis quando são utilizados os processos de 64 bits. Se ativar esta definição de política, o Internet Explorer 11 usará os processos de separador de 64 bits quando em execução no modo protegido avançado em versões de 64 bits do Windows. Se desativar esta definição de política, o Internet Explorer 11 usará os processos de separador de 32 bits quando em execução no modo protegido avançado em versões de 64 bits do Windows. Se não configurar esta definição de política, os utilizadores podem ativar esta funcionalidade ativada ou desativada com as definições do Internet Explorer. Esta funcionalidade está desativada por predefinição.
  
  **Predefinido**: Enabled 
  
- **Internet Explorer ignorar erros de certificado**  
  Esta definição de política impede que o utilizador a ignorar erros de certificado de Secure Sockets Layer/Transport Layer Security (SSL/TLS) que interrompem a navegação (como "expirada", "revogado" ou erros de "erro de correspondência do nome") no Internet Explorer. Se ativar esta definição de política, o utilizador não é possível continuar a navegar. Se desabilitar ou não configura esta definição de política, o utilizador pode optar por ignorar erros de certificado e continuar a navegar.
  
  **Predefinido**: Desativado 
  
- **Carregamento de zona de internet do Internet Explorer de arquivos XAML**  
  Esta definição de política permite-lhe gerir o carregamento de ficheiros de de Extensible Application Markup Language (XAML). XAML é uma linguagem de marcação declarativa baseada em XML usada para criar interfaces do usuário avançadas e gráficos que tiram partido do Windows Presentation Foundation. Se ativar esta definição de política e defina a caixa de lista pendente para ativar, arquivos XAML são automaticamente carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se definir a caixa de lista pendente à linha de comandos, é pedido ao utilizador para carregar arquivos XAML. Se desativar esta definição de política, os arquivos XAML não são carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se não configurar esta definição de política, o usuário pode decidir se pretende carregar arquivos XAML no Internet Explorer.
  
  **Predefinido**: Desativar 
  
- **Downloads de prompt automática do Internet Explorer internet zona para o ficheiro**  
  Esta definição de política determina se é pedido aos utilizadores para as transferências de ficheiros não iniciada pelo utilizador. Independentemente desta definição, os utilizadores irão receber caixas de diálogo de download de arquivo para downloads iniciada pelo utilizador. Se ativar esta definição, os utilizadores irão receber uma caixa de diálogo de download de arquivo para tentativas de transferência automática. Se desabilitar ou não configura esta definição, as transferências de ficheiros que não são iniciados pelo usuário são bloqueadas e os utilizadores verão a barra de notificação, em vez da caixa de diálogo de download do arquivo. Os utilizadores podem, em seguida, clicar a barra de notificação para permitir que o pedido de transferência de ficheiros.
  
  **Predefinido**: Enabled  
  
- **Aviso de segurança da zona para ficheiros potencialmente não seguros de restritos do Internet Explorer**  
  Esta definição de política controla se a mensagem de "Abrir ficheiro – Aviso de segurança" é apresentada quando o utilizador tenta abrir arquivos executáveis ou de outros ficheiros potencialmente não seguros (a partir de uma partilha de ficheiros à intranet com o Explorador de ficheiros, por exemplo). Se ativar esta definição de política e defina a caixa de lista pendente para ativar, abrir estes ficheiros sem um aviso de segurança. Se definir a caixa de lista pendente à linha de comandos, é apresentado um aviso de segurança antes de abrir os ficheiros. Se desativar esta definição de política, estes ficheiros não abrem. Se não configurar esta definição de política, o utilizador pode configurar como o computador lida com esses arquivos. Por predefinição, estes ficheiros estão bloqueados na zona restrita, ativada em zonas da Intranet e o computador Local e definidos para solicitar nas zonas Internet e confiáveis da.
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer em várias filtro de scripts do site**  
  Esta política controla se o filtro de scripts de sites (XSS) irá detetar e prevenir injeções de script entre sites em Web sites nesta zona. Se ativar esta definição de política, o Filtro XSS está ativado para os sites desta zona e o Filtro XSS tenta bloquear injeções de script entre sites. Se desativar esta definição de política, o Filtro XSS está desativado para sites desta zona e o Internet Explorer permite injeções de script entre sites.
  
  **Predefinido**: Enabled 
  
- **Contingência de Internet Explorer para SSL3**  
  Esta definição de política permite-lhe bloquear uma contingência insegura para SSL 3.0. Quando esta política está ativada, Internet Explorer irá tentar ligar a sites usando o SSL 3.0 ou abaixo quando falha TLS 1.0 ou superior. Recomendamos que não permitir contingência insegura para evitar um ataque man-in-the-middle. Esta política não afeta os protocolos de segurança estão ativados. Se desativar esta política, são utilizadas as predefinições do sistema.
  
  **Predefinido**: Não existem sites 
  
- **Bloqueado ecrã inteligentes de zona de internet do Internet Explorer**  
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.
  
  **Predefinido**: Enabled 
  
- **Internet Explorer restrito a aplicativos de inicialização de zona e arquivos num iFrame**  
  Esta definição de política permite-lhe gerir se os aplicativos podem ser executados e arquivos podem ser transferidos a partir de uma referência IFRAME no HTML das páginas nesta zona. Se ativar esta definição de política, os utilizadores podem executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona. Se desativar esta definição de política, os utilizadores são impedidos de execução de aplicativos e o download de arquivos de IFRAMEs nas páginas nesta zona. Se não configurar esta definição de política, os utilizadores são impedidos de execução de aplicativos e o download de arquivos de IFRAMEs nas páginas nesta zona.
  
  **Predefinido**: Desativar 
  
- **Internet Explorer ignore os avisos do SmartScreen sobre ficheiros invulgares**  
  Esta definição de política determina se o utilizador pode ignorar avisos do Filtro SmartScreen. O Filtro SmartScreen avisa o utilizador sobre ficheiros executáveis que usuários do Internet Explorer geralmente não transferirem a partir da Internet. Se ativar esta definição de política, os avisos do Filtro SmartScreen impedir o utilizador. Se desabilitar ou não configura esta definição de política, o utilizador pode ignorar avisos do Filtro SmartScreen.
  
  **Predefinido**: Desativado  
  
- **Bloqueador de pop-up de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se indesejados janelas de pop-up aparecem. Janelas de pop-up que foram abertas quando o utilizador final clica num link não são bloqueadas. Se ativar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer. Se desativar esta definição de política, janelas pop-up não são impedidas de aparecer. Se não configurar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer.
  
  **Predefinido**: Ativar  
  
- **Internet Explorer processa a manipulação do MIME consistente**  
  Internet Explorer contém aos comportamentos binários dinâmicos: os componentes que encapsulam a funcionalidade específica para os elementos HTML ao qual estão anexadas. Esta definição de política de controlos se a definição de restrição de segurança de comportamento binário é impedida ou não permitida. Se ativar esta definição de política, são impedidos aos comportamentos binários para os processos de Explorador de ficheiros e o Internet Explorer. Se desativar esta definição de política, aos comportamentos binários são permitidos para os processos de Explorador de ficheiros e o Internet Explorer. Se não configurar esta definição de política, são impedidos aos comportamentos binários para os processos de Explorador de ficheiros e o Internet Explorer.
  
  **Predefinido**: Enabled  
  
- **Permissões de java de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.
  
  **Predefinido**: Desativar o java  
    
  
- **Controles do Internet Explorer Active X no modo protegido**  
  Esta definição de política impede que os controles ActiveX em execução no modo protegido, quando o modo protegido avançado está ativado. Quando um utilizador tiver um controle ActiveX instalado que não é compatível com modo protegido avançado e um Web site tenta carregar o controle, o Internet Explorer notifica o utilizador e oferece a opção para executar o Web site no modo protegido regular. Esta definição de política desativa esta notificação e força todos os Web sites para executar no modo protegido avançado. Modo protegido avançado proporciona proteção adicional contra sites mal-intencionados utilizando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam, pelo menos, Windows 8, o modo protegido avançado também limita os locais do Internet Explorer pode ler a partir do Registro e o sistema de ficheiros. Quando o modo protegido avançado está ativado e um utilizador se depara com um Web site que tenta carregar um controle ActiveX que não é compatível com modo protegido avançado, o Internet Explorer notifica o utilizador e oferece a opção para desativar o modo protegido avançado para esse determinado site. Se ativar esta definição de política, o Internet Explorer não dar ao usuário a opção para desativar o modo protegido avançado. Todos os Web sites de modo protegido serão executado no modo protegido avançado. Se desabilitar ou não configura esta definição de política, o Internet Explorer notifica os utilizadores e fornece uma opção para executar Web sites com os controles ActiveX incompatíveis no modo protegido regular.  
  
  **Predefinido**: Desativado  
  
- **Carregamento de zona restritos do Internet Explorer de arquivos XAML**  
  Esta definição de política permite-lhe gerir o carregamento de ficheiros de de Extensible Application Markup Language (XAML). XAML é uma linguagem de marcação declarativa baseada em XML usada para criar interfaces do usuário avançadas e gráficos que tiram partido do Windows Presentation Foundation. Se ativar esta definição de política e defina a caixa de lista pendente para ativar, arquivos XAML são automaticamente carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se definir a caixa de lista pendente à linha de comandos, é pedido ao utilizador para carregar arquivos XAML. Se desativar esta definição de política, os arquivos XAML não são carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se não configurar esta definição de política, o usuário pode decidir se pretende carregar arquivos XAML no Internet Explorer.
  
  **Predefinido**: Desativar  
  
- **Restrições de segurança de janela com script de processos do Internet Explorer**  
  Internet Explorer permite que os scripts por meio de programação abrir, redimensionar e reposicionar windows de vários tipos. A funcionalidade de segurança de restrições de janela restringe janelas pop-ups e proíbe scripts do windows na qual as barras de título e o estado não são visíveis para o utilizador ou oculte o título dos outros Windows e as barras de estado de exibição. Se ativar esta definição de política, com scripts do windows são restrito para todos os processos. Se desabilitar ou não configura esta definição de política, com scripts do windows não são restrito.
  
  **Predefinido**: Enabled   
  
- **Zona restrita do Internet Explorer executar Active X controlos e plug-ins**  
  Esta definição de política permite-lhe gerir se os controles ActiveX e plug-ins pode executar em páginas da zona especificada. Se ativar esta definição de política, controlos e plug-ins podem ser executados sem intervenção do utilizador. Se tiver selecionado a linha de comandos na caixa de lista pendente, os usuários são mais freqüentes para escolher se pretende permitir que os controles ou plug-in para ser executado. Se desativar esta definição de política, controlos e plug-ins são impedidos de execução. Se não configurar esta definição de política, controlos e plug-ins são impedidos de execução.
  
  **Predefinido**: Desativar  
  
- **Script de zona de Internet Explorer restrito que Active X controla marcados como seguro para scripting**  
  Esta definição de política permite-lhe gerir se um controle ActiveX marcados como seguro para scripting pode interagir com um script. Se ativar esta definição de política, a interação de script pode ocorrer automaticamente sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir a interação de script. Se desativar esta definição de política, a interação de script é impedida de ocorrer. Se não configurar esta definição de política, a interação de script é impedida de ocorrer.
  
  **Predefinido**: Desativar  
  
- **Opções de início de sessão de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir as definições para as opções de início de sessão. Se ativar esta definição de política, pode escolher entre o início de sessão seguintes opções. 
  - *Anónimo* - a utilizar anónimo início de sessão para desative a autenticação HTTP e utilizar a conta de convidado apenas para o protocolo Common Internet File System (CIFS). 
  - *Linha de comandos* -aviso de utilização para o nome de utilizador e palavra-passe para os utilizadores da consulta de IDs de utilizador e palavras-passe. Depois de um utilizador é consultado, estes valores podem ser utilizados em automaticamente para o resto da sessão. 
  - *Início de sessão automático em apenas na zona de Intranet* -Utilize esta opção para os utilizadores da consulta para IDs de utilizador e palavras-passe noutras zonas. Depois de um utilizador é consultado, estes valores podem ser utilizados em automaticamente para o resto da sessão. 
  - *Automática inicie a sessão com o nome do usuário atual e a palavra-passe*-Utilize esta opção para tentar iniciar sessão com a resposta de desafio do Windows NT (também conhecido como autenticação de NTLM). Se o servidor suportar a resposta de desafio do Windows NT, o início de sessão utiliza nome de utilizador de rede do utilizador e palavra-passe para iniciar sessão. Se o servidor não suporta a resposta de desafio do Windows NT, o utilizador é consultado para fornecer o nome de utilizador e palavra-passe. 

  Se desativar esta definição de política, o início de sessão está definido como *automático iniciar sessão apenas na zona de Intranet*. Se não configurar esta definição de política, o início de sessão está definido como *Prompt* nome de utilizador e palavra-passe.
  
  **Predefinido**: Anónima  
  
- **Internet Explorer fidedigna inicializar de zona e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script.
  
  **Predefinido**: Desativar  
  
- **Revogação de certificados de servidor de verificação do Internet Explorer**  
  Esta definição de política permite-lhe gerir se o Internet Explorer irá verificar o estado de revogação de certificados dos servidores. Os certificados são revogados quando forem comprometidos ou já não são válidas e esta opção protege os usuários de submeter dados confidenciais a um site que pode ser fraudulentos ou não segura. Se ativar esta definição de política, Internet Explorer irá verificar se os certificados de servidor tiverem sido revogados. Se desativar esta definição de política, o Internet Explorer não verificar os certificados de servidor para ver se eles foram revogados. Se não configurar esta definição de política, o Internet Explorer não verificar os certificados de servidor para ver se eles foram revogados.
  
  **Predefinido**: Enabled 
  
- **Zona de internet do Internet Explorer menos sites com privilégios**  
  Esta definição de política permite-lhe gerir se sites da Web de zonas com menos privilégios, tais como Sites restritos, pode navegar para esta zona. Se ativar esta definição de política, Web sites de zonas com menos privilégios pode abrir novas janelas no ou navegue para esta zona. A zona de segurança serão executados sem a camada adicional de segurança que é fornecida pela proteção da funcionalidade de segurança de elevação de zona. Se selecionar a linha de comandos na caixa de lista pendente, é emitido um aviso ao utilizador que potencialmente perigoso navegação está prestes a ocorrer. Se desativar esta definição de política, são impedidas as navegações possivelmente prejudiciais. A funcionalidade de segurança do Internet Explorer está nesta zona conforme definido pela proteção de controlo de recursos de elevação de zona. Se não configurar esta definição de política, Web sites de zonas com menos privilégios pode abrir novas janelas no ou navegue para esta zona.
  
  **Predefinido**: Desativar  
  
- **Downloads do ficheiro de zona restritos do Internet Explorer**  
  Esta definição de política permite-lhe gerir se downloads de arquivos são permitidos da zona. Esta opção é determinada pela zona da página com a ligação que faz com que o download, não a partir do qual o ficheiro é entregue de zona. Se ativar esta definição de política, os ficheiros podem ser baixados da zona. Se desativar esta definição de política, os ficheiros são impedidos de que está a ser transferido a partir da zona. Se não configurar esta definição de política, os ficheiros são impedidos de que está a ser transferido a partir da zona.
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer executar componentes do .NET Framework baseia-se assinado com Authenticode**  
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que estão assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados assinados. Se desativar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados. Se não configurar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados.
  
  **Predefinido**: Desativar  
  
- **Impedir o Internet Explorer por instalação de utilizador de controles de Active X**  
  Esta definição de política permite-lhe impedir a instalação de controles ActiveX numa base por utilizador. Se ativar esta definição de política, os controles ActiveX não podem ser instalados numa base por utilizador. Se desabilitar ou não configura esta definição de política, os controles ActiveX podem ser instalados numa base por utilizador.
  
  **Predefinido**: Enabled  
  
- **Impedir o Internet Explorer gerir o Filtro SmartScreen**  
  Esta definição de política impede que o utilizador gira o Filtro SmartScreen, que avisa o usuário se o Web site que visitar é conhecido por fraudulentas tentativas recolher informações pessoais por meio de "phishing", ou que é conhecido por hospedar malware. Se ativar esta definição de política, não é pedido ao utilizador para o Filtro SmartScreen. Todos os endereços de Web site que não estão nos filtros permitem que lista são automaticamente enviados à Microsoft sem pedir intervenção do utilizador. Se desabilitar ou não configura esta definição de política, é pedido ao utilizador que decida se pretende ativar o Filtro SmartScreen durante a experiência de primeira execução.
  
  **Predefinido**: Ativar  
  
- **Internet Explorer processa a funcionalidade de segurança de farejamento MIME**  
  Esta definição de política determina se a detecção de MIME do Internet Explorer irá impedir que a promoção de um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se ativar esta definição de política, a detecção de MIME nunca promover um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se desativar esta definição de política, os processos do Internet Explorer permitirá uma pesquisa MIME promover um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se não configurar esta definição de política, a detecção de MIME nunca promover um ficheiro de um tipo para um tipo de ficheiro mais perigoso.
  
  **Predefinido**: Enabled  
  
- **Transferência de zona restritos do Internet Explorer assinado controles Active X**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX assinados de uma página na zona. Se ativar esta política, os utilizadores podem transferir assinados controles sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido. Se desativar a definição de política, não é possível transferir controles assinados. Se não configurar esta definição de política, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido.
  
  **Predefinido**: Desativar  
  
- **Preenchimento automático de Internet Explorer**  
  Esta funcionalidade de conclusão automática pode Lembre-se e sugere nomes de utilizador e palavras-passe em formulários. Se ativar esta definição, o utilizador não é possível alterar "nome de utilizador e palavras-passe em formulários" ou "Avisar-me para guardar palavras-passe". A funcionalidade completa de automática para nomes de utilizador e palavras-passe em formulários é ativada. Precisa decidir se pretende selecionar "Avisar-me para guardar palavras-passe". Se desativar esta definição o utilizador não é possível alterar "nome de utilizador e palavras-passe em formulários" ou "Avisar-me para guardar palavras-passe". A funcionalidade completa de automática para nomes de utilizador e palavras-passe em formulários está desativada. O utilizador também não é possível optar por ser-lhe pedido para guardar palavras-passe. Se não configurar esta definição, o utilizador tem a liberdade de Ativando automática concluída para o nome de utilizador e palavras-passe em formulários e a opção de solicitar a guardar palavras-passe. Para apresentar esta opção, os utilizadores abrir a caixa de diálogo Opções da Internet, clique no separador de conteúdo e clique no botão configurações.
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer permitir VBscript executar**  
  Esta definição de política permite-lhe decidir se VBScript pode ser executado nas páginas em horários específicos do Internet Explorer. As opções incluem: 
  - *Ativar* -VBScript é executado nas páginas em horários específicos, sem qualquer interação do utilizador. 
  - *Linha de comandos* -funcionários-lhe pedidos se pretende permitir que o VBScript executar na zona. 
  - *Desativar* -VBScript é impedido de executar na zona. Se desativar ou não configurar esta definição de política, o VBScript é executado sem qualquer interação na zona especificada. 
  
  **Predefinido**: Desativar  
  
- **Internet Explorer, permitir que a zona restritas apenas aprovados domínios usar controles de Active X tdc**  
  Esta definição de política controla se o utilizador pode executar o controle TDC ActiveX nos Web sites. Se ativar esta definição de política, o controle TDC ActiveX não será executado de Web sites nesta zona. Se desativar esta definição de política, o controle de TDC Active X será executado de todos os sites desta zona.
  
  **Predefinido**: Enabled  
  
- **Zona de confiança do Internet Explorer não são executados antimalware controles Active X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.
  
  **Predefinido**: Desativado 
  
- **Permissões do java de zona de computador local do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para segurança média.
  
  **Predefinido**: Desativar o java 
  
- **Antimalware não execute de zona de intranet do Internet Explorer Active X controles** esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se eles são seguros carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.
  
  **Predefinido**: Desativado  

- **Scriptlets de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir se o utilizador pode executar scriptlets. Se ativar esta definição de política, o utilizador pode executar scriptlets. Se desativar esta definição de política, o utilizador não é possível executar scriptlets. Se não configurar esta definição de política, o utilizador pode ativar ou desativar scriptlets.
  
  **Predefinido**: Desativado  
  
- **Barra de notificação de processos do Internet Explorer**  
  Esta definição de política permite-lhe gerir se a barra de notificação é apresentada para processos do Internet Explorer, quando instala ficheiros ou de código é restrita. Por predefinição, a barra de notificação é apresentada para processos do Internet Explorer. Se ativar esta definição de política, apresenta a barra de notificação para os processos do Internet Explorer. Se desativar esta definição de política, a barra de notificação não ser apresentada para processos do Internet Explorer. Se não configurar esta definição de política, não exibe a barra de notificação para processos do Internet Explorer.
  
  **Predefinido**: Enabled  
  
- **Transferência de zona de internet do Internet Explorer assinado controles ActiveX**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX assinados de uma página na zona. Se ativar esta política, os utilizadores podem transferir assinados controles sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido. Se desativar a definição de política, não é possível transferir controles assinados. Se não configurar esta definição de política, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido.
  
  **Predefinido**: Desativar  
  
- **Ecrã de inteligente de zona restritas do Internet Explorer**  
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer remover executar este botão de tempo para controles de Active X desatualizados**  
  Esta definição de política permite-lhe impedir que os utilizadores visualizem o botão "Executar agora" e a execução de controles específicos de ActiveX desatualizados no Internet Explorer. Se ativar esta definição de política, os utilizadores não verão o botão "Executar agora" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Se desabilitar ou não configura esta definição de política, os utilizadores verão o botão "Executar agora" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Clicar neste botão permite que o utilizador executar uma vez o controle ActiveX desatualizado. Para obter mais informações, consulte "Desatualizado os controles ActiveX" na Biblioteca TechNet do Internet Explorer.
  
  **Predefinido**: Enabled 
  
- **Aplicativos de inicialização de zona de internet do Internet Explorer e arquivos num iframe**  
  Esta definição de política permite-lhe gerir se os aplicativos podem ser executados e arquivos podem ser transferidos a partir de uma referência IFRAME no HTML das páginas nesta zona. Se ativar esta definição de política, os utilizadores podem executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona. Se desativar esta definição de política, os utilizadores são impedidos de execução de aplicativos e o download de arquivos de IFRAMEs nas páginas nesta zona. Se não configurar esta definição de política, os utilizadores são consultados para escolher se pretende executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona
  
  **Predefinido**: Desativar 
  
- **Zona restrita do Internet Explorer navegue windows e os quadros em diferentes domínios**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão no windows diferentes. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e de destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição.
  
  **Predefinido**: Desativar  
  
- **Ecrã inteligente de zona de internet do Internet Explorer**  
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer é bloqueado por permissões de java da zona de confiança**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.
  
  **Predefinido**: Desativar o java 
  
- **Internet Explorer verificar assinaturas em programas baixados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer verifica a existência de assinaturas digitais (que identifica o publicador de software assinado e verifica se ainda não foram modificado ou adulterado) em computadores de usuários antes de transferir os programas executáveis. Se ativar esta definição de política, o Internet Explorer verificar as assinaturas digitais de programas executáveis e apresentar as suas identidades antes de transferi-los para computadores de usuários. Se desativar esta definição de política, o Internet Explorer não verificar as assinaturas digitais de programas executáveis ou visualizar suas identidades antes de transferi-los para computadores de usuários. Se não configurar esta política, o Internet Explorer não verificar as assinaturas digitais de programas executáveis ou visualizar suas identidades antes de transferi-los para computadores de usuários.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer restrito a zona de script de controles de navegador da web**  
  Esta definição de política determina se uma página pode controlar o embedded WebBrowser controles por meio de script. Se ativar esta definição de política, é permitido o acesso de script para o controle WebBrowser. Se desativar esta definição de política, não é permitido o acesso de script para o controle WebBrowser. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o acesso de script para o controle WebBrowser. Por predefinição, o acesso de script para o controle WebBrowser é permitido apenas no computador Local e zonas da Intranet.
  
  **Predefinido**: Desativado  
  
- **Filtro de scripts do site em várias de zona restrita do Internet Explorer**  
  Esta política controla se o filtro de scripts de sites (XSS) irá detetar e prevenir injeções de script entre sites em Web sites nesta zona. Se ativar esta definição de política, o Filtro XSS está ativado para os sites desta zona e o Filtro XSS tenta bloquear injeções de script entre sites. Se desativar esta definição de política, o Filtro XSS está desativado para sites desta zona e o Internet Explorer permite injeções de script entre sites.
  
  **Predefinido**: Enabled  
  
- **Zona restrita do Internet Explorer binária e comportamentos de script**  
  Esta definição de política permite-lhe gerir comportamentos de binários e de script dinâmicos: os componentes que encapsulam a funcionalidade específica para elementos HTML para o qual foram anexados. Se ativar esta definição de política, comportamentos de binários e de script estão disponíveis. Se selecionar administrador aprovado na caixa de lista pendente, apenas os comportamentos listados nos comportamentos de aprovação de administrador em diretiva de restrição de segurança de comportamentos binários estão disponíveis. Se desativar esta definição de política, comportamentos de binários e de script não estão disponíveis, a menos que os aplicativos implementaram um Gestor de segurança personalizada. Se não configurar esta definição de política, comportamentos de binários e de script não estão disponíveis, a menos que os aplicativos implementaram um Gestor de segurança personalizada.
  
  **Predefinido**: Desativar  
  
- **Verificação de definições de segurança do Internet Explorer**  
  Esta definição de política desativa a funcionalidade de verificação de definições de segurança, que verifica as definições de segurança do Internet Explorer para determinar quando as definições do Internet Explorer de colocar em risco. Se ativar esta definição de política, a funcionalidade está desativada. Se desabilitar ou não configura esta definição de política, a funcionalidade está ativada.
  
  **Predefinido**: Enabled  
  
- **Aviso de segurança do Internet Explorer internet zona para ficheiros potencialmente não seguros**  
  Esta definição de política controla se a mensagem de "Abrir ficheiro – Aviso de segurança" é apresentada quando o utilizador tenta abrir arquivos executáveis ou de outros ficheiros potencialmente não seguros (a partir de uma partilha de ficheiros à intranet com o Explorador de ficheiros, por exemplo). Se ativar esta definição de política e defina a caixa de lista pendente para ativar, abrir estes ficheiros sem um aviso de segurança. Se definir a caixa de lista pendente à linha de comandos, é apresentado um aviso de segurança antes de abrir os ficheiros. Se desativar esta definição de política, estes ficheiros não abrem. Se não configurar esta definição de política, o utilizador pode configurar como o computador lida com esses arquivos. Por predefinição, estes ficheiros estão bloqueados na zona restrita, ativada em zonas da Intranet e o computador Local e definidos para solicitar nas zonas Internet e confiáveis da.
  
  **Predefinido**: Mensagem  
  
- **Permissões do java de zona de intranet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para segurança média.
  
  **Predefinido**: Segurança alta 
  
- **Controles do Internet Explorer bloquear desatualizado Active X**  </br>
  Esta definição de política determina se os blocos do Internet Explorer específicos desatualizados controles ActiveX. Os controles ActiveX desatualizados nunca são bloqueados na zona de Intranet. Se ativar esta definição de política, Internet Explorer para bloquear os controles ActiveX desatualizados. Se desabilitar ou não configura esta definição de política, o Internet Explorer continua a bloquear os controles ActiveX desatualizados específicos. Para obter mais informações, consulte "Desatualizado os controles ActiveX" na Biblioteca TechNet do Internet Explorer.
  
  **Predefinido**: Enabled  
  
- **Bloqueador de pop-up de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir se indesejados janelas de pop-up aparecem. Janelas de pop-up que foram abertas quando o utilizador final clica num link não são bloqueadas. Se ativar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer. Se desativar esta definição de política, janelas pop-up não são impedidas de aparecer. Se não configurar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer.
  
  **Predefinido**: Ativar  
  
- **Restrição de segurança de protocolo do Internet Explorer processos MK**  
  A definição de política de restrição de segurança do protocolo MK reduz a área de superfície de ataque ao impedir que o protocolo MK. Recursos alojados no protocolo MK irão falhar. Se ativar esta definição de política, o protocolo MK é impedido de Explorador de ficheiros e o Internet Explorer e recursos alojados no protocolo MK irão falhar. Se desativar esta definição de política, as aplicações podem utilizar o API ao protocolo MK. Recursos alojados no protocolo MK irão funcionar para os processos de Explorador de ficheiros e o Internet Explorer. Se não configurar esta definição de política, o protocolo MK é impedido de Explorador de ficheiros e o Internet Explorer e recursos alojados no protocolo MK irão falhar.
  
  **Predefinido**: Enabled  
  
- **Permissões de java de zona fidedignos do Internet Explorer**  </br>
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para baixa segurança.
  
  **Predefinido**: Segurança alta  
  
- **Internet Explorer restrito a zona de scripts de miniaplicativos java**  
  Esta definição de política permite-lhe gerir se miniaplicativos são expostos a scripts dentro da zona. Se ativar esta definição de política, os scripts podem aceder miniaplicativos automaticamente sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que scripts aceder aos miniaplicativos. Se desativar esta definição de política, os scripts são impedidos de aceder miniaplicativos. Se não configurar esta definição de política, os scripts são impedidos de aceder miniaplicativos.
  
  **Predefinido**: Desativar  
  
- **Bloqueado de permissões de java de zona restritas do Internet Explorer**  </br>
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.
  
  **Predefinido**: Desativar o java 
  
- **Permitir que a zona de internet de Internet Explorer apenas aprovados domínios para usar controles ActiveX**  </br>
  Esta definição de política controla se é pedido ao utilizador para permitir que os controles ActiveX ser executada em Web sites que não seja o site no qual instalado o controle ActiveX. Se ativar esta definição de política, é pedido ao utilizador antes de controles ActiveX podem ser executados de Web sites nesta zona. O utilizador pode optar por permitir que o controle ser executada a partir do site atual ou de todos os sites. Se desativar esta definição de política, o utilizador não vê a linha de comandos da ActiveX por site e controles ActiveX podem ser executados de todos os sites desta zona.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer incluem todos os caminhos de rede**  
  Internet Explorer incluem todos os caminhos de rede
  
  **Predefinido**: Desativado 
  
- **Modo protegido de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe ativar o modo protegido. Modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo as localizações que o Internet Explorer pode gravar no Registro e o sistema de ficheiros. Se ativar esta definição de política, o modo protegido é ativado. O utilizador não é possível desativar o modo protegido. Se desativar esta definição de política, o modo protegido é desativado. O utilizador não é possível ativar o modo protegido. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o modo protegido.
  
  **Predefinido**: Ativar 
  
- **Inicializar a zona de internet do Internet Explorer e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script.
  
  **Predefinido**: Desativar 
  
- **Bloqueado SmartScreen zona restritos do Internet Explorer**  </br>
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.
  
  **Predefinido**: Enabled  
  
- **Deteção de falhas do Internet Explorer**  
  Esta definição de política permite-lhe gerir a funcionalidade de deteção de falhas de gestão do suplemento. Se ativar esta definição de política, uma falha no Internet Explorer exibirão comportamento encontrado no Windows XP Professional Service Pack 1 e em versões anteriores, ou seja, para invocar o relatório de erros do Windows. Todas as definições de política para o relatório de erros do Windows continuam a aplicar. Se desabilitar ou não configura esta definição de política, a funcionalidade de deteção de falhas para a gestão de suplemento é funcional.
  
  **Predefinido**: Desativado  
  
- **Permissões do java de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para alta segurança.
  
  **Predefinido**: Desativar o java  
  
- **Scripting ativo do Internet Explorer restrito zona**  
  Esta definição de política permite-lhe gerir se o código de script nas páginas na zona é executado. Se ativar esta definição de política, o código de script nas páginas na zona pode ser executado automaticamente. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o código de script nas páginas na zona para executar. Se desativar esta definição de política, o código de script em páginas na zona é impedido de execução. Se não configurar esta definição de política, o código de script nas páginas na zona é impedido de execução.
  
  **Predefinido**: Desativar  
  
- **Opções de início de sessão da zona de internet de Internet Explorer**  
  Esta definição de política permite-lhe gerir as definições para as opções de início de sessão. Se ativar esta definição de política, pode escolher entre o início de sessão seguintes opções. Logon anônimo desative a autenticação HTTP e a utilização de convidado conta apenas para o protocolo Common Internet File System (CIFS). Solicitar nome de utilizador e palavra-passe para os utilizadores da consulta para IDs de utilizador e palavras-passe. Depois de um utilizador é consultado, estes valores podem ser utilizados em silenciosamente durante o restante período da sessão. Registo automático em apenas na zona de Intranet para os utilizadores da consulta para IDs de utilizador e palavras-passe noutras zonas. Depois de um utilizador é consultado, estes valores podem ser utilizados em automaticamente para o resto da sessão. Automática inicie sessão com o nome de utilizador atual e a palavra-passe para tentar log sobre como utilizar a resposta de desafio do Windows NT (também conhecido como autenticação de NTLM). Se o servidor suportar a resposta de desafio de Windows NT, o início de sessão utiliza nome de utilizador de rede do utilizador e palavra-passe para iniciar sessão. Se se o servidor não suporta a resposta de desafio do Windows NT, o utilizador é consultado para fornecer o nome de utilizador e palavra-passe. Se desativar esta definição de política, início de sessão está definida como registo automático ativado, apenas na zona de Intranet. Se não configurar esta definição de política, o início de sessão está definida como o início de sessão automático numa zona de Intranet apenas em.
  
  **Predefinido**: Mensagem  
  
- **Zona restrita do Internet Explorer permitir vbscript executar**  </br>  
  Esta definição de política permite-lhe gerir se o VBScript possa ser executado nas páginas da zona especificada no Internet Explorer. Se selecionou ativar na caixa de lista pendente, o VBScript pode ser executados sem intervenção do utilizador. Se tiver selecionado a linha de comandos na caixa de lista pendente, é pedido aos utilizadores escolher se pretende permitir que o VBScript seja executado. Se tiver selecionado o desativar a na caixa de lista pendente, o VBScript é impedido de execução. Se não configurar ou desativar esta definição de política, o VBScript é impedido de execução.
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer arraste conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão no windows diferentes. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e de destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição.
  
  **Predefinido**: Desativado 
  
- **Inicializar a zona de intranet do Internet Explorer e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script.
  
  **Predefinido**: Desativar 
  
- **Inclusões de download do Internet Explorer**  
  Esta definição de política impede que o utilizador ter de inclusões (anexos de ficheiros) transferido a partir de um feed para o computador do usuário. Se ativar esta definição de política, o utilizador não é possível definir o motor de sincronização do Feed para transferir um bastidor através da página de propriedades de Feed. Um desenvolvedor não é possível alterar a definição de transferência através das APIs do Feed. Se desabilitar ou não configura esta definição de política, o utilizador pode definir o motor de sincronização do Feed para transferir um bastidor através da página de propriedades de Feed. Um desenvolvedor pode alterar a definição de transferência através das APIs do Feed.
  
  **Predefinido**: Desativado  
  
- **Controles sem assinatura do Active X de transferência de zona restrita do Internet Explorer**  </br>
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando proveniente de uma zona não fidedigna. Se ativar esta definição de política, os utilizadores podem executar controles sem assinatura sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o controle não assinado executar. Se desativar esta definição de política, os utilizadores não é possível executar controles sem assinatura. Se não configurar esta definição de política, os utilizadores não é possível executar controles sem assinatura.
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer arrastar o conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando proveniente de uma zona não fidedigna. Se ativar esta definição de política, os utilizadores podem executar controles sem assinatura sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o controle não assinado executar. Se desativar esta definição de política, os utilizadores não é possível executar controles sem assinatura. Se não configurar esta definição de política, os utilizadores não é possível executar controles sem assinatura.
  
  **Predefinido**: Desativado  
  
- **Processos do Internet Explorer restringem a instalação do Active X**  </br>
  Esta definição de política permite que os aplicativos hospedando o controle de navegador da Web bloquear a pedir a confirmação automática de instalação do controle ActiveX. Se ativar esta definição de política, o controle do navegador da Web irá bloquear a pedir a confirmação automática da instalação de controle do ActiveX para todos os processos. Se desabilitar ou não configura esta definição de política, o controle de navegador da Web não bloqueará a pedir a confirmação automática da instalação de controle do ActiveX para todos os processos.
  
  **Predefinido**: Enabled  
  
- **Scriptlets de zona de internet do Internet Explorer** esta definição de política permite-lhe gerir se o utilizador pode executar scriptlets. Se ativar esta definição de política, o utilizador pode executar scriptlets. Se desativar esta definição de política, o utilizador não é possível executar scriptlets. Se não configurar esta definição de política, o utilizador pode ativar ou desativar scriptlets.
  
  **Predefinido**: Desativar  
  
- **Zona restrita do Internet Explorer arrastar e soltar ou copiar e colar ficheiros**  
  Esta definição de política permite-lhe gerir se os utilizadores podem arrastar arquivos ou copiar e colar ficheiros de uma origem dentro da zona. Se ativar esta definição de política, os utilizadores podem arrastar arquivos ou copiar e colar ficheiros a partir desta zona automaticamente. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende arrastar ou copiar ficheiros a partir desta zona. Se desativar esta definição de política, os utilizadores são impedidos de arrastar arquivos ou copiar e colar ficheiros a partir desta zona. Se não configurar esta definição de política, os utilizadores são consultados para escolher se pretende arrastar ou copiar ficheiros a partir desta zona.
  
  **Predefinido**: Desativar  
  
- **Software do Internet Explorer quando a assinatura é inválida** </br>
  Esta definição de política permite-lhe gerir se software, como controles ActiveX e transferências de ficheiros, pode ser instalado ou executado pelo utilizador, mesmo que a assinatura é inválida. Uma assinatura inválida pode indicar que alguém tenha adulterado o ficheiro. Se ativar esta definição de política, é pedido aos utilizadores para instalar ou executar ficheiros com uma assinatura inválida. Se desativar esta definição de política, os utilizadores não é possível executar ou instalar ficheiros com uma assinatura inválida. Se não configurar esta política, os utilizadores podem optar por executar ou instalar ficheiros com uma assinatura inválida.
  
  **Predefinido**: Desativado  
  
- **Copiar de zona do Internet Explorer restrito e colar por meio de script** </br> Esta definição de política permite-lhe gerir se scripts podem realizar uma operação de área de transferência (por exemplo, as ações cortar, copiar e colar) numa determinada região. Se ativar esta definição de política, um script pode realizar uma operação de área de transferência. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados sobre a execução de operações de área de transferência. Se desativar esta definição de política, um script não é possível efetuar uma operação de área de transferência. Se não configurar esta definição de política, um script não é possível efetuar uma operação de área de transferência.
  
  **Predefinido**: Desativar  
  
- **Zona restrita do Internet Explorer arraste conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão no windows diferentes. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e de destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição.  <br><br>
  **Predefinido**: Desativado  
  
- **Usuários do Internet Explorer, adicionar sites**  
  Impede que os utilizadores de adicionar ou remover sites de zonas de segurança. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, as definições de gestão do site para zonas de segurança estão desativadas. (Para ver a gestão de site as definições para as zonas de segurança, na caixa de diálogo Opções da Internet, clique no separador de segurança em, em seguida, clique no botão de Sites.) Se desativar esta política ou não configurá-lo, os usuários podem adicionar sites da Web ou remover sites de zonas de Sites confiáveis e Sites restritos e altere as definições para a zona de Local Intranet. Esta política impede os utilizadores alterem as definições de gestão do site para zonas de segurança estabelecidas pelo administrador. Nota: A política "Desativar a página de segurança" (localizada no painel de controlo do administrativos\Componentes Windows\Internet Explorer\Painel de \User Configuration\Administrative), que remove a guia de segurança a partir da interface, tem precedência sobre esta política. Se estiver ativada, esta política é ignorada. Além disso, consulte o "zonas de segurança: Utilizar apenas as definições de máquina"política.
  
  **Predefinido**: Desativado  
  
- **Script de zona de internet do Internet Explorer iniciadas pelo windows**  
  Esta definição de política permite-lhe gerir restrições para janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Se ativar esta definição de política, não se aplicam a segurança de restrições do Windows nesta zona. A zona de segurança é executado sem a camada de segurança fornecida por esta funcionalidade adicional. Se desativar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows. Se não configurar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows.
  
  **Predefinido**: Desativado  
  
- **As zonas de segurança do Internet Explorer utilizam apenas as definições de máquina**  
  Aplica-se de informações da zona de segurança para todos os utilizadores do mesmo computador. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, as alterações que faz com que o utilizador a uma zona de segurança serão aplicada a todos os utilizadores do computador. Se desativar esta política ou não configurá-lo, os usuários do mesmo computador podem estabelecer suas próprias definições de zona de segurança. Utilize esta política para garantir que as definições de zona de segurança se aplicam de forma uniforme no mesmo computador e não variam de usuário a usuário. Além disso, consulte o "zonas de segurança: não permitir que os usuários alterem as políticas de" política.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer é bloqueado por permissões de java de zona de computador local**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados
  
  **Predefinido**: Desativar o java 
  
- **Zona restrita do Internet Explorer não execute antimalware controles Active X**  </br>
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.
  
  **Predefinido**: Desativado  
  
- **Zona restrita do Internet Explorer executar componentes da habilitação do .NET Framework assinado com authenticode**  
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que estão assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados assinados. Se desativar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados. Se não configurar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados.
  
  **Predefinido**: Desativar  
  
- **Acesso de zona de restrito de Internet Explorer para origens de dados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer pode acessar dados de outra zona de segurança com o Microsoft XML Parser (MSXML) ou ActiveX Data Objects (ADO). Se ativar esta definição de política, os utilizadores podem carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que uma página carregar na zona que utiliza o MSXML ou o ADO para acessar dados de outro site na zona. Se desativar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se não configurar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona.
  
  **Predefinido**: Desativar 
  
- **Zona de internet do Internet Explorer não são executados antimalware controles ActiveX**  </br>
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.
  
  **Predefinido**: Desativado  
  
- **Copiar de zona de internet do Internet Explorer e colar por meio de script** </br> Esta definição de política permite-lhe gerir se scripts podem realizar uma operação de área de transferência (por exemplo, as ações cortar, copiar e colar) numa determinada região. Se ativar esta definição de política, um script pode realizar uma operação de área de transferência. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados sobre a execução de operações de área de transferência. Se desativar esta definição de política, um script não é possível efetuar uma operação de área de transferência. Se não configurar esta definição de política, um script pode realizar uma operação de área de transferência.
  
  **Predefinido**: Desativar  
  
- **Internet Explorer utilizar o serviço do instalador do Active X**  </br>
  Esta definição de política permite-lhe especificar como os controles ActiveX são instalados. Se ativar esta definição de política, os controles ActiveX são instalados apenas se o ActiveX Installer Service está presente e não foi configurado para permitir a instalação de controles ActiveX. Se desabilitar ou não configura esta definição de política, os controles ActiveX, incluindo controlos por utilizador, são instalados através do processo de instalação padrão.
  
  **Predefinido**: Enabled  
  
- **Proteção contra elevação de zona de processos do Internet Explorer**  
  Internet Explorer coloca restrições em cada página da Web é aberto. As restrições são dependentes tanto a localização da página da Web (Internet, Intranet, zona de computador Local e assim por diante). Por exemplo, páginas da Web no computador local têm as restrições de segurança menor e encontram-se na zona de computador Local, fazer a segurança do computador Local zona principal alvo para que usuários mal-intencionados. Se ativar esta definição de política, qualquer zona pode ser protegida contra elevação de zona para todos os processos. Se desabilitar ou não configura esta definição de política, processos que não sejam o Internet Explorer ou aos listados na lista de processos recebem sem essa proteção.
  
  **Predefinido**: Enabled  
  
- **Os controles ActiveX não assinados de transferência de zona de internet do Internet Explorer**  </br>
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando proveniente de uma zona não fidedigna. Se ativar esta definição de política, os utilizadores podem executar controles sem assinatura sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o controle não assinado executar. Se desativar esta definição de política, os utilizadores não é possível executar controles sem assinatura. Se não configurar esta definição de política, os utilizadores não é possível executar controles sem assinatura.
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer navegue windows e os quadros em diferentes domínios**  </br>
  Esta definição de política permite-lhe gerir a abertura do windows e os quadros e acesso de aplicações em diferentes domínios. Se ativar esta definição de política, os utilizadores podem abrir windows e quadros de outros domínios e aplicações de acesso de outros domínios. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o windows e os quadros para aceder às aplicações de outros domínios. Se desativar esta definição de política, os utilizadores não é possível abrir o windows e os quadros para aceder às aplicações de diferentes domínios. Se não configurar esta definição de política, os utilizadores podem abrir windows e quadros de outros domínios e aplicações de acesso de outros domínios.
  
  **Predefinido**: Desativar  
  
- **Atualizações de zona de internet do Internet Explorer a barra de status por meio de script**  
  Esta definição de política permite-lhe gerir se um script pode atualizar a barra de status na zona. Se ativar esta definição de política, os scripts podem atualizar a barra de status. Se desabilitar ou não configura esta definição de política, o script não é permitido para atualizar a barra de status.
  
  **Predefinido**: Desativado  
  
- **Zona restrita do Internet Explorer incluir o caminho local, ao carregar ficheiros para o servidor**  </br> Esta definição de política controla se as informações de caminho local são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se as informações de caminho local são enviadas, algumas informações podem inadvertidamente reveladas para o servidor. Por exemplo, os arquivos enviados a partir do ambiente de trabalho do usuário podem conter o nome de utilizador como parte do caminho. Se ativar esta definição de política, informações de caminho são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se desativar esta definição de política, informações de caminho são removidas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se não configurar esta definição de política, o usuário pode escolher se as informações de caminho são enviadas quando estiver a carregar um ficheiro através de um formulário HTML. Por predefinição, são enviadas informações de caminho.
  
  **Predefinido**: Desativado  
  
- **Processos do Internet Explorer restringem a transferência de ficheiros**  </br> Esta definição de política permite que as aplicações que alojam o controle Web Browser bloquear a pedir a confirmação automática de downloads de arquivos que não são iniciada pelo utilizador. Se ativar esta definição de política, o controle do navegador da Web irá bloquear a pedir a confirmação automática de downloads de arquivos que não são iniciado para todos os processos de utilizador. Se desativar esta definição de política, o controle de navegador da Web não bloqueará a pedir a confirmação automática de downloads de arquivos que não são iniciado para todos os processos de utilizador.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer, permitir que a zona restritas apenas aprovados domínios usar controles de Active X**  </br>
  Esta definição de política controla se é pedido ao utilizador para permitir que os controles ActiveX ser executada em Web sites que não seja o site no qual instalado o controle ActiveX. Se ativar esta definição de política, é pedido ao utilizador antes de controles ActiveX podem ser executados de Web sites nesta zona. O utilizador pode optar por permitir que o controle ser executada a partir do site atual ou de todos os sites. Se desativar esta definição de política, o utilizador não vê a linha de comandos da ActiveX por site e controles ActiveX podem ser executados de todos os sites desta zona.
  
  **Predefinido**: Enabled  
  
- **A inicializar de zona restrita do Internet Explorer e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script.
  
  **Predefinido**: Desativar  
  
- **Usuários do Internet Explorer, alteração de políticas**  
    Impede os utilizadores alterem as definições de zona de segurança. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, o botão de nível personalizado e o controlo de deslize do nível de segurança no separador de segurança na caixa de diálogo Opções da Internet estão desativadas. Se desativar esta política ou não configurá-lo, os utilizadores podem alterar as definições para as zonas de segurança. Esta política impede os utilizadores alterem as definições de zona de segurança estabelecidas pelo administrador. Nota: A política "Desativar a página de segurança" (localizada no painel de controlo do administrativos\Componentes Windows\Internet Explorer\Painel de \User Configuration\Administrative), que remove a guia de segurança do Internet Explorer, no painel de controlo, terão precedência sobre Esta política. Se estiver ativada, esta política é ignorada. Além disso, consulte o "zonas de segurança: Utilizar apenas as definições de máquina"política.
    
  **Predefinido**: Desativado  
  
- **Modo protegido do Internet Explorer zona restritas**  
  Esta definição de política permite-lhe ativar o modo protegido. Modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo as localizações que o Internet Explorer pode gravar no Registro e o sistema de ficheiros. Se ativar esta definição de política, o modo protegido é ativado. O utilizador não é possível desativar o modo protegido. Se desativar esta definição de política, o modo protegido é desativado. O utilizador não é possível ativar o modo protegido. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o modo protegido.
  
  **Predefinido**: Ativar  
  
- **Persistência de dados de utilizador de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir a preservação de informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Quando um usuário retorne a uma página persistente, o estado da página pode ser restaurado se esta definição de política está configurada corretamente. Se ativar esta definição de política, os usuários possam preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se desativar esta definição de política, os usuários não é possível preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se não configurar esta definição de política, os usuários possam preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco.
  
  **Predefinido**: Desativado  
  
- **Scripts de zona de internet do Internet Explorer de controles de navegador da web**  
 
  Esta definição de política determina se uma página pode controlar o embedded WebBrowser controles por meio de script. Se ativar esta definição de política, é permitido o acesso de script para o controle WebBrowser. Se desativar esta definição de política, não é permitido o acesso de script para o controle WebBrowser. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o acesso de script para o controle WebBrowser. Por predefinição, o acesso de script para o controle WebBrowser é permitido apenas no computador Local e zonas da Intranet.
  
  **Predefinido**: Desativado  
  
- **Persistência de dados de utilizador de zona restritos do Internet Explorer**  
    Esta definição de política permite-lhe gerir a preservação de informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Quando um usuário retorne a uma página persistente, o estado da página pode ser restaurado se esta definição de política está configurada corretamente. Se ativar esta definição de política, os usuários possam preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se desativar esta definição de política, os usuários não é possível preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se não configurar esta definição de política, os usuários não é possível preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco.  
  
  **Predefinido**: Desativado  
  
- **Bloqueado de permissões de java de zona de intranet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.
  
  **Predefinido**: Desativar o java  
  
- **Modo protegido do Internet Explorer avançada**  
  Modo protegido avançado proporciona proteção adicional contra sites mal-intencionados utilizando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam, pelo menos, Windows 8, o modo protegido avançado também limita os locais do Internet Explorer pode ler a partir do Registro e o sistema de ficheiros. Se ativar esta definição de política, o modo protegido avançado está ativado. Qualquer zona que tenha o modo protegido ativado irá utilizar o modo protegido avançado. Os utilizadores não será possível desativar o modo protegido avançado. Se desativar esta definição de política, o modo protegido avançado está desativado. Qualquer zona que tenha o modo protegido ativado irá utilizar a versão do modo protegido, introduzido no Internet Explorer 7 para Windows Vista. Se não configurar esta política, os utilizadores podem ativar ou desativar o modo protegido avançado no separador Avançadas da caixa de diálogo Opções da Internet.
  
  **Predefinido**: Enabled  
  
- **Internet Explorer ignore os avisos do SmartScreen**  
  Esta definição de política determina se o utilizador pode ignorar avisos do Filtro SmartScreen. O Filtro SmartScreen avisa o utilizador sobre ficheiros executáveis que usuários do Internet Explorer geralmente não transferirem a partir da Internet. Se ativar esta definição de política, os avisos do Filtro SmartScreen impedir o utilizador. Se desabilitar ou não configura esta definição de política, o utilizador pode ignorar avisos do Filtro SmartScreen.
  
  **Predefinido**: Desativado  
  
- **Atualização de meta de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir se o navegador de um usuário pode ser redirecionado para outra página da Web, se o autor da página da Web usa a definição de metadados de atualização (etiqueta) para redirecionar os navegadores para outra página da Web. Se ativar esta definição de política, o navegador de um usuário que carrega uma página que contém uma definição de metadados de atualização de Active Directory pode ser redirecionado para outra página da Web. Se desativar esta definição de política, navegador de um usuário que carrega uma página que contém uma definição de metadados de atualização de Active Directory não pode ser redirecionado para outra página da Web. Se não configurar esta definição de política, navegador de um usuário que carrega uma página que contém uma definição de metadados de atualização de Active Directory não pode ser redirecionado para outra página da Web.
  
  **Predefinido**: Desativado  
  
## <a name="local-policies-security-options"></a>Opções de segurança de políticas locais
Para obter mais informações, consulte [CSP de política - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) na documentação do Windows. 

- **Restringir o acesso anónimo a pipes nomeados e partilhas**  
  Quando ativada, esta definição de segurança restringe o acesso anónimo a partilhas e pipes para as definições para: (1) pipes nomeados que podem ser acedidos anonimamente (2) partilhas que podem ser acedidas anonimamente
  
  **Predefinido**: Sim  
  
- **Servidores baseados em segurança de sessão mínima para NTLM SSP**  
  Esta definição de segurança permite que um servidor exigir a negociação de encriptação de 128 bits e/ou de segurança de sessão de NTLMv2. Estes valores dependem do valor de definição de segurança de nível de autenticação do LAN Manager. As opções são: Exigir a segurança de sessão de NTLMv2: A ligação irá falhar se não estiver negociada a integridade de mensagens. Exigir encriptação de 128 bits. A ligação irá falhar se a encriptação forte (128 bits) não é negociada.
  
  **Predefinido**: Exigir encriptação de 128 bits e de NTLM V2  
  
- **Minutos de inatividade do ecrã de bloqueio quando ativa a proteção de tela**  
  O Windows repara na inatividade de um início de sessão e, se a quantidade de tempo inativo exceder o limite de inatividade, então, a proteção de ecrã será executado, bloqueando a sessão.
  
  **Predefinido**: 15
  
- **Necessitam de cliente para assinar comunicações digitalmente sempre** esta definição de segurança determina se todo o tráfego de canal de segurança iniciado pelo membro de domínio tem de ser assinado ou criptografado. Quando um computador é associado um domínio, é criada uma conta de computador. Depois disso, quando o sistema é iniciado, ele usa a palavra-passe da conta de computador para criar um canal seguro com um controlador de domínio para o seu domínio. Este canal seguro é utilizado para executar operações como o NTLM passar por autenticação, pesquisa de nome/SID de LSA e muito mais. Esta definição determina se a todo o tráfego de canal de segurança iniciado pelo membro de domínio cumpre os requisitos mínimos de segurança. Especificamente determina se todo o tráfego de canal de segurança iniciado pelo membro de domínio tem de ser assinado ou criptografado. Se esta política estiver ativada, em seguida, o canal seguro não ser estabelecido, a menos que a assinatura ou encriptação de todo o tráfego de canal seguro é negociada. Se esta política estiver desativada, em seguida, encriptação e assinatura de todo o tráfego de canal seguro é negociado com o controlador de domínio caso em que o nível de assinatura e encriptação depende da versão do controlador de domínio e as definições das duas seguintes políticas: Membro de domínio: Encriptar digitalmente dados de canal seguro (quando possível) membro de domínio: Digitalmente o início de sessão proteger os dados de canal (quando possível)
  
  **Predefinido**: Sim
  
- **Nível de autenticação**  
  Esta definição de segurança determina qual protocolo de autenticação de desafio/resposta é utilizado para inícios de sessão de rede. Esta opção afeta o nível de protocolo de autenticação utilizado por clientes, o nível de segurança de sessão negociada e o nível de autenticação aceite pelos servidores da seguinte forma:  
  - *Enviar respostas de LM e NTLM*: Os clientes utilizam a autenticação LM e NTLM e nunca usar segurança de sessão de NTLMv2; controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Enviar LM e NTLM - NTLMv2 se negociado*: Os clientes utilizam a autenticação LM e NTLM e usar segurança de sessão de NTLMv2, se o servidor suportá-lo. controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Enviar resposta NTLM apenas*: Os clientes a utilizar apenas autenticação NTLM e usar segurança de sessão de NTLMv2, se o servidor suportá-lo. controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Enviar resposta de NTLMv2 apenas*: Os clientes utilizam apenas a autenticação NTLMv2 e usar segurança de sessão de NTLMv2, se o servidor suportá-lo. controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Envie resposta de NTLMv2 apenas. Recusar LM*: Os clientes utilizam apenas a autenticação NTLMv2 e usar segurança de sessão de NTLMv2, se o servidor suportá-lo. controladores de domínio recusam LM (aceitar apenas a autenticação NTLM e NTLMv2). 
  - *Envie resposta de NTLMv2 apenas. Recusar LM e NTLM*: Os clientes utilizam apenas a autenticação NTLMv2 e usar segurança de sessão de NTLMv2, se o servidor suportá-lo. controladores de domínio recusam LM e NTLM (aceitar apenas a autenticação NTLMv2). 
    
  **Predefinido**: Envie resposta de NTLMv2 apenas. Recusar LM e NTLM
  
- **Impedir que os clientes a enviar de palavras-passe não encriptadas para servidores SMB de terceiros**  
  Se esta definição de segurança estiver ativada, o redirecionador de bloco de mensagem de servidor (SMB) pode enviar palavras-passe de texto sem formatação para servidores SMB não Microsoft que não suportam a encriptação de palavra-passe durante a autenticação. Enviar palavras-passe não encriptadas é um risco de segurança.
  
  **Predefinido**: Sim
  
- **Desativar servidor assinar digitalmente comunicações sempre**  
  Esta definição de segurança determina se o cliente SMB tenta negociar a assinatura de pacotes SMB. O protocolo do server message block (SMB) fornece a base para ficheiros do Microsoft e a partilha de impressão e muitas outras operações de rede, como administração remota do Windows. Para impedir ataques man-in-the-middle que modificar pacotes SMB em trânsito, o protocolo SMB suporta a assinatura digital de pacotes SMB. Esta definição de política determina se o componente de cliente SMB tenta negociar a assinatura para estabelecer a ligação a um servidor do SMB de pacotes SMB. Se esta definição estiver ativada, o cliente de rede Microsoft pedirá o servidor para efetuar após a configuração de sessão de assinatura de pacotes SMB. Se a assinatura de pacotes tiver sido ativada no servidor, a assinatura de pacotes será negociada. Se esta política estiver desativada, o cliente SMB nunca negociar a assinatura de pacotes SMB.
  
  **Predefinido**: Sim
  
- **Comportamento de solicitação de elevação do administrador**  
  Esta definição de política controla o comportamento do prompt de elevação para administradores. As opções são: 
    - *Elevar sem pedir*: Permite que as contas com privilégios executar uma operação que exige elevação sem a necessidade de consentimento ou credenciais. Nota: Utilize esta opção apenas nos ambientes mais restritos. 
    - *Pedido de credenciais no ambiente de trabalho seguro*: Quando uma operação requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para introduzir um nome de utilizador com privilégios e uma palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com privilégio mais alto disponível do utilizador. 
    - *Pedir consentimento no ambiente de trabalho seguro*: Quando uma operação requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para selecionar permitir ou negar. Se o usuário seleciona o permitir, a operação continuará com privilégio mais alto disponível do utilizador. 
    - *Pedido de credenciais*: Quando uma operação requer elevação de privilégios, é pedido ao utilizador para introduzir um nome de utilizador administrativo e a palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
    - *Pedir consentimento*: Quando uma operação requer elevação de privilégios, é pedido ao utilizador para selecionar permitir ou negar. Se o usuário seleciona o permitir, a operação continuará com privilégio mais alto disponível do utilizador.  
    - *Pedir consentimento para binários não Windows*: Quando uma operação para um aplicativo não-Microsoft requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para selecionar permitir ou negar. Se o usuário seleciona o permitir, a operação continuará com privilégio mais alto disponível do utilizador.   
  
  **Predefinido**: Pedir consentimento no ambiente de trabalho seguro
  
- **Clientes baseados na segurança de sessão mínima para NTLM SSP**  
  Esta definição de segurança permite que um cliente requerer a negociação de encriptação de 128 bits e/ou de segurança de sessão de NTLMv2. Estes valores dependem do valor de definição de segurança de nível de autenticação do LAN Manager. As opções são:
  - Exigir a segurança de sessão de NTLMv2: A ligação irá falhar se o protocolo de NTLMv2 não é negociado. 
  - *Exigir encriptação de 128 bits*: A ligação irá falhar se a encriptação forte (128 bits) não é negociada.
  - *Exigir encriptação de 128 bits e de NTLMv2*. 

  **Predefinido**: Exigir encriptação de 128 do NTLM V2
  
- **Comportamento de remoção do smart card**  
    Esta definição de segurança determina o que acontece quando o smart card para um utilizador com sessão iniciada é removido de leitor de smart card. As opções são:
     - *Nenhuma ação*. 
     - *Bloquear estação de trabalho* -a estação de trabalho é bloqueada quando o smart card é removido, permitindo que os usuários deixar a área, tome o smart card com eles e ainda manter uma sessão protegida.
     - *Forçar fim da sessão* -o utilizador é automaticamente terminada quando o smart card é removido.
     - *Desligar a sessão de ambiente de trabalho remoto* -remoção do smart card termina a sessão sem o utilizador terminar sessão. Isso permite que o usuário inserir o smart card e retomar a sessão mais tarde, ou em outro cartão inteligente leitor computador equipado com, sem ter de iniciar sessão novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.  <br><br>
    
  **Predefinido**: Bloquear estação de trabalho
  
- **Bloquear a enumeração anónima de contas e partilhas SAM**  
  Esta definição de segurança determina se deve permitir a enumeração anónima de SAM, contas e partilhas. Windows permite aos utilizadores anónimos realizar determinadas atividades, tais como enumerar os nomes de contas de domínio e partilhas de rede. Isso é conveniente, por exemplo, quando um administrador pretende conceder acesso a utilizadores num domínio fidedigno que não mantêm uma relação de confiança recíproco. Se não pretender permitir a enumeração anónima de SAM, contas e partilhas, em seguida, definir esta política como *Sim*.
  
  **Predefinido**: Sim
  
- **Início de sessão remoto do bloco com palavra-passe em branco**  
  Esta definição de segurança determina se as contas locais que não estão protegidos por senha podem ser utilizadas para iniciar sessão a partir de localizações que não seja o console do computador físico. Se estiver ativada, as contas locais que não estão protegidos por senha tem de utilizar o teclado do computador para iniciar sessão. 

  *Aviso*: Computadores que não estão em localizações fisicamente seguras sempre devem impor políticas de palavra-passe segura para todas as contas de utilizador local. Caso contrário, qualquer pessoa com acesso físico ao computador pode faça logon com uma conta de utilizador que não tem uma palavra-passe. Isso é especialmente importante para computadores portáteis. 

  Se aplicar esta política de segurança para a todos os utilizadores de grupo, ninguém pode iniciar sessão através dos serviços de ambiente de trabalho remoto. Esta definição não afeta logons que utilizar contas de domínio. É possível para aplicações que utilizam inícios de sessão interativos remotos para ignorar esta definição.
  
  **Predefinido**: Sim
  
- **Comportamento de solicitação de elevação de usuário padrão**  
  Esta definição de política controla o comportamento do prompt de elevação para usuários padrão. 
  - *Negar automaticamente pedidos de elevação*: Quando uma operação requer elevação de privilégios, um configurável acesso negado é apresentada a mensagem de erro. Uma empresa que está executando áreas de trabalho como usuário padrão pode escolher esta definição para reduzir as chamadas de suporte técnico. 
  - *Pedido de credenciais no ambiente de trabalho seguro*: Quando uma operação requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para introduzir um nome de utilizador diferente e uma palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Pedido de credenciais*: Quando uma operação requer elevação de privilégios, é pedido ao utilizador para introduzir um nome de utilizador administrativo e a palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável.  
  
  **Predefinido**: Negar automaticamente pedidos de elevação
  
- **Exigir o modo de aprovação de administrador para os administradores**  
  Esta definição de política controla o comportamento de todas as definições de política de controlo de conta de usuário (UAC) para o computador. Se alterar esta definição de política, deve reiniciar o computador. As opções são:   
  - *Não configurado*: Modo de aprovação de administrador e todas as definições de política UAC relacionadas estão desativadas. Nota: Se esta definição de política estiver desativada, o Centro de segurança notifica-o de que a segurança geral do sistema operacional foi reduzida. 
  - *Sim*: Modo de aprovação de administrador está ativado. Esta política tem de estar ativada e as definições de política UAC relacionadas tem de ser definidas adequadamente para permitir que a conta de administrador incorporada e todos os outros utilizadores que são membros do grupo Administradores para executar no modo de aprovação de administrador.  
  
  **Predefinido**: Sim
  
- **Impedir a enumeração anónima de contas SAM**  
  Esta definição de segurança determina quais permissões adicionais são concedidas para ligações anónimas para o computador. Windows permite aos utilizadores anónimos realizar determinadas atividades, tais como enumerar os nomes de contas de domínio e partilhas de rede. Isso é conveniente, por exemplo, quando um administrador pretende conceder acesso a utilizadores num domínio fidedigno que não mantêm uma relação de confiança recíproco. Esta opção de segurança permite que as restrições adicionais ser colocado em ligações anónimas da seguinte forma: 
  - *Sim*: Não permitir a enumeração de SAM contas. Esta opção substitui todos os utilizadores por Authenticated Users as permissões de segurança para os recursos.
  - *Não configurado*: Não existem restrições adicionais. Contar com as permissões predefinidas.  
  
  **Predefinido**: Sim
  
- **Permitir chamadas remotas para o Gestor de contas de segurança**  
  Esta definição de política permite-lhe restringir ligações rpc remoto para SAM. Se não selecionada, é utilizado o descritor de segurança padrão.
  
  **Predefinido**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Utilizar o modo de aprovação de administrador**  
  Esta definição de política controla o comportamento de modo de aprovação de administrador para a conta interna de administrador. As opções são: 
  - *Sim*: A conta interna administrador utiliza o modo de aprovação de administrador. Por predefinição, a qualquer operação que exige elevação de privilégios pedirá ao utilizador para aprovar a operação. 
  - *Não configurado*: A conta interna administrador executa todos os aplicativos com privilégio administrativo completo.  

  **Predefinido**: Sim
  
- **Permitir que as aplicações de acesso de interface do Usuário para localizações seguras**  
  Esta definição de política de controlos se programas de acessibilidade de Interface do usuário (UIAccess ou UIA) podem desativar automaticamente o ambiente de trabalho seguro para pedidos de elevação utilizado por um usuário padrão. 
  - *Sim*: Os programas UIA, incluindo assistência remota do Windows, desativar automaticamente o ambiente de trabalho seguro para pedidos de elevação. Se não desativar o "User Account Control: Mude para o ambiente de trabalho seguro quando pedir elevação"definição de política, as instruções apresentadas na área de trabalho do utilizador interativo em vez de área de trabalho protegida. 
  - *Não configurado*: Área de trabalho protegida pode ser desativado apenas pelo utilizador do ambiente de trabalho interativo ou ao desativar o "User Account Control: Mude para o ambiente de trabalho seguro quando pedir elevação"definição de política.  

  **Predefinido**: Sim

- **Detectar instalações de aplicativos e aviso de elevação**  
  Esta definição de política controla o comportamento de deteção de instalação de aplicações para o computador. As opções são: 
  - *Ativado*: Quando um pacote de instalação do aplicativo é detectado que requer a elevação de privilégio, é pedido ao utilizador para introduzir um nome de utilizador administrativo e a palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Desativado*: Pacotes de instalação de aplicações não são detetados e prompt de elevação. As empresas que executam desktops de usuário padrão e usar delegados tecnologias de instalação, como instalação de Software da diretiva de grupo ou Systems Management Server (SMS), deve desativar esta definição de política. Neste caso, a detecção de instalador é desnecessária.  
  
  **Predefinido**: Sim
  
- **Impedir que armazenar o valor de hash do LAN manager na próxima alteração de palavra-passe**  
  Esta definição de segurança determina se, na próxima alteração de palavra-passe, o valor de hash LAN Manager (LM) para a nova palavra-passe é armazenado. O hash LM é relativamente fraca e propenso a ataques, as compared with o hash de NT do Windows mais criptograficamente forte. Uma vez que o hash LM é armazenado no computador local na base de dados de segurança, as palavras-passe podem ser comprometidas se a base de dados de segurança for atacado.
  
  **Predefinido**: Sim

- **Virtualizar o arquivo e registro falhas de escrita por localizações de utilizador**  
  Esta definição de política de controlos se falhas de escrita de aplicações são redirecionadas para locais de sistema de registro e arquivo definidos. Esta definição de política atenua os aplicativos que são executados como administrador e escrever dados de tempo de execução de aplicações para *% ProgramFiles %*, *% Windir %*, *%Windir%\system32*, ou *HKLM\Software*.
  
  **Predefinido**: Sim

## <a name="ms-security-guide"></a>Guia de segurança do MS  
Para obter mais informações, consulte [CSP de política - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) na documentação do Windows.  

- **Aplicar restrições de UAC para contas locais no início de sessão de rede**  
  **Predefinido**: Enabled
  
- **Configuração de início do controlador de cliente do SMB v1**  
  **Predefinido**: Controlador desativado
  
- **Servidor do SMB v1**  
  **Predefinido**: Desativado
  
- **Autenticação resumida**  
  **Predefinido**: Desativado
  
- **Manipulação de exceção estruturada substituir a proteção**  
  **Predefinido**: Enabled
  
## <a name="mss-legacy"></a>MSS legado  
Para obter mais informações, consulte [CSP de política - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) na documentação do Windows.  

- **Rede IP de origem encaminhamento ao nível de proteção**  
  **Predefinido**: Proteção mais alta  
  
- **Rede ignorar pedidos de versão de nome do NetBIOS, exceto de servidores WINS**  
  **Predefinido**: Enabled
  
- **Nível de proteção de encaminhamento do IPv6 origem de rede**  
  **Predefinido**: Proteção mais alta

- **OSPF gerado de substituição de redirecionamentos ICMP de rede**  
  **Predefinido**: Desativado
  
## <a name="power"></a>Power  
Para obter mais informações, consulte [CSP de política - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) na documentação do Windows.  

- **Exigir palavra-passe na reativação enquanto ligado**  
  Esta definição de política especifica se é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se ativar ou não configurar esta definição de política, é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se desativar esta definição de política, o utilizador não é solicitado uma palavra-passe quando o sistema sai do modo de suspensão.
  
  **Predefinido**: Enabled
  
- **Estados de espera durante a suspensão enquanto com bateria**  
  Esta definição de política gere se o Windows podem utilizar Estados de espera ao colocar o computador num Estado de suspensão. Se ativar ou não configurar esta definição de política, o Windows utiliza os Estados de espera para colocar o computador num Estado de suspensão. Se desativar esta definição de política, os Estados de espera (S1-S3) não são permitidos.
  
  **Predefinido**: Desativado
  
- **Estados de espera durante a suspensão enquanto ligado**  
  Esta definição de política gere se o Windows podem utilizar Estados de espera ao colocar o computador num Estado de suspensão. Se ativar ou não configurar esta definição de política, o Windows utiliza os Estados de espera para colocar o computador num Estado de suspensão. Se desativar esta definição de política, os Estados de espera (S1-S3) não são permitidos.
  
  **Predefinido**: Desativado
  
- **Exigir palavra-passe na reativação enquanto com bateria**  
  Esta definição de política especifica se é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se ativar ou não configurar esta definição de política, é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se desativar esta definição de política, o utilizador não é solicitado uma palavra-passe quando o sistema sai do modo de suspensão.
  
  **Predefinido**: Enabled
  
## <a name="remote-desktop-services"></a>Serviços de Ambiente de Trabalho Remoto  
Para obter mais informações, consulte [CSP de política - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) na documentação do Windows.  

- **Bloquear a gravação de palavra-passe**  
  Controla se as palavras-passe podem ser guardadas neste computador de conexão de área de trabalho remoto. Se ativar esta definição da palavra-passe a guardar a caixa de seleção na conexão de área de trabalho remoto está desativada e os utilizadores não poderão guardar palavras-passe. Quando um utilizador abre um ficheiro RDP através da ligação de ambiente de trabalho remoto e salva suas configurações, são eliminados a qualquer palavra-passe que existia anteriormente no ficheiro RDP. Se desativar esta definição ou deixá-lo não configurado, o utilizador pode guardar palavras-passe através da ligação de ambiente de trabalho remoto.
  
   **Predefinido**: Enabled
  
- **Proteger as comunicações de RPC**  
  Especifica se um servidor de anfitrião de sessões de ambiente de trabalho remoto requer comunicação RPC segura com todos os clientes ou permite a comunicação protegida. Pode utilizar esta definição para reforçar a segurança da comunicação RPC com clientes ao permitir que apenas autenticada e criptografada pedidos. Se o estado estiver definido como ativado, os serviços de ambiente de trabalho remoto aceita os pedidos de clientes RPC que oferecem suporte a solicitações seguras e não permite a comunicação segura com os clientes não fidedignos. Se o estado estiver definido como desativado, os serviços de ambiente de trabalho remoto sempre solicitações de segurança para todo o tráfego RPC. No entanto, a comunicação protegida é permitida para clientes RPC que não responderem ao pedido. Se o estado estiver definido como não configurada, é permitida a comunicação protegida. Nota: A interface RPC é utilizada para administrar e configurar o Remote Desktop Services.
  
  **Predefinido**: Enabled
  
- **Redirecionamento de unidade de bloco**  
  Esta definição de política especifica se impede o mapeamento de unidades de cliente numa sessão de serviços de ambiente de trabalho remoto (redirecionamento de unidade). Por predefinição, um servidor de anfitrião de sessões de RD mapeia unidades de cliente automaticamente após a ligação. Unidades mapeadas aparecem na árvore de pastas de sessão no Explorador de ficheiros ou de computador no formato  *\<letradaunidade >* no  *\<computername >*. Pode utilizar esta definição de política para substituir esse comportamento. Se ativar esta definição de política, redirecionamento de unidade de cliente não é permitido em sessões de serviços de ambiente de trabalho remoto e redirecionamento de cópia de ficheiros de área de transferência não é permitido em computadores que executam o Windows Server 2003, Windows 8 e Windows XP. Se desativar esta definição de política, o redirecionamento de unidade de cliente é sempre permitido. Além disso, redirecionamento de cópia de ficheiros de área de transferência é sempre permitido se o redirecionamento de área de transferência é permitido. Se não configurar esta definição de política, redirecionamento de unidade de cliente e o redirecionamento de cópia de ficheiros de área de transferência não estão especificados no nível de diretiva de grupo.
  
  **Predefinido**: Enabled
  
- **Pedido de palavra-passe após a ligação**  
  Esta definição de política especifica se os serviços de ambiente de trabalho remoto pede sempre o cliente para uma palavra-passe após a ligação. Pode utilizar esta definição para impor um pedido de palavra-passe para os usuários fazendo logon em serviços de ambiente de trabalho remoto, mesmo que eles já fornecidos a palavra-passe no cliente de conexão de área de trabalho remoto. Por predefinição, os serviços de ambiente de trabalho remoto permite que os usuários façam logon automaticamente ao introduzir uma palavra-passe no cliente de conexão de área de trabalho remoto. Se ativar esta definição de política, os utilizadores não podem automaticamente iniciar sessão para os serviços de ambiente de trabalho remoto, fornecendo as respetivas palavras-passe no cliente de conexão de área de trabalho remoto. eles for pedidos uma palavra-passe iniciar sessão. Se desativar esta definição de política, os usuários podem sempre fazem logon Remote Desktop Services automaticamente ao fornecer as respetivas palavras-passe no cliente de conexão de área de trabalho remoto. Se não configurar esta definição de política, o início de sessão automático não está especificado no nível de diretiva de grupo. 
  
  **Predefinido**: Enabled
  
- **Nível de encriptação da ligação de cliente de serviços de ambiente de trabalho remoto**  
  Especifica se exige o uso de um nível de criptografia específicas para proteger as comunicações entre computadores cliente e servidores de anfitrião de sessões de RD durante a ligações de protocolo RDP (Remote Desktop). Esta política aplica-se apenas quando estiver a utilizar encriptação nativa do RDP. No entanto, a encriptação nativa de RDP (em oposição a encriptação SSL) não é recomendada. Esta política não se aplica a encriptação SSL. Se ativar esta definição de política, todas as comunicações entre clientes e servidores de anfitrião de sessões de RD durante ligações remotas tem de utilizar o método de encriptação especificado nesta definição. Por predefinição, o nível de encriptação é definido como alto. Os seguintes métodos de encriptação estão disponíveis:  
  - *Alta*: A definição de elevada encripta os dados enviados do cliente para o servidor e do servidor para o cliente usando a criptografia forte de 128 bits. Utilize este nível de encriptação em ambientes que contenham apenas clientes de 128 bits (por exemplo, os clientes que executam a conexão de área de trabalho remoto). Os clientes que não suportam este nível de encriptação não é possível ligar aos servidores de anfitrião de sessões de RD.  
  - *Compatível com o cliente*: A definição de cliente compatível encripta os dados enviados entre o cliente e o servidor em que a força da chave máximo suportado pelo cliente. Utilize este nível de encriptação em ambientes que incluem os clientes que não suportam a encriptação de 128 bits.  
  - *Baixa*: A definição de baixa encripta apenas os dados enviados do cliente para o servidor usando a criptografia de 56 bits.  
  
  Se desabilitar ou não configura esta definição, o nível de encriptação a utilizar para ligações remotas para servidores de anfitrião de sessões de RD não é imposto por meio da diretiva de grupo. A conformidade FIPS importante pode ser configurada por meio da criptografia de sistema. Utilizar algoritmos compatíveis com FIPS para encriptação, hash e assinatura definições na política de grupo (em computador configuração Windows Settings\Local \ Opções.) A definição compatíveis com FIPS criptografa e descriptografa os dados enviados do cliente para o servidor e do servidor ao cliente, com os algoritmos de criptografia do Federal Information Processing Standard (FIPS) 140, através de módulos criptográficos da Microsoft. Utilize este nível de encriptação quando a comunicação entre clientes e servidores de anfitrião de sessões de RD requer o nível mais elevado de encriptação.
  
  **Predefinido**: Alta
  
## <a name="remote-management"></a>Gestão Remota  
Para obter mais informações, consulte [CSP de política - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) na documentação do Windows.  

- **Executar o bloco de armazenamento como credenciais**  
  Autenticação básica do cliente
  
  **Predefinido**: Enabled
  
- **Autenticação básica**  
  Esta definição de política permite-lhe gerir se o serviço de gestão remota do Windows (WinRM) aceita autenticação básica de um cliente remoto. Se ativar esta definição de política, o serviço WinRM aceita autenticação básica de um cliente remoto. Se desabilitar ou não configura esta definição de política, o serviço WinRM não aceita a autenticação básica de um cliente remoto.
  
  **Predefinido**: Desativado
  
- **Autenticação de texto implícita de cliente de bloco**  
  Esta definição de política permite-lhe gerir se o cliente de gestão remota do Windows (WinRM) utiliza a autenticação resumida. Se ativar esta definição de política, o cliente WinRM não usa a autenticação resumida. Se desabilitar ou não configura esta definição de política, o cliente WinRM utiliza autenticação resumida.
  
  **Predefinido**: Enabled
  
- **Tráfego não criptografado**  
  Esta definição de política permite-lhe gerir se o serviço de gestão remota do Windows (WinRM) envia e recebe mensagens não encriptadas através da rede. Se ativar esta definição de política, o cliente WinRM envia e recebe mensagens não encriptadas através da rede. Se desabilitar ou não configura esta definição de política, o cliente WinRM envia ou recebe apenas as mensagens encriptadas através da rede.  
  
  **Predefinido**: Desativado
  
- **Tráfego de cliente não encriptada**  
  Esta definição de política permite-lhe gerir se o cliente de gestão remota do Windows (WinRM) envia e recebe mensagens não encriptadas através da rede. Se ativar esta definição de política, o cliente WinRM envia e recebe mensagens não encriptadas através da rede. Se desabilitar ou não configura esta definição de política, o cliente WinRM envia ou recebe apenas as mensagens encriptadas através da rede.
  
  **Predefinido**: Desativado
  
- **Autenticação básica do cliente**  
  Esta definição de política permite-lhe gerir se o cliente de gestão remota do Windows (WinRM) utiliza a autenticação básica. Se ativar esta definição de política, o cliente WinRM utiliza a autenticação básica. Se o WinRM está configurado para utilizar o transporte HTTP, o nome de utilizador e palavra-passe são enviadas através da rede como texto não encriptado. Se desabilitar ou não configura esta definição de política, o cliente WinRM não usa a autenticação básica.
  
  **Predefinido**: Desativado
  

## <a name="remote-procedure-call"></a>Chamada de procedimento remoto  
Para obter mais informações, consulte [CSP de política - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) na documentação do Windows.  

- **Opções de RPC não autenticado de clientes**  
  Esta definição de política controla como o tempo de execução do servidor RPC processa não autenticados RPC clientes que se conectam aos servidores RPC. Esta definição de política irá afetar todos os aplicativos de RPC. Num ambiente de domínio, utilize esta definição de política com cuidado, dado que pode afetar uma ampla variedade de funcionalidades, incluindo o próprio de processamento de diretiva de grupo. Reverter uma alteração para esta definição de política pode exigir a intervenção manual de cada computador afetado. Esta definição de política nunca deve ser aplicada a um controlador de domínio. Se desativar esta definição de política, o tempo de execução do servidor RPC utilizará o valor de "Autenticado" no cliente Windows e o valor de "None" em versões do Windows Server que suportam esta definição de política. Se não configurar esta definição de política, continua a ser desativado. O tempo de execução do servidor RPC se comporta como se ele foi ativado com o valor de "Autenticado" utilizado para o cliente do Windows e o valor de "None" utilizada para SKUs de servidor que suportam esta definição de política. Se ativar esta definição de política, ele direciona o tempo de execução de servidor RPC para restringir não autenticados RPC clientes que se conectam a servidores RPC em execução numa máquina. Um cliente é considerado um cliente autenticado se este utilizar um pipe nomeado para comunicar com o servidor ou se ele usa a segurança de RPC. Esta restrição, dependendo do valor selecionado para esta definição de política pode isentar Interfaces RPC que pediu-se especificamente para ser acessível aos clientes não autenticados.  
  - *Nenhum* permite que todos os clientes RPC ligar a servidores RPC executado no computador em que a definição de política é aplicada. 
  - *Autenticado* permite que apenas os clientes RPC autenticado (por definição acima) para ligar a servidores RPC executado no computador em que a definição de política é aplicada. Isenções são concedidas a interfaces que pediram-los. 
  - *Autenticado sem exceções* permite que apenas os clientes RPC autenticado (por definição acima) para ligar a servidores RPC executado no computador em que a definição de política é aplicada. Sem exceções são permitidas. Nota: Esta definição de política não será aplicada até que o sistema for reiniciado.  

  **Predefinido**: Autenticado

## <a name="search"></a>Pesquisa 
Para obter mais informações, consulte [CSP de política - pesquisa](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) na documentação do Windows.  

- **Desativar a indexação de itens encriptados**  
  Permite ou proíbe a indexação de itens. Este parâmetro é para o indexador do Windows Search, que controla a indexação itens que são encriptados, tais como os ficheiros do Windows Information Protection (WIP) protegido. Quando a política está ativada, os itens protegidos pelo WIP são indexados e os respetivos metadados são armazenados numa localização não encriptada. Os metadados incluem conteúdos como o caminho do ficheiro e a data de modificação. Quando a política estiver desativada, os itens protegidos pelo WIP não são indexados e não são exibidos nos resultados na Cortana ou ficheiro explorer. O desempenho das aplicações de fotografias e do Groove também poderá ser afetado se existirem muitos ficheiros multimédia protegidos pelo WIP no dispositivo.
  
**Predefinido**: Sim
  
## <a name="smart-screen"></a>Smart Screen  
Para obter mais informações, consulte [CSP de política - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.  

- **Bloquear a execução de ficheiros não verificados**  
  Impedir o utilizador de executar ficheiros não verificados. 
  - *Não configurado* -funcionários podem ignorar os avisos do SmartScreen e executar ficheiros maliciosos. 
  - *Sim* – os funcionários não é possível ignorar os avisos do SmartScreen e executar ficheiros maliciosos.

  **Predefinido**: Sim

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **Exigir o SmartScreen para aplicações e ficheiros**  
  Permite aos administradores de TI configurar o SmartScreen para Windows.

  **Predefinido**: Sim
  
## <a name="system"></a>Sistema  
Para obter mais informações, consulte [CSP de política - sistema](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) na documentação do Windows.  

- **Inicialização de driver de início de arranque de sistema**  
  Esta definição de política permite-lhe especificar os drivers de inicialização são inicializados com base numa classificação de determinado por um driver de inicialização antecipada Antimalware iniciar. O driver de inicialização antecipada Antimalware de lançamento pode devolver as seguintes classificações para cada controlador de inicialização: 
  - *Boa*: O driver foi assinado e ainda não adulterado.  
  - *Ruim* -o driver foi identificado como software maligno. Recomendamos que não permita conhecidos controladores incorretos ser inicializado. 
  - *Ruim, mas necessário para o arranque*: O driver foi identificado como software maligno, mas o computador não pode inicializar com êxito sem carregar este controlador. 
  - *Desconhecido* -este controlador não tenha sido atestado por seu aplicativo de deteção de malware e não foi classificado pelo driver de inicialização antecipada Antimalware iniciar.  

  Se ativar esta definição de política, pode escolher quais drivers de inicialização para inicializar da próxima vez que o computador for iniciado. Se desabilitar ou não configurar esta política de definição, os drivers de início de inicialização for determinados desconhecido, bom ou ruim, mas é crítico de arranque é inicializados e a inicialização de controladores identificado como sendo má é ignorada. Se seu aplicativo de deteção de malware não inclui um driver de inicialização antecipada Antimalware iniciar ou se o driver de inicialização antecipada Antimalware iniciar tiver sido desativada, esta definição não tem qualquer efeito e todos os drivers de inicialização são inicializados.  
  
  **Predefinido**: Desconhecido bom e ruim críticas


## <a name="wi-fi"></a>Wi-Fi  
Para obter mais informações, consulte [CSP de política - Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) na documentação do Windows.  

- **Bloquear a partilha da Internet**  
  Especifica se a partilha da internet é permitida no dispositivo.  

  **Predefinido**: Sim  

- **Bloquear automaticamente ligação a hotspots Wi-Fi**  
  Permitir ou não ao dispositivo ligar automaticamente a hotspots Wi-Fi.  

  **Predefinido**: Sim  
  
## <a name="windows-connection-manager"></a>Gestor de ligações do Windows  
Para obter mais informações, consulte [CSP de política - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) na documentação do Windows.  

- **Ligação de bloco para redes de domínio**  
  Esta definição de política impede que computadores Conectando a uma rede baseada no domínio e um domínio com base em rede ao mesmo tempo. Se esta definição de política estiver ativada, o computador reage a tentativas de ligação de rede automática e manual com base nas seguintes circunstâncias: 
  - Tentativas de ligação automática quando o computador já está ligado a uma rede baseada em domínio, todas as tentativas de ligação automática a redes de domínio não são bloqueadas. Quando o computador já está ligado a uma rede baseada em domínio, as tentativas de ligação automática a redes com base em domínio são bloqueadas. 
  - Tentativas de ligação manual quando o computador já está ligado a um domínio com base em rede ou uma rede baseada em domínio sobre a mídia diferente de Ethernet e um utilizador tenta criar uma ligação manual a uma rede adicional em violação da presente política definir, desliga a ligação de rede existente e a ligação manual é permitida. Quando o computador já está ligado a um são um domínio com base em rede ou uma rede baseada em domínio sobre Ethernet e um utilizador tenta criar uma ligação manual a uma rede adicional em violação desta definição de política, é a ligação de Ethernet existente mantido, e a tentativa de ligação manual é bloqueada.  

  Se esta definição de política não está configurada ou está desativada, os computadores têm permissão para ligar em simultâneo ao domínio e redes de domínio não.  

  **Predefinido**: Enabled
  
## <a name="windows-defender"></a>Windows Defender  
Para obter mais informações, consulte [CSP de política - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.  

- **Analisar mensagens de correio recebidas**  
  Permite ou proíbe a verificação de e-mail.
  
  **Predefinido**: Sim  

- **Tipo de processo filho de lançamento de aplicações do Office**  
  Aplicações do Office não têm permissão para criar processos de subordinados. Isto inclui Word, Excel, PowerPoint, OneNote e acesso. Este é um comportamento típico de malware, especialmente para ataques baseados na macro que tentam utilizar aplicações do Office para iniciar ou transferir executáveis mal-intencionados.
  
  **Predefinido**: Bloquear
  
- **Tipo de consentimento de submissão de exemplo do Defender**  
  Nível no Windows Defender para enviar dados de consentimento de verificações para o utilizador. Se já tiver sido concedido o consentimento necessário, o Windows Defender envia-os. Caso contrário, (e se o usuário especificou nunca para perguntar), a interface do Usuário é iniciado para pedir consentimento do utilizador (quando o Defender/AllowCloudProtection é permitido) antes de enviar dados.
  
  **Predefinido**: Enviar automaticamente amostras seguras 
  
- **Intervalo de atualização de assinatura (em horas)**  
  Intervalo de atualização de assinatura de Defender em horas
  
  **Predefinido**: 4
  
- **Script transferido o tipo de execução do payload**  
  Script de Defender transferido o tipo de execução do payload
  
  **Predefinido**: Bloquear
  
- **Impedir que o tipo de roubo de credenciais**  
  Windows Defender Credential Guard utiliza segurança baseada em virtualização para isolar segredos, permitindo apenas software de sistema com privilégios possam acessá-los. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, tal como Ataques PtH ou PtT. Windows Defender Credential Guard impede estes ataques protegendo os hashes de palavra-passe NTLM, permissão de concessão de permissões Kerberos e as credenciais armazenadas por aplicações como credenciais de domínio.
  
  **Predefinido**: Ativar

- **Tipo de execução de conteúdo de e-mail**  
  Esta regra bloqueia os seguintes tipos de ficheiro de que está a ser executado ou iniciados a partir de uma mensagem de e-mail vista no Microsoft Outlook ou webmail (como Gmail.com ou Outlook.com): Executável arquivos (por exemplo, .exe,. dll ou. scr), arquivos de Script (por exemplo, um .ps do PowerShell, VisualBasic. vbs ou arquivo do JavaScript. js) ficheiros de arquivo de Script.
  
  **Predefinido**: Bloquear
  
- **Tipo de proteção de rede**  
  Esta política permite-lhe ativar a proteção de rede (bloco/auditoria) e desativado no Windows Defender Exploit Guard. Proteção de rede é uma funcionalidade do Windows Defender Exploit Guard que protege os funcionários com qualquer aplicação de aceder ao atos fraudulentos de phishing, sites que hospedam a exploração e conteúdo malicioso na Internet. Isto inclui a impedir de browsers de terceiros de ligar a sites perigosos. Tipo de valor é o número inteiro. Se habilitar essa configuração, proteção de rede está ativada e os funcionários não podem desativá-la. Seu comportamento pode ser controlado pelas seguintes opções: Bloco e de auditoria. Se ativar esta política com a opção "Bloquear", os utilizadores e aplicações estão bloqueadas de se ligar a domínios perigosos. Pode ver esta atividade no Centro de segurança do Windows Defender. Se ativar esta política com a opção "Auditoria", os utilizadores/aplicações não serão bloqueadas se a domínios perigosos. No entanto, ainda verá esta atividade no Centro de segurança do Windows Defender. Se desativar esta política, os utilizadores/aplicações não serão bloqueadas se a domínios perigosos. Não verá qualquer atividade de rede no Centro de segurança do Windows Defender. Se não configurar esta política, o bloqueio de rede está desativada por predefinição.
  
  **Predefinido**: Ativar
  
- **Agendar dia da análise do Defender**  
  Defender agendar dia da análise.
  
  **Predefinido**: todos os dias
  
- **Proteção fornecida pela cloud**  
  Para proteger melhor o seu PC, o Windows Defender irá enviar informações à Microsoft sobre quaisquer problemas que encontra. Microsoft irá analisar essas informações, obter mais informações sobre problemas que afetam o utilizador e outros clientes e oferecer soluções aprimoradas.
  
  **Predefinido**:  Sim  

- **Defender potencialmente indesejado ação da aplicação**  
  A funcionalidade de proteção de aplicação potencialmente indesejável (PUA) no Windows Defender Antivirus pode identificar e bloquear PUAs transfiram e instalem em pontos finais na sua rede. Esses aplicativos não são considerados vírus, malware ou outros tipos de ameaças, mas podem executar ações nos pontos de extremidade que negativamente afetam o desempenho ou a utilizam. PUA também pode consultar os aplicativos que são considerados como tendo uma reputação ruim. Um comportamento típico PUA inclui: Vários tipos de software agrupamento injeção do Ad em navegadores da web Driver e otimizadores de registo que detetar problemas, pagamento de pedido para corrigir os erros, mas permanecem no ponto final e fazer sem alterações ou otimizações (também conhecido como programas de "não autorizados antivírus"). Esses aplicativos podem aumentar o risco da sua rede que está a ser infetado com software maligno, fazer com que infeções de software maligno ser mais difícil para identificar e pode desperdiçar recursos de TI em Limpar as aplicações.  
  
  **Predefinido**: Bloquear  

- **Tipo de código de macro de oculto de script**  
  Software maligno e outras ameaças podem tentar ofuscar ou ocultar o respetivo código malicioso em alguns arquivos de script. Esta regra impede que os scripts que parecem estar ocultado a execução.
  
  **Predefinido**: Bloquear
  
- **Analisar unidades amovíveis durante uma análise completa**  
  Permite que o Windows Defender analisar quanto a software mal-intencionado e indesejado em unidades amovíveis (por exemplo, unidades flash) durante uma análise completa. Antivírus do Windows Defender analisa todos os ficheiros em dispositivos USB antes da execução.
  
  **Predefinido**: Sim  
  
- **Analisar ficheiros de arquivo**  
  O Defender analise ficheiros de arquivo.
  
  **Predefinido**: Sim
  
- **Monitorização de comportamento**  
  Permite ou proíbe a funcionalidade de monitorização de comportamento do Windows Defender. Incorporado no Windows 10, destes sensores a recolhem e processam sinais comportamentais do sistema operacional e envia estes dados de sensor para sua instância de cloud privada, isolados, do Windows Defender ATP.
  
  **Predefinido**: Sim

- **Analisar ficheiros abertos a partir de pastas de rede**  
  Se os ficheiros são só de leitura, o utilizador não será capaz de remover qualquer software maligno detetado.
  
  **Predefinido**: Sim

- **Tipo de processo USB não fidedigno**  
  Com esta regra, os administradores podem impedir que ficheiros executáveis não assinados ou não fidedignos em execução a partir de unidades amovíveis USB, incluindo cartões SD.
  
  **Predefinido**: Bloquear
  
- **Aplicações do Office outros processam o tipo de injeção**  
  Aplicações do Office, incluindo o Word, Excel, PowerPoint e OneNote, não poderá injetar código noutros processos. Isso é normalmente utilizado por software maligno para executar código malicioso numa tentativa de ocultar a atividade de mecanismos de verificação de antivírus.
  
  **Predefinido**:  Bloquear
  
- **Código de macro do Office que tipo de importações do Win32**  
  Software maligno pode utilizar o código de macro ficheiros do Office para importar e carregar DLLs Win32, o que, em seguida, pode ser utilizado para efetuar chamadas de API para permitir a infecção em todo o sistema. Esta regra tenta bloquear ficheiros do Office que contêm código de macro que é capaz de importar as Win32 DLLs. Isto inclui Word, Excel, PowerPoint e OneNote.
  
  **Predefinido**: Bloquear  
  
- **Nível de bloco de nuvem do Defender**  
  Nível de bloco do Defender na cloud.
  
  **Predefinido**: Não Configurado

- **Monitorização em tempo real**  
  Defender requer a monitorização em tempo real.
  
  **Predefinido**: Sim
  
- **Office aplicações executável criação ou lançamento tipo de conteúdo**  
  Esta regra destina-se comportamentos comuns utilizados por suplementos suspeitos e maliciosos e scripts (extensões), que criam ou iniciar ficheiros executáveis. Essa é uma técnica de malware típico. As extensões são bloqueadas sejam utilizados pelas aplicações do Office. Normalmente, estas extensões utilizam o Windows Scripting Host (.wsh ficheiros) para executar scripts que automatizar determinadas tarefas ou fornecer funcionalidades de suplemento criados pelo utilizador
  
  **Predefinido**: Bloquear

## <a name="windows-ink-workspace"></a>Área de trabalho do Windows Ink  
Para obter mais informações, consulte [CSP de política - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) na documentação do Windows.  

- **Área de trabalho do Ink**  
  Especifica se pretende permitir que o utilizador aceda à área de trabalho da ink. 
  - *Desativada* -acesso à tinta a área de trabalho está desativado. A funcionalidade está desativada.
  - *Ativado* - funcionalidade da área de trabalho do Ink está ativada, mas o utilizador não é possível aceder à mesma acima do ecrã de bloqueio.
  - *Não configurado* - funcionalidade da área de trabalho do Ink está ativada e o utilizador pode utilizá-lo acima do ecrã de bloqueio.  

  **Predefinido**: Enabled
 
## <a name="windows-powershell"></a>Windows PowerShell  
Para obter mais informações, consulte [CSP de política - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) na documentação do Windows.  

- **Script de shell do shell de energia bloquear o Registro em log**  
  Esta definição de política ativa o registo de todas as entradas de script do PowerShell para o registo de eventos da Microsoft-Windows-PowerShell/Operational. Se ativar esta definição de política, o Windows PowerShell irá iniciar o processamento de comandos, blocos de script, funções e scripts - se invocada interativamente ou através da automatização. Se desativar esta definição de política, o registo de entrada de script do PowerShell está desativado. Se ativar o registo de invocação de bloco do Script, o PowerShell adicionalmente regista eventos quando a invocação de um comando, o bloco de script, a função ou o script inicia ou para. Ativar o registo de invocação gera um grande volume de registos de eventos. Nota: Esta definição de política existe na configuração do computador e configuração do usuário no Editor de diretiva de grupo. A definição de política de configuração do computador tem precedência sobre a definição de política de configuração do usuário.
  
  **Predefinido**: Enabled
 
