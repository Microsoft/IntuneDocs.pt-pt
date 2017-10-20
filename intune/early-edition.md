---
title: "Edição antecipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: abb5612545174e3fd134c38fb763e02d379b50d0
ms.sourcegitcommit: b330045a4f9a807e6e2772c4ed4e1e1148e1f1f9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/13/2017
---
# <a name="the-early-edition-for-microsoft-intune---october-2017"></a>A edição antecipada do Microsoft Intune – outubro de 2017

A **edição antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não partilhe estas informações fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
>As seguintes alterações estão em desenvolvimento para o Intune. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->



## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública) <!-- 710595 -->   
Com o Azure Active Directory (Azure AD), poderá restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure.

### <a name="troubleshoot-enrollment-issues------746324----"></a>Resolução de problemas de inscrição <!--- 746324 --->  
A área de trabalho Resolução de Problemas irá apresentar problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Agora, os administradores podem configurar as definições de Firewall num dispositivo através de um perfil de configuração de dispositivo <!-- 951708 -->   
Os administradores podem ativar a firewall para os dispositivos, bem como configurar vários protocolos para redes de domínio privadas e públicas.  Poderá encontrar estas definições de firewall no perfil "Proteção de ponto final".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>O Windows Defender Application Guard ajuda a proteger os dispositivos de sites não fidedignos, consoante as definições da sua organização <!-- 958257 -->   
Os administradores podem definir sites como "fidedigno" ou "empresarial" através de um fluxo do Windows Information Protection ou do novo perfil "Limite de rede" nas configurações dos dispositivos. Se forem visualizados com o Microsoft Edge, todos os sites que não estiverem indicados no limite de rede fidedigno de um dispositivo com o Windows 10 de 64 bits serão abertos num browser com um computador virtual Hyper-V.

Poderá encontrar o Application Guard nos perfis de configuração de dispositivos, no perfil "Proteção de ponto final". A partir daí, os administradores podem configurar a interação entre o browser virtualizado e o computador anfitrião, sites fidedignos e não fidedignos e os dados de armazenamento gerados no browser virtualizado. Para utilizar o Application Guard num dispositivo, é necessário configurar primeiro um limite de rede. É importante definir apenas um limite de rede para um dispositivo.  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>O Windows Defender Application Guard no Windows 10 Enterprise fornece um modo para confiar apenas em aplicações autorizadas <!-- 1031096 -->    
Com milhares de novos ficheiros maliciosos a serem criados todos os dias, a deteção com base em assinatura de antivírus para combater software maligno poderá deixar de ser uma defesa adequada contra novos ataques. Com o Windows Defender Application Guard no Windows 10 Enterprise, pode alterar a configuração do dispositivo de um modo em que as aplicações são fidedignas, a menos que sejam bloqueadas por um antivírus ou por outra solução de segurança, para um modo em que o sistema operativo confia apenas nas aplicações autorizadas pela sua empresa. A atribuição de fidedignidade a aplicações é feita no Windows Defender Application Guard.

Com o Intune, pode configurar as políticas de controlo de aplicações no modo "apenas auditoria" ou no modo de imposição. As aplicações não serão bloqueadas ao serem executadas no modo "apenas auditoria". O modo "apenas auditoria" regista todos os eventos nos registos do cliente local. Também pode configurar se pretende que apenas os componentes Windows e as aplicações da Loja Windows tenham permissão para serem executados ou se pretende permitir a execução de aplicações adicionais com boa reputação, conforme definidas pelo Gráfico de Segurança Inteligente.

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Nova página de estado de inscrição para inscrições de dispositivos Windows 10 <!--1063201-->    
Agora pode configurar uma saudação a ser apresentada quando os seus utilizadores inscreverem dispositivos Windows 10. Utilize o **Ecrã do Estado de Inscrição** para configurar uma mensagem personalizada e uma hiperligação a apresentar aos seus utilizadores finais quando estes inscreverem os respetivos dispositivos Windows 10.  O **Ecrã do Estado de Inscrição** também proporciona aos utilizadores finais uma visão geral sobre o progresso das definições de política que estão a ser aplicadas ao seu dispositivo.  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>O Windows Defender Exploit Guard é um novo conjunto de funcionalidades de prevenção de intrusões para o Windows 10 <!-- 1063615 -->   
O Windows Defender Exploit Guard inclui regras personalizadas para reduzir a exploração de aplicações, impede ameaças de macros e scripts, bloqueia automaticamente ligações de rede a endereço IP com baixa reputação e ajuda a proteger os dados de ransomware e ameaças desconhecidas. O Windows Defender Exploit Guard consiste nos seguintes componentes:

