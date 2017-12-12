---
title: Novidades do Microsoft Intune
titlesuffix: Azure portal
description: Descobrir as novidades do Intune no portal do Azure
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/20/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3e17a932eb77d5b5917c18e4383cbbfb2aeb539
ms.sourcegitcommit: 70dc0aaad51b447e173b663d1092d993dc81ffdd
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/02/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Pode também descobrir quais são as [alterações futuras](#whats-coming), os [avisos importantes](#notices) sobre o serviço e as informações sobre [versões anteriores](whats-new-archive.md).

> [!Note]
> Muitas destas funcionalidades também serão suportadas, em algum momento, em implementações híbridas com o Configuration Manager. Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-november-27-2017"></a>Semana de 27 de novembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos
 
#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Resolução de problemas de inscrição <!-- 746324 --> 

A área de trabalho **Resolução de Problemas** agora apresenta os problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros. 

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrições de inscrição atribuídas a grupos <!-- 747598 -->
 
Enquanto administrador do Intune, agora pode [criar restrições de inscrição personalizadas de Tipo de Dispositivo e Limite de Dispositivo para grupos de utilizadores](enrollment-restrictions-set.md).
 
O Portal do Azure do Intune permite-lhe criar até 25 instâncias de cada tipo de restrição que podem depois ser atribuídas a grupos de utilizadores. As restrições atribuídas a grupos substituem as restrições predefinidas.
 
Todas as instâncias de um tipo de restrição são mantidas numa lista estritamente ordenada. Esta ordem define um valor de prioridade para a resolução do conflito. Um utilizador afetado por mais do que uma instância de restrição só é restringido pela instância com o valor de prioridade mais elevada. Pode alterar a prioridade de uma determinada instância ao arrastá-la para uma posição diferente na lista. 
 
Esta funcionalidade será lançada com a migração das definições do Android for Work do menu de inscrição do Android for Work para o menu Restrições de Inscrição. Como esta migração pode demorar vários dias, poderão ser atualizadas outras partes da sua conta no lançamento de novembro antes da ativação da atribuição de grupos nas Restrições de Inscrição.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Suporte para múltiplos conectores do Serviço de Inscrição de Dispositivos de Rede (NDES) <!-- 1528104 -->

O NDES permite a execução de dispositivos móveis sem credenciais de domínio para obter certificados com base no protocolo SCEP (Simple Certificate Enrollment Protocol). Com esta atualização, são suportados múltiplos conectores do NDES. 

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 EEready-->
 
**Nota**: as seguintes alterações começarão a ser implementadas com a atualização de novembro, mas a execução na sua conta poderá demorar algum tempo. Receberá uma notificação de confirmação no portal do Office 365 quando estas alterações entrarem em vigor na sua conta. Após a implementação, terá opções de capacidade de gestão adicionais. Não existirão alterações à experiência do utilizador final durante a implementação.
 
O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)
 
Por predefinição, as definições dos dispositivos Android for Work são as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.
 
Se bloquear a inscrição pessoal do Android for Work, só será possível inscrever dispositivos Android empresariais como Android for Work.
 
Ao trabalhar com as novas definições, considere o seguinte:
 
##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se nunca tiver integrado a inscrição do Android for Work
 
A nova plataforma do Android for Work está bloqueada nas Restrições de Tipos de Dispositivos predefinidas. Depois de integrar a funcionalidade, pode permitir que os dispositivos sejam inscritos com o Android for Work. Para tal, altere a predefinição ou crie uma nova Restrição de Tipo de Dispositivo para substituir a Restrição de Tipo de Dispositivo predefinida.
 
##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se já tiver integrado a inscrição do Android for Work
 
Se já a tiver integrado, a sua situação depende da definição que escolher:
 
| Definição | Estado do Android for Work em Restrição de Tipo de Dispositivo predefinida | Notas |
| --- | --- | --- |
| **Gerir todos os dispositivos como Android** | Bloqueado | Todos os dispositivos Android têm de ser inscritos sem o Android for Work. |
| **Gerir dispositivos suportados como Android for Work** | Permitido | Todos os dispositivos Android que suportam o Android for Work têm de ser inscritos com o Android for Work. |
| **Gerir dispositivos suportados para utilizadores apenas nestes grupos como Android for Work** | Bloqueado | Foi criada uma política de Restrição de Tipo de Dispositivo separada para substituir a predefinição. Esta política define os grupos que selecionou anteriormente para permitir a inscrição do Android for Work. Os utilizadores nos grupos selecionados continuarão a poder inscrever os seus dispositivos Android for Work. Todos os outros utilizadores não efetuam a inscrição com o Android for Work. |
 
Em todos os casos, mantém-se o seu regulamento pretendido. Não é necessária nenhuma ação da sua parte para manter a permissão global ou por grupo do Android for Work no seu ambiente.

### <a name="app-management"></a>Gestão de aplicações
  
#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>O relatório de instalação da aplicação foi atualizado para incluir o estado Instalação Pendente <!-- 1249446 -->  

O relatório **Estado de instalação de aplicação** acessível para cada aplicação através da lista **Aplicação** na carga de trabalho **Aplicações móveis** contém uma contagem de **Instalações Pendente** para Utilizadores e Dispositivos.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API do inventário de aplicações para iOS 11 para a Deteção de Ameaças para Dispositivos Móveis <!-- 1391759 -->

O Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Deteção de Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Pode recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS 11 ou uma versão superior.

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


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reiniciar dispositivos iOS remotamente (apenas supervisionado) <!-- 1424595 -->

Agora pode acionar o reinício de um dispositivo supervisionado com o iOS 10.3 ou superior ao utilizar uma ação de dispositivo. Para obter mais informações sobre como utilizar a ação de reinício de dispositivos, veja [Reiniciar remotamente dispositivos com o Intune](device-restart.md).

> [!Note]
> Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.

#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune <!-- 1437691 -->

Pode bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral dos dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Suporte para novos detalhes do perfil SCEP <!-- 1559808 -->

