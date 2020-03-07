---
title: Definições de proteção para dispositivos Windows 10 no Microsoft Intune - Azure Microsoft Docs
description: Nos dispositivos Windows 10, utilize ou configure as definições de proteção de pontos finais para ativar as funcionalidades do Microsoft Defender, incluindo O Guarda de Aplicações, Firewall, SmartScreen, encriptação e BitLocker, Exploit Guard, Control de Aplicações, Centro de Segurança e Segurança em dispositivos locais em Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: mattsha
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 467e347a84cef1fb7ac302da5a4264f23b4be5a2
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78368488"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Definições do Windows 10 (e mais tarde) para proteger dispositivos que utilizem Intune

O Microsoft Intune inclui muitas definições para ajudar a proteger os seus dispositivos. Este artigo descreve todas as definições que pode ativar e configurar no Windows 10 e em dispositivos mais recentes. Estas definições são criadas num perfil de configuração de proteção de ponto final em Intune para controlar a segurança, incluindo BitLocker e Microsoft Defender.  

Para configurar o Antivírus Microsoft Defender, consulte [as restrições do dispositivo Do Windows 10](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).  

## <a name="before-you-begin"></a>Antes de começar  

Crie um perfil de configuração do dispositivo de [proteção de pontofinal](endpoint-protection-configure.md).  

