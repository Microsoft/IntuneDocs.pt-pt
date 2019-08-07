---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833543"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Em desenvolvimento para Microsoft Intune – agosto de 2019

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

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>Controlar o comportamento de desinstalação do aplicativo iOS no cancelamento do registro do dispositivo <!-- 3504144 -->
Os administradores poderão gerenciar se um aplicativo é removido ou mantido em um dispositivo quando o registro do dispositivo é cancelado no nível de um usuário ou de um grupo de dispositivos. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Categorizar Microsoft Store para aplicativos de negócios <!-- 3926922 -->
Você poderá categorizar Microsoft Store para aplicativos de negócios. Para fazer isso, escolha**aplicativos** **cliente aplicativos** > do **Intune** > > selecione uma**categoria**de **informações** > do aplicativo Microsoft Store para o aplicativo de negócios >. No menu suspenso, atribua uma categoria.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android e iOS permitirão que você controle o conteúdo de notificação do aplicativo para contas da organização. Este recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android <!-- 3041956  -->
Para instalações de aplicativos disponíveis em dispositivos Android de perfil de trabalho, você pode exibir o status de instalação do aplicativo e a versão instalada dos aplicativos gerenciados Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Algumas restrições de dispositivo iOS não supervisionadas ficarão supervisionadas somente com a versão iOS 13,0 <!-- 4867809  -->
Algumas configurações serão aplicadas a dispositivos supervisionados, começando com a versão 13,0 do iOS. Essas configurações incluem:

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

Se essas configurações forem configuradas e atribuídas a dispositivos não supervisionados antes da versão 13,0 do iOS, as configurações ainda serão aplicadas a esses dispositivos não supervisionados. Eles ainda se aplicam após a atualização dos dispositivos para iOS 13,0. Essas restrições são removidas em dispositivos não supervisionados que são armazenados em backup e restaurados. 

Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](device-restrictions-ios.md).

Aplica-se a:  
- iOS 13,0 e mais recente

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Novas configurações e alterações nas configurações existentes para restringir recursos em dispositivos iOS e macOS <!-- 4867699 4867709  -->
Você poderá criar perfis para restringir as configurações em dispositivos que executam Ios e MacOS (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Ios** ou **MacOS** para plataforma Digite > **restrições de dispositivo**). Os seguintes recursos serão adicionados:

- Em >  restriçõesde > dispositivo MacOS**nuvem e armazenamento**, use a nova configuração de entrega para impedir que os usuários iniciem o trabalho em um dispositivo MacOS e continue trabalhando em outro dispositivo MacOS ou Ios.
  Para ver as configurações atuais, vá para [configurações do dispositivo MacOS para permitir ou restringir recursos usando o Intune](device-restrictions-macos.md).
- Em**restrições de dispositivo** **Ios** > , há algumas alterações:
  - **Aplicativos internos localizam** **meu iPhone (apenas**no modo supervisionado): >  Nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - **Os aplicativos** > internos**encontram meus amigos (apenas**no modo supervisionado): Nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - **Modificação sem fio** > **do estado de Wi-Fi (somente supervisionado)** : Nova configuração que impede que os usuários liguem ou desativem o Wi-Fi no dispositivo.
  - **QuickPath de teclado e dicionário** >  **(somente supervisionado)** : Nova configuração que bloqueia o recurso QuickPath.
  - **Nuvem e armazenamento**: A **continuação da atividade** é renomeada para **entrega**.

  Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](device-restrictions-ios.md).

Aplica-se a:  
- macOS 10,15 e mais recente
- iOS 13 e mais recente

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Controlar os aplicativos, arquivos, documentos e pastas que são abertos quando o usuário entra em dispositivos macOS <!--3914202  -->
Você poderá habilitar e configurar recursos em dispositivos MacOS (**perfis** > de**configuração** > do dispositivo**Criar perfil** > **MacOS** para plataforma > **recursos do dispositivo** para tipo de perfil). 

Haverá novas configurações de itens de logon para controlar quais aplicativos, arquivos, documentos e pastas serão abertos quando um usuário entrar no dispositivo registrado. 

Para ver as configurações atuais, vá para [configurações de recurso de dispositivo MacOS no Intune](macos-device-features-settings.md).

Aplica-se a:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Novos recursos para dispositivos Android Enterprise dedicados no modo de vários aplicativos <!-- 3755304 3041943 3041946  -->
Você poderá controlar recursos e configurações em uma experiência de estilo de quiosque em seus dispositivos Android Enterprise dedicados. Para fazer isso, escolha **configuração** > do dispositivo**perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **somente proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil.

