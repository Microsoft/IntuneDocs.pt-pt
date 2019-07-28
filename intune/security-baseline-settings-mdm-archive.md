---
title: Arquivo-de configurações de linhas de base de segurança do MDM do Intune para Windows 10
titleSuffix: Microsoft Intune
description: Arquivo de versões de lançamento anteriores das configurações de linha de base de segurança do MDM para gerenciar o Windows 10 com o Microsoft Intune
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 220327c48712881e57efa1a91b9d00a64ba3e0be
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884691"
---
<!-- This article contains the exact baseline details for baseline versions that were previously published in security-baseline-settings-mdm.md.  -->

# <a name="archive-of-mdm-security-baseline-settings"></a>Arquivo morto das configurações de linha de base de segurança do MDM  

Exibir detalhes das versões arquivadas da linha de base de segurança do MDM para o Intune.  

Quando uma nova linha de base de segurança do MDM é liberada, a lista anterior de configurações é movida do artigo configurações de linha de base de segurança para este arquivo morto. Essas versões ainda têm suporte para uso, e esse arquivo é fornecido para auxiliar na compreensão das configurações padrão para versões de linha de base mais antigas.

Quando uma versão de linha de base não tiver mais suporte para uso, ela será então removida deste artigo.

- Exibir as configurações que estão disponíveis na [linha de base de segurança do MDM atual](security-baseline-settings-mdm.md) 
- Saiba mais sobre [linhas de base de segurança](security-baselines.md)e como atualizar a versão de linha de base em seus perfis de linha de base de segurança.

## <a name="preview-mdm-security-baseline-for-october-2018"></a>Visualizar: Linha de base de segurança do MDM para outubro de 2018  

*Essa linha de base é substituída pela [linha de base de segurança do MDM para Spring 2019 (19H1)](security-baseline-settings-mdm.md)*

### <a name="above-lock"></a>Acima do bloqueio  

Para obter mais informações, consulte [Policy CSP-AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) na documentação do Windows.  

- **Bloquear a exibição de notificações do sistema**  
  Essa configuração de política permite impedir que as notificações do aplicativo apareçam na tela de bloqueio. Se você habilitar essa configuração de política, nenhuma notificação de aplicativo será exibida na tela de bloqueio. Se você desabilitar ou não definir essa configuração de política, os usuários poderão escolher quais aplicativos exibem notificações na tela de bloqueio.
  
  **Padrão**: Sim  

### <a name="app-runtime"></a>Tempo de execução do aplicativo  

Para obter mais informações, [consulte Policy CSP-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) AppRuntime na documentação do Windows.  

- **Contas da Microsoft opcionais para aplicativos da Windows Store**  
  Essa configuração de política permite controlar se as contas da Microsoft são opcionais para aplicativos da Windows Store que exigem uma conta para entrar. Essa política afeta apenas os aplicativos da Windows Store que dão suporte a ela. Se você habilitar essa configuração de política, os aplicativos da Windows Store que normalmente exigem um conta Microsoft de entrada permitirão que os usuários entrem com uma conta empresarial. Se você desabilitar ou não definir essa configuração de política, os usuários deverão entrar com um conta Microsoft.  
  
  **Padrão**: Enabled  

### <a name="application-management"></a>Gerenciamento de aplicativos  

Para obter mais informações, consulte [Policy CSP-ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) na documentação do Windows.  

- **Bloquear DVR de jogos (somente desktop)**  
  Configura se a gravação e a difusão de jogos são permitidas.
  
  **Padrão**: Sim  

### <a name="auto-play"></a>Reprodução automática  

Para obter mais informações, consulte [CSP da política-reprodução automática](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) na documentação do Windows.  

- **Comportamento de execução automática padrão de reprodução automática**  
  Essa configuração afeta o comportamento padrão para comandos de Autorun. Os comandos de Autorun são armazenados em arquivos autorun. inf e podem iniciar programas de instalação ou outras rotinas. Quando *habilitado*, os administradores podem alterar o comportamento padrão de Autorun em um dispositivo que executa o Windows Vista ou posterior. O comportamento pode ser definido como: a) desabilitar completamente os comandos de autorun ou b) reverter para o comportamento anterior ao Windows Vista da execução automática do comando autorun. Quando definido como *desabilitado* ou *não configurado*, os dispositivos que executam o Windows Vista ou posterior solicitam ao usuário se um comando de Autorun deve ser executado.
  
  **Padrão**: Não executar  
  
- **Modo de reprodução automática**  
  Essa configuração de política permite que você desative o recurso de reprodução automática. A reprodução automática começa a ler a partir de uma unidade assim que você insere a mídia na unidade. Como resultado, o arquivo de instalação de programas e a música em mídia de áudio são iniciados imediatamente. Antes do Windows XP SP2, a reprodução automática é desabilitada por padrão em unidades removíveis, como a unidade de disquete (mas não a unidade de CD-ROM) e em unidades de rede. A partir do Windows XP SP2, a reprodução automática é habilitada para unidades removíveis também, incluindo unidades zip e alguns dispositivos de armazenamento em massa USB. Se você habilitar essa configuração de política, a reprodução automática será desabilitada em unidades de CD-ROM e de mídia removível ou desabilitada em todas as unidades. Essa configuração de política desabilita a reprodução automática em tipos de unidades adicionais. Você não pode usar essa configuração para habilitar a reprodução automática em unidades nas quais ela está desabilitada por padrão. Se você desabilitar ou não definir essa configuração de política, a reprodução automática será habilitada. Nota: Essa configuração de política aparece nas pastas configuração do computador e configuração do usuário. Se as configurações de política entrarem em conflito, a configuração de política na configuração do computador terá precedência sobre a configuração de política na configuração do usuário.
  
  **Padrão**: Desativado

- **Bloquear reprodução automática para dispositivos que não são de volume**  
  Essa configuração de política não permite a reprodução automática de dispositivos MTP, como câmeras ou telefones. Se você habilitar essa configuração de política, a reprodução automática não será permitida para dispositivos MTP, como câmeras ou telefones. Se você desabilitar ou não definir essa configuração de política, a reprodução automática será habilitada para dispositivos que não são de volume.
  
  **Padrão**: Enabled  

### <a name="bitlocker"></a>Pelo  

Para obter mais informações, [consulte CSP de política](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) -BitLocker na documentação do Windows.  

- **Política de unidade removível do armário de bits**  
  Essa configuração de política é usada para controlar o método de criptografia e a intensidade de codificação. Os valores dessa política determinam a força da codificação que o BitLocker usa para criptografia. As empresas podem querer controlar o nível de criptografia para aumentar a segurança (o AES-256 é mais seguro do que o AES-128). Se você habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada.

  Para política de unidade removível de armário de bits, defina as seguintes configurações:

  - **Exigir criptografia para acesso de gravação**  
    **Padrão**: Sim  

  - **Método de criptografia**  
    **Padrão**: CBC 256bit do AES  

- **Política de unidade fixa do armário de bits**  
  Essa configuração de política é usada para controlar o método de criptografia e a intensidade de codificação. Os valores dessa política determinam a força da codificação que o BitLocker usa para criptografia. As empresas podem querer controlar o nível de criptografia para aumentar a segurança (o AES-256 é mais seguro do que o AES-128). Se você habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada.  
 
  Para política de unidade fixa do armário de bits, defina as seguintes configurações: 
  - **Método de criptografia**  
    **Padrão**: XTS 256bit AES  

- **Política de unidade do sistema do armário de bits**  
  Essa configuração de política é usada para controlar o método de criptografia e a intensidade de codificação. Os valores dessa política determinam a força da codificação que o BitLocker usa para criptografia. As empresas podem querer controlar o nível de criptografia para aumentar a segurança (o AES-256 é mais seguro do que o AES-128). Se você habilitar essa configuração, poderá configurar um algoritmo de criptografia e a intensidade de codificação de chave para unidades de dados fixas, unidades do sistema operacional e unidades de dados removíveis individualmente. Para unidades fixas e do sistema operacional, recomendamos que você use o algoritmo XTS-AES. Para unidades removíveis, você deve usar AES-CBC 128-bit ou AES-CBC 256-bit se a unidade for usada em outros dispositivos que não estão executando o Windows 10, versão 1511 ou posterior. A alteração do método de criptografia não terá efeito se a unidade já estiver criptografada ou se a criptografia estiver em andamento. Nesses casos, essa configuração de política é ignorada.  

  Para a política de unidade do sistema do armário de bits, defina as seguintes configurações:
  - **Método de criptografia**  
    **Padrão**: XTS 256bit AES  

### <a name="browser"></a>Browser  

Para obter mais informações, consulte [Policy CSP-browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) na documentação do Windows.  

- **Exigir SmartScreen para o Microsoft Edge**  

  O Microsoft Edge usa o Windows Defender SmartScreen (ativado) para proteger os usuários contra possíveis golpes de phishing e softwares mal-intencionados por padrão. Além disso, por padrão, os usuários não podem desabilitar (desligar) o Windows Defender SmartScreen. Habilitar essa política desativa o Windows Defender SmartScreen e impede que os usuários o liguem. Não configure essa política para permitir que os usuários optem por ativar ou desativar o Windows Defender SmartScreen.  
  
  **Padrão**: Sim  
  
- **Bloquear acesso a sites mal-intencionados**  

  Por padrão, o Microsoft Edge permite que os usuários ignorem (ignoram) os avisos do Windows Defender SmartScreen sobre sites potencialmente mal-intencionados, permitindo que eles continuem no site. Com essa política, no entanto, você pode configurar o Microsoft Edge para impedir que os usuários ignorem os avisos, bloqueando-os de continuar para o site.
  
  **Padrão**: Sim  
  
- **Bloquear download de arquivo não verificado** Por padrão, o Microsoft Edge permite que os usuários ignorem (ignoram) os avisos do Windows Defender SmartScreen sobre arquivos potencialmente mal-intencionados, permitindo que eles continuem baixando os arquivos não verificados. Habilitar essa política impede que os usuários ignorem os avisos, bloqueando-os do download dos arquivos não verificados.
  
  **Padrão**: Sim  
  
- **Bloquear Gerenciador de senhas**  
  Por padrão, o Microsoft Edge usa o Gerenciador de senhas automaticamente, permitindo que os usuários gerenciadorem senhas localmente. Desabilitar essa política restringe o Microsoft Edge de usar o Gerenciador de senhas. Não configure essa política se desejar permitir que os usuários escolham salvar e gerenciar senhas localmente usando o Gerenciador de senhas.
  
  **Padrão**: Sim  
  
- **Impedir substituições de erro de certificado**  
  Essa configuração de política impede que o usuário ignore erros de certificado de protocolo SSL/TLS (segurança de camada de transporte) que interrompem a navegação (como erros "expirados", "revogados" ou "incompatibilidade de nome") no Internet Explorer. Se você habilitar essa configuração de política, o usuário não poderá continuar a navegação. Se você desabilitar ou não definir essa configuração de política, o usuário poderá optar por ignorar os erros de certificado e continuar a navegação.
  
  **Padrão**: Sim  

### <a name="connectivity"></a>Conectividade  

Para obter mais informações, consulte [CSP da política-conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) na documentação do Windows.  

- **Bloquear o download da Internet para publicação na Web e assistentes de ordenação online**  
  Essa configuração de política especifica se o Windows deve baixar uma lista de provedores para os assistentes de publicação na Web e de ordenação online. Esses assistentes permitem que os usuários selecionem em uma lista de empresas que fornecem serviços como armazenamento online e impressão fotográfica. Por padrão, o Windows exibe os provedores baixados de um site do Windows, além dos provedores especificados no registro. Se você habilitar essa configuração de política, o Windows não baixará os provedores e somente os provedores de serviço armazenados em cache na exibição do Registro local. Se você desabilitar ou não definir essa configuração de política, uma lista de provedores será baixada quando o usuário usar os assistentes de publicação na Web ou de ordenação online. Para obter mais informações que incluem detalhes sobre como especificar provedores de serviço no registro, consulte a documentação para os assistentes de publicação na Web e ordenação online.  
  
  **Padrão**: Enabled  

- **Bloquear o download de drivers de impressão via HTTP**  
  Essa configuração de política especifica se deve permitir que este cliente baixe pacotes de driver de impressão via HTTP. Para configurar a impressão HTTP, os drivers que não são da caixa de entrada precisam ser baixados via HTTP. Nota: Essa configuração de política não impede que o cliente imprima em impressoras na intranet ou na Internet via HTTP. Ele proíbe apenas o download de drivers que ainda não estão instalados localmente. Se você habilitar essa configuração de política, os drivers de impressão não poderão ser baixados via HTTP. Se você desabilitar ou não definir essa configuração de política, os usuários poderão baixar drivers de impressão via HTTP.
  
  **Padrão**: Enabled  

### <a name="credentials-delegation"></a>Delegação de credenciais  

Para obter mais informações, [consulte Policy CSP-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) CredentialsDelegation na documentação do Windows.  

- **Delegação de host remoto de credenciais não exportáveis**  
  O host remoto permite a delegação de credenciais não exportáveis. Ao usar a delegação de credenciais, os dispositivos fornecem uma versão exportável de credenciais para o host remoto, o que expõe os usuários ao risco de roubo de credenciais de invasores no host remoto. Se você habilitar essa configuração de política, o host oferecerá suporte ao administrador restrito ou ao modo de proteção de credencial remota. Se você desabilitar ou não definir essa configuração de política, não haverá suporte para administração restrita e modo de proteção de credencial remota. O usuário sempre precisará passar suas credenciais para o host.  

  
  **Padrão**: Enabled  

### <a name="credentials-ui"></a>IU de credenciais  

Para obter mais informações, consulte [Policy CSP-CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) na documentação do Windows.  

- **Enumerar administradores** Essa configuração de política controla se as contas de administrador são exibidas quando um usuário tenta elevar um aplicativo em execução. Por padrão, as contas de administrador não são exibidas quando o usuário tenta elevar um aplicativo em execução. Se você habilitar essa configuração de política, todas as contas de administrador local no PC são exibidas para que o usuário possa escolher uma e digitar a senha correta. Se você desabilitar essa configuração de política, os usuários sempre precisarão digitar um nome de usuário e senha para elevar.  

  
  **Padrão**: Desativado  

### <a name="data-protection"></a>Proteção de dados  

Para obter mais informações, [consulte CSP de política-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) dataprotection na documentação do Windows.  

- **Bloquear o acesso direto à memória**  
  Essa configuração de política permite bloquear o DMA (acesso direto à memória) para todas as portas de downstream PCI conectadas a quente até que um usuário faça logon no Windows. Quando um usuário fizer logon, o Windows enumerará os dispositivos PCI conectados às portas PCI plug-host. Toda vez que o usuário bloqueia a máquina, o DMA é bloqueado em portas PCI de plugue a quente sem dispositivos filhos até que o usuário faça logon novamente. Os dispositivos que já foram enumerados quando o computador foi desbloqueado continuarão funcionando até serem desconectados. Essa configuração de política só é imposta quando o BitLocker ou a criptografia de dispositivo está habilitada.
  
  
  **Padrão**: Sim  

### <a name="device-guard"></a>Proteção do dispositivo  

Para obter mais informações, [consulte Policy CSP-](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) DeviceGuard na documentação do Windows.  

- **Proteção de credenciais**  
  Essa configuração permite que os usuários ativem o Credential Guard com segurança baseada em virtualização para ajudar a proteger as credenciais na próxima reinicialização.
   
  **Padrão**: Habilitar com bloqueio de UEFI 

- **Habilitar a segurança baseada em virtualização**  </br>
  Ativa a VBS (segurança baseada em virtualização) na próxima reinicialização. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.
  
  **Padrão**: Sim  

- **Iniciar o System Guard**    
  **Padrão**: Enabled  

### <a name="device-installation"></a>Instalação do dispositivo  

Para obter mais informações, consulte [Policy CSP-DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) na documentação do Windows.  

- **Instalação de dispositivo de hardware por identificadores de dispositivo**  
  Essa configuração de política permite especificar uma lista de Plug and Play IDs de hardware e IDs compatíveis para dispositivos que o Windows é impedido de instalar. Essa configuração de política tem precedência sobre qualquer outra configuração de diretiva que permita que o Windows instale um dispositivo. Se você habilitar essa configuração de política, o Windows será impedido de instalar um dispositivo cuja ID de hardware ou ID compatível apareça na lista que você criar. Se você habilitar essa configuração de política em um servidor de área de trabalho remota, a configuração de política afetará o redirecionamento dos dispositivos especificados de um cliente de área de trabalho remota para o servidor de área de trabalho remota. Se você desabilitar ou não definir essa configuração de política, os dispositivos poderão instalar e atualizar conforme permitido ou impedido por outras configurações de política.
  
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
  
  **Padrão**: Bloquear a instalação do dispositivo de hardware  

  Quando *Bloquear instalação de dispositivo de hardware* estiver selecionado, as configurações a seguir estarão disponíveis.
  - **Remover dispositivos de hardware correspondentes**    
  Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por classes de instalação* está definida para *bloquear a instalação do dispositivo de hardware*.  

    **Padrão**: *Nenhuma configuração padrão*  

  - **Identificadores de dispositivo de hardware que são bloqueados**  
    Essa configuração está disponível somente quando *a instalação do dispositivo de hardware por classes de instalação* está definida para *bloquear a instalação do dispositivo de hardware*.
    
    **Padrão**: *Nenhuma configuração padrão*  