Agora, os administradores podem configurar definições adicionais ao criar um perfil SCEP em plataformas Windows, iOS, macOS e Android.  Os administradores podem definir o IMEI, o número de série ou o nome comum, incluindo o e-mail, no formato do nome do requerente.

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747----"></a>Gerir dispositivos macOS inscritos com Jamf através do motor de conformidade de dispositivo do Intune <!---1592747 --->
No início de 2018, o Jamf enviará informações sobre o estado do dispositivo macOS ao Intune que, em seguida, avaliará a conformidade com as políticas definidas na consola do Intune. Com base no estado de conformidade do dispositivo, bem como outras condições (como a localização, risco do utilizador, etc.), o acesso condicional estabelecerá a conformidade dos dispositivos macOS que tentem aceder a aplicações na nuvem e no local ligadas com o Azure Active Directory, incluindo o Office 365.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Reter dados durante uma reposição de fábrica <!--1588489 -->
Quando repõe uma versão 1709 ou posterior do Windows 10 para as definições de fábrica, fica disponível uma nova capacidade. Os administradores podem especificar se a inscrição de dispositivos e outros dados aprovisionados são retidos num dispositivo através de uma reposição de fábrica. 

Os seguintes dados são retidos através de uma reposição de fábrica:
- Contas de utilizador associadas ao dispositivo
- Estado da máquina (associação a um domínio, associado ao Azure Active Directory)
- Inscrição na MDM
- Aplicações OEM instaladas (aplicações Win32 e da loja)
- Perfil de utilizador
- Dados de utilizador fora do perfil de utilizador
- Início de sessão automático de utilizador
 
Os seguintes dados não são retidos:
- Ficheiros do utilizador
- Aplicações instaladas pelo utilizador (aplicações Win32 e da loja)
- Definições do dispositivo não predefinidas

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Atribuições de cadência de atualização do Windows 10 são apresentadas <!-- 1621837 -->
Durante a **Resolução de problemas** do utilizador que está a ver, pode ver todas as atribuições de cadências de atualização do Windows 10.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Definições da frequência de relatórios de Proteção Avançada Contra Ameaças do Windows Defender <!--- 1455974  --->
O serviço de Proteção Avançada Contra Ameaças do Windows Defender (WDATP) permite aos administradores gerir a frequência de relatórios dos dispositivos geridos. Com a nova opção **Acelerar a frequência do relatório de telemetria**, o WDATP recolhe os dados e avalia os riscos com mais frequência. A predefinição dos relatórios otimiza a velocidade e o desempenho. O aumento da frequência de relatórios pode ser útil para dispositivos de alto risco. Poderá encontrar esta definição no perfil **Windows Defender ATP** nas **Configurações do dispositivo**.

#### <a name="audit-updates----1412961---"></a>Atualizações de auditoria <!-- 1412961 -->  
A auditoria do Intune fornece um registo das operações de alteração relacionadas com o Intune.  Todas as operações de criação, atualização, eliminação e realização de tarefas remotas são capturadas e retidas durante um ano.  O portal do Azure fornece uma vista dos dados de auditoria dos últimos 30 dias em cada carga de trabalho e podem ser filtrados.  A Graph API correspondente permite a obtenção dos dados de auditoria armazenados do último ano. 

A Auditoria está localizada no grupo **MONITORIZAÇÃO**. Existe um item de menu **Registos de Auditoria** para cada carga de trabalho.   


## <a name="week-of-november-20-2017"></a>Semana de 20 de novembro de 2017

### <a name="app-management"></a>Gestão de aplicações

#### <a name="google-play-protect-support-on-android----908720---"></a>Suporte ao Google Play Protect no Android<!-- 908720 -->

Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune suportará as funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet. Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente.
A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play. O acesso condicional pode impedir que os utilizadores acedam a recursos da empresa caso o dispositivo não esteja em conformidade com os requisitos do Google Play Protect.