Os seguintes recursos serão adicionados:
-  > **Vários aplicativos dedicados de**dispositivos: O **botão página inicial virtual** pode ser mostrado passando o dedo para cima no dispositivo ou flutuando na tela para que os usuários possam movê-lo.
-  > **Vários aplicativos dedicados de**dispositivos: O **acesso à lanterna** permite que os usuários usem a lanterna. 
-  > **Vários aplicativos dedicados de**dispositivos: O **controle de volume de mídia** permite que os usuários controlem o volume de mídia do dispositivo usando um controle deslizante. 
-  > **Vários aplicativos dedicados de**dispositivos:  Habilitar uma proteção de tela, carregar uma imagem personalizada e controlar quando a proteção de tela é mostrada.

Para ver as configurações atuais, vá para [configurações do dispositivo Android Enterprise para permitir ou restringir recursos usando o Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:  
- Dispositivos Android Enterprise dedicados

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Novos perfis de aplicativo e configuração para dispositivos Android Enterprise totalmente gerenciados <!-- 3574215  -->
Usando perfis, você poderá definir configurações que aplicam configurações de VPN, email e Wi-Fi aos dispositivos Android Enterprise totalmente gerenciados. Você poderá:
- Use perfis de aplicativo para implantar configurações de email do Outlook, Gmail e nove work.
- Use perfis de configuração de dispositivo para implantar configurações de certificado raiz confiável.
- Use perfis de configuração de dispositivo para implantar configurações de VPN e Wi-Fi.

Os usuários serão autenticados com seu nome de usuário e senha para perfis de VPN, Wi-Fi e de email. Atualmente, a autenticação baseada em certificado não está disponível. 

Aplica-se a:  
- Android Enterprise totalmente gerenciado

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Suporte para perfis VPN IKEv2 para iOS <!-- 1943438 -->
Você poderá criar perfis de VPN para o cliente VPN nativo do iOS usando o protocolo IKEv2. IKEv2 é um novo tipo de conexão no **dispositivo** > **perfis** > de configuração**Criar perfil** > **Ios** para plataforma > **VPN** para tipo de perfil > **configurações**.

Esses perfis de VPN configuram o cliente VPN nativo. Portanto, nenhum aplicativo cliente VPN é instalado ou enviado por push para dispositivos gerenciados. Esse recurso requer que os dispositivos sejam registrados no Intune (registro de MDM).

Para ver as configurações de VPN atuais que você pode configurar, vá para [definir configurações de VPN em dispositivos IOS em Microsoft Intune](vpn-settings-ios.md).

Aplica-se a: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>Ignorar mais telas no assistente de configuração <!--4877451 -->
Você poderá definir perfis de Programa de registro de dispositivos para ignorar as seguintes telas do assistente de configuração: 
- Hora da tela
- Configuração do touch ID

Para fazer isso, acesse **registro** > de dispositivo inscrição da**Apple** > tokens do**programa de registro** > escolha um token > **perfis** > escolha um perfil > **Propriedades** > **Editar** ao lado de **personalização do assistente de configuração**.
Para obter mais informações sobre a personalização do assistente de configuração, consulte [criar um perfil de registro da Apple ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Suporte ao administrador do dispositivo de registro do Android <!-- 4869749  -->
A opção de registro de administrador de dispositivo Android será adicionada à página de registro do Android (registro**Android**de**registro** > de dispositivo do**Intune** > ). O administrador do dispositivo Android ainda estará habilitado por padrão para todos os locatários.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa <!-- 4394993  -->
Usando a redução, você poderá personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Número de Build incluído na página de hardware do dispositivo Android <!-- 4461910  -->
Uma nova entrada na página de hardware para cada dispositivo Android incluirá o número de Build do sistema operacional do dispositivo.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurar o limite de tempo de limpeza de dispositivo automático para 30 dias <!--4231059  -->
Você poderá definir o limite de tempo de limpeza do dispositivo automático como 30 dias (em vez do limite atual de 90 dias) após a última entrada. Para fazer isso, vá para**dispositivos** > do **Intune** > **Configurar** > **regras de limpeza do dispositivo**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

### <a name="default-scope-tag----3702875---"></a>Marca de escopo padrão <!-- 3702875 -->
Uma nova marca de escopo padrão interna estará disponível. Todos os objetos do Intune não marcados que dão suporte a marcas de escopo serão automaticamente atribuídos à marca de escopo padrão. A marca de escopo **padrão** será adicionada a todas as atribuições de função existentes para manter a paridade com a experiência de administração hoje. Se você não quiser que um administrador Veja objetos do Intune com marcas de escopo padrão, remova a marca de escopo padrão da atribuição de função. Esse recurso é semelhante ao recurso de escopos de segurança no System Center Configuration Manager.

<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="import-and-export-security-baselines------3408610------------"></a>Importar e exportar linhas de base de segurança    <!--3408610          -->  
Estamos adicionando a capacidade de exportar e importar linhas de base de segurança. Esse recurso permitirá que você faça suas personalizações com você e compartilhe-as entre os ambientes do Intune.

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.




