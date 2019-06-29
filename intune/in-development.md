---
title: No desenvolvimento – Microsoft Intune
titleSuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 633bf52084ad261f768cb4e59aaf4ce0ab5cd5bc
ms.sourcegitcommit: 46f4d3d160e18aeab9de7477eedc8351fbb78c85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/29/2019
ms.locfileid: "67468720"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>No desenvolvimento do Microsoft Intune – Julho de 2019

Para ajudar na preparação de sua e planejamento, esta página, listas de atualizações de interface do Usuário do Intune e recursos que estão em desenvolvimento, mas ainda não lançadas. Além disso:

- Se prevemos que precisará executar uma ação antes de uma alteração, vamos publicar uma mensagem complementar do Centro de mensagens do Office.
- Quando um recurso é iniciado na produção, como uma pré-visualização ou em disponibilidade geral, a descrição da funcionalidade irá mover esta página e para o [página Novidades](whats-new.md).
- Esta página e o [página Novidades](whats-new.md) são atualizados periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte a [M365 Roteiro](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e as linhas do tempo.

> [!Note]
> Estes itens refletem as expectativas de atuais da Microsoft sobre as capacidades do Intune numa versão futura. Datas e funcionalidades individuais podem ser alteradas. Nem todos os itens no desenvolvimento de tem uma descrição da funcionalidade nesta página.

**RSS feed**: Seja notificado quando esta página é atualizada ao copiar e colar o URL seguinte no seu leitor de feeds: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Os utilizadores de dispositivos, podem ver todas as aplicações geridas que tenham instalado ou tentou instalar <!-- 2352913 -->
Portal da empresa para Windows listará todas as aplicações geridas (tanto necessárias quanto disponíveis) que estão instaladas no dispositivo de um utilizador. Os utilizadores serão capazes de vista de tentativa e pendentes instalações de aplicações e respetivos Estados atuais. Se sua organização não torne as aplicações necessárias ou disponíveis, os utilizadores verão uma mensagem que explica que não existem aplicações da empresa foram instaladas. Os utilizadores também serão capazes de classificar ou filtrar as suas aplicações por Estado da instalação.

### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Notificações personalizadas para utilizadores e grupos    <!-- 16766574   -->
Em breve será capaz de enviar as notificações push personalizadas ad-hoc a partir da aplicação Portal da empresa aos utilizadores nos dispositivos iOS e Android que gere com o Intune. Estas notificações personalizadas não estão associadas a determinado funcionalidades do Intune e pode ser usadas para qualquer finalidade necessitam, incluindo notificações gerais que pretende enviar para alguns ou todos os seus funcionários.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar o conteúdo de notificação de aplicação para contas de organização <!-- 2576686 -->
Intune políticas de proteção (aplicação) em dispositivos Android e iOS vão permitir-lhe conteúdo de notificação da aplicação de controlo para contas de organização. Esta funcionalidade irá necessitar de suporte de aplicações e poderá não estar disponível para todas as aplicações da aplicação ativada. Para obter mais informações sobre a aplicação, consulte [quais são as políticas de proteção de aplicações?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Aplicação Google Play disponível, geração de relatórios para perfis de trabalho Android <!-- 3041956  -->
Para instalações de aplicações disponíveis em dispositivos de perfil de trabalho Android, pode ver o estado de instalação de aplicações, bem como a versão instalada do aplicações geridas do Google Play. Para obter mais informações, consulte [como monitorizar as políticas de proteção de aplicações](app-protection-policies-monitor.md), [Android gerir dispositivos de perfil de trabalho com o Intune](android-enterprise-overview.md) e [tipo de aplicação do Google Play gerido](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Suporte para perfis de IKEv2 VPN para iOS <!-- 1943438 -->
Poderá criar perfis VPN para o cliente VPN nativo iOS utilizando o protocolo IKEv2. IKEv2 é um novo tipo de ligação no **configuração do dispositivo** > **perfis** > **criar perfil** > **iOS**  para a plataforma > **VPN** para o tipo de perfil > **definições**.

Estes perfis VPN configurar o cliente VPN nativo. Portanto, não existem aplicações de cliente VPN forem instaladas ou enviada por push para dispositivos geridos. Esta funcionalidade requer a dispositivos inscritos no Intune (inscrição de MDM).

Para ver as definições atuais do VPN, pode configurar, aceda à [definições de VPN configurar em dispositivos iOS no Microsoft Intune](vpn-settings-ios.md).

Aplica-se a: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilize "regras de aplicabilidade" quando criar perfis de configuração de dispositivo Windows 10 <!-- 2549910 -->
Criar perfis de configuração de dispositivo Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma). Poderá criar uma **regra de aplicabilidade** para que o perfil apenas se aplica a uma edição específica ou uma versão específica. Por exemplo, criar um perfil que permite que algumas configurações de disco BitLocker. Depois de adicionar o perfil, utilize uma regra de aplicabilidade para que o perfil apenas se aplica a dispositivos com o Windows 10 Enterprise.

Aplica-se a: 
- Windows 10 e posterior

### <a name="administrative-templates-for-group-policy---------3510695---"></a>Modelos administrativos de política de grupo     <!--  3510695 -->
Para ajudar a melhorar a segurança para dispositivos na cloud, vamos lançar modelos administrativos que lhe permitirá utilizar o Intune para configurar as definições de política de grupo selecionadas para Windows PCs.  Estes modelos de utilizam o fornecedor de serviços de configuração de política (CSP) para fornecer até 2500 definições adicionais do Office, o Windows e o OneDrive.

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>Gerir o FileVault para macOS   <!--  3858502 + 1210104   -->
Será capaz de utilizar um perfil de configuração de dispositivo do Intune endpoint protection para gerir a encriptação de chave FileVault para dispositivos macOS. Isto inclui a caução da visualização das e rodar as chaves de encriptação de dispositivos da sua empresa. Os utilizadores finais será capazes de recuperar essas chaves através do site do Portal da empresa.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Definições avançadas do Firewall do Windows Defender   <!--  1311949     -->
Como pré-visualização pública, em breve poderá utilizar o Intune para gerir as regras de firewall personalizadas nos clientes para o Windows Defender.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Novo designer de configuração ao criar um perfil de OEMConfig do Android Enterprise <!-- 3712769  -->
No Intune, pode criar um perfil de configuração de dispositivo que utiliza uma aplicação de OEMConfig (configuração do dispositivo > perfis > Criar perfil > Android enterprise para a plataforma > OEMConfig para tipo de perfil). Ao fazê-lo, um editor de JSON é aberto com um modelo e os valores que pode alterar. Esta atualização inclui um Designer de configuração com uma experiência de usuário aprimorada que mostra detalhes incorporados na aplicação, incluindo os títulos, descrições e muito mais. O editor de JSON ainda está disponível e mostra todas as alterações que fizer no Designer de configuração.

Para ver as definições atuais, aceda à [utilizar e gerir dispositivos Android Enterprise com OEMConfig](android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="improve-device-location---3855417---"></a>Melhorar a localização do dispositivo<!-- 3855417 -->
Será capaz de ampliar para as coordenadas exatas de um dispositivo utilizando o **localizar dispositivo** ação. Para obter mais informações sobre como localizar dispositivos iOS perdidos, consulte [localizar dispositivos iOS perdidos](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurar o limite de tempo de limpeza automática de dispositivo para baixo até 30 dias <!--4231059  -->
Será capaz de definir o limite de tempo de limpeza de automático de dispositivos mais curto 30 dias (em vez de limite atual de 90 dias) após o último início de sessão. Para tal, aceda a **Intune** > **dispositivos** > **configuração** > **limpa a regras do dispositivo**.


<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="import-and-export-security-baselines------3408610------------"></a>Importar e exportar linhas de base de segurança    <!--3408610          -->  
Estamos a adicionar a capacidade de exportar e importar linhas de base de segurança para que possa tirar suas personalizações consigo e partilhá-los entre ambientes do Intune.



<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