- Saiba [Como criar uma política de conformidade de dispositivos para ativar o Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas <!-- 1414050  -->

As aplicações geridas pelo SDK da Aplicação Intune podem enviar mensagens SMS.

## <a name="week-of-november-13-2017"></a>Semana de 13 de novembro de 2017

### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>A aplicação Portal da Empresa para macOS está disponível <!--1541700-->
O Portal da Empresa do Intune no macOS tem uma experiência atualizada, a qual foi otimizada para apresentar corretamente todas as informações e notificações de conformidade que os utilizadores precisam para todos os dispositivos inscritos. Além disso, após implementar o Portal da Empresa do Intune num dispositivo, o Microsoft AutoUpdate para macOS fornecerá as atualizações. Pode transferir o novo Portal da Empresa do Intune para macOS ao iniciar sessão no site do Portal da Empresa do Intune a partir de um dispositivo macOS.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>O Microsoft Planner faz agora parte da lista de gestão de aplicações móveis (MAM) de aplicações aprovadas <!-- 1248473 -->
A aplicação Microsoft Planner para iOS e Android faz agora parte das aplicações aprovadas para a gestão de aplicações móveis (MAM). A aplicação pode ser configurada através do painel Proteção de Aplicações do Intune no portal do Azure para todos os inquilinos.
- Saiba mais sobre a [Lista MAM de aplicações aprovadas](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frequência de atualização dos requisitos de VPN por Aplicação em dispositivos iOS <!-- 1547061 -->  
Os administradores podem agora remover os requisitos de VPN por Aplicação para as aplicações em dispositivos iOS; os dispositivos afetados serão removidos após a próxima entrada do Intune, o que geralmente ocorre num espaço de 15 minutos.  

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Suporte para o pacote de gestão do System Center Operations Manager do conector do Exchange <!-- 885457 -->
O pacote de gestão do System Center Operations Manager (SCOM) do conector do Exchange está agora disponível para ajudá-lo a analisar os registos do conector do Exchange. Este pacote de gestão proporciona-lhe várias formas de monitorizar o serviço quando precisar de resolver problemas.

## <a name="week-of-november-6-2017"></a>Semana de 6 de novembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestão para dispositivos Windows 10 <!-- 1243445 -->
A cogestão é uma solução que proporciona a transição de uma gestão tradicional para uma moderna, além de permitir que faça essa transição de forma faseada. Na sua génese, a cogestão é uma solução em que os dispositivos Windows 10 são geridos simultaneamente pelo Configuration Manager e pelo Microsoft Intune, além de estar associada ao Active Directory (AD) e ao Azure Active Directory (Azure AD).  Esta configuração proporciona-lhe uma forma de modernizar a gestão com ao longo do tempo e ao ritmo mais adequado para a sua organização, caso não consiga efetuar a mudança de uma só vez.  

#### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Nova página de estado de inscrição para inscrições de dispositivos Windows 10 <!--1063201-->    
Agora pode configurar uma saudação a ser apresentada quando os seus utilizadores inscreverem dispositivos Windows 10. Utilize o **Ecrã do Estado de Inscrição** para configurar uma mensagem personalizada e uma hiperligação a apresentar aos seus utilizadores finais quando estes inscreverem os respetivos dispositivos Windows 10.  O **Ecrã do Estado de Inscrição** também proporciona aos utilizadores finais uma visão geral sobre o progresso das definições de política que estão a ser aplicadas ao seu dispositivo.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Restringir a Inscrição do Windows por versão do SO <!-- 245498 -->
Enquanto administrador do Intune, pode especificar uma versão mínima e máxima do Windows 10 para a inscrição de dispositivos. Pode definir estas restrições no painel **Configurações da Plataforma**.

O Intune irá continuar a suportar a inscrição de telemóveis e PCs com o Windows 8.1. No entanto, apenas as versões do Windows 10 podem ser definidas com os limites mínimo e máximo. Para permitir a inscrição de dispositivos com o Windows 8.1, deixe o limite mínimo em branco.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 1631236 -->
Está disponível um novo alerta para dispositivos Windows AutoPilot não atribuídos na página **Microsoft Intune** > **Inscrição de dispositivos** > **Descrição geral**. Este alerta mostra o número de dispositivos do programa AutoPilot que não têm perfis de implementação do AutoPilot atribuídos. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows AutoPilot e informações detalhadas sobre os mesmos. Para obter mais informações, veja [Inscrever dispositivos Windows com o programa de implementação do Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Botão de atualização da lista Dispositivos    <!-- 1333581 -->
Como a lista Dispositivos não atualiza automaticamente, pode utilizar o novo botão Atualizar para atualizar os dispositivos que são apresentados na lista.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Suporte para a Autoridade de Certificação (AC) da Symantec Cloud <!-- 1333638 -->    
Atualmente, o Intune suporta a AC da Symantec Cloud, cuja permite que o Intune Certificate Connector envie certificados PKCS da AC da Symantec Cloud para dispositivos geridos pelo Intune. Se já estiver a utilizar o Intune Certificate Connector com a Autoridade de Certificação (CA) da Microsoft, pode utilizar a configuração existente do Intune Certificate Connector para incluir o suporte à AC da Symantec.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Novos itens adicionados ao inventário de dispositivos   <!--1404455 -->
Nesta versão, adicionámos os seguintes novos itens ao [inventário feito por dispositivo inscrito](device-inventory.md):

- Endereço MAC Wi-Fi
- Espaço de armazenamento total
- Espaço livre total
- MEID
- Operadora subscritora


### <a name="app-management"></a>Gestão de aplicações
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Definir o acesso a aplicações através de uma atualização de segurança mínima para Android no dispositivo <!-- 1278463 -->   
Um administrador pode definir a atualização de segurança mínima para Android que tem de ser instalada no dispositivo, de modo a obter acesso a uma aplicação gerida numa conta gerida.

> [!Note]  
> Esta funcionalidade apenas restringe atualizações de segurança lançadas pela Google em dispositivos Android 6.0+.

#### <a name="app-conditional-launch-support----1193313---"></a>Suporte para execução condicional de aplicações <!-- 1193313 -->
Os administradores de TI já podem definir um requisito através do portal de administração do Azure para impor um código de acesso em vez de um PIN numérico através da gestão de aplicações móveis (MAM) quando a aplicações é executada. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. Esta versão do Intune irá ativar esta funcionalidade **apenas no iOS**. O Intune suporta um código de acesso de forma semelhante a um PIN numérico: a aplicação define um comprimento mínimo e permite sequências e carateres repetidos. Esta funcionalidade requer que a participação de aplicações (por exemplo, WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune com o código desta funcionalidade para que as definições do código de acesso sejam impostas nas aplicações visadas.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número da Versão de Aplicação para aplicações de linha de negócio no relatório de estado de instalação do dispositivo <!-- 1233999 -->
Com esta versão, o relatório de estado de instalação do Dispositivo apresenta o número da versão de aplicação das aplicações de linha de negócio para iOS e Android. Pode utilizar estas informações para resolver problemas nas suas aplicações ou localizar dispositivos que estão a ser executados com versões desatualizadas da aplicação.


### <a name="device-configuration"></a>Configuração do dispositivo
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Agora, os administradores podem configurar as definições de Firewall num dispositivo através de um perfil de configuração de dispositivo <!-- 951708 -->   
Os administradores podem ativar a firewall para os dispositivos, bem como configurar vários protocolos para redes de domínio privadas e públicas.  Poderá encontrar estas definições de firewall no perfil "Proteção de ponto final".

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>O Windows Defender Application Guard ajuda a proteger os dispositivos de sites não fidedignos, consoante as definições da sua organização <!-- 958257 -->   
Os administradores podem definir sites como "fidedigno" ou "empresarial" através de um fluxo do Windows Information Protection ou do novo perfil "Limite de rede" nas configurações dos dispositivos. Se forem visualizados com o Microsoft Edge, todos os sites que não estiverem indicados no limite de rede fidedigno de um dispositivo com o Windows 10 de 64 bits serão abertos num browser com um computador virtual Hyper-V.

Poderá encontrar o Application Guard nos perfis de configuração de dispositivos, no perfil "Proteção de ponto final". A partir daí, os administradores podem configurar a interação entre o browser virtualizado e o computador anfitrião, sites fidedignos e não fidedignos e os dados de armazenamento gerados no browser virtualizado. Para utilizar o Application Guard num dispositivo, é necessário configurar primeiro um limite de rede. É importante definir apenas um limite de rede para um dispositivo.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>O Controlo de Aplicações do Windows Defender no Windows 10 Enterprise fornece um modo para confiar apenas em aplicações autorizadas <!-- 1031096 -->    
Com milhares de novos ficheiros maliciosos a serem criados todos os dias, a deteção com base em assinatura de antivírus para combater software maligno poderá deixar de ser uma defesa adequada contra novos ataques. Com o Controlo de Aplicações do Windows Defender no Windows 10 Enterprise, pode alterar a configuração do dispositivo de um modo em que as aplicações são fidedignas, a menos que sejam bloqueadas por um antivírus ou por outra solução de segurança, para um modo em que o sistema operativo confia apenas nas aplicações autorizadas pela sua empresa. A atribuição de fidedignidade a aplicações é feita no Controlo de Aplicações do Windows Defender.

Com o Intune, pode configurar as políticas de controlo de aplicações no modo "apenas auditoria" ou no modo de imposição. As aplicações não serão bloqueadas ao serem executadas no modo "apenas auditoria". O modo "apenas auditoria" regista todos os eventos nos registos do cliente local. Também pode configurar se pretende que apenas os componentes Windows e as aplicações da Microsoft Store tenham permissão para serem executados ou se pretende permitir a execução de aplicações adicionais com boa reputação, conforme definidas pelo Gráfico de Segurança Inteligente.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>O Windows Defender Exploit Guard é um novo conjunto de funcionalidades de prevenção de intrusões para o Windows 10 <!-- 1063615 -->   
O Windows Defender Exploit Guard inclui regras personalizadas para reduzir a exploração de aplicações, impede ameaças de macros e scripts, bloqueia automaticamente ligações de rede a endereço IP com baixa reputação e ajuda a proteger os dados de ransomware e ameaças desconhecidas. O Windows Defender Exploit Guard consiste nos seguintes componentes:

- A **Redução da Superfície de Ataque (ASR)** fornece regras que lhe permitem impedir ameaças de macros, scripts e e-mail.
- O **Acesso a Pastas Controladas** bloqueia automaticamente o acesso a conteúdos de pastas protegidas.
- O **Filtro de Rede** bloqueia a ligação de saída de qualquer aplicação para um IP/domínio com baixa reputação
- A **Exploit Protection** fornece restrições de memória, fluxo de controlos e de políticas que podem ser utilizadas para proteger um aplicação de exploits.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gerir scripts do PowerShell no Intune para dispositivos Windows 10 <!-- 790537 -->

A extensão de gestão do Intune permite-lhe carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão complementa as funcionalidades de gestão de dispositivos móveis (MDM) do Windows 10 e facilita a sua transição para a gestão moderna. Para obter detalhes, veja [Manage PowerShell scripts in Intune for Windows 10 devices (Gerir scripts do PowerShell no Intune para dispositivos Windows 10)](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Novas definições de restrição de dispositivos para Windows 10      <!-- 1308850 -->
-    Mensagens (apenas para telemóveis) – desativar mensagens de teste ou MMS
-    Palavra-passe – definições para ativar o sistema FIPS e utilizar dispositivos secundários Windows Hello para efeitos de autenticação 
-    Apresentação – definições para ativar ou desativar o Dimensionamento de GDI para aplicações legadas

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrições de dispositivos Windows 10 no modo de local público <!-- 1308872 -->   
Pode restringir os utilizadores de dispositivos Windows 10 ao modo de local público, que os limita a um conjunto de aplicações predefinidas.  Para fazê-lo, crie um perfil de restrição de dispositivos Windows 10 e configure as definições do modo de local público.

O modo de local público suporta dois modos: **quiosque de uma aplicação** (permite que um utilizador execute apenas uma aplicação) ou **quiosque de várias aplicações** (concede acesso a um conjunto de aplicações).  Defina a conta de utilizador e o nome do dispositivo, o qual determina as aplicações suportadas).  Quando o utilizador tiver sessão iniciada, este será limitado às aplicações definidas.  Para saber mais, veja [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

O modo de local público necessita que:

- O Intune seja a autoridade MDM.
- As aplicações já estejam instaladas no dispositivo alvo.
- O dispositivo esteja [devidamente aprovisionado](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Novo perfil de configuração de dispositivos para a criação de limites de rede <!-- 1311967 -->   
Criámos um perfil de configuração de dispositivos denominado **Limite de rede** que poderá encontrar juntamente com os seus restantes perfis de configuração de dispositivos. Utilize este perfil para definir os recursos online que pretende que sejam considerados como empresariais e fidedignos. Tem de definir um limite de rede para um dispositivo *antes* de as funcionalidades como o Windows Defender Application Guard e o Windows Information Protection poderem ser utilizadas no dispositivo. É importante definir apenas um limite de rede para cada dispositivo.

Pode definir os recursos do Enterprise Cloud, intervalos de endereços IP e servidores proxy internos que pretende que sejam considerados fidedignos. Assim que o definir, o limite de rede pode ser utilizado por outras funcionalidades, tais como o Windows Defender Application Guard e o Windows Information Protection.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Duas definições adicionais do Antivírus do Windows Defender <!-- 1338409 -->  
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

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adição da VPN do Citrix para dispositivos Windows 10 <!-- 1512457 -->  
Pode configurar a VPN do Citrix nos respetivos dispositivos Windows 10. Pode selecionar a VPN do Citrix na lista *Selecione um tipo de ligação* no painel **VPN Base** ao configurar uma VPN para o Windows 10 e posterior.

> [!Note]
> A configuração do Citrix existia para os sistemas iOS e Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>As ligações Wi-Fi suportam chaves pré-partilhadas no iOS <!-- 1550823 -->
Os clientes podem configurar perfis de Wi-Fi para utilizar chaves pré-partilhadas (PSK) para ligações Pessoais WPA/WPA2 em dispositivos iOS. Estes perfis são enviados via push para o dispositivo do utilizador quando o dispositivo está inscrito no Intune.

Quando o perfil tiver sido enviado para o dispositivo, o passo seguinte depende da configuração do perfil.  Se estiver definido para ligar automaticamente, assim o faz quando a rede se tornar necessária.  Quando o perfil está definido para ligar manualmente, o utilizador tem de ativar a ligação manualmente.  

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Acesso a registos de aplicações geridas para iOS <!-- 1469920 -->
Agora, os utilizadores finais com o Managed Browser instalado podem ver o estado da gestão de todas as aplicações publicadas da Microsoft e enviar registos para resolver os problemas das respetivas aplicações iOS geridas.

Para saber como ativar o modo de resolução de problemas num Managed Browser num dispositivo iOS, veja [How to access to managed app logs using the Managed Browser on iOS (Como aceder a registos de aplicações geridas com o Managed Browser no iOS)](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa para iOS na versão 2.9.0 <!---1417174--->

Melhorámos o fluxo de trabalho da configuração de dispositivos na aplicação Portal da Empresa para iOS. O tipo de linguagem é mais simples. Além disso, combinámos os ecrãs sempre que possível. Também tornámos o tipo de linguagem mais específico para a sua empresa ao utilizar o nome da mesma em todo o texto de configuração. Pode ver este fluxo de trabalho atualizado em  [novidades na página da IU para aplicações](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>A entidade User contém dados de utilizador no modelo de dados do Armazém de Dados <!-- 1544273 -->
A primeira versão do modelo de dados do Armazém de Dados do Intune continha apenas dados de histórico recentes do Intune. Os criadores de relatórios não conseguiam capturar o estado atual de um utilizador. Nesta atualização, a **entidade User** é preenchida com os dados de utilizador mais recentes.


## <a name="week-of-october-30-2017"></a>Semana de 30 de outubro de 2017

### <a name="app-management"></a>Gestão de aplicações

#### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>O número da versão da aplicação de linha de negócio para iOS e Android está visível <!-- 1380712 -->

As aplicações no Intune apresentam agora o número da versão de aplicações de linha de negócio para iOS e Android. O número é apresentado no portal do Azure na lista de aplicações e no painel de descrição geral da aplicação. Os utilizadores finais podem ver o número da aplicação na aplicação Portal da Empresa e no portal Web.

__Número da versão completo__ – O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), por exemplo, 2.2(2.2.17560800).

O número da versão completo tem dois componentes:

 - **Versão**  
   O número da versão é o número da versão legível por humanos da aplicação. Este número é utilizado pelos utilizadores finais para identificar diferentes versões da aplicação.

 - **Número de Compilação**  
    O número de compilação é um número interno que pode ser utilizado para detetar aplicações e gerir a aplicação de forma programática. O número de compilação refere-se a uma iteração da aplicação que faz referência a alterações no código.

Saiba mais sobre os números de versão e o desenvolvimento de aplicações de linha de negócio em [Introdução ao SDK da Aplicação Microsoft Intune](app-sdk-get-started.md#line-of-business-app-version-numbers).

#### <a name="device-and-app-management-integration----677972---"></a>Integração da gestão de dispositivos e aplicações <!-- 677972 -->   
Agora que tanto a gestão de dispositivos móveis (MDM) do Intune como a gestão de aplicações móveis (MAM) se encontram acessíveis no portal do Azure, o Intune iniciou a integração da experiência de administradores de TI em torno da gestão de aplicações e dispositivos. Estas alterações foram concebidas de modo a simplificar a sua experiência de gestão de dispositivos e aplicações.

Saiba mais sobre as alterações de MDM e MAM anunciadas no [blogue da equipa de suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

#### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Novos alertas de inscrição para dispositivos da Apple <!-- 1471790 -->
A página de descrição geral para inscrição apresentará alertas úteis para os administradores de TI sobre a gestão de dispositivos da Apple. Os alertas serão apresentados na página Descrição Geral quando o certificado push de MDM da Apple estiver prestes a expirar ou já tiver expirado, quando o token do Programa de Registo de Aparelho estiver prestes a expirar ou já tiver expirado e quando existirem dispositivos não atribuídos no Programa de Registo de Aparelho.

#### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Substituição do token de suporte para a configuração de aplicações sem inscrição de dispositivos <!-- 1080364 -->

Pode utilizar tokens para valores dinâmicos em configurações da aplicação para aplicações em dispositivos que não estejam inscritos. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos](app-configuration-policies-managed-app.md).

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Atualizações à aplicação Portal da Empresa para Windows 10 <!--1299474-->
A página Definições na aplicação Portal da Empresa para Windows 10 foi atualizada para tornar as definições e as ações do utilizador em causa mais consistentes em todas as definições. Também foi atualizada para corresponder ao esquema de outras aplicações do Windows. Pode encontrar imagens antes/depois na página [novidades na página da IU para aplicações](whats-new-app-ui.md).

#### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para dispositivos Windows 10 <!--1337920-->
Adicionámos o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para Windows 10. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã **Acerca de**.

#### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Pedidos de comentários sobre a aplicação Portal da Empresa para Android<!--1165249-->
A aplicação Portal da Empresa para Android solicita agora comentários aos utilizadores finais. Este feedback são enviados diretamente para a Microsoft e fornecem aos utilizadores finais uma oportunidade para reverem a aplicação na Google Play Store pública. Os comentários não são obrigatórios e podem ser dispensados facilmente para os utilizadores poderem continuar a utilizar a aplicação.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

#### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ajudar os utilizadores a resolver problemas com a aplicação Portal da Empresa para Android <!---1573324, 1573150, 1558616, 1564878--->

A aplicação Portal da Empresa para Android adicionou instruções para ajudar os utilizadores finais a compreender e, sempre que possível, a resolver autonomamente novos casos de utilização.
- Os utilizadores finais serão encaminhados para o (portal do Azure Active Directory) [https://account.activedirectory.windowsazure.com/r/#/profile] para remover um dispositivo se tiverem atingido o número máximo de dispositivos que estão autorizados a adicionar.
- Os utilizadores finais recebem uma lista de passos a seguir para os ajudar a [corrigir erros de ativação em dispositivos Samsung KNOX](https://go.microsoft.com/fwlink/?linkid=859718) ou a [desativar o modo de poupança de energia](/intune-user-help/power-saving-mode-android). Se nenhuma dessas soluções resolver o problema, forneceremos uma explicação sobre como [enviar registos para a Microsoft](/intune-user-help/send-logs-to-microsoft-ios).

#### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nova ação "Resolver" disponível para dispositivos Android <!---1583480--->

A aplicação Portal da Empresa para Android está a introduzir a ação "Resolver" na página _Atualizar definições do dispositivo_. A seleção desta opção levará o utilizador diretamente para a definição que está a fazer com que o dispositivo não esteja em conformidade. A aplicação Portal da Empresa para Android suporta atualmente esta ação para as definições de [código de acesso do dispositivo](/intune-user-help/set-your-pin-or-password-android), [depuração de USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [Origens Desconhecidas](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

#### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicador de progresso da configuração do dispositivo no Portal da Empresa para Android <!---1565657--->
A aplicação Portal da Empresa para Android mostra um indicador de progresso da configuração do dispositivo quando um utilizador está a inscrever o dispositivo. O indicador mostra novos estados, a começar por “A configurar o dispositivo…”, seguido de “A registar o dispositivo…”, “A concluir o registo do dispositivo...” e “A concluir a configuração do dispositivo...”.

## <a name="week-of-october-23-2017"></a>Semana de 23 de outubro de 2017

### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Suporte para a autenticação baseada em certificados no Portal da Empresa para iOS <!--1029830-->
Adicionámos o suporte para a autenticação baseada em certificados (CBA) na aplicação Portal da Empresa para iOS. Os utilizadores com CBA devem introduzir o seu nome de utilizador e, em seguida, tocar na ligação "Iniciar sessão com um certificado". A CBA já é suportada na aplicação Portal da Empresa para Android e Windows. Pode obter mais informações na página [Iniciar sessão na aplicação Portal da Empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

#### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição. <!-- 1334712 -->

As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android já podem ser instaladas sem qualquer pedido de inscrição.

## <a name="week-of-october-16-2017"></a>Semana de 16 de outubro de 2017
### <a name="device-enrollment"></a>Inscrição de dispositivos
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Suporte do Programa Windows AutoPilot Deployment no Microsoft Intune <!-- 747617  -->
Agora pode utilizar o Microsoft Intune com o Programa Windows AutoPilot Deployment para permitir que os utilizadores aprovisionem os respetivos dispositivos da empresa sem envolver o departamento de TI. Pode personalizar a configuração inicial (OOBE) e guiar os utilizadores para associarem os respetivos dispositivos ao Azure AD e inscrevê-los no Intune. Ao trabalharem em conjunto, o Microsoft Intune e o Windows AutoPilot eliminam a necessidade de implementar, manter e gerir imagens de sistema operativo. Para obter detalhes, veja [Enroll Windows devices using Windows AutoPilot Deployment Program (Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment)](https://docs.microsoft.com/intune/enrollment-autopilot).

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>Guia de introdução da inscrição de dispositivos <!-- 1425655 --> 
O guia de introdução está disponível em **Inscrição de dispositivos** e fornece uma tabela de referência para gerir plataformas e configurar o processo de inscrição. Uma breve descrição de cada item e as ligações para documentos com instruções passo a passo fornecem documentos úteis para simplificar a introdução.

#### <a name="device-categorization----1427491---"></a>Categorização de dispositivos <!-- 1427491 -->
O gráfico da plataforma de dispositivos inscritos do painel **Dispositivos > Descrição Geral** organiza os dispositivos por plataforma, incluindo Android, iOS, macOS, Windows e Windows Mobile.  Os dispositivos com outros sistemas operativos são agrupados em "Outro".  Isto inclui dispositivos fabricados pela Blackberry, NOKIA, entre outros.  

Para saber quais são os dispositivos afetados no seu inquilino, selecione **Gerir > Todos os dispositivos** e, em seguida, utilize o **Filtro** para limitar o campo **SO**.

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954681 -->  
Pode controlar o acesso aos recursos empresariais a partir de dispositivos móveis através do acesso condicional com base na avaliação de riscos realizada pelo Zimperium, uma solução de Defesa Contra Ameaças para Dispositivos Móveis que está integrada com o Microsoft Intune.

##### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Pode configurar políticas de acesso condicional de EMS baseadas na avaliação de riscos do Zimperium, que é ativada através de políticas de conformidade do dispositivo do Intune, as quais pode utilizar para permitir ou impedir que os dispositivos não conformes acedam aos recursos empresariais com base em ameaças detetadas.

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 <!--- 978575, 1308849, -->  
Estamos a adicionar novas definições ao perfil de restrição de dispositivos com o Windows 10 na categoria Windows Defender SmartScreen.

Para obter detalhes sobre o perfil de restrição de dispositivos com o Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos com o Windows 10 e posterior)]( device-restrictions-windows-10.md).

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Suporte remoto para dispositivos Windows e Windows Mobile <!-- 1070473 -->  
O Intune pode utilizar o software [TeamViewer](https://www.teamviewer.com), comprado separadamente, para lhe permitir disponibilizar assistência remota aos utilizadores com o Windows e dispositivos Windows Mobile.

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analisar dispositivos com o Windows Defender <!-- 1280988  1280990   -->
Pode executar uma **Análise rápida**, **Análise completa** e **Atualizar assinaturas** com o Antivírus do Windows Defender em dispositivos Windows 10 geridos. No painel de descrição geral do dispositivo, escolha a ação a executar no dispositivo. Ser-lhe-á pedido para confirmar a ação antes do comando ser enviado para o dispositivo. 

**Análise rápida**: uma análise rápida analisa as localizações onde se inicia o registo do software maligno, tais como chaves do registo e pastas de arranque conhecidas do Windows. Uma análise rápida demora cerca de cinco minutos. Combinada com a definição **Proteção em tempo real sempre ativada**, que analisa os ficheiros quando são abertos, quando são fechados e sempre que um utilizador navega para uma pasta, a análise rápida ajuda a fornecer proteção contra software maligno que poderá estar no sistema ou no kernel. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Análise completa**: pode ser útil uma análise completa em dispositivos que encontraram uma ameaça de software maligno para identificar se existem componentes inativos que requerem uma limpeza mais detalhada- É também útil para executar análises a pedido. Uma análise completa pode demorar cerca de uma hora. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Atualizar assinaturas**: o comando de atualização de assinaturas atualiza as definições e as assinaturas do software maligno do Windows Defender Antivirus. Este comando ajuda a garantir que o Windows Defender Antivirus é eficaz na deteção de software maligno. Esta funcionalidade destina-se apenas a dispositivos Windows 10, com ligação à Internet dos dispositivos pendente. 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>O botão Ativar/Desativar é removido da página Autoridade de Certificação do Intune do portal do Azure no Intune <!-- 1400455 -->
 Vamos eliminar um passo extra na configuração do Certificate Connector no Intune. Neste momento, pode transferir o Certificate Connector e, em seguida, ativá-lo na consola do Intune. No entanto, se desativar o conector na consola do Intune, este continuará a emitir certificados.

##### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A partir de outubro, o botão Ativar/Desativar deixará de ser apresentado na página Autoridade de Certificação no portal do Azure. A funcionalidade do conector permanece igual. Os certificados continuam a ser implementados nos dispositivos inscritos no Intune. Pode continuar a transferir e instalar o Certificate Connector. Para interromper a emissão de certificados, desinstale o Certificate Connector em vez de o desativar.

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se tiver o Certificate Connector desativado, deve desinstalá-lo.

### <a name="device-configuration"></a>Configuração do dispositivo
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 Team <!--- 1308838 -->
Nesta versão, adicionámos muitas definições novas ao perfil de restrição de dispositivos Windows 10 Team para ajudar a controlar os dispositivos Surface Hub.

Para obter mais informações sobre este perfil, veja [Definições de restrição de dispositivos Windows 10 Team](device-restrictions-windows-10-teams.md).

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedir que os utilizadores de dispositivos Android alterem a data e hora dos dispositivos <!-- 1333292 -->
Pode utilizar uma [política de dispositivo personalizada do Android](custom-settings-android.md) para impedir que os utilizadores de dispositivos Android alterem a data e a hora do dispositivo.

Para tal, configure uma política personalizada do Android com a definição URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Defina esta opção como **TRUE**e, em seguida, atribua-a aos grupos necessários.

#### <a name="bitlocker-device-configuration----1397398---"></a>Configuração do dispositivo BitLocker <!-- 1397398 -->
A opção **Encriptação Windows > Definições Base** inclui uma nova definição **Aviso para a encriptação de outro disco**, que permitirá desativar o [pedido de aviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para a encriptação de outro disco que poderá estar em utilização no dispositivo do utilizador.  O pedido de aviso necessita de consentimento do utilizador final para configurar o BitLocker no dispositivo e bloqueia a configuração do BitLocker até confirmação do utilizador final.  A nova definição desativa o aviso do utilizador final.


### <a name="app-management"></a>Gestão de aplicações
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>As aplicações do Volume Purchase Program for Business irão sincronizar com o seu Inquilino do Intune <!-- 800882 -->  
Os programadores de terceiros podem distribuir em privado aplicações aos membros autorizados do Volume Purchase Program (VPP) for Business especificados no iTunes Connect. Estes membros do VPP for Business podem iniciar sessão na Loja de Aplicações do Volume Purchase Program e comprar as suas aplicações.

Com esta versão, as aplicações do VPP for Business compradas pelo utilizador final começarão a sincronizar com os respetivos inquilinos do Intune.

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selecionar a loja do país da Apple para sincronizar aplicações VPP <!-- 1332311 -->  
Pode configurar o Volume Purchase Program (VPP) ao carregar o token VPP. O Intune sincroniza as aplicações VPP para todas as regiões a partir da loja do país do VPP especificada.

> [!NOTE]  
> Atualmente, o Intune só sincroniza as aplicações VPP a partir da loja do país do VPP que corresponda à região do Intune na qual foi criado o inquilino do Intune.


### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloquear ações de copiar e colar entre perfis de trabalho e pessoais no Android for Work <!-- 1098994 -->
Com esta versão, pode configurar o perfil de trabalho do Android for Work para bloquear as ações de copiar e colar entre aplicações pessoais e de trabalho. Pode encontrar esta nova definição no perfil **Restrições do dispositivo** da Plataforma **Android for Work** em **Definições do perfil de trabalho**.

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Criar aplicações iOS limitadas a Lojas de Aplicações da Apple regionais específicas <!-- 1281692 -->
Poderá especificar a região do país durante a criação de uma aplicação gerida pela Loja de Aplicações da Apple.

> [!Note]  
> Atualmente, só pode criar aplicações geridas pela Apple App Store que estejam presentes na loja dos E.U.A.

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Atualizar o utilizador do VPP para iOS e as aplicações licenciadas de dispositivos <!-- 1305564 -->  
Poderá configurar o token VPP para iOS para atualizar todas as aplicações compradas para esse token através do serviço Intune. O Intune vai detetar as atualizações de aplicações VPP no interior da loja de aplicações e emiti-las automaticamente para o dispositivo quando este entra.

Para obter passos para configurar um token do VPP e ativar as atualizações automáticas, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados do Armazém de Dados do Intune <!-- 1187917 -->
Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado.

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Rever a conformidade das políticas das cadências de atualização do Windows 10 <!-- 1067886 -->
Poderá rever um relatório das políticas das cadências de atualização do Windows 10 em Atualizações de software > Por estado de implementação da cadência de atualização. O relatório das políticas inclui o estado de implementação das cadências de atualização configuradas. 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Novo relatório que indica os dispositivos iOS com versões mais antigas do iOS <!-- 1352223 -->
O relatório **Dispositivos iOS desatualizados** está disponível na área de trabalho **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização iOS com atualizações disponíveis. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Ver as atribuições de políticas de proteção de aplicações para resolução de problemas <!--  1475003 -->
Nesta versão futura, a opção **Política de proteção de aplicações** será adicionada a **Atribuições**, na lista pendente disponível no painel de resolução de problemas. Agora, pode selecionar as políticas de proteção de aplicações para ver as políticas de proteção de aplicações que foram atribuídas aos utilizadores selecionados.



## <a name="week-of-october-2-2017"></a>Semana de 2 de outubro de 2017
### <a name="intune-apps"></a>Aplicações do Intune
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa <!--1490692-->
Melhorámos o fluxo de trabalho da configuração de dispositivos na aplicação Portal da Empresa para Android. O tipo de linguagem é mais simples e específico para a sua empresa. Além disso, combinámos os ecrãs sempre que possível. Pode ver estas melhorias na página [Novidades na IU da aplicação](whats-new-app-ui.md#week-of-october-2-2017).

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Orientação melhorada no pedido de acesso aos contactos em dispositivos Android <!--1484985-->

A aplicação Portal da Empresa para Android exige frequentemente que o utilizador final aceite as permissões de Contactos. Se um utilizador final recusar este acesso, verá agora uma notificação na aplicação que o alerta para o conceder para acesso condicional. 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Remediação de arranque seguro para Android <!--1490712-->

Os utilizadores finais com dispositivos Android poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema. 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notificações push adicionais para utilizadores finais na aplicação Portal da Empresa para Android Oreo <!--1475932-->

Os utilizadores finais receberão notificações adicionais a indicar quando a aplicação Portal da Empresa para Android Oreo está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune. Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas nos respetivos dispositivos. Isto faz parte da [otimização geral da IU do Portal da Empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) para a aplicação Portal da Empresa para Android Oreo. 

Existem mais otimizações para novos elementos da IU que estão ativadas no Android Oreo.  Os utilizadores finais receberão notificações adicionais a indicar quando o Portal da Empresa está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune.  Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas no dispositivo.

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Novo comportamentos para a aplicação Portal da Empresa para Android com perfis de trabalho <!---1485783--->

Quando inscreve um dispositivo Android for Work num perfil de trabalho, é a aplicação Portal da Empresa no perfil de trabalho que executa as tarefas de gestão no dispositivo. 

Se estiver a utilizar uma aplicação ativada para MAM no perfil pessoal, a aplicação Portal da Empresa para Android já não terá qualquer utilidade. Para melhorar a experiência do perfil de trabalho, o Intune ocultará automaticamente a aplicação Portal da Empresa depois de inscrever com sucesso o perfil de trabalho.

A aplicação Portal da Empresa para Android pode ser ativada em qualquer altura no perfil pessoal. para tal, navegue para o [Portal da Empresa na Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e toque em **Ativar**.

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Mudança do Portal da Empresa para Windows 8.1 e do Windows Phone 8.1 para modo de suporte <!--1428681-->

A partir de outubro de 2017, as aplicações Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 irão passar para o modo de suporte, o que significa que as aplicações e os cenários existentes, tais como inscrição e conformidade, continuarão a ter suporte nestas plataformas. Estas aplicações continuarão a estar disponíveis para transferência através dos canais de lançamento existentes, tais como a Loja Microsoft. 

Quando estiverem no modo de suporte, estas aplicações receberão apenas atualizações de segurança críticas. Não haverá quaisquer atualizações ou funcionalidades adicionais para estas aplicações. Para obter novas funcionalidades, recomendamos que atualize os dispositivos para Windows 10 ou Windows 10 Mobile. 


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>Bloquear a inscrição de dispositivos Samsung Knox não suportados <!--- 1490695 --->

A aplicação Portal da Empresa apenas tenta inscrever dispositivos Samsung Knox suportados. Para evitar erros de ativação KNOX que impeçam a inscrição MDM, a tentativa de inscrição do dispositivo só é efetuada se o dispositivo aparecer na [lista de dispositivos publicados pela Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Os dispositivos Samsung poderão ter números de modelo compatíveis ou não com o KNOX. Verifique a compatibilidade com o Knox junto do revendedor do seu dispositivo antes da compra e implementação. Poderá encontrar a lista completa de dispositivos verificados nas [Definições da política para Android e Samsung KNOX Standard](/intune/supported-devices-browsers.md#intune-supported-devices).

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171126, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas em dispositivos inscritos <!--1165314-->
Iremos adicionar o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo em todas as aplicações Portal da Empresa. Isto permitirá aos utilizadores saber mais sobre a privacidade diretamente a partir do artigo [Que informações pode a sua empresa ver?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Isto será implementado em todas as aplicações Portal da Empresa brevemente. Anunciámos esta funcionalidade para iOS em [setembro](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).


## <a name="week-of-september-25-2017"></a>Semana de 25 de setembro de 2017

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-supports-ios-11---1428975--"></a>O Intune suporta o iOS 11 <!--1428975-->
O Intune suporta o iOS 11. Isto foi anteriormente anunciado no [blogue de Suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

#### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!---1164477--->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. 

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Ação de atualizar adicionada à aplicação Portal da Empresa para Windows 10 <!--1132468-->
A aplicação Portal da Empresa para Windows 10 permite aos utilizadores atualizar os dados na aplicação, ao pedir para atualizar ou, em computadores, ao premir F5.



## <a name="notices"></a>Avisos

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android <!-- 1490731 EEready-->
 
**Nota**: as seguintes alterações começarão a ser implementadas com a atualização de novembro, mas a execução na sua conta poderá demorar algum tempo. Receberá uma notificação de confirmação no portal do Office 365 quando estas alterações entrarem em vigor na sua conta. Após a implementação, terá opções de capacidade de gestão adicionais. Não existirão alterações à experiência do utilizador final durante a implementação.
 
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

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>O suporte para OS X Mavericks 10.10 e versões anteriores do macOS está a ser descontinuado <!--1489263, plan for change for 1802-->
Estamos a anunciar que vamos começar a descontinuar a inscrição de dispositivos com o OS X Yosemite 10.10 e com versões anteriores do macOS em fevereiro de 2018. O Intune suporta totalmente o OS X El Capitan 10.11 e as versões mais recentes.

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Novo caminho para dispositivos geridos na Graph API <!-- 1586728 -->
Estamos a alterar o caminho utilizado para aceder a dispositivos geridos na versão beta da Graph API. 

| | |
|--|--|
| Caminho atual |  https://graph.microsoft.com/beta/managedDevices |
| Novo caminho | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Ambos os caminhos estarão a funcionar ao longo do mês de outubro. Após a versão de serviço de outubro, apenas o novo caminho estará funcional.  Se estiver a utilizar a Graph API para aceder a dispositivos geridos, atualize e verifique os seus scripts e aplicações através do novo caminho. Para ver alterações adicionais, veja o [registo de alterações da Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) mensal.


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder ao portal do Azure.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Substituição das funções de administração no portal do Azure
As funções de administração de gestão de aplicações móveis (MAM) existentes (Contribuidor, Proprietário e Só de leitura) utilizadas no portal clássico do Intune (Silverlight) estão a ser substituídas por um conjunto completo de novos controlos de administração baseados em funções (RBAC) no portal do Azure no Intune. Após concluir a migração para o portal do Azure, terá de atribuir novamente os administradores a estas novas funções de administração. Para obter mais informações sobre as RBAC e as novas funções, veja [Controlo de acesso baseado em funções do Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Novidades futuras

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gerir dispositivos macOS inscritos com Jamf através do motor de conformidade de dispositivo do Intune <!---1592747--->
No início de 2018, o Jamf enviará informações sobre o estado do dispositivo macOS ao Intune que, em seguida, avaliará a conformidade com as políticas definidas na consola do Intune. Com base no estado de conformidade do dispositivo, bem como outras condições (como a localização, risco do utilizador, etc.), o acesso condicional estabelecerá a conformidade dos dispositivos macOS que tentem aceder a aplicações na nuvem e no local ligadas com o Azure Active Directory, incluindo o Office 365.

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Alterações ao suporte para a aplicação Portal da Empresa do Intune para iOS <!-- 1164474  -->
Em breve, será apresentada uma nova versão da aplicação Portal da Empresa do Microsoft Intune para iOS que suportará apenas dispositivos com o iOS 9.0 ou posterior. A versão do Portal da Empresa que suporta o iOS 8 continuará disponível durante um curto período de tempo. No entanto, tenha em atenção que, caso também utilize aplicações iOS com MAM ativada, suportamos o iOS 9.0 e posterior, pelo que deverá garantir que os seus utilizadores finais atualizam para a versão mais recente do SO. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Informamo-lo desta situação antecipadamente, mesmo sem termos datas específicas, para que tenha tempo para planear. Certifique-se de que os seus utilizadores atualizaram para o iOS 9 e posterior e, quando a aplicação Portal da Empresa for lançada, peça aos seus utilizadores que atualizem a mesma.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Incentive os utilizadores a atualizarem para o iOS 9.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.  Incentive os utilizadores a instalarem a nova versão do Portal da Empresa para tirarem partido das novas funcionalidades que oferece.

Aceda ao Intune no portal do Azure, vá para Dispositivos > Todos os Dispositivos e filtre pela versão do iOS para ver os dispositivos atuais com sistemas operativos anteriores ao iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->
A Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS.

Disponibilizamos uma versão da aplicação do Portal da Empresa para iOS através do programa TestFlight da Apple que impõe os novos requisitos da ATS. Se gostaria de a experimentar para testar a sua conformidade com a ATS, envie um e-mail para <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app"> CompanyPortalBeta@microsoft.com </a> com o seu nome próprio, apelido, endereço de e-mail e o nome da empresa. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

## <a name="see-also"></a>Veja também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na IU do Portal da Empresa](whats-new-app-ui.md)
* [Novidades nos meses anteriores](whats-new-archive.md)
