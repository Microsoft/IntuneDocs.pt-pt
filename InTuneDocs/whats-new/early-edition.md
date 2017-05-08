---
title: "Edição antecipada | Documentos da Microsoft"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: d7f25657fc7cfb9298809f76f198810718e58c39
ms.lasthandoff: 04/27/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>A edição antecipada do Microsoft Intune – abril de 2017

A **Edição Antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
> As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas funcionalidades

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Estado da instalação de aplicações melhorado para a aplicação Portal da Empresa do Windows 10 <!--676495-->

A aplicação Portal da Empresa do Windows 10 irá apresentar agora uma barra de progresso da instalação para todas as instalações de aplicações modernas iniciadas a partir do Portal da Empresa. Pode ver as novas mensagens de estado da aplicação Portal da Empresa para o Windows 10 na [página Novidades na IU da Aplicação Intune](whats-new-in-intune-app-ui.md).

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Mensagem de estado melhorada na aplicação Portal da Empresa para iOS <!--744866-->

Serão apresentadas novas mensagens mais específicas na aplicação Portal da Empresa para iOS para fornecer informações mais acessíveis sobre as ocorrências nos dispositivos. Estes erros eram anteriormente incluídos numa mensagem de erro geral que informava "O Portal da Empresa Está Temporariamente Indisponível". Além disso, se um utilizador iniciar o Portal da Empresa em iOS sem estar ligado à Internet, verá uma barra de estado persistente na home page a informar "Sem Ligação à Internet."

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>My Apps disponível para o Managed Browser <!--822308, 822303-->

O Microsoft My Apps agora tem melhor suporte no Managed Browser. Os utilizadores do Managed Browser que não forem geridos poderão aceder diretamente ao serviço My Apps e às aplicações SaaS aprovisionadas pelo administrador. Os utilizadores geridos através do Intune poderão continuar a aceder ao My Apps a partir do marcador incorporado no Managed Browser.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Novos ícones para o Managed Browser e o Portal da Empresa <!--918433, 918431-->

O Managed Browser receberá ícones atualizados nas versões para Android e iOS da aplicação. O novo ícone irá incluir o emblema do Intune atualizado para o tornar mais consistente com outras aplicações no Enterprise Mobility + Security (EM+S). Pode ver o novo ícone do Managed Browser na [página Novidades na IU da aplicação Intune](whats-new-in-intune-app-ui.md).

O Portal da Empresa também receberá ícones atualizados para as versões para Android, iOS e Windows da aplicação para melhorar a consistência com outras aplicações no EM+S. Estes ícones serão lançados gradualmente nas plataformas a partir de abril até finais de maio.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Suporte de início de sessão único a partir do Portal da Empresa para iOS para o Outlook para iOS <!--834012-->

Os utilizadores já não precisam de iniciar sessão na aplicação Outlook se já tiverem sessão iniciada no Portal da Empresa para iOS no mesmo dispositivo com a mesma conta. Quando os utilizadores iniciarem o Outlook, poderão selecionar a conta e iniciar sessão automaticamente. Também estamos a trabalhar no sentido de adicionar esta funcionalidade a outras aplicações da Microsoft.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progresso de início de sessão no Portal da Empresa para Android <!--953374-->

Uma atualização à aplicação Portal da Empresa para Android mostra um indicador de progresso de início de sessão quando o utilizador inicia ou retoma a aplicação. O indicador mostra novos estados de progresso, a começar por "A ligar...", "A iniciar sessão..." e depois "A verificar os requisitos de segurança..." antes de o utilizador poder aceder à aplicação. Pode ver os novos ecrãs para a aplicação Portal da Empresa para Android na [página Novidades na IU da Aplicação Intune](whats-new-in-intune-app-ui.md).


## <a name="notices"></a>Avisos

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>A Apple passará a exigir atualizações para a Segurança de Transporte de Aplicações <!--748318-->

