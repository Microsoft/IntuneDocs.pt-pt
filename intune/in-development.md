---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9b02deb529bd6a9bca882fecb3d55d9db513191
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427177"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Em desenvolvimento para Microsoft Intune – julho de 2019

Para ajudá-lo em sua preparação e planejamento, esta página lista as atualizações da interface do usuário do Intune e os recursos que estão em desenvolvimento, mas ainda não foram lançados. Além disso:

- Se prevemos que você precisará tomar uma atitude antes de uma alteração, publicaremos uma postagem complementar do centro de mensagens do Office.
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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android e iOS permitirão que você controle o conteúdo de notificação do aplicativo para contas da organização. Este recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android <!-- 3041956  -->
Para instalações de aplicativos disponíveis em dispositivos Android de perfil de trabalho, você pode exibir o status de instalação do aplicativo, bem como a versão instalada dos aplicativos gerenciados Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Suporte para perfis VPN IKEv2 para iOS <!-- 1943438 -->
Você poderá criar perfis de VPN para o cliente VPN nativo do iOS usando o protocolo IKEv2. IKEv2 é um novo tipo de conexão no **dispositivo** > **perfis** > de configuração**Criar perfil** > **Ios** para plataforma > **VPN** para tipo de perfil > **configurações**.

Esses perfis de VPN configuram o cliente VPN nativo. Portanto, nenhum aplicativo cliente VPN é instalado ou enviado por push para dispositivos gerenciados. Esse recurso requer que os dispositivos sejam registrados no Intune (registro de MDM).

Para ver as configurações de VPN atuais que você pode configurar, vá para [definir configurações de VPN em dispositivos IOS em Microsoft Intune](vpn-settings-ios.md).

Aplica-se a: iOS


<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurar o limite de tempo de limpeza de dispositivo automático para 30 dias <!--4231059  -->
Você poderá definir o limite de tempo de limpeza do dispositivo automático como 30 dias (em vez do limite atual de 90 dias) após a última entrada. Para fazer isso, vá para**dispositivos** > do **Intune** > **Configurar** > **regras de limpeza do dispositivo**.

<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="import-and-export-security-baselines------3408610------------"></a>Importar e exportar linhas de base de segurança    <!--3408610          -->  
Estamos adicionando a capacidade de exportar e importar linhas de base de segurança para que você possa fazer suas personalizações com você e compartilhá-las entre os ambientes do Intune.


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


