---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4beb9c841cb2f4a5b7198fe031caa67da9e28842
ms.sourcegitcommit: 4bf23327af734a9811d555fbd566c31239e2acd6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/29/2019
ms.locfileid: "72999442"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>Em desenvolvimento para Microsoft Intune – novembro de 2019

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Suporte a S/MIME para Microsoft Outlook Mobile <!-- 2669398  -->
O Intune dará suporte à entrega de certificados de criptografia e autenticação S/MIME que podem ser usados com o Outlook Mobile no iOS e no Android. Para obter informações relacionadas, consulte [configurações de email para dispositivos IOS](~/configuration/email-settings-ios.md) e [configurações de email para dispositivos Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Suporte a configurações personalizadas para aplicativos macOS <!-- 4736278  -->
O Intune dará suporte a configurações personalizadas, permitindo que você adicione chaves e valores específicos a um arquivo de lista de propriedades de preferências (. plist) existente para configurar aplicativos macOS e o dispositivo. Nem todos os aplicativos dão suporte a preferências gerenciadas e, em alguns casos, apenas configurações específicas podem ser gerenciadas. As configurações são implantadas somente por meio do canal do dispositivo. Você deve carregar somente arquivos de lista de propriedades ou arquivos. XML que destinam-se às configurações de canal do dispositivo.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Valor do tipo de atribuição no Windows Portal da Empresa <!-- 5459950  -->
A página **aplicativos instalados** do aplicativo Windows portal da empresa será atualizada. A coluna **tipo de atribuição** da página **aplicativos instalados** foi atualizada para ser chamada "exigida pela sua organização". Os valores possíveis são **Sim** ou **não** para designar aplicativos necessários versus disponíveis. Essa alteração está sendo feita em resposta a alguma confusão do usuário final. Para obter mais informações sobre o portal da empresa do Windows, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](~/apps/company-portal-app.md).

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Aplicar modo escuro no Portal da Empresa do iOS <!-- 4911422  -->
O modo escuro está planejado para Portal da Empresa do iOS. Você poderá baixar aplicativos da empresa, gerenciar seus dispositivos e obter suporte de ti no esquema de cores de sua escolha. Para obter mais informações sobre Portal da Empresa do iOS, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](../apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Executar aplicativos Win32 em dispositivos de modo S do Windows 10 <!-- 3747604  --> 
Você poderá instalar e executar aplicativos Win32 em dispositivos que são gerenciados no modo Windows 10 S. Crie uma ou mais políticas complementares para o modo S usando as ferramentas do PowerShell do Windows Defender Application Control (WDAC). Use o portal de assinatura do Device Guard para assinar as políticas complementares. Em seguida, carregue e distribua as políticas por meio do Intune. 

No Intune, você encontrará esse recurso selecionando **aplicativos cliente** > **políticas complementares do Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Definir a disponibilidade do aplicativo com base em uma data e hora <!-- 3510685  -->
Como administrador, você poderá configurar a hora de início e a data limite para um aplicativo necessário. Na hora de início, a extensão de gerenciamento do Intune baixará o conteúdo do aplicativo e irá armazená-lo em cache. O aplicativo será instalado na hora do prazo. Para aplicativos disponíveis, a hora de início determinará quando o aplicativo estiver visível no Portal da Empresa. 

Para definir a disponibilidade do aplicativo com base na data e hora:

1. No Intune, selecione **aplicativos cliente** > **aplicativos**. 
1. Selecione um aplicativo na lista ou adicione um novo selecionando **Adicionar**. 
1. Na folha do aplicativo, selecione **atribuições** > **Adicionar grupo**. 
1. Defina o **tipo de atribuição** como **obrigatório** e, em seguida, selecione **grupos incluídos**. 
1. Defina **tornar este aplicativo necessário para que todos os usuários** sejam **Sim**. 
1. Selecione **Editar** para modificar as opções de **experiência do usuário final** . 
1. Na folha **experiência do usuário final** , defina o **tempo disponível do software** conforme necessário. 

Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Exigir que aplicativos Win32 reiniciem <!-- 3136567  -->
Você poderá exigir que um aplicativo Win32 seja reiniciado após uma instalação bem-sucedida. Você pode escolher a quantidade de tempo (o período de carência) antes da reinicialização.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Exibir notificações para o aplicativo Portal da Empresa no Windows <!-- 1808082  -->
Atualizaremos o aplicativo Portal da Empresa em dispositivos Windows para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização mostrará notificações para aplicativos disponíveis somente quando o status da instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Exibir mensagens de status de instalação para o aplicativo Portal da Empresa <!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.
- O aplicativo foi instalado com êxito, mas requer uma reinicialização.
- O aplicativo está no processo de instalação, mas requer uma reinicialização para continuar.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
O aplicativo do Intune em dispositivos Android e iOS permitirá que você controle o conteúdo de notificação do aplicativo para contas da organização. Esse recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Usar certificados PKCS com perfis Wi-Fi em dispositivos Windows 10 e posteriores <!-- 3246388  -->
No momento, você pode autenticar perfis Wi-Fi do Windows com certificados SCEP (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma > **Wi-Fi** para tipo de perfil > **tipo de EAP** > **Enterprise** ). Você poderá usar certificados PKCS com seus perfis de Wi-Fi do Windows. Esse recurso permite que os usuários autentiquem perfis Wi-Fi usando perfis de certificado PKCS novos ou existentes em seu locatário. 

Para obter mais informações sobre perfis Wi-Fi, consulte [Adicionar configurações de Wi-Fi para dispositivos Windows 10 e posteriores no Intune](../configuration/wi-fi-settings-windows.md).

Aplica-se a:
- Windows 10 e posterior

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Novas configurações de ExchangeActiveSync ao criar um perfil de configuração de dispositivo de email em dispositivos iOS <!-- 4892824  --> 
Em dispositivos iOS/iPadOS, você pode configurar a conectividade de email em um perfil de configuração de dispositivo (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios/iPadOS** para plataforma > **email** para tipo de perfil). 

Haverá novas configurações de ExchangeActiveSync disponíveis, incluindo:
- Escolha os serviços a serem sincronizados (ou bloqueie a sincronização), como email, calendário e contatos.
- Permitir que os usuários (ou bloquear) alterem as configurações de sincronização para esses serviços em seus dispositivos. 

Para ver as configurações atuais, vá para [configurações de perfil de email para dispositivos IOS no Intune](../configuration/email-settings-ios.md).

Aplica-se a:
- iOS 13,0 e mais recente
- iPadOS 13,0 e mais recente

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Impedir que os usuários adicionem contas pessoais do Google ao proprietário do dispositivo Android Enterprise e dispositivos dedicados <!-- 5353228  -->
Você poderá impedir que os usuários criem contas pessoais do Google no proprietário do dispositivo Android Enterprise e dispositivos dedicados (**configuração do dispositivo** **perfis** de >  > **Criar perfil** > **Android Enterprise** para a plataforma > **proprietário do dispositivo, somente > restrições de dispositivo** para o tipo de perfil > configurações de **contas e usuários**).

Para ver as configurações atuais que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Proprietário do dispositivo corporativo Android
- Dispositivos Android Enterprise dedicados

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>O log do lado do servidor para a configuração de comandos Siri é removido no perfil de restrições de dispositivo iOS <!-- 5468501  -->
Em dispositivos iOS, você pode criar um perfil de restrições de dispositivo que configura o log do lado do servidor para comandos Siri (**configuração do dispositivo** **perfis** de >  > **Criar perfil** > **Ios/iPadOS** para plataforma > **Restrições de dispositivo** para o tipo de perfil > **aplicativos internos**). A configuração **log do lado do servidor para comandos Siri** será removida.

Essa configuração será removida do console de administração do Intune. Essa configuração não tem nenhum efeito no dispositivo, embora as políticas existentes que tenham essa configuração configurada continuem a mostrar a configuração. Se você quiser remover a configuração de políticas existentes, vá para a política, faça uma pequena edição, salve-a e a política será atualizada.

Para ver as configurações que você pode definir, consulte [configurações do dispositivo IOS e iPadOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Editar o valor do nome do dispositivo para dispositivos de piloto automático<!-- 2640074  -->
Você poderá editar o valor do nome do dispositivo para dispositivos de piloto automático ingressados no Azure AD. Para fazer isso, acesse **Intune** > **registro de dispositivo** > **registro do Windows** > **dispositivos** > do **Windows AutoPilot** > escolha o dispositivo > alterar o valor **nome do dispositivo** no painel direito > **Salvar**.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Editar o valor da marca do grupo para dispositivos de piloto automático<!-- 4816775 -->
Você poderá editar o valor da **marca do grupo** para dispositivos de piloto automático:

1. Selecione **Intune**  > **registro de dispositivo**  > **registro do Windows**  > **dispositivos** **Windows AutoPilot**  > .
1. Escolha o dispositivo.
1. No painel à direita, altere o valor da **marca de grupo** .
1. Selecione **Guardar**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Direcione os grupos de usuários do macOS para exigir o gerenciamento de JAMF <!-- 4061739 -->
Você poderá direcionar grupos específicos de usuários para exigir que seus dispositivos macOS sejam gerenciados pelo JAMF. Esse direcionamento permitirá que você aplique a integração de conformidade do JAMF a um subconjunto de dispositivos macOS enquanto outros dispositivos continuam a ser gerenciados pelo Intune. O direcionamento também permitirá que você migre gradualmente os dispositivos dos usuários de um sistema de MDM (gerenciamento de dispositivo móvel) para o outro.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Aplicações do Intune

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Experiência aprimorada de registro do macOS no Portal da Empresa <!-- 5074349  -->
O Portal da Empresa para a experiência de registro do macOS terá um processo de registro mais simples que se alinhará mais com o Portal da Empresa da experiência de registro do iOS. Os usuários do dispositivo verão:  

* Uma interface do usuário mais elegante.  
* Uma lista de verificação de registro aprimorada.  
* Instruções mais claras sobre como registrar seus dispositivos.  
* Opções de solução de problemas aprimoradas.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Design de lista de verificação aprimorado no aplicativo Portal da Empresa para Android<!-- 5550857  -->
A lista de verificação de configuração no aplicativo Portal da Empresa para Android será atualizada com um design leve e novos ícones. As alterações serão alinhadas com as atualizações recentes feitas no aplicativo Portal da Empresa para iOS.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoramento e solução de problemas

### <a name="updated-support-experience-------5012398------"></a>Experiência de suporte atualizada   <!--  5012398    -->
Como parte de aprimoramentos contínuos, atualizaremos a experiência de suporte no console do Intune.  Aprimoraremos a pesquisa no console e os comentários para problemas comuns e simplificaremos o fluxo de trabalho para entrar em contato com o suporte.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Duplicar funções personalizadas ou internas <!-- 1081938 -->
Você poderá copiar funções internas e personalizadas. Para fazer isso, acesse **Intune** > **funções** > **todas as funções** > escolha uma função na lista > **duplicada**. Certifique-se de inserir um novo nome que seja exclusivo.

<!-- ***********************************************-->

## <a name="security"></a>Segurança

### <a name="bitlocker-key-rotation--------2564951--------"></a>Rotação de chave do BitLocker     <!-- 2564951      -->
Você poderá usar o Intune para girar as chaves de recuperação do BitLocker para dispositivos gerenciados que executam o Windows versão 1909 ou posterior. 

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).
