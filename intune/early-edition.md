---
title: "Edição antecipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d612f0e3ff3f38d51488818916479e8291c9e453
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---november-2017"></a>A edição antecipada do Microsoft Intune – novembro de 2017

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


### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada <!-- 1332318 -->
O tipo de aplicação **Incorporada** permite-lhe criar e atribuir aplicações do Office 365 mais facilmente aos dispositivos iOS e Android que está a gerir. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Suporte de Início de Sessão Único para iOS <!-- 1333645 -->  
Poderá utilizar o Início de Sessão Único para utilizadores do iOS. As aplicações iOS que estão codificadas para procurar as credenciais dos utilizadores no payload de Início de Sessão Único são compatíveis com esta atualização de configuração do payload. Também pode utilizar o UPN e o ID de Dispositivo do Intune para configurar o Nome Principal e o Realm.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API do inventário de aplicações para iOS 11 para a Deteção de Ameaças para Dispositivos Móveis <!-- 1391759 -->
O Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Deteção de Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Poderá recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS 11 ou uma versão superior.

**Inventário de aplicações**  
Os inventários de dispositivos iOS pessoais ou empresariais com o iOS 11 ou uma versão superior são enviados para o seu fornecedor de serviços de MTD. Os dados no inventário de aplicações incluem:

 - ID da Aplicação
 - Versão da Aplicação
 - Versão Abreviada da Aplicação
 - Nome da Aplicação
 - Tamanho da Coleção de Pacotes de Aplicação
 - Tamanho Dinâmico da Aplicação
 - A aplicação é ou não validada
 - A aplicação é ou não gerida

### <a name="audit-updates----1412961---"></a>Atualizações de auditoria <!-- 1412961 -->  
A auditoria do Intune fornece um registo das operações de alteração relacionadas com o Intune.  Todas as operações de criação, atualização, eliminação e realização de tarefas remotas são capturadas e retidas durante um ano.  O portal do Azure fornece uma vista dos dados de auditoria dos últimos 30 dias em cada carga de trabalho e podem ser filtrados.  A Graph API correspondente permite a obtenção dos dados de auditoria armazenados do último ano. 

A Auditoria está localizada no grupo **MONITORIZAÇÃO**. Existe um item de menu **Registos de Auditoria** para cada carga de trabalho.   

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas <!-- 1414050  -->
As aplicações geridas pelo SDK da Aplicação Intune poderão enviar mensagens SMS.

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reiniciar dispositivos iOS remotamente (apenas supervisionado) <!-- 1424595 -->
Poderá acionar o reinício de um dispositivo supervisionado com o iOS 10.3 ou uma versão superior ao utilizar uma ação de dispositivo. Para obter mais informações sobre como utilizar a ação de reinício de dispositivos, veja [Reiniciar remotamente dispositivos com o Intune](device-restart.md).

> [!Note]  
> Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune <!-- 1437691 -->
Poderá bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](device-remote-lock.md).

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Definições da frequência de relatórios de Proteção Avançada Contra Ameaças do Windows Defender <!--- 1455974  --->
O serviço de Proteção Avançada Contra Ameaças do Windows Defender (WDATP) permite aos administradores gerir a frequência de relatórios dos dispositivos geridos. Com a nova opção **Acelerar a frequência do relatório de telemetria**, o WDATP recolhe os dados e avalia os riscos com mais frequência. A predefinição dos relatórios otimiza a velocidade e o desempenho. O aumento da frequência de relatórios pode ser útil para dispositivos de alto risco. Poderá encontrar esta definição no perfil **Windows Defender ATP** nas **Configurações do dispositivo**.

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>A resolução de conflitos de atribuição mudou para as aplicações da loja iOS <!-- 1480316 -->
Os utilizadores finais poderão reparar numa alteração quanto à disponibilidade das aplicações da loja iOS. Atualmente, uma aplicação que tenha sido atribuída a dois grupos com um conflito entre **Necessário e Disponível** e **Não Aplicável** é resolvida para **Necessário e Disponível**. Com a alteração, uma aplicação com este conflito é resolvida para **Não Aplicável**.

A alteração diz respeito à confusão gerada quando uma aplicação é atribuída a múltiplos grupos com intenções diferentes no que diz respeito às aplicações.

Se pretender ter a sua aplicação disponível no Portal dos Técnicos de Informação e no Portal da Empresa antes do lançamento do serviço em novembro, tem duas opções:

