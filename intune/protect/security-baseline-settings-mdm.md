---
title: Configurações de linhas de base de segurança do Intune para Windows 10
titleSuffix: Microsoft Intune
description: Examine os padrões e as configurações disponíveis que são encontradas na linha de base de segurança do MDM do Windows para dispositivos Windows 10 gerenciados com o Intune.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7bba4617aa756c5f7168a2febf1a3f1ffdd2029
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71731960"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Configurações de linha de base de segurança do MDM para o Intune  

Exiba as configurações de linha de base de segurança do MDM com suporte pelo Microsoft Intune para dispositivos que executam o Windows 10 ou posterior. Os valores padrão para as configurações nessa linha de base representam a configuração recomendada para os dispositivos aplicáveis e podem não coincidir com os padrões de linha de base de outras linhas de base de segurança.  

A versão de linha de base mais recente é a **linha de base de segurança MDM para maio de 2019**  

Para saber mais sobre o que mudou na versão mais recente desta linha de base da versão anterior, consulte [o que mudou no novo modelo](#whats-changed-in-the-new-template).  

> [!NOTE]  
> Em junho de 2019, a linha de base de segurança do MDM de visualização foi substituída pelo lançamento da *linha de base de segurança do MDM para o modelo de maio de 2019* , que está geralmente disponível (não em versão prévia). Os perfis criados antes da disponibilidade da linha de base de segurança do MDM para a linha de base de *maio de 2019* não serão atualizados para refletir as configurações e os valores que estão na linha de base de segurança do MDM para a versão 2019 de maio.  Embora não seja possível criar novos perfis com base no modelo de visualização, você pode editar e continuar a usar perfis criados anteriormente com base no modelo de visualização.   
  
Para saber mais sobre como usar linhas de base de segurança com o Intune, confira [usar linhas de base de segurança](security-baselines.md).  


   
## <a name="above-lock"></a>Acima do bloqueio  
Para obter mais informações, consulte [Policy CSP-AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) na documentação do Windows.  

- **Bloquear a exibição de notificações do sistema**  
  Essa configuração de política permite impedir que as notificações do aplicativo apareçam na tela de bloqueio. Se você habilitar essa configuração de política, nenhuma notificação de aplicativo será exibida na tela de bloqueio. Se você desabilitar ou não definir essa configuração de política, os usuários poderão escolher quais aplicativos exibem notificações na tela de bloqueio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Padrão**: Sim  

- **Ativar voz de aplicativos da tela bloqueada**  

  **Padrão**: Desativado

## <a name="app-runtime"></a>Tempo de execução do aplicativo    
Para obter mais informações, [consulte Policy CSP-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) AppRuntime na documentação do Windows.  

- **Contas da Microsoft opcionais para aplicativos da Windows Store**  
  Essa configuração de política permite controlar se as contas da Microsoft são opcionais para aplicativos da Windows Store que exigem uma conta para entrar. Essa política afeta apenas os aplicativos da Windows Store que dão suporte a ela. Se você habilitar essa configuração de política, os aplicativos da Windows Store que normalmente exigem um conta Microsoft de entrada permitirão que os usuários entrem com uma conta empresarial. Se você desabilitar ou não definir essa configuração de política, os usuários deverão entrar com um conta Microsoft.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Padrão**: Enabled  

## <a name="application-management"></a>Gerenciamento de aplicativos   
Para obter mais informações, consulte [Policy CSP-ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) na documentação do Windows.  

- **Bloquear o controle do usuário sobre instalações**  
  Essa configuração de política permite que os usuários alterem as opções de instalação que normalmente estão disponíveis somente para administradores do sistema. Se você habilitar essa configuração de política, alguns dos recursos de segurança do Windows Installer serão ignorados. Ele permite que as instalações concluam que, caso contrário, seriam interrompidas devido a uma violação de segurança. Se você desabilitar ou não definir essa configuração de política, os recursos de segurança do Windows Installer evitarão que os usuários alterem as opções de instalação normalmente reservadas para administradores do sistema, como especificar o diretório no qual os arquivos são instalados. Se Windows Installer detectar que um pacote de instalação permitiu que o usuário alterasse uma opção protegida, ele interromperá a instalação e exibirá uma mensagem. Esses recursos de segurança operam somente quando o programa de instalação está sendo executado em um contexto de segurança privilegiado no qual ele tem acesso aos diretórios negados ao usuário. Essa configuração de política é projetada para ambientes menos restritivos. Ele pode ser usado para burlar erros em um programa de instalação que impede a instalação do software.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Padrão**: Sim

- **Bloquear instalações de aplicativos MSI com privilégios elevados**  
  Essa configuração de política direciona Windows Installer para usar permissões elevadas ao instalar qualquer programa no sistema.  
  - *Se você habilitar essa configuração de política*, os privilégios serão estendidos para todos os programas. Esses privilégios geralmente são reservados para programas que foram atribuídos ao usuário (oferecidos na área de trabalho), atribuídos ao computador (instalado automaticamente) f ou disponibilizados em Adicionar ou remover programas no painel de controle. Essa configuração de perfil permite que os usuários instalem programas que exigem acesso a diretórios que o usuário pode não ter permissão para exibir ou alterar, incluindo diretórios em computadores altamente restritos.
  - *Se você desabilitar ou não definir essa configuração de política*, o sistema aplicará as permissões do usuário atual ao instalar programas que um administrador de sistema não distribui ou oferece. Nota: Essa configuração de política aparece nas pastas configuração do computador e configuração do usuário. Para tornar essa configuração de política eficaz, você deve habilitá-la em ambas as pastas. Atenção Os usuários experientes podem aproveitar as permissões que essa configuração de política concede para alterar seus privilégios e obter acesso permanente a arquivos e pastas restritos. Observe que a versão de configuração do usuário dessa configuração de política não tem garantia de segurança.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Padrão**: Sim

- **Bloquear DVR de jogos (somente desktop)**  
  Configura se a gravação e a difusão de jogos são permitidas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Padrão**: Sim  

## <a name="auto-play"></a>Reprodução automática   
Para obter mais informações, consulte [CSP da política-reprodução automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) na documentação do Windows.  

- **Comportamento de execução automática padrão de reprodução automática**  
  Essa configuração afeta o comportamento padrão para comandos de Autorun. Os comandos de Autorun são armazenados em arquivos autorun. inf e podem iniciar programas de instalação ou outras rotinas. Quando *habilitado*, os administradores podem alterar o comportamento padrão de Autorun em um dispositivo que executa o Windows Vista ou posterior. O comportamento pode ser definido como: a) desabilitar completamente os comandos de autorun ou b) reverter para o comportamento anterior ao Windows Vista da execução automática do comando autorun. Quando definido como *desabilitado* ou *não configurado*, os dispositivos que executam o Windows Vista ou posterior solicitam ao usuário se um comando de Autorun deve ser executado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Padrão**: Não executar  
  
- **Modo de reprodução automática**  
  Essa configuração de política permite que você desative o recurso de reprodução automática. A reprodução automática começa a ler a partir de uma unidade assim que você insere a mídia na unidade. Como resultado, o arquivo de instalação de programas e a música em mídia de áudio são iniciados imediatamente. Antes do Windows XP SP2, a reprodução automática é desabilitada por padrão em unidades removíveis, como a unidade de disquete (mas não a unidade de CD-ROM) e em unidades de rede. A partir do Windows XP SP2, a reprodução automática é habilitada para unidades removíveis também, incluindo unidades zip e alguns dispositivos de armazenamento em massa USB. Se você habilitar essa configuração de política, a reprodução automática será desabilitada em unidades de CD-ROM e de mídia removível ou desabilitada em todas as unidades. Essa configuração de política desabilita a reprodução automática em tipos de unidades adicionais. Você não pode usar essa configuração para habilitar a reprodução automática em unidades nas quais ela está desabilitada por padrão. Se você desabilitar ou não definir essa configuração de política, a reprodução automática será habilitada. Nota: Essa configuração de política aparece nas pastas configuração do computador e configuração do usuário. Se as configurações de política entrarem em conflito, a configuração de política na configuração do computador terá precedência sobre a configuração de política na configuração do usuário.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Padrão**: Desativado

- **Bloquear reprodução automática para dispositivos que não são de volume**  
  Essa configuração de política não permite a reprodução automática de dispositivos MTP, como câmeras ou telefones. Se você habilitar essa configuração de política, a reprodução automática não será permitida para dispositivos MTP, como câmeras ou telefones. Se você desabilitar ou não definir essa configuração de política, a reprodução automática será habilitada para dispositivos que não são de volume.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Padrão**: Enabled  

## <a name="bitlocker"></a>Pelo    
Para obter mais informações, [consulte CSP de política](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) -BitLocker na documentação do Windows.  

- **Política de unidade removível do armário de bits**  
  Essa configuração de política é usada para controlar o método de criptografia e a intensidade de codificação. Os valores dessa política determinam a força da codificação que o BitLocker usa para criptografia. As empresas podem querer controlar o nível de criptografia para aumentar a segurança (o AES-256 é mais seguro do que o AES-128). Se você habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Para política de unidade removível de armário de bits, defina a seguinte configuração:

  - **Exigir criptografia para acesso de gravação**  
    **Padrão**: Sim  
  

## <a name="browser"></a>Browser  
Para obter mais informações, consulte [Policy CSP-browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) na documentação do Windows.  

- **Exigir SmartScreen para o Microsoft Edge**  
  O Microsoft Edge usa o Windows Defender SmartScreen (ativado) para proteger os usuários contra possíveis golpes de phishing e softwares mal-intencionados por padrão. Além disso, por padrão, os usuários não podem desabilitar (desligar) o Windows Defender SmartScreen. Habilitar essa política desativa o Windows Defender SmartScreen e impede que os usuários o liguem. Não configure essa política para permitir que os usuários optem por ativar ou desativar o Windows Defender SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Padrão**: Sim  
  
- **Bloquear acesso a sites mal-intencionados**  
  Por padrão, o Microsoft Edge permite que os usuários ignorem (ignoram) os avisos do Windows Defender SmartScreen sobre sites potencialmente mal-intencionados, permitindo que eles continuem no site. Com essa política, no entanto, você pode configurar o Microsoft Edge para impedir que os usuários ignorem os avisos, bloqueando-os de continuar para o site.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Padrão**: Sim  
  
- **Bloquear download de arquivo não verificado**  
  Por padrão, o Microsoft Edge permite que os usuários ignorem (ignoram) os avisos do Windows Defender SmartScreen sobre arquivos potencialmente mal-intencionados, permitindo que eles continuem baixando os arquivos não verificados. Habilitar essa política impede que os usuários ignorem os avisos, bloqueando-os do download dos arquivos não verificados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Padrão**: Sim  
  
- **Bloquear Gerenciador de senhas**  
  Por padrão, o Microsoft Edge usa o Gerenciador de senhas automaticamente, permitindo que os usuários gerenciadorem senhas localmente. Desabilitar essa política restringe o Microsoft Edge de usar o Gerenciador de senhas. Não configure essa política se desejar permitir que os usuários escolham salvar e gerenciar senhas localmente usando o Gerenciador de senhas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Padrão**: Sim  
  
- **Impedir substituições de erro de certificado**  
  Essa configuração de política impede que o usuário ignore erros de certificado de protocolo SSL/TLS (segurança de camada de transporte) que interrompem a navegação (como erros "expirados", "revogados" ou "incompatibilidade de nome") no Internet Explorer. Se você habilitar essa configuração de política, o usuário não poderá continuar a navegação. Se você desabilitar ou não definir essa configuração de política, o usuário poderá optar por ignorar os erros de certificado e continuar a navegação.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Padrão**: Sim  

## <a name="connectivity"></a>Conectividade  
Para obter mais informações, consulte [CSP da política-conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) na documentação do Windows.  

- **Bloquear o download da Internet para publicação na Web e assistentes de ordenação online**  
  Essa configuração de política especifica se o Windows deve baixar uma lista de provedores para os assistentes de publicação na Web e de ordenação online. Esses assistentes permitem que os usuários selecionem em uma lista de empresas que fornecem serviços como armazenamento online e impressão fotográfica. Por padrão, o Windows exibe os provedores baixados de um site do Windows, além dos provedores especificados no registro. Se você habilitar essa configuração de política, o Windows não baixará os provedores e somente os provedores de serviço armazenados em cache na exibição do Registro local. Se você desabilitar ou não definir essa configuração de política, uma lista de provedores será baixada quando o usuário usar os assistentes de publicação na Web ou de ordenação online. Para obter mais informações que incluem detalhes sobre como especificar provedores de serviço no registro, consulte a documentação para os assistentes de publicação na Web e ordenação online.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Padrão**: Enabled  

- **Configurar o acesso seguro a caminhos UNC**  
  Essa configuração de política define o acesso seguro aos caminhos UNC. Se você habilitar essa política, o Windows só permitirá o acesso aos caminhos UNC especificados depois de atender aos requisitos de segurança adicionais.
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **Padrão**: Configurar o Windows para permitir acesso somente aos caminhos UNC especificados depois de atender aos requisitos de segurança adicionais
  
  Quando *Configurar o Windows para permitir somente o acesso aos caminhos UNC especificados depois de atender aos requisitos de segurança adicionais* estiver selecionado, você poderá configurar a lista de caminhos UNC * LSN.
  - **Lista de caminhos UNC protegidos**  
    Selecione **Adicionar** para especificar sinalizadores de segurança adicionais e caminhos de servidor.  

- **Bloquear o download de drivers de impressão via HTTP**  
  Essa configuração de política especifica se deve permitir que este cliente baixe pacotes de driver de impressão via HTTP. Para configurar a impressão HTTP, os drivers que não são da caixa de entrada precisam ser baixados via HTTP. Nota: Essa configuração de política não impede que o cliente imprima em impressoras na intranet ou na Internet via HTTP. Ele proíbe apenas o download de drivers que ainda não estão instalados localmente. Se você habilitar essa configuração de política, os drivers de impressão não poderão ser baixados via HTTP. Se você desabilitar ou não definir essa configuração de política, os usuários poderão baixar drivers de impressão via HTTP.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Padrão**: Enabled  

## <a name="credentials-delegation"></a>Delegação de credenciais  
Para obter mais informações, [consulte Policy CSP-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) CredentialsDelegation na documentação do Windows.  

- **Delegação de host remoto de credenciais não exportáveis**  
  O host remoto permite a delegação de credenciais não exportáveis. Ao usar a delegação de credenciais, os dispositivos fornecem uma versão exportável de credenciais para o host remoto, o que expõe os usuários ao risco de roubo de credenciais de invasores no host remoto. Se você habilitar essa configuração de política, o host oferecerá suporte ao administrador restrito ou ao modo de proteção de credencial remota. Se você desabilitar ou não definir essa configuração de política, não haverá suporte para administração restrita e modo de proteção de credencial remota. O usuário sempre precisará passar suas credenciais para o host.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Padrão**: Enabled  

## <a name="credentials-ui"></a>IU de credenciais  
Para obter mais informações, consulte [Policy CSP-CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) na documentação do Windows.  

- **Enumerar administradores** Essa configuração de política controla se as contas de administrador são exibidas quando um usuário tenta elevar um aplicativo em execução. Por padrão, as contas de administrador não são exibidas quando o usuário tenta elevar um aplicativo em execução. Se você habilitar essa configuração de política, todas as contas de administrador local no PC são exibidas para que o usuário possa escolher uma e digitar a senha correta. Se você desabilitar essa configuração de política, os usuários sempre precisarão digitar um nome de usuário e senha para elevar.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Padrão**: Desativado  

## <a name="data-protection"></a>Proteção de dados  
Para obter mais informações, [consulte CSP de política-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) dataprotection na documentação do Windows.  

- **Bloquear o acesso direto à memória**  
  Essa configuração de política permite bloquear o DMA (acesso direto à memória) para todas as portas de downstream PCI conectadas a quente até que um usuário faça logon no Windows. Quando um usuário fizer logon, o Windows enumerará os dispositivos PCI conectados às portas PCI plug-host. Toda vez que o usuário bloqueia a máquina, o DMA é bloqueado em portas PCI de plugue a quente sem dispositivos filhos até que o usuário faça logon novamente. Os dispositivos que já foram enumerados quando o computador foi desbloqueado continuarão funcionando até serem desconectados. Essa configuração de política só é imposta quando o BitLocker ou a criptografia de dispositivo está habilitada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Padrão**: Sim  

## <a name="device-guard"></a>Proteção do dispositivo  
Para obter mais informações, [consulte Policy CSP-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) DeviceGuard na documentação do Windows.  

- **Proteção de credenciais**  
  Essa configuração permite que os usuários ativem o Credential Guard com segurança baseada em virtualização para ajudar a proteger as credenciais na próxima reinicialização.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Padrão**: Habilitar com bloqueio de UEFI 

- **Habilitar a segurança baseada em virtualização**   
  Ativa a VBS (segurança baseada em virtualização) na próxima reinicialização. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Padrão**: Sim  


- **Iniciar o System Guard**    
  **Padrão**: Enabled  

## <a name="device-installation"></a>Instalação do dispositivo  
Para obter mais informações, consulte [Policy CSP-DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) na documentação do Windows.  

- **Instalação de dispositivo de hardware por identificadores de dispositivo**  
  Essa configuração de política permite especificar uma lista de Plug and Play IDs de hardware e IDs compatíveis para dispositivos que o Windows é impedido de instalar. Essa configuração de política tem precedência sobre qualquer outra configuração de diretiva que permita que o Windows instale um dispositivo. Se você habilitar essa configuração de política, o Windows será impedido de instalar um dispositivo cuja ID de hardware ou ID compatível apareça na lista que você criar. Se você habilitar essa configuração de política em um servidor de área de trabalho remota, a configuração de política afetará o redirecionamento dos dispositivos especificados de um cliente de área de trabalho remota para o servidor de área de trabalho remota. Se você desabilitar ou não definir essa configuração de política, os dispositivos poderão instalar e atualizar conforme permitido ou impedido por outras configurações de política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **Padrão**: Bloquear a instalação do dispositivo de hardware  

  Quando *Bloquear instalação de dispositivo de hardware* estiver selecionado, as configurações a seguir estarão disponíveis.

  - **Remover dispositivos de hardware correspondentes**   
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por identificadores de dispositivo* está definida para *bloquear a instalação do dispositivo de hardware*.
    
    **Padrão**: Sim

  - **Identificadores de dispositivo de hardware que são bloqueados**  
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por identificadores de dispositivo* está definida para *bloquear a instalação do dispositivo de hardware*.
    
    **Padrão**: Sim  
  
