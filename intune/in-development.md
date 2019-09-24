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
ms.openlocfilehash: 6c88dca505c3ef9d9d552e55e9991679f5f5e0fa
ms.sourcegitcommit: 5968a38c302394d4b0cf81156e7b52531cdec107
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71198817"
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

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portal da Empresa mensagens de status de instalação do aplicativo <!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.
- O aplicativo foi instalado com êxito, mas requer uma reinicialização.
- O aplicativo está no processo de instalação, mas requer uma reinicialização para continuar.

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android e iOS permitirão que você controle o conteúdo de notificação do aplicativo para contas da organização. Este recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android <!-- 3041956  -->
Para instalações de aplicativos disponíveis em dispositivos Android de perfil de trabalho, você pode exibir o status de instalação do aplicativo e a versão instalada dos aplicativos gerenciados Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
<!--## Device configuration-->

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa <!-- 4394993  -->
Usando a redução, você poderá personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implantar atualizações de software em dispositivos macOS <!-- 3194876 -->
Você poderá implantar atualizações de software em grupos de dispositivos macOS. Esse recurso inclui o arquivo crítico, firmware, configuração e outras atualizações. Você poderá enviar atualizações no próximo check-in do dispositivo ou selecionar uma agenda semanal para implantar atualizações dentro ou fora do tempo que você definir. Isso ajuda quando você deseja atualizar dispositivos fora do horário de trabalho padrão ou quando o suporte técnico está totalmente na equipe. Você também obterá um relatório detalhado de todos os dispositivos macOS com atualizações implantadas. Você pode analisar o relatório de acordo com o dispositivo para ver os status de atualizações específicas.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

### <a name="updated-support-experience-------5012398------"></a>Experiência de suporte atualizada   <!--  5012398    -->
Como parte dos aprimoramentos contínuos, atualizaremos a experiência de suporte no console do Intune.  Vamos melhorar a pesquisa no console e os comentários para problemas comuns e simplificar o fluxo de trabalho para entrar em contato com o suporte.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.