### <a name="device-lock"></a>Bloqueio de dispositivo  

Para obter mais informações, consulte [Policy CSP-DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) na documentação do Windows.  

- **Impedir o uso da câmera**  
  Desabilita a opção de alternância da câmera da tela de bloqueio em configurações do PC e impede que uma câmera seja invocada na tela de bloqueio. Por padrão, os usuários podem habilitar a invocação de uma câmera disponível na tela de bloqueio. Se você habilitar essa configuração, os usuários não poderão mais habilitar ou desabilitar o acesso à câmera da tela de bloqueio nas configurações do PC e a câmera não poderá ser invocada na tela de bloqueio. 
  
  **Padrão**: Enabled  

- **Exigir senha**  
  Especifica se o bloqueio de dispositivo está habilitado.
  
  **Padrão**: Sim  
  
  Quando *exigir senha* estiver definido como *Sim*, as configurações a seguir estarão disponíveis.

  - **Contagem de conjunto de caracteres mínimo de senha**  
    O número de tipos de elementos complexos (letras maiúsculas e minúsculas, números e pontuação) necessários para um PIN ou senha forte. O PIN impõe o seguinte comportamento para dispositivos móveis e de desktop: 1-dígitos somente dois dígitos e letras minúsculas são necessários três dígitos, letras minúsculas e letras maiúsculas são necessárias. Sem suporte em contas da Microsoft da área de trabalho e contas de domínio. 4-dígitos, letras minúsculas, letras maiúsculas e caracteres especiais são necessários. Sem suporte na área de trabalho. O valor predefinido é 1. 
    
    **Padrão**: 3  
  
  - **Número de falhas de início de sessão antes de eliminar os dados do dispositivo**  
    O número de falhas de autenticação permitidas antes que o dispositivo seja apagado. Um valor de 0 desabilita A funcionalidade de apagamento do dispositivo.
    
    **Padrão**: 10  
  
  - **Expiração da Palavra-passe (dias)**  
    A configuração de política de duração máxima da senha determina o tempo (em dias) que uma senha pode ser usada antes que o sistema exija que o usuário a altere. Você pode definir senhas para expirar após um número de dias entre 1 e 999, ou pode especificar que as senhas nunca expirem definindo o número de dias como 0. Se a duração máxima da senha estiver entre 1 e 999 dias, a duração mínima da senha deverá ser menor que a duração máxima da senha. Se a duração máxima da senha for definida como 0, a duração mínima da senha poderá ser qualquer valor entre 0 e 998 dias.
    
    **Padrão**: 60  
  
  - **Tipo obrigatório de palavra-passe**  
    Determina o tipo de PIN ou senha necessária.
    
    **Padrão**: Alfanumérico  
  
  - **Comprimento mínimo da palavra-passe**  
    A configuração de política comprimento mínimo da senha determina o número mínimo de caracteres que podem criar uma senha para uma conta de usuário. Você pode definir um valor entre 1 e 14 caracteres ou pode estabelecer que nenhuma senha seja necessária definindo o número de caracteres como 0.
    
    **Padrão**: 8  

  - **Bloquear senhas simples**  
    Especifica se os PINs ou senhas, como "1111" ou "1234", são permitidos. Para a área de trabalho, ele também controla o uso de senhas de imagem.
    
    **Padrão**: Sim  
      *Uma configuração de Sim impede o uso de senhas simples.* 

  - **Impedir a reutilização de palavras-passe anteriores**  
    Especifica quantas senhas podem ser armazenadas no histórico que não podem ser usadas. O valor inclui a senha atual do usuário. Por exemplo, com uma configuração de *1* , o usuário não pode reutilizar sua senha atual ao escolher uma nova senha. Uma configuração de *5* significa que um usuário não pode definir sua nova senha para sua senha atual ou com qualquer uma de suas quatro senhas anteriores.
    
    **Padrão**: 24  

- **Impedir apresentação de slides**  
  Desabilita as configurações de apresentação de slides da tela de bloqueio nas configurações do computador e impede que uma apresentação de slides seja reproduzida na tela de bloqueio. Por padrão, os usuários podem habilitar uma apresentação de slides que será executada Depois de bloquear o computador. Se você habilitar essa configuração, os usuários não poderão modificar as configurações de apresentação de slides nas configurações do PC e nenhuma apresentação de slides poderá ser iniciada.
  
    **Padrão**: Enabled  
    *Uma configuração habilitada impede que as apresentações de slides sejam executadas.* 

- **Idade mínima de senha em dias**  
  A configuração de política de duração mínima da senha determina o período de tempo (em dias) que uma senha deve ser usada antes que o usuário possa alterá-la. Você pode definir um valor entre 1 e 998 dias ou pode permitir alterações de senha imediatamente definindo o número de dias como 0. A duração mínima da senha deve ser menor que a duração máxima da senha, a menos que a duração máxima da senha seja definida como 0, indicando que as senhas nunca expirarão. Se a duração máxima da senha for definida como 0, a duração mínima da senha poderá ser definida para qualquer valor entre 0 e 998.
  
    **Padrão**: 1  

### <a name="event-log-service"></a>Serviço log de eventos  

Para obter mais informações, consulte [Policy CSP-EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) na documentação do Windows.  

- **Tamanho máximo do arquivo de log de segurança em KB**  
  Essa configuração de política especifica o tamanho máximo do arquivo de log em kilobytes. Se você habilitar essa configuração de política, poderá configurar o tamanho máximo do arquivo de log entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobytes. Se você desabilitar ou não definir essa configuração de política, o tamanho máximo do arquivo de log será definido como o valor configurado localmente. Esse valor pode ser alterado pelo administrador local usando a caixa de diálogo Propriedades do log e o padrão é 20 megabytes.
  
   **Padrão**: 196608  

- **Tamanho máximo do arquivo de log do sistema em KB**  
  Essa configuração de política especifica o tamanho máximo do arquivo de log em kilobytes. Se você habilitar essa configuração de política, poderá configurar o tamanho máximo do arquivo de log entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobytes. Se você desabilitar ou não definir essa configuração de política, o tamanho máximo do arquivo de log será definido como o valor configurado localmente. Esse valor pode ser alterado pelo administrador local usando a caixa de diálogo Propriedades do log e o padrão é 20 megabytes.
  
  **Padrão**: 32768  

- **Tamanho máximo do arquivo de log do aplicativo em KB**  
  Essa configuração de política especifica o tamanho máximo do arquivo de log em kilobytes. Se você habilitar essa configuração de política, poderá configurar o tamanho máximo do arquivo de log entre 1 megabyte (1024 quilobytes) e 2 terabytes (2147483647 quilobytes) em incrementos de kilobytes. Se você desabilitar ou não definir essa configuração de política, o tamanho máximo do arquivo de log será definido como o valor configurado localmente. Esse valor pode ser alterado pelo administrador local usando a caixa de diálogo Propriedades do log e o padrão é 20 megabytes.
  
  **Padrão**: 32768  

### <a name="experience"></a>Experiência  

Para obter mais informações, consulte [Policy CSP-Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) na documentação do Windows.  

- **Bloquear destaque do Windows**  
  Permite que os administradores de ti desativem todos os recursos do Windows Spotlight – janela destaque na tela de bloqueio, dicas do Windows, recursos do Microsoft Consumer e outros recursos relacionados.
  
  **Padrão**: Sim  

  Quando *Bloquear destaque do Windows* estiver definido como *Sim*, as configurações a seguir estarão disponíveis.
  
  - **Bloquear sugestões de terceiros no destaque do Windows**  
    Especifica se é permitido permitir sugestões de aplicativos e conteúdo de editores de software de terceiros em recursos de destaque do Windows, como o destaque da tela de bloqueio, aplicativos sugeridos no menu iniciar e dicas do Windows. Os usuários ainda podem ver sugestões para recursos, aplicativos e serviços da Microsoft.
      
    **Padrão**: Sim  
  - **Bloquear recursos específicos do consumidor**  
    Permite que os administradores de ti ativem experiências que normalmente são apenas para consumidores, como sugestões de início, notificações de associação, instalação de aplicativo post-OOBE e blocos de redirecionamento.
    
    **Padrão**: Sim  


### <a name="exploit-guard"></a>Exploit Guard  

Para obter mais informações, consulte [Policy CSP-ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) na documentação do Windows.  

- **Exploração de XML de proteção**  
  Permite que o administrador de ti envie uma configuração que represente as opções de mitigação de aplicativo e sistema desejadas para todos os dispositivos na organização. A configuração é representada por um XML. A proteção contra explorações ajuda a proteger dispositivos contra malware que usam explorações para disseminar e infectar. Você usa o aplicativo de segurança do Windows ou o PowerShell para criar um conjunto de atenuações (conhecido como uma configuração). Você pode exportar essa configuração como um arquivo XML e compartilhá-la com vários computadores na sua rede para que todos tenham o mesmo conjunto de configurações de mitigação. Você também pode converter e importar um arquivo XML de configuração do EMET existente em um XML de configuração do Exploit Protection.
  
  **Padrão**: *O XML de exemplo é fornecido* 
 
### <a name="file-explorer"></a>Explorador de Ficheiros  

Para obter mais informações, consulte [CSP de política – FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) na documentação do Windows.  

- **Bloquear a prevenção de execução de dados**  
  Desabilitar a prevenção de execução de dados pode permitir que determinados aplicativos de plug-in herdados funcionem sem encerrar o Explorer.
  
  **Padrão**: Desativado  
   
- **Bloquear terminação de heap ao corromper**  
  Desabilitar a terminação de heap na corrupção pode permitir que determinados aplicativos de plug-in herdados funcionem sem encerrar o Explorer imediatamente, embora o Explorer ainda possa ser encerrado inesperadamente mais tarde.
  
  **Padrão**: Desativado  
    

### <a name="internet-explorer"></a>Internet Explorer  

Para obter mais informações, consulte [CSP da política-InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) na documentação do Windows.  

- **Acesso à zona da Internet do Internet Explorer a fontes de dados**  
  Essa configuração de política permite que você gerencie se o Internet Explorer pode acessar dados de outra zona de segurança usando o Microsoft XML Parser (MSXML) ou o ActiveX Data Objects (ADO). Se você habilitar essa configuração de política, os usuários poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que uma página seja carregada na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você desabilitar essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você não definir essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona.
  
  **Padrão**: Desativar  
  
- **Conteúdo de arrastar zona restrita do Internet Explorer de diferentes domínios no Windows**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários não podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa configuração de política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem na mesma janela. Os usuários não podem alterar essa configuração na caixa de diálogo Opções da Internet.
  
  **Padrão**: Desativado
  
- **Aviso de incompatibilidade de endereço de certificado do Internet Explorer**  
  Essa configuração de política permite ativar o aviso de segurança de incompatibilidade de endereço de certificado. Quando essa configuração de política está ativada, o usuário é avisado ao visitar sites HTTP seguros (HTTPS) que apresentam certificados emitidos para um endereço de site diferente. Esse aviso ajuda a evitar ataques de falsificação. Se você habilitar essa configuração de política, o aviso de incompatibilidade de endereço de certificado sempre aparecerá. Se você desabilitar ou não definir essa configuração de política, o usuário poderá escolher se o aviso de incompatibilidade de endereço de certificado aparecerá (usando a página avançado no painel de controle da Internet).
  
  **Padrão**: Enabled 
  
- **Sites com menos privilégios de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se sites de zonas com menos privilégios, como sites da Internet, podem navegar nessa zona. Se você habilitar essa configuração de política, os sites de zonas com menos privilégios poderão abrir novas janelas no ou navegar até essa zona. A zona de segurança será executada sem a camada adicional de segurança fornecida pelo recurso de segurança proteção contra elevação de zona. Se você selecionar prompt na caixa suspensa, um aviso será emitido para o usuário que a navegação potencialmente arriscada está prestes a ocorrer. Se você desabilitar essa configuração de política, a navegação possivelmente prejudicial será impedida. O recurso de segurança do Internet Explorer está ativado nessa zona como definido pelo controle de recurso de elevação de zona. Se você não definir essa configuração de política, as navegações possivelmente prejudiciais serão impedidas. O recurso de segurança do Internet Explorer está ativado nessa zona como definido pelo controle de recurso de elevação de zona.
  
  **Padrão**: Desativar  
  
- **Prompt automático de zona restrita do Internet Explorer para downloads de arquivo**  
  Essa configuração de política determina se os usuários são solicitados a fornecer downloads de arquivos não iniciados pelo usuário. Independentemente dessa configuração, os usuários receberão caixas de diálogo de download de arquivo para downloads iniciados pelo usuário. Se você habilitar essa configuração, os usuários receberão uma caixa de diálogo de download de arquivo para tentativas de download automática. Se você desabilitar ou não definir essa configuração, os downloads de arquivos que não forem iniciados pelo usuário serão bloqueados e os usuários verão a barra de notificação, em vez da caixa de diálogo de download de arquivo. Os usuários podem clicar na barra de notificação para permitir o prompt de download de arquivo.
  
  **Padrão**: Desativado
  
- **Componentes dependentes da Internet Internet Explorer .NET Framework**  
  Essa configuração de política permite que você gerencie se .NET Framework componentes que não estão assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados sem assinatura. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados não assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados sem assinatura. Se você não definir essa configuração de política, o Internet Explorer executará componentes gerenciados sem assinatura.
  
  **Padrão**: Desativar 
  
- **Zona Internet do Internet Explorer permite que somente domínios aprovados usem controles ActiveX TDC**  
  Essa configuração de política controla se o usuário pode executar o controle ActiveX TDC nos sites. Se você habilitar essa configuração de política, o controle ActiveX TDC não será executado de sites nesta zona. Se você desabilitar essa configuração de política, o controle ativo X TDC será executado de todos os sites nesta zona.
  
  **Padrão**: Enabled 
  
- **Windows iniciado pelo script de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie restrições em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status. Se você habilitar essa configuração de política, a segurança das restrições do Windows não será aplicada nessa zona. A zona de segurança é executada sem a camada adicional de segurança fornecida por esse recurso. Se você desabilitar essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo. Se você não definir essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluam as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo.
  
  **Padrão**: Desativado 
  
- **Zona Internet do Internet Explorer incluir caminho local ao carregar arquivos no servidor**  
  Essa configuração de política controla se as informações de caminho local são enviadas quando o usuário está carregando um arquivo por meio de um formulário HTML. Se as informações de caminho local forem enviadas, algumas informações poderão ser reveladas acidentalmente ao servidor. Por exemplo, os arquivos enviados da área de trabalho do usuário podem conter o nome de usuário como parte do caminho. Se você habilitar essa configuração de política, as informações de caminho serão enviadas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você desabilitar essa configuração de política, as informações de caminho serão removidas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você não definir essa configuração de política, o usuário poderá escolher se as informações de caminho são enviadas quando carregam um arquivo por meio de um formulário HTML. Por padrão, as informações de caminho são enviadas.
  
  **Padrão**: Desativado 
  
- **O Internet Explorer desabilita processos no modo protegido avançado**  
  Essa configuração de política determina se o Internet Explorer 11 usa processos de 64 bits (para maior segurança) ou processos de 32 bits (para maior compatibilidade) durante a execução em modo protegido aprimorado nas versões de 64 bits do Windows. Importante: Alguns controles ActiveX e barras de ferramentas podem não estar disponíveis quando são usados processos de 64 bits. Se você habilitar essa configuração de política, o Internet Explorer 11 usará os processos de guia de 64 bits ao executar no modo protegido aprimorado nas versões de 64 bits do Windows. Se você desabilitar essa configuração de política, o Internet Explorer 11 usará os processos de guia de 32 bits ao executar no modo protegido aprimorado nas versões de 64 bits do Windows. Se você não definir essa configuração de política, os usuários poderão ativar ou desativar esse recurso usando as configurações do Internet Explorer. Esse recurso está desativado por padrão.
  
  **Padrão**: Enabled 
  
- **Ignorar erros de certificado do Internet Explorer**  
  Essa configuração de política impede que o usuário ignore erros de certificado de protocolo SSL/TLS (segurança de camada de transporte) que interrompem a navegação (como erros "expirados", "revogados" ou "incompatibilidade de nome") no Internet Explorer. Se você habilitar essa configuração de política, o usuário não poderá continuar a navegação. Se você desabilitar ou não definir essa configuração de política, o usuário poderá optar por ignorar os erros de certificado e continuar a navegação.
  
  **Padrão**: Desativado 
  
- **Carregamento de zona da Internet do Internet Explorer de arquivos XAML**  
  Essa configuração de política permite que você gerencie o carregamento de arquivos de Extensible Application Markup Language (XAML). O XAML é uma linguagem de marcação declarativa baseada em XML comumente usada para criar interfaces de usuário avançadas e gráficos que aproveitam o Windows Presentation Foundation. Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, os arquivos XAML serão carregados automaticamente no Internet Explorer. O usuário não pode alterar esse comportamento. Se você definir a caixa suspensa como prompt, o usuário será solicitado a carregar arquivos XAML. Se você desabilitar essa configuração de política, os arquivos XAML não serão carregados no Internet Explorer. O usuário não pode alterar esse comportamento. Se você não definir essa configuração de política, o usuário poderá decidir se deseja carregar arquivos XAML dentro do Internet Explorer.
  
  **Padrão**: Desativar 
  
