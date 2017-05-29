---
title: "Edição antecipada | Documentos da Microsoft"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 249a902e6e10f799dcff4e1c46da90cd62f2c125
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>Edição antecipada do Microsoft Intune – maio de 2017

A **Edição Antecipada** oferece uma lista de funcionalidades disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

> [!Note]
> As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Novas funcionalidades

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Suporte de início de sessão único a partir do Portal da Empresa para iOS para o Outlook para iOS <!--834012-->

Os utilizadores não terão mais de iniciar sessão na aplicação Outlook se já tiverem sessão iniciada no Portal da Empresa para iOS no mesmo dispositivo com a mesma conta. Quando os utilizadores iniciarem o Outlook, poderão selecionar a conta e iniciar sessão automaticamente. Também estamos a trabalhar no sentido de adicionar esta funcionalidade a outras aplicações da Microsoft.

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificação melhorada para PINs de arranque do Samsung KNOX <!--1087143-->

Quando os utilizadores finais têm de definir um PIN de arranque em dispositivos Samsung KNOX para ficarem em conformidade com a encriptação, a notificação apresentada aos utilizadores finais irá colocá-los no local exato na aplicação Definições quando toca na notificação.  Anteriormente, a notificação enviava o utilizador final para o ecrã de alteração da palavra-passe.

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>Promover a versão mais recente do Portal da Empresa para Android <!--1098661-->

Os utilizadores finais verão uma notificação na aplicação quando tiver sido lançada uma nova versão recomendada da aplicação do Portal da Empresa para Android no ecrã de Notificações da aplicação. Esta notificação informará os utilizadores que uma “atualização do Portal da Empresa está disponível”. Tocar na notificação abrirá uma página Web que mostra a lista de lojas de aplicações disponíveis onde pode transferir a versão atualizada. 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>Melhorias na sincronização da aplicação com a Atualização para Criativos do Windows 10 <!-- 676505 -->

O Portal da Empresa para Windows 10 iniciará automaticamente uma sincronização para pedidos de instalação de aplicações para dispositivos com a Atualização para Criativos do Windows 10 (1704). Tal reduzirá o problema da interrupção da instalação de aplicações durante o estado “Sincronização Pendente”. Além disso, os utilizadores poderão iniciar manualmente uma sincronização a partir da própria aplicação. 

O Portal da Empresa para Windows 10 também exporá um botão de atualização para permitir ao utilizador atualizar o conteúdo na aplicação sempre que necessário. 

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

Não irá afetar as suas implementações existentes em dispositivos geridos através do agente do Intune para PC. No entanto, após a migração, não poderá implementar appxs migradas em novos dispositivos geridos através do agente do Intune para PC que não tenham sido abrangidas anteriormente.

