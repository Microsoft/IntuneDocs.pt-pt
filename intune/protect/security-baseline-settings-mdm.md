---
title: Definições de base de segurança insinadas para o Windows 10
titleSuffix: Microsoft Intune
description: Reveja as predefinições e as definições disponíveis que se encontram na linha de segurança do Windows MDM para dispositivos Windows 10 que gere com o Intune.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff7d3b39dc7675a00c5fba204609848f28a64dab
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977840"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Definições de base de segurança do MDM para Intune  

Ver as definições de base de segurança do MDM que o Microsoft Intune suporta para dispositivos que executam o Windows 10 ou mais tarde. Os valores predefinidos para as definições nesta linha de base representam a configuração recomendada para dispositivos aplicáveis, e podem não corresponder às predefinições de base de outras linhas de base de segurança.  

A versão mais recente é MDM **Security Baseline para maio de 2019**  

Para saber o que mudou na versão mais recente desta linha de base, veja [o que mudou no novo modelo.](#whats-changed-in-the-new-template)  

> [!NOTE]  
> Em junho de 2019, a linha de base de segurança do MDM de pré-visualização foi substituída pela libertação do modelo de Base de Segurança do MDM para maio de *2019,* que geralmente está disponível (não em pré-visualização). Os perfis criados antes da disponibilidade da linha de base de segurança do MDM para maio de *2019* não serão atualizados para refletir as definições e valores que estão na linha de base de segurança do MDM para maio de 2019.  Embora não possa criar novos perfis com base no modelo de pré-visualização, pode editar e continuar a utilizar perfis que criou anteriormente baseados no modelo de pré-visualização. 
  
Para aprender a usar as linhas de base de segurança com o Intune, consulte use as linhas de base de [segurança](security-baselines.md).  

## <a name="above-lock"></a>Acima do bloqueio  
Para mais informações, consulte [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) na documentação do Windows.  

- **Exibição por bloco de notificações de torradas**  
  Esta definição de política permite evitar que as notificações das aplicações apareçam no ecrã de bloqueio. Se ativar esta definição de política, não são apresentadas notificações de aplicações no ecrã de bloqueio. Se desativar ou não configurar esta definição de política, os utilizadores podem escolher quais as aplicações que exibem notificações no ecrã de bloqueio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Padrão**: Sim  

- **Aplicativos de ativação de voz a partir de ecrã bloqueado**  

  **Predefinição**: Desativado

## <a name="app-runtime"></a>Tempo de execução da aplicação    
Para mais informações, consulte [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) na documentação do Windows.  

- **Microsoft conta opcional para aplicações da Windows Store**  
  Esta definição de política permite controlar se as contas da Microsoft são opcionais para aplicações da Windows Store que exigem uma conta para iniciar sessão. Esta política apenas afeta aplicações da Windows Store que a suportam. Se ativar esta definição de política, as aplicações da Windows Store que normalmente exigem uma conta Microsoft para iniciar sessão permitirão que os utilizadores assinem com uma conta empresarial. Se desativar ou não configurar esta definição de política, os utilizadores devem iniciar sessão com uma conta Microsoft.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Predefinição**: Ativado  

## <a name="application-management"></a>Gestão de Aplicações   
Para mais informações, consulte [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) na documentação do Windows.  

- **Bloqueie o controlo do utilizador sobre as instalações**  
  Esta definição de política permite que os utilizadores alterem as opções de instalação que normalmente estão disponíveis apenas para administradores do sistema. Se ativar esta definição de política, algumas das funcionalidades de segurança do Instalador do Windows são ignoradas. Permite que as instalações completem que, de outra forma, seriam interrompidas devido a violação de segurança. Se desativar ou não configurar esta definição de política, as funcionalidades de segurança do Instalador do Windows impedem que os utilizadores mudem as opções de instalação normalmente reservadas aos administradores do sistema, tais como especificar o diretório para o qual os ficheiros estão instalados. Se o Instalador do Windows detetar que um pacote de instalação permitiu ao utilizador alterar uma opção protegida, esta para a instalação e exibe uma mensagem. Estas funcionalidades de segurança funcionam apenas quando o programa de instalação funciona num contexto de segurança privilegiado e tem acesso a diretórios negados ao utilizador. Esta definição de política destina-se a ambientes menos restritivos. Pode ser usado para contornar erros num programa de instalação que impede a instalação do software.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Padrão**: Sim

- **Bloquear instalações de aplicativos com privilégios elevados**  
  Esta definição de política direciona o Instalador do Windows a utilizar permissões elevadas quando instala qualquer programa no sistema.  
  - *Se permitir esta definição*de política, os privilégios são alargados a todos os programas. Normalmente, estes privilégios são reservados para programas que tenham sido atribuídos ao utilizador (oferecidos no ambiente de trabalho), atribuídos ao computador (instalado automaticamente)f, ou disponibilizados em Programas Add ou Remove no Painel de Controlo. Esta definição de perfil permite que os utilizadores instalem programas que requerem acesso a diretórios que o utilizador possa não ter permissão para visualizar ou alterar, incluindo diretórios em computadores altamente restritos.
  - *Se desativar ou não configurar esta definição*de política, o sistema aplica as permissões do utilizador atual quando instala programas que um administrador do sistema não distribui ou oferece. Nota: Esta definição de política aparece tanto nas pastas de Configuração do Computador como na Configuração do Utilizador. Para tornar esta definição de política eficaz, deve ative-a em ambas as pastas. Atenção: Os utilizadores qualificados podem tirar partido das permissões que esta definição de políticas concede para alterar os seus privilégios e obter acesso permanente a ficheiros e pastas restritas. Note que a versão de Configuração do Utilizador desta definição de política não é garantida para ser segura.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Padrão**: Sim

- **Block game DVR (apenas desktop)**  
  Configura se é permitida a gravação e a transmissão de jogos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Padrão**: Sim  

## <a name="auto-play"></a>Reprodução automática   
Para mais informações, consulte [Policy CSP - Reprodução automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) na documentação do Windows.  

- **Comportamento de execução automática de reprodução automática de reprodução automática**  
  Esta definição afeta o comportamento padrão dos comandos Autorun. Os comandos Autorun são armazenados em ficheiros autorun.inf e podem lançar programas de instalação ou outras rotinas. Quando *ativado,* os administradores podem alterar o comportamento de autorun predefinido num dispositivo que executa o Windows Vista ou posteriormente. O comportamento pode ser definido para: a) desativar completamente os comandos autorun, ou b) reverter para o comportamento pré-Windows Vista de executar automaticamente o comando autorun. Quando definido para *Desativado* ou *Não Configurado*, os dispositivos que executam o Windows Vista ou posteriormente solicitam ao utilizador se um comando autorun deve ser executado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Predefinição**: Não executar  
  
- **Modo de reprodução automática**  
  Esta definição de política permite-lhe desligar a função De Reprodução Automática. A reprodução automática começa a ler a partir de uma unidade assim que inserir os meios de comunicação na unidade. Como resultado, o arquivo de configuração de programas e a música nos meios de áudio começam imediatamente. Antes do Windows XP SP2, a Reprodução automática é desativada por padrão em unidades amovíveis, como a unidade de disco floppy (mas não a unidade DeC-ROM) e nas unidades de rede. Começando pelo Windows XP SP2, a Reprodução Automática também está ativada para unidades amovíveis, incluindo unidades Zip e alguns dispositivos de armazenamento de massa USB. Se ativar esta definição de política, a Reprodução automática é desativada em CD-ROM e unidades de mídia amovíveis ou desativada em todas as unidades. Esta definição de política desativa a reprodução automática em tipos adicionais de unidades. Não é possível utilizar esta definição para ativar a Reprodução Automática nas unidades em que é desativada por defeito. Se desativar ou não configurar esta definição de política, o AutoPlay está ativado. Nota: Esta definição de política aparece tanto nas pastas de Configuração do Computador como na Configuração do Utilizador. Se as definições de política forem contraditórias, a definição de política na Configuração do Computador tem precedência sobre a definição de política na Configuração do Utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Predefinição**: Desativado

- **Bloquear a reprodução automática para dispositivos não volume**  
  Esta definição de política proíbe o AutoPlay para dispositivos MTP, como câmaras ou telefones. Se ativar esta definição de política, o AutoPlay não é permitido para dispositivos MTP como câmaras ou telefones. Se desativar ou não configurar esta definição de política, o AutoPlay está ativado para dispositivos não volume.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Predefinição**: Ativado  

## <a name="bitlocker"></a>BitLocker    
Para mais informações, consulte [Policy CSP - BitLocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) na documentação do Windows.  

- **Política de unidade amovível BitLocker**  
  Esta definição de política é usada para controlar o método de encriptação e a força da cifra. Os valores desta política determinam a força da cifra que o BitLocker utiliza para encriptação. As empresas podem querer controlar o nível de encriptação para uma maior segurança (a AES-256 é mais forte do que a AES-128). Se ativar esta definição, será capaz de configurar um algoritmo de encriptação e uma força de cifra chave para unidades de dados fixas, unidades do sistema operativo e unidades de dados amovíveis individualmente. Para unidades fixas e funcionais do sistema, recomendamos que utilize o algoritmo XTS-AES. Para unidades amovíveis, deve utilizar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for utilizada noutros dispositivos que não estejam a executar o Windows 10, versão 1511 ou mais tarde. A alteração do método de encriptação não tem qualquer efeito se a unidade já estiver encriptada ou se a encriptação estiver em curso. Nestes casos, esta definição de política é ignorada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Para a política de unidade amovível BitLocker, configure a seguinte definição:

  - **Exigir encriptação para o acesso à escrita**  
    **Padrão**: Sim  
  

## <a name="browser"></a>Browser  
Para mais informações, consulte [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) na documentação do Windows.  

- **Requerer smartScreen para microsoft edge**  
  O Microsoft Edge utiliza o Microsoft Defender SmartScreen (ligado) para proteger os utilizadores de potenciais esquemas de phishing e software malicioso por padrão. Além disso, por padrão, os utilizadores não podem desativar (desligar) o Microsoft Defender SmartScreen. Ativar esta política desliga o Microsoft Defender SmartScreen e impede que os utilizadores o desliguem. Não configure esta política para permitir que os utilizadores optem por ligar ou desligar o SmartScreen do Microsoft.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Padrão**: Sim  
  
- **Bloqueie o acesso malicioso ao site**  
  Por padrão, o Microsoft Edge permite que os utilizadores contornem (ignore) os avisos do Microsoft Defender SmartScreen sobre sites potencialmente maliciosos, permitindo-lhes continuar no site. No entanto, com esta política, pode configurar o Microsoft Edge para evitar que os utilizadores convertem os avisos, impedindo-os de continuarem no site.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Padrão**: Sim  
  
- **Bloquear o download de ficheiros não verificados**  
  Por predefinição, o Microsoft Edge permite que os utilizadores contornem (ignore) os avisos do Microsoft Defender SmartScreen sobre ficheiros potencialmente maliciosos, permitindo-lhes continuar a descarregar os ficheiros não verificados. Permitir esta política impede que os utilizadores convertem os avisos, impedindo-os de descarregar os ficheiros não verificados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Padrão**: Sim  
  
- **Gestor de passwords de bloco**  
  Por padrão, o Microsoft Edge utiliza o Password Manager automaticamente, permitindo que os utilizadores registem senhas localmente. A desativação desta política impede o Microsoft Edge de utilizar o Password Manager. Não configure esta política se pretender que os utilizadores optem por guardar e gerir senhas localmente utilizando o Password Manager.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Padrão**: Sim  
  
- **Evitar a sobreposições de erros do certificado**  
  Esta definição de política impede o utilizador de ignorar erros de certificado de segurança de camadas seguras (SSL/TLS) que interrompem a navegação (tais como erros "expirados", "revogados" ou "desajuste de nomes") no Internet Explorer. Se ativar esta definição de política, o utilizador não pode continuar a navegar. Se desativar ou não configurar esta definição de política, o utilizador pode optar por ignorar erros de certificado e continuar a navegar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Padrão**: Sim  

## <a name="connectivity"></a>Conectividade  
Para mais informações, consulte [Política CSP - Conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) na documentação do Windows.  

- **Bloquear o download da Internet para publicações web e assistentes de encomendas online**  
  Esta definição de política especifica se o Windows deve descarregar uma lista de fornecedores para os assistentes de publicação web e encomendas online. Estes assistentes permitem que os utilizadores selecionem a partir de uma lista de empresas que fornecem serviços como armazenamento on-line e impressão fotográfica. Por padrão, o Windows apresenta fornecedores descarregados de um website do Windows, além dos fornecedores especificados no registo. Se ativar esta definição de política, o Windows não descarrega fornecedores e apenas os prestadores de serviços que estão em cache no ecrã do registo local. Se desativar ou não configurar esta definição de política, uma lista de fornecedores descarrega quando o utilizador utiliza os assistentes de publicação web ou de encomendas online. Para mais informações que incluam detalhes sobre a especificação dos prestadores de serviços no registo, consulte a documentação para a publicação web e assistentes de encomendas online.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Predefinição**: Ativado  

- **Configure o acesso seguro aos caminhos da CNU**  
  Esta definição de políticas configura o acesso assegurado aos caminhos da CNU. Se ativar esta política, o Windows só permite o acesso aos caminhos específicos do CNU após o cumprimento de requisitos de segurança adicionais.
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **Predefinição**: Configure o Windows apenas para permitir o acesso aos caminhos específicos da CNU após o cumprimento de requisitos adicionais de segurança
  
  Quando *Configurar o Windows para permitir somente o acesso aos caminhos UNC especificados depois de atender aos requisitos de segurança adicionais* estiver selecionado, você poderá configurar a lista de caminhos UNC * LSN.
  - **Lista de caminhos endurecidos do CNU**  
    Selecione **Adicionar** para especificar bandeiras de segurança adicionais e caminhos do servidor.  

- **Bloquear o download de condutores de impressão em HTTP**  
  Esta definição de política especifica se permite que este cliente descarregue os pacotes de controladores impressos em HTTP. Para configurar a impressão HTTP, os condutores que não inbox precisam de ser descarregados em HTTP. Nota: Esta definição de política não impede o cliente de imprimir para impressoras na Intranet ou na Internet através de HTTP. Apenas proíbe o download de condutores que ainda não estejam instalados localmente. Se ativar esta definição de política, os controladores de impressão não podem ser descarregados em HTTP. Se desativar ou não configurar esta definição de política, os utilizadores podem descarregar os controladores de impressão em HTTP.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Predefinição**: Ativado  

## <a name="credentials-delegation"></a>Delegação de Credenciais  
Para mais informações, consulte [Política CSP - CredenciaisDelegação](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) na documentação do Windows.  

- **Delegação remota de hospedeiros de credenciais não exportáveis**  
  O hospedeiro remoto permite a delegação de credenciais não exportáveis. Ao utilizar a delegação credencial, os dispositivos fornecem uma versão exportável de credenciais ao hospedeiro remoto, o que expõe os utilizadores ao risco de roubo de credenciais de agressores no hospedeiro remoto. Se ativar esta definição de política, o hospedeiro suporta o modo Detenção Restrita ou Guarda Credencial Remota. Se desativar ou não configurar esta definição de política, a Administração Restrita e o modo de Guarda Credencial Remota não são suportados. O utilizador terá sempre de passar as suas credenciais ao anfitrião.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Predefinição**: Ativado  

## <a name="credentials-ui"></a>Credenciais UI  
Para mais informações, consulte [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) na documentação do Windows.  

- **Enumerar administradores** Esta definição de política controla se as contas do administrador exibem quando um utilizador tenta elevar uma aplicação em execução. Por predefinição, as contas do administrador não são apresentadas quando o utilizador tenta elevar uma aplicação de execução. Se ativar esta definição de política, todas as contas do administrador local no visor do PC para que o utilizador possa escolher uma e introduzir a palavra-passe correta. Se desativar esta definição de política, os utilizadores serão sempre obrigados a escrever um nome de utilizador e uma palavra-passe para elevar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Predefinição**: Desativado  

## <a name="data-protection"></a>Proteção de dados  
Para mais informações, consulte [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) na documentação do Windows.  

- **Bloquear o acesso à memória direta**  
  Esta definição de política permite bloquear o acesso à memória direta (DMA) para todas as portas a jusante pluggable a quente até que um utilizador inicie sessão no Windows. Assim que um utilizador iniciar sessão, o Windows enumerará os dispositivos PCI ligados às portas PCI plug do hospedeiro. Sempre que o utilizador bloqueia a máquina, o DMA é bloqueado em portas PCI de ficha quente sem dispositivos para crianças até que o utilizador volte a entrar. Os dispositivos que já estavam enumerados quando a máquina foi desbloqueada continuarão a funcionar até desligarem a tomada. Esta definição de política só é aplicada quando o BitLocker ou a encriptação do dispositivo estiverem ativadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Padrão**: Sim  

## <a name="device-guard"></a>Guarda de Dispositivos  
Para mais informações, consulte [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) na documentação do Windows.  

- **Guarda Credencial**  
  Esta definição permite que os utilizadores liguem a Guarda Credencial com segurança baseada em virtualização para ajudar a proteger as credenciais no próximo reboot.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Predefinição**: Ativar com bloqueio UEFI 

- Ativar  de **segurança baseadas em virtualização**  
  Liga a segurança baseada em virtualização (VBS) no próximo reboot. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Padrão**: Sim  


- **  ** de guarda do sistema de lançamento  
  **Predefinição**: Ativado  

## <a name="device-installation"></a>Instalação de Dispositivos  
Para mais informações, consulte [Policy CSP - Instalação](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) de Dispositivos na documentação do Windows.  

- **Instalação de dispositivos de hardware por identificadores de dispositivos**  
  Esta definição de política permite especificar uma lista de IDs de hardware plug e play e IDs compatíveis para dispositivos que o Windows está impedido de instalar. Esta definição de política tem precedência sobre qualquer outra definição de política que permita ao Windows instalar um dispositivo. Se ativar esta definição de política, o Windows está impedido de instalar um dispositivo cujo ID de hardware ou ID compatível aparece na lista que cria. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a definição de política afeta a reorientação dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desativar ou não configurar esta definição de política, os dispositivos podem instalar e atualizar conforme permitido ou impedido por outras definições de política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **Predefinição**: Bloquear a instalação de dispositivos de hardware  

  Quando a instalação do *dispositivo de hardware block* for selecionada, as seguintes definições estão disponíveis.

  - **Remova dispositivos de hardware correspondentes**   
    Esta definição só está disponível quando a instalação de dispositivos de *hardware por identificadores* de dispositivo saem definidas para bloquear a instalação do dispositivo de *hardware*.
    
    **Padrão**: Sim

  - **Identificadores de dispositivos de hardware que estão bloqueados**  
    Esta definição só está disponível quando a instalação de dispositivos de *hardware por identificadores* de dispositivo saem definidas para bloquear a instalação do dispositivo de *hardware*.
    
    **Padrão**: Sim  
  
- **Instalação de dispositivos de hardware por classes de configuração**  
  Esta definição de política permite especificar uma lista de identificadores de configuração de dispositivos globalmente únicos (GUIDs) para os controladores de dispositivos que o Windows está impedido de instalar. Esta definição de política tem precedência sobre qualquer outra definição de política que permita ao Windows instalar um dispositivo. Se ativar esta definição de política, o Windows está impedido de instalar ou atualizar os controladores do dispositivo cuja classe GUIDs de configuração do dispositivo aparece na lista que cria. Se ativar esta definição de política num servidor de ambiente de trabalho remoto, a definição de política afeta a reorientação dos dispositivos especificados de um cliente de ambiente de trabalho remoto para o servidor de ambiente de trabalho remoto. Se desativar ou não configurar esta definição de política, o Windows pode instalar e atualizar dispositivos conforme permitido ou impedido por outras definições de política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Predefinição**: Bloquear a instalação de dispositivos de hardware  

  Quando a instalação do *dispositivo de hardware block* for selecionada, as seguintes definições estão disponíveis.
  - **Remova dispositivos de hardware correspondentes**    
    Esta definição só está disponível quando a instalação do *dispositivo de hardware por classes* de configuração estiver definida para bloquear a instalação de dispositivos de *hardware*.  

    **Predefinição**: *Nenhuma configuração predefinida*  

  - **Identificadores de dispositivos de hardware que estão bloqueados**  
    Esta definição só está disponível quando a instalação do *dispositivo de hardware por classes* de configuração estiver definida para bloquear a instalação de dispositivos de *hardware*.
    
    **Predefinição**: *Nenhuma configuração predefinida*  

