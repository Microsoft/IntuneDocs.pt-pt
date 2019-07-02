---
title: Definições de linhas de base de segurança do Intune para Windows 10
titleSuffix: Microsoft Intune
description: Definições de linha de base de segurança do Intune para gerir o Windows 10
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56e1a1e07a403afa4db405d276c55be1ef8ddfd8
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494569"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Definições de linha de base de segurança MDM do Intune  

Veja as definições de linha de base de segurança MDM que são suportados pelo Microsoft Intune para dispositivos que executam o Windows 10 ou posterior. Os valores predefinidos para as definições nesta linha de base representam a configuração recomendada para dispositivos aplicáveis e podem não corresponder aos padrões de linha de base de outras linhas de base de segurança.  

A versão de linha de base mais recente é **linha de base de segurança de MDM para atualização de Spring 2019 (1 de 19 horas)**  

Para saber mais sobre o que mudou na versão mais recente desta linha de base da versão anterior, veja [o que mudou no novo modelo](#whats-changed-in-the-new-template).  

> [!NOTE]  
> Em Junho de 2019, a linha de base de segurança MDM pré-visualização foi substituída pela versão dos *linha de base de segurança de MDM para atualização de Spring 2019 (1 de 19 horas)* modelo, que é generaly disponível (não em pré-visualização). Perfis que foram criados antes da disponibilidade dos *linha de base de segurança de MDM para atualização de Spring 2019 (1 de 19 horas)* linha de base não atualizados para refletir as definições e os valores que estão na linha de base de segurança de MDM para atualização de Spring 2019 (19 horas 1 ) versão.  Embora não é possível criar novos perfis com base no modelo de pré-visualização, pode editar e continuar a utilizar os perfis que criou anteriormente baseiam-se no modelo de pré-visualização.   
  
Para saber mais sobre como utilizar linhas de base de segurança com o Intune, veja [utilizar linhas de base de segurança](security-baselines.md).  


   
## <a name="above-lock"></a>Acima de bloqueio  
Para obter mais informações, consulte [CSP de política - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) na documentação do Windows.  

- **Exibição de bloco de notificações do sistema**  
  Esta definição de política permite-lhe impedir que as notificações de aplicações de aparecer no ecrã de bloqueio. Se ativar esta definição de política, não existem notificações da aplicação são apresentadas no ecrã de bloqueio. Se desabilitar ou não configura esta definição de política, os usuários podem escolher quais as aplicações apresentar as notificações no ecrã de bloqueio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Predefinido**: Sim  

- **Voz ativar aplicações a partir do ecrã bloqueado**  

  **Predefinido**: Desativado

## <a name="app-runtime"></a>Tempo de execução da aplicação    
Para obter mais informações, consulte [CSP de política - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) na documentação do Windows.  

- **Contas Microsoft opcionais para aplicações da Windows Store**  
  Esta definição de política permite-lhe controlar se as contas Microsoft são opcionais para aplicações da Windows Store que requerem uma conta para iniciar sessão. Esta política afeta apenas as aplicações do Windows Store que o suportam. Se ativar esta definição de política, aplicações da Windows Store que exigem, normalmente, uma conta Microsoft para iniciar sessão permitirá aos utilizadores iniciar sessão com uma conta da empresa em vez disso. Se desabilitar ou não configura esta definição de política, os utilizadores devem iniciar sessão com uma conta Microsoft.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Predefinido**: Enabled  

## <a name="application-management"></a>Gestão de aplicações   
Para obter mais informações, consulte [CSP de política - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) na documentação do Windows.  

- **Controle de usuário de bloco através de instalações**  
  Esta definição de política permite aos utilizadores alterar as opções de instalação que normalmente estão disponíveis apenas para os administradores de sistema. Se ativar esta definição de política, alguns dos recursos de segurança do Windows Installer são ignorados. Ele permite que as instalações para concluir que caso contrário, seriam queria ser interrompidas devido a uma violação de segurança. Se desabilitar ou não configurar esta definição de política, os recursos de segurança do Windows Installer impedem os utilizadores alterem as opções de instalação, normalmente reservadas para os administradores de sistema, tais como especificar o diretório ao qual os ficheiros são instalados. Se o Windows Installer detetar que um pacote de instalação tem a permissão ao utilizador alterar uma opção protegida, interrompe a instalação e exibe uma mensagem. Estas funcionalidades de segurança funcionam apenas quando o programa de instalação está em execução num contexto de segurança com privilégios em que tem acesso a diretórios negado ao utilizador. Esta definição de política foi concebida para ambientes menos restritivos. Pode ser utilizado para contornar erros num programa de instalação que impede que o software que está a ser instalado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067060)  

    **Predefinido**: Sim

- **Instalações de aplicações do bloco MSI com privilégios elevados**  
  Esta definição de política direciona o Windows Installer para utilizar permissões elevadas, quando instalar qualquer programa no sistema.  
  - *Se ativar esta definição de política*, privilégios são expandidos para todos os programas. Esses privilégios são normalmente reservados para programas que foram atribuídos ao utilizador (oferecido no ambiente de trabalho), atribuído à f do computador (instalado automaticamente) ou disponibilizados em Adicionar ou remover programas no painel de controlo. Esta definição de perfil permite aos utilizadores instalar programas que exigem acesso a diretórios que o utilizador poderá não ter permissão para ver ou alterar, incluindo diretórios nos computadores altamente restritas.
  - *Se desabilitar ou não configurar esta definição de política*, o sistema se aplica as permissões do utilizador atual quando instalar programas que um administrador de sistema não distribuir ou oferta. Nota: Esta definição de política é apresentada de configuração do computador e as pastas de configuração do usuário. Para tornar esta definição de política em vigor, tem de ativá-la em ambas as pastas. Atenção: Os utilizadores qualificados podem aproveitar as permissões esta concede alterar seus privilégios e obter acesso permanente a restrito de ficheiros e pastas de definição de política. Tenha em atenção que a versão de configuração do usuário desta definição de política não é garantida para ser seguro.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Predefinido**: Sim

- **Bloquear o gravador de jogo (apenas ambiente de trabalho)**  
  Configura se é permitida a gravação e a difusão de jogos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Predefinido**: Sim  

## <a name="auto-play"></a>Reprodução automática   
Para obter mais informações, consulte [CSP de política - reprodução automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) na documentação do Windows.  

- **Comportamento de execução de automática de padrão de reprodução automática**  
  Esta definição afeta o comportamento predefinido para comandos de execução automática. Comandos de execução automática são armazenados em arquivos Autorun. inf e podem iniciar programas de instalação ou outras rotinas. Quando *ativado*, os administradores podem alterar o comportamento de execução automática do padrão num dispositivo que executa o Windows Vista ou posterior. Comportamento pode ser definido como: a) completamente desativar comandos de execução automática ou b) reverter para o comportamento do anteriores ao Windows Vista de automaticamente executar o comando de execução automática. Quando definido como *desativada* ou *não configurada*, os dispositivos que executam o Windows Vista ou posterior perguntar ao usuário sobre um comando de execução automática deve ser executado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Predefinido**: Não executar  
  
- **Modo de reprodução automática**  
  Esta definição de política permite-lhe desativar a funcionalidade de reprodução automática. Reprodução automática começa a leitura de uma unidade assim que insira o suporte de dados na unidade. Como resultado, o ficheiro de configuração de programas e a música no suporte de dados de áudio começar imediatamente. Antes do Windows XP SP2, a reprodução automática está desativada por predefinição em unidades amovíveis, como a unidade de disquete (mas não a unidade de CD-ROM) e em unidades de rede. A partir do Windows XP SP2, o reprodução automática está ativada-se para unidades amovíveis, incluindo unidades Zip e alguns dispositivos de armazenamento em massa USB. Se ativar esta definição de política, reprodução automática está desativada em CD-ROM e unidades de mídia removível ou desativado em todas as unidades. Esta definição de política Desabilita a reprodução automática em tipos adicionais de unidades. Não é possível utilizar esta definição para ativar a reprodução automática em unidades em que está desativada por predefinição. Se desabilitar ou não configura esta definição de política, reprodução automática está ativada. Nota: Esta definição de política é apresentada nas pastas a configuração do computador e a configuração do usuário. Se as definições de política entrarem em conflito, a definição de política na configuração do computador tem precedência sobre a definição de política na configuração de utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Predefinido**: Desativado

- **Bloquear a reprodução automática para dispositivos não volume**  
  Esta definição de política não permite reprodução automática para dispositivos do MTP, como câmeras ou telefones. Se ativar esta definição de política, reprodução automática não é permitida para dispositivos do MTP, como câmeras ou telefones. Se desabilitar ou não configura esta definição de política, reprodução automática está ativada para dispositivos não volume.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Predefinido**: Enabled  

## <a name="bitlocker"></a>BitLocker    
Para obter mais informações, consulte [CSP de política - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) na documentação do Windows.  

- **Pouco cacifo unidade amovível política**  
  Esta definição de política é utilizada para controlar o método de encriptação e a força de cifras. Os valores desta política determinam a força da cifra que utiliza o BitLocker para a encriptação. As empresas podem querer controlar o nível de encriptação para maior segurança (AES-256 é mais forte do que AES-128). Se ativar esta definição, poderá configurar um algoritmo de encriptação e a força da codificação de chave para unidades de dados fixas, unidades de sistema operativo e unidades de dados amovíveis individualmente. Para unidades de sistema operacionais e fixo, recomendamos que utilize o algoritmo de XTS-AES. Para unidades amovíveis, deve usar AES-CBC 128 bits ou AES-CBC 256 bits se a unidade é utilizada em outros dispositivos que não estão a executar o Windows 10, versão 1511 ou posterior. Alterar o método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação está em curso. Nestes casos, esta definição de política é ignorada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Para a política de unidade amovível cacifo de Bit, configure a definição seguinte:

    - **Exigir encriptação de acesso de escrita**  
      **Predefinido**: Sim  
  

## <a name="browser"></a>Browser  
Para obter mais informações, consulte [CSP de política - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) na documentação do Windows.  

- **Exigir o SmartScreen para o Microsoft Edge**  
  Microsoft Edge utiliza o Windows Defender SmartScreen (ativado) para proteger os usuários contra potenciais atos fraudulentos de phishing e software malicioso por predefinição. Além disso, por predefinição, os utilizadores não é possível desativar (desative) Windows Defender SmartScreen. Ativar esta política se desligar o Windows Defender SmartScreen e impedir que os utilizadores ativá-la. Não configure esta política para permitir que os utilizadores que optar por ativar ou desativar a defender de Windows SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Predefinido**: Sim  
  
- **Bloquear o acesso do site malicioso**  
  Por predefinição, o Microsoft Edge permite aos utilizadores ignorar (ignorar) os avisos do Windows Defender SmartScreen sobre sites potencialmente maliciosos, permitindo-lhes continuar para o site. Com esta política, pode configurar Microsoft Edge para impedir que os utilizadores ignorem os avisos do utilizador, bloqueando-los continue para o site.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Predefinido**: Sim  
  
- **Bloquear a transferência de ficheiros não verificados**  
  Por predefinição, o Microsoft Edge permite aos utilizadores ignorar (ignorar) os avisos do Windows Defender SmartScreen sobre ficheiros potencialmente maliciosos, permitindo que os utilizadores continuem a transferir os ficheiros não verificados. Ativar esta política impede os utilizadores ignorem os avisos,-los a bloquear a transferência dos ficheiros não verificados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Predefinido**: Sim  
  
- **Gestor de palavra-passe de bloco**  
  Por predefinição, Microsoft Edge utiliza o Gestor de palavra-passe automaticamente, permitindo que os usuários a palavras-passe manager localmente. A desativar esta política restringe o Microsoft Edge de utilizando o Gestor de palavra-passe. Não configure esta política se pretender permitir que os utilizadores que optar por guardar e gerir palavras-passe localmente utilizando o Gestor de palavra-passe.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Predefinido**: Sim  
  
- **Impedir as substituições de erro de certificado**  
  Esta definição de política impede que o utilizador a ignorar erros de certificado de Secure Sockets Layer/Transport Layer Security (SSL/TLS) que interrompem a navegação (como "expirada", "revogado" ou erros de "erro de correspondência do nome") no Internet Explorer. Se ativar esta definição de política, o utilizador não é possível continuar a navegar. Se desabilitar ou não configura esta definição de política, o utilizador pode optar por ignorar erros de certificado e continuar a navegar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Predefinido**: Sim  

## <a name="connectivity"></a>Conectividade  
Para obter mais informações, consulte [CSP de política - conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) na documentação do Windows.  

- **Transferência de Internet de bloco para web de publicação e ordenação online assistentes**  
  Esta definição de política especifica se o Windows devem transferir uma lista de fornecedores para a web de publicação e ordenação online assistentes. Estes assistentes permitem que os utilizadores selecionarem uma lista de empresas que fornecem serviços como o armazenamento online e impressão photographic. Por predefinição, o Windows apresenta fornecedores transferidos a partir de um site do Windows para além de fornecedores especificado no registo. Se ativar esta definição de política, o Windows não transferir fornecedores e apenas os fornecedores de serviços que estão em cache no visor de registo local. Se desabilitar ou não configura esta definição de política, uma lista de fornecedores transfere quando o utilizador utiliza a web de publicação ou pedidos online assistentes. Para obter mais informações que inclui detalhes sobre a especificação de fornecedores de serviços no Registro, consulte a documentação para a web de publicação e ordenação online assistentes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Predefinido**: Enabled  

- **Bloquear o download dos controladores de impressão por HTTP**  
  Esta definição de política especifica se pretende permitir que este cliente transferir pacotes de controladores de impressão por HTTP. Para configurar a impressão de HTTP, drivers de caixa de entrada não tem de ser transferidos através de HTTP. Nota: Esta definição de política não impede que o cliente de impressão para impressoras na Intranet ou na Internet através de HTTP. Apenas proíbe a transferência de controladores que ainda não estiverem instalados localmente. Se ativar esta definição de política, os controladores de impressão não pode ser transferido através de HTTP. Se desabilitar ou não configura esta definição de política, os utilizadores podem transferir controladores de impressão por HTTP.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Predefinido**: Enabled  

## <a name="credentials-delegation"></a>Delegação de credenciais  
Para obter mais informações, consulte [CSP de política - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) na documentação do Windows.  

- **Delegação de anfitrião remoto de credenciais não exportável**  
  Anfitrião remoto permite que a delegação de credenciais não exportável. Ao utilizar a delegação de credenciais, os dispositivos fornecem uma versão exportável de credenciais para o anfitrião remoto, que expõe os utilizadores ao risco de roubo de credenciais contra invasores no anfitrião remoto. Se ativar esta definição de política, o anfitrião suporta o modo Admin restrito ou de Credential Guard remoto. Se desabilitar ou não configura esta definição de política, administração restrito e o modo de Credential Guard remoto não são suportados. Usuário sempre precisará passar as credenciais para o anfitrião.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Predefinido**: Enabled  

## <a name="credentials-ui"></a>Credenciais da interface do Usuário  
Para obter mais informações, consulte [CSP de política - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) na documentação do Windows.  

- **Enumerar os administradores** esta política de definição de controles se as contas de administrador da tela quando um utilizador tenta elevar um aplicativo em execução. Por predefinição, as contas de administrador não são apresentadas quando o utilizador tenta elevar um aplicativo em execução. Se ativar esta definição de política, todas as contas de administrador local no PC apresentam para que o utilizador possa escolher um e introduza a palavra-passe correta. Se desativar esta definição de política, os usuários sempre terão de escreva um nome de utilizador e palavra-passe para elevar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Predefinido**: Desativado  

## <a name="data-protection"></a>Proteção de dados  
Para obter mais informações, consulte [CSP de política - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) na documentação do Windows.  

- **Bloquear acesso direto à memória**  
  Esta definição de política permite-lhe bloquear o acesso direto à memória (DMA) para todos os hot conectáveis PCI downstream portas até que um utilizador inicia sessão no Windows. Assim que um utilizador inicia sessão, o Windows irão enumerar os dispositivos PCI ligados as portas PCI do host plug. Sempre que o utilizador bloqueia a máquina, DMA está bloqueado nas portas PCI plug frequente sem dispositivos filhos até que o usuário fizer logon novamente. Dispositivos que já foram enumerados quando a máquina foi desbloqueada continuarão a funcionar até que não-conectado. Esta definição de política é imposta apenas quando a encriptação BitLocker ou o dispositivo está ativada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Predefinido**: Sim  

## <a name="device-guard"></a>O Device Guard  
Para obter mais informações, consulte [CSP de política - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) na documentação do Windows.  

- **Credential Guard**  
  Esta definição permite aos utilizadores ativar o Credential Guard com a segurança baseada em virtualização para ajudar a proteger as credenciais no próximo reinício.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Predefinido**: Ativar com bloqueio UEFI 

- **Ativar a virtualização com base em segurança**   
  Ativa a virtualização de segurança baseada em (VBS) no próximo reinício. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Predefinido**: Sim  


- **Inicie a proteção do sistema**    
  **Predefinido**: Enabled  

## <a name="device-installation"></a>Instalação de dispositivo  
Para obter mais informações, consulte [CSP de política - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) na documentação do Windows.  

- **Instalação de dispositivo de hardware por identificadores de dispositivo**  
  Esta definição de política permite-lhe especificar uma lista de IDs de hardware Plug and Play e identificações compatíveis com dispositivos que o Windows é impedidos de instalar. Esta definição de política tem precedência sobre qualquer outra definição de política que permite que o Windows instalar um dispositivo. Se ativar esta definição de política, o Windows é impedidos de instalar um dispositivo cujo hardware identificação compatível ou ID é apresentado na lista que cria. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a definição de política afeta o redirecionamento dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desabilitar ou não configura esta definição de política, os dispositivos podem instalar e atualizar como permitido ou impedido por outras configurações de diretiva.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
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
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
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
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Predefinido**: Enabled  