- **Prompt automático da zona Internet do Internet Explorer para downloads de arquivos**  
  Essa configuração de política determina se os usuários são solicitados a fornecer downloads de arquivos não iniciados pelo usuário. Independentemente dessa configuração, os usuários receberão caixas de diálogo de download de arquivo para downloads iniciados pelo usuário. Se você habilitar essa configuração, os usuários receberão uma caixa de diálogo de download de arquivo para tentativas de download automática. Se você desabilitar ou não definir essa configuração, os downloads de arquivos que não forem iniciados pelo usuário serão bloqueados e os usuários verão a barra de notificação, em vez da caixa de diálogo de download de arquivo. Os usuários podem clicar na barra de notificação para permitir o prompt de download de arquivo.
  
  **Padrão**: Enabled  
  
- **Aviso de segurança de zona restrita do Internet Explorer para arquivos potencialmente não seguros**  
  Essa configuração de política controla se a mensagem de "aviso de segurança de arquivo aberto" aparece quando o usuário tenta abrir arquivos executáveis ou outros arquivos potencialmente não seguros (de um compartilhamento de arquivos de intranet usando o explorador de arquivos, por exemplo). Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, esses arquivos abrirão sem um aviso de segurança. Se você definir a caixa suspensa como avisar, um aviso de segurança será exibido antes da abertura dos arquivos. Se você desabilitar essa configuração de política, esses arquivos não abrirão. Se você não definir essa configuração de política, o usuário poderá configurar como o computador lida com esses arquivos. Por padrão, esses arquivos são bloqueados na zona restrita, habilitados nas zonas da intranet e do computador local e definidos como prompt na Internet e nas zonas confiáveis.
  
  **Padrão**: Desativar  
  
- **Filtro de script entre sites da zona Internet do Internet Explorer**  
  Essa política controla se o filtro XSS (script entre sites) detectará e impedirá injeçãos de script entre sites em sites nessa zona. Se você habilitar essa configuração de política, o filtro XSS será ativado para sites nessa zona e o filtro XSS tentará bloquear as injeções de script entre sites. Se você desabilitar essa configuração de política, o filtro XSS será desativado para sites nesta zona e o Internet Explorer permitirá injeçãos de script entre sites.
  
  **Padrão**: Enabled 
  
- **Fallback do Internet Explorer para SSL3**  
  Essa configuração de política permite bloquear um fallback inseguro para SSL 3,0. Quando essa política estiver habilitada, o Internet Explorer tentará se conectar a sites usando SSL 3,0 ou inferior quando o TLS 1,0 ou superior falhar. Recomendamos que você não permita o fallback inseguro para evitar um ataque man-in-the-Middle. Essa política não afeta quais protocolos de segurança estão habilitados. Se você desabilitar essa política, os padrões do sistema serão usados.
  
  **Padrão**: Nenhum site 
  
- **Tela inteligente da zona da Internet bloqueada do Internet Explorer**  
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.
  
  **Padrão**: Enabled 
  
- **Aplicativos e arquivos de inicialização de zona restrita do Internet Explorer em um iFrame**  
  Essa configuração de política permite que você gerencie se os aplicativos podem ser executados e se os arquivos podem ser baixados de uma referência de IFRAME no HTML das páginas desta zona. Se você habilitar essa configuração de política, os usuários poderão executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de executar aplicativos e baixar arquivos de IFRAMEs nas páginas dessa zona. Se você não definir essa configuração de política, os usuários serão impedidos de executar aplicativos e baixar arquivos de IFRAMEs nas páginas dessa zona.
  
  **Padrão**: Desativar 
  
- **O Internet Explorer ignora avisos de tela inteligente sobre arquivos incomuns**  
  Essa configuração de política determina se o usuário pode ignorar avisos do filtro do SmartScreen. O filtro do SmartScreen avisa o usuário sobre arquivos executáveis que os usuários do Internet Explorer geralmente não baixam da Internet. Se você habilitar essa configuração de política, os avisos do filtro do SmartScreen bloquearão o usuário. Se você desabilitar ou não definir essa configuração de política, o usuário poderá ignorar os avisos do filtro do SmartScreen.
  
  **Padrão**: Desativado  
  
- **Bloqueador de pop-ups de zona da Internet do Internet Explorer**  
  Essa configuração de política permite que você gerencie se janelas pop-up indesejadas são exibidas. Janelas pop-up que são abertas quando o usuário final clica em um link não são bloqueadas. Se você habilitar essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida. Se você desabilitar essa configuração de política, as janelas pop-up não serão impedidas de serem exibidas. Se você não definir essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida.
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa a manipulação de MIME consistente**  
  O Internet Explorer contém comportamentos binários dinâmicos: componentes que encapsulam funcionalidades específicas para os elementos HTML aos quais eles estão anexados. Essa configuração de política controla se a configuração de restrição de segurança de comportamento binário é impedida ou permitida. Se você habilitar essa configuração de política, os comportamentos binários serão impedidos para os processos do explorador de arquivos e do Internet Explorer. Se você desabilitar essa configuração de política, comportamentos binários serão permitidos para os processos do explorador de arquivos e do Internet Explorer. Se você não definir essa configuração de política, os comportamentos binários serão impedidos para os processos do explorador de arquivos e do Internet Explorer.
  
  **Padrão**: Enabled  
  
- **Permissões Java da zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.
  
  **Padrão**: Desabilitar Java  
    
  
- **Controles do Internet Explorer Active X no modo protegido**  
  Essa configuração de política impede que os controles ActiveX sejam executados no modo protegido quando o modo protegido aprimorado está habilitado. Quando um usuário tem um controle ActiveX instalado que não é compatível com o modo protegido aprimorado e um site tenta carregar o controle, o Internet Explorer notifica o usuário e dá a opção de executar o site no modo protegido normal. Essa configuração de política desabilita essa notificação e força todos os sites a serem executados no modo protegido avançado. O modo protegido avançado fornece proteção adicional contra sites mal-intencionados usando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam pelo menos o Windows 8, o modo protegido aprimorado também limita os locais em que o Internet Explorer pode ler no registro e no sistema de arquivos. Quando o modo protegido aprimorado é habilitado e um usuário entra em um site que tenta carregar um controle ActiveX que não é compatível com o modo protegido avançado, o Internet Explorer notifica o usuário e dá a opção de desabilitar o modo protegido avançado para Esse site específico. Se você habilitar essa configuração de política, o Internet Explorer não dará ao usuário a opção de desabilitar o modo protegido avançado. Todos os sites do modo protegido serão executados no modo protegido avançado. Se você desabilitar ou não definir essa configuração de política, o Internet Explorer notificará os usuários e fornecerá uma opção para executar sites com controles ActiveX incompatíveis no modo protegido normal.  
  
  **Padrão**: Desativado  
  
- **Carregamento de zona restrita do Internet Explorer de arquivos XAML**  
  Essa configuração de política permite que você gerencie o carregamento de arquivos de Extensible Application Markup Language (XAML). O XAML é uma linguagem de marcação declarativa baseada em XML comumente usada para criar interfaces de usuário avançadas e gráficos que aproveitam o Windows Presentation Foundation. Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, os arquivos XAML serão carregados automaticamente no Internet Explorer. O usuário não pode alterar esse comportamento. Se você definir a caixa suspensa como prompt, o usuário será solicitado a carregar arquivos XAML. Se você desabilitar essa configuração de política, os arquivos XAML não serão carregados no Internet Explorer. O usuário não pode alterar esse comportamento. Se você não definir essa configuração de política, o usuário poderá decidir se deseja carregar arquivos XAML dentro do Internet Explorer.
  
  **Padrão**: Desativar  
  
- **O Internet Explorer processa restrições de segurança de janela com script**  
  O Internet Explorer permite que os scripts abram, redimensionem e reposicionem as janelas de vários tipos programaticamente. O recurso de segurança restrições de janela restringe as janelas pop-up e proíbe que os scripts exibam janelas nas quais as barras de título e status não são visíveis para o usuário ou ofuscam outras barras de título e status do Windows. Se você habilitar essa configuração de política, as janelas com script serão restringidas para todos os processos. Se você desabilitar ou não definir essa configuração de política, as janelas com script não serão restringidas.
  
  **Padrão**: Enabled   
  
- **A zona restrita do Internet Explorer executa controles e plugins do Active X**  
  Essa configuração de política permite que você gerencie se os controles ActiveX e plug-ins podem ser executados em páginas da zona especificada. Se você habilitar essa configuração de política, os controles e plug-ins poderão ser executados sem a intervenção do usuário. Se você selecionou prompt na caixa suspensa, os usuários serão solicitados a escolher se deseja permitir que os controles ou o plug-in sejam executados. Se você desabilitar essa configuração de política, os controles e plug-ins serão impedidos de serem executados. Se você não definir essa configuração de política, os controles e plug-ins serão impedidos de serem executados.
  
  **Padrão**: Desativar  
  
- **Controles Active X do script de zona restrita do Internet Explorer marcados como seguros para scripts**  
  Essa configuração de política permite que você gerencie se um controle ActiveX marcado como seguro para scripts pode interagir com um script. Se você habilitar essa configuração de política, a interação do script poderá ocorrer automaticamente sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir a interação do script. Se você desabilitar essa configuração de política, a interação do script será impedida de ocorrer. Se você não definir essa configuração de política, a interação do script será impedida de ocorrer.
  
  **Padrão**: Desativar  
  
- **Opções de logon de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie configurações para opções de entrada. Se você habilitar essa configuração de política, poderá escolher entre as seguintes opções de entrada. 
  - *Anônimo* -use a entrada anônima para desabilitar a autenticação http e usar a conta de convidado somente para o protocolo CIFS (Common Internet File System). 
  - *Prompt* -use solicitar nome de usuário e senha para consultar usuários de IDs de usuário e senhas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. 
  - *Entrada automática somente na zona da intranet* – Use esta opção para consultar usuários de IDs de usuário e senhas em outras zonas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. 
  - *Entrar automaticamente com nome de usuário e senha atuais*-Use esta opção para tentar entrar usando a resposta de desafio do Windows NT (também conhecida como autenticação NTLM). Se o servidor oferecer suporte à resposta de desafio do Windows NT, a entrada usará o nome de usuário e a senha de rede do usuário para entrar. Se o servidor não oferecer suporte à resposta de desafio do Windows NT, o usuário será consultado para fornecer o nome de usuário e a senha. 

  Se você desabilitar essa configuração de política, a entrada será definida como *logon automático somente na zona da intranet*. Se você não definir essa configuração de política, a entrada será definida para *solicitar* o nome de usuário e a senha.
  
  **Padrão**: Anónima  
  
- **Os controles de inicialização de zona confiável do Internet Explorer e script ativo X não estão marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script.
  
  **Padrão**: Desativar  
  
- **Verificação de revogação de certificado do servidor do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o Internet Explorer verificará o status de revogação dos certificados dos servidores. Os certificados são revogados quando são comprometidos ou não são mais válidos, e essa opção protege os usuários do envio de dados confidenciais para um site que pode ser fraudulento ou não seguro. Se você habilitar essa configuração de política, o Internet Explorer verificará se os certificados de servidor foram revogados. Se você desabilitar essa configuração de política, o Internet Explorer não verificará os certificados do servidor para ver se eles foram revogados. Se você não definir essa configuração de política, o Internet Explorer não verificará os certificados do servidor para ver se eles foram revogados.
  
  **Padrão**: Enabled 
  
- **Sites com menos privilégios do Internet Explorer Internet Zone**  
  Essa configuração de política permite que você gerencie se sites de zonas com menos privilégios, como sites restritos, podem navegar para essa zona. Se você habilitar essa configuração de política, os sites de zonas com menos privilégios poderão abrir novas janelas no ou navegar até essa zona. A zona de segurança será executada sem a camada adicional de segurança fornecida pelo recurso de segurança proteção contra elevação de zona. Se você selecionar prompt na caixa suspensa, um aviso será emitido para o usuário que a navegação potencialmente arriscada está prestes a ocorrer. Se você desabilitar essa configuração de política, as navegações possivelmente prejudiciais serão impedidas. O recurso de segurança do Internet Explorer está ativado nessa zona como definido pelo controle de recurso de elevação de zona. Se você não definir essa configuração de política, os sites de zonas com menos privilégios poderão abrir novas janelas no ou navegar até essa zona.
  
  **Padrão**: Desativar  
  
- **Downloads de arquivos de zona restritas do Internet Explorer**  
  Essa configuração de política permite que você gerencie se os downloads de arquivo são permitidos da zona. Essa opção é determinada pela zona da página com o link que está causando o download, não a zona da qual o arquivo é entregue. Se você habilitar essa configuração de política, os arquivos poderão ser baixados da zona. Se você desabilitar essa configuração de política, os arquivos serão impedidos de serem baixados da zona. Se você não definir essa configuração de política, os arquivos serão impedidos de serem baixados da zona.
  
  **Padrão**: Desativar  
  
- **Internet Explorer execução de Internet .NET Framework componentes dependentes assinados com Authenticode**  
  Essa configuração de política permite que você gerencie se .NET Framework componentes assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados assinados. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados. Se você não definir essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados.
  
  **Padrão**: Desativar  
  
- **O Internet Explorer impede a instalação por usuário de controles do Active X**  
  Essa configuração de política permite que você impeça a instalação de controles ActiveX por usuário. Se você habilitar essa configuração de política, os controles ActiveX não poderão ser instalados por usuário. Se você desabilitar ou não definir essa configuração de política, os controles ActiveX poderão ser instalados por usuário.
  
  **Padrão**: Enabled  
  
- **Filtro de impedimento de gerenciamento de tela inteligente do Internet Explorer**  
  Essa configuração de política impede que o usuário gerencie o Filtro SmartScreen, que avisa o usuário se o site que ele visita é conhecido por tentativas fraudulentas de coletar informações pessoais por meio de "phishing" ou é conhecido por hospedar malware. Se você habilitar essa configuração de política, o usuário não será solicitado a ativar o filtro do SmartScreen. Todos os endereços de sites que não estão na lista de permissões de filtros são enviados automaticamente à Microsoft sem avisar o usuário. Se você desabilitar ou não definir essa configuração de política, o usuário receberá uma solicitação para decidir se deseja ativar o filtro do SmartScreen durante a experiência da primeira execução.
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa o recurso de segurança de detecção de MIME**  
  Essa configuração de política determina se a detecção de MIME do Internet Explorer impedirá a promoção de um arquivo de um tipo para um tipo de arquivo mais perigoso. Se você habilitar essa configuração de política, a detecção de MIME nunca promoverá um arquivo de um tipo para um tipo de arquivo mais perigoso. Se você desabilitar essa configuração de política, os processos do Internet Explorer permitirão que uma detecção de MIME promova um arquivo de um tipo para um tipo de arquivo mais perigoso. Se você não definir essa configuração de política, a detecção de MIME nunca promoverá um arquivo de um tipo para um tipo de arquivo mais perigoso.
  
  **Padrão**: Enabled  
  
- **Controles ActiveX assinados do download de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX assinados de uma página na zona. Se você habilitar essa política, os usuários poderão baixar controles assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente. Se você desabilitar a configuração de política, os controles assinados não poderão ser baixados. Se você não definir essa configuração de política, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente.
  
  **Padrão**: Desativar  
  
- **Preenchimento automático do Internet Explorer**  
  Esse recurso de preenchimento automático pode se lembrar e sugerir nomes de usuário e senhas em formulários. Se você habilitar essa configuração, o usuário não poderá alterar "nome de usuário e senhas em formulários" ou "avisar para salvar senhas". O recurso de preenchimento automático para nomes de usuário e senhas em formulários é ativado. Você precisa decidir se deseja selecionar "avisar para salvar senhas". Se você desabilitar essa configuração, o usuário não poderá alterar "nome de usuário e senhas em formulários" ou "avisar para salvar senhas". O recurso de preenchimento automático para nomes de usuário e senhas em formulários é desativado. O usuário também não pode optar por ser solicitado a salvar senhas. Se você não definir essa configuração, o usuário terá a liberdade de ativar o preenchimento automático para nome de usuário e senhas em formulários e a opção de solicitar o salvamento de senhas. Para exibir essa opção, os usuários abrem a caixa de diálogo Opções da Internet, clicam na guia conteúdo e clicam no botão Configurações.
  
  **Padrão**: Desativar  
  
- **Internet Explorer permitir que o VBscript seja executado**  
  Essa configuração de política permite que você decida se o VBScript pode ser executado em páginas em zonas específicas do Internet Explorer. As opções incluem: 
  - *Enable* -VBScript é executado em páginas em zonas específicas, sem qualquer interação. 
  - *Prompt* -os funcionários são solicitados a permitir que o VBScript seja executado na zona. 
  - *Disable* -o VBScript é impedido de ser executado na zona. Se você desabilitar ou não definir essa configuração de política, o VBScript será executado sem nenhuma interação na zona especificada. 
  
  **Padrão**: Desativar  
  
- **Zona restrita do Internet Explorer permitir que somente domínios aprovados usem controles do ativo X TDC**  
  Essa configuração de política controla se o usuário pode executar o controle ActiveX TDC nos sites. Se você habilitar essa configuração de política, o controle ActiveX TDC não será executado de sites nesta zona. Se você desabilitar essa configuração de política, o controle ativo X TDC será executado de todos os sites nesta zona.
  
  **Padrão**: Enabled  
  