## <a name="device-lock"></a>Bloqueio de dispositivos  
Para mais informações, consulte [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) na documentação do Windows.  

- **Impedir o uso da câmara**  
  Desativa o interruptor de alternância da câmara de bloqueio nas definições do PC e impede que uma câmara seja invocada no ecrã de bloqueio. Por predefinição, os utilizadores podem ativar a invocação de uma câmara disponível no ecrã de bloqueio. Se ativar esta definição, os utilizadores deixarão de poder ativar ou desativar o acesso da câmara de bloqueio nas definições do PC, e a câmara não pode ser invocada no ecrã de bloqueio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Predefinição**: Ativado  

- **Exigir senha**  
  Especifica se o bloqueio do dispositivo está ativado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Padrão**: Sim  
  
  Quando *a palavra-passe requerida* for definida para *Sim,* as seguintes definições estão disponíveis.

  - **Contagem mínima de caracteres de palavra-passe**  
    O número de tipos de elementos complexos (letras maiúsculas e minúsculas, números e pontuação) necessários para um PIN ou palavra-passe forte. Pin aplica o seguinte comportamento para dispositivos de ambiente de trabalho e dispositivos móveis: 1 - Dígitos apenas 2 - Dígitos e letras minúsculas são necessários 3 - São necessários dígitos, letras minúsculas e letras maiúsculas. Não suportado nas contas desktop da Microsoft e nas contas de domínio. 4 - São necessários dígitos, letras minúsculas, letras maiúsculas e caracteres especiais. Não suportado no ambiente de trabalho. O valor predefinido é 1.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Padrão**: 3  

  - **Número de falhas de início de sessão antes de eliminar os dados do dispositivo**  
    O número de falhas de autenticação permitidas antes de o dispositivo ser apagado. Um valor de 0 desativa a funcionalidade de limpeza do dispositivo.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Padrão**: 10  

  - **Expiração da Palavra-passe (dias)**  
    A definição máxima da política de idade da palavra-passe determina a duração (em dias) de que uma palavra-passe pode ser utilizada antes de o sistema exigir que o utilizador a altere. Pode definir senhas para expirar após um número de dias entre 1 e 999, ou pode especificar que as palavras-passe nunca expiram definindo o número de dias a 0. Se a idade máxima da senha for entre 1 e 999 dias, a idade mínima da senha deve ser inferior à idade máxima da senha. Se a idade máxima da senha for fixada para 0, a idade mínima da senha pode ser qualquer valor entre 0 e 998 dias.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Padrão**: 60  

  - **Tipo obrigatório de palavra-passe**  
    Determina o tipo de PIN ou palavra-passe necessário.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Padrão**: Alfanumérico  

  - **Comprimento mínimo da palavra-passe**  
    A definição mínima de comprimento da palavra-passe determina o menor número de caracteres que podem compor uma palavra-passe para uma conta de utilizador. Pode definir um valor entre 1 e 14 caracteres, ou pode estabelecer que não é necessária nenhuma palavra-passe definindo o número de caracteres para 0.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Padrão**: 8  

  - **Bloqueie senhas simples**  
    Especifica se são permitidas PINs ou palavras-passe como "1111" ou "1234". Para o ambiente de trabalho, também controla a utilização de palavras-passe de imagem.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Padrão**: Sim  
      *Uma definição de Sim impede a utilização de senhas simples.* 

  - **Impedir a reutilização de palavras-passe anteriores**  
    Especifica quantas palavras-passe podem ser armazenadas na história que não podem ser usadas. O valor inclui a senha atual do utilizador. Por exemplo, com uma definição de *1* o utilizador não pode reutilizar a sua senha atual ao escolher uma nova senha. Uma definição de *5* significa que um utilizador não pode definir a sua nova palavra-passe para a sua senha atual ou qualquer uma das suas quatro senhas anteriores.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Predefinição**: 24  

- **Prevenir a apresentação de diapositivos**  
  Desativa as definições de apresentação de ecrã de bloqueio nas definições do PC e impede que uma apresentação de diapositivos seja reproduzido no ecrã de bloqueio. Por predefinição, os utilizadores podem ativar uma apresentação de diapositivos que será executada depois de bloquearem a máquina. Se ativar esta definição, os utilizadores não podem modificar as definições de apresentação de diapositivos nas definições do PC e nenhuma apresentação de diapositivos pode começar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Predefinição**: Ativado  
  *Uma definição de Ativado impede que os slides se esgotem.* 

- **Idade mínima da palavra-passe em dias**  
  A definição mínima de definição da idade da palavra-passe determina o período de tempo (em dias) que deve ser utilizada uma palavra-passe antes de o utilizador a alterar. Pode definir um valor entre 1 e 998 dias, ou pode permitir alterações de senha imediatamente, definindo o número de dias para 0. A idade mínima da palavra-passe deve ser inferior à idade máxima da senha, a menos que a idade máxima da senha esteja definida para 0, indicando que as palavras-passe nunca caducarão. Se a idade máxima da senha for fixada para 0, a idade mínima da senha pode ser definida para qualquer valor entre 0 e 998.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Padrão**: 1  