- **Exigir palavra-passe**  
  Especifica se o bloqueio do dispositivo está ativado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Predefinido**: Sim  
  
    Quando *exigir palavra-passe* está definida como *Sim*, as seguintes definições estão disponíveis.

    - **Contagem de conjunto de caracteres de mínimo de palavra-passe**  
      O número de tipos de elementos complexos (letras maiúsculas e minúsculas, números e pontuação) necessários para um PIN ou palavra-passe forte. PIN impõe o seguinte comportamento para computadores e dispositivos móveis: 1 - dígitos apenas 2 - dígitos e letras minúsculas são necessárias 3 - dígitos, letras minúsculas, e têm de letras maiúsculas. Não é suportado em contas do ambiente de trabalho Microsoft e contas de domínio. 4 - dígitos, letras minúsculas, letras maiúsculas e carateres especiais são necessários. Não é suportado no desktop. O valor predefinido é 1.  
      [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067055)  
      
      **Predefinido**: 3  
  
    - **Número de falhas de início de sessão antes de eliminar os dados do dispositivo**  
      O número de falhas de autenticação permitidas antes do dispositivo é apagado. Um valor de 0 desativa a funcionalidade de limpeza do dispositivo.  
      [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067030)  
        
      **Predefinido**: 10  
  
    - **Expiração da Palavra-passe (dias)**  
      A definição de política de idade de palavra-passe máximo determina a forma como há muito tempo (em dias) que uma palavra-passe pode ser utilizada antes do sistema exige que o utilizador para alterá-lo. Pode definir palavras-passe para expirar após um número de dias entre 1 e 999, ou pode especificar que as palavras-passe nunca expirem ao definir o número de dias para 0. Se a idade de palavra-passe de máximo é entre 1 e 999 dias, a idade mínima da palavra-passe tem de ser inferior a idade máxima da palavra-passe. Se a idade de palavra-passe máximo for definida como 0, a idade de palavra-passe mínimo pode ser qualquer valor entre 0 e 998 dias.  
      [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067028)  
      
      **Predefinido**: 60  
  
    - **Tipo obrigatório de palavra-passe**  
      Determina o tipo de PIN ou palavra-passe necessária.  
      [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067027)  
      
      **Predefinido**: Alfanumérico  
  
    - **Comprimento mínimo da palavra-passe**  
      A definição de política de comprimento de palavra-passe mínima determina o menor número de carateres que podem tornar uma palavra-passe para uma conta de utilizador. Pode definir um valor entre 1 e 14 carateres, ou pode estabelecer que nenhuma palavra-passe é necessária para definir o número de carateres como 0.  
      [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067024)  
      
      **Predefinido**: 8  
  
    - **Bloquear palavras-passe simples**  
      Especifica se os PINs ou palavras-passe como "1111" ou "1234" são permitidas. Para a área de trabalho, este também controla o uso de senhas com imagem.  
      [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067127) 
      
      **Predefinido**: Sim  
        *Uma definição de Sim impede a utilização de palavras-passe simples.* 

  - **Impedir a reutilização de palavras-passe anteriores**  
    Especifica quantas palavras-passe podem ser armazenadas no histórico de que não pode ser utilizado. O valor inclui a palavra-passe do utilizador atual. Por exemplo, com uma definição de *1* o utilizador não é possível reutilizar a palavra-passe atual ao escolher uma nova palavra-passe. Uma definição de *5* significa que um utilizador não é possível definir a palavra-passe nova para a palavra-passe atual ou qualquer uma das suas palavras-passe anteriores quatro.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Predefinido**: 24  

- **Impedir a apresentação de diapositivos**  
  Desativa as definições de apresentação de slides do ecrã de bloqueio em definições do PC e impede que uma apresentação de diapositivos reproduzindo no ecrã de bloqueio. Por predefinição, os utilizadores podem ativar uma apresentação de slides que será executado depois que a máquina de bloqueio. Se ativar esta definição, os utilizadores não é possível modificar as definições de apresentação de slides nas definições do PC, e não de slides pode começar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Predefinido**: Enabled  
  *Uma definição de ativado impede que o slide mostra a execução.* 

- **Idade mínima da palavra-passe em dias**  
  A definição de política de idade de palavra-passe mínima determina o período de tempo (em dias) que uma palavra-passe tem de ser utilizada antes do utilizador pode alterá-lo. Pode definir um valor entre 1 e 998 dias, ou pode permitir que as alterações de palavra-passe imediatamente ao definir o número de dias para 0. A idade mínima da palavra-passe tem de ser inferior a idade de palavra-passe máximo, a menos que a idade máxima da palavra-passe está definida como 0, que indica que as palavras-passe nunca expira. Se a idade máxima da palavra-passe é definida como 0, a idade mínima da palavra-passe pode ser definida para qualquer valor entre 0 e 998.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Predefinido**: 1  

