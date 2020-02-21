---
title: Em desenvolvimento - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune apresenta-se em desenvolvimento
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
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514574"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Em desenvolvimento para microsoft Intune - fevereiro 2020

Para ajudar na sua prontidão e planeamento, esta página lista atualizações e funcionalidades intune UI que estão em desenvolvimento mas ainda não foram lançadas. Além das informações nesta página: 

- Se anteciparmos que terá de agir antes de uma mudança, publicaremos um post complementar no Centro de Mensagens do Office.
- Quando uma funcionalidade entra em produção, seja uma pré-visualização ou geralmente disponível, a descrição da funcionalidade passará desta página para [o que é novo](whats-new.md).
- Esta página e a nova página [do What's](whats-new.md) são atualizadas periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte o roteiro da [Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para entregas estratégicas e prazos.

> [!NOTE]
> Esta página reflete as nossas expectativas atuais sobre as capacidades intune num lançamento futuro. As datas e as características individuais podem mudar. Esta página não descreve todas as funcionalidades em desenvolvimento.

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Apresentar notificações para a aplicação Portal da Empresa no Windows<!-- 1808082  -->
Atualizaremos a aplicação Portal da Empresa em dispositivos Windows para exibir notificações de torradas aos utilizadores, mesmo quando a aplicação estiver fechada. A atualização mostrará notificações para aplicações disponíveis apenas quando o estado de instalação estiver concluído ou falhado. A aplicação Portal da Empresa não apresentará notificações para aplicações necessárias. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Mostrar mensagens de estado de instalação para a aplicação Portal da Empresa<!-- 2514416  -->
A aplicação Portal da Empresa mostrará mensagens adicionais de estado de instalação de aplicações aos utilizadores finais. As seguintes condições aplicar-se-ão às novas funcionalidades de dependência win32:
- A aplicação falhou na instalação. As dependências definidas pelo administrador não foram satisfeitas.

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Redirecione os clipes web para o Microsoft Edge em dispositivos iOS/iPadOS<!-- 5455276 -->
Os web clips, que funcionam como aplicações web fixas em dispositivos iOS/iPadOS, terão de ser atualizados. Os clips web recentemente implantados serão abertos no Microsoft Edge em vez do Navegador Gerido Intune, se necessário para abrir num navegador protegido. Tem de redirecionar os clips web pré-existentes para garantir que se abrem no Microsoft Edge em vez do Navegador Gerido.

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

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfis de configuração de dispositivos de rede com fios para dispositivos macOS<!-- 3508686  -->
Um novo perfil de configuração do dispositivo macOS estará disponível que configura redes com fios (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **macOS** para plataforma > **Rede Com fios** para tipo de perfil). Utilize esta funcionalidade para criar perfis 802.1x para gerir redes com fios e implementar estas redes com fios para os seus dispositivos macOS.

Aplica-se a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>Perfis VPN com ligações VPN IKEv2 podem usar sempre com dispositivos iOS/iPadOS <!-- 1947932 idready -->
Nos dispositivos iOS/iPadOS, pode criar um perfil VPN que utiliza uma ligação IKEv2 (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **iOS/iPadOS** para plataforma > **VPN** para o tipo de perfil). Numa futura atualização, pode configurar sempre com o IKEv2. Quando configurados, os perfis VPN IKEv2 ligam-se automaticamente e mantêm-se ligados (ou reconectarem-se rapidamente) à VPN. Mantém-se ligado mesmo quando se desloca entre redes ou dispositivos de reinício.

No iOS/iPadOS, a VPN sempre on-on está limitada aos perfis IKEv2.

Para ver as definições atuais do IKEv2 pode configurar, vá adicionar [definições VPN em dispositivos iOS/iPadOS no Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Aplica-se a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Melhoria da experiência de interface do utilizador ao criar perfis de configuração em dispositivos iOS/iPadOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Quando criar um perfil para dispositivos iOS/iPadOS ou macOS, a experiência no Endpoint Management Admin Center será atualizada. Esta alteração impacta os seguintes perfis de configuração do dispositivo **(Dispositivos** > Perfis de **Configuração** > **Criar perfil** > **iOS** ou **macOS** para a plataforma):

- Personalizado: iOS/iPadOS, macOS
- Funcionalidades do dispositivo: iOS/iPadOS, macOS
- Restrições ao dispositivo: iOS/iPadOS, macOS
- Proteção endpoint: macOS
- Extensões: macOS
- Ficheiro preferencial: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Melhoria da experiência de interface do utilizador ao criar perfis de configuração OEMConfig em dispositivos Android Enterprise<!-- 5568645 idready  -->
Quando cria ou edita um perfil OEMConfig para dispositivos Android Enterprise, a experiência no centro de administração endpoint Management é atualizada. A experiência atualizada fornecerá um resumo das definições que configurado num ápice. Esta alteração afeta o perfil de configuração do dispositivo OEMConfig (**Dispositivos** > perfis de **configuração** > **Criar perfil** > **Android Enterprise** para plataforma > **OEMConfig** para o tipo de perfil).

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
## <a name="monitoring-and-troubleshooting"></a>Monitorização e resolução de problemas

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Experiência melhorada de reporte intune<!-- 3791418 idready -->
Intune agora fornece uma experiência de reporte melhorada, incluindo novos tipos de relatórios, melhor organização de relatórios, opiniões mais focadas, melhor funcionalidade de relatório, bem como dados mais consistentes e oportunos. A experiência de reporte passará da pré-visualização pública para a GA (disponibilidade geral). Além disso, o lançamento da GA fornecerá suporte de localização, correções de bugs, melhorias de design e dados agregados de conformidade de dispositivos em azulejos no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Os novos tipos de relatórios centram-se nos seguintes exemplos:
- **Operacional** - Fornece novos registos com foco negativo para a saúde. 
- **Organizacional** - Fornece um resumo mais amplo do estado geral.
- **Histórico** - Fornece padrões e tendências ao longo de um período de tempo.
- **Especialista** - Permite-lhe utilizar dados brutos para criar os seus próprios relatórios personalizados.

O primeiro conjunto de novos relatórios centra-se na conformidade do dispositivo. Para mais informações, consulte blog [- Microsoft Intune reporting framework](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) and [Intune reports](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune Roles alterações na interface do utilizador<!--5801612 idready-->
A interface de utilizador do [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **a administração do Inquilino** > **Roles** será alterada para um design mais fácil de usar e intuitivo. Esta experiência fornece as mesmas definições e detalhes que utiliza agora, no entanto a nova experiência emprega um processo semelhante ao de um assistente.


<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Suporte de credenciais derivadas em dispositivos Android COBO<!--4839592-->
Poderá utilizar credenciais derivadas em dispositivos geridos pela Android Enterprise. O apoio será incluído para recuperar uma credencial derivada para Entrust Datacard, Intercede e DISA Purebred. Poderá utilizar uma credencial derivada para autenticação de apps, Wi-Fi, VPN ou s/MIME assinando e/ou encriptação com aplicações que a suportam.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Utilize a política Antivírus para gerir as definições para o Antivírus do Microsoft Defender e a experiência de Segurança do Windows<!--6131401 -->
A partir do nó de *segurança Endpoint,* poderá configurar as definições para **Antivírus**. Quando configurar a política para o Antivírus, definirá as definições para os seus dispositivos Windows 10 através de dois tipos de perfil:

- Microsoft Defender Antivírus: Gerir as definições para proteção de nuvens, exclusões antivírus, reparação, opções de digitalização e muito mais.
- Experiência de Segurança do Windows: Gerir a forma como os utilizadores experimentam as definições de Segurança do Windows nos seus dispositivos. Poderá configurar o que os utilizadores finais podem ver no centro de Segurança do Microsoft Defender e nas notificações que recebem. 

<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Veja também
Para mais detalhes sobre os recentes desenvolvimentos, consulte [o que há de novo no Microsoft Intune](whats-new.md).


