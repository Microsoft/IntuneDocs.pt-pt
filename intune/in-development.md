---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166355"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>Em desenvolvimento para Microsoft Intune-setembro de 2019

Para ajudá-lo em sua preparação e planejamento, esta página lista as atualizações da interface do usuário do Intune e os recursos que estão em desenvolvimento, mas ainda não foram lançados. Além disso:

- Se prevemos que você precisará tomar medidas antes de uma alteração, publicaremos uma postagem complementar do centro de mensagens do Office.
- Quando um recurso é iniciado na produção, como uma visualização ou disponível para o público geral, a descrição do recurso será movida para fora desta página e para a [página o que há de novo](whats-new.md).
- Esta página e a [página novidades](whats-new.md) são atualizadas periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte o [roteiro do M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e cronogramas.

> [!Note]
> Esses itens refletem as expectativas atuais da Microsoft sobre os recursos do Intune que estão chegando em uma versão futura. As datas e os recursos individuais podem mudar. Nem todos os itens no desenvolvimento têm uma descrição de recurso nesta página.

**RSS feed**: Seja notificado quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feed:`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestão de aplicações

### <a name="managed-google-play-private-lob-apps----1464182----"></a>Aplicativos LOB privados Google Play gerenciados <!-- 1464182  -->
O Intune permitirá que os administradores de ti publiquem aplicativos LOB Android privados em Google Play gerenciados por meio de um iframe inserido no console do Intune.  Atualmente, os administradores de ti precisam publicar aplicativos LOB diretamente no console de publicação de reprodução do Google, que requer muitas etapas e está muito demorando.  Esse novo recurso permite a publicação fácil de aplicativos LOB com um conjunto mínimo de etapas sem a necessidade de sair do console do Intune.  Qualquer um dos cenários de gerenciamento do Android Enterprise que usam Google Play gerenciados pode aproveitar esse recurso (perfil de trabalho, dispositivos dedicados, totalmente gerenciados e não registrados).  No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Em seguida, selecione **Google Play gerenciado** na lista **tipo de aplicativo** . Para obter mais informações sobre aplicativos Google Play gerenciados, consulte [adicionar aplicativos gerenciados de Google Play a dispositivos Android Enterprise com o Intune](apps-add-android-for-work.md).

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portal da Empresa mensagens de status de instalação do aplicativo <!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.
- O aplicativo foi instalado com êxito, mas requer uma reinicialização.
- O aplicativo está no processo de instalação, mas requer uma reinicialização para continuar.

### <a name="managed-google-play-iframe-support----2871756----"></a>Suporte a Google Play iframe gerenciado <!-- 2871756  -->
O Intune fornecerá suporte para adicionar e gerenciar links da Web diretamente no console do Intune, por meio do iframe Google Playdor gerenciado.  Isso permite que os administradores de ti enviem um gráfico de URL e ícone e, em seguida, implantem esses links em dispositivos como aplicativos Android regulares. Qualquer um dos cenários de gerenciamento do Android Enterprise que usam Google Play gerenciados pode aproveitar esse recurso (perfil de trabalho, dispositivos dedicados, totalmente gerenciados e não registrados).  No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Em seguida, selecione **Google Play gerenciado** na lista **tipo de aplicativo** . Para obter mais informações sobre aplicativos Google Play gerenciados, consulte [adicionar aplicativos gerenciados de Google Play a dispositivos Android Enterprise com o Intune](apps-add-android-for-work.md).

### <a name="macos-support-for-vpp-apps----3173501----"></a>suporte do macOS para aplicativos VPP <!-- 3173501  -->
os aplicativos macOS que você comprou usando o Apple Business Manager serão exibidos no console do quando os tokens de VPP da Apple forem sincronizados no Intune. Você pode atribuir, revogar e reatribuir licenças baseadas em usuário e dispositivo para grupos usando o console do. Microsoft Intune ajuda a gerenciar aplicativos VPP adquiridos para uso em sua empresa:
- Comunicar informações sobre a licença a partir da App Store.
- Controlar o número de licenças que utilizou.
- Ajudá-lo a não instalar mais cópias da aplicação do que as que tem.
Para obter mais informações sobre o Intune e o VPP, consulte [gerenciar aplicativos e livros adquiridos por volume com o Microsoft Intune](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>suporte para macOS para aplicativos Web <!-- 3174427  -->
Você poderá instalar aplicativos Web, que permitem adicionar um atalho a uma URL na Web, para o Dock usando o macOS Portal da Empresa. Os usuários finais podem acessar a ação de **instalação** na página de detalhes do aplicativo para um aplicativo Web no MacOS portal da empresa. Para obter mais informações sobre o tipo de aplicativo de **link da Web** , consulte [adicionar aplicativos ao Microsoft Intune](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Atribuir o Microsoft Edge beta para macOS <!-- 4678761  -->
Você poderá adicionar e atribuir a versão mais recente do Microsoft Edge beta ao Intune para dispositivos macOS. No Intune, selecione aplicativos **cliente** >  > aplicativos**Adicionar aplicativo** > **Microsoft Edge-MacOS**. Em seguida, atribua o Microsoft Edge beta aos grupos pretendidos. O Microsoft AutoUpdate (MAU) mantém o Microsoft Edge atualizado. Para obter mais informações sobre o Microsoft Edge, consulte [gerenciar o acesso via Web usando o Microsoft Edge com o Microsoft Intune](manage-microsoft-edge.md).

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Ler e gravar API do Graph operações para aplicativos do Intune <!-- 5031704  -->
Os aplicativos poderão chamar o API do Graph do Intune com operações de leitura e gravação usando a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android e iOS permitirão que você controle o conteúdo de notificação do aplicativo para contas da organização. Este recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android <!-- 3041956  -->
Para instalações de aplicativos disponíveis em dispositivos Android de perfil de trabalho, você pode exibir o status de instalação do aplicativo e a versão instalada dos aplicativos gerenciados Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>Os recursos do dispositivo, as restrições de dispositivo e os perfis de extensão para as configurações do iOS e do macOS são mostrados pelo tipo de registro <!-- 4886161  -->

No Intune, você cria perfis para dispositivos IOS e MacOS (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** ou **MacOS** para plataforma > **recursos do dispositivo** , **Restrições de dispositivo**ou **extensões** para o tipo de perfil). Atualmente, as configurações disponíveis nesses perfis são listadas. 

Em uma atualização futura, as configurações disponíveis no portal do Intune serão categorizadas pelo tipo de registro ao qual se aplicam:

- iOS
  - Todos os tipos de registro
  - Registro de dispositivo e registro de dispositivo automatizado
  - Registro de dispositivo automatizado

- macOS
  - Todos os tipos de registro
  - Inscrição de dispositivos
  - Usuário aprovado e registro de dispositivo automatizado
  - Registro de dispositivo automatizado

Aplica-se a:

- iOS
  - [Funcionalidades do dispositivo](ios-device-features-settings.md)
  - [Restrições de dispositivos](device-restrictions-ios.md)

- macOS
  - [Funcionalidades do dispositivo](macos-device-features-settings.md)
  - [Restrições de dispositivos](device-restrictions-macos.md)
  - [extensões](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>Novas configurações de controle de voz para dispositivos iOS supervisionados em execução no modo de quiosque <!-- 4892835  -->

No Intune, você pode criar políticas para executar dispositivos IOS supervisionados como um quiosque, ou dispositivo dedicado (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para plataforma >  **Restrições de dispositivo** para o tipo de perfil > **quiosque (somente supervisionado)** ). 

Em uma atualização futura, haverá novas configurações que você pode controlar:

- **Controle de voz**: Habilita o controle de voz no dispositivo no modo de quiosque.
- **Modificação do controle de voz**: Permitir que os usuários alterem a configuração de controle de voz no dispositivo no modo de quiosque.

Para ver as configurações atuais, vá para [configurações do quiosque do IOS (apenas no modo supervisionado)](device-restrictions-ios.md#kiosk).

Aplica-se a:

- iOS 13,0 e posterior

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Usar o logon único para aplicativos e sites em seus dispositivos iOS e macOS <!-- 4893175  -->
Em uma atualização futura, haverá algumas novas configurações de logon único para dispositivos IOS e MacOS (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Ios** ou **MacOS** para recursos de **dispositivo** > de plataforma para tipo de perfil).

Use essas configurações para configurar uma experiência de logon único, especialmente para aplicativos e sites que usam a autenticação Kerberos. Você pode escolher entre uma extensão de aplicativo de logon único de credencial genérica e a extensão Kerberos interna da Apple.

Para ver os recursos atuais do dispositivo que você pode configurar, vá para [recursos do dispositivo IOS](ios-device-features-settings.md) e [recursos do dispositivo MacOS](macos-device-features-settings.md).

Aplica-se a:

- iOS 13,0 e mais recente
- macOS 10,15 e mais recente

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Associar domínios a aplicativos em dispositivos macOS 10.15 + <!-- 4898079  -->
Em dispositivos MacOS, você pode configurar diferentes recursos e enviar esses recursos por push para seus dispositivos usando uma política (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **MacOS** para recursos de **dispositivo** > de plataforma para tipo de perfil). Em uma atualização futura, você poderá associar domínios a seus aplicativos. Esse recurso ajuda a compartilhar credenciais com sites relacionados ao seu aplicativo e pode ser usado com a extensão de logon único da Apple, links universais e preenchimento de senha. 

Para ver os recursos atuais que você pode configurar, vá para [configurações de recurso de dispositivo MacOS no Intune](macos-device-features-settings.md).

Aplica-se a:

- macOS 10,15 e mais recente

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Use "iTunes" e "apps" na URL da iTunes App Store ao mostrar ou ocultar aplicativos em dispositivos supervisionados do iOS <!-- 4928474  --> 
No Intune, você pode criar políticas para mostrar ou ocultar aplicativos em seus dispositivos IOS supervisionados (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para plataforma > **dispositivo restrições** para o tipo de perfil > **Mostrar ou ocultar aplicativos (somente supervisionado)** ). 

Você pode inserir a URL da iTunes App Store, `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`como. Em uma atualização futura, você poderá usar `apps` o e `itunes` o na URL, como:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Para obter mais informações sobre essas configurações, consulte [Mostrar ou ocultar aplicativos](device-restrictions-ios.md#show-or-hide-apps).

Aplica-se a:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Suporte para perfis VPN IKEv2 para iOS <!-- 1943438 -->
Você poderá criar perfis de VPN para o cliente VPN nativo do iOS usando o protocolo IKEv2. IKEv2 é um novo tipo de conexão no **dispositivo** > **perfis** > de configuração**Criar perfil** > **Ios** para plataforma > **VPN** para tipo de perfil > **configurações**.

Esses perfis de VPN configuram o cliente VPN nativo. Portanto, nenhum aplicativo cliente VPN é instalado ou enviado por push para dispositivos gerenciados. Esse recurso requer que os dispositivos sejam registrados no Intune (registro de MDM).

Para ver as configurações de VPN atuais que você pode configurar, vá para [definir configurações de VPN em dispositivos IOS em Microsoft Intune](vpn-settings-ios.md).

Aplica-se a: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Novos locatários ficarão desaparecendo do gerenciamento de administrador de dispositivos Android <!-- 4869790  -->
Os recursos de administrador do dispositivo do Android foram substituídos pelo Android Enterprise. Portanto, é recomendável usar Android Enterprise para novos registros em vez disso. Em uma atualização futura, novos locatários precisarão concluir as seguintes etapas de pré-requisito no registro do Android para usar o gerenciamento de administrador do dispositivo: Vá para > **registro** >  > de dispositivo do Intune registro do Android dispositivos pessoais e de propriedade corporativa com privilégios de administração de dispositivo usar dispositivo >  **administrador para gerenciar dispositivos**.

Os locatários existentes não sofrerão alteração em seus ambientes. 

Para obter mais informações sobre o administrador do dispositivo Android no Intune, consulte [registro do administrador do dispositivo Android](android-enroll-device-administrator.md).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa <!-- 4394993  -->
Usando a redução, você poderá personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implantar atualizações de software em dispositivos macOS <!-- 3194876 -->
Você poderá implantar atualizações de software em grupos de dispositivos macOS. Esse recurso inclui o arquivo crítico, firmware, configuração e outras atualizações. Você poderá enviar atualizações no próximo check-in do dispositivo ou selecionar uma agenda semanal para implantar atualizações dentro ou fora do tempo que você definir. Isso ajuda quando você deseja atualizar dispositivos fora do horário de trabalho padrão ou quando o suporte técnico está totalmente na equipe. Você também obterá um relatório detalhado de todos os dispositivos macOS com atualizações implantadas. Você pode analisar o relatório de acordo com o dispositivo para ver os status de atualizações específicas.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Enviar notificações personalizadas para um dispositivo <!-- 4928910  -->
Você poderá enviar notificações personalizadas para dispositivos específicos que têm o Portal da Empresa ou o aplicativo do Intune instalado. Para fazer isso, acesse**dispositivos** > do **Intune** > **todos os dispositivos** > escolha um dispositivo > **mais** > **enviar notificação personalizada**. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Atualizações para recursos totalmente gerenciados do Android Enterprise <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Adicionaremos o seguinte suporte para dispositivos Android totalmente gerenciados:

- Os certificados SCEP para Android totalmente gerenciado estarão disponíveis para autenticação de certificado em dispositivos gerenciados como proprietário do dispositivo. Os certificados SCEP já têm suporte em dispositivos de perfil de trabalho.  Com certificados SCEP para o proprietário do dispositivo, você poderá: <!-- 5227935 -->
    - Criar perfil SCEP sob a seção do Android Enterprise
    - vincular certificados SCEP para fazer o perfil de Wi-Fi para autenticação
    - vincular certificados SCEP a perfis de VPN para autenticação
    - vincular certificados SCEP para perfis de email para autenticação (por meio da configuração de aplicativo)
- Os aplicativos do sistema terão suporte em dispositivos Android Enterprise. No Intune, você adicionará um aplicativo Android Enterprise System selecionando **aplicativos** >  > cliente aplicativos**Adicionar**. Na lista **tipo de aplicativo** , selecione **aplicativo Android Enterprise System**. Para obter mais informações sobre como adicionar aplicações ao Intune, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md). <!-- 4062195 -->
- Em **conformidade** > do dispositivo**Android Enterprise** > **dispositivo proprietário**, você poderá criar uma política de conformidade que defina o nível de atestado do Google SafetyNet.   <!-- 4631425 -->
- Em dispositivos Android Enterprise totalmente gerenciados, haverá suporte para os provedores de defesa contra ameaças móveis. Em **conformidade** > do dispositivo**Android Enterprise** > **dispositivo proprietário**, você pode escolher um nível de ameaça aceitável. <!-- 4631440 --> [As configurações do Android Enterprise para marcar dispositivos como compatíveis ou não compatíveis usando o Intune](compliance-policy-create-android-for-work.md#device-owner) listam as configurações atuais.


Aplica-se a: 
- Dispositivos Android Enterprise totalmente gerenciados

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

### <a name="updated-support-experience-------5012398------"></a>Experiência de suporte atualizada   <!--  5012398    -->
Como parte dos aprimoramentos contínuos, atualizaremos a experiência de suporte no console do Intune.  Vamos melhorar a pesquisa no console e os comentários para problemas comuns e simplificar o fluxo de trabalho para entrar em contato com o suporte.     

<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Proteção contra violação para o Windows Defender antivírus  <!-- 4705448       -->
Adicionaremos proteção de *violação* às configurações que o Intune pode gerenciar para o Windows Defender antivírus. Você poderá usar um perfil de configuração de dispositivo para o Windows 10 Endpoint Protection para ativar ou desativar a proteção contra violação.  Para obter mais informações sobre a proteção contra violações, consulte [impedir alterações de configurações de segurança com a proteção contra violações](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) na documentação do Windows. 


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.