- **A zona confiável do Internet Explorer não executa antimalware em controles do Active X**  
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.
  
  **Padrão**: Desativado 
  
- **Permissões Java da zona do computador local do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como segurança média.
  
  **Padrão**: Desabilitar Java 
  
- A **zona da intranet do Internet Explorer não executa antimalware em controles do Active X** Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.
  
  **Padrão**: Desativado  

- **Zona de permissão scriptlets do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o usuário pode executar scriptlets. Se você habilitar essa configuração de política, o usuário poderá executar scriptlets. Se você desabilitar essa configuração de política, o usuário não poderá executar o scriptlets. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o scriptlets.
  
  **Padrão**: Desativado  
  
- **Barra de notificação de processos do Internet Explorer**  
  Essa configuração de política permite que você gerencie se a barra de notificação é exibida para processos do Internet Explorer quando instalações de arquivo ou código são restritas. Por padrão, a barra de notificação é exibida para processos do Internet Explorer. Se você habilitar essa configuração de política, a barra de notificação será exibida para os processos do Internet Explorer. Se você desabilitar essa configuração de política, a barra de notificação não será exibida para processos do Internet Explorer. Se você não definir essa configuração de política, a barra de notificação não será exibida para processos do Internet Explorer.
  
  **Padrão**: Enabled  
  
- **Controles ActiveX assinados do download de Internet Zone Internet Explorer**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX assinados de uma página na zona. Se você habilitar essa política, os usuários poderão baixar controles assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente. Se você desabilitar a configuração de política, os controles assinados não poderão ser baixados. Se você não definir essa configuração de política, os usuários serão consultados se deseja baixar os controles assinados por editores que não são confiáveis. O código assinado por editores confiáveis é baixado silenciosamente.
  
  **Padrão**: Desativar  
  
- **Tela inteligente da zona restrita do Internet Explorer**  
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.
  
  **Padrão**: Enabled  
  
- **Botão Remover executar este tempo do Internet Explorer para controles ativos X desatualizados**  
  Essa configuração de política permite impedir que os usuários vejam o botão "executar desta vez" e executem controles ActiveX desatualizados específicos no Internet Explorer. Se você habilitar essa configuração de política, os usuários não verão o botão "executar desta vez" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Se você desabilitar ou não definir essa configuração de política, os usuários verão o botão "executar desta vez" na mensagem de aviso que aparece quando o Internet Explorer bloqueia um controle ActiveX desatualizado. Clicar nesse botão permite que o usuário execute o controle ActiveX desatualizado uma vez. Para obter mais informações, consulte "controles ActiveX desatualizados" na biblioteca do TechNet do Internet Explorer.
  
  **Padrão**: Enabled 
  
- **Inicialização de aplicativos e arquivos de Internet do Internet Explorer em um iframe**  
  Essa configuração de política permite que você gerencie se os aplicativos podem ser executados e se os arquivos podem ser baixados de uma referência de IFRAME no HTML das páginas desta zona. Se você habilitar essa configuração de política, os usuários poderão executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de executar aplicativos e baixar arquivos de IFRAMEs nas páginas dessa zona. Se você não definir essa configuração de política, os usuários serão consultados para escolher se deseja executar aplicativos e baixar arquivos de IFRAMEs nas páginas desta zona
  
  **Padrão**: Desativar 
  
- **Zona restrita do Internet Explorer navegue por janelas e quadros entre domínios diferentes**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração.
  
  **Padrão**: Desativar  
  
- **Tela inteligente da Internet do Internet Explorer**  
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.
  
  **Padrão**: Enabled  
  
- **O Internet Explorer bloqueou as permissões de Java da zona confiável**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.
  
  **Padrão**: Desabilitar Java 
  
- **O Internet Explorer verifica as assinaturas nos programas baixados**  
  Essa configuração de política permite que você gerencie se o Internet Explorer verifica assinaturas digitais (que identifica o editor de software assinado e verifica se ele não foi modificado ou adulterado) em computadores de usuários antes de baixar programas executáveis. Se você habilitar essa configuração de política, o Internet Explorer verificará as assinaturas digitais de programas executáveis e exibirá suas identidades antes de baixá-los para os computadores dos usuários. Se você desabilitar essa configuração de política, o Internet Explorer não verificará as assinaturas digitais de programas executáveis nem exibirá suas identidades antes de baixá-los nos computadores dos usuários. Se você não configurar essa política, o Internet Explorer não verificará as assinaturas digitais de programas executáveis nem exibirá suas identidades antes de baixá-los nos computadores dos usuários.
  
  **Padrão**: Enabled  
  
- **Script de zona restrita do Internet Explorer de controles de navegador da Web**  
  Essa configuração de política determina se uma página pode controlar controles WebBrowser inseridos por meio de script. Se você habilitar essa configuração de política, o acesso de script ao controle WebBrowser será permitido. Se você desabilitar essa configuração de política, o acesso de script ao controle WebBrowser não será permitido. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o acesso de script ao controle WebBrowser. Por padrão, o acesso de script ao controle WebBrowser é permitido apenas no computador local e nas zonas da intranet.
  
  **Padrão**: Desativado  
  
- **Filtro de script entre sites de zona restrita do Internet Explorer**  
  Essa política controla se o filtro XSS (script entre sites) detectará e impedirá injeçãos de script entre sites em sites nessa zona. Se você habilitar essa configuração de política, o filtro XSS será ativado para sites nessa zona e o filtro XSS tentará bloquear as injeções de script entre sites. Se você desabilitar essa configuração de política, o filtro XSS será desativado para sites nesta zona e o Internet Explorer permitirá injeçãos de script entre sites.
  
  **Padrão**: Enabled  
  
- **Comportamentos de script e binários de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie comportamentos binários e de script dinâmicos: componentes que encapsulam funcionalidades específicas para elementos HTML aos quais eles foram anexados. Se você habilitar essa configuração de política, os comportamentos binários e de script estarão disponíveis. Se você selecionar administrador aprovado na caixa suspensa, somente os comportamentos listados nos comportamentos aprovados pelo administrador sob a política de restrição de segurança de comportamentos binários estarão disponíveis. Se você desabilitar essa configuração de política, os comportamentos binários e de script não estarão disponíveis, a menos que os aplicativos tenham implementado um Gerenciador de segurança personalizado. Se você não definir essa configuração de política, os comportamentos binários e de script não estarão disponíveis, a menos que os aplicativos tenham implementado um Gerenciador de segurança personalizado.
  
  **Padrão**: Desativar  
  
- **Verificação de configurações de segurança do Internet Explorer**  
  Essa configuração de política desativa o recurso de verificação de configurações de segurança, que verifica as configurações de segurança do Internet Explorer para determinar quando as configurações colocam o Internet Explorer em risco. Se você habilitar essa configuração de política, o recurso será desativado. Se você desabilitar ou não definir essa configuração de política, o recurso será ativado.
  
  **Padrão**: Enabled  
  
- **Aviso de segurança de zona da Internet do Internet Explorer para arquivos potencialmente não seguros**  
  Essa configuração de política controla se a mensagem de "aviso de segurança de arquivo aberto" aparece quando o usuário tenta abrir arquivos executáveis ou outros arquivos potencialmente não seguros (de um compartilhamento de arquivos de intranet usando o explorador de arquivos, por exemplo). Se você habilitar essa configuração de política e definir a caixa suspensa como habilitar, esses arquivos abrirão sem um aviso de segurança. Se você definir a caixa suspensa como avisar, um aviso de segurança será exibido antes da abertura dos arquivos. Se você desabilitar essa configuração de política, esses arquivos não abrirão. Se você não definir essa configuração de política, o usuário poderá configurar como o computador lida com esses arquivos. Por padrão, esses arquivos são bloqueados na zona restrita, habilitados nas zonas da intranet e do computador local e definidos como prompt na Internet e nas zonas confiáveis.
  
  **Padrão**: Mensagem  
  
- **Permissões Java da zona Intranet do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como segurança média.
  
  **Padrão**: Alta segurança 
  
- **Bloqueio do Internet Explorer/controles ativos X desatualizados**  </br>
  Essa configuração de política determina se o Internet Explorer bloqueia controles ActiveX desatualizados específicos. Controles ActiveX desatualizados nunca são bloqueados na zona da intranet. Se você habilitar essa configuração de política, o Internet Explorer parará de bloquear controles ActiveX desatualizados. Se você desabilitar ou não definir essa configuração de política, o Internet Explorer continuará a bloquear controles ActiveX desatualizados específicos. Para obter mais informações, consulte "controles ActiveX desatualizados" na biblioteca do TechNet do Internet Explorer.
  
  **Padrão**: Enabled  
  
- **Bloqueador de pop-ups de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se janelas pop-up indesejadas são exibidas. Janelas pop-up que são abertas quando o usuário final clica em um link não são bloqueadas. Se você habilitar essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida. Se você desabilitar essa configuração de política, as janelas pop-up não serão impedidas de serem exibidas. Se você não definir essa configuração de política, a exibição da maioria das janelas pop-up indesejadas será impedida.
  
  **Padrão**: Ativar  
  
- **O Internet Explorer processa a restrição de segurança de protocolo MK**  
  A configuração de política de restrição de segurança de protocolo MK reduz a área da superfície de ataque, impedindo o protocolo MK. Os recursos hospedados no protocolo MK falharão. Se você habilitar essa configuração de política, o protocolo MK será impedido para o explorador de arquivos e o Internet Explorer, e os recursos hospedados no protocolo MK falharão. Se você desabilitar essa configuração de política, os aplicativos poderão usar a API de protocolo MK. Os recursos hospedados no protocolo MK funcionarão para os processos do explorador de arquivos e do Internet Explorer. Se você não definir essa configuração de política, o protocolo MK será impedido para o explorador de arquivos e o Internet Explorer, e os recursos hospedados no protocolo MK falharão.
  
  **Padrão**: Enabled  
  
- **Permissões Java de zona confiável do Internet Explorer**  </br>
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como segurança baixa.
  
  **Padrão**: Alta segurança  
  
- **Script de zona restrita do Internet Explorer de miniaplicativos Java**  
  Essa configuração de política permite que você gerencie se os applets são expostos aos scripts dentro da zona. Se você habilitar essa configuração de política, os scripts poderão acessar miniaplicativos automaticamente sem a intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que os scripts acessem os applets. Se você desabilitar essa configuração de política, os scripts serão impedidos de acessar miniaplicativos. Se você não definir essa configuração de política, os scripts serão impedidos de acessar miniaplicativos.
  
  **Padrão**: Desativar  
  
- **O Internet Explorer bloqueou as permissões de Java da zona restrita**  </br>
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.
  
  **Padrão**: Desabilitar Java 
  
- **Zona Internet do Internet Explorer permitir somente domínios aprovados para usar controles ActiveX**  </br>
  Essa configuração de política controla se o usuário é solicitado a permitir que os controles ActiveX sejam executados em sites que não sejam o site que instalou o controle ActiveX. Se você habilitar essa configuração de política, o usuário será solicitado antes que os controles ActiveX possam ser executados de sites nesta zona. O usuário pode optar por permitir que o controle seja executado a partir do site atual ou de todos os sites. Se você desabilitar essa configuração de política, o usuário não verá o prompt do ActiveX por site e os controles ActiveX poderão ser executados de todos os sites nesta zona.
  
  **Padrão**: Enabled  
  
- **O Internet Explorer inclui todos os caminhos de rede**  
  O Internet Explorer inclui todos os caminhos de rede
  
  **Padrão**: Desativado 
  
- **Modo protegido de zona Internet Explorer**  
  Essa configuração de política permite ativar o modo protegido. O modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo os locais em que o Internet Explorer pode gravar no registro e no sistema de arquivos. Se você habilitar essa configuração de política, o modo protegido será ativado. O usuário não pode desativar o modo protegido. Se você desabilitar essa configuração de política, o modo protegido será desativado. O usuário não pode ativar o modo protegido. Se você não definir essa configuração de política, o usuário poderá ativar ou desativar o modo protegido.
  
  **Padrão**: Ativar 
  
- **Inicialização de zona da Internet do Internet Explorer e controles do script ativo X não marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script.
  
  **Padrão**: Desativar 
  
- **Tela inteligente da zona restrita bloqueada do Internet Explorer**  </br>
  Essa configuração de política controla se o Filtro SmartScreen verifica as páginas nessa zona em busca de conteúdo mal-intencionado. Se você habilitar essa configuração de política, o filtro do SmartScreen verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você desabilitar essa configuração de política, o filtro do SmartScreen não verificará as páginas nessa zona em busca de conteúdo mal-intencionado. Se você não definir essa configuração de política, o usuário poderá escolher se o filtro do SmartScreen verificará se há conteúdo mal-intencionado nas páginas dessa zona. Nota: No Internet Explorer 7, essa configuração de política controla se o filtro de phishing verifica se há conteúdo mal-intencionado nas páginas dessa zona.
  
  **Padrão**: Enabled  
  
- **Detecção de falhas do Internet Explorer**  
  Essa configuração de política permite que você gerencie o recurso de detecção de falhas do gerenciamento de Complementos. Se você habilitar essa configuração de política, uma falha no Internet Explorer exibirá o comportamento encontrado no Windows XP Professional Service Pack 1 e versões anteriores, para invocar Relatório de Erros do Windows. Todas as configurações de política para Relatório de Erros do Windows continuam a ser aplicadas. Se você desabilitar ou não definir essa configuração de política, o recurso de detecção de pane para o gerenciamento de Complementos será funcional.
  
  **Padrão**: Desativado  
  
- **Permissões Java da zona Internet do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, a permissão será definida como alta segurança.
  
  **Padrão**: Desabilitar Java  
  
- **Script ativo de zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o código de script em páginas na zona é executado. Se você habilitar essa configuração de política, o código de script em páginas na zona poderá ser executado automaticamente. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o código de script em páginas na zona seja executado. Se você desabilitar essa configuração de política, o código de script em páginas na zona será impedido de ser executado. Se você não definir essa configuração de política, o código de script em páginas na zona será impedido de ser executado.
  
  **Padrão**: Desativar  
  
- **Opções de logon na Internet Zone do Internet Explorer**  
  Essa configuração de política permite que você gerencie configurações para opções de entrada. Se você habilitar essa configuração de política, poderá escolher entre as seguintes opções de entrada. Logon anônimo para desabilitar a autenticação HTTP e usar a conta de convidado somente para o protocolo CIFS (Common Internet File System). Solicite o nome de usuário e a senha para consultar os usuários de IDs de usuário e senhas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. Logon automático somente na zona da intranet para consultar os usuários de IDs de usuário e senhas em outras zonas. Depois que um usuário é consultado, esses valores podem ser usados silenciosamente para o restante da sessão. Conexão automática com o nome de usuário e a senha atuais para tentar fazer logon usando a resposta de desafio do Windows NT (também conhecida como autenticação NTLM). Se o servidor oferecer suporte à resposta de desafio do Windows NT, a entrada usará o nome de usuário e a senha de rede do usuário para fazer logon. Se o servidor não oferecer suporte à resposta de desafio do Windows NT, o usuário será consultado para fornecer o nome de usuário e a senha. Se você desabilitar essa configuração de política, a opção entrar será definida como logon automático somente na zona da intranet. Se você não definir essa configuração de política, a opção entrar será definida como logon automático somente na zona da intranet.
  
  **Padrão**: Mensagem  
  
- **Zona restrita do Internet Explorer permitir que o VBScript seja executado**  </br>  
  Essa configuração de política permite que você gerencie se o VBScript pode ser executado em páginas da zona especificada no Internet Explorer. Se você selecionou habilitar na caixa suspensa, o VBScript poderá ser executado sem intervenção do usuário. Se você selecionou prompt na caixa suspensa, os usuários serão solicitados a escolher se deseja permitir que o VBScript seja executado. Se você selecionou desabilitar na caixa suspensa, o VBScript será impedido de ser executado. Se você não definir ou desabilitar essa configuração de política, o VBScript será impedido de ser executado.
  
  **Padrão**: Desativar  
  
- **Zona Internet do Internet Explorer arrastar conteúdo de diferentes domínios no Windows**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração.
  
  **Padrão**: Desativado 
  
- **Inicialização de zona da intranet do Internet Explorer e controles do script ativo X não marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script.
  
  **Padrão**: Desativar 
  
- **Compartimentos de download do Internet Explorer**  
  Essa configuração de política impede que o usuário tenha os compartimentos (anexos de arquivo) baixados de um feed para o computador do usuário. Se você habilitar essa configuração de política, o usuário não poderá definir o mecanismo de sincronização de feeds para baixar um compartimento por meio da página de propriedades do feed. Um desenvolvedor não pode alterar a configuração de download por meio das APIs de feed. Se você desabilitar ou não definir essa configuração de política, o usuário poderá definir o mecanismo de sincronização de feeds para baixar um compartimento por meio da página de propriedades do feed. Um desenvolvedor pode alterar a configuração de download por meio das APIs de feed.
  
  **Padrão**: Desativado  
  
- **Controle de zona restrita do Internet Explorer-baixar controles ActiveX não assinados**  </br>
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando provenientes de uma zona não confiável. Se você habilitar essa configuração de política, os usuários poderão executar controles não assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o controle não assinado seja executado. Se você desabilitar essa configuração de política, os usuários não poderão executar controles não assinados. Se você não definir essa configuração de política, os usuários não poderão executar controles não assinados.
  
  **Padrão**: Desativar  
  
