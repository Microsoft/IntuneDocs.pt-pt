---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35d64aba1c4c9a06e295699ac862198c29d8b9b1
ms.sourcegitcommit: 9f91d803dfc39336a954b79ccec6420e58375d31
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211559"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Você também pode encontrar [avisos importantes](#notices), [versões anteriores](whats-new-archive.md)e informações sobre [como as atualizações de serviço do Intune são lançadas](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Cada [atualização mensal](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) pode levar até três dias para ser imdistribuição e estará na seguinte ordem:
> - Dia 1: Pacífico Asiático (na Pacífico)
> - Dia 2: Europa, Oriente Médio, África (EMEA)
> - Dia 3: América do Norte
> 
> É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.
>
> Confira a [página em desenvolvimento](in-development.md) para obter uma lista de recursos futuros em uma versão.

**RSS feed**: Seja notificado quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feed:`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Semana de 16 de setembro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações 

#### <a name="managed-google-play-private-lob-apps----1464182----"></a>Aplicativos LOB privados Google Play gerenciados <!-- 1464182  -->
O Intune agora permite que os administradores de ti publiquem aplicativos LOB Android privados em Google Play gerenciados por meio de um iframe inserido no console do Intune.  Anteriormente, os administradores de ti precisavam publicar aplicativos LOB diretamente no console de publicação de reprodução do Google, que exigia várias etapas e estava demorando. Esse novo recurso permite a publicação fácil de aplicativos LOB com um conjunto mínimo de etapas, sem a necessidade de sair do console do Intune.  Os administradores não precisarão registrar-se manualmente como desenvolvedor com o Google e não precisarão mais pagar a taxa de registro do Google $25.  Qualquer um dos cenários de gerenciamento do Android Enterprise que usam Google Play gerenciados pode aproveitar esse recurso (perfil de trabalho, dispositivos dedicados, totalmente gerenciados e não registrados). No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Em seguida, selecione **Google Play gerenciado** na lista **tipo de aplicativo** . Para obter mais informações sobre aplicativos Google Play gerenciados, consulte [adicionar aplicativos gerenciados de Google Play a dispositivos Android Enterprise com o Intune](apps-add-android-for-work.md).

#### <a name="company-portal-experience----1473353-3598357---"></a>Experiência Portal da Empresa <!-- 1473353, 3598357 -->
O Portal da Empresa está sendo atualizado. Você poderá usar vários filtros na página de aplicativos dentro do Portal da Empresa. A página de detalhes do dispositivo também está sendo atualizada com uma experiência de usuário aprimorada. Estamos no processo de distribuir essas atualizações para todos os clientes e esperar que sejam concluídas até o final da próxima semana.

#### <a name="macos-support-for-web-apps----3174427---"></a>suporte para macOS para aplicativos Web <!-- 3174427 -->
Os aplicativos Web, que permitem adicionar um atalho a uma URL na Web, podem ser instalados no Dock usando o Portal da Empresa macOS. Os usuários finais podem acessar a ação de **instalação** na página de detalhes do aplicativo para um aplicativo Web no MacOS portal da empresa. Para obter mais informações sobre o tipo de aplicativo de **link da Web** , consulte [adicionar aplicativos ao Microsoft Intune](apps-add.md) e [adicionar aplicativos Web ao Microsoft Intune](web-app.md).

#### <a name="macos-support-for-vpp-apps----3173501----"></a>suporte do macOS para aplicativos VPP <!-- 3173501  -->
aplicativos macOS, adquiridos usando o Apple Business Manager, são exibidos no console do quando os tokens de VPP da Apple são sincronizados no Intune. Você pode atribuir, revogar e reatribuir licenças baseadas no usuário e no dispositivo para grupos usando o console do Intune. Microsoft Intune ajuda a gerenciar aplicativos VPP adquiridos para uso em sua empresa:
- Comunicar informações sobre a licença a partir da App Store.
- Controlar o número de licenças que utilizou.
- Ajudando você a impedir a instalação de mais cópias do aplicativo do que você possui.

Para obter mais informações sobre o Intune e o VPP, consulte [gerenciar aplicativos e livros adquiridos por volume com o Microsoft Intune](vpp-apps.md).

#### <a name="managed-google-play-iframe-support----2871756----"></a>Suporte a Google Play iframe gerenciado <!-- 2871756  -->
O Intune agora oferece suporte para adicionar e gerenciar links da Web diretamente no console do Intune por meio do iframe Google Playdor gerenciado.  Isso permite que os administradores de ti enviem um gráfico de URL e ícone e, em seguida, implantem esses links em dispositivos como aplicativos Android regulares. Qualquer um dos cenários de gerenciamento do Android Enterprise que usam Google Play gerenciados pode aproveitar esse recurso (perfil de trabalho, dispositivos dedicados, totalmente gerenciados e não registrados). No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Em seguida, selecione **Google Play gerenciado** na lista **tipo de aplicativo** . Para obter mais informações sobre aplicativos Google Play gerenciados, consulte [adicionar aplicativos gerenciados de Google Play a dispositivos Android Enterprise com o Intune](apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices----4252734----"></a>Instalar silenciosamente aplicativos LOB Android em dispositivos pretas <!-- 4252734  -->
Ao instalar aplicativos de LOB (linha de negócios) do Android em [dispositivos pretas](android-zebra-mx-overview.md), em vez de ser solicitado a baixar e instalar o aplicativo LOB, você poderá instalar o aplicativo silenciosamente. No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**. Para obter mais informações, consulte [Adicionar um aplicativo de linha de negócios Android a Microsoft Intune](lob-apps-android.md).

No momento, depois que o aplicativo de LOB for baixado, uma notificação de **êxito no download** será exibida no dispositivo do usuário. A notificação só pode ser descartada tocando em **limpar tudo** na sombra da notificação. Esse problema de notificação será corrigido em uma versão futura e a instalação será completamente silenciosa sem nenhum indicador visual.

#### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Ler e gravar API do Graph operações para aplicativos do Intune <!-- 5031704  -->
Os aplicativos podem chamar o API do Graph do Intune com operações de leitura e gravação usando a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios----3586942----"></a>Compartilhamento e criptografia de dados protegidos para o SDK de aplicativos do Intune para iOS <!-- 3586942  -->
Quando a encriptação está ativada por políticas de proteção de aplicações, o SDK da aplicação Intune para iOS utilizará as chaves de encriptação de 256 bits. Todos os aplicativos precisarão ter uma versão 8.1.1 do SDK para permitir o compartilhamento de dados protegidos.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438-----"></a>Suporte para perfis VPN IKEv2 para iOS <!-- 1943438   -->
Nessa atualização, você pode criar perfis de VPN para o cliente VPN nativo do iOS usando o protocolo IKEv2. IKEv2 é um novo tipo de conexão **no dispositivo** > **perfis** > de configuração**Criar perfil** > **Ios** para plataforma > **VPN** para tipo de perfil > **tipo de conexão**.

Esses perfis de VPN configuram o cliente VPN nativo, portanto, nenhum aplicativo cliente VPN é instalado ou enviado por push para dispositivos gerenciados. Esse recurso requer que os dispositivos sejam registrados no Intune (registro de MDM).

Para ver as configurações de VPN atuais que você pode configurar, vá para [definir configurações de VPN em dispositivos IOS](vpn-settings-ios.md).

Aplica-se a:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161-----"></a>Os recursos do dispositivo, as restrições de dispositivo e os perfis de extensão para as configurações do iOS e do macOS são mostrados pelo tipo de registro <!-- 4886161   -->

No Intune, você cria perfis para dispositivos IOS e MacOS (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** ou **MacOS** para plataforma > **recursos do dispositivo** , **Restrições de dispositivo**ou **extensões** para o tipo de perfil). 

Nessa atualização, as configurações disponíveis no portal do Intune são categorizadas pelo tipo de registro ao qual se aplicam:

- iOS
  - Registro de usuário
  - Inscrição de dispositivos
  - Registro de dispositivo automatizado (supervisionado)
  - Todos os tipos de registro

- macOS
  - Usuário aprovado
  - Inscrição de dispositivos
  - Registro de dispositivo automatizado
  - Todos os tipos de registro

Aplica-se a:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835-----"></a>Novas configurações de controle de voz para dispositivos iOS supervisionados em execução no modo de quiosque <!-- 4892835   -->
No Intune, você pode criar políticas para executar dispositivos IOS supervisionados como um quiosque, ou dispositivo dedicado (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para plataforma >  **Restrições de dispositivo** para o tipo de perfil > **quiosque**). 

Nessa atualização, há novas configurações que você pode controlar:
- **Controle de voz**: Habilita o controle de voz no dispositivo no modo de quiosque.
- **Modificação do controle de voz**: Permitir que os usuários alterem a configuração de controle de voz no dispositivo no modo de quiosque.

Para ver as configurações atuais, vá para [configurações de quiosque do IOS](device-restrictions-ios.md#kiosk).

Aplica-se a:
- iOS 13,0 e posterior

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175-----"></a>Usar o logon único para aplicativos e sites em seus dispositivos iOS e macOS <!-- 4893175   -->
Nesta atualização, há algumas novas configurações de logon único para dispositivos IOS e MacOS (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Ios** ou **MacOS** para plataforma > **Recursos do dispositivo** para o tipo de perfil).

Use essas configurações para configurar uma experiência de logon único, especialmente para aplicativos e sites que usam a autenticação Kerberos. Você pode escolher entre uma extensão de aplicativo de logon único de credencial genérica e a extensão Kerberos interna da Apple.

Para ver os recursos atuais do dispositivo que você pode configurar, vá para [recursos do dispositivo IOS](ios-device-features-settings.md) e [recursos do dispositivo MacOS](macos-device-features-settings.md).

Aplica-se a:
- iOS 13,0 e mais recente
- macOS 10,15 e mais recente

#### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079-----"></a>Associar domínios a aplicativos em dispositivos macOS 10.15 + <!-- 4898079   -->
Em dispositivos MacOS, você pode configurar diferentes recursos e enviar esses recursos por push para seus dispositivos usando uma política (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **MacOS** para recursos de **dispositivo** > de plataforma para tipo de perfil). Nessa atualização, você pode associar domínios a seus aplicativos. Esse recurso ajuda a compartilhar credenciais com sites relacionados ao seu aplicativo e pode ser usado com a extensão de logon único da Apple, links universais e preenchimento de senha. 

Para ver os recursos atuais que você pode configurar, vá para [configurações de recurso de dispositivo MacOS no Intune](macos-device-features-settings.md).

Aplica-se a:
- macOS 10,15 e mais recente

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474-----"></a>Use "iTunes" e "apps" na URL da iTunes App Store ao mostrar ou ocultar aplicativos em dispositivos supervisionados do iOS <!-- 4928474   --> 
No Intune, você pode criar políticas para mostrar ou ocultar aplicativos em seus dispositivos IOS supervisionados (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para plataforma > **dispositivo restrições** para o tipo de perfil > **Mostrar ou ocultar aplicativos**). 

Você pode inserir a URL da iTunes App Store, `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`como. Nessa atualização, `apps` e `itunes` podem ser usados na URL, como:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Para obter mais informações sobre essas configurações, consulte [Mostrar ou ocultar aplicativos](device-restrictions-ios.md#show-or-hide-apps).

Aplica-se a:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Os valores do tipo de senha da política de conformidade do Windows 10 são mais claros e correspondem ao CSP<!-- 5138985 -->
Em dispositivos Windows 10, você pode criar uma política de conformidade que exige recursos de senha específicos (**políticas** > de**conformidade** > do dispositivo**crie a política** > **Windows 10 e posterior** para Segurança do **sistema**> plataforma). Nesta atualização:
- Os valores de **tipo de senha** são mais claros e atualizados para corresponder ao [CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- A configuração **expiração da senha (dias)** é atualizada para permitir valores de 1-730 dias. 

Para obter mais informações sobre as configurações de conformidade do Windows 10, consulte [configurações do Windows 10 e posteriores para marcar dispositivos como em conformidade ou sem conformidade](compliance-policy-create-windows.md). 

Aplica-se a:
- Windows 10 e posterior

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access-------4092920---"></a>Interface do usuário atualizada para configurar o acesso no local do Microsoft Exchange    <!-- 4092920 -->  
Atualizamos o console do onde você configura o acesso do [Microsoft Exchange no local](conditional-access-exchange-create.md). Todas as configurações para o acesso ao Exchange local agora estão disponíveis no mesmo painel do console em que você habilita o *controle de acesso local do Exchange*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices----1109650----"></a>Permitir ou restringir a adição de widgets de aplicativo à tela inicial em dispositivos Android Enterprise Work Profile <!-- 1109650  --> 
Em dispositivos Android Enterprise, você pode configurar recursos no perfil de trabalho (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Android Enterprise** para plataforma >  **Perfil de trabalho somente > restrições de dispositivo** para o tipo de perfil). Nessa atualização, você pode permitir que os usuários adicionem widgets expostos por aplicativos de perfil de trabalho à tela inicial do dispositivo.

Para ver as configurações que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](device-restrictions-android-for-work.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790-----"></a>Novos locatários ficarão desaparecendo do gerenciamento de administrador de dispositivos Android <!-- 4869790   -->
Os recursos de administrador do dispositivo do Android foram substituídos pelo Android Enterprise. Portanto, é recomendável usar Android Enterprise para novos registros em vez disso. Em uma atualização futura, novos locatários precisarão concluir as seguintes etapas de pré-requisito no registro do Android para usar o gerenciamento de administrador do dispositivo: Vá para > **registro** >  > de dispositivo do Intune registro do Android dispositivos pessoais e de propriedade corporativa com privilégios de administração de dispositivo usar dispositivo >  **administrador para gerenciar dispositivos**.

Os locatários existentes não sofrerão alteração em seus ambientes. 

Para obter mais informações sobre o administrador do dispositivo Android no Intune, consulte [registro do administrador do dispositivo Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile----5012045-idmiss---"></a>Lista de dispositivos DEP associados a um perfil <!-- 5012045 idmiss -->
Agora você pode ver uma lista paginável de dispositivos DEP (Automated Programa de registro de dispositivos) que estão associados a um perfil. Você pode pesquisar a lista em qualquer página da lista. Para ver a lista, acesse**registro** > de dispositivo do **Intune** > **tokens do programa** de registro da**Apple** > > escolha um token > **perfis** > escolha um perfil >  **Dispositivos atribuídos** (em **Monitor**). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="more-android-fully-managed-support----3464667-4631425-4631440-5227935-4062195-----"></a>Mais suporte totalmente gerenciado do Android <!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Adicionamos o seguinte suporte para dispositivos Android totalmente gerenciados:

- Os certificados SCEP para Android totalmente gerenciado estão disponíveis para autenticação de certificado em dispositivos gerenciados como proprietário do dispositivo. Os certificados SCEP já têm suporte em dispositivos de perfil de trabalho.  Com certificados SCEP para o proprietário do dispositivo, você poderá: <!-- 5227935 -->
    - Criar perfil SCEP sob a seção do Android Enterprise
    - vincular certificados SCEP para fazer o perfil de Wi-Fi para autenticação
    - vincular certificados SCEP a perfis de VPN para autenticação
    - vincular certificados SCEP para os perfis de email para autenticação (via AppConfig)
- Os aplicativos do sistema têm suporte em dispositivos Android Enterprise. No Intune, adicione um aplicativo Android Enterprise System selecionando **aplicativos** >  > cliente aplicativos**Adicionar**. Na lista **tipo de aplicativo** , selecione **aplicativo Android Enterprise System**. Para obter mais informações, consulte [adicionar aplicativos do Android Enterprise System a Microsoft Intune](apps-ae-system.md). <!-- 4062195 -->
- Em **conformidade** > do dispositivo**Android Enterprise** > **dispositivo proprietário**, você pode criar uma política de conformidade que define o nível de atestado do Google SafetyNet.   <!-- 4631425 -->
- Em dispositivos Android Enterprise totalmente gerenciados, há suporte para os provedores de defesa contra ameaças móveis. Em **conformidade** > do dispositivo**Android Enterprise** > **dispositivo proprietário**, você pode escolher um nível de ameaça aceitável. <!-- 4631440 --> [As configurações do Android Enterprise para marcar dispositivos como compatíveis ou não compatíveis usando o Intune](compliance-policy-create-android-for-work.md#device-owner) listam as configurações atuais.
- Em dispositivos Android Enterprise totalmente gerenciados, o aplicativo Microsoft Launcher agora pode ser configurado por meio de políticas de proteção de aplicativo para permitir uma experiência de usuário final padronizada no dispositivo totalmente gerenciado. O aplicativo Microsoft Launcher pode ser usado para personalizar seu dispositivo Android. Usando o aplicativo junto com uma conta de conta Microsoft ou de trabalho/escola, você pode acessar seu calendário, documentos e atividades recentes em seu feed personalizado. <!-- 5334044 -->

Com essa atualização, estamos felizes em anunciar que o suporte do Intune para Android Enterprise totalmente gerenciado já está disponível para o público geral. 

Aplica-se a: 
- Dispositivos Android Enterprise totalmente gerenciados

#### <a name="send-custom-notifications-to-a-single-device-----4928910---"></a>Enviar notificações personalizadas para um único dispositivo  <!-- 4928910 -->
Agora você pode selecionar um único dispositivo e, em seguida, usar uma ação de dispositivo remoto para [Enviar uma notificação personalizada somente para esse dispositivo](custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment----4950491---"></a>As ações de limpeza e redefinição de senha não estão disponíveis para dispositivos iOS registrados usando o registro de usuário <!-- 4950491 -->
O registro de usuário é um novo tipo de registro de dispositivo da Apple. Quando você registra dispositivos usando o registro de usuário, as ações remotas de limpeza e redefinição de senha não estarão disponíveis para esses dispositivos.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices----4665317---"></a>Suporte do Intune para dispositivos do Catalina para iOS 13 e macOS <!-- 4665317 -->
O Intune agora dá suporte ao gerenciamento de dispositivos do iOS 13 e do macOS. Para obter mais informações, consulte a [postagem de blog do suporte a Microsoft Intune para IOS 13 e iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation-------3444125---"></a>Suporte BitLocker para rotação de senha de recuperação controlada pelo cliente   <!--  3444125 -->
Use as configurações do Intune Endpoint Protection para configurar a [rotação de senha de recuperação controlada pelo cliente](endpoint-protection-windows-10.md#windows-encryption) para o BitLocker em dispositivos que executam o Windows versão 1909 ou posterior.

Essa configuração inicia uma atualização de senha de recuperação controlada pelo cliente após uma recuperação de unidade do sistema operacional (usando o bootmgr ou WinRE) e o desbloqueio de senha de recuperação em uma unidade de dados fixa. Essa configuração atualiza a senha de recuperação específica que foi usada e outras senhas não utilizadas no volume permanecem inalteradas. Para obter mais informações, consulte a documentação do CSP do BitLocker para [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#configurerecoverypasswordrotation).

#### <a name="tamper-protection-for-windows-defender-antivirus-----4705448----------"></a>Proteção contra violação para o Windows Defender antivírus  <!-- 4705448        -->
Use o Intune para gerenciar a *proteção contra adulterações* para o Windows Defender antivírus. Você encontrará a [configuração de proteção contra violações](endpoint-protection-windows-10.md#windows-defender-security-center) no grupo da central de segurança do Microsoft defender quando usar perfis de configuração do dispositivo para o Windows 10 Endpoint Protection. Você pode definir a proteção de violação como *habilitada* para ativar as restrições de proteção do Temper, definir *desabilitado* para desativá-las ou definir*não configurado* para deixar a configuração atual de dispositivos em vigor.  

Para obter mais informações sobre a proteção contra violações, consulte [impedir alterações de configurações de segurança com a proteção contra violações](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) na documentação do Windows. 

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available-----5317392---------"></a>As configurações avançadas para o Windows Defender firewall já estão disponíveis para o público geral <!--  5317392       -->  
As [regras de firewall personalizadas do Windows Defender para o Endpoint Protection](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), que você configura como parte de um perfil de configuração de dispositivo, estão fora da visualização pública e estão disponíveis para o público geral (GA).  Você pode usar essas regras para especificar o comportamento de entrada e saída para aplicativos, endereços de rede e portas. Essas regras foram lançadas em julho como uma visualização pública. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-now-support-terms-of-use-policies----2358863-idmiss---"></a>As marcas de escopo agora dão suporte a políticas de termos de uso <!-- 2358863 idmiss -->
Agora você pode atribuir [marcas de escopo](scope-tags.md) a políticas de termos de uso. Para fazer isso, acesse os**termos e condições** de**registro** > de dispositivo do **Intune** > > escolha um item na lista >**marcas de escopo** de **Propriedades** > > escolha uma marca de escopo.

## <a name="week-of-september-9-2019"></a>Semana de 9 de setembro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="updates-to-microsoft-intune-app----4997846---"></a>Atualizações para Microsoft Intune aplicativo <!-- 4997846 -->
O aplicativo Microsoft Intune para Android foi atualizado com os seguintes aprimoramentos:
- Atualizado e aprimorado o layout para incluir a navegação inferior para as ações mais importantes.
- Adicionada uma página adicional que mostra o perfil do usuário.
- Adicionada a exibição de notificações acionáveis no aplicativo para o usuário, como a necessidade de atualizar suas configurações de dispositivo.
- Adicionada a exibição de notificações por push personalizadas, alinhando o aplicativo com o suporte adicionado recentemente no aplicativo Portal da Empresa para iOS e Android. Para obter mais informações, consulte [enviar notificações personalizadas no Intune](custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993---"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa <!-- 4394993 -->
Usando a redução, você pode personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo. Para obter mais informações, consulte [como configurar o aplicativo portal da empresa do Intune](company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Semana de 2 de setembro de 2019

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-user-interface-update--tenant-status-dashboard-----5273210----"></a>Atualização da interface do usuário do Intune – painel de status do locatário  <!-- 5273210  -->
A interface do usuário para o painel de status do locatário foi atualizada para se alinhar com os estilos de interface do usuário do Azure. Para obter mais informações, consulte [status do locatário](tenant-status.md).


## <a name="week-of-august-26-2019"></a>Semana de 26 de agosto de 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Definir configurações do Microsoft Edge usando modelos administrativos para Windows 10 e mais recente <!-- 5228061 -->

No Windows 10 e dispositivos mais recentes, você pode criar modelos administrativos para definir configurações de política de grupo no Intune. Nesta atualização, você pode definir as configurações que se aplicam ao Microsoft Edge versão 77 e mais recentes.

Para saber mais sobre modelos administrativos, confira [usar modelos do Windows 10 para definir configurações de política de grupo no Intune](administrative-templates-windows.md).

Aplica-se a:

- Windows 10 e mais recente (Windows RS4 +)

## <a name="week-of-august-12-2019"></a>Semana de 12 de agosto de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>Controlar o comportamento de desinstalação do aplicativo iOS no cancelamento do registro do dispositivo <!-- 3504144   -->
Os administradores podem gerenciar se um aplicativo é removido ou mantido em um dispositivo quando o registro do dispositivo é cancelado no nível de um usuário ou de um grupo de dispositivos. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Categorizar Microsoft Store para aplicativos de negócios <!-- 3926922 -->
Você pode categorizar Microsoft Store para aplicativos de negócios. Para fazer isso, escolha**aplicativos** **cliente aplicativos** > do **Intune** > > selecione uma**categoria**de **informações** > do aplicativo Microsoft Store para o aplicativo de negócios >. No menu suspenso, atribua uma categoria.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Notificações personalizadas para usuários do Microsoft Intune app <!-- 4843354  -->
O aplicativo Microsoft Intune para Android agora dá suporte à exibição de notificações por push personalizadas, alinhando-a com o suporte adicionado recentemente nos aplicativos Portal da Empresa para iOS e Android. Para obter mais informações, consulte [enviar notificações personalizadas no Intune](custom-notifications.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Novos recursos para dispositivos Android Enterprise dedicados no modo de vários aplicativos <!-- 3755304 3041943 3041946   -->
No Intune, você pode controlar os recursos e as configurações em uma experiência de estilo de quiosque em seus dispositivos Android Enterprise dedicados (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Android Enterprise** para plataforma > **somente proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil).

Nesta atualização, os seguintes recursos estão sendo adicionados:

-  > **Vários aplicativos dedicados de**dispositivos: O **botão página inicial virtual** pode ser mostrado passando o dedo para cima no dispositivo ou flutuando na tela para que os usuários possam movê-lo.
-  > **Vários aplicativos dedicados de**dispositivos: O **acesso à lanterna** permite que os usuários usem a lanterna. 
-  > **Vários aplicativos dedicados de**dispositivos: O **controle de volume de mídia** permite que os usuários controlem o volume de mídia do dispositivo usando um controle deslizante. 
-  > **Vários aplicativos dedicados de**dispositivos:  **Habilitar uma proteção de tela**, carregar uma imagem personalizada e controlar quando a proteção de tela é mostrada.

Para ver as configurações atuais, vá para [configurações do dispositivo Android Enterprise para permitir ou restringir recursos usando o Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:  
- Dispositivos Android Enterprise dedicados

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Novos perfis de aplicativo e configuração para dispositivos Android Enterprise totalmente gerenciados <!-- 3574215 3574238 3574235 3574232   -->
Usando perfis, você pode definir configurações que aplicam configurações de VPN, email e Wi-Fi aos dispositivos do proprietário do seu dispositivo Android Enterprise (totalmente gerenciado). Nesta atualização, você pode:

- Use [as políticas de configuração de aplicativo](app-configuration-policies-use-android.md) para implantar as configurações de email do Outlook, do Gmail e noves.
- Use perfis de configuração de dispositivo para implantar [configurações de certificado raiz confiável](certificates-configure.md).
- Use perfis de configuração de dispositivo para implantar configurações de [VPN](vpn-settings-android-enterprise.md) e [Wi-Fi](wi-fi-settings-android-enterprise.md) .

> [!IMPORTANT]
> Com esse recurso, os usuários se autenticam com seu nome de usuário e senha para perfis de VPN, Wi-Fi e de email. Atualmente, a autenticação baseada em certificado não está disponível. 

Aplica-se a:  
- Proprietário do dispositivo Android Enterprise (totalmente gerenciado)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>Controlar os aplicativos, arquivos, documentos e pastas que são abertos quando os usuários entram em dispositivos macOS <!--3914202   -->
Você pode habilitar e configurar recursos em dispositivos MacOS (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **MacOS** para plataforma > **recursos de dispositivo** para tipo de perfil) . 

Nessa atualização, há uma nova configuração de itens de logon para controlar quais aplicativos, arquivos, documentos e pastas são abertos quando um usuário entra no dispositivo registrado. 

Para ver as configurações atuais, vá para [configurações de recurso de dispositivo MacOS no Intune](macos-device-features-settings.md).

Aplica-se a:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Os prazos substituem as configurações de reinicialização envolvidas para Windows Update anéis   <!-- 4464404        -->
Para alinhar [as alterações de serviço do Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)recentes, os anéis de atualização do Windows 10 do Intune agora [dão suporte a configurações para prazos](windows-update-settings.md). Os *prazos* determinam quando um dispositivo instala atualizações de segurança e recursos.  Em dispositivos que executam o Windows 10 1903 ou posterior, os *prazos* substituem as configurações para *reinicialização envolvida*.  No futuro, os *prazos* também substituirão a *reinicialização envolvida* em versões anteriores do Windows 10.  

Quando você não configura os *prazos*, os dispositivos continuam a usar suas configurações de *reinicialização envolvidas* , no entanto, o [Intune preterirá o suporte para configurações de reinicialização envolvidas](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) em uma atualização futura.  

Planeje o uso de *prazos* para todos os seus dispositivos Windows 10. Depois que as configurações dos *prazos* estiverem em vigor, você poderá alterar as configurações do Intune para *reinicialização iniciada* para não ser configurada. Quando definido como não configurado, o Intune para de gerenciar essas configurações em dispositivos, mas não remove as últimas configurações da configuração do dispositivo. Portanto, as últimas configurações definidas para *reinicialização iniciada* permanecem ativas e em uso nos dispositivos até que essas configurações sejam modificadas por um método diferente do Intune. Posteriormente, quando a versão dos dispositivos do Windows mudar ou quando o suporte do Intune para *prazos* se expandir para a versão dos dispositivos do Windows, o dispositivo começará a usar as novas configurações, que já estão em vigor.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Suporte para vários conectores de certificado Microsoft Intune   <!--   4704642      -->
O Intune agora dá suporte à instalação e ao uso de vários [conectores de certificado Microsoft Intune para operações PKCS](certficates-pfx-configure.md). Essa alteração dá suporte ao balanceamento de carga e alta disponibilidade do conector. Cada instância de conector pode processar solicitações de certificado do Intune.  Se um conector não estiver disponível, outros conectores continuarão processando solicitações. 

Para usar vários conectores, você não precisa atualizar para a versão mais recente do software do conector.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Novas configurações e alterações nas configurações existentes para restringir recursos em dispositivos iOS e macOS <!-- 4867699 4867709   -->
Você pode criar perfis para restringir as configurações em dispositivos que executam o Ios e o MacOS (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** ou **MacOS** para o tipo de plataforma > **Restrições de dispositivo**). Essa atualização inclui os seguintes recursos:

- Em >  restriçõesde > dispositivo MacOS**nuvem e armazenamento**, use a nova configuração de entrega para impedir que os usuários iniciem o trabalho em um dispositivo MacOS e continue trabalhando em outro dispositivo MacOS ou Ios.

  Para ver as configurações atuais, vá para [configurações do dispositivo MacOS para permitir ou restringir recursos usando o Intune](device-restrictions-macos.md).

- Em**restrições de dispositivo** **Ios** > , há algumas alterações:

  - Aplicativos > internos**localizam meu iPhone (apenas no modo supervisionado)** : Nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - **Os aplicativos** > internos**encontram meus amigos (apenas no modo supervisionado)** : Nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - **Modificação sem fio** > **do estado de Wi-Fi (somente supervisionado)** : Nova configuração que impede que os usuários liguem ou desativem o Wi-Fi no dispositivo.
  - **QuickPath de teclado e dicionário** >  **(somente supervisionado)** : Nova configuração que bloqueia o recurso QuickPath.
  - **Nuvem e armazenamento**: A **continuação da atividade** é renomeada para **entrega**.

  Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](device-restrictions-ios.md).

Aplica-se a:  
- macOS 10,15 e mais recente
- iOS 13 e mais recente

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Algumas restrições de dispositivo iOS não supervisionadas ficarão supervisionadas somente com a versão iOS 13,0 <!-- 4867809   -->
Nessa atualização, algumas configurações se aplicam a dispositivos supervisionados com a versão 13,0 do iOS. Se essas configurações forem configuradas e atribuídas a dispositivos não supervisionados antes da versão 13,0 do iOS, as configurações ainda serão aplicadas a esses dispositivos não supervisionados. Eles ainda se aplicam após a atualização dos dispositivos para iOS 13,0. Essas restrições são removidas em dispositivos não supervisionados que são armazenados em backup e restaurados. 

Essas configurações incluem:

- App Store, Visualização de Documentos, Jogos
  - Loja de aplicações
  - Conteúdo explícito do iTunes, música, podcast ou notícias
  - Adicionando Game Center amigos
  - Jogos para vários jogadores
- Aplicações Incorporadas
  - Câmara
    - FaceTime
  - Safari
    - Preenchimento automático
- Cloud e Armazenamento
  - Backup no iCloud
  - Bloquear a sincronização de documentos do iCloud
  - Bloquear sincronização de cadeia de chaves do iCloud

Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](device-restrictions-ios.md).

Aplica-se a:  
- iOS 13,0 e mais recente

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Status do dispositivo melhorado para criptografia macOS FileVault  <!-- 4944983         -->
Atualizamos várias das mensagens de [status do dispositivo](encryption-monitor.md#device-encryption-status) para a criptografia FileVault em dispositivos MacOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>Algumas configurações de verificação do Windows Defender antivírus no relatório mostram um status de falha <!-- 5119229 -->
No Intune, você pode criar políticas para usar o Windows Defender antivírus para verificar seus dispositivos Windows 10 (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Windows 10 e posterior** para plataforma > **restrições de dispositivo** para o tipo de perfil > **Windows Defender antivírus**). O **tempo para executar uma verificação rápida diária e o** **tipo de verificação do sistema para executar** relatórios mostra um status de falha, quando é, na verdade, um status de êxito. 

Nessa atualização, esse comportamento é fixo. Portanto, o **tempo para executar uma verificação rápida diária** e o **tipo de verificação do sistema para executar** configurações mostra um status de êxito quando as verificações são concluídas com êxito e mostram um status de falha quando as configurações falham ao serem aplicadas. 

Para obter mais informações sobre as configurações do Windows Defender antivírus, consulte [configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos usando o Intune](device-restrictions-windows-10.md#microsoft-defender-antivirus). 

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="default-scope-tags----3702875----"></a>Marcas de escopo padrão <!-- 3702875  -->
Uma nova marca de escopo padrão interna agora está disponível. Todos os objetos do Intune não marcados que dão suporte a marcas de escopo são automaticamente atribuídos à marca de escopo padrão. A marca de escopo **padrão** é adicionada a todas as atribuições de função existentes para manter a paridade com a experiência de administração hoje. Se você não quiser que um administrador Veja objetos do Intune com a marca de escopo padrão, remova a marca de escopo padrão da atribuição de função. Esse recurso é semelhante ao recurso de escopos de segurança no System Center Configuration Manager. Para obter mais informações, consulte [usar o RBAC e marcas de escopo para para distribuí-lo](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Suporte ao administrador do dispositivo de registro do Android <!-- 4869749   -->
A opção de registro de administrador de dispositivo Android foi adicionada à página de registro do Android (registro**Android**de**registro** > de dispositivo do**Intune** > ). O administrador do dispositivo Android ainda estará habilitado por padrão para todos os locatários.  Para obter mais informações, consulte [registro de administrador do dispositivo Android](android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Ignorar mais telas no assistente de configuração <!--4877451  -->
Você pode definir perfis de Programa de registro de dispositivos para ignorar as seguintes telas do assistente de configuração:
- Para iOS
    - Aparência
    - Idioma Express
    - Idioma preferencial
    - Migração de dispositivo para dispositivo
- Para macOS
    - Hora da tela
    - Configuração do touch ID

Para obter mais informações sobre a personalização do assistente de configuração, consulte [criar um perfil de registro da Apple para IOS](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) e [criar um perfil de registro da Apple para MacOS ](device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Adicionar uma coluna de usuário ao processo de carregamento de CSV de dispositivo do AutoPilot <!-- 3823054 -->
Agora você pode adicionar uma coluna de usuário ao upload de CSV para dispositivos do AutoPilot. Isso permite que você atribua usuários em massa no momento em que importar o CSV. Para obter mais informações, consulte [registrar dispositivos Windows no Intune usando o piloto automático do Windows](enrollment-autopilot.md).


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurar o limite de tempo de limpeza de dispositivo automático para 30 dias <!--4231059  -->
Você pode definir o limite de tempo de limpeza do dispositivo automático como 30 dias (em vez do limite anterior de 90 dias) após a última entrada. Para fazer isso, vá para**dispositivos** > do **Intune** > **Configurar** > **regras de limpeza do dispositivo**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Número de Build incluído na página de hardware do dispositivo Android <!-- 4461910   -->
Uma nova entrada na página hardware para cada dispositivo Android inclui o número de Build do sistema operacional do dispositivo. Para obter mais informações, consulte [Exibir detalhes do dispositivo no Intune](device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Semana de 5 de agosto de 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Pretas Technologies é um OEM com suporte para o OEMConfig em dispositivos Android Enterprise  <!-- 4843713 -->

No Intune, você pode criar perfis de configuração de dispositivo e aplicar configurações a dispositivos Android Enterprise usando OEMConfig (**perfis** > de**configuração** > do dispositivo**Criar perfil**  >   **Android Enterprise** para plataforma > **OEMConfig** para tipo de perfil).

Nessa atualização, o pretas Technologies é um fabricante de equipamento original (OEM) com suporte para o OEMConfig. Para obter mais informações sobre o OEMConfig, consulte [usar e gerenciar dispositivos Android Enterprise com o OEMConfig](android-oem-configuration-overview.md).

Aplica-se a:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Semana de 22 de julho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Notificações personalizadas para usuários e grupos    <!-- 16766574          -->
Envie notificações por push personalizadas do aplicativo Portal da Empresa para os usuários em dispositivos Android e iOS que você gerencia com o Intune. Essas notificações por push móveis são altamente personalizáveis com texto livre e podem ser usadas para qualquer finalidade. Você pode direcioná-los para grupos de usuários diferentes em sua organização. Para obter mais informações, consulte [notificações personalizadas](custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>Aplicativo do controlador de política de dispositivo do Google <!-- 3041950  -->
O aplicativo de tela inicial gerenciado agora fornece acesso ao aplicativo de política de dispositivo Android do Google. O aplicativo de tela inicial gerenciado é um iniciador personalizado usado para dispositivos registrados no Intune como dispositivos do Android Enterprise (AE) dedicados usando o modo de quiosque de vários aplicativos. Você pode acessar o aplicativo de política de dispositivo Android ou orientar os usuários para o aplicativo de política de dispositivo Android, para fins de suporte e depuração. Esse recurso de inicialização está disponível no momento em que o dispositivo é registrado e bloqueado na tela inicial gerenciada. Nenhuma instalação adicional é necessária para usar essa funcionalidade.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Configurações de proteção do Outlook para dispositivos iOS e Android <!-- 3212619 -->
Agora você pode definir definições gerais de configuração de aplicativo e de proteção de dados para o Outlook para iOS e Android usando controles simples de administrador do Intune sem registro de dispositivo. As definições gerais de configuração de aplicativo fornecem paridade com as configurações que os administradores podem habilitar ao gerenciar o Outlook para iOS e Android em dispositivos registrados. Para obter mais informações sobre as configurações do Outlook, consulte [implantando definições de configuração de aplicativo do Outlook para IOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Use "regras de aplicabilidade" ao criar perfis de configuração de dispositivo do Windows 10 <!-- 2549910 eeready   idstaged -->

Você cria perfis de configuração de dispositivo do Windows 10 (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Windows 10** para plataforma > **regras de aplicabilidade**). Nessa atualização, você pode criar uma **regra de aplicabilidade** para que o perfil se aplique somente a uma edição específica ou a uma versão específica. Por exemplo, você cria um perfil que habilita algumas configurações do BitLocker. Depois de adicionar o perfil, use uma regra de aplicabilidade para que o perfil se aplique somente a dispositivos que executam o Windows 10 Enterprise.

Para adicionar uma regra de aplicabilidade, consulte [regras de aplicabilidade](device-profile-create.md#applicability-rules).

Aplica-se a: Windows 10 e posterior

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>Usar tokens para adicionar informações específicas do dispositivo em perfis personalizados para dispositivos iOS e macOS <!-- 3330008  -->
Você pode usar perfis personalizados em dispositivos IOS e MacOS para definir configurações e recursos não internos no Intune (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** ou **MacOS** para plataforma > **personalizado** para o tipo de perfil). Nessa atualização, você pode adicionar tokens aos seus `.mobileconfig` arquivos para adicionar informações específicas do dispositivo. Por exemplo, você pode adicionar `Serial Number: {{serialnumber}}` ao seu arquivo de configuração para mostrar o número de série do dispositivo.

Para criar um perfil personalizado, consulte [configurações](custom-settings-ios.md) personalizadas do Ios ou [configurações personalizadas do MacOS](custom-settings-macos.md).

Aplica-se a:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Novo designer de configuração ao criar um perfil de OEMConfig para Android Enterprise <!-- 3712769   -->
No Intune, você pode criar um perfil de configuração de dispositivo que usa um aplicativo OEMConfig (configuração de dispositivo > perfis > Criar perfil > Android Enterprise para plataforma > OEMConfig para o tipo de perfil). Quando você faz isso, um editor de JSON é aberto com um modelo e valores para que você altere. 

Essa atualização inclui um designer de configuração com uma experiência de usuário aprimorada que mostra detalhes inseridos no aplicativo, incluindo títulos, descrições e muito mais. O editor de JSON ainda está disponível e mostra as alterações feitas no designer de configuração.

Para ver as configurações atuais, vá para [usar e gerenciar dispositivos Android Enterprise com o OEMConfig](android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Interface do usuário atualizada para configurar o Windows Hello  <!-- 4089576            -->
Atualizamos o console do onde você [configura o Intune para usar o Windows Hello para empresas](windows-hello.md). Agora, todos os parâmetros de configuração estão disponíveis no mesmo painel do console em que você habilita o suporte para o Windows Hello. 


#### <a name="intune-powershell-sdk----4924113---"></a>SDK do Intune PowerShell <!-- 4924113 --> 
O SDK do PowerShell do Intune, que fornece suporte para a API do Intune por meio do Microsoft Graph, foi atualizado para a versão 6.1907.1.0. O SDK agora dá suporte ao seguinte:
- Funciona com a automação do Azure.
- Dá suporte a operações de leitura de autenticação somente de aplicativo. 
- Dá suporte a nomes abreviados amigáveis como aliases.
- Está em conformidade com as convenções de nomenclatura do PowerShell. Especificamente, o `PSCredential` parâmetro ( `Connect-MSGraph` no cmdlet) foi renomeado para `Credential`.
- Dá suporte à especificação manual do valor `Content-Type` do cabeçalho ao usar `Invoke-MSGraphRequest` o cmdlet.

Para obter mais informações, consulte [SDK do PowerShell para Microsoft Intune API do Graph](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Atualizações para restrições de registro  <!-- 2871968 -->
As restrições de registro para novos locatários foram atualizadas para que os perfis de trabalho do Android Enterprise sejam permitidos por padrão. Os locatários existentes não sofrerão alteração. Para usar perfis de trabalho do Android Enterprise, você ainda precisa [conectar sua conta do Intune à sua conta de Google Play gerenciada](connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Atualizações de interface do usuário para registro da Apple e restrições de registro <!--4089575, 4089579  -->
Ambos os processos a seguir usam uma interface do usuário de estilo de assistente:
- Registro de dispositivo da Apple. Para obter mais informações, consulte [registrar automaticamente dispositivos IOS com o programa de registro de dispositivos da Apple](device-enrollment-program-enroll-ios.md).
- Criação de restrição de registro. Para obter mais informações, consulte [definir restrições de registro](enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Manipulando a pré-configuração de identificadores de dispositivos corporativos para dispositivos Android Q <!-- 4711509  idmiss -->
No Android Q (V10), o Google removerá a capacidade de agentes de MDM em dispositivos Android gerenciados por legado (administrador do dispositivo) para coletar informações de identificador de dispositivo.  O Intune tem um recurso que permite que os administradores de ti [configurem previamente uma lista de números de série de dispositivos ou IMEIs](corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) para marcar automaticamente esses dispositivos como corporativos. Esse recurso não funcionará para dispositivos Android Q gerenciados pelo administrador do dispositivo.  Independentemente de o número de série ou IMEI do dispositivo ser carregado, ele sempre será considerado pessoal durante o registro do Intune.  Você pode alternar manualmente a propriedade para o corporativo após o registro.  Isso afeta apenas os novos registros e os dispositivos registrados existentes não são afetados.  Dispositivos Android gerenciados com perfis de trabalho não são afetados por essa alteração e continuarão funcionando como fazem hoje.  Além disso, os dispositivos Android Q registrados como administrador do dispositivo não poderão mais reportar o número de série ou IMEI no console do Intune como propriedades do dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Os ícones foram alterados para registros corporativos do Android (perfil de trabalho, dispositivos dedicados e dispositivos totalmente gerenciados) <!-- 4977730 -->
Os ícones para perfis de registro do Android Enterprise foram alterados. Para ver os novos ícones, vá para**registro** > do **Intune** > **registro do Android** > Procure em perfis de **registro**.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Alteração de coleta de dados de diagnóstico do Windows <!-- 4113859 -->
O valor padrão para coleta de dados de diagnóstico foi alterado para dispositivos que executam o Windows 10, versão 1903 e posterior. A partir do Windows 10 1903, a coleta de dados de diagnóstico é habilitada por padrão. Os dados de diagnóstico do Windows são dados técnicos vitais de dispositivos Windows sobre o dispositivo e como o Windows e o software relacionado estão sendo executados. Para obter mais informações, consulte [configurar dados de diagnóstico do Windows em sua organização](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Os dispositivos de piloto automático também são aceitos na telemetria "completa", a menos que definido de outra forma no perfil do AutoPilot com [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="improve-device-location---3855417----"></a>Melhorar o local do dispositivo<!-- 3855417  -->
Você pode ampliar as coordenadas exatas de um dispositivo usando a ação **Localizar dispositivo** . Para obter mais informações sobre como localizar dispositivos iOS perdidos, consulte [localizar dispositivos IOS perdidos](device-locate.md).


### <a name="device-security"></a>Segurança do dispositivo

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Configurações avançadas do Windows Defender firewall (visualização pública)  <!--  1311949     -->  
Use o Intune para gerenciar [regras de firewall personalizadas como parte de um perfil de configuração de dispositivo para o](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) Endpoint Protection no Windows 10. As regras podem especificar o comportamento de entrada e saída para aplicativos, endereços de rede e portas. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Interface do usuário atualizada para gerenciar linhas de base de segurança   <!-- 4091125     -->
Atualizamos a [experiência de criação e edição](security-baselines.md#create-the-profile) no console do Intune para nossas linhas de base de segurança. As alterações incluem:

Um formato de estilo de assistente mais simples, que é condensado para uma única folha. dentro de uma folha. Esse novo design desaparece com a expansão da folha que exige que os profissionais de ti se aprofundem em vários painéis separados.  
Agora você pode criar atribuições como parte da experiência de criação e edição, em vez de ter que retornar posteriormente para atribuir linhas de base. Adicionamos um resumo das configurações que você pode exibir antes de criar uma nova linha de base e ao editar uma existente. Ao editar, o resumo mostra apenas a lista de itens definidos dentro de uma categoria de propriedades que estão sendo editadas.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Semana de 15 de julho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Tela inicial gerenciada e ícones de configurações gerenciadas <!-- 4918107 -->
O ícone do aplicativo de tela inicial gerenciado e o ícone de **configurações gerenciadas** foram atualizados. O aplicativo de tela inicial gerenciado só é usado por dispositivos registrados no Intune como dispositivos dedicados do Android Enterprise (AE) e executados em modo de quiosque com vários aplicativos. Para obter mais informações sobre o aplicativo de tela inicial gerenciado, consulte [Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise](app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Política de dispositivo Android em dispositivos Android Enterprise dedicados <!-- 4918136 -->
Você pode acessar o aplicativo de política de dispositivo Android na tela de depuração do aplicativo de tela inicial gerenciada. O aplicativo de tela inicial gerenciado só é usado por dispositivos registrados no Intune como dispositivos dedicados do Android Enterprise (AE) e executados em modo de quiosque com vários aplicativos. Para obter mais informações, consulte [Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise](app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>atualizações de Portal da Empresa do iOS <!-- 3902931 -->
O nome da sua empresa nos prompts de gerenciamento de aplicativo iOS substituirá o texto atual "i.manage.microsoft.com". Por exemplo, os usuários verão o nome da empresa em vez de "i.manage.microsoft.com" quando os usuários tentarem instalar um aplicativo iOS do Portal da Empresa ou quando os usuários permitirem o gerenciamento do aplicativo. Isso será distribuído para todos os clientes durante os próximos dias.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>Gerenciar FileVault para macOS   <!--  3858502 + 4557986 + 1210104  -->
Você pode usar o Intune para [gerenciar a criptografia de chave FileVault para dispositivos MacOS](encrypt-devices.md). Para criptografar dispositivos, use um perfil de configuração de dispositivo do Endpoint Protection.

Nosso suporte para FileVault inclui criptografia de dispositivos não criptografados, caução de uma chave de recuperação pessoal de dispositivos, rotação automática ou manual de chaves de criptografia pessoais e recuperação de chave para seus dispositivos corporativos. Os usuários finais também podem usar o site Portal da Empresa para obter a chave de recuperação pessoal para seus dispositivos criptografados. 

Também expandimos o relatório de criptografia para incluir [informações sobre](encryption-monitor.md) as informações no lado do FileVault para o BitLocker, para que você possa exibir todos os detalhes de criptografia do dispositivo em um único lugar. 

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>A redefinição do Windows AutoPilot remove o usuário principal do dispositivo <!-- 4156123 -->
Quando a redefinição do AutoPilot é usada em um dispositivo, o usuário primário do dispositivo será removido. O próximo usuário que entrar após a redefinição será definido como o usuário primário. Este recurso será distribuído para todos os clientes durante os próximos dias.

## <a name="week-of-july-8-2019"></a>Semana de 8 de julho de 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Novas configurações do Office, do Windows e do OneDrive nos modelos administrativos do Windows 10 <!-- 3510695 -->

Você pode criar modelos administrativos no Intune que imitam o gerenciamento de política de grupo local (**perfis** > de**Gerenciamento** > de dispositivos**Criar perfil** > **Windows 10 e posterior** para **modelo administrativo** do > de plataforma para tipo de perfil).

Essa atualização inclui mais configurações do Office, do Windows e do OneDrive que você pode adicionar aos seus modelos. Com essas novas configurações, agora você pode definir mais de 2500 configurações que são 100% baseadas em nuvem.

Para saber mais sobre esse recurso, consulte [usar modelos do Windows 10 para definir configurações de política de grupo no Intune](administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

## <a name="week-of-july-1-2019"></a>Semana de 1º de julho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>AAD e aplicativo em dispositivos Android Enterprise <!-- 3574267 -->
Ao integrar dispositivos Android Enterprise totalmente gerenciados, os usuários agora serão registrados com o Azure Active Directory (AAD) durante a configuração inicial de seu dispositivo novo ou de redefinição de fábrica. Anteriormente para um dispositivo totalmente gerenciado, após a conclusão da instalação, o usuário precisava iniciar manualmente o aplicativo Microsoft Intune para iniciar o registro do AAD. Agora, quando o usuário chega no dispositivo home page após a configuração inicial, o dispositivo é registrado e inscrito.

Além das atualizações do AAD, as políticas de proteção de aplicativo do Intune (aplicativo) agora têm suporte em dispositivos Android Enterprise totalmente gerenciados. Essa funcionalidade ficará disponível à medida que for distribuída. Para obter mais informações, consulte [adicionar aplicativos gerenciados Google Play a dispositivos Android Enterprise com o Intune](apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Semana de 24 de junho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configurar qual navegador tem permissão para vincular aos dados da organização <!-- 3145939 -->
As políticas de Proteção de Aplicativo do Intune (aplicativo) em dispositivos Android e iOS agora permitem transferir links da Web da organização para um navegador específico além do Intune Managed Browser ou do Microsoft Edge.  Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>A página todos os aplicativos identifica Microsoft Store online/offline para aplicativos de negócios<!--4089647 -->
A página **todos os aplicativos** agora inclui rótulos para identificar aplicativos Microsoft Store for Business (MSFB) como aplicativos online ou offline. Cada aplicativo MSFB agora inclui um sufixo para **online** ou **offline**. A página de detalhes do aplicativo também inclui o **tipo de licença** e **dá suporte** a informações de instalação de contexto de dispositivo (somente aplicativos licenciados offline).

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Portal da Empresa aplicativo em dispositivos compartilhados do Windows <!--4393553 -->
Agora, os usuários podem acessar o aplicativo Portal da Empresa em dispositivos compartilhados do Windows. Os usuários finais verão um rótulo **compartilhado** no bloco do dispositivo. Isso se aplica ao aplicativo Windows Portal da Empresa versão 10.3.45609.0 e posterior.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Exibir todos os aplicativos instalados da página da Web do New Portal da Empresa <!-- 4224326 -->
A página novos **aplicativos instalados** do portal da empresa site lista todos os aplicativos gerenciados (necessários e disponíveis) que estão instalados nos dispositivos de um usuário. Além do tipo de atribuição, os usuários podem ver o editor do aplicativo, a data de publicação e o status da instalação atual. Se você não tiver feito aplicativos necessários ou disponíveis para seus usuários, eles verão uma mensagem explicando que nenhum aplicativo da empresa foi instalado. Para ver a nova página na Web, acesse o [site do portal da empresa](https://portal.manage.microsoft.com) e clique em **aplicativos instalados**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>Nova exibição permite que os usuários do aplicativo vejam todos os aplicativos gerenciados instalados no dispositivo <!-- 2352913 -->  
O aplicativo Portal da Empresa para Windows agora lista todos os aplicativos gerenciados (necessários e disponíveis) que estão instalados no dispositivo de um usuário. Os usuários também podem ver tentativas e instalações de Aplicativos pendentes e seus status atuais. Se você não tiver feito aplicativos necessários ou disponíveis para seus usuários, eles verão uma mensagem explicando que nenhum aplicativo da empresa foi instalado. Para ver o novo modo de exibição, acesse o painel de navegação portal da empresa **e selecione** > aplicativos**instalados aplicativos**.    

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Definir configurações para extensões de kernel em dispositivos macOS <!-- 2043024 -->
Em dispositivos MacOS, você pode criar um perfil de configuração de dispositivo (**perfis** > de**configuração** > de dispositivo**Criar perfil** > escolher **MacOS** para plataforma). Essa atualização inclui um novo grupo de configurações que permitem configurar e usar extensões de kernel em seus dispositivos. Você pode adicionar extensões específicas ou permitir todas as extensões de um parceiro ou desenvolvedor específico.

Para saber mais sobre esse recurso, consulte [visão geral das extensões do kernel](kernel-extensions-overview-macos.md) e [configurações de extensão do kernel](kernel-extensions-settings-macos.md).

Aplica-se a: macOS 10.13.2 e posterior

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>Os aplicativos da configuração armazenar somente para dispositivos Windows 10 incluem mais opções de configuração <!-- 2697002 -->
Ao criar um perfil de restrições de dispositivo para dispositivos Windows, você pode usar **os aplicativos da configuração armazenar somente** para que os usuários instalem apenas os aplicativos da Windows Store (**perfis**  >  de**configuração** > de dispositivo **Criar perfil** Windows 10 **e posterior** para plataforma > **restrições de dispositivo** para o tipo de perfil).  >  Nessa atualização, essa configuração é expandida para dar suporte a mais opções. 

Para ver a nova configuração, vá para [configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos](device-restrictions-windows-10.md#app-store).

Aplica-se a: Windows 10 e posterior

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Implantar vários perfis de dispositivo do pretas Mobility Extensions em um dispositivo, mesmo grupo de usuários ou no mesmo grupo de dispositivos <!-- 4089955 -->
No Intune, você pode usar o MX (pretas Mobility Extensions) em um perfil de configuração de dispositivo para personalizar as configurações de dispositivos pretas que não são internos no Intune. No momento, você pode implantar um perfil em um único dispositivo. Nesta atualização, você pode implantar vários perfis para:
- O mesmo grupo de usuários
- O mesmo grupo de dispositivos
- Um único dispositivo

[Use e gerencie dispositivos pretas com as extensões de mobilidade do pretas no Microsoft Intune](android-zebra-mx-overview.md) mostra como usar o MX no Intune.

Aplica-se a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Algumas configurações de quiosque em dispositivos iOS são definidas usando "bloquear", substituindo "permitir" <!-- 4404075  -->
Quando você cria um perfil de restrições de dispositivo em dispositivos IOS (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para tipo de perfil **> quiosque**), você define o **bloqueio automático**, o **comutador de toque**, a rotação de **tela**, o botão de suspensão da **tela**e os botões de **volume**. 

Nessa atualização, os valores são **Block** (bloqueia o recurso) e **não configurados** (permite o recurso). Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos](device-restrictions-ios.md#kiosk). 

Aplica-se a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>Usar ID facial para autenticação de senha em dispositivos iOS <!-- 4490704 -->
Ao criar um perfil de restrições de dispositivo para dispositivos iOS, você pode usar uma impressão digital para uma senha. Nessa atualização, as configurações de senha de impressão digital também permitem o reconhecimento facial (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para plataforma > **dispositivo restrições** para o tipo de perfil > **senha**). Como resultado, as seguintes configurações foram alteradas:

- O **desbloqueio de impressão digital** agora é **ID de toque e desbloqueio de ID facial**.
- A **modificação de impressão digital (somente supervisionado)** agora é a **ID de toque e a modificação da ID de face (somente supervisionado)** .

A ID de face está disponível no iOS 11,0 e posterior. Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](device-restrictions-ios.md#password).

Aplica-se a: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>Restringir os recursos de jogos e da loja de aplicativos em dispositivos iOS agora depende da região de classificações <!-- 4593948 -->
Em dispositivos IOS, você pode permitir ou restringir recursos relacionados a jogos, a loja de aplicativos e a exibição de documentos (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Ios** para plataforma > **Restrições de dispositivo** para o tipo de perfil > **loja de aplicativos, exibição de documento, jogos**). Você também pode escolher a região de classificações, como a Estados Unidos. 

Nessa atualização, o recurso de **aplicativos** é movido para ser um filho para a **região de classificações**e depende da **região de classificações**. Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Suporte do Windows AutoPilot para ingresso híbrido no Azure AD <!-- 4809146-->
O Windows AutoPilot para dispositivos existentes agora dá suporte à junção híbrida do Azure AD (além do suporte existente para ingresso no Azure AD). Aplica-se aos dispositivos Windows 10 versão 1809 e acima. Para obter mais informações, consulte [Windows AutoPilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Gestão de dispositivos

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Consulte o nível de patch de segurança para dispositivos Android <!-- 4461911 -->
Agora você pode ver o nível de patch de segurança para dispositivos Android. Para fazer isso, escolha**dispositivos** > do **Intune** > **todos os dispositivos** > escolha um dispositivo > **hardware**.
O nível do patch está listado na seção **sistema operacional** .

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Atribuir marcas de escopo a todos os dispositivos gerenciados em um grupo de segurança <!-- 3173810 -->
Agora você pode atribuir marcas de escopo a um grupo de segurança e todos os dispositivos no grupo de segurança também serão associados a essas marcas de escopo. Todos os dispositivos nesses grupos também serão atribuídos à marca de escopo. As marcas de escopo definidas com esse recurso substituirão as marcas de escopo definidas com o fluxo atual de marcas de escopo do dispositivo. Para obter mais informações, consulte [usar RBAC e marcas de escopo para distribuí-lo](scope-tags.md).

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="use-keyword-search-with-security-baselines-------"></a>Usar pesquisa de palavra-chave com linhas de base de segurança <!--  -->
Ao criar ou editar [perfis de linha de base de segurança](security-baselines.md#create-the-profile), você pode especificar palavras-chave na nova barra de *pesquisa* para filtrar os grupos de configurações disponíveis para aqueles que contêm seus critérios de pesquisa. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>O recurso de linhas de base de segurança agora está disponível para o público geral  <!-- 3785395 -->
O recurso de **linhas de base de segurança** está fora de visualização e agora está disponível para o público geral (GA).  Isso significa que o recurso está pronto para uso na produção. No entanto, os modelos de linha de base individuais podem permanecer na versão prévia e serem avaliados e liberados para GA em suas próprias agendas.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>O modelo de linha de base de segurança do MDM já está disponível ao público geral   <!-- 3794072, 4217151,  3534649 -->
O modelo de linha de base de segurança do MDM foi removido da visualização e agora está disponível para o público geral (GA). O modelo GA é identificado como a **linha de base de segurança do MDM para maio de 2019**.  Esse é um novo modelo e não uma atualização da versão de visualização.  Como um novo modelo, você precisará examinar as [configurações que ele contém](security-baseline-settings-windows.md)e, em seguida, criar novos perfis para implantar o modelo em seu dispositivo. Outros modelos de linha de base de segurança podem permanecer em versão prévia. Para obter uma lista de linhas de base disponíveis, consulte [linhas de base de segurança disponíveis](security-baselines.md#available-security-baselines).  

Além de ser um novo modelo, a *linha de base de segurança do MDM para o modelo de maio de 2019* inclui as duas configurações que anunciamos recentemente em nosso artigo em desenvolvimento:  
- Acima do bloqueio: Ativar aplicativos de voz de uma tela bloqueada  
- DeviceGuard: Use a VBS (segurança baseada em virtualização) na próxima reinicialização dos dispositivos.  

A *linha de base de segurança do MDM para maio de 2019* também inclui a adição de várias novas configurações, a remoção de outras e uma revisão do valor padrão de uma configuração. Para obter uma lista detalhada das alterações de visualização para GA, consulte **o que mudou no novo modelo**.

#### <a name="security-baseline-versioning-----3194322---"></a>Controle de versão de linha de base de segurança  <!-- 3194322 -->
Linhas de base de segurança para o suporte do Intune controle de versão. Com esse suporte, à medida que novas versões de cada linha de base de segurança são liberadas, você pode atualizar seus perfis de linha de base de segurança existentes para usar a versão de linha de base mais recente sem precisar recriar e implantar uma nova linha de base do zero. Além disso, no console do Intune, você pode exibir informações sobre cada linha de base, como o número de perfis individuais que usa a linha de base, quantas versões de linha de base são usadas por seus perfis e quando a versão mais recente de uma segurança específica a linha de base foi.  Para obter mais informações, consulte **linhas de base de segurança**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>A configuração usar chaves de segurança para entrada foi movida  <!-- 4501151 -->
A definição de configuração do dispositivo para a proteção de identidade chamada **usar chaves de segurança para entrar** não é mais encontrada como uma subconfiguração de *Configurar o Windows Hello para empresas*. Agora é uma configuração de nível superior que está sempre disponível, mesmo quando você não habilita o uso do Windows Hello para empresas. Para obter mais informações, consulte [proteção de identidade](identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>Novas permissões para administradores de grupo atribuídos   <!-- 4504437   -->
A função interna de administrador da escola do Intune agora tem permissões CRUD (criar, ler, atualizar e excluir) para aplicativos gerenciados. Essa atualização significa que, se você estiver atribuído como um administrador de grupo no Intune para Educação, agora poderá criar, exibir, atualizar e excluir os MDM Push Certificate do iOS, tokens de servidor MDM do iOS e tokens VPP do iOS, juntamente com [todas as permissões existentes que você tem](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Para executar qualquer uma dessas ações, vá para **configurações** > de locatário**Gerenciamento de dispositivo IOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Os aplicativos podem usar o API do Graph para chamar operações de leitura sem credenciais de usuário <!-- 4655885 -->
Os aplicativos podem chamar o Intune API do Graph operações de leitura com a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Aplicar marcas de escopo a Microsoft Store para aplicativos de negócios <!-- 4392555 -->
Agora você pode aplicar marcas de escopo a Microsoft Store para aplicativos de negócios. Para obter mais informações sobre marcas de escopo, consulte [usar o controle de acesso baseado em função (RBAC) e marcas de escopo para distribuí-lo](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Semana de 17 de junho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-features-in-microsoft-intune-app"></a>Novos recursos no aplicativo Microsoft Intune
Adicionamos novos recursos ao aplicativo Microsoft Intune (versão prévia) para Android. Os usuários em dispositivos Android totalmente gerenciados agora podem:  

* Exiba e gerencie os dispositivos registrados por meio do Portal da Empresa do Intune ou Microsoft Intune aplicativo.    
* Entre em contato com a organização para obter suporte.    
* Envie seus comentários para a Microsoft.    
* Exiba os termos e condições, se definido por sua organização.    

## <a name="week-of-june-10-2019"></a>Semana de 10 de junho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Novos aplicativos de exemplo mostrando a integração do SDK do Intune disponível no GitHub <!-- 2653471 -->
A conta do GitHub msintuneappsdk adicionou novos aplicativos de exemplo para iOS (Swift), Android, Xamarin. iOS, Xamarin Forms e Xamarin. Android. Esses aplicativos destinam-se a complementar nossa documentação existente e fornecem demonstrações de como integrar o SDK de aplicativos do Intune em seus próprios aplicativos móveis. Se você for um desenvolvedor de aplicativos que precisa de diretrizes adicionais do SDK do Intune, consulte os seguintes exemplos vinculados:
- [Chat](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) -um aplicativo de mensagens instantâneas Ios (Swift) nativo que usa a Adal (biblioteca de autenticação Azure Active Directory) para autenticação orientada.
- [Tasker](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) -um aplicativo de lista de tarefas do Android nativo que usa a Adal para autenticação orientada.
- [Tasker](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) -um aplicativo de lista de tarefas do Xamarin. Android que usa a Adal para autenticação orientada, esse repositório também tem o aplicativo Xamarin. Forms.
- [Aplicativo de exemplo do xamarin. Ios](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – um aplicativo de exemplo básicas Xamarin. Ios.

## <a name="week-of-may-27-2019"></a>Semana de 27 de maio de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Relatórios de aplicativos potencialmente prejudiciais em dispositivos Android <!-- 4223162 -->
O Intune agora fornece informações de relatório adicionais sobre aplicativos potencialmente prejudiciais em dispositivos Android. 

## <a name="week-of-may-20-2019"></a>Semana de 20 de maio de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="windows-company-portal-app----3316993---"></a>Aplicação do Portal da Empresa do Windows <!-- 3316993 -->
O aplicativo Windows Portal da Empresa agora terá uma nova página rotulada **dispositivos**. A página **dispositivos** mostrará os usuários finais todos os seus dispositivos registrados. Os usuários verão essa alteração na Portal da Empresa quando usarem a versão 10.3.4291.0 e posterior. Para obter informações sobre como configurar o Portal da Empresa, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](company-portal-app.md).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nome do atributo NúmeroDoPedido do dispositivo AutoPilot alterado para a marca de grupo <!-- 4659453 -->

Para torná-lo mais intuitivo, o nome do atributo **NúmeroDoPedido** em dispositivos AutoPilot foi alterado para a **marca de grupo**. Ao usar o CSVs para carregar as informações do dispositivo AutoPilot, você deve usar a marca Group como o cabeçalho da coluna, não OrderID.  

## <a name="week-of-may-13-2019"></a>Semana de 13 de maio de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>As políticas do Intune atualizam o método de autenticação e Portal da Empresa instalação do aplicativo  <!-- 1927359  -->
Em dispositivos já registrados por meio do assistente de configuração por meio de um dos métodos de registro de dispositivo corporativo da Apple, o Intune não dará mais suporte ao Portal da Empresa quando ele é instalado manualmente pelos usuários finais da loja de aplicativos. Esta alteração é relevante apenas quando se autenticar com o Assistente de configuração da Apple durante a inscrição. Esta alteração afeta também apenas dispositivos iOS inscritos através de:  
* Do Apple configurator

* Gerente de negócios da Apple

* Gestor Escolar da Apple

* Programa de inscrição de dispositivos Apple (DEP)

Se os utilizadores instalarem a aplicação Portal da empresa a partir da App store e, em seguida, tentar inscrever estes dispositivos através do mesmo, receberá um erro. Esses dispositivos deverão usar apenas o Portal da Empresa quando ele for enviado por push, automaticamente, pelo Intune durante o registro. Perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Se pretender que os utilizadores de dispositivos do DEP para o portal da empresa, terá de especificar as suas preferências num perfil de inscrição. 

Além disso, a tela **identificar seu dispositivo** no portal da empresa do IOS está sendo removida. Portanto, os administradores que desejam habilitar o acesso condicional ou implantar aplicativos da empresa devem atualizar o perfil de registro do DEP. Esse requisito só se aplicará se o registro de DEP for autenticado com o assistente de configuração. Nesse caso, você deve enviar o Portal da Empresa para o dispositivo. Para fazer isso, escolha**registro** > de dispositivo do **Intune** > **tokens do programa** de registro da**Apple** > > escolha um token > **perfis** > escolha um perfil >  **Propriedades** > definir **instalar portal da empresa** como **Sim**.

Para instalar o Portal da Empresa em dispositivos DEP já registrados, você precisará acessar os aplicativos cliente do Intune > e enviá-los como um aplicativo gerenciado com as políticas de configuração de aplicativo. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurar como os usuários finais atualizam um aplicativo de linha de negócios (LOB) usando uma política de proteção de aplicativo <!-- 3568384 -->
Agora você pode configurar onde os usuários finais podem obter uma versão atualizada de um aplicativo de linha de negócios (LOB). Os usuários finais verão esse recurso na caixa de diálogo de inicialização condicional **versão do aplicativo mín** , que solicitará que os usuários finais atualizem para uma versão mínima do aplicativo LOB. Você deve fornecer esses detalhes de atualização como parte de sua política de proteção de aplicativo LOB (aplicativo). Esse recurso está disponível no iOS e no Android. No iOS, esse recurso requer que o aplicativo seja integrado (ou encapsulado usando a ferramenta de encapsulamento) com o SDK do Intune para iOS v. 10.0.7 ou superior. No Android, esse recurso exigiria a Portal da Empresa mais recente. Para configurar como um usuário final atualiza um aplicativo LOB, o aplicativo precisa de uma política de configuração de aplicativo gerenciado enviada a ele com `com.microsoft.intune.myappstore`a chave,. O valor enviado definirá a qual armazenamento o usuário final fará o download do aplicativo. Se o aplicativo for implantado por meio do Portal da Empresa, o `CompanyPortal`valor deverá ser. Para qualquer outro armazenamento, você deve inserir uma URL completa.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Scripts do PowerShell de extensão de gerenciamento do Intune  <!-- 3734186  -->
Você pode configurar scripts do PowerShell para serem executados com os privilégios de administrador do usuário no dispositivo. Para obter mais informações, consulte [usar scripts do PowerShell em dispositivos Windows 10 no Intune](intune-management-extension.md) e gerenciamento de aplicativos do [Win32](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Gerenciamento de aplicativo empresarial do Android <!-- 4459905 -->
Para facilitar para os administradores de ti configurar e usar o gerenciamento do Android Enterprise, o Intune adicionará automaticamente quatro aplicativos comuns do Android Enterprise ao console de administração do Intune. Os quatro aplicativos do Android Enterprise são os seguintes aplicativos:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** -usados para cenários totalmente gerenciados do Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -ajuda você a entrar em suas contas se usar a verificação de dois fatores.
- **[Portal da empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** -usado para as políticas de proteção de aplicativo (aplicativo) e cenários de perfil de trabalho do Android Enterprise.
- [Tela inicial gerenciada](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -usada para cenários do Android Enterprise dedicado/quiosque.

Anteriormente, os administradores de ti precisariam localizar e aprovar manualmente esses aplicativos no [repositório de Google Play gerenciado](https://play.google.com/store/apps) como parte da instalação. Essa alteração remove as etapas manuais anteriores para tornar mais fácil e rápido para os clientes usarem o gerenciamento do Android Enterprise.

Os administradores verão esses quatro aplicativos automaticamente adicionados à lista de aplicativos do Intune no momento em que eles conectam seu locatário do Intune pela primeira vez a Google Play gerenciadas. Para obter mais informações, consulte [conectar sua conta do Intune à sua conta do Google Play gerenciado](connect-intune-android-enterprise.md). Para locatários que já conectaram seu locatário ou que já usam o Android Enterprise, não há nada que os administradores precisem fazer. Esses quatro aplicativos aparecerão automaticamente dentro de 7 dias após a conclusão da distribuição do serviço de maio de 2019.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Conector de certificado PFX atualizado para Microsoft Intune  <!-- 1533038 -->
Lançamos uma atualização para o [conector de certificado pfx para Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) que aborda um problema em que os certificados PFX existentes continuam a ser reprocessados, o que faz com que o conector pare de processar novas solicitações.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Tarefas de segurança do Intune para o defender ATP (em visualização pública)     <!-- 3208597 -->
Na visualização pública, você pode usar o Intune para gerenciar [tarefas de segurança para a ATP (proteção avançada contra ameaças) do Microsoft defender](atp-manage-vulnerabilities.md). Essa integração com ATP e adiciona uma abordagem baseada em risco para descobrir, priorizar e corrigir vulnerabilidades de ponto de extremidade e configurações incorretas, reduzindo o tempo entre a descoberta e a mitigação.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Verificar um chipset TPM em uma política de conformidade de dispositivo do Windows 10 <!-- 3617671   idstaged-->
Muitos dispositivos Windows 10 e posteriores têm chipsets Trusted Platform Module (TPM). Essa atualização inclui uma nova configuração de conformidade que verifica a versão do chip do TPM no dispositivo. 

[As configurações de política de conformidade do Windows 10 e posteriores](compliance-policy-create-windows.md#device-security) descrevem essa configuração.

Aplica-se a: Windows 10 e posterior

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Impedir que os usuários finais modifiquem seus HotSpots pessoais e desabilitem o log do servidor Siri em dispositivos iOS <!-- 4097904   -->  
Você cria um perfil de restrições de dispositivo no dispositivo IOS (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o perfil tipo). Essa atualização inclui novas configurações que você pode configurar:

- **Aplicativos internos**: Registro em log do lado do servidor para comandos Siri
- **Sem fio**: Modificação do usuário de hotspot pessoal (somente supervisionado)

Para ver essas configurações, vá para [configurações de aplicativo interno para IOS](device-restrictions-ios.md#built-in-apps) e [configurações sem fio para IOS](device-restrictions-ios.md#wireless).

Aplica-se a: iOS 12,2 e mais recente

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Novas configurações de restrição de dispositivo de aplicativo de sala de aula para dispositivos macOS <!-- 4097905   --> 
Você pode criar perfis de configuração de dispositivo para dispositivos MacOS (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **MacOS** para plataforma > **restrições de dispositivo** para tipo de perfil). Essa atualização inclui novas configurações de aplicativo de sala de aula, a opção de bloquear capturas de tela e a opção de desabilitar a biblioteca de fotos do iCloud.

Para ver as configurações atuais, vá para [configurações do dispositivo MacOS para permitir ou restringir recursos usando o Intune](device-restrictions-macos.md).

Aplica-se a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>A configuração de senha do iOS para acessar a loja de aplicativos foi renomeada<!-- 4557891  -->
A **configuração senha para acessar a loja de aplicativos** é renomeada para exigir a **senha da iTunes Store para todas as compras** (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Ios** para a plataforma > **restrições de dispositivo** para o tipo de perfil > loja de **aplicativos, exibição de documentos e jogos**).

Para ver as configurações disponíveis, vá para [loja de aplicativos, exibição de documento, configurações de jogos do IOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Linha de base da proteção avançada contra ameaças do Microsoft defender (versão prévia)  <!--  3754134 -->
Adicionamos uma visualização de linha de base de segurança para as configurações de [proteção avançada contra ameaças do Microsoft defender](security-baseline-settings-defender-atp.md) . Essa linha de base está disponível quando seu ambiente atende aos pré-requisitos para usar a [proteção avançada contra ameaças do Microsoft defender](advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>A página de status de registro do Windows (ESP) já está disponível para o público geral <!-- 3605348 -->
A página de status de registro agora está fora de visualização. Para obter mais informações, consulte [Configurar uma página de status de registro](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Atualização da interface do usuário do Intune-criação do perfil de registro do AutoPilot  <!-- 4593669 -->
A interface do usuário para criar um perfil de registro do AutoPilot foi atualizada para se alinhar com os estilos de interface do usuário do Azure. Para obter mais informações, consulte [criar um perfil de registro do AutoPilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile). Avançando, os cenários adicionais do Intune serão atualizados para esse novo estilo de interface do usuário.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Habilitar a redefinição do AutoPilot para todos os dispositivos Windows <!-- 4225665 -->
A redefinição do AutoPilot agora funciona para todos os dispositivos Windows, mesmo aqueles não configurados para usar a página status do registro. Se uma página de status de registro não tiver sido configurada para o dispositivo durante o registro inicial do dispositivo, o dispositivo passará diretamente para a área de trabalho após a entrada. Pode levar até oito horas para sincronizar e aparecer em conformidade no Intune. Para obter mais informações, consulte [Redefinir dispositivos com a redefinição remota do piloto automático do Windows](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Formato IMEI exato não necessário ao pesquisar todos os dispositivos <!--30407680 -->
Você não precisará incluir espaços em números IMEI ao pesquisar **todos os dispositivos**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>A exclusão de um dispositivo no portal da Apple será refletida no portal do Intune <!--2489996 -->
Se um dispositivo for excluído dos portais da Apple Programa de registro de dispositivos ou do Apple Business Manager, o dispositivo será excluído automaticamente do Intune durante a próxima sincronização.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>A página de status de registro agora rastreia aplicativos Win32 <!-- 2714451 -->
Isso se aplica somente a dispositivos que executam o Windows 10 versão 1903 e posterior. Para obter mais informações, consulte [Configurar uma página de status de registro](windows-enrollment-status.md).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Redefinir e apagar dispositivos em massa usando o API do Graph <!-- 3295288 -->
Agora você pode redefinir e apagar até 100 dispositivos em massa usando o API do Graph.


### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>O relatório de criptografia está fora de visualização pública   <!-- 4587546      -->
O [relatório para BitLocker e criptografia de dispositivo](encryption-monitor.md) agora está disponível para o público geral e não faz mais parte da visualização pública. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Assinatura do Outlook e configurações biométricas para dispositivos iOS e Android <!-- 4050557 -->
Agora você pode especificar se a assinatura padrão está habilitada no Outlook em dispositivos iOS e Android. Além disso, você pode optar por permitir que os usuários alterem a configuração biométrica no Outlook no iOS.

## <a name="week-of-may-6-2019"></a>Semana de 6 de maio de 2019 

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Suporte ao controle de acesso à rede (NAC) para acesso de F5 para dispositivos iOS <!-- 4500808 -->

F5 lançou uma atualização para BIG-IP 13 que permite a funcionalidade de NAC para acesso F5 no iOS no Intune. Para usar esse recurso:

- Atualize BIG-IP para 13.1.1.5 Refresh. Não há suporte para BIG-IP 14.
- Integre BIG-IP ao Intune para NAC. Etapas na [visão geral: Configurar o APM para verificações de postura de dispositivo com](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)sistemas de gerenciamento de ponto de extremidade.
- Marque a configuração **habilitar o controle de acesso à rede (NAC)** no perfil VPN no Intune.

Para ver a configuração disponível, vá para [definir configurações de VPN em dispositivos IOS](vpn-settings-ios.md).

Aplica-se a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Conector de certificado PFX atualizado para Microsoft Intune <!-- doc-vso 1521237  -->  
Lançamos uma atualização para o [conector de certificado pfx para Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) que descarta o intervalo de sondagem de 5 minutos a 30 segundos.

## <a name="week-of-april-22-2019"></a>Semana de 22 de abril de 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Use o Compliance Manager para criar Avaliações para Microsoft Intune<!-- 4404750 -->

[Gerente de conformidade](https://servicetrust.microsoft.com/ComplianceManager) (abre outro site da Microsoft) é uma ferramenta de avaliação de riscos baseada em fluxo de trabalho no portal de confiança do serviço da Microsoft. Ele permite que você controle, atribua e verifique as atividades de conformidade regulatória de sua organização relacionadas aos serviços da Microsoft. Você pode criar sua própria avaliação de conformidade com o Office 365, o Azure, o Dynamics, os serviços profissionais e o Intune. O Intune tem duas avaliações disponíveis – FFIEC e GDPR.

O Compliance Manager ajuda você a concentrar seus esforços dividindo controles – controles gerenciados pela Microsoft e controles gerenciados por sua organização. Você pode concluir as avaliações e, em seguida, exportar e imprimir as avaliações.

[FFIEC (Conselho de exame de instituições financeiras federais)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (abre outro site da Microsoft) a conformidade é um conjunto de padrões para o banco online emitido pelo FFIEC. É a avaliação mais solicitada para instituições financeiras que usam o Intune. Ele interpreta como o Intune ajuda a atender às diretrizes do FFIEC segurança cibernética relacionadas a cargas de trabalho de nuvem pública. A avaliação do FFIEC do Intune é a segunda avaliação do FFIEC no Compliance Manager.

No exemplo a seguir, você pode ver a divisão dos controles do FFIEC. A Microsoft abrange 64 controles. Você é responsável pelos 12 controles restantes.

![Consulte uma avaliação do Intune de exemplo para o FFIEC, incluindo as ações do cliente e as ações da Microsoft](./media/intune-ffiec-assessment-status.png)

[Regulamento geral sobre a proteção de dados (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (abre outro site da Microsoft) é uma lei da União Europeia (UE) que ajuda a proteger os direitos de indivíduos e seus dados. O GDPR é a avaliação mais solicitada para ajudar a cumprir os regulamentos de privacidade. 

No exemplo a seguir, você verá a divisão dos controles GDPR. A Microsoft abrange 49 controles. Você é responsável pelos demais controles 66.

![Consulte uma avaliação do Intune de exemplo para GDPR, incluindo as ações do cliente e as ações da Microsoft](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Semana de 15 de abril de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Criptografia OpenSSL para políticas de proteção de aplicativo Android <!-- 3747362 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android agora usam uma biblioteca de criptografia OpenSSL que é compatível com FIPS 140-2. Para obter mais informações, consulte a seção [criptografia](app-protection-policy-settings-android.md#encryption) das [configurações de política de proteção de aplicativo Android em Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Habilitar dependências de aplicativo Win32 <!-- 2617348  -->
Como administrador, você pode exigir que outros aplicativos sejam instalados como dependências antes de instalar seu aplicativo Win32. Especificamente, o dispositivo deve instalar os aplicativos dependentes antes de instalar o aplicativo Win32. No Intune, selecione **aplicativos** >  > cliente aplicativos**Adicionar** para exibir a folha **Adicionar aplicativo** . Selecione **aplicativo do Windows (Win32)** como o **tipo de aplicativo**. Depois de adicionar o aplicativo, você pode selecionar **dependências** para adicionar os aplicativos dependentes que devem ser instalados antes que o aplicativo Win32 possa ser instalado. Para obter mais informações, consulte [Intune autônomo-gerenciamento de aplicativos do Win32](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Informações de instalação de versão do aplicativo para Microsoft Store para aplicativos de negócios <!-- 3537391   -->
Os relatórios de instalação do aplicativo incluem informações de versão do aplicativo para Microsoft Store para aplicativos de negócios. No Intune, selecione**aplicativos**de **aplicativos** > cliente. Selecione um **Microsoft Store para o aplicativo de negócios** e selecione o **status de instalação do dispositivo** na seção **monitorar** .

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Adições a regras de requisito de aplicativos Win32 <!-- 3676883   -->
Você pode criar regras de requisitos com base em scripts do PowerShell, valores de registro e informações do sistema de arquivos. No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Em seguida, selecione **aplicativo do Windows (Win32)** como o **tipo de aplicativo** na folha **Adicionar aplicativo** .  Selecione **requisitos** > **Adicionar** para configurar regras de requisito adicionais. Em seguida, selecione o **tipo de arquivo**, o **registro**ou o **script** como o **tipo de requisito**. Para obter mais informações, consulte [Win32 app Management](apps-win32-app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurar seus aplicativos Win32 para serem instalados em dispositivos adicionados ao Azure AD registrados no Intune <!-- 3695227  -->
Você pode atribuir seus aplicativos Win32 para serem instalados em dispositivos ingressados no Azure AD registrados no Intune. Para obter mais informações sobre aplicativos Win32 no Intune, consulte [Gerenciamento de aplicativos Win32](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---3794259----"></a>Visão geral do dispositivo mostra o usuário principal <!--3794259  -->
A página Visão geral do dispositivo mostrará o usuário primário, também chamado de usuário de afinidade de dispositivo de usuário (UDA). Para ver o usuário primário de um dispositivo, escolha**dispositivos** > do **Intune** > **todos os dispositivos** > escolha um dispositivo. O usuário primário será exibido próximo à parte superior da página **visão geral** .

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Relatórios adicionais da aplicação do Managed Google Play para dispositivos de perfil de trabalho do Android Enterprise <!-- 4105925  -->
Para as aplicações do Managed Google Play implementadas para dispositivos de perfil de trabalho do Android Enterprise, pode ver o número de versão específica da aplicação instalada num dispositivo. Tal só se aplica às aplicações obrigatórias.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>teclados de terceiros do iOS <!-- 4111843   -->
O suporte de política de proteção de aplicativo do Intune (aplicativo) para a configuração de **teclados de terceiros** para IOS não é mais suportado devido a uma alteração na plataforma Ios. Você não poderá definir essa configuração no console de administração do Intune e ela não será imposta no cliente no SDK do aplicativo do Intune.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Definir configurações de logon e opções de reinicialização de controle em dispositivos macOS <!-- 1210083  -->
Em dispositivos MacOS, você pode criar um perfil de configuração de dispositivo (**perfis** > de**configuração** > de dispositivo**Criar perfil** > escolher **MacOS** para plataforma > **recursos de dispositivo** para o perfil tipo). Essa atualização inclui novas configurações de janela de logon, como mostrar uma faixa personalizada, escolher como os usuários entram, mostrar ou ocultar as configurações de energia e muito mais.

Para ver essas configurações, vá para [configurações de recurso do dispositivo MacOS](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurar o WiFi no Android Enterprise, dispositivos dedicados de proprietário do dispositivo em execução no modo de quiosque de vários aplicativos <!--3041940  -->
Você pode habilitar as configurações no Android Enterprise, o proprietário do dispositivo ao executar como um dispositivo dedicado no modo de quiosque de vários aplicativos. Nessa atualização, você pode permitir que os usuários configurem e se conectem a redes wifi (**perfis** > de**configuração** > de dispositivo do**Intune** > **Criar perfil** > **Android Enterprise** para plataforma > **somente proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil >**modo de quiosque**de **dispositivos** > dedicados: > **Configuração do wifi**de vários aplicativos). 

Para ver todas as configurações que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos](device-restrictions-android-for-work.md).

Aplica-se a: Dispositivos Android Enterprise dedicados em execução no modo de quiosque de vários aplicativos


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurar o Bluetooth e o emparelhamento no Android Enterprise, dispositivos dedicados de proprietário do dispositivo em execução no modo de quiosque de vários aplicativos <!-- 3041941  -->
Você pode habilitar as configurações no Android Enterprise, o proprietário do dispositivo ao executar como um dispositivo dedicado no modo de quiosque de vários aplicativos. Nessa atualização, você pode permitir que os usuários finais habilitem o Bluetooth e Emparelhem dispositivos via Bluetooth (**perfis** > de**configuração** > de dispositivo do**Intune** > **Criar perfil**  >   **Android Enterprise** para plataforma > **somente proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil >**modo de quiosque**de **dispositivos** > dedicados: **Configuração de Bluetooth de vários aplicativos** > ). 

Para ver todas as configurações que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos](device-restrictions-android-for-work.md).

Aplica-se a: Dispositivos Android Enterprise dedicados em execução no modo de quiosque de vários aplicativos

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Criar e usar perfis de configuração de dispositivo OEMConfig no Intune <!-- 3305883  -->
Nesta atualização, o Intune dá suporte à configuração de dispositivos Android Enterprise com OEMConfig. Especificamente, você pode criar um perfil de configuração de dispositivo e aplicar configurações a dispositivos Android Enterprise usando OEMConfig (**perfis** > de**configuração** > do dispositivo**Criar perfil**  >   **Android Enterprise** para plataforma).

O suporte para OEMs está atualmente em uma base por OEM. Se um aplicativo OEMConfig que você deseja não estiver disponível na lista de aplicativos OEMConfig, `IntuneOEMConfig@microsoft.com`contate.

Para saber mais sobre esse recurso, acesse [usar e gerenciar dispositivos Android Enterprise com o OEMConfig em Microsoft Intune](android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notificações de Windows Update  <!-- 3316758, 3316782  -->
Adicionamos duas *configurações de experiência do usuário* às configurações de Windows Update Ring que você pode gerenciar no console do Intune. Agora você pode:
- Bloquear ou permitir que os usuários [verifiquem se há atualizações do Windows](windows-update-settings.md).
- Gerencie o [nível de notificação Windows Update](windows-update-settings.md) que os usuários veem.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Novas configurações de restrição de dispositivo para Android Enterprise, proprietário do dispositivo <!-- 3574254  -->
Em dispositivos Android Enterprise, você pode criar um perfil de restrição de dispositivo para permitir ou restringir recursos, definir regras de senha e mais (**perfis** > de**configuração** > do dispositivo**Criar perfil** > escolher  **Android Enterprise** para plataforma > **proprietário do dispositivo apenas > restrições de dispositivo** para o tipo de perfil). 

Essa atualização inclui novas configurações de senha, permite acesso completo a aplicativos em Google Play Store para dispositivos totalmente gerenciados e muito mais. Para ver a lista atual de configurações, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos](device-restrictions-android-for-work.md). 

Aplica-se a: Dispositivos Android Enterprise totalmente gerenciados

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verificar um chipset TPM em uma política de conformidade de dispositivo do Windows 10 <!-- 3617671 -->

Esse recurso está atrasado e está planejado para ser lançado posteriormente.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Alterações de interface do usuário atualizadas para o navegador Microsoft Edge em dispositivos Windows 10 e posteriores <!-- 3775833   -->
Ao criar um perfil de configuração de dispositivo, você pode permitir ou restringir recursos do Microsoft Edge no Windows 10 e em dispositivos posteriores (**perfis** > de**configuração** > de dispositivo**Criar perfil**  >   **Windows 10 e posterior** para plataforma, > **restrições de dispositivo** para o tipo de perfil > **navegador Microsoft Edge**). Nessa atualização, as configurações do Microsoft Edge são mais descritivas e mais fáceis de entender. 

Para ver esses recursos, acesse [navegador Microsoft Edge configurações de restrição de dispositivo](device-restrictions-windows-10.md#microsoft-edge-browser).

Aplica-se a: Windows 10 e posterior

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Suporte expandido para dispositivos Android Enterprise totalmente gerenciados (versão prévia)  <!--   3903241, 3903244, 3903246   -->
Ainda em uma visualização pública, expandimos nosso suporte de dispositivos Android Enterprise totalmente gerenciados ([lançados primeiro em janeiro de 2019](whats-new.md#week-of-january-14-2019) para incluir o seguinte: 

- Em dispositivos totalmente gerenciados e dedicados, você pode criar [políticas de conformidade](compliance-policy-create-android-for-work.md) para incluir regras de senha e requisitos de sistema operacional (**políticas** > de**conformidade** > do dispositivo**criar política**  >  **Android Enterprise** para plataforma > **proprietário do dispositivo** para o tipo de perfil). 

  Em dispositivos dedicados, o dispositivo pode mostrar como **não compatível**. O acesso condicional não está disponível em dispositivos dedicados. Realize algumas tarefas ou ações para que os dispositivos dedicados fiquem em conformidade com as políticas atribuídas.

- [Acesso condicional](conditional-access.md) -políticas de acesso condicional que se aplicam ao Android também se aplicam a dispositivos Android Enterprise totalmente gerenciados. Agora, os usuários podem registrar seu dispositivo totalmente gerenciado no Azure Active Directory usando o **aplicativo Microsoft Intune**. Em seguida, consulte e resolva quaisquer problemas de conformidade para acessar recursos organizacionais.

- Novo aplicativo de usuário final (Microsoft Intune aplicativo) – há um novo aplicativo de usuário final para dispositivos Android totalmente gerenciados chamado **Microsoft Intune**. Esse novo aplicativo é leve e moderno e fornece uma funcionalidade semelhante à do Portal da Empresa aplicativo, mas para dispositivos totalmente gerenciados. Para obter mais informações, consulte [Microsoft Intune aplicativo em Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Para configurar dispositivos Android totalmente gerenciados, vá para **registro** > de dispositivo registro do**Android** > **dispositivos de usuário totalmente gerenciados e de propriedade corporativa**. O suporte para dispositivos Android totalmente gerenciados permanece em versão prévia, e alguns recursos do Intune podem não estar totalmente funcionais.  

Para saber mais sobre essa visualização, consulte nosso blog, [Microsoft Intune-Preview 2 para dispositivos Android Enterprise totalmente gerenciados](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configurar o perfil para ignorar algumas telas durante o assistente de configuração <!-- 2276470  -->
Ao criar um perfil de registro do macOS, você pode configurá-lo para ignorar qualquer uma das telas a seguir quando um usuário passar pelo assistente de configuração:
- Aparência
- Sinal de Exibição
- iCloudStorage se você criar um novo perfil ou editar um perfil, as telas ignorar selecionadas precisarão ser sincronizadas com o servidor MDM da Apple.  Os usuários podem emitir uma sincronização manual dos dispositivos para que não haja atraso na separação das alterações de perfil.
Para obter mais informações, consulte [registrar automaticamente dispositivos MacOS com o programa de registro de dispositivos ou o Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Nomeação de dispositivo em massa ao registrar dispositivos iOS corporativos<!--3566569  -->
Ao usar um dos métodos de registro corporativo da Apple (DEP/ABM/ASM), você pode definir um formato de nome de dispositivo para nomear automaticamente dispositivos iOS de entrada. Você pode especificar um formato que inclua o tipo de dispositivo e o número de série em seu modelo. Para fazer isso, escolha**registro** > de dispositivo do **Intune** > **tokens** > do programa de registro da**Apple** > **selecionar um token** >**criar**  > **formato de nomenclatura do dispositivo**de perfil. Você pode editar perfis existentes, mas somente os dispositivos recém sincronizados terão o nome aplicado.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Mensagem de tempo limite padrão atualizada na página de status do registro <!-- 3959331 -->
Atualizamos a mensagem de tempo limite padrão que os usuários veem quando a página de status de registro (ESP) excede o valor de tempo limite especificado no perfil ESP. A nova mensagem padrão é o que os usuários veem e os ajuda a entender as próximas ações a serem executadas com a implantação do ESP.  

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Desativar dispositivos não compatíveis  <!-- 1827291   -->
Esse recurso foi atrasado e está planejado para uma versão futura.


### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Alterações do Intune data warehouse V 1.0 refletindo de volta para a versão beta <!-- 4403765 -->
Quando o V 1.0 foi introduzido pela primeira vez em 1808, ele difere de algumas maneiras significativas da API beta. Em 1903, essas alterações serão refletidas de volta para a versão da API beta. Se você tiver relatórios importantes que usam a versão da API beta, é altamente recomendável trocar esses relatórios para V 1.0 para evitar alterações significativas. Para obter mais informações, consulte [log de alterações para a API de data warehouse do Intune](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorar o status da linha de base de segurança (visualização pública) <!-- 3082047 --> 
Adicionamos uma [exibição por categoria](security-baselines-monitor.md#per-category-view) ao monitoramento de linhas de base de segurança. (As linhas de base de segurança permanecem na versão prévia). A exibição por categoria exibe cada categoria da linha de base junto com a porcentagem de dispositivos que se enquadram em cada grupo de status dessa categoria. Agora você pode ver quantos dispositivos não correspondem às categorias individuais, estão configurados incorretamente ou não são aplicáveis.

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Marcas de escopo para tokens de VPP da Apple <!--2371886  -->
Agora você pode adicionar marcas de escopo a tokens de VPP da Apple. Somente os usuários atribuídos com a mesma marca de escopo terão acesso ao token do Apple VPP com essa marca. Os aplicativos VPP e os livros eletrônicos adquiridos com esse token herdam suas marcas de escopo. Para obter mais informações sobre marcas de escopo, consulte [usar RBAC e marcas de escopo](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Semana de 1º de abril de 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Conectores de certificado atualizados  <!-- ICM 113304612 -->
Lançamos atualizações para o conector de [certificado do Intune e o conector de certificado pfx para Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors). As novas versões corrigem vários problemas conhecidos.  

### <a name="app-management"></a>Gestão de aplicações

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS <!-- 2536024 -->
O home page do aplicativo Portal da Empresa para dispositivos iOS foi reprojetado. Com essa alteração, a home page seguirá melhor os padrões da interface do usuário do iOS e também proporcionará uma capacidade de descoberta aprimorada para aplicativos e livros eletrônicos.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Alterações no registro de Portal da Empresa para usuários do dispositivo iOS 12 <!--3448635 -->  
As Portal da Empresa para as telas e etapas de registro do iOS foram atualizadas para alinhar com as alterações de registro do MDM lançadas no Apple iOS 12,2. O fluxo de trabalho atualizado solicita que os usuários:  

* Permita que o Safari Abra o site Portal da Empresa e baixe o perfil de gerenciamento antes de retornar ao aplicativo Portal da Empresa.  
* Abra o aplicativo configurações para instalar o perfil de gerenciamento em seu dispositivo.
* Retorne ao aplicativo Portal da Empresa para concluir o registro.  

Para ver as etapas e telas de registro atualizadas, consulte [registrar dispositivo IOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Semana de 25 de março de 2019

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Suporte para o aplicativo de conformidade de Power BI da folha de data warehouse no Microsoft Intune <!-- 4260871 -->
Anteriormente, o link **baixar Power bi arquivo** na folha **data warehouse do Intune** baixou um relatório data warehouse do Intune (arquivo. pbix). Este relatório foi substituído pelo aplicativo de conformidade Power BI. O aplicativo de conformidade Power BI não exigirá carregamento ou configuração especial. Ele será aberto diretamente no portal do Power BI online e exibirá dados especificamente para seu locatário do Intune com base em suas credenciais. No Intune, selecione o link **configurar data warehouse do Intune** no lado direito da folha do Intune. Em seguida, clique em **obter Power bi aplicativo**. Para obter mais informações, consulte [conectar-se ao data warehouse com Power bi](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Semana de 18 de março de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Implantar o Microsoft Visio e o Microsoft Project <!-- 3725386  -->
Agora você pode implantar o Microsoft Visio pro para Office 365 e o cliente de área de trabalho do Microsoft Project online como aplicativos independentes em dispositivos Windows 10 usando Microsoft Intune, se você tiver licenças para esses aplicativos. No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar** para exibir a folha **Adicionar aplicativo** . Na folha **Adicionar aplicativo** , selecione **Windows 10** como o **tipo de aplicativo**. Em seguida, selecione **Configurar pacote de aplicativos** para selecionar os aplicativos a serem instalados. Para obter mais informações sobre os aplicativos do Office 365 para dispositivos Windows 10, consulte [atribuir aplicativos do office 365 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Alteração do nome do produto Microsoft Visio pro para Office 365 <!-- 3593653  -->
**O Microsoft Visio pro para Office 365** agora será conhecido como **Microsoft Visio online plano 2**.  Para obter mais informações sobre o Microsoft Visio, consulte [Visio online plano 2](https://products.office.com/visio/visio-online-plan-2). Para obter mais informações sobre os aplicativos do Office 365 para dispositivos Windows 10, consulte [atribuir aplicativos do office 365 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Configuração de limite de caracteres da política de proteção de aplicativo do Intune (aplicativo) <!-- 3291302  -->
Os administradores do Intune podem especificar uma exceção ao aplicativo do Intune **restringir recortar, copiar e colar com a configuração de política de outros aplicativos** .  Como administrador, você pode especificar o número de caracteres que podem ser recortados ou copiados de um aplicativo gerenciado. Essa configuração permitirá o compartilhamento do número especificado de caracteres para qualquer aplicativo, independentemente da configuração "restringir recortar, copiar e colar com outros aplicativos". Observe que a versão do aplicativo Portal da Empresa do Intune para Android requer a versão 5.0.4364.0 ou posterior. Para obter mais informações, consulte [proteção de dados Ios](app-protection-policy-settings-ios.md#data-protection), [proteção de dados Android](app-protection-policy-settings-android.md#data-protection)e [análise de logs de proteção de aplicativo cliente](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Ferramenta de implantação do Office (ODT) XML para implantação do Office ProPlus <!-- 3192477   -->
Você poderá fornecer o XML da ferramenta de implantação do Office (ODT) ao criar uma instância do Office Pro Plus no console de administração do Intune. Isso permitirá maior personalização se as opções de interface do usuário do Intune existentes não atenderem às suas necessidades. Para obter mais informações, consulte [atribuir aplicativos do Office 365 a dispositivos Windows 10 com Microsoft Intune](apps-add-office365.md) e [Opções de configuração para a ferramenta de implantação do Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Os ícones de aplicativo agora serão exibidos com um plano de fundo gerado automaticamente <!-- 1429026  -->
No aplicativo Windows Portal da Empresa, os ícones de aplicativo agora serão exibidos com um plano de fundo gerado automaticamente com base na cor dominante do ícone (se puder ser detectado). Quando aplicável, esse plano de fundo substituirá a borda cinza que estava visível anteriormente nos blocos do aplicativo. Os usuários verão essa alteração nas versões do Portal da Empresa posteriores a 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Instalar aplicativos disponíveis usando o aplicativo Portal da Empresa após o registro em massa do Windows <!-- 2751523   -->
Os dispositivos Windows registrados no Intune usando o [registro em massa do Windows](windows-bulk-enroll.md) (pacotes de provisionamento) poderão usar o aplicativo portal da empresa para instalar os aplicativos disponíveis. Para obter mais informações sobre o aplicativo Portal da Empresa, consulte [adicionar manualmente o portal da empresa do Windows 10](store-apps-company-portal-app.md) e [como configurar o aplicativo Microsoft Intune portal da empresa](company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>O aplicativo Microsoft Teams pode ser selecionado como parte do pacote de aplicativos do Office <!-- 3828932  -->
O aplicativo Microsoft Teams pode ser incluído ou excluído como parte da instalação do Office Pro Plus app Suite. Esse recurso funciona para o Office Pro Plus número de Build 16.0.11328.20116 +. O usuário deve sair e, em seguida, entrar no dispositivo para que a instalação seja concluída. No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Selecione um dos tipos de aplicativo do **pacote do Office 365** e, em seguida, selecione **Configurar pacote de aplicativos**.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Iniciar automaticamente um aplicativo ao executar vários aplicativos no modo de quiosque em dispositivos Windows 10 e posteriores <!-- 2351390 -->

No Windows 10 e em dispositivos posteriores, você pode executar um dispositivo no modo de quiosque e executar muitos aplicativos. Nessa atualização, há uma configuração de **inicialização** automática (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Windows 10 e posterior** para plataforma > **quiosque** para tipo de perfil > **quiosque de vários aplicativos**). Use essa configuração para iniciar automaticamente um aplicativo quando o usuário entrar no dispositivo.

Para ver uma lista e uma descrição de todas as configurações de quiosque, consulte [Windows 10 e configurações de dispositivo posteriores para executar como um quiosque no Intune](kiosk-settings-windows.md).

Aplica-se a: Windows 10 e posterior

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Os logs operacionais também mostram detalhes sobre dispositivos não compatíveis <!-- 4063755  -->
Ao rotear logs do Intune para recursos do Azure monitor, você também pode rotear os logs operacionais. Nessa atualização, os logs operacionais também fornecem informações sobre dispositivos sem conformidade. 

Para obter mais informações sobre esse recurso, consulte [enviar dados de log para armazenamento, hubs de eventos ou log Analytics no Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Rotear logs para Azure Monitor em mais cargas de trabalho do Intune <!-- 3804627 -->
No Intune, você pode rotear logs de auditoria e operacionais para os hubs de eventos, o armazenamento e o log Analytics em Azure monitor (**configurações de diagnóstico**de**monitoramento** > do**Intune** > ). Nessa atualização, você pode rotear esses logs em mais cargas de trabalho do Intune, incluindo conformidade, configurações, aplicativos cliente e muito mais. 

Para saber mais sobre os logs de roteamento para Azure Monitor, consulte [enviar dados de log para armazenamento, hubs de eventos ou log Analytics](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Criar e usar extensões de mobilidade em dispositivos Android pretas no Intune <!-- 3305880   -->
Nesta atualização, o Intune dá suporte à configuração de dispositivos Android pretas. Especificamente, você pode criar um perfil de configuração de dispositivo e aplicar configurações a dispositivos Android pretas usando perfis MX (extensões de mobilidade) gerados pelo > StageNow (**perfis**  >   **de configuração de dispositivo Criar perfil** > **Android** para plataforma > **perfil MX (somente pretas)** para o tipo de perfil).

Para obter mais informações sobre esse recurso, consulte [usar e gerenciar dispositivos pretas com extensões de mobilidade no Intune](android-zebra-mx-overview.md).

Aplica-se a: Android

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Relatório de criptografia para dispositivos Windows 10 (em visualização pública)<!-- 2351538 -->  
Use o novo [relatório de criptografia (versão prévia)](encryption-monitor.md) para exibir detalhes sobre o status de criptografia de seus dispositivos Windows 10. Os detalhes disponíveis incluem uma versão do TPM de dispositivos, prontidão de criptografia e status, relatório de erros e muito mais.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Acessar chaves de recuperação do BitLocker no portal do Intune (em visualização pública) <!-- 2351547   -->  
Agora você pode usar o Intune para [Exibir detalhes](encryption-monitor.md) sobre a ID de chave do BitLocker e as chaves de recuperação do BitLocker, de Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Suporte do Microsoft Edge para cenários do Intune em dispositivos iOS e Android <!-- 3411007 -->
O Microsoft Edge dará suporte a todos os mesmos cenários de gerenciamento que o Intune Managed Browser com a adição de melhorias à experiência do usuário final. Os recursos do Microsoft Edge Enterprise habilitados pelas políticas do Intune incluem identidade dupla, integração de política de proteção de aplicativo, integração de proxy de aplicativo do Azure e atalhos de home page e favoritos gerenciados. Para obter mais informações, consulte [suporte do Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>O conector do Exchange Online/Intune preteri o suporte para dispositivos EAS somente <!--3105122  -->
O console do Intune não dá mais suporte à exibição e ao gerenciamento de dispositivos somente EAS conectados ao Exchange Online com o conector do Intune. Em vez disso, você tem as seguintes opções:
- Registrar dispositivos no MDM (gerenciamento de dispositivo móvel)
- Usar políticas de Proteção de Aplicativo do Intune para gerenciar seus dispositivos
- Usar os controles do Exchange conforme descrito em [clientes e dispositivos móveis no Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Pesquisar a página todos os dispositivos de um dispositivo exato usando [nome] <!--4254930 -->
Agora você pode pesquisar um nome de dispositivo exato. Vá para > **dispositivos** {} do Intune todos os dispositivos > na caixa de pesquisa, coloque o nome do dispositivo com para procurar uma correspondência exata. >  Por exemplo, **{Device12345}** .

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Suporte para conectores adicionais na página de status do locatário <!-- 3617202  -->
A [página status do locatário](tenant-status.md) agora exibe informações de status para conectores adicionais, incluindo a ATP ( *proteção avançada contra ameaças) do Windows Defender* e outros conectores de defesa contra ameaças móveis.

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Concedendo acesso somente leitura do Intune a algumas funções de Azure Active Directory <!-- 3637917  -->
O acesso somente leitura do Intune foi concedido às seguintes funções do Azure AD. As permissões concedidas com as funções do Azure AD substituem as permissões concedidas com o RBAC (controle de acesso baseado em função) do Intune.

Acesso somente leitura aos dados de auditoria do Intune:

- Administrador de conformidade
- Administrador de dados de conformidade

Acesso somente leitura a todos os dados do Intune:

- Administrador de Segurança
- Operador de segurança
- Leitor de segurança

Para obter mais informações, consulte [controle de acesso baseado em função](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Marcas de escopo para perfis de provisionamento de aplicativo iOS <!--2934430   -->
Você pode adicionar uma marca de escopo a um perfil de provisionamento de aplicativo iOS para que somente as pessoas com funções também atribuídas a essa marca de escopo tenham acesso ao perfil de provisionamento de aplicativo iOS. Para obter mais informações, consulte [usar RBAC e marcas de escopo](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Marcas de escopo para políticas de configuração de aplicativo <!--2371891   -->
Você pode adicionar uma marca de escopo a uma política de configuração de aplicativo para que somente as pessoas com funções também atribuídas a essa marca de escopo tenham acesso à política de configuração de aplicativo. A política de configuração de aplicativo só pode ser destinada ou associada a aplicativos atribuídos à mesma marca de escopo. Para obter mais informações, consulte [usar RBAC e marcas de escopo](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Suporte do Microsoft Edge para cenários do Intune em dispositivos iOS e Android <!-- 3411007 -->
O Microsoft Edge dará suporte a todos os mesmos cenários de gerenciamento que o Intune Managed Browser com a adição de melhorias à experiência do usuário final. Os recursos do Microsoft Edge Enterprise habilitados pelas políticas do Intune incluem identidade dupla, integração de política de proteção de aplicativo, integração de proxy de aplicativo do Azure e atalhos de home page e favoritos gerenciados. Para obter mais informações, consulte [suporte do Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Semana de 25 de fevereiro de 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="intune-powershell-module----951068----"></a>Módulo do Intune PowerShell <!-- 951068  -->
O módulo do Intune PowerShell, que fornece suporte para a API do Intune por meio do Microsoft Graph, agora está disponível no [Microsoft Galeria do PowerShell](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Detalhes sobre como usar este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemplos de cenário usando este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Suporte aprimorado para otimização de entrega  <!--3183757  -->
Expandimos o suporte no Intune para configurar a otimização de entrega. Agora você pode configurar uma lista expandida de [configurações de otimização de entrega](delivery-optimization-settings.md) e direcioná-la para seus dispositivos diretamente do console do Intune.


## <a name="week-of-february-18-2019"></a>Semana de 18 de fevereiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>O Intune aproveitará Google Play proteger APIs em dispositivos Android <!-- 2577355   -->
Alguns administradores de ti enfrentam um cenário de BYOD em que os usuários finais podem acabar com a raiz ou jailbreakingr seus celulares. Esse comportamento, embora às vezes não seja mal intencional, resulta em um bypass de muitas políticas do Intune que são definidas para proteger os dados da organização em dispositivos de usuário final. Portanto, o Intune fornece detecção de raiz e jailbreak para dispositivos registrados e não registrados. Com esta versão, o Intune agora aproveitará Google Play proteger APIs para adicionar às nossas verificações de detecção de raiz existentes para dispositivos não registrados. Embora o Google não compartilhe integralmente as verificações de detecção de raiz que ocorrem, esperamos que essas APIs detectem usuários que fizeram a raiz de seus dispositivos por qualquer motivo, desde a personalização do dispositivo até a capacidade de obter atualizações mais recentes do sistema operacional em dispositivos mais antigos. Esses usuários podem então ser impedidos de acessar dados corporativos ou suas contas corporativas podem ser apagadas de seus aplicativos habilitados para políticas. Para um valor adicional, o administrador de ti agora terá várias atualizações de relatório na folha Proteção de Aplicativo do Intune-o relatório "usuários sinalizados" mostrará quais usuários são detectados por meio da verificação de API SafetyNet do Google Play Protect, o relatório "aplicativos potencialmente prejudiciais" Mostre quais aplicativos são detectados por meio da verificação da API de aplicativos de verificação do Google. Esse recurso está disponível no Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informações do aplicativo Win32 disponíveis na folha de solução de problemas <!-- 2617342   -->
Agora você pode coletar arquivos de log de falha para uma instalação de aplicativo Win32 da folha de **solução de problemas** de aplicativo do Intune. Para obter mais informações sobre solução de problemas de instalação de aplicativo, consulte [solucionar problemas de instalação de aplicativo](troubleshoot-app-install.md) e [solucionar problemas de aplicativos Win32](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Detalhes de status do aplicativo para aplicativos iOS <!-- 3761235   -->
Há novas mensagens de erro de instalação de aplicativo relacionadas ao seguinte:
- Falha para aplicativos VPP ao instalar em iPad compartilhado
- Falha quando a loja de aplicativos está desabilitada
- Falha ao localizar a licença do VPP para o aplicativo
- Falha ao instalar aplicativos de sistema com o provedor de MDM
- Falha ao instalar aplicativos quando o dispositivo está no modo perdido ou no modo de quiosque
- Falha ao instalar o aplicativo quando o usuário não está conectado à loja de aplicativos

No Intune, selecione**aplicativos** **cliente** > aplicativo > "nome do aplicativo" > **status de instalação do dispositivo**. Novas mensagens de erro estarão disponíveis na coluna **detalhes de status** .

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Tela de novas categorias de aplicativo no aplicativo Portal da Empresa para Windows 10<!-- 3834780  -->
Uma nova tela chamada **categorias de aplicativo** foi adicionada para melhorar a navegação e a experiência de seleção do aplicativo no portal da empresa para Windows 10. Os usuários agora verão seus aplicativos classificados em categorias, como em **destaque**, **educação**e **produtividade**. Essa alteração aparece em Portal da Empresa versões 10.3.3451.0 e posteriores. Para exibir a nova tela, consulte [o que há de novo na interface do usuário do aplicativo](whats-new-app-ui.md). Para obter mais informações sobre aplicativos no Portal da Empresa, consulte [instalar e compartilhar aplicativos em seu dispositivo](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Aplicativo de conformidade Power BI <!-- 1455231 doc-work-item -->
Acesse suas data warehouse do Intune no Power BI online usando o aplicativo de [conformidade do Intune (data warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) . Com este Power BI aplicativo, agora você pode acessar e compartilhar relatórios pré-criados sem nenhuma configuração e sem sair do navegador da Web. Para obter informações adicionais, consulte [Change log-Power bi aplicativo de conformidade](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Os scripts do PowerShell podem ser executados em um host de 64 bits em dispositivos de 64 bits <!-- 1862675   -->
Quando você adiciona um script do PowerShell a um perfil de configuração do dispositivo, o script sempre é executado no 32-bit, mesmo em sistemas operacionais de 64 bits. Com essa atualização, um administrador pode executar o script em um host do PowerShell de 64 bits em dispositivos de 64 bits **(configuração** > do dispositivo**scripts** > do PowerShell**Adicionar** > **configuração**  >  **Execute o script no host do PowerShell de 64 bits**).

Para obter mais detalhes sobre como usar o PowerShell, consulte [scripts do PowerShell no Intune](intune-management-extension.md).

Aplica-se a: Windows 10 e posterior

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>os usuários do macOS são solicitados a atualizar sua senha <!-- 1873216 -->
O Intune está impondo a configuração **ChangeAtNextAuth** em dispositivos MacOS. Essa configuração afeta os usuários finais e os dispositivos que têm políticas de senha de conformidade ou perfis de senha de restrição de dispositivo. Os usuários finais são solicitados uma vez para atualizar sua senha. Esse prompt ocorre sempre que um usuário executa pela primeira vez uma tarefa que requer autenticação, como entrar no dispositivo. Os usuários também podem ser solicitados a atualizar sua senha ao fazer qualquer coisa que exija privilégios administrativos, como solicitar o acesso ao conjunto de chaves. 

Qualquer política de senha nova ou existente é alterada pelo administrador solicitando os usuários finais novamente para atualizar sua senha.

Aplica-se a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Atribuir certificados SCEP a um dispositivo macOS-não-usuário    <!-- 2340521    -->
Você pode atribuir certificados de protocolo SCEP (SCEP) usando atributos de dispositivo para dispositivos macOS, incluindo dispositivos sem afinidade de usuário, e associar o perfil de certificado a perfis Wi-Fi ou VPN. Isso expande o suporte que já temos para [atribuir certificados SCEP a dispositivos com e sem afinidade de usuário](certificates-profile-scep.md) que executa Windows, Ios e Android.  Esta atualização adiciona a opção para selecionar um tipo de certificado de *dispositivo* quando você configura um perfil de certificado SCEP para o MacOS.

Aplica-se a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Atualização da interface do usuário de acesso condicional do Intune   <!-- 2432313   -->
Fizemos melhorias na interface do usuário para acesso condicional no console do Intune. Estas incluem:
- Substituída a folha de *acesso condicional* do Intune pela folha de Azure Active Directory. Isso garante que você terá acesso a toda a gama de configurações e configurações para [acesso condicional](conditional-access.md) (que permanece como uma tecnologia do Azure AD), no console do Intune. 
- Renomeamos a folha de *acesso local* para *acesso ao Exchange*e realocamos a configuração do *conector de serviço do Exchange* para essa folha renomeada.  Essa alteração consolida o local em que você [configura e monitora detalhes relacionados ao Exchange Online e locais](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Os aplicativos navegador de quiosque e navegador Microsoft Edge podem ser executados em dispositivos Windows 10 no modo de quiosque <!-- 2935135   -->
Você pode usar dispositivos Windows 10 no modo de quiosque para executar um aplicativo ou muitos aplicativos. Essa atualização inclui várias alterações no uso de aplicativos de navegador no modo de quiosque, incluindo:

- Adicione o navegador Microsoft Edge ou o navegador de quiosque para executar como aplicativos no dispositivo de quiosque (**perfis** > de**configuração** > de dispositivo**novo perfil** > **Windows 10 e posterior** para plataforma > **quiosque** para tipo de perfil).
- Novos recursos e configurações estão disponíveis para permitir ou restringir (**perfis** > de**configuração** > do dispositivo**novo perfil** > **Windows 10 e posterior** para plataforma > **restrições de dispositivo** para o tipo de perfil), incluindo:

- Navegador Microsoft Edge:
  - Usar o modo de quiosque do Microsoft Edge
  - Atualizar o navegador após o tempo ocioso

- Favoritos e pesquisa:
  - Permitir alterações no mecanismo de pesquisa

Para obter uma lista dessas configurações, consulte:

- [Configurações do dispositivo Windows 10 e posterior para execução como um quiosque](kiosk-settings-windows.md)
- [Restrições de dispositivo do navegador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Favoritos e restrições de dispositivo de pesquisa](device-restrictions-windows-10.md##favorites-and-search)

Aplica-se a: Windows 10 e posterior

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Novas configurações de restrição de dispositivo para dispositivos iOS e macOS <!-- 3448774   -->
Você pode restringir algumas configurações e recursos em dispositivos que executam Ios e MacOS (**perfis** > de**configuração** > do dispositivo**novo perfil** > **Ios** ou **MacOS** para plataforma >  **Restrições de dispositivo** para o tipo de perfil). Esta atualização adiciona mais recursos e configurações que você pode controlar, incluindo a configuração de tempo da tela, alteração das configurações do eSIM e planos de celular e muito mais em dispositivos iOS. Além disso, atrasar a visibilidade do usuário de atualizações de software e bloquear o cache de conteúdo em dispositivos macOS. 

Para ver os recursos e as configurações que você pode restringir, consulte:

- [configurações de restrição de dispositivo iOS](device-restrictions-ios.md)
- [configurações de restrição de dispositivo macOS](device-restrictions-macos.md)

Aplica-se a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Os dispositivos "quiosque" agora são chamados de "dispositivos dedicados" em dispositivos Android Enterprise <!-- 3598402   -->
Para alinhar com a terminologia do Android, o **quiosque** é alterado para **dispositivos dedicados** para dispositivos Android Enterprise (**perfis** > de**configuração** > do dispositivo**Criar perfil** > * * Android Enterprise para plataforma > **proprietário do dispositivo somente** > **restrições** > de dispositivo**dispositivos dedicados**).

Para ver as configurações disponíveis, vá para [configurações do dispositivo para permitir ou restringir recursos](device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>O Safari e atrasando as configurações do iOS de visibilidade da atualização de software do usuário estão se movendo na interface do usuário do Intune <!-- 3640850, 3803313   -->
Para dispositivos iOS, você pode definir as configurações do Safari e configurar as atualizações de software. Nesta atualização, essas configurações estão mudando para diferentes partes da interface do usuário do Intune:

- As configurações do Safari movidas do **Safari** (**configuração** > do dispositivo**perfis** > **novo perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil) para **[Aplicativos internos](device-restrictions-ios.md#built-in-apps)** .
- A **visibilidade da atualização de software do usuário de atraso para dispositivos IOS supervisionados** (**políticas de atualização de** **atualizações** > de software para IOS) está mudando para as **restrições** > de dispositivo **[geral](device-restrictions-ios.md#general)** .  Para obter detalhes sobre o impacto sobre as políticas existentes, consulte [atualizações de software do IOS](software-updates-ios.md#configure-the-policy). 

Para obter uma lista das configurações, consulte:

- [restrições de dispositivo iOS](device-restrictions-ios.md) 
- [atualizações de software do iOS](software-updates-ios.md)

Esta funcionalidade aplica-se a: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Habilitar restrições nas configurações do dispositivo é renomeado para tempo de tela em dispositivos iOS <!-- 3699164   -->
Você pode configurar as **restrições de habilitação nas configurações do dispositivo** em dispositivos IOS supervisionados (**perfis** > de**configuração** > do dispositivo**novo perfil** > **Ios** para plataforma > **Restrições de dispositivo** para o tipo de perfil > **geral**). Nessa atualização, essa configuração é renomeada para **tempo de tela (somente supervisionado)** . 

O comportamento é o mesmo. Especificamente 

- iOS 11.4.1 e anterior: **Bloquear** impede que os utilizadores finais definam as suas próprias restrições nas definições do dispositivo. 
- iOS 12.0 e posterior: **Bloquear** impede que os usuários finais definam seu próprio **tempo de tela** nas configurações do dispositivo, incluindo conteúdo & restrições de privacidade. Os dispositivos atualizados para iOS 12,0 não verão mais a guia restrições nas configurações do dispositivo. Estas definições estão em **Tempo do Ecrã**. 

Para obter uma lista das configurações, consulte [restrições de dispositivo IOS](device-restrictions-ios.md#general).

Aplica-se a: 
- iOS


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Renomear um dispositivo Windows registrado <!-- 1911112  -->
Agora você pode renomear um dispositivo Windows 10 registrado (RS4 ou posterior). Para fazer isso, escolha**dispositivos** > do **Intune** > **todos os dispositivos** > escolha um dispositivo > **renomear dispositivo**. Atualmente, esse recurso não dá suporte à renomeação de dispositivos Windows do Azure AD híbridos.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Atribuir automaticamente marcas de escopo a recursos criados por um administrador com esse escopo <!-- 3173823  -->
Quando um administrador cria um recurso, todas as marcas de escopo atribuídas ao administrador serão automaticamente atribuídas a esses novos recursos.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>O relatório de registro com falha se move para a folha de registro do dispositivo <!-- 3560202  -->
O relatório de registros **com falha** foi movido para a seção **Monitor** da folha **registro do dispositivo** . Duas novas colunas (método de registro e versão do sistema operacional) foram adicionadas.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Portal da Empresa relatório de abandono renomeado para inscrições incompletas do usuário <!--3815076 eemiss -->
O relatório de **abandono portal da empresa** foi renomeado para **registros de usuário incompletos**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Semana de 4 de fevereiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Modo escuro do Intune macOS Portal da Empresa <!-- 3300524  -->
O Portal da Empresa do Intune no macOS agora dá suporte ao modo escuro para macOS. Quando você habilita o modo escuro em um dispositivo macOS 10.14 +, o Portal da Empresa ajustará sua aparência às cores que refletem esse modo.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Semana de 21 de janeiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notificações do sistema para aplicativos Win32 <!-- 3136566   -->
Você pode suprimir a exibição de notificações do sistema de usuário final por atribuição de aplicativo. No Intune, selecione aplicativos de **aplicativos** > cliente > selecione as **atribuições** > de > de aplicativo**incluem grupos**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Atualização da interface do usuário das políticas de proteção de aplicativo <!-- 3251427  -->
Alteramos os rótulos de configurações e botões para a proteção de aplicativo do Intune para facilitar a compreensão. Algumas das alterações incluem:  
- Os controles são alterados de **Sim** / **nenhum** controle para **Bloquear** / principalmente**permitir** e **desabilitar** / controles**Enable** . Os rótulos também são atualizados.  
- As configurações são reformatadas, portanto, a configuração e seu rótulo são lado a lado no controle, para fornecer melhor navegação.   

As configurações padrão e o número de configurações permanecem os mesmos, mas essa alteração permite que o usuário entenda, navegue e utilize as configurações mais facilmente para aplicar as políticas de proteção de aplicativo selecionadas. Para obter informações, consulte Configurações do [Ios](app-protection-policy-settings-ios.md) e [configurações do Android](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Configurações adicionais para o Outlook <!-- 3301182  -->
Agora você pode definir as seguintes configurações adicionais para o Outlook para iOS e Android usando o Intune:

- Permitir que apenas contas corporativas ou de estudante sejam usadas no Outlook no iOS e no Android
- Implantar a autenticação moderna para o Office 365 e contas locais de autenticação moderna híbrida
- Use `SAMAccountName` para o campo nome de usuário no perfil de email quando a autenticação básica estiver selecionada
- Permitir que os contatos sejam salvos
- Configurar os destinatários externos dicas de Recipient
- Configurar a **caixa de entrada focada**
- Exigir biometria para acessar o Outlook para iOS
- Bloquear imagens externas

> [!NOTE]
> Se você estiver usando políticas de Proteção de Aplicativo do Intune para gerenciar o acesso para identidades corporativas, considere não habilitar a **biometria de requerer**. Para obter mais informações, consulte **exigir credenciais corporativas para acesso** às configurações de acesso do [Ios](app-protection-policy-settings-ios.md#access-requirements) e configurações de [acesso do Android](app-protection-policy-settings-android.md#access-requirements).

Para obter mais informações, consulte [definições de configuração do Microsoft Outlook](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Excluir aplicativos corporativos do Android <!-- 1352553 -->
Você pode excluir aplicativos Google Play gerenciados do Microsoft Intune. Para eliminar uma aplicação do Managed Google Play, abra o Microsoft Intune no portal do Azure e selecione **Aplicações cliente** > **Aplicações**. Na lista de aplicações, selecione as reticências (...) à direita da aplicação do Managed Google Play e, em seguida, selecione **Eliminar** na lista apresentada. Quando elimina uma aplicação do Managed Google Play da lista de aplicações, essa aplicação passa automaticamente a não aprovada.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo de aplicações do Managed Google Play <!-- 1352580 -->
O tipo de aplicativo **Google Play gerenciado** permitirá que você adicione especificamente [aplicativos gerenciados de Google Play](https://play.google.com/work/search?q=microsoft&c=apps) ao Intune. Como administrador do Intune, agora você pode procurar, Pesquisar, aprovar, sincronizar e atribuir aplicativos de Google Play gerenciados aprovados no Intune.  Já não precisa de procurar na consola do Managed Google Play separadamente e já não tem de se autenticar novamente.  No Intune,**selecione aplicativos** >  **cliente** > aplicativos**Adicionar**. Na lista **tipo de aplicativo** , selecione **Google Play gerenciado** como o tipo de aplicativo.

### <a name="default-android-pin-keyboard----3802457---"></a>Teclado padrão de PIN do Android <!-- 3802457 -->
Para os usuários finais que definiram um PIN de política de Proteção de Aplicativo do Intune (aplicativo) em seus dispositivos Android com o tipo de PIN ' numeric ', eles agora verão o teclado Android padrão em vez da interface do usuário do teclado do Android fixa que foi previamente projetada. Essa alteração foi feita para ser consistente ao usar teclados padrão no Android e no iOS, para ambos os tipos de PIN de ' numeric ' e/ou ' senha '. Para obter mais informações sobre as configurações de acesso do usuário final no Android, como o PIN do aplicativo, consulte [requisitos de acesso do Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Usar as configurações recomendadas pela Microsoft com linhas de base de segurança (visualização pública) <!-- 2055484   -->

O Intune tem integração com outros serviços centrados na segurança, incluindo o Windows Defender ATP e o Office 365 ATP. Os clientes estão a pedir uma estratégia comum e um conjunto coeso de fluxos de trabalho de segurança de ponto a ponto em todos os serviços do Microsoft 365. O nosso objetivo é alinhar estratégias para desenvolver soluções que criem uma ponte entre operações de segurança e tarefas de administrador comuns. No Intune, pretendemos cumprir este objetivo através da publicação de um conjunto de "Linhas de base de segurança" recomendadas pela Microsoft (**Intune** > **Linhas de base de segurança**).  Um administrador pode criar políticas de segurança diretamente dessas linhas de base e, em seguida, implantá-las em seus usuários. Você também pode personalizar as recomendações de práticas recomendadas para atender às necessidades da sua organização. O Intune assegura que os dispositivos permanecem em conformidade com estas linhas de base e notifica os administradores de utilizadores ou dispositivos que não estejam em conformidade.

Esse recurso está em visualização pública, de modo que qualquer perfil criado agora não passará para os modelos de linhas de base de segurança que estão geralmente disponíveis (GA). Você não deve planejar usar esses modelos de visualização em seu ambiente de produção.

Para saber mais sobre linhas de base de segurança, confira [criar uma linha de base de segurança do Windows 10 no Intune](security-baselines-monitor.md).

Esta funcionalidade aplica-se a: Windows 10 e posterior

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Não administradores podem habilitar o BitLocker em dispositivos Windows 10 ingressados no Azure AD<!-- 2147379   -->
Quando ativa as definições do BitLocker em dispositivos Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** para a plataforma > **proteção de ponto final** para o tipo de perfil > **encriptação Windows**), adicionar as definições do BitLocker. 

Esta atualização inclui uma nova definição de disco BitLocker para permitir que os usuários padrão (não-administradores) ativar a encriptação. 

Para ver as configurações, vá para [configurações do Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Verificar a conformidade de Configuration Manager <!-- 2192052  eepublished  -->
Essa atualização inclui uma nova configuração de conformidade System Center Configuration Manager (**políticas** > de**conformidade** > do dispositivo**criar política** > **Windows 10 e posterior**  >   **Configuration Manager conformidade**). O Configuration Manager envia sinais de conformidade ao Intune. Usando essa configuração, você pode exigir que todos os sinais de Configuration Manager retornem "em conformidade".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se algum programa no dispositivo estiver em um estado desconhecido, o dispositivo não será compatível no Intune.

[Configuration Manager conformidade](compliance-policy-create-windows.md#configuration-manager-compliance) descreve essa configuração.

Aplica-se a: Windows 10 e posterior

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalizar o papel de parede em dispositivos iOS supervisionados usando um perfil de configuração de dispositivo <!-- 2809324   -->
Ao criar um perfil de configuração de dispositivo para dispositivos IOS, você pode personalizar alguns recursos (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Ios** para plataforma >  **Recursos do dispositivo** para o tipo de perfil). Essa atualização inclui novas configurações de **papel de parede** que permitem que um administrador use uma imagem. png,. jpg ou. jpeg na tela inicial ou na tela de bloqueio. Essas configurações de papel de parede se aplicam somente a dispositivos supervisionados. 

Para obter uma lista dessas configurações, consulte [configurações de recurso do dispositivo IOS](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>O quiosque do Windows 10 está disponível para o público geral <!-- 3594661  -->
Nessa atualização, o recurso de quiosque no Windows 10 e em dispositivos posteriores está geralmente disponível (GA). Para ver todas as configurações que você pode adicionar e configurar, consulte [configurações de quiosque para Windows 10 (e posterior)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>O compartilhamento de contatos via Bluetooth é removido nas restrições de dispositivo > proprietário do dispositivo para Android Enterprise <!-- 3598396   -->
Quando você cria um perfil de restrições de dispositivo para dispositivos Android Enterprise, há um **compartilhamento de contatos por meio** da configuração de Bluetooth. Nesta atualização, a configuração **compartilhamento de contatos via Bluetooth** é removida (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Android Enterprise** para plataforma >  **As restrições de dispositivo > proprietário do dispositivo** para o tipo de perfil > **geral**). 

A configuração de **compartilhamento de contatos via Bluetooth** não tem suporte para gerenciamento de proprietário do dispositivo Android Enterprise. Assim, quando essa configuração é removida, ela não afetará nenhum dispositivo ou locatários, mesmo que essa configuração esteja habilitada e configurada em seu ambiente.

Para ver a lista atual de configurações, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos](device-restrictions-android-for-work.md).

Aplica-se a: Proprietário do dispositivo corporativo Android

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Suporte de apagamento seletivo para WIP sem dispositivos de registro <!-- 1434452 -->
A proteção de informações do Windows sem registro (WIP-WE) permite que os clientes protejam seus dados corporativos em dispositivos Windows 10 sem a necessidade de registro completo de MDM. Depois que os documentos são protegidos com uma política WIP-nós, os dados protegidos podem ser apagados seletivamente por um administrador do Intune. Ao selecionar o usuário e o dispositivo e enviar uma solicitação de apagamento, todos os dados que foram protegidos por meio da política WIP-WE se tornarão inutilizáveis. No Intune, no portal do Azure, selecione **Aplicação móvel** > **Eliminação seletiva da aplicação**.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Novos logs operacionais e capacidade de enviar logs para serviços de Azure Monitor <!-- 3762211  -->
O Intune tem log de auditoria interno que rastreia eventos conforme são feitas alterações. Essa atualização inclui novos recursos de log, incluindo: 
- Logs operacionais (versão prévia) que mostram detalhes sobre usuários e dispositivos registrados, incluindo êxito e tentativas com falha.
- Os logs de auditoria e os logs operacionais podem ser enviados para Azure Monitor, incluindo contas de armazenamento, hubs de eventos e log Analytics. Esses serviços permitem que você armazene, use análises como Splunk e QRadar e obtenha visualizações de seus dados de registro em log.

[Enviar dados de log para armazenamento, hubs de eventos ou log Analytics no Intune](review-logs-using-azure-monitor.md) fornece mais informações sobre esse recurso.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorar mais telas do assistente de configuração em um dispositivo de DEP do iOS <!-- 2687509  -->
Além das telas que você pode ignorar no momento, você pode definir dispositivos do iOS DEP para ignorar as seguintes telas no assistente de configuração quando um usuário registra o dispositivo: Tom de vídeo, privacidade, migração do Android, botão página inicial, iMessage & FaceTime, integração, migração de inspeção, aparência, hora da tela, atualização de software, instalação do SIM.
Para escolher que telas para ignorar, aceda a **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token > **Perfis** > Escolha um perfil > **propriedades** > **personalização do Assistente de configuração** > Escolha **ocultar**  para qualquer telas que pretende ignorar > **OK**.
Se você criar um novo perfil ou editar um perfil, as telas ignorar selecionadas precisarão ser sincronizadas com o servidor MDM da Apple. Os usuários podem emitir uma sincronização manual dos dispositivos para que não haja atraso na separação das alterações de perfil.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>APLICATIVO Android Enterprise – implantação de aplicativo <!-- 1171203 -->
Para dispositivos Android em uma política de proteção de aplicativo não registrada sem registro (APP-WE), agora você pode usar o Google Play gerenciado para implantar aplicativos de armazenamento e aplicativos LOB para os usuários. Especificamente, você pode fornecer aos usuários finais um catálogo de aplicativos e uma experiência de instalação que não exige mais que os usuários finais afrouxem a postura de segurança de seus dispositivos, permitindo instalações de fontes desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Semana de 14 de janeiro de 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Visualização do suporte para dispositivos Android de propriedade corporativa e totalmente gerenciado <!-- 1574342  -->
O Intune agora dá suporte a dispositivos Android totalmente gerenciados, um cenário de "proprietário do dispositivo" de propriedade da empresa, em que os dispositivos são totalmente gerenciados por ele e são afiliados a usuários individuais. Isso permite que os administradores gerenciem todo o dispositivo, imponham um intervalo estendido de controles de política indisponíveis para perfis de trabalho e restringe os usuários a instalarem aplicativos somente de Google Play gerenciados. Para obter mais informações, consulte [Configurar o registro do Intune de dispositivos Android totalmente gerenciados](android-fully-managed-enroll.md) e [registrar seus dispositivos dedicados ou dispositivos totalmente gerenciados](android-dedicated-devices-fully-managed-enroll.md).  Observe que esse recurso está em versão prévia. Alguns recursos do Intune, como certificados, conformidade e acesso condicional, não estão disponíveis no momento com dispositivos de usuário totalmente gerenciados do Android.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Semana de 7 de janeiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-app-pin----2298397---"></a>PIN do aplicativo do Intune <!-- 2298397 -->
Como administrador de ti, agora você pode configurar o número de dias que um usuário final pode esperar até que o PIN do seu aplicativo do Intune seja alterado. A nova configuração é *redefinição de Pin após o número de dias* e está disponível na portal do Azure selecionando**aplicativos** > cliente do **Intune** > **políticas** > de proteção de aplicativo**criar política**  >  **Configurações** do **Requisitos de acesso.**  >  Disponível para dispositivos [Ios](app-protection-policy-settings-ios.md) e [Android](app-protection-policy-settings-android.md) , esse recurso dá suporte a um valor inteiro positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campos de relatório de dispositivo do Intune <!-- 2748738 -->
O Intune fornece campos de relatório de dispositivo adicionais, incluindo ID de registro do aplicativo, fabricante do Android, modelo e versão do patch de segurança, bem como o modelo do iOS. No Intune, esses campos estão disponíveis selecionando **aplicativos** > cliente**status de proteção do aplicativo** e escolhendo **relatório de proteção do aplicativo: Ios, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão. 


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Os modelos administrativos estão em visualização pública e movidos para seu próprio perfil de configuração <!-- 3322847 -->

Os modelos administrativos no Intune (**modelos administrativos**de**configuração** > de dispositivo) estão atualmente em visualização pública. Com esta atualização:

- Os modelos administrativos incluem as configurações de 300 que podem ser gerenciadas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
- Os modelos administrativos estão disponíveis em visualização pública.
- Os modelos administrativos estão mudando dos**modelos administrativos** de **configuração** > de dispositivo para**perfis** > de **configuração** > de dispositivo**Criar perfil** > em  **Plataforma**, escolha **Windows 10 e posterior** > em **tipo de perfil**, escolha **modelos administrativos**.
- O relatório está habilitado

Para ler mais sobre esse recurso, vá para [modelos do Windows 10 para definir as configurações da política de grupo](administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Usar S/MIME para criptografar e assinar vários dispositivos para um usuário  <!-- 1333642 -->
Esta atualização inclui a encriptação de e-mails com S/MIME através de um novo perfil de certificado importado (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > selecione a plataforma > tipo de perfil **Certificados PKCS importados**). No Intune, pode importar certificados no formato PFX. O Intune pode enviar esses mesmos certificados para múltiplos dispositivos inscritos por um único utilizador. Isto também inclui:
- O perfil de e-mail nativo do iOS suporta a ativação da encriptação S/MIME através de certificados importados no formato PFX.
- O aplicativo de email nativo em Windows Phone 10 dispositivos usa automaticamente o certificado S/MIME.
- Os certificados privados podem ser fornecidos a várias plataformas. No entanto, nem todas as aplicações de e-mail suportam S/MIME.
- Noutras plataformas, talvez seja necessário configurar manualmente a aplicação de e-mail para permitir o S/MIME.  
- As aplicações de e-mail que suportam a encriptação S/MIME conseguem obter certificados para a encriptação S/MIME de e-mails de uma forma que não é suportada por MDM, como a leitura a partir do arquivo de certificados do respetivo publicador.
Para obter mais informações sobre esse recurso, consulte [visão geral de S/MIME para assinar e criptografar email](certificates-s-mime-encryption-sign.md).
Suportado no: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Novas opções para se conectar e manter as regras automaticamente ao usar as configurações de DNS no Windows 10 e em dispositivos posteriores <!-- 1333665, 2999078 -->
No Windows 10 e em dispositivos posteriores, você pode criar um perfil de configuração de VPN que inclui uma lista de servidores DNS para resolver domínios, como contoso.com. Essa atualização inclui novas configurações para resolução de nomes (**perfis** > de**configuração** > de dispositivo**Criar perfil** > escolha **Windows 10 e posterior** para plataforma > escolha **VPN** para tipo de perfil >**Adicionar** **configurações** >de DNS): 
- **Conectar automaticamente**: Quando **habilitado**, o dispositivo se conecta automaticamente à VPN quando um dispositivo entra em contato com um domínio que você insere, como contoso.com.
- **Persistente**: Por padrão, todas as regras de tabela de política de resolução de nome (NRPT) ficam ativas, desde que o dispositivo esteja conectado usando esse perfil de VPN. Quando essa configuração é **habilitada** em uma regra NRPT, a regra permanece ativa no dispositivo, mesmo quando a VPN é desconectada. A regra permanece até que o perfil VPN seja removido ou até que a regra seja manualmente removida, o que pode ser feito usando o PowerShell.
[As configurações de VPN do Windows 10](vpn-settings-windows-10.md) descrevem as configurações. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Usar detecção de rede confiável para perfis VPN em dispositivos Windows 10 <!-- 1500165 -->
Ao usar a detecção de rede confiável, você pode impedir que perfis VPN criem automaticamente uma conexão VPN quando o usuário já estiver em uma rede confiável. Com essa atualização, você pode adicionar sufixos DNS para habilitar a detecção de rede confiável em dispositivos que executam o Windows 10 e posterior (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **Windows 10 e mais tarde** para a plataforma > **VPN** para o tipo de perfil).
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) lista as definições de VPN atuais.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gerenciar dispositivos Windows Holographic for Business usados por vários usuários <!-- 1907917, 1063203 -->
No momento, você pode definir configurações de computador compartilhado em dispositivos Windows 10 e Windows Holographic for Business usando uma configuração de OMA-URI personalizada. Com essa atualização, um novo perfil é adicionado para definir configurações de dispositivo compartilhado (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Windows 10 e posterior**  >   **Dispositivo de vários usuários compartilhado**).
Para saber mais sobre esse recurso, vá para [configurações do Intune para gerenciar dispositivos compartilhados](shared-user-device-settings.md).
Aplica-se a: Windows 10 e posterior, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Novas configurações de atualização do Windows 10 <!--2626030  2512994  -->
Para seus [anéis de atualização do Windows 10](windows-update-for-business-configure.md), você pode configurar:
- **Comportamento de atualização automática** – usar uma nova opção, *Redefinir para padrão* para restaurar as configurações de atualização automática originais em um computador com Windows 10 em computadores que executam a *atualização de outubro de 2018*
- **Bloquear o usuário de pausar atualizações do Windows** – defina uma nova configuração de atualizações de software que permite bloquear ou permitir que os usuários pausem a instalação da atualização das *configurações* de suas máquinas. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>os perfis de email do iOS podem usar assinatura e criptografia S/MIME <!-- 2662949 -->
Você pode criar um perfil de email que inclui configurações diferentes. Essa atualização inclui configurações S/MIME que podem ser usadas para assinar e criptografar comunicações por email em dispositivos IOS (**perfis** > de**configuração** > do dispositivo**Criar perfil** > escolher **Ios** para plataforma > **email** para o tipo de perfil).
[definições de configuração de email do IOS](email-settings-ios.md) lista as configurações.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algumas configurações do BitLocker dão suporte ao Windows 10 Pro Edition<!-- 2727036 -->
Você pode criar um perfil de configuração que define as configurações do Endpoint Protection em dispositivos Windows 10, incluindo o BitLocker. Esta atualização adiciona suporte para o Windows 10 Professional Edition para algumas configurações do BitLocker. Para ver essas configurações de proteção, vá para [configurações do Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>A configuração de dispositivo compartilhado foi renomeada para bloquear a mensagem da tela para dispositivos iOS no portal do Azure<!-- 2809362 -->
Ao criar um perfil de configuração para dispositivos iOS, você pode adicionar definições de **configuração de dispositivo compartilhado** para mostrar texto específico na tela de bloqueio. Essa atualização inclui as seguintes alterações: 
- O **configuração de dispositivos partilhados** definições no portal do Azure são o nome mudadas para "Mensagem de ecrã de bloqueio (apenas supervisionada)" (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > Escolha **funcionalidades do dispositivo** para o tipo de perfil > **bloqueio Mensagem de ecrã**).
- Ao adicionar mensagens da tela de bloqueio, você pode inserir um número de série, um nome de dispositivo ou outro valor específico de dispositivo como uma variável em **informações de marca de ativo** e nota de rodapé da tela de **bloqueio**. Por exemplo, pode introduzir `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` usando chaves de saída. [iOS tokens](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) apresenta uma lista de tokens disponíveis que podem ser utilizados.
[Configurações para exibir mensagens na tela de bloqueio](shared-device-settings-ios.md) lista as configurações.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nova loja de aplicativos, exibição de documento, configurações de restrição de dispositivo de jogos adicionadas a dispositivos iOS <!-- 2827760-->
Em **configuração** > do dispositivo**perfis** > ,**crie perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **loja de aplicativos, exibição de documento, jogos**, as seguintes configurações são adicionadas: Permitir que aplicativos gerenciados gravem contatos em contas de contatos não gerenciados permitem que aplicativos não gerenciados leiam de contas de contatos gerenciados para ver essas configurações, vá para [restrições de dispositivo IOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Novas notificações, dicas e configurações de keyguard para dispositivos Android Enterprise do proprietário do dispositivo <!-- 3201839 3201843 -->
Esta atualização inclui várias novas funcionalidades em dispositivos Android Enterprise quando em execução como proprietário do dispositivo. Para utilizar estas funcionalidades, aceda a **configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma**, escolha **Android Enterprise** > no **tipo de perfil**, escolha **proprietário do dispositivo só** > **dispositivo Restrições**.

Os novos recursos incluem: 

- Desabilite as notificações do sistema de mostrar, incluindo chamadas de entrada, alertas do sistema, erros do sistema e muito mais.
- Sugere ignorar tutoriais e dicas iniciais para aplicativos que são abertos na primeira vez.
- Desabilite as configurações avançadas do keyguard, como a câmera, as notificações, o desbloqueio de impressão digital e muito mais.


Para ver as configurações, vá para [configurações de restrição de dispositivo Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Dispositivos Android Enterprise do proprietário do dispositivo podem usar Always On conexões VPN <!-- 3202194 -->
Nesta atualização, pode utilizar ligações VPN sempre ativada nos dispositivos de proprietário do dispositivo Android empresarial. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN sempre ativada no **configuração do dispositivo** > **perfis** > **criar perfil**  >   **Android enterprise** para a plataforma > **restrições de dispositivos** para o proprietário do dispositivo só > **conectividade** definições. Para ver as configurações, vá para [configurações de restrição de dispositivo Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nova configuração para encerrar processos no Gerenciador de tarefas em dispositivos Windows 10 <!-- 3285177 --> 
Esta atualização inclui uma nova definição para terminar a processos usando o Gerenciador de tarefas em dispositivos Windows 10. Utilizar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma** , escolha **Windows 10** > no **tipo de perfil**, escolha **restrições de dispositivos** > **geral** definições), optar por permitir ou impedir que esta definição.
Para ver essas configurações, vá para [configurações de restrição de dispositivo do Windows 10](device-restrictions-windows-10.md).
Aplica-se a: Windows 10 e posterior


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mensagens de falha de restrição de registro mais detalhadas <!-- 3111564 -->
Mensagens de erro mais detalhadas estão disponíveis quando as restrições de registro não são atendidas. Para ver estas mensagens, aceda à **Intune** > **resolução de problemas** > e consulte a tabela de falhas de inscrição. Para obter mais informações, consulte a [lista falhas de registro](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="tenant-status-dashboard-----1124854---"></a>Painel de status do locatário  <!-- 1124854 -->
A [página novo status do locatário](tenant-status.md) fornece um único local onde você pode exibir o status e os detalhes relacionados para seu locatário.  O painel é dividido em quatro áreas:
- **Detalhes do locatário** – exibe informações que incluem o nome e o local do seu locatário, sua autoridade de MDM, o total de dispositivos registrados em seu locatário e suas contagens de licenças. Esta seção também lista a versão de serviço atual para seu locatário.
- **Status do conector** -exibe informações sobre os conectores disponíveis que você configurou e também pode listar aqueles que ainda não foram habilitados.  
   Com base no estado atual de cada conector, eles são sinalizados como íntegros, de aviso ou não íntegros. Selecione um conector para detalhar e exibir detalhes ou configurar informações adicionais para ele.
- **Integridade do serviço do Intune** – exibe detalhes sobre incidentes ativos ou interrupções para seu locatário. As informações nesta seção são recuperadas diretamente do centro de mensagens do Office.
- **Notícias do Intune** – exibe mensagens ativas para seu locatário. As mensagens incluem itens como notificações quando seu locatário recebe os recursos mais recentes do Intune.  As informações nesta seção são recuperadas diretamente do centro de mensagens do Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nova experiência de ajuda e suporte no Portal da Empresa para Windows 10 <!-- 1488939-->
O novo Portal da Empresa ajuda & página de suporte ajuda os usuários a solucionar problemas e solicitar ajuda para problemas de aplicativo e acesso. Na nova página, eles podem enviar detalhes de erro de email e log de diagnóstico e encontrar os detalhes da assistência técnica de sua organização. Eles também encontrarão uma seção de perguntas frequentes com links para a documentação relevante do Intune. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nova experiência de ajuda e suporte para o Intune   <!-- #3307080 -->
Estamos distribuindo a nova experiência de ajuda e suporte para todos os locatários nos próximos dias. Essa nova experiência está disponível para o Intune e pode ser acessada ao usar as folhas do Intune no [portal do Azure](https://portal.azure.com/).
A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Essas soluções são oferecidas por meio de um algoritmo de aprendizado de máquina baseado em regra, orientado pelas consultas do usuário. Além das diretrizes específicas do problema, você usa o novo fluxo de trabalho de criação de caso para abrir um caso de suporte por email ou telefone. Essa nova experiência substitui a ajuda anterior e a experiência de suporte de um conjunto estático de opções pré-selecionadas que se baseiam na área do console em que você está ao abrir a ajuda e o suporte. Para obter mais informações, consulte [como obter suporte para Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apps----1081941---"></a>Marcas de escopo para aplicativos <!-- 1081941 -->
Você pode criar marcas de escopo para limitar o acesso a funções e aplicativos. Você pode adicionar uma marca de escopo a um aplicativo para que somente as pessoas com funções também atribuídas a essa marca de escopo tenham acesso ao aplicativo. Atualmente, os aplicativos adicionados ao Intune a partir de Google Play gerenciados ou aplicativos adquiridos usando Apple Volume Purchase Program (VPP) não podem ser atribuídos a marcas de escopo (o suporte futuro é planejado). Para obter mais informações, consulte [usar marcas de escopo para filtrar políticas](scope-tags.md).

## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