Para obter mais informações sobre os prestadores de serviços de configuração (CSPs), consulte a referência do prestador de serviços de [configuração](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="microsoft-defender-application-guard"></a>Guarda de aplicações do Microsoft Defender  

Ao utilizar o Microsoft Edge, o Microsoft Defender Application Guard protege o seu ambiente de sites que não são confiáveis pela sua organização. Quando os utilizadores visitam sites que não estão listados no limite da rede isolada, os sites abrem-se numa sessão de navegação virtual Hyper-V. Os sites fidedignos são definidos por um limite de rede, que são configurados na Configuração do Dispositivo.  

O Application Guard só está disponível para dispositivos com o Windows 10 (64 bits). Se utilizar este perfil, instalará um componente do Win32 para ativar o Application Guard.  

- **Guarda de Aplicações**  
  **Predefinição**: Não configurado  
   Guarda de aplicações CSP: [Definições/Permitirguardadedefender](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Ativado para Edge** - Liga esta funcionalidade, que abre sites não confiáveis num recipiente de navegação virtualizado Hyper-V.  
  - **Não configurado** - Qualquer site (confiável e não confiável) pode abrir no dispositivo.  

- **Comportamento de clipboard**  
  **Predefinição**: Não configurado  
   Application Guard CSP: [Definições/Definições de clipboard](https://go.microsoft.com/fwlink/?linkid=872351)  

  Escolha quais as ações de cópia e pasta que são permitidas entre o PC local e o navegador virtual Application Guard.  
  - **Não configurado**  
  - **Permitir copiar e colar do PC para o navegador apenas**  
  - **Permitir copiar e colar do navegador para PC apenas**  
  - **Permitir cópia e pasta entre PC e browser**  
  - **Cópia e pasta de blocos entre PC e browser**  

- **Conteúdo de clipboard**  
  Esta definição só está disponível quando o comportamento da *clipboard* estiver definido para uma das definições de *permitir.*  
  **Predefinição**: Não configurado  
  Resguardo de aplicação CSP: [Definições/ClipboardFileTypeType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Selecione o conteúdo permitido da pasta.  
  - **Não configurado**  
  - **Texto**  
  - **Imagens**  
  - **Texto e imagens**  

- **Conteúdo externo em sites empresariais**  
  **Predefinição**: Não configurado  
  Guarda de aplicações CSP: [Definições/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **Bloco** - Bloqueie o conteúdo de sites não aprovados a partir do carregamento.  
  - **Não configurados** - Os sites não empresariais podem abrir no dispositivo.  
 
- **Imprimir a partir do navegador virtual**  
  **Predefinição**: Não configurado  
  Guarda de aplicação CSP: [Definições/Definições de Impressão](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Permitir** - Permite a impressão de conteúdo selecionado a partir do navegador virtual.  
  - **Não configurado** Desative todas as funcionalidades de impressão.  

  Quando *permitir a* impressão, pode configurar a seguinte definição:
  - **Tipo de impressão(s)** Selecione uma ou mais das seguintes opções:  
    - PDF  
    - XPS  
    - Impressoras locais
    - Impressoras de rede  

- **Recolher registos**  
  **Predefinição**: Não configurado  
  Application Guard CSP: [Auditoria/AuditoriaApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Permitir** - Recolher registos para eventos que ocorram dentro de uma sessão de navegação da Guarda de Aplicações.  
  - **Não configurado** - Não recolha nenhum registo dentro da sessão de navegação.  

- **Reter dados de navegador gerados pelo utilizador**  
  **Predefinição**: Não configurado  
  Guarda de aplicação CSP: [Configurações/Persistência de Permitir](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Permitir** Guarde os dados dos utilizadores (como palavras-passe, favoritos e cookies) que são criados durante uma sessão de navegação virtual do Application Guard.  
  - **Não configurado** Elimine os ficheiros e dados descarregados pelo utilizador quando o dispositivo recomeçar, ou quando um utilizador se signa.  

- **Aceleração gráfica**  
 **Predefinição**: Não configurado  
  Guarda de aplicação CSP: [Configurações/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **Enable** - Carregue sites e vídeo com grande intensidade gráfica mais rapidamente, obtendo acesso a uma unidade de processamento de gráficos virtuais.  
  - **Não configurado** Utilize o CPU do dispositivo para gráficos; Não utilize a unidade de processamento de gráficos virtuais.  

- **Descarregue ficheiros para o sistema de ficheiros anfitrião**  
  **Predefinição**: Não configurado  
  Guarda de aplicação CSP: [Definições/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Enable** - Os utilizadores podem descarregar ficheiros do navegador virtualizado para o sistema operativo anfitrião.  
  - **Não configurado** - Mantém os ficheiros locais no dispositivo e não descarrega ficheiros para o sistema de ficheiros do anfitrião.  

## <a name="microsoft-defender-firewall"></a>Microsoft Defender Firewall  
 
### <a name="global-settings"></a>Definições globais  

Estas definições são aplicáveis a todos os tipos de rede.  

- **Protocolo de Transferência de Ficheiros**  
  **Predefinição**: Não configurado  
   Firewall CSP: [MdmStore/Global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **Bloco** - Desativar ftp audato.  
  - **Não configurado** - A firewall faz filtragem de FTP imponente para permitir ligações secundárias.  

- **Associação de segurança tempo inativo antes da eliminação**  
  **Predefinição**: *Não configurado*  
   Firewall CSP: [MdmStore/Global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   Especifique um tempo de inatividade em segundos, após o qual as associações de segurança são eliminadas.   

- **Codificação de chaves pré-partilhadas**  
  **Predefinição**: Não configurado  
   Firewall CSP: [MdmStore/Global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Ativar** - Encódigo as teclas pré-sheard utilizando uTF-8.  
   - **Não configurado** - Encódigo as teclas pré-sheard utilizando o valor da loja local.  

- **Isenções IPsec**  
  **Predefinição**: *0 selecionado*  
   Firewall CSP: [MdmStore/Global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   Selecione um ou mais dos seguintes tipos de tráfego a ficarem isentos do IPsec:  
   - **Descoberta de vizinho de códigos do tipo IPv6 ICMP**  
   - **ICMP**  
   - **Descoberta de router de códigos do tipo IPv6 ICMP**  
   - **Tráfego de rede de IPv4 e IPv6 DHCP**  

- **Verificação da lista de revogação do certificado**  
  **Predefinição**: Não configurado  
  Firewall CSP: [MdmStore/Global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  Escolha como o dispositivo verifica a lista de revogação do certificado. As opções incluem:  
  - **Desativar a verificação de CRL**  
  - **Falhar a verificação do CRL apenas no certificado revogado**  
  - **Falhar a verificação de CRL em qualquer erro encontrado**.  
 

- **Oportunisticamente correspondem ao conjunto de autenticação por módulo de teclas**  
  **Predefinição**: Não configurado  
  Firewall CSP: [MdmStore/Global/OportunistaMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Ativar** Os módulos de teclagem devem ignorar apenas as suites de autenticação que não suportam.  
  - **Não configurados**, Os módulos de chave devem ignorar todo o conjunto de autenticação se não suportarem todas as suites de autenticação especificadas no conjunto.  


- **Fila de pacotes**  
  **Predefinição**: Não configurado  
  Firewall CSP: [Mdmstore/Global/EnablePacketqueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Especifique como o software de dimensionamento no lado de receção está ativado para a receção encriptada e texto claro para a frente para o cenário de gateway do túnel IPsec. Esta definição confirma que a ordem do pacote está preservada. As opções incluem:  
  - **Não configurado**  
  - **Desativar todas as filas de pacotes**  
  - **Fila de pacotes encriptados de entrada**  
  - **Pacotes de fila após desencriptação é realizado apenas para reencaminhamento**  
  - **Configure os pacotes de entrada e saída**  

### <a name="network-settings"></a>Definições de rede  

As seguintes definições são listadas neste artigo uma única vez, mas todas se aplicam aos três tipos específicos de rede:  
- **Rede de domínio (local de trabalho)**  
- **Rede privada (detetável)**  
- **Rede pública (não descoberta)**  

#### <a name="general-settings"></a>Definições gerais  

- **Microsoft Defender Firewall**  
  **Predefinição**: Não configurado  
  Firewall CSP: [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Ativar** - Ligue a firewall e segurança avançada. 
  - **Não configurado** Permite todo o tráfego de rede, independentemente de quaisquer outras definições de política.  

- **Modo stealth**  
  **Predefinição**: Não configurado  
  Firewall CSP: [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **Não configurado**  
  - **Bloco** - Firewall está bloqueado de funcionar em modo furtivo. Esta definição também lhe permite bloquear a **Exceção de pacotes seguros com IPsec**.  
  - **Permitir** - A firewall funciona em modo furtivo, o que ajuda a evitar respostas a pedidos de sondagem.  

- **Isenção de pacote garantido iPsec com modo stealth**  
  **Predefinição**: Não configurado  
  Firewall CSP: [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Esta opção é ignorada se o *modo Stealth* estiver definido para *bloquear*.  

  - **Não configurado**  
  - **Bloco** - Pacotes garantidos IPSec não recebem isenções.  
  - **Permitir** - Permitir isenções. O modo de stealth da firewall NÃO DEVE IMPEDIR que o computador hospedeiro responda ao tráfego de rede não solicitado que é protegido pelo IPsec.  

- **Protegido**  
  **Predefinição**: Não configurado  
  Firewall CSP: [Blindado](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **Não configurado**  
    - **Bloco** - Quando o Microsoft Defender Firewall estiver ligado e esta definição estiver definida para *bloquear*, todo o tráfego de entrada está bloqueado, independentemente de outras definições de política. 
    - **Permitir** - Quando definido para *permitir*, esta definição é desligada - e o tráfego de entrada é permitido com base em outras definições de política.

- **Respostas unicast a emissões multicast**  
  **Predefinição**: Não configurado  
  Firewall CSP: [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  Normalmente, não quer receber respostas unicast para mensagens multicast ou de difusão. Estas respostas podem indicar um ataque de negação de serviço (DOS) ou um intruso que tenta sondar um computador ao vivo conhecido.  
  - **Não configurado**  
  - **Bloco** - Desative as respostas unicast a emissões multicast.  
  - **Permitir** - Permitir respostas unicast a emissões multicast.  

- **Notificações de entrada**  
  **Predefinição**: Não configurado  
  Firewall CSP: [Desativar Notificações](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **Não configurado**  
  - **Block** - Ocultar notificações para utilizações quando uma aplicação está bloqueada de ouvir numa porta.  
  - **Permitir** - Permite esta definição e pode apresentar uma notificação aos utilizadores quando uma aplicação está bloqueada de ouvir numa porta.  

- **Ação predefinida para ligações de saída**  
  **Predefinição**: Não configurado  
  Firewall CSP: [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  Configure a firewall de ação predefinida e executa em ligações de saída. Esta definição será aplicada na versão 1809 do Windows ou superior.  

  - **Não configurado**  
  - **Bloco** - A ação de firewall padrão não é executada no tráfego de saída a menos que seja explicitamente especificado para não bloquear.  
  - **Permitir** - As ações de firewall padrão funcionam em ligações de saída.  

- **Ação predefinida para ligações de entrada**  
  **Predefinição**: Não configurado  
  Firewall CSP: [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **Não configurado**  
  - **Bloco** - A ação de firewall padrão não é executada em ligações de entrada.  
  - **Permitir** - As ações de firewall padrão funcionam em ligações de entrada.  

#### <a name="rule-merging"></a>Intercalação de regras  

- **Aplicação autorizada Microsoft Defender Firewall regras da loja local**  
  **Predefinição**: Não configurado  
  Firewall CSP: [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **Não configurado**  
  - **Bloco** - As regras de firewall de aplicação autorizadas na loja local são ignoradas e não aplicadas.  
  - **Permitir** -
   Escolher **Ativar** aplica regras de firewall na loja local para que sejam reconhecidas e executadas.  

- **Regras globais da Microsoft Defender Firewall da loja local**  
  **Predefinição**: Não configurado  
  Firewall CSP: [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **Não configurado**  
  - **Bloco** - As regras globais de firewall portuário na loja local são ignoradas e não aplicadas.  
  - **Permitir** - Aplicar regras globais de firewall portuário na loja local para ser reconhecido e aplicado.  

- **Regras do Microsoft Defender Firewall da loja local**  
  **Predefinição**: Não configurado  
  Firewall CSP: [Permitir fusão política local](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **Não configurado**  
  - **Bloco** - As regras de firewall da loja local são ignoradas e não aplicadas.
  - **Permitir** - Aplicar regras de firewall na loja local para ser reconhecido e aplicado.  

- **Regras iPsec da loja local**  
  **Predefinição**: Não configurado  
  Firewall CSP: [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **Não configurado**  
  - **Bloco** - As regras de segurança de ligação da loja local são ignoradas e não aplicadas, independentemente da versão do esquema e da versão da regra de segurança de ligação.  
  - **Permitir** - Aplicar regras de segurança de ligação a partir da loja local, independentemente das versões de regras de segurança de esquemas ou de ligação.  

### <a name="firewall-rules"></a>Regras de firewall  

Pode **adicionar** uma ou mais regras personalizadas de Firewall. Para mais informações, consulte [Adicionar regras de firewall personalizadas para dispositivos Windows 10](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

As regras de Firewall personalizadas suportam as seguintes opções:  

#### <a name="general-settings"></a>Definições gerais:  

- **Nome**  
  **Predefinição**: *Sem nome*  

  Especifique um nome amigável para a sua regra. Este nome aparecerá na lista de regras para ajudá-lo a identificá-lo.  

- **Descrição**  
  **Predefinição**: *Nenhuma descrição*  

  Forneça uma descrição da regra.  

- **Direção**   
  **Predefinição**: Não configurado  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/Direção](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Especifique se esta regra se aplica ao tráfego **de entrada**ou **saída.** Quando definida como **Não configurada,** a regra aplica-se automaticamente ao tráfego de saída.  

- **Ação**  
  **Predefinição**: Não configurado  
  Firewall CSP: [FirewallRules /*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action), and [*FirewallRulesName*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Selecione a partir de **Permitir** ou **Bloquear**. Quando definida como **Não configurada,** a regra não se define para permitir o tráfego.  

- **Tipo de rede**  
  **Predefinição**: 0 selecionado  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/Perfis](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Selecione até três tipos de tipos de rede aos quais esta regra pertence. As opções incluem **Domínio,** **Privado**e **Público.**  Se não forem selecionados tipos de rede, a regra aplica-se aos três tipos de rede.  

#### <a name="application-settings"></a>Definições da aplicação  

- **Aplicação(s)**  
  **Padrão**: Todos  

  Controlar as ligações para uma aplicação ou programa. Selecione uma das seguintes opções e, em seguida, complete a configuração adicional:  
  - **Nome de família pacote** - Especifique um nome de família pacote. Para encontrar o nome da família do pacote, utilize o comando PowerShell **Get-AppxPackage**.   
    Firewall CSP: [FirewallRules/*FirewallRuleName*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - Caminho de **ficheiros** – Deve especificar um caminho de ficheiro para uma aplicação no dispositivo cliente, que pode ser um caminho absoluto, ou um caminho relativo. Por exemplo: C:\Windows\System\Notepad.exe ou %WINDIR%\Notepad.exe.  
    Firewall CSP: [FirewallRules/*FirewallRuleName*/App/Filepath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Serviço Windows** – Especifique o nome curto do serviço Windows se for um serviço e não uma aplicação que envie ou receba tráfego. Para encontrar o nome curto do serviço, utilize o comando PowerShell **Get-Service**.  
    Firewall CSP: [FirewallRules/*FirewallRuleName*/App/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Tudo**– *Não existe nenhuma configuração adicional.*  

#### <a name="ip-address-settings"></a>Definições de endereço IP  

Especifique os endereços locais e remotos a que esta regra se aplica.  

- **Endereços locais**    
  **Predefinição**: Qualquer endereço  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Selecione **qualquer endereço** ou **endereço especificado**.  

  Quando utilizar *o endereço Especificado,* adicione um ou mais endereços como uma lista separada de vírpostas de endereços locais abrangidos pela regra. Fichas válidas incluem:  
  - Use um asterisco "*" para *qualquer* endereço local. Se usar um asterisco, deve ser o único símbolo que usa.  
  - Para especificar uma sub-rede, utilize a máscara de sub-rede ou a notação prefixo da rede. Se não for especificada uma máscara de sub-rede nem um prefixo de rede, a máscara de sub-rede não se aplica a 255.255.255.255.  
  - Um endereço IPv6 válido.  
  - Uma gama de endereços IPv4 no formato de "iniciar endereço - endereço final" sem espaços incluídos.  
  - Uma gama de endereços IPv6 no formato de "iniciar endereço - endereço final" sem espaços incluídos.  

- **Endereços remotos**  
  **Predefinição**: Qualquer endereço  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Selecione **qualquer endereço** ou **endereço especificado**.  

  Quando utilizar *o endereço Especificado,* adicione um ou mais endereços como uma lista separada de endereços remotos que estão abrangidos pela regra. Tokens não são sensíveis ao caso. Fichas válidas incluem:  
  - Utilize um asterisco "*" para *qualquer* endereço remoto. Se usar um asterisco, deve ser o único símbolo que usa.  
  - "Defaultgateway"  
  - "DHCP"  
  - "DNS"  
  - "VITÓRIAS"  
  - "Intranet" (suportado nas versões 1809 do Windows e posteriormente)  
  - "RmtIntranet" (suportado nas versões Windows 1809 e posteriormente)  
  - "Internet" (suportado nas versões 1809 do Windows e mais tarde)  
  - "Ply2Renders" (suportado nas versões 1809 do Windows e posteriormente)  
  - "LocalSubnet" indica qualquer endereço local na subnet local.  
  - Para especificar uma sub-rede, utilize a máscara de sub-rede ou a notação prefixo da rede. Se não for especificada uma máscara de sub-rede nem um prefixo de rede, a máscara de sub-rede não se aplica a 255.255.255.255.  
  - Um endereço IPv6 válido.  
  - Uma gama de endereços IPv4 no formato de "iniciar endereço - endereço final" sem espaços incluídos.  
  - Uma gama de endereços IPv6 no formato de "iniciar endereço - endereço final" sem espaços incluídos.  

#### <a name="port-and-protocol-settings"></a>Definições de porto e protocolo  
Especifique as portas locais e remotas a que se aplica esta regra.  

- **Protocolo**  
  **Padrão**: Qualquer  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Selecione a partir do seguinte e complete quaisquer configurações necessárias:  
  - **Tudo** – Não existe nenhuma configuração adicional disponível.  
  - **TCP** – Configure portas locais e remotas. Ambas as opções suportam Todas as portas ou portas especificadas. Introduza as portas especificadas utilizando uma lista separada da vírvia.  
    - **Portas locais** - Firewall CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Portas remotas** - Firewall CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** – Configure portas locais e remotas. Ambas as opções suportam Todas as portas ou portas especificadas. Introduza as portas especificadas utilizando uma lista separada da vírvia.  
    - **Portas locais** - Firewall CSP: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Portas remotas** - Firewall CSP: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Personalizado** – Especifique um número de **protocolo** personalizado de 0 a 255.  

#### <a name="advanced-configuration"></a>Configuração avançada  
- **Tipos de interface**  
  **Predefinição**: 0 selecionado  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Selecione entre as seguintes opções:  
  - **Acesso remoto**  
  - **Sem fios**  
  - **Rede local**  

- **Apenas permitir ligações destes utilizadores**  
  **Predefinição**: Todos os utilizadores *(Predefinições de todas as utilizações quando nenhuma lista é especificada)*  
  Firewall CSP: [FirewallRules/*FirewallRuleName*/Lista de Autorização de Utilizadores Locais](https://aka.ms/intunefirewallauthorizedusers)  

  Especifique uma lista de utilizadores locais autorizados para esta regra. Uma lista de utilizadores autorizados não pode ser especificada se esta regra se aplica a um serviço Windows.  


## <a name="microsoft-defender-smartscreen-settings"></a>Definições do Microsoft Defender SmartScreen  
 
O Microsoft Edge tem de ser instalado no dispositivo.  

- **SmartScreen para apps e ficheiros**  
  **Predefinição**: Não configurado  
   Smartscreen CSP: [Smartscreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **Não configurado** - Desativa a utilização do SmartScreen.  
  - **Ativar** - Ativar o Windows SmartScreen para a execução de ficheiros e executar aplicações. O SmartScreen é um componente anti-phishing e anti-malware baseado na cloud.  

- **Execução de ficheiros não verificados**  
  **Predefinição**: Não configurado  
   SmartScreen CSP: [Smartscreen/PreventoverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Não configurado** - Desativa esta funcionalidade e permite que os utilizadores finais executem ficheiros que não tenham sido verificados.  
  - **Bloquear** - Evitar que os utilizadores finais executem ficheiros que não tenham sido verificados pelo Windows SmartScreen.  

## <a name="windows-encryption"></a>Encriptação do Windows  
 
### <a name="windows-settings"></a>Definições do Windows  

- **Encriptar dispositivos**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [RequiredeviceCrypton](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Requerio** - Insto os utilizadores a ativarem a encriptação do dispositivo. Consoante a edição do Windows e configuração do sistema, poderá ser pedido aos utilizadores:  
    - Para confirmar que a encriptação de outro fornecedor não está ativada.  
    - Seja obrigado a desligar a encriptação bitLocker drive e, em seguida, voltar a ligar o BitLocker.  
  - **Não configurado**  
  
  Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável.  

- **Encriptar cartão de armazenamento (apenas para dispositivos móveis)**  
  *Esta definição aplica-se apenas ao telemóvel do Windows 10.*  
  **Predefinição**: Não configurado  
  BitLocker CSP: [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - **Exija** encriptar quaisquer cartões de armazenamento amovíveis utilizados pelo dispositivo.  
  - **Não configurado** - Não exija encriptação do cartão de armazenamento e não leve o utilizador a ligá-lo.  

### <a name="bitlocker-base-settings"></a>Definições base do BitLocker  

As definições base são definições de BitLocker universais para todos os tipos de unidades de dados. Estas definições gerem as tarefas de encriptação ou opções de configuração de unidades que o utilizador final pode modificar para todos os tipos de unidades de dados.  

- **Aviso para outra encriptação do disco**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [AllowWarningForOtherDiskCrypton](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Block** - Desative o aviso se outro serviço de encriptação do disco estiver no dispositivo.  
  - **Não configurado** - Deixe ser mostrado o aviso para outra encriptação do disco.  

  > [!TIP]  
  > Para instalar o BitLocker automaticamente e silenciosamente num dispositivo que é Azure AD juntou-se e executa o Windows 1809 ou mais tarde, esta definição deve ser definida para *bloquear*. Para mais informações, consulte [silenciosamente o BitLocker nos dispositivos](../protect/encrypt-devices.md#silently-enable-bitlocker-on-devices).

  Quando definido para *bloquear,* pode configurar a seguinte definição:  

  - **Permitir que os utilizadores padrão permitam a encriptação durante o Azure AD Join**  
    *Esta definição aplica-se apenas aos dispositivos Azure Ative Directory (Azure ADJ) e depende da definição anterior, `Warning for other disk encryption`.*  
    **Predefinição**: Não configurado  
    BitLocker CSP: [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Permitir** - Os utilizadores standard (não administradores) podem ativar a encriptação BitLocker quando estão inscritos.  
     - **Não configurados** apenas os Administradores podem ativar a encriptação BitLocker no dispositivo.  

  > [!TIP]  
  > Para instalar o BitLocker automaticamente e silenciosamente num dispositivo que é Azure AD juntou-se e executa o Windows 1809 ou mais tarde, esta definição deve ser definida para *permitir*. Para mais informações, consulte [silenciosamente o BitLocker nos dispositivos](../protect/encrypt-devices.md#silently-enable-bitlocker-on-devices).

- **Configurar métodos de encriptação**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Ativar** - Configure algoritmos de encriptação para sistema operativo, dados e unidades amovíveis.  
  - **Não configurado** - O BitLocker utiliza o XTS-AES 128 bit como método de encriptação padrão, ou utiliza o método de encriptação especificado por qualquer script de configuração.  

  Quando programado para *ativar,* pode configurar as seguintes definições:  

  - **Encriptação para unidades de sistema operativo**  
    **Padrão**: XTS-AES 128 bit  
   
    Escolha o método de encriptação para acionar o sistema operativo. Recomendamos que utilize o algoritmo XTS-AES.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

  - **Encriptação para unidades de dados fixas**  
    **Padrão**: AES-CBC 128-bit  
   
    Escolha o método de encriptação para unidades de dados fixas (incorporadas). Recomendamos que utilize o algoritmo XTS-AES.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

  - **Encriptação para unidades de dados amovíveis**  
    **Padrão**: AES-CBC 128-bit  

    Escolha o método de encriptação para unidades de dados amovíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker  

Estas definições aplicam-se especificamente a unidades de dados do sistema operativo.  

- **Autenticação adicional no arranque**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Exigir** - Configurar os requisitos de autenticação para o arranque do computador, incluindo a utilização do Módulo plataforma fidedigna (TPM).  
  - **Não configurado** - Configure apenas opções básicas em dispositivos com um TPM.  

  Quando definido para *exigir,* pode configurar as seguintes definições:  

  - **BitLocker com chip do TPM não compatível**  
    **Predefinição**: Não configurado  

    - **Block** - Desative a utilização do BitLocker quando um dispositivo não tem um chip TPM compatível.  
    - **Não configurado** - Os utilizadores podem utilizar o BitLocker sem um chip TPM compatível. O BitLocker poderá precisar de uma palavra-passe ou de uma chave de arranque.  

  - **Startup TPM compatível**  
    **Padrão**: Permitir TPM  

    Configure se o TPM for permitido, obrigatório ou não permitido.  

    - **Permitir TPM**  
    - **Não permita tPM**  
    - **Exigir TPM**  

  - **PIN de arranque tpm compatível**  
    **Predefinição**: Permitir o PIN de arranque com o TPM  

    Opte por permitir, não permitir ou exigir a utilização de um PIN de arranque com o chip TPM. Para ativar um PIN de arranque, é necessária interação por parte do utilizador final.  

    - **Permitir pin de arranque com TPM**  
    - **Não permita o PIN de arranque com TPM**  
    - **Requerer pin de arranque com TPM**

    > [!TIP]
    > Para instalar o BitLocker automaticamente e silenciosamente num dispositivo que é Azure AD juntou-se e executa o Windows 1809 ou mais tarde, esta definição não deve ser definida para *exigir PIN de arranque com TPM*. Para mais informações, consulte [silenciosamente o BitLocker nos dispositivos](../protect/encrypt-devices.md#silently-enable-bitlocker-on-devices).

  - **Chave de arranque TPM compatível**  
    **Predefinição**: Permitir a chave de arranque com tPM  

    Opte por permitir, não permitir ou exigir a utilização de uma chave de arranque com o chip TPM. Para ativar uma chave de arranque, é necessária interação por parte do utilizador final.  

    - **Permitir chave de arranque com TPM**  
    - **Não permita a chave de arranque com TPM**  
    - **Requerer chave de arranque com TPM**  

    > [!TIP]
    > Para instalar o BitLocker automaticamente e silenciosamente num dispositivo que é Azure AD juntou-se e executa o Windows 1809 ou mais tarde, esta definição não deve ser definida para *exigir a chave de arranque com TPM*. Para mais informações, consulte [silenciosamente o BitLocker nos dispositivos](../protect/encrypt-devices.md#silently-enable-bitlocker-on-devices).

  - **Chave de arranque TPM compatível e PIN**  
    **Predefinição**: Permitir a chave de arranque e pin com TPM  

    Opte por permitir, não permitir ou exigir a utilização de uma chave de arranque e PIN com o chip TPM. Para ativar uma chave e PIN de arranque, é necessária interação por parte do utilizador final.  
    - **Permitir chave de arranque e PIN com TPM**  
    - **Não permita a chave de arranque e PIN com TPM**  
    - **Requerer chave de arranque e PIN com TPM**   

    > [!TIP]  
    > Para instalar o BitLocker automaticamente e silenciosamente num dispositivo que é Azure AD juntou-se e executa o Windows 1809 ou mais tarde, esta definição não deve ser definida para exigir chave de *arranque e PIN com TPM*. Para mais informações, consulte [silenciosamente o BitLocker nos dispositivos](../protect/encrypt-devices.md#silently-enable-bitlocker-on-devices).

- **Comprimento mínimo do PIN**  
    **Predefinição**: Não configurado  
    BitLocker CSP: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Ativar** Configure um comprimento mínimo para o PIN de arranque tpm.  
    - **Não configurado** - Os utilizadores podem configurar um PIN de arranque de qualquer comprimento entre 6 e 20 dígitos.  

  Quando programado para *ativar,* pode configurar a seguinte definição:  

  - **Caracteres mínimos**  
    **Predefinição**: BitLocker CSP *não configurado:* [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    Introduza o número de caracteres necessários para o PIN de arranque a partir de **4**-**20**.  

- **Recuperação de unidade soso**  
  **Predefinição**: Não configurado   
  BitLocker CSP: [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Ativar** - Controle como o sistema operativo protegido pelo BitLocker se recupera quando a informação de arranque necessária não estiver disponível.  
  - **Não configurado** - As opções de recuperação padrão são suportadas para a recuperação do BitLocker. Por predefinição, é permitida uma DRA, as opções de recuperação são escolhidas pelo utilizador, incluindo a palavra-passe de recuperação e a chave de recuperação, e as informações de recuperação não são apoiadas em DS AD.  

  Quando programado para *ativar,* pode configurar as seguintes definições:  

  - **Agente de recuperação de dados baseado em certificado**  
    **Predefinição**: Não configurado  
     
    - **Bloquear** - Evite a utilização de um agente de recuperação de dados com unidades de SO protegidas pelo BitLocker.  
    - **Não configurado** - Permitir que os agentes de recuperação de dados sejam utilizados com unidades de sistema operativo seladas pelo BitLocker.  

  - **Criação de senha de recuperação do utilizador**  
    **Predefinição**: Permitir senha de recuperação de 48 dígitos  

    Escolha se os utilizadores são permitidos, necessários ou não autorizados a gerar uma senha de recuperação de 48 dígitos.  
    - **Permitir senha de recuperação de 48 dígitos**  
    - **Não permita a palavra-passe de recuperação de 48 dígitos**  
    - **Requerer senha de recuperação de 48 dígitos**  

  - **Chave de criação de utilizadores de recuperação**  
    **Predefinição**: Permitir a chave de recuperação de 256 bits  

    Escolha se os utilizadores são permitidos, necessários ou não autorizados a gerar uma chave de recuperação de 256 bits.  
    - **Permitir a chave de recuperação de 256 bits**  
    - **Não permita a chave de recuperação de 256 bits**  
    - **Requerer chave de recuperação de 256 bits**  

  - **Opções de recuperação no assistente de configuração BitLocker**  
    **Predefinição**: Não configurado  

    - **Bloco** - Os utilizadores não podem ver e alterar as opções de recuperação. Quando definido para 
    - **Não configurado** - Os utilizadores podem ver e alterar as opções de recuperação quando ligam o BitLocker. 
 
  - **Guarde informações de recuperação do BitLocker para o Diretório Ativo do Azure**  
    **Predefinição**: Não configurado  

    - **Ativar** - Armazenar as informações de recuperação bitLocker para o Azure Ative Directory (Azure AD).  
    - **Não configurado** - As informações de recuperação do BitLocker não estão armazenadas em AAD.  

  - **Informação de recuperação bitLocker armazenada no Diretório Ativo azure**  
    **Predefinição**: Palavras-passe de recuperação de backup e pacotes chave  

    Configure quais as partes das informações de recuperação bitLocker armazenadas em Azure AD. Escolha entre:  
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**  
    - **Apenas palavras-passe de recuperação de cópia de segurança**  

  - **Rotação da palavra-passe de recuperação orientada pelo cliente**  
    **Predefinição**: Rotação de chaves ativada para dispositivos unidos pelo Azure  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Esta definição inicia uma rotação de palavra-passe de recuperação orientada pelo cliente após uma recuperação de unidade solado (quer utilizando o bootmgr ou o WinRE).  

    - Não configurado  
    - Rotação da chave desativada  
    - Rotação de chave ativada para degelos unidos pela AD azure  
    - Rotação de chaves ativada para dispositivos Azure AD e Híbridos  

  - **Armazenar informações de recuperação no Diretório Ativo da Azure antes de ativar o BitLocker**  
    **Predefinição**: Não configurado  
 
     Impedir que os utilizadores ativem o BitLocker a menos que o computador recue com sucesso as informações de recuperação do BitLocker para o Diretório Ativo do Azure.  

    - **Require** - Impeça os utilizadores de ligar o BitLocker a menos que as informações de recuperação do BitLocker sejam armazenadas com sucesso em Azure AD.  
    - **Não configurado** - Os utilizadores podem ligar o BitLocker, mesmo que as informações de recuperação não forem armazenadas com sucesso no Azure AD.  

- **Mensagem de recuperação pré-arranque e URL**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Ativar** - Configure a mensagem e o URL que visualizam no ecrã de recuperação da chave de pré-arranque.  
  - **Não configurado** - Desative esta funcionalidade.  
  
  Quando programado para *ativar,* pode configurar a seguinte definição:  
  - **Mensagem de recuperação pré-arranque**  
    **Predefinição**: Utilize a mensagem de recuperação predefinida e o URL   
 
    Configure como a mensagem de recuperação pré-arranque exibe aos utilizadores. Escolha entre:  
    - **Utilizar mensagem de recuperação predefinida e URL**  
    - **Utilizar mensagem de recuperação vazia e URL**  
    - **Utilizar mensagem de recuperação personalizada**  
    - **Utilizador URL de recuperação personalizada**  

### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker  

Estas definições aplicam-se especificamente a unidades de dados fixas.  

- **Escreva acesso a unidade de dados fixa não protegida pela BitLocker**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Bloco** - Dê acesso apenas a leitura a unidades de dados que não estejam protegidas pelo BitLocker.  
  - **Não configurado** - Por padrão, leia e escreva acesso a unidades de dados que não estejam encriptadas.  

- **Recuperação de unidade fixa**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Ativar** - Controle como as unidades fixas protegidas pelo BitLocker se recuperam quando a informação de arranque necessária não estiver disponível.  
  - **Não configurado** - Desative esta funcionalidade.  

  Quando programado para *ativar,* pode configurar as seguintes definições:  

  - **Agente de recuperação de dados**  
    **Predefinição**: Não configurado  
 
    - **Bloco** - Evite a utilização do agente de recuperação de dados com unidades fixas protegidas pelo BitLocker Editor de Política. 
    - **Não configurado** - Permite a utilização de agentes de recuperação de dados com unidades fixas protegidas pelo BitLocker.  

  - **Criação de senha de recuperação do utilizador**  
    **Predefinição**: Permitir senha de recuperação de 48 dígitos  

    Escolha se os utilizadores são permitidos, necessários ou não autorizados a gerar uma senha de recuperação de 48 dígitos.  
    - **Permitir senha de recuperação de 48 dígitos**  
    - **Não permita a palavra-passe de recuperação de 48 dígitos**  
    - **Requerer senha de recuperação de 48 dígitos**  

  - **Chave de criação de utilizadores de recuperação**  
    **Predefinição**: Permitir a chave de recuperação de 256 bits

    Escolha se os utilizadores são permitidos, necessários ou não autorizados a gerar uma chave de recuperação de 256 bits.
    - **Permitir a chave de recuperação de 256 bits**  
    - **Não permita a chave de recuperação de 256 bits**  
    - **Requerer chave de recuperação de 256 bits**  

  - **Opções de recuperação no assistente de configuração BitLocker**  
    **Predefinição**: Não configurado  

    - **Bloco** - Os utilizadores não podem ver e alterar as opções de recuperação. Quando definido para 
    - **Não configurado** - Os utilizadores podem ver e alterar as opções de recuperação quando ligam o BitLocker.
 
  - **Guarde informações de recuperação do BitLocker para o Diretório Ativo do Azure**  
    **Predefinição**: Não configurado  

    - **Ativar** - Armazenar as informações de recuperação bitLocker para o Azure Ative Directory (Azure AD).  
    - **Não configurado** - As informações de recuperação do BitLocker não estão armazenadas em AAD.

  - **Informação de recuperação bitLocker armazenada no Diretório Ativo azure**  
    **Predefinição**: Palavras-passe de recuperação de backup e pacotes chave  

    Configure quais as partes das informações de recuperação bitLocker armazenadas em Azure AD. Escolha entre:  
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**  
    - **Apenas palavras-passe de recuperação de cópia de segurança**  

  - **Rotação da palavra-passe de recuperação orientada pelo cliente**  
    **Predefinição**: Rotação de chaves ativada para dispositivos unidos pelo Azure  
    BitLocker CSP: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Esta definição inicia uma rotação de palavra-passe de recuperação orientada pelo cliente após uma recuperação de unidade solado (quer utilizando o bootmgr ou o WinRE).  

    - Não configurado  
    - Rotação da chave desativada  
    - Rotação de chave ativada para degelos unidos pela AD azure  
    - Rotação de chaves ativada para dispositivos Azure AD e Híbridos  

  - **Armazenar informações de recuperação no Diretório Ativo da Azure antes de ativar o BitLocker**  
    **Predefinição**: Não configurado  
 
    Impedir que os utilizadores ativem o BitLocker a menos que o computador recue com sucesso as informações de recuperação do BitLocker para o Diretório Ativo do Azure.  

    - **Require** - Impeça os utilizadores de ligar o BitLocker a menos que as informações de recuperação do BitLocker sejam armazenadas com sucesso em Azure AD.  
    - **Não configurado** - Os utilizadores podem ligar o BitLocker, mesmo que as informações de recuperação não forem armazenadas com sucesso no Azure AD.  

### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados removíveis do BitLocker  

Estas definições aplicam-se especificamente a unidades de dados amovíveis.  

- **Escreva acesso a unidade de dados amovível não protegido pela BitLocker**  
  **Predefinição**: Não configurado  
  BitLocker CSP: [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Bloco** - Dê acesso apenas a leitura a unidades de dados que não estejam protegidas pelo BitLocker.  
  - **Não configurado** - Por padrão, leia e escreva acesso a unidades de dados que não estejam encriptadas.  

  Quando programado para *ativar,* pode configurar a seguinte definição:  

  - **Escreva acesso a dispositivos configurados noutra organização**  
    **Predefinição**: Não configurado  

    - **Bloco** - Bloquear o acesso a dispositivos configurados noutra organização.  
    - **Não configurado** - Negar o acesso à escrita.  
 
## <a name="microsoft-defender-exploit-guard"></a>Microsoft Defender Exploit Guard  

Utilize [a proteção de exploração](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) para gerir e reduzir a superfície de ataque das aplicações utilizadas pelos seus colaboradores.  

### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque  

As regras de redução de superfície de ataque ajudam a prevenir comportamentos que o malware usa frequentemente para infetar computadores com código malicioso.  

#### <a name="attack-surface-reduction-rules"></a>Regras de Redução de Superfície de Ataque  

- **Marcar o roubo de credenciais do sistema de autoridade de segurança local do Windows**  
  **Predefinição**: Não configurado  
  Regra: Roubo de credenciais de bloco do subsistema da autoridade de [segurança local do Windows (lsass.exe)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  Ajude a prevenir ações e aplicações que são normalmente usadas através da exploração de malware para infetar máquinas.  

  - **Não configurado**  
  - **Ativar** - Roubo de credenciais de bandeira do subsistema da autoridade de segurança local do Windows (lsass.exe).  
  - **Apenas auditoria**  

- **Criação de processos a partir de Adobe Reader (beta)**  
  **Predefinição**: Não configurado  
  Regra: [Bloqueie o Leitor de Adobe de criar processos infantis](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **Não configurado**  
  - **Ativar** - Bloqueie os processos infantis que são criados a partir do Adobe Reader.  
  - **Apenas auditoria**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Regras para impedir ameaças macro do Office  

Impeça as aplicações do Office de realizarem as seguintes ações:  

- **Aplicações do Office a injetar noutros processos (sem exceções)**  
  **Predefinição**: Não configurado  
  Regra: [Aplicações do Block Office de injetar código noutros processos](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **Não configurado**  
  - **Block** - Block Office apps de injetar em outros processos.  
  - **Apenas auditoria**  

- **Aplicações/macros do Office a criar conteúdo executável**  
  **Predefinição**: Não configurado  
  Regra: [Aplicações do Block Office da criação de conteúdo executável](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **Não configurado**  
  - **Block** - Block Office apps e macros de criar conteúdo executável.  
  - **Apenas auditoria**  

- **Aplicações do Office a iniciar processos subordinados**  
  **Predefinição**: Não configurado  
  Regra: [Bloqueie todas as candidaturas do Office à criação de processos infantis](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **Não configurado**  
  - **Block** - Block Office apps de lançamento de processos infantis.  
  - **Apenas auditoria**  
  
- **Importações do Win32 provenientes de código macro do Office**  
  **Predefinição**: Não configurado  
  Regra: [Block Win32 API liga das macros do Office](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **Não configurado**  
  - **Bloco** - Block Win32 importações de macro código no Office.  
  - **Apenas auditoria**  
  
- **Criação de processos a partir de produtos de comunicação do Office**  
  **Predefinição**: Não configurado  
  Regra: [Bloquear aplicação de comunicação do Office da criação de processos infantis](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **Não configurado**  
  - **Enable** - Bloquear a criação de processos infantis a partir de aplicações de comunicações do Office.  
  - **Apenas auditoria**  

#### <a name="rules-to-prevent-script-threats"></a>Regras para impedir ameaças de script  

Bloqueie os itens seguintes para impedir ameaças de script:  

- **Código macro js/vbs/ps/ oculto**  
  **Predefinição**: Não configurado  
  Regra: [Bloquear a execução de scripts potencialmente obfuscados](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **Não configurado**  
  - **Bloco** - Bloqueie qualquer js/vbs/ps/macro código obfuscated.  
  - **Apenas auditoria**  

- **js/vbs a executar payload transferido da Internet (sem exceções)**  
  **Predefinição**: Não configurado  
  Regra: [Bloqueie o JavaScript ou o VBScript a partir do lançamento de conteúdo executável descarregado](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **Não configurado**  
  - **Bloco** - Bloqueie js/vbs da execução da carga útil descarregada da Internet.  
  - **Apenas auditoria**  

- **Processo de criação de comandos PSExec e WMI**  
  **Predefinição**: Não configurado  
  Regra: [Criações de processo sinuosos com origem nos comandos PSExec e WMI](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **Não configurado**  
  - **Bloco** - Bloqueie criações de processos originários de comandos PSExec e WMI.  
  
  - **Apenas auditoria**  

- **Processos não fidedignos e não assinados que executam a partir de USB**  
  **Predefinição**: Não configurado  
  Regra: [Bloqueie processos não confiáveis e não assinados que vão a partir de USB](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **Não configurado**  
  - **Bloco** - Bloqueie processos não confiáveis e não assinados que funcionam a partir de USB.  
  - **Apenas auditoria**  
  
- **Ficheiros executáveis que não correspondam a uma prevalência, idade ou lista de critérios de confiança**  
  **Predefinição**: Não configurado  
  Regra: [Bloquear ficheiros executáveis de executar a menos que satisfaçam um critério de prevalência, idade ou lista de confiança](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **Não configurado**  
  - **Bloco** - Bloqueie ficheiros executáveis de executar a menos que satisfaçam critérios de prevalência, idade ou lista fidedigna.  
  - **Apenas auditoria**  

#### <a name="rules-to-prevent-email-threats"></a>Regras para impedir ameaças de e-mail  

Bloqueie o seguinte para impedir ameaças de e-mail:  

- **Execução de conteúdo executável (exe, dll, ps, js, vbs, etc.) retirado do e-mail (webmail/cliente de correio) (sem exceções)**  
  **Predefinição**: Não configurado  
  Regra: [Bloquear conteúdo executável a partir de cliente de e-mail e webmail](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **Não configurado**  
  - **Bloco** - Bloquear execução de conteúdo executável (exe, dll, ps, js, vbs, etc.) retirados de e-mail (webmail/mail-client).  
  - **Apenas auditoria**  

#### <a name="rules-to-protect-against-ransomware"></a>Regras para proteger contra ransomware  

- **Proteção de ransomware avançada**  
  Predefinição: Não configurado  
  Regra: [Utilize proteção avançada contra ransomware](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - **Não configurado**  
  - **Ativar** - Utilize uma proteção agressiva de ransomware.  
  - **Apenas auditoria**  

#### <a name="attack-surface-reduction-exceptions"></a>Exceções da Redução da Superfície de Ataque

- **Ficheiros e pastas para excluir das regras de redução de superfícies de ataque**  
  Defender CSP: [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importar** um ficheiro .csv que contenha ficheiros e pastas para excluir das regras de redução da superfície de ataque.  
  - **Adicione** manualmente ficheiros ou pastas locais.  

> [!IMPORTANT]  
> Para permitir a instalação e execução adequadas das aplicações LOB Win32, as definições anti-malware devem excluir a digitalização dos seguintes diretórios:  
> **Nas máquinas de clientes X64:**  
> *C:\Ficheiros do programa (x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **Nas máquinas de clientes X86:**  
> *C:\Program Files\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Acesso a pastas controladas  

Ajude a [proteger dados valiosos](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) de aplicações e ameaças maliciosas, como ransomware.  

- **Proteção de pastas**  
  **Predefinição**: Não configurado  
  Defender CSP: [EnableControlledfolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.  

  - **Não configurado**  
  - **Ativar**  
  - **Apenas auditoria**  
  - **Modificação do disco de blocos**  
  - **Modificação do disco de auditoria**  

  Quando selecionar uma configuração diferente de *Não configurada,* pode configurar:  
  - **Lista de aplicações que têm acesso a pastas protegidas**  
    Defender CSP: [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importar** um ficheiro .csv que contenha uma lista de aplicações.  
    - **Adicione** aplicativos a esta lista manualmente.  

  - **Lista de pastas adicionais que precisam de ser protegidas**  
    Defender CSP: [Pastas protegidas de controlo de pastas](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importar** um ficheiro .csv que contenha uma lista de pastas.  
    - **Adicione** as pastas a esta lista manualmente.  

### <a name="network-filtering"></a>Filtragem de rede  

Bloqueie ligações de saída de qualquer aplicação para endereços IP ou domínios com baixa reputação. A filtragem da rede é suportada tanto no modo Auditoria como no modo Block.  

- **Proteção da rede**  
  **Predefinição**: Não configurado  
  Defender CSP: [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  A intenção desta configuração é proteger os utilizadores finais de apps com acesso a esquemas de phishing, sites de hospedagem de exploração e conteúdo malicioso na Internet. Também impede que os navegadores de terceiros se conectem a sites perigosos.  

  - **Não configurado** - Desative esta funcionalidade. Os utilizadores e aplicações não estão impedidos de se conectarem a domínios perigosos. Os administradores não conseguem ver esta atividade no Microsoft Defender Security Center.  
  - **Ativar** - Ligue a proteção da rede e bloqueie os utilizadores e aplicações da ligação a domínios perigosos. Os administradores podem ver esta atividade no Microsoft Defender Security Center.  
  - **Auditoria apenas:** - Os utilizadores e aplicações não estão impedidos de se ligarem a domínios perigosos. Os administradores podem ver esta atividade no Microsoft Defender Security Center.  

### <a name="exploit-protection"></a>Exploit Protection  

- **Upload XML**  
  **Predefinição**: *Não configurado*  

  Para utilizar a proteção de exploração para [proteger os dispositivos de explorações,](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)crie um ficheiro XML que inclua as definições de mitigação do sistema e da aplicação que deseja. Existem dois métodos para criar o ficheiro XML:  

  - *PowerShell* - Utilize um ou mais dos cmdlets PowerShell *get-process,* *Set-ProcessMitigation*e *ConvertTo-ProcessMitigationPolicy* PowerShell. Os cmdlets configuram definições de mitigação e exportam uma representação XML deles.  

  - *Microsoft Defender Security Center UI* - No Microsoft Defender Security Center, clique no controlo de App & browser e, em seguida, percorra para a parte inferior do ecrã resultante para encontrar a Explore Protection. Em primeiro lugar, utilize as definições do sistema e os separadores das definições de programa para configurar definições de atenuação. Em seguida, localize a ligação de definições de Exportação na parte inferior do ecrã para exportar uma representação XML dos mesmos.  

- **Edição do utilizador da interface de proteção de exploração**  
  **Predefinição**: Não configurado  
  ExploitGuard CSP: [Explorações DeProteção](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Block** - Faça upload de um ficheiro XML que lhe permite configurar a memória, o fluxo de controlo e as restrições de política. As definições no ficheiro XML podem servir para proteger uma aplicação de exploits.  
  - **Não configurado** - Não é utilizada configuração personalizada.  

## <a name="microsoft-defender-application-control"></a>Controlo de aplicações do Microsoft Defender  

Escolha aplicações adicionais que precisam de ser auditadas ou que possam ser de confiança para serem executadas pelo Microsoft Defender Application Control. Os componentes do Windows e todas as aplicações da Microsoft Store são automaticamente considerados de confiança para serem executados.  


- **Políticas de integridade do código de controlo de aplicações**  
  **Predefinição**: Não configurado  
   CSP: [AppLocker CSP](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Aplicar** - Escolha as políticas de integridade do código de controlo de aplicações para os dispositivos dos seus utilizadores.  
  
    Depois de ativado num dispositivo, o Controlo de Aplicações só pode ser desativado alterando o modo de *'Aplicar* para *Auditoria'.* Se alterar do modo de *Impor* para *Não Configurado* o Controlo de Aplicações continuará a ser imposto nos dispositivos atribuídos.  

  - **Não configurado** - O Controlo de Aplicações não é adicionado aos dispositivos. No entanto, as definições anteriormente adicionadas continuam a ser aplicadas nos dispositivos atribuídos. 
 
  - **Apenas auditoria** - As candidaturas não estão bloqueadas. Todos os eventos estão registados nos registos do cliente local.  

## <a name="microsoft-defender-credential-guard"></a>Guarda Credencial do Microsoft Defender  

A Guarda Credencial do Microsoft Defender protege contra ataques de roubo de credenciais. Isola os segredos para permitir o acesso apenas a software de sistema com privilégios.  

- **Guarda Credencial**  
  **Predefinição**: Desativar  
  [DispositivoGuarda CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Desativar** - Desligue a Guarda Credential remotamente, se foi previamente ligada com a opção **de bloqueio Ativada sem a** opção de bloqueio UEFI.  

  - **Ativar com o bloqueio UEFI** - A Guarda Credential não pode ser desativada remotamente utilizando uma chave de registo ou uma política de grupo.  

    > [!NOTE]
    > Se utilizar esta definição e, em seguida, quiser desativar o Credential Guard, terá de definir a Política de Grupo como **Desativado**. Além disso, tem de limpar fisicamente as informações de configuração de UEFI de cada computador. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.  

  - **Ativar sem bloqueio UEFI** - Permite que a Guarda Credencial seja desativada remotamente utilizando a Política de Grupo. Os dispositivos que utilizam esta definição têm de ter a versão 1511 ou mais recente do Windows 10.  

  Quando ativa a Guarda *Credencial,* estão também ativadas as seguintes funcionalidades necessárias:  
  
  - **Segurança baseada em virtualização** (VBS)  
    Liga-se durante a próxima reinicialização. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.  
  - **Bota segura com acesso à memória do diretório**  
    Liga o VBS com proteções Secure Boot e acesso à memória direta (DMA). As proteções de DMA necessitam de suporte de hardware e são ativadas apenas em dispositivos configurados corretamente.  

## <a name="microsoft-defender-security-center"></a>Centro de Segurança Microsoft Defender  

O Microsoft Defender Security Center funciona como uma aplicação ou processo separado de cada uma das funcionalidades individuais. Apresenta notificações através do Centro de Ação. Atua como colecionador ou único local para ver o estado e executar alguma configuração para cada uma das funcionalidades. Saiba mais nos docs do [Microsoft Defender.](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center)  

### <a name="microsoft-defender-security-center-app-and-notifications"></a>Aplicação e notificações do Microsoft Defender Security Center  

Bloqueie o acesso do utilizador final às várias áreas da aplicação Microsoft Defender Security Center. Ocultar uma secção também bloqueia notificações relacionadas.  

- **Proteção contra vírus e ameaças**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [Disablevirusui](https://go.microsoft.com/fwlink/?linkid=873662)  

  Configure se os utilizadores finais puderem ver a área de proteção contra vírus e ameaças no Microsoft Defender Security Center. Ocultar esta secção também bloqueará todas as notificações relacionadas com o Vírus e a proteção contra ameaças.  

  - **Não configurado**  
  - **Esconder**  

- **Proteção ransomware**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Configure se os utilizadores finais puderem visualizar a área de proteção ransomware no Microsoft Defender Security Center. Ocultar esta secção também bloqueará todas as notificações relacionadas com a proteção ransomware.  

  - **Não configurado**  
  - **Esconder**  

- **Proteção de Conta**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [Desativação AccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  Configure se os utilizadores finais puderem visualizar a área de proteção da conta no Microsoft Defender Security Center. Ocultar esta secção também bloqueará todas as notificações relacionadas com a proteção de Conta.  

  - **Não configurado**  
  - **Esconder**  

- **Firewall e proteção da rede**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  Configure se os utilizadores finais puderem visualizar a firewall e a área de proteção de rede no centro de segurança Do Microsoft Defender. Ocultar esta secção também bloqueará todas as notificações relacionadas com firewall e proteção de rede.  

  - **Não configurado**  
  - **Esconder**  

- **Controlo de aplicativos e navegador**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [Disableappbrowserui](https://go.microsoft.com/fwlink/?linkid=873669)  

  Configure se os utilizadores finais puderem ver a app e a área de controlo do navegador no centro de Segurança do Microsoft Defender. Ocultar esta secção também bloqueará todas as notificações relacionadas com o controlo de Apps e navegador.  

  - **Não configurado**  
  - **Esconder**  

- **Proteção de hardware**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [DesactivaçãoSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  Configure se os utilizadores finais puderem visualizar a área de proteção de hardware no Microsoft Defender Security Center. Ocultar esta secção também bloqueará todas as notificações relacionadas com a proteção de Hardware.  

  - **Não configurado**  
  - **Esconder**  

- **Desempenho e estado de funcionamento do dispositivo**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [DisablehealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  Configure se os utilizadores finais puderem visualizar o desempenho do Dispositivo e a área de saúde no centro de segurança do Microsoft Defender. Ocultar esta secção também bloqueará todas as notificações relacionadas com o desempenho e saúde do Dispositivo.  
  
  - **Não configurado**  
  - **Esconder**  

- **Opções de família**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [DisableFamilyui](https://go.microsoft.com/fwlink/?linkid=873673)  

  Configure se os utilizadores finais puderem visualizar a área de opções familiares no centro de Segurança Do Microsoft Defender. Ocultar esta secção também bloqueará todas as notificações relacionadas com opções familiares.  
  
  - **Não configurado**  
  - **Esconder**  

- **Notificações das áreas expostas da app**  
  **Predefinição**: Não configurado  
  WindowsDefenderSecurityCenter CSP: [Desativar Notificações](https://go.microsoft.com/fwlink/?linkid=873675)  

  Escolha quais as notificações a apresentar aos utilizadores finais. As notificações não críticas incluem resumos da atividade antivírus do Microsoft Defender, incluindo notificações quando os exames estiverem concluídos. Todas as outras notificações são consideradas críticas.  

  - **Não configurado**  
  - **Bloquear notificações não críticas**  
  - **Bloqueie todas as notificações**  

- **Ícone do Centro de Segurança do Windows na bandeja do sistema**  
  **Predefinição**: Não configurado  

  Configure o visualizar o controlo da área de notificação. O utilizador precisa de assinar e iniciar sessão ou reiniciar o computador para que esta definição faça efeito.  
  
  - **Não configurado**  
  - **Esconder**  

- **Botão TPM claro**  
  **Predefinição**: Não configurado  

  Configure o visor do botão Clear TPM.  
  
  - **Não configurado**  
  - **Desativar**  

- **Aviso de atualização de firmware TPM**  
  **Predefinição**: Não configurado  
  
  Configure o visor da atualização TPM Firmware quando for detetado um firmware vulnerável.  

  - **Não configurado**  
  - **Esconder**  

- **Proteção de Adulteração**  
  **Predefinição**: Não configurado

  Ligue ou desligue a Proteção de Adulteração nos dispositivos. Para utilizar a Proteção contra adulteração, deve integrar a Proteção avançada de [Ameaças do Microsoft Defender com o Intune](advanced-threat-protection.md), e ter [licenças Enterprise Mobility + Security E5](../fundamentals/licenses.md).  
  - **Não configurado** - Não é feita qualquer alteração nas definições do dispositivo.
  - **Ativado** - A Proteção contra adulterações é ativada e as restrições são aplicadas nos dispositivos.
  - **Deficientes** - A Proteção contra adulterações é desligada e as restrições não são aplicadas.

### <a name="it-contact-information"></a>Informação de contacto de TI  

Forneça informações de contacto de TI que apareçam na aplicação microsoft Defender Security Center e nas notificações da aplicação.  

Pode optar por **Mostrar na aplicação e nas notificações**, **Mostrar apenas na aplicação**, **Mostrar apenas nas notificações** ou **Não mostrar**. Introduza o **Nome da organização de TI** e pelo menos uma das seguintes opções de contacto:  


- **Informações de contacto informática**  
  **Predefinição**: Não exibir  
  WindowsDefenderSecurityCenter CSP: [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Configure onde exibir informações de contacto de TI para os utilizadores finais.  
  
  - **Exibição na app e em notificações**  
  - **Exibir apenas na aplicação**  
  - **Exibir apenas em notificações**  
  - **Não exiba**  

  Quando configurado para visualizar, pode configurar as seguintes definições:  

  - **Nome da organização de TI**  
    **Predefinição**: *Não configurado*  
    WindowsDefenderSecurityCenter CSP: [Nome da empresa](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **Número de telefone ou ID do Skype do departamento de TI**  
    **Predefinição**: *Não configurado*  
    WindowsDefenderSecurityCenter CSP: [Telefone](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **Endereço de e-mail do departamento de TI**  
    **Predefinição**: *Não configurado*  
    WindowsDefenderSecurityCenter CSP: [E-mail](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **URL do site de suporte de TI**  
    **Predefinição**: *Não configurado*  
    WindowsDefenderSecurityCenter CSP: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Opções de segurança do dispositivo local  

Utilize estas opções para configurar as definições da segurança local em dispositivos Windows 10.  

### <a name="accounts"></a>Contas  

- **Adicione novas contas da Microsoft**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Bloco** Impedir que os utilizadores adicionem novas contas da Microsoft ao dispositivo.  
  - **Não configurado** - Os utilizadores podem utilizar as contas da Microsoft no dispositivo.  

- **Início remoto sem senha**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Bloco** - Permita que apenas contas locais com senhas em branco assinem utilizando o teclado do dispositivo.  
   - **Não configurado** - Permita que contas locais com senhas em branco sintetizam em outros locais que não o dispositivo físico.  

#### <a name="admin"></a>Admin  

- **Conta de administração local**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Bloco** Impedir a utilização de uma conta de administração local.  
  - **Não configurado**  

- **Renomear conta de administração**  
  **Predefinição**: *Não configurado*  
  Opções locais DeSegurança CSP: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Defina um nome de conta diferente a associar ao identificador de segurança (SID) para a conta "Administrador".  

 #### <a name="guest"></a>Convidado  

- **Conta de hóspedes**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: Opções de [segurança de políticas locais](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Bloco** - Impedir a utilização de uma conta De hóspedes.  
  - **Não configurado**  

- **Renomear a conta de hóspedes**  
  **Predefinição**: *Não configurado*  
  Opções locais de segurança CSP: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Defina um nome de conta diferente a associar ao identificador de segurança (SID) para a conta "Hóspede".  

### <a name="devices"></a>Dispositivos  

- **Dispositivo de desacoplamento sem logon**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Bloco** - Os utilizadores podem premir o botão de ejeção física de um dispositivo portátil para desancorar com segurança o dispositivo.  
  - **Não configurado** - Um utilizador deve iniciar sessão no dispositivo e receber permissão para desancorar o dispositivo.  

- **Instale controladores de impressoras para impressoras partilhadas**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Ativado** - Qualquer utilizador pode instalar um controlador de impressora como parte da ligação a uma impressora partilhada.  
  - **Não configurado** - Só os Administradores podem instalar um controlador de impressora como parte da ligação a uma impressora partilhada.  

- **Restringir o acesso cD-ROM ao utilizador ativo local**  
  **Predefinição**: Não configurado  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Ativado** - Apenas o utilizador de sessão de sessão interativa pode utilizar os meios de CD-ROM. Se esta política estiver ativada e ninguém tiver sessão iniciada de forma interativa, a unidade de CD-ROM será acedida através da rede.  
  - **Não configurado** - Qualquer pessoa tem acesso ao CD-ROM.  

- **Formato e ejetar meios amovíveis**  
  **Predefinição**: Administradores  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  Defina quem é autorizado a formatar e ejetar meios NTFS amovíveis:  
  - **Não configurado**  
  - **Administradores**  
  - **Administradores e Utilizadores Avançados**  
  - **Administradores e Utilizadores Interativos**  

### <a name="interactive-logon"></a>Início de sessão interativo  

- **Minutos de inatividade do ecrã de bloqueio até que o protetor de ecrã seja ativado**  
  **Predefinição**: *Não configurado*  
  Opções locais DeSegurança CSP: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  Introduza os minutos máximos de inatividade no ecrã de entrada do ambiente de trabalho interativo até o protetor de ecrã começar. (**0** - **99999**)  

- **Exigir CTRL+ALT+DEL para iniciar sessão**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Ativar** - Premir CTRL+ALT+DEL não é necessário para que os utilizadores possam iniciar sessão.  
  - **Não configurado** Exija que os utilizadores pressionem CTRL+ALT+DEL antes de iniciars sessão no Windows.  

- **Comportamento de remoção de cartões inteligentes**  
  **Padrão**: Bloquear a estação de trabalho   
  Opções de segurança de políticas locais CSP: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  Determina o que acontece quando o cartão inteligente para um utilizador ligado é removido do leitor de cartões inteligentes. As opções são:  

  - **Lock Workstation** - A estação de trabalho fica bloqueada quando o cartão inteligente é removido. Esta opção permite que os utilizadores saiam da área, levem os seus smart cards e permaneçam numa sessão protegida.  
  - **Sem ação**  
  - **Force Logoff** - O utilizador é automaticamente desligado quando o cartão inteligente é removido.  
  - **Desligue se uma sessão de Serviços** de Ambiente de Trabalho Remoto - A remoção do cartão inteligente desliga a sessão sem desligar o utilizador. Esta opção permite que o utilizador insira o smart card e retome a sessão mais tarde, ou noutro computador com um leitor de smart cards, sem ter de iniciar sessão novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.  

#### <a name="display"></a>Apresentar  

- **Informações do utilizador no ecrã de bloqueio**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  Configure as informações do utilizador que são exibidas quando a sessão estiver bloqueada. Se não estiverem configuradas, serão apresentados o nome a apresentar do utilizador, o domínio e o nome de utilizador.  

  - **Não configurado**  
  - **O nome a apresentar do utilizador, o domínio e o nome de utilizador**  
  - **Apenas o nome a apresentar do utilizador**  
  - **Não apresentar informações do utilizador**  

- **Ocultar último utilizador inscrito**  
  **Predefinição**: Não configurado  
  Opções de segurança de políticas locais CSP: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Ativar** - Ocultar o nome de utilizador.  
  - **Não configurado** - Mostre o último nome de utilizador.  

- **Ocultar o nome de utilizador no início do
  ** **Predefinido**: Não configurado  
  Opções de Segurança local CSP: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Ativar** - Ocultar o nome de utilizador.  
  - **Não configurado** - Mostre o último nome de utilizador.  

- **Título de mensagem de logon**  
  **Predefinição**: *Não configurado*  
  Opções locais DeSegurança CSP: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  Detete o título da mensagem para os utilizadores que saem.  

- **Texto de mensagem de início**  
  **Predefinição**: *Não configurado*  
  Opções locais DeSegurança CSP: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  Detete o texto da mensagem para os utilizadores que saem.  
  
### <a name="network-access-and-security"></a>Acesso à rede e segurança

- **Acesso anónimo a Canos e Partilhas Nomeados**  
  **Predefinição**: Não configurado  
  Opções de Segurança local CSP: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Não configurado** - Restringir o acesso anónimo às definições de partilha e de tubo sem nome. Aplica-se as definições que podem ser acedidas anonimamente.  
  - **Block** - Desative esta política, disponibilizando acesso anónimo.  

- **Enumeração anónima das contas SAM**  
  **Predefinição**: Não configurado  
  Opções de Segurança local CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **Não configurado** - Os utilizadores anónimos podem enumerar as contas SAM.  
  - **Bloco** - Evite a enumeração anónima das contas SAM.  

- **Enumeração anónima das contas e ações da SAM**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Não configurado** - Os utilizadores anónimos podem enumerar os nomes das contas de domínio e das partilhas de rede.  
  - **Bloco** - Evite a enumeração anónima das contas e ações da SAM. 

- **Valor hash do gestor lan armazenado na mudança de senha**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Determine se o valor de hash para senhas é armazenado da próxima vez que a palavra-passe for alterada. 
  - **Não configurado** - O valor do hash não é armazenado  
  - **Bloco** - O Lan Manager (LM) armazena o valor de hash para a nova senha.  

- **Pedidos de autenticação PKU2U**  
  **Predefinição**: Não configurado  
  Opções de Segurança Local Opções CSP: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **Não configurado**- Permitir pedidos de PU2U.  
  - **Bloco** - Bloquear pedidos de autenticação PKU2U para o dispositivo.  

- **Restringir ligações RPC remotas à SAM**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **Não configurado** - Utilize o descritor de segurança predefinido, que pode permitir que utilizadores e grupos efetivos remotos de RPC para o SAM.
  - **Permitir** - Negar aos utilizadores e grupos de fazer chamadas RPC remotas para o Gestor de Contas de Segurança (SAM), que armazena contas de utilizador e palavras-passe. **O permitir** também permite alterar a cadeia padrão de definição de descritorededantes de segurança (SDDL) para permitir ou negar explicitamente utilizadores e grupos para fazer estas chamadas remotas.  

    - **Descritor de segurança**  
      **Predefinição**: *Não configurado*  
    
- **Segurança mínima da sessão para clientes baseados em NTLM SSP**  
  **Padrão**: Nenhum  
  Opções locais DeSegurança CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Esta definição de segurança permite que um servidor exija a negociação de encriptação de 128 bits e/ou segurança de sessão NTLMv2.  

  - **Nenhum**  
  - **Exigir segurança da sessão NTLMv2**  
  - **Requerem encriptação de 128 bits**  
  - **Encriptação NTLMv2 e 128 bits**  
 
- **Segurança mínima da sessão para servidor baseado ntlm SSP**  
  **Padrão**: Nenhum  
  Opções de Segurança local CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Esta definição de segurança determina qual o protocolo de autenticação de desafio/resposta utilizado para os logons de rede.  

  - **Nenhum**  
  - **Exigir segurança da sessão NTLMv2**  
  - **Requerem encriptação de 128 bits**  
  - **Encriptação NTLMv2 e 128 bits**  

- **Nível de autenticação do gestor lan**  
  **Padrão**: LM e NTLM  
  Opções locais DeSegurança CSP: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM e NTLM**  
  - **LM, NTLM e NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 e não LM**  
  - **NTLMv2 e não LM ou NTLM**  
  
- **Logotipos de hóspedes inseguros**  
  **Predefinição**: Não configurado  
  LanmanWorkstation CSP: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Se ativar esta definição, o cliente SMB rejeitará logotipos de hóspedes inseguros.  

  - **Não configurado**  
  - **Bloco** - O cliente SMB rejeita logotipos de hóspedes inseguros.  

### <a name="recovery-console-and-shutdown"></a>Consola de recuperação e encerramento  

- **Limpar o ficheiro de página da memória virtual ao desligar**  
  **Predefinição**: Não configurado  
   Opções locais de segurança CSP: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Ativar** - Limpe o ficheiro de página de memória virtual quando o dispositivo estiver desativado.  
  - **Não configurado** - Não limpa a memória virtual.  

- **Desligar sem login**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Bloco** - Ocultar a opção de encerramento no sinal do Windows no ecrã. Os utilizadores têm de iniciar sessão no dispositivo e, em seguida, encerrar.  
  - **Não configurado** - Permita que os utilizadores desliguem o dispositivo do sinal do Windows no ecrã.  

### <a name="user-account-control"></a>Controlo de conta de utilizador  

- **Integridade da UIA sem localização segura**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **Block** - As aplicações que se encontram num local seguro no sistema de ficheiros serão executadas apenas com integridade uIAccess.  
  - **Não configurado** - Permite que as aplicações sejam executadas com integridade uIAccess, mesmo que as aplicações não estejam num local seguro no sistema de ficheiros.  

- **Virtualize falhas de registo e registo de escrita em locais por utilizador**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Ativado** - Aplicações que escrevem dados para locais protegidos falham.  
  - **Não configurado** - As falhas de escrita da aplicação são redirecionadas no tempo de execução para definir as localizações do utilizador para o sistema de ficheiros e registo.  

- **Só elevar ficheiros executáveis que são assinados e validados**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Ativado** - Faça cumprir a validação da via de certificação PKI para um ficheiro executável antes de poder ser executado.  
  - **Não configurado** - Não imponha a validação do caminho de certificação PKI antes que um ficheiro executável possa ser executado.  

#### <a name="uia-elevation-prompt-behavior"></a>Comportamento rápido de elevação da UIA  

- **Elevação para administradores**  
  **Predefinição**: Solicitação de consentimento para binários não Windows  
  Opções locais DeSegurança CSP: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Defina o comportamento do pedido de elevação para administradores no Modo de Aprovação de Administradores.  

  - **Não configurado**  
  - **Elevar sem perguntar**  
  - **Pedir credenciais no ambiente de trabalho seguro**  
  - **Pedir credenciais**  
  - **Pedir consentimento**  
  - **Pedido de consentimento para binários não Windows**  


- **Aviso de elevação para utilizadores padrão**  
  **Padrão**: Solicitação de credenciais  
  Opções locais DeSegurança CSP: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  Defina o comportamento do pedido de elevação para os utilizadores padrão.  

  - **Não configurado**  
  - **Negar automaticamente pedidos de elevação**  
  - **Pedir credenciais no ambiente de trabalho seguro**  
  - **Pedir credenciais**  

- **Elevação da rota leva ao ambiente de trabalho interativo do utilizador**  
  **Predefinição**: Não configurado  
  Opções locais de segurança CSP: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Habilitado** - Todos os pedidos de elevação para ir para o ambiente de trabalho do utilizador interativo em vez do ambiente de trabalho seguro. São utilizadas todas as definições de política de comportamento de pedidos para administradores e utilizadores padrão.  
  - **Não configurado** - Force todos os pedidos de elevação vão para o ambiente de trabalho seguro, independentemente de quaisquer definições de política de comportamento rápida para administradores e utilizadores padrão.

- **Alerta elevado para instalações de aplicações**  
  **Predefinição**: Não configurado  
  Opções de Segurança local CSP: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Ativado** - Os pacotes de instalação de aplicação não são detetados ou solicitados para elevação.
   - **Não configurado** - Os utilizadores são solicitados para um nome administrativo de utilizador e senha quando um pacote de instalação de aplicação requer privilégios elevados.

- **Aviso de elevação da UIA sem ambiente de trabalho seguro**  
  **Predefinição**: Não configurado  
  Opções de Segurança local CSP: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Ativar** - Permitir que as aplicações UIAccess indiquem a elevação, sem utilizar o ambiente de trabalho seguro.  
- **Não configurado** - As solicitações de elevação utilizam um ambiente de trabalho seguro.  

#### <a name="admin-approval-mode"></a>Modo de Aprovação de Administradores  

- **Modo de aprovação de administrador para administrador incorporado**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Ativado** - Permita que a conta de Administrador incorporado utilize o Modo de Aprovação do Administrador. Qualquer operação que necessite de elevação de privilégios pede ao utilizador para aprovar a operação.  
  - **Não configurado** - executa todas as aplicações com privilégios de administração completos.  

- **Executar todos os administradores no Modo de Aprovação de Administradores**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Ativado**- Ativar o modo de aprovação do Administrador.  
  - **Não configurado** - Desativar o Modo de Aprovação de Administradores e todas as definições de política relacionadas com o UAC.  

### <a name="microsoft-network-client"></a>Cliente de Rede da Microsoft  

- **Comunicações de sinal de forma digital (se o servidor concordar)**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  Determina se o cliente SMB negoceia a assinatura do pacote SMB.  
  - **Bloco** - O cliente SMB nunca negoceia a assinatura de pacotes SMB.
  - **Não configurado** - O cliente da rede Microsoft pede ao servidor para executar a assinatura de pacote SMB no momento da configuração da sessão. Se a assinatura de pacotes estiver ativada no servidor, a assinatura de pacotes será negociada.  

- **Envie senha não encriptada para servidores SMB de terceiros**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Block** - O redirector do Bloco de Mensagens do Servidor (SMB) pode enviar palavras-passe simples para servidores SMB não Microsoft que não suportam encriptação de palavra-passe durante a autenticação.  
  - **Não configurado** - Bloqueie o envio de senhas de texto simples. As palavras-passe estão encriptadas.  

- **Comunicações de sinal digital (sempre)**  
  **Predefinição**: Não configurado  
  Opções locais DeSegurança CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Ativar** - O cliente da rede Microsoft não comunica com um servidor de rede da Microsoft a menos que esse servidor concorde com a assinatura de pacotes SMB.  
  - **Não configurado** - A assinatura do pacote SMB é negociada entre o cliente e o servidor.  

### <a name="microsoft-network-server"></a>Servidor de Rede da Microsoft  
  
- **Assinar comunicações digitalmente (se o cliente concordar)**  
  **Predefinição**: Não configurado  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Enable** - O servidor de rede da Microsoft negoceia a assinatura de pacotes SMB conforme solicitado pelo cliente. Ou seja, se a assinatura de pacotes estiver ativada no cliente, a assinatura de pacotes será negociada.  
  - **Não configurado** - O cliente SMB nunca negoceia a assinatura de pacotes SMB.  

- **Comunicações de sinal digital (sempre)**  
  **Predefinição**: Não configurado  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Ativar** - O servidor da rede Microsoft não comunica com um cliente da rede Microsoft a menos que esse cliente concorde com a assinatura de pacotes SMB.  
  - **Não configurado** - A assinatura do pacote SMB é negociada entre o cliente e o servidor.  

## <a name="xbox-services"></a>Serviços Xbox

- **Tarefa de poupança de jogo xbox**  
  **Predefinição**: Não configurado  
  CSP: [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Esta definição determina se a Xbox Game Save Task está ativada ou desativada.  
  - **Habilitado**
  - **Não configurado**

- **Serviço de Gestão de Acessórios Xbox**  
  **Predefinição**: Manual  
  CSP: [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  Esta definição determina o tipo de início do Serviço de Gestão do Acessório.  
  - **Manual**
  - **Automático**
  - **Deficientes**

- **Serviço de Gerente Auth Xbox Live**  
  **Predefinição**: Manual  
  CSP: [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Esta definição determina o tipo de início do Serviço de Gerente live Auth.  
  - **Manual**
  - **Automático**
  - **Deficientes**
 
- **Serviço de salvamento de jogos xbox ao vivo**  
  **Predefinição**: Manual  
  CSP: [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Esta definição determina o tipo de início do Serviço de Salvamento de Jogos Ao Vivo.  
  - **Manual**
  - **Automático**
  - **Deficientes**

- **Serviço de Rede Xbox Live**  
  **Predefinição**: Manual  
  CSP: [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Esta definição determina o tipo de início do Serviço de Rede.  
  - **Manual**
  - **Automático**
  - **Deficientes**

## <a name="user-rights"></a>Direitos dos Utilizadores

- **Aceda ao Credential Manager como chamador de confiança**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/AccessCredentialManagerAsTrustedCaller](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accesscredentialmanagerastrustedcaller)

  Este direito de utilizador é utilizado pelo Credential Manager durante as operações de Backup e Restauro. As credenciais guardadas pelos utilizadores podem ser comprometidas se este privilégio for dado a outras entidades.
  - **Não configurado**
  - **Permitir**

- **Permitir o login local**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/AllowLocalLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-allowlocallogon)

  Este direito de utilizador determina quais os utilizadores que podem iniciar sessão no computador.
  - **Não configurado**
  - **Permitir**

- **Permitir o acesso da Rede**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/AccessFromNetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accessfromnetwork)

  Este direito de utilizador determina quais os utilizadores e grupos que podem ligar-se ao computador sobre a rede.
  - **Não configurado**
  - **Permitir**

- **Agir como parte do Sistema Operativo**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/ActaspartofTheOperatingSystem](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-actaspartoftheoperatingsystem)

  Agir como parte do Sistema Operativo
  - **Não configurado**
  - **Permitir**  

- **Ficheiros e diretórios de backup**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/BackupFilesAndDirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-backupfilesanddirectories)

  Este direito de utilizador determina quais os utilizadores que podem contornar as permissões de ficheiros, diretórios, registos e outros objetos persistentes ao fazer backup de ficheiros e diretórios.
  - **Não configurado**
  - **Permitir**

- **Alterar o tempo do sistema**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/ChangeSystemTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-changesystemtime)

  Este direito de utilizador determina quais os utilizadores e grupos que podem alterar a hora e a data no relógio interno do computador.
  - **Não configurado**
  - **Permitir**

- **Criar objetos globais**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/CreateGlobalObjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createglobalobjects)

  Esta definição de segurança determina se os utilizadores podem criar objetos globais que estão disponíveis para todas as sessões. Os utilizadores que possam criar objetos globais podem afetar processos que decorrem nas sessões de outros utilizadores, o que pode levar à falha da aplicação ou à corrupção de dados.
  - **Não configurado**
  - **Permitir**

- **Criar ficheiro de página**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/CreatePagefile](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpagefile)

  Este direito de utilizador determina quais os utilizadores e grupos que podem chamar uma API interna para criar e alterar o tamanho de um ficheiro de página.
  - **Não configurado**
  - **Permitir**

- **Criar objetos partilhados permanentes**  
  **Predefinição**: Não configurado  
  CSP: [Direitos de utilizador/criarobjetos partilhados permanentes](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpermanentsharedobjects)

  Este direito de utilizador determina quais as contas que podem ser utilizadas por processos para criar um objeto de diretório utilizando o gestor de objetos.
  - **Não configurado**
  - **Permitir**

- **Criar ligações simbólicas**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/CreateSymbolicLinks](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createsymboliclinks)

  Este direito de utilizador determina se o utilizador pode criar uma ligação simbólica a partir do computador para o qual está ligado.
  - **Não configurado**
  - **Permitir**

- **Criar fichas**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/CreateToken](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createtoken)

  Este direito de utilizador determina quais os utilizadores/grupos que podem ser utilizados por processos para criar um símbolo que pode ser usado para ter acesso a quaisquer recursos locais quando o processo utiliza uma API interna para criar um sinal de acesso.
  - **Não configurado**
  - **Permitir**

- **Programas de depuração**  
  **Predefinição**: Não configurado  
    CSP: [UserRights/DebugPrograms](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-debugprograms)

  Este direito de utilizador determina quais os utilizadores que podem anexar um desordeiro a qualquer processo ou ao núcleo.
  - **Não configurado**
  - **Permitir**

- **Negar o acesso da rede**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/DenyAccessFromNetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyaccessfromnetwork)

  Este direito de utilizador determina quais os utilizadores que estão impedidos de aceder a um computador por toda a rede.
  - **Não configurado**
  - **Permitir**

- **Negar o log on como um serviço**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/DenyLocalLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denylocallogon)

  Esta definição de segurança determina quais as contas de serviço que estão impedidas de registar um processo como serviço.
  - **Não configurado**
  - **Permitir**

- **Negar iniciar sessão através dos Serviços de Ambiente de Trabalho Remoto**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/DenyRemoteDesktopServicesLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyremotedesktopserviceslogon)

  Este direito de utilizador determina quais os utilizadores e grupos que estão proibidos de iniciar sessão como cliente dos Serviços de Ambiente de Trabalho Remoto.
  - **Não configurado**
  - **Permitir**

- **Permitir a delegação**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/Enabledelegação](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-enabledelegation)

 Este direito de utilizador determina quais os utilizadores que podem definir a definição de Confiança para delegação num utilizador ou objeto de computador.
  - **Não configurado**
  - **Permitir**

- **Gerar auditorias de segurança**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/GenerateSecurityAudits](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-generatesecurityaudits)

  Este direito de utilizador determina quais as contas que podem ser utilizadas por um processo para adicionar entradas ao registo de segurança. O registo de segurança é usado para rastrear acesso não autorizado ao sistema.
  - **Não configurado**
  - **Permitir**

- **Fazer-se passar por um cliente**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/ImpersonateClient](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-impersonateclient)

  Atribuir este direito de utilizador a um utilizador permite que os programas em execução em nome desse utilizador se personifiquem de um cliente. Exigir este direito de utilizador a este tipo de personificação impede um utilizador não autorizado de convencer um cliente a ligar-se a um serviço que criou e, em seguida, personificar esse cliente, o que pode elevar as permissões do utilizador não autorizado para níveis administrativos ou de sistema.
  - **Não configurado**
  - **Permitir**

- **Aumentar a prioridade de agendamento**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/AumentarA Prioridade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-increaseschedulingpriority) de Agendamento

  Este direito de utilizador determina quais as contas que podem utilizar um processo com o acesso da Write Property a outro processo para aumentar a prioridade de execução atribuída ao outro processo.
  - **Não configurado**
  - **Permitir**

- **Carregador e descarregar controladores de dispositivos**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/LoadunloadDeviceDrivers](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-loadunloaddevicedrivers)

  Este direito de utilizador determina quais os utilizadores que podem carregar e descarregar dinamicamente os controladores do dispositivo ou outro código no modo kernel.
  - **Não configurado**
  - **Permitir**

- **Bloquear páginas na memória**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/LockMemory](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-lockmemory)

  Este direito de utilizador determina quais as contas que podem utilizar um processo para manter os dados na memória física, o que impede o sistema de apagar os dados para a memória virtual no disco.
  - **Não configurado**
  - **Permitir**

- **Gerir registo de auditoria e segurança**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/ManageAuditingAndSecurityLog](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-manageauditingandsecuritylog)

  Este direito de utilizador determina quais os utilizadores que podem especificar opções de auditoria de acesso a objetos para recursos individuais, tais como ficheiros, objetos de Diretório Ativo e chaves de registo.
  - **Não configurado**
  - **Permitir**

- **Executar tarefas de manutenção de volume**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/ManageVolume](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-managevolume)

  Este direito de utilizador determina quais os utilizadores e grupos que podem executar tarefas de manutenção num volume, como desfragmentação remota.
  - **Não configurado**
  - **Permitir**

- **Modificar os valores ambientais do firmware**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/ModificarFirmwareEnvironment](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyfirmwareenvironment)

  Este direito de utilizador determina quem pode modificar os valores ambientais do firmware.
  - **Não configurado**
  - **Permitir**

- **Modificar uma etiqueta de objeto**  
  **Predefinição**: Não configurado  
  CSP: [Userrights/ModificarObjectLabel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyobjectlabel)

  Este direito de utilizador determina quais as contas de utilizador que podem modificar a etiqueta de integridade dos objetos, tais como ficheiros, chaves de registo ou processos detidos por outros utilizadores.
  - **Não configurado**
  - **Permitir**

- **Processo único de perfil**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/ProfileSingleProcess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-profilesingleprocess)

  Este direito de utilizador determina quais os utilizadores que podem utilizar ferramentas de monitorização do desempenho para monitorizar o desempenho dos processos do sistema.
  - **Não configurado**
  - **Permitir**

- **Paragem remota**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/RemoteShutdown](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-remoteshutdown)

  Este direito de utilizador determina quais os utilizadores autorizados a desligar um computador a partir de uma localização remota da rede. O uso indevido deste direito de utilizador pode resultar numa negação de serviço.
  - **Não configurado**
  - **Permitir**
  
- **Restaurar ficheiros e diretórios**  
  **Predefinição**: Não configurado  
  CSP: [UserRights/RestoreFilesAndDirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-restorefilesanddirectories)
  
  Este direito de utilizador determina quais os utilizadores que podem contornar as permissões de ficheiros, diretórios, registos e outros objetos persistentes ao restaurar ficheiros e diretórios de reserva, e determina quais os utilizadores que podem definir qualquer diretor de segurança válido como proprietário de um objeto.
  - **Não configurado**
  - **Permitir**
  
- **Tomar posse de ficheiros ou objetos**  
  **Predefinição**: Não configurado  
  CSP: [Direitos de Utilizador/Apropriação](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-takeownership)

  Este direito de utilizador determina quais os utilizadores que podem apropriar-se de qualquer objeto titular no sistema, incluindo objetos de Diretório Ativo, ficheiros e pastas, impressoras, chaves de registo, processos e fios.
  - **Não configurado**
  - **Permitir**

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](../configuration/device-profile-assign.md)e [monitorize o seu estado](../configuration/device-profile-monitor.md).  

Configure as definições de proteções de pontofinal nos dispositivos [macOS.](endpoint-protection-macos.md)  