- **Instalação de dispositivo de hardware por classes de instalação**  
  Essa configuração de política permite que você especifique uma lista de identificadores globais exclusivos (GUIDs) de classe de instalação de dispositivo para drivers de dispositivo que o Windows é impedido de instalar. Essa configuração de política tem precedência sobre qualquer outra configuração de diretiva que permita que o Windows instale um dispositivo. Se você habilitar essa configuração de política, o Windows será impedido de instalar ou atualizar drivers de dispositivo cujos GUIDs de classe de instalação de dispositivo aparecerão na lista que você criar. Se você habilitar essa configuração de política em um servidor de área de trabalho remota, a configuração de política afetará o redirecionamento dos dispositivos especificados de um cliente de área de trabalho remota para o servidor de área de trabalho remota. Se você desabilitar ou não definir essa configuração de política, o Windows poderá instalar e atualizar dispositivos como permitidos ou impedidos por outras configurações de política.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Padrão**: Bloquear a instalação do dispositivo de hardware  

  Quando *Bloquear instalação de dispositivo de hardware* estiver selecionado, as configurações a seguir estarão disponíveis.
  - **Remover dispositivos de hardware correspondentes**    
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por classes de instalação* está definida para *bloquear a instalação do dispositivo de hardware*.  

    **Padrão**: *Nenhuma configuração padrão*  

  - **Identificadores de dispositivo de hardware que são bloqueados**  
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por classes de instalação* está definida para *bloquear a instalação do dispositivo de hardware*.
    
    **Padrão**: *Nenhuma configuração padrão*  

## <a name="device-lock"></a>Bloqueio de dispositivo  
Para obter mais informações, consulte [Policy CSP-DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) na documentação do Windows.  

- **Impedir o uso da câmera**  
  Desabilita a opção de alternância da câmera da tela de bloqueio em configurações do PC e impede que uma câmera seja invocada na tela de bloqueio. Por padrão, os usuários podem habilitar a invocação de uma câmera disponível na tela de bloqueio. Se você habilitar essa configuração, os usuários não poderão mais habilitar ou desabilitar o acesso à câmera da tela de bloqueio nas configurações do PC e a câmera não poderá ser invocada na tela de bloqueio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Padrão**: Enabled  

- **Exigir senha**  
  Especifica se o bloqueio de dispositivo está habilitado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Padrão**: Sim  
  
  Quando *exigir senha* estiver definido como *Sim*, as configurações a seguir estarão disponíveis.

  - **Contagem de conjunto de caracteres mínimo de senha**  
    O número de tipos de elementos complexos (letras maiúsculas e minúsculas, números e pontuação) necessários para um PIN ou senha forte. O PIN impõe o seguinte comportamento para dispositivos móveis e de desktop: 1-dígitos somente dois dígitos e letras minúsculas são necessários três dígitos, letras minúsculas e letras maiúsculas são necessárias. Sem suporte em contas da Microsoft da área de trabalho e contas de domínio. 4-dígitos, letras minúsculas, letras maiúsculas e caracteres especiais são necessários. Sem suporte na área de trabalho. O valor predefinido é 1.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Padrão**: 3  

  - **Número de falhas de início de sessão antes de eliminar os dados do dispositivo**  
    O número de falhas de autenticação permitidas antes que o dispositivo seja apagado. Um valor de 0 desabilita A funcionalidade de apagamento do dispositivo.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Padrão**: 10  

  - **Expiração da Palavra-passe (dias)**  
    A configuração de política de duração máxima da senha determina o tempo (em dias) que uma senha pode ser usada antes que o sistema exija que o usuário a altere. Você pode definir senhas para expirar após um número de dias entre 1 e 999, ou pode especificar que as senhas nunca expirem definindo o número de dias como 0. Se a duração máxima da senha estiver entre 1 e 999 dias, a duração mínima da senha deverá ser menor que a duração máxima da senha. Se a duração máxima da senha for definida como 0, a duração mínima da senha poderá ser qualquer valor entre 0 e 998 dias.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Padrão**: 60  

  - **Tipo obrigatório de palavra-passe**  
    Determina o tipo de PIN ou senha necessária.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Padrão**: Alfanumérico  

  - **Comprimento mínimo da palavra-passe**  
    A configuração de política comprimento mínimo da senha determina o número mínimo de caracteres que podem criar uma senha para uma conta de usuário. Você pode definir um valor entre 1 e 14 caracteres ou pode estabelecer que nenhuma senha seja necessária definindo o número de caracteres como 0.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Padrão**: 8  

  - **Bloquear senhas simples**  
    Especifica se os PINs ou senhas, como "1111" ou "1234", são permitidos. Para a área de trabalho, ele também controla o uso de senhas de imagem.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Padrão**: Sim  
      *Uma configuração de Sim impede o uso de senhas simples.* 

  - **Impedir a reutilização de palavras-passe anteriores**  
    Especifica quantas senhas podem ser armazenadas no histórico que não podem ser usadas. O valor inclui a senha atual do usuário. Por exemplo, com uma configuração de *1* , o usuário não pode reutilizar sua senha atual ao escolher uma nova senha. Uma configuração de *5* significa que um usuário não pode definir sua nova senha para sua senha atual ou com qualquer uma de suas quatro senhas anteriores.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Padrão**: 24  

- **Impedir apresentação de slides**  
  Desabilita as configurações de apresentação de slides da tela de bloqueio nas configurações do computador e impede que uma apresentação de slides seja reproduzida na tela de bloqueio. Por padrão, os usuários podem habilitar uma apresentação de slides que será executada Depois de bloquear o computador. Se você habilitar essa configuração, os usuários não poderão modificar as configurações de apresentação de slides nas configurações do PC e nenhuma apresentação de slides poderá ser iniciada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Padrão**: Enabled  
  *Uma configuração habilitada impede que as apresentações de slides sejam executadas.* 

- **Idade mínima de senha em dias**  
  A configuração de política de duração mínima da senha determina o período de tempo (em dias) que uma senha deve ser usada antes que o usuário possa alterá-la. Você pode definir um valor entre 1 e 998 dias ou pode permitir alterações de senha imediatamente definindo o número de dias como 0. A duração mínima da senha deve ser menor que a duração máxima da senha, a menos que a duração máxima da senha seja definida como 0, indicando que as senhas nunca expirarão. Se a duração máxima da senha for definida como 0, a duração mínima da senha poderá ser definida para qualquer valor entre 0 e 998.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Padrão**: 1  