1. Remova a atribuição **Não Aplicável** do seu grupo.
2. Crie um novo grupo que não inclua os membros com a intenção **Necessário e Disponível** atribuída e atribua a intenção **Não Aplicável** a esse grupo.

Para obter mais informações, veja [Como atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

> [!Note]
> Após o lançamento, deixará de poder ver ou modificar as atribuições de aplicação da Gestão de Dispositivos Móveis (MDM) na consola clássica do Intune. No entanto, pode utilizar a consola do Azure ou a Graph API do Intune para fazer as suas atribuições de aplicações.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 -->
O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)

Por predefinição, as definições dos dispositivos Android for Work serão as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.
 
Se bloquear a inscrição pessoal do Android for Work, só será possível inscrever dispositivos Android empresariais como Android for Work.

Ao trabalhar com as novas definições, considere o seguinte:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se nunca tiver integrado a inscrição do Android for Work
A nova plataforma do Android for Work está bloqueada nas Restrições de Tipos de Dispositivos predefinidas. Depois de integrar a funcionalidade, pode permitir que os dispositivos sejam inscritos com o Android for Work. Para tal, altere a predefinição ou crie uma nova Restrição de Tipo de Dispositivo para substituir a Restrição de Tipo de Dispositivo predefinida.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se já tiver integrado a inscrição do Android for Work
Se já a tiver integrado, a sua situação depende da definição que escolher:

| Definição | Estado do Android for Work em Restrição de Tipo de Dispositivo predefinida | Notas |
| --- | --- | --- |
| **Gerir todos os dispositivos como Android** | Bloqueado | Todos os dispositivos Android têm de ser inscritos sem o Android for Work. |
| **Gerir dispositivos suportados como Android for Work** | Permitido | Todos os dispositivos Android que suportam o Android for Work têm de ser inscritos com o Android for Work. |
| **Gerir dispositivos suportados para utilizadores apenas nestes grupos como Android for Work** | Bloqueado | Foi criada uma política de Restrição de Tipo de Dispositivo separada para substituir a predefinição. Esta política define os grupos que selecionou anteriormente para permitir a inscrição do Android for Work. Os utilizadores nos grupos selecionados continuarão a poder inscrever os seus dispositivos Android for Work. Todos os outros utilizadores não efetuam a inscrição com o Android for Work. |

Em todos os casos, mantém-se o seu regulamento pretendido. Não é necessária nenhuma ação da sua parte para manter a permissão global ou por grupo do Android for Work no seu ambiente.

Estas alterações começarão a ser implementadas com a atualização de novembro, mas a execução na sua conta poderá demorar algum tempo. Receberá uma notificação de confirmação no portal do Office 365 quando estas alterações entrarem em vigor na sua conta.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Suporte para múltiplos conectores do Serviço de Inscrição de Dispositivos de Rede (NDES) <!-- 1528104 -->
O NDES permite a execução de dispositivos móveis sem credenciais de domínio para obter certificados com base no protocolo SCEP (Simple Certificate Enrollment Protocol). Com esta atualização, serão suportados múltiplos conectores do NDES.

### <a name="new-scep-profile-details-supported----1559808---"></a>Suporte para novos detalhes do perfil SCEP <!-- 1559808 -->
Os administradores poderão configurar definições adicionais ao criar um perfil SCEP em plataformas Windows, iOS, macOS e Android.  Os administradores podem definir o IMEI, o número de série ou o nome comum, incluindo o e-mail, no formato do nome do requerente.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar um PIN da aplicação para iOS <!-- 1586774 -->
Em breve poderá exigir um PIN para aplicações específicas para iOS. Pode configurar a data de expiração em dias e a obrigatoriedade de introdução de PIN através do portal do Azure. Quando for necessário, um utilizador terá de definir e utilizar um PIN novo para ter acesso a uma aplicação iOS. Apenas as aplicações iOS que têm ativada a proteção de aplicações com o SDK da Aplicação Intune suportarão esta funcionalidade.

### <a name="retain-data-during-a-factory-reset-----1588489---"></a>Reter dados durante uma reposição de fábrica <!-- 1588489 -->
Estamos a adicionar suporte para uma nova capacidade de Reposição de fábrica do Windows. Atualmente, os administradores podem especificar se a inscrição de dispositivos e outros dados aprovisionados são retidos num dispositivo através de uma reposição de fábrica. 
 