A partir da primavera de 2017, a Apple anunciou que irá impor requisitos específicos para a Segurança de Transporte de Aplicações (ATS). A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune que utilizam as aplicações do Portal da Empresa para iOS. Consulte o nosso [blogue de suporte do Intune](https://aka.ms/compportalats) para obter mais detalhes.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->

Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal de pré-visualização do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Novidades futuras para Appx no Intune no Azure <!-- 1000270 -->

Como parte da migração do Intune para o Azure, estamos a efetuar três alterações a appx:

1. Adicionar um novo tipo de aplicação appx na consola clássica do Intune que só pode ser implementada em dispositivos inscritos em MDM.
2. Alterar o tipo de aplicação appx existente para apenas ser direcionada para PCs geridos através do agente do Intune para PC.
3. Converter todas as appxs existentes em appxs de MDM com a migração.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?

Não irá afetar as suas implementações existentes em dispositivos geridos através do agente do Intune para PC. No entanto, após a migração, não poderá implementar appxs migradas em novos dispositivos geridos através do agente do Intune para PC que não tenham sido abrangidas anteriormente.

#### <a name="what-action-do-i-need-to-take"></a>Que medidas tenho de tomar

Após a migração, terá de voltar a carregar a appx como uma appx para PC, se quiser efetuar novas implementações em PC. Para saber mais, veja [Appx changes in Intune on Azure (Alterações a appx no Intune no Azure)](https://aka.ms/appxchange) no blogue da Equipa de Suporte do Intune.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure <!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Suporte para opções de configuração gerida para aplicações Android <!-- 621621 -->

As aplicações Android na Play Store que suportam opções de configuração gerida podem ser configuradas pelo Intune.  Esta funcionalidade permite às TI ver a lista de valores de configuração suportados por uma aplicação e disponibiliza IU de primeira classe assistida para lhes permitir configurar os valores.

### <a name="remote-assistance-for-android-devices----675418---"></a>Assistência remota para dispositivos Android <!-- 675418 -->

O Intune irá utilizar o software [TeamViewer](https://www.teamviewer.com), adquirido separadamente, para lhe permitir disponibilizar assistência remota aos seus utilizadores com dispositivos Android.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nova política para PINs complexos em Android <!-- 722069 -->

Pode definir um tipo de palavra-passe obrigatório de complexo Numérico num perfil de dispositivo Android para dispositivos com o Android 5.0 e superior.  Utilize esta definição para impedir que os utilizadores dos dispositivos criem um PIN que contenha números repetidos ou consecutivos, como 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Suporte adicional para dispositivos Android for Work

- **Gerir definições de palavra-passe e perfil de trabalho** <!-- 612808 -->

  Adicionámos uma nova política de restrição para dispositivos Android for Work que lhe permite gerir as definições de palavra-passe e perfil de trabalho em dispositivos Android for Work geridos por si.

- **Permitir a partilha de dados entre perfis de trabalho e pessoais** <!-- 1045102 -->

  Atualizámos a definição **Partilha de dados entre os perfis de trabalho e pessoais** num perfil de restrição para dispositivos Android for Work com novas opções para o ajudar a configurar a partilha de dados entre perfis de trabalho e pessoais.

- **Restringir as ações de copiar e colar entre perfis de trabalho e pessoais** <!-- 1046094 -->

  Ao gerir dispositivos Android for Work com o Intune, as ações de copiar e colar entre aplicações de trabalho e pessoais são permitidas. Agora adicionámos um perfil de dispositivo personalizado para dispositivos Android for Work que lhe permite decidir se as ações de copiar e colar entre aplicações de trabalho e pessoais são permitidas.

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Atribuir aplicações LOB a dispositivos iOS e Android <!-- 1057568 -->

Pode atribuir aplicações linha de negócio para iOS (ficheiros .ipa) e Android (ficheiros .apk) a utilizadores ou dispositivos.

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>Novas políticas para dispositivos iOS <!-- 723774, 723815, 723826, 723830, 723832 -->

- **Aplicações no ecrã principal** – pode utilizar uma política de dispositivo para controlar que aplicações os utilizadores veem no ecrã principal do dispositivo iOS. Esta política altera o esquema do ecrã principal mas não implementa aplicações não instaladas que tenha especificado.

- **Ligações a dispositivos AirPrint** – pode utilizar uma política de dispositivo do Intune para controlar a que dispositivos AirPrint (impressoras em rede) os utilizadores finais do dispositivo iOS se podem ligar.

- **Ligações a dispositivos AirPlay** – pode utilizar uma política de dispositivo do Intune para controlar a que dispositivos AirPlay (por exemplo, a Apple TV) os utilizadores finais do dispositivo iOS se podem ligar.

- **Mensagem de ecrã de bloqueio personalizada** – pode configurar uma mensagem personalizada que os utilizadores verão no ecrã de bloqueio do dispositivo iOS, que substitui a mensagem de ecrã de bloqueio predefinida.

- **Filtro de conteúdo Web** – pode controlar que sites os utilizadores dos dispositivos iOS podem visitar através de um dos dois métodos:

  - Adicionar URLs permitidos e bloqueados através do filtro de conteúdo Web incorporado da Apple.
  - Permitir o acesso apenas a sites específicos no browser Safari. Serão criados marcadores no Safari para cada site que especificar.


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir notificações push para aplicações para iOS <!-- 723767 -->

Num perfil de restrição para dispositivos do Intune, pode configurar as seguintes definições de notificação para dispositivos iOS:

- Ativar ou desativar notificações por completo para uma aplicação específica.
- Ativar ou desativar notificações para uma aplicação específica na central de notificações.
- Especificar o tipo de alerta: **Nenhum**, **Faixa** ou **Aviso Modal**.
- Especificar se são permitidos emblemas para esta aplicação.
- Especificar se são permitidos sons de notificação.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar que aplicações iOS são executadas em modo de aplicação única autónomo <!-- 737837 -->

Pode utilizar um perfil de dispositivo do Intune para configurar os dispositivos iOS para executar aplicações específicas em modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado para que possa apenas executar essa aplicação. Um exemplo desta funcionalidade é quando configura uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações da aplicação forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar domínios de confiança para navegação Web e de e-mail em dispositivos iOS <!-- 723765 -->

Para um perfil de restrição para dispositivos iOS, pode configurar as seguintes definições de domínio:

- **Domínios de e-mail não marcados** – e-mails que o utilizador envia ou recebe que não correspondam aos domínios que especifica aqui serão marcados como não sendo de confiança.

- **Domínios Web geridos** – os documentos transferidos a partir dos URLs que especificar aqui serão considerados como geridos (apenas para Safari).  

- **Domínios de preenchimento automático da palavra-passe do Safari** – os utilizadores podem guardar palavras-passe no Safari apenas de URLs que correspondam aos padrões que especificar aqui. Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado e não configurado para múltiplos utilizadores. (iOS 9.3 e superior)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicações do VPP disponíveis no Portal da Empresa para iOS <!-- 748782 -->

Pode atribuir aplicações iOS compradas em volume (VPP) como instalações em modo **Disponível** aos utilizadores finais. Os utilizadores finais precisarão de uma conta da Apple Store para instalar a aplicação.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar eBooks a partir da Apple VPP Store <!-- 800878 -->

Pode sincronizar eBooks que tenha comprado na loja do programa de compras em volume da Apple com o Intune e atribuí-los aos utilizadores.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestão de vários utilizadores para dispositivos Samsung KNOX Standard <!-- 971988 -->

Os dispositivos que executem o Samsung KNOX Standard agora suportam a gestão de vários utilizadores do Intune. Isto significa que os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure Active Directory e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não.  Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Definições de restrição adicionais para dispositivos Windows <!-- 818566 -->

Adicionámos suporte para mais definições de restrição para dispositivos Windows, tal como suporte adicional para o browser Edge, personalização do ecrã de bloqueio do dispositivo, personalizações do menu Iniciar, padrões de fundo definidos por pesquisas do Destaque do Windows e definição de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Suporte para múltiplos utilizadores da Atualização para Criativos do Windows 10 <!-- 822547 -->

Adicionámos suporte para a gestão de múltiplos utilizadores para dispositivos a executar a Atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory. Tal significa que quando outros utilizadores padrão iniciarem sessão no dispositivo com as credenciais do Azure AD, receberão as aplicações e as políticas atribuídas aos seus nomes de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como a instalação de aplicações.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para PCs com Windows 10 <!-- 1004830 -->

Neste lançamento, adicionámos uma ação de dispositivo Fresh Start para PCs com Windows 10.  Ao executar esta ação, as aplicações instaladas no PC são removidas e o PC é automaticamente atualizado para a versão mais recente do Windows. Esta ação pode ajudar a remover aplicações OEM que vêm frequentemente pré-instaladas num PC novo. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Caminhos de atualização do Windows 10 adicionais<!-- 903672 -->

Agora, pode criar uma política de atualização de edição para atualizar os dispositivos para as seguintes edições do Windows 10 adicionais:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscrever dispositivos Windows 10 em volume <!-- 747607 -->

Pode associar um grande número de dispositivos que executam a atualização para Criativos do Windows 10 ao Azure Active Directory e ao Intune com o Windows Configuration Designer (WCD). Para ativar a inscrição de MDM automática para o seu inquilino do Azure AD, crie um pacote de aprovisionamento que associe os dispositivos ao seu inquilino do Azure AD através do Windows Configuration Designer e aplique o pacote aos dispositivos pertencentes à empresa que pretende inscrever e gerir em massa. Assim que o pacote for aplicado aos dispositivos, estes são associados ao Azure AD, inscritos no Intune e estarão prontos para os seus utilizadores do Azure AD iniciarem sessão.  Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as políticas atribuídas e as aplicações necessárias. De momento, os cenários self-service e Portal da Empresa não são suportados.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>Novas definições de MAM para PIN e localizações de armazenamento gerido <!-- 58112, 736644 -->

Estão disponíveis duas novas definições de aplicações para o ajudar com cenários de MAM (gestão de aplicações móveis):

- **Desativar o PIN da aplicação quando o PIN do dispositivo for gerido** – deteta se está presente um PIN no dispositivo inscrito e, caso esteja, ignora o PIN da aplicação acionado pelas políticas de proteção da aplicação. Esta definição permitirá reduzir o número de pedidos de PIN quando os utilizadores abrirem uma aplicação com MAM ativada num dispositivo inscrito. Esta funcionalidade está disponível para Android e iOS.

- **Selecionar em que serviços de armazenamento podem ser guardados os dados empresariais** – permite-lhe especificar as localizações de armazenamento onde podem ser guardados dados empresariais. Os utilizadores podem guardar nos serviços de localização de armazenamento selecionados, o que significa que todos os que não estiverem listados serão bloqueados.

  Lista dos serviços de localização de armazenamento:

  - OneDrive para Empresas
  - SharePoint Online
  - Armazenamento local


### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.

