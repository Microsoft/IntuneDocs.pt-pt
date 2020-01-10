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
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827824"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Em desenvolvimento para Microsoft Intune-janeiro de 2020

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Exibir notificações para o aplicativo Portal da Empresa no Windows<!-- 1808082  -->
Atualizaremos o aplicativo Portal da Empresa em dispositivos Windows para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização mostrará notificações para aplicativos disponíveis somente quando o status da instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Exibir mensagens de status de instalação para o aplicativo Portal da Empresa<!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>Redirecionar clipes da Web para o Microsoft Edge em dispositivos iOS<!-- 5455276 idready -->
Os clipes da Web, que atuam como aplicativos Web fixados em dispositivos iOS, precisarão ser atualizados. Os clipes da Web implantados recentemente serão abertos no Microsoft Edge em vez de Intune Managed Browser se necessário para abrir em um navegador protegido. Você deve redirecionar os clipes da Web preexistentes para garantir que eles sejam abertos no Microsoft Edge em vez de Managed Browser. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Alteração da experiência do usuário ao adicionar aplicativos ao Intune<!-- 4705829 idready -->
Você verá uma nova experiência do usuário ao adicionar aplicativos por meio do Intune. Essa experiência fornece as mesmas configurações e os detalhes que você usou anteriormente, no entanto, a nova experiência segue um processo do tipo assistente antes de adicionar um aplicativo ao Intune. Essa nova experiência também fornece uma página de revisão antes de adicionar o aplicativo. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **aplicativos** > **todos os aplicativos** > **Adicionar**. Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----3136567--"></a>Exigir que aplicativos Win32 reiniciem <!-- 3136567-->
Você pode exigir que um aplicativo Win32 precise ser reiniciado após uma instalação bem-sucedida. Além disso, você pode escolher a quantidade de tempo (o período de carência) antes que a reinicialização deva ocorrer.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Adicionar configurações de proxy automáticas a perfis de Wi-Fi para perfis de trabalho do Android Enterprise<!-- 4490822 idready -->
Em dispositivos Android Enterprise de perfil de trabalho, você pode criar perfis de Wi-Fi. Ao escolher o tipo de empresa Wi-Fi, você também pode inserir o tipo de protocolo EAP (Extensible Authentication Protocol) usado em sua rede Wi-Fi.

Em uma atualização futura, ao escolher o tipo Enterprise, você poderá inserir configurações de proxy automáticas, incluindo uma URL do servidor proxy, como `proxy.contoso.com`.

Para ver as configurações de Wi-Fi atuais que você pode configurar, vá para [Adicionar configurações de Wi-Fi para dispositivos que executam o Android Enterprise e Android quiosque no Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfis de configuração de dispositivo de rede com fio para dispositivos macOS<!-- 3508686  -->
Um novo perfil de configuração de dispositivo macOS estará disponível para configurar redes com fio (**configuração de dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **rede com fio** para o tipo de perfil). Use esse recurso para criar perfis 802.1 x para gerenciar redes com fio e implantar essas redes com fio em seus dispositivos macOS.

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
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>Bloquear registros do Android por fabricante do dispositivo<!--5197392 idready-->
Você poderá bloquear a inscrição de dispositivos com base no fabricante do dispositivo. Isso se aplica ao administrador do dispositivo Android e aos dispositivos Android Enterprise Work Profile. Para ver as restrições de registro, vá para o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)> **dispositivos** > **restrições de registro**.



<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos


### <a name="new-information-in-device-details---4471759-5604099----"></a>Novas informações nos detalhes do dispositivo<!-- 4471759 5604099  -->
As informações a seguir serão adicionadas à página **visão geral** para dispositivos:
- Capacidade de memória (quantidade de memória física no dispositivo)
- Capacidade de armazenamento (quantidade de armazenamento físico no dispositivo) 
- Tipo e velocidade do processador da CPU
- RAM e dados de processador

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>Novo Gerenciador de segurança de ponto de extremidade de função interna do Intune<!--4253397 idready-->
Uma nova função interna do Intune estará disponível: o Gerenciador de segurança do ponto de extremidade. Essa nova função dá aos administradores acesso completo ao nó do Gerenciador de ponto de extremidade no Intune e acesso somente pronto a outras áreas. A função é uma expansão da função "administrador de segurança" do Azure AD. Se atualmente você tiver apenas administradores globais como funções, não haverá nenhuma alteração necessária. Se você usar funções e quiser a granularidade que o Gerenciador de segurança de ponto de extremidade fornece, atribua essa função quando ela estiver disponível. Para obter mais informações sobre funções internas, consulte [controle de acesso baseado em função](role-based-access-control.md).

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Alterações de interface do usuário de funções do Intune recebidas<!--5801612 idready-->
A interface do usuário para o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > a **Administração de locatário** as **funções** > serão alteradas para um design mais amigável e intuitivo. Essa experiência fornece as mesmas configurações e os detalhes que você usa agora, no entanto, a nova experiência emprega um processo do tipo assistente.


<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Suporte a credenciais derivadas em dispositivos Android COBO<!--4839592-->
Você poderá usar credenciais derivadas em dispositivos Android Enterprise totalmente gerenciados. O suporte será incluído para recuperar uma credencial derivada para Entrust Datacard, intercedam e DISA purebred. Você poderá usar uma credencial derivada para autenticação de aplicativo, Wi-Fi, VPN ou assinatura S/MIME e/ou criptografia com aplicativos que dão suporte a ela. 

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).


