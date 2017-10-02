---
title: "Edição antecipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0ac0d1fd2f618339f847201f333d3f32561ca6b1
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="the-early-edition-for-microsoft-intune---september-2017"></a>Edição antecipada do Microsoft Intune – setembro de 2017

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


### <a name="google-play-protect-support-on-android----908720----"></a>Suporte ao Google Play Protect no Android<!-- 908720  -->  
Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune suportará as funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet.  Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente. A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play.  O acesso condicional pode impedir que os utilizadores acedam a recursos da empresa caso o dispositivo não esteja em conformidade com os requisitos do Google Play Protect. 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedir que os utilizadores de dispositivos Android alterem a data e hora dos dispositivos <!-- 1333292 -->
Pode utilizar uma [política de dispositivo personalizada do Android](custom-settings-android.md) para impedir que os utilizadores de dispositivos Android alterem a data e a hora do dispositivo.
Para tal, configure uma política personalizada do Android com a definição URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Defina esta opção como **TRUE**e, em seguida, atribua-a aos grupos necessários.

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Ver as atribuições de políticas de proteção de aplicações para resolução de problemas <!--  1475003 -->
Nesta versão futura, a opção **Política de proteção de aplicações** será adicionada a **Atribuições**, na lista pendente disponível no painel de resolução de problemas. Agora, pode selecionar as políticas de proteção de aplicações para ver as políticas de proteção de aplicações que foram atribuídas aos utilizadores selecionados.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Criar aplicações iOS limitadas a Lojas de Aplicações da Apple regionais específicas <!-- 1281692 -->
Poderá especificar a região do país durante a criação de uma aplicação gerida pela Loja de Aplicações da Apple.

> [!NOTE]  
> Atualmente, só pode criar aplicações geridas pela Loja de Aplicações da Apple que estejam presentes na loja dos EUA.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selecionar a loja do país da Apple para sincronizar aplicações VPP <!-- 1332311 -->  
Pode configurar o Volume Purchase Program (VPP) ao carregar o token VPP. O Intune sincroniza as aplicações VPP para todas as regiões a partir da loja do país do VPP especificada.

> [!NOTE]  
> Atualmente, o Intune só sincroniza as aplicações VPP a partir da loja do país do VPP que corresponda à região do Intune na qual foi criado o inquilino do Intune.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Atualizar o utilizador do VPP para iOS e as aplicações licenciadas de dispositivos <!-- 1305564 -->  
Poderá configurar o token VPP para iOS para atualizar todas as aplicações compradas para esse token através do serviço Intune. O Intune vai detetar as atualizações de aplicações VPP no interior da loja de aplicações e emiti-las automaticamente para o dispositivo quando este entra.

### <a name="ios-11-support----1428975---"></a>Suporte para iOS 11 <!-- 1428975 -->
Quando for lançado pela Apple, o Intune irá suportar o iOS 11.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 Team <!--- 1308838  -->
Nesta versão, adicionámos muitas definições novas ao perfil de restrição de dispositivos Windows 10 Team para ajudar a controlar os dispositivos Surface Hub.
Para obter mais informações sobre este perfil, veja [Definições de restrição de dispositivos Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="support-for-windows-10-edition-upgrade-policy------903672-1119689---"></a>Suporte para a política de atualização da edição do Windows 10 <!-- 903672, 1119689 -->  
Poderá criar uma política de atualização da edição do Windows 10 que atualize os dispositivos Windows 10 para Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10 ](edition-upgrade-configure-windows-10.md).