## <a name="dma-guard"></a>Guarda DMA  
Para mais informações, consulte [Policy CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) na documentação do Windows.
- **Enumeração de dispositivos externos incompatíveis com a Proteção Kernel DMA**  
  Esta política destina-se a proporcionar segurança adicional contra dispositivos externos capazes de DMA. Permite um maior controlo sobre a enumeração de dispositivos externos capazes de DMA incompatíveis com o isolamento da memória de DMA/dispositivo e o sandboxing. Esta política só entra em vigor quando a Kernel DMA Protection é suportada e ativada pelo firmware do sistema. Kernel DMA Protection é uma funcionalidade de plataforma que não pode ser controlada através da política ou do utilizador final. Tem de ser apoiado pelo sistema no momento da produção. Para verificar se o sistema suporta a Proteção Kernel DMA, verifique o campo de proteção Kernel DMA na página sumária do MSINFO32.exe.  
  [Saiba mais](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Padrão**: Bloquear tudo   

## <a name="event-log-service"></a>Serviço de Log de Eventos  
Para mais informações, consulte [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) na documentação do Windows.  

- **Tamanho máximo de ficheiro de registo de segurança em KB**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho máximo do ficheiro de registo entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobyte. Se desativar ou não configurar esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local utilizando o diálogo Log Properties e não se aplica a 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Padrão**: 196608  

- **Registo de sistema tamanho máximo de ficheiro em KB**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho máximo do ficheiro de registo entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobyte. Se desativar ou não configurar esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local utilizando o diálogo Log Properties e não se aplica a 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Predefinição**: 32768  

- **Registo de aplicação tamanho máximo de ficheiro em KB**  
  Esta definição de política especifica o tamanho máximo do ficheiro de registo em quilobytes. Se ativar esta definição de política, pode configurar o tamanho máximo do ficheiro de registo entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobyte. Se desativar ou não configurar esta definição de política, o tamanho máximo do ficheiro de registo está definido para o valor configurado localmente. Este valor pode ser alterado pelo administrador local utilizando o diálogo Log Properties e não se aplica a 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Predefinição**: 32768  

## <a name="experience"></a>Experiência  
Para mais informações, consulte [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentação.  

- **Holofotes das janelas de blocos**  
  Permite que os administradores de TI desliguem todas as funcionalidades do Windows Spotlight - Holofotes de janela no ecrã de bloqueio, Windows Tips, funcionalidades do consumidor da Microsoft e outras funcionalidades relacionadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Padrão**: Sim  

  Quando o *Block Windows Spotlight* estiver definido para *Sim,* as seguintes definições estão disponíveis.
  
  - **Bloqueie sugestões de terceiros no Windows Spotlight**  
    Especifica se permite sugestões de apps e conteúdos de editores de software de terceiros em funcionalidades de destaque do Windows, como os holofotes do ecrã de bloqueio, as aplicações sugeridas no menu Iniciar e as dicas do Windows. Os utilizadores podem ainda ver sugestões para funcionalidades, apps e serviços da Microsoft.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Padrão**: Sim  
  - **Bloqueie as funcionalidades específicas do consumidor**  
    Permite que os administradores de TI liguem experiências que normalmente são apenas para consumidores, tais como sugestões de Início, notificações de Adesão, instalação de apps pós-OOBE e azulejos redirecionados.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Padrão**: Sim  

## <a name="exploit-guard"></a>Explorar guarda  
Para mais informações, consulte [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) na documentação do Windows.  

- **Explorar a proteção XML**  
  Permite ao administrador de TI empurrar uma configuração que represente o sistema desejado e opções de mitigação de aplicações a todos os dispositivos da organização. A configuração é representada por um XML. A proteção de exploração ajuda a proteger os dispositivos de malware que usam explorações para espalhar e infetar. Utiliza a aplicação De Segurança do Windows ou powerShell para criar um conjunto de atenuações (conhecida como configuração). Em seguida, pode exportar esta configuração como um ficheiro XML e partilhá-la com várias máquinas na sua rede para que todas tenham o mesmo conjunto de definições de mitigação. Também pode converter e importar um ficheiro XML de configuração EMET existente numa configuração de proteção de exploração XML.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Padrão**: *A amostra xml é fornecida* 
 
## <a name="file-explorer"></a>Explorador de Ficheiros  
Para mais informações, consulte [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) na documentação do Windows.  

- **Bloquear a prevenção da execução de dados**  
  A desativação da prevenção da execução de dados pode permitir que certas aplicações plug-in do legado funcionem sem terminar o Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Predefinição**: Desativado  
   
- **Bloqueio de denúncia de corrupção**  
  A desativação da corrupção pode permitir que certas aplicações plug-in do legado funcionem sem terminar imediatamente o Explorer, embora o Explorer possa ainda terminar inesperadamente mais tarde.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Predefinição**: Desativado  
    

## <a name="internet-explorer"></a>Internet Explorer  
Para mais informações, consulte [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) na documentação do Windows.  

- **Internet Explorer limita atualizações de zona para barra de estado via script**  
  Esta definição de política permite-lhe gerir se o script é autorizado a atualizar a barra de estado dentro da zona. 
  - *Se ativar esta definição de política,* o script é permitido atualizar a barra de estado.
  - *Se desativar ou não configurar esta definição*de política, o script não está autorizado a atualizar a barra de estado.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Predefinição**: Desativado

- **Internet Explorer internet zone drag and drop or copy and paste files**  
  Esta definição de política permite-lhe gerir se os utilizadores podem arrastar ficheiros ou copiar e colar ficheiros a partir de uma fonte dentro da zona. Se ativar esta definição de política, os utilizadores podem arrastar ficheiros ou copiar e colar ficheiros desta zona automaticamente. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se devem arrastar ou copiar ficheiros desta zona. Se desativar esta definição de política, os utilizadores são impedidos de arrastar ficheiros ou copiar e colar ficheiros desta zona. Se não configurar esta definição de política, os utilizadores podem arrastar ficheiros ou copiar e colar ficheiros desta zona automaticamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Predefinição**: Desativar

- Zona restrita do **Internet Explorer .NET Estrutura componentes dependentes**    
  Esta definição de política permite-lhe gerir se os componentes .NET Framework que não estão assinados com a Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controlos geridos referenciados a partir de uma etiqueta de objeto e executáveis geridos referenciados a partir de um link. Se ativar esta definição de política, o Internet Explorer executará componentes geridos não assinados. Se selecionar O Aviso na caixa de lançamento, o Internet Explorer irá solicitar ao utilizador que determine se executa componentes geridos não assinados. Se desativar esta definição de política, o Internet Explorer não executará componentes geridos não assinados. Se não configurar esta definição de política, o Internet Explorer não executará componentes geridos não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Predefinição**: Desativar


- **A zona de máquina local do Internet Explorer não executa antimalware contra os controlos Ative X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware contra controlos ActiveX, para verificar se são seguros para carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se não configurar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Os utilizadores podem ligar ou desligar este comportamento, utilizando as definições de Segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Predefinição**: Desativado

- **Acesso à zona de internet do Internet Do Internet Explorer a fontes de dados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer pode aceder a dados de outra zona de segurança utilizando o Microsoft XML Parser (MSXML) ou ActiveX Data Objects (ADO). Se ativar esta definição de política, os utilizadores podem carregar uma página na zona que utiliza MSXML ou ADO para aceder a dados de outro site da zona. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem que uma página carregue na zona que utiliza mSXML ou ADO para aceder a dados de outro site da zona. Se desativar esta definição de política, os utilizadores não podem carregar uma página na zona que utiliza MSXML ou ADO para aceder a dados de outro site da zona. Se não configurar esta definição de política, os utilizadores não podem carregar uma página na zona que utiliza MSXML ou ADO para aceder a dados de outro site na zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer restringiu conteúdo de arrasto de zona de diferentes domínios dentro das janelas**  
  Esta definição de política permite-lhe definir opções para arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão na mesma janela. Se ativar esta definição de política e clicar em Ativar, os utilizadores podem arrastar o conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão na mesma janela. Os usuários não podem alterar essa configuração. Se ativar esta definição de política e clicar em Desativar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão na mesma janela. Os utilizadores não podem alterar esta definição no diálogo das Opções de Internet. No Internet Explorer 10, se desativar esta definição de política ou não configurar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão na mesma janela. Os utilizadores podem alterar esta definição no diálogo das Opções de Internet. No Internet Explorer 9 e versões anteriores, se desativar esta definição de política ou não configurar, os utilizadores podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão na mesma janela. Os utilizadores não podem alterar esta definição no diálogo das Opções de Internet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Predefinição**: Desativado
  
- **Aviso de desajuste de endereço do Internet Explorer**  
  Esta definição de política permite-lhe ativar o aviso de segurança de desajuste do endereço do certificado. Quando esta definição de política é ativada, o utilizador é avisado ao visitar websites Secure HTTP (HTTPS) que apresentam certificados emitidos para um endereço de site diferente. Este aviso ajuda a prevenir ataques de falsificação. Se ativar esta definição de política, o aviso de desajuste do endereço do certificado aparece sempre. Se desativar ou não configurar esta definição de política, o utilizador pode escolher se o aviso de desajuste do endereço de certificado aparece (utilizando a página Avançada no painel de Controlo de Internet).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Predefinição**: Ativado 
  
- **Internet Explorer zona restrita menos sites privilegiados**  
  Esta definição de política permite-lhe gerir se os Web sites de zonas menos privilegiadas, como sites de Internet, podem navegar para esta zona. Se ativar esta definição de política, os Web sites de zonas menos privilegiadas podem abrir novas janelas ou navegar para dentro desta zona. A zona de segurança funcionará sem a camada adicional de segurança fornecida pela função de segurança Protection from Zone Elevation. Se selecionar O Aviso na caixa de entrega, é emitido um aviso ao utilizador de que está prestes a ocorrer uma navegação potencialmente arriscada. Se desativar esta definição de política, possivelmente evita-se a navegação prejudicial. A funcionalidade de segurança do Internet Explorer está nesta zona, tal como definida pela Proteção contra o controlo da funcionalidade de elevação da zona. Se não configurar esta definição de política, as navegações possivelmente nocivas são evitadas. A funcionalidade de segurança do Internet Explorer está nesta zona, tal como definida pela Proteção contra o controlo da funcionalidade de elevação da zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer restrito de zona automática para downloads de ficheiros**  
  Esta definição de política determina se os utilizadores são solicitados para downloads de ficheiros não iniciados pelo utilizador. Independentemente desta definição, os utilizadores receberão diálogos de descarregamento de ficheiros para downloads iniciados pelo utilizador. Se ativar esta definição, os utilizadores receberão um diálogo de descarregamento de ficheiros para tentativas automáticas de descarregamento. Se desativar ou não configurar esta definição, os downloads de ficheiros que não são iniciados pelo utilizador estão bloqueados e os utilizadores verão a barra de Notificação em vez do diálogo de descarregamento de ficheiros. Os utilizadores podem então clicar na barra de Notificação para permitir o aviso de descarregamento do ficheiro.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Predefinição**: Desativado
  
- **Zona de internet do Internet Explorer .NET Estrutura componentes dependentes**  
  Esta definição de política permite-lhe gerir se os componentes .NET Framework que não estão assinados com a Authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controlos geridos referenciados a partir de uma etiqueta de objeto e executáveis geridos referenciados a partir de um link. Se ativar esta definição de política, o Internet Explorer executará componentes geridos não assinados. Se selecionar O Aviso na caixa de lançamento, o Internet Explorer irá solicitar ao utilizador que determine se executa componentes geridos não assinados. Se desativar esta definição de política, o Internet Explorer não executará componentes geridos não assinados. Se não configurar esta definição de política, o Internet Explorer executará componentes geridos não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Predefinição**: Desativar 
  
- **A zona de internet do Internet Explorer permite que apenas os domínios aprovados utilizem controlos Tdc ActiveX**  
  Esta definição de política controla se o utilizador puder executar o controlo TDC ActiveX nos websites. Se ativar esta definição de política, o controlo TDC ActiveX não será executado a partir de websites nesta zona. Se desativar esta definição de política, o controlo TDC Ative X será executado a partir de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Predefinição**: Ativado 
  
- **Roteiro de zona restrita do Internet Explorer iniciado janelas**  
  Esta definição de política permite-lhe gerir restrições em janelas e janelas pop-up iniciadas por scripts que incluem o título e barras de estado. Se ativar esta definição de política, a segurança das Restrições do Windows não se aplica nesta zona. A zona de segurança funciona sem a camada adicional de segurança fornecida por esta funcionalidade. Se desativar esta definição de política, as possíveis ações nocivas contidas em janelas e janelas pop-up iniciadas por scripts que incluem o título e as barras de estado não podem ser executadas. Esta funcionalidade de segurança do Internet Explorer encontra-se nesta zona, tal como dita a definição de controlo de funcionalidades de controlo de funcionalidades de restrições de segurança do Windows scripted para o processo. Se não configurar esta definição de política, as possíveis ações nocivas contidas em janelas e janelas pop-up iniciadas por scripts que incluem o título e as barras de estado não podem ser executadas. Esta funcionalidade de segurança do Internet Explorer encontra-se nesta zona, tal como dita a definição de controlo de funcionalidades de controlo de funcionalidades de restrições de segurança do Windows scripted para o processo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Predefinição**: Desativado 
  
- **A zona de internet do Internet Explorer do Internet inclui o caminho local ao carregar ficheiros para o servidor**  
  Esta definição de política controla se as informações do caminho local forem enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se as informações do caminho local forem enviadas, algumas informações podem ser reveladas involuntariamente ao servidor. Por exemplo, os ficheiros enviados do ambiente de trabalho do utilizador podem conter o nome do utilizador como parte do caminho. Se ativar esta definição de política, as informações do caminho são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se desativar esta definição de política, as informações do caminho são removidas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se não configurar esta definição de política, o utilizador pode escolher se as informações do caminho são enviadas quando fazem o upload de um ficheiro através de um formulário HTML. Por padrão, a informação do caminho é enviada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Predefinição**: Desativado 
  
- **O Internet Explorer desativa os processos em modo protegido melhorado**  
  Esta definição de política determina se o Internet Explorer 11 utiliza processos de 64 bits (para maior segurança) ou processos de 32 bits (para maior compatibilidade) quando funciona em Modo Protegido Melhorado em versões de 64 bits do Windows. Importante: Alguns controlos ActiveX e barras de ferramentas podem não estar disponíveis quando são utilizados processos de 64 bits. Se ativar esta definição de política, o Internet Explorer 11 utilizará processos de separadores de 64 bits quando estiver em modo protegido melhorado em versões de 64 bits do Windows. Se desativar esta definição de política, o Internet Explorer 11 utilizará processos de separador de 32 bits quando estiver em modo protegido melhorado em versões de 64 bits do Windows. Se não configurar esta definição de política, os utilizadores podem ligar ou desligar esta funcionalidade utilizando as definições do Internet Explorer. Esta funcionalidade é desligada por defeito.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Predefinição**: Ativado 
  
- **Internet Explorer ignora erros de certificado**  
  Esta definição de política impede o utilizador de ignorar erros de certificado de segurança de camadas seguras (SSL/TLS) que interrompem a navegação (tais como erros "expirados", "revogados" ou "desajuste de nomes") no Internet Explorer. Se ativar esta definição de política, o utilizador não pode continuar a navegar. Se desativar ou não configurar esta definição de política, o utilizador pode optar por ignorar erros de certificado e continuar a navegar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Predefinição**: Desativado 
  
- **Internet Explorer internet carregamento de ficheiros XAML**  
  Esta definição de política permite-lhe gerir o carregamento de ficheiros extensíveis de linguagem de marcação de aplicações (XAML). XAML é uma linguagem de marcação declarativa baseada em XML comumente usada para criar interfaces e gráficos de utilizador ricos que tiram partido da Fundação de Apresentação do Windows. Se ativar esta definição de política e definir a caixa de lançamento para ativar, os ficheiros XAML são automaticamente carregados dentro do Internet Explorer. O utilizador não pode mudar este comportamento. Se definir a caixa de entrega para Prompt, o utilizador é solicitado para carregar ficheiros XAML. Se desativar esta definição de política, os ficheiros XAML não são carregados dentro do Internet Explorer. O utilizador não pode mudar este comportamento. Se não configurar esta definição de política, o utilizador pode decidir se carrega ficheiros XAML dentro do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Predefinição**: Desativar 
  
- **Internet Explorer internet zone pedido automático para downloads de ficheiros**  
  Esta definição de política determina se os utilizadores são solicitados para downloads de ficheiros não iniciados pelo utilizador. Independentemente desta definição, os utilizadores receberão diálogos de descarregamento de ficheiros para downloads iniciados pelo utilizador. Se ativar esta definição, os utilizadores receberão um diálogo de descarregamento de ficheiros para tentativas automáticas de descarregamento. Se desativar ou não configurar esta definição, os downloads de ficheiros que não são iniciados pelo utilizador estão bloqueados e os utilizadores verão a barra de Notificação em vez do diálogo de descarregamento de ficheiros. Os utilizadores podem então clicar na barra de Notificação para permitir o aviso de descarregamento do ficheiro.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Predefinição**: Desativado  
  
- **Aviso de segurança de zona restrito do Internet Explorer para ficheiros potencialmente inseguros**  
  Esta definição de política controla se a mensagem "Open File - Security Warning" aparecer quando o utilizador tenta abrir ficheiros executáveis ou outros ficheiros potencialmente inseguros (a partir de uma partilha de ficheiros intranet utilizando o File Explorer, por exemplo). Se ativar esta definição de política e definir a caixa de lançamento para ativar, estes ficheiros abrem-se sem aviso de segurança. Se definir a caixa de entrega para Prompt, aparece um aviso de segurança antes de os ficheiros abrirem. Se desativar esta definição de política, estes ficheiros não abrem. Se não configurar esta definição de política, o utilizador pode configurar a forma como o computador lida com estes ficheiros. Por predefinição, estes ficheiros estão bloqueados na zona Restrita, ativadas nas zonas intranet e local de computador, e definidas para serem solicitadas nas zonas internet e trusted.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Predefinição**: Desativar  
  
- **Filtro de scripts de internet da zona de internet do Internet Explorer**  
  Esta política controla se o filtro de scripts cross-site (XSS) detetar e prevenir injeções de scripts transversais em websites desta zona. Se ativar esta definição de política, o Filtro XSS é ligado para sites nesta zona e o Filtro XSS tenta bloquear as injeções de script seletivas. Se desativar esta definição de política, o Filtro XSS é desligado para sites nesta zona, e o Internet Explorer permite injeções de scripts transversais.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Predefinição**: Ativado 
  
- **Recuo do Internet Explorer para o SSL3**  
  Esta definição de política permite bloquear uma recaída insegura para SSL 3.0. Quando esta política estiver ativada, o Internet Explorer tentará ligar-se a sites que utilizem sl 3.0 ou abaixo quando o TLS 1.0 ou maior falhar. Recomendamos que não permita um recuo inseguro para evitar um ataque de homem no meio. Esta política não afeta os protocolos de segurança que estão ativados. Se desativar esta política, são utilizados incumprimentos do sistema.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Padrão**: Sem sites  

- **Suporte de encriptação do Internet Explorer**  
  Esta definição de política permite-lhe desligar o suporte para a Segurança da Camada de Transporte (TLS) 1.0, TLS 1.1, TLS 1.2, Secure Sockets Layer (SSL) 2.0 ou SSL 3.0 no navegador. TLS e SSL são protocolos que ajudam a proteger a comunicação entre o navegador e o servidor alvo. Quando o navegador tenta configurar uma comunicação protegida com o servidor alvo, o navegador e o servidor negoceiam qual o protocolo e a versão a utilizar. O navegador e o servidor tentam corresponder à lista de protocolos e versões suportados um do outro, e selecionam a correspondência mais preferida. Se ativar esta definição de política, o navegador negoceia ou não negoceia um túnel de encriptação utilizando os métodos de encriptação que seleciona a partir da lista de drop-down. Se desativar ou não configurar esta definição de política, o utilizador pode selecionar qual o método de encriptação que o navegador suporta.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Predefinição**: 2 itens: TLS v1.1 e TLS v1.2  
  *Selecione a seta para baixo para visualizar as opções que pode selecionar para esta definição.*
  
- **Internet Explorer bloqueado por tela inteligente da zona da Internet**  
  Esta definição de política controla se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen analisa as páginas desta zona para obter conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não digitaliza páginas nesta zona para obter conteúdo malicioso. Se não configurar esta definição de política, o utilizador pode escolher se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o Filtro de Phishing digitaliza páginas nesta zona para conteúdos maliciosos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Predefinição**: Ativado 
  
- **Aplicações e ficheiros de lançamento de zona restrita do Internet Explorer num iFrame**  
  Esta definição de política permite-lhe gerir se as aplicações podem ser executadas e os ficheiros podem ser descarregados a partir de uma referência IFRAME no HTML das páginas desta zona. Se ativar esta definição de política, os utilizadores podem executar aplicações e descarregar ficheiros a partir de IFRAMEs nas páginas desta zona sem a intervenção do utilizador. Se selecionar o Prompt na caixa de entrega, os utilizadores são questionados para escolher se executam aplicações e descarregam ficheiros a partir de IFRAMEs nas páginas desta zona. Se desativar esta definição de política, os utilizadores estão impedidos de executar aplicações e de descarregar ficheiros a partir de IFRAMEs nas páginas desta zona. Se não configurar esta definição de política, os utilizadores estão impedidos de executar aplicações e de descarregar ficheiros a partir de IFRAMEs nas páginas desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Predefinição**: Desativar 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  Esta definição de política determina se o utilizador pode contornar as advertências do Filtro SmartScreen. O Filtro SmartScreen avisa o utilizador sobre ficheiros executáveis que os utilizadores do Internet Explorer não descarregam normalmente a partir da Internet. Se ativar esta definição de política, os avisos do Filtro SmartScreen bloqueiam o utilizador. Se desativar ou não configurar esta definição de política, o utilizador pode contornar as advertências do Filtro SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Predefinição**: Desativado  
  
- **Bloqueador popup da zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se aparecem janelas pop-up indesejadas. As janelas pop-up que são abertas quando o utilizador final clica num link não estão bloqueadas. Se ativar esta definição de política, a maioria das janelas pop-up indesejadas estão impedidas de aparecer. Se desativar esta definição de política, as janelas pop-up não estão impedidas de aparecer. Se não configurar esta definição de política, a maioria das janelas pop-up indesejadas estão impedidas de aparecer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa um manuseamento consistente de MIME**  
  O Internet Explorer contém comportamentos binários dinâmicos: componentes que encapsulam a funcionalidade específica para os elementos HTML aos quais estão ligados. Esta definição de política controla se a definição de restrição de segurança do comportamento binário é impedida ou permitida. Se ativar esta definição de política, os comportamentos binários são evitados para os processos do Explorador de Ficheiros e do Internet Explorer. Se desativar esta definição de política, são permitidos comportamentos binários para os processos do Explorador de Ficheiros e do Internet Explorer. Se não configurar esta definição de política, os comportamentos binários são evitados para os processos do Explorador de Ficheiros e do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Predefinição**: Ativado  
  
- **Permissões restritas de java do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, as maçãs Java são desativadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Predefinição**: Desative o java  
    
  
- **Controle o Internet Explorer Ative X em modo protegido**  
  Esta definição de política impede que os controlos ActiveX sejam acionados no modo protegido quando o modo protegido melhorado estiver ativado. Quando um utilizador tem um controlo ActiveX instalado que não é compatível com o Modo Protegido Melhorado e um website tenta carregar o controlo, o Internet Explorer notifica o utilizador e dá a opção de executar o website em modo protegido regular. Esta definição de política desativa esta notificação e obriga todos os websites a funcionar em Modo Protegido Melhorado. O Modo Protegido Melhorado fornece proteção adicional contra websites maliciosos utilizando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam pelo menos o Windows 8, o Modo Protegido Melhorado também limita as localizações que o Internet Explorer pode ler no registo e no sistema de ficheiros. Quando o modo protegido melhorado está ativado, e um utilizador encontra um website que tenta carregar um controlo ActiveX que não é compatível com o Modo Protegido Melhorado, o Internet Explorer notifica o utilizador e dá a opção de desativar o Modo Protegido Melhorado para que site em particular. Se ativar esta definição de política, o Internet Explorer não dará ao utilizador a opção de desativar o Modo Protegido Melhorado. Todos os websites do Modo Protegido serão executados em Modo Protegido Melhorado. Se desativar ou não configurar esta definição de política, o Internet Explorer informa os utilizadores e oferece uma opção para executar websites com controlos ActiveX incompatíveis no modo protegido regular.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Predefinição**: Desativado  
  
- **Internet Explorer restrito carregamento de zonas de ficheiros XAML**  
  Esta definição de política permite-lhe gerir o carregamento de ficheiros extensíveis de linguagem de marcação de aplicações (XAML). XAML é uma linguagem de marcação declarativa baseada em XML comumente usada para criar interfaces e gráficos de utilizador ricos que tiram partido da Fundação de Apresentação do Windows. Se ativar esta definição de política e definir a caixa de lançamento para ativar, os ficheiros XAML são automaticamente carregados dentro do Internet Explorer. O utilizador não pode mudar este comportamento. Se definir a caixa de entrega para Prompt, o utilizador é solicitado para carregar ficheiros XAML. Se desativar esta definição de política, os ficheiros XAML não são carregados dentro do Internet Explorer. O utilizador não pode mudar este comportamento. Se não configurar esta definição de política, o utilizador pode decidir se carrega ficheiros XAML dentro do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Predefinição**: Desativar  
  
- **O Internet Explorer processa restrições de segurança de janelas scripted**  
  O Internet Explorer permite que os scripts possam abrir, redimensionar e reposicionar programaticamente janelas de vários tipos. A função de segurança de Restrições de Janelas restringe as janelas popup e proíbe que os scripts apresentem janelas nas quais o título e as barras de estado não sejam visíveis para o utilizador ou obstar o título e as barras de estado de outros Windows. Se ativar esta definição de política, as janelas escritas são restritas para todos os processos. Se desativar ou não configurar esta definição de política, as janelas escritas não são restritas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Predefinição**: Ativado   
  
- **Internet Explorer área restrita executar controles e plugins Ative X**  
  Esta definição de política permite-lhe gerir se os controlos e plug-ins do ActiveX podem ser executados em páginas a partir da zona especificada. Se ativar esta definição de política, os controlos e os plug-ins podem ser executados sem a intervenção do utilizador. Se selecionou o Prompt na caixa de entrega, pede-se aos utilizadores que escolham se permitem que os controlos ou o plug-in sejam executados. Se desativar esta definição de política, os controlos e os plug-ins são impedidos de funcionar. Se não configurar esta definição de política, os controlos e os plug-ins são impedidos de funcionar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Predefinição**: Desativar  
  
- **Script de zona restrita do Internet Explorer Ative X controles marcados como seguros para scripts**  
  Esta definição de política permite-lhe gerir se um controlo ActiveX marcado como seguro para scripts pode interagir com um script. Se ativar esta definição de política, a interação do script pode ocorrer automaticamente sem a intervenção do utilizador. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem a interação do script. Se desativar esta definição de política, a interação do script está impedida de ocorrer. Se não configurar esta definição de política, a interação do script está impedida de ocorrer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Predefinição**: Desativar  
  
- **Opções restritas de logon de zona do Internet Explorer**  
  Esta definição de política permite-lhe gerir as definições para iniciar sessão. Se ativar esta definição de política, pode escolher entre as seguintes opções de inscrição. 
  - *Anonymous* - Utilize o registo anónimo para desativar a autenticação HTTP e utilize a conta de hóspedes apenas para o protocolo do Sistema Comum de Ficheiros de Internet (CIFS). 
  - *Solicitação* - Utilize o pedido de nome do utilizador e palavra-passe para consultar os utilizadores para identificações de utilizadores e palavras-passe. Depois de um utilizador ser consultado, estes valores podem ser utilizados silenciosamente durante o resto da sessão. 
  - *Iniciar sessão automática apenas na zona intranet* - Utilize esta opção para consultar os utilizadores de IDs e senhas de utilização noutras zonas. Depois de um utilizador ser consultado, estes valores podem ser utilizados silenciosamente durante o resto da sessão. 
  - *Iniciar sessão automática com o nome de utilizador e a palavra-passe atual*- Utilize esta opção para tentar iniciar o sessão utilizando o Windows NT Challenge Response (também conhecido como autenticação NTLM). Se o servidor suportar o Windows NT Challenge Response, o sinal de utilização utiliza o nome de utilizador da rede do utilizador e a palavra-passe para iniciar sessão. Se o servidor não suportar o Windows NT Challenge Response, o utilizador é consultado para fornecer o nome de utilizador e a palavra-passe. 

  Se desativar esta definição de política, o início de sessão é definido para *iniciar sessão automática apenas na zona Intranet*. Se não configurar esta definição de política, o iniciar sessão está definido para *O Nome de Utilizador* e palavra-passe.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Padrão**: Anónimo  
  
- **Zona fidedigna do Internet Explorer inicializar e script Controlos Ative X não marcados como seguros**  
  Esta definição de política permite-lhe gerir os controlos ActiveX não marcados como seguros. Se ativar esta definição de política, os controlos ActiveX funcionam, carregados com parâmetros e escritos sem definir a segurança do objeto para dados ou scripts não confiáveis. Esta definição não é recomendada, exceto para zonas seguras e administradas. Esta definição faz com que os controlos inseguros e seguros sejam inicializados e scripts, ignorando os comandos Script ActiveX marcados como seguros para a opção de script. Se ativar esta definição de política e selecionar o Prompt na caixa de lançamento, os utilizadores são questionados se permitem que o controlo carregue com parâmetros ou scripts. Se desativar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não são carregados com parâmetros ou scripts. Se não configurar esta definição de política, os utilizadores são questionados se permitem que o controlo carregue com parâmetros ou scripts.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer verificar revogação do certificado do servidor**  
  Esta definição de política permite-lhe gerir se o Internet Explorer verificará o estado de revogação dos certificados dos servidores. Os certificados são revogados quando estão comprometidos ou já não são válidos, e esta opção protege os utilizadores de submeter dados confidenciais a um site que possa ser fraudulento ou não seguro. Se ativar esta definição de política, o Internet Explorer verificará se os certificados de servidor foram revogados. Se desativar esta definição de política, o Internet Explorer não verificará os certificados do servidor para ver se foram revogados. Se não configurar esta definição de política, o Internet Explorer não verificará os certificados do servidor para ver se foram revogados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Predefinição**: Ativado 
  
- **Internet Explorer internet zone menos sites privilegiados**  
  Esta definição de política permite-lhe gerir se os Web sites de zonas menos privilegiadas, como sites restritos, podem navegar para esta zona. Se ativar esta definição de política, os Web sites de zonas menos privilegiadas podem abrir novas janelas ou navegar para dentro desta zona. A zona de segurança funcionará sem a camada adicional de segurança fornecida pela função de segurança Protection from Zone Elevation. Se selecionar O Aviso na caixa de entrega, é emitido um aviso ao utilizador de que está prestes a ocorrer uma navegação potencialmente arriscada. Se desativar esta definição de política, as navegações possivelmente nocivas são evitadas. A funcionalidade de segurança do Internet Explorer está nesta zona, tal como definida pela Proteção contra o controlo da funcionalidade de elevação da zona. Se não configurar esta definição de política, os Web sites de zonas menos privilegiadas podem abrir novas janelas ou navegar para dentro desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Predefinição**: Desativar  
  
- **Transferências de ficheiros de zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe gerir se os downloads de ficheiros são permitidos a partir da zona. Esta opção é determinada pela zona da página com o link que causa o download, e não a zona a partir da qual o ficheiro é entregue. Se ativar esta definição de política, os ficheiros podem ser descarregados a partir da zona. Se desativar esta definição de política, os ficheiros são impedidos de serem descarregados da zona. Se não configurar esta definição de política, os ficheiros são impedidos de serem descarregados da zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer internet zone run .NET Framework componentes dependentes assinados com Authenticode**  
  Esta definição de política permite-lhe gerir se os componentes .NET Framework que são assinados com authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controlos geridos referenciados a partir de uma etiqueta de objeto e executáveis geridos referenciados a partir de um link. Se ativar esta definição de política, o Internet Explorer executará componentes geridos assinados. Se selecionar O Prompt na caixa de lançamento, o Internet Explorer irá solicitar ao utilizador que determine se executa os componentes geridos assinados. Se desativar esta definição de política, o Internet Explorer não executará componentes geridos assinados. Se não configurar esta definição de política, o Internet Explorer não executará componentes geridos assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Predefinição**: Desativar  
  
- **O Internet Explorer impede por utilizador a instalação de controlos Ative X**  
  Esta definição de política permite-lhe impedir a instalação de controlos ActiveX por utilizador. Se ativar esta definição de política, os controlos ActiveX não podem ser instalados numa base por utilizador. Se desativar ou não configurar esta definição de política, os controlos ActiveX podem ser instalados numa base por utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Predefinição**: Ativado  
  
- **O Internet Explorer impede a gestão do filtro de ecrã inteligente**  
  Esta definição de política impede o utilizador de gerir o Filtro SmartScreen, que avisa o utilizador se o site que visita é conhecido por tentativas fraudulentas de recolher informações pessoais através de "phishing", ou é conhecido por hospedar malware. Se ativar esta definição de política, o utilizador não é solicitado a ligar o Filtro SmartScreen. Todos os endereços do site que não estejam nos filtros permitem que a lista seja enviada automaticamente para a Microsoft sem avisar o utilizador. Se desativar ou não configurar esta definição de política, o utilizador é solicitado a decidir se liga o Filtro SmartScreen durante a experiência de primeira execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Padrão**: Ativar  
  
- **Internet Explorer processa recurso de segurança de sniffing MIME**  
  Esta definição de política determina se o cheiro do Internet Explorer MIME impedirá a promoção de um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se ativar esta definição de política, o cheiro mime nunca promoverá um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se desativar esta definição de política, os processos do Internet Explorer permitirão que um cheiro mime promova um ficheiro de um tipo para um tipo de ficheiro mais perigoso. Se não configurar esta definição de política, o cheiro mime nunca promoverá um ficheiro de um tipo para um tipo de ficheiro mais perigoso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer restrita de saque de zona assinada por Ative X**  
  Esta definição de política permite-lhe gerir se os utilizadores podem descarregar controlos ActiveX assinados a partir de uma página na zona. Se ativar esta política, os utilizadores podem descarregar controlos assinados sem a intervenção do utilizador. Se selecionar o Prompt na caixa de entrega, os utilizadores são questionados se descarregam os controlos assinados por editores que não são de confiança. O código assinado por editores fidedignos é descarregado silenciosamente. Se desativar a definição de política, os controlos assinados não podem ser descarregados. Se não configurar esta definição de política, os utilizadores são questionados se descarregam os controlos assinados por editores que não são de confiança. O código assinado por editores fidedignos é descarregado silenciosamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Predefinição**: Desativar  
  
- **Internet Explorer auto completo**  
  Esta função Auto-Complete pode lembrar-se e sugerir nomes de utilizador e palavras-passe em Formulários. Se ativar esta definição, o utilizador não pode alterar "nome de utilizador e palavras-passe nos formulários" ou "solicitar-me para guardar senhas". A função Auto Complete para nomes de utilizador e palavras-passe em Formulários é ligada. Tem de decidir se se leciona "me indique a guardar senhas". Se desativar esta definição, o utilizador não pode alterar "nome de utilizador e palavras-passe nos formulários" ou "pedir-me para guardar senhas". A funcionalidade Auto Complete para nomes de utilizador e palavras-passe em Formulários está desligada. O utilizador também não pode optar por ser solicitado para guardar palavras-passe. Se não configurar esta definição, o utilizador tem a liberdade de ligar automaticamente completo para o nome do utilizador e palavras-passe nos formulários e a opção de pedir para guardar palavras-passe. Para visualizar esta opção, os utilizadores abrem a caixa de diálogo opções de Internet, clicam no Separador Conteúdo e clicam no botão Definições.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Predefinição**: Desativado  
  
- **A zona de internet do Internet Explorer permite que o VBscript corra**  
  Esta definição de política permite-lhe decidir se o VBScript pode ser executado em páginas em zonas específicas do Internet Explorer. As opções incluem: 
  - *Ativar* - O VBScript corre em páginas em zonas específicas, sem qualquer interação. 
  - *Solicitação* - Os colaboradores são solicitados a permitir que o VBScript corra na zona. 
  - *Desativar* - O VBScript está impedido de funcionar na zona. Se desativar ou não configurar esta definição de política, o VBScript funciona sem qualquer interação na zona especificada.    

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Predefinição**: Desativar  
  
- **A zona restrita do Internet Explorer permite que apenas os domínios aprovados utilizem controlos TDC Ative X**  
  Esta definição de política controla se o utilizador puder executar o controlo TDC ActiveX nos websites. Se ativar esta definição de política, o controlo TDC ActiveX não será executado a partir de websites nesta zona. Se desativar esta definição de política, o controlo TDC Ative X será executado a partir de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Predefinição**: Ativado  
  
- **A zona fidedigna do Internet Explorer não executa antimalware contra controlos Ative X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware contra controlos ActiveX, para verificar se são seguros para carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Os utilizadores podem ligar ou desligar este comportamento, utilizando as definições de Segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Predefinição**: Desativado 
  
- **Permissões de java da zona de máquina local do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, a permissão é definida para a Segurança Média.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Predefinição**: Desative o java 
  
- **A zona intranet do Internet Explorer não executa antimalware contra controlos Ative X**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware contra controlos ActiveX, para verificar se são seguros para carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se não configurar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Os utilizadores podem ligar ou desligar este comportamento, utilizando as definições de Segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Predefinição**: Desativado  

- **Scriptlets de zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe gerir se o utilizador pode executar scriptlets. Se ativar esta definição de política, o utilizador pode executar scriptlets. Se desativar esta definição de política, o utilizador não pode executar scriptlets. Se não configurar esta definição de política, o utilizador pode ativar ou desativar scriptlets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Predefinição**: Desativado  
  
- **Internet Explorer processa barra de notificação**  
  Esta definição de política permite-lhe gerir se a barra de notificação é exibida para os processos do Internet Explorer quando as instalações de ficheiros ou códigos são restritas. Por predefinição, a barra de notificação é apresentada para os processos do Internet Explorer. Se ativar esta definição de política, a barra de notificação apresenta os Processos do Internet Explorer. Se desativar esta definição de política, a barra de notificação não será exibida para os processos do Internet Explorer. Se não configurar esta definição de política, a barra de Notificação não exibe processos de Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer internet download assinado controlos ActiveX**  
  Esta definição de política permite-lhe gerir se os utilizadores podem descarregar controlos ActiveX assinados a partir de uma página na zona. Se ativar esta política, os utilizadores podem descarregar controlos assinados sem a intervenção do utilizador. Se selecionar o Prompt na caixa de entrega, os utilizadores são questionados se descarregam os controlos assinados por editores que não são de confiança. O código assinado por editores fidedignos é descarregado silenciosamente. Se desativar a definição de política, os controlos assinados não podem ser descarregados. Se não configurar esta definição de política, os utilizadores são questionados se descarregam os controlos assinados por editores que não são de confiança. O código assinado por editores fidedignos é descarregado silenciosamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Predefinição**: Desativar  
  
- **Tela inteligente de zona restrita do Internet Explorer**  
  Esta definição de política controla se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen analisa as páginas desta zona para obter conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não digitaliza páginas nesta zona para obter conteúdo malicioso. Se não configurar esta definição de política, o utilizador pode escolher se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o Filtro de Phishing digitaliza páginas nesta zona para conteúdos maliciosos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer remove executar este botão de tempo para controlos Ative X desatualizados**  
  Esta definição de política permite-lhe impedir que os utilizadores vejam o botão "Run this time" e de executar controlos ActiveX desatualizados específicos no Internet Explorer. Se ativar esta definição de política, os utilizadores não verão o botão "Executar desta vez" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controlo ActiveX desatualizado. Se desativar ou não configurar esta definição de política, os utilizadores verão o botão "Executar desta vez" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controlo ActiveX desatualizado. Clicar neste botão permite ao utilizador executar o controlo ActiveX desatualizado uma vez. Para mais informações, consulte "Controlos ActiveX Desatualizados" na biblioteca do Internet Explorer TechNet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Predefinição**: Ativado 
  
- **Aplicações e ficheiros de lançamento de zona de internet do Internet Explorer no iframe**  
  Esta definição de política permite-lhe gerir se as aplicações podem ser executadas e os ficheiros podem ser descarregados a partir de uma referência IFRAME no HTML das páginas desta zona. Se ativar esta definição de política, os utilizadores podem executar aplicações e descarregar ficheiros a partir de IFRAMEs nas páginas desta zona sem a intervenção do utilizador. Se selecionar o Prompt na caixa de entrega, os utilizadores são questionados para escolher se executam aplicações e descarregam ficheiros a partir de IFRAMEs nas páginas desta zona. Se desativar esta definição de política, os utilizadores estão impedidos de executar aplicações e de descarregar ficheiros a partir de IFRAMEs nas páginas desta zona. Se não configurar esta definição de política, os utilizadores são questionados para escolher se executam aplicações e descarregam ficheiros a partir de IFRAMEs nas páginas desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Predefinição**: Desativar 
  
- **Internet Explorer área restrita navegar janelas e quadros em diferentes domínios**  
  Esta definição de política permite-lhe definir opções para arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em janelas diferentes. Se ativar esta definição de política e clicar em Ativar, os utilizadores podem arrastar o conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração. Se ativar esta definição de política e clicar em Desativar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando tanto a fonte como o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se desativar esta definição de política ou não configurar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em janelas diferentes. Os utilizadores podem alterar esta definição no diálogo das Opções de Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não a configurar, os utilizadores podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Predefinição**: Desativar  
  
- **Tela inteligente da zona de internet do Internet Explorer**  
  Esta definição de política controla se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen analisa as páginas desta zona para obter conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não digitaliza páginas nesta zona para obter conteúdo malicioso. Se não configurar esta definição de política, o utilizador pode escolher se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o Filtro de Phishing digitaliza páginas nesta zona para conteúdos maliciosos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer bloqueou permissões java de zona de confiança**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, as maçãs Java são desativadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Predefinição**: Desative o java 
  
- **Internet Explorer verifica assinaturas em programas descarregados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer verifica as assinaturas digitais (que identifica o editor de software assinado e verifica que não foi modificado ou adulterado) nos computadores dos utilizadores antes de descarregar programas executáveis. Se ativar esta definição de política, o Internet Explorer verificará as assinaturas digitais de programas executáveis e mostrará as suas identidades antes de as descarregar para computadores de utilizador. Se desativar esta definição de política, o Internet Explorer não verificará as assinaturas digitais de programas executáveis ou mostrará as suas identidades antes de as descarregar para computadores de utilizador. Se não configurar esta política, o Internet Explorer não verificará as assinaturas digitais de programas executáveis ou mostrará as suas identidades antes de as descarregar para computadores de utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Predefinição**: Ativado  
  
- **Scripting de zona restrita do Internet Explorer dos controlos do navegador web**  
  Esta definição de política determina se uma página pode controlar os controlos do WebBrowser incorporados através do script. Se ativar esta definição de política, é permitido o acesso ao script ao controlo WebBrowser. Se desativar esta definição de política, o acesso do script ao controlo webBrowser não é permitido. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o acesso do script ao controlo do WebBrowser. Por predefinição, o acesso ao script ao controlo WebBrowser só é permitido nas zonas Local Machine e Intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Predefinição**: Desativado  
  
- **Filtro de scripts de área seletiva restrita do Internet Explorer**  
  Esta política controla se o filtro de scripts cross-site (XSS) detetar e prevenir injeções de scripts transversais em websites desta zona. Se ativar esta definição de política, o Filtro XSS é ligado para sites nesta zona e o Filtro XSS tenta bloquear as injeções de script seletivas. Se desativar esta definição de política, o Filtro XSS é desligado para sites nesta zona, e o Internet Explorer permite injeções de scripts transversais.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Predefinição**: Ativado  
  
- **Comportamentos binários e scripts de zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe gerir comportamentos binários dinâmicos e de scripts: componentes que encapsulam funcionalidades específicas para elementos HTML aos quais foram anexados. Se ativar esta definição de política, estão disponíveis comportamentos binários e scripts. Se selecionar administrador aprovado na caixa de entrega, apenas estão disponíveis comportamentos listados nos Comportamentos aprovados pela Administração ao abrigo da política de restrição de segurança de comportamentos binários. Se desativar esta definição de política, os comportamentos binários e de script não estão disponíveis, a menos que as aplicações tenham implementado um gestor de segurança personalizado. Se não configurar esta definição de política, os comportamentos binários e de script não estão disponíveis, a menos que as aplicações tenham implementado um gestor de segurança personalizado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Predefinição**: Desativar  
  
- **Verificação de definições de segurança do Internet Explorer**  
  Esta definição de política desliga a funcionalidade de verificação de definições de segurança, que verifica as definições de segurança do Internet Explorer para determinar quando as definições colocam o Internet Explorer em risco. Se ativar esta definição de política, a funcionalidade está desligada. Se desativar ou não configurar esta definição de política, a funcionalidade é ativada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Predefinição**: Ativado  
  
- **Aviso de segurança da zona de internet do Internet Explorer para ficheiros potencialmente inseguros**  
  Esta definição de política controla se a mensagem "Open File - Security Warning" aparecer quando o utilizador tenta abrir ficheiros executáveis ou outros ficheiros potencialmente inseguros (a partir de uma partilha de ficheiros intranet utilizando o File Explorer, por exemplo). Se ativar esta definição de política e definir a caixa de lançamento para ativar, estes ficheiros abrem-se sem aviso de segurança. Se definir a caixa de entrega para Prompt, aparece um aviso de segurança antes de os ficheiros abrirem. Se desativar esta definição de política, estes ficheiros não abrem. Se não configurar esta definição de política, o utilizador pode configurar a forma como o computador lida com estes ficheiros. Por predefinição, estes ficheiros estão bloqueados na zona Restrita, ativadas nas zonas intranet e local de computador, e definidas para serem solicitadas nas zonas internet e trusted.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Padrão**: Pronta  
  
- **Permissões de java da zona intranet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, a permissão é definida para a Segurança Média.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Predefinição**: Alta segurança 
  
- **O bloqueio do Internet Explorer desatualizado Ative X controla**   
  Esta definição de política determina se o Internet Explorer bloqueia controlos ActiveX desatualizados específicos. Os controlos ActiveX desatualizados nunca são bloqueados na Zona intranet. Se ativar esta definição de política, o Internet Explorer deixa de bloquear controlos ActiveX desatualizados. Se desativar ou não configurar esta definição de política, o Internet Explorer continua a bloquear controlos ActiveX desatualizados específicos. Para mais informações, consulte "Controlos ActiveX Desatualizados" na biblioteca do Internet Explorer TechNet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Predefinição**: Ativado  
  
- **Bloqueador de popup de zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe gerir se aparecem janelas pop-up indesejadas. As janelas pop-up que são abertas quando o utilizador final clica num link não estão bloqueadas. Se ativar esta definição de política, a maioria das janelas pop-up indesejadas estão impedidas de aparecer. Se desativar esta definição de política, as janelas pop-up não estão impedidas de aparecer. Se não configurar esta definição de política, a maioria das janelas pop-up indesejadas estão impedidas de aparecer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Padrão**: Ativar  
  
- **Internet Explorer processa restrição de segurança do protocolo MK**  
  A definição da política de restrição de segurança do protocolo MK reduz a área de superfície de ataque, impedindo o protocolo MK. Os recursos acolhidos no protocolo MK falharão. Se ativar esta definição de política, o Protocolo MK é impedido para o File Explorer e o Internet Explorer, e os recursos alojados no protocolo MK falharão. Se desativar esta definição de política, as aplicações podem utilizar o protocolo MK API. Os recursos alojados no protocolo MK funcionarão para os processos do File Explorer e do Internet Explorer. Se não configurar esta definição de política, o Protocolo MK está impedido para o File Explorer e o Internet Explorer, e os recursos alojados no protocolo MK falharão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer trusted zone java permissões**   
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, a permissão é definida para a Baixa Segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Predefinição**: Alta segurança  
  
- **Roteiro de zona restrita do Internet Explorer de maçãs java**  
  Esta definição de política permite-lhe gerir se as maçãs estão expostas a scripts dentro da zona. Se ativar esta definição de política, os scripts podem aceder automaticamente aos applets sem a intervenção do utilizador. Se selecionar O Prompt na caixa de entrega, os utilizadores estão questionados para escolher se permitem que scripts acedam a applets. Se desativar esta definição de política, os scripts são impedidos de aceder a applets. Se não configurar esta definição de política, os scripts são impedidos de aceder a applets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer bloqueou permissões restritas** de java de zona   
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, as maçãs Java são desativadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Predefinição**: Desative o java 
  
- A zona de **internet do Internet Explorer permite que apenas os domínios aprovados utilizem controlos ActiveX**   
  Esta definição de política controla se o utilizador for solicitado a permitir que os controlos ActiveX possam ser executados em websites que não o website que instalou o controlo ActiveX. Se ativar esta definição de política, o utilizador é solicitado antes que os controlos ActiveX possam ser executados a partir de websites nesta zona. O utilizador pode optar por permitir que o controlo possa ser executado a partir do site atual ou de todos os sites. Se desativar esta definição de política, o utilizador não vê o pedido do ActiveX por site, e os controlos ActiveX podem ser executados a partir de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Predefinição**: Ativado  
  
- **O Internet Explorer inclui todos os caminhos da rede**  
  O Internet Explorer inclui todos os caminhos da rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Predefinição**: Desativado 
  
- **Modo protegido pela zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe ligar o Modo Protegido. O Modo Protegido ajuda a proteger o Internet Explorer de vulnerabilidades exploradas, reduzindo os locais a que o Internet Explorer pode escrever no registo e no sistema de ficheiros. Se ativar esta definição de política, o Modo Protegido está ligado. O utilizador não pode desligar o Modo Protegido. Se desativar esta definição de política, o Modo Protegido está desligado. O utilizador não pode ligar o Modo Protegido. Se não configurar esta definição de política, o utilizador pode ligar ou desligar o Modo Protegido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Padrão**: Ativar 
  
- **Internet Explorer internet zona inicializar e script Controlos Ative X não marcados como seguros**  
  Esta definição de política permite-lhe gerir os controlos ActiveX não marcados como seguros. Se ativar esta definição de política, os controlos ActiveX funcionam, carregados com parâmetros e escritos sem definir a segurança do objeto para dados ou scripts não confiáveis. Esta definição não é recomendada, exceto para zonas seguras e administradas. Esta definição faz com que os controlos inseguros e seguros sejam inicializados e scripts, ignorando os comandos Script ActiveX marcados como seguros para a opção de script. Se ativar esta definição de política e selecionar o Prompt na caixa de lançamento, os utilizadores são questionados se permitem que o controlo carregue com parâmetros ou scripts. Se desativar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não são carregados com parâmetros ou scripts. Se não configurar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não estão carregados com parâmetros ou scripts.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Predefinição**: Desativar 
  
- **Internet Explorer bloqueado por ** de ecrã inteligente de zona restrita  
  Esta definição de política controla se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Se ativar esta definição de política, o Filtro SmartScreen analisa as páginas desta zona para obter conteúdo malicioso. Se desativar esta definição de política, o Filtro SmartScreen não digitaliza páginas nesta zona para obter conteúdo malicioso. Se não configurar esta definição de política, o utilizador pode escolher se o Filtro SmartScreen digitaliza páginas nesta zona para obter conteúdo malicioso. Nota: No Internet Explorer 7, esta definição de política controla se o Filtro de Phishing digitaliza páginas nesta zona para conteúdos maliciosos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Predefinição**: Ativado  
  
- **Deteção de acidentes do Internet Explorer**  
  Esta definição de política permite-lhe gerir a funcionalidade de deteção de acidentes de gestão addon. Se ativar esta definição de política, um crash no Internet Explorer irá exibir comportamentos encontrados no Windows XP Professional Service Pack 1 e anterior, nomeadamente para invocar o Windows Error Reporting. Todas as definições de política para O Relato de Erros do Windows continuam a ser aplicadas. Se desativar ou não configurar esta definição de política, a funcionalidade de deteção de colisões para gestão de suplementos está funcional.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Predefinição**: Desativado  
  
- **Permissões java da zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, a permissão é definida para Alta Segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Predefinição**: Desative o java  
  
- **Scripts ativos de zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe gerir se o código de script nas páginas da zona é executado. Se ativar esta definição de política, o código de script nas páginas da zona pode ser executado automaticamente. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem que o código de script nas páginas da zona seja executado. Se desativar esta definição de política, o código de script nas páginas da zona está impedido de funcionar. Se não configurar esta definição de política, o código de script nas páginas da zona está impedido de funcionar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Predefinição**: Desativar  
  
- **Opções de logon de internet do Internet Explorer do Internet Explorer**  
  Esta definição de política permite-lhe gerir as definições para iniciar sessão. Se ativar esta definição de política, pode escolher entre as seguintes opções de inscrição. Iniciar sessão anónima para desativar a autenticação HTTP e utilizar a conta do hóspede apenas para o protocolo do Sistema Comum de Ficheiros de Internet (CIFS). Solicita-me o nome do utilizador e a palavra-passe para consultar os utilizadores para identificações de utilizadores e palavras-passe. Depois de um utilizador ser consultado, estes valores podem ser utilizados silenciosamente durante o resto da sessão. Iniciar sessão automática apenas na zona intranet para consultar os utilizadores de IDs e senhas de utilização noutras zonas. Depois de um utilizador ser consultado, estes valores podem ser utilizados silenciosamente durante o resto da sessão. Inicie sessão automática com o nome de utilizador atual e a palavra-passe para tentar iniciar sessão utilizando o Windows NT Challenge Response (também conhecido como autenticação NTLM). Se o servidor suportar o Windows NT Challenge Response, o sinal de utilização utiliza o nome de utilizador e a palavra-passe da rede do utilizador para iniciar sessão. Se o servidor não suportar o Windows NT Challenge Response, o utilizador é consultado para fornecer o nome de utilizador e a palavra-passe. Se desativar esta definição de política, o login é definido para iniciar sessão automática apenas na zona Intranet. Se não configurar esta definição de política, o signo é definido para iniciar sessão automática apenas na zona Intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Padrão**: Pronta  
  
- **A zona restrita do Internet Explorer permite que o vbscript corra**   
  Esta definição de política permite-lhe gerir se o VBScript pode ser executado em páginas da zona especificada no Internet Explorer. Se selecionou Ativar na caixa de lançamento, o VBScript pode ser executado sem a intervenção do utilizador. Se selecionou o Prompt na caixa de lançamento, os utilizadores são convidados a escolher se permitem que o VBScript seja executado. Se selecionou Desativar na caixa de lançamento, o VBScript está impedido de funcionar. Se não configurar ou desativar esta definição de política, o VBScript está impedido de funcionar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer internet zone arrastar conteúdo de diferentes domínios através de janelas**  
  Esta definição de política permite-lhe definir opções para arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em janelas diferentes. Se ativar esta definição de política e clicar em Ativar, os utilizadores podem arrastar o conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração. Se ativar esta definição de política e clicar em Desativar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando tanto a fonte como o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se desativar esta definição de política ou não configurar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em janelas diferentes. Os utilizadores podem alterar esta definição no diálogo das Opções de Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não a configurar, os utilizadores podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Predefinição**: Desativado 
  
- **A zona intranet do Internet Explorer inicializa e script Ative X controles não marcados como seguros**  
  Esta definição de política permite-lhe gerir os controlos ActiveX não marcados como seguros. Se ativar esta definição de política, os controlos ActiveX funcionam, carregados com parâmetros e escritos sem definir a segurança do objeto para dados ou scripts não confiáveis. Esta definição não é recomendada, exceto para zonas seguras e administradas. Esta definição faz com que os controlos inseguros e seguros sejam inicializados e scripts, ignorando os comandos Script ActiveX marcados como seguros para a opção de script. Se ativar esta definição de política e selecionar o Prompt na caixa de lançamento, os utilizadores são questionados se permitem que o controlo carregue com parâmetros ou scripts. Se desativar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não são carregados com parâmetros ou scripts. Se não configurar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não estão carregados com parâmetros ou scripts.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Predefinição**: Desativar 
  
- **Recintos de descarregamento do Internet Explorer**  
  Esta definição de política impede que o utilizador tenha recintos (anexos de ficheiros) descarregados de um feed para o computador do utilizador. Se ativar esta definição de política, o utilizador não pode definir o Motor Feed Sync para descarregar um recinto através da página da propriedade feed. Um desenvolvedor não pode alterar a definição de descarregamento através das APIs de alimentação. Se desativar ou não configurar esta definição de política, o utilizador pode definir o Motor Feed Sync para descarregar um recinto através da página de propriedade feed. Um desenvolvedor pode alterar a definição de descarregamento através das APIs de alimentação.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Predefinição**: Desativado  
  
- **Internet Explorer restrita descarregamento de zona não assinada controlos Ative X**  
  Esta definição de política permite-lhe gerir se os utilizadores podem descarregar controlos ActiveX não assinados a partir da zona. Este código é potencialmente prejudicial, especialmente quando se vem de uma zona não confiável. Se ativar esta definição de política, os utilizadores podem executar controlos não assinados sem a intervenção do utilizador. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem que o controlo não assinado seja executado. Se desativar esta definição de política, os utilizadores não podem executar controlos não assinados. Se não configurar esta definição de política, os utilizadores não podem executar controlos não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer internet zone arrastar conteúdo de diferentes domínios dentro das janelas**  
  Esta definição de política permite-lhe gerir se os utilizadores podem descarregar controlos ActiveX não assinados a partir da zona. Este código é potencialmente prejudicial, especialmente quando se vem de uma zona não confiável. Se ativar esta definição de política, os utilizadores podem executar controlos não assinados sem a intervenção do utilizador. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem que o controlo não assinado seja executado. Se desativar esta definição de política, os utilizadores não podem executar controlos não assinados. Se não configurar esta definição de política, os utilizadores não podem executar controlos não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Predefinição**: Desativado  
  
- **Os processos do Internet Explorer restringem** a instalação do Ative X   
  Esta definição de política permite que as aplicações que hospedam o Controlo do Navegador Web bloqueiem o pedido automático de instalação de controlo ActiveX. Se ativar esta definição de política, o Controlo do Navegador Web bloqueará a instalação automática de controlo ActiveX para todos os processos. Se desativar ou não configurar esta definição de política, o Controlo do Navegador Web não bloqueará a instalação automática de controlo ActiveX para todos os processos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Predefinição**: Ativado  
  
- **Scriptlets de zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir se o utilizador pode executar scriptlets. Se ativar esta definição de política, o utilizador pode executar scriptlets. Se desativar esta definição de política, o utilizador não pode executar scriptlets. Se não configurar esta definição de política, o utilizador pode ativar ou desativar scriptlets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer restrito de arrasto de zona e largar ou copiar e colar ficheiros**  
  Esta definição de política permite-lhe gerir se os utilizadores podem arrastar ficheiros ou copiar e colar ficheiros a partir de uma fonte dentro da zona. Se ativar esta definição de política, os utilizadores podem arrastar ficheiros ou copiar e colar ficheiros desta zona automaticamente. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se devem arrastar ou copiar ficheiros desta zona. Se desativar esta definição de política, os utilizadores são impedidos de arrastar ficheiros ou copiar e colar ficheiros desta zona. Se não configurar esta definição de política, os utilizadores são questionados para escolher se devem arrastar ou copiar ficheiros desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Predefinição**: Desativar  
  
- **Software do Internet Explorer quando a assinatura é inválida**  
  Esta definição de política permite-lhe gerir se o software, como os controlos Do ActiveX e os downloads de ficheiros, pode ser instalado ou executado pelo utilizador, mesmo que a assinatura seja inválida. Uma assinatura inválida pode indicar que alguém adulterou o ficheiro. Se ativar esta definição de política, os utilizadores são solicitados a instalar ou executar ficheiros com uma assinatura inválida. Se desativar esta definição de política, os utilizadores não podem executar ou instalar ficheiros com uma assinatura inválida. Se não configurar esta política, os utilizadores podem optar por executar ou instalar ficheiros com uma assinatura inválida.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Predefinição**: Desativado  
  
- **Cópia e pasta restrita do Internet Explorer via script**  
  Esta definição de política permite-lhe gerir se os scripts podem executar uma operação de prancheta (por exemplo, cortar, copiar e colar) numa região especificada. Se ativar esta definição de política, um script pode executar uma operação de prancheta. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados sobre se devem ou não realizar operações de clipboard. Se desativar esta definição de política, um guião não pode executar uma operação de prancheta. Se não configurar esta definição de política, um script não pode executar uma operação de prancheta.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer restringiu o conteúdo de arrasto de zona de diferentes domínios através das janelas**  
  Esta definição de política permite-lhe definir opções para arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em janelas diferentes. Se ativar esta definição de política e clicar em Ativar, os utilizadores podem arrastar o conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração. Se ativar esta definição de política e clicar em Desativar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando tanto a fonte como o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se desativar esta definição de política ou não configurar, os utilizadores não podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em janelas diferentes. Os utilizadores podem alterar esta definição no diálogo das Opções de Internet. No Internet Explorer 9 e versões anteriores, se desativar esta política ou não a configurar, os utilizadores podem arrastar conteúdo de um domínio para um domínio diferente quando a fonte e o destino estão em diferentes janelas. Os usuários não podem alterar essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Predefinição**: Desativado  
  
- **Utilizadores do Internet Explorer adicionando sites**  
  Impede que os utilizadores adicionem ou removam sites de zonas de segurança. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, as definições de gestão do site para as zonas de segurança são desativadas. (Para ver as definições de gestão do site para zonas de segurança, na caixa de diálogo opções de Internet, clique no separador Segurança e, em seguida, clique no botão Sites.) Se desativar esta política ou não a configurar, os utilizadores podem adicionar Web sites ou remover sites das zonas de Sites Fidedignos e Sites Restritos e alterar as definições para a zona intranet local. Esta política impede que os utilizadores mudem as definições de gestão do site para as zonas de segurança estabelecidas pelo administrador. Nota: A política "Desativar a página de segurança" (localizada em \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), que remove o separador De Segurança da interface, tem precedência sobre esta política. Se for ativada, esta política é ignorada. Consulte também a política "Zonas de segurança: Utilize apenas as definições da máquina".  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Predefinição**: Desativado  
  
- **Roteiro de zona de internet do Internet Explorer do Internet iniciado**  
  Esta definição de política permite-lhe gerir restrições em janelas e janelas pop-up iniciadas por scripts que incluem o título e barras de estado. Se ativar esta definição de política, a segurança das Restrições do Windows não se aplica nesta zona. A zona de segurança funciona sem a camada adicional de segurança fornecida por esta funcionalidade. Se desativar esta definição de política, as possíveis ações nocivas contidas em janelas e janelas pop-up iniciadas por scripts que incluem o título e as barras de estado não podem ser executadas. Esta funcionalidade de segurança do Internet Explorer encontra-se nesta zona, tal como dita a definição de controlo de funcionalidades de controlo de funcionalidades de restrições de segurança do Windows scripted para o processo. Se não configurar esta definição de política, as possíveis ações nocivas contidas em janelas e janelas pop-up iniciadas por scripts que incluem o título e as barras de estado não podem ser executadas. Esta funcionalidade de segurança do Internet Explorer encontra-se nesta zona, tal como dita a definição de controlo de funcionalidades de controlo de funcionalidades de restrições de segurança do Windows scripted para o processo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Predefinição**: Desativado  
  
- **As zonas de segurança do Internet Explorer utilizam apenas as definições da máquina**  
  Aplica informações de zona de segurança a todos os utilizadores do mesmo computador. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, as alterações que o utilizador faz para uma zona de segurança aplicar-se-ão a todos os utilizadores desse computador. Se desativar esta política ou não a configurar, os utilizadores do mesmo computador podem estabelecer as suas próprias definições de zona de segurança. Utilize esta política para garantir que as definições da zona de segurança se aplicam uniformemente ao mesmo computador e não variam de utilizador para utilizador. Consulte também a política "Zonas de Segurança: não permita que os utilizadores mudem as políticas".  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer bloqueou permissões java da zona de máquina local**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, as maçãs Java são desativadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Predefinição**: Desative o java 
  
- A zona restrita do **Internet Explorer não executa antimalware contra os controlos Ative X**   
  Esta definição de política determina se o Internet Explorer executa programas antimalware contra controlos ActiveX, para verificar se são seguros para carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Os utilizadores podem ligar ou desligar este comportamento, utilizando as definições de Segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Predefinição**: Desativado  
  
- **Internet Explorer área restrita executado .NET Estrutura componentes dependentes assinados com autenticação**  
  Esta definição de política permite-lhe gerir se os componentes .NET Framework que são assinados com authenticode podem ser executados a partir do Internet Explorer. Estes componentes incluem controlos geridos referenciados a partir de uma etiqueta de objeto e executáveis geridos referenciados a partir de um link. Se ativar esta definição de política, o Internet Explorer executará componentes geridos assinados. Se selecionar O Prompt na caixa de lançamento, o Internet Explorer irá solicitar ao utilizador que determine se executa os componentes geridos assinados. Se desativar esta definição de política, o Internet Explorer não executará componentes geridos assinados. Se não configurar esta definição de política, o Internet Explorer não executará componentes geridos assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Predefinição**: Desativar  
  
- **Internet Explorer restringiu o acesso à zona a fontes de dados**  
  Esta definição de política permite-lhe gerir se o Internet Explorer pode aceder a dados de outra zona de segurança utilizando o Microsoft XML Parser (MSXML) ou ActiveX Data Objects (ADO). Se ativar esta definição de política, os utilizadores podem carregar uma página na zona que utiliza MSXML ou ADO para aceder a dados de outro site da zona. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem que uma página carregue na zona que utiliza mSXML ou ADO para aceder a dados de outro site da zona. Se desativar esta definição de política, os utilizadores não podem carregar uma página na zona que utiliza MSXML ou ADO para aceder a dados de outro site da zona. Se não configurar esta definição de política, os utilizadores não podem carregar uma página na zona que utiliza MSXML ou ADO para aceder a dados de outro site na zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Predefinição**: Desativar 
  
- **A zona de internet do Internet Explorer não executa antimalware contra controlos ActiveX**  
  Esta definição de política determina se o Internet Explorer executa programas antimalware contra controlos ActiveX, para verificar se são seguros para carregar em páginas. Se ativar esta definição de política, o Internet Explorer não verificará com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se desativar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Se não configurar esta definição de política, o Internet Explorer verifica sempre com o seu programa antimalware para ver se é seguro criar uma instância do controlo ActiveX. Os utilizadores podem ligar ou desligar este comportamento, utilizando as definições de Segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Predefinição**: Desativado  
  
- **Cópia e pasta da zona de internet do Internet Explorer através do script**  
  Esta definição de política permite-lhe gerir se os scripts podem executar uma operação de prancheta (por exemplo, cortar, copiar e colar) numa região especificada. Se ativar esta definição de política, um script pode executar uma operação de prancheta. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados sobre se devem ou não realizar operações de clipboard. Se desativar esta definição de política, um guião não pode executar uma operação de prancheta. Se não configurar esta definição de política, um script pode executar uma operação de prancheta.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Predefinição**: Desativar  
  
- **O Internet Explorer utiliza o serviço de instalação Ative X**  
  Esta definição de política permite especificar como os controlos ActiveX são instalados. Se ativar esta definição de política, os comandos ActiveX só são instalados se o Serviço de Instalação ActiveX estiver presente e tiver sido configurado para permitir a instalação de controlos ActiveX. Se desativar ou não configurar esta definição de política, os controlos ActiveX, incluindo controlos por utilizador, são instalados através do processo de instalação padrão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Predefinição**: Ativado  
  
- **O Internet Explorer processa a proteção contra a elevação da zona**  
  O Internet Explorer coloca restrições em cada página Web que abre. As restrições dependem da localização da página Web (Internet, Intranet, zona de Máquina Local, e assim por diante). Por exemplo, as páginas Web no computador local têm menos restrições de segurança e estão na zona local da máquina, tornando a zona de segurança da Máquina Local um alvo privilegiado para utilizadores mal-intencionados. Se ativar esta definição de política, qualquer zona pode ser protegida da elevação da zona para todos os processos. Se desativar ou não configurar esta definição de política, os processos que não o Internet Explorer ou os listados na Lista de Processos não recebem essa proteção.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer internet descarregue controlos ActiveX não assinados**   
  Esta definição de política permite-lhe gerir se os utilizadores podem descarregar controlos ActiveX não assinados a partir da zona. Este código é potencialmente prejudicial, especialmente quando se vem de uma zona não confiável. Se ativar esta definição de política, os utilizadores podem executar controlos não assinados sem a intervenção do utilizador. Se selecionar O Aviso na caixa de entrega, os utilizadores são questionados para escolher se permitem que o controlo não assinado seja executado. Se desativar esta definição de política, os utilizadores não podem executar controlos não assinados. Se não configurar esta definição de política, os utilizadores não podem executar controlos não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Predefinição**: Desativar  
  
- A zona de **internet do Internet Explorer do Internet navega janelas e quadros em diferentes domínios**   
  Esta definição de política permite-lhe gerir a abertura de janelas e molduras e o acesso de aplicações em diferentes domínios. Se ativar esta definição de política, os utilizadores podem abrir janelas e quadros de outros domínios e aceder a aplicações de outros domínios. Se selecionar o Prompt na caixa de entrega, os utilizadores são questionados se permitem que janelas e caixilharias acedam a aplicações de outros domínios. Se desativar esta definição de política, os utilizadores não podem abrir janelas e quadros para aceder a aplicações de diferentes domínios. Se não configurar esta definição de política, os utilizadores podem abrir janelas e quadros de outros domínios e aceder a aplicações de outros domínios.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Predefinição**: Desativar  
  
- **Atualizações da zona de internet do Internet Explorer para barra de estado via script**  
  Esta definição de política permite-lhe gerir se um script pode atualizar a barra de estado dentro da zona. Se ativar esta definição de política, os scripts podem atualizar a barra de estado. Se desativar ou não configurar esta definição de política, o script não está autorizado a atualizar a barra de estado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Predefinição**: Desativado  
  
- **A zona restrita do Internet Explorer inclui o caminho local ao carregar ficheiros para o servidor**  
  Esta definição de política controla se as informações do caminho local forem enviadas quando o utilizador estiver a carregar um ficheiro através de um formulário HTML. Se as informações do caminho local forem enviadas, algumas informações podem ser reveladas involuntariamente ao servidor. Por exemplo, os ficheiros enviados do ambiente de trabalho do utilizador podem conter o nome do utilizador como parte do caminho. Se ativar esta definição de política, as informações do caminho são enviadas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se desativar esta definição de política, as informações do caminho são removidas quando o utilizador está a carregar um ficheiro através de um formulário HTML. Se não configurar esta definição de política, o utilizador pode escolher se as informações do caminho são enviadas quando estão a enviar um ficheiro através de um formulário HTML. Por padrão, a informação do caminho é enviada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Predefinição**: Desativado  
  
- **Os processos do Internet Explorer restringem** o download de ficheiros   
  Esta definição de política permite que as aplicações que hospedam o Controlo do Navegador Web bloqueiem a solicitação automática de transferências de ficheiros que não são iniciadas pelo utilizador. Se ativar esta definição de política, o Controlo do Navegador Web bloqueará a solicitação automática de transferências de ficheiros que não são iniciados pelo utilizador para todos os processos. Se desativar esta definição de política, o Controlo de Navegador web não bloqueará a solicitação automática de transferências de ficheiros que não são iniciados pelo utilizador para todos os processos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Predefinição**: Ativado  
  
- A zona restrita do **Internet Explorer permite que apenas os domínios aprovados utilizem controlos Ative X**   
  Esta definição de política controla se o utilizador for solicitado a permitir que os controlos ActiveX possam ser executados em websites que não o website que instalou o controlo ActiveX. Se ativar esta definição de política, o utilizador é solicitado antes que os controlos ActiveX possam ser executados a partir de websites nesta zona. O utilizador pode optar por permitir que o controlo possa ser executado a partir do site atual ou de todos os sites. Se desativar esta definição de política, o utilizador não vê o pedido do ActiveX por site, e os controlos ActiveX podem ser executados a partir de todos os sites desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Predefinição**: Ativado  
  
- **Internet Explorer área restrita inicializar e script Controlos Ative X não marcados como seguros**  
  Esta definição de política permite-lhe gerir os controlos ActiveX não marcados como seguros. Se ativar esta definição de política, os controlos ActiveX funcionam, carregados com parâmetros e escritos sem definir a segurança do objeto para dados ou scripts não confiáveis. Esta definição não é recomendada, exceto para zonas seguras e administradas. Esta definição faz com que os controlos inseguros e seguros sejam inicializados e scripts, ignorando os comandos Script ActiveX marcados como seguros para a opção de script. Se ativar esta definição de política e selecionar o Prompt na caixa de lançamento, os utilizadores são questionados se permitem que o controlo carregue com parâmetros ou scripts. Se desativar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não são carregados com parâmetros ou scripts. Se não configurar esta definição de política, os controlos ActiveX que não podem ser tornados seguros não estão carregados com parâmetros ou scripts.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Predefinição**: Desativar  
  
- **Utilizadores do Internet Explorer que mudam as políticas**  
  Impede que os utilizadores mudem as definições da zona de segurança. Uma zona de segurança é um grupo de Web sites com o mesmo nível de segurança. Se ativar esta política, o botão De Nível Personalizado e o slider de nível de segurança no separador Segurança na caixa de diálogo Opções de Internet são desativados. Se desativar esta política ou não a configurar, os utilizadores podem alterar as definições para zonas de segurança. Esta política impede que os utilizadores mudem as definições de zona de segurança estabelecidas pelo administrador. Nota: A política "Desativar a página de segurança" (localizada em \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), que remove o separador de segurança do Internet Explorer no Painel de Controlo, tem precedência sobre esta política. Se for ativada, esta política é ignorada. Consulte também a política "Zonas de segurança: Utilize apenas as definições da máquina".  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Predefinição**: Desativado  
  
- **Modo protegido por zona restrita do Internet Explorer**  
  Esta definição de política permite-lhe ligar o Modo Protegido. O Modo Protegido ajuda a proteger o Internet Explorer de vulnerabilidades exploradas, reduzindo os locais a que o Internet Explorer pode escrever no registo e no sistema de ficheiros. Se ativar esta definição de política, o Modo Protegido está ligado. O utilizador não pode desligar o Modo Protegido. Se desativar esta definição de política, o Modo Protegido está desligado. O utilizador não pode ligar o Modo Protegido. Se não configurar esta definição de política, o utilizador pode ligar ou desligar o Modo Protegido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Padrão**: Ativar  
  
- **Persistência de dados de utilizadores da zona de internet do Internet Explorer**  
  Esta definição de política permite-lhe gerir a preservação da informação no histórico do navegador, nos favoritos, numa loja XML, ou diretamente dentro de uma página Web guardada para disco. Quando um utilizador retorna a uma página persistiu, o estado da página pode ser restaurado se esta definição de política estiver devidamente configurada. Se ativar esta definição de política, os utilizadores podem preservar informações no histórico do navegador, nos favoritos, numa loja XML ou diretamente dentro de uma página Web guardada para disco. Se desativar esta definição de política, os utilizadores não podem preservar informações no histórico do navegador, nos favoritos, numa loja XML ou diretamente dentro de uma página Web guardada para disco. Se não configurar esta definição de política, os utilizadores podem preservar informações no histórico do navegador, nos favoritos, numa loja XML ou diretamente dentro de uma página Web guardada para disco.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Predefinição**: Desativado  
  
- **Scripting de zona de internet do Internet Explorer do Internet dos controlos do navegador web**  
 
  Esta definição de política determina se uma página pode controlar os controlos do WebBrowser incorporados através do script. Se ativar esta definição de política, é permitido o acesso ao script ao controlo WebBrowser. Se desativar esta definição de política, o acesso do script ao controlo webBrowser não é permitido. Se não configurar esta definição de política, o utilizador pode ativar ou desativar o acesso do script ao controlo do WebBrowser. Por predefinição, o acesso ao script ao controlo WebBrowser só é permitido nas zonas Local Machine e Intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Predefinição**: Desativado  
  
- **Internet Explorer restringiu a persistência de dados de utilizadores de zona**  
  Esta definição de política permite-lhe gerir a preservação da informação no histórico do navegador, nos favoritos, numa loja XML, ou diretamente dentro de uma página Web guardada para disco. Quando um utilizador retorna a uma página persistiu, o estado da página pode ser restaurado se esta definição de política estiver devidamente configurada. Se ativar esta definição de política, os utilizadores podem preservar informações no histórico do navegador, nos favoritos, numa loja XML ou diretamente dentro de uma página Web guardada para disco. Se desativar esta definição de política, os utilizadores não podem preservar informações no histórico do navegador, nos favoritos, numa loja XML ou diretamente dentro de uma página Web guardada para disco. Se não configurar esta definição de política, os utilizadores não podem preservar informações no histórico do navegador, nos favoritos, numa loja XML ou diretamente dentro de uma página Web guardada para disco.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Predefinição**: Desativado  
  
- **Internet Explorer bloqueou permissões java da zona intranet**  
  Esta definição de política permite-lhe gerir permissões para applets Java. Se ativar esta definição de política, pode escolher opções a partir da caixa de lançamento. Personalizado, para controlar as definições de permissões individualmente. A Low Safety permite que as applets realizem todas as operações. A Medium Safety permite que as applets corram na sua caixa de areia (uma área na memória fora da qual o programa não pode fazer chamadas), além de capacidades como o espaço de risco (uma área de armazenamento segura e segura no computador cliente) e o ficheiro controlado pelo utilizador I/O. A Alta Segurança permite que as maçãs corram na sua caixa de areia. Desative Java para evitar que as maçãs se esgotem. Se desativar este cenário de política, as maçãs Java não podem correr. Se não configurar esta definição de política, as maçãs Java são desativadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Predefinição**: Desative o java  
  
- **Modo protegido melhorado do Internet Explorer**  
  O Modo Protegido Melhorado fornece proteção adicional contra websites maliciosos utilizando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam pelo menos o Windows 8, o Modo Protegido Melhorado também limita as localizações que o Internet Explorer pode ler no registo e no sistema de ficheiros. Se ativar esta definição de política, o modo de proteção melhorado está ligado. Qualquer zona ativada pelo modo protegido utilizará o modo protegido melhorado. Os utilizadores não poderão desativar o Modo Protegido Melhorado. Se desativar esta definição de política, o modo proteção melhorado está desligado. Qualquer zona ativada pelo Modo Protegido utilizará a versão do Modo Protegido introduzida no Internet Explorer 7 para o Windows Vista. Se não configurar esta política, os utilizadores podem ligar ou desligar o Modo Protegido Melhorado no separador Avançado do diálogo opções de Internet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Predefinição**: Ativado  
  
- **Avisos de ecrã inteligente do Internet Explorer bypass**  
  Esta definição de política determina se o utilizador pode contornar as advertências do Filtro SmartScreen. O Filtro SmartScreen avisa o utilizador sobre ficheiros executáveis que os utilizadores do Internet Explorer não descarregam normalmente a partir da Internet. Se ativar esta definição de política, os avisos do Filtro SmartScreen bloqueiam o utilizador. Se desativar ou não configurar esta definição de política, o utilizador pode contornar as advertências do Filtro SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Predefinição**: Desativado  
  
- **Internet Explorer área restrita meta refresh**  
  Esta definição de política permite-lhe gerir se o navegador de um utilizador pode ser redirecionado para outra página Web se o autor da página Web utilizar a definição Meta Refresh (tag) para redirecionar os navegadores para outra página Web. Se ativar esta definição de política, o navegador de um utilizador que carregue uma página contendo uma definição de Meta Refresh ativa pode ser redirecionado para outra página Web. Se desativar esta definição de política, o navegador de um utilizador que carrega uma página contendo uma definição de Meta Refresh ativa não pode ser redirecionado para outra página Web. Se não configurar esta definição de política, o navegador de um utilizador que carrega uma página contendo uma definição de Meta Refresh ativa não pode ser redirecionado para outra página Web.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Predefinição**: Desativado  
  
## <a name="local-policies-security-options"></a>Opções de Segurança das Políticas Locais
Para mais informações, consulte [Política CSP - LocaiSPolíticasOp](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) na documentação do Windows. 

- **Restringir o acesso anónimo a canos e partilhas nomeados**  
  Quando ativado, esta definição de segurança restringe o acesso anónimo a ações e tubos às definições para: (1) Tubos nomeados que podem ser acedidos anonimamente (2) Partilhas que podem ser acedidas de forma anónima.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Padrão**: Sim  
  
- **Segurança mínima de sessão para servidores baseados em NTLM SSP**  
  Esta definição de segurança permite que um servidor exija a negociação de encriptação de 128 bits e/ou segurança de sessão NTLMv2. Estes valores dependem do valor de definição de nível de segurança do Lan Manager Authentication Level. As opções são: Exigir segurança da sessão NTLMv2: A ligação falhará se a integridade da mensagem não for negociada. Requer encriptação de 128 bits. A ligação falhará se a encriptação forte (128 bits) não for negociada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Predefinição**: Requerer encriptação NTLM V2 e 128 bits  
  
- **Minutos de inatividade do ecrã de bloqueio até que o protetor de ecrã seja ativado**  
  O Windows nota a inatividade de uma sessão de logon e, se a quantidade de tempo inativo exceder o limite de inatividade, então o protetor de ecrã será executado, bloqueando a sessão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Predefinição**: 15
  
- **Exigir que o cliente assine sempre comunicações digitalmente** Esta definição de segurança determina se todo o tráfego de canal seguro iniciado pelo membro do domínio deve ser assinado ou encriptado. Quando um computador se junta a um domínio, é criada uma conta de computador. Depois disso, quando o sistema começa, utiliza a palavra-passe da conta do computador para criar um canal seguro com um controlador de domínio para o seu domínio. Este canal seguro é utilizado para realizar operações como a passagem da NTLM através da autenticação, LSA SID/nome Lookup e muito mais. Esta definição determina se todo o tráfego de canal seguro iniciado pelo membro do domínio satisfaz os requisitos mínimos de segurança. Especificamente, determina se todo o tráfego de canal seguro iniciado pelo membro do domínio deve ser assinado ou encriptado. Se esta política estiver ativada, o canal seguro não será estabelecido a menos que seja negociada a assinatura ou encriptação de todo o tráfego de canais seguros. Se esta política for desativada, então a encriptação e a assinatura de todo o tráfego de canal seguro são negociados com o Controlador de Domínio, caso em que o nível de assinatura e encriptação depende da versão do Controlador de Domínio e das definições dos dois seguintes políticas: Membro do domínio: Encriptar digitalmente dados de canais seguros (quando possível) Membro do domínio: Sinal digitalmente dados de canal seguro (quando possível).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Padrão**: Sim
  
- **Nível de autenticação**  
  Esta definição de segurança determina qual o protocolo de autenticação de desafio/resposta utilizado para os logons de rede. Esta escolha afeta o nível de protocolo de autenticação utilizado pelos clientes, o nível de segurança da sessão negociado, e o nível de autenticação aceite pelos servidores da seguinte forma:  
  - *Enviar respostas LM e NTLM* - Os clientes usam a autenticação LM e NTLM e nunca usam a segurança da sessão NTLMv2; os controladores de domínio aceitam a autenticação LM, NTLM e NTLMv2. 
  - *Envie LM e NTLM - NTLMv2 se negociado* - Os clientes usam a autenticação LM e NTLM e utilizam a segurança da sessão NTLMv2 se o servidor o suportar; os controladores de domínio aceitam a autenticação LM, NTLM e NTLMv2. 
  - *Enviar apenas resposta NTLM* - Os clientes usam apenas a autenticação NTLM e utilizam a segurança da sessão NTLMv2 se o servidor a suportar; os controladores de domínio aceitam a autenticação LM, NTLM e NTLMv2. 
  - *Enviar apenas resposta NTLMv2* - Os clientes usam apenas a autenticação NTLMv2 e utilizam a segurança da sessão NTLMv2 se o servidor a suportar; os controladores de domínio aceitam a autenticação LM, NTLM e NTLMv2. 
  - *Envie apenas resposta NTLMv2. Recusa LM* - Os clientes usam apenas a autenticação NTLMv2 e utilizam a segurança da sessão NTLMv2 se o servidor o suportar; os controladores de domínio recusam LM (aceitar apenas a autenticação NTLM e NTLMv2). 
  - *Envie apenas resposta NTLMv2. Recusa LM e NTLM* - Os clientes usam apenas a autenticação NTLMv2 e utilizam a segurança da sessão NTLMv2 se o servidor o suportar; os controladores de domínio recusam LM e NTLM (aceitar apenas a autenticação NTLMv2).  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Predefinição**: Enviar apenas a resposta NTLMv2. Recusar LM e NTLM
  
- **Impedir que os clientes enviem senhas não encriptadas para servidores SMB de terceiros**  
  Se esta definição de segurança estiver ativada, o redirector do Bloco de Mensagens do Servidor (SMB) pode enviar senhas de texto simples para servidores SMB não Microsoft que não suportem encriptação de palavra-passe durante a autenticação. Enviar senhas não encriptadas é um risco de segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Padrão**: Sim
  
- **Requerem que o servidor assine as comunicações digitalmente sempre**  
  Esta definição de segurança determina se o cliente SMB tenta negociar a assinatura do pacote SMB. O protocolo do bloco de mensagens do servidor (SMB) fornece a base para a partilha de ficheiros e impressão da Microsoft e muitas outras operações de networking, como a administração remota do Windows. Para evitar ataques man-in-the-Middle que modificam pacotes SMB em trânsito, o protocolo SMB dá suporte à assinatura digital de pacotes SMB. Esta definição de política determina se o componente do cliente SMB tenta negociar a assinatura de pacotes SMB quando se conecta a um servidor SMB. Se esta definição estiver ativada, o cliente da rede Microsoft pedirá ao servidor para realizar a assinatura do pacote SMB após a configuração da sessão. Se a assinatura de pacotes tiver sido ativada no servidor, a assinatura de pacotes será negociada. Se esta política for desativada, o cliente SMB nunca negociará a assinatura do pacote SMB.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Padrão**: Sim
  
- **Comportamento de elevação do administrador**  
  Esta definição de política controla o comportamento do pedido de elevação para os administradores. As opções são: 
  - *Elevar sem solicitação* - Permite que contas privilegiadas realizem uma operação que requer elevação sem necessidade de consentimento ou credenciais. Nota: Utilize esta opção apenas nos ambientes mais constrangidos. 
  - *Solicita-te credenciais no ambiente* de trabalho seguro - Quando uma operação requer elevação de privilégios, o utilizador é solicitado no ambiente de trabalho seguro para introduzir um nome de utilizador privilegiado e uma palavra-passe. Se o utilizador introduzir credenciais válidas, a operação continua com o maior privilégio disponível do utilizador. 
  - *Solicitação para consentimento no ambiente* de trabalho seguro - Quando uma operação requer elevação de privilégio, o utilizador é solicitado no ambiente de trabalho seguro para selecionar licença ou negar. Se o utilizador selecionar licença, a operação continua com o maior privilégio disponível do utilizador. 
  - *Solicitação de credenciais* - Quando uma operação requer elevação de privilégio, o utilizador é solicitado a introduzir um nome de utilizador administrativo e senha. Se o utilizador introduzir credenciais válidas, a operação continua com o privilégio aplicável. 
  - *Solicitação de consentimento* - Quando uma operação requer elevação de privilégio, o utilizador é solicitado a selecionar licença ou negar. Se o utilizador selecionar licença, a operação continua com o maior privilégio disponível do utilizador.  
  - *Solicitação de consentimento para binários não Windows* - Quando uma operação para uma aplicação não Microsoft requer elevação de privilégio, o utilizador é solicitado no ambiente de trabalho seguro para selecionar licença ou negar. Se o utilizador selecionar licença, a operação continua com o maior privilégio disponível do utilizador. 
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Predefinição**: Solicitação para consentimento no ambiente de trabalho seguro
  
- **Segurança mínima de sessão para clientes baseados em NTLM SSP**  
  Esta definição de segurança permite que um cliente exija a negociação de encriptação de 128 bits e/ou segurança de sessão NTLMv2. Estes valores dependem do valor de definição de nível de segurança do Lan Manager Authentication Level. As opções são:
  - Exigir segurança da *sessão NTLMv2* - A ligação falhará se o protocolo NTLMv2 não for negociado. 
  - *Requerer encriptação de 128 bits* - A ligação falhará se a encriptação forte (128 bits) não for negociada.
  - *Exija encriptação NTLMv2 e 128 bits*.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Predefinição**: Requerer encriptação NTLM V2 128
  
- **Comportamento de remoção de cartões inteligentes**  
  Esta definição de segurança determina o que acontece quando o cartão inteligente para um utilizador ligado é removido do leitor de cartões inteligentes. As opções são:
  - *Sem ação.* 
  - *Lock Workstation* - A estação de trabalho fica bloqueada quando o cartão inteligente é removido, permitindo que os utilizadores saiam da área, levem consigo o seu cartão inteligente e mantenham ainda uma sessão protegida.
  - *Force Logoff* - o utilizador é automaticamente desligado quando o cartão inteligente é removido.
  - *Desconecte a sessão de ambiente* de trabalho remoto - A remoção do cartão inteligente desliga a sessão sem desligar o utilizador. Isto permite ao utilizador inserir o cartão inteligente e retomar a sessão mais tarde, ou em outro computador equipado com cartão inteligente, sem ter de voltar a iniciar sessão. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Padrão**: Bloquear a estação de trabalho
  
- **Bloqueie a enumeração anónima das contas e ações da SAM**  
  Esta definição de segurança determina se permite a enumeração anónima das contas e ações da SAM. O Windows permite que utilizadores anónimos realizem determinadas atividades, tais como enumerar os nomes das contas de domínio e das partilhas de rede. Isto é conveniente, por exemplo, quando um administrador quer conceder acesso aos utilizadores num domínio de confiança que não mantenha uma confiança recíproca. Se não quiser permitir a enumeração anónima das contas e ações da SAM, então der essa política a *Sim*.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Padrão**: Sim
  
- **Bloqueie o logon remoto com senha em branco**  
  Esta definição de segurança determina se as contas locais que não estão protegidas podem ser usadas para iniciar sessão a partir de outros locais que não a consola de computador físico. Se ativadas, as contas locais que não estejam protegidas por palavra-passe devem utilizar o teclado do computador para iniciar sessão. 

  *Aviso*: Os computadores que não se localizam fisicamente devem aplicar políticas de senha fortes para todas as contas de utilizadores locais. Caso contrário, qualquer pessoa com acesso físico ao computador pode iniciar sessão utilizando uma conta de utilizador que não tenha uma senha. Isto é especialmente importante para computadores portáteis. 

  Se aplicar esta política de segurança ao grupo Todos, ninguém pode iniciar sessão através dos Serviços de Ambiente de Trabalho Remoto. Esta definição não afeta os logons que utilizam contas de domínio. É possível aplicações que usam logons interativos remotos para contornar esta configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Padrão**: Sim
  
- **Comportamento de elevação padrão do utilizador**  
  Esta definição de política controla o comportamento do pedido de elevação para os utilizadores padrão. 
  - *Negar automaticamente os pedidos* de elevação - Quando uma operação requer elevação de privilégio, é apresentada uma mensagem de erro de acesso configurável. Uma empresa que esteja a executar desktops como utilizador padrão pode escolher esta definição para reduzir as chamadas de secretária de ajuda. 
  - *Solicita-te credenciais no ambiente* de trabalho seguro - Quando uma operação requer elevação de privilégios, o utilizador é solicitado no ambiente de trabalho seguro para introduzir um nome e senha de utilizador diferentes. Se o utilizador introduzir credenciais válidas, a operação continua com o privilégio aplicável. 
  - *Solicitação de credenciais* - Quando uma operação requer elevação de privilégio, o utilizador é solicitado a introduzir um nome de utilizador administrativo e senha. Se o utilizador introduzir credenciais válidas, a operação continua com o privilégio aplicável.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Predefinição**: Negar automaticamente os pedidos de elevação
  
- **Exigir modo de aprovação de administradores para administradores**  
  Esta definição de política controla o comportamento de todas as definições de política de Controlo de Conta de Utilizador (UAC) para o computador. Se alterar esta definição de política, tem de reiniciar o computador. As opções são:   
  - *Não configurado* - O Modo de Aprovação do Administrador e todas as definições de política uac relacionadas são desativadas. Nota: Se esta definição de política for desativada, o Centro de Segurança informa que a segurança global do sistema operativo foi reduzida. 
  - *Sim* - O Modo de Aprovação de Administrador está ativado. Esta política deve ser ativada e as definições de política uac relacionadas devem ser definidas adequadamente para permitir que a conta de Administrador incorporado e todos os outros utilizadores que sejam membros do grupo administradores possam executar no Modo de Aprovação de Administradores.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Padrão**: Sim
  
- **Evitar a enumeração anónima das contas SAM**  
  Esta definição de segurança determina que permissões adicionais são concedidas para ligações anónimas ao computador. O Windows permite que utilizadores anónimos realizem determinadas atividades, tais como enumerar os nomes das contas de domínio e das partilhas de rede. Isto é conveniente, por exemplo, quando um administrador quer conceder acesso aos utilizadores num domínio de confiança que não mantenha uma confiança recíproca. Esta opção de segurança permite que sejam colocadas restrições adicionais em ligações anónimas da seguinte forma: 
  - *Sim* - Não permita a enumeração das contas SAM. Esta opção substitui todos os utilizadores autenticados nas permissões de segurança para recursos.
  - *Não configurado* - Sem restrições adicionais. Confie em permissões padrão.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Padrão**: Sim
  
- **Permitir chamadas remotas para gestor de contas de segurança**  
  Esta definição de política permite-lhe restringir as ligações remotas de rpc à SAM. Se não for selecionado, o descritor de segurança predefinido é utilizado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Predefinição**: *O:BAG:BAD:(A;; RC;;; BA)*

- **Utilize o modo de aprovação de administradores**  
  Esta definição de política controla o comportamento do Modo de Aprovação de Administradores para a conta de Administrador incorporado. As opções são: 
  - *Sim* - A conta de administrador incorporado utiliza o Modo de Aprovação do Administrador. Por predefinição, qualquer operação que exija elevação de privilégios levará o utilizador a aprovar a operação. 
  - *Não Configurado* - A conta de Administrador incorporado executa todas as aplicações com pleno privilégio administrativo. 

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Padrão**: Sim
  
- **Permitir aplicações de acesso ui para locais seguros**  
  Esta definição de política controla se os programas de acessibilidade da interface do utilizador (UIAccess ou UIA) podem desativar automaticamente o ambiente de trabalho seguro para obter indicações de elevação utilizadas por um utilizador padrão. 
  - *Sim* - Os programas UIA, incluindo o Windows Remote Assistance, desativam automaticamente o ambiente de trabalho seguro para obter indicações de elevação. Se não desativar a definição de definição de "Controlo de Conta do Utilizador: Mude para o ambiente de trabalho seguro quando pedir elevação", as indicações aparecem no ambiente de trabalho do utilizador interativo em vez do ambiente de trabalho seguro. 
  - *Não configurado*: - O ambiente de trabalho seguro só pode ser desativado pelo utilizador do ambiente de trabalho interativo ou desativando a definição de política "User Account Control: Switch para o ambiente de trabalho seguro quando pedir elevação".  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Padrão**: Sim

- **Detetar instalações de aplicações e solicitação para elevação**  
  Esta definição de política controla o comportamento da deteção de instalação de aplicação para o computador. As opções são: 
  - *Ativado* - Quando é detetado um pacote de instalação de aplicação que requer elevação de privilégios, o utilizador é solicitado a introduzir um nome administrativo de utilizador e uma palavra-passe. Se o utilizador introduzir credenciais válidas, a operação continua com o privilégio aplicável. 
  - *Desativado* - Os pacotes de instalação de aplicação não são detetados e solicitados para elevação. As empresas que estão a executar desktops de utilizadores padrão e utilizam tecnologias de instalação delegadas, como a Instalação de Software de Política de Grupo ou o Servidor de Gestão de Sistemas (SMS) devem desativar esta definição de política. Neste caso, a deteção do instalador é desnecessária.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Padrão**: Sim
  
- **Evite armazenar valor hash do gestor lan na próxima alteração de senha**  
  Esta definição de segurança determina se, na próxima alteração de senha, o lan manager (LM) valor hash para a nova palavra-passe é armazenado. O hash LM é relativamente fraco e propenso a atacar, em comparação com o hash nt do Windows NT criptograficamente mais forte. Uma vez que o hash LM é armazenado no computador local na base de dados de segurança, as palavras-passe podem ser comprometidas se a base de dados de segurança for atacada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Padrão**: Sim

- **Virtualize falhas de registo e registo por localização de utilizadores**  
  Esta definição de política controla se as falhas de escrita da aplicação são redirecionadas para locais definidos de registo e sistema de ficheiros. Esta definição de política atenua aplicações que funcionam como administrador e escrevem dados de aplicações a tempo de execução para *%ProgramFiles%* , *%Windir%* , *%Windir%\system32*, ou *HKLM\Software*.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Padrão**: Sim

## <a name="ms-security-guide"></a>Guia de Segurança Sra.  
Para mais informações, consulte [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) na documentação do Windows.  

- **Aplicar restrições uac às contas locais em início de rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Predefinição**: Ativado
  
- **Configuração de início do controlador do cliente SMB v1**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Predefinição**: Controlador deficiente
  
- **Servidor SMB v1**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Predefinição**: Desativado
  
- **Autenticação digestiva**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Predefinição**: Desativado
  
- **Proteção por exceção estruturada sobre a sobreescrita**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Predefinição**: Ativado
  
## <a name="mss-legacy"></a>Legado da Sra.  
Para mais informações, consulte [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) na documentação do Windows.  

- **Nível de proteção de encaminhamento de fonte IP da rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Padrão**: Proteção mais elevada  
  
- **Rede ignora pedidos de lançamento de nome NetBIOS exceto de servidores WINS**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Predefinição**: Ativado
  
- **Nível de proteção de encaminhamento de fonte IPv6**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Padrão**: Proteção mais elevada

- **Rede ICMP redireciona os OSPF gerados**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Predefinição**: Desativado
  
## <a name="power"></a>Poder  
Para mais informações, consulte [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentação.  

- **Exigir senha no velório enquanto está ligado**  
  Esta definição de política especifica se o utilizador for solicitado para obter uma senha quando o sistema recomeçar do sono. Se ativar ou não configurar esta definição de política, o utilizador é solicitado para obter uma palavra-passe quando o sistema recomeçar a partir do sono. Se desativar esta definição de política, o utilizador não é solicitado para obter uma palavra-passe quando o sistema retoma do sono.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Predefinição**: Ativado
  
- **Estados de espera ao dormir durante a bateria**  
  Esta definição de política gere se o Windows puder utilizar estados de espera ao colocar o computador em estado de sono. Se ativar ou não configurar esta definição de política, o Windows utiliza estados de espera para colocar o computador em estado de sono. Se desativar esta definição de política, os Estados de prontidão (S1-S3) não são permitidos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Predefinição**: Desativado
  
- **Estados de espera ao dormir em vez de ligados**  
  Esta definição de política gere se o Windows puder utilizar estados de espera ao colocar o computador em estado de sono. Se ativar ou não configurar esta definição de política, o Windows utiliza estados de espera para colocar o computador em estado de sono. Se desativar esta definição de política, os Estados de prontidão (S1-S3) não são permitidos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Predefinição**: Desativado
  
- **Requerer senha no despertar enquanto está na bateria**  
  Esta definição de política especifica se o utilizador for solicitado para obter uma senha quando o sistema recomeçar do sono. Se ativar ou não configurar esta definição de política, o utilizador é solicitado para obter uma palavra-passe quando o sistema recomeçar a partir do sono. Se desativar esta definição de política, o utilizador não é solicitado para obter uma palavra-passe quando o sistema retoma do sono.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Predefinição**: Ativado

## <a name="remote-assistance"></a>Assistência Remota
- **Assistência Remota solicitada**  
  Esta definição de política permite-lhe ligar ou desligar a Assistência Remota Solicitada (Pedir) assistência remota neste computador. 
  - *Se ativar esta definição*de política, os utilizadores deste computador podem usar e-mail ou transferência de ficheiros para pedir ajuda a alguém. Além disso, os utilizadores podem utilizar programas de mensagens instantâneas para permitir ligações a este computador, e pode configurar definições adicionais de Assistência Remota. 
  - *Se desativar esta definição*de política, os utilizadores deste computador não podem utilizar e-mail ou transferência de ficheiros para pedir ajuda a alguém. Além disso, os utilizadores não podem utilizar programas de mensagens instantâneas para permitir ligações a este computador. 
  - *Se não configurar esta definição*de política, os utilizadores podem ligar ou desligar a Assistência Remota solicitada (Pedir) a si próprias em Propriedades do Sistema no Painel de Controlo. Os utilizadores também podem configurar as definições de Assistência Remota. 

  Se ativar esta definição de política, tem duas formas de permitir que os ajudantes forneçam assistência remota: "Permita que os ajudantes apenas vejam o computador" ou "Permita que os ajudantes controlem remotamente o computador." A definição da política "Tempo máximo de bilhete" estabelece um limite no tempo que um convite de Assistência Remota criado através da utilização de e-mail ou transferência de ficheiros pode permanecer aberto. A definição "Selecione o método de envio de convites por e-mail" especifica qual a norma de e-mail a utilizar para enviar convites de assistência remota. Dependendo do seu programa de e-mail, pode utilizar a norma Mailto (o destinatário do convite conecta-se através de um link de Internet) ou a norma SMAPI (MapI simples) (o convite está anexado à sua mensagem de e-mail). Esta definição de política não está disponível no Windows Vista uma vez que o SMAPI é o único método suportado. Se ativar esta definição de política, deve também permitir exceções adequadas à firewall para permitir comunicações de assistência remota.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Predefinição**: Desativar a assistência remota

  Quando programado para ativar a *assistência remota,* configure as seguintes definições adicionais:  
  - **Autorização solicitada pela Assistência Remota**  
    **Padrão**: Visualização  

  - **Valor máximo do tempo do bilhete**  
    **Predefinição**: *Não configurado*  

  - **Período máximo de tempo de bilhete**  
    **Predefinição**: Minutos    

  - **Método de convite por e-mail**  
    **Padrão**: MAPI simples

  
## <a name="remote-desktop-services"></a>Serviços de Ambiente de Trabalho Remoto  
Para mais informações, consulte [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) na documentação do Windows.  

- **Bloquear a poupança de palavra-passe**  
  Controla se as palavras-passe podem ser guardadas neste computador a partir da Ligação remota de ambiente de trabalho. Se ativar esta definição da caixa de verificação de poupança de palavras-passe em Remote Desktop Connection está desativada e os utilizadores não poderão guardar palavras-passe. Quando um utilizador abre um ficheiro RDP utilizando a Ligação remota de ambiente de trabalho e guarde as suas definições, qualquer palavra-passe que existiu anteriormente no ficheiro RDP é eliminada. Se desativar esta definição ou a deixar não configurada, o utilizador pode guardar palavras-passe utilizando a Ligação remota de ambiente de trabalho.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Predefinição**: Ativado
  
- **Comunicação RPC segura**  
  Especifica se um servidor de anfitrião de sessão de ambiente de trabalho remoto requer uma comunicação RPC segura com todos os clientes ou permite uma comunicação não segura. Pode utilizar esta definição para reforçar a segurança da comunicação RPC com os clientes, permitindo apenas pedidos autenticados e encriptados. Se o estado for definido para Enabled, remote Desktop Services aceita pedidos de clientes RPC que suportam pedidos seguros, e não permite comunicação não segura com clientes não confiáveis. Se o estado for definido para Desativado, os Serviços de Ambiente de Trabalho Remoto sempre solicitam segurança para todo o tráfego de RPC. No entanto, é permitida uma comunicação não segura para clientes RPC que não respondam ao pedido. Se o estado estiver definido para não configurado, é permitida uma comunicação não segura. Nota: A interface RPC é utilizada para administrar e configurar serviços de ambiente de trabalho remotos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Predefinição**: Ativado
  
- **Redirecionamento de unidade de bloqueio**  
  Esta definição de política especifica se deve impedir o mapeamento das unidades do cliente numa sessão de Serviços de Ambiente de Trabalho Remoto (redirecionamento de unidade). Por predefinição, um servidor rd Session Host mapeia o cliente automaticamente após a ligação. As unidades mapeadas aparecem na pasta da sessão no File Explorer ou no Computador no formato *\<driveletter>* em *\<nome de computador>* . Pode usar esta definição de política para anular este comportamento. Se ativar esta definição de política, a redirecção de unidade do cliente não é permitida nas sessões de Serviços de Ambiente de Trabalho Remoto, e a redirecção de cópias de ficheiros de clipboard não é permitida em computadores que executam o Windows Server 2003, Windows 8 e Windows XP. Se desativar esta definição de política, a reorientação da unidade do cliente é sempre permitida. Além disso, a redirecção da cópia do ficheiro de clipboard é sempre permitida se for permitida a reorientação da área de clipboard. Se não configurar esta definição de política, a redirecção de direção do cliente e a redirecção da cópia de ficheiros de clipboard não são especificadas ao nível da Política de Grupo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Predefinição**: Ativado
  
- **Solicitação para senha após ligação**  
  Esta definição de política especifica se os Serviços de Ambiente de Trabalho Remoto supor sempre o cliente para obter uma palavra-passe após a ligação. Pode utilizar esta definição para impor um pedido de senha para os utilizadores que iniciam sessão nos Serviços de Ambiente de Trabalho Remoto, mesmo que já tenham fornecido a palavra-passe no cliente de Ligação remota de ambiente de trabalho. Por predefinição, os Serviços de Ambiente de Trabalho Remoto permitem que os utilizadores iniciem automaticamente o início, inserindo uma palavra-passe no cliente de Ligação remota de ambiente de trabalho. Se ativar esta definição de política, os utilizadores não podem iniciar sessão automaticamente nos Serviços de Ambiente de Trabalho Remoto, fornecendo as suas palavras-passe no cliente de Ligação remota de ambiente de trabalho. são solicitados para que uma senha entre. Se desativar esta definição de política, os utilizadores podem sempre iniciar sessão nos Serviços de Ambiente de Trabalho Remoto sem equei, fornecendo automaticamente as suas palavras-passe no cliente de Ligação remota de ambiente de trabalho. Se não configurar esta definição de política, o logon automático não é especificado ao nível da Política de Grupo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Predefinição**: Ativado
  
- **Nível de encriptação de ligação ao cliente dos serviços de ambiente de trabalho remoto**  
  Especifica se deve exigir a utilização de um nível de encriptação específico para proteger as comunicações entre computadores clientes e servidores rd session host durante as ligações do Protocolo de Ambiente de Trabalho Remoto (RDP). Esta política só se aplica quando se está a usar encriptação de RDP nativa. No entanto, a encriptação de RDP nativo (ao contrário da encriptação SSL) não é recomendada. Esta política não se aplica à encriptação SSL. Se ativar esta definição de política, todas as comunicações entre clientes e servidores rd session host durante ligações remotas devem utilizar o método de encriptação especificado nesta definição. Por padrão, o nível de encriptação está definido para Alto. Estão disponíveis os seguintes métodos de encriptação:  
  - *High* - A configuração alta encripta os dados enviados do cliente para o servidor e do servidor para o cliente utilizando uma encriptação forte de 128 bits. Utilize este nível de encriptação em ambientes que contenham apenas 128 clientes (por exemplo, clientes que executam a Ligação remota de ambiente de trabalho). Os clientes que não suportam este nível de encriptação não podem ligar-se aos servidores rd Session Host.  
  - *Compatível com* o cliente - A definição compatível com o Cliente encripta os dados enviados entre o cliente e o servidor na força-chave máxima suportada pelo cliente. Use este nível de encriptação em ambientes que incluem clientes que não suportam encriptação de 128 bits.  
  - *Low* - A configuração Low encripta apenas os dados enviados do cliente para o servidor utilizando encriptação de 56 bits.  
  
  Se desativar ou não configurar esta definição, o nível de encriptação a utilizar para ligações remotas aos servidores rd Session Host não é aplicado através da Política do Grupo. A conformidade importante com os FIPS pode ser configurada através da criptografia do Sistema. Utilize algoritmos compatíveis com FIPS para encriptação, hashing e definições de assinatura na Política de Grupo (em configuração de computador\Definições do Windows\Definições de segurança\Políticas locais\Opções de segurança.) A definição de definição compatível com FIPS encripta e desencripta os dados enviados do cliente para o servidor e do servidor para o cliente, com os algoritmos de encriptação Standard de Processamento de Informação Federal (FIPS) 140, utilizando módulos criptográficos da Microsoft. Utilize este nível de encriptação quando as comunicações entre clientes e servidores rd session host requerem o mais alto nível de encriptação.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Padrão**: Alto
  
## <a name="remote-management"></a>Gestão Remota  
Para mais informações, consulte [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) na documentação do Windows.  

- **Bloquear o armazenamento funcionam como credenciais**  
  Autenticação básica do cliente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Predefinição**: Ativado
  
- **Autenticação básica**  
  Esta definição de política permite-lhe gerir se o serviço de Gestão Remota do Windows (WinRM) aceita a autenticação Básica de um cliente remoto. Se ativar esta definição de política, o serviço WinRM aceita a autenticação Básica de um cliente remoto. Se desativar ou não configurar esta definição de política, o serviço WinRM não aceita autenticação Básica de um cliente remoto.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Predefinição**: Desativado
  
- **Bloquear a autenticação de digestão do cliente**  
  Esta definição de política permite-lhe gerir se o cliente de Gestão Remota do Windows (WinRM) utiliza a autenticação Digest. Se ativar esta definição de política, o cliente WinRM não utiliza a autenticação Digest. Se desativar ou não configurar esta definição de política, o cliente WinRM utiliza a autenticação Digest.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Predefinição**: Ativado
  
- **Tráfego não encriptado**  
  Esta definição de política permite-lhe gerir se o serviço de Gestão Remota do Windows (WinRM) envia e recebe mensagens não encriptadas na rede. Se ativar esta definição de política, o cliente WinRM envia e recebe mensagens não encriptadas pela rede. Se desativar ou não configurar esta definição de política, o cliente WinRM envia ou recebe apenas mensagens encriptadas pela rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Predefinição**: Desativado
  
- **Tráfego não encriptado do cliente**  
  Esta definição de política permite-lhe gerir se o cliente de Gestão Remota do Windows (WinRM) envia e recebe mensagens não encriptadas pela rede. Se ativar esta definição de política, o cliente WinRM envia e recebe mensagens não encriptadas pela rede. Se desativar ou não configurar esta definição de política, o cliente WinRM envia ou recebe apenas mensagens encriptadas pela rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Predefinição**: Desativado
  
- **Autenticação básica do cliente**  
  Esta definição de política permite-lhe gerir se o cliente de Gestão Remota do Windows (WinRM) utiliza a autenticação Básica. Se ativar esta definição de política, o cliente WinRM utiliza a autenticação Básica. Se o WinRM estiver configurado para utilizar o transporte HTTP, o nome do utilizador e a palavra-passe são enviados para a rede como texto claro. Se desativar ou não configurar esta definição de política, o cliente WinRM não utiliza a autenticação Básica.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Predefinição**: Desativado
  
## <a name="remote-procedure-call"></a>Chamada de procedimento remoto  
Para mais informações, consulte [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) na documentação do Windows.  

- **Opções de cliente não autenticadas RPC**  
  Esta definição de política controla a forma como o tempo de funcionamento do servidor RPC lida com clientes RPC não autenticados que se ligam aos servidores RPC. Esta definição de política tem impacto em todas as aplicações RPC. Num ambiente de domínio, utilize esta definição de política com cuidado, pois pode afetar uma vasta gama de funcionalidades, incluindo o próprio processamento da política de grupo. Reverter uma alteração a esta definição de política pode requerer uma intervenção manual em cada máquina afetada. Esta definição de política nunca deve ser aplicada a um controlador de domínio. Se desativar esta definição de política, o tempo de execução do servidor RPC utiliza o valor de "Autenticado" no Cliente windows e o valor de "Nenhum" nas versões do Windows Server que suportam esta definição de política. Se não configurar esta definição de política, permanece desativada. O tempo de funcionação do servidor RPC comporta-se como se estivesse ativado com o valor de "Autenticado" utilizado para o Windows Client e o valor de "Nenhum" utilizado para o Server SKUs que suporta esta definição de política. Se ativar esta definição de política, direciona o tempo de execução do servidor RPC para restringir os clientes RPC não autenticados que se ligam aos servidores RPC que funcionam numa máquina. Um cliente é considerado um cliente autenticado se utilizar um tubo nomeado para comunicar com o servidor ou se utilizar a Segurança RPC. As Interfaces RPC que tenham pedido especificamente para serem acessíveis por clientes não autenticados podem estar isentas desta restrição, dependendo do valor selecionado para esta definição de política.  
  - *Nenhum* permite que todos os clientes RPC se conectem aos Servidores RPC em execução na máquina na qual a definição de política é aplicada. 
  - *Autenticado* permite que apenas os Clientes RPC autenticados (de acordo com a definição acima) se conectem aos Servidores RPC em execução na máquina em que a definição de política é aplicada. São concedidas isenções às interfaces que as solicitaram. 
  - *Autenticado sem exceções* permite que apenas os Clientes RPC autenticados (de acordo com a definição acima) se conectem aos Servidores RPC em execução na máquina em que a definição de política é aplicada. Não são permitidas exceções. Nota: Esta definição de política não será aplicada até que o sistema seja reiniciado.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Padrão**: Autenticado

## <a name="search"></a>Procura 
Para mais informações, consulte [Policy CSP - Procure](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) na documentação do Windows.  

- **Desativar itens encriptados de indexação**  
  Permite ou proíbe a indexação de itens. Este switch é para o Indexante de Pesquisa do Windows, que controla se irá indexar itens que estão encriptados, como os ficheiros protegidos de Proteção de Informação do Windows (WIP). Quando a política está ativada, os itens protegidos pelo WIP são indexados e os respetivos metadados são armazenados numa localização não encriptada. Os metadados incluem conteúdos como o caminho do ficheiro e a data de modificação. Quando a apólice é desativada, os itens protegidos do WIP não são indexados e não aparecem nos resultados em Cortana ou explorador de ficheiros. O desempenho das aplicações de fotografias e do Groove também poderá ser afetado se existirem muitos ficheiros multimédia protegidos pelo WIP no dispositivo.  
  [Saiba mais]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Padrão**: Sim
  
## <a name="smart-screen"></a>Tela Inteligente  
Para mais informações, consulte [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.  

- **Bloquear a execução de ficheiros não verificados**  
  Bloqueie o utilizador de executar ficheiros não verificados. 
  - *Não Configurado* - Os colaboradores podem ignorar os avisos smartScreen e executar ficheiros maliciosos. 
  - *Sim* – Os colaboradores não podem ignorar os avisos do SmartScreen e executar ficheiros maliciosos.

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Padrão**: Sim

- **Requerer smartScreen para apps e ficheiros**  
  Permite que os administradores de TI configurem o SmartScreen para windows.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Padrão**: Sim
  
## <a name="system"></a>Sistema  
Para mais informações, consulte [Política CSP - Sistema](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) na documentação do Windows.  

- **Inicialização do controlador do arranque do sistema**  
  Esta definição de política permite especificar quais os controladores de arranque de arranque são inicializados com base numa classificação determinada por um controlador antimalware de lançamento precoce. O controlador de arranque antimalware de lançamento antecipado pode devolver as seguintes classificações para cada condutor de arranque de arranque: 
  - *O* motorista foi contratado e não foi adulterado.  
  - *Mau* - O condutor foi identificado como malware. Recomendamos que não permita que os maus condutores conhecidos sejam inicializados. 
  - *Mau, mas necessário para o arranque* - O condutor foi identificado como malware, mas o computador não consegue arrancar sem carregar este controlador. 
  - *Unknown* - Este controlador não foi atestado pela sua aplicação de deteção de malware e não foi classificado pelo controlador de arranque antimalware de lançamento precoce.  

  Se ativar esta definição de política, pode escolher quais os controladores de arranque para inicializar a próxima vez que o computador for iniciado. Se desativar ou não configurar esta definição de política, os controladores de arranque de arranque determinados a ser bons, desconhecidos ou maus, mas a Boot Critical são inicializadas e a inicialização dos condutores determinados a ser Mau é ignorada. Se a sua aplicação de deteção de malware não incluir um controlador de arranque antimalware de lançamento precoce ou se o seu controlador de arranque antimalware de lançamento precoce tiver sido desativado, esta definição não tem efeito e todos os controladores de arranque de arranque são inicializados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Padrão**: Bom desconhecido e mau crítico


## <a name="wi-fi"></a>Wi-Fi  
Para mais informações, consulte [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) na documentação do Windows.  

- **Block Partilha de Internet**  
  Especifica se a partilha de internet é possível no dispositivo.   
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Padrão**: Sim  

- **Bloquear Ligar-se automaticamente aos hotspots Wi-Fi**  
  Permitir ou não permitir que o dispositivo se ligue automaticamente aos hotspots Wi-Fi.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Padrão**: Sim  
  
## <a name="windows-connection-manager"></a>Gestor de ligação ao Windows  
Para mais informações, consulte [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) na documentação do Windows.  

- **Bloquear a ligação a redes não-domínio**  
  Esta definição de política impede que os computadores se conectem tanto a uma rede baseada em domínios como a uma rede não baseada em domínios ao mesmo tempo. Se esta definição de política estiver ativada, o computador responde a tentativas de ligação automática e manual de rede com base nas seguintes circunstâncias: 
  - Tentativas de ligação automática Quando o computador já está ligado a uma rede baseada em domínios, todas as tentativas de ligação automática a redes não-domínio são bloqueadas. Quando o computador já está ligado a uma rede não baseada em domínios, as tentativas de ligação automática a redes baseadas em domínios são bloqueadas. 
  - Tentativas de ligação manual Quando o computador já está ligado a uma rede não baseada em domínios ou a uma rede baseada em domínios através de meios que não o Ethernet, e um utilizador tenta criar uma ligação manual a uma rede adicional em violação desta política definição, a ligação de rede existente desliga-se e a ligação manual é permitida. Quando o computador já está ligado a uma rede não baseada em domínios ou a uma rede baseada em domínios sobre o Ethernet, e um utilizador tenta criar uma ligação manual a uma rede adicional em violação desta definição de política, a ligação Ethernet existente é mantida e a tentativa de ligação manual está bloqueada.  

  Se esta definição de política não estiver configurada ou for desativada, os computadores podem ligar-se simultaneamente a redes de domínio e não-domínio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Predefinição**: Ativado
  
## <a name="microsoft-defender"></a>Microsoft Defender  
Para mais informações, consulte [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.  

- **Digitalizar mensagens de correio de entrada**  
  Permite ou proíbe a digitalização de e-mail.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Padrão**: Sim  

- **Aplicativos de escritório lançam tipo de processo infantil**  
  As aplicações de escritório não serão autorizadas a criar processos infantis. Isto inclui Word, Excel, PowerPoint, OneNote e Access. Este é um comportamento típico de malware, especialmente para ataques macro-baseados que tentam usar aplicações do Office para lançar ou descarregar executáveis maliciosos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Predefinição**: Bloco
  
- **Tipo de consentimento de submissão de amostra de defensor**  
  Verifica o nível de consentimento do utilizador no Microsoft Defender para enviar dados. Se o consentimento exigido já tiver sido concedido, o Microsoft Defender submete-os. Caso contrário, (e se o utilizador tiver especificado nunca pedir), a UI é lançada para pedir o consentimento do utilizador (quando o Defender/AllowCloudProtection é permitido) antes de enviar dados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Predefinição**: Enviar amostras seguras automaticamente 
  
- **Intervalo de atualização de assinatura (em horas)**  
  Intervalo de atualização de assinatura de defender em horas
  
  **Padrão**: 4
  
- **Script descarregado tipo de execução de carga útil**  
  Script defensor descarregado tipo de execução de carga útil
  
  **Predefinição**: Bloco
  
- **Prevenir o tipo de roubo de credenciais**  
  A Microsoft Defender Credential Guard usa segurança baseada em virtualização para isolar segredos para que apenas o software privilegiado do sistema possa aceder aos mesmos. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, como pass-the-Hash ou Pass-The-Ticket. A Microsoft Defender Credential Guard impede estes ataques protegendo as hashes de senha NTLM, os bilhetes de concessão de bilhetes Kerberos e credenciais armazenadas por aplicações como credenciais de domínio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Padrão**: Ativar

- **Tipo de execução de conteúdo de e-mail**  
  Esta regra bloqueia os seguintes tipos de ficheiros de serem executados ou lançados a partir de um e-mail visto no Microsoft Outlook ou no webmail (como Gmail.com ou Outlook.com): Ficheiros executáveis (tais como ficheiros de script .exe, .dll ou .scr) (tais como powerShell .ps, VisualBasic .vbs, ou ficheiro sinuoso do Script ScriptScript .js. Script.  
  [Saiba mais](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail) 
  
  **Predefinição**: Bloco

- **Lançamento do leitor adobe em processo infantil**  

  **Padrão**: Ativar

- **Tipo de proteção de rede**  
  Esta política permite-lhe ativar a proteção da rede (block/audit) ou desligar no Microsoft Defender Exploit Guard. A proteção de rede é uma funcionalidade do Microsoft Defender Exploit Guard que protege os funcionários que usam qualquer aplicação para aceder a esquemas de phishing, sites de hospedagem de exploração e conteúdo malicioso na Internet. Isto inclui impedir que os navegadores de terceiros se conectem a sites perigosos. O tipo de valor é inteiro. Se ativar esta definição, a proteção da rede é ativada e os funcionários não podem desligá-lo. O seu comportamento pode ser controlado pelas seguintes opções: Bloquear e Auditar. Se ativar esta política com a opção "Block", os utilizadores e aplicações estão impedidos de se ligarem a domínios perigosos. Pode ver esta atividade no Microsoft Defender Security Center. Se ativar esta política com a opção "Auditoria", os utilizadores/aplicações não serão impedidos de se ligarem a domínios perigosos. No entanto, ainda vai ver esta atividade no Microsoft Defender Security Center. Se desativar esta política, os utilizadores/aplicações não serão impedidos de se ligarem a domínios perigosos. Não verá nenhuma atividade de rede no Microsoft Defender Security Center. Se não configurar esta política, o bloqueio da rede é desativado por defeito.  
  [Saiba mais](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)  
  
  **Padrão**: Ativar
  
- **Dia de scan do defender**  
  O defender marca o dia da varredura.
  
  **Padrão**: Todos os dias
  
- **Proteção entregue em nuvem**  
  Para melhor proteger o seu PC, o Microsoft Defender enviará informações à Microsoft sobre quaisquer problemas que encontre. A Microsoft analisará essa informação, aprenderá mais sobre problemas que afetam o mesmo e outros clientes e oferecerá soluções melhoradas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Padrão**: Sim  

- **Defender ação de aplicação potencialmente indesejada**  
  A funcionalidade de proteção de aplicações potencialmente indesejadas (PUA) no Antivírus Do Microsoft Defender pode identificar e bloquear as API de descarregar e instalar em pontos finais da sua rede. Estas aplicações não são consideradas vírus, malware ou outros tipos de ameaças, mas podem realizar ações em pontos finais que afetam negativamente o seu desempenho ou uso. A PUA também pode referir-se a aplicações que são consideradas como tendo uma má reputação. O comportamento típico da PUA inclui: Vários tipos de software que agregam a injeção de anúncios em navegadores web O condutor e os otimizadores de registo que detetam problemas, solicitam o pagamento para corrigir os erros, mas permanecem no ponto final e não fazem alterações ou otimizações (também conhecidas como " programas antivírus desonestos). Estas aplicações podem aumentar o risco de a sua rede estar infetada com malware, fazer com que as infeções por malware sejam mais difíceis de identificar e podem desperdiçar recursos de TI na limpeza das aplicações.  
  [Saiba mais](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Predefinição**: Bloco  

- **Script obfuscated macro código tipo**  
  Malware e outras ameaças podem tentar obstar ou esconder o seu código malicioso em alguns ficheiros de script. Esta regra impede que os scripts que parecem estar obfuscados de correr.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Predefinição**: Bloco
  
- **Digitalizar unidades amovíveis durante uma varredura completa**  
  Permite ao Microsoft Defender procurar software malicioso e indesejado em unidades amovíveis (por exemplo, pen drives) durante uma varredura completa. O Microsoft Defender Antivírus digitaliza todos os ficheiros em dispositivos USB antes da execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Padrão**: Sim  
  
- **Analisar ficheiros de arquivo**  
  Os ficheiros de arquivo do Defender scan.
  
  **Padrão**: Sim
  
- **Monitorização do comportamento**  
  Permite ou proíbe a funcionalidade de Monitorização de Comportamento do Microsoft Defender. Incorporados no Windows 10, estes sensores recolhem e processam sinais comportamentais do sistema operativo e enviam estes dados de sensores para a sua instância privada, isolada e cloud do Microsoft Defender ATP.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Padrão**: Sim

- **Scan ficheiros abertos a partir de pastas de rede**  
  Se os ficheiros forem apenas de leitura, o utilizador não será capaz de remover qualquer malware detetado.
  
  **Padrão**: Sim

- **Tipo de processo USB não confiável**  
  Com esta regra, os administradores podem impedir que ficheiros executáveis não assinados ou não confiáveis sejam executados a partir de unidades amovíveis USB, incluindo cartões SD.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Predefinição**: Bloco
  
- **Aplicativos de escritório outro tipo de injeção de processo**  
  As aplicações de escritório, incluindo Word, Excel, PowerPoint e OneNote, não serão capazes de injetar código noutros processos. Isto é normalmente usado por malware para executar código malicioso numa tentativa de esconder a atividade de motores de digitalização antivírus.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Predefinição**: Bloco
  
- **O código macro do escritório permite o tipo de importações Win32**  
  O malware pode usar o código macro nos ficheiros do Office para importar e carregar DLLs Win32, que podem ser usados para fazer chamadas API para permitir mais infeções em todo o sistema. Esta regra tenta bloquear ficheiros do Office que contêm código macro capaz de importar DLLs Win32. Isto inclui Word, Excel, PowerPoint e OneNote.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Predefinição**: Bloco  
  
- **Nível de bloco de nuvem de defensor**  
  Nível de bloco de nuvem de defensor.
  
  **Predefinição**: Não configurado

- **Monitorização em tempo real**  
  Defender requer monitorização em tempo real.
  
  **Padrão**: Sim
 
- **Aplicativos de comunicação do escritório lançam-se num processo infantil**  

  **Padrão**: Ativar

- **Aplicações de escritório executáveis criação de conteúdo ou tipo de lançamento**  
  Esta regra visa comportamentos típicos usados por addons e scripts suspeitos e maliciosos (extensões) que criam ou lançam ficheiros executáveis. Esta é uma técnica típica de malware. As extensões estão bloqueadas de serem usadas por aplicações do Office. Normalmente, estas extensões utilizam o Windows Scripting Host (ficheiros.wsh) para executar scripts que automatizam determinadas tarefas ou fornecem funcionalidades adicionais criadas pelo utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Predefinição**: Bloco

## <a name="microsoft-defender-firewall"></a>Microsoft defender firewall  
Para mais informações, consulte [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) na documentação dos Protocolos do Windows.  

- **Domínio de perfil de firewall**  
  Especifica os perfis a que a regra pertence: Domínio, Privado, Público. Este valor representa o perfil para redes ligadas a domínios.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Ligações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Ligações de saída necessárias**  
    **Padrão**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Firewall ativado**  
    **Padrão**: Permitido

- **Público de perfil firewall**  
  Especifica os perfis a que a regra pertence: Domínio, Privado, Público. Para nós, este número é um eixo de uma comunidade que quer saber para onde vai e quer saber para onde vai e quer saber para onde vai e quer saber Estas redes são classificadas como públicas pelos administradores do servidor. A classificação acontece na primeira vez que o anfitrião se conecta à rede. Normalmente, estas redes são as dos aeroportos, cafés e outros locais públicos onde os pares da rede ou o administrador da rede não são de confiança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Ligações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Ligações de saída necessárias**  
    **Padrão**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Firewall ativado**  
    **Padrão**: Permitido

  - **Regras de segurança de ligação da política do grupo não fundidas**  
    **Padrão**: Sim

  - **Regras políticas da política de grupo não fundidas**  
    **Padrão**: Sim

- **Perfil de firewall privado**  
  Especifica os perfis a que a regra pertence: Domínio, Privado, Público. Este valor representa o perfil para redes privadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Ligações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Ligações de saída necessárias**  
    **Padrão**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Firewall ativado**  
    **Padrão**: Permitido

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas  

- **Bloqueie janelas Olá para negócios**  
    O Windows Hello for Business é um método alternativo para iniciar sessão no Windows substituindo palavras-passe, Smart Cards e Cartões Inteligentes Virtuais.  
  - Quando definido para *desativar,* os dispositivos aprovisionam o Windows Hello for Business.
  - Quando definido para *Não configurado,* a linha de base não afeta a definição de política do dispositivo. Isto significa que o estado atual do Windows Hello for Business num dispositivo permanece no lugar.

  Pode desativar o Windows Hello for Business quando configurar a [inscrição](windows-hello.md)do Windows, ou como parte de um perfil de configuração do dispositivo para [proteção de identidade](identity-protection-configure.md).  

  - **Predefinição**: Ativado

  As seguintes definições estão disponíveis quando esta definição estiver definida para *desativar*.

  - **Permitir a utilização de uma luta anti-falsificação melhorada, quando disponível**  
    Se Sim, os dispositivos utilizarão uma maior enão, quando disponível. Se não, a falsificação será bloqueada. Não configurado irá honrar as configurações feitas no cliente.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067192)

    **Padrão**: Sim

  - **Letras minúsculas em PIN**  
    Se *necessário,* o PIN do utilizador deve incluir pelo menos uma letra minúscula.

    **Padrão**: Permitido

  - **Caracteres especiais em PIN**  
    Se *necessário,* o PIN do utilizador deve incluir pelo menos um personagem especial.

    **Padrão**: Permitido

  - **Comprimento mínimo pin**  
    O comprimento mínimo do PIN deve ser entre 4 e 127.

    **Padrão**: 6

  - **Letras maiúsculas em PIN**  
    Se *necessário,* o PIN do utilizador deve incluir pelo menos uma letra maiúscula.

    **Padrão**: Permitido


## <a name="windows-ink-workspace"></a>Espaço de trabalho de tinta windows  
Para mais informações, consulte [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) na documentação do Windows.  

- **Espaço de trabalho de tinta**  
  Especifica se permite ao utilizador aceder ao espaço de trabalho de tinta. 
  - *Desativado* - o acesso ao espaço de trabalho de tinta é desativado. O recurso está desativado.
  - *Ativado* - A função De Trabalho da Tinta está ligada, mas o utilizador não pode aceder-lhe acima do ecrã de bloqueio.
  - *Não configurado* - A função de espaço de trabalho de tinta está ligada e o utilizador pode usá-lo acima do ecrã de bloqueio.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Predefinição**: Ativado
 
## <a name="windows-powershell"></a>Windows PowerShell  
Para mais informações, consulte [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) na documentação do Windows.  

- **Madeira de bloco de script de concha de concha de potência**  
  Esta definição de política permite o registo de todas as entradas de script powerShell para o registo de eventos Microsoft-Windows-PowerShell/Operational. Se ativar esta definição de política, o Windows PowerShell registará o processamento de comandos, blocos de scripts, funções e scripts - seja invocado interativamente, quer através da automação. Se desativar esta definição de política, o registo da entrada do script PowerShell é desativado. Se ativar o Registo de Invocação de Bloqueio de Script, o PowerShell regista adicionalmente eventos quando a invocação de um comando, bloco de script, função ou script começa ou para. Ativar a exploração de registos de exploração gera um elevado volume de registos de eventos. Nota: Esta definição de política existe tanto na Configuração do Computador como na Configuração do Utilizador no Editor de Política do Grupo. A definição da política de configuração do computador tem precedência sobre a definição da política de configuração do utilizador.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Predefinição**: Ativado

## <a name="whats-changed-in-the-new-template"></a>O que mudou no novo modelo
O modelo de Base de Segurança do MDM para maio de *2019* tem as seguintes alterações do modelo de *pré-visualização.*

### <a name="changes-to-the-baseline-settings"></a>Alterações nas definições de base
As seguintes definições são:
- *Novidade* nesta última versão da linha de base.
- *Removido* desta versão mais recente, mas esteve presente na versão anterior.
- *Revisto de* alguma forma pela forma como as definições apareceram na versão anterior. 

*[Novo]* [**Acima da fechadura:** ](#above-lock)
- **Aplicativos de ativação de voz a partir de ecrã bloqueado**    

*[Nova]* [**Gestão de Aplicações:** ](#application-management) 
- **Bloqueie o controlo do utilizador sobre as instalações**  
- **Instalações de aplicações Block MSI com privilégios elevados**  

*[Removido]* [**BitLocker:** ](#bitlocker)  
- BitLocker política de unidade amovível > **Método de encriptação**
- Política de **unidade fixa BitLocker** *(todas as definições)*
- Política de **unidade de sistema BitLocker** *(todas as configurações)*

*[Nova]* [**Conectividade:** ](#connectivity)
- **Configure o acesso seguro aos caminhos da CNU**

*[Novo]* [**Dispositivo Guarda:** ](#device-guard)
- **Segurança baseada em virtualização**

*[Novo]* [**DMA Guarda:** ](#dma-guard)
- **Enumeração de dispositivos externos incompatíveis com a Proteção Kernel DMA**  

*[Novo]* [**Internet Explorer:** ](#internet-explorer)
- **Explorer internet zone atualizações para barra de estado via script**
- **Internet Explorer internet zone drag and drop or copy and paste files**  
- **Zona restrita do Internet Explorer .NET Estrutura componentes dependentes**  
- **A zona de máquina local do Internet Explorer não executa antimalware contra os controlos Ative X**
- **Suporte de encriptação do Internet Explorer**  

*[Revisto]* [**Internet Explorer:** ](#internet-explorer)
- **Internet Explorer internet zone automatic prompt for file downloads** > O valor padrão é agora **desativado**. Na pré-visualização, este foi definido para Enabled.

*[Nova]* [**Assistência Remota:** ](#remote-assistance)  
- **Assistência Remota solicitada** 
  - **Autorização solicitada pela Assistência Remota**
  - **Valor máximo do tempo do bilhete**  
  - **Período máximo de tempo de bilhete**  
  - **Método de convite por e-mail**


*[Novo]* [**Microsoft Defender:** ](#microsoft-defender)
- **Lançamento do leitor adobe em processo infantil**  
- **Aplicativos de comunicação do escritório lançam-se num processo infantil** 

*[Novo]* [ **Microsoft Defender Firewall**](#microsoft-defender-firewall)
- **Domínio de perfil de firewall**  
  - **Ligações de entrada bloqueadas**  
  - **Ligações de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall ativado**  
- **Público de perfil firewall**  
  - **Ligações de entrada bloqueadas**  
  - **Ligações de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall ativado** 
  - **Regras de segurança de ligação da política do grupo não fundidas**   
  - **Regras políticas da política de grupo não fundidas**  
- **Perfil de firewall privado**  
  - **Ligações de entrada bloqueadas**  
  - **Ligações de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall ativado**  

*[Novo]* [**Windows Hello for Business**](#windows-hello-for-business):  
- **Bloqueie janelas Olá para negócios**
  - **Permitir a utilização de uma luta anti-falsificação melhorada, quando disponível**  
  - **Letras minúsculas em PIN** 
  - **Caracteres especiais em PIN** 
  - **Comprimento mínimo pin**  
  - **Letras maiúsculas em PIN** 