## <a name="dma-guard"></a>Proteção de DMA  
Para obter mais informações, consulte [CSP de política - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) na documentação do Windows.
- **Enumeração de dispositivos externos incompatíveis com a proteção do DMA de Kernel**  
  Esta política destina-se para fornecer segurança adicional para dispositivos compatíveis com o DMA externos. Ele permite mais controlo sobre a enumeração de dispositivos compatíveis com o DMA externos incompatível com o isolamento de memória DMA. o remapeamento/dispositivo e áreas de segurança. Esta política só tem efeito quando a proteção do DMA de Kernel é suportada e ativada pelo firmware do sistema. Proteção de DMA de kernel é uma funcionalidade de plataforma que não pode ser controlada através de política ou do utilizador final. Tem de ser suportado pelo sistema no momento da produção. Para verificar se o sistema suporta a proteção do DMA de Kernel, verifique o campo de Kernel DMA proteção na página de resumo do MSINFO32.exe.  
  [Saiba mais](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Predefinido**: Bloquear todos   

## <a name="event-log-service"></a>Serviço de registo de eventos  
Para obter mais informações, consulte [CSP de política - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) na documentação do Windows.  

- **Tamanho máximo do ficheiro de registo de segurança no artigo BDC**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho do ficheiro de registo máximo para ser entre 1 megabyte (1024 quilobytes) e 2 terabytes (quilobytes 2147483647) em incrementos de kilobytes. Se desabilitar ou não configura esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local usando a caixa de diálogo de propriedades de registo e é assumida como predefinição para 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Predefinido**: 196608  

- **Tamanho máximo do ficheiro de registo de sistema no artigo BDC**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho do ficheiro de registo máximo para ser entre 1 megabyte (1024 quilobytes) e 2 terabytes (quilobytes 2147483647) em incrementos de kilobytes. Se desabilitar ou não configura esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local usando a caixa de diálogo de propriedades de registo e é assumida como predefinição para 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Predefinido**: 32768  

- **Tamanho máximo do ficheiro de registo de aplicação no artigo BDC**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho do ficheiro de registo máximo para ser entre 1 megabyte (1024 quilobytes) e 2 terabytes (quilobytes 2147483647) em incrementos de kilobytes. Se desabilitar ou não configura esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local usando a caixa de diálogo de propriedades de registo e é assumida como predefinição para 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Predefinido**: 32768  

## <a name="experience"></a>Experiência  
Para obter mais informações, consulte [CSP de política - experiência](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) na documentação do Windows.  

- **Bloquear destaque do Windows**  
  Permite que os administradores de TI desativar todos os Windows funcionalidades de destaque - destaque do Windows no funcionalidades do consumidor do bloqueio ecrã, dicas do Windows, Microsoft e outras funcionalidades relacionadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Predefinido**: Sim  

  Quando *destaque do Windows bloquear* está definida como *Sim*, as seguintes definições estão disponíveis.
  
  - **Bloquear as sugestões de terceiros no destaque do Windows**  
    Especifica se a permitir sugestões de aplicações e conteúdos do software de terceiros publicadores no Windows em destaque funcionalidades como o destaque do ecrã de bloqueio, aplicações sugeridas no menu Iniciar e dicas do Windows. Utilizadores ainda poderão ver sugestões de funcionalidades, aplicações e serviços Microsoft.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Predefinido**: Sim  
  - **Bloquear recursos específicos do consumidor**  
    Permite que os administradores de TI ativem experiências normalmente destinadas a consumidores apenas, tais como sugestões de início, notificações de associação, instalação de aplicações pós-OOBE, e mosaicos de redirecionamento.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Predefinido**: Sim  

## <a name="exploit-guard"></a>Exploit Guard  
Para obter mais informações, consulte [CSP de política - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) na documentação do Windows.  

- **Proteção de exploração XML**  
  Permite que o administrador de TI produzir uma configuração que representa o sistema pretendido e as opções de atenuação do aplicativo para todos os dispositivos da organização. A configuração é representada por um XML. Exploit protection ajuda a proteger os dispositivos contra software maligno que utilize explorações para distribuir e infectar. Utilize a aplicação de segurança do Windows ou o PowerShell para criar um conjunto de atenuações (conhecido como configuração). Em seguida, pode exportar esta configuração como um arquivo XML e partilhe-a com várias máquinas na sua rede para que todos eles têm o mesmo conjunto de definições de atenuação. Também pode converter e importar um arquivo XML de configuração EMET existente para um XML de configuração da proteção de exploração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Predefinido**: *Xml de exemplo é fornecido* 
 
## <a name="file-explorer"></a>Explorador de Ficheiros  
Para obter mais informações, consulte [CSP de política - Explorador de ficheiros](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) na documentação do Windows.  

- **Prevenção de execução de dados de bloco**  
  Desabilitar a prevenção de execução de dados pode permitir que determinados aplicativos herdados de plug-ins a funcionar sem terminação Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Predefinido**: Desativado  
   
- **Terminação de área dinâmica para dados de bloco em Corrupção**  
  Desativar a terminação de área dinâmica para dados em corrupção pode permitir que determinados aplicativos herdados de plug-ins a funcionar sem terminação Explorer imediatamente, embora Explorer pode ainda terminar inesperadamente mais tarde.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Predefinido**: Desativado  
    

## <a name="internet-explorer"></a>Internet Explorer  
Para obter mais informações, consulte [CSP de política - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) na documentação do Windows.  

- **Atualizações de zona do Internet Explorer restrito à barra de estado por meio de script**  
  Esta definição de política permite-lhe gerir se o script tem permissão para atualizar a barra de status na zona. 
  - *Se ativar esta definição de política*, script tem permissão para atualizar a barra de status.
  - *Se desabilitar ou não configurar esta definição de política*, script não tem permissão para atualizar a barra de status.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Predefinido**: Desativado

- **Zona de internet do Internet Explorer arrastar e soltar ou copiar e colar ficheiros**  
  Esta definição de política permite-lhe gerir se os utilizadores podem arrastar arquivos ou copiar e colar ficheiros de uma origem dentro da zona. Se ativar esta definição de política, os utilizadores podem arrastar arquivos ou copiar e colar ficheiros a partir desta zona automaticamente. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende arrastar ou copiar ficheiros a partir desta zona. Se desativar esta definição de política, os utilizadores são impedidos de arrastar arquivos ou copiar e colar ficheiros a partir desta zona. Se não configurar esta definição de política, os utilizadores podem arrastar arquivos ou copiar e colar ficheiros a partir desta zona automaticamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Predefinido**: Desativar

- **Componentes da habilitação do .NET Framework de zona restritos do Internet Explorer**    
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que não estejam assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados não assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados não assinados. Se desativar esta definição de política, o Internet Explorer não será executado componentes gerenciados não assinados. Se não configurar esta definição de política, o Internet Explorer não será executado componentes gerenciados não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Predefinido**: Desativar


- **Zona de computador local do Internet Explorer não execute antimalware controles Active X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Predefinido**: Desativado

- **Acesso da zona de internet do Internet Explorer para origens de dados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer pode acessar dados de outra zona de segurança com o Microsoft XML Parser (MSXML) ou ActiveX Data Objects (ADO). Se ativar esta definição de política, os utilizadores podem carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que uma página carregar na zona que utiliza o MSXML ou o ADO para acessar dados de outro site na zona. Se desativar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se não configurar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Predefinido**: Desativar  
  
- **Zona restrita do Internet Explorer arrastar o conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão na mesma janela. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores não é possível alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta definição de política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão na mesma janela. Os utilizadores não é possível alterar esta definição na caixa de diálogo Opções da Internet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Predefinido**: Desativado
  
- **Aviso de erro de correspondência do endereço de certificado do Internet Explorer**  
  Esta definição de política permite-lhe ativar o aviso de segurança de erro de correspondência de endereço do certificado. Quando esta definição de política é ativada, o usuário é avisado quando visita Web sites HTTP Secure (HTTPS) que presentes certificados emitidos para um endereço de outro Web site. Este aviso ajuda a impedir ataques de falsificação. Se ativar esta definição de política, o certificado endereço erro de correspondência de aviso sempre será exibido. Se desabilitar ou não configura esta definição de política, o usuário pode escolher se o aviso de erro de correspondência do endereço de certificado é apresentado (ao utilizar a página avançada no painel de controlo da Internet).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Predefinido**: Enabled 
  
- **Zona restrita do Internet Explorer menos sites com privilégios**  
  Esta definição de política permite-lhe gerir se sites da Web de zonas com menos privilégios, tais como sites da Internet, pode navegar para esta zona. Se ativar esta definição de política, Web sites de zonas com menos privilégios pode abrir novas janelas no ou navegue para esta zona. A zona de segurança serão executados sem a camada adicional de segurança que é fornecida pela proteção da funcionalidade de segurança de elevação de zona. Se selecionar a linha de comandos na caixa de lista pendente, é emitido um aviso ao utilizador que potencialmente perigoso navegação está prestes a ocorrer. Se desativar esta definição de política, é impedida a navegação possivelmente prejudicial. A funcionalidade de segurança do Internet Explorer está nesta zona conforme definido pela proteção de controlo de recursos de elevação de zona. Se não configurar esta definição de política, são impedidas as navegações possivelmente prejudiciais. A funcionalidade de segurança do Internet Explorer está nesta zona conforme definido pela proteção de controlo de recursos de elevação de zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Predefinido**: Desativar  
  
- **Downloads do Internet Explorer zona restritas automática linha de comandos para o ficheiro**  
  Esta definição de política determina se é pedido aos utilizadores para as transferências de ficheiros não iniciada pelo utilizador. Independentemente desta definição, os utilizadores irão receber caixas de diálogo de download de arquivo para downloads iniciada pelo utilizador. Se ativar esta definição, os utilizadores irão receber uma caixa de diálogo de download de arquivo para tentativas de transferência automática. Se desabilitar ou não configura esta definição, as transferências de ficheiros que não são iniciados pelo usuário são bloqueadas e os utilizadores verão a barra de notificação, em vez da caixa de diálogo de download do arquivo. Os utilizadores podem, em seguida, clicar a barra de notificação para permitir que o pedido de transferência de ficheiros.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Predefinido**: Desativado
  
- **Componentes da habilitação de .NET Framework zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que não são assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados não assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados não assinados. Se desativar esta definição de política, o Internet Explorer não irá executar componentes gerenciados não assinados. Se não configurar esta definição de política, o Internet Explorer será executado componentes gerenciados não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Predefinido**: Desativar 
  
- **Permitir que a zona de internet de Internet Explorer apenas aprovados domínios para usar controles do ActiveX tdc**  
  Esta definição de política controla se o utilizador pode executar o controle TDC ActiveX nos Web sites. Se ativar esta definição de política, o controle TDC ActiveX não será executado de Web sites nesta zona. Se desativar esta definição de política, o controle de TDC Active X será executado de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Predefinido**: Enabled 
  
- **Script de zona do Internet Explorer restrito iniciadas pelo windows**  
  Esta definição de política permite-lhe gerir restrições para janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Se ativar esta definição de política, não se aplicam a segurança de restrições do Windows nesta zona. A zona de segurança é executado sem a camada de segurança fornecida por esta funcionalidade adicional. Se desativar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows. Se não configurar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Predefinido**: Desativado 
  
- **Zona de internet do Internet Explorer incluir o caminho local, ao carregar ficheiros para o servidor**  
  Esta definição de política controla se as informações de caminho local são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se as informações de caminho local são enviadas, algumas informações podem inadvertidamente reveladas para o servidor. Por exemplo, os arquivos enviados a partir do ambiente de trabalho do usuário podem conter o nome de utilizador como parte do caminho. Se ativar esta definição de política, informações de caminho são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se desativar esta definição de política, informações de caminho são removidas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se não configurar esta definição de política, o usuário pode escolher se as informações de caminho são enviadas quando eles carregam um ficheiro através de um formulário HTML. Por predefinição, são enviadas informações de caminho.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Predefinido**: Desativado 
  
- **Internet Explorer desativar processos no modo protegido avançado**  
  Esta definição de política determina se Internet Explorer 11 utiliza os processos de 64 bits (para maior segurança) ou processos de 32 bits (para maior compatibilidade) quando em execução no modo protegido avançado em versões de 64 bits do Windows. Importante: Alguns controles ActiveX e barras de ferramentas poderão não estar disponíveis quando são utilizados os processos de 64 bits. Se ativar esta definição de política, o Internet Explorer 11 usará os processos de separador de 64 bits quando em execução no modo protegido avançado em versões de 64 bits do Windows. Se desativar esta definição de política, o Internet Explorer 11 usará os processos de separador de 32 bits quando em execução no modo protegido avançado em versões de 64 bits do Windows. Se não configurar esta definição de política, os utilizadores podem ativar esta funcionalidade ativada ou desativada com as definições do Internet Explorer. Esta funcionalidade está desativada por predefinição.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Predefinido**: Enabled 
  
- **Internet Explorer ignorar erros de certificado**  
  Esta definição de política impede que o utilizador a ignorar erros de certificado de Secure Sockets Layer/Transport Layer Security (SSL/TLS) que interrompem a navegação (como "expirada", "revogado" ou erros de "erro de correspondência do nome") no Internet Explorer. Se ativar esta definição de política, o utilizador não é possível continuar a navegar. Se desabilitar ou não configura esta definição de política, o utilizador pode optar por ignorar erros de certificado e continuar a navegar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Predefinido**: Desativado 
  
- **Carregamento de zona de internet do Internet Explorer de arquivos XAML**  
  Esta definição de política permite-lhe gerir o carregamento de ficheiros de de Extensible Application Markup Language (XAML). XAML é uma linguagem de marcação declarativa baseada em XML usada para criar interfaces do usuário avançadas e gráficos que tiram partido do Windows Presentation Foundation. Se ativar esta definição de política e defina a caixa de lista pendente para ativar, arquivos XAML são automaticamente carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se definir a caixa de lista pendente à linha de comandos, é pedido ao utilizador para carregar arquivos XAML. Se desativar esta definição de política, os arquivos XAML não são carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se não configurar esta definição de política, o usuário pode decidir se pretende carregar arquivos XAML no Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Predefinido**: Desativar 
  
- **Downloads de prompt automática do Internet Explorer internet zona para o ficheiro**  
  Esta definição de política determina se é pedido aos utilizadores para as transferências de ficheiros não iniciada pelo utilizador. Independentemente desta definição, os utilizadores irão receber caixas de diálogo de download de arquivo para downloads iniciada pelo utilizador. Se ativar esta definição, os utilizadores irão receber uma caixa de diálogo de download de arquivo para tentativas de transferência automática. Se desabilitar ou não configura esta definição, as transferências de ficheiros que não são iniciados pelo usuário são bloqueadas e os utilizadores verão a barra de notificação, em vez da caixa de diálogo de download do arquivo. Os utilizadores podem, em seguida, clicar a barra de notificação para permitir que o pedido de transferência de ficheiros.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Predefinido**: Desativado  
  
- **Aviso de segurança da zona para ficheiros potencialmente não seguros de restritos do Internet Explorer**  
  Esta definição de política controla se a mensagem de "Abrir ficheiro – Aviso de segurança" é apresentada quando o utilizador tenta abrir arquivos executáveis ou de outros ficheiros potencialmente não seguros (a partir de uma partilha de ficheiros à intranet com o Explorador de ficheiros, por exemplo). Se ativar esta definição de política e defina a caixa de lista pendente para ativar, abrir estes ficheiros sem um aviso de segurança. Se definir a caixa de lista pendente à linha de comandos, é apresentado um aviso de segurança antes de abrir os ficheiros. Se desativar esta definição de política, estes ficheiros não abrem. Se não configurar esta definição de política, o utilizador pode configurar como o computador lida com esses arquivos. Por predefinição, estes ficheiros estão bloqueados na zona restrita, ativada em zonas da Intranet e o computador Local e definidos para solicitar nas zonas Internet e confiáveis da.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer em várias filtro de scripts do site**  
  Esta política controla se o filtro de scripts de sites (XSS) irá detetar e prevenir injeções de script entre sites em Web sites nesta zona. Se ativar esta definição de política, o Filtro XSS está ativado para os sites desta zona e o Filtro XSS tenta bloquear injeções de script entre sites. Se desativar esta definição de política, o Filtro XSS está desativado para sites desta zona e o Internet Explorer permite injeções de script entre sites.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Predefinido**: Enabled 
  
- **Contingência de Internet Explorer para SSL3**  
  Esta definição de política permite-lhe bloquear uma contingência insegura para SSL 3.0. Quando esta política está ativada, Internet Explorer irá tentar ligar a sites usando o SSL 3.0 ou abaixo quando falha TLS 1.0 ou superior. Recomendamos que não permitir contingência insegura para evitar um ataque man-in-the-middle. Esta política não afeta os protocolos de segurança estão ativados. Se desativar esta política, são utilizadas as predefinições do sistema.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Predefinido**: Não existem sites  

- **Suporte de encriptação do Internet Explorer**  
  Esta definição de política permite-lhe desativar o suporte para o Transport Layer Security (TLS) 1.0, TLS 1.1, TLS 1.2, proteger o SSL (Sockets Layer) 2.0 ou SSL 3.0 no browser. TLS e SSL são protocolos que ajudam a proteger a comunicação entre o browser e o servidor de destino. Quando o navegador tenta definir uma comunicação protegida com o servidor de destino, o navegador e o servidor negociam qual protocolo e a versão a utilizar. O browser e o servidor tentam combinar uns dos outros, lista de protocolos suportados e as versões e selecionarem a correspondência das preferências. Se ativar esta definição de política, o navegador negocia ou não negociar um túnel de encriptação utilizando os métodos de encriptação que selecionou na lista pendente. Se desabilitar ou não configurar esta definição de política, o usuário pode selecionar qual encriptação suporta o método do navegador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Predefinido**: 2 itens:  Versão do TLS 1.1 e a versão do TLS 1.2  
  *Selecione a seta para baixo para apresentar as opções que pode selecionar para esta definição.*
  
- **Bloqueado ecrã inteligentes de zona de internet do Internet Explorer**  
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Predefinido**: Enabled 
  
- **Internet Explorer restrito a aplicativos de inicialização de zona e arquivos num iFrame**  
  Esta definição de política permite-lhe gerir se os aplicativos podem ser executados e arquivos podem ser transferidos a partir de uma referência IFRAME no HTML das páginas nesta zona. Se ativar esta definição de política, os utilizadores podem executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona. Se desativar esta definição de política, os utilizadores são impedidos de execução de aplicativos e o download de arquivos de IFRAMEs nas páginas nesta zona. Se não configurar esta definição de política, os utilizadores são impedidos de execução de aplicativos e o download de arquivos de IFRAMEs nas páginas nesta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Predefinido**: Desativar 
  
- **Internet Explorer ignore os avisos do SmartScreen sobre ficheiros invulgares**  
  Esta definição de política determina se o utilizador pode ignorar avisos do Filtro SmartScreen. O Filtro SmartScreen avisa o utilizador sobre ficheiros executáveis que usuários do Internet Explorer geralmente não transferirem a partir da Internet. Se ativar esta definição de política, os avisos do Filtro SmartScreen impedir o utilizador. Se desabilitar ou não configura esta definição de política, o utilizador pode ignorar avisos do Filtro SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Predefinido**: Desativado  
  
- **Bloqueador de pop-up de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se indesejados janelas de pop-up aparecem. Janelas de pop-up que foram abertas quando o utilizador final clica num link não são bloqueadas. Se ativar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer. Se desativar esta definição de política, janelas pop-up não são impedidas de aparecer. Se não configurar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Predefinido**: Ativar  
  
- **Internet Explorer processa a manipulação do MIME consistente**  
  Internet Explorer contém aos comportamentos binários dinâmicos: os componentes que encapsulam a funcionalidade específica para os elementos HTML ao qual estão anexadas. Esta definição de política de controlos se a definição de restrição de segurança de comportamento binário é impedida ou não permitida. Se ativar esta definição de política, são impedidos aos comportamentos binários para os processos de Explorador de ficheiros e o Internet Explorer. Se desativar esta definição de política, aos comportamentos binários são permitidos para os processos de Explorador de ficheiros e o Internet Explorer. Se não configurar esta definição de política, são impedidos aos comportamentos binários para os processos de Explorador de ficheiros e o Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Predefinido**: Enabled  
  
- **Permissões de java de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Predefinido**: Desativar o java  
    
  
- **Controles do Internet Explorer Active X no modo protegido**  
  Esta definição de política impede que os controles ActiveX em execução no modo protegido, quando o modo protegido avançado está ativado. Quando um utilizador tiver um controle ActiveX instalado que não é compatível com modo protegido avançado e um Web site tenta carregar o controle, o Internet Explorer notifica o utilizador e oferece a opção para executar o Web site no modo protegido regular. Esta definição de política desativa esta notificação e força todos os Web sites para executar no modo protegido avançado. Modo protegido avançado proporciona proteção adicional contra sites mal-intencionados utilizando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam, pelo menos, Windows 8, o modo protegido avançado também limita os locais do Internet Explorer pode ler a partir do Registro e o sistema de ficheiros. Quando o modo protegido avançado está ativado e um utilizador se depara com um Web site que tenta carregar um controle ActiveX que não é compatível com modo protegido avançado, o Internet Explorer notifica o utilizador e oferece a opção para desativar o modo protegido avançado para esse determinado site. Se ativar esta definição de política, o Internet Explorer não dar ao usuário a opção para desativar o modo protegido avançado. Todos os Web sites de modo protegido serão executado no modo protegido avançado. Se desabilitar ou não configura esta definição de política, o Internet Explorer notifica os utilizadores e fornece uma opção para executar Web sites com os controles ActiveX incompatíveis no modo protegido regular.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Predefinido**: Desativado  
  
- **Carregamento de zona restritos do Internet Explorer de arquivos XAML**  
  Esta definição de política permite-lhe gerir o carregamento de ficheiros de de Extensible Application Markup Language (XAML). XAML é uma linguagem de marcação declarativa baseada em XML usada para criar interfaces do usuário avançadas e gráficos que tiram partido do Windows Presentation Foundation. Se ativar esta definição de política e defina a caixa de lista pendente para ativar, arquivos XAML são automaticamente carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se definir a caixa de lista pendente à linha de comandos, é pedido ao utilizador para carregar arquivos XAML. Se desativar esta definição de política, os arquivos XAML não são carregados dentro do Internet Explorer. O utilizador não pode alterar este comportamento. Se não configurar esta definição de política, o usuário pode decidir se pretende carregar arquivos XAML no Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Predefinido**: Desativar  
  
- **Restrições de segurança de janela com script de processos do Internet Explorer**  
  Internet Explorer permite que os scripts por meio de programação abrir, redimensionar e reposicionar windows de vários tipos. A funcionalidade de segurança de restrições de janela restringe janelas pop-ups e proíbe scripts do windows na qual as barras de título e o estado não são visíveis para o utilizador ou oculte o título dos outros Windows e as barras de estado de exibição. Se ativar esta definição de política, com scripts do windows são restrito para todos os processos. Se desabilitar ou não configura esta definição de política, com scripts do windows não são restrito.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Predefinido**: Enabled   
  
- **Zona restrita do Internet Explorer executar Active X controlos e plug-ins**  
  Esta definição de política permite-lhe gerir se os controles ActiveX e plug-ins pode executar em páginas da zona especificada. Se ativar esta definição de política, controlos e plug-ins podem ser executados sem intervenção do utilizador. Se tiver selecionado a linha de comandos na caixa de lista pendente, os usuários são mais freqüentes para escolher se pretende permitir que os controles ou plug-in para ser executado. Se desativar esta definição de política, controlos e plug-ins são impedidos de execução. Se não configurar esta definição de política, controlos e plug-ins são impedidos de execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Predefinido**: Desativar  
  
- **Script de zona de Internet Explorer restrito que Active X controla marcados como seguro para scripting**  
  Esta definição de política permite-lhe gerir se um controle ActiveX marcados como seguro para scripting pode interagir com um script. Se ativar esta definição de política, a interação de script pode ocorrer automaticamente sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir a interação de script. Se desativar esta definição de política, a interação de script é impedida de ocorrer. Se não configurar esta definição de política, a interação de script é impedida de ocorrer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Predefinido**: Desativar  
  
- **Opções de início de sessão de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir as definições para as opções de início de sessão. Se ativar esta definição de política, pode escolher entre o início de sessão seguintes opções. 
  - *Anónimo* - a utilizar anónimo início de sessão para desative a autenticação HTTP e utilizar a conta de convidado apenas para o protocolo Common Internet File System (CIFS). 
  - *Linha de comandos* -aviso de utilização para o nome de utilizador e palavra-passe para os utilizadores da consulta de IDs de utilizador e palavras-passe. Depois de um utilizador é consultado, estes valores podem ser utilizados em automaticamente para o resto da sessão. 
  - *Início de sessão automático em apenas na zona de Intranet* -Utilize esta opção para os utilizadores da consulta para IDs de utilizador e palavras-passe noutras zonas. Depois de um utilizador é consultado, estes valores podem ser utilizados em automaticamente para o resto da sessão. 
  - *Automática inicie a sessão com o nome do usuário atual e a palavra-passe*-Utilize esta opção para tentar iniciar sessão com a resposta de desafio do Windows NT (também conhecido como autenticação de NTLM). Se o servidor suportar a resposta de desafio do Windows NT, o início de sessão utiliza nome de utilizador de rede do utilizador e palavra-passe para iniciar sessão. Se o servidor não suporta a resposta de desafio do Windows NT, o utilizador é consultado para fornecer o nome de utilizador e palavra-passe. 

  Se desativar esta definição de política, o início de sessão está definido como *automático iniciar sessão apenas na zona de Intranet*. Se não configurar esta definição de política, o início de sessão está definido como *Prompt* nome de utilizador e palavra-passe.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Predefinido**: Anónima  
  
- **Internet Explorer fidedigna inicializar de zona e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Predefinido**: Desativar  
  
- **Revogação de certificados de servidor de verificação do Internet Explorer**  
  Esta definição de política permite-lhe gerir se o Internet Explorer irá verificar o estado de revogação de certificados dos servidores. Os certificados são revogados quando forem comprometidos ou já não são válidas e esta opção protege os usuários de submeter dados confidenciais a um site que pode ser fraudulentos ou não segura. Se ativar esta definição de política, Internet Explorer irá verificar se os certificados de servidor tiverem sido revogados. Se desativar esta definição de política, o Internet Explorer não verificar os certificados de servidor para ver se eles foram revogados. Se não configurar esta definição de política, o Internet Explorer não verificar os certificados de servidor para ver se eles foram revogados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Predefinido**: Enabled 
  
- **Zona de internet do Internet Explorer menos sites com privilégios**  
  Esta definição de política permite-lhe gerir se sites da Web de zonas com menos privilégios, tais como Sites restritos, pode navegar para esta zona. Se ativar esta definição de política, Web sites de zonas com menos privilégios pode abrir novas janelas no ou navegue para esta zona. A zona de segurança serão executados sem a camada adicional de segurança que é fornecida pela proteção da funcionalidade de segurança de elevação de zona. Se selecionar a linha de comandos na caixa de lista pendente, é emitido um aviso ao utilizador que potencialmente perigoso navegação está prestes a ocorrer. Se desativar esta definição de política, são impedidas as navegações possivelmente prejudiciais. A funcionalidade de segurança do Internet Explorer está nesta zona conforme definido pela proteção de controlo de recursos de elevação de zona. Se não configurar esta definição de política, Web sites de zonas com menos privilégios pode abrir novas janelas no ou navegue para esta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Predefinido**: Desativar  
  
- **Downloads do ficheiro de zona restritos do Internet Explorer**  
  Esta definição de política permite-lhe gerir se downloads de arquivos são permitidos da zona. Esta opção é determinada pela zona da página com a ligação que faz com que o download, não a partir do qual o ficheiro é entregue de zona. Se ativar esta definição de política, os ficheiros podem ser baixados da zona. Se desativar esta definição de política, os ficheiros são impedidos de que está a ser transferido a partir da zona. Se não configurar esta definição de política, os ficheiros são impedidos de que está a ser transferido a partir da zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer executar componentes do .NET Framework baseia-se assinado com Authenticode**  
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que estão assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados assinados. Se desativar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados. Se não configurar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Predefinido**: Desativar  
  
- **Impedir o Internet Explorer por instalação de utilizador de controles de Active X**  
  Esta definição de política permite-lhe impedir a instalação de controles ActiveX numa base por utilizador. Se ativar esta definição de política, os controles ActiveX não podem ser instalados numa base por utilizador. Se desabilitar ou não configura esta definição de política, os controles ActiveX podem ser instalados numa base por utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Predefinido**: Enabled  
  
- **Impedir o Internet Explorer gerir o Filtro SmartScreen**  
  Esta definição de política impede que o utilizador gira o Filtro SmartScreen, que avisa o usuário se o Web site que visitar é conhecido por fraudulentas tentativas recolher informações pessoais por meio de "phishing", ou que é conhecido por hospedar malware. Se ativar esta definição de política, não é pedido ao utilizador para o Filtro SmartScreen. Todos os endereços de Web site que não estão nos filtros permitem que lista são automaticamente enviados à Microsoft sem pedir intervenção do utilizador. Se desabilitar ou não configura esta definição de política, é pedido ao utilizador que decida se pretende ativar o Filtro SmartScreen durante a experiência de primeira execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Predefinido**: Ativar  
  
- **Internet Explorer processa a funcionalidade de segurança de farejamento MIME**  
  Esta definição de política determina se a detecção de MIME do Internet Explorer irá impedir que a promoção de um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se ativar esta definição de política, a detecção de MIME nunca promover um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se desativar esta definição de política, os processos do Internet Explorer permitirá uma pesquisa MIME promover um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se não configurar esta definição de política, a detecção de MIME nunca promover um ficheiro de um tipo para um tipo de ficheiro mais perigoso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Predefinido**: Enabled  
  
- **Transferência de zona restritos do Internet Explorer assinado controles Active X**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX assinados de uma página na zona. Se ativar esta política, os utilizadores podem transferir assinados controles sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido. Se desativar a definição de política, não é possível transferir controles assinados. Se não configurar esta definição de política, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Predefinido**: Desativar  
  
- **Preenchimento automático de Internet Explorer**  
  Esta funcionalidade de conclusão automática pode Lembre-se e sugere nomes de utilizador e palavras-passe em formulários. Se ativar esta definição, o utilizador não é possível alterar "nome de utilizador e palavras-passe em formulários" ou "Avisar-me para guardar palavras-passe". A funcionalidade completa de automática para nomes de utilizador e palavras-passe em formulários é ativada. Precisa decidir se pretende selecionar "Avisar-me para guardar palavras-passe". Se desativar esta definição o utilizador não é possível alterar "nome de utilizador e palavras-passe em formulários" ou "Avisar-me para guardar palavras-passe". A funcionalidade completa de automática para nomes de utilizador e palavras-passe em formulários está desativada. O utilizador também não é possível optar por ser-lhe pedido para guardar palavras-passe. Se não configurar esta definição, o utilizador tem a liberdade de Ativando automática concluída para o nome de utilizador e palavras-passe em formulários e a opção de solicitar a guardar palavras-passe. Para apresentar esta opção, os utilizadores abrir a caixa de diálogo Opções da Internet, clique no separador de conteúdo e clique no botão configurações.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Predefinido**: Desativado  
  
- **Zona de internet do Internet Explorer permitir VBscript executar**  
  Esta definição de política permite-lhe decidir se VBScript pode ser executado nas páginas em horários específicos do Internet Explorer. As opções incluem: 
  - *Ativar* -VBScript é executado nas páginas em horários específicos, sem qualquer interação do utilizador. 
  - *Linha de comandos* -funcionários-lhe pedidos se pretende permitir que o VBScript executar na zona. 
  - *Desativar* -VBScript é impedido de executar na zona. Se desativar ou não configurar esta definição de política, o VBScript é executado sem qualquer interação na zona especificada.    

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Predefinido**: Desativar  
  
- **Internet Explorer, permitir que a zona restritas apenas aprovados domínios usar controles de Active X tdc**  
  Esta definição de política controla se o utilizador pode executar o controle TDC ActiveX nos Web sites. Se ativar esta definição de política, o controle TDC ActiveX não será executado de Web sites nesta zona. Se desativar esta definição de política, o controle de TDC Active X será executado de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Predefinido**: Enabled  
  
- **Zona de confiança do Internet Explorer não são executados antimalware controles Active X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Predefinido**: Desativado 
  
- **Permissões do java de zona de computador local do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para segurança média.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Predefinido**: Desativar o java 
  
- **Zona de intranet do Internet Explorer não execute antimalware controles Active X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Predefinido**: Desativado  

- **Scriptlets de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir se o utilizador pode executar scriptlets. Se ativar esta definição de política, o utilizador pode executar scriptlets. Se desativar esta definição de política, o utilizador não é possível executar scriptlets. Se não configurar esta definição de política, o utilizador pode ativar ou desativar scriptlets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Predefinido**: Desativado  
  
- **Barra de notificação de processos do Internet Explorer**  
  Esta definição de política permite-lhe gerir se a barra de notificação é apresentada para processos do Internet Explorer, quando instala ficheiros ou de código é restrita. Por predefinição, a barra de notificação é apresentada para processos do Internet Explorer. Se ativar esta definição de política, apresenta a barra de notificação para os processos do Internet Explorer. Se desativar esta definição de política, a barra de notificação não ser apresentada para processos do Internet Explorer. Se não configurar esta definição de política, não exibe a barra de notificação para processos do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Predefinido**: Enabled  
  
- **Transferência de zona de internet do Internet Explorer assinado controles ActiveX**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX assinados de uma página na zona. Se ativar esta política, os utilizadores podem transferir assinados controles sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido. Se desativar a definição de política, não é possível transferir controles assinados. Se não configurar esta definição de política, os utilizadores são consultados se pretende transferir controles assinados pelos publicadores que não são confiáveis. Código assinado por fabricantes fidedignos silenciosamente é transferido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Predefinido**: Desativar  
  
- **Ecrã de inteligente de zona restritas do Internet Explorer**  
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer remover executar este botão de tempo para controles de Active X desatualizados**  
  Esta definição de política permite-lhe impedir que os utilizadores visualizem o botão "Executar agora" e a execução de controles específicos de ActiveX desatualizados no Internet Explorer. Se ativar esta definição de política, os utilizadores não verão o botão "Executar agora" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Se desabilitar ou não configura esta definição de política, os utilizadores verão o botão "Executar agora" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Clicar neste botão permite que o utilizador executar uma vez o controle ActiveX desatualizado. Para obter mais informações, consulte "Desatualizado os controles ActiveX" na Biblioteca TechNet do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Predefinido**: Enabled 
  
- **Aplicativos de inicialização de zona de internet do Internet Explorer e arquivos num iframe**  
  Esta definição de política permite-lhe gerir se os aplicativos podem ser executados e arquivos podem ser transferidos a partir de uma referência IFRAME no HTML das páginas nesta zona. Se ativar esta definição de política, os utilizadores podem executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona. Se desativar esta definição de política, os utilizadores são impedidos de execução de aplicativos e o download de arquivos de IFRAMEs nas páginas nesta zona. Se não configurar esta definição de política, os utilizadores são consultados para escolher se pretende executar aplicações e transferir os ficheiros do IFRAMEs nas páginas nesta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Predefinido**: Desativar 
  
- **Zona restrita do Internet Explorer navegue windows e os quadros em diferentes domínios**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão no windows diferentes. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e de destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Predefinido**: Desativar  
  
- **Ecrã inteligente de zona de internet do Internet Explorer**  
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer é bloqueado por permissões de java da zona de confiança**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Predefinido**: Desativar o java 
  
- **Internet Explorer verificar assinaturas em programas baixados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer verifica a existência de assinaturas digitais (que identifica o publicador de software assinado e verifica se ainda não foram modificado ou adulterado) em computadores de usuários antes de transferir os programas executáveis. Se ativar esta definição de política, o Internet Explorer verificar as assinaturas digitais de programas executáveis e apresentar as suas identidades antes de transferi-los para computadores de usuários. Se desativar esta definição de política, o Internet Explorer não verificar as assinaturas digitais de programas executáveis ou visualizar suas identidades antes de transferi-los para computadores de usuários. Se não configurar esta política, o Internet Explorer não verificar as assinaturas digitais de programas executáveis ou visualizar suas identidades antes de transferi-los para computadores de usuários.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer restrito a zona de script de controles de navegador da web**  
  Esta definição de política determina se uma página pode controlar o embedded WebBrowser controles por meio de script. Se ativar esta definição de política, é permitido o acesso de script para o controle WebBrowser. Se desativar esta definição de política, não é permitido o acesso de script para o controle WebBrowser. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o acesso de script para o controle WebBrowser. Por predefinição, o acesso de script para o controle WebBrowser é permitido apenas no computador Local e zonas da Intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Predefinido**: Desativado  
  
- **Filtro de scripts do site em várias de zona restrita do Internet Explorer**  
  Esta política controla se o filtro de scripts de sites (XSS) irá detetar e prevenir injeções de script entre sites em Web sites nesta zona. Se ativar esta definição de política, o Filtro XSS está ativado para os sites desta zona e o Filtro XSS tenta bloquear injeções de script entre sites. Se desativar esta definição de política, o Filtro XSS está desativado para sites desta zona e o Internet Explorer permite injeções de script entre sites.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Predefinido**: Enabled  
  
- **Zona restrita do Internet Explorer binária e comportamentos de script**  
  Esta definição de política permite-lhe gerir comportamentos de binários e de script dinâmicos: os componentes que encapsulam a funcionalidade específica para elementos HTML para o qual foram anexados. Se ativar esta definição de política, comportamentos de binários e de script estão disponíveis. Se selecionar administrador aprovado na caixa de lista pendente, apenas os comportamentos listados nos comportamentos de aprovação de administrador em diretiva de restrição de segurança de comportamentos binários estão disponíveis. Se desativar esta definição de política, comportamentos de binários e de script não estão disponíveis, a menos que os aplicativos implementaram um Gestor de segurança personalizada. Se não configurar esta definição de política, comportamentos de binários e de script não estão disponíveis, a menos que os aplicativos implementaram um Gestor de segurança personalizada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Predefinido**: Desativar  
  
- **Verificação de definições de segurança do Internet Explorer**  
  Esta definição de política desativa a funcionalidade de verificação de definições de segurança, que verifica as definições de segurança do Internet Explorer para determinar quando as definições do Internet Explorer de colocar em risco. Se ativar esta definição de política, a funcionalidade está desativada. Se desabilitar ou não configura esta definição de política, a funcionalidade está ativada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Predefinido**: Enabled  
  
- **Aviso de segurança do Internet Explorer internet zona para ficheiros potencialmente não seguros**  
  Esta definição de política controla se a mensagem de "Abrir ficheiro – Aviso de segurança" é apresentada quando o utilizador tenta abrir arquivos executáveis ou de outros ficheiros potencialmente não seguros (a partir de uma partilha de ficheiros à intranet com o Explorador de ficheiros, por exemplo). Se ativar esta definição de política e defina a caixa de lista pendente para ativar, abrir estes ficheiros sem um aviso de segurança. Se definir a caixa de lista pendente à linha de comandos, é apresentado um aviso de segurança antes de abrir os ficheiros. Se desativar esta definição de política, estes ficheiros não abrem. Se não configurar esta definição de política, o utilizador pode configurar como o computador lida com esses arquivos. Por predefinição, estes ficheiros estão bloqueados na zona restrita, ativada em zonas da Intranet e o computador Local e definidos para solicitar nas zonas Internet e confiáveis da.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Predefinido**: Mensagem  
  
- **Permissões do java de zona de intranet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para segurança média.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Predefinido**: Segurança alta 
  
- **Controles do Internet Explorer bloquear desatualizado Active X**   
  Esta definição de política determina se os blocos do Internet Explorer específicos desatualizados controles ActiveX. Os controles ActiveX desatualizados nunca são bloqueados na zona de Intranet. Se ativar esta definição de política, Internet Explorer para bloquear os controles ActiveX desatualizados. Se desabilitar ou não configura esta definição de política, o Internet Explorer continua a bloquear os controles ActiveX desatualizados específicos. Para obter mais informações, consulte "Desatualizado os controles ActiveX" na Biblioteca TechNet do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Predefinido**: Enabled  
  
- **Bloqueador de pop-up de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir se indesejados janelas de pop-up aparecem. Janelas de pop-up que foram abertas quando o utilizador final clica num link não são bloqueadas. Se ativar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer. Se desativar esta definição de política, janelas pop-up não são impedidas de aparecer. Se não configurar esta definição de política, mais janelas de pop-up indesejadas são impedidas de aparecer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Predefinido**: Ativar  
  
- **Restrição de segurança de protocolo do Internet Explorer processos MK**  
  A definição de política de restrição de segurança do protocolo MK reduz a área de superfície de ataque ao impedir que o protocolo MK. Recursos alojados no protocolo MK irão falhar. Se ativar esta definição de política, o protocolo MK é impedido de Explorador de ficheiros e o Internet Explorer e recursos alojados no protocolo MK irão falhar. Se desativar esta definição de política, as aplicações podem utilizar o API ao protocolo MK. Recursos alojados no protocolo MK irão funcionar para os processos de Explorador de ficheiros e o Internet Explorer. Se não configurar esta definição de política, o protocolo MK é impedido de Explorador de ficheiros e o Internet Explorer e recursos alojados no protocolo MK irão falhar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Predefinido**: Enabled  
  
- **Permissões de java de zona fidedignos do Internet Explorer**   
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para baixa segurança.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Predefinido**: Segurança alta  
  
- **Internet Explorer restrito a zona de scripts de miniaplicativos java**  
  Esta definição de política permite-lhe gerir se miniaplicativos são expostos a scripts dentro da zona. Se ativar esta definição de política, os scripts podem aceder miniaplicativos automaticamente sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que scripts aceder aos miniaplicativos. Se desativar esta definição de política, os scripts são impedidos de aceder miniaplicativos. Se não configurar esta definição de política, os scripts são impedidos de aceder miniaplicativos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Predefinido**: Desativar  
  
- **Bloqueado de permissões de java de zona restritas do Internet Explorer**   
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Predefinido**: Desativar o java 
  
- **Permitir que a zona de internet de Internet Explorer apenas aprovados domínios para usar controles ActiveX**   
  Esta definição de política controla se é pedido ao utilizador para permitir que os controles ActiveX ser executada em Web sites que não seja o site no qual instalado o controle ActiveX. Se ativar esta definição de política, é pedido ao utilizador antes de controles ActiveX podem ser executados de Web sites nesta zona. O utilizador pode optar por permitir que o controle ser executada a partir do site atual ou de todos os sites. Se desativar esta definição de política, o utilizador não vê a linha de comandos da ActiveX por site e controles ActiveX podem ser executados de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer incluem todos os caminhos de rede**  
  Internet Explorer incluem todos os caminhos de rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Predefinido**: Desativado 
  
- **Modo protegido de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe ativar o modo protegido. Modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo as localizações que o Internet Explorer pode gravar no Registro e o sistema de ficheiros. Se ativar esta definição de política, o modo protegido é ativado. O utilizador não é possível desativar o modo protegido. Se desativar esta definição de política, o modo protegido é desativado. O utilizador não é possível ativar o modo protegido. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o modo protegido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Predefinido**: Ativar 
  
- **Inicializar a zona de internet do Internet Explorer e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Predefinido**: Desativar 
  
- **Bloqueado SmartScreen zona restritos do Internet Explorer**   
  Esta definição de política de controlos se o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen verifica páginas nesta zona relativamente a conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não faça análises páginas nesta zona relativamente a conteúdo malicioso. Se não configurar esta definição de política, o usuário pode escolher se o Filtro SmartScreen analisa páginas nesta zona relativamente a conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o filtro de Phishing analisa páginas nesta zona relativamente a conteúdo malicioso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Predefinido**: Enabled  
  
- **Deteção de falhas do Internet Explorer**  
  Esta definição de política permite-lhe gerir a funcionalidade de deteção de falhas de gestão do suplemento. Se ativar esta definição de política, uma falha no Internet Explorer exibirão comportamento encontrado no Windows XP Professional Service Pack 1 e em versões anteriores, ou seja, para invocar o relatório de erros do Windows. Todas as definições de política para o relatório de erros do Windows continuam a aplicar. Se desabilitar ou não configura esta definição de política, a funcionalidade de deteção de falhas para a gestão de suplemento é funcional.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Predefinido**: Desativado  
  
- **Permissões do java de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, a permissão esteja definida para alta segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Predefinido**: Desativar o java  
  
- **Scripting ativo do Internet Explorer restrito zona**  
  Esta definição de política permite-lhe gerir se o código de script nas páginas na zona é executado. Se ativar esta definição de política, o código de script nas páginas na zona pode ser executado automaticamente. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o código de script nas páginas na zona para executar. Se desativar esta definição de política, o código de script em páginas na zona é impedido de execução. Se não configurar esta definição de política, o código de script nas páginas na zona é impedido de execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Predefinido**: Desativar  
  
- **Opções de início de sessão da zona de internet de Internet Explorer**  
  Esta definição de política permite-lhe gerir as definições para as opções de início de sessão. Se ativar esta definição de política, pode escolher entre o início de sessão seguintes opções. Logon anônimo desative a autenticação HTTP e a utilização de convidado conta apenas para o protocolo Common Internet File System (CIFS). Solicitar nome de utilizador e palavra-passe para os utilizadores da consulta para IDs de utilizador e palavras-passe. Depois de um utilizador é consultado, estes valores podem ser utilizados em silenciosamente durante o restante período da sessão. Registo automático em apenas na zona de Intranet para os utilizadores da consulta para IDs de utilizador e palavras-passe noutras zonas. Depois de um utilizador é consultado, estes valores podem ser utilizados em automaticamente para o resto da sessão. Automática inicie sessão com o nome de utilizador atual e a palavra-passe para tentar log sobre como utilizar a resposta de desafio do Windows NT (também conhecido como autenticação de NTLM). Se o servidor suportar a resposta de desafio de Windows NT, o início de sessão utiliza nome de utilizador de rede do utilizador e palavra-passe para iniciar sessão. Se o servidor não suporta a resposta de desafio do Windows NT, o utilizador é consultado para fornecer o nome de utilizador e palavra-passe. Se desativar esta definição de política, início de sessão está definida como registo automático ativado, apenas na zona de Intranet. Se não configurar esta definição de política, o início de sessão está definida como o início de sessão automático numa zona de Intranet apenas em.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Predefinido**: Mensagem  
  
- **Zona restrita do Internet Explorer permitir vbscript executar**   
  Esta definição de política permite-lhe gerir se o VBScript possa ser executado nas páginas da zona especificada no Internet Explorer. Se selecionou ativar na caixa de lista pendente, o VBScript pode ser executados sem intervenção do utilizador. Se tiver selecionado a linha de comandos na caixa de lista pendente, é pedido aos utilizadores escolher se pretende permitir que o VBScript seja executado. Se tiver selecionado o desativar a na caixa de lista pendente, o VBScript é impedido de execução. Se não configurar ou desativar esta definição de política, o VBScript é impedido de execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer arraste conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão no windows diferentes. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e de destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Predefinido**: Desativado 
  
- **Inicializar a zona de intranet do Internet Explorer e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Predefinido**: Desativar 
  
- **Inclusões de download do Internet Explorer**  
  Esta definição de política impede que o utilizador ter de inclusões (anexos de ficheiros) transferido a partir de um feed para o computador do usuário. Se ativar esta definição de política, o utilizador não é possível definir o motor de sincronização do Feed para transferir um bastidor através da página de propriedades de Feed. Um desenvolvedor não é possível alterar a definição de transferência através das APIs do Feed. Se desabilitar ou não configura esta definição de política, o utilizador pode definir o motor de sincronização do Feed para transferir um bastidor através da página de propriedades de Feed. Um desenvolvedor pode alterar a definição de transferência através das APIs do Feed.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Predefinido**: Desativado  
  
- **Controles sem assinatura do Active X de transferência de zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando proveniente de uma zona não fidedigna. Se ativar esta definição de política, os utilizadores podem executar controles sem assinatura sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o controle não assinado executar. Se desativar esta definição de política, os utilizadores não é possível executar controles sem assinatura. Se não configurar esta definição de política, os utilizadores não é possível executar controles sem assinatura.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer arrastar o conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando proveniente de uma zona não fidedigna. Se ativar esta definição de política, os utilizadores podem executar controles sem assinatura sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o controle não assinado executar. Se desativar esta definição de política, os utilizadores não é possível executar controles sem assinatura. Se não configurar esta definição de política, os utilizadores não é possível executar controles sem assinatura.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Predefinido**: Desativado  
  
- **Processos do Internet Explorer restringem a instalação do Active X**   
  Esta definição de política permite que os aplicativos hospedando o controle de navegador da Web bloquear a pedir a confirmação automática de instalação do controle ActiveX. Se ativar esta definição de política, o controle do navegador da Web irá bloquear a pedir a confirmação automática da instalação de controle do ActiveX para todos os processos. Se desabilitar ou não configura esta definição de política, o controle de navegador da Web não bloqueará a pedir a confirmação automática da instalação de controle do ActiveX para todos os processos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Predefinido**: Enabled  
  
- **Scriptlets de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se o utilizador pode executar scriptlets. Se ativar esta definição de política, o utilizador pode executar scriptlets. Se desativar esta definição de política, o utilizador não é possível executar scriptlets. Se não configurar esta definição de política, o utilizador pode ativar ou desativar scriptlets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Predefinido**: Desativar  
  
- **Zona restrita do Internet Explorer arrastar e soltar ou copiar e colar ficheiros**  
  Esta definição de política permite-lhe gerir se os utilizadores podem arrastar arquivos ou copiar e colar ficheiros de uma origem dentro da zona. Se ativar esta definição de política, os utilizadores podem arrastar arquivos ou copiar e colar ficheiros a partir desta zona automaticamente. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende arrastar ou copiar ficheiros a partir desta zona. Se desativar esta definição de política, os utilizadores são impedidos de arrastar arquivos ou copiar e colar ficheiros a partir desta zona. Se não configurar esta definição de política, os utilizadores são consultados para escolher se pretende arrastar ou copiar ficheiros a partir desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Predefinido**: Desativar  
  
- **Software do Internet Explorer quando a assinatura é inválida**  
  Esta definição de política permite-lhe gerir se software, como controles ActiveX e transferências de ficheiros, pode ser instalado ou executado pelo utilizador, mesmo que a assinatura é inválida. Uma assinatura inválida pode indicar que alguém tenha adulterado o ficheiro. Se ativar esta definição de política, é pedido aos utilizadores para instalar ou executar ficheiros com uma assinatura inválida. Se desativar esta definição de política, os utilizadores não é possível executar ou instalar ficheiros com uma assinatura inválida. Se não configurar esta política, os utilizadores podem optar por executar ou instalar ficheiros com uma assinatura inválida.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Predefinido**: Desativado  
  
- **Copiar de zona do Internet Explorer restrito e colar por meio de script**  
  Esta definição de política permite-lhe gerir se scripts podem realizar uma operação de área de transferência (por exemplo, as ações cortar, copiar e colar) numa determinada região. Se ativar esta definição de política, um script pode realizar uma operação de área de transferência. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados sobre a execução de operações de área de transferência. Se desativar esta definição de política, um script não é possível efetuar uma operação de área de transferência. Se não configurar esta definição de política, um script não é possível efetuar uma operação de área de transferência.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Predefinido**: Desativar  
  
- **Zona restrita do Internet Explorer arraste conteúdo de diferentes domínios no windows**  
  Esta definição de política permite-lhe definir as opções de arrastar o conteúdo de um domínio para um domínio diferente quando a origem e destino estão no windows diferentes. Se ativar esta definição de política e clique em ativar, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. Se ativar esta definição de política e clique em desativar, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e de destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição. No Internet Explorer 10, se desativar esta definição de política ou não configurá-lo, os utilizadores não é possível arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores podem alterar esta definição na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não configurá-lo, os utilizadores podem arrastar conteúdo de um domínio para outro domínio quando a origem e destino estão no windows diferentes. Os utilizadores não é possível alterar esta definição.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Predefinido**: Desativado  
  
- **Usuários do Internet Explorer, adicionar sites**  
  Impede que os utilizadores de adicionar ou remover sites de zonas de segurança. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, as definições de gestão do site para zonas de segurança estão desativadas. (Para ver a gestão de site as definições para as zonas de segurança, na caixa de diálogo Opções da Internet, clique no separador de segurança em, em seguida, clique no botão de Sites.) Se desativar esta política ou não configurá-lo, os usuários podem adicionar sites da Web ou remover sites de zonas de Sites confiáveis e Sites restritos e altere as definições para a zona de Local Intranet. Esta política impede os utilizadores alterem as definições de gestão do site para zonas de segurança estabelecidas pelo administrador. Nota: A política "Desativar a página de segurança" (localizada no painel de controlo do administrativos\Componentes Windows\Internet Explorer\Painel de \User Configuration\Administrative), que remove a guia de segurança a partir da interface, tem precedência sobre esta política. Se estiver ativada, esta política é ignorada. Além disso, consulte o "zonas de segurança: Utilizar apenas as definições de máquina"política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Predefinido**: Desativado  
  
- **Script de zona de internet do Internet Explorer iniciadas pelo windows**  
  Esta definição de política permite-lhe gerir restrições para janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Se ativar esta definição de política, não se aplicam a segurança de restrições do Windows nesta zona. A zona de segurança é executado sem a camada de segurança fornecida por esta funcionalidade adicional. Se desativar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows. Se não configurar esta definição de política, não é possível executar ações prejudiciais possíveis contidas em janelas de pop-up iniciadas por script e do windows que incluem as barras de título e o estado. Esta funcionalidade de segurança do Internet Explorer é nesta zona conforme ditado pela definição para o processo de controlo do recurso incluído num script restrições de segurança do Windows.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Predefinido**: Desativado  
  
- **As zonas de segurança do Internet Explorer utilizam apenas as definições de máquina**  
  Aplica-se de informações da zona de segurança para todos os utilizadores do mesmo computador. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, as alterações que faz com que o utilizador a uma zona de segurança serão aplicada a todos os utilizadores do computador. Se desativar esta política ou não configurá-lo, os usuários do mesmo computador podem estabelecer suas próprias definições de zona de segurança. Utilize esta política para garantir que as definições de zona de segurança se aplicam de forma uniforme no mesmo computador e não variam de usuário a usuário. Além disso, consulte o "zonas de segurança: não permitir que os usuários alterem as políticas de" política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer é bloqueado por permissões de java de zona de computador local**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Predefinido**: Desativar o java 
  
- **Zona restrita do Internet Explorer não execute antimalware controles Active X**   
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Predefinido**: Desativado  
  
- **Zona restrita do Internet Explorer executar componentes da habilitação do .NET Framework assinado com authenticode**  
  Esta definição de política permite-lhe gerir se os componentes do .NET Framework que estão assinados com Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controles gerenciados referenciados a partir de uma marca object e executáveis gerenciados referenciados a partir de uma ligação. Se ativar esta definição de política, o Internet Explorer será executado componentes gerenciados assinados. Se selecionar a linha de comandos na caixa de lista pendente, o Internet Explorer pedirá ao utilizador para determinar se deve executar componentes gerenciados assinados. Se desativar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados. Se não configurar esta definição de política, o Internet Explorer não irá executar componentes gerenciados assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Predefinido**: Desativar  
  
- **Acesso de zona de restrito de Internet Explorer para origens de dados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer pode acessar dados de outra zona de segurança com o Microsoft XML Parser (MSXML) ou ActiveX Data Objects (ADO). Se ativar esta definição de política, os utilizadores podem carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que uma página carregar na zona que utiliza o MSXML ou o ADO para acessar dados de outro site na zona. Se desativar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona. Se não configurar esta definição de política, os utilizadores não é possível carregar uma página na zona que utiliza o MSXML ou o ADO para acessar dados a partir de outro site na zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Predefinido**: Desativar 
  
- **Zona de internet do Internet Explorer não são executados antimalware controles ActiveX**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware controles ActiveX, para verificar se o que estão seguras carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verifique com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa de antimalware para ver se é segura criar uma instância do controle ActiveX. Os utilizadores podem ativar esse comportamento ou desativar, utilizando as definições de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Predefinido**: Desativado  
  
- **Copiar de zona de internet do Internet Explorer e colar por meio de script**  
  Esta definição de política permite-lhe gerir se scripts podem realizar uma operação de área de transferência (por exemplo, as ações cortar, copiar e colar) numa determinada região. Se ativar esta definição de política, um script pode realizar uma operação de área de transferência. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados sobre a execução de operações de área de transferência. Se desativar esta definição de política, um script não é possível efetuar uma operação de área de transferência. Se não configurar esta definição de política, um script pode realizar uma operação de área de transferência.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Predefinido**: Desativar  
  
- **Internet Explorer utilizar o serviço do instalador do Active X**  
  Esta definição de política permite-lhe especificar como os controles ActiveX são instalados. Se ativar esta definição de política, os controles ActiveX são instalados apenas se o ActiveX Installer Service está presente e não foi configurado para permitir a instalação de controles ActiveX. Se desabilitar ou não configura esta definição de política, os controles ActiveX, incluindo controlos por utilizador, são instalados através do processo de instalação padrão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Predefinido**: Enabled  
  
- **Proteção contra elevação de zona de processos do Internet Explorer**  
  Internet Explorer coloca restrições em cada página da Web é aberto. As restrições são dependentes tanto a localização da página da Web (Internet, Intranet, zona de computador Local e assim por diante). Por exemplo, páginas da Web no computador local têm as restrições de segurança menor e encontram-se na zona de computador Local, fazer a segurança do computador Local zona principal alvo para que usuários mal-intencionados. Se ativar esta definição de política, qualquer zona pode ser protegida contra elevação de zona para todos os processos. Se desabilitar ou não configura esta definição de política, processos que não sejam o Internet Explorer ou aos listados na lista de processos recebem sem essa proteção.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Predefinido**: Enabled  
  
- **Os controles ActiveX não assinados de transferência de zona de internet do Internet Explorer**   
  Esta definição de política permite-lhe gerir se os utilizadores podem transferir os controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando proveniente de uma zona não fidedigna. Se ativar esta definição de política, os utilizadores podem executar controles sem assinatura sem intervenção do utilizador. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados para escolher se pretende permitir que o controle não assinado executar. Se desativar esta definição de política, os utilizadores não é possível executar controles sem assinatura. Se não configurar esta definição de política, os utilizadores não é possível executar controles sem assinatura.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Predefinido**: Desativar  
  
- **Zona de internet do Internet Explorer navegue windows e os quadros em diferentes domínios**   
  Esta definição de política permite-lhe gerir a abertura do windows e os quadros e acesso de aplicações em diferentes domínios. Se ativar esta definição de política, os utilizadores podem abrir windows e quadros de outros domínios e aplicações de acesso de outros domínios. Se selecionar a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o windows e os quadros para aceder às aplicações de outros domínios. Se desativar esta definição de política, os utilizadores não é possível abrir o windows e os quadros para aceder às aplicações de diferentes domínios. Se não configurar esta definição de política, os utilizadores podem abrir windows e quadros de outros domínios e aplicações de acesso de outros domínios.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Predefinido**: Desativar  
  
- **Atualizações de zona de internet do Internet Explorer a barra de status por meio de script**  
  Esta definição de política permite-lhe gerir se um script pode atualizar a barra de status na zona. Se ativar esta definição de política, os scripts podem atualizar a barra de status. Se desabilitar ou não configura esta definição de política, o script não é permitido para atualizar a barra de status.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Predefinido**: Desativado  
  
- **Zona restrita do Internet Explorer incluir o caminho local, ao carregar ficheiros para o servidor**  
  Esta definição de política controla se as informações de caminho local são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se as informações de caminho local são enviadas, algumas informações podem inadvertidamente reveladas para o servidor. Por exemplo, os arquivos enviados a partir do ambiente de trabalho do usuário podem conter o nome de utilizador como parte do caminho. Se ativar esta definição de política, informações de caminho são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se desativar esta definição de política, informações de caminho são removidas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se não configurar esta definição de política, o usuário pode escolher se as informações de caminho são enviadas quando estiver a carregar um ficheiro através de um formulário HTML. Por predefinição, são enviadas informações de caminho.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Predefinido**: Desativado  
  
- **Processos do Internet Explorer restringem a transferência de ficheiros**   
  Esta definição de política permite que as aplicações que alojam o controle Web Browser bloquear a pedir a confirmação automática de downloads de arquivos que não são iniciada pelo utilizador. Se ativar esta definição de política, o controle do navegador da Web irá bloquear a pedir a confirmação automática de downloads de arquivos que não são iniciado para todos os processos de utilizador. Se desativar esta definição de política, o controle de navegador da Web não bloqueará a pedir a confirmação automática de downloads de arquivos que não são iniciado para todos os processos de utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer, permitir que a zona restritas apenas aprovados domínios usar controles de Active X**   
  Esta definição de política controla se é pedido ao utilizador para permitir que os controles ActiveX ser executada em Web sites que não seja o site no qual instalado o controle ActiveX. Se ativar esta definição de política, é pedido ao utilizador antes de controles ActiveX podem ser executados de Web sites nesta zona. O utilizador pode optar por permitir que o controle ser executada a partir do site atual ou de todos os sites. Se desativar esta definição de política, o utilizador não vê a linha de comandos da ActiveX por site e controles ActiveX podem ser executados de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Predefinido**: Enabled  
  
- **A inicializar de zona restrita do Internet Explorer e script que controla Active X não marcados como seguro**  
  Esta definição de política permite-lhe de gerenciar controles ActiveX não marcados como seguros. Se ativar esta definição de política, controles ActiveX executam, carregá-lo com parâmetros e com script sem definir a segurança de objeto para dados não confiáveis ou scripts. Esta definição não é recomendável, exceto para zonas administradas e seguras. Esta definição faz com que os controles confiável e seguros ser inicializado e programado, ignorar os controles de Script ActiveX marcados como seguro para a opção de criação de scripts. Se ativar esta definição de política e selecione a linha de comandos na caixa de lista pendente, os utilizadores são consultados se pretende permitir que o controle carregar com parâmetros ou com script. Se desativar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script. Se não configurar esta definição de política, controles ActiveX que não não possível efetuar seguros não são carregados com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Predefinido**: Desativar  
  
- **Usuários do Internet Explorer, alteração de políticas**  
  Impede os utilizadores alterem as definições de zona de segurança. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, o botão de nível personalizado e o controlo de deslize do nível de segurança no separador de segurança na caixa de diálogo Opções da Internet estão desativadas. Se desativar esta política ou não configurá-lo, os utilizadores podem alterar as definições para as zonas de segurança. Esta política impede os utilizadores alterem as definições de zona de segurança estabelecidas pelo administrador. Nota: A política "Desativar a página de segurança" (localizada no painel de controlo do administrativos\Componentes Windows\Internet Explorer\Painel de \User Configuration\Administrative), que remove a guia de segurança do Internet Explorer, no painel de controlo, terão precedência sobre Esta política. Se estiver ativada, esta política é ignorada. Além disso, consulte o "zonas de segurança: Utilizar apenas as definições de máquina"política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Predefinido**: Desativado  
  
- **Modo protegido do Internet Explorer zona restritas**  
  Esta definição de política permite-lhe ativar o modo protegido. Modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo as localizações que o Internet Explorer pode gravar no Registro e o sistema de ficheiros. Se ativar esta definição de política, o modo protegido é ativado. O utilizador não é possível desativar o modo protegido. Se desativar esta definição de política, o modo protegido é desativado. O utilizador não é possível ativar o modo protegido. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o modo protegido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Predefinido**: Ativar  
  
- **Persistência de dados de utilizador de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir a preservação de informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Quando um usuário retorne a uma página persistente, o estado da página pode ser restaurado se esta definição de política está configurada corretamente. Se ativar esta definição de política, os usuários possam preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se desativar esta definição de política, os usuários não é possível preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se não configurar esta definição de política, os usuários possam preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Predefinido**: Desativado  
  
- **Scripts de zona de internet do Internet Explorer de controles de navegador da web**  
 
  Esta definição de política determina se uma página pode controlar o embedded WebBrowser controles por meio de script. Se ativar esta definição de política, é permitido o acesso de script para o controle WebBrowser. Se desativar esta definição de política, não é permitido o acesso de script para o controle WebBrowser. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o acesso de script para o controle WebBrowser. Por predefinição, o acesso de script para o controle WebBrowser é permitido apenas no computador Local e zonas da Intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Predefinido**: Desativado  
  
- **Persistência de dados de utilizador de zona restritos do Internet Explorer**  
  Esta definição de política permite-lhe gerir a preservação de informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Quando um usuário retorne a uma página persistente, o estado da página pode ser restaurado se esta definição de política está configurada corretamente. Se ativar esta definição de política, os usuários possam preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se desativar esta definição de política, os usuários não é possível preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco. Se não configurar esta definição de política, os usuários não é possível preservar as informações no histórico do navegador, nos Favoritos, num arquivo XML ou diretamente dentro de uma página da Web guardado no disco.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Predefinido**: Desativado  
  
- **Bloqueado de permissões de java de zona de intranet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para miniaplicativos Java. Se ativar esta definição de política, pode escolher as opções da caixa de lista pendente. Personalizadas, para controlar as definições de permissões individualmente. Segurança baixa permite miniaplicativos executar todas as operações. Segurança média permite miniaplicativos executar em sua área de segurança (uma área na memória fora do que o programa não é possível fazer chamadas), além de recursos, como o espaço scratch (uma área de armazenamento seguro e fiável no computador cliente) e o ficheiro controlada pelo utilizador e/s. Segurança alta permite miniaplicativos executar em sua área de segurança. Desative o Java para impedir que qualquer miniaplicativos em execução. Se desativar esta definição de política, não é possível executar miniaplicativos Java. Se não configurar esta definição de política, miniaplicativos Java estão desativados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Predefinido**: Desativar o java  
  
- **Modo protegido do Internet Explorer avançada**  
  Modo protegido avançado proporciona proteção adicional contra sites mal-intencionados utilizando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam, pelo menos, Windows 8, o modo protegido avançado também limita os locais do Internet Explorer pode ler a partir do Registro e o sistema de ficheiros. Se ativar esta definição de política, o modo protegido avançado está ativado. Qualquer zona que tenha o modo protegido ativado irá utilizar o modo protegido avançado. Os utilizadores não será possível desativar o modo protegido avançado. Se desativar esta definição de política, o modo protegido avançado está desativado. Qualquer zona que tenha o modo protegido ativado irá utilizar a versão do modo protegido, introduzido no Internet Explorer 7 para Windows Vista. Se não configurar esta política, os utilizadores podem ativar ou desativar o modo protegido avançado no separador Avançadas da caixa de diálogo Opções da Internet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Predefinido**: Enabled  
  
- **Internet Explorer ignore os avisos do SmartScreen**  
  Esta definição de política determina se o utilizador pode ignorar avisos do Filtro SmartScreen. O Filtro SmartScreen avisa o utilizador sobre ficheiros executáveis que usuários do Internet Explorer geralmente não transferirem a partir da Internet. Se ativar esta definição de política, os avisos do Filtro SmartScreen impedir o utilizador. Se desabilitar ou não configura esta definição de política, o utilizador pode ignorar avisos do Filtro SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Predefinido**: Desativado  
  
- **Atualização de meta de zona do Internet Explorer restrito**  
  Esta definição de política permite-lhe gerir se o navegador de um usuário pode ser redirecionado para outra página da Web, se o autor da página da Web usa a definição de metadados de atualização (etiqueta) para redirecionar os navegadores para outra página da Web. Se ativar esta definição de política, o navegador de um usuário que carrega uma página que contém uma definição de metadados de atualização de Active Directory pode ser redirecionado para outra página da Web. Se desativar esta definição de política, navegador de um usuário que carrega uma página que contém uma definição de metadados de atualização de Active Directory não pode ser redirecionado para outra página da Web. Se não configurar esta definição de política, navegador de um usuário que carrega uma página que contém uma definição de metadados de atualização de Active Directory não pode ser redirecionado para outra página da Web.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Predefinido**: Desativado  
  
## <a name="local-policies-security-options"></a>Opções de segurança de políticas locais
Para obter mais informações, consulte [CSP de política - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) na documentação do Windows. 

- **Restringir o acesso anónimo a pipes nomeados e partilhas**  
  Quando ativada, esta definição de segurança restringe o acesso anónimo a partilhas e pipes para as definições para: (1) pipes nomeados que podem ser acedidos anonimamente (2) partilhas que podem ser acedidas anonimamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Predefinido**: Sim  
  
- **Servidores baseados em segurança de sessão mínima para NTLM SSP**  
  Esta definição de segurança permite que um servidor exigir a negociação de encriptação de 128 bits e/ou de segurança de sessão de NTLMv2. Estes valores dependem do valor de definição de segurança de nível de autenticação do LAN Manager. As opções são: Exigir a segurança de sessão de NTLMv2: A ligação irá falhar se não estiver negociada a integridade de mensagens. Exigir encriptação de 128 bits. A ligação irá falhar se a encriptação forte (128 bits) não é negociada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Predefinido**: Exigir encriptação de 128 bits e de NTLM V2  
  
- **Minutos de inatividade do ecrã de bloqueio quando ativa a proteção de tela**  
  O Windows repara na inatividade de um início de sessão e, se a quantidade de tempo inativo exceder o limite de inatividade, então, a proteção de ecrã será executado, bloqueando a sessão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Predefinido**: 15
  
- **Necessitam de cliente para assinar comunicações digitalmente sempre** esta definição de segurança determina se todo o tráfego de canal de segurança iniciado pelo membro de domínio tem de ser assinado ou criptografado. Quando um computador é associado um domínio, é criada uma conta de computador. Depois disso, quando o sistema é iniciado, ele usa a palavra-passe da conta de computador para criar um canal seguro com um controlador de domínio para o seu domínio. Este canal seguro é utilizado para executar operações como o NTLM passar por autenticação, pesquisa de nome/SID de LSA e muito mais. Esta definição determina se a todo o tráfego de canal de segurança iniciado pelo membro de domínio cumpre os requisitos mínimos de segurança. Especificamente determina se todo o tráfego de canal de segurança iniciado pelo membro de domínio tem de ser assinado ou criptografado. Se esta política estiver ativada, em seguida, o canal seguro não ser estabelecido, a menos que a assinatura ou encriptação de todo o tráfego de canal seguro é negociada. Se esta política estiver desativada, em seguida, encriptação e assinatura de todo o tráfego de canal seguro é negociado com o controlador de domínio caso em que o nível de assinatura e encriptação depende da versão do controlador de domínio e as definições das duas seguintes políticas: Membro de domínio: Encriptar digitalmente dados de canal seguro (quando possível) membro de domínio: Digitalmente o início de sessão proteger os dados de canal (quando possível).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Predefinido**: Sim
  
- **Nível de autenticação**  
  Esta definição de segurança determina qual protocolo de autenticação de desafio/resposta é utilizado para inícios de sessão de rede. Esta opção afeta o nível de protocolo de autenticação utilizado por clientes, o nível de segurança de sessão negociada e o nível de autenticação aceite pelos servidores da seguinte forma:  
  - *Enviar respostas de LM e NTLM* -clientes de utilizam a autenticação LM e NTLM e nunca usar segurança de sessão de NTLMv2; controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Enviar LM e NTLM - NTLMv2 se negociado* -clientes de utilizam a autenticação LM e NTLM e utilizam segurança de sessão de NTLMv2, se o servidor suportar; controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Enviar resposta NTLM apenas* -clientes utilizam apenas autenticação NTLM e utilizam a segurança de sessão de NTLMv2, se o servidor suportar; controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Enviar resposta de NTLMv2 apenas* -clientes utilizam apenas a autenticação NTLMv2 e utilizam a segurança de sessão de NTLMv2, se o servidor suportar; controladores de domínio aceitam a autenticação NTLMv2, NTLM e LM. 
  - *Envie resposta de NTLMv2 apenas. Recusar LM* -clientes utilizam apenas a autenticação NTLMv2 e utilizam a segurança de sessão de NTLMv2, se o servidor suportar; controladores de domínio recusam LM (aceitar apenas a autenticação NTLM e NTLMv2). 
  - *Envie resposta de NTLMv2 apenas. Recusar LM e NTLM* -clientes utilizam apenas a autenticação NTLMv2 e utilizam a segurança de sessão de NTLMv2, se o servidor suportar; controladores de domínio recusam LM e NTLM (aceitar apenas a autenticação NTLMv2).  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Predefinido**: Envie resposta de NTLMv2 apenas. Recusar LM e NTLM
  
- **Impedir que os clientes a enviar de palavras-passe não encriptadas para servidores SMB de terceiros**  
  Se esta definição de segurança estiver ativada, o redirecionador de bloco de mensagem de servidor (SMB) pode enviar palavras-passe de texto sem formatação para servidores SMB não Microsoft que não suportam a encriptação de palavra-passe durante a autenticação. Enviar palavras-passe não encriptadas é um risco de segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Predefinido**: Sim
  
- **Exigir assinatura digital sempre de comunicações de servidor**  
  Esta definição de segurança determina se o cliente SMB tenta negociar a assinatura de pacotes SMB. O protocolo do server message block (SMB) fornece a base para ficheiros do Microsoft e a partilha de impressão e muitas outras operações de rede, como administração remota do Windows. Para impedir ataques man-in-the-middle que modificar pacotes SMB em trânsito, o protocolo SMB suporta a assinatura digital de pacotes SMB. Esta definição de política determina se o componente de cliente SMB tenta negociar a assinatura para estabelecer a ligação a um servidor do SMB de pacotes SMB. Se esta definição estiver ativada, o cliente de rede Microsoft pedirá o servidor para efetuar após a configuração de sessão de assinatura de pacotes SMB. Se a assinatura de pacotes tiver sido ativada no servidor, a assinatura de pacotes será negociada. Se esta política estiver desativada, o cliente SMB nunca negociar a assinatura de pacotes SMB.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Predefinido**: Sim
  
- **Comportamento de solicitação de elevação do administrador**  
  Esta definição de política controla o comportamento do prompt de elevação para administradores. As opções são: 
    - *Elevar sem pedir* -permite que as contas com privilégios executar uma operação que exige elevação sem a necessidade de consentimento ou credenciais. Nota: Utilize esta opção apenas nos ambientes mais restritos. 
    - *Pedido de credenciais no ambiente de trabalho seguro* - quando uma operação requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para introduzir um nome de utilizador com privilégios e uma palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com privilégio mais alto disponível do utilizador. 
    - *Pedir consentimento no ambiente de trabalho seguro* - quando uma operação requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para selecionar permitir ou negar. Se o usuário seleciona o permitir, a operação continuará com privilégio mais alto disponível do utilizador. 
    - *Pedido de credenciais* - quando uma operação requer elevação de privilégios, é pedido ao utilizador para introduzir um nome de utilizador administrativo e a palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
    - *Pedir consentimento* - quando uma operação requer elevação de privilégios, é pedido ao utilizador para selecionar permitir ou negar. Se o usuário seleciona o permitir, a operação continuará com privilégio mais alto disponível do utilizador.  
    - *Pedir consentimento para binários não Windows* - quando uma operação para uma aplicação de terceiros exige elevação de privilégios, é pedido ao utilizador para selecionar permitir ou negar na área de trabalho segura. Se o usuário seleciona o permitir, a operação continuará com privilégio mais alto disponível do utilizador. 
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Predefinido**: Pedir consentimento no ambiente de trabalho seguro
  
- **Clientes baseados na segurança de sessão mínima para NTLM SSP**  
  Esta definição de segurança permite que um cliente requerer a negociação de encriptação de 128 bits e/ou de segurança de sessão de NTLMv2. Estes valores dependem do valor de definição de segurança de nível de autenticação do LAN Manager. As opções são:
  - *Exigir a segurança de sessão de NTLMv2* -a ligação irá falhar se o protocolo de NTLMv2 não é negociado. 
  - *Exigir encriptação de 128 bits* -a ligação irá falhar se a encriptação forte (128 bits) não é negociada.
  - *Exigir encriptação de 128 bits e de NTLMv2*.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Predefinido**: Exigir encriptação de 128 do NTLM V2
  
- **Comportamento de remoção do smart card**  
    Esta definição de segurança determina o que acontece quando o smart card para um utilizador com sessão iniciada é removido de leitor de smart card. As opções são:
     - *Nenhuma ação*. 
     - *Bloquear estação de trabalho* -a estação de trabalho é bloqueada quando o smart card é removido, permitindo que os usuários deixar a área, tome o smart card com eles e ainda manter uma sessão protegida.
     - *Forçar fim da sessão* -o utilizador é automaticamente terminada quando o smart card é removido.
     - *Desligar a sessão de ambiente de trabalho remoto* -remoção do smart card termina a sessão sem o utilizador terminar sessão. Isso permite que o usuário inserir o smart card e retomar a sessão mais tarde, ou em outro cartão inteligente leitor computador equipado com, sem ter de iniciar sessão novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Predefinido**: Bloquear estação de trabalho
  
- **Bloquear a enumeração anónima de contas e partilhas SAM**  
  Esta definição de segurança determina se deve permitir a enumeração anónima de SAM, contas e partilhas. Windows permite aos utilizadores anónimos realizar determinadas atividades, tais como enumerar os nomes de contas de domínio e partilhas de rede. Isso é conveniente, por exemplo, quando um administrador pretende conceder acesso a utilizadores num domínio fidedigno que não mantêm uma relação de confiança recíproco. Se não pretender permitir a enumeração anónima de SAM, contas e partilhas, em seguida, definir esta política como *Sim*.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Predefinido**: Sim
  
- **Início de sessão remoto do bloco com palavra-passe em branco**  
  Esta definição de segurança determina se as contas locais que não estão protegidos por senha podem ser utilizadas para iniciar sessão a partir de localizações que não seja o console do computador físico. Se estiver ativada, as contas locais que não estão protegidos por senha tem de utilizar o teclado do computador para iniciar sessão. 

  *Aviso*: Computadores que não estão em localizações fisicamente seguras sempre devem impor políticas de palavra-passe segura para todas as contas de utilizador local. Caso contrário, qualquer pessoa com acesso físico ao computador pode faça logon com uma conta de utilizador que não tem uma palavra-passe. Isso é especialmente importante para computadores portáteis. 

  Se aplicar esta política de segurança para a todos os utilizadores de grupo, ninguém pode iniciar sessão através dos serviços de ambiente de trabalho remoto. Esta definição não afeta logons que utilizar contas de domínio. É possível para aplicações que utilizam inícios de sessão interativos remotos para ignorar esta definição.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Predefinido**: Sim
  
- **Comportamento de solicitação de elevação de usuário padrão**  
  Esta definição de política controla o comportamento do prompt de elevação para usuários padrão. 
  - *Negar automaticamente pedidos de elevação* - quando uma operação requer elevação de privilégios, um configurável acesso negado é apresentada a mensagem de erro. Uma empresa que está executando áreas de trabalho como usuário padrão pode escolher esta definição para reduzir as chamadas de suporte técnico. 
  - *Pedido de credenciais no ambiente de trabalho seguro* - quando uma operação requer elevação de privilégios, é pedido ao utilizador no ambiente de trabalho seguro para introduzir um nome de utilizador diferente e uma palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Pedido de credenciais* - quando uma operação requer elevação de privilégios, é pedido ao utilizador para introduzir um nome de utilizador administrativo e a palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Predefinido**: Negar automaticamente pedidos de elevação
  
- **Exigir o modo de aprovação de administrador para os administradores**  
  Esta definição de política controla o comportamento de todas as definições de política de controlo de conta de usuário (UAC) para o computador. Se alterar esta definição de política, deve reiniciar o computador. As opções são:   
  - *Não configurado* -modo de aprovação de administrador e todos os relacionados com as definições de política UAC estão desativadas. Nota: Se esta definição de política estiver desativada, o Centro de segurança notifica-o de que a segurança geral do sistema operacional foi reduzida. 
  - *Sim* -modo de aprovação de administrador está ativada. Esta política tem de estar ativada e as definições de política UAC relacionadas tem de ser definidas adequadamente para permitir que a conta de administrador incorporada e todos os outros utilizadores que são membros do grupo Administradores para executar no modo de aprovação de administrador.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Predefinido**: Sim
  
- **Impedir a enumeração anónima de contas SAM**  
  Esta definição de segurança determina quais permissões adicionais são concedidas para ligações anónimas para o computador. Windows permite aos utilizadores anónimos realizar determinadas atividades, tais como enumerar os nomes de contas de domínio e partilhas de rede. Isso é conveniente, por exemplo, quando um administrador pretende conceder acesso a utilizadores num domínio fidedigno que não mantêm uma relação de confiança recíproco. Esta opção de segurança permite que as restrições adicionais ser colocado em ligações anónimas da seguinte forma: 
  - *Sim* -não permitir a enumeração de SAM contas. Esta opção substitui todos os utilizadores por Authenticated Users as permissões de segurança para os recursos.
  - *Não configurado* -sem restrições adicionais. Contar com as permissões predefinidas.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Predefinido**: Sim
  
- **Permitir chamadas remotas para o Gestor de contas de segurança**  
  Esta definição de política permite-lhe restringir ligações rpc remoto para SAM. Se não selecionada, é utilizado o descritor de segurança padrão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Predefinido**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Utilizar o modo de aprovação de administrador**  
  Esta definição de política controla o comportamento de modo de aprovação de administrador para a conta interna de administrador. As opções são: 
  - *Sim* -a conta interna administrador utiliza o modo de aprovação de administrador. Por predefinição, a qualquer operação que exige elevação de privilégios pedirá ao utilizador para aprovar a operação. 
  - *Não configurado* -a conta interna administrador executa todos os aplicativos com privilégio administrativo completo. 

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Predefinido**: Sim
  
- **Permitir que as aplicações de acesso de interface do Usuário para localizações seguras**  
  Esta definição de política de controlos se programas de acessibilidade de Interface do usuário (UIAccess ou UIA) podem desativar automaticamente o ambiente de trabalho seguro para pedidos de elevação utilizado por um usuário padrão. 
  - *Sim* -os programas UIA, incluindo assistência remota do Windows, desativar automaticamente o ambiente de trabalho seguro para pedidos de elevação. Se não desativar o "User Account Control: Mude para o ambiente de trabalho seguro quando pedir elevação"definição de política, as instruções apresentadas na área de trabalho do utilizador interativo em vez de área de trabalho protegida. 
  - *Não configurado*:-área de trabalho protegida pode ser desativado apenas pelo utilizador do ambiente de trabalho interativo ou ao desativar o "User Account Control: Mude para o ambiente de trabalho seguro quando pedir elevação"definição de política.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Predefinido**: Sim

- **Detectar instalações de aplicativos e aviso de elevação**  
  Esta definição de política controla o comportamento de deteção de instalação de aplicações para o computador. As opções são: 
  - *Ativado* - quando um pacote de instalação do aplicativo é detetado que requer a elevação de privilégio, é pedido ao utilizador para introduzir um nome de utilizador administrativo e a palavra-passe. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Desativado* -pacotes de instalação de aplicações não são detetados e prompt de elevação. As empresas que executam desktops de usuário padrão e usar delegados tecnologias de instalação, como instalação de Software da diretiva de grupo ou Systems Management Server (SMS), deve desativar esta definição de política. Neste caso, a detecção de instalador é desnecessária.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Predefinido**: Sim
  
- **Impedir que armazenar o valor de hash do LAN manager na próxima alteração de palavra-passe**  
  Esta definição de segurança determina se, na próxima alteração de palavra-passe, o valor de hash LAN Manager (LM) para a nova palavra-passe é armazenado. O hash LM é relativamente fraca e propenso a ataques, as compared with o hash de NT do Windows mais criptograficamente forte. Uma vez que o hash LM é armazenado no computador local na base de dados de segurança, as palavras-passe podem ser comprometidas se a base de dados de segurança for atacado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Predefinido**: Sim

- **Virtualizar o arquivo e registro falhas de escrita por localizações de utilizador**  
  Esta definição de política de controlos se falhas de escrita de aplicações são redirecionadas para locais de sistema de registro e arquivo definidos. Esta definição de política atenua os aplicativos que são executados como administrador e escrever dados de tempo de execução de aplicações para *% ProgramFiles %* , *% Windir %* , *%Windir%\system32*, ou *HKLM\Software*.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Predefinido**: Sim

## <a name="ms-security-guide"></a>Guia de segurança do MS  
Para obter mais informações, consulte [CSP de política - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) na documentação do Windows.  

- **Aplicar restrições de UAC para contas locais no início de sessão de rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Predefinido**: Enabled
  
- **Configuração de início do controlador de cliente do SMB v1**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Predefinido**: Controlador desativado
  
- **Servidor do SMB v1**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Predefinido**: Desativado
  
- **Autenticação resumida**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Predefinido**: Desativado
  
- **Manipulação de exceção estruturada substituir a proteção**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Predefinido**: Enabled
  
## <a name="mss-legacy"></a>MSS legado  
Para obter mais informações, consulte [CSP de política - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) na documentação do Windows.  

- **Rede IP de origem encaminhamento ao nível de proteção**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Predefinido**: Proteção mais alta  
  
- **Rede ignorar pedidos de versão de nome do NetBIOS, exceto de servidores WINS**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Predefinido**: Enabled
  
- **Nível de proteção de encaminhamento do IPv6 origem de rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Predefinido**: Proteção mais alta

- **OSPF gerado de substituição de redirecionamentos ICMP de rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Predefinido**: Desativado
  
## <a name="power"></a>Power  
Para obter mais informações, consulte [CSP de política - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) na documentação do Windows.  

- **Exigir palavra-passe na reativação enquanto ligado**  
  Esta definição de política especifica se é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se ativar ou não configurar esta definição de política, é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se desativar esta definição de política, o utilizador não é solicitado uma palavra-passe quando o sistema sai do modo de suspensão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Predefinido**: Enabled
  
- **Estados de espera durante a suspensão enquanto com bateria**  
  Esta definição de política gere se o Windows podem utilizar Estados de espera ao colocar o computador num Estado de suspensão. Se ativar ou não configurar esta definição de política, o Windows utiliza os Estados de espera para colocar o computador num Estado de suspensão. Se desativar esta definição de política, os Estados de espera (S1-S3) não são permitidos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Predefinido**: Desativado
  
- **Estados de espera durante a suspensão enquanto ligado**  
  Esta definição de política gere se o Windows podem utilizar Estados de espera ao colocar o computador num Estado de suspensão. Se ativar ou não configurar esta definição de política, o Windows utiliza os Estados de espera para colocar o computador num Estado de suspensão. Se desativar esta definição de política, os Estados de espera (S1-S3) não são permitidos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Predefinido**: Desativado
  
- **Exigir palavra-passe na reativação enquanto com bateria**  
  Esta definição de política especifica se é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se ativar ou não configurar esta definição de política, é pedido ao utilizador uma palavra-passe quando o sistema sai do modo de suspensão. Se desativar esta definição de política, o utilizador não é solicitado uma palavra-passe quando o sistema sai do modo de suspensão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Predefinido**: Enabled

## <a name="remote-assistance"></a>Assistência Remota
- **Assistência remota solicitada**  
  Esta definição de política permite-lhe ativar ou desativar a assistência remota do Solicited (pedir) neste computador. 
  - *Se ativar esta definição de política*, os utilizadores neste computador podem utilizar a transferência de e-mail ou ficheiro pedir a alguém para obter ajuda. Além disso, os utilizadores podem utilizar programas de mensagens instantâneas para permitir ligações a este computador, e pode configurar definições adicionais da assistência remota. 
  - *Se desativar esta definição de política*, os utilizadores neste computador não é possível utilizar a transferência de e-mail ou ficheiro pedir a alguém para obter ajuda. Além disso, os utilizadores não é possível utilizar programas de mensagens instantâneas para permitir ligações a este computador. 
  - *Se não configurar esta definição de política*, os utilizadores podem ativar ou desativar Solicited (pedir) de assistência remota próprios nas propriedades do sistema no painel de controlo. Os utilizadores também podem configurar definições da assistência remota. 

  Se ativar esta definição de política, tem duas formas de permitir auxiliares fornecer assistência remota: "Permitir auxiliares para ver apenas o computador" ou "Permitir auxiliares controlar remotamente o computador". O "pedido de suporte tempo máximo" definição de política define um limite na quantidade de tempo que um criados com a transferência de ficheiro ou e-mail de convite de assistência remota pode permanecer aberto. A ", selecione o método para enviar convites de e-mail" definição especifica qual padrão de e-mail a utilizar para enviar convites de assistência remota. Dependendo do seu programa de e-mail, pode utilizar o protocolo padrão (o destinatário de convite liga-se através de um link da Internet) ou o SMAPI (MAPI simples) padrão (o convite é anexado à sua mensagem de e-mail). Esta definição de política não está disponível no Windows Vista, uma vez que o SMAPI é o único método suportado. Se ativar esta definição de política também deverá habilitar exceções de firewall adequadas permitir comunicações de assistência remota.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Predefinido**: Desativar a assistência remota

  Quando definido como *ativar a assistência remota*, configure as seguintes definições adicionais:  
  - **Assistência remota solicitado permissão**  
    **Predefinido**: Vista  

  - **Valor de tempo máximo do pedido de suporte**  
    **Predefinido**: *Não configurado*  

  - **Período de tempo de pedido de suporte máximo**  
    **Predefinido**: Minutos    

  - **Método de convite por email**  
    **Predefinido**: MAPI simples

  
## <a name="remote-desktop-services"></a>Serviços de Ambiente de Trabalho Remoto  
Para obter mais informações, consulte [CSP de política - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) na documentação do Windows.  

- **Bloquear a gravação de palavra-passe**  
  Controla se as palavras-passe podem ser guardadas neste computador de conexão de área de trabalho remoto. Se ativar esta definição da palavra-passe a guardar a caixa de seleção na conexão de área de trabalho remoto está desativada e os utilizadores não poderão guardar palavras-passe. Quando um utilizador abre um ficheiro RDP através da ligação de ambiente de trabalho remoto e salva suas configurações, são eliminados a qualquer palavra-passe que existia anteriormente no ficheiro RDP. Se desativar esta definição ou deixá-lo não configurado, o utilizador pode guardar palavras-passe através da ligação de ambiente de trabalho remoto.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Predefinido**: Enabled
  
- **Proteger as comunicações de RPC**  
  Especifica se um servidor de anfitrião de sessões de ambiente de trabalho remoto requer comunicação RPC segura com todos os clientes ou permite a comunicação protegida. Pode utilizar esta definição para reforçar a segurança da comunicação RPC com clientes ao permitir que apenas autenticada e criptografada pedidos. Se o estado estiver definido como ativado, os serviços de ambiente de trabalho remoto aceita os pedidos de clientes RPC que oferecem suporte a solicitações seguras e não permite a comunicação segura com os clientes não fidedignos. Se o estado estiver definido como desativado, os serviços de ambiente de trabalho remoto sempre solicitações de segurança para todo o tráfego RPC. No entanto, a comunicação protegida é permitida para clientes RPC que não responderem ao pedido. Se o estado estiver definido como não configurada, é permitida a comunicação protegida. Nota: A interface RPC é utilizada para administrar e configurar o Remote Desktop Services.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Predefinido**: Enabled
  
- **Redirecionamento de unidade de bloco**  
  Esta definição de política especifica se impede o mapeamento de unidades de cliente numa sessão de serviços de ambiente de trabalho remoto (redirecionamento de unidade). Por predefinição, um servidor de anfitrião de sessões de RD mapeia unidades de cliente automaticamente após a ligação. Unidades mapeadas aparecem na árvore de pastas de sessão no Explorador de ficheiros ou de computador no formato  *\<letradaunidade >* no  *\<computername >* . Pode utilizar esta definição de política para substituir esse comportamento. Se ativar esta definição de política, redirecionamento de unidade de cliente não é permitido em sessões de serviços de ambiente de trabalho remoto e redirecionamento de cópia de ficheiros de área de transferência não é permitido em computadores que executam o Windows Server 2003, Windows 8 e Windows XP. Se desativar esta definição de política, o redirecionamento de unidade de cliente é sempre permitido. Além disso, redirecionamento de cópia de ficheiros de área de transferência é sempre permitido se o redirecionamento de área de transferência é permitido. Se não configurar esta definição de política, redirecionamento de unidade de cliente e o redirecionamento de cópia de ficheiros de área de transferência não estão especificados no nível de diretiva de grupo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Predefinido**: Enabled
  
- **Pedido de palavra-passe após a ligação**  
  Esta definição de política especifica se os serviços de ambiente de trabalho remoto pede sempre o cliente para uma palavra-passe após a ligação. Pode utilizar esta definição para impor um pedido de palavra-passe para os usuários fazendo logon em serviços de ambiente de trabalho remoto, mesmo que eles já fornecidos a palavra-passe no cliente de conexão de área de trabalho remoto. Por predefinição, os serviços de ambiente de trabalho remoto permite que os usuários façam logon automaticamente ao introduzir uma palavra-passe no cliente de conexão de área de trabalho remoto. Se ativar esta definição de política, os utilizadores não podem automaticamente iniciar sessão para os serviços de ambiente de trabalho remoto, fornecendo as respetivas palavras-passe no cliente de conexão de área de trabalho remoto. eles for pedidos uma palavra-passe iniciar sessão. Se desativar esta definição de política, os usuários podem sempre fazem logon Remote Desktop Services automaticamente ao fornecer as respetivas palavras-passe no cliente de conexão de área de trabalho remoto. Se não configurar esta definição de política, o início de sessão automático não está especificado no nível de diretiva de grupo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Predefinido**: Enabled
  
- **Nível de encriptação da ligação de cliente de serviços de ambiente de trabalho remoto**  
  Especifica se exige o uso de um nível de criptografia específicas para proteger as comunicações entre computadores cliente e servidores de anfitrião de sessões de RD durante a ligações de protocolo RDP (Remote Desktop). Esta política aplica-se apenas quando estiver a utilizar encriptação nativa do RDP. No entanto, a encriptação nativa de RDP (em oposição a encriptação SSL) não é recomendada. Esta política não se aplica a encriptação SSL. Se ativar esta definição de política, todas as comunicações entre clientes e servidores de anfitrião de sessões de RD durante ligações remotas tem de utilizar o método de encriptação especificado nesta definição. Por predefinição, o nível de encriptação é definido como alto. Os seguintes métodos de encriptação estão disponíveis:  
  - *Alta* -a alta definição encripta os dados enviados do cliente para o servidor e do servidor para o cliente usando a criptografia forte de 128 bits. Utilize este nível de encriptação em ambientes que contenham apenas clientes de 128 bits (por exemplo, os clientes que executam a conexão de área de trabalho remoto). Os clientes que não suportam este nível de encriptação não é possível ligar aos servidores de anfitrião de sessões de RD.  
  - *Compatível com o cliente* -definição compatível cliente encripta os dados enviados entre o cliente e o servidor em que a força da chave máximo suportado pelo cliente. Utilize este nível de encriptação em ambientes que incluem os clientes que não suportam a encriptação de 128 bits.  
  - *Baixa* -definição de baixa a encripta apenas os dados enviados do cliente para o servidor usando a criptografia de 56 bits.  
  
  Se desabilitar ou não configura esta definição, o nível de encriptação a utilizar para ligações remotas para servidores de anfitrião de sessões de RD não é imposto por meio da diretiva de grupo. A conformidade FIPS importante pode ser configurada por meio da criptografia de sistema. Utilizar algoritmos compatíveis com FIPS para encriptação, hash e assinatura definições na política de grupo (em computador configuração Windows Settings\Local \ Opções.) A definição compatíveis com FIPS criptografa e descriptografa os dados enviados do cliente para o servidor e do servidor ao cliente, com os algoritmos de criptografia do Federal Information Processing Standard (FIPS) 140, através de módulos criptográficos da Microsoft. Utilize este nível de encriptação quando a comunicação entre clientes e servidores de anfitrião de sessões de RD requer o nível mais elevado de encriptação.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Predefinido**: Alta
  
## <a name="remote-management"></a>Gestão Remota  
Para obter mais informações, consulte [CSP de política - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) na documentação do Windows.  

- **Executar o bloco de armazenamento como credenciais**  
  Autenticação básica do cliente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Predefinido**: Enabled
  
- **Autenticação básica**  
  Esta definição de política permite-lhe gerir se o serviço de gestão remota do Windows (WinRM) aceita autenticação básica de um cliente remoto. Se ativar esta definição de política, o serviço WinRM aceita autenticação básica de um cliente remoto. Se desabilitar ou não configura esta definição de política, o serviço WinRM não aceita a autenticação básica de um cliente remoto.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Predefinido**: Desativado
  
- **Autenticação de texto implícita de cliente de bloco**  
  Esta definição de política permite-lhe gerir se o cliente de gestão remota do Windows (WinRM) utiliza a autenticação resumida. Se ativar esta definição de política, o cliente WinRM não usa a autenticação resumida. Se desabilitar ou não configura esta definição de política, o cliente WinRM utiliza autenticação resumida.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Predefinido**: Enabled
  
- **Tráfego não criptografado**  
  Esta definição de política permite-lhe gerir se o serviço de gestão remota do Windows (WinRM) envia e recebe mensagens não encriptadas através da rede. Se ativar esta definição de política, o cliente WinRM envia e recebe mensagens não encriptadas através da rede. Se desabilitar ou não configura esta definição de política, o cliente WinRM envia ou recebe apenas as mensagens encriptadas através da rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Predefinido**: Desativado
  
- **Tráfego de cliente não encriptada**  
  Esta definição de política permite-lhe gerir se o cliente de gestão remota do Windows (WinRM) envia e recebe mensagens não encriptadas através da rede. Se ativar esta definição de política, o cliente WinRM envia e recebe mensagens não encriptadas através da rede. Se desabilitar ou não configura esta definição de política, o cliente WinRM envia ou recebe apenas as mensagens encriptadas através da rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Predefinido**: Desativado
  
- **Autenticação básica do cliente**  
  Esta definição de política permite-lhe gerir se o cliente de gestão remota do Windows (WinRM) utiliza a autenticação básica. Se ativar esta definição de política, o cliente WinRM utiliza a autenticação básica. Se o WinRM está configurado para utilizar o transporte HTTP, o nome de utilizador e palavra-passe são enviadas através da rede como texto não encriptado. Se desabilitar ou não configura esta definição de política, o cliente WinRM não usa a autenticação básica.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Predefinido**: Desativado
  
## <a name="remote-procedure-call"></a>Chamada de procedimento remoto  
Para obter mais informações, consulte [CSP de política - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) na documentação do Windows.  

- **Opções de RPC não autenticado de clientes**  
  Esta definição de política controla como o tempo de execução do servidor RPC processa não autenticados RPC clientes que se conectam aos servidores RPC. Esta definição de política irá afetar todos os aplicativos de RPC. Num ambiente de domínio, utilize esta definição de política com cuidado, dado que pode afetar uma ampla variedade de funcionalidades, incluindo o próprio de processamento de diretiva de grupo. Reverter uma alteração para esta definição de política pode exigir a intervenção manual de cada computador afetado. Esta definição de política nunca deve ser aplicada a um controlador de domínio. Se desativar esta definição de política, o tempo de execução do servidor RPC utilizará o valor de "Autenticado" no cliente Windows e o valor de "None" em versões do Windows Server que suportam esta definição de política. Se não configurar esta definição de política, continua a ser desativado. O tempo de execução do servidor RPC se comporta como se ele foi ativado com o valor de "Autenticado" utilizado para o cliente do Windows e o valor de "None" utilizada para SKUs de servidor que suportam esta definição de política. Se ativar esta definição de política, ele direciona o tempo de execução de servidor RPC para restringir não autenticados RPC clientes que se conectam a servidores RPC em execução numa máquina. Um cliente é considerado um cliente autenticado se este utilizar um pipe nomeado para comunicar com o servidor ou se ele usa a segurança de RPC. Esta restrição, dependendo do valor selecionado para esta definição de política pode isentar Interfaces RPC que pediu-se especificamente para ser acessível aos clientes não autenticados.  
  - *Nenhum* permite que todos os clientes RPC ligar a servidores RPC executado no computador em que a definição de política é aplicada. 
  - *Autenticado* permite que apenas os clientes RPC autenticado (por definição acima) para ligar a servidores RPC executado no computador em que a definição de política é aplicada. Isenções são concedidas a interfaces que pediram-los. 
  - *Autenticado sem exceções* permite que apenas os clientes RPC autenticado (por definição acima) para ligar a servidores RPC executado no computador em que a definição de política é aplicada. Sem exceções são permitidas. Nota: Esta definição de política não será aplicada até que o sistema for reiniciado.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Predefinido**: Autenticado

## <a name="search"></a>Pesquisa 
Para obter mais informações, consulte [CSP de política - pesquisa](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) na documentação do Windows.  

- **Desativar a indexação de itens encriptados**  
  Permite ou proíbe a indexação de itens. Este parâmetro é para o indexador do Windows Search, que controla a indexação itens que são encriptados, tais como os ficheiros do Windows Information Protection (WIP) protegido. Quando a política está ativada, os itens protegidos pelo WIP são indexados e os respetivos metadados são armazenados numa localização não encriptada. Os metadados incluem conteúdos como o caminho do ficheiro e a data de modificação. Quando a política estiver desativada, os itens protegidos pelo WIP não são indexados e não são exibidos nos resultados na Cortana ou ficheiro explorer. O desempenho das aplicações de fotografias e do Groove também poderá ser afetado se existirem muitos ficheiros multimédia protegidos pelo WIP no dispositivo.  
  [Saiba mais]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Predefinido**: Sim
  
## <a name="smart-screen"></a>Smart Screen  
Para obter mais informações, consulte [CSP de política - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.  

- **Bloquear a execução de ficheiros não verificados**  
  Impedir o utilizador de executar ficheiros não verificados. 
  - *Não configurado* -funcionários podem ignorar os avisos do SmartScreen e executar ficheiros maliciosos. 
  - *Sim* – os funcionários não é possível ignorar os avisos do SmartScreen e executar ficheiros maliciosos.

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Predefinido**: Sim

- **Exigir o SmartScreen para aplicações e ficheiros**  
  Permite aos administradores de TI configurar o SmartScreen para Windows.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Predefinido**: Sim
  
## <a name="system"></a>Sistema  
Para obter mais informações, consulte [CSP de política - sistema](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) na documentação do Windows.  

- **Inicialização de driver de início de arranque de sistema**  
  Esta definição de política permite-lhe especificar os drivers de inicialização são inicializados com base numa classificação de determinado por um driver de inicialização antecipada Antimalware iniciar. O driver de inicialização antecipada Antimalware de lançamento pode devolver as seguintes classificações para cada controlador de inicialização: 
  - *Boa* -o driver foi assinado e ainda não adulterado.  
  - *Ruim* -o driver foi identificado como software maligno. Recomendamos que não permita conhecidos controladores incorretos ser inicializado. 
  - *Ruim, mas necessário para o arranque* - o driver foi identificado como software maligno, mas o computador não pode inicializar com êxito sem carregar este controlador. 
  - *Desconhecido* -este controlador não tenha sido atestado por seu aplicativo de deteção de malware e não foi classificado pelo driver de inicialização antecipada Antimalware iniciar.  

  Se ativar esta definição de política, pode escolher quais drivers de inicialização para inicializar da próxima vez que o computador for iniciado. Se desabilitar ou não configurar esta política de definição, os drivers de início de inicialização for determinados desconhecido, bom ou ruim, mas é crítico de arranque é inicializados e a inicialização de controladores identificado como sendo má é ignorada. Se seu aplicativo de deteção de malware não inclui um driver de inicialização antecipada Antimalware iniciar ou se o driver de inicialização antecipada Antimalware iniciar tiver sido desativada, esta definição não tem qualquer efeito e todos os drivers de inicialização são inicializados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Predefinido**: Desconhecido bom e ruim críticas


## <a name="wi-fi"></a>Wi-Fi  
Para obter mais informações, consulte [CSP de política - Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) na documentação do Windows.  

- **Bloquear a partilha da Internet**  
  Especifica se a partilha da internet é permitida no dispositivo.   
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Predefinido**: Sim  

- **Bloquear automaticamente ligação a hotspots Wi-Fi**  
  Permitir ou não ao dispositivo ligar automaticamente a hotspots Wi-Fi.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Predefinido**: Sim  
  
## <a name="windows-connection-manager"></a>Gestor de ligações do Windows  
Para obter mais informações, consulte [CSP de política - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) na documentação do Windows.  

- **Ligação de bloco para redes de domínio**  
  Esta definição de política impede que computadores Conectando a uma rede baseada no domínio e um domínio com base em rede ao mesmo tempo. Se esta definição de política estiver ativada, o computador reage a tentativas de ligação de rede automática e manual com base nas seguintes circunstâncias: 
  - Tentativas de ligação automática quando o computador já está ligado a uma rede baseada em domínio, todas as tentativas de ligação automática a redes de domínio não são bloqueadas. Quando o computador já está ligado a uma rede baseada em domínio, as tentativas de ligação automática a redes com base em domínio são bloqueadas. 
  - Tentativas de ligação manual quando o computador já está ligado a um domínio com base em rede ou uma rede baseada em domínio sobre a mídia diferente de Ethernet e um utilizador tenta criar uma ligação manual a uma rede adicional em violação da presente política definir, desliga a ligação de rede existente e a ligação manual é permitida. Quando o computador já está ligado a um são um domínio com base em rede ou uma rede baseada em domínio sobre Ethernet e um utilizador tenta criar uma ligação manual a uma rede adicional em violação desta definição de política, é a ligação de Ethernet existente mantido, e a tentativa de ligação manual é bloqueada.  

  Se esta definição de política não está configurada ou está desativada, os computadores têm permissão para ligar em simultâneo ao domínio e redes de domínio não.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Predefinido**: Enabled
  
## <a name="windows-defender"></a>Windows Defender  
Para obter mais informações, consulte [CSP de política - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.  

- **Analisar mensagens de correio recebidas**  
  Permite ou proíbe a verificação de e-mail.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Predefinido**: Sim  

- **Tipo de processo filho de lançamento de aplicações do Office**  
  Aplicações do Office não têm permissão para criar processos de subordinados. Isto inclui Word, Excel, PowerPoint, OneNote e acesso. Este é um comportamento típico de malware, especialmente para ataques baseados na macro que tentam utilizar aplicações do Office para iniciar ou transferir executáveis mal-intencionados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Predefinido**: Bloquear
  
- **Tipo de consentimento de submissão de exemplo do Defender**  
  Nível no Windows Defender para enviar dados de consentimento de verificações para o utilizador. Se já tiver sido concedido o consentimento necessário, o Windows Defender envia-os. Caso contrário, (e se o usuário especificou nunca para perguntar), a interface do Usuário é iniciado para pedir consentimento do utilizador (quando o Defender/AllowCloudProtection é permitido) antes de enviar dados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Predefinido**: Enviar automaticamente amostras seguras 
  
- **Intervalo de atualização de assinatura (em horas)**  
  Intervalo de atualização de assinatura de Defender em horas
  
  **Predefinido**: 4
  
- **Script transferido o tipo de execução do payload**  
  Script de Defender transferido o tipo de execução do payload
  
  **Predefinido**: Bloquear
  
- **Impedir que o tipo de roubo de credenciais**  
  Windows Defender Credential Guard utiliza segurança baseada em virtualização para isolar segredos, permitindo apenas software de sistema com privilégios possam acessá-los. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, tal como Ataques PtH ou PtT. Windows Defender Credential Guard impede estes ataques protegendo os hashes de palavra-passe NTLM, permissão de concessão de permissões Kerberos e as credenciais armazenadas por aplicações como credenciais de domínio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Predefinido**: Ativar

- **Tipo de execução de conteúdo de e-mail**  
  Esta regra bloqueia os seguintes tipos de ficheiro de que está a ser executado ou iniciados a partir de uma mensagem de e-mail vista no Microsoft Outlook ou webmail (como Gmail.com ou Outlook.com): Executável arquivos (por exemplo, .exe,. dll ou. scr), arquivos de Script (por exemplo, um .ps do PowerShell, VisualBasic. vbs ou arquivo do JavaScript. js) ficheiros de arquivo de Script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Predefinido**: Bloquear

- **Criar o leitor Adobe num processo filho**  

  **Predefinido**: Ativar

- **Tipo de proteção de rede**  
  Esta política permite-lhe ativar a proteção de rede (bloco/auditoria) e desativado no Windows Defender Exploit Guard. Proteção de rede é uma funcionalidade do Windows Defender Exploit Guard que protege os funcionários com qualquer aplicação de aceder ao atos fraudulentos de phishing, sites que hospedam a exploração e conteúdo malicioso na Internet. Isto inclui a impedir de browsers de terceiros de ligar a sites perigosos. Tipo de valor é o número inteiro. Se habilitar essa configuração, proteção de rede está ativada e os funcionários não podem desativá-la. Seu comportamento pode ser controlado pelas seguintes opções: Bloco e de auditoria. Se ativar esta política com a opção "Bloquear", os utilizadores e aplicações estão bloqueadas de se ligar a domínios perigosos. Pode ver esta atividade no Centro de segurança do Windows Defender. Se ativar esta política com a opção "Auditoria", os utilizadores/aplicações não serão bloqueadas se a domínios perigosos. No entanto, ainda verá esta atividade no Centro de segurança do Windows Defender. Se desativar esta política, os utilizadores/aplicações não serão bloqueadas se a domínios perigosos. Não verá qualquer atividade de rede no Centro de segurança do Windows Defender. Se não configurar esta política, o bloqueio de rede está desativada por predefinição.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **Predefinido**: Ativar
  
- **Agendar dia da análise do Defender**  
  Defender agendar dia da análise.
  
  **Predefinido**: todos os dias
  
- **Proteção fornecida pela cloud**  
  Para proteger melhor o seu PC, o Windows Defender irá enviar informações à Microsoft sobre quaisquer problemas que encontra. Microsoft irá analisar essas informações, obter mais informações sobre problemas que afetam o utilizador e outros clientes e oferecer soluções aprimoradas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Predefinido**:  Sim  

- **Defender potencialmente indesejado ação da aplicação**  
  A funcionalidade de proteção de aplicação potencialmente indesejável (PUA) no Windows Defender Antivirus pode identificar e bloquear PUAs transfiram e instalem em pontos finais na sua rede. Esses aplicativos não são considerados vírus, malware ou outros tipos de ameaças, mas podem executar ações nos pontos de extremidade que negativamente afetam o desempenho ou a utilizam. PUA também pode consultar os aplicativos que são considerados como tendo uma reputação ruim. Um comportamento típico PUA inclui: Vários tipos de software agrupamento injeção do Ad em navegadores da web Driver e otimizadores de registo que detetar problemas, pagamento de pedido para corrigir os erros, mas permanecem no ponto final e fazer sem alterações ou otimizações (também conhecido como programas de "não autorizados antivírus"). Esses aplicativos podem aumentar o risco da sua rede que está a ser infetado com software maligno, fazer com que infeções de software maligno ser mais difícil para identificar e pode desperdiçar recursos de TI em Limpar as aplicações.  
  [Saiba mais](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Predefinido**: Bloquear  

- **Tipo de código de macro de oculto de script**  
  Software maligno e outras ameaças podem tentar ofuscar ou ocultar o respetivo código malicioso em alguns arquivos de script. Esta regra impede que os scripts que parecem estar ocultado a execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Predefinido**: Bloquear
  
- **Analisar unidades amovíveis durante uma análise completa**  
  Permite que o Windows Defender analisar quanto a software mal-intencionado e indesejado em unidades amovíveis (por exemplo, unidades flash) durante uma análise completa. Antivírus do Windows Defender analisa todos os ficheiros em dispositivos USB antes da execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Predefinido**: Sim  
  
- **Analisar ficheiros de arquivo**  
  O Defender analise ficheiros de arquivo.
  
  **Predefinido**: Sim
  
- **Monitorização de comportamento**  
  Permite ou proíbe a funcionalidade de monitorização de comportamento do Windows Defender. Incorporado no Windows 10, destes sensores a recolhem e processam sinais comportamentais do sistema operacional e envia estes dados de sensor para sua instância de cloud privada, isolados, do Microsoft Defender ATP.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Predefinido**: Sim

- **Analisar ficheiros abertos a partir de pastas de rede**  
  Se os ficheiros são só de leitura, o utilizador não será capaz de remover qualquer software maligno detetado.
  
  **Predefinido**: Sim

- **Tipo de processo USB não fidedigno**  
  Com esta regra, os administradores podem impedir que ficheiros executáveis não assinados ou não fidedignos em execução a partir de unidades amovíveis USB, incluindo cartões SD.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Predefinido**: Bloquear
  
- **Aplicações do Office outros processam o tipo de injeção**  
  Aplicações do Office, incluindo o Word, Excel, PowerPoint e OneNote, não poderá injetar código noutros processos. Isso é normalmente utilizado por software maligno para executar código malicioso numa tentativa de ocultar a atividade de mecanismos de verificação de antivírus.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Predefinido**:  Bloquear
  
- **Código de macro do Office que tipo de importações do Win32**  
  Software maligno pode utilizar o código de macro ficheiros do Office para importar e carregar DLLs Win32, o que, em seguida, pode ser utilizado para efetuar chamadas de API para permitir a infecção em todo o sistema. Esta regra tenta bloquear ficheiros do Office que contêm código de macro que é capaz de importar as Win32 DLLs. Isto inclui Word, Excel, PowerPoint e OneNote.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Predefinido**: Bloquear  
  
- **Nível de bloco de nuvem do Defender**  
  Nível de bloco do Defender na cloud.
  
  **Predefinido**: Não Configurado

- **Monitorização em tempo real**  
  Defender requer a monitorização em tempo real.
  
  **Predefinido**: Sim
 
- **Lançamento de aplicações do Office communication num processo filho**  

  **Predefinido**:  Ativar

- **Office aplicações executável criação ou lançamento tipo de conteúdo**  
  Esta regra destina-se comportamentos comuns utilizados por suplementos suspeitos e maliciosos e scripts (extensões), que criam ou iniciar ficheiros executáveis. Essa é uma técnica de malware típico. As extensões são bloqueadas sejam utilizados pelas aplicações do Office. Normalmente, estas extensões utilizam o Windows Scripting Host (.wsh ficheiros) para executar scripts que automatizar determinadas tarefas ou fornecer funcionalidades de suplemento criados pelo utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Predefinido**: Bloquear

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender  
Para obter mais informações, consulte [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) na documentação de protocolos do Windows.  

- **Domínio do perfil de firewall**  
  Especifica os perfis ao qual pertence a regra: Domain, Private, Public. Este valor representa o perfil para redes que estão ligados a domínios.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Ligações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Ligações de saída necessárias**  
    **Predefinido**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Firewall ativada**  
    **Predefinido**: Permitido

- **Perfil da Firewall do público**  
  Especifica os perfis ao qual pertence a regra: Domain, Private, Public. Este valor representa o perfil para redes públicas. Estas redes são classificadas como públicas pelos administradores do host de servidor. A classificação aparece na primeira vez que o anfitrião se conecta à rede. Normalmente, estas redes são aqueles em aeroportos e cafés e outros locais públicos, onde os elementos de rede na rede ou o administrador de rede não são confiáveis.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Ligações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Ligações de saída necessárias**  
    **Predefinido**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Firewall ativada**  
    **Predefinido**: Permitido

  - **Regras de segurança de ligação da política de grupo não intercaladas**  
    **Predefinido**: Sim

  - **Regras de política da política de grupo não intercaladas**  
    **Predefinido**: Sim

- **Perfil da firewall privada**  
  Especifica os perfis ao qual pertence a regra: Domain, Private, Public. Este valor representa o perfil para redes privadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067041)  

   - **Ligações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Ligações de saída necessárias**  
    **Predefinido**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Predefinido**: Sim

  - **Firewall ativada**  
    **Predefinido**: Permitido

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas  
- **Exigir anti-spoofing avançado, quando disponível**  
  Se Sim, dispositivos utilizarão antisspoofing avançado, quando disponível. Se não, antisspoofing será bloqueado. Não configurado, serão aplicadas as configurações no cliente definidas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Predefinido**: Sim

- **Configurar o Windows Hello para empresas**   
  Windows Hello para empresas é um método alternativo para iniciar sessão no Windows, substituindo as palavras-passe, Smart Cards e Smart Cards virtuais. Se ativar ou não configurar esta definição de política, o dispositivo Aprovisiona Windows Hello para empresas. Se desativar esta definição de política, o dispositivo não aprovisionar o Windows Hello para empresas para qualquer utilizador.

  **Predefinido**: Sim

- **Exigir minúsculas no PIN**  
  Se for necessário, PIN do utilizador tem de incluir, pelo menos, uma letra minúscula.

  **Predefinido**: Permitido

- **Exigir carateres especiais no PIN**  
  Se for necessário, PIN do utilizador tem de incluir, pelo menos, um caráter especial.

  **Predefinido**: Permitido

- **Comprimento mínimo do PIN**  
  Comprimento mínimo do PIN tem de ter entre 4 e 127.

  **Predefinido**: 6

- **Exigir maiúsculas no PIN**  
  Se for necessário, PIN do utilizador tem de incluir, pelo menos, uma letra maiúscula.

  **Predefinido**: Permitido

## <a name="windows-ink-workspace"></a>Área de trabalho do Windows Ink  
Para obter mais informações, consulte [CSP de política - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) na documentação do Windows.  

- **Área de trabalho do Ink**  
  Especifica se pretende permitir que o utilizador aceda à área de trabalho da ink. 
  - *Desativada* -acesso à tinta a área de trabalho está desativado. A funcionalidade está desativada.
  - *Ativado* - funcionalidade da área de trabalho do Ink está ativada, mas o utilizador não é possível aceder à mesma acima do ecrã de bloqueio.
  - *Não configurado* - funcionalidade da área de trabalho do Ink está ativada e o utilizador pode utilizá-lo acima do ecrã de bloqueio.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Predefinido**: Enabled
 
## <a name="windows-powershell"></a>Windows PowerShell  
Para obter mais informações, consulte [CSP de política - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) na documentação do Windows.  

- **Script de shell do shell de energia bloquear o Registro em log**  
  Esta definição de política ativa o registo de todas as entradas de script do PowerShell para o registo de eventos da Microsoft-Windows-PowerShell/Operational. Se ativar esta definição de política, o Windows PowerShell irá iniciar o processamento de comandos, blocos de script, funções e scripts - se invocada interativamente ou através da automatização. Se desativar esta definição de política, o registo de entrada de script do PowerShell está desativado. Se ativar o registo de invocação de bloco do Script, o PowerShell adicionalmente regista eventos quando a invocação de um comando, o bloco de script, a função ou o script inicia ou para. Ativar o registo de invocação gera um grande volume de registos de eventos. Nota: Esta definição de política existe na configuração do computador e configuração do usuário no Editor de diretiva de grupo. A definição de política de configuração do computador tem precedência sobre a definição de política de configuração do usuário.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Predefinido**: Enabled

## <a name="whats-changed-in-the-new-template"></a>O que mudou no novo modelo
O *linha de base de segurança de MDM para atualização de Spring 2019 (1 de 19 horas)* modelo tem as seguintes alterações da *pré-visualização* modelo.

### <a name="changes-to-the-baseline-settings"></a>Alterações às definições de linha de base
As seguintes definições são:
- *Novo* nesta versão mais recente da linha de base.
- *Removido* desta versão de linha de base mais recente, mas estavam presentes na versão anterior.
- *Revisto* de alguma forma de como as definições apareceram na versão anterior. 

*[Novo]*  [ **Acima bloqueio**](#above-lock):
-  **Voz ativar aplicações a partir do ecrã bloqueado**    

*[Novo]*  [ **Gestão de aplicações**](#application-management): 
- **Controle de usuário de bloco através de instalações**  
- **Instalações de aplicações do bloco MSI com privilégios elevados**  

*[Removido]*  [ **Bitlocker**](#bitlocker):  
- Política de unidade amovível cacifo de bits > **método de encriptação**
- **Cacifo de bit fixo de política de unidade** *(todas as definições)*
- **Política de unidade de sistema do cacifo de bit** *(todas as definições)*

*[Novo]*  [ **Conectividade**](#connectivity):
- **Configurar o acesso seguro aos caminhos UNC**

*[Novo]*  [ **Device Guard**](#device-guard):
- **Segurança de Virtualização com base em**


*[Novo]*  [ **DMA Guard**](#dma-guard):
- **Enumeração de dispositivos externos incompatíveis com a proteção do DMA de Kernel**  

*[Novo]*  [ **Internet Explorer**](#internet-explorer):
- **Atualizações de zona de internet Explorer a barra de status por meio de script**
- **Zona de internet do Internet Explorer arrastar e soltar ou copiar e colar ficheiros**  
- **Componentes da habilitação do .NET Framework de zona restritos do Internet Explorer**  
- **Zona de computador local do Internet Explorer não execute antimalware controles Active X**
- **Suporte de encriptação do Internet Explorer**  

*[Revisto]*  [ **Internet Explorer**](#internet-explorer):
- **Prompt automática do Internet Explorer internet zona para transferências de ficheiros** > o valor predefinido é agora **desativado**. Em pré-visualização, esse era definido como ativado.

*[Novo]*  [ **Assistência remota**](#remote-assistance):  
- **Assistência remota solicitada** 
  - **Assistência remota solicitado permissão**
  - **Valor de tempo máximo do pedido de suporte**  
  - **Período de tempo de pedido de suporte máximo**  
  - **Método de convite por email**


*[New]* [**WIndows Defender**](#windows-defender):
- **Criar o leitor Adobe num processo filho**  
- **Lançamento de aplicações do Office communication num processo filho** 

*[New]* [**Windows Defender Firewall**](#windows-defender-firewall)
- **Domínio do perfil de firewall**  
  - **Ligações de entrada bloqueadas**  
  - **Ligações de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall ativada**  
- **Perfil da Firewall do público**  
  - **Ligações de entrada bloqueadas**  
  - **Ligações de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall ativada** 
  - **Regras de segurança de ligação da política de grupo não intercaladas**   
  - **Regras de política da política de grupo não intercaladas**  
- **Perfil da firewall privada**  
  - **Ligações de entrada bloqueadas**  
  - **Ligações de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall ativada**  

*[Novo]*  [ **Windows Hello para empresas**](#windows-hello-for-business):  
- **Exigir anti-spoofing avançado, quando disponível**  
- **Configurar o Windows Hello para empresas**  
- **Exigir minúsculas no PIN** 
- **Exigir carateres especiais no PIN** 
- **Comprimento mínimo do PIN**  
- **Exigir maiúsculas no PIN** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Windows Defender SmartScreen. Enabling this policy turns off Windows Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Windows defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Windows Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Windows Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Windows Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Windows Defender Exploit Guard. Network protection is a feature of Windows Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Windows Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Windows Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Windows Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Windows Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Windows Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Windows Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Windows Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