- **Zona Internet do Internet Explorer arrastar conteúdo de diferentes domínios no Windows**  
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando provenientes de uma zona não confiável. Se você habilitar essa configuração de política, os usuários poderão executar controles não assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o controle não assinado seja executado. Se você desabilitar essa configuração de política, os usuários não poderão executar controles não assinados. Se você não definir essa configuração de política, os usuários não poderão executar controles não assinados.
  
  **Padrão**: Desativado  
  
- **Os processos do Internet Explorer restringem a instalação do Active X**  </br>
  Essa configuração de política permite que os aplicativos que hospedam o controle do navegador da Web bloqueiem a solicitação automática de instalação do controle ActiveX. Se você habilitar essa configuração de política, o controle do navegador da Web bloqueará a solicitação automática de instalação do controle ActiveX para todos os processos. Se você desabilitar ou não definir essa configuração de política, o controle do navegador da Web não bloqueará a solicitação automática de instalação do controle ActiveX para todos os processos.
  
  **Padrão**: Enabled  
  
- **Área de Internet do Internet Explorer scriptlets** Essa configuração de política permite que você gerencie se o usuário pode executar scriptlets. Se você habilitar essa configuração de política, o usuário poderá executar scriptlets. Se você desabilitar essa configuração de política, o usuário não poderá executar o scriptlets. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o scriptlets.
  
  **Padrão**: Desativar  
  
- **Arrastar e soltar zona restrita do Internet Explorer ou copiar e colar arquivos**  
  Essa configuração de política permite que você gerencie se os usuários podem arrastar arquivos ou copiar e colar arquivos de uma fonte dentro da zona. Se você habilitar essa configuração de política, os usuários poderão arrastar arquivos ou copiar e colar arquivos dessa zona automaticamente. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja arrastar ou copiar arquivos dessa zona. Se você desabilitar essa configuração de política, os usuários serão impedidos de arrastar arquivos ou copiar e colar arquivos dessa zona. Se você não definir essa configuração de política, os usuários serão consultados para escolher se deseja arrastar ou copiar arquivos dessa zona.
  
  **Padrão**: Desativar  
  
- **Software do Internet Explorer quando a assinatura é inválida** </br>
  Essa configuração de política permite que você gerencie se o software, como controles ActiveX e downloads de arquivos, pode ser instalado ou executado pelo usuário, embora a assinatura seja inválida. Uma assinatura inválida pode indicar que alguém foi adulterado com o arquivo. Se você habilitar essa configuração de política, os usuários serão solicitados a instalar ou executar arquivos com uma assinatura inválida. Se você desabilitar essa configuração de política, os usuários não poderão executar ou instalar arquivos com uma assinatura inválida. Se você não configurar essa política, os usuários poderão optar por executar ou instalar arquivos com uma assinatura inválida.
  
  **Padrão**: Desativado  
  
- **Cópia e colagem de zona restrita do Internet Explorer via script** </br> Essa configuração de política permite que você gerencie se os scripts podem executar uma operação de área de transferência (por exemplo, recortar, copiar e colar) em uma região especificada. Se você habilitar essa configuração de política, um script poderá executar uma operação de área de transferência. Se você selecionar prompt na caixa suspensa, os usuários serão consultados sobre se deseja executar operações de área de transferência. Se você desabilitar essa configuração de política, um script não poderá executar uma operação de área de transferência. Se você não definir essa configuração de política, um script não poderá executar uma operação de área de transferência.
  
  **Padrão**: Desativar  
  
- **Conteúdo de arrastar zona restrita do Internet Explorer de domínios diferentes no Windows**  
  Essa configuração de política permite que você defina opções para arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Se você habilitar essa configuração de política e clicar em habilitar, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. Se você habilitar essa configuração de política e clicar em Desabilitar, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração. No Internet Explorer 10, se você desabilitar essa configuração de política ou não configurá-la, os usuários não poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários podem alterar essa configuração na caixa de diálogo Opções da Internet. No Internet Explorer 9 e versões anteriores, se você desabilitar essa política ou não configurá-la, os usuários poderão arrastar o conteúdo de um domínio para um domínio diferente quando a origem e o destino estiverem em janelas diferentes. Os usuários não podem alterar essa configuração.  <br><br>
  **Padrão**: Desativado  
  
- **Usuários do Internet Explorer adicionando sites**  
  Impede que os usuários adicionem ou removam sites de zonas de segurança. Uma zona de segurança é um grupo de sites com o mesmo nível de segurança. Se você habilitar essa política, as configurações de gerenciamento de site para zonas de segurança serão desabilitadas. (Para ver as configurações de gerenciamento de site para zonas de segurança, na caixa de diálogo Opções da Internet, clique na guia Segurança e, em seguida, clique no botão sites.) Se você desabilitar essa política ou não configurá-la, os usuários poderão adicionar sites ou remover sites das zonas sites confiáveis e sites restritos e alterar as configurações da zona da intranet local. Essa política impede que os usuários alterem as configurações de gerenciamento de site para zonas de segurança estabelecidas pelo administrador. Nota: A política "desabilitar a página de segurança" (localizada em \ Configuração do Computador\modelos Administrativos\Componentes do Windows\internet Explorer\painel de controle), que remove a guia Segurança da interface, tem precedência sobre essa política. Se estiver habilitado, essa política será ignorada. Além disso, consulte "zonas de segurança: Use a política apenas configurações do computador ".
  
  **Padrão**: Desativado  
  
- **Windows iniciado por script de zona da Internet Explorer**  
  Essa configuração de política permite que você gerencie restrições em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status. Se você habilitar essa configuração de política, a segurança das restrições do Windows não será aplicada nessa zona. A zona de segurança é executada sem a camada adicional de segurança fornecida por esse recurso. Se você desabilitar essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluem as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo. Se você não definir essa configuração de política, as possíveis ações prejudiciais contidas em janelas pop-up iniciadas por script e janelas que incluam as barras de título e status não poderão ser executadas. Esse recurso de segurança do Internet Explorer está ativado nessa zona, conforme ditado pela configuração de controle de recurso de restrições de segurança do Windows com script para o processo.
  
  **Padrão**: Desativado  
  
- **As zonas de segurança do Internet Explorer usam apenas as configurações do computador**  
  Aplica informações da zona de segurança a todos os usuários do mesmo computador. Uma zona de segurança é um grupo de sites com o mesmo nível de segurança. Se você habilitar essa política, as alterações que o usuário fizer em uma zona de segurança serão aplicadas a todos os usuários desse computador. Se você desabilitar essa política ou não configurá-la, os usuários do mesmo computador poderão estabelecer suas próprias configurações de zona de segurança. Use essa política para garantir que as configurações de zona de segurança se apliquem uniformemente ao mesmo computador e não variem de usuário para usuário. Além disso, consulte a política "zonas de segurança: não permitir que os usuários alterem políticas".
  
  **Padrão**: Enabled  
  
- **O Internet Explorer bloqueou as permissões Java da zona do computador local**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados
  
  **Padrão**: Desabilitar Java 
  
- **Zona restrita do Internet Explorer não executa antimalware em controles do Active X**  </br>
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.
  
  **Padrão**: Desativado  
  
- **Execução de zona restrita do Internet Explorer .NET Framework componentes dependentes assinados com Authenticode**  
  Essa configuração de política permite que você gerencie se .NET Framework componentes assinados com Authenticode podem ser executados no Internet Explorer. Esses componentes incluem controles gerenciados referenciados de uma marca de objeto e executáveis gerenciados referenciados por meio de um link. Se você habilitar essa configuração de política, o Internet Explorer executará componentes gerenciados assinados. Se você selecionar prompt na caixa suspensa, o Internet Explorer solicitará que o usuário determine se os componentes gerenciados assinados serão executados. Se você desabilitar essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados. Se você não definir essa configuração de política, o Internet Explorer não executará componentes gerenciados assinados.
  
  **Padrão**: Desativar  
  
- **Acesso à zona restrita do Internet Explorer a fontes de dados**  
  Essa configuração de política permite que você gerencie se o Internet Explorer pode acessar dados de outra zona de segurança usando o Microsoft XML Parser (MSXML) ou o ActiveX Data Objects (ADO). Se você habilitar essa configuração de política, os usuários poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que uma página seja carregada na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você desabilitar essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona. Se você não definir essa configuração de política, os usuários não poderão carregar uma página na zona que usa MSXML ou ADO para acessar dados de outro site na zona.
  
  **Padrão**: Desativar 
  
- **A zona Internet do Internet Explorer não executa antimalware em controles ActiveX**  </br>
  Essa configuração de política determina se o Internet Explorer executa programas antimalware em controles ActiveX, para verificar se eles são seguros para carregar em páginas. Se você habilitar essa configuração de política, o Internet Explorer não verificará com seu programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você desabilitar essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Se você não definir essa configuração de política, o Internet Explorer sempre verificará o programa antimalware para ver se é seguro criar uma instância do controle ActiveX. Os usuários podem ativar ou desativar esse comportamento, usando as configurações de segurança do Internet Explorer.
  
  **Padrão**: Desativado  
  
- **Cópia e colagem de zona Internet do Internet Explorer via script** </br> Essa configuração de política permite que você gerencie se os scripts podem executar uma operação de área de transferência (por exemplo, recortar, copiar e colar) em uma região especificada. Se você habilitar essa configuração de política, um script poderá executar uma operação de área de transferência. Se você selecionar prompt na caixa suspensa, os usuários serão consultados sobre se deseja executar operações de área de transferência. Se você desabilitar essa configuração de política, um script não poderá executar uma operação de área de transferência. Se você não definir essa configuração de política, um script poderá executar uma operação de área de transferência.
  
  **Padrão**: Desativar  
  
- **Serviço do instalador do Internet Explorer usando o Active X**  </br>
  Essa configuração de política permite que você especifique como os controles ActiveX são instalados. Se você habilitar essa configuração de política, os controles ActiveX serão instalados somente se o serviço instalador do ActiveX estiver presente e tiver sido configurado para permitir a instalação de controles ActiveX. Se você desabilitar ou não definir essa configuração de política, os controles ActiveX, incluindo controles por usuário, serão instalados por meio do processo de instalação padrão.
  
  **Padrão**: Enabled  
  
- **O Internet Explorer processa a proteção contra elevação de zona**  
  O Internet Explorer estabelece restrições em cada página da Web que ele abre. As restrições são dependentes do local da página da Web (Internet, intranet, zona do computador local e assim por diante). Por exemplo, as páginas da Web no computador local têm o mínimo de restrições de segurança e estão na zona do computador local, tornando a zona de segurança do computador local um destino principal para usuários mal-intencionados. Se você habilitar essa configuração de política, qualquer zona poderá ser protegida da elevação de zona para todos os processos. Se você desabilitar ou não definir essa configuração de política, processos diferentes do Internet Explorer ou aqueles listados na lista de processos não receberão essa proteção.
  
  **Padrão**: Enabled  
  
- **Internet Zone baixar controles ActiveX não assinados**  </br>
  Essa configuração de política permite que você gerencie se os usuários podem baixar controles ActiveX não assinados da zona. Esse código é potencialmente prejudicial, especialmente quando provenientes de uma zona não confiável. Se você habilitar essa configuração de política, os usuários poderão executar controles não assinados sem intervenção do usuário. Se você selecionar prompt na caixa suspensa, os usuários serão consultados para escolher se deseja permitir que o controle não assinado seja executado. Se você desabilitar essa configuração de política, os usuários não poderão executar controles não assinados. Se você não definir essa configuração de política, os usuários não poderão executar controles não assinados.
  
  **Padrão**: Desativar  
  
- **Zona Internet do Internet Explorer navegar pelas janelas e quadros entre domínios diferentes**  </br>
  Essa configuração de política permite que você gerencie a abertura de janelas e quadros e o acesso de aplicativos em diferentes domínios. Se você habilitar essa configuração de política, os usuários poderão abrir janelas e quadros de outros domínios e acessar aplicativos de outros domínios. Se você selecionar prompt na caixa suspensa, os usuários serão consultados se deseja permitir que janelas e quadros acessem aplicativos de outros domínios. Se você desabilitar essa configuração de política, os usuários não poderão abrir janelas e quadros para acessar aplicativos de domínios diferentes. Se você não definir essa configuração de política, os usuários poderão abrir janelas e quadros de outros domínios e acessar aplicativos de outros domínios.
  
  **Padrão**: Desativar  
  
- **Atualizações de zona da Internet do Internet Explorer para barra de status por meio de script**  
  Essa configuração de política permite que você gerencie se um script pode atualizar a barra de status dentro da zona. Se você habilitar essa configuração de política, os scripts poderão atualizar a barra de status. Se você desabilitar ou não definir essa configuração de política, o script não poderá atualizar a barra de status.
  
  **Padrão**: Desativado  
  
- **A zona restrita do Internet Explorer inclui o caminho local ao carregar arquivos no servidor**  </br> Essa configuração de política controla se as informações de caminho local são enviadas quando o usuário está carregando um arquivo por meio de um formulário HTML. Se as informações de caminho local forem enviadas, algumas informações poderão ser reveladas acidentalmente ao servidor. Por exemplo, os arquivos enviados da área de trabalho do usuário podem conter o nome de usuário como parte do caminho. Se você habilitar essa configuração de política, as informações de caminho serão enviadas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você desabilitar essa configuração de política, as informações de caminho serão removidas quando o usuário estiver carregando um arquivo por meio de um formulário HTML. Se você não definir essa configuração de política, o usuário poderá escolher se as informações de caminho serão enviadas quando estiverem carregando um arquivo por meio de um formulário HTML. Por padrão, as informações de caminho são enviadas.
  
  **Padrão**: Desativado  
  
- **Os processos do Internet Explorer restringem o download do arquivo**  </br> Essa configuração de política permite que aplicativos que hospedam o controle de navegador da Web bloqueiem a solicitação automática de downloads de arquivos que não são iniciados pelo usuário. Se você habilitar essa configuração de política, o controle de navegador da Web bloqueará a solicitação automática de downloads de arquivo que não são iniciados pelo usuário para todos os processos. Se você desabilitar essa configuração de política, o controle de navegador da Web não bloqueará a solicitação automática de downloads de arquivo que não são iniciados pelo usuário para todos os processos.
  
  **Padrão**: Enabled  
  
- **Zona restrita do Internet Explorer permitir que somente domínios aprovados usem controles ActiveX**  </br>
  Essa configuração de política controla se o usuário é solicitado a permitir que os controles ActiveX sejam executados em sites que não sejam o site que instalou o controle ActiveX. Se você habilitar essa configuração de política, o usuário será solicitado antes que os controles ActiveX possam ser executados de sites nesta zona. O usuário pode optar por permitir que o controle seja executado a partir do site atual ou de todos os sites. Se você desabilitar essa configuração de política, o usuário não verá o prompt do ActiveX por site e os controles ActiveX poderão ser executados de todos os sites nesta zona.
  
  **Padrão**: Enabled  
  
- **Os controles de inicialização de zona restrita do Internet Explorer e script ativo X não estão marcados como seguros**  
  Essa configuração de política permite que você gerencie controles ActiveX não marcados como seguros. Se você habilitar essa configuração de política, os controles ActiveX são executados, carregados com parâmetros e com script sem definir a segurança de objeto para dados ou scripts não confiáveis. Essa configuração não é recomendada, exceto para zonas seguras e administradas. Essa configuração faz com que controles seguros e não seguros sejam inicializados e com script, ignorando os controles ActiveX de script marcados como seguros para a opção de script. Se você habilitar essa configuração de política e selecionar avisar na caixa suspensa, os usuários serão consultados se deseja permitir que o controle seja carregado com parâmetros ou com script. Se você desabilitar essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script. Se você não definir essa configuração de política, os controles ActiveX que não puderem ser tornados seguros não serão carregados com parâmetros ou com script.
  
  **Padrão**: Desativar  
  
- **Usuários do Internet Explorer alterando políticas**  
    Impede que os usuários alterem as configurações de zona de segurança. Uma zona de segurança é um grupo de sites com o mesmo nível de segurança. Se você habilitar essa política, o botão de nível personalizado e o controle deslizante de nível de segurança na guia Segurança da caixa de diálogo Opções da Internet serão desabilitados. Se você desabilitar essa política ou não configurá-la, os usuários poderão alterar as configurações de zonas de segurança. Essa política impede que os usuários alterem as configurações de zona de segurança estabelecidas pelo administrador. Nota: A política "desabilitar a página de segurança" (localizada em \ Configuração do Computador\modelos Administrativos\Componentes do Windows\internet Explorer\painel de controle), que remove a guia Segurança do Internet Explorer no painel de controle, tem precedência sobre Esta política. Se estiver habilitado, essa política será ignorada. Além disso, consulte "zonas de segurança: Use a política apenas configurações do computador ".
    
  **Padrão**: Desativado  
  
