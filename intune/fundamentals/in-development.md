---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912641"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Em desenvolvimento para Microsoft Intune-janeiro de 2020

Para ajudar na preparação e no planejamento, esta página lista as atualizações da interface do usuário do Intune e os recursos que estão em desenvolvimento, mas ainda não foram lançados. Além das informações nesta página: 

- Se prevemos que você precisará tomar medidas antes de uma alteração, publicaremos uma postagem complementar no centro de mensagens do Office.
- Quando um recurso entra em produção, seja uma visualização ou geralmente disponível, a descrição do recurso passará dessa [página para as novidades.](whats-new.md)
- Esta página e a página [novidades](whats-new.md) são atualizadas periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte o [roteiro de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e cronogramas.

> [!NOTE]
> Esta página reflete nossas expectativas atuais sobre os recursos do Intune em uma versão futura. As datas e os recursos individuais podem mudar. Esta página não descreve todos os recursos no desenvolvimento.

**Feed RSS**: Descubra quando esta página é atualizada copiando e colando o seguinte URL no leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Exibir notificações para o aplicativo Portal da Empresa no Windows<!-- 1808082  -->
Atualizaremos o aplicativo Portal da Empresa em dispositivos Windows para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização mostrará notificações para aplicativos disponíveis somente quando o status da instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Exibir mensagens de status de instalação para o aplicativo Portal da Empresa<!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Redirecionar clipes da Web para o Microsoft Edge em dispositivos iOS<!-- 5455276 -->
Os clipes da Web, que atuam como aplicativos Web fixados em dispositivos iOS, precisarão ser atualizados. Os clipes da Web implantados recentemente serão abertos no Microsoft Edge em vez de Intune Managed Browser se necessário para abrir em um navegador protegido. Você deve redirecionar os clipes da Web preexistentes para garantir que eles sejam abertos no Microsoft Edge em vez de Managed Browser. 


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfis de configuração de dispositivo de rede com fio para dispositivos macOS<!-- 3508686  -->
Um novo perfil de configuração do dispositivo macOS estará disponível que configura redes com fios (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **macOS** para plataforma > **Rede Com fios** para tipo de perfil). Use esse recurso para criar perfis 802.1 x para gerenciar redes com fio e implantar essas redes com fio em seus dispositivos macOS.

Aplica-se a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>Perfis VPN com conexões VPN IKEv2 podem usar o Always on com dispositivos iOS <!-- 1947932 idready -->
Em dispositivos iOS, você pode criar um perfil VPN que usa uma conexão IKEv2 (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios/iPadOS** para plataforma > **VPN** para o tipo de perfil). Em uma atualização futura, você pode configurar o Always on com o IKEv2. Quando configurados, os perfis VPN IKEv2 se conectam automaticamente e permanecem conectados (ou reconectam-se rapidamente) à VPN. Ele permanece conectado mesmo ao se mover entre redes ou reiniciar dispositivos.

No iOS, a VPN AlwaysOn é limitada a perfis IKEv2.

Para ver as configurações IKEv2 atuais que você pode configurar, vá para [Adicionar configurações de VPN em dispositivos IOS em Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Aplica-se a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Experiência aprimorada de interface do usuário ao criar perfis de configuração em dispositivos iOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Quando você cria um perfil para dispositivos iOS ou macOS, a experiência no centro de administração do gerenciamento de pontos de extremidade será atualizada. Essa alteração afeta os seguintes perfis de configuração de dispositivo (**dispositivos** > **perfis de configuração** > **Criar perfil** > **Ios** ou **MacOS** para plataforma):

- Personalizado: iOS, macOS
- Recursos do dispositivo: iOS, macOS
- Restrições de dispositivo: iOS, macOS
- Endpoint Protection: macOS
- Extensões: macOS
- Arquivo de preferência: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Experiência aprimorada de interface do usuário ao criar perfis de configuração do OEMConfig em dispositivos Android Enterprise<!-- 5568645 idready  -->
Quando você cria ou edita um perfil do OEMConfig para dispositivos Android Enterprise, a experiência no centro de administração do gerenciamento de pontos de extremidade é atualizada. A experiência atualizada fornecerá um resumo das configurações que você configurou em um relance. Essa alteração afeta o perfil de configuração do dispositivo OEMConfig (**dispositivos** > **perfis de configuração** > **Criar perfil** > **Android Enterprise** para plataforma > **OEMConfig** para o tipo de perfil).

Esta funcionalidade aplica-se a:
- Android Enterprise 

<!-- ***********************************************-->
<!--## Device enrollment-->



<!-- ***********************************************-->
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Alterações de interface do usuário de funções do Intune recebidas<!--5801612 idready-->
A interface do usuário para o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > a **Administração de locatário** as **funções** > serão alteradas para um design mais amigável e intuitivo. Essa experiência fornece as mesmas configurações e os detalhes que você usa agora, no entanto, a nova experiência emprega um processo do tipo assistente.


<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Suporte a credenciais derivadas em dispositivos Android COBO<!--4839592-->
Você poderá usar credenciais derivadas em dispositivos Android Enterprise totalmente gerenciados. O suporte será incluído para recuperar uma credencial derivada para Entrust Datacard, intercedam e DISA purebred. Você poderá usar uma credencial derivada para autenticação de aplicativo, Wi-Fi, VPN ou assinatura S/MIME e/ou criptografia com aplicativos que dão suporte a ela. 

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Veja também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).