- A **Redução da Superfície de Ataque (ASR)** fornece regras que lhe permitem impedir ameaças de macros, scripts e e-mail.
- O **Acesso a Pastas Controladas** bloqueia automaticamente o acesso a conteúdos de pastas protegidas.
- O **Filtro de Rede** bloqueia a ligação de saída de qualquer aplicação para um IP/domínio com baixa reputação
- A **Exploit Protection** fornece restrições de memória, fluxo de controlos e de políticas que podem ser utilizadas para proteger um aplicação de exploits.

### <a name="app-conditional-launch-support----1193313---"></a>Suporte para execução condicional de aplicações <!-- 1193313 -->
Os administradores de TI já podem definir um requisito através do portal de administração do Azure para impor um código de acesso em vez de um PIN numérico através da gestão de aplicações móveis (MAM) quando a aplicações é executada. Caso esteja configurado, será pedido ao utilizador que defina e utilize um código de acesso antes de este poder aceder a aplicações otimizadas para MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. Esta versão do Intune irá ativar esta funcionalidade **apenas no iOS**. O Intune suporta um código de acesso de forma semelhante a um PIN numérico: a aplicação define um comprimento mínimo e permite sequências e carateres repetidos. Esta funcionalidade requer que a participação das aplicações (por exemplo, o WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune com o código desta funcionalidade para que as definições do código de acesso sejam impostas nas aplicações alvo.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número da Versão de Aplicação para aplicações de linha de negócio no relatório de estado de instalação do dispositivo <!-- 1233999 -->  
O relatório de estado de instalação do dispositivo irá apresentar o número da versão de aplicação das aplicações de linha de negócio para iOS e Android. Pode utilizar estas informações para resolver problemas nas suas aplicações ou localizar dispositivos que estão a ser executados com versões desatualizadas da aplicação.

### <a name="co-management-for-windows-10-devices-----124445---"></a>Cogestão para dispositivos Windows 10 <!-- 124445 -->
A cogestão é uma solução que proporciona a transição de uma gestão tradicional para uma moderna, além de permitir que faça essa transição de forma faseada. Na sua génese, a cogestão é uma solução em que os dispositivos Windows 10 são geridos simultaneamente pelo Configuration Manager e pelo Microsoft Intune, além de estar associada ao Active Directory (AD) e ao Azure Active Directory (Azure AD).  Esta configuração proporciona-lhe uma forma de modernizar a gestão com ao longo do tempo e ao ritmo mais adequado para a sua organização, caso não consiga efetuar a mudança de uma só vez.  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Definir o acesso a aplicações através de uma atualização de segurança mínima para Android no dispositivo <!-- 1278463 -->   
Um administrador poderá definir a atualização de segurança mínima para Android que tem de ser instalada no dispositivo, de modo a obter acesso a uma aplicação gerida numa conta gerida.

> [!Note]  
> Esta funcionalidade apenas restringe atualizações de segurança lançadas pela Google em dispositivos Android 6.0+.

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Novas definições de restrição de dispositivos para Windows 10      <!-- 1308850 -->
-    Mensagens (apenas para telemóveis) – desativar mensagens de teste ou MMS
-    Palavra-passe – definições para ativar o sistema FIPS e utilizar dispositivos secundários Windows Hello para efeitos de autenticação 
-    Apresentação – definições para ativar ou desativar o Dimensionamento de GDI para aplicações legadas


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrições de dispositivos Windows 10 no modo de local público <!-- 1308872 -->   
Poderá restringir os utilizadores de dispositivos Windows 10 ao modo de local público (no Windows 10, este modo é denominado como modo de quiosque), que os limita a um conjunto de aplicações predefinidas.  Para fazê-lo, crie um perfil de restrição de dispositivos Windows 10 e configure as definições do modo de local público.

O modo de local público suporta dois modos: **quiosque de uma aplicação** (permite que um utilizador execute apenas uma aplicação) ou **quiosque de várias aplicações** (concede acesso a um conjunto de aplicações).  Defina a conta de utilizador e o nome do dispositivo, o qual determina as aplicações suportadas).  Quando o utilizador tiver sessão iniciada, este será limitado às aplicações definidas.  Para saber mais, veja [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

O modo de local público necessita que:

- O Intune seja a autoridade MDM.
- As aplicações já estejam instaladas no dispositivo alvo.
- O dispositivo esteja [devidamente aprovisionado](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Novo perfil de configuração de dispositivos para a criação de limites de rede <!-- 1311967 -->   
Criámos um perfil de configuração de dispositivos denominado **Limite de rede** que poderá encontrar juntamente com os seus restantes perfis de configuração de dispositivos. Utilize este perfil para definir os recursos online que pretende que sejam considerados como empresariais e fidedignos. Tem de definir um limite de rede para um dispositivo *antes* de as funcionalidades como o Windows Defender Application Guard e o Windows Information Protection poderem ser utilizadas no dispositivo. É importante definir apenas um limite de rede para cada dispositivo.

Pode definir os recursos do Enterprise Cloud, intervalos de endereços IP e servidores proxy internos que pretende que sejam considerados fidedignos. Assim que o definir, o limite de rede pode ser utilizado por outras funcionalidades, tais como o Windows Defender Application Guard e o Windows Information Protection.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Duas definições adicionais do Antivírus do Windows Defender <!-- 1338409 -->  
**Nível de bloqueio de ficheiros**

| | |
|---|---|
| Não Configurado | A definição **Não Configurado** utiliza o nível de bloqueio predefinido do Antivírus do Windows Defender e oferece um sistema de deteção avançado sem aumentar o risco de detetar ficheiros legítimos. |
| Alto | A opção**Alto** aplica um nível de deteção elevado.
| Alto +  | A opção **Alto +** proporciona o nível de deteção Alto com medidas adicionais de proteção que podem afetar o desempenho do cliente.
| Tolerância zero  | A opção **Tolerância zero** bloqueia todos os executáveis desconhecidos. |

Embora seja pouco provável, mudar para o nível **Alto** pode fazer com que alguns ficheiros legítimos sejam detetados.
Recomendamos que mude o Nível de bloqueio de ficheiros para o valor predefinido **Não configurado**.

**Extensão do tempo limite para a pesquisa de ficheiros pela cloud**  

| | |
|--|--|
| Número de segundos (0-50) | Especifique o período de tempo máximo em que o Antivírus do Windows Defender deve bloquear um ficheiro enquanto aguarda por um resultado da cloud. O período predefinido é de 10 segundos: o tempo adicional que for especificado aqui (até um máximo de 50 segundos) será adicionado a esses 10 segundos. Na maioria dos casos, a pesquisa demora muito menos tempo do que o tempo máximo permitido. Alargar o período de tempo permite que a cloud investigue ficheiros suspeitos de forma mais minuciosa. Recomendamos que ative esta definição e especifique, no mínimo, um aumento de 20 segundos adicionais. |


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Suporte para a Autoridade de Certificação (AC) da Symantec Cloud <!-- 1333638 -->    
Atualmente, o Intune suporta a AC da Symantec Cloud, cuja permite que o Intune Certificate Connector envie certificados PKCS da AC da Symantec Cloud para dispositivos geridos pelo Intune. Se já estiver a utilizar o Intune Certificate Connector com a Autoridade de Certificação (CA) da Microsoft, pode utilizar a configuração existente do Intune Certificate Connector para incluir o suporte à AC da Symantec.


### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa <!--1490692-->  
Estamos a melhorar o fluxo de trabalho da configuração de dispositivos na aplicação Portal da Empresa para Android. O tipo de linguagem será mais simples e específico para a sua empresa. Além disso, iremos combinar os ecrãs sempre que possível. 

### <a name="block-unsupported-samsung-knox-device-activation------1490695----"></a>Bloquear a ativação de dispositivos Samsung Knox não suportados <!--- 1490695 --->  
A aplicação Portal da Empresa tenta apenas a ativação do Samsung KNOX durante a inscrição MDM se o dispositivo for apresentado na [lista de dispositivos KNOX suportados](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Esta restrição ajuda a evitar erros de ativação de KNOX que impedem a inscrição MDM. Os dispositivos que não suportam a ativação do Samsung KNOX são inscritos como dispositivos Android padrão. Um dispositivo Samsung pode ter alguns números de modelo que suportem o KNOX, enquanto outros não. Verifique a compatibilidade com o KNOX junto do revendedor do seu dispositivo antes da compra e implementação de dispositivos Samsung.

A seguinte lista de modelos de dispositivos Samsung não suporta KNOX e são inscritos como dispositivos Android nativos pela aplicação Portal da Empresa para Android:

| **Nome do Dispositivo** | **Números de Modelo do Dispositivo** |
| --- | --- |
| Galaxy A3 | SM-A300G<br>SM-A310Y<br>SM-A320FL |
| Galaxy A5 | SM-A500G |
| Galaxy Alpha | SM-G850M |
| Galaxy Avant | SM-G386T |
| Galaxy C9/C9 Pro | SM-C900F |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime | SM-G530M |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M<br>SM-J320W8 |
| Galaxy J5 | SM-J500G |
| Galaxy J7 | SM-J710F |
| Galaxy J7 Prime | SM-J727T1 |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 5 | SM-N920G<br>SM-N920I<br>SM-N920W8 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy NotePRO 12.2&quot; | SM-P902 |
| Galaxy On5 | SM-G570MSM-G570Y |
| Galaxy On7 | SM-G600FY<br>SM-G610M<br>SM-G610Y |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Active | GT-I9295 |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W<br>SM-G900M |
| Galaxy S5 Neo | SM-G903M |
| Galaxy S6 Edge | 404SCSM-G925I<br>SM-G928G |
| Galaxy Tab A 7.0&quot; | SM-T280SM-T285 |
| Galaxy Tab A 9.7&quot; | SM-P555M |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116SM-T210SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adição da VPN do Citrix para dispositivos Windows 10 <!-- 1512457 -->  
O cliente poderá configurar a VPN do Citrix nos seus dispositivos Windows 10. Pode selecionar a VPN do Citrix na lista *Selecione um tipo de ligação* no painel **VPN Base** ao configurar uma VPN para o Windows 10 e posterior.

> [!Note]
> A configuração do Citrix existia para os sistemas iOS e Android.





<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Suporte ao Google Play Protect no Android<!-- 908720  -->  
Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune suportará as funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet.  Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente. A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play.  O acesso condicional pode impedir que os utilizadores acedam a recursos da empresa caso o dispositivo não esteja em conformidade com os requisitos do Google Play Protect. 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedir que os utilizadores de dispositivos Android alterem a data e hora dos dispositivos <!-- 1333292 -->
Pode utilizar uma [política de dispositivo personalizada do Android](custom-settings-android.md) para impedir que os utilizadores de dispositivos Android alterem a data e a hora do dispositivo.
Para tal, configure uma política personalizada do Android com a definição URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange, defina a opção como **TRUE**e, em seguida, atribua-a aos grupos necessários.

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Ver as atribuições de políticas de proteção de aplicações para resolução de problemas <!--  1475003 -->
Nesta versão futura, a opção **Política de proteção de aplicações** será adicionada a **Atribuições**, na lista pendente disponível no painel de resolução de problemas. Agora, pode selecionar as políticas de proteção de aplicações para ver as políticas de proteção de aplicações que foram atribuídas aos utilizadores selecionados.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Criar aplicações iOS limitadas a Lojas de Aplicações da Apple regionais específicas <!-- 1281692 -->
Poderá especificar a região do país durante a criação de uma aplicação gerida pela Loja de Aplicações da Apple.

> [!NOTE]  
> Atualmente, só pode criar aplicações geridas pela Loja de Aplicações da Apple que estejam presentes na loja dos EUA.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selecionar a loja do país da Apple para sincronizar aplicações VPP <!-- 1332311 -->  
Poderá configurar o Volume Purchase Program (VPP) ao carregar o token VPP. O Intune sincroniza as aplicações VPP para todas as regiões a partir da loja do país do VPP especificada.

> [!NOTE]  
> Atualmente, o Intune só sincroniza as aplicações VPP a partir da loja do país do VPP que corresponda à região do Intune na qual foi criado o inquilino do Intune.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Atualizar o utilizador do VPP para iOS e as aplicações licenciadas de dispositivos <!-- 1305564 -->  
Poderá configurar o token VPP para iOS para atualizar todas as aplicações compradas para esse token através do serviço Intune. O Intune vai detetar as atualizações de aplicações VPP no interior da loja de aplicações e emiti-las automaticamente para o dispositivo quando este entra.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 Team <!--- 1308838  -->
Adicionámos muitas definições novas ao perfil de restrição de dispositivos Windows 10 Team para ajudar a controlar os dispositivos Surface Hub.
Para obter mais informações sobre este perfil, veja [Definições de restrição de dispositivos Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Suporte para a política de atualização da edição do Windows 10 <!-- 903672(archived), 1119689 -->  
Poderá criar uma política de atualização da edição do Windows 10 que atualize os dispositivos Windows 10 para Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10](edition-upgrade-configure-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Suporte remoto para Windows e dispositivos móveis do Windows <!-- 1070473 -->    
O Intune poderá utilizar o software [TeamViewer](https://www.teamviewer.com), comprado separadamente, para lhe permitir disponibilizar assistência remota aos utilizadores com o Windows e dispositivos Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analisar dispositivos com o Windows Defender <!-- 1280988  1280990   -->
Será capaz de executar uma **Análise rápida**, **Análise completa** e **Atualizar assinaturas** com o Windows Defender Antivirus em dispositivos Windows 10 geridos. No painel de descrição geral do dispositivo, escolha a ação a executar no dispositivo. Ser-lhe-á pedido para confirmar a ação antes do comando ser enviado para o dispositivo. 

**Análise rápida**: uma análise rápida analisa as localizações onde se inicia o registo do software maligno, tais como chaves do registo e pastas de arranque conhecidas do Windows. Uma análise rápida demora cerca de cinco minutos. Combinada com a definição **Proteção em tempo real sempre ativada**, que analisa os ficheiros quando são abertos, quando são fechados e sempre que um utilizador navega para uma pasta, a análise rápida ajuda a fornecer proteção contra software maligno que poderá estar no sistema ou no kernel. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Análise completa**: pode ser útil uma análise completa em dispositivos que encontraram uma ameaça de software maligno para identificar se existem componentes inativos que requerem uma limpeza mais detalhada- É também útil para executar análises a pedido. Uma análise completa pode demorar cerca de uma hora. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Atualizar assinaturas**: o comando de atualização de assinaturas atualiza as definições e as assinaturas do software maligno do Windows Defender Antivirus. Este comando ajuda a garantir que o Windows Defender Antivirus é eficaz na deteção de software maligno. Esta funcionalidade destina-se apenas a dispositivos Windows 10, com ligação à Internet dos dispositivos pendente. 

### <a name="bitlocker-device-configuration----1397398---"></a>Configuração do dispositivo BitLocker <!-- 1397398 -->  
A definição **Encriptação do Windows > Definições Base** incluirá uma nova definição **Aviso para a encriptação de outro disco**, que permitirá desativar o [pedido de aviso](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para a encriptação de outro disco que poderá estar em utilização no dispositivo do utilizador.  O pedido de aviso necessita de consentimento do utilizador para configurar o BitLocker no dispositivo e bloqueia a configuração do BitLocker até confirmação do utilizador final.  A nova definição desativa o aviso do utilizador final.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Mudança do Portal da Empresa para Windows 8.1 e do Windows Phone 8.1 para modo de suporte <!--1428681-->
A partir de outubro de 2017, as aplicações Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 irão passar para o modo de suporte, o que significa que as aplicações e os cenários existentes, tais como inscrição e conformidade, continuarão a ter suporte nestas plataformas. Estas aplicações continuarão a estar disponíveis para transferência através dos canais de lançamento existentes, tais como a Loja Microsoft. 

Quando estiverem no modo de suporte, estas aplicações receberão apenas atualizações de segurança críticas. Não haverá quaisquer atualizações ou funcionalidades adicionais para estas aplicações. Para obter novas funcionalidades, recomendamos que atualize os dispositivos para Windows 10 ou Windows 10 Mobile. 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloquear ações de copiar e colar entre perfis de trabalho e pessoais no Android for Work <!-- 1098994 -->   
Poderá configurar o perfil de trabalho do Android for Work para bloquear as ações de copiar e colar entre aplicações pessoais e de trabalho. Pode encontrar esta nova definição no perfil **Restrições do dispositivo** da Plataforma **Android for Work** em **Definições do perfil de trabalho**.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Novo comportamentos para a aplicação Portal da Empresa para Android com perfis de trabalho <!---1485783--->
Quando inscreve um dispositivo Android for Work num perfil de trabalho, é a aplicação Portal da Empresa no perfil de trabalho que executa as tarefas de gestão no dispositivo. Se estiver a utilizar uma aplicação ativada para MAM no perfil pessoal, a aplicação Portal da Empresa para Android já não terá qualquer utilidade. Para melhorar a experiência do perfil de trabalho, o Intune ocultará automaticamente a aplicação Portal da Empresa depois de inscrever com sucesso o perfil de trabalho.

A aplicação Portal da Empresa para Android pode ser ativada em qualquer altura no perfil pessoal. para tal, navegue para o [Portal da Empresa na Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e toque em **Ativar**.

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Intune MAM e suplementos do Outlook para Android <!-- 1450688 -->
Dentro de poucas semanas, a equipa do Office irá anunciar suplementos para o Outlook para Android. Este conjunto de funcionalidades já existe no Outlook para Windows, iOS, Web e Mac. Uma vez que os suplementos são geridos através do Exchange, os utilizadores serão capazes de copiar e partilhar dados e mensagens no Outlook e em aplicações de suplementos não geridas, exceto se os suplementos forem desativados pelo administrador do Exchange. 

Para gerir as permissões de acesso do utilizador aos suplementos, colabore com o administrador do Exchange para confirmar que as políticas de proteção de dados MAM se aplicam aos suplementos.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se as políticas do Exchange já estiverem definidas para o sideload ou a instalação de suplementos, não precisa de ler mais nada. As políticas de MAM serão aplicadas de acordo com o esperado. Se, no entanto, tiver definido políticas de MAM para restringir as operações de cortar, copiar e colar no Outlook para Android e não tiver definido a política de suplementos no Exchange, saiba que, por predefinição, os utilizadores conseguirão instalar os suplementos no Outlook. Estes suplementos podem aceder ao corpo da mensagem, ao assunto e a outras propriedades da mensagem. Pode desativar a capacidade do utilizador em instalar suplementos. Para tal, peça ao Administrador do Exchange para remover as funções "As Minhas Aplicações do Marketplace" e "As Minhas Aplicações Personalizadas".

A alteração da definição no Exchange será aplicada ao Outlook para Windows, iOS, Web, Mac e dispositivos móveis. 

#### <a name="what-do-i-need-to-do"></a>O que preciso fazer?
Reveja hoje as suas políticas do Exchange. Informe o departamento de TI e a equipa de suporte técnico. Contacte a nossa equipa de suporte com dúvidas ou preocupações específicas. 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados do Armazém de Dados do Intune <!-- 1187917 -->
Poderá criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado.




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>Ações de não conformidade <!--730266  846515 -->     
As *ações de não conformidade* são uma nova funcionalidade de políticas de conformidade que lhe permitirá tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Novo relatório que indica os dispositivos iOS com versões mais antigas do iOS <!-- 1352223 -->
O relatório **Dispositivos iOS desatualizados** estará disponível na área de trabalho **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização iOS com atualizações disponíveis. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Novas definições para o perfil de restrição de dispositivos Windows 10
<!--- 978575, 1308849, -->
Estamos a adicionar novas definições ao perfil de restrição de dispositivos com o Windows 10 na categoria Windows Defender SmartScreen.

Para obter detalhes sobre o perfil de restrição de dispositivos com o Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos com o Windows 10 e posterior)]( device-restrictions-windows-10.md).

### <a name="android-for-work-support-for-lookout----1087312---"></a>Suporte do Android for Work para Lookout <!-- 1087312 -->   
O conector do Intune com o Lookout suportará dispositivos Android for Work ao utilizar a aplicação Lookout for Work. Pode implementar a aplicação Lookout dentro ou fora do contentor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Proteção de Aplicações Intune e Citrix MDX Development Tools <!-- 709185 -->
Pode gerir dispositivos e aplicações ao combinar o Citrix XenMobile MDX e o Microsoft Intune. Isto permite-lhe gerir aplicações com a política de proteção da aplicação Intune ao utilizar a tecnologia mVPN da Citrix.

Pode encontrar um repositório de códigos que contém a Ferramenta de Encapsulamento de Aplicações do Intune para iOS e Android, integrada com a tecnologia Citrix MDX mVPN.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954681 -->
Pode controlar o acesso aos recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Zimperium, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Pode configurar políticas de acesso condicional de EMS baseadas na avaliação de riscos do Zimperium, que é ativada através de políticas de conformidade do dispositivo do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->   
Pode ter múltiplas funções de Servidor de Acesso de Cliente (CAS) para o conector do Exchange no local. Por exemplo, se o CAS principal falhar, o conector do Exchange receberá uma consulta para reverter para outros CASs. Esta funcionalidade garante que o serviço não é interrompido.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Pacote de gestão do System Center Operations Manager para o conector do Exchange <!-- 885457 -->   
O pacote de gestão do System Center Operations Manager para o conector do Exchange estará disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta pacote de gestão proporciona formas diferentes de monitorizar o Intune quando precisar de resolver problemas.


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171127, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Os dispositivos que não forem atualizados antes do início de outubro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.


## <a name="intune-apps"></a>Aplicações do Intune

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Orientação melhorada no pedido de acesso aos contactos em dispositivos Android <!--1484985-->   
A aplicação Portal da Empresa para Android exige frequentemente que o utilizador final aceite as permissões de Contactos. Se um utilizador final recusar este acesso, o mesmo verá uma notificação na aplicação que o alerta para o conceder para acesso condicional.

### <a name="secure-startup-remediation-for-android---1490712--"></a>Remediação de arranque seguro para Android <!--1490712-->     
Os utilizadores finais com dispositivos Android poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema.


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redirecionar utilizadores do macOS para a nova aplicação Portal da Empresa <!--1380728-->   
Quando um utilizador final inicia sessão no site do Portal da Empresa para inscrever o seu dispositivo macOS, este será direcionado para transferir a nova aplicação Portal da Empresa para macOS para concluir o processo. Isto ocorre nos dispositivos macOS que utilizam o OS X El Capitan 10.11 ou posterior. 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Suporte para a autenticação baseada em certificados no Portal da Empresa para iOS <!--1029830-->
Adicionámos o suporte para a autenticação baseada em certificados (CBA) na aplicação Portal da Empresa para iOS. Os utilizadores com CBA devem introduzir o seu nome de utilizador e, em seguida, tocar na ligação "Iniciar sessão com um certificado". A CBA já é suportada na aplicação Portal da Empresa para Android e Windows. Pode obter mais informações na página [Iniciar sessão na aplicação Portal da Empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

<!-- the following are present prior to 1710 -->

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>Melhorias na pesquisa no site do Portal da Empresa <!--1331697-->  
Estamos a melhorar as nossas capacidades de pesquisa da aplicação, a começar com o [site do Portal da Empresa](https://portal.manage.microsoft.com). As pesquisas serão agora efetuadas em categorias de aplicações para além dos campos Nome e Descrição. Os resultados serão ordenados, por predefinição, por ordem decrescente de relevância. 

Os utilizadores do iOS também receberão esta alteração, uma vez que o site do Portal da Empresa também é utilizado como parte da aplicação Portal da Empresa para iOS. As aplicações do Portal da Empresa para Android e Windows irão receber atualizações semelhantes nos próximos meses.

Estamos ainda a aperfeiçoar a forma como a relevância é controlada, pelo que pedimos que nos indique como está a funcionar através da ligação "Comentários" na parte inferior do site do Portal da Empresa.

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Ação de atualizar adicionada à aplicação Portal da Empresa para Windows 10 <!--1132468-->  
A aplicação Portal da Empresa para Windows 10 permitirá aos utilizadores atualizar os dados na aplicação, ao pedir para atualizar ou, em ambientes de trabalho, ao premir F5.


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição. <!-- 1334712 -->
As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android podem ser instaladas sem qualquer pedido de inscrição.

### <a name="ios-company-portal-display-large-icons----1454593---"></a>O Portal da Empresa para iOS apresenta ícones grandes <!-- 1454593 -->
Estamos a corrigir um problema conhecido sobre a forma como Portal da Empresa para iOS apresenta os ícones no mosaico da aplicação. Se carregar ícones da aplicação de 120 x 120 pixels ou superior, serão agora apresentados no [site do Portal da Empresa] (https://portal.manage.microsoft.com) e nas páginas das aplicações do Portal da Empresa para iOS com o tamanho máximo do mosaico da aplicação.

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!-- 1374196 -->
A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores veem uma mensagem de erro acionável amigável: "Inscreveu o número máximo de dispositivos permitidos pela sua equipa de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."




## <a name="notices"></a>Avisos

### <a name="device-and-app-management-integration----677972---"></a>Integração da gestão de dispositivos e aplicações <!-- 677972 -->   
Agora que tanto a gestão de dispositivos móveis (MDM) do Intune como a gestão de aplicações móveis (MAM) se encontram acessíveis no portal do Azure, o Intune iniciou a integração da experiência de administradores de TI em torno da gestão de aplicações e dispositivos. Estas alterações foram concebidas de modo a simplificar a sua experiência de gestão de dispositivos e aplicações.

Saiba mais sobre as alterações de MDM e MAM anunciadas no [blogue da equipa de suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->   
A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.


### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Novo caminho para dispositivos geridos na Graph API <!-- 1586728 -->  
Na versão de serviço do Intune de outubro, iremos efetuar uma alteração ao caminho utilizado para aceder a dispositivos geridos na versão beta da Graph API.

| | |
|--|--|
| Caminho atual |  https://graph.microsoft.com/beta/managedDevices |
| Novo caminho | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Ambos os caminhos estarão a funcionar ao longo do mês de outubro. Após a versão de serviço de outubro, apenas o novo caminho estará funcional.  Se estiver a utilizar a Graph API para aceder a dispositivos geridos, atualize e verifique os seus scripts e aplicações através do novo caminho. Para ver alterações adicionais, veja o [registo de alterações da Graph API](https://developer.microsoft.com/en-us/graph/docs/concepts/changelog) mensal.

### <a name="see-also"></a>Veja também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
