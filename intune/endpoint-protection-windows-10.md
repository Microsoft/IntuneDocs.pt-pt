---
title: Configurações de proteção para dispositivos Windows 10 no Microsoft Intune-Azure | Microsoft Docs
description: Em dispositivos Windows 10, use ou defina as configurações do Endpoint Protection para habilitar os recursos do Windows Defender, incluindo o Application Guard, o firewall, o SmartScreen, a criptografia e o BitLocker, o Exploit Guard, o controle de aplicativos, a central de segurança e a segurança em dispositivos locais no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cdd5ae83d1ef71be31ad4507b32d2d4484da58cb
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71301737"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Configurações do Windows 10 (e posterior) para proteger dispositivos usando o Intune  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]  

O Microsoft Intune inclui muitas configurações para ajudar a proteger seus dispositivos. Este artigo descreve todas as configurações que você pode habilitar e configurar no Windows 10 e em dispositivos mais recentes. Essas configurações são criadas em um perfil de configuração do Endpoint Protection no Intune para controlar a segurança, incluindo o BitLocker e o Windows Defender.  

Para configurar o Windows Defender antivírus, consulte [restrições de dispositivo do Windows 10](device-restrictions-windows-10.md#microsoft-defender-antivirus).  

## <a name="before-you-begin"></a>Antes de começar  

[Criar um perfil de configuração de dispositivo do Endpoint Protection](endpoint-protection-configure.md).  

Para obter mais informações sobre provedores de serviços de configuração (CSPs), consulte [referência do provedor de serviços de configuração](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard  

Ao utilizar o Microsoft Edge, o Windows Defender Application Guard protege o seu ambiente contra sites que a sua organização não considera como sendo de confiança. Quando os usuários visitam sites que não estão listados em seu limite de rede isolado, os sites são abertos em uma sessão de navegação virtual do Hyper-V. Os sites confiáveis são definidos por um limite de rede, que são configurados na configuração do dispositivo.  

O Application Guard só está disponível para dispositivos com o Windows 10 (64 bits). Se utilizar este perfil, instalará um componente do Win32 para ativar o Application Guard.  

- **Proteção de aplicativo**  
  **Padrão**: Não configurado  
   CSP do Application Guard: [Configurações/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Habilitado para borda** – ativa esse recurso, que abre sites não confiáveis em um contêiner de navegação virtualizado do Hyper-V.  
  - **Não configurado** -qualquer site (confiável e não confiável) pode ser aberto no dispositivo.  

- **Comportamento da área de transferência**  
  **Padrão**: Não configurado  
   CSP do Application Guard: [Configurações/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  Escolha quais ações de copiar e colar são permitidas entre o computador local e o navegador virtual do Application Guard.  
  - **Não configurado**  
  - **Permitir copiar e colar do PC para o navegador somente**  
  - **Permitir copiar e colar do navegador para o PC somente**  
  - **Permitir copiar e colar entre PC e navegador**  
  - **Bloquear copiar e colar entre PC e navegador**  

- **Conteúdo da área de transferência**  
  Essa configuração está disponível somente quando o *comportamento da área de transferência* é definido como uma das configurações de *permissão* .  
  **Padrão**: Não configurado  
  CSP do Application Guard: [Configurações/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Selecione o conteúdo da área de transferência permitido.  
  - **Não configurado**  
  - **Text**  
  - **Imagens**  
  - **Texto e imagens**  

- **Conteúdo externo em sites corporativos**  
  **Padrão**: Não configurado  
  CSP do Application Guard: [Configurações/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **Bloquear o** carregamento de conteúdo de sites não aprovados de blocos.  
  - **Não configurado** -sites não empresariais podem ser abertos no dispositivo.  
 
- **Imprimir do navegador virtual**  
  **Padrão**: Não configurado  
  CSP do Application Guard: [Configurações/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Permitir** – permite a impressão do conteúdo selecionado do navegador virtual.  
  - **Não configurado** Desabilitar todos os recursos de impressão.  

  Ao *permitir* a impressão, você pode definir a seguinte configuração:
  - **Tipo (s) de impressão** Selecione uma ou mais das seguintes opções:  
    - PDF  
    - XPS  
    - Impressoras locais
    - Impressoras de rede  

- **Coletar logs**  
  **Padrão**: Não configurado  
  CSP do Application Guard: [Auditoria/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Allow** -coletar logs de eventos que ocorrem em uma sessão de navegação do Application Guard.  
  - **Não configurado** -não colete nenhum log dentro da sessão de navegação.  

- **Manter dados de navegador gerados pelo usuário**  
  **Padrão**: Não configurado  
  CSP do Application Guard: [Configurações/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Permitir** Salve os dados do usuário (como senhas, favoritos e cookies) que são criados durante uma sessão de navegação virtual do Application Guard.  
  - **Não configurado** Descartar arquivos e dados baixados pelo usuário quando o dispositivo for reiniciado ou quando um usuário sair.  

- **Aceleração de gráficos**  
 **Padrão**: Não configurado  
  CSP do Application Guard: [Configurações/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **Habilitar** -carregar sites e vídeos com uso intensivo de gráficos com mais rapidez ao obter acesso a uma unidade de processamento gráfico virtual.  
  - **Não configurado** Use a CPU do dispositivo para gráficos; Não use a unidade de processamento gráfico virtual.  

- **Baixar arquivos para o sistema de arquivos do host**  
  **Padrão**: Não configurado  
  CSP do Application Guard: [Configurações/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Habilitar** -os usuários podem baixar arquivos do navegador virtualizado para o sistema operacional do host.  
  - **Não configurado** -mantém os arquivos locais no dispositivo e não baixa os arquivos para o sistema de arquivos do host.  

## <a name="windows-defender-firewall"></a>Firewall do Windows Defender  
 
### <a name="global-settings"></a>Definições globais  

Estas definições são aplicáveis a todos os tipos de rede.  

- **protocolo FTP**  
  **Padrão**: Não configurado  
   CSP do firewall: [MdmStore/global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **Bloquear** -desabilitar FTP com estado.  
  - **Não configurado** -o firewall monitora a filtragem de FTP para permitir conexões secundárias.  

- **Tempo ocioso de associação de segurança antes da exclusão**  
  **Padrão**: *Não configurado*  
   CSP do firewall: [MdmStore/global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   Especifique um tempo ocioso em segundos, após o qual as associações de segurança são excluídas.   

- **Codificação de chave pré-compartilhada**  
  **Padrão**: Não configurado  
   CSP do firewall: [MdmStore/global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Enable** -codificar chaves distorcedas usando UTF-8.  
   - **Não configurado** – codifique chaves distorcidos usando o valor do repositório local.  

- **Isenções IPsec**  
  **Padrão**: *0 selecionados*  
   CSP do firewall: [MdmStore/global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   Selecione um ou mais dos seguintes tipos de tráfego a serem isentos do IPsec:  
   - **Descoberta de vizinho de códigos do tipo IPv6 ICMP**  
   - **ICMP**  
   - **Descoberta de router de códigos do tipo IPv6 ICMP**  
   - **Tráfego de rede de IPv4 e IPv6 DHCP**  

- **Verificação da lista de certificados revogados**  
  **Padrão**: Não configurado  
  CSP do firewall: [MdmStore/global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  Escolha como o dispositivo verifica a lista de certificados revogados. As opções incluem:  
  - **Desabilitar verificação de CRL**  
  - **Falha na verificação de CRL somente no certificado revogado**  
  - **Falha na verificação de CRL em qualquer erro encontrado**.  
 

- **Correspondência oportuna de conjunto de autenticação por módulo de criação de chave**  
  **Padrão**: Não configurado  
  CSP do firewall: [MdmStore/global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Habilitar** Os módulos de criação de chaves devem ignorar apenas os conjuntos de autenticação para os quais eles não oferecem suporte.  
  - **Não configurado**, os módulos de chaveamento devem ignorar o conjunto de autenticação inteiro se não oferecerem suporte a todos os pacotes de autenticação especificados no conjunto.  


- **Enfileiramento de pacotes**  
  **Padrão**: Não configurado  
  CSP do firewall: [MdmStore/global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Especifique como o dimensionamento de software no lado de recebimento está habilitado para recebimento criptografado e texto não criptografado para o cenário de gateway de túnel IPsec. Essa configuração confirma que a ordem do pacote é preservada. As opções incluem:  
  - **Não configurado**  
  - **Desabilitar todos os enfileiramentos de pacotes**  
  - **Enfileirar somente pacotes criptografados de entrada**  
  - **Os pacotes de fila após a descriptografia são executados somente para encaminhamento**  
  - **Configurar pacotes de entrada e de saída**  

### <a name="network-settings"></a>Definições de rede  

As configurações a seguir são listadas neste artigo uma única vez, mas todas se aplicam aos três tipos de rede específicos:  
- **Rede de domínio (local de trabalho)**  
- **Rede privada (detectável)**  
- **Rede pública (não detectável)**  

#### <a name="general-settings"></a>Definições gerais  

- **Firewall do Windows Defender**  
  **Padrão**: Não configurado  
  CSP do firewall: [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Habilitar** -ativar o firewall e segurança avançada. 
  - **Não configurado** Permite todo o tráfego de rede, independentemente de qualquer outra configuração de política.  

- **Modo furtivo**  
  **Padrão**: Não configurado  
  CSP do firewall: [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **Não configurado**  
  - O **bloqueio** do firewall está impedido de operar no modo furtivo. Esta definição também lhe permite bloquear a **Exceção de pacotes seguros com IPsec**.  
  - **Permitir** -o firewall opera no modo furtivo, o que ajuda a evitar respostas para solicitações de investigação.  

- **Isenção de pacote protegido por IPsec com modo furtivo**  
  **Padrão**: Não configurado  
  CSP do firewall: [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Essa opção será ignorada se o *modo stealth* estiver definido como *Bloquear*.  

  - **Não configurado**  
  - **Bloquear** -os pacotes protegidos por IPsec não recebem isenções.  
  - **Permitir** -habilitar isenções. O modo stealth do firewall não deve impedir que o computador host responda ao tráfego de rede não solicitado que é protegido pelo IPsec.  

- **Blindadas**  
  **Padrão**: Não configurado  
  CSP do firewall: [Blindadas](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **Não configurado**  
    - **Bloquear** – quando o Windows Defender firewall está ativado e essa configuração é definida como *Bloquear*, todo o tráfego de entrada é bloqueado, independentemente de outras configurações de política. 
    - **Allow** -quando definido como *permitir*, essa configuração é desativada e o tráfego de entrada é permitido com base em outras configurações de política.

- **Respostas unicast para difusões multicast**  
  **Padrão**: Não configurado  
  CSP do firewall: [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  Normalmente, não quer receber respostas unicast para mensagens multicast ou de difusão. Essas respostas podem indicar um ataque de negação de serviço (DOS) ou um invasor tentando sondar um computador em tempo real conhecido.  
  - **Não configurado**  
  - **Bloquear** -desabilitar respostas unicast para difusões multicast.  
  - **Permitir** -permitir respostas unicast para difusões multicast.  

- **Notificações de entrada**  
  **Padrão**: Não configurado  
  CSP do firewall: [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **Não configurado**  
  - **Bloquear** -ocultar notificações a serem usadas quando um aplicativo for impedido de escutar em uma porta.  
  - **Permitir** – habilita essa configuração e pode mostrar uma notificação para os usuários quando um aplicativo é impedido de escutar em uma porta.  

- **Ação padrão para conexões de saída**  
  **Padrão**: Não configurado  
  CSP do firewall: [Outboundaction](https://aka.ms/intune-firewall-outboundaction)  
  
  Configure a ação padrão que o firewall executa em conexões de saída. Essa configuração será aplicada ao Windows versão 1809 e superior.  

  - **Não configurado**  
  - **Bloquear** -a ação de firewall padrão não é executada no tráfego de saída, a menos que seja explicitamente especificado para não bloquear.  
  - **Permitir** -ações de firewall padrão executadas em conexões de saída.  

- **Ação padrão para conexões de entrada**  
  **Padrão**: Não configurado  
  CSP do firewall: [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **Não configurado**  
  - **Bloquear** -a ação de firewall padrão não é executada em conexões de entrada.  
  - **Permitir que** ações de firewall padrão sejam executadas em conexões de entrada.  

#### <a name="rule-merging"></a>Intercalação de regras  

- **Regras do Windows Defender Firewall do aplicativo autorizado do repositório local**  
  **Padrão**: Não configurado  
  CSP do firewall: [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **Não configurado**  
  - **Bloquear** -as regras de firewall do aplicativo autorizado no repositório local são ignoradas e não são impostas.  
  - **Permitir** Escolha habilitar aplica regras de firewall no repositório local para que elas sejam reconhecidas e impostas. -
     

- **Regras de porta global do Windows Defender Firewall do repositório local**  
  **Padrão**: Não configurado  
  CSP do firewall: [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **Não configurado**  
  - **Bloquear** -as regras de firewall de porta global no repositório local são ignoradas e não são impostas.  
  - **Permitir** -aplicar regras de firewall de porta global no repositório local para serem reconhecidas e impostas.  

- **Regras do Windows Defender Firewall do repositório local**  
  **Padrão**: Não configurado  
  CSP do firewall: [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **Não configurado**  
  - As regras de firewall de **bloqueio** do repositório local são ignoradas e não são impostas.
  - **Permitir** -aplicar regras de firewall no repositório local para ser reconhecido e imposto.  

- **Regras de IPsec do repositório local**  
  **Padrão**: Não configurado  
  CSP do firewall: [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **Não configurado**  
  - **Bloquear** – as regras de segurança de conexão do repositório local são ignoradas e não são impostas, independentemente da versão do esquema e da versão da regra de segurança de conexão.  
  - **Permitir** -aplicar regras de segurança de conexão do repositório local, independentemente das versões de regra de segurança de esquema ou de conexão.  

### <a name="firewall-rules"></a>Regras de firewall  

Você pode **Adicionar** uma ou mais regras de firewall personalizadas. Para obter mais informações, consulte [adicionar regras personalizadas de firewall para dispositivos Windows 10](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

As regras de firewall personalizadas dão suporte às seguintes opções:  

#### <a name="general-settings"></a>Configurações gerais:  

- **Name**  
  **Padrão**: *Sem nome*  

  Especifique um nome amigável para a regra. Esse nome aparecerá na lista de regras para ajudá-lo a identificá-lo.  

- **Descrição**  
  **Padrão**: *Sem descrição*  

  Forneça uma descrição da regra.  

- **Direção**   
  **Padrão**: Não configurado  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Especifique se essa regra se aplica ao tráfego de **entrada**ou de **saída** . Quando definido como **não configurado**, a regra se aplica automaticamente ao tráfego de saída.  

- **ação**  
  **Padrão**: Não configurado  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)e [FirewallRules/*FirewallRuleName*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Selecione de **permitir** ou **Bloquear**. Quando definido como **não configurado**, a regra assume como padrão permitir o tráfego.  

- **Tipo de rede**  
  **Padrão**: 0 selecionado  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Selecione até três tipos de tipos de rede aos quais essa regra pertence. As opções incluem **domínio**, **privado**e **público**.  Se nenhum tipo de rede for selecionado, a regra se aplicará a todos os três tipos de rede.  

#### <a name="application-settings"></a>Definições da aplicação  

- **Aplicativo (s)**  
  **Padrão**: Todos  

  Controlar conexões para um aplicativo ou programa. Selecione uma das seguintes opções e, em seguida, conclua a configuração adicional:  
  - **Nome da família de pacotes** – especifique um nome de família de pacotes. Para localizar o nome da família de pacotes, use o comando **Get-AppxPackage**do PowerShell.   
    CSP do firewall: [FirewallRules/*FirewallRuleName*/app/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **Caminho do arquivo** – você deve especificar um caminho de arquivo para um aplicativo no dispositivo cliente, que pode ser um caminho absoluto ou um caminho relativo. Por exemplo:  C:\Windows\System\Notepad.exe ou%WINDIR%\Notepad.exe.  
    CSP do firewall: [FirewallRules/*FirewallRuleName*/app/FilePath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Serviço do Windows** – especifique o nome curto do serviço do Windows se ele for um serviço e não um aplicativo que envia ou recebe tráfego. Para localizar o nome curto do serviço, use o comando do PowerShell **Get-Service**.  
    CSP do firewall: [FirewallRules/*FirewallRuleName*/app/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Tudo**– *nenhuma configuração adicional está disponível*.  

#### <a name="ip-address-settings"></a>Configurações de endereço IP  

Especifique os endereços locais e remotos aos quais essa regra se aplica.  

- **Endereços locais**    
  **Padrão**: Qualquer endereço  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Selecione **qualquer endereço** ou **endereço especificado**.  

  Ao usar o *endereço especificado*, você adiciona um ou mais endereços como uma lista separada por vírgulas de endereços locais que são cobertos pela regra. Os tokens válidos incluem:  
  - Use um asterisco "*" para *qualquer* endereço local. Se você usar um asterisco, ele deverá ser o único token que você usar.  
  - Para especificar uma sub-rede, use a máscara de sub-rede ou a notação de prefixo de rede. Se nem uma máscara de sub-rede nem um prefixo de rede for especificado, a máscara de sub-rede padrão será 255.255.255.255.  
  - Um endereço IPv6 válido.  
  - Um intervalo de endereços IPv4 no formato "endereço inicial do endereço final" sem espaços incluídos.  
  - Um intervalo de endereços IPv6 no formato "endereço inicial de endereço final" sem espaços incluídos.  

- **Endereços remotos**  
  **Padrão**: Qualquer endereço  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Selecione **qualquer endereço** ou **endereço especificado**.  

  Ao usar o *endereço especificado*, você adiciona um ou mais endereços como uma lista separada por vírgulas de endereços remotos que são cobertos pela regra. Os tokens não diferenciam maiúsculas de minúsculas. Os tokens válidos incluem:  
  - Use um asterisco "*" para *qualquer* endereço remoto. Se você usar um asterisco, ele deverá ser o único token que você usar.  
  - DefaultGateway  
  - DHCP  
  - DNS  
  - WINS  
  - "Intranet" (com suporte nas versões 1809 e posteriores do Windows)  
  - "RmtIntranet" (com suporte nas versões 1809 e posteriores do Windows)  
  - "Internet" (com suporte no Windows versões 1809 e posteriores)  
  - "Ply2Renders" (com suporte nas versões 1809 e posteriores do Windows)  
  - "LocalSubnet" indica qualquer endereço local na sub-rede local.  
  - Para especificar uma sub-rede, use a máscara de sub-rede ou a notação de prefixo de rede. Se nem uma máscara de sub-rede nem um prefixo de rede for especificado, a máscara de sub-rede padrão será 255.255.255.255.  
  - Um endereço IPv6 válido.  
  - Um intervalo de endereços IPv4 no formato "endereço inicial do endereço final" sem espaços incluídos.  
  - Um intervalo de endereços IPv6 no formato "endereço inicial de endereço final" sem espaços incluídos.  

#### <a name="port-and-protocol-settings"></a>Configurações de porta e protocolo  
Especifique as portas locais e remotas às quais essa regra se aplica.  

- **Protocolo**  
  **Padrão**: Any  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Selecione uma das seguintes opções e conclua as configurações necessárias:  
  - **Tudo** – nenhuma configuração adicional está disponível.  
  - **TCP** – configurar portas locais e remotas. Ambas as opções dão suporte a todas as portas ou portas especificadas. Insira as portas especificadas usando uma lista separada por vírgulas.  
    - **Portas locais** -CSP de firewall: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Portas remotas** -CSP de firewall: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** – configurar portas locais e remotas. Ambas as opções dão suporte a todas as portas ou portas especificadas. Insira as portas especificadas usando uma lista separada por vírgulas.  
    - **Portas locais** -CSP de firewall: [FirewallRules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Portas remotas** -CSP de firewall: [FirewallRules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Personalizado** – especifique um número de **protocolo** personalizado de 0 a 255.  

#### <a name="advanced-configuration"></a>Configuração avançada  
- **Tipos de interface**  
  **Padrão**: 0 selecionado  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/interfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Selecione uma das seguintes opções:  
  - **Acesso remoto**  
  - **Sem fio**  
  - **Rede de área local**  

- **Permitir conexões somente desses usuários**  
  **Padrão**: Todos os usuários *(o padrão é todos os usos quando nenhuma lista é especificada)*  
  CSP do firewall: [FirewallRules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  Especifique uma lista de usuários locais autorizados para esta regra. Uma lista de usuários autorizados não poderá ser especificada se essa regra se aplicar a um serviço do Windows.  


## <a name="windows-defender-smartscreen-settings"></a>Definições do Windows Defender SmartScreen  
 
O Microsoft Edge deve ser instalado no dispositivo.  

- **SmartScreen para aplicativos e arquivos**  
  **Padrão**: Não configurado  
   CSP do SmartScreen: [SmartScreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **Não configurado** -desabilita o uso do SmartScreen.  
  - **Habilitar** -habilitar o Windows SmartScreen para execução de arquivos e executar aplicativos. O SmartScreen é um componente anti-phishing e anti-malware baseado na cloud.  

- **Execução de arquivos não verificados**  
  **Padrão**: Não configurado  
   CSP do SmartScreen: [SmartScreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Não configurado** -desabilita esse recurso e permite que os usuários finais executem arquivos que não foram verificados.  
  - **Bloquear** – impedir que os usuários finais executem arquivos que não foram verificados pelo Windows SmartScreen.  

## <a name="windows-encryption"></a>Encriptação do Windows  
 
### <a name="windows-settings"></a>Definições do Windows  

Essas configurações de criptografia se aplicam a todas as versões do Windows 10.  

- **Criptografar dispositivos**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Exigir** -solicitar que os usuários habilitem a criptografia do dispositivo. Consoante a edição do Windows e configuração do sistema, poderá ser pedido aos utilizadores:  
    - Para confirmar que a criptografia de outro provedor não está habilitada.  
    - Ser necessário para desligar Criptografia de Unidade de Disco BitLocker e, em seguida, ativar o BitLocker novamente.  
  - **Não configurado**  
  
  Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável.  

- **Criptografar cartão de armazenamento (somente dispositivos móveis)**  
  *Essa configuração se aplica somente ao Windows 10 Mobile.*  
  **Padrão**: Não configurado  
  CSP do BitLocker: [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - **Exigir** para criptografar quaisquer cartões de armazenamento removíveis usados pelo dispositivo.  
  - **Não configurado** -não exige criptografia de cartão de memória e não solicita que o usuário o ative.  

### <a name="bitlocker-base-settings"></a>Definições base do BitLocker  

As definições base são definições de BitLocker universais para todos os tipos de unidades de dados. Estas definições gerem as tarefas de encriptação ou opções de configuração de unidades que o utilizador final pode modificar para todos os tipos de unidades de dados.  

- **Aviso para outra criptografia de disco**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Bloquear** – desabilite o prompt de aviso se outro serviço de criptografia de disco estiver no dispositivo.  
  - **Não configurado** -permite que o aviso para outra criptografia de disco seja mostrado.  

  Quando definido como *Bloquear*, você pode definir a seguinte configuração:  

  - **Permitir que usuários padrão habilitem a criptografia durante o ingresso no Azure AD**  
    *Essa configuração se aplica somente a dispositivos Unidos Azure Active Directory (Azure ADJ) e depende da configuração anterior, `Warning for other disk encryption`.*  
    **Padrão**: Não configurado  
    CSP do BitLocker: [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Permitir** -usuários padrão (não administradores) podem habilitar a criptografia BitLocker quando conectado.  
     - **Não configurado** somente os administradores podem habilitar a criptografia BitLocker no dispositivo.  

- **Configurar métodos de criptografia**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Habilitar** -configurar algoritmos de criptografia para sistema operacional, dados e unidades removíveis.  
  - **Não configurado** -o BitLocker usa o XTS-AES 128 bit como o método de criptografia padrão ou usa o método de criptografia especificado por qualquer script de instalação.  

  Quando definido como *habilitar*, você pode definir as seguintes configurações:  

  - **Criptografia para unidades do sistema operacional**  
    **Padrão**: XTS-AES 128-bit  
   
    Escolha o método de criptografia para unidades do sistema operacional. Recomendamos que utilize o algoritmo XTS-AES.  
    - **AES-CBC 128 bits**  
    - **AES-CBC 256 bits**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

  - **Criptografia para unidades de dados fixas**  
    **Padrão**: AES-CBC 128 bits  
   
    Escolha o método de criptografia para unidades de dados fixas (internas). Recomendamos que utilize o algoritmo XTS-AES.  
    - **AES-CBC 128 bits**  
    - **AES-CBC 256 bits**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

  - **Criptografia para unidades de dados removíveis**  
    **Padrão**: AES-CBC 128 bits  

    Escolha o método de criptografia para unidades de dados removíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.  
    - **AES-CBC 128 bits**  
    - **AES-CBC 256 bits**  
    - **XTS-AES 128-bit**  
    - **XTS-AES 256-bit**  

### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker  

Estas definições aplicam-se especificamente a unidades de dados do sistema operativo.  

- **Autenticação adicional na inicialização**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Exigir** -configurar os requisitos de autenticação para a inicialização do computador, incluindo o uso de Trusted Platform Module (TPM).  
  - **Não configurado** – configure apenas as opções básicas em dispositivos com um TPM.  

  Quando definido como *exigir*, você pode definir as seguintes configurações:  

  - **BitLocker com chip do TPM não compatível**  
    **Padrão**: Não configurado  

    - **Bloquear** -desabilitar o uso do BitLocker quando um dispositivo não tiver um chip TPM compatível.  
    - **Não configurado** -os usuários podem usar o BitLocker sem um chip TPM compatível. O BitLocker poderá precisar de uma palavra-passe ou de uma chave de arranque.  

  - **Inicialização de TPM compatível**  
    **Padrão**: Permitir TPM  

    Configure se o TPM é permitido, obrigatório ou não permitido.  

    - **Permitir TPM**  
    - **Não permitir TPM**  
    - **Exigir TPM**  

  - **PIN de inicialização do TPM compatível**  
    **Padrão**: Permitir PIN de inicialização com TPM  

    Escolha permitir, não permitir ou exigir o uso de um PIN de inicialização com o chip do TPM. Para ativar um PIN de arranque, é necessária interação por parte do utilizador final.  

    - **Permitir PIN de inicialização com TPM**  
    - **Não permitir PIN de inicialização com TPM**  
    - **Exigir PIN de inicialização com TPM**

  - **Chave de inicialização do TPM compatível**  
    **Padrão**: Permitir chave de inicialização com TPM  

    Opte por permitir, não permitir ou exigir o uso de uma chave de inicialização com o chip do TPM. Para ativar uma chave de arranque, é necessária interação por parte do utilizador final.  

    - **Permitir chave de inicialização com TPM**  
    - **Não permitir chave de inicialização com TPM**  
    - **Exigir chave de inicialização com TPM**  

  - **Chave de inicialização e PIN compatíveis do TPM**  
    **Padrão**: Permitir chave de inicialização e PIN com TPM  

    Escolha permitir, não permitir ou exigir o uso de uma chave de inicialização e o PIN com o chip do TPM. Para ativar uma chave e PIN de arranque, é necessária interação por parte do utilizador final.  
    - **Permitir chave de inicialização e PIN com TPM**  
    - **Não permitir chave de inicialização e PIN com TPM**  
    - **Exigir chave de inicialização e PIN com TPM**   

- **Comprimento mínimo do PIN**  
    **Padrão**: Não configurado  
    CSP do BitLocker: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Habilitar** Configure um comprimento mínimo para o PIN de inicialização do TPM.  
    - **Não configurado** -os usuários podem configurar um PIN de inicialização de qualquer comprimento entre 6 e 20 dígitos.  

  Quando definido como *habilitar*, você pode definir a seguinte configuração:  

  - **Mínimo de caracteres**  
    **Padrão**: *Não configurado* CSP do BitLocker: [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    Insira o número de caracteres necessários para o PIN de inicialização de **4**-**20**.  

- **Recuperação de unidade do sistema operacional**  
  **Padrão**: Não configurado   
  CSP do BitLocker: [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Habilitar** -controlar como as unidades do sistema operacional protegidas pelo BitLocker são recuperadas quando as informações de inicialização necessárias não estão disponíveis.  
  - **Não configurado** -as opções de recuperação padrão têm suporte para a recuperação do BitLocker. Por padrão, um DRA é permitido, as opções de recuperação são escolhidas pelo usuário, incluindo a senha de recuperação e a chave de recuperação, e não é feito backup das informações de recuperação para AD DS.  

  Quando definido como *habilitar*, você pode definir as seguintes configurações:  

  - **Agente de recuperação de dados com base em certificado**  
    **Padrão**: Não configurado  
     
    - **Bloquear** – impedir o uso do agente de recuperação de dados com unidades de sistema operacional protegidas pelo BitLocker.  
    - **Não configurado** -permite que os agentes de recuperação de dados sejam usados com unidades do sistema operacional protegidas pelo BitLocker.  

  - **Criação de senha de recuperação do usuário**  
    **Padrão**: Permitir senha de recuperação de 48 dígitos  

    Escolha se os usuários são permitidos, necessários ou não têm permissão para gerar uma senha de recuperação de 48 dígitos.  
    - **Permitir senha de recuperação de 48 dígitos**  
    - **Não permitir senha de recuperação de 48 dígitos**  
    - **Exigir senha de recuperação de 48 dígitos**  

  - **Criação de chave de recuperação do usuário**  
    **Padrão**: Permitir chave de recuperação de 256 bits  

    Escolha se os usuários são permitidos, necessários ou não têm permissão para gerar uma chave de recuperação de 256 bits.  
    - **Permitir chave de recuperação de 256 bits**  
    - **Não permitir chave de recuperação de 256 bits**  
    - **Exigir chave de recuperação de 256 bits**  

  - **Opções de recuperação no assistente de instalação do BitLocker**  
    **Padrão**: Não configurado  

    - **Bloquear** -os usuários não podem ver e alterar as opções de recuperação. Quando definido como 
    - **Não configurado** -os usuários podem ver e alterar as opções de recuperação ao ativarem o BitLocker. 
 
  - **Salvar informações de recuperação do BitLocker para Azure Active Directory**  
    **Padrão**: Não configurado  

    - **Habilitar** -armazenar as informações de recuperação do BitLocker para Azure Active Directory (Azure AD).  
    - **Não configurado** -as informações de recuperação do BitLocker não são armazenadas no AAD.  

  - **Informações de recuperação do BitLocker armazenadas no Azure Active Directory**  
    **Padrão**: Senhas de recuperação de backup e pacotes de chaves  

    Configure quais partes das informações de recuperação do BitLocker são armazenadas no Azure AD. Escolha entre:  
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**  
    - **Apenas palavras-passe de recuperação de cópia de segurança**  

  - **Rotação de senha de recuperação controlada pelo cliente**  
    **Padrão**: Rotação de chaves habilitada para dispositivos ingressados no Azure AD  
    CSP do BitLocker: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Essa configuração inicia uma rotação de senha de recuperação controlada pelo cliente após uma recuperação de unidade do sistema operacional (seja usando bootmgr ou WinRE).  

    - Não configurado  
    - Rotação de chaves desabilitada  
    - Rotação de chaves habilitada para deices unida do Azure AD  
    - Rotação de chaves habilitada para o Azure AD e dispositivos ingressados no híbrido  

  - **Armazenar informações de recuperação em Azure Active Directory antes de habilitar o BitLocker**  
    **Padrão**: Não configurado  
 
     Impedir que os usuários habilitem o BitLocker, a menos que o computador faça o backup com êxito das informações de recuperação do BitLocker para Azure Active Directory.  

    - **Exigir** -impedir que os usuários ativem o BitLocker, a menos que as informações de recuperação do BitLocker sejam armazenadas com êxito no Azure AD.  
    - **Não configurado** -os usuários podem ativar o BitLocker, mesmo que as informações de recuperação não sejam armazenadas com êxito no Azure AD.  

- **Mensagem e URL de recuperação de pré-inicialização**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Habilitar** -configurar a mensagem e a URL que são exibidas na tela de recuperação de chave de pré-inicialização.  
  - **Não configurado** -desabilite esse recurso.  
  
  Quando definido como *habilitar*, você pode definir a seguinte configuração:  
  - **Mensagem de recuperação de pré-inicialização**  
    **Padrão**: Usar mensagem e URL de recuperação padrão   
 
    Configure como a mensagem de recuperação de pré-inicialização é exibida para os usuários. Escolha entre:  
    - **Utilizar mensagem de recuperação predefinida e URL**  
    - **Utilizar mensagem de recuperação vazia e URL**  
    - **Utilizar mensagem de recuperação personalizada**  
    - **Utilizador URL de recuperação personalizada**  

### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker  

Essas configurações se aplicam especificamente a unidades de dados fixas.  

- **Acesso de gravação a unidades de dados fixas não protegidas pelo BitLocker**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Bloquear** – conceda acesso somente leitura a unidades de dados que não são protegidas pelo BitLocker.  
  - **Não configurado** -por padrão, acesso de leitura e gravação a unidades de dados que não são criptografadas.  

- **Recuperação de unidade fixa**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Habilitar** -controlar como as unidades fixas protegidas pelo BitLocker são recuperadas quando as informações de inicialização necessárias não estão disponíveis.  
  - **Não configurado** -desabilite esse recurso.  

  Quando definido como *habilitar*, você pode definir as seguintes configurações:  

  - **Agente de recuperação de dados**  
    **Padrão**: Não configurado  
 
    - **Bloquear** – impedir o uso do agente de recuperação de dados com o editor de política de unidades fixas protegidas pelo BitLocker. 
    - **Não configurado** – habilita o uso de agentes de recuperação de dados com unidades fixas protegidas pelo BitLocker.  

  - **Criação de senha de recuperação do usuário**  
    **Padrão**: Permitir senha de recuperação de 48 dígitos  

    Escolha se os usuários são permitidos, necessários ou não têm permissão para gerar uma senha de recuperação de 48 dígitos.  
    - **Permitir senha de recuperação de 48 dígitos**  
    - **Não permitir senha de recuperação de 48 dígitos**  
    - **Exigir senha de recuperação de 48 dígitos**  

  - **Criação de chave de recuperação do usuário**  
    **Padrão**: Permitir chave de recuperação de 256 bits

    Escolha se os usuários são permitidos, necessários ou não têm permissão para gerar uma chave de recuperação de 256 bits.
    - **Permitir chave de recuperação de 256 bits**  
    - **Não permitir chave de recuperação de 256 bits**  
    - **Exigir chave de recuperação de 256 bits**  

  - **Opções de recuperação no assistente de instalação do BitLocker**  
    **Padrão**: Não configurado  

    - **Bloquear** -os usuários não podem ver e alterar as opções de recuperação. Quando definido como 
    - **Não configurado** -os usuários podem ver e alterar as opções de recuperação ao ativarem o BitLocker.
 
  - **Salvar informações de recuperação do BitLocker para Azure Active Directory**  
    **Padrão**: Não configurado  

    - **Habilitar** -armazenar as informações de recuperação do BitLocker para Azure Active Directory (Azure AD).  
    - **Não configurado** -as informações de recuperação do BitLocker não são armazenadas no AAD.

  - **Informações de recuperação do BitLocker armazenadas no Azure Active Directory**  
    **Padrão**: Senhas de recuperação de backup e pacotes de chaves  

    Configure quais partes das informações de recuperação do BitLocker são armazenadas no Azure AD. Escolha entre:  
    - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**  
    - **Apenas palavras-passe de recuperação de cópia de segurança**  

  - **Rotação de senha de recuperação controlada pelo cliente**  
    **Padrão**: Rotação de chaves habilitada para dispositivos ingressados no Azure AD  
    CSP do BitLocker: [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Essa configuração inicia uma rotação de senha de recuperação controlada pelo cliente após uma recuperação de unidade do sistema operacional (seja usando bootmgr ou WinRE).  

    - Não configurado  
    - Rotação de chaves desabilitada  
    - Rotação de chaves habilitada para deices unida do Azure AD  
    - Rotação de chaves habilitada para o Azure AD e dispositivos ingressados no híbrido  

  - **Armazenar informações de recuperação em Azure Active Directory antes de habilitar o BitLocker**  
    **Padrão**: Não configurado  
 
    Impedir que os usuários habilitem o BitLocker, a menos que o computador faça o backup com êxito das informações de recuperação do BitLocker para Azure Active Directory.  

    - **Exigir** -impedir que os usuários ativem o BitLocker, a menos que as informações de recuperação do BitLocker sejam armazenadas com êxito no Azure AD.  
    - **Não configurado** -os usuários podem ativar o BitLocker, mesmo que as informações de recuperação não sejam armazenadas com êxito no Azure AD.  

### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados removíveis do BitLocker  

Essas configurações se aplicam especificamente a unidades de dados removíveis.  

- **Acesso de gravação a uma unidade de dados removível não protegida pelo BitLocker**  
  **Padrão**: Não configurado  
  CSP do BitLocker: [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Bloquear** – conceda acesso somente leitura a unidades de dados que não são protegidas pelo BitLocker.  
  - **Não configurado** -por padrão, acesso de leitura e gravação a unidades de dados que não são criptografadas.  

  Quando definido como *habilitar*, você pode definir a seguinte configuração:  

  - **Acesso de gravação a dispositivos configurados em outra organização**  
    **Padrão**: Não configurado  

    - **Bloquear o** acesso de gravação para dispositivos configurados em outra organização.  
    - **Não configurado** -negar acesso de gravação.  
 
## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard  

Utilize o [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) para gerir e reduzir a superfície de ataque de aplicações utilizadas pelos seus funcionários.  

### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque  

Para obter informações sobre as regras de *redução da superfície de ataque* , consulte reduzir as superfícies de [ataque com o Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) na documentação do Windows Defender Exploit Guard.  

#### <a name="attack-surface-reduction-rules"></a>Regras de redução da superfície de ataque  

- **Marcar o roubo de credenciais do sistema de autoridade de segurança local do Windows**  
  **Padrão**: Não configurado  
  Exploit Guard: [Regras de redução da superfície de ataque](https://go.microsoft.com/fwlink/?linkid=874499)

  Ajude a evitar ações e aplicativos que normalmente são usados por malware de busca de exploração para infectar computadores.  
  - **Não configurado**  
  - **Habilitar** -sinalizar roubo de credencial do subsistema de autoridade de segurança local do Windows (Lsass. exe).  
  - **Somente auditoria**  

- **Criação de processo do Adobe Reader (beta)**  
  **Padrão**: Não configurado  
  Exploit Guard: [Regras de redução da superfície de ataque](https://go.microsoft.com/fwlink/?linkid=853979)  

  - **Não configurado**  
  - **Habilitar** -bloquear processos filho que são criados a partir do Adobe Reader.  
  - **Somente auditoria**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Regras para impedir ameaças macro do Office  

Impeça as aplicações do Office de realizarem as seguintes ações:  

- **Aplicações do Office a injetar noutros processos (sem exceções)**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872974)  

  - **Não configurado**  
  - **Bloqueie a injeção** de aplicativos do Office em outros processos.  
  - **Somente auditoria**  

- **Aplicações/macros do Office a criar conteúdo executável**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872975)  

  - **Não configurado**  
  - **Bloqueie o** bloqueio de aplicativos e macros do Office de criar conteúdo executável.  
  - **Somente auditoria**  

- **Aplicações do Office a iniciar processos subordinados**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872976)  

  - **Não configurado**  
  - **Bloquear o** bloqueio de aplicativos do Office para iniciar processos filho.  
  - **Somente auditoria**  
  
- **Importações do Win32 provenientes de código macro do Office**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872977)  

  - **Não configurado**  
  - **Bloco** -bloquear importações do Win32 do código de macro no Office.  
  - **Somente auditoria**  
  
- **Criação de processos de produtos de comunicação do Office**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=874499)  

  - **Não configurado**  
  - **Habilitar** -Bloquear criação de processo filho de aplicativos de comunicações do Office.  
  - **Somente auditoria**  

#### <a name="rules-to-prevent-script-threats"></a>Regras para impedir ameaças de script  

Bloqueie os itens seguintes para impedir ameaças de script:  

- **Código macro js/vbs/ps/ oculto**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872978)    

  - **Não configurado**  
  - **Bloquear-bloquear** qualquer código js/vbs/PS/macro ofuscado.  
  - **Somente auditoria**  

- **js/vbs a executar payload transferido da Internet (sem exceções)**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872979)  

  - **Não configurado**  
  - **Bloquear** -bloquear js/vbs da carga de execução baixada da Internet.  
  - **Somente auditoria**  

- **Processo de criação de comandos PSExec e WMI**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=874500)  

  - **Não configurado**  
  - Criações de processo de bloqueio de **bloco** provenientes de comandos do PsExec e do WMI.  
  
  - **Somente auditoria**  

- **Processos não fidedignos e não assinados que executam a partir de USB**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=874502)    

  - **Não configurado**  
  - Bloquear **bloqueia** processos não confiáveis e não assinados que são executados do USB.  
  - **Somente auditoria**  
  
- **Ficheiros executáveis que não correspondam a uma prevalência, idade ou lista de critérios de confiança**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=874503)    

  - **Não configurado**  
  - **Bloqueie a** execução de arquivos executáveis, a menos que eles atendam a um critério de prevalência, idade ou lista confiável.  
  - **Somente auditoria**  

#### <a name="rules-to-prevent-email-threats"></a>Regras para impedir ameaças de e-mail  

Bloqueie o seguinte para impedir ameaças de e-mail:  

- **Execução de conteúdo executável (exe, dll, ps, js, vbs, etc.) retirado do e-mail (webmail/cliente de correio) (sem exceções)**  
  **Padrão**: Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=872980)  

  - **Não configurado**  
  - **Bloquear a execução** de conteúdo executável (exe, dll, PS, js, vbs, etc.) removido do email (webmail/email).  
  - **Somente auditoria**  

#### <a name="rules-to-protect-against-ransomware"></a>Regras para proteger contra ransomware  

- **Proteção de ransomware avançada**  
  Predefinição:  Não configurado  
  [Documentação do Exploit Guard](https://go.microsoft.com/fwlink/?linkid=874504)  

  - **Não configurado**  
  - **Habilitar** -usar proteção agressiva de ransomware.  
  - **Somente auditoria**  

#### <a name="attack-surface-reduction-exceptions"></a>Exceções da Redução da Superfície de Ataque

- **Arquivos e pasta a serem excluídos das regras de redução da superfície de ataque**  
  CSP do defender: [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importe** um arquivo. csv que contenha arquivos e pastas para excluir das regras de redução da superfície de ataque.  
  - **Adicione** arquivos ou pastas locais manualmente.  

> [!IMPORTANT]  
> Para permitir a instalação e execução correta de aplicativos LOB Win32, as configurações de anti-malware devem excluir os seguintes diretórios de serem verificados:  
> **Em computadores cliente x64**:  
> *C:\Arquivos de programas (x86) \Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **Em computadores cliente x86**:  
> *C:\Arquivos de Programas\microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Acesso a pastas controladas  

Ajude a [proteger dados valiosos](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) de aplicativos mal-intencionados e ameaças, como ransomware.  

- **Proteção de pasta**  
  **Padrão**: Não configurado  
  CSP do defender: [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.  

  - **Não configurado**  
  - **Desabilitar**  
  - **Somente auditoria**  
  - **Bloquear modificação de disco**  
  - **Modificação de disco de auditoria**  

  Quando você seleciona uma configuração diferente de *não configurado*, você pode configurar:  
  - **Lista de aplicativos que têm acesso a pastas protegidas**  
    CSP do defender: [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importe** um arquivo. csv que contenha uma lista de aplicativos.  
    - **Adicione** aplicativos a essa lista manualmente.  

  - **Lista de pastas adicionais que precisam ser protegidas**  
    CSP do defender: [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importe** um arquivo. csv que contenha uma lista de pastas.  
    - **Adicione** pastas a essa lista manualmente.  

### <a name="network-filtering"></a>Filtragem de rede  

Bloquear conexões de saída de qualquer aplicativo para endereços IP ou domínios com baixa reputação. Há suporte para a filtragem de rede no modo de auditoria e de bloqueio.  

- **Proteção de rede**  
  **Padrão**: Não configurado  
  CSP do defender: [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  A intenção dessa configuração é proteger os usuários finais de aplicativos com acesso a golpes de phishing, sites de Hospedagem de exploração e conteúdo mal-intencionado na Internet. Ele também impede que navegadores de terceiros se conectem a sites perigosos.  

  - **Não configurado** -desabilite esse recurso. Os usuários e aplicativos não estão impedidos de se conectar a domínios perigosos. Os administradores não podem ver essa atividade na central de segurança do Windows Defender.  
  - **Habilitar** -ativar a proteção de rede e impedir que usuários e aplicativos se conectem a domínios perigosos. Os administradores podem ver essa atividade na central de segurança do Windows Defender.  
  - **Somente auditoria**:-os usuários e aplicativos não são impedidos de se conectar a domínios perigosos. Os administradores podem ver essa atividade na central de segurança do Windows Defender.  

### <a name="exploit-protection"></a>Exploit Protection  
 

- **Carregar XML**  
  **Padrão**: *Não configurado*  

  Para usar a proteção contra Exploit para [proteger dispositivos contra explorações](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), crie um arquivo XML que inclui as configurações de mitigação do sistema e do aplicativo que você deseja. Há dois métodos para criar o arquivo XML:  

  - *PowerShell* -use um ou mais dos cmdlets do PowerShell *Get-ProcessMitigation*, *set-ProcessMitigation*e *ConvertTo-ProcessMitigationPolicy* . Os cmdlets configuram definições de mitigação e exportam uma representação XML deles.  

  - *Interface do usuário da central de segurança do Windows Defender* -na central de segurança do Windows Defender, clique em aplicativo & controle de navegador e role até a parte inferior da tela resultante para encontrar proteção de exploração. Em primeiro lugar, utilize as definições do sistema e os separadores das definições de programa para configurar definições de atenuação. Em seguida, localize a ligação de definições de Exportação na parte inferior do ecrã para exportar uma representação XML dos mesmos.  

- **Edição de usuário da interface de proteção de exploração**  
  **Padrão**: Não configurado  
  CSP ExploitGuard: [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Bloquear** – carregar um arquivo XML que permite configurar a memória, o fluxo de controle e as restrições de política. As definições no ficheiro XML podem servir para proteger uma aplicação de exploits.  
  - **Não configurado** -nenhuma configuração personalizada é usada.  

## <a name="windows-defender-application-control"></a>Controlo de Aplicações do Windows Defender  

Escolha aplicativos adicionais que precisam ser auditados pelo ou que podem ser confiáveis para execução pelo controle de aplicativos do Windows Defender. Os componentes do Windows e todas as aplicações da Microsoft Store são automaticamente considerados de confiança para serem executados.  


- **Políticas de integridade de código de controle de aplicativo**  
  **Padrão**: Não configurado  
   CSP: [CSP do AppLocker](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Impor** -escolha as políticas de integridade de código de controle de aplicativo para os dispositivos dos usuários.  
  
    Depois de habilitado em um dispositivo, o controle de aplicativo só pode ser desabilitado alterando o modo de *impor* para *somente auditoria*. Se alterar do modo de *Impor* para *Não Configurado* o Controlo de Aplicações continuará a ser imposto nos dispositivos atribuídos.  

  - **Não configurado** -o controle de aplicativo não é adicionado aos dispositivos. No entanto, as configurações que foram adicionadas anteriormente continuam a ser impostas em dispositivos atribuídos. 
 
  - **Somente auditoria** -os aplicativos não são bloqueados. Todos os eventos são registrados nos logs do cliente local.  

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard  

O Windows Defender Credential Guard protege contra ataques de roubo de credenciais. Isola os segredos para permitir o acesso apenas a software de sistema com privilégios.  

- **Proteção de credenciais**  
  **Padrão**: Desativar  
  [CSP DeviceGuard](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Desabilitar** – desativar a proteção de credenciais remotamente, se ela tiver sido ativada anteriormente com a opção **habilitado sem bloqueio de UEFI** .  

  - **Habilitar com bloqueio UEFI** -o Credential Guard não pode ser desabilitado remotamente usando uma chave do registro ou uma política de grupo.  

    > [!NOTE]
    > Se utilizar esta definição e, em seguida, quiser desativar o Credential Guard, terá de definir a Política de Grupo como **Desativado**. Além disso, tem de limpar fisicamente as informações de configuração de UEFI de cada computador. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.  

  - **Habilitar sem bloqueio de UEFI** – permite que o Credential Guard seja desabilitado remotamente usando política de grupo. Os dispositivos que utilizam esta definição têm de ter a versão 1511 ou mais recente do Windows 10.  

  Quando você *habilita* o Credential Guard, os seguintes recursos necessários também são habilitados:  
  
  - **Segurança baseada em virtualização** VBS  
    Ativa durante a próxima reinicialização. A segurança baseada em Virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Windows Hypervisor.  
  - **Inicialização segura com acesso à memória do diretório**  
    Ativa o VBS com a inicialização segura e proteções de DMA (acesso direto à memória). As proteções de DMA necessitam de suporte de hardware e são ativadas apenas em dispositivos configurados corretamente.  

## <a name="windows-defender-security-center"></a>Centro de Segurança do Windows Defender  

O Centro de Segurança do Windows Defender funciona como uma aplicação ou processo separado de cada uma das funcionalidades individuais. Apresenta notificações através do Centro de Ação. Ele atua como um coletor ou um único local para ver o status e executar algumas configurações para cada um dos recursos. Saiba mais na documentação do [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).  

### <a name="windows-defender-security-center-app-and-notifications"></a>Aplicações e notificações do Centro de Segurança do Windows Defender  

Bloqueie o acesso de utilizadores finais a várias áreas da aplicação Centro de Segurança do Windows Defender. Ocultar uma secção também bloqueia notificações relacionadas.  

- **Proteção contra vírus e ameaças**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  Configure se os usuários finais podem exibir a área de proteção contra vírus e ameaças na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas à proteção contra vírus e ameaças.  

  - **Não configurado**  
  - **Exibe**  

- **Proteção contra ransomware**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Configurar se os usuários finais puderem exibir a área de proteção contra ransomware na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas à proteção contra ransomware.  

  - **Não configurado**  
  - **Exibe**  

- **Proteção da conta**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  Configurar se os usuários finais puderem exibir a área proteção da conta na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas à proteção da conta.  

  - **Não configurado**  
  - **Exibe**  

- **Firewall e proteção da rede**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  Configurar se os usuários finais puderem exibir a área de proteção de firewall e rede na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas ao firewall e à proteção de rede.  

  - **Não configurado**  
  - **Exibe**  

- **Controle de aplicativo e navegador**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  Configurar se os usuários finais puderem exibir a área de controle do aplicativo e do navegador na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas ao aplicativo e ao controle de navegador.  

  - **Não configurado**  
  - **Exibe**  

- **Proteção de hardware**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  Configurar se os usuários finais puderem exibir a área de proteção de hardware na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas à proteção de hardware.  

  - **Não configurado**  
  - **Exibe**  

- **Desempenho e estado de funcionamento do dispositivo**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  Configurar se os usuários finais puderem exibir a área de desempenho e integridade do dispositivo na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas ao desempenho e à integridade do dispositivo.  
  
  - **Não configurado**  
  - **Exibe**  

- **Opções de família**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  Configurar se os usuários finais puderem exibir a área de opções da família na central de segurança do Windows Defender. Ocultar esta seção também bloqueará todas as notificações relacionadas às opções da família.  
  
  - **Não configurado**  
  - **Exibe**  

- **Notificações das áreas de aplicativo exibidas**  
  **Padrão**: Não configurado  
  CSP WindowsDefenderSecurityCenter: [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  Escolha quais notificações exibir para os usuários finais. As notificações não críticas incluem resumos de atividade do Antivírus do Windows Defender, incluindo notificações quando as análises forem concluídas. Todas as outras notificações são consideradas críticas.  

  - **Não configurado**  
  - **Bloquear notificações não críticas**  
  - **Bloquear todas as notificações**  

- **Ícone da central de segurança do Windows na bandeja do sistema**  
  **Padrão**: Não configurado  

  Configure a exibição do controle da área de notificação. O usuário precisa sair e entrar ou reiniciar o computador para que essa configuração entre em vigor.  
  
  - **Não configurado**  
  - **Exibe**  

- **Botão limpar TPM**  
  **Padrão**: Não configurado  

  Configure a exibição do botão limpar TPM.  
  
  - **Não configurado**  
  - **Desativar**  

- **Aviso de atualização de firmware do TPM**  
  **Padrão**: Não configurado  
  
  Configure a exibição do firmware do TPM de atualização quando um firmware vulnerável for detectado.  

  - **Não configurado**  
  - **Exibe**  

- **Proteção contra violações**  
  **Padrão**: Não configurado

  Ativar ou desativar a proteção contra violação em dispositivos. Para usar a proteção contra violações, você deve [integrar a proteção avançada contra ameaças do Microsoft defender com o Intune](advanced-threat-protection.md)e ter [Enterprise Mobility + Security licenças E5](licenses.md).  
  - **Não configurado** -nenhuma alteração é feita nas configurações do dispositivo.
  - **Habilitado** -a proteção contra violação está ativada e as restrições são impostas nos dispositivos.
  - **Desabilitado** -a proteção contra violações está desativada e as restrições não são impostas.

### <a name="it-contact-information"></a>Informação de contacto de TI  

Forneça as informações de contacto de TI para que sejam apresentadas na aplicação Centro de Segurança do Windows Defender e nas notificações da aplicação.  

Pode optar por **Mostrar na aplicação e nas notificações**, **Mostrar apenas na aplicação**, **Mostrar apenas nas notificações** ou **Não mostrar**. Introduza o **Nome da organização de TI** e pelo menos uma das seguintes opções de contacto:  


- **Informações de contato de ti**  
  **Padrão**: Não exibir  
  CSP WindowsDefenderSecurityCenter: [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Configure onde exibir informações de contato para os usuários finais.  
  
  - **Exibir no aplicativo e em notificações**  
  - **Exibir somente no aplicativo**  
  - **Exibir somente em notificações**  
  - **Não exibir**  

  Quando configurado para exibir, você pode definir as seguintes configurações:  

  - **Nome da organização de ti**  
    **Padrão**: *Não configurado*  
    CSP WindowsDefenderSecurityCenter: [CompanyName](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **Número de telefone ou ID do Skype do departamento de TI**  
    **Padrão**: *Não configurado*  
    CSP WindowsDefenderSecurityCenter: [Telemóvel](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **Endereço de e-mail do departamento de TI**  
    **Padrão**: *Não configurado*  
    CSP WindowsDefenderSecurityCenter: [e-mail](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **URL do site de suporte de TI**  
    **Padrão**: *Não configurado*  
    CSP WindowsDefenderSecurityCenter: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Opções de segurança do dispositivo local  

Utilize estas opções para configurar as definições da segurança local em dispositivos Windows 10.  

### <a name="accounts"></a>Contas  

- **Adicionar novas contas da Microsoft**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Bloquear** Impedir que os usuários adicionem novas contas da Microsoft ao dispositivo.  
  - **Não configurado** -os usuários podem usar contas da Microsoft no dispositivo.  

- **Logon remoto sem senha**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Bloquear** – permitir que apenas contas locais com senhas em branco entrem usando o teclado do dispositivo.  
   - **Não configurado** – permitir que contas locais com senhas em branco entrem em locais diferentes do dispositivo físico.  

#### <a name="admin"></a>administrador  

- **Conta de administrador local**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Bloquear** Impedir o uso de uma conta de administrador local.  
  - **Não configurado**  

- **Renomear conta do administrador**  
  **Padrão**: *Não configurado*  
  CSP LocalPoliciesSecurityOptions: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Defina um nome de conta diferente a ser associado ao SID (identificador de segurança) da conta "administrador".  

 #### <a name="guest"></a>Convidado  

- **Conta de convidado**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Bloquear** – impedir o uso de uma conta de convidado.  
  - **Não configurado**  

- **Renomear conta de convidado**  
  **Padrão**: *Não configurado*  
  CSP LocalPoliciesSecurityOptions: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Defina um nome de conta diferente a ser associado ao SID (identificador de segurança) da conta "convidado".  

### <a name="devices"></a>Dispositivos  

- **Desencaixar dispositivo sem logon**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Bloquear** – os usuários podem pressionar o botão de ejeção física de um dispositivo portátil encaixado para desencaixar com segurança o dispositivo.  
  - **Não configurado** -um usuário deve entrar no dispositivo e receber permissão para desencaixar o dispositivo.  

- **Instalar drivers de impressora para impressoras compartilhadas**  
  **Padrão**:  Não configurado  
  CSP LocalPoliciesSecurityOptions: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Habilitado** – qualquer usuário pode instalar um driver de impressora como parte da conexão a uma impressora compartilhada.  
  - **Não configurado** -somente administradores podem instalar um driver de impressora como parte da conexão a uma impressora compartilhada.  

- **Restringir o acesso ao CD-ROM ao usuário ativo local**  
  **Padrão**:  Não configurado  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Habilitado** – somente o usuário conectado interativamente pode usar a mídia de CD-ROM. Se esta política estiver ativada e ninguém tiver sessão iniciada de forma interativa, a unidade de CD-ROM será acedida através da rede.  
  - **Não configurado** -qualquer pessoa tem acesso ao CD-ROM.  

- **Formatar e ejetar mídia removível**  
  **Padrão**: Administradores  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  Defina quem tem permissão para formatar e ejetar mídia NTFS removível:  
  - **Não configurado**  
  - **Administradores**  
  - **Administradores e Utilizadores Avançados**  
  - **Administradores e Utilizadores Interativos**  

### <a name="interactive-logon"></a>Início de sessão interativo  

- **Minutos de inatividade de tela de bloqueio até que a proteção de tela seja ativada**  
  **Padrão**: *Não configurado*  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  Insira o máximo de minutos de inatividade na tela de entrada da área de trabalho interativa até que a proteção de tela seja iniciada. (**0** - **99999**)  

- **Exigir CTRL + ALT + DEL para fazer logon**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Habilitar** -pressionar Ctrl + Alt + Del não é necessário para que os usuários entrem.  
  - **Não configurado** Exigir que os usuários pressionem CTRL + ALT + DEL antes de fazer logon no Windows.  

- **Comportamento de remoção de cartão inteligente**  
  **Padrão**: Bloquear estação de trabalho   
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  Determina o que acontece quando o cartão inteligente de um usuário conectado é removido do leitor de cartão inteligente. As opções são:  

  - **Bloquear estação de trabalho** -a estação de trabalho é bloqueada quando o cartão inteligente é removido. Esta opção permite que os utilizadores saiam da área, levem os seus smart cards e permaneçam numa sessão protegida.  
  - **Nenhuma ação**  
  - **Forçar logoff** – o usuário é desconectado automaticamente quando o cartão inteligente é removido.  
  - **Desconectar se uma sessão serviços de área de trabalho remota** -a remoção do cartão inteligente desconecta a sessão sem fazer logoff do usuário. Esta opção permite que o utilizador insira o smart card e retome a sessão mais tarde, ou noutro computador com um leitor de smart cards, sem ter de iniciar sessão novamente. Se a sessão for local, esta política funciona da mesma forma que Bloquear Estação de Trabalho.  

#### <a name="display"></a>Apresentar  

- **Informações do usuário na tela de bloqueio**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  Configure as informações do usuário que são exibidas quando a sessão está bloqueada. Se não estiverem configuradas, serão apresentados o nome a apresentar do utilizador, o domínio e o nome de utilizador.  

  - **Não configurado**  
  - **O nome a apresentar do utilizador, o domínio e o nome de utilizador**  
  - **Apenas o nome a apresentar do utilizador**  
  - **Não apresentar informações do utilizador**  

- **Ocultar último usuário conectado**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Enable** -oculta o nome de usuário.  
  - **Não configurado** -mostra o último nome de usuário.  

- **Ocultar nome de usuário no**
  **padrão**de entrada: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Enable** -oculta o nome de usuário.  
  - **Não configurado** -mostra o último nome de usuário.  

- **Título da mensagem de logon**  
  **Padrão**: *Não configurado*  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  Defina o título da mensagem para usuários entrando.  

- **Texto da mensagem de logon**  
  **Padrão**: *Não configurado*  
  CSP LocalPoliciesSecurityOptions: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  Defina o texto da mensagem para usuários que se conectam.  
  
### <a name="network-access-and-security"></a>Acesso à rede e segurança

- **Acesso anônimo a pipes nomeados e compartilhamentos**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Não configurado** – restrinja o acesso anônimo ao compartilhamento e às configurações de pipe nomeado. Aplica-se as definições que podem ser acedidas anonimamente.  
  - **Bloquear** -desabilitar esta política, disponibilizando o acesso anônimo.  

- **Enumeração anônima de contas SAM**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **Não configurado** -os usuários anônimos podem enumerar contas Sam.  
  - **Bloquear** – impedir a enumeração anônima de contas Sam.  

- **Enumeração anônima de contas e compartilhamentos SAM**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Não configurado** -os usuários anônimos podem enumerar os nomes de contas de domínio e compartilhamentos de rede.  
  - **Bloquear** – impedir a enumeração anônima de contas e compartilhamentos Sam. 

- **Valor de hash do LAN Manager armazenado na alteração de senha**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Determine se o valor de hash para senhas é armazenado na próxima vez em que a senha for alterada. 
  - **Não configurado** -o valor de hash não está armazenado  
  - **Bloquear** – o LM (Gerenciador de LAN) armazena o valor de hash para a nova senha.  

- **Solicitações de autenticação PKU2U**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **Não configurado**-permitir solicitações PU2U.  
  - **Bloqueie as** solicitações de autenticação PKU2U para o dispositivo.  

- **Restringir conexões RPC remotas ao SAM**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **Não configurado** -use o descritor de segurança padrão, que pode permitir que usuários e grupos façam chamadas RPC remotas para o Sam.
  - **Permitir** -negar que usuários e grupos façam chamadas RPC remotas para o Sam (Gerenciador de contas de segurança), que armazena contas de usuário e senhas. **Permitir** também permite que você altere a cadeia de caracteres SDDL (linguagem de definição de descritor de segurança) padrão para permitir ou negar explicitamente usuários e grupos para fazer essas chamadas remotas.  

    - **Descritor de segurança**  
      **Padrão**: *Não configurado*  
    
- **Segurança mínima de sessão para clientes baseados em NTLM SSP**  
  **Padrão**: Nenhum  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Essa configuração de segurança permite que um servidor exija a negociação de criptografia de 128 bits e/ou segurança de sessão NTLMv2.  

  - **Nenhum**  
  - **Exigir segurança de sessão NTLMv2**  
  - **Exigir criptografia de 128 bits**  
  - **Criptografia NTLMv2 e 128 bits**  
 
- **Segurança mínima de sessão para o servidor baseado em NTLM SSP**  
  **Padrão**: Nenhum  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Essa configuração de segurança determina qual protocolo de autenticação de desafio/resposta é usado para logons de rede.  

  - **Nenhum**  
  - **Exigir segurança de sessão NTLMv2**  
  - **Exigir criptografia de 128 bits**  
  - **Criptografia NTLMv2 e 128 bits**  

- **Nível de autenticação do LAN Manager**  
  **Padrão**: LM e NTLM  
  CSP LocalPoliciesSecurityOptions: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM e NTLM**  
  - **LM, NTLM e NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 e não LM**  
  - **NTLMv2 e não LM ou NTLM**  
  
- **Logons de convidado não seguros**  
  **Padrão**: Não configurado  
  CSP LanmanWorkstation: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Se você habilitar essa configuração, o cliente SMB rejeitará logons de convidado inseguros.  

  - **Não configurado**  
  - **Bloquear** – o cliente SMB rejeita logons de convidado inseguros.  

### <a name="recovery-console-and-shutdown"></a>Consola de recuperação e encerramento  

- **Limpar arquivo de paginação de memória virtual ao desligar**  
  **Padrão**: Não configurado  
   CSP LocalPoliciesSecurityOptions: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Habilitar** -limpar o arquivo de paginação de memória virtual quando o dispositivo estiver desligado.  
  - **Não configurado** – não limpa a memória virtual.  

- **Desligar sem fazer logon**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Bloquear** -oculta a opção de desligamento na tela de entrada do Windows. Os utilizadores têm de iniciar sessão no dispositivo e, em seguida, encerrar.  
  - **Não configurado** – permitir que os usuários desliguem o dispositivo da tela de entrada do Windows.  

### <a name="user-account-control"></a>Controlo de conta de utilizador  

- **Integridade de UIA sem local seguro**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - Os aplicativos de **bloco** que estão em um local seguro no sistema de arquivos serão executados somente com a integridade do UIAccess.  
  - **Não configurado** – permite que os aplicativos sejam executados com integridade de UIAccess, mesmo que os aplicativos não estejam em um local seguro no sistema de arquivos.  

- **Virtualizar falhas de gravação de arquivo e registro para locais por usuário**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Habilitado** -os aplicativos que gravam dados em locais protegidos falham.  
  - **Não configurado** -as falhas de gravação do aplicativo são redirecionadas em tempo de execução para locais de usuário definidos para o sistema de arquivos e o registro.  

- **Elevar somente arquivos executáveis assinados e validados**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Habilitado** – impor a validação do caminho de certificação PKI para um arquivo executável antes que ele possa ser executado.  
  - **Não configurado** – não impor a validação de caminho de certificação PKI antes que um arquivo executável possa ser executado.  

#### <a name="uia-elevation-prompt-behavior"></a>Comportamento do prompt de elevação de UIA  

- **Solicitação de elevação para administradores**  
  **Padrão**: Solicitar consentimento para binários não Windows  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Defina o comportamento da solicitação de elevação para administradores no modo de aprovação de administrador.  

  - **Não configurado**  
  - **Elevar sem perguntar**  
  - **Pedir credenciais no ambiente de trabalho seguro**  
  - **Pedir credenciais**  
  - **Pedir consentimento**  
  - **Solicitar consentimento para binários não Windows**  


- **Solicitação de elevação para usuários padrão**  
  **Padrão**: Solicitar credenciais  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  Defina o comportamento da solicitação de elevação para usuários padrão.  

  - **Não configurado**  
  - **Negar automaticamente pedidos de elevação**  
  - **Pedir credenciais no ambiente de trabalho seguro**  
  - **Pedir credenciais**  

- **Direcionar solicitações de elevação para área de trabalho interativa do usuário**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Habilitado** -todas as solicitações de elevação para ir para a área de trabalho do usuário interativo em vez da área de trabalho segura. São utilizadas todas as definições de política de comportamento de pedidos para administradores e utilizadores padrão.  
  - **Não configurado** – forçar todas as solicitações de elevação ir para a área de trabalho segura, independentemente de qualquer configuração de política de comportamento de prompt para administradores e usuários padrão.

- **Prompt com privilégios elevados para instalações de aplicativos**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Habilitado** -os pacotes de instalação de aplicativo não são detectados ou são solicitados a fornecer elevação.
   - **Não configurado** -os usuários são solicitados a fornecer um nome de usuário administrativo e uma senha quando um pacote de instalação de aplicativo requer privilégios elevados.

- **Solicitação de elevação de UIA sem área de trabalho segura**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Habilitar** – permitir que aplicativos UIAccess solicitem elevação, sem usar a área de trabalho segura.  
- **Não configurado** -as solicitações de elevação usam uma área de trabalho segura.  

#### <a name="admin-approval-mode"></a>Modo de aprovação de administrador  

- **Modo de aprovação de administrador para administrador interno**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Habilitado** – permitir que a conta de administrador interna use o modo de aprovação de administrador. Qualquer operação que necessite de elevação de privilégios pede ao utilizador para aprovar a operação.  
  - **Não configurado** – executa todos os aplicativos com privilégios de administrador completo.  

- **Executar todos os administradores no modo de aprovação de administrador**  
  **Padrão**: Não Configurado  
  CSP LocalPoliciesSecurityOptions: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Habilitado**– habilitar o modo de aprovação de administrador.  
  - **Não configurado** -desabilitar o modo de aprovação de administrador e todas as configurações de política de UAC relacionadas.  

### <a name="microsoft-network-client"></a>Cliente de Rede da Microsoft  

- **Assinar digitalmente as comunicações (se o servidor concordar)**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  Determina se o cliente SMB negocia a assinatura de pacote SMB.  
  - **Bloquear** – o cliente SMB nunca negocia a assinatura de pacote SMB.
  - **Não configurado** -o cliente de rede da Microsoft solicita que o servidor execute a assinatura de pacote SMB na configuração da sessão. Se a assinatura de pacotes estiver ativada no servidor, a assinatura de pacotes será negociada.  

- **Enviar senha não criptografada para servidores SMB de terceiros**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Bloquear** – o redirecionador de protocolo SMB pode enviar senhas de texto não criptografado a servidores SMB não Microsoft que não dão suporte à criptografia de senha durante a autenticação.  
  - **Não configurado** -bloqueia o envio de senhas de texto sem formatação. As senhas são criptografadas.  

- **Assinar digitalmente as comunicações (sempre)**  
  **Padrão**: Não configurado  
  CSP LocalPoliciesSecurityOptions: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Habilitar** -o cliente de rede da Microsoft não se comunica com um servidor de rede da Microsoft, a menos que o servidor concorde com a assinatura de pacote SMB.  
  - **Não configurado** -a assinatura de pacote SMB é negociada entre o cliente e o servidor.  

### <a name="microsoft-network-server"></a>Servidor de Rede da Microsoft  
  
- **Assinar digitalmente as comunicações (se o cliente concordar)**  
  **Padrão**: Não configurado  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Habilitar** -o servidor de rede da Microsoft negocia a assinatura de pacote SMB conforme solicitado pelo cliente. Ou seja, se a assinatura de pacotes estiver ativada no cliente, a assinatura de pacotes será negociada.  
  - **Não configurado** -o cliente SMB nunca negocia a assinatura de pacote SMB.  

- **Assinar digitalmente as comunicações (sempre)**  
  **Padrão**: Não configurado  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Habilitar** -o servidor de rede da Microsoft não se comunica com um cliente de rede da Microsoft, a menos que o cliente concorde com a assinatura de pacote SMB.  
  - **Não configurado** -a assinatura de pacote SMB é negociada entre o cliente e o servidor.  

## <a name="xbox-services"></a>Serviços do Xbox

- **Tarefa de salvamento de jogo do Xbox**  
  **Padrão**: Não configurado  
  CSP: [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Essa configuração determina se a tarefa de salvamento do jogo Xbox está habilitada ou desabilitada.  
  - **Habilitado**
  - **Não configurado**

- **Serviço de gerenciamento de acessórios do Xbox**  
  **Padrão**: Manual  
  CSP: [Sistemaservices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  Essa configuração determina o tipo de início do serviço de gerenciamento de acessórios.  
  - **Manual**
  - **Automático**
  - **Desativado**

- **Serviço do Gerenciador de autenticação Xbox Live**  
  **Padrão**: Manual  
  CSP: [Sistemaservices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Essa configuração determina o tipo de início do serviço do Gerenciador de autenticação dinâmica.  
  - **Manual**
  - **Automático**
  - **Desativado**
 
- **Serviço de salvamento do jogo Xbox Live**  
  **Padrão**: Manual  
  CSP: [Sistemaservices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Essa configuração determina o tipo de início do serviço de salvamento de jogo ao vivo.  
  - **Manual**
  - **Automático**
  - **Desativado**

- **Serviço de rede Xbox Live**  
  **Padrão**: Manual  
  CSP: [Sistemaservices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Essa configuração determina o tipo de início do serviço de rede.  
  - **Manual**
  - **Automático**
  - **Desativado**

## <a name="next-steps"></a>Passos seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md)e [monitore seu status](device-profile-monitor.md).  

Configure as definições de proteção de ponto de extremidade em dispositivos [MacOS](endpoint-protection-macos.md) .  