- **Modo protegido de zona restrita do Internet Explorer**  
  Essa configuração de política permite ativar o modo protegido. O modo protegido ajuda a proteger o Internet Explorer contra vulnerabilidades exploradas, reduzindo os locais em que o Internet Explorer pode gravar no registro e no sistema de arquivos. Se você habilitar essa configuração de política, o modo protegido será ativado. O usuário não pode desativar o modo protegido. Se você desabilitar essa configuração de política, o modo protegido será desativado. O usuário não pode ativar o modo protegido. Se você não definir essa configuração de política, o usuário poderá ativar ou desativar o modo protegido.
  
  **Padrão**: Ativar  
  
- **Persistência de dados de usuário da zona Internet do Internet Explorer**  
  Essa configuração de política permite que você gerencie a preservação de informações no histórico do navegador, em favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Quando um usuário retornar a uma página persistente, o estado da página poderá ser restaurado se essa configuração de política estiver configurada adequadamente. Se você habilitar essa configuração de política, os usuários poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você desabilitar essa configuração de política, os usuários não poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você não definir essa configuração de política, os usuários poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco.
  
  **Padrão**: Desativado  
  
- **Script de Internet do Internet Explorer de controles de navegador da Web**  
 
  Essa configuração de política determina se uma página pode controlar controles WebBrowser inseridos por meio de script. Se você habilitar essa configuração de política, o acesso de script ao controle WebBrowser será permitido. Se você desabilitar essa configuração de política, o acesso de script ao controle WebBrowser não será permitido. Se você não definir essa configuração de política, o usuário poderá habilitar ou desabilitar o acesso de script ao controle WebBrowser. Por padrão, o acesso de script ao controle WebBrowser é permitido apenas no computador local e nas zonas da intranet.
  
  **Padrão**: Desativado  
  
- **Persistência de dados de usuário de zona restrita do Internet Explorer**  
    Essa configuração de política permite que você gerencie a preservação de informações no histórico do navegador, em favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Quando um usuário retornar a uma página persistente, o estado da página poderá ser restaurado se essa configuração de política estiver configurada adequadamente. Se você habilitar essa configuração de política, os usuários poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você desabilitar essa configuração de política, os usuários não poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco. Se você não definir essa configuração de política, os usuários não poderão preservar as informações no histórico do navegador, nos favoritos, em um repositório XML ou diretamente em uma página da Web salva em disco.  
  
  **Padrão**: Desativado  
  
- **Permissões Java da zona de intranet bloqueada do Internet Explorer**  
  Essa configuração de política permite que você gerencie permissões para miniaplicativos Java. Se você habilitar essa configuração de política, poderá escolher opções na caixa suspensa. Personalizado, para controlar as configurações de permissões individualmente. A segurança baixa permite que os applets executem todas as operações. A segurança média permite que os applets sejam executados em sua área restrita (uma área na memória fora da qual o programa não pode fazer chamadas), além de recursos como espaço transitório (uma área de armazenamento segura e seguro no computador cliente) e e/s de arquivo controlado pelo usuário. A alta segurança permite que os applets sejam executados na área restrita. Desabilite o Java para impedir que os applets sejam executados. Se você desabilitar essa configuração de política, os miniaplicativos Java não poderão ser executados. Se você não definir essa configuração de política, os miniaplicativos Java serão desabilitados.
  
  **Padrão**: Desabilitar Java  
  
- **Modo protegido aprimorado do Internet Explorer**  
  O modo protegido avançado fornece proteção adicional contra sites mal-intencionados usando processos de 64 bits em versões de 64 bits do Windows. Para computadores que executam pelo menos o Windows 8, o modo protegido aprimorado também limita os locais em que o Internet Explorer pode ler no registro e no sistema de arquivos. Se você habilitar essa configuração de política, o modo protegido avançado será ativado. Qualquer zona que tenha o modo protegido habilitado usará o modo protegido avançado. Os usuários não poderão desabilitar o modo protegido avançado. Se você desabilitar essa configuração de política, o modo protegido avançado será desativado. Qualquer zona que tenha o modo protegido habilitado usará a versão do modo protegido introduzido no Internet Explorer 7 para Windows Vista. Se você não configurar essa política, os usuários poderão ativar ou desativar o modo protegido avançado na guia Avançado da caixa de diálogo Opções da Internet.
  
  **Padrão**: Enabled  
  
- **Avisos de tela inteligente de bypass do Internet Explorer**  
  Essa configuração de política determina se o usuário pode ignorar avisos do filtro do SmartScreen. O filtro do SmartScreen avisa o usuário sobre arquivos executáveis que os usuários do Internet Explorer geralmente não baixam da Internet. Se você habilitar essa configuração de política, os avisos do filtro do SmartScreen bloquearão o usuário. Se você desabilitar ou não definir essa configuração de política, o usuário poderá ignorar os avisos do filtro do SmartScreen.
  
  **Padrão**: Desativado  
  
- **Meta Refresh da zona restrita do Internet Explorer**  
  Essa configuração de política permite que você gerencie se o navegador de um usuário pode ser redirecionado para outra página da Web se o autor da página da Web usar a configuração de meta Refresh (marca) para redirecionar os navegadores para outra página da Web. Se você habilitar essa configuração de política, o navegador de um usuário que carrega uma página que contém uma configuração de meta Refresh ativa pode ser redirecionado para outra página da Web. Se você desabilitar essa configuração de política, o navegador de um usuário que carregar uma página que contém uma configuração de meta Refresh ativa não poderá ser redirecionado para outra página da Web. Se você não definir essa configuração de política, o navegador de um usuário que carregar uma página que contém uma configuração de meta Refresh ativa não poderá ser redirecionado para outra página da Web.
  
  **Padrão**: Desativado  
  
### <a name="local-policies-security-options"></a>Opções de segurança de políticas locais
Para obter mais informações, consulte [Policy CSP-LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) na documentação do Windows. 

- **Restringir o acesso anônimo a pipes nomeados e compartilhamentos**  
  Quando habilitada, essa configuração de segurança restringe o acesso anônimo a compartilhamentos e pipes para as configurações de: (1) pipes nomeados que podem ser acessados anonimamente (2) compartilhamentos que podem ser acessados anonimamente
  
  **Padrão**: Sim  
  
- **Segurança mínima de sessão para servidores baseados em NTLM SSP**  
  Essa configuração de segurança permite que um servidor exija a negociação de criptografia de 128 bits e/ou segurança de sessão NTLMv2. Esses valores são dependentes do valor de configuração de segurança do nível de autenticação do LAN Manager. As opções são: Exigir segurança de sessão NTLMv2: A conexão falhará se a integridade da mensagem não for negociada. Exigir criptografia de 128 bits. A conexão falhará se a criptografia forte (128 bits) não for negociada.
  
  **Padrão**: Exigir criptografia NTLM V2 e 128 bits  
  
- **Minutos de inatividade de tela de bloqueio até que a proteção de tela seja ativada**  
  O Windows repara na inatividade de um início de sessão e, se a quantidade de tempo inativo exceder o limite de inatividade, então, a proteção de ecrã será executado, bloqueando a sessão.
  
  **Padrão**: 15
  
- **Exigir que o cliente assine sempre as comunicações digitalmente** Essa configuração de segurança determina se todo o tráfego de canal seguro iniciado pelo membro do domínio deve ser assinado ou criptografado. Quando um computador ingressa em um domínio, uma conta de computador é criada. Depois disso, quando o sistema é iniciado, ele usa a senha da conta de computador para criar um canal seguro com um controlador de domínio para seu domínio. Esse canal seguro é usado para executar operações como autenticação de passagem de NTLM, pesquisa de nome/SID de LSA e muito mais. Essa configuração determina se todo o tráfego de canal seguro iniciado pelo membro do domínio atende aos requisitos mínimos de segurança. Especificamente, ele determina se todo o tráfego de canal seguro iniciado pelo membro do domínio deve ser assinado ou criptografado. Se essa política estiver habilitada, o canal seguro não será estabelecido, a menos que a assinatura ou a criptografia de todo o tráfego de canal seguro seja negociada. Se essa política estiver desabilitada, a criptografia e a assinatura de todo o tráfego de canal seguro serão negociadas com o controlador de domínio, caso em que o nível de assinatura e criptografia depende da versão do controlador de domínio e das configurações dos dois seguintes Policie Membro do domínio: Criptografar digitalmente os dados do canal seguro (quando possível) membro do domínio: Assinar digitalmente os dados do canal seguro (quando possível)
  
  **Padrão**: Sim
  
- **Nível de autenticação**  
  Essa configuração de segurança determina qual protocolo de autenticação de desafio/resposta é usado para logons de rede. Essa escolha afeta o nível de protocolo de autenticação usado pelos clientes, o nível de segurança de sessão negociado e o nível de autenticação aceito pelos servidores da seguinte maneira:  
  - *Enviar respostas LM e NTLM*: Os clientes usam a autenticação LM e NTLM e nunca usam a segurança de sessão NTLMv2; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar LM e NTLM-NTLMv2 se negociado*: Os clientes usam a autenticação LM e NTLM e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar somente resposta NTLM*: Os clientes usam somente a autenticação NTLM e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar somente resposta NTLMv2*: Os clientes usam somente a autenticação NTLMv2 e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio aceitam autenticação LM, NTLM e NTLMv2. 
  - *Enviar somente resposta NTLMv2. Recusar LM*: Os clientes usam somente a autenticação NTLMv2 e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio recusam LM (aceitam somente autenticação NTLM e NTLMv2). 
  - *Enviar somente resposta NTLMv2. Recusar LM e NTLM*: Os clientes usam somente a autenticação NTLMv2 e usam a segurança de sessão NTLMv2 se o servidor oferecer suporte a ele; os controladores de domínio recusam LM e NTLM (aceitam somente a autenticação NTLMv2). 
    
  **Padrão**: Enviar somente resposta NTLMv2. Recusar LM e NTLM
  
- **Impedir que os clientes enviem senhas não criptografadas para servidores SMB de terceiros**  
  Se essa configuração de segurança estiver habilitada, o redirecionador de protocolo SMB poderá enviar senhas de texto não criptografado a servidores SMB não Microsoft que não ofereçam suporte à criptografia de senha durante a autenticação. O envio de senhas não criptografadas é um risco à segurança.
  
  **Padrão**: Sim
  
- **Desabilitar sempre as comunicações de assinatura digital do servidor**  
  Essa configuração de segurança determina se o cliente SMB tenta negociar a assinatura de pacotes SMB. O protocolo SMB fornece a base para o compartilhamento de arquivos e impressão da Microsoft e muitas outras operações de rede, como a administração remota do Windows. Para evitar ataques man-in-the-Middle que modificam pacotes SMB em trânsito, o protocolo SMB dá suporte à assinatura digital de pacotes SMB. Essa configuração de política determina se o componente cliente SMB tenta negociar a assinatura de pacote SMB quando se conecta a um servidor SMB. Se essa configuração estiver habilitada, o cliente de rede da Microsoft solicitará que o servidor execute a assinatura de pacote SMB na configuração da sessão. Se a assinatura de pacotes tiver sido ativada no servidor, a assinatura de pacotes será negociada. Se essa política estiver desabilitada, o cliente SMB nunca negociará a assinatura de pacotes SMB.
  
  **Padrão**: Sim
  
- **Comportamento da solicitação de elevação do administrador**  
  Essa configuração de política controla o comportamento da solicitação de elevação para administradores. As opções são: 
  - *Elevar sem avisar*: Permite que contas com privilégios executem uma operação que requer elevação sem exigir consentimento ou credenciais. Nota: Use essa opção somente nos ambientes mais restritos. 
  - *Solicitar credenciais na área de trabalho segura*: Quando uma operação requer elevação de privilégio, o usuário recebe uma solicitação na área de trabalho segura para inserir um nome de usuário e senha privilegiados. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio mais alto disponível do usuário. 
  - *Solicitar consentimento na área de trabalho segura*: Quando uma operação requer elevação de privilégio, o usuário recebe uma solicitação na área de trabalho segura para selecionar permitir ou negar. Se o usuário selecionar permitir, a operação continuará com o privilégio mais alto disponível do usuário. 
  - *Solicitar credenciais*: Quando uma operação requer elevação de privilégio, o usuário é solicitado a inserir um nome de usuário administrativo e uma senha. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Solicitar consentimento*: Quando uma operação requer elevação de privilégio, o usuário recebe uma solicitação para selecionar permitir ou negar. Se o usuário selecionar permitir, a operação continuará com o privilégio mais alto disponível do usuário.  
  - *Solicitar consentimento para binários não Windows*: Quando uma operação para um aplicativo que não é da Microsoft requer elevação de privilégio, o usuário recebe uma solicitação na área de trabalho segura para selecionar permitir ou negar. Se o usuário selecionar permitir, a operação continuará com o privilégio mais alto disponível do usuário.   
  
  **Padrão**: Solicitar consentimento na área de trabalho segura
  
- **Segurança mínima de sessão para clientes baseados em NTLM SSP**  
  Essa configuração de segurança permite que um cliente exija a negociação de criptografia de 128 bits e/ou segurança de sessão NTLMv2. Esses valores são dependentes do valor de configuração de segurança do nível de autenticação do LAN Manager. As opções são:
  - Exigir segurança de sessão NTLMv2: A conexão falhará se o protocolo NTLMv2 não for negociado. 
  - *Exigir criptografia de 128 bits*: A conexão falhará se a criptografia forte (128 bits) não for negociada.
  - *Exigir criptografia NTLMv2 e 128 bits*. 

  **Padrão**: Exigir criptografia NTLM v2 128
  
- **Comportamento de remoção de cartão inteligente**  
  Essa configuração de segurança determina o que acontece quando o cartão inteligente de um usuário conectado é removido do leitor de cartão inteligente. As opções são:
  - *Nenhuma ação*. 
  - *Bloquear estação de trabalho* -a estação de trabalho é bloqueada quando o cartão inteligente é removido, permitindo que os usuários saiam da área, usem seu cartão inteligente e ainda mantenham uma sessão protegida.
  - *Forçar logoff* – o usuário é desconectado automaticamente quando o cartão inteligente é removido.
  - *Desconectar área de trabalho remota sessão* – a remoção do cartão inteligente desconecta a sessão sem fazer logoff do usuário. Isso permite que o usuário insira o cartão inteligente e retome a sessão mais tarde, ou em outro computador equipado com leitor de cartão inteligente, sem precisar fazer logon novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.  <br><br>

  **Padrão**: Bloquear estação de trabalho
  
- **Bloquear a enumeração anônima de contas e compartilhamentos SAM**  
  Essa configuração de segurança determina se a enumeração anônima de contas e compartilhamentos SAM deve ser permitida. O Windows permite que usuários anônimos executem determinadas atividades, como a enumeração de nomes de contas de domínio e compartilhamentos de rede. Isso é conveniente, por exemplo, quando um administrador deseja conceder acesso a usuários em um domínio confiável que não mantém uma confiança recíproca. Se você não quiser permitir a enumeração anônima de contas e compartilhamentos SAM, defina essa política como *Sim*.
  
  **Padrão**: Sim
  
- **Bloquear logon remoto com senha em branco**  
  Essa configuração de segurança determina se as contas locais que não são protegidas por senha podem ser usadas para fazer logon de locais diferentes do console do computador físico. Se habilitada, as contas locais que não são protegidas por senha devem usar o teclado do computador para fazer logon. 

  *Aviso*: Os computadores que não estão em locais fisicamente seguros sempre devem impor políticas de senha forte para todas as contas de usuário locais. Caso contrário, qualquer pessoa com acesso físico ao computador pode fazer logon usando uma conta de usuário que não tenha uma senha. Isso é especialmente importante para computadores portáteis. 

  Se você aplicar essa política de segurança ao grupo everyone, ninguém poderá fazer logon por meio de Serviços de Área de Trabalho Remota. Essa configuração não afeta os logons que usam contas de domínio. É possível que os aplicativos que usam logons interativos remotos ignorem essa configuração.
  
  **Padrão**: Sim
  
- **Comportamento de prompt de elevação de usuário padrão**  
  Essa configuração de política controla o comportamento da solicitação de elevação para usuários padrão. 
  - *Negar automaticamente solicitações de elevação*: Quando uma operação requer elevação de privilégio, uma mensagem de erro de acesso negado configurável é exibida. Uma empresa que esteja executando áreas de trabalho como usuário padrão pode escolher essa configuração para reduzir as chamadas de suporte técnico. 
  - *Solicitar credenciais na área de trabalho segura*: Quando uma operação requer elevação de privilégio, o usuário recebe uma solicitação na área de trabalho segura para inserir um nome de usuário e senha diferentes. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Solicitar credenciais*: Quando uma operação requer elevação de privilégio, o usuário é solicitado a inserir um nome de usuário administrativo e uma senha. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável.  
  
  **Padrão**: Negar automaticamente solicitações de elevação
  
- **Exigir o modo de aprovação de administrador para administradores**  
  Essa configuração de política controla o comportamento de todas as configurações de política de controle de conta de usuário (UAC) para o computador. Se você alterar essa configuração de política, deverá reiniciar o computador. As opções são:   
  - *Não configurado*: O modo de aprovação de administrador e todas as configurações de política de UAC relacionadas estão desabilitados. Nota: Se essa configuração de política estiver desabilitada, a central de segurança o notificará de que a segurança geral do sistema operacional foi reduzida. 
  - *Sim*: O modo de aprovação de administrador está habilitado. Essa política deve ser habilitada e as configurações de política de UAC relacionadas devem ser definidas adequadamente para permitir que a conta de administrador interna e todos os outros usuários que são membros do grupo Administradores sejam executados no modo de aprovação de administrador.  
  
  **Padrão**: Sim
  