## <a name="dma-guard"></a>Proteção de DMA  
Para obter mais informações, consulte [Policy CSP-DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) na documentação do Windows.
- **Enumeração de dispositivos externos incompatíveis com a proteção de kernel DMA**  
  Essa política destina-se a fornecer segurança adicional contra dispositivos compatíveis com DMA externo. Ele permite mais controle sobre a enumeração de dispositivos compatíveis com DMA externo incompatíveis com o isolamento de memória de dispositivo/remapeamento de DMA e área restrita. Essa política só entra em vigor quando há suporte para a proteção do kernel DMA e ela é habilitada pelo firmware do sistema. A proteção de kernel DMA é um recurso de plataforma que não pode ser controlado pela política ou pelo usuário final. Ele precisa ser suportado pelo sistema no momento da fabricação. Para verificar se o sistema dá suporte à proteção de kernel DMA, verifique o campo proteção DMA do kernel na página Resumo do MSINFO32. exe.  
  [Saiba mais](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Padrão**: Bloquear tudo   

## <a name="event-log-service"></a>Serviço log de eventos  
Para obter mais informações, consulte [Policy CSP-EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) na documentação do Windows.  

- **Tamanho máximo do arquivo de log de segurança em KB**  
  Essa configuração de política especifica o tamanho máximo do arquivo de log em kilobytes. Se você habilitar essa configuração de política, poderá configurar o tamanho máximo do arquivo de log entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobytes. Se você desabilitar ou não definir essa configuração de política, o tamanho máximo do arquivo de log será definido como o valor configurado localmente. Esse valor pode ser alterado pelo administrador local usando a caixa de diálogo Propriedades do log e o padrão é 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Padrão**: 196608  

- **Tamanho máximo do arquivo de log do sistema em KB**  
  Essa configuração de política especifica o tamanho máximo do arquivo de log em kilobytes. Se você habilitar essa configuração de política, poderá configurar o tamanho máximo do arquivo de log entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobytes. Se você desabilitar ou não definir essa configuração de política, o tamanho máximo do arquivo de log será definido como o valor configurado localmente. Esse valor pode ser alterado pelo administrador local usando a caixa de diálogo Propriedades do log e o padrão é 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Padrão**: 32768  

- **Tamanho máximo do arquivo de log do aplicativo em KB**  
  Essa configuração de política especifica o tamanho máximo do arquivo de log em kilobytes. Se você habilitar essa configuração de política, poderá configurar o tamanho máximo do arquivo de log entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobytes. Se você desabilitar ou não definir essa configuração de política, o tamanho máximo do arquivo de log será definido como o valor configurado localmente. Esse valor pode ser alterado pelo administrador local usando a caixa de diálogo Propriedades do log e o padrão é 20 megabytes.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Padrão**: 32768  

## <a name="experience"></a>Experiência  
Para obter mais informações, consulte [Policy CSP-Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) na documentação do Windows.  

- **Bloquear destaque do Windows**  
  Permite que os administradores de ti desativem todos os recursos do Windows Spotlight – janela destaque na tela de bloqueio, dicas do Windows, recursos do Microsoft Consumer e outros recursos relacionados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Padrão**: Sim  

  Quando *Bloquear destaque do Windows* estiver definido como *Sim*, as configurações a seguir estarão disponíveis.
  
  - **Bloquear sugestões de terceiros no destaque do Windows**  
    Especifica se é permitido permitir sugestões de aplicativos e conteúdo de editores de software de terceiros em recursos de destaque do Windows, como o destaque da tela de bloqueio, aplicativos sugeridos no menu iniciar e dicas do Windows. Os usuários ainda podem ver sugestões para recursos, aplicativos e serviços da Microsoft.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Padrão**: Sim  
  - **Bloquear recursos específicos do consumidor**  
    Permite que os administradores de ti ativem experiências que normalmente são apenas para consumidores, como sugestões de início, notificações de associação, instalação de aplicativo post-OOBE e blocos de redirecionamento.  
    [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Padrão**: Sim  

## <a name="exploit-guard"></a>Exploit Guard  
Para obter mais informações, consulte [Policy CSP-ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) na documentação do Windows.  

- **Exploração de XML de proteção**  
  Permite que o administrador de ti envie uma configuração que represente as opções de mitigação de aplicativo e sistema desejadas para todos os dispositivos na organização. A configuração é representada por um XML. A proteção contra explorações ajuda a proteger dispositivos contra malware que usam explorações para disseminar e infectar. Você usa o aplicativo de segurança do Windows ou o PowerShell para criar um conjunto de atenuações (conhecido como uma configuração). Você pode exportar essa configuração como um arquivo XML e compartilhá-la com vários computadores na sua rede para que todos tenham o mesmo conjunto de configurações de mitigação. Você também pode converter e importar um arquivo XML de configuração do EMET existente em um XML de configuração do Exploit Protection.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Padrão**: *O XML de exemplo é fornecido* 
 
## <a name="file-explorer"></a>Explorador de Ficheiros  
Para obter mais informações, consulte [CSP de política – FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) na documentação do Windows.  

- **Bloquear a prevenção de execução de dados**  
  Desabilitar a prevenção de execução de dados pode permitir que determinados aplicativos de plug-in herdados funcionem sem encerrar o Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Padrão**: Desativado  
   
- **Bloquear terminação de heap ao corromper**  
  Desabilitar a terminação de heap na corrupção pode permitir que determinados aplicativos de plug-in herdados funcionem sem encerrar o Explorer imediatamente, embora o Explorer ainda possa ser encerrado inesperadamente mais tarde.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Padrão**: Desativado  
    

## <a name="internet-explorer"></a>Internet Explorer  
Para obter mais informações, consulte [CSP da política-InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) na documentação do Windows.  

- **Atualizações de zona restritas do Internet Explorer para a barra de status por meio de script**  
  Essa configuração de política permite que você gerencie se o script tem permissão para atualizar a barra de status dentro da zona. 
  - *Se você habilitar essa configuração de política*, o script poderá atualizar a barra de status.
  - *Se você desabilitar ou não definir essa configuração de política*, o script não poderá atualizar a barra de status.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Padrão**: Desativado

- **Arrastar e soltar na zona Internet do Internet Explorer ou copiar e colar arquivos**  
  Essa configuração de política permite que você gerencie se os usuários podem arrastar arquivos ou copiar e colar arquivos de uma fonte dentro da zona. Se você habilitar essa configuração de política, os usuários poderão arrastar arquivos ou copiar e colar arquivos dessa zona automaticamente. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja arrastar ou copiar arquivos dessa zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de arrastar arquivos ou copiar e colar arquivos dessa zona. Se você não definir essa configuração de política, os usuários poderão arrastar arquivos ou copiar e colar arquivos dessa zona automaticamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Padrão**: Desativar

- **Componentes dependentes .NET Framework zona restrita do Internet Explorer**    
  Essa configuração de política permite que você gerencie se .NET Framework componentes que não estão assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados sem assinatura. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados não assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados sem assinatura. Se você não definir essa configuração de política, o Internet Explorer não executará componentes gerenciados sem assinatura.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Padrão**: Desativar


- **A zona do computador local do Internet Explorer não executa antimalware em controles ativos X**  
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Padrão**: Desativado

- **Acesso à zona da Internet do Internet Explorer a fontes de dados**  
  Essa configuração de política permite que você gerencie se o Internet Explorer pode acessar dados de outra zona de segurança usando o Microsoft XML Parser (MSXML) ou o ActiveX Data Objects (ADO). Se você habilitar essa configuração de política, os usuários poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que uma página seja carregada na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você desabilitar essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você não definir essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Padrão**: Desativar  
  
- **Conteúdo de arrastar zona restrita do Internet Explorer de diferentes domínios no Windows**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários não podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa configuração de política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários não podem alterar essa configuração na caixa de diálogo Opções da Internet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Padrão**: Desativado
  
- **Aviso de incompatibilidade de endereço de certificado do Internet Explorer**  
  Essa configuração de política permite ativar o aviso de segurança de incompatibilidade de endereço de certificado. Quando essa configuração de política está ativada, o usuário é avisado ao visitar sites HTTP seguros (HTTPS) que apresentam certificados emitidos para um endereço de site diferente. Esse aviso ajuda a evitar ataques de falsificação. Se você habilitar essa configuração de política, o aviso de incompatibilidade de endereço de certificado sempre aparecerá. Se você desabilitar ou não definir essa configuração de política, o usuário poderá escolher se o aviso de incompatibilidade de endereço de certificado aparecerá (usando a página avançado no painel de controle da Internet).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Padrão**: Enabled 
  
- **Sites com menos privilégios de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se sites de zonas com menos privilégios, como sites da Internet, podem navegar nessa zona. Se você habilitar essa configuração de política, os sites de zonas com menos privilégios poderão abrir novas janelas no ou navegar até essa zona. A zona de segurança será executada sem a camada adicional de segurança fornecida pelo recurso de segurança proteção contra elevação de zona. Se você selecionar prompt na caixa suspensa, um aviso será emitido para o usuário que a navegação potencialmente arriscada está prestes a ocorrer. Se você desabilitar essa configuração de política, a navegação possivelmente prejudicial será impedida. O recurso de segurança do Internet Explorer está ativado nessa zona como definido pelo controle de recurso de elevação de zona. Se você não definir essa configuração de política, as navegações possivelmente prejudiciais serão impedidas. O recurso de segurança do Internet Explorer está ativado nessa zona como definido pelo controle de recurso de elevação de zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Padrão**: Desativar  
  
- **Prompt automático de zona restrita do Internet Explorer para downloads de arquivo**  
  Essa configuração de política determina se os usuários são solicitados a fornecer downloads de arquivos não iniciados pelo usuário. Independentemente dessa configuração, os usuários receberão caixas de diálogo de download de arquivo para downloads iniciados pelo usuário. Se você habilitar essa configuração, os usuários receberão uma caixa de diálogo de download de arquivo para tentativas de download automática. Se você desabilitar ou não definir essa configuração, os downloads de arquivos que não forem iniciados pelo usuário serão bloqueados e os usuários verão a barra de notificação, em vez da caixa de diálogo de download de arquivo. Os usuários podem clicar na barra de notificação para permitir o prompt de download de arquivo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Padrão**: Desativado
  
- **Componentes dependentes da Internet Internet Explorer .NET Framework**  
  Essa configuração de política permite que você gerencie se .NET Framework componentes que não estão assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados sem assinatura. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados não assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados sem assinatura. Se você não definir essa configuração de política, o Internet Explorer executará componentes gerenciados sem assinatura.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Padrão**: Desativar 
  
- **Zona Internet do Internet Explorer permite que somente domínios aprovados usem controles ActiveX TDC**  
  Essa configuração de política controla se o usuário pode executar o controle ActiveX TDC nos sites. Se você habilitar essa configuração de política, o controle ActiveX TDC não será executado de sites nesta zona. Se você desabilitar essa configuração de política, o controle ativo X TDC será executado de todos os sites nesta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Padrão**: Enabled 
  
- **Windows iniciado pelo script de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie restrições em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status. Se você habilitar essa configuração de política, a segurança das restrições do Windows não será aplicada nessa zona. A zona de segurança é executada sem a camada adicional de segurança fornecida por esse recurso. Se você desabilitar essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo. Se você não definir essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluam as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Padrão**: Desativado 
  
- **Zona Internet do Internet Explorer incluir caminho local ao carregar arquivos no servidor**  
  Essa configuração de política controla se as informações de caminho local são enviadas quando o usuário está carregando um arquivo por meio de um formulário HTML. Se as informações de caminho local forem enviadas, algumas informações poderão ser reveladas acidentalmente ao servidor. Por exemplo, os arquivos enviados da área de trabalho do usuário podem conter o nome de usuário como parte do caminho. Se você habilitar essa configuração de política, as informações de caminho serão enviadas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você desabilitar essa configuração de política, as informações de caminho serão removidas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você não definir essa configuração de política, o usuário poderá escolher se as informações de caminho são enviadas quando carregam um arquivo por meio de um formulário HTML. Por padrão, as informações de caminho são enviadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Padrão**: Desativado 
  
- **O Internet Explorer desabilita processos no modo protegido avançado**  
  Essa configuração de política determina se o Internet Explorer 11 usa processos de 64 bits (para maior segurança) ou processos de 32 bits (para maior compatibilidade) durante a execução em modo protegido aprimorado nas versões de 64 bits do Windows. Importante: Alguns controles ActiveX e barras de ferramentas podem não estar disponíveis quando são usados processos de 64 bits. Se você habilitar essa configuração de política, o Internet Explorer 11 usará os processos de guia de 64 bits ao executar no modo protegido aprimorado nas versões de 64 bits do Windows. Se você desabilitar essa configuração de política, o Internet Explorer 11 usará os processos de guia de 32 bits ao executar no modo protegido aprimorado nas versões de 64 bits do Windows. Se você não definir essa configuração de política, os usuários poderão ativar ou desativar esse recurso usando as configurações do Internet Explorer. Esse recurso está desativado por padrão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Padrão**: Enabled 
  
- **Ignorar erros de certificado do Internet Explorer**  
  Essa configuração de política impede que o usuário ignore erros de certificado de protocolo SSL/TLS (segurança de camada de transporte) que interrompem a navegação (como erros "expirados", "revogados" ou "incompatibilidade de nome") no Internet Explorer. Se você habilitar essa configuração de política, o usuário não poderá continuar a navegação. Se você desabilitar ou não definir essa configuração de política, o usuário poderá optar por ignorar os erros de certificado e continuar a navegação.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Padrão**: Desativado 
  
- **Carregamento de zona da Internet do Internet Explorer de arquivos XAML**  
  Essa configuração de política permite que você gerencie o carregamento de arquivos de Extensible Application Markup Language (XAML). O XAML é uma linguagem de marcação declarativa baseada em XML comumente usada para criar interfaces de usuário avançadas e gráficos que aproveitam o Windows Presentation Foundation. Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, os arquivos XAML serão carregados automaticamente no Internet Explorer. O usuário não pode alterar esse comportamento. Se você definir a caixa suspensa como prompt, o usuário será solicitado a carregar arquivos XAML. Se você desabilitar essa configuração de política, os arquivos XAML não serão carregados no Internet Explorer. O usuário não pode alterar esse comportamento. Se você não definir essa configuração de política, o usuário poderá decidir se deseja carregar arquivos XAML dentro do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Padrão**: Desativar 
  
- **Prompt automático da zona Internet do Internet Explorer para downloads de arquivos**  
  Essa configuração de política determina se os usuários são solicitados a fornecer downloads de arquivos não iniciados pelo usuário. Independentemente dessa configuração, os usuários receberão caixas de diálogo de download de arquivo para downloads iniciados pelo usuário. Se você habilitar essa configuração, os usuários receberão uma caixa de diálogo de download de arquivo para tentativas de download automática. Se você desabilitar ou não definir essa configuração, os downloads de arquivos que não forem iniciados pelo usuário serão bloqueados e os usuários verão a barra de notificação, em vez da caixa de diálogo de download de arquivo. Os usuários podem clicar na barra de notificação para permitir o prompt de download de arquivo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Padrão**: Desativado  
  
- **Aviso de segurança de zona restrita do Internet Explorer para arquivos potencialmente não seguros**  
  Essa configuração de política controla se a mensagem de "aviso de segurança de arquivo aberto" aparece quando o usuário tenta abrir arquivos executáveis ou outros arquivos potencialmente não seguros (de um compartilhamento de arquivos de intranet usando o explorador de arquivos, por exemplo). Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, esses arquivos abrirão sem um aviso de segurança. Se você definir a caixa suspensa como avisar, um aviso de segurança será exibido antes da abertura dos arquivos. Se você desabilitar essa configuração de política, esses arquivos não abrirão. Se você não definir essa configuração de política, o usuário poderá configurar como o computador lida com esses arquivos. Por padrão, esses arquivos são bloqueados na zona restrita, habilitados nas zonas da intranet e do computador local e definidos como prompt na Internet e nas zonas confiáveis.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Padrão**: Desativar  
  
- **Filtro de script entre sites da zona Internet do Internet Explorer**  
  Essa política controla se o filtro XSS (script entre sites) detectará e impedirá injeçãos de script entre sites em sites nessa zona. Se você habilitar essa configuração de política, o filtro XSS será ativado para sites nessa zona e o filtro XSS tentará bloquear as injeções de script entre sites. Se você desabilitar essa configuração de política, o filtro XSS será desativado para sites nesta zona e o Internet Explorer permitirá injeçãos de script entre sites.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Padrão**: Enabled 
  
- **Fallback do Internet Explorer para SSL3**  
  Essa configuração de política permite bloquear um fallback inseguro para SSL 3,0. Quando essa política estiver habilitada, o Internet Explorer tentará se conectar a sites usando SSL 3,0 ou inferior quando o TLS 1,0 ou superior falhar. Recomendamos que você não permita o fallback inseguro para evitar um ataque man-in-the-Middle. Essa política não afeta quais protocolos de segurança estão habilitados. Se você desabilitar essa política, os padrões do sistema serão usados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Padrão**: Nenhum site  

- **Suporte à criptografia do Internet Explorer**  
  Essa configuração de política permite que você desative o suporte para TLS (Transport Layer Security) 1,0, TLS 1,1, TLS 1,2, protocolo SSL (SSL) 2,0 ou SSL 3,0 no navegador. TLS e SSL são protocolos que ajudam a proteger a comunicação entre o navegador e o servidor de destino. Quando o navegador tenta configurar uma comunicação protegida com o servidor de destino, o navegador e o servidor negociam qual protocolo e versão usar. O navegador e o servidor tentam corresponder à lista de protocolos e versões com suporte, e selecionam a correspondência mais preferencial. Se você habilitar essa configuração de política, o navegador negociará ou não negociará um túnel de criptografia usando os métodos de criptografia que você selecionar na lista suspensa. Se você desabilitar ou não definir essa configuração de política, o usuário poderá selecionar o método de criptografia ao qual o navegador dá suporte.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Padrão**: 2 itens:  TLS v 1.1 e TLS v 1.2  
  *Selecione a seta para baixo para exibir as opções que você pode selecionar para essa configuração.*
  
- **Tela inteligente da zona da Internet bloqueada do Internet Explorer**  
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Padrão**: Enabled 
  
- **Aplicativos e arquivos de inicialização de zona restrita do Internet Explorer em um iFrame**  
  Essa configuração de política permite que você gerencie se os aplicativos podem ser executados e se os arquivos podem ser baixados de uma referência de IFRAME no HTML das páginas desta zona. Se você habilitar essa configuração de política, os usuários poderão executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de executar aplicativos e baixar arquivos de IFRAMEs nas páginas dessa zona. Se você não definir essa configuração de política, os usuários serão impedidos de executar aplicativos e baixar arquivos de IFRAMEs nas páginas dessa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Padrão**: Desativar 
  
- **O Internet Explorer ignora avisos de tela inteligente sobre arquivos incomuns**  
  Essa configuração de política determina se o usuário pode ignorar avisos do filtro do SmartScreen. O filtro do SmartScreen avisa o usuário sobre arquivos executáveis que os usuários do Internet Explorer geralmente não baixam da Internet. Se você habilitar essa configuração de política, os avisos do filtro do SmartScreen bloquearão o usuário. Se você desabilitar ou não definir essa configuração de política, o usuário poderá ignorar os avisos do filtro do SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Padrão**: Desativado  
  
- **Bloqueador de pop-ups de zona da Internet do Internet Explorer**  
  Essa configuração de política permite que você gerencie se janelas pop-up indesejadas são exibidas. Janelas pop-up que são abertas quando o usuário final clica em um link não são bloqueadas. Se você habilitar essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida. Se você desabilitar essa configuração de política, as janelas pop-up não serão impedidas de serem exibidas. Se você não definir essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa a manipulação de MIME consistente**  
  O Internet Explorer contém comportamentos binários dinâmicos: componentes que encapsulam funcionalidades específicas para os elementos HTML aos quais eles estão anexados. Essa configuração de política controla se a configuração de restrição de segurança de comportamento binário é impedida ou permitida. Se você habilitar essa configuração de política, os comportamentos binários serão impedidos para os processos do explorador de arquivos e do Internet Explorer. Se você desabilitar essa configuração de política, comportamentos binários serão permitidos para os processos do explorador de arquivos e do Internet Explorer. Se você não definir essa configuração de política, os comportamentos binários serão impedidos para os processos do explorador de arquivos e do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Padrão**: Enabled  
  
- **Permissões Java da zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Padrão**: Desabilitar Java  
    
  
- **Controles do Internet Explorer Active X no modo protegido**  
  Essa configuração de política impede que os controles ActiveX sejam executados no modo protegido quando o modo protegido aprimorado está habilitado. Quando um usuário tem um controle ActiveX instalado que não é compatível com o modo protegido aprimorado e um site tenta carregar o controle, o Internet Explorer notifica o usuário e dá a opção de executar o site no modo protegido normal. Essa configuração de política desabilita essa notificação e força todos os sites a serem executados no modo protegido avançado. O modo protegido avançado fornece proteção adicional contra sites mal-intencionados usando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam pelo menos o Windows 8, o modo protegido aprimorado também limita os locais em que o Internet Explorer pode ler no registro e no sistema de arquivos. Quando o modo protegido aprimorado é habilitado e um usuário entra em um site que tenta carregar um controle ActiveX que não é compatível com o modo protegido avançado, o Internet Explorer notifica o usuário e dá a opção de desabilitar o modo protegido avançado para Esse site específico. Se você habilitar essa configuração de política, o Internet Explorer não dará ao usuário a opção de desabilitar o modo protegido avançado. Todos os sites do modo protegido serão executados no modo protegido avançado. Se você desabilitar ou não definir essa configuração de política, o Internet Explorer notificará os usuários e fornecerá uma opção para executar sites com controles ActiveX incompatíveis no modo protegido normal.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Padrão**: Desativado  
  
- **Carregamento de zona restrita do Internet Explorer de arquivos XAML**  
  Essa configuração de política permite que você gerencie o carregamento de arquivos de Extensible Application Markup Language (XAML). O XAML é uma linguagem de marcação declarativa baseada em XML comumente usada para criar interfaces de usuário avançadas e gráficos que aproveitam o Windows Presentation Foundation. Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, os arquivos XAML serão carregados automaticamente no Internet Explorer. O usuário não pode alterar esse comportamento. Se você definir a caixa suspensa como prompt, o usuário será solicitado a carregar arquivos XAML. Se você desabilitar essa configuração de política, os arquivos XAML não serão carregados no Internet Explorer. O usuário não pode alterar esse comportamento. Se você não definir essa configuração de política, o usuário poderá decidir se deseja carregar arquivos XAML dentro do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Padrão**: Desativar  
  
- **O Internet Explorer processa restrições de segurança de janela com script**  
  O Internet Explorer permite que os scripts abram, redimensionem e reposicionem as janelas de vários tipos programaticamente. O recurso de segurança restrições de janela restringe as janelas pop-up e proíbe que os scripts exibam janelas nas quais as barras de título e status não são visíveis para o usuário ou ofuscam outras barras de título e status do Windows. Se você habilitar essa configuração de política, as janelas com script serão restringidas para todos os processos. Se você desabilitar ou não definir essa configuração de política, as janelas com script não serão restringidas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Padrão**: Enabled   
  
- **A zona restrita do Internet Explorer executa controles e plugins do Active X**  
  Essa configuração de política permite que você gerencie se os controles ActiveX e plug-ins podem ser executados em páginas da zona especificada. Se você habilitar essa configuração de política, os controles e plug-ins poderão ser executados sem a intervenção do usuário. Se você selecionou prompt na caixa suspensa, os usuários serão solicitados a escolher se deseja permitir que os controles ou o plug-in sejam executados. Se você desabilitar essa configuração de política, os controles e plug-ins serão impedidos de serem executados. Se você não definir essa configuração de política, os controles e plug-ins serão impedidos de serem executados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Padrão**: Desativar  
  
- **Controles Active X do script de zona restrita do Internet Explorer marcados como seguros para scripts**  
  Essa configuração de política permite que você gerencie se um controle ActiveX marcado como seguro para scripts pode interagir com um script. Se você habilitar essa configuração de política, a interação do script poderá ocorrer automaticamente sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir a interação do script. Se você desabilitar essa configuração de política, a interação do script será impedida de ocorrer. Se você não definir essa configuração de política, a interação do script será impedida de ocorrer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Padrão**: Desativar  
  
- **Opções de logon de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie configurações para opções de entrada. Se você habilitar essa configuração de política, poderá escolher entre as seguintes opções de entrada. 
  - *Anônimo* -use a entrada anônima para desabilitar a autenticação http e usar a conta de convidado somente para o protocolo CIFS (Common Internet File System). 
  - *Prompt* -use solicitar nome de usuário e senha para consultar usuários de IDs de usuário e senhas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. 
  - *Entrada automática somente na zona da intranet* – Use esta opção para consultar usuários de IDs de usuário e senhas em outras zonas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. 
  - *Entrar automaticamente com nome de usuário e senha atuais*-Use esta opção para tentar entrar usando a resposta de desafio do Windows NT (também conhecida como autenticação NTLM). Se o servidor oferecer suporte à resposta de desafio do Windows NT, a entrada usará o nome de usuário e a senha de rede do usuário para entrar. Se o servidor não oferecer suporte à resposta de desafio do Windows NT, o usuário será consultado para fornecer o nome de usuário e a senha. 

  Se você desabilitar essa configuração de política, a entrada será definida como *logon automático somente na zona da intranet*. Se você não definir essa configuração de política, a entrada será definida para *solicitar* o nome de usuário e a senha.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Padrão**: Anónima  
  
- **Os controles de inicialização de zona confiável do Internet Explorer e script ativo X não estão marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Padrão**: Desativar  
  
- **Verificação de revogação de certificado do servidor do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o Internet Explorer verificará o status de revogação dos certificados dos servidores. Os certificados são revogados quando são comprometidos ou não são mais válidos, e essa opção protege os usuários do envio de dados confidenciais para um site que pode ser fraudulento ou não seguro. Se você habilitar essa configuração de política, o Internet Explorer verificará se os certificados de servidor foram revogados. Se você desabilitar essa configuração de política, o Internet Explorer não verificará os certificados do servidor para ver se eles foram revogados. Se você não definir essa configuração de política, o Internet Explorer não verificará os certificados do servidor para ver se eles foram revogados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Padrão**: Enabled 
  
- **Sites com menos privilégios do Internet Explorer Internet Zone**  
  Essa configuração de política permite que você gerencie se sites de zonas com menos privilégios, como sites restritos, podem navegar para essa zona. Se você habilitar essa configuração de política, os sites de zonas com menos privilégios poderão abrir novas janelas no ou navegar até essa zona. A zona de segurança será executada sem a camada adicional de segurança fornecida pelo recurso de segurança proteção contra elevação de zona. Se você selecionar prompt na caixa suspensa, um aviso será emitido para o usuário que a navegação potencialmente arriscada está prestes a ocorrer. Se você desabilitar essa configuração de política, as navegações possivelmente prejudiciais serão impedidas. O recurso de segurança do Internet Explorer está ativado nessa zona como definido pelo controle de recurso de elevação de zona. Se você não definir essa configuração de política, os sites de zonas com menos privilégios poderão abrir novas janelas no ou navegar até essa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Padrão**: Desativar  
  
- **Downloads de arquivos de zona restritas do Internet Explorer**  
  Essa configuração de política permite que você gerencie se os downloads de arquivo são permitidos da zona. Essa opção é determinada pela zona da página com o link que está causando o download, não a zona da qual o arquivo é entregue. Se você habilitar essa configuração de política, os arquivos poderão ser baixados da zona. Se você desabilitar essa configuração de política, os arquivos serão impedidos de serem baixados da zona. Se você não definir essa configuração de política, os arquivos serão impedidos de serem baixados da zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Padrão**: Desativar  
  
- **Internet Explorer execução de Internet .NET Framework componentes dependentes assinados com Authenticode**  
  Essa configuração de política permite que você gerencie se .NET Framework componentes assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados assinados. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados. Se você não definir essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Padrão**: Desativar  
  
- **O Internet Explorer impede a instalação por usuário de controles do Active X**  
  Essa configuração de política permite que você impeça a instalação de controles ActiveX por usuário. Se você habilitar essa configuração de política, os controles ActiveX não poderão ser instalados por usuário. Se você desabilitar ou não definir essa configuração de política, os controles ActiveX poderão ser instalados por usuário.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Padrão**: Enabled  
  
- **Filtro de impedimento de gerenciamento de tela inteligente do Internet Explorer**  
  Essa configuração de política impede que o usuário gerencie o Filtro SmartScreen, que avisa o usuário se o site que ele visita é conhecido por tentativas fraudulentas de coletar informações pessoais por meio de "phishing" ou é conhecido por hospedar malware. Se você habilitar essa configuração de política, o usuário não será solicitado a ativar o filtro do SmartScreen. Todos os endereços de sites que não estão na lista de permissões de filtros são enviados automaticamente à Microsoft sem avisar o usuário. Se você desabilitar ou não definir essa configuração de política, o usuário receberá uma solicitação para decidir se deseja ativar o filtro do SmartScreen durante a experiência da primeira execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa o recurso de segurança de detecção de MIME**  
  Essa configuração de política determina se a detecção de MIME do Internet Explorer impedirá a promoção de um arquivo de um tipo para um tipo de arquivo mais perigoso. Se você habilitar essa configuração de política, a detecção de MIME nunca promoverá um arquivo de um tipo para um tipo de arquivo mais perigoso. Se você desabilitar essa configuração de política, os processos do Internet Explorer permitirão que uma detecção de MIME promova um arquivo de um tipo para um tipo de arquivo mais perigoso. Se você não definir essa configuração de política, a detecção de MIME nunca promoverá um arquivo de um tipo para um tipo de arquivo mais perigoso.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Padrão**: Enabled  
  
- **Controles ActiveX assinados do download de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX assinados de uma página na zona. Se você habilitar essa política, os usuários poderão baixar controles assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente. Se você desabilitar a configuração de política, os controles assinados não poderão ser baixados. Se você não definir essa configuração de política, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Padrão**: Desativar  
  
- **Preenchimento automático do Internet Explorer**  
  Esse recurso de preenchimento automático pode se lembrar e sugerir nomes de usuário e senhas em formulários. Se você habilitar essa configuração, o usuário não poderá alterar "nome de usuário e senhas em formulários" ou "avisar para salvar senhas". O recurso de preenchimento automático para nomes de usuário e senhas em formulários é ativado. Você precisa decidir se deseja selecionar "avisar para salvar senhas". Se você desabilitar essa configuração, o usuário não poderá alterar "nome de usuário e senhas em formulários" ou "avisar para salvar senhas". O recurso de preenchimento automático para nomes de usuário e senhas em formulários é desativado. O usuário também não pode optar por ser solicitado a salvar senhas. Se você não definir essa configuração, o usuário terá a liberdade de ativar o preenchimento automático para nome de usuário e senhas em formulários e a opção de solicitar o salvamento de senhas. Para exibir essa opção, os usuários abrem a caixa de diálogo Opções da Internet, clicam na guia conteúdo e clicam no botão Configurações.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Padrão**: Desativado  
  
- **Internet Explorer permitir que o VBscript seja executado**  
  Essa configuração de política permite que você decida se o VBScript pode ser executado em páginas em zonas específicas do Internet Explorer. As opções incluem: 
  - *Enable* -VBScript é executado em páginas em zonas específicas, sem qualquer interação. 
  - *Prompt* -os funcionários são solicitados a permitir que o VBScript seja executado na zona. 
  - *Disable* -o VBScript é impedido de ser executado na zona. Se você desabilitar ou não definir essa configuração de política, o VBScript será executado sem nenhuma interação na zona especificada.    

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Padrão**: Desativar  
  
- **Zona restrita do Internet Explorer permitir que somente domínios aprovados usem controles do ativo X TDC**  
  Essa configuração de política controla se o usuário pode executar o controle ActiveX TDC nos sites. Se você habilitar essa configuração de política, o controle ActiveX TDC não será executado de sites nesta zona. Se você desabilitar essa configuração de política, o controle ativo X TDC será executado de todos os sites nesta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Padrão**: Enabled  
  
- **A zona confiável do Internet Explorer não executa antimalware em controles do Active X**  
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Padrão**: Desativado 
  
- **Permissões Java da zona do computador local do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como segurança média.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Padrão**: Desabilitar Java 
  
- **A zona da intranet do Internet Explorer não executa antimalware em controles do Active X**  
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Padrão**: Desativado  

- **Zona de permissão scriptlets do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o usuário pode executar scriptlets. Se você habilitar essa configuração de política, o usuário poderá executar scriptlets. Se você desabilitar essa configuração de política, o usuário não poderá executar o scriptlets. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o scriptlets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Padrão**: Desativado  
  
- **Barra de notificação de processos do Internet Explorer**  
  Essa configuração de política permite que você gerencie se a barra de notificação é exibida para processos do Internet Explorer quando instalações de arquivo ou código são restritas. Por padrão, a barra de notificação é exibida para processos do Internet Explorer. Se você habilitar essa configuração de política, a barra de notificação será exibida para os processos do Internet Explorer. Se você desabilitar essa configuração de política, a barra de notificação não será exibida para processos do Internet Explorer. Se você não definir essa configuração de política, a barra de notificação não será exibida para processos do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Padrão**: Enabled  
  
- **Controles ActiveX assinados do download de Internet Zone Internet Explorer**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX assinados de uma página na zona. Se você habilitar essa política, os usuários poderão baixar controles assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente. Se você desabilitar a configuração de política, os controles assinados não poderão ser baixados. Se você não definir essa configuração de política, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Padrão**: Desativar  
  
- **Tela inteligente da zona restrita do Internet Explorer**  
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Padrão**: Enabled  
  
- **Botão Remover executar este tempo do Internet Explorer para controles ativos X desatualizados**  
  Essa configuração de política permite impedir que os usuários vejam o botão "executar desta vez" e executem controles ActiveX desatualizados específicos no Internet Explorer. Se você habilitar essa configuração de política, os usuários não verão o botão "executar desta vez" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Se você desabilitar ou não definir essa configuração de política, os usuários verão o botão "executar desta vez" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Clicar nesse botão permite que o usuário execute o controle ActiveX desatualizado uma vez. Para obter mais informações, consulte "controles ActiveX desatualizados" na biblioteca do TechNet do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Padrão**: Enabled 
  
- **Inicialização de aplicativos e arquivos de Internet do Internet Explorer em um iframe**  
  Essa configuração de política permite que você gerencie se os aplicativos podem ser executados e se os arquivos podem ser baixados de uma referência de IFRAME no HTML das páginas desta zona. Se você habilitar essa configuração de política, os usuários poderão executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de executar aplicativos e baixar arquivos de IFRAMEs nas páginas dessa zona. Se você não definir essa configuração de política, os usuários serão consultados para escolher se deseja executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Padrão**: Desativar 
  
- **Zona restrita do Internet Explorer navegue por janelas e quadros entre domínios diferentes**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Padrão**: Desativar  
  
- **Tela inteligente da Internet do Internet Explorer**  
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Padrão**: Enabled  
  
- **O Internet Explorer bloqueou as permissões de Java da zona confiável**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Padrão**: Desabilitar Java 
  
- **O Internet Explorer verifica as assinaturas nos programas baixados**  
  Essa configuração de política permite que você gerencie se o Internet Explorer verifica assinaturas digitais (que identifica o editor de software assinado e verifica se ele não foi modificado ou adulterado) em computadores de usuários antes de baixar programas executáveis. Se você habilitar essa configuração de política, o Internet Explorer verificará as assinaturas digitais de programas executáveis e exibirá suas identidades antes de baixá-los para os computadores dos usuários. Se você desabilitar essa configuração de política, o Internet Explorer não verificará as assinaturas digitais de programas executáveis nem exibirá suas identidades antes de baixá-los nos computadores dos usuários. Se você não configurar essa política, o Internet Explorer não verificará as assinaturas digitais de programas executáveis nem exibirá suas identidades antes de baixá-los nos computadores dos usuários.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Padrão**: Enabled  
  
- **Script de zona restrita do Internet Explorer de controles de navegador da Web**  
  Essa configuração de política determina se uma página pode controlar controles WebBrowser inseridos por meio de script. Se você habilitar essa configuração de política, o acesso de script ao controle WebBrowser será permitido. Se você desabilitar essa configuração de política, o acesso de script ao controle WebBrowser não será permitido. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o acesso de script ao controle WebBrowser. Por padrão, o acesso de script ao controle WebBrowser é permitido apenas no computador local e nas zonas da intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Padrão**: Desativado  
  
- **Filtro de script entre sites de zona restrita do Internet Explorer**  
  Essa política controla se o filtro XSS (script entre sites) detectará e impedirá injeçãos de script entre sites em sites nessa zona. Se você habilitar essa configuração de política, o filtro XSS será ativado para sites nessa zona e o filtro XSS tentará bloquear as injeções de script entre sites. Se você desabilitar essa configuração de política, o filtro XSS será desativado para sites nesta zona e o Internet Explorer permitirá injeçãos de script entre sites.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Padrão**: Enabled  
  
- **Comportamentos de script e binários de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie comportamentos binários e de script dinâmicos: componentes que encapsulam funcionalidades específicas para elementos HTML aos quais eles foram anexados. Se você habilitar essa configuração de política, os comportamentos binários e de script estarão disponíveis. Se você selecionar administrador aprovado na caixa suspensa, somente os comportamentos listados nos comportamentos aprovados pelo administrador sob a política de restrição de segurança de comportamentos binários estarão disponíveis. Se você desabilitar essa configuração de política, os comportamentos binários e de script não estarão disponíveis, a menos que os aplicativos tenham implementado um Gerenciador de segurança personalizado. Se você não definir essa configuração de política, os comportamentos binários e de script não estarão disponíveis, a menos que os aplicativos tenham implementado um Gerenciador de segurança personalizado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Padrão**: Desativar  
  
- **Verificação de configurações de segurança do Internet Explorer**  
  Essa configuração de política desativa o recurso de verificação de configurações de segurança, que verifica as configurações de segurança do Internet Explorer para determinar quando as configurações colocam o Internet Explorer em risco. Se você habilitar essa configuração de política, o recurso será desativado. Se você desabilitar ou não definir essa configuração de política, o recurso será ativado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Padrão**: Enabled  
  
- **Aviso de segurança de zona da Internet do Internet Explorer para arquivos potencialmente não seguros**  
  Essa configuração de política controla se a mensagem de "aviso de segurança de arquivo aberto" aparece quando o usuário tenta abrir arquivos executáveis ou outros arquivos potencialmente não seguros (de um compartilhamento de arquivos de intranet usando o explorador de arquivos, por exemplo). Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, esses arquivos abrirão sem um aviso de segurança. Se você definir a caixa suspensa como avisar, um aviso de segurança será exibido antes da abertura dos arquivos. Se você desabilitar essa configuração de política, esses arquivos não abrirão. Se você não definir essa configuração de política, o usuário poderá configurar como o computador lida com esses arquivos. Por padrão, esses arquivos são bloqueados na zona restrita, habilitados nas zonas da intranet e do computador local e definidos como prompt na Internet e nas zonas confiáveis.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Padrão**: Mensagem  
  
- **Permissões Java da zona Intranet do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como segurança média.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Padrão**: Alta segurança 
  
- **Bloqueio do Internet Explorer/controles ativos X desatualizados**   
  Essa configuração de política determina se o Internet Explorer bloqueia controles ActiveX desatualizados específicos. Controles ActiveX desatualizados nunca são bloqueados na zona da intranet. Se você habilitar essa configuração de política, o Internet Explorer parará de bloquear controles ActiveX desatualizados. Se você desabilitar ou não definir essa configuração de política, o Internet Explorer continuará a bloquear controles ActiveX desatualizados específicos. Para obter mais informações, consulte "controles ActiveX desatualizados" na biblioteca do TechNet do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Padrão**: Enabled  
  
- **Bloqueador de pop-ups de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se janelas pop-up indesejadas são exibidas. Janelas pop-up que são abertas quando o usuário final clica em um link não são bloqueadas. Se você habilitar essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida. Se você desabilitar essa configuração de política, as janelas pop-up não serão impedidas de serem exibidas. Se você não definir essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa a restrição de segurança de protocolo MK**  
  A configuração de política de restrição de segurança de protocolo MK reduz a área da superfície de ataque, impedindo o protocolo MK. Os recursos hospedados no protocolo MK falharão. Se você habilitar essa configuração de política, o protocolo MK será impedido para o explorador de arquivos e o Internet Explorer, e os recursos hospedados no protocolo MK falharão. Se você desabilitar essa configuração de política, os aplicativos poderão usar a API de protocolo MK. Os recursos hospedados no protocolo MK funcionarão para os processos do explorador de arquivos e do Internet Explorer. Se você não definir essa configuração de política, o protocolo MK será impedido para o explorador de arquivos e o Internet Explorer, e os recursos hospedados no protocolo MK falharão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Padrão**: Enabled  
  
- **Permissões Java de zona confiável do Internet Explorer**   
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como segurança baixa.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Padrão**: Alta segurança  
  
- **Script de zona restrita do Internet Explorer de miniaplicativos Java**  
  Essa configuração de política permite que você gerencie se os applets são expostos aos scripts dentro da zona. Se você habilitar essa configuração de política, os scripts poderão acessar miniaplicativos automaticamente sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que os scripts acessem os applets. Se você desabilitar essa configuração de política, os scripts serão impedidos de acessar miniaplicativos. Se você não definir essa configuração de política, os scripts serão impedidos de acessar miniaplicativos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Padrão**: Desativar  
  
- **O Internet Explorer bloqueou as permissões de Java da zona restrita**   
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Padrão**: Desabilitar Java 
  
- **Zona Internet do Internet Explorer permitir somente domínios aprovados para usar controles ActiveX**   
  Essa configuração de política controla se o usuário é solicitado a permitir que os controles ActiveX sejam executados em sites que não sejam o site que instalou o controle ActiveX. Se você habilitar essa configuração de política, o usuário será solicitado antes que os controles ActiveX possam ser executados de sites nesta zona. O usuário pode optar por permitir que o controle seja executado a partir do site atual ou de todos os sites. Se você desabilitar essa configuração de política, o usuário não verá o prompt do ActiveX por site e os controles ActiveX poderão ser executados de todos os sites nesta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Padrão**: Enabled  
  
- **O Internet Explorer inclui todos os caminhos de rede**  
  O Internet Explorer inclui todos os caminhos de rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Padrão**: Desativado 
  
- **Modo protegido de zona Internet Explorer**  
  Essa configuração de política permite ativar o modo protegido. O modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo os locais em que o Internet Explorer pode gravar no registro e no sistema de arquivos. Se você habilitar essa configuração de política, o modo protegido será ativado. O usuário não pode desativar o modo protegido. Se você desabilitar essa configuração de política, o modo protegido será desativado. O usuário não pode ativar o modo protegido. Se você não definir essa configuração de política, o usuário poderá ativar ou desativar o modo protegido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Padrão**: Ativar 
  
- **Inicialização de zona da Internet do Internet Explorer e controles do script ativo X não marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Padrão**: Desativar 
  
- **Tela inteligente da zona restrita bloqueada do Internet Explorer**   
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Padrão**: Enabled  
  
- **Detecção de falhas do Internet Explorer**  
  Essa configuração de política permite que você gerencie o recurso de detecção de falhas do gerenciamento de Complementos. Se você habilitar essa configuração de política, uma falha no Internet Explorer exibirá o comportamento encontrado no Windows XP Professional Service Pack 1 e versões anteriores, para invocar Relatório de Erros do Windows. Todas as configurações de política para Relatório de Erros do Windows continuam a ser aplicadas. Se você desabilitar ou não definir essa configuração de política, o recurso de detecção de pane para o gerenciamento de Complementos será funcional.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Padrão**: Desativado  
  
- **Permissões Java da zona Internet do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como alta segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Padrão**: Desabilitar Java  
  
- **Script ativo de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o código de script em páginas na zona é executado. Se você habilitar essa configuração de política, o código de script em páginas na zona poderá ser executado automaticamente. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o código de script em páginas na zona seja executado. Se você desabilitar essa configuração de política, o código de script em páginas na zona será impedido de ser executado. Se você não definir essa configuração de política, o código de script em páginas na zona será impedido de ser executado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Padrão**: Desativar  
  
- **Opções de logon na Internet Zone do Internet Explorer**  
  Essa configuração de política permite que você gerencie configurações para opções de entrada. Se você habilitar essa configuração de política, poderá escolher entre as seguintes opções de entrada. Logon anônimo para desabilitar a autenticação HTTP e usar a conta de convidado somente para o protocolo CIFS (Common Internet File System). Solicite o nome de usuário e a senha para consultar os usuários de IDs de usuário e senhas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. Logon automático somente na zona da intranet para consultar os usuários de IDs de usuário e senhas em outras zonas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. Conexão automática com o nome de usuário e a senha atuais para tentar fazer logon usando a resposta de desafio do Windows NT (também conhecida como autenticação NTLM). Se o servidor oferecer suporte à resposta de desafio do Windows NT, a entrada usará o nome de usuário e a senha de rede do usuário para fazer logon. Se o servidor não oferecer suporte à resposta de desafio do Windows NT, o usuário será consultado para fornecer o nome de usuário e a senha. Se você desabilitar essa configuração de política, a opção entrar será definida como logon automático somente na zona da intranet. Se você não definir essa configuração de política, a opção entrar será definida como logon automático somente na zona da intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Padrão**: Mensagem  
  
- **Zona restrita do Internet Explorer permitir que o VBScript seja executado**   
  Essa configuração de política permite que você gerencie se o VBScript pode ser executado em páginas da zona especificada no Internet Explorer. Se você selecionou habilitar na caixa suspensa, o VBScript poderá ser executado sem intervenção do usuário. Se você selecionou prompt na caixa suspensa, os usuários serão solicitados a escolher se deseja permitir que o VBScript seja executado. Se você selecionou desabilitar na caixa suspensa, o VBScript será impedido de ser executado. Se você não definir ou desabilitar essa configuração de política, o VBScript será impedido de ser executado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Padrão**: Desativar  
  
- **Zona Internet do Internet Explorer arrastar conteúdo de diferentes domínios no Windows**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Padrão**: Desativado 
  
- **Inicialização de zona da intranet do Internet Explorer e controles do script ativo X não marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Padrão**: Desativar 
  
- **Compartimentos de download do Internet Explorer**  
  Essa configuração de política impede que o usuário tenha os compartimentos (anexos de arquivo) baixados de um feed para o computador do usuário. Se você habilitar essa configuração de política, o usuário não poderá definir o mecanismo de sincronização de feeds para baixar um compartimento por meio da página de propriedades do feed. Um desenvolvedor não pode alterar a configuração de download por meio das APIs de feed. Se você desabilitar ou não definir essa configuração de política, o usuário poderá definir o mecanismo de sincronização de feeds para baixar um compartimento por meio da página de propriedades do feed. Um desenvolvedor pode alterar a configuração de download por meio das APIs de feed.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Padrão**: Desativado  
  
- **Controle de zona restrita do Internet Explorer-baixar controles ActiveX não assinados**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando provenientes de uma zona não confiável. Se você habilitar essa configuração de política, os usuários poderão executar controles não assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o controle não assinado seja executado. Se você desabilitar essa configuração de política, os usuários não poderão executar controles não assinados. Se você não definir essa configuração de política, os usuários não poderão executar controles não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Padrão**: Desativar  
  
- **Zona Internet do Internet Explorer arrastar conteúdo de diferentes domínios no Windows**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando provenientes de uma zona não confiável. Se você habilitar essa configuração de política, os usuários poderão executar controles não assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o controle não assinado seja executado. Se você desabilitar essa configuração de política, os usuários não poderão executar controles não assinados. Se você não definir essa configuração de política, os usuários não poderão executar controles não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Padrão**: Desativado  
  
- **Os processos do Internet Explorer restringem a instalação do Active X**   
  Essa configuração de política permite que os aplicativos que hospedam o controle do navegador da Web bloqueiem a solicitação automática de instalação do controle ActiveX. Se você habilitar essa configuração de política, o controle do navegador da Web bloqueará a solicitação automática de instalação do controle ActiveX para todos os processos. Se você desabilitar ou não definir essa configuração de política, o controle do navegador da Web não bloqueará a solicitação automática de instalação do controle ActiveX para todos os processos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Padrão**: Enabled  
  
- **Área de Internet do Internet Explorer scriptlets**  
  Essa configuração de política permite que você gerencie se o usuário pode executar scriptlets. Se você habilitar essa configuração de política, o usuário poderá executar scriptlets. Se você desabilitar essa configuração de política, o usuário não poderá executar o scriptlets. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o scriptlets.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Padrão**: Desativar  
  
- **Arrastar e soltar zona restrita do Internet Explorer ou copiar e colar arquivos**  
  Essa configuração de política permite que você gerencie se os usuários podem arrastar arquivos ou copiar e colar arquivos de uma fonte dentro da zona. Se você habilitar essa configuração de política, os usuários poderão arrastar arquivos ou copiar e colar arquivos dessa zona automaticamente. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja arrastar ou copiar arquivos dessa zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de arrastar arquivos ou copiar e colar arquivos dessa zona. Se você não definir essa configuração de política, os usuários serão consultados para escolher se deseja arrastar ou copiar arquivos dessa zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Padrão**: Desativar  
  
- **Software do Internet Explorer quando a assinatura é inválida**  
  Essa configuração de política permite que você gerencie se o software, como controles ActiveX e downloads de arquivos, pode ser instalado ou executado pelo usuário, embora a assinatura seja inválida. Uma assinatura inválida pode indicar que alguém foi adulterado com o arquivo. Se você habilitar essa configuração de política, os usuários serão solicitados a instalar ou executar arquivos com uma assinatura inválida. Se você desabilitar essa configuração de política, os usuários não poderão executar ou instalar arquivos com uma assinatura inválida. Se você não configurar essa política, os usuários poderão optar por executar ou instalar arquivos com uma assinatura inválida.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Padrão**: Desativado  
  
- **Cópia e colagem de zona restrita do Internet Explorer via script**  
  Essa configuração de política permite que você gerencie se os scripts podem executar uma operação de área de transferência (por exemplo, recortar, copiar e colar) em uma região especificada. Se você habilitar essa configuração de política, um script poderá executar uma operação de área de transferência. Se você selecionar prompt na caixa suspensa, os usuários serão consultados sobre se deseja executar operações de área de transferência. Se você desabilitar essa configuração de política, um script não poderá executar uma operação de área de transferência. Se você não definir essa configuração de política, um script não poderá executar uma operação de área de transferência.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Padrão**: Desativar  
  
- **Conteúdo de arrastar zona restrita do Internet Explorer de domínios diferentes no Windows**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Padrão**: Desativado  
  
- **Usuários do Internet Explorer adicionando sites**  
  Impede que os usuários adicionem ou removam sites de zonas de segurança. Uma zona de segurança é um grupo de sites com o mesmo nível de segurança. Se você habilitar essa política, as configurações de gerenciamento de site para zonas de segurança serão desabilitadas. (Para ver as configurações de gerenciamento de site para zonas de segurança, na caixa de diálogo Opções da Internet, clique na guia Segurança e, em seguida, clique no botão sites.) Se você desabilitar essa política ou não configurá-la, os usuários poderão adicionar sites ou remover sites das zonas sites confiáveis e sites restritos e alterar as configurações da zona da intranet local. Essa política impede que os usuários alterem as configurações de gerenciamento de site para zonas de segurança estabelecidas pelo administrador. Nota: A política "desabilitar a página de segurança" (localizada em \ Configuração do Computador\modelos Administrativos\Componentes do Windows\internet Explorer\painel de controle), que remove a guia Segurança da interface, tem precedência sobre essa política. Se estiver habilitado, essa política será ignorada. Além disso, consulte "zonas de segurança: Use a política apenas configurações do computador ".  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Padrão**: Desativado  
  
- **Windows iniciado por script de zona da Internet Explorer**  
  Essa configuração de política permite que você gerencie restrições em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status. Se você habilitar essa configuração de política, a segurança das restrições do Windows não será aplicada nessa zona. A zona de segurança é executada sem a camada adicional de segurança fornecida por esse recurso. Se você desabilitar essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo. Se você não definir essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluam as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Padrão**: Desativado  
  
- **As zonas de segurança do Internet Explorer usam apenas as configurações do computador**  
  Aplica informações da zona de segurança a todos os usuários do mesmo computador. Uma zona de segurança é um grupo de sites com o mesmo nível de segurança. Se você habilitar essa política, as alterações que o usuário fizer em uma zona de segurança serão aplicadas a todos os usuários desse computador. Se você desabilitar essa política ou não configurá-la, os usuários do mesmo computador poderão estabelecer suas próprias configurações de zona de segurança. Use essa política para garantir que as configurações de zona de segurança se apliquem uniformemente ao mesmo computador e não variem de usuário para usuário. Além disso, consulte a política "zonas de segurança: não permitir que os usuários alterem políticas".  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Padrão**: Enabled  
  
- **O Internet Explorer bloqueou as permissões Java da zona do computador local**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Padrão**: Desabilitar Java 
  
- **Zona restrita do Internet Explorer não executa antimalware em controles do Active X**   
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Padrão**: Desativado  
  
- **Execução de zona restrita do Internet Explorer .NET Framework componentes dependentes assinados com Authenticode**  
  Essa configuração de política permite que você gerencie se .NET Framework componentes assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados assinados. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados. Se você não definir essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Padrão**: Desativar  
  
- **Acesso à zona restrita do Internet Explorer a fontes de dados**  
  Essa configuração de política permite que você gerencie se o Internet Explorer pode acessar dados de outra zona de segurança usando o Microsoft XML Parser (MSXML) ou o ActiveX Data Objects (ADO). Se você habilitar essa configuração de política, os usuários poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que uma página seja carregada na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você desabilitar essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você não definir essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Padrão**: Desativar 
  
- **A zona Internet do Internet Explorer não executa antimalware em controles ActiveX**  
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Padrão**: Desativado  
  
- **Cópia e colagem de zona Internet do Internet Explorer via script**  
  Essa configuração de política permite que você gerencie se os scripts podem executar uma operação de área de transferência (por exemplo, recortar, copiar e colar) em uma região especificada. Se você habilitar essa configuração de política, um script poderá executar uma operação de área de transferência. Se você selecionar prompt na caixa suspensa, os usuários serão consultados sobre se deseja executar operações de área de transferência. Se você desabilitar essa configuração de política, um script não poderá executar uma operação de área de transferência. Se você não definir essa configuração de política, um script poderá executar uma operação de área de transferência.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Padrão**: Desativar  
  
- **Serviço do instalador do Internet Explorer usando o Active X**  
  Essa configuração de política permite que você especifique como os controles ActiveX são instalados. Se você habilitar essa configuração de política, os controles ActiveX serão instalados somente se o serviço instalador do ActiveX estiver presente e tiver sido configurado para permitir a instalação de controles ActiveX. Se você desabilitar ou não definir essa configuração de política, os controles ActiveX, incluindo controles por usuário, serão instalados por meio do processo de instalação padrão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Padrão**: Enabled  
  
- **O Internet Explorer processa a proteção contra elevação de zona**  
  O Internet Explorer estabelece restrições em cada página da Web que ele abre. As restrições são dependentes do local da página da Web (Internet, intranet, zona do computador local e assim por diante). Por exemplo, as páginas da Web no computador local têm o mínimo de restrições de segurança e estão na zona do computador local, tornando a zona de segurança do computador local um destino principal para usuários mal-intencionados. Se você habilitar essa configuração de política, qualquer zona poderá ser protegida da elevação de zona para todos os processos. Se você desabilitar ou não definir essa configuração de política, processos diferentes do Internet Explorer ou aqueles listados na lista de processos não receberão essa proteção.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Padrão**: Enabled  
  
- **Internet Zone baixar controles ActiveX não assinados**   
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando provenientes de uma zona não confiável. Se você habilitar essa configuração de política, os usuários poderão executar controles não assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o controle não assinado seja executado. Se você desabilitar essa configuração de política, os usuários não poderão executar controles não assinados. Se você não definir essa configuração de política, os usuários não poderão executar controles não assinados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Padrão**: Desativar  
  
- **Zona Internet do Internet Explorer navegar pelas janelas e quadros entre domínios diferentes**   
  Essa configuração de política permite que você gerencie a abertura de janelas e quadros e o acesso de aplicativos em diferentes domínios. Se você habilitar essa configuração de política, os usuários poderão abrir janelas e quadros de outros domínios e acessar aplicativos de outros domínios. Se você selecionar prompt na caixa suspensa, os usuários serão consultados se deseja permitir que janelas e quadros acessem aplicativos de outros domínios. Se você desabilitar essa configuração de política, os usuários não poderão abrir janelas e quadros para acessar aplicativos de domínios diferentes. Se você não definir essa configuração de política, os usuários poderão abrir janelas e quadros de outros domínios e acessar aplicativos de outros domínios.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Padrão**: Desativar  
  
- **Atualizações de zona da Internet do Internet Explorer para barra de status por meio de script**  
  Essa configuração de política permite que você gerencie se um script pode atualizar a barra de status dentro da zona. Se você habilitar essa configuração de política, os scripts poderão atualizar a barra de status. Se você desabilitar ou não definir essa configuração de política, o script não poderá atualizar a barra de status.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Padrão**: Desativado  
  
- **A zona restrita do Internet Explorer inclui o caminho local ao carregar arquivos no servidor**  
  Essa configuração de política controla se as informações de caminho local são enviadas quando o usuário está carregando um arquivo por meio de um formulário HTML. Se as informações de caminho local forem enviadas, algumas informações poderão ser reveladas acidentalmente ao servidor. Por exemplo, os arquivos enviados da área de trabalho do usuário podem conter o nome de usuário como parte do caminho. Se você habilitar essa configuração de política, as informações de caminho serão enviadas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você desabilitar essa configuração de política, as informações de caminho serão removidas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você não definir essa configuração de política, o usuário poderá escolher se as informações de caminho serão enviadas quando estiverem carregando um arquivo por meio de um formulário HTML. Por padrão, as informações de caminho são enviadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Padrão**: Desativado  
  
- **Os processos do Internet Explorer restringem o download do arquivo**   
  Essa configuração de política permite que aplicativos que hospedam o controle de navegador da Web bloqueiem a solicitação automática de downloads de arquivos que não são iniciados pelo usuário. Se você habilitar essa configuração de política, o controle de navegador da Web bloqueará a solicitação automática de downloads de arquivo que não são iniciados pelo usuário para todos os processos. Se você desabilitar essa configuração de política, o controle de navegador da Web não bloqueará a solicitação automática de downloads de arquivo que não são iniciados pelo usuário para todos os processos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Padrão**: Enabled  
  
- **Zona restrita do Internet Explorer permitir que somente domínios aprovados usem controles ActiveX**   
  Essa configuração de política controla se o usuário é solicitado a permitir que os controles ActiveX sejam executados em sites que não sejam o site que instalou o controle ActiveX. Se você habilitar essa configuração de política, o usuário será solicitado antes que os controles ActiveX possam ser executados de sites nesta zona. O usuário pode optar por permitir que o controle seja executado a partir do site atual ou de todos os sites. Se você desabilitar essa configuração de política, o usuário não verá o prompt do ActiveX por site e os controles ActiveX poderão ser executados de todos os sites nesta zona.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Padrão**: Enabled  
  
- **Os controles de inicialização de zona restrita do Internet Explorer e script ativo X não estão marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Padrão**: Desativar  
  
- **Usuários do Internet Explorer alterando políticas**  
  Impede que os usuários alterem as configurações de zona de segurança. Uma zona de segurança é um grupo de sites com o mesmo nível de segurança. Se você habilitar essa política, o botão de nível personalizado e o controle deslizante de nível de segurança na guia Segurança da caixa de diálogo Opções da Internet serão desabilitados. Se você desabilitar essa política ou não configurá-la, os usuários poderão alterar as configurações de zonas de segurança. Essa política impede que os usuários alterem as configurações de zona de segurança estabelecidas pelo administrador. Nota: A política "desabilitar a página de segurança" (localizada em \ Configuração do Computador\modelos Administrativos\Componentes do Windows\internet Explorer\painel de controle), que remove a guia Segurança do Internet Explorer no painel de controle, tem precedência sobre Esta política. Se estiver habilitado, essa política será ignorada. Além disso, consulte "zonas de segurança: Use a política apenas configurações do computador ".  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Padrão**: Desativado  
  
- **Modo protegido de zona restrita do Internet Explorer**  
  Essa configuração de política permite ativar o modo protegido. O modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo os locais em que o Internet Explorer pode gravar no registro e no sistema de arquivos. Se você habilitar essa configuração de política, o modo protegido será ativado. O usuário não pode desativar o modo protegido. Se você desabilitar essa configuração de política, o modo protegido será desativado. O usuário não pode ativar o modo protegido. Se você não definir essa configuração de política, o usuário poderá ativar ou desativar o modo protegido.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Padrão**: Ativar  
  
- **Persistência de dados de usuário da zona Internet do Internet Explorer**  
  Essa configuração de política permite que você gerencie a preservação de informações no histórico do navegador, em favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Quando um usuário retornar a uma página persistente, o estado da página poderá ser restaurado se essa configuração de política estiver configurada adequadamente. Se você habilitar essa configuração de política, os usuários poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você desabilitar essa configuração de política, os usuários não poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você não definir essa configuração de política, os usuários poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Padrão**: Desativado  
  
- **Script de Internet do Internet Explorer de controles de navegador da Web**  
 
  Essa configuração de política determina se uma página pode controlar controles WebBrowser inseridos por meio de script. Se você habilitar essa configuração de política, o acesso de script ao controle WebBrowser será permitido. Se você desabilitar essa configuração de política, o acesso de script ao controle WebBrowser não será permitido. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o acesso de script ao controle WebBrowser. Por padrão, o acesso de script ao controle WebBrowser é permitido apenas no computador local e nas zonas da intranet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Padrão**: Desativado  
  
- **Persistência de dados de usuário de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie a preservação de informações no histórico do navegador, em favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Quando um usuário retornar a uma página persistente, o estado da página poderá ser restaurado se essa configuração de política estiver configurada adequadamente. Se você habilitar essa configuração de política, os usuários poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você desabilitar essa configuração de política, os usuários não poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você não definir essa configuração de política, os usuários não poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Padrão**: Desativado  
  
- **Permissões Java da zona de intranet bloqueada do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Padrão**: Desabilitar Java  
  
- **Modo protegido aprimorado do Internet Explorer**  
  O modo protegido avançado fornece proteção adicional contra sites mal-intencionados usando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam pelo menos o Windows 8, o modo protegido aprimorado também limita os locais em que o Internet Explorer pode ler no registro e no sistema de arquivos. Se você habilitar essa configuração de política, o modo protegido avançado será ativado. Qualquer zona que tenha o modo protegido habilitado usará o modo protegido avançado. Os usuários não poderão desabilitar o modo protegido avançado. Se você desabilitar essa configuração de política, o modo protegido avançado será desativado. Qualquer zona que tenha o modo protegido habilitado usará a versão do modo protegido introduzido no Internet Explorer 7 para Windows Vista. Se você não configurar essa política, os usuários poderão ativar ou desativar o modo protegido avançado na guia Avançado da caixa de diálogo Opções da Internet.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Padrão**: Enabled  
  
- **Avisos de tela inteligente de bypass do Internet Explorer**  
  Essa configuração de política determina se o usuário pode ignorar avisos do filtro do SmartScreen. O filtro do SmartScreen avisa o usuário sobre arquivos executáveis que os usuários do Internet Explorer geralmente não baixam da Internet. Se você habilitar essa configuração de política, os avisos do filtro do SmartScreen bloquearão o usuário. Se você desabilitar ou não definir essa configuração de política, o usuário poderá ignorar os avisos do filtro do SmartScreen.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Padrão**: Desativado  
  
- **Meta Refresh da zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o navegador de um usuário pode ser redirecionado para outra página da Web se o autor da página da Web usar a configuração de meta Refresh (marca) para redirecionar os navegadores para outra página da Web. Se você habilitar essa configuração de política, o navegador de um usuário que carrega uma página que contém uma configuração de meta Refresh ativa pode ser redirecionado para outra página da Web. Se você desabilitar essa configuração de política, o navegador de um usuário que carregar uma página que contém uma configuração de meta Refresh ativa não poderá ser redirecionado para outra página da Web. Se você não definir essa configuração de política, o navegador de um usuário que carregar uma página que contém uma configuração de meta Refresh ativa não poderá ser redirecionado para outra página da Web.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Padrão**: Desativado  
  
## <a name="local-policies-security-options"></a>Opções de segurança de políticas locais
Para obter mais informações, consulte [Policy CSP-LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) na documentação do Windows. 

- **Restringir o acesso anônimo a pipes nomeados e compartilhamentos**  
  Quando habilitada, essa configuração de segurança restringe o acesso anônimo a compartilhamentos e pipes para as configurações de: (1) pipes nomeados que podem ser acessados anonimamente (2) compartilhamentos que podem ser acessados anonimamente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Padrão**: Sim  
  
- **Segurança mínima de sessão para servidores baseados em NTLM SSP**  
  Essa configuração de segurança permite que um servidor exija a negociação de criptografia de 128 bits e/ou segurança de sessão NTLMv2. Esses valores são dependentes do valor de configuração de segurança do nível de autenticação do LAN Manager. As opções são: Exigir segurança de sessão NTLMv2: A conexão falhará se a integridade da mensagem não for negociada. Exigir criptografia de 128 bits. A conexão falhará se a criptografia forte (128 bits) não for negociada.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Padrão**: Exigir criptografia NTLM V2 e 128 bits  
  
- **Minutos de inatividade de tela de bloqueio até que a proteção de tela seja ativada**  
  O Windows repara na inatividade de um início de sessão e, se a quantidade de tempo inativo exceder o limite de inatividade, então, a proteção de ecrã será executado, bloqueando a sessão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Padrão**: 15
  
- **Exigir que o cliente assine sempre as comunicações digitalmente** Essa configuração de segurança determina se todo o tráfego de canal seguro iniciado pelo membro do domínio deve ser assinado ou criptografado. Quando um computador ingressa em um domínio, uma conta de computador é criada. Depois disso, quando o sistema é iniciado, ele usa a senha da conta de computador para criar um canal seguro com um controlador de domínio para seu domínio. Esse canal seguro é usado para executar operações como autenticação de passagem de NTLM, pesquisa de nome/SID de LSA e muito mais. Essa configuração determina se todo o tráfego de canal seguro iniciado pelo membro do domínio atende aos requisitos mínimos de segurança. Especificamente, ele determina se todo o tráfego de canal seguro iniciado pelo membro do domínio deve ser assinado ou criptografado. Se essa política estiver habilitada, o canal seguro não será estabelecido, a menos que a assinatura ou a criptografia de todo o tráfego de canal seguro seja negociada. Se essa política estiver desabilitada, a criptografia e a assinatura de todo o tráfego de canal seguro serão negociadas com o controlador de domínio, caso em que o nível de assinatura e criptografia depende da versão do controlador de domínio e das configurações dos dois seguintes Policie Membro do domínio: Criptografar digitalmente os dados do canal seguro (quando possível) membro do domínio: Assinar digitalmente os dados do canal seguro (quando possível).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Padrão**: Sim
  
- **Nível de autenticação**  
  Essa configuração de segurança determina qual protocolo de autenticação de desafio/resposta é usado para logons de rede. Essa escolha afeta o nível de protocolo de autenticação usado pelos clientes, o nível de segurança de sessão negociado e o nível de autenticação aceito pelos servidores da seguinte maneira:  
  - *Enviar respostas LM e NTLM* -os clientes usam a autenticação LM e NTLM e nunca usam a segurança de sessão NTLMv2; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar LM e NTLM-NTLMv2 se negociados* -os clientes usam a autenticação LM e NTLM e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar somente resposta NTLM* -os clientes usam somente a autenticação NTLM e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar somente resposta NTLMv2* – os clientes usam somente a autenticação NTLMv2 e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar somente resposta NTLMv2. Recusar LM* -os clientes usam somente a autenticação NTLMv2 e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; controladores de domínio recusam LM (aceitam somente autenticação NTLM e NTLMv2). 
  - *Enviar somente resposta NTLMv2. Recusar LM e NTLM* -os clientes usam somente a autenticação NTLMv2 e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio recusam LM e NTLM (aceitam somente a autenticação NTLMv2).  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Padrão**: Enviar somente resposta NTLMv2. Recusar LM e NTLM
  
- **Impedir que os clientes enviem senhas não criptografadas para servidores SMB de terceiros**  
  Se essa configuração de segurança estiver habilitada, o redirecionador de protocolo SMB poderá enviar senhas de texto não criptografado a servidores SMB não Microsoft que não ofereçam suporte à criptografia de senha durante a autenticação. O envio de senhas não criptografadas é um risco à segurança.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Padrão**: Sim
  
- **Exigir comunicações de assinatura digital do servidor sempre**  
  Essa configuração de segurança determina se o cliente SMB tenta negociar a assinatura de pacotes SMB. O protocolo SMB fornece a base para o compartilhamento de arquivos e impressão da Microsoft e muitas outras operações de rede, como a administração remota do Windows. Para evitar ataques man-in-the-Middle que modificam pacotes SMB em trânsito, o protocolo SMB dá suporte à assinatura digital de pacotes SMB. Essa configuração de política determina se o componente cliente SMB tenta negociar a assinatura de pacote SMB quando se conecta a um servidor SMB. Se essa configuração estiver habilitada, o cliente de rede da Microsoft solicitará que o servidor execute a assinatura de pacote SMB na configuração da sessão. Se a assinatura de pacotes tiver sido ativada no servidor, a assinatura de pacotes será negociada. Se essa política estiver desabilitada, o cliente SMB nunca negociará a assinatura de pacotes SMB.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Padrão**: Sim
  
- **Comportamento da solicitação de elevação do administrador**  
  Essa configuração de política controla o comportamento da solicitação de elevação para administradores. As opções são: 
  - *Elevar sem avisar* – permite que contas com privilégios executem uma operação que requer elevação sem a necessidade de consentimento ou credenciais. Nota: Use essa opção somente nos ambientes mais restritos. 
  - *Solicitar credenciais na área de trabalho segura* – quando uma operação requer elevação de privilégio, o usuário é solicitado na área de trabalho segura para inserir um nome de usuário e senha privilegiados. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio mais alto disponível do usuário. 
  - *Solicitar consentimento na área de trabalho segura* – quando uma operação requer elevação de privilégio, o usuário é solicitado na área de trabalho segura para selecionar permitir ou negar. Se o usuário selecionar permitir, a operação continuará com o privilégio mais alto disponível do usuário. 
  - *Solicitar credenciais* – quando uma operação requer elevação de privilégio, o usuário é solicitado a inserir um nome de usuário administrativo e uma senha. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Solicitar consentimento* -quando uma operação requer elevação de privilégio, o usuário recebe uma solicitação para selecionar permitir ou negar. Se o usuário selecionar permitir, a operação continuará com o privilégio mais alto disponível do usuário.  
  - *Solicitar consentimento para binários não Windows* -quando uma operação para um aplicativo que não é da Microsoft requer elevação de privilégio, o usuário é solicitado na área de trabalho segura para selecionar permitir ou negar. Se o usuário selecionar permitir, a operação continuará com o privilégio mais alto disponível do usuário. 
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Padrão**: Solicitar consentimento na área de trabalho segura
  
- **Segurança mínima de sessão para clientes baseados em NTLM SSP**  
  Essa configuração de segurança permite que um cliente exija a negociação de criptografia de 128 bits e/ou segurança de sessão NTLMv2. Esses valores são dependentes do valor de configuração de segurança do nível de autenticação do LAN Manager. As opções são:
  - *Exigir segurança de sessão NTLMv2* -a conexão falhará se o protocolo NTLMv2 não for negociado. 
  - *Exigir criptografia de 128 bits* -a conexão falhará se a criptografia forte (128 bits) não for negociada.
  - *Exigir criptografia NTLMv2 e 128 bits*.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Padrão**: Exigir criptografia NTLM v2 128
  
- **Comportamento de remoção de cartão inteligente**  
  Essa configuração de segurança determina o que acontece quando o cartão inteligente de um usuário conectado é removido do leitor de cartão inteligente. As opções são:
  - *Nenhuma ação*. 
  - *Bloquear estação de trabalho* -a estação de trabalho é bloqueada quando o cartão inteligente é removido, permitindo que os usuários saiam da área, usem seu cartão inteligente e ainda mantenham uma sessão protegida.
  - *Forçar logoff* – o usuário é desconectado automaticamente quando o cartão inteligente é removido.
  - *Desconectar área de trabalho remota sessão* – a remoção do cartão inteligente desconecta a sessão sem fazer logoff do usuário. Isso permite que o usuário insira o cartão inteligente e retome a sessão mais tarde, ou em outro computador equipado com leitor de cartão inteligente, sem precisar fazer logon novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Padrão**: Bloquear estação de trabalho
  
- **Bloquear a enumeração anônima de contas e compartilhamentos SAM**  
  Essa configuração de segurança determina se a enumeração anônima de contas e compartilhamentos SAM deve ser permitida. O Windows permite que usuários anônimos executem determinadas atividades, como a enumeração de nomes de contas de domínio e compartilhamentos de rede. Isso é conveniente, por exemplo, quando um administrador deseja conceder acesso a usuários em um domínio confiável que não mantém uma confiança recíproca. Se você não quiser permitir a enumeração anônima de contas e compartilhamentos SAM, defina essa política como *Sim*.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Padrão**: Sim
  
- **Bloquear logon remoto com senha em branco**  
  Essa configuração de segurança determina se as contas locais que não são protegidas por senha podem ser usadas para fazer logon de locais diferentes do console do computador físico. Se habilitada, as contas locais que não são protegidas por senha devem usar o teclado do computador para fazer logon. 

  *Aviso*: Os computadores que não estão em locais fisicamente seguros sempre devem impor políticas de senha forte para todas as contas de usuário locais. Caso contrário, qualquer pessoa com acesso físico ao computador pode fazer logon usando uma conta de usuário que não tenha uma senha. Isso é especialmente importante para computadores portáteis. 

  Se você aplicar essa política de segurança ao grupo everyone, ninguém poderá fazer logon por meio de Serviços de Área de Trabalho Remota. Essa configuração não afeta os logons que usam contas de domínio. É possível que os aplicativos que usam logons interativos remotos ignorem essa configuração.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Padrão**: Sim
  
- **Comportamento de prompt de elevação de usuário padrão**  
  Essa configuração de política controla o comportamento da solicitação de elevação para usuários padrão. 
  - *Negar automaticamente solicitações de elevação* – quando uma operação requer elevação de privilégio, uma mensagem de erro de acesso negado configurável é exibida. Uma empresa que esteja executando áreas de trabalho como usuário padrão pode escolher essa configuração para reduzir as chamadas de suporte técnico. 
  - *Solicitar credenciais na área de trabalho segura* – quando uma operação requer elevação de privilégio, o usuário é solicitado na área de trabalho segura para inserir um nome de usuário e senha diferentes. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Solicitar credenciais* – quando uma operação requer elevação de privilégio, o usuário é solicitado a inserir um nome de usuário administrativo e uma senha. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Padrão**: Negar automaticamente solicitações de elevação
  
- **Exigir o modo de aprovação de administrador para administradores**  
  Essa configuração de política controla o comportamento de todas as configurações de política de controle de conta de usuário (UAC) para o computador. Se você alterar essa configuração de política, deverá reiniciar o computador. As opções são:   
  - *Não configurado* -o modo de aprovação de administrador e todas as configurações de política de UAC relacionadas estão desabilitados. Nota: Se essa configuração de política estiver desabilitada, a central de segurança o notificará de que a segurança geral do sistema operacional foi reduzida. 
  - *Sim* – o modo de aprovação de administrador está habilitado. Essa política deve ser habilitada e as configurações de política de UAC relacionadas devem ser definidas adequadamente para permitir que a conta de administrador interna e todos os outros usuários que são membros do grupo Administradores sejam executados no modo de aprovação de administrador.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Padrão**: Sim
  
- **Impedir enumeração anônima de contas SAM**  
  Essa configuração de segurança determina quais permissões adicionais são concedidas para conexões anônimas ao computador. O Windows permite que usuários anônimos executem determinadas atividades, como a enumeração de nomes de contas de domínio e compartilhamentos de rede. Isso é conveniente, por exemplo, quando um administrador deseja conceder acesso a usuários em um domínio confiável que não mantém uma confiança recíproca. Essa opção de segurança permite que restrições adicionais sejam colocadas em conexões anônimas da seguinte maneira: 
  - *Sim* -não permitir enumeração de contas Sam. Essa opção substitui todos os usuários autenticados nas permissões de segurança para recursos.
  - *Não configurado* -sem restrições adicionais. Conte com as permissões padrão.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Padrão**: Sim
  
- **Permitir chamadas remotas para o Gerenciador de contas de segurança**  
  Essa configuração de política permite restringir conexões RPC remotas ao SAM. Se não for selecionado, o descritor de segurança padrão será usado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Padrão**: *O:BAG: INADEQUADO: (A;; RC;;; BA*

- **Usar o modo de aprovação de administrador**  
  Essa configuração de política controla o comportamento do modo de aprovação de administrador para a conta de administrador interno. As opções são: 
  - *Sim* – a conta de administrador interna usa o modo de aprovação de administrador. Por padrão, qualquer operação que exija elevação de privilégio solicitará que o usuário aprove a operação. 
  - *Não configurado* -a conta de administrador interno executa todos os aplicativos com privilégio administrativo completo. 

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Padrão**: Sim
  
- **Permitir aplicativos de acesso à interface do usuário para locais seguros**  
  Essa configuração de política controla se os programas de acessibilidade da interface do usuário (UIAccess ou UIA) podem desabilitar automaticamente a área de trabalho segura para solicitações de elevação usadas por um usuário padrão. 
  - *Sim* -UIA programas, incluindo a assistência remota do Windows, desabilita automaticamente a área de trabalho segura para solicitações de elevação. Se você não desabilitar o "controle de conta de usuário: Mude para a configuração de política da área de trabalho segura ao solicitar elevação ", os prompts aparecem na área de trabalho do usuário interativo em vez da área de trabalho segura. 
  - *Não configurado*:-a área de trabalho segura pode ser desabilitada somente pelo usuário da área de trabalho interativa ou desabilitando o "controle de conta de usuário: Alterne para a área de trabalho segura ao solicitar elevação ".  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Padrão**: Sim

- **Detectar instalações de aplicativos e solicitar elevação**  
  Essa configuração de política controla o comportamento da detecção de instalação do aplicativo para o computador. As opções são: 
  - *Habilitado* – quando um pacote de instalação de aplicativo é detectado e requer elevação de privilégio, o usuário é solicitado a inserir um nome de usuário administrativo e uma senha. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Desabilitado* -os pacotes de instalação de aplicativos não são detectados e são solicitados a fornecer elevação. As empresas que executam desktops de usuário padrão e usam tecnologias de instalação delegadas, como o Política de Grupo de Instalação de Software ou o Systems Management Server (SMS), devem desabilitar essa configuração de política. Nesse caso, a detecção do instalador é desnecessária.  
  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Padrão**: Sim
  
- **Impedir o armazenamento do valor de hash do LAN Manager na próxima alteração de senha**  
  Essa configuração de segurança determina se, na próxima alteração de senha, o valor de hash do LM (LAN Manager) para a nova senha será armazenado. O hash do LM é relativamente fraco e propenso a ataques, em comparação com o hash do Windows NT criptograficamente mais forte. Como o hash do LM é armazenado no computador local no banco de dados de segurança, as senhas podem ser comprometidas se o banco de dados de segurança for atacado.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Padrão**: Sim

- **Virtualizar falhas de gravação de arquivo e registro para locais por usuário**  
  Essa configuração de política controla se as falhas de gravação do aplicativo são redirecionadas para os locais do registro e do sistema de arquivos definidos. Essa configuração de política reduz os aplicativos que são executados como administrador e grava dados de aplicativo em tempo de execução em *% ProgramFiles%* , *% windir%* , *%windir%\System32*ou *HKLM\Software*.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Padrão**: Sim

## <a name="ms-security-guide"></a>Guia de segurança da MS  
Para obter mais informações, consulte [Policy CSP-MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) na documentação do Windows.  

- **Aplicar restrições de UAC a contas locais no logon de rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Padrão**: Enabled
  
- **Configuração de inicialização do driver de cliente SMB v1**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Padrão**: Driver desabilitado
  
- **Servidor SMB v1**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Padrão**: Desativado
  
- **Autenticação resumida**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Padrão**: Desativado
  
- **Manipulação de exceção estruturada substituir proteção**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Padrão**: Enabled
  
## <a name="mss-legacy"></a>MSS herdado  
Para obter mais informações, consulte [Policy CSP-MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) na documentação do Windows.  

- **Nível de proteção de roteamento de origem IP de rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Padrão**: Proteção mais alta  
  
- **Rede ignorar solicitações de liberação de nome NetBIOS exceto de servidores WINS**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Padrão**: Enabled
  
- **Nível de proteção de roteamento de origem IPv6 da rede**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Padrão**: Proteção mais alta

- **Redirecionamentos de ICMP de rede substituem o OSPF gerado**  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Padrão**: Desativado
  
## <a name="power"></a>Alimentar  
Para obter mais informações, consulte [CSP da política – Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) na documentação do Windows.  

- **Exigir senha ao ativar enquanto conectado**  
  Essa configuração de política especifica se o usuário é solicitado a fornecer uma senha quando o sistema sai do estado de suspensão. Se você habilitar ou não definir essa configuração de política, o usuário será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão. Se você desabilitar essa configuração de política, o usuário não será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Padrão**: Enabled
  
- **Estados de espera quando estiverem em suspensão durante a bateria**  
  Essa configuração de política gerencia se o Windows pode usar Estados de espera ao colocar o computador em estado de suspensão. Se você habilitar ou não definir essa configuração de política, o Windows usará Estados de espera para colocar o computador em estado de suspensão. Se você desabilitar essa configuração de política, os Estados de espera (S1-S3) não serão permitidos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Padrão**: Desativado
  
- **Estados de espera quando conectados em suspensão**  
  Essa configuração de política gerencia se o Windows pode usar Estados de espera ao colocar o computador em estado de suspensão. Se você habilitar ou não definir essa configuração de política, o Windows usará Estados de espera para colocar o computador em estado de suspensão. Se você desabilitar essa configuração de política, os Estados de espera (S1-S3) não serão permitidos.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Padrão**: Desativado
  
- **Exigir senha ao ativar enquanto estiver na bateria**  
  Essa configuração de política especifica se o usuário é solicitado a fornecer uma senha quando o sistema sai do estado de suspensão. Se você habilitar ou não definir essa configuração de política, o usuário será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão. Se você desabilitar essa configuração de política, o usuário não será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Padrão**: Enabled

## <a name="remote-assistance"></a>Assistência Remota
- **Assistência remota solicitada**  
  Essa configuração de política permite ativar ou desativar a assistência remota solicitada (solicitar) neste computador. 
  - *Se você habilitar essa configuração de política*, os usuários neste computador poderão usar o email ou a transferência de arquivos para pedir ajuda a alguém. Além disso, os usuários podem usar programas de mensagens instantâneas para permitir conexões com este computador, e você pode definir configurações de assistência remota adicionais. 
  - *Se você desabilitar essa configuração de política*, os usuários neste computador não poderão usar email ou transferência de arquivo para pedir ajuda a alguém. Além disso, os usuários não podem usar programas de mensagens instantâneas para permitir conexões com este computador. 
  - *Se você não definir essa configuração de política*, os usuários poderão ativar ou desativar a assistência remota solicitada (solicitar) em Propriedades do sistema no painel de controle. Os usuários também podem configurar as configurações de assistência remota. 

  Se você habilitar essa configuração de política, terá duas maneiras de permitir que os auxiliares forneçam assistência remota: "Permitir que os auxiliares exibam apenas o computador" ou "permitir que os auxiliares controlem o computador remotamente". A configuração de política "tempo máximo de tíquete" define um limite na quantidade de tempo que um convite de assistência remota criado usando email ou transferência de arquivos pode permanecer aberto. A configuração "selecionar o método para enviar convites por email" especifica qual padrão de email usar para enviar convites de assistência remota. Dependendo do seu programa de email, você pode usar o padrão mailto (o destinatário do convite se conecta por meio de um link da Internet) ou o padrão SMAPI (Simple MAPI) (o convite é anexado à mensagem de email). Essa configuração de política não está disponível no Windows Vista, pois a SMAPI é o único método com suporte. Se você habilitar essa configuração de política, também deverá habilitar as exceções de firewall apropriadas para permitir comunicações de assistência remota.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Padrão**: Desabilitar a assistência remota

  Quando definido para *habilitar a assistência remota*, defina as seguintes configurações adicionais:  
  - **Permissão de assistência remota solicitada**  
    **Padrão**: Vista  

  - **Valor de tempo máximo de tíquete**  
    **Padrão**: *Não configurado*  

  - **Período de tempo máximo de tíquete**  
    **Padrão**: Minutos    

  - **Método de convite por email**  
    **Padrão**: MAPI simples

  
## <a name="remote-desktop-services"></a>Serviços de Ambiente de Trabalho Remoto  
Para obter mais informações, consulte [Policy CSP-RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) na documentação do Windows.  

- **Bloquear salvamento de senha**  
  Controla se as senhas podem ser salvas neste computador de Conexão de Área de Trabalho Remota. Se você habilitar essa configuração, a caixa de seleção Salvar senha no Conexão de Área de Trabalho Remota será desabilitada e os usuários não poderão salvar senhas. Quando um usuário abre um arquivo RDP usando Conexão de Área de Trabalho Remota e salva suas configurações, qualquer senha que anteriormente existia no arquivo RDP é excluída. Se você desabilitar essa configuração ou deixá-la não configurada, o usuário poderá salvar senhas usando Conexão de Área de Trabalho Remota.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Padrão**: Enabled
  
- **Comunicação segura de RPC**  
  Especifica se um servidor de Host da Sessão da Área de Trabalho Remota requer comunicação de RPC segura com todos os clientes ou permite comunicação não segura. Você pode usar essa configuração para reforçar a segurança da comunicação RPC com clientes, permitindo apenas solicitações autenticadas e criptografadas. Se o status for definido como habilitado, Serviços de Área de Trabalho Remota aceitará solicitações de clientes RPC que dão suporte a solicitações seguras e não permitirá a comunicação não segura com clientes não confiáveis. Se o status for definido como desabilitado, Serviços de Área de Trabalho Remota sempre solicitará segurança para todo o tráfego RPC. No entanto, a comunicação não segura é permitida para clientes RPC que não respondem à solicitação. Se o status for definido como não configurado, a comunicação não segura será permitida. Nota: A interface RPC é usada para administrar e configurar Serviços de Área de Trabalho Remota.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Padrão**: Enabled
  
- **Bloquear redirecionamento de unidade**  
  Essa configuração de política especifica se é para impedir o mapeamento de unidades cliente em uma sessão de Serviços de Área de Trabalho Remota (redirecionamento de unidade). Por padrão, um servidor Host da Sessão RD mapeia automaticamente as unidades do cliente após a conexão. As unidades mapeadas aparecem na árvore de pastas de sessões no explorador de arquivos ou no computador no formato  *\<DriveLetter >* em  *\<ComputerName >* . Você pode usar essa configuração de política para substituir esse comportamento. Se você habilitar essa configuração de política, o redirecionamento de unidade de cliente não será permitido em sessões de Serviços de Área de Trabalho Remota, e o redirecionamento de cópia de arquivo da área de transferência não será permitido em computadores que executam o Windows Server 2003, Windows 8 e Windows XP. Se você desabilitar essa configuração de política, o redirecionamento de unidade de cliente sempre será permitido. Além disso, o redirecionamento de cópia de arquivo da área de transferência sempre será permitido se o redirecionamento de área de transf for permitido. Se você não definir essa configuração de política, o redirecionamento de unidade de cliente e de cópia de arquivo da área de transferência não serão especificados no nível de Política de Grupo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Padrão**: Enabled
  
- **Solicitar senha na conexão**  
  Essa configuração de política especifica se Serviços de Área de Trabalho Remota sempre solicita uma senha ao cliente durante a conexão. Você pode usar essa configuração para impor um prompt de senha para os usuários que fazem logon no Serviços de Área de Trabalho Remota, mesmo que eles já tenham fornecido a senha no cliente do Conexão de Área de Trabalho Remota. Por padrão, Serviços de Área de Trabalho Remota permite que os usuários façam logon automaticamente digitando uma senha no cliente Conexão de Área de Trabalho Remota. Se você habilitar essa configuração de política, os usuários não poderão fazer logon automaticamente no Serviços de Área de Trabalho Remota fornecendo suas senhas no cliente Conexão de Área de Trabalho Remota. Ele será solicitado a fornecer uma senha para fazer logon. Se você desabilitar essa configuração de política, os usuários sempre poderão fazer logon no Serviços de Área de Trabalho Remota automaticamente fornecendo suas senhas no cliente Conexão de Área de Trabalho Remota. Se você não definir essa configuração de política, o logon automático não será especificado no nível de Política de Grupo.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Padrão**: Enabled
  
- **Nível de criptografia de conexão de cliente dos serviços de área de trabalho remota**  
  Especifica se o uso de um nível de criptografia específico deve ser necessário para proteger as comunicações entre computadores cliente e servidores de Host da Sessão RD durante as conexões de protocolo RDP (RDP). Essa política só se aplica quando você está usando a criptografia RDP nativa. No entanto, a criptografia RDP nativa (em oposição à criptografia SSL) não é recomendada. Esta política não se aplica à criptografia SSL. Se você habilitar essa configuração de política, todas as comunicações entre clientes e servidores de Host da Sessão RD durante conexões remotas deverão usar o método de criptografia especificado nessa configuração. Por padrão, o nível de criptografia é definido como alto. Os seguintes métodos de criptografia estão disponíveis:  
  - *Alta* -a configuração alta criptografa os dados enviados do cliente para o servidor e do servidor para o cliente usando a criptografia de 128 bits forte. Use esse nível de criptografia em ambientes que contêm somente clientes de 128 bits (por exemplo, clientes que executam o Conexão de Área de Trabalho Remota). Os clientes que não suportam esse nível de criptografia não podem se conectar a servidores Host da Sessão RD.  
  - *Compatível com cliente* – a configuração compatível com o cliente criptografa os dados enviados entre o cliente e o servidor na restrição de chave máxima com suporte pelo cliente. Use esse nível de criptografia em ambientes que incluem clientes que não dão suporte à criptografia de 128 bits.  
  - *Baixa* -a configuração baixa criptografa apenas os dados enviados do cliente para o servidor usando a criptografia de 56 bits.  
  
  Se você desabilitar ou não definir essa configuração, o nível de criptografia a ser usado para conexões remotas com Host da Sessão RD servidores não será aplicado por meio de Política de Grupo. A conformidade de FIPS importante pode ser configurada por meio da criptografia do sistema. Use algoritmos compatíveis com FIPS para criptografia, hash e configurações de assinatura no Política de Grupo (em configuração do computador \ \ \ \ Opções de autenticação.) A configuração compatível com FIPS criptografa e descriptografa os dados enviados do cliente para o servidor e do servidor para o cliente, com os algoritmos de criptografia do padrão FIPS (FIPS) 140, usando os módulos de criptografia da Microsoft. Use esse nível de criptografia quando as comunicações entre clientes e servidores de Host da Sessão RD exigirem o nível mais alto de criptografia.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Padrão**: Alta
  
## <a name="remote-management"></a>Gestão Remota  
Para obter mais informações, consulte [Policy CSP-RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) na documentação do Windows.  

- **Bloquear o armazenamento de credenciais executar como**  
  Autenticação básica do cliente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Padrão**: Enabled
  
- **Autenticação básica**  
  Essa configuração de política permite que você gerencie se o serviço de Gerenciamento Remoto do Windows (WinRM) aceita a autenticação básica de um cliente remoto. Se você habilitar essa configuração de política, o serviço WinRM aceitará a autenticação básica de um cliente remoto. Se você desabilitar ou não definir essa configuração de política, o serviço WinRM não aceitará a autenticação básica de um cliente remoto.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Padrão**: Desativado
  
- **Bloquear a autenticação Digest do cliente**  
  Essa configuração de política permite que você gerencie se o cliente do Gerenciamento Remoto do Windows (WinRM) usa a autenticação Digest. Se você habilitar essa configuração de política, o cliente WinRM não usará a autenticação Digest. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM usará a autenticação Digest.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Padrão**: Enabled
  
- **Tráfego não criptografado**  
  Essa configuração de política permite que você gerencie se o serviço de Gerenciamento Remoto do Windows (WinRM) envia e recebe mensagens não criptografadas pela rede. Se você habilitar essa configuração de política, o cliente WinRM enviará e receberá mensagens não criptografadas pela rede. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM enviará ou receberá somente mensagens criptografadas pela rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Padrão**: Desativado
  
- **Tráfego de cliente não criptografado**  
  Essa configuração de política permite que você gerencie se o cliente do Gerenciamento Remoto do Windows (WinRM) envia e recebe mensagens não criptografadas pela rede. Se você habilitar essa configuração de política, o cliente WinRM enviará e receberá mensagens não criptografadas pela rede. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM enviará ou receberá somente mensagens criptografadas pela rede.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Padrão**: Desativado
  
- **Autenticação básica do cliente**  
  Essa configuração de política permite que você gerencie se o cliente do Gerenciamento Remoto do Windows (WinRM) usa a autenticação básica. Se você habilitar essa configuração de política, o cliente WinRM usará a autenticação básica. Se o WinRM estiver configurado para usar o transporte HTTP, o nome de usuário e a senha serão enviados pela rede como texto não criptografado. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM não usará a autenticação básica.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Padrão**: Desativado
  
## <a name="remote-procedure-call"></a>Chamada de procedimento remoto  
Para obter mais informações, consulte [Policy CSP-RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) na documentação do Windows.  

- **Opções de cliente não autenticado RPC**  
  Essa configuração de política controla como o tempo de execução do servidor RPC lida com clientes RPC não autenticados se conectando a servidores RPC. Essa configuração de política afeta todos os aplicativos RPC. Em um ambiente de domínio, use essa configuração de política com cuidado, pois ela pode afetar uma ampla gama de funcionalidades, incluindo o próprio processamento da diretiva de grupo. A reversão de uma alteração para essa configuração de política pode exigir intervenção manual em cada computador afetado. Essa configuração de política nunca deve ser aplicada a um controlador de domínio. Se você desabilitar essa configuração de política, o tempo de execução do servidor RPC usará o valor "autenticado" no cliente Windows e o valor de "nenhum" em versões do Windows Server que dão suporte a essa configuração de política. Se você não definir essa configuração de política, ela permanecerá desabilitada. O tempo de execução do servidor RPC se comporta como se estivesse habilitado com o valor "autenticado" usado para o cliente Windows e o valor de "nenhum" usado para SKUs de servidor que dão suporte a essa configuração de política. Se você habilitar essa configuração de política, ela direcionará o tempo de execução do servidor RPC para restringir os clientes RPC não autenticados que se conectam a servidores RPC em execução em um computador. Um cliente será considerado um cliente autenticado se usar um pipe nomeado para se comunicar com o servidor ou se usar a segurança RPC. As interfaces RPC que solicitaram especificamente que sejam acessíveis por clientes não autenticados podem estar isentas dessa restrição, dependendo do valor selecionado para essa configuração de política.  
  - *Nenhum* permite que todos os clientes RPC se conectem a servidores RPC em execução no computador no qual a configuração de política é aplicada. 
  - *Autenticado* permite que somente clientes RPC autenticados (de acordo com a definição acima) se conectem a servidores RPC em execução no computador no qual a configuração de política é aplicada. As isenções são concedidas a interfaces que as solicitaram. 
  - *Autenticado sem exceções* permite que somente clientes RPC autenticados (de acordo com a definição acima) se conectem a servidores RPC em execução no computador no qual a configuração de política é aplicada. Nenhuma exceção é permitida. Nota: Essa configuração de política não será aplicada até que o sistema seja reinicializado.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Padrão**: Autenticado

## <a name="search"></a>Pesquisa 
Para obter mais informações, consulte [CSP da política – Pesquisar](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) na documentação do Windows.  

- **Desabilitar a indexação de itens criptografados**  
  Permite ou proíbe a indexação de itens. Essa opção é para o indexador do Windows Search, que controla se ele indexará itens que são criptografados, como os arquivos protegidos por WIP (proteção de informações do Windows). Quando a política está ativada, os itens protegidos pelo WIP são indexados e os respetivos metadados são armazenados numa localização não encriptada. Os metadados incluem conteúdos como o caminho do ficheiro e a data de modificação. Quando a política estiver desabilitada, os itens protegidos por WIP não serão indexados e não aparecerão nos resultados na Cortana ou no explorador de arquivos. O desempenho das aplicações de fotografias e do Groove também poderá ser afetado se existirem muitos ficheiros multimédia protegidos pelo WIP no dispositivo.  
  [Saiba mais]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Padrão**: Sim
  
## <a name="smart-screen"></a>Tela inteligente  
Para obter mais informações, consulte [CSP da política-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.  

- **Bloquear a execução de arquivos não verificados**  
  Impedir que o usuário execute arquivos não verificados. 
  - *Não configurado* -os funcionários podem ignorar os avisos do SmartScreen e executar arquivos mal-intencionados. 
  - *Sim* – os funcionários não podem ignorar avisos do SmartScreen e executar arquivos mal-intencionados.

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Padrão**: Sim

- **Exigir SmartScreen para aplicativos e arquivos**  
  Permite que os administradores de ti configurem o SmartScreen para Windows.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Padrão**: Sim
  
## <a name="system"></a>Sistema  
Para obter mais informações, consulte [CSP da política – sistema](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) na documentação do Windows.  

- **Inicialização do driver iniciar inicialização do sistema**  
  Essa configuração de política permite que você especifique quais drivers de inicialização inicial são inicializados com base em uma classificação determinada por um driver de inicialização de antimalware de início antecipado. O driver de inicialização de antimalware de início antecipado pode retornar as seguintes classificações para cada driver de inicialização inicial: 
  - *Bom* -o driver foi assinado e não foi violado.  
  - *Mal* -o driver foi identificado como malware. Recomendamos que você não permita que drivers inválidos conhecidos sejam inicializados. 
  - *Inadequado, mas necessário para inicialização* -o driver foi identificado como malware, mas o computador não pode ser inicializado com êxito sem carregar esse driver. 
  - *Desconhecido* -este driver não foi atestado pelo seu aplicativo de detecção de malware e não foi classificado pelo driver de inicialização de antimalware de início antecipado.  

  Se você habilitar essa configuração de política, poderá escolher quais drivers de inicialização inicial serão inicializados na próxima vez em que o computador for iniciado. Se você desabilitar ou não definir essa configuração de política, os drivers de início de inicialização determinoum ser bons, desconhecidos ou ruins, mas a inicialização crítica será inicializada e a inicialização de drivers determinados como defeituosos será ignorada. Se o seu aplicativo de detecção de malware não incluir um driver de inicialização de antimalware de início antecipado ou se o driver de inicialização de antimalware de início antecipado tiver sido desabilitado, essa configuração não terá nenhum efeito e todos os drivers de inicialização iniciada serão inicializados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Padrão**: Bom desconhecido e crítico ruim


## <a name="wi-fi"></a>Wi-Fi  
Para obter mais informações, consulte [Policy CSP-WiFi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) na documentação do Windows.  

- **Bloquear compartilhamento de Internet**  
  Especifica se o compartilhamento da Internet é possível no dispositivo.   
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Padrão**: Sim  

- **Bloquear a conexão automática a hotspots Wi-Fi**  
  Permitir ou impedir que o dispositivo se conecte automaticamente a hotspots Wi-Fi.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Padrão**: Sim  
  
## <a name="windows-connection-manager"></a>Gerenciador de conexões do Windows  
Para obter mais informações, consulte [Policy CSP-WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) na documentação do Windows.  

- **Bloquear conexão a redes que não são de domínio**  
  Essa configuração de política impede que os computadores se conectem a uma rede baseada em domínio e a uma rede não baseada em domínio ao mesmo tempo. Se essa configuração de política estiver habilitada, o computador responderá a tentativas automáticas e manuais de conexão de rede com base nas seguintes circunstâncias: 
  - Tentativas de conexão automática quando o computador já está conectado a uma rede baseada em domínio, todas as tentativas de conexão automática para redes que não são de domínio são bloqueadas. Quando o computador já estiver conectado a uma rede não baseada em domínio, as tentativas de conexão automática para redes baseadas em domínio serão bloqueadas. 
  - Tentativas de conexão manual quando o computador já está conectado a uma rede não baseada em domínio ou a uma rede baseada em domínio por meio de mídia diferente de Ethernet, e um usuário tenta criar uma conexão manual com uma rede adicional em violação dessa política configuração, a conexão de rede existente é desconectada e a conexão manual é permitida. Quando o computador já estiver conectado a uma rede não baseada em domínio ou a uma rede baseada em domínio pela Ethernet, e um usuário tentar criar uma conexão manual com uma rede adicional em violação dessa configuração de política, a conexão Ethernet existente será mantido e a tentativa de conexão manual é bloqueada.  

  Se essa configuração de política não estiver configurada ou estiver desabilitada, os computadores terão permissão para se conectar simultaneamente a redes de domínio e fora do domínio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Padrão**: Enabled
  
## <a name="windows-defender"></a>Windows Defender  
Para obter mais informações, consulte [Policy CSP-defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.  

- **Examinar mensagens de email recebidas**  
  Permite ou não a verificação de email.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Padrão**: Sim  

- **Tipo de processo filho de lançamento de aplicativos do Office**  
  Os aplicativos do Office não terão permissão para criar processos filho. Isso inclui o Word, o Excel, o PowerPoint, o OneNote e o Access. Esse é um comportamento típico de malware, especialmente para ataques baseados em macro que tentam usar aplicativos do Office para iniciar ou baixar executáveis mal-intencionados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Padrão**: Bloquear
  
- **Tipo de consentimento de envio de amostra do defender**  
  Verifica o nível de consentimento do usuário no Windows Defender para enviar dados. Se o consentimento necessário já tiver sido concedido, o Windows defender os enviará. Caso contrário, (e se o usuário tiver especificado nunca perguntar), a interface do usuário será iniciada para solicitar o consentimento do usuário (quando o defender/AllowCloudProtection for permitido) antes de enviar dados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Padrão**: Enviar amostras seguras automaticamente 
  
- **Intervalo de atualização de assinatura (em horas)**  
  Intervalo de atualização de assinatura do defender em horas
  
  **Padrão**: 4
  
- **Tipo de execução de conteúdo baixado por script**  
  Tipo de execução de conteúdo baixado do defender script
  
  **Padrão**: Bloquear
  
- **Impedir tipo de roubo de credencial**  
  O Windows Defender Credential Guard usa segurança baseada em virtualização para isolar segredos para que somente o software de sistema privilegiado possa acessá-los. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, tal como Ataques PtH ou PtT. O Windows Defender Credential Guard impede esses ataques ao proteger os hashes de senha NTLM, tíquetes de concessão de permissão Kerberos e credenciais armazenadas por aplicativos como credenciais de domínio.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Padrão**: Ativar

- **Tipo de execução de conteúdo de email**  
  Essa regra impede que os seguintes tipos de arquivo sejam executados ou iniciados de um email visto no Microsoft Outlook ou webmail (como Gmail.com ou Outlook.com): Arquivos de script executáveis (como. exe,. dll ou. SCR) (como um arquivo PowerShell. PS, VisualBasic. vbs ou JavaScript. js).  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Padrão**: Bloquear

- **Lançamento do Adobe Reader em um processo filho**  

  **Padrão**: Ativar

- **Tipo de proteção de rede**  
  Essa política permite ativar a proteção de rede (bloquear/auditar) ou desativado no Windows Defender Exploit Guard. A proteção de rede é um recurso do Windows Defender Exploit Guard que protege os funcionários que usam qualquer aplicativo de acessar golpes de phishing, sites de Hospedagem de exploração e conteúdo mal-intencionado na Internet. Isso inclui impedir que navegadores de terceiros se conectem a sites perigosos. O tipo de valor é inteiro. Se você habilitar essa configuração, a proteção de rede será ativada e os funcionários não poderão desativá-la. Seu comportamento pode ser controlado pelas seguintes opções: Bloquear e auditar. Se você habilitar essa política com a opção "bloquear", os usuários e aplicativos serão impedidos de se conectar a domínios perigosos. Você pode ver essa atividade na central de segurança do Windows Defender. Se você habilitar essa política com a opção "auditoria", os usuários/aplicativos não serão impedidos de se conectar a domínios perigosos. No entanto, você ainda verá essa atividade na central de segurança do Windows Defender. Se você desabilitar essa política, os usuários/aplicativos não serão impedidos de se conectar a domínios perigosos. Você não verá nenhuma atividade de rede na central de segurança do Windows Defender. Se você não configurar essa política, o bloqueio de rede será desabilitado por padrão.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **Padrão**: Ativar
  
- **Dia da verificação de agenda do defender**  
  Dia da verificação de agenda do defender.
  
  **Padrão**: Todos os dias
  
- **Proteção entregue na nuvem**  
  Para proteger melhor seu PC, o Windows Defender enviará informações à Microsoft sobre quaisquer problemas encontrados. A Microsoft analisará essas informações, aprenderá mais sobre problemas que afetam você e outros clientes, além de oferecer soluções aprimoradas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Padrão**:  Sim  

- **Ação de aplicativo potencialmente indesejado defender**  
  O recurso de proteção de aplicativo potencialmente indesejado (PUA) no Windows Defender antivírus pode identificar e bloquear o download e a instalação do PUAs em pontos de extremidade em sua rede. Esses aplicativos não são considerados vírus, malware ou outros tipos de ameaças, mas podem executar ações em pontos de extremidade que afetam negativamente o desempenho ou o uso. O PUA também pode se referir a aplicativos que são considerados uma má reputação. O comportamento típico do PUA inclui: Vários tipos de injeção de anúncios de agrupamento de software em navegadores da Web driver e otimizadores de registro que detectam problemas, solicitam o pagamento para corrigir os erros, mas permanecem no ponto de extremidade e não fazem alterações ou otimizações (também conhecidas como programas "antivírus não autorizados"). Esses aplicativos podem aumentar o risco de sua rede ser infectada com malware, fazer com que as infecções de malware sejam mais difíceis de identificar e podem desperdiçar recursos de ti para limpar os aplicativos.  
  [Saiba mais](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Padrão**: Bloquear  

- **Script de tipo de código de macro ofuscado**  
  Malware e outras ameaças podem tentar ofuscar ou ocultar seu código mal-intencionado em alguns arquivos de script. Essa regra impede que os scripts que parecem estar ofuscados sejam executados.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Padrão**: Bloquear
  
- **Verificar unidades removíveis durante uma verificação completa**  
  Permite que o Windows Defender Verifique se há software mal-intencionado e indesejado em unidades removíveis (por exemplo, unidades flash) durante uma verificação completa. O Windows Defender antivírus examina todos os arquivos em dispositivos USB antes da execução.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Padrão**: Sim  
  
- **Analisar ficheiros de arquivo**  
  Defender verificar arquivos mortos.
  
  **Padrão**: Sim
  
- **Monitoramento de comportamento**  
  Permite ou não a funcionalidade de monitoramento de comportamento do Windows Defender. Inserido no Windows 10, esses sensores coletam e processam sinais comportamentais do sistema operacional e enviam esses dados de sensor para sua instância privada, isolada e de nuvem do Microsoft defender ATP.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Padrão**: Sim

- **Verificar arquivos abertos de pastas de rede**  
  Se os arquivos forem somente leitura, o usuário não poderá remover nenhum malware detectado.
  
  **Padrão**: Sim

- **Tipo de processo USB não confiável**  
  Com essa regra, os administradores podem impedir que arquivos executáveis não assinados ou não confiáveis sejam executados a partir de unidades removíveis USB, incluindo cartões SD.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Padrão**: Bloquear
  
- **Outro tipo de injeção de processo de aplicativos do Office**  
  Os aplicativos do Office, incluindo o Word, o Excel, o PowerPoint e o OneNote, não poderão injetar código em outros processos. Normalmente, isso é usado por malware para executar código mal-intencionado em uma tentativa de ocultar a atividade de mecanismos de verificação antivírus.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Padrão**:  Bloquear
  
- **Código de macro do Office permitir tipo de importações do Win32**  
  O malware pode usar o código de macro em arquivos do Office para importar e carregar as DLLs do Win32, que podem ser usadas para fazer chamadas à API para permitir uma infecção adicional em todo o sistema. Essa regra tenta bloquear os arquivos do Office que contêm o código de macro que é capaz de importar as DLLs do Win32. Isso inclui o Word, o Excel, o PowerPoint e o OneNote.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Padrão**: Bloquear  
  
- **Nível de bloco do defender Cloud**  
  Nível de bloco do defender Cloud.
  
  **Padrão**: Não Configurado

- **Monitoramento em tempo real**  
  O defender requer monitoramento em tempo real.
  
  **Padrão**: Sim
 
- **Aplicativos de comunicação do Office são iniciados em um processo filho**  

  **Padrão**:  Ativar

- **Criação de conteúdo executável de aplicativos do Office ou tipo de inicialização**  
  Essa regra destina-se a comportamentos típicos usados por Complementos suspeitos e mal-intencionados e scripts (extensões) que criam ou iniciam arquivos executáveis. Essa é uma técnica típica de malware. As extensões são impedidas de serem usadas pelos aplicativos do Office. Normalmente, essas extensões usam o Windows Scripting Host (arquivos. WSH) para executar scripts que automatizam determinadas tarefas ou fornecem recursos de complemento criados pelo usuário.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Padrão**: Bloquear

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender  
Para obter mais informações, consulte [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) na documentação de protocolos do Windows.  

- **Domínio do perfil de firewall**  
  Especifica os perfis aos quais a regra pertence: Domínio, privado, público. Esse valor representa o perfil para redes que estão conectadas a domínios.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Conexões de entrada bloqueadas**  
    **Padrão**: Sim

  - **Conexões de saída necessárias**  
    **Padrão**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Firewall habilitado**  
    **Padrão**: Permitido

- **Perfil de firewall público**  
  Especifica os perfis aos quais a regra pertence: Domínio, privado, público. Esse valor representa o perfil para redes públicas. Essas redes são classificadas como públicas pelos administradores no host do servidor. A classificação ocorre na primeira vez que o host se conecta à rede. Normalmente, essas redes são os aeroportos, cafeterias e outros locais públicos em que os colegas na rede ou o administrador de rede não são confiáveis.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Conexões de entrada bloqueadas**  
    **Padrão**: Sim

  - **Conexões de saída necessárias**  
    **Padrão**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Firewall habilitado**  
    **Padrão**: Permitido

  - **Regras de segurança de conexão da política de grupo não mescladas**  
    **Padrão**: Sim

  - **Regras de política da política de grupo não mesclada**  
    **Padrão**: Sim

- **Perfil de firewall privado**  
  Especifica os perfis aos quais a regra pertence: Domínio, privado, público. Esse valor representa o perfil para redes privadas.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Conexões de entrada bloqueadas**  
    **Padrão**: Sim

  - **Conexões de saída necessárias**  
    **Padrão**: Sim 

  - **Notificações de entrada bloqueadas**  
    **Padrão**: Sim

  - **Firewall habilitado**  
    **Padrão**: Permitido

## <a name="windows-hello-for-business"></a>Windows Hello para Empresas  
- **Exigir antifalsificação avançada, quando disponível**  
  Em caso afirmativo, os dispositivos usarão antifalsificação avançada, quando disponível. Se não, a antifalsificação será bloqueada. Não configurado respeitará as configurações feitas no cliente.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Padrão**: Sim

- **Configurar o Windows Hello para empresas**   
    O Windows Hello para empresas é um método alternativo para entrar no Windows, substituindo senhas, cartões inteligentes e cartões inteligentes virtuais.  

  - Quando definido como *Sim*, você habilita essa política e o dispositivo provisiona o Windows Hello para empresas.  
  - Quando definido como *não configurado*, a linha de base não afeta a configuração de política do dispositivo. Isso significa que, se o Windows Hello para empresas estiver desabilitado em um dispositivo, ele permanecerá desabilitado. Se estiver habilitado, ele permanecerá habilitado. 

  Não é possível desabilitar o Windows Hello para empresas por meio desta linha de base. Você pode desabilitar o Windows Hello para empresas ao configurar o [registro do Windows](windows-hello.md)ou como parte de um perfil de configuração do dispositivo para a proteção de [identidade](identity-protection-configure.md).  

  **Padrão**: Sim

- **Exigir letras minúsculas no PIN**  
  Se necessário, o PIN do usuário deve incluir pelo menos uma letra minúscula.

  **Padrão**: Permitido

- **Exigir caracteres especiais no PIN**  
  Se necessário, o PIN do usuário deve incluir pelo menos um caractere especial.

  **Padrão**: Permitido

- **Comprimento mínimo do PIN**  
  O comprimento mínimo do PIN deve estar entre 4 e 127.

  **Padrão**: 6

- **Exigir letras maiúsculas no PIN**  
  Se necessário, o PIN do usuário deve incluir pelo menos uma letra maiúscula.

  **Padrão**: Permitido

## <a name="windows-ink-workspace"></a>Espaço de trabalho do Windows Ink  
Para obter mais informações, consulte [Policy CSP-WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) na documentação do Windows.  

- **Espaço de trabalho de tinta**  
  Especifica se deve permitir que o usuário acesse o espaço de trabalho de tinta. 
  - *Desabilitado* -o acesso ao espaço de trabalho de tinta está desabilitado. O recurso está desativado.
  - *Habilitado* – o recurso de espaço de trabalho de tinta está ativado, mas o usuário não pode acessá-lo acima da tela de bloqueio.
  - *Não configurado* -o recurso de espaço de trabalho de tinta está ativado e o usuário pode usá-lo acima da tela de bloqueio.  

  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Padrão**: Enabled
 
## <a name="windows-powershell"></a>Windows PowerShell  
Para obter mais informações, consulte [Policy CSP-WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) na documentação do Windows.  

- **Log do bloco de script do shell do Power Shell**  
  Essa configuração de política habilita o log de todas as entradas de script do PowerShell para o log de eventos Microsoft-Windows-PowerShell/Operational. Se você habilitar essa configuração de política, o Windows PowerShell registrará em log o processamento de comandos, blocos de script, funções e scripts – sejam invocados interativamente ou através da automação. Se você desabilitar essa configuração de política, o log da entrada de script do PowerShell será desabilitado. Se você habilitar o log de invocação de bloco de script, o PowerShell também registrará eventos quando a invocação de um comando, bloco de script, função ou script iniciar ou parar. Habilitar o log de invocação gera um alto volume de logs de eventos. Nota: Essa configuração de política existe sob configuração do computador e configuração do usuário no editor de Política de Grupo. A configuração da política de configuração do computador tem precedência sobre a configuração de política de configuração de usuário.  
  [Saiba mais](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Padrão**: Enabled

## <a name="whats-changed-in-the-new-template"></a>O que mudou no novo modelo
A *linha de base de segurança do MDM para o modelo 2019 de maio* tem as seguintes alterações do modelo de *Visualização* .

### <a name="changes-to-the-baseline-settings"></a>Alterações nas configurações de linha de base
As seguintes configurações são:
- *Novo* nesta versão mais recente da linha de base.
- *Removido* desta versão de linha de base mais recente, mas estava presente na versão anterior.
- Revisado de alguma forma de como as configurações apareciam na versão anterior. 

*[Novo]* [**acima do bloqueio**](#above-lock):
- **Ativar voz de aplicativos da tela bloqueada**    

*[Novo]* [**Gerenciamento de aplicativos**](#application-management): 
- **Bloquear o controle do usuário sobre instalações**  
- **Bloquear instalações de aplicativos MSI com privilégios elevados**  

*[Removido]* [**BitLocker**](#bitlocker):  
- Política de unidade removível do armário de bits > **método de criptografia**
- **Política de unidade fixa do armário de bits** *(todas as configurações)*
- **Política de unidade do sistema do armário de bits** *(todas as configurações)*

*[Novo]* [**conectividade**](#connectivity):
- **Configurar o acesso seguro a caminhos UNC**

*[Novo]* [**proteção do dispositivo**](#device-guard):
- **Segurança baseada em virtualização**


*[Novo]* [**proteção de DMA**](#dma-guard):
- **Enumeração de dispositivos externos incompatíveis com a proteção de kernel DMA**  

*[Novo]* [**Internet Explorer**](#internet-explorer):
- **Atualizações de zona da Internet do Explorer na barra de status por meio de script**
- **Arrastar e soltar na zona Internet do Internet Explorer ou copiar e colar arquivos**  
- **Componentes dependentes .NET Framework zona restrita do Internet Explorer**  
- **A zona do computador local do Internet Explorer não executa antimalware em controles ativos X**
- **Suporte à criptografia do Internet Explorer**  

*[Revisado]* [**Internet Explorer**](#internet-explorer):
- **Prompt automático da zona Internet do Internet Explorer para downloads de arquivo** > o valorpadrão agora está desabilitado. Em visualização, isso foi definido como habilitado.

*[Novo]* [**assistência remota**](#remote-assistance):  
- **Assistência remota solicitada** 
  - **Permissão de assistência remota solicitada**
  - **Valor de tempo máximo de tíquete**  
  - **Período de tempo máximo de tíquete**  
  - **Método de convite por email**


*[New]* [**WIndows Defender**](#windows-defender):
- **Lançamento do Adobe Reader em um processo filho**  
- **Aplicativos de comunicação do Office são iniciados em um processo filho** 

*[Novo]* [ **Windows Defender firewall**](#windows-defender-firewall)
- **Domínio do perfil de firewall**  
  - **Conexões de entrada bloqueadas**  
  - **Conexões de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall habilitado**  
- **Perfil de firewall público**  
  - **Conexões de entrada bloqueadas**  
  - **Conexões de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall habilitado** 
  - **Regras de segurança de conexão da política de grupo não mescladas**   
  - **Regras de política da política de grupo não mesclada**  
- **Perfil de firewall privado**  
  - **Conexões de entrada bloqueadas**  
  - **Conexões de saída necessárias**  
  - **Notificações de entrada bloqueadas**  
  - **Firewall habilitado**  

*[Novo]* [**Windows Hello para empresas**](#windows-hello-for-business):  
- **Exigir antifalsificação avançada, quando disponível**  
- **Configurar o Windows Hello para empresas**  
- **Exigir letras minúsculas no PIN** 
- **Exigir caracteres especiais no PIN** 
- **Comprimento mínimo do PIN**  
- **Exigir letras maiúsculas no PIN** 



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
