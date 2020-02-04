---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cafe9d3036a727d79de88eda050399138da55675
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977755"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Em desenvolvimento para microsoft Intune - fevereiro 2020

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

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>melhorias na experiência do utilizador do portal da empresa macOS<!-- 5568987 -->
Estamos a fazer melhorias na experiência de inscrição de dispositivos macOS e na aplicação Do Portal da Empresa para o Mac. Pode esperar o seguinte:
- Uma melhor experiência do Microsoft **AutoUpdate** durante a inscrição que irá garantir que os seus utilizadores tenham a versão mais recente do Portal da Empresa.
- Um passo de verificação de conformidade melhorado durante a inscrição.
- Suporte para IDs de incidentecopiados, para que os seus utilizadores possam enviar erros dos seus dispositivos para a sua equipa de suporte da empresa mais rapidamente.

Para obter mais informações sobre a inscrição e a aplicação Portal da Empresa para Mac, consulte Inscrever o seu dispositivo macOS utilizando a aplicação Portal da Empresa (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp). 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Ecrã removido do Portal da Empresa, inscrição de perfil de trabalho Android<!--6103987 -->
O **próximo** ecrã será removido do fluxo de inscrição de perfil de trabalho Android no Portal da Empresa, para simplificar a experiência do utilizador. Vá ao [Enroll with Android work profile]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile) para ver o fluxo atual de inscrição de perfil de trabalho Android.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>Aplicação microsoft Defender Advanced Threat Protection (ATP) para macOS<!-- 5424518 idready -->
A Intune fornecerá uma forma fácil de implementar a aplicação Microsoft Defender Advanced Threat Protection (ATP) para o macOS para gerir dispositivos Mac. Para mais informações, consulte [o Microsoft Defender Advanced Threat Protection for Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

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
## <a name="device-management"></a>Gestão de dispositivos

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Alterar o utilizador primário para dispositivos Windows <!-- 3794742 -->
Poderá alterar o Utilizador Principal para dispositivos híbridos windows e Azure AD. Para tal, vá a **Intune** > **Devices** > **Todos os dispositivos** > escolha um dispositivo > **Propriedades** > **Utilizador Primário**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Número de série na página de certificado Apple MDM Push<!--5947765 -->
A página do certificado Apple MDM Push mostrará o número de série. O número de série é necessário para recuperar o acesso ao certificado Apple MDM Push se o acesso ao Apple ID que criou o certificado for perdido. Para ver o número de série, vá a **Dispositivos** > **iOS** > **matrícula do iOS** > **certificado Apple MDM Push**.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Escolha quais as atualizações iOS/iPadOS para empurrar para dispositivos matriculados<!--5879689 -->
Poderá escolher uma atualização específica do iOS/iPadOS para empurrar para dispositivos que se inscreveram utilizando o Apple Business Manager ou o Apple School Manager. Estes dispositivos devem ter uma política de configuração do dispositivo definida para atrasar a visibilidade da atualização do software durante alguns dias. Para ver esta funcionalidade, vá ao MEM > **Dispositivos** > **iOS** > **Atualizar as políticas para iOS/iPadOS** > Criar **perfil**.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Novas opções de calendário de atualizações para empurrar atualizações do OS para dispositivos iOS/iPadOS inscritos<!--5879689-->
Poderá a partir das seguintes opções ao agendar atualizações do sistema operativo para dispositivos iOS/iPadOS. Isto aplica-se a dispositivos que utilizaram os tipos de matrículas do Apple Business Manager ou do Apple School Manager.
- Atualização no próximo check-in
- Atualização durante o horário programado
- Atualização fora do horário programado

Para as duas últimas opções, pode criar várias janelas de tempo.

Para ver as novas opções, vá ao MEM > **Dispositivos** > **iOS** > **Atualizar as políticas para o iOS/iPadOS** > Criar o **perfil**.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoramento e solução de problemas

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Experiência melhorada de reporte intune<!-- 3791418 idready -->
O Intune agora fornece uma experiência de relatório aprimorada, incluindo novos tipos de relatórios, melhor organização de relatórios, exibições mais focadas, funcionalidade de relatório aprimorada, bem como dados mais consistentes e oportunos. A experiência de reporte passará da pré-visualização pública para a GA (disponibilidade geral). Além disso, o lançamento da GA fornecerá suporte de localização, correções de bugs, melhorias de design e dados agregados de conformidade de dispositivos em azulejos no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Os novos tipos de relatório se concentram no seguinte:
- **Operacional** -fornece registros atualizados com um foco de integridade negativo. 
- **Organizacional** – fornece um resumo mais amplo do estado geral.
- **Histórico** -fornece padrões e tendências ao longo de um período de tempo.
- **Especialista** – permite que você use dados brutos para criar seus próprios relatórios personalizados.

O primeiro conjunto de novos relatórios se concentra na conformidade do dispositivo. Para obter mais informações, consulte [estrutura de relatórios de Microsoft Intune de blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) e [relatórios do Intune](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Alterações de interface do usuário de funções do Intune recebidas<!--5801612 idready-->
A interface do usuário para o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > a **Administração de locatário** as **funções** > serão alteradas para um design mais amigável e intuitivo. Essa experiência fornece as mesmas configurações e os detalhes que você usa agora, no entanto, a nova experiência emprega um processo do tipo assistente.


<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Suporte a credenciais derivadas em dispositivos Android COBO<!--4839592-->
Você poderá usar credenciais derivadas em dispositivos Android Enterprise totalmente gerenciados. O suporte será incluído para recuperar uma credencial derivada para Entrust Datacard, intercedam e DISA purebred. Você poderá usar uma credencial derivada para autenticação de aplicativo, Wi-Fi, VPN ou assinatura S/MIME e/ou criptografia com aplicativos que dão suporte a ela.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Utilize a política Antivírus para gerir as definições para o Antivírus do Microsoft Defender e a experiência de Segurança do Windows<!--6131401 -->
A partir do nó de *segurança Endpoint,* poderá configurar as definições para **Antivírus**. Quando configurar a política para o Antivírus, definirá as definições para os seus dispositivos Windows 10 através de dois tipos de perfil:

- Microsoft Defender Antivírus: Gerir as definições para proteção de nuvens, exclusões antivírus, reparação, opções de digitalização e muito mais.
- Experiência de Segurança do Windows: Gerir a forma como os utilizadores experimentam as definições de Segurança do Windows nos seus dispositivos. Poderá configurar o que os utilizadores finais podem ver no centro de Segurança do Microsoft Defender e nas notificações que recebem. 

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Veja também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).