### <a name="review-policy-compliance-for-windows-10-update-rings----1352223---"></a>Rever a conformidade das políticas das cadências de atualização do Windows 10 <!-- 1352223 -->  
Poderá rever um relatório das políticas das cadências de atualização do Windows 10 em **Atualizações de software** > **Por estado da implementação das cadências de atualização**. O relatório das políticas inclui o estado de implementação das cadências de atualização configuradas. 

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Aplicação Portal da Empresa do Windows 10 adicionada à política de permissão do Windows Information Protection <!-- 677129 -->  
A aplicação Portal da Empresa do Windows 10 será atualizada para suportar o Windows Information Protection (WIP). A aplicação pode ser adicionada à política de permissão do WIP. Com esta alteração, a aplicação já não tem de ser adicionada à lista **Excluídas**. 

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Suporte remoto para Windows e dispositivos móveis do Windows <!-- 1070473 -->    
O Intune poderá utilizar o software [TeamViewer](https://www.teamviewer.com), comprado separadamente, para lhe permitir disponibilizar assistência remota aos utilizadores com o Windows e dispositivos Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analisar dispositivos com o Windows Defender <!-- 1280988  1280990   -->
Será capaz de executar uma **Análise rápida**, **Análise completa** e **Atualizar assinaturas** com o Windows Defender Antivirus em dispositivos Windows 10 geridos. No painel de descrição geral do dispositivo, escolha a ação a executar no dispositivo. Ser-lhe-á pedido para confirmar a ação antes do comando ser enviado para o dispositivo. 

**Análise rápida**: uma análise rápida analisa as localizações onde se inicia o registo do software maligno, tais como chaves do registo e pastas de arranque conhecidas do Windows. Uma análise rápida demora cerca de cinco minutos. Combinada com a definição **Proteção em tempo real sempre ativada**, que analisa os ficheiros quando são abertos, quando são fechados e sempre que um utilizador navega para uma pasta, a análise rápida ajuda a fornecer proteção contra software maligno que poderá estar no sistema ou no kernel. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Análise completa**: pode ser útil uma análise completa em dispositivos que encontraram uma ameaça de software maligno para identificar se existem componentes inativos que requerem uma limpeza mais detalhada- É também útil para executar análises a pedido. Uma análise completa pode demorar cerca de uma hora. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Atualizar assinaturas**: o comando de atualização de assinaturas atualiza as definições e as assinaturas do software maligno do Windows Defender Antivirus. Este comando ajuda a garantir que o Windows Defender Antivirus é eficaz na deteção de software maligno. Esta funcionalidade destina-se apenas a dispositivos Windows 10, com ligação à Internet dos dispositivos pendente. 

### <a name="bitlocker-device-configuration----1397398---"></a>Configuração do dispositivo BitLocker <!-- 1397398 -->  
A definição **Encriptação do Windows > Definições Base** incluirá uma nova definição **Aviso para a encriptação de outro disco**, que permitirá desativar o [pedido de aviso](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para a encriptação de outro disco que poderá estar em utilização no dispositivo do utilizador.  O pedido de aviso necessita de consentimento do utilizador final para configurar o BitLocker no dispositivo e bloqueia a configuração do BitLocker até confirmação do utilizador final.  A nova definição desativa o aviso do utilizador final.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Mudança do Portal da Empresa para Windows 8.1 e do Windows Phone 8.1 para modo de suporte <!--1428681-->
A partir de outubro de 2017, as aplicações Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 irão passar para o modo de suporte, o que significa que as aplicações e os cenários existentes, tais como inscrição e conformidade, continuarão a ter suporte nestas plataformas. Estas aplicações continuarão a estar disponíveis para transferência através dos canais de lançamento existentes, tais como a Loja Microsoft. 

Quando estiverem no modo de suporte, estas aplicações receberão apenas atualizações de segurança críticas. Não haverá quaisquer atualizações ou funcionalidades adicionais para estas aplicações. Para obter novas funcionalidades, recomendamos que atualize os dispositivos para Windows 10 ou Windows 10 Mobile. 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloquear ações de copiar e colar entre perfis de trabalho e pessoais no Android for Work <!-- 1098994 -->   
Com esta versão, pode configurar o perfil de trabalho do Android for Work para bloquear as ações de copiar e colar entre aplicações pessoais e de trabalho. Pode encontrar esta nova definição no perfil **Restrições do dispositivo** da Plataforma **Android for Work** em **Definições do perfil de trabalho**.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Novo comportamentos para a aplicação Portal da Empresa para Android com perfis de trabalho <!---1485783--->
Quando inscreve um dispositivo Android for Work num perfil de trabalho, é a aplicação Portal da Empresa no perfil de trabalho que executa as tarefas de gestão no dispositivo. Se estiver a utilizar uma aplicação ativada para MAM no perfil pessoal, a aplicação Portal da Empresa para Android já não terá qualquer utilidade. Para melhorar a experiência do perfil de trabalho, o Intune ocultará automaticamente a aplicação Portal da Empresa depois de inscrever com sucesso o perfil de trabalho.

A aplicação Portal da Empresa para Android pode ser ativada em qualquer altura no perfil pessoal. para tal, navegue para o [Portal da Empresa na Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e toque em **Ativar**.

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Intune MAM e suplementos do Outlook para Android <!-- 1450688 -->
Dentro de poucas semanas, a equipa do Office irá anunciar suplementos para o Outlook para Android. Este conjunto de funcionalidades já existe no Outlook para Windows, iOS, Web e Mac. Uma vez que os suplementos são geridos através do Exchange, os utilizadores serão capazes de copiar e partilhar dados e mensagens no Outlook e em aplicações de suplementos não geridas, exceto se os suplementos forem desativados pelo administrador do Exchange. 

Para gerir as permissões de acesso do utilizador aos suplementos, colabore com o administrador do Exchange para confirmar que as políticas de proteção de dados MAM se aplicam aos suplementos.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se as políticas do Exchange já estiverem definidas para o sideload ou a instalação de suplementos, não precisa de ler mais nada. As políticas de MAM serão aplicadas de acordo com o esperado. Se, no entanto, tiver definido políticas de MAM para restringir as operações de cortar, copiar e colar no Outlook para Android e não tiver definido a política de suplementos no Exchange, saiba que, por predefinição, os utilizadores conseguirão instalar os suplementos no Outlook. Estes suplementos podem aceder ao corpo da mensagem, ao assunto e a outras propriedades da mensagem. Pode desativar a capacidade do utilizador final em instalar suplementos. Para tal, peça ao Administrador do Exchange para remover as funções “As Minhas Aplicações do Marketplace” e “As Minhas Aplicações Personalizadas”. Para obter mais detalhes, veja a ligação de informações adicionais partilhada abaixo.

Tenha em atenção que a alteração da definição no Exchange será aplicada ao Outlook para Windows, iOS, Web, Mac e dispositivos móveis. 

#### <a name="what-do-i-need-to-do"></a>O que preciso fazer?
Reveja hoje as suas políticas do Exchange. Informe o departamento de TI e a equipa de suporte técnico. Contacte a nossa equipa de suporte com dúvidas ou preocupações específicas. 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados do Armazém de Dados do Intune <!-- 1187917 -->
Poderá criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado.


<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--"></a>Ações de não conformidade <!--730266-->     
*As ações de não conformidade* são uma nova funcionalidade de políticas de conformidade que lhe permite tomar medidas em dispositivos que não estejam em conformidade. Pode especificar uma ou múltiplas ações e o período de tempo em que devem ocorrer. Por exemplo, pode informar os utilizadores acerca dos dispositivos não conformes, imediatamente depois de estes se tornarem não conformes, por e-mail ou pode impedir os dispositivos não conformes de acederem aos recursos empresariais após um período de tolerância de 3 dias através do Acesso Condicional.

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

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Nova ligação da IU da política de acesso condicional do Azure AD do Intune <!-- 1016201 -->
Os administradores de TI podem definir políticas condicionais com base nas aplicações através da nova IU da política de acesso condicional na carga de trabalho do Azure AD. Por enquanto, as políticas de acesso condicional com base nas aplicações presentes na secção Proteção de Aplicações do Intune no Azure permanecem no local e são impostas lado a lado. Também haverá uma ligação útil para a nova IU da política de acesso condicional no Azure AD, a partir da carga de trabalho do Intune.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Suporte de elevada disponibilidade do conector do Exchange no local <!-- 676614 -->   
Pode ter múltiplas funções de Servidor de Acesso de Cliente (CAS) para o conector do Exchange no local. Por exemplo, se o CAS principal falhar, o conector do Exchange receberá uma consulta para reverter para outros CASs. Esta funcionalidade garante que o serviço não é interrompido.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Pacote de gestão do System Center Operations Manager para o conector do Exchange <!-- 885457 -->   
O pacote de gestão do System Center Operations Manager para o conector do Exchange estará disponível para ajudá-lo a analisar os registos do conector do Exchange. Esta pacote de gestão proporciona formas diferentes de monitorizar o Intune quando precisar de resolver problemas.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fim do suporte para iOS 8.0 <!---1164477--->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações.  

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fim do suporte para Android 4.3 e anterior <!---1171127, 1326920 --->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Os dispositivos que não forem atualizados antes do início de outubro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Lembrete de Suporte da Plataforma: o suporte base do Windows Phone 8.1 irá terminar a 11 de julho de 2017 <!-- 1327781 -->  
A 11 de julho de 2017, será o fim do suporte base da plataforma do Windows Phone 8.1. O suporte de PCs com Windows 8.1 não será afetado.

Não existe impacto imediato nos dispositivos Windows Phone 8.1 que sejam geridos pelo serviço do Intune. Os dispositivos inscritos continuam a funcionar e todas as políticas, configurações e aplicações continuarão a funcionar conforme esperado. Tenha em atenção que não existem melhorias para a plataforma do Windows Phone 8.1 no Serviço do Intune e para a aplicação Portal da Empresa do Windows Phone 8.1.

Recomendamos que atualize os dispositivos Windows Phone 8.1 elegíveis para o Windows 10 Mobile quando for possível. 





## <a name="intune-apps"></a>Aplicações do Intune
### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Ação de atualizar adicionada à aplicação Portal da Empresa para Windows 10 <!--1132468-->
A aplicação Portal da Empresa para Windows 10 permitirá aos utilizadores atualizar os dados na aplicação, ao pedir para atualizar ou, em ambientes de trabalho, ao premir F5.


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição. <!-- 1334712 -->
As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android podem ser instaladas sem qualquer pedido de inscrição.

### <a name="ios-company-portal-display-large-icons----1454593---"></a>O Portal da Empresa para iOS apresenta ícones grandes <!-- 1454593 -->
Estamos a corrigir um problema conhecido sobre a forma como Portal da Empresa para iOS apresenta os ícones no mosaico da aplicação. Se carregar ícones da aplicação de 120 x 120 pixels ou superior, serão agora apresentados no [site do Portal da Empresa] (https://portal.manage.microsoft.com) e nas páginas das aplicações do Portal da Empresa para iOS com o tamanho máximo do mosaico da aplicação.

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android------1396349---"></a>Linguagem de compreensão mais fácil na aplicação do Portal da Empresa para Android <!---1396349--->    
O texto do processo de inscrição da aplicação Portal da Empresa para Android foi simplificado para facilitar a inscrição dos utilizadores finais. 


<!-- the following are present prior to 1709 -->


### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Suporte do Intune Managed Browser para iOS e Android <!---1374196--->
A partir de outubro de 2017, a aplicação Intune Managed Browser no Android irá suportar apenas dispositivos a executar o Android 4.4 e posterior. A aplicação Intune Managed Browser no iOS irá suportar apenas dispositivos a executar o iOS 9.0 e posterior. As versões anteriores do Android e iOS poderão continuar a utilizar o Managed Browser, mas não poderão instalar novas versões da aplicação e poderão não conseguir aceder a todas as funcionalidades da aplicação. Aconselhamos que atualize estes dispositivos para uma versão do sistema operativo suportada.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição <!---1169910--->  
Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensagem de erro melhorada para quando um utilizador atinge o número máximo de dispositivos que é permitido inscrever <!-- 1270370 -->
Em vez de uma mensagem de erro genérica, os utilizadores veem uma mensagem de erro acionável amigável: "Inscreveu o número máximo de dispositivos permitidos pela sua equipa de TI. Remova um dispositivo inscrito ou peça ajuda ao seu administrador de TI."

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informe os utilizadores finais acerca das informações do dispositivo que podem ser vistas para iOS <!--739894-->
Iremos adicionar o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para iOS. Isto permite que os utilizadores obtenham mais informações sobre privacidade diretamente a partir desta página, através da documentação de utilizador final do Intune. Também poderão localizar estas informações no ecrã Acerca de.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>As páginas de detalhes das aplicações apresentam novas informações em dispositivos Android <!--1287476-->
A página de detalhes das aplicações da aplicação Portal da Empresa para Android apresentará as categorias da aplicação que o administrador de TI definir para a respetiva aplicação.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>As caixas de diálogo da Gestão de Aplicações Móveis (MAM) do Intune têm agora uma interface moderna <!-- 1199015 -->
As caixas de diálogo da Gestão de Aplicações Móveis (MAM) do Intune foram atualizadas para um aspeto e funcionalidade modernos. O estilo de funcionamento das caixas de diálogo permanece igual.

Em dispositivos Android modernos, as caixas de diálogo de erros ou notificações apresentadas pelo Intune terão um aspeto e funcionalidade atualizados.



## <a name="notices"></a>Avisos
### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->   
A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Planear a alteração: o Intune vai alterar a experiência do Portal de Parceiros do Intune <!-- 1050016 -->
A partir da atualização de serviço que se realizará em meados de maio de 2017, iremos remover a página Parceiro do Intune de manage.microsoft.com.  

Se for um administrador parceiro, já não poderá ver e agir em nome dos clientes a partir da página Parceiro do Intune. Em vez disso, terá de iniciar sessão num dos dois outros portais de parceiro da Microsoft.

Poderá iniciar sessão nas contas de cliente que gere a partir do [Centro de Parceiros da Microsoft](https://partnercenter.microsoft.com/) e do [Centro de Administração do Microsoft Office 365 para Parceiros](https://portal.office.com/). De futuro, utilize um destes sites para gerir os seus clientes.



### <a name="see-also"></a>Veja também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