Após a migração, terá de voltar a carregar a appx como uma appx para PC, se quiser efetuar novas implementações em PC. Para saber mais, veja [Appx changes in Intune on Azure (Alterações a appx no Intune no Azure)](https://aka.ms/appxchange) no blogue da Equipa de Suporte do Intune.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Pré-visualização pública da nova experiência de administrador do Intune no Azure <!--736542-->

No início de 2017 iremos migrar toda a nossa experiência de administrador para o Azure, permitindo uma gestão poderosa e integrada de fluxos de trabalho de EMS principais numa plataforma de serviço moderna extensível com Graph API.

Os novos inquilinos de avaliação começarão a ver a pré-visualização pública da nova experiência de administrador no portal do Azure este mês. Enquanto estiverem no estado de pré-visualização, as capacidades e a paridade com a consola do Intune existente serão proporcionadas iterativamente.

A experiência de administração no portal do Azure irá utilizar a já anunciada nova funcionalidade de agrupamento e filtragem; quando o seu inquilino existente é migrado para a nova experiência de agrupamento, o utilizador também será migrado para pré-visualizar a nova experiência de administração do inquilino. Entretanto, se pretende testar ou observar qualquer uma das novas funcionalidades até que o seu inquilino seja migrado, inscreva-se para uma nova conta de avaliação do Intune ou veja a [nova documentação](https://docs.microsoft.com/intune/what-is-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Suporte para opções de configuração gerida para aplicações Android <!-- 621621 -->

Poderá configurar aplicações Android na Play Store que suportam opções de configuração gerida.  Esta funcionalidade permite-lhe ver a lista de valores de configuração suportados por uma aplicação e disponibiliza IU de primeira classe assistida para lhes permitir configurar os valores.

### <a name="remote-assistance-for-android-devices----675418---"></a>Assistência remota para dispositivos Android <!-- 675418 -->

O Intune irá utilizar o software [TeamViewer](https://www.teamviewer.com), adquirido separadamente, para lhe permitir disponibilizar assistência remota aos seus utilizadores com dispositivos Android.

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Permissões pré-configuradas de dispositivos para aplicações Android for Work <!-- 621614 -->

Para aplicações implementadas para perfis de trabalho de dispositivos Android for Work, poderá configurar o estado das permissões para aplicações individuais. Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, solicitarão aos utilizadores que aceitem ou recusem as permissões.  Por exemplo, se uma aplicação utilizar o microfone do dispositivo, o utilizador final ser solicitado a conceder permissão à aplicação para utilizar o microfone. Esta funcionalidade vai permitir-lhe definir permissões em nome do utilizador final.  O administrador pode configurar permissões para

- Recusar automaticamente sem notificar o utilizador
- Aprovar automaticamente sem notificar o utilizador
- Solicitar o utilizador a aceitar ou recusar.

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>Definir um PIN específico de cada aplicação para dispositivos Android for Work <!--728976-->

Poderá definir uma política de código de acesso aplicada apenas a aplicações no perfil de trabalho para dispositivos Android 7.0 e superior geridos como um dispositivo Android for Work.  As opções incluem:

- Definir apenas uma política de código de acesso para todos os dispositivos – este é o código de acesso que o utilizador final tem de utilizar para desbloquear os dispositivos completos
- Definir apenas uma política de código de acesso do perfil de trabalho – os utilizadores finais serão solicitados a introduzir um código de acesso sempre que qualquer aplicação no perfil de trabalho é aberta.
- Definir uma política de perfil de trabalho e de dispositivo – o departamento de TI tem a opção de definir uma política de código de acesso do dispositivo e uma política de código de acesso do perfil de trabalho com diferentes níveis de segurança (por exemplo, um PIN de 4 dígitos para desbloquear o dispositivo, mas um PIN de 6 dígitos para abrir qualquer aplicação de trabalho)

>[!NOTE]
> Esta opção só estará disponível para o Android 7.0 e superior.  Por predefinição, o utilizador final terá a opção de utilizar os dois PINs definidos separadamente ou pode optar por combinar os dois PINs definidos no mais forte dos dois.

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>Gerir a palavra-passe e outras definições de Android for Work <!--1102534-->

Estamos a adicionar uma nova política de restrição para dispositivos Android for Work que lhe permite gerir as definições de palavra-passe e perfil de trabalho em dispositivos Android for Work.

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>Nova política de filtros de conteúdo Web para dispositivos iOS <!-- 723832 -->

Poderá controlar os sites que os utilizadores dos dispositivos iOS podem visitar através de um dos dois métodos:

  - Adicionar URLs permitidos e bloqueados através do filtro de conteúdo Web incorporado da Apple.
  - Permitir o acesso apenas a sites específicos no browser Safari. Serão criados marcadores no Safari para cada site que especificar.

### <a name="apple-school-manager-asm-support---748864--"></a>Suporte do Gestor de Escola da Apple (ASM) <!--748864-->

O Intune suporta a utilização do Gestor de Escola da Apple (ASM) em vez do Programa de Inscrição de Dispositivos Apple para fornecer uma inscrição inicial de dispositivos iOS. A integração do ASM é necessária para utilizar a aplicação Sala de Aula para iPads Partilhados e para ativar a sincronização de dados do ASM no Azure Active Directory através da School Data Sync (SDS) da Microsoft.  

### <a name="shared-ipad-support---770395-1044681---"></a>Suporte de iPad Partilhado <!--770395, 1044681 -->

O Intune suportará a configuração do modo iPad Partilhado no perfil de inscrição para o Programa de Inscrição de Dispositivos da Apple ou o Gestor de Escola de Apple. Esta definição permite o início de sessão de vários IDs Apple geridos no mesmo dispositivo.

Vamos também expandir o suporte da gestão da aplicação Sala de Aula para iOS para incluir alunos que iniciem sessão em iPads partilhados com o ID Apple gerido deles.

### <a name="new-windows-device-restriction-settings---978585--"></a>Novas definições de restrição para dispositivos Windows <!--978585-->

Estamos a adicionar definições ao perfil de restrição de dispositivos Windows que controlam funcionalidades como ligação sem fios, deteção de dispositivos, mudança de tarefas e mensagens de erro do cartão SIM.

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>Aplicação do Office 365 ProPlus disponível para dispositivos Windows 10 <!--1121362-->

Estamos a adicionar o novo tipo de aplicação do Office 365 ProPlus que torna mais fácil a atribuição de aplicações do Office 365 ProPlus para dispositivos Windows 10. Além disso, também poderá instalar o Microsoft Project e Microsoft Visio, se for proprietário de licenças dos mesmos. As aplicações que pretende serão agrupadas e aparecerão como uma aplicação na lista de aplicações na consola do Intune.

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>Nova lista de permissões/bloqueios para o Browser Gerido <!--682960-->

Poderá configurar a lista de permissões/bloqueios de domínios e URLs do Browser Gerido com as definições de Configuração da Aplicação do Intune no Portal do Azure. Isto pode ser configurado para o Browser Gerido, independentemente de estar a ser utilizado num dispositivo gerido ou não gerido.

### <a name="new-app-configuration-capabilities----677969---"></a>Novas capacidades de configuração de aplicações <!-- 677969 -->

Esta funcionalidade será equivalente à configuração de aplicações da gestão de dispositivos móveis (MDM). Permite aos administradores a aplicação de mais valores de configuração de aplicações além dos já disponibilizados através das políticas de proteção de aplicações na MAM sem canal de inscrição.

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>Novas condições de políticas de proteção de aplicações para MAM <!--679864-->

Poderá definir um requisito para a MAM sem utilizadores de inscrição através da Consola de Administração que impõe o seguinte:

- Versão mínima da aplicação
- Versão mínima do sistema operativo
- Versão mínima do SDK da Aplicação Intune da aplicação de destino (apenas iOS)

Esta funcionalidade estará disponível para Android e iOS. O Intune suporta a imposição da versão mínima para versões de plataformas de SO, versões de aplicações e SDK da Aplicação Intune. No iOS, as aplicações com o SDK integrado podem também definir a imposição de uma versão mínima ao nível do SDK.

O utilizador não poderá aceder à aplicação de destino se não forem cumpridos os requisitos mínimos através da política de proteção de aplicações nos três níveis diferentes mencionados acima. Neste momento, o utilizador pode remover a respetiva conta (para aplicações de várias identidades), fechar a aplicação e/ou atualizar o respetivo SO ou a versão da aplicação para satisfazer os requisitos.

Além disso, também poderá configurar definições adicionais através da Consola de Administração para fornecer uma notificação sem bloqueios que recomenda um SO ou uma atualização de aplicações. Esta notificação pode ser fechada e a aplicação pode ser utilizada normalmente.

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Alterar a sua autoridade MDM sem anular a inscrição dos dispositivos geridos <!--1103950-->

Poderá alterar a sua autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Na consola do Gestor de Configuração, pode alterar a sua autoridade MDM a partir da opção Definir para o Gestor de Configuração (híbrido) para o Microsoft Intune (autónomo) ou vice-versa.


### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.

