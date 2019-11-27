---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540726"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Em desenvolvimento para Microsoft Intune-dezembro de 2019

Para ajudar na preparação e no planejamento, esta página lista as atualizações da interface do usuário do Intune e os recursos que estão em desenvolvimento, mas ainda não foram lançados. Além das informações nesta página:

- Se prevemos que você precisará tomar medidas antes de uma alteração, publicaremos uma postagem complementar no centro de mensagens do Office.
- Quando um recurso entra em produção, seja uma visualização ou geralmente disponível, a descrição do recurso passará dessa [página para as novidades.](whats-new.md)
- Esta página e a página [novidades](whats-new.md) são atualizadas periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte o [roteiro de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e cronogramas.

> [!NOTE]
> Esta página reflete nossas expectativas atuais sobre os recursos do Intune em uma versão futura. As datas e os recursos individuais podem mudar. Esta página não descreve todos os recursos no desenvolvimento.

**RSS feed**: descubra quando essa página é atualizada copiando e colando a seguinte URL em seu leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestão de aplicações

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>aplicativos de VPP licenciados para o usuário do iOS<!-- 5619268 idready -->
Para dispositivos iOS de registro de usuário, os usuários finais não serão mais apresentados com aplicativos VPP licenciados para dispositivos implantados como disponíveis. No entanto, os usuários finais continuarão a ver todos os aplicativos VPP licenciados pelo usuário dentro do Portal da Empresa. Para obter mais informações sobre aplicativos VPP, consulte [como gerenciar aplicativos Ios e MacOS adquiridos por meio de Apple Volume Purchase Program com Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Recuperar a chave de recuperação pessoal de dispositivos macOS criptografados com memória<!-- 4851745 idready -->
Os usuários finais poderão recuperar sua chave de recuperação pessoal (FileVault Key) usando o aplicativo Portal da Empresa do iOS. O dispositivo que tem a chave de recuperação pessoal deve ser registrado com o Intune e criptografado com o FileVault por meio do Intune. Usando o aplicativo Portal da Empresa do iOS, um usuário final pode abrir o modo de exibição da Web do Safari e recuperar sua chave de recuperação pessoal. No Intune, selecione **dispositivos** > *o dispositivo MacOS criptografado e registrado* > **obter a chave de recuperação**. Para obter mais informações sobre FileVault, consulte [criptografia FileVault para MacOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="microsoft-app-icons-update--4677605--"></a>Atualização de ícones do aplicativo Microsoft<!--4677605-->
Os ícones usados para aplicativos da Microsoft no painel de direcionamento de aplicativo para políticas de proteção de aplicativo e políticas de configuração de aplicativo serão atualizados.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Suporte a S/MIME para Microsoft Outlook Mobile<!-- 2669398  -->
O Intune dará suporte à entrega de certificados de criptografia e autenticação S/MIME que podem ser usados com o Outlook Mobile no iOS e no Android. Para obter informações relacionadas, consulte [configurações de email para dispositivos IOS](~/configuration/email-settings-ios.md) e [configurações de email para dispositivos Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Suporte a configurações personalizadas para aplicativos macOS<!-- 4736278  -->
O Intune dará suporte a configurações personalizadas, permitindo que você adicione chaves e valores específicos a um arquivo de lista de propriedades de preferências (. plist) existente para configurar aplicativos macOS e o dispositivo. Nem todos os aplicativos dão suporte a preferências gerenciadas e, em alguns casos, apenas configurações específicas podem ser gerenciadas. As configurações são implantadas somente por meio do canal do dispositivo. Você deve carregar somente arquivos de lista de propriedades ou arquivos. XML que destinam-se às configurações de canal do dispositivo.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Exibir notificações para o aplicativo Portal da Empresa no Windows<!-- 1808082  -->
Atualizaremos o aplicativo Portal da Empresa em dispositivos Windows para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização mostrará notificações para aplicativos disponíveis somente quando o status da instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Exibir mensagens de status de instalação para o aplicativo Portal da Empresa<!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização<!-- 2576686 -->
O aplicativo do Intune em dispositivos Android e iOS permitirá que você controle o conteúdo de notificação do aplicativo para contas da organização. Esse recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Impedir que os usuários configurem credenciais de certificado no repositório de chaves gerenciado em dispositivos Android Enterprise de proprietário do dispositivo<!-- 3311998 idready -->
Em dispositivos Android Enterprise Device Owner, haverá uma nova configuração para impedir que os usuários configurem suas credenciais de certificado no repositório de chaves gerenciado (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **proprietário do dispositivo > apenas restrições de dispositivo** para o tipo de perfil > **usuários + contas**).

Para ver as configurações atuais, vá para [configurações do dispositivo Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Proprietário do dispositivo corporativo Android, incluindo dispositivos dedicados e totalmente gerenciados

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Perfis de configuração de dispositivo de rede com fio para dispositivos macOS<!-- 3508686 idready -->
Em dispositivos macOS, uma atualização futura incluirá um novo perfil de configuração de dispositivo que configura redes com fio (**configuração do dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **rede com fio** para o tipo de perfil). Use esse recurso para criar perfis 802.1 x para gerenciar redes com fio e implantar essas redes com fio em seus dispositivos macOS.

Aplica-se a:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Adicionar configurações de proxy automáticas a perfis de Wi-Fi para perfis de trabalho do Android Enterprise<!-- 4490822 idready -->
Em dispositivos Android Enterprise de perfil de trabalho, você pode criar perfis de Wi-Fi. Ao escolher o tipo de empresa Wi-Fi, você também pode inserir o tipo de protocolo EAP (Extensible Authentication Protocol) usado em sua rede Wi-Fi.

Em uma atualização futura, ao escolher o tipo Enterprise, você poderá inserir configurações de proxy automáticas, incluindo uma URL do servidor proxy, como `proxy.contoso.com`.

Para ver as configurações de Wi-Fi atuais que você pode configurar, vá para [Adicionar configurações de Wi-Fi para dispositivos que executam o Android Enterprise e Android quiosque no Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>Habilitar o NAC (controle de acesso à rede) com o Cisco AnyConnect VPN em dispositivos iOS<!-- 4860111 idready -->
Em dispositivos iOS, você pode criar um perfil VPN e usar tipos de conexão diferentes, incluindo o Cisco AnyConnect (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **VPN** para o tipo de perfil > **Cisco AnyConnect** para o tipo de conexão). 

Em uma atualização futura, você poderá habilitar o NAC (controle de acesso à rede) com o Cisco AnyConnect. Para usar esse recurso:

1. No [Guia do administrador do Cisco Identity Services Engine](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html), use as etapas em **configurando Microsoft Intune como um servidor MDM** para configurar o Cisco Identity Services Engine (ISE) no Azure.
2. No perfil de configuração de dispositivo do Intune, selecione a configuração **habilitar o controle de acesso à rede (NAC)** .

Para ver todas as configurações de VPN disponíveis, vá para [definir configurações de VPN em dispositivos IOS](../configuration/vpn-settings-ios.md).

Aplica-se a:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Experiência de logon único atualizada para aplicativos e sites em seus dispositivos iOS, iPadOS e macOS<!-- 4999578 idready -->
O Intune está adicionando mais configurações de logon único para dispositivos iOS, iPadOS e macOS. No momento, você pode configurar as extensões de aplicativo SSO de credencial e a extensão Kerberos interna da Apple no Intune. Em uma atualização futura, você poderá configurar extensões de aplicativo SSO de redirecionamento gravadas por sua organização ou pelo seu provedor de identidade. 

Use essas configurações para configurar uma experiência de logon único contínuo para aplicativos e sites que usam métodos de autenticação modernos, como OAuth e SAML2. 

Para ver as configurações de extensão do aplicativo SSO que você pode configurar, acesse [SSO no Ios](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) e [SSO no MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Aplica-se a:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Exigir o uso de teclados aprovados no Android<!--4761794 IDready -->
Você poderá especificar uma lista de teclados aprovados para uso em aplicativos Android gerenciados. A partir do aplicativo gerenciado, o usuário será solicitado a alternar para um dos teclados aprovados já instalados em seu dispositivo ou, se necessário, eles serão direcionados para o Google Play Store baixar e configurar um dos teclados aprovados. O usuário só poderá editar campos de texto em um aplicativo gerenciado se o teclado ativo for um dos keyboards aprovados.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Usar certificados PKCS com perfis Wi-Fi em dispositivos Windows 10 e posteriores<!-- 3246388  -->
No momento, você pode autenticar perfis Wi-Fi do Windows com certificados SCEP (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma > **Wi-Fi** para tipo de perfil > **tipo de EAP** > **Enterprise** ). Você poderá usar certificados PKCS com seus perfis de Wi-Fi do Windows. Esse recurso permite que os usuários autentiquem perfis Wi-Fi usando perfis de certificado PKCS novos ou existentes em seu locatário. 

Para obter mais informações sobre perfis Wi-Fi, consulte [Adicionar configurações de Wi-Fi para dispositivos Windows 10 e posteriores no Intune](../configuration/wi-fi-settings-windows.md).

Aplica-se a:
- Windows 10 e posterior

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Novas configurações de ExchangeActiveSync ao criar um perfil de configuração de dispositivo de email em dispositivos iOS<!-- 4892824  --> 
Em dispositivos iOS/iPadOS, você pode configurar a conectividade de email em um perfil de configuração de dispositivo (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios/iPadOS** para plataforma > **email** para tipo de perfil). 

Haverá novas configurações de ExchangeActiveSync disponíveis, incluindo:
- Escolha os serviços a serem sincronizados (ou bloqueie a sincronização), como email, calendário e contatos.
- Permitir que os usuários (ou bloquear) alterem as configurações de sincronização para esses serviços em seus dispositivos. 

Para ver as configurações atuais, vá para [configurações de perfil de email para dispositivos IOS no Intune](../configuration/email-settings-ios.md).

Aplica-se a:
- iOS 13,0 e mais recente
- iPadOS 13,0 e mais recente

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Impedir que os usuários adicionem contas pessoais do Google ao proprietário do dispositivo Android Enterprise e dispositivos dedicados<!-- 5353228  -->
Você poderá impedir que os usuários criem contas pessoais do Google no proprietário do dispositivo Android Enterprise e dispositivos dedicados (**configuração do dispositivo** **perfis** de >  > **Criar perfil** > **Android Enterprise** para a plataforma > **proprietário do dispositivo, somente > restrições de dispositivo** para o tipo de perfil > configurações de **contas e usuários**).

Para ver as configurações atuais que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Proprietário do dispositivo corporativo Android
- Dispositivos Android Enterprise dedicados

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>O log do lado do servidor para a configuração de comandos Siri é removido no perfil de restrições de dispositivo iOS<!-- 5468501  -->
Em dispositivos iOS, você pode criar um perfil de restrições de dispositivo que configura o log do lado do servidor para comandos Siri (**configuração do dispositivo** **perfis** de >  > **Criar perfil** > **Ios/iPadOS** para plataforma > **Restrições de dispositivo** para o tipo de perfil > **aplicativos internos**). A configuração **log do lado do servidor para comandos Siri** será removida.

Essa configuração será removida do console de administração do Intune. Essa configuração não tem nenhum efeito no dispositivo, embora as políticas existentes que tenham essa configuração configurada continuem a mostrar a configuração. Se você quiser remover a configuração de políticas existentes, vá para a política, faça uma pequena edição, salve-a e a política será atualizada.

Para ver as configurações que você pode definir, consulte [configurações do dispositivo IOS e iPadOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoramento e solução de problemas

### <a name="centralized-audit-logs--5603185-5697164--"></a>Logs de auditoria centralizados<!--5603185, 5697164-->
Uma nova experiência de log de auditoria centralizada coletará logs de auditoria para todas as categorias em uma única página. You'l ser capaz de filtrar os logs para obter os dados que você está procurando. Para ver os logs de auditoria, acesse **Administração de locatários** > **logs de auditoria**. Para obter mais informações, consulte [alteração futura para logs de auditoria no Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>Segurança

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Usar perfis de certificado PKCS para provisionar dispositivos com certificados<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
Você poderá usar um perfil de certificado PKCS para emitir certificados para dispositivos, expandindo o nosso suporte atual para certificados baseados no usuário. Certificados baseados em dispositivo terão suporte para as plataformas Android, iOS e Windows e podem ser usados para perfis de Wi-Fi e VPN.

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).


