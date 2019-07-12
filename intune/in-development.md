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
ms.openlocfilehash: 47e1a3870e1da1514ad07e8dad5c6117ffc108a9
ms.sourcegitcommit: ce9cae824a79223eab3c291fd5d5e377efac84cb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67842705"
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


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Notificações personalizadas para usuários e grupos    <!-- 16766574   -->
Em breve, você poderá enviar notificações por push ad hoc personalizadas do aplicativo Portal da Empresa para os usuários em dispositivos iOS e Android gerenciados com o Intune. Essas notificações personalizadas não estão ligadas a recursos específicos do Intune e podem ser usadas para qualquer finalidade necessária, incluindo notificações gerais que você deseja enviar a alguns ou a todos os seus funcionários.  

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

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Use "regras de aplicabilidade" ao criar perfis de configuração de dispositivo do Windows 10 <!-- 2549910 -->
Você cria perfis de configuração de dispositivo do Windows 10 (**perfis** > de**configuração** > de dispositivo**Criar perfil** > **Windows 10** para plataforma). Você poderá criar uma **regra de aplicabilidade** para que o perfil se aplique somente a uma edição específica ou a uma versão específica. Por exemplo, você cria um perfil que habilita algumas configurações do BitLocker. Depois de adicionar o perfil, use uma regra de aplicabilidade para que o perfil se aplique somente a dispositivos que executam o Windows 10 Enterprise.

Aplica-se a: 
- Windows 10 e posterior

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>Gerenciar FileVault para macOS   <!--  3858502 + 1210104   -->
Você poderá usar um perfil de configuração de dispositivo do Intune Endpoint Protection para gerenciar a criptografia de chave FileVault para dispositivos macOS. Isso inclui a caução de, a exibição e a rotação das chaves de criptografia de seus dispositivos corporativos. Os usuários finais poderão recuperar essas chaves por meio do site Portal da Empresa.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Configurações avançadas para o Windows Defender firewall   <!--  1311949     -->
Como uma visualização pública, em breve você poderá usar o Intune para gerenciar as regras de firewall personalizadas em clientes do Windows Defender.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Novo designer de configuração ao criar um perfil de OEMConfig para Android Enterprise <!-- 3712769  -->
No Intune, você pode criar um perfil de configuração de dispositivo que usa um aplicativo OEMConfig (configuração de dispositivo > perfis > Criar perfil > Android Enterprise para plataforma > OEMConfig para o tipo de perfil). Quando você faz isso, um editor de JSON é aberto com um modelo e valores para que você altere. Essa atualização inclui um designer de configuração com uma experiência de usuário aprimorada que mostra detalhes inseridos no aplicativo, incluindo títulos, descrições e muito mais. O editor de JSON ainda está disponível e mostra as alterações feitas no designer de configuração.

Para ver as configurações atuais, vá para [usar e gerenciar dispositivos Android Enterprise com o OEMConfig](android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="improve-device-location---3855417---"></a>Melhorar o local do dispositivo<!-- 3855417 -->
Você poderá ampliar as coordenadas exatas de um dispositivo usando a ação **Localizar dispositivo** . Para obter mais informações sobre como localizar dispositivos iOS perdidos, consulte [localizar dispositivos IOS perdidos](device-locate.md).

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