- **Impedir enumeração anônima de contas SAM**  
  Essa configuração de segurança determina quais permissões adicionais são concedidas para conexões anônimas ao computador. O Windows permite que usuários anônimos executem determinadas atividades, como a enumeração de nomes de contas de domínio e compartilhamentos de rede. Isso é conveniente, por exemplo, quando um administrador deseja conceder acesso a usuários em um domínio confiável que não mantém uma confiança recíproca. Essa opção de segurança permite que restrições adicionais sejam colocadas em conexões anônimas da seguinte maneira: 
  - *Sim*: Não permitir enumeração de contas SAM. Essa opção substitui todos os usuários autenticados nas permissões de segurança para recursos.
  - *Não configurado*: Sem restrições adicionais. Conte com as permissões padrão.  
  
  **Padrão**: Sim
  
- **Permitir chamadas remotas para o Gerenciador de contas de segurança**  
  Essa configuração de política permite restringir conexões RPC remotas ao SAM. Se não for selecionado, o descritor de segurança padrão será usado.
  
  **Padrão**: *O:BAG: INADEQUADO: (A;; RC;;; BA*

- **Usar o modo de aprovação de administrador**  
  Essa configuração de política controla o comportamento do modo de aprovação de administrador para a conta de administrador interno. As opções são: 
  - *Sim*: A conta de administrador interno usa o modo de aprovação de administrador. Por padrão, qualquer operação que exija elevação de privilégio solicitará que o usuário aprove a operação. 
  - *Não configurado*: A conta de administrador interno executa todos os aplicativos com privilégio administrativo completo.  

  **Padrão**: Sim
  
- **Permitir aplicativos de acesso à interface do usuário para locais seguros**  
  Essa configuração de política controla se os programas de acessibilidade da interface do usuário (UIAccess ou UIA) podem desabilitar automaticamente a área de trabalho segura para solicitações de elevação usadas por um usuário padrão. 
  - *Sim*: Os programas UIA, incluindo a assistência remota do Windows, desabilitam automaticamente a área de trabalho segura para solicitações de elevação. Se você não desabilitar o "controle de conta de usuário: Mude para a configuração de política da área de trabalho segura ao solicitar elevação ", os prompts aparecem na área de trabalho do usuário interativo em vez da área de trabalho segura. 
  - *Não configurado*: A área de trabalho segura pode ser desabilitada somente pelo usuário da área de trabalho interativa ou desabilitando o "controle de conta de usuário: Alterne para a área de trabalho segura ao solicitar elevação ".  

  **Padrão**: Sim

- **Detectar instalações de aplicativos e solicitar elevação**  
  Essa configuração de política controla o comportamento da detecção de instalação do aplicativo para o computador. As opções são: 
  - *Habilitado*: Quando é detectado um pacote de instalação de aplicativo que requer elevação de privilégio, o usuário é solicitado a inserir um nome de usuário administrativo e uma senha. Se o usuário inserir credenciais válidas, a operação continuará com o privilégio aplicável. 
  - *Desativado*: Os pacotes de instalação do aplicativo não são detectados e são solicitados a fornecer elevação. As empresas que executam desktops de usuário padrão e usam tecnologias de instalação delegadas, como o Política de Grupo de Instalação de Software ou o Systems Management Server (SMS), devem desabilitar essa configuração de política. Nesse caso, a detecção do instalador é desnecessária.  
  
  **Padrão**: Sim
  
- **Impedir o armazenamento do valor de hash do LAN Manager na próxima alteração de senha**  
  Essa configuração de segurança determina se, na próxima alteração de senha, o valor de hash do LM (LAN Manager) para a nova senha será armazenado. O hash do LM é relativamente fraco e propenso a ataques, em comparação com o hash do Windows NT criptograficamente mais forte. Como o hash do LM é armazenado no computador local no banco de dados de segurança, as senhas podem ser comprometidas se o banco de dados de segurança for atacado.
  
  **Padrão**: Sim

- **Virtualizar falhas de gravação de arquivo e registro para locais por usuário**  
  Essa configuração de política controla se as falhas de gravação do aplicativo são redirecionadas para os locais do registro e do sistema de arquivos definidos. Essa configuração de política reduz os aplicativos que são executados como administrador e grava dados de aplicativo em tempo de execução em *% ProgramFiles%* , *% windir%* , *%windir%\System32*ou *HKLM\Software*.
  
  **Padrão**: Sim

### <a name="ms-security-guide"></a>Guia de segurança da MS  

Para obter mais informações, consulte [Policy CSP-MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) na documentação do Windows.  

- **Aplicar restrições de UAC a contas locais no logon de rede**  
  **Padrão**: Enabled
  
- **Configuração de inicialização do driver de cliente SMB v1**  
  **Padrão**: Driver desabilitado
  
- **Servidor SMB v1**  
  **Padrão**: Desativado
  
- **Autenticação resumida**  
  **Padrão**: Desativado
  
- **Manipulação de exceção estruturada substituir proteção**  
  **Padrão**: Enabled
  
### <a name="mss-legacy"></a>MSS herdado  

Para obter mais informações, consulte [Policy CSP-MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) na documentação do Windows.  

- **Nível de proteção de roteamento de origem IP de rede**  
  **Padrão**: Proteção mais alta  
  
- **Rede ignorar solicitações de liberação de nome NetBIOS exceto de servidores WINS**  
  **Padrão**: Enabled
  
- **Nível de proteção de roteamento de origem IPv6 da rede**  
  **Padrão**: Proteção mais alta

- **Redirecionamentos de ICMP de rede substituem o OSPF gerado**  
  **Padrão**: Desativado
  
### <a name="power"></a>Alimentar  

Para obter mais informações, consulte [CSP da política – Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) na documentação do Windows.  

- **Exigir senha ao ativar enquanto conectado**  
  Essa configuração de política especifica se o usuário é solicitado a fornecer uma senha quando o sistema sai do estado de suspensão. Se você habilitar ou não definir essa configuração de política, o usuário será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão. Se você desabilitar essa configuração de política, o usuário não será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão.
  
  **Padrão**: Enabled
  
- **Estados de espera quando estiverem em suspensão durante a bateria**  
  Essa configuração de política gerencia se o Windows pode usar Estados de espera ao colocar o computador em estado de suspensão. Se você habilitar ou não definir essa configuração de política, o Windows usará Estados de espera para colocar o computador em estado de suspensão. Se você desabilitar essa configuração de política, os Estados de espera (S1-S3) não serão permitidos.
  
  **Padrão**: Desativado
  
- **Estados de espera quando conectados em suspensão**  
  Essa configuração de política gerencia se o Windows pode usar Estados de espera ao colocar o computador em estado de suspensão. Se você habilitar ou não definir essa configuração de política, o Windows usará Estados de espera para colocar o computador em estado de suspensão. Se você desabilitar essa configuração de política, os Estados de espera (S1-S3) não serão permitidos.
  
  **Padrão**: Desativado
  
- **Exigir senha ao ativar enquanto estiver na bateria**  
  Essa configuração de política especifica se o usuário é solicitado a fornecer uma senha quando o sistema sai do estado de suspensão. Se você habilitar ou não definir essa configuração de política, o usuário será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão. Se você desabilitar essa configuração de política, o usuário não será solicitado a fornecer uma senha quando o sistema for retomado do estado de suspensão.
  
  **Padrão**: Enabled
  
### <a name="remote-desktop-services"></a>Serviços de Ambiente de Trabalho Remoto  

Para obter mais informações, consulte [Policy CSP-RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) na documentação do Windows.  

- **Bloquear salvamento de senha**  
  Controla se as senhas podem ser salvas neste computador de Conexão de Área de Trabalho Remota. Se você habilitar essa configuração, a caixa de seleção Salvar senha no Conexão de Área de Trabalho Remota será desabilitada e os usuários não poderão salvar senhas. Quando um usuário abre um arquivo RDP usando Conexão de Área de Trabalho Remota e salva suas configurações, qualquer senha que anteriormente existia no arquivo RDP é excluída. Se você desabilitar essa configuração ou deixá-la não configurada, o usuário poderá salvar senhas usando Conexão de Área de Trabalho Remota.
  
   **Padrão**: Enabled
  
- **Comunicação segura de RPC**  
  Especifica se um servidor de Host da Sessão da Área de Trabalho Remota requer comunicação de RPC segura com todos os clientes ou permite comunicação não segura. Você pode usar essa configuração para reforçar a segurança da comunicação RPC com clientes, permitindo apenas solicitações autenticadas e criptografadas. Se o status for definido como habilitado, Serviços de Área de Trabalho Remota aceitará solicitações de clientes RPC que dão suporte a solicitações seguras e não permitirá a comunicação não segura com clientes não confiáveis. Se o status for definido como desabilitado, Serviços de Área de Trabalho Remota sempre solicitará segurança para todo o tráfego RPC. No entanto, a comunicação não segura é permitida para clientes RPC que não respondem à solicitação. Se o status for definido como não configurado, a comunicação não segura será permitida. Nota: A interface RPC é usada para administrar e configurar Serviços de Área de Trabalho Remota.
  
  **Padrão**: Enabled
  
- **Bloquear redirecionamento de unidade**  
  Essa configuração de política especifica se é para impedir o mapeamento de unidades cliente em uma sessão de Serviços de Área de Trabalho Remota (redirecionamento de unidade). Por padrão, um servidor Host da Sessão RD mapeia automaticamente as unidades do cliente após a conexão. As unidades mapeadas aparecem na árvore de pastas de sessões no explorador de arquivos ou no computador no formato  *\<DriveLetter >* em  *\<ComputerName >* . Você pode usar essa configuração de política para substituir esse comportamento. Se você habilitar essa configuração de política, o redirecionamento de unidade de cliente não será permitido em sessões de Serviços de Área de Trabalho Remota, e o redirecionamento de cópia de arquivo da área de transferência não será permitido em computadores que executam o Windows Server 2003, Windows 8 e Windows XP. Se você desabilitar essa configuração de política, o redirecionamento de unidade de cliente sempre será permitido. Além disso, o redirecionamento de cópia de arquivo da área de transferência sempre será permitido se o redirecionamento de área de transf for permitido. Se você não definir essa configuração de política, o redirecionamento de unidade de cliente e de cópia de arquivo da área de transferência não serão especificados no nível de Política de Grupo.
  
  **Padrão**: Enabled
  
- **Solicitar senha na conexão**  
  Essa configuração de política especifica se Serviços de Área de Trabalho Remota sempre solicita uma senha ao cliente durante a conexão. Você pode usar essa configuração para impor um prompt de senha para os usuários que fazem logon no Serviços de Área de Trabalho Remota, mesmo que eles já tenham fornecido a senha no cliente do Conexão de Área de Trabalho Remota. Por padrão, Serviços de Área de Trabalho Remota permite que os usuários façam logon automaticamente digitando uma senha no cliente Conexão de Área de Trabalho Remota. Se você habilitar essa configuração de política, os usuários não poderão fazer logon automaticamente no Serviços de Área de Trabalho Remota fornecendo suas senhas no cliente Conexão de Área de Trabalho Remota. Ele será solicitado a fornecer uma senha para fazer logon. Se você desabilitar essa configuração de política, os usuários sempre poderão fazer logon no Serviços de Área de Trabalho Remota automaticamente fornecendo suas senhas no cliente Conexão de Área de Trabalho Remota. Se você não definir essa configuração de política, o logon automático não será especificado no nível de Política de Grupo. 
  
  **Padrão**: Enabled
  
- **Nível de criptografia de conexão de cliente dos serviços de área de trabalho remota**  
  Especifica se o uso de um nível de criptografia específico deve ser necessário para proteger as comunicações entre computadores cliente e servidores de Host da Sessão RD durante as conexões de protocolo RDP (RDP). Essa política só se aplica quando você está usando a criptografia RDP nativa. No entanto, a criptografia RDP nativa (em oposição à criptografia SSL) não é recomendada. Esta política não se aplica à criptografia SSL. Se você habilitar essa configuração de política, todas as comunicações entre clientes e servidores de Host da Sessão RD durante conexões remotas deverão usar o método de criptografia especificado nessa configuração. Por padrão, o nível de criptografia é definido como alto. Os seguintes métodos de criptografia estão disponíveis:  
  - *Alto*: A configuração alta criptografa os dados enviados do cliente para o servidor e do servidor para o cliente usando a criptografia de 128 bits forte. Use esse nível de criptografia em ambientes que contêm somente clientes de 128 bits (por exemplo, clientes que executam o Conexão de Área de Trabalho Remota). Os clientes que não suportam esse nível de criptografia não podem se conectar a servidores Host da Sessão RD.  
  - *Compatível com cliente*: A configuração compatível com o cliente criptografa os dados enviados entre o cliente e o servidor na restrição de chave máxima com suporte pelo cliente. Use esse nível de criptografia em ambientes que incluem clientes que não dão suporte à criptografia de 128 bits.  
  - *Baixo*: A configuração baixa criptografa apenas os dados enviados do cliente para o servidor usando a criptografia de 56 bits.  
  
  Se você desabilitar ou não definir essa configuração, o nível de criptografia a ser usado para conexões remotas com Host da Sessão RD servidores não será aplicado por meio de Política de Grupo. A conformidade de FIPS importante pode ser configurada por meio da criptografia do sistema. Use algoritmos compatíveis com FIPS para criptografia, hash e configurações de assinatura no Política de Grupo (em configuração do computador \ \ \ \ Opções de autenticação.) A configuração compatível com FIPS criptografa e descriptografa os dados enviados do cliente para o servidor e do servidor para o cliente, com os algoritmos de criptografia do padrão FIPS (FIPS) 140, usando os módulos de criptografia da Microsoft. Use esse nível de criptografia quando as comunicações entre clientes e servidores de Host da Sessão RD exigirem o nível mais alto de criptografia.
  
  **Padrão**: Alta
  
### <a name="remote-management"></a>Gestão Remota  

Para obter mais informações, consulte [Policy CSP-RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) na documentação do Windows.  

- **Bloquear o armazenamento de credenciais executar como**  
  Autenticação básica do cliente
  
  **Padrão**: Enabled
  
- **Autenticação básica**  
  Essa configuração de política permite que você gerencie se o serviço de Gerenciamento Remoto do Windows (WinRM) aceita a autenticação básica de um cliente remoto. Se você habilitar essa configuração de política, o serviço WinRM aceitará a autenticação básica de um cliente remoto. Se você desabilitar ou não definir essa configuração de política, o serviço WinRM não aceitará a autenticação básica de um cliente remoto.
  
  **Padrão**: Desativado
  
- **Bloquear a autenticação Digest do cliente**  
  Essa configuração de política permite que você gerencie se o cliente do Gerenciamento Remoto do Windows (WinRM) usa a autenticação Digest. Se você habilitar essa configuração de política, o cliente WinRM não usará a autenticação Digest. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM usará a autenticação Digest.
  
  **Padrão**: Enabled
  
- **Tráfego não criptografado**  
  Essa configuração de política permite que você gerencie se o serviço de Gerenciamento Remoto do Windows (WinRM) envia e recebe mensagens não criptografadas pela rede. Se você habilitar essa configuração de política, o cliente WinRM enviará e receberá mensagens não criptografadas pela rede. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM enviará ou receberá somente mensagens criptografadas pela rede.  
  
  **Padrão**: Desativado
  
- **Tráfego de cliente não criptografado**  
  Essa configuração de política permite que você gerencie se o cliente do Gerenciamento Remoto do Windows (WinRM) envia e recebe mensagens não criptografadas pela rede. Se você habilitar essa configuração de política, o cliente WinRM enviará e receberá mensagens não criptografadas pela rede. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM enviará ou receberá somente mensagens criptografadas pela rede.
  
  **Padrão**: Desativado
  
- **Autenticação básica do cliente**  
  Essa configuração de política permite que você gerencie se o cliente do Gerenciamento Remoto do Windows (WinRM) usa a autenticação básica. Se você habilitar essa configuração de política, o cliente WinRM usará a autenticação básica. Se o WinRM estiver configurado para usar o transporte HTTP, o nome de usuário e a senha serão enviados pela rede como texto não criptografado. Se você desabilitar ou não definir essa configuração de política, o cliente WinRM não usará a autenticação básica.
  
  **Padrão**: Desativado
  

### <a name="remote-procedure-call"></a>Chamada de procedimento remoto  

Para obter mais informações, consulte [Policy CSP-RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) na documentação do Windows.  

- **Opções de cliente não autenticado RPC**  
  Essa configuração de política controla como o tempo de execução do servidor RPC lida com clientes RPC não autenticados se conectando a servidores RPC. Essa configuração de política afeta todos os aplicativos RPC. Em um ambiente de domínio, use essa configuração de política com cuidado, pois ela pode afetar uma ampla gama de funcionalidades, incluindo o próprio processamento da diretiva de grupo. A reversão de uma alteração para essa configuração de política pode exigir intervenção manual em cada computador afetado. Essa configuração de política nunca deve ser aplicada a um controlador de domínio. Se você desabilitar essa configuração de política, o tempo de execução do servidor RPC usará o valor "autenticado" no cliente Windows e o valor de "nenhum" em versões do Windows Server que dão suporte a essa configuração de política. Se você não definir essa configuração de política, ela permanecerá desabilitada. O tempo de execução do servidor RPC se comporta como se estivesse habilitado com o valor "autenticado" usado para o cliente Windows e o valor de "nenhum" usado para SKUs de servidor que dão suporte a essa configuração de política. Se você habilitar essa configuração de política, ela direcionará o tempo de execução do servidor RPC para restringir os clientes RPC não autenticados que se conectam a servidores RPC em execução em um computador. Um cliente será considerado um cliente autenticado se usar um pipe nomeado para se comunicar com o servidor ou se usar a segurança RPC. As interfaces RPC que solicitaram especificamente que sejam acessíveis por clientes não autenticados podem estar isentas dessa restrição, dependendo do valor selecionado para essa configuração de política.  
  - *Nenhum* permite que todos os clientes RPC se conectem a servidores RPC em execução no computador no qual a configuração de política é aplicada. 
  - *Autenticado* permite que somente clientes RPC autenticados (de acordo com a definição acima) se conectem a servidores RPC em execução no computador no qual a configuração de política é aplicada. As isenções são concedidas a interfaces que as solicitaram. 
  - *Autenticado sem exceções* permite que somente clientes RPC autenticados (de acordo com a definição acima) se conectem a servidores RPC em execução no computador no qual a configuração de política é aplicada. Nenhuma exceção é permitida. Nota: Essa configuração de política não será aplicada até que o sistema seja reinicializado.  

  **Padrão**: Autenticado

### <a name="search"></a>Pesquisa  

Para obter mais informações, consulte [CSP da política – Pesquisar](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) na documentação do Windows.  

- **Desabilitar a indexação de itens criptografados**  
  Permite ou proíbe a indexação de itens. Essa opção é para o indexador do Windows Search, que controla se ele indexará itens que são criptografados, como os arquivos protegidos por WIP (proteção de informações do Windows). Quando a política está ativada, os itens protegidos pelo WIP são indexados e os respetivos metadados são armazenados numa localização não encriptada. Os metadados incluem conteúdos como o caminho do ficheiro e a data de modificação. Quando a política estiver desabilitada, os itens protegidos por WIP não serão indexados e não aparecerão nos resultados na Cortana ou no explorador de arquivos. O desempenho das aplicações de fotografias e do Groove também poderá ser afetado se existirem muitos ficheiros multimédia protegidos pelo WIP no dispositivo.
  
**Padrão**: Sim
  
### <a name="smart-screen"></a>Tela inteligente  

Para obter mais informações, consulte [CSP da política-SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) na documentação do Windows.  

- **Bloquear a execução de arquivos não verificados**  
  Impedir que o usuário execute arquivos não verificados. 
  - *Não configurado* -os funcionários podem ignorar os avisos do SmartScreen e executar arquivos mal-intencionados. 
  - *Sim* – os funcionários não podem ignorar avisos do SmartScreen e executar arquivos mal-intencionados.

  **Padrão**: Sim

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **Exigir SmartScreen para aplicativos e arquivos**  
  Permite que os administradores de ti configurem o SmartScreen para Windows.

  **Padrão**: Sim
  
### <a name="system"></a>Sistema  

Para obter mais informações, consulte [CSP da política – sistema](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) na documentação do Windows.  

- **Inicialização do driver iniciar inicialização do sistema**  
  Essa configuração de política permite que você especifique quais drivers de inicialização inicial são inicializados com base em uma classificação determinada por um driver de inicialização de antimalware de início antecipado. O driver de inicialização de antimalware de início antecipado pode retornar as seguintes classificações para cada driver de inicialização inicial: 
  - *Bom*: O driver foi assinado e não foi adulterado.  
  - *Mal* -o driver foi identificado como malware. Recomendamos que você não permita que drivers inválidos conhecidos sejam inicializados. 
  - *Inadequado, mas necessário para a inicialização*: O driver foi identificado como malware, mas o computador não pode ser inicializado com êxito sem carregar este driver. 
  - *Desconhecido* -este driver não foi atestado pelo seu aplicativo de detecção de malware e não foi classificado pelo driver de inicialização de antimalware de início antecipado.  

  Se você habilitar essa configuração de política, poderá escolher quais drivers de inicialização inicial serão inicializados na próxima vez em que o computador for iniciado. Se você desabilitar ou não definir essa configuração de política, os drivers de início de inicialização determinoum ser bons, desconhecidos ou ruins, mas a inicialização crítica será inicializada e a inicialização de drivers determinados como defeituosos será ignorada. Se o seu aplicativo de detecção de malware não incluir um driver de inicialização de antimalware de início antecipado ou se o driver de inicialização de antimalware de início antecipado tiver sido desabilitado, essa configuração não terá nenhum efeito e todos os drivers de inicialização iniciada serão inicializados.  
  
  **Padrão**: Bom desconhecido e crítico ruim


### <a name="wi-fi"></a>Wi-Fi  

Para obter mais informações, consulte [Policy CSP-WiFi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) na documentação do Windows.  

- **Bloquear compartilhamento de Internet**  
  Especifica se o compartilhamento da Internet é possível no dispositivo.  

  **Padrão**: Sim  

- **Bloquear a conexão automática a hotspots Wi-Fi**  
  Permitir ou impedir que o dispositivo se conecte automaticamente a hotspots Wi-Fi.  

  **Padrão**: Sim  
  
### <a name="windows-connection-manager"></a>Gerenciador de conexões do Windows  

Para obter mais informações, consulte [Policy CSP-WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) na documentação do Windows.  

- **Bloquear conexão a redes que não são de domínio**  
  Essa configuração de política impede que os computadores se conectem a uma rede baseada em domínio e a uma rede não baseada em domínio ao mesmo tempo. Se essa configuração de política estiver habilitada, o computador responderá a tentativas automáticas e manuais de conexão de rede com base nas seguintes circunstâncias: 
  - Tentativas de conexão automática quando o computador já está conectado a uma rede baseada em domínio, todas as tentativas de conexão automática para redes que não são de domínio são bloqueadas. Quando o computador já estiver conectado a uma rede não baseada em domínio, as tentativas de conexão automática para redes baseadas em domínio serão bloqueadas. 
  - Tentativas de conexão manual quando o computador já está conectado a uma rede não baseada em domínio ou a uma rede baseada em domínio por meio de mídia diferente de Ethernet, e um usuário tenta criar uma conexão manual com uma rede adicional em violação dessa política configuração, a conexão de rede existente é desconectada e a conexão manual é permitida. Quando o computador já estiver conectado a uma rede não baseada em domínio ou a uma rede baseada em domínio pela Ethernet, e um usuário tentar criar uma conexão manual com uma rede adicional em violação dessa configuração de política, a conexão Ethernet existente será mantido e a tentativa de conexão manual é bloqueada.  

  Se essa configuração de política não estiver configurada ou estiver desabilitada, os computadores terão permissão para se conectar simultaneamente a redes de domínio e fora do domínio.  

  **Padrão**: Enabled
  
### <a name="windows-defender"></a>Windows Defender  

Para obter mais informações, consulte [Policy CSP-defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) na documentação do Windows.  

- **Examinar mensagens de email recebidas**  
  Permite ou não a verificação de email.
  
  **Padrão**: Sim  

- **Tipo de processo filho de lançamento de aplicativos do Office**  
  Os aplicativos do Office não terão permissão para criar processos filho. Isso inclui o Word, o Excel, o PowerPoint, o OneNote e o Access. Esse é um comportamento típico de malware, especialmente para ataques baseados em macro que tentam usar aplicativos do Office para iniciar ou baixar executáveis mal-intencionados.
  
  **Padrão**: Bloquear
  
- **Tipo de consentimento de envio de amostra do defender**  
  Verifica o nível de consentimento do usuário no Windows Defender para enviar dados. Se o consentimento necessário já tiver sido concedido, o Windows defender os enviará. Caso contrário, (e se o usuário tiver especificado nunca perguntar), a interface do usuário será iniciada para solicitar o consentimento do usuário (quando o defender/AllowCloudProtection for permitido) antes de enviar dados.
  
  **Padrão**: Enviar amostras seguras automaticamente 
  
- **Intervalo de atualização de assinatura (em horas)**  
  Intervalo de atualização de assinatura do defender em horas
  
  **Padrão**: 4
  
- **Tipo de execução de conteúdo baixado por script**  
  Tipo de execução de conteúdo baixado do defender script
  
  **Padrão**: Bloquear
  
- **Impedir tipo de roubo de credencial**  
  O Windows Defender Credential Guard usa segurança baseada em virtualização para isolar segredos para que somente o software de sistema privilegiado possa acessá-los. O acesso não autorizado a estes segredos pode levar a ataques de roubo de credenciais, tal como Ataques PtH ou PtT. O Windows Defender Credential Guard impede esses ataques ao proteger os hashes de senha NTLM, tíquetes de concessão de permissão Kerberos e credenciais armazenadas por aplicativos como credenciais de domínio.
  
  **Padrão**: Ativar

- **Tipo de execução de conteúdo de email**  
  Essa regra impede que os seguintes tipos de arquivo sejam executados ou iniciados de um email visto no Microsoft Outlook ou webmail (como Gmail.com ou Outlook.com): Arquivos de script executáveis (como. exe,. dll ou. SCR) (como um arquivo PowerShell. PS, VisualBasic. vbs ou JavaScript. js).
  
  **Padrão**: Bloquear
  
- **Tipo de proteção de rede**  
  Essa política permite ativar a proteção de rede (bloquear/auditar) ou desativado no Windows Defender Exploit Guard. A proteção de rede é um recurso do Windows Defender Exploit Guard que protege os funcionários que usam qualquer aplicativo de acessar golpes de phishing, sites de Hospedagem de exploração e conteúdo mal-intencionado na Internet. Isso inclui impedir que navegadores de terceiros se conectem a sites perigosos. O tipo de valor é inteiro. Se você habilitar essa configuração, a proteção de rede será ativada e os funcionários não poderão desativá-la. Seu comportamento pode ser controlado pelas seguintes opções: Bloquear e auditar. Se você habilitar essa política com a opção "bloquear", os usuários e aplicativos serão impedidos de se conectar a domínios perigosos. Você pode ver essa atividade na central de segurança do Windows Defender. Se você habilitar essa política com a opção "auditoria", os usuários/aplicativos não serão impedidos de se conectar a domínios perigosos. No entanto, você ainda verá essa atividade na central de segurança do Windows Defender. Se você desabilitar essa política, os usuários/aplicativos não serão impedidos de se conectar a domínios perigosos. Você não verá nenhuma atividade de rede na central de segurança do Windows Defender. Se você não configurar essa política, o bloqueio de rede será desabilitado por padrão.
  
  **Padrão**: Ativar
  
- **Dia da verificação de agenda do defender**  
  Dia da verificação de agenda do defender.
  
  **Padrão**: Todos os dias
  
- **Proteção entregue na nuvem**  
  Para proteger melhor seu PC, o Windows Defender enviará informações à Microsoft sobre quaisquer problemas encontrados. A Microsoft analisará essas informações, aprenderá mais sobre problemas que afetam você e outros clientes, além de oferecer soluções aprimoradas.
  
  **Padrão**:  Sim  

- **Ação de aplicativo potencialmente indesejado defender**  
  O recurso de proteção de aplicativo potencialmente indesejado (PUA) no Windows Defender antivírus pode identificar e bloquear o download e a instalação do PUAs em pontos de extremidade em sua rede. Esses aplicativos não são considerados vírus, malware ou outros tipos de ameaças, mas podem executar ações em pontos de extremidade que afetam negativamente o desempenho ou o uso. O PUA também pode se referir a aplicativos que são considerados uma má reputação. O comportamento típico do PUA inclui: Vários tipos de injeção de anúncios de agrupamento de software em navegadores da Web driver e otimizadores de registro que detectam problemas, solicitam o pagamento para corrigir os erros, mas permanecem no ponto de extremidade e não fazem alterações ou otimizações (também conhecidas como programas "antivírus não autorizados"). Esses aplicativos podem aumentar o risco de sua rede ser infectada com malware, fazer com que as infecções de malware sejam mais difíceis de identificar e podem desperdiçar recursos de ti para limpar os aplicativos.  
  
  **Padrão**: Bloquear  

- **Script de tipo de código de macro ofuscado**  
  Malware e outras ameaças podem tentar ofuscar ou ocultar seu código mal-intencionado em alguns arquivos de script. Essa regra impede que os scripts que parecem estar ofuscados sejam executados.
  
  **Padrão**: Bloquear
  
- **Verificar unidades removíveis durante uma verificação completa**  
  Permite que o Windows Defender Verifique se há software mal-intencionado e indesejado em unidades removíveis (por exemplo, unidades flash) durante uma verificação completa. O Windows Defender antivírus examina todos os arquivos em dispositivos USB antes da execução.
  
  **Padrão**: Sim  
  
- **Analisar ficheiros de arquivo**  
  Defender verificar arquivos mortos.
  
  **Padrão**: Sim
  
- **Monitoramento de comportamento**  
  Permite ou não a funcionalidade de monitoramento de comportamento do Windows Defender. Inserido no Windows 10, esses sensores coletam e processam sinais comportamentais do sistema operacional e enviam esses dados de sensor para sua instância privada, isolada e de nuvem do Microsoft defender ATP.
  
  **Padrão**: Sim

- **Verificar arquivos abertos de pastas de rede**  
  Se os arquivos forem somente leitura, o usuário não poderá remover nenhum malware detectado.
  
  **Padrão**: Sim

- **Tipo de processo USB não confiável**  
  Com essa regra, os administradores podem impedir que arquivos executáveis não assinados ou não confiáveis sejam executados a partir de unidades removíveis USB, incluindo cartões SD.
  
  **Padrão**: Bloquear
  
- **Outro tipo de injeção de processo de aplicativos do Office**  
  Os aplicativos do Office, incluindo o Word, o Excel, o PowerPoint e o OneNote, não poderão injetar código em outros processos. Normalmente, isso é usado por malware para executar código mal-intencionado em uma tentativa de ocultar a atividade de mecanismos de verificação antivírus.
  
  **Padrão**:  Bloquear
  
- **Código de macro do Office permitir tipo de importações do Win32**  
  O malware pode usar o código de macro em arquivos do Office para importar e carregar as DLLs do Win32, que podem ser usadas para fazer chamadas à API para permitir uma infecção adicional em todo o sistema. Essa regra tenta bloquear os arquivos do Office que contêm o código de macro que é capaz de importar as DLLs do Win32. Isso inclui o Word, o Excel, o PowerPoint e o OneNote.
  
  **Padrão**: Bloquear  
  
- **Nível de bloco do defender Cloud**  
  Nível de bloco do defender Cloud.
  
  **Padrão**: Não Configurado

- **Monitoramento em tempo real**  
  O defender requer monitoramento em tempo real.
  
  **Padrão**: Sim
  
- **Criação de conteúdo executável de aplicativos do Office ou tipo de inicialização**  
  Essa regra destina-se a comportamentos típicos usados por Complementos suspeitos e mal-intencionados e scripts (extensões) que criam ou iniciam arquivos executáveis. Essa é uma técnica típica de malware. As extensões são impedidas de serem usadas pelos aplicativos do Office. Normalmente, essas extensões usam o Windows Scripting Host (arquivos. WSH) para executar scripts que automatizam determinadas tarefas ou fornecem recursos complementares criados pelo usuário
  
  **Padrão**: Bloquear

### <a name="windows-ink-workspace"></a>Espaço de trabalho do Windows Ink  

Para obter mais informações, consulte [Policy CSP-WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) na documentação do Windows.  

- **Espaço de trabalho de tinta**  
  Especifica se deve permitir que o usuário acesse o espaço de trabalho de tinta. 
  - *Desabilitado* -o acesso ao espaço de trabalho de tinta está desabilitado. O recurso está desativado.
  - *Habilitado* – o recurso de espaço de trabalho de tinta está ativado, mas o usuário não pode acessá-lo acima da tela de bloqueio.
  - *Não configurado* -o recurso de espaço de trabalho de tinta está ativado e o usuário pode usá-lo acima da tela de bloqueio.  

  **Padrão**: Enabled
 
### <a name="windows-powershell"></a>Windows PowerShell  

Para obter mais informações, consulte [Policy CSP-WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) na documentação do Windows.  

- **Log do bloco de script do shell do Power Shell**  
  Essa configuração de política habilita o log de todas as entradas de script do PowerShell para o log de eventos Microsoft-Windows-PowerShell/Operational. Se você habilitar essa configuração de política, o Windows PowerShell registrará em log o processamento de comandos, blocos de script, funções e scripts – sejam invocados interativamente ou através da automação. Se você desabilitar essa configuração de política, o log da entrada de script do PowerShell será desabilitado. Se você habilitar o log de invocação de bloco de script, o PowerShell também registrará eventos quando a invocação de um comando, bloco de script, função ou script iniciar ou parar. Habilitar o log de invocação gera um alto volume de logs de eventos. Nota: Essa configuração de política existe sob configuração do computador e configuração do usuário no editor de Política de Grupo. A configuração da política de configuração do computador tem precedência sobre a configuração de política de configuração de usuário.
  
  **Padrão**: Enabled
 
## <a name="next-steps"></a>Passos seguintes  

[Exibir a versão de linha de base atual](security-baseline-settings-mdm.md)  
[Atualizar perfis para usar uma nova versão de linha de base](security-baselines.md#change-the-baseline-instance-for-a-profile)