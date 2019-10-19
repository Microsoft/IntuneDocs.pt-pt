---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601534"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Em desenvolvimento para Microsoft Intune-outubro de 2019

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

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Atribuir o Microsoft Edge beta para macOS <!-- 4678761  -->
Você poderá adicionar e atribuir a versão mais recente do Microsoft Edge beta ao Intune para dispositivos macOS. 

Para atribuir o Microsoft Edge beta para dispositivos macOS:
1. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar aplicativo** > **Microsoft Edge-MacOS**. 
1. Atribua o Microsoft Edge beta aos grupos pretendidos. O Microsoft AutoUpdate (MAU) mantém o Microsoft Edge atualizado. 
 
Para obter mais informações sobre o Microsoft Edge, consulte [gerenciar o acesso via Web usando o Microsoft Edge com o Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
O aplicativo do Intune em dispositivos Android e iOS permitirá que você controle o conteúdo de notificação do aplicativo para contas da organização. Esse recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Novo perfil de interface de configuração de firmware de dispositivo para dispositivos que executam o Windows 10 e posterior <!-- 2266073  -->
No Windows 10 e posterior, você pode criar um perfil de configuração de dispositivo para controlar as configurações e os recursos: 

1. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
1. Para a plataforma, selecione **Windows 10 e posterior**. 
 
Um novo tipo de perfil de interface de configuração de firmware de dispositivo permitirá que o Intune gerencie configurações de UEFI (BIOS).

Para obter informações sobre as configurações atuais que você pode configurar, consulte [aplicar recursos e configurações em seus dispositivos usando perfis de dispositivo no Microsoft Intune](../configuration/device-profiles.md).

Esse recurso se aplica ao Windows 10 RS5 (1809) e posterior, em selecionar dispositivos.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>Para dispositivos iOS, personalize a janela de privacidade de registro do Portal da Empresa <!-- 4394993  -->
Ao usar a redução, você poderá personalizar a janela de privacidade de Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você pode personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Editar o valor da marca do grupo para dispositivos de piloto automático<!-- 4816775 -->
Você poderá editar o valor da **marca do grupo** para dispositivos de piloto automático:

1. Selecione **Intune**  > **registro de dispositivo**  > **registro do Windows**  > **dispositivos** **Windows AutoPilot**  > .
1. Escolha o dispositivo.
1. No painel à direita, altere o valor da **marca de grupo** .
1. Selecione **Guardar**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Direcione os grupos de usuários do macOS para exigir o gerenciamento de JAMF <!-- 4061739 -->
Você poderá direcionar grupos específicos de usuários para exigir que seus dispositivos macOS sejam gerenciados pelo JAMF. Esse direcionamento permitirá que você aplique a integração de conformidade do JAMF a um subconjunto de dispositivos macOS enquanto outros dispositivos continuam a ser gerenciados pelo Intune. O direcionamento também permitirá que você migre gradualmente os dispositivos dos usuários de um sistema de MDM (gerenciamento de dispositivo móvel) para o outro.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implantar atualizações de software em dispositivos macOS <!-- 3194876 -->
Você poderá implantar atualizações de software em grupos de dispositivos macOS. Esse recurso inclui o arquivo crítico, firmware, configuração e outras atualizações. Você pode enviar atualizações no próximo check-in do dispositivo. Ou você pode selecionar uma agenda semanal para implantar atualizações dentro ou fora dos períodos que você definiu. 

Esse recurso ajuda quando você deseja atualizar dispositivos fora do horário de trabalho padrão ou fora do horário em que o suporte técnico está totalmente na equipe. Você também obterá um relatório detalhado de todos os dispositivos macOS que têm atualizações implantadas. Você pode analisar o relatório por dispositivo para ver o status de uma atualização específica.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoramento e solução de problemas

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Relatório do Android na página Visão geral de dispositivos <!-- 2984353  -->
Vamos adicionar um novo relatório à página **visão geral de dispositivos** . O relatório exibe quantos dispositivos Android foram registrados em cada solução de gerenciamento de dispositivo. O gráfico mostra as contagens de dispositivos para o perfil de trabalho, totalmente gerenciado, dedicado e de administrador de dispositivo registrado. 

Para ver o relatório, escolha o **Intune** > **dispositivos** > **visão geral**.

### <a name="updated-support-experience-------5012398------"></a>Experiência de suporte atualizada   <!--  5012398    -->
Como parte de aprimoramentos contínuos, atualizaremos a experiência de suporte no console do Intune.  Aprimoraremos a pesquisa no console e os comentários para problemas comuns e simplificaremos o fluxo de trabalho para entrar em contato com o suporte.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).
