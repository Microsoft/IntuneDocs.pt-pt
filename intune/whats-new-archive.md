---
title: Novidades nos meses anteriores do Microsoft Intune
titleSuffix: Intune on Azure
description: "Veja os anúncios mais antigos na página Novidades do Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 06/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf2322a4009310e5dd561693ea6b3cdb97ab6e28
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novidades do Microsoft Intune – meses anteriores

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Suporte para gerir a aplicação Sala de Aula da Apple

Já pode gerir a aplicação Sala de Aula do iOS nos dispositivos iPad. Configure a aplicação Sala de Aula no iPad dos professores com os dados corretos da turma e dos estudantes e, em seguida, configure os iPads dos estudantes registados numa turma para que possa controlá-los através da aplicação.
Para obter detalhes, veja [Configure iOS education settings (Configurar as definições de educação do iOS)](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Suporte para opções de configuração gerida para aplicações Android <!-- 621621 -->

As aplicações Android na Play Store que suportam opções de configuração gerida podem agora ser configuradas pelo Intune.  Esta funcionalidade permite às TI ver a lista de valores de configuração suportados por uma aplicação e disponibiliza IU de primeira classe assistida para lhes permitir configurar os valores.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nova política para PINs complexos em Android <!-- 722069 -->

Pode agora definir um tipo de [palavra-passe](device-restrictions-android.md#password) obrigatório de Numérica complexa num perfil de dispositivo Android para dispositivos com o Android 5.0 e superior.  Utilize esta definição para impedir que os utilizadores dos dispositivos criem um PIN que contenha números repetidos ou consecutivos, como 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Suporte adicional para dispositivos Android for Work

- **Gerir definições de palavra-passe e perfil de trabalho** <!-- 612808 -->

  Esta nova política de restrição para dispositivos Android for Work permite-lhe agora gerir as definições de palavra-passe e perfil de trabalho em dispositivos Android for Work geridos por si.

- **Permitir a partilha de dados entre perfis de trabalho e pessoais** <!-- 1045102 -->

Este perfil de restrição para dispositivos Android for Work tem agora novas opções para o ajudar a configurar a partilha de dados entre perfis de trabalho e perfis pessoais.

- **Restringir as ações de copiar e colar entre perfis de trabalho e pessoais** <!-- 1046094 -->

  Um novo perfil de dispositivo personalizado para dispositivos Android for Work permite-lhe agora decidir se as ações de copiar e colar entre aplicações de trabalho e pessoais são permitidas.

Para obter mais informações, veja [Restrições de dispositivos para Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Atribuir aplicações LOB a dispositivos iOS e Android <!-- 1057568 -->

Agora pode atribuir aplicações de linha de negócio (LOB) para [iOS](lob-apps-ios.md) (ficheiros .ipa) e [Android](lob-apps-android.md) (ficheiros .apk) a utilizadores ou dispositivos.

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Novas políticas de dispositivos para iOS <!-- 723774, 723815, 723826, 723830 -->

- **Aplicações no Ecrã principal** – controla as aplicações que os utilizadores veem no [Ecrã principal do dispositivo iOS](home-screen-settings-ios.md). Esta política altera o esquema do ecrã principal, mas não implementa aplicações.

- **Ligações a dispositivos AirPrint** – controla os [dispositivos AirPrint](air-print-settings-ios-macos.md) (impressoras de rede) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Ligações a dispositivos AirPlay** – controla os [dispositivos AirPlay](airplay-settings-ios.md) (como a Apple TV) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Mensagem de ecrã de bloqueio personalizada** – configura uma mensagem personalizada que os utilizadores verão no ecrã de bloqueio do dispositivo iOS, que substitui a mensagem de ecrã de bloqueio predefinida. Para mais informações, veja [Ativar o modo perdido em dispositivos iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir notificações push para aplicações para iOS <!-- 723767 -->

Num perfil de restrição para dispositivos do Intune, pode agora configurar as seguintes [definições de notificação](app-notification-settings-ios.md) para dispositivos iOS:

- Ativar ou desativar notificações por completo para uma aplicação específica.
- Ativar ou desativar notificações para uma aplicação específica na central de notificações.
- Especificar o tipo de alerta: **Nenhum**, **Faixa** ou **Aviso Modal**.
- Especificar se são permitidos emblemas para esta aplicação.
- Especificar se são permitidos sons de notificação.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar que aplicações iOS são executadas em modo de aplicação única autónomo <!-- 737837 -->

Pode agora utilizar um perfil de dispositivo do Intune para configurar os dispositivos iOS para executar aplicações específicas no [modo de aplicação única autónomo](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado para que possa apenas executar essa aplicação. Um exemplo desta funcionalidade é quando configura uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações da aplicação forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar domínios de confiança para navegação Web e de e-mail em dispositivos iOS <!-- 723765 -->

Para um perfil de restrição para dispositivos iOS, pode agora configurar as seguintes [definições de domínio](device-restrictions-ios.md#domains):

- **Domínios de e-mail não marcados** – e-mails que o utilizador envia ou recebe que não correspondam aos domínios que especifica aqui serão marcados como não sendo de confiança.

- **Domínios Web geridos** – os documentos transferidos a partir dos URLs que especificar aqui serão considerados como geridos (apenas para Safari).  

- **Domínios de preenchimento automático da palavra-passe do Safari** – os utilizadores podem guardar palavras-passe no Safari apenas de URLs que correspondam aos padrões que especificar aqui. Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado e não configurado para múltiplos utilizadores. (iOS 9.3 e superior)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicações do VPP disponíveis no Portal da Empresa para iOS <!-- 748782 -->

Pode agora atribuir aos utilizadores finais aplicações iOS compradas em grandes volumes (VPP) como instalações no modo **Disponível**. Os utilizadores finais precisarão de uma conta da Apple Store para instalar a aplicação.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar eBooks a partir da Apple VPP Store <!-- 800878 -->

Agora pode [sincronizar livros](vpp-apps-ios.md) que tenha comprado na loja do Apple Volume Purchase Program com o Intune e atribuí-los aos utilizadores.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestão de vários utilizadores para dispositivos Samsung KNOX Standard <!-- 971988 -->

Os dispositivos que executem o Samsung KNOX Standard agora suportam a [gestão de vários utilizadores](android-enroll.md) do Intune. Isto significa que os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure Active Directory e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não.  Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Definições de restrição adicionais para dispositivos Windows <!-- 818566 -->

Adicionamos suporte para mais [definições de restrição para dispositivos Windows](device-restrictions-windows-10.md), tais como suporte adicional para o browser Edge, personalização do ecrã de bloqueio do dispositivo, personalizações do menu Iniciar, imagens de fundo definidas por pesquisas do Destaque do Windows e definição de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Suporte para múltiplos utilizadores da Atualização para Criativos do Windows 10 <!-- 822547 -->

Adicionamos suporte para a [gestão de vários utilizadores](windows-enroll.md) para dispositivos a executar a Atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory. Tal significa que, quando outros utilizadores padrão iniciarem sessão no dispositivo com as credenciais do Azure AD, receberão as aplicações e as políticas atribuídas aos seus nomes de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como instalar aplicações.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para PCs com Windows 10 <!-- 1004830 -->

Está agora disponível uma [ação de dispositivo Fresh Start](device-fresh-start.md) para PCs com Windows 10.  Ao executar esta ação, as aplicações instaladas no PC são removidas e o PC é automaticamente atualizado para a versão mais recente do Windows. Esta ação pode ajudar a remover aplicações OEM que vêm frequentemente pré-instaladas num PC novo. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Caminhos de atualização do Windows 10 adicionais<!-- 903672 -->

Agora, pode criar uma [política de atualização de edição para atualizar os dispositivos](edition-upgrade-configure-windows-10.md) para as seguintes edições do Windows 10 adicionais:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscrever dispositivos Windows 10 em volume <!-- 747607 -->

Agora, pode juntar-se a um grande número de dispositivos que executam a atualização para Criativos do Windows 10 para o Azure Active Directory e o Intune com o Windows Configuration Designer (WCD). Para ativar a [inscrição na MDM em massa](windows-bulk-enroll.md) para o seu inquilino do Azure AD, crie um pacote de aprovisionamento que associe dispositivos ao seu inquilino do Azure AD através do Windows Configuration Designer e aplique o pacote aos dispositivos pertencentes à empresa que pretende inscrever e gerir em massa. Assim que o pacote for aplicado aos dispositivos, estes são associados ao Azure AD, inscritos no Intune e estarão prontos para os seus utilizadores do Azure AD iniciarem sessão.  Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as políticas atribuídas e as aplicações necessárias. Os cenários Self-service e Portal da Empresa não são atualmente suportados.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Novas definições de MAM para PIN e localizações de armazenamento gerido <!-- 581122, 736644 -->

Estão agora disponíveis duas novas definições de aplicações para o ajudar em cenários de MAM (gestão de aplicações móveis):

- **Desativar o PIN da aplicação quando o PIN do dispositivo for gerido** – deteta se está presente um PIN no dispositivo inscrito e, caso esteja, ignora o PIN da aplicação acionado pelas políticas de proteção da aplicação. Esta definição permitirá reduzir o número de pedidos de PIN quando os utilizadores abrirem uma aplicação com MAM ativada num dispositivo inscrito. Esta funcionalidade está disponível para Android e iOS.

- **Selecionar em que serviços de armazenamento podem ser guardados os dados empresariais** – permite-lhe especificar as localizações de armazenamento onde podem ser guardados dados empresariais. Os utilizadores podem guardar nos serviços de localização de armazenamento selecionados, o que significa que todos os que não estiverem listados serão bloqueados.

  Lista dos serviços de localização de armazenamento:

  - OneDrive para Empresas
  - SharePoint Online
  - Armazenamento local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portal de resolução de problemas de suporte técnico <!-- 907448 -->

O novo [portal de resolução de problemas](help-desk-operators.md) permite aos operadores de suporte técnico e aos administradores do Intune verem os utilizadores e os seus dispositivos e executar tarefas para resolver problemas técnicos do Intune.

## <a name="march-2017"></a>Março de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Suporte para o Modo Perdido no iOS <!--431695-->

Para os dispositivos iOS 9.3 e posteriores, o Intune adicionou o suporte para o **Modo Perdido**. Agora, pode bloquear um dispositivo para impedir toda a utilização e apresentar um número de telefone de contacto e uma mensagem no ecrã de bloqueio do dispositivo.

O utilizador final só poderá desbloquear o dispositivo quando um administrador desativar o Modo Perdido. Quando o Modo Perdido está ativado, pode utilizar a ação **Localizar dispositivo** para apresentar a localização geográfica do dispositivo num mapa na consola do Intune.

O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado.

Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](device-management.md)?

### <a name="improvements-to-device-actions-report---677150--"></a>Melhorias ao relatório de Ações de Dispositivos<!--677150-->

Melhoramos o relatório de Ações de Dispositivos para um melhor desempenho. Além disso, agora pode filtrar o relatório por estado. Por exemplo, pode filtrar o relatório para mostrar apenas as ações de dispositivo que foram concluídas.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->

Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Atribuir aplicações de LOB a utilizadores com dispositivos não inscritos <!--748823-->

Agora pode atribuir aplicações de linha de negócio da loja aos utilizadores, quer os respetivos dispositivos estejam ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, o utilizador terá de aceder ao site do Portal da Empresa para o instalar, em vez da aplicação Portal da Empresa.

### <a name="new-compliance-reports---846671--"></a>Novos relatórios de conformidade <!--846671-->

Tem agora relatórios de conformidade que lhe dão a postura de conformidade dos dispositivos na sua empresa e lhe permitem rapidamente resolver problemas relacionados com a conformidade encontrados pelos utilizadores. Pode ver informações sobre o

- Estado de conformidade geral dos dispositivos
- Estado de conformidade de uma definição individual
- Estado de conformidade de uma política individual

Também pode utilizar estes relatórios para desagregar um dispositivo individual e ver as definições e políticas específicas que afetam esse dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acesso direto aos cenários de inscrição da Apple <!--951869-->

Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Intune clássico. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.


## <a name="february-2017"></a>Fevereiro de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747600, 795782-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.

* A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.  
* Existe uma opção adicional para bloquear a inscrição de dispositivos pessoais apenas para iOS e Android.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas as ações em dispositivos geridos <!--677150-->
Um novo relatório __Ações de Dispositivos__ mostra quem efetuou ações remotas como a reposição de dados de fábrica em dispositivos e o estado dessas ações. Veja [O que é a gestão de dispositivos?](device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas <!--664691-->
Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="custom-app-categories---748805--"></a>Categorias de aplicações personalizadas <!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="display-device-categories---814654--"></a>Mostrar categorias dos dispositivos <!--814654-->
Agora pode ver a categoria do dispositivo como uma coluna na lista de dispositivos. Também pode editar a categoria a partir da secção de propriedades do painel de propriedades do dispositivo. Veja [Como adicionar uma aplicação ao Intune](apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurar definições do Windows Update para Empresas <!--776716-->

O Windows como um Serviço é a nova forma de disponibilizar atualizações para o Windows 10. A partir do Windows 10, todas as novas Atualizações de Funcionalidades e Atualizações de Qualidade irão conter o conteúdo de todas as atualizações anteriores. Tal significa que, desde que instale a atualização mais recente, sabe que os dispositivos Windows 10 estão completamente atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações para não ter de aprovar atualizações individuais para grupos de dispositivos. Pode continuar a gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações e o Windows Update irá garantir que as atualizações são instaladas no momento certo. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem ao Windows Update diretamente para obterem as atualizações. Utilize o Intune para configurar e gerir **anéis de atualização do Windows 10**. Um anel de atualização contém um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Para obter detalhes, veja [Configure Windows Update for Business settings (Configurar definições do Windows Update para Empresas)](windows-update-for-business-configure.md).

## <a name="january-2017"></a>Janeiro de 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Atribuir aplicações de linha de negócio se os dispositivos estiverem ou não inscritos <!--748823-->
Pode agora atribuir aplicações de linha de negócio a partir da loja aos utilizadores se os respetivos dispositivos estiverem ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, este tem de aceder ao site do Portal da Empresa para instalá-lo, em vez da aplicação Portal da Empresa. Veja [O que é a gestão de aplicações](app-management.md).

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver o problema no qual os dispositivos iOS estão inativos ou a consola de administração não consegue comunicar com os mesmos
Quando os dispositivos dos utilizadores perdem o contacto com o Intune, pode dar-lhes novos passos de resolução de problemas que os ajudem a recuperar o acesso aos recursos da empresa. Consulte [Os dispositivos estão inativos ou a consola de administração não consegue comunicar com os mesmos](enrollment-troubleshoot.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Dezembro de 2016 (versão inicial)

### <a name="telecom-expense-management-integration-in-azure-portal--747605--"></a>Integração da gestão de despesas de telecomunicações no portal do Azure<!--747605-->
Estamos agora a começar a pré-visualizar a integração com os serviços de gestão de despesas de telecomunicações (TEM) de terceiros no portal do Azure. Pode utilizar o Intune para impor limites de utilização de dados nacionais e itinerantes. Estamos a começar essas integrações com [Saaswedo](http://www.saaswedo.com). Para ativar esta funcionalidade no seu inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune-classic/troubleshoot/get-support).

- Implementar e gerir aplicações de uma loja para dispositivos iOS, Android e Windows
- Implementar e gerir aplicações de uma linha de negócio (LOB) para dispositivos iOS, Android e Windows
- Implementar e gerir aplicações compradas em volume para dispositivos iOS e Windows
- Implementar e gerir aplicações Web para dispositivos Android, iOS e Windows
- Perfis de configuração de aplicações geridas iOS
- Configurar políticas de proteção de aplicações e implementar aplicações de linha de negócio em dispositivos que não estão inscritos com o Intune
- Perfis de VPN, VPN por aplicação, Wi-Fi, e-mail e perfis de certificados
- Políticas de conformidade
- Acesso condicional para o Azure AD
- Acesso condicional para o Exchange no Local
- Inscrição de dispositivos
- Controlo de acesso baseado em funções

## <a name="deprecated-features-in-the-azure-portal"></a>Funcionalidades preteridas no portal do Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Suporte para revisão de linha por linha de identificadores de hardware
O portal do Azure não suporta a revisão de linha por linha de identificadores de hardware para números IMEI e números de série da Apple. Na consola clássica do Intune, pode importar os detalhes de um ficheiro valores separados por vírgulas (.csv) e substituir os detalhes existentes de identificadores de hardware individuais. O portal do Azure oferece uma opção única e simplificada que substitui automaticamente os detalhes de todos os identificadores de hardware ou ignora os detalhes novos para os identificadores existentes.

#### <a name="how-this-affects-you"></a>De que forma o afeta
No portal do Azure, não poderá decidir, linha por linha, os dispositivos de Identidade Internacional do Equipamento Móvel (IMEI) a atualizar. A consola clássica do Intune continuará a suportar esta funcionalidade.

#### <a name="how-to-get-ready-for-this-change"></a>Como se preparar para esta alteração
Estamos a disponibilizar estas informações com antecedência para que, se for afetado, possa avisar os seus administradores de suporte em relação a esta alteração. Esta alteração vai coincidir com a transição para o portal do Azure, antecipada para o primeiro semestre de 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Suporte para perfis predefinidos de Inscrição de Dispositivos da Empresa no DEP da Apple
O portal do Azure não suporta o perfil “predefinido” de Inscrição de Dispositivos de Empresa para números de série de dispositivos do Programa de Inscrição de Dispositivos (DEP) da Apple. Esta funcionalidade, disponível na consola clássica do Intune, vai ser descontinuada para evitar atribuições inadvertidas de perfis. No portal do Azure, os números de série sincronizados a partir de uma conta de DEP da Apple não terão inicialmente nenhum perfil de Inscrição de Dispositivos de Empresa atribuído.

#### <a name="how-this-affects-you"></a>De que forma o afeta
No portal do Azure, não poderá definir uma política de perfil predefinida em todos os dispositivos da Apple. A consola clássica do Intune continuará a suportar esta funcionalidade.

#### <a name="how-to-get-ready-for-this-change"></a>Como se preparar para esta alteração
Estamos a disponibilizar estas informações com antecedência para que, se for afetado, possa avisar os seus administradores de suporte em relação a esta alteração. Esta situação vai coincidir com a transição para o portal do Azure, antecipada para o primeiro semestre de 2017.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