Os seguintes dados são retidos através de uma reposição de fábrica:
- Contas de utilizador associadas ao dispositivo
- Estado da máquina (associação a um domínio, AADJ)
- Inscrição na MDM
- Aplicações OEM instaladas (aplicações Win32 e da loja)
- Perfil de utilizador
- Dados de utilizador fora do perfil de utilizador
- Início de sessão automático de utilizador
 
Os dados seguintes não são preservados:
- Ficheiros do utilizador
- Aplicações instaladas pelo utilizador (aplicações Win32 e da loja)
- Definições do dispositivo não predefinidas 

### <a name="app-install-status-report-now-a-bar-chart----1249446---"></a>Relatório do estado de instalação de aplicação agora em gráfico de barras <!-- 1249446 -->  
O relatório **Estado de instalação de aplicação** acessível para cada aplicação através da lista **Aplicação** na carga de trabalho **Aplicações móveis** será em breve convertido em gráfico de barras.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Adicionar "Encontrar iPhone" para dispositivos pessoais <!--1427287-->
Poderá ver se os dispositivos iOS têm o Bloqueio de Ativação ativado. Esta funcionalidade estava anteriormente disponível no portal clássico do Intune.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrições de inscrição atribuídas a grupos <!-- 747598 -->
Enquanto administrador do Intune, poderá criar restrições de inscrição personalizadas de Tipo de Dispositivo e Limite de Dispositivo para grupos de utilizadores.
 
O Portal do Azure do Intune permite-lhe criar até 25 instâncias de cada tipo de restrição que podem depois ser atribuídas a grupos de utilizadores. As restrições atribuídas a grupos substituem as restrições predefinidas.
 
Todas as instâncias de um tipo de restrição são mantidas numa lista estritamente ordenada. Esta ordem define um valor de prioridade para a resolução do conflito. Um utilizador afetado por mais do que uma instância de restrição só é restringido pela instância com o valor de prioridade mais elevada. Pode alterar a prioridade de uma determinada instância ao arrastá-la para uma posição diferente na lista. 
 
Esta funcionalidade será lançada com a migração das definições do Android for Work do menu de inscrição do Android for Work para o menu Restrições de Inscrição. Como esta migração pode demorar vários dias, poderão ser atualizadas outras partes da sua conta no lançamento de novembro antes da ativação da atribuição de grupos nas Restrições de Inscrição.

### <a name="windows-10-update-ring-assignments-are-displayed----1621837---"></a>Atribuições de cadência de atualização do Windows 10 são apresentadas <!-- 1621837 -->
Durante a **Resolução de problemas** do utilizador que está a ver, poderá ver todas as atribuições de cadências de atualização do Windows 10.  



<!-- the following are present prior to 1711 -->

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

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número da versão de aplicação para aplicações de linha de negócio no relatório de estado de instalação do dispositivo <!-- 1233999 -->  
O relatório de estado de instalação do dispositivo irá apresentar o número da versão de aplicação das aplicações de linha de negócio para iOS e Android. Pode utilizar estas informações para resolver problemas nas suas aplicações ou localizar dispositivos que estão a ser executados com versões desatualizadas da aplicação.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestão para dispositivos Windows 10 <!-- 1243445 -->
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



### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adição da VPN do Citrix para dispositivos Windows 10 <!-- 1512457 -->  
O cliente poderá configurar a VPN do Citrix nos seus dispositivos Windows 10. Pode selecionar a VPN do Citrix na lista *Selecione um tipo de ligação* no painel **VPN Base** ao configurar uma VPN para o Windows 10 e posterior.

> [!Note]
> A configuração do Citrix existia para os sistemas iOS e Android.



<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Suporte ao Google Play Protect no Android<!-- 908720  -->  
Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune suportará as funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet.  Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente. A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play.  O acesso condicional pode impedir que os utilizadores acedam a recursos da empresa caso o dispositivo não esteja em conformidade com os requisitos do Google Play Protect. 


### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Suporte para a política de atualização da edição do Windows 10 <!-- 903672(archived), 1119689 -->  
Poderá criar uma política de atualização da edição do Windows 10 que atualize os dispositivos Windows 10 para Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>Ações de não conformidade <!--730266  846515 -->     
As *ações de não conformidade* são uma nova funcionalidade de políticas de conformidade que lhe permitirá tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

### <a name="android-for-work-support-for-lookout----1087312---"></a>Suporte do Android for Work para Lookout <!-- 1087312 -->   
O conector do Intune com o Lookout suportará dispositivos Android for Work ao utilizar a aplicação Lookout for Work. Pode implementar a aplicação Lookout dentro ou fora do contentor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Proteção de Aplicações Intune e Citrix MDX Development Tools <!-- 709185 -->
Pode gerir dispositivos e aplicações ao combinar o Citrix XenMobile MDX e o Microsoft Intune. Isto permite-lhe gerir aplicações com a política de proteção da aplicação Intune ao utilizar a tecnologia mVPN da Citrix.

Pode encontrar um repositório de códigos que contém a Ferramenta de Encapsulamento de Aplicações do Intune para iOS e Android, integrada com a tecnologia Citrix MDX mVPN.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->   
Pode ter múltiplas funções de Servidor de Acesso de Cliente (CAS) para o conector do Exchange no local. Por exemplo, se o CAS principal falhar, o conector do Exchange receberá uma consulta para reverter para outros CASs. Esta funcionalidade garante que o serviço não é interrompido.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Pacote de gestão do System Center Operations Manager para o conector do Exchange <!-- 885457 -->   
O pacote de gestão do System Center Operations Manager para o conector do Exchange estará disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta pacote de gestão proporciona formas diferentes de monitorizar o Intune quando precisar de resolver problemas.





## <a name="intune-apps"></a>Aplicações do Intune

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ajudar os utilizadores a resolver problemas com a aplicação Portal da Empresa para Android <!---1573324, 1573150, 1558616, 1564878--->
A aplicação Portal da Empresa para Android está a adicionar instruções para ajudar os utilizadores a compreender e, sempre que possível, a resolver autonomamente novos casos de utilização. 

- Será apresentada uma nova mensagem que explica que foi implementada uma política de conformidade para encriptação, mas o [fabricante do dispositivo não está a encriptar o dispositivo](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android), de acordo com as [diretrizes recomendadas da Google] (https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean).
- Os utilizadores finais serão encaminhados para o (portal do Azure Active Directory) [https://account.activedirectory.windowsazure.com/r/#/profile] para remover um dispositivo se tiverem atingido o número máximo de dispositivos que estão autorizados a adicionar. 
- Os utilizadores finais recebem uma lista de passos a seguir para os ajudar a [corrigir erros de ativação em dispositivos Samsung KNOX](https://go.microsoft.com/fwlink/?linkid=859718) ou a [desativar o modo de poupança de energia](/intune-user-help/power-saving-mode-android). Se nenhuma dessas soluções resolver o problema, forneceremos uma explicação sobre como [enviar registos para a Microsoft](/intune-user-help/send-logs-to-microsoft-ios). 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nova ação "Resolver" disponível para dispositivos Android <!---1583480--->
A aplicação Portal da Empresa para Android está a introduzir a ação "Resolver" na página _Atualizar definições do dispositivo_. A seleção desta opção levará o utilizador diretamente para a definição que está a fazer com que o dispositivo não esteja em conformidade. A aplicação Portal da Empresa para Android suporta atualmente esta ação para as definições de [código de acesso do dispositivo](/intune-user-help/set-your-pin-or-password-android), [encriptação de dispositivos](/intune-user-help/encrypt-your-device-android), [depuração de USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [Origens Desconhecidas](/intune-user-help/you-need-to-turn-off-unknown-sources-android). 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redirecionar utilizadores do macOS para a nova aplicação Portal da Empresa <!--1380728-->   
Quando um utilizador final inicia sessão no site do Portal da Empresa para inscrever o seu dispositivo macOS, este será direcionado para transferir a nova aplicação Portal da Empresa para macOS para concluir o processo. Isto ocorre nos dispositivos macOS que utilizam o OS X El Capitan 10.11 ou posterior. 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição. <!-- 1334712 -->
As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android podem ser instaladas sem qualquer pedido de inscrição.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!-- 1374196 -->
A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores veem uma mensagem de erro acionável amigável: "Inscreveu o número máximo de dispositivos permitidos pela sua equipa de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."




## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.




### <a name="see-also"></a>Veja também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
