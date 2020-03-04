---
title: Em desenvolvimento - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune apresenta-se em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260236"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>Em desenvolvimento para microsoft Intune - março 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Redirecione os clipes web para o Microsoft Edge em dispositivos iOS/iPadOS<!-- 5455276 -->
Os web clips, que funcionam como aplicações web fixas em dispositivos iOS/iPadOS, terão de ser atualizados. Os clips web recentemente implantados serão abertos no Microsoft Edge em vez do Navegador Gerido Intune, se necessário para abrir num navegador protegido. Tem de redirecionar os clips web pré-existentes para garantir que se abrem no Microsoft Edge em vez do Navegador Gerido.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>atualizações do Portal macOS e iOS da empresa<!-- 5779439, 5780234  -->
O painel de perfil do macOS e do portal da empresa iOS será atualizado para incluir o botão de sinalização. Além disso, esta atualização incluirá melhorias de UI no painel de perfil no Portal da Empresa macOS. Para mais informações sobre o Portal da Empresa, consulte [como configurar a aplicação Microsoft Intune Company Portal](~/apps/company-portal-app.md).

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>Atualizações para branding e painel de personalização<!-- 5236032 -->
Estamos a atualizar o painel Intune que atualmente se chama "Branding e personalização" com melhorias, incluindo:

- Renomear o painel para **personalização.**
- Melhorar a organização e o design das configurações.
- Melhorar o texto de definições e as pontas de ferramentas.

Para encontrar estas definições em Intune, navegue para o [centro de administração](https://go.microsoft.com/fwlink/?linkid=2109431) do Microsoft Endpoint Manager e, selecione a **administração do Tenant** > **Personalização**. Para obter informações sobre a personalização existente, consulte [como configurar a aplicação Microsoft Intune Company Portal](~/apps/company-portal-app.md).

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>Configure a extensão da aplicação iOS Microsoft Azure AD SSO<!-- 567534  -->
A equipa da Microsoft Azure AD está a desenvolver uma extensão de aplicação de inscrição única (SSO) para permitir aos utilizadores do iOS e iPadOS 13.0+ acederem perfeitamente às aplicações e websites da Microsoft com um único sinal. Quando a extensão da extensão da aplicação AAD SSO for lançada, poderá configurar a extensão SSO com as **funcionalidades** do Dispositivo > perfil de extensão de **aplicação de início único** na consola de administração com cliques mínimos. 

Para obter mais informações sobre as extensões da aplicação iOS SSO ou como configurar as funcionalidades do dispositivo, consulte a extensão da [aplicação de início de sessão individual](~/configuration/device-features-configure.md#single-sign-on-app-extension).

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>Portal da empresa para o iOS para apoiar o modo paisagístico<!--6048329  -->
Os utilizadores poderão inscrever os seus dispositivos, encontrar aplicações e obter suporte de TI utilizando a orientação do ecrã à sua escolha. A aplicação detetará e ajustará automaticamente os ecrãs para encaixar no retrato ou no modo de paisagem, a menos que os utilizadores bloqueiem o ecrã no modo retrato. 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Configure se a inscrição estiver disponível no Portal da Empresa para Android e iOS<!-- 4260128 idready idstaged -->
Estará disponível uma nova definição que lhe permite configurar se a inscrição de dispositivos no Portal da Empresa nos dispositivos Android e iOS está disponível com solicitações, disponíveis sem avisos ou indisponíveis para os utilizadores. Para encontrar estas definições em Intune, navegue para o centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e, selecione a **administração do Tenant** > **personalização** > **Editar** > Dispositivo **de inscrição**. Para obter mais informações sobre a personalização do Portal da Empresa existente, consulte [como configurar a aplicação Microsoft Intune Company Portal](~/apps/company-portal-app.md).

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Melhor experiência de inscrição no Portal da Empresa para Android<!-- 6103997  -->
Estamos a atualizar o layout de vários ecrãs de acesso no aplicativo Portal da Empresa para Android para tornar a experiência mais moderna, simples e limpa para os utilizadores.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfis de configuração de dispositivos de rede com fios para dispositivos macOS<!-- 3508686  -->
Um novo perfil de configuração do dispositivo macOS estará disponível que configura redes com fios (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **macOS** para plataforma > **Rede Com fios** para tipo de perfil). Utilize esta funcionalidade para criar perfis 802.1x para gerir redes com fios e implementar estas redes com fios para os seus dispositivos macOS.

Aplica-se a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>Perfis VPN com ligações VPN IKEv2 podem usar sempre com dispositivos iOS/iPadOS <!-- 1947932  -->
Nos dispositivos iOS/iPadOS, pode criar um perfil VPN que utiliza uma ligação IKEv2 (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **iOS/iPadOS** para plataforma > **VPN** para o tipo de perfil). Numa futura atualização, pode configurar sempre com o IKEv2. Quando configurados, os perfis VPN IKEv2 ligam-se automaticamente e mantêm-se ligados (ou reconectarem-se rapidamente) à VPN. Mantém-se ligado mesmo quando se desloca entre redes ou dispositivos de reinício.

No iOS/iPadOS, a VPN sempre on-on está limitada aos perfis IKEv2.

Para ver as definições atuais do IKEv2 pode configurar, vá adicionar [definições VPN em dispositivos iOS/iPadOS no Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Aplica-se a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>Melhoria da experiência de interface do utilizador ao criar perfis de configuração em dispositivos iOS/iPadOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
Quando criar um perfil para dispositivos iOS/iPadOS ou macOS, a experiência no Endpoint Management Admin Center será atualizada. Esta alteração impacta os seguintes perfis de configuração do dispositivo **(Dispositivos** > Perfis de **Configuração** > **Criar perfil** > **iOS** ou **macOS** para a plataforma):

- Personalizado: iOS/iPadOS, macOS
- Funcionalidades do dispositivo: iOS/iPadOS, macOS
- Restrições ao dispositivo: iOS/iPadOS, macOS
- Proteção endpoint: macOS
- Extensões: macOS
- Ficheiro preferencial: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Melhoria da experiência de interface do utilizador ao criar perfis de configuração OEMConfig em dispositivos Android Enterprise<!-- 5568645   -->
Quando cria ou edita um perfil OEMConfig para dispositivos Android Enterprise, a experiência no centro de administração endpoint Management é atualizada. A experiência atualizada fornecerá um resumo das definições que configurado num ápice. Esta alteração afeta o perfil de configuração do dispositivo OEMConfig (**Dispositivos** > perfis de **configuração** > **Criar perfil** > **Android Enterprise** para plataforma > **OEMConfig** para o tipo de perfil).

Esta funcionalidade aplica-se a:
- Android Enterprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>Definição de modificação de definições de regulação da aplicação da empresa será removida dos perfis de restrição do dispositivo iOS/iPadOS<!-- 6225131  -->
Nos dispositivos iOS/iPadOS, cria-se um perfil de restrições de**dispositivos** ( Perfis de configuração de **dispositivos** >  > **Criar perfil** > **iOS/iPadOS** para **restrições** de plataforma > dispositivo para tipo de perfil). A definição de modificação de definições de regulação da **aplicação Enterprise** será removida pela Apple e será removida do Intune. Se utilizar atualmente esta definição num perfil, não tem impacto e permanecerá no seu perfil até criar um novo perfil. Esta definição também será removida de qualquer relatório em Intune.

Aplica-se a:
- iOS/iPadOS

Para ver as definições que pode restringir, vá às definições do [dispositivo iOS e iPadOS para permitir ou restringir as funcionalidades](../configuration/device-restrictions-ios.md).

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>As definições e valores do perfil de configuração do dispositivo serão atualizados para plataformas Windows<!-- 4091122 -->
Quando cria perfis de configuração de dispositivos para plataformas Windows **(Dispositivos** > Perfis de **Configuração** > **Criar perfil** > qualquer opção **do Windows** para plataforma), algumas definições e os seus valores são diferentes do CSP, e podem ser confusos. Os nomes de definição e os seus valores serão atualizados para serem mais claros.

Aplica-se a:

- Windows 10 e perfis posteriores de configuração do dispositivo
- Windows Holographic para perfis de configuração de dispositivos empresariais
- Perfis de configuração do dispositivo Windows 8.1
- Perfis de configuração do dispositivo Windows Phone 8.1

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Melhoria da experiência de interface de utilizador ao criar perfis de restrições de dispositivos em dispositivos Android e Android Enterprise<!-- 5841361 -->
Quando criar um perfil para dispositivos Android ou Android Enterprise, a experiência no centro de administração endpoint Management será atualizada. Esta alteração impacta os seguintes perfis de configuração do dispositivo **(Dispositivos** > Perfis de **Configuração** > **Criar perfil** > **administrador de dispositivos Android** ou Android **Enterprise** para plataforma):

- Restrições ao dispositivo: Administrador de dispositivos Android
- Restrições ao dispositivo: Proprietário de dispositivos Android Enterprise
- Restrições ao dispositivo: Perfil de trabalho Android Enterprise

Para obter mais informações sobre as restrições do dispositivo, pode configurar, consulte o [administrador do dispositivo Android](../configuration/device-restrictions-android.md) e o Android [Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Eliminar pacotes e conjuntos de pacotes em perfis de configuração de dispositivos OEMConfig em dispositivos Android Enterprise<!-- 5550355  -->
Nos dispositivos Android Enterprise, cria e atualiza os perfis da OEMConfig. Os utilizadores poderão eliminar pacotes e conjuntos de pacotes utilizando o designer de **configuração** em Intune.

Para obter mais informações sobre os perfis da OEMConfig, consulte [use e gerencie dispositivos Android Enterprise com OEMConfig no Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Esta funcionalidade aplica-se a:
- Android Enterprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>Suporte para WPA e WPA2 nos perfis wi-fi da empresa iOS<!--6215273   -->
Estamos adicionando o campo *do tipo de Segurança* ao perfil [Wi-Fi da Empresa para iOS](../configuration/wi-fi-settings-ios.md) (**Dispositivos** > perfis de **configuração** > **Criar perfil** e selecionar **iOS/iPadOS** para *plataforma* e, em seguida, **Wi-Fi** para *Perfil).* Isto é semelhante às opções disponíveis para um perfil Wi-Fi Básico para iOS. Com esta alteração poderá criar novos perfis que especificam um tipo de segurança de **WPA-Enterprise** ou **WPA/WPA2-Enterprise,** e depois especificar uma seleção para o *tipo EAP*.

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>Nova experiência do utilizador para perfis de certificado, e-mail, VPN e Wi-Fi<!-- 5615208   -->
Estávamos a atualizar a [experiência](../configuration/device-profile-create.md) do utilizador no Endpoint Management Admin Center (**Dispositivos** > Perfis de **Configuração** > **Criar perfil**) para criar e modificar os seguintes tipos de perfis. A nova experiência apresentará as mesmas definições de antes, mas utiliza uma experiência semelhante a um assistente que não requer tanto scrolling horizontal. Não terá de modificar as configurações existentes com a nova experiência.
- Credencial derivada
- E-mail
- Certificado PKCS
- Certificado PKCS importado
- Certificado SCEP
- Certificado fidedigno
- VPN
- Wi-Fi

**(Dispositivos** > perfis de **configuração** > **Criar perfil,** e depois para *o tipo de perfil* selecione qualquer um dos perfis anteriores.)

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>Configure a aplicação ATP microsoft defender para macOS  <!-- 5520115  -->
Em breve poderá configurar as [definições](../protect/endpoint-protection-macos.md) da aplicação ATP do Microsoft Defender para dispositivos que executam o macOS como parte de um perfil de configuração de dispositivos de proteção endpoint **(Dispositivos** > perfis de **configuração** > **Criar perfil,** selecionar **o macOS** para a *Plataforma*e, em seguida, **proteção Endpoint** para o *tipo de Perfil).* Haverá oito configurações para a configuração do dispositivo macOS. 

O Defender ATP é suportado no macOS 10.13 (High Sierra) e posteriormente, e a aplicação [ATP Microsoft Defender](../apps/apps-advanced-threat-protection-macos.md) deve ser implementada no dispositivo *após* a aplicação desta definição. As definições devem ser enviadas para o dispositivo antes da aplicação ser implementada. As versões beta do macOS não serão suportadas.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>Nova definição de FileVault para a política de configuração do dispositivo de proteção de pontofinal macOS<!-- 5459801   -->
Estamos adicionando uma nova definição à categoria FileVault dentro do modelo de proteção de [ponto final macOS:](../protect/endpoint-protection-macos.md) Ocultar a chave de recuperação. **(Dispositivos** > perfis de **configuração** > **Criar perfil,** selecione **o macOS** para a *Plataforma* e, em seguida, a **proteção endpoint** para o *tipo de perfil).* Esta definição esconde a chave pessoal do utilizador final durante a encriptação FileVault 2. Um utilizador do dispositivo pode visualizar a sua chave de recuperação pessoal a qualquer momento a partir da aplicação portal da empresa iOS ou do portal da empresa para o dispositivo macOS encriptado. Para ver a chave de recuperação pessoal, podem ir aos detalhes do dispositivo e clicar na *chave de recuperação do get*.

Esta definição não estará disponível na política previamente criada. Terá de recriar as políticas do FileVault para configurar esta definição para a utilizar. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>Atualização da UI ao configurar a política de conformidade <!-- 3961639  -->
Estamos a atualizar o UI para configurar políticas de conformidade no gestor do Microsoft Endpoint (**Dispositivos** > **políticas** de conformidade > **Políticas** > **Criar Políticas).** Verá uma nova experiência de utilizador que fornece as mesmas definições e detalhes que utilizou anteriormente. A nova experiência seguirá um processo semelhante a um assistente para criar uma política de conformidade e incluirá a página onde pode adicionar *Atribuições* para a apólice e, em seguida, uma página *sumária* onde pode rever a sua configuração antes de criar a apólice. 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Configure o agente de otimização de entrega ao descarregar conteúdo da aplicação Win32<!-- 5410945  -->
Poderá configurar o agente de Otimização de Entregas para descarregar conteúdo da aplicação Win32, tanto em segundo plano como em modo de primeiro plano, com base na atribuição. Para as aplicações Win32 existentes, os conteúdos continuarão a descarregar em modo de fundo. No centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Dispositivos** > perfis de **configuração** > **Criar o perfil**. Selecione **o Windows 10 e mais tarde** como **Plataforma**. No **tipo de perfil,** selecione **Otimização de Entrega**. Para mais informações sobre a Otimização de Entregas, consulte a [gestão da aplicação Win32 - Otimização de Entrega](~/apps/apps-win32-app-management.md#delivery-optimization).


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Alterar o utilizador primário para dispositivos Windows <!-- 3794742 -->
Poderá alterar o Utilizador Principal para dispositivos híbridos windows e Azure AD. Para tal, vá a **Intune** > **Devices** > **Todos os dispositivos** > escolha um dispositivo > **Propriedades** > **Utilizador Primário**. 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Novo relatório Android na página de visão geral dos Dispositivos Android<!-- 5435435 -->
Vamos adicionar um relatório à consola de administração do Microsoft Endpoint Manager na página de visão geral dos Dispositivos Android que mostra quantos dispositivos Android foram matriculados em cada solução de gestão de dispositivos. Este gráfico (como o mesmo gráfico já na consola Azure) mostra o perfil de trabalho, totalmente gerido, dedicado e administrador de dispositivos inscrito seleções. Para ver o relatório, escolha **Dispositivos** > **Visão Geral**do ** > Android** .

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>Suporte de scripts PowerShell para dispositivos BYOD<!-- 1862833  -->
Os scripts PowerShell suportarão dispositivos registados em Intune. Para obter mais informações sobre o PowerShell, consulte [scripts PowerShell em dispositivos Windows 10 em Intune](~/apps/intune-management-extension.md). Esta funcionalidade não suporta dispositivos que executam a edição home do Windows 10.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>Propriedades adicionais de inventário de dispositivos de armazém de dados<!-- 6125732  -->
Propriedades adicionais de inventário de dispositivos estarão disponíveis usando o Intune Data Warehouse. As seguintes propriedades serão expostas através da recolha de [dispositivos:](~/developer/intune-data-warehouse-collections.md#devices)
- Capacidade de armazenamento 
- Capacidade de memória
- Versão do Office 365
- Modelo de dispositivo

Para mais informações sobre o Data Warehouse, consulte a [Microsoft Intune Data Warehouse API](~/developer/reports-nav-intune-data-warehouse.md).

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Orientar os utilizadores da gestão de administrador de dispositivos Android para a gestão de perfis de trabalho<!--5857738-->
Estamos a lançar uma nova definição de conformidade para a plataforma de administrador de dispositivos Android. Esta definição permite-lhe tornar um dispositivo incompatível se for gerido com o administrador do dispositivo.

Nestes dispositivos não conformes, na página de **definições** do dispositivo Update os utilizadores verão a **mensagem de configuração de move para nova gestão de dispositivos.** Se tocarem no botão **Resolver,** serão guiados através:

1. Não se matriculando na gestão do administrador de dispositivos
2. Matriculamento na gestão de perfil de trabalho
3. Resolução de questões de conformidade 
 
A Google está a diminuir o suporte do administrador de dispositivos em novas versões Android, num esforço para se mudar para uma gestão moderna, mais rica e segura de dispositivos com o Android Enterprise.  A Intune só pode fornecer suporte total para dispositivos Android geridos por administrador de dispositivos que executam o Android 10 e, posteriormente, através do Q2 CY2020. Dispositivos geridos por administrador de dispositivos (exceto Samsung) que estão a executar o Android 10 ou mais tarde depois desta época não serão capazes de ser totalmente geridos. Em particular, os dispositivos com impacto não receberão novos requisitos de senha. Para mais informações, consulte este [Aviso](#decreasing-support-for-android-device-administrator).

### <a name="retire-noncompliant-devices---1827291---"></a>Dispositivos não conformes de aposentadoria<!-- 1827291 -->
Estamos adicionando uma nova ação de conformidade opcional para reformar um dispositivo não conforme (**Dispositivos** > **Políticas** de Conformidade > **Políticas** > **Criar políticas** e, em seguida, visualizar *ações* disponíveis sobre as ações para a página *de incumprimento).*  A retirada de um dispositivo não conforme remove todos os dados da empresa do mesmo, e também remove o dispositivo de ser gerido pela Intune. Esta ação funciona quando o valor configurado em dias é atingido. O valor mínimo é de 30 dias.  A aprovação explícita da administração de TI será necessária para retirar os dispositivos utilizando a secção *de dispositivos não conformes* com aposentadoria, onde os administradores podem reformar todos os dispositivos elegíveis.

### <a name="new-information-in-device-details---5604099---"></a>Novas informações sobre detalhes do dispositivo<!-- 5604099 -->
As seguintes informações estarão na página **'Overview'** para dispositivos:
- Capacidade de armazenamento (quantidade de armazenamento físico no dispositivo)
- Capacidade de memória (quantidade de memória física no dispositivo)

### <a name="script-support-for-macos-devices---4280361----"></a>Suporte de script para dispositivos macOS<!-- 4280361  -->
Poderá adicionar e implementar scripts para dispositivos macOS. Este suporte alarga a sua capacidade de configurar dispositivos macOS para além do que é possível utilizando capacidades nativas de MDM em dispositivos macOS. 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>Ajuda e suporte atualização de fluxo de trabalho para apoiar serviços adicionais<!-- 5654170 -->
Estamos a atualizar a página de Ajuda e Suporte no centro de administração do Microsoft Endpoint Manager para que possa escolher o tipo de gestão que utiliza, para fornecer melhor suporte específico (**Resolução de problemas + suporte** >  **Ajuda e suporte).** Com esta alteração poderá selecionar entre os seguintes tipos de gestão:
- Gestor de Configuração (inclui Desktop Analytics)
- Intune
- Cogestão

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>Segurança

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Suporte de credenciais derivadas em dispositivos Android COBO<!--4839592-->
Poderá utilizar credenciais derivadas em dispositivos geridos pela Android Enterprise. O apoio será incluído para recuperar uma credencial derivada para Entrust Datacard, Intercede e DISA Purebred. Poderá utilizar uma credencial derivada para autenticação de apps, Wi-Fi, VPN ou s/MIME assinando e/ou encriptação com aplicações que a suportam.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Utilize a política Antivírus para gerir as definições para o Antivírus do Microsoft Defender e a experiência de Segurança do Windows<!--6131401 -->
A partir do nó de *segurança Endpoint,* poderá configurar as definições para **Antivírus**. Quando configurar a política para o Antivírus, definirá as definições para os seus dispositivos Windows 10 através de dois tipos de perfil:

- Microsoft Defender Antivírus: Gerir as definições para proteção de nuvens, exclusões antivírus, reparação, opções de digitalização e muito mais.
- Experiência de Segurança do Windows: Gerir a forma como os utilizadores experimentam as definições de Segurança do Windows nos seus dispositivos. Poderá configurar o que os utilizadores finais podem ver no centro de Segurança do Microsoft Defender e nas notificações que recebem.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>Chave de recuperação encriptada pessoal do utilizador<!-- 6273943 -->
Uma nova funcionalidade Intune estará disponível que permite aos utilizadores recuperarem a sua chave de recuperação de **FileVault** encriptada pessoal para dispositivos Mac através da aplicação Portal da Empresa Android ou através da aplicação Android Intune. Haverá um link tanto na aplicação Portal da Empresa como na aplicação Intune que abrirá um navegador Chrome para o Portal da Empresa Web onde o utilizador pode ver a chave de recuperação **do FileVault** necessária para aceder aos seus dispositivos Mac. Para obter mais informações sobre encriptação, consulte [Utilize a encriptação do dispositivo com Intune](~/protect/encrypt-devices.md).

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>Definições de preferências de privacidade para dispositivos macOS<!-- 2934232 --> 
Com o lançamento do macOS Catalina 10.15, a Apple adicionou novos melhoramentos de segurança e privacidade. Por defeito, as aplicações e processos não conseguem aceder a dados específicos sem o consentimento do utilizador. Se os utilizadores não fornecerem o consentimento, as aplicações e processos podem não funcionar. A Intune está a adicionar suporte para configurações que permitem aos administradores de TI permitir ou proibir o consentimento de acesso de dados em nome dos utilizadores finais em dispositivos que executam o macOS 10.14 ou posteriormente. Estas definições garantirão que as aplicações e processos continuem a funcionar corretamente e reduzem o número de indicações que os utilizadores finais experimentam. 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Texto e etiquetas ui atualizados para definições de perfil de proteção de ponto final do Windows 10<!-- 5983747 -->
Estamos a atualizar o texto para várias definições que configura como perfis de configuração do dispositivo Windows 10 para facilitar a compreensão das definições pretendidas e resultados. 

As definições que estamos a atualizar incluem perfis de configuração do dispositivo Windows 10 para: 
- [Restrições](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) ao dispositivo > Microsoft Defender Antivírus  
- [Proteção endpoint](../protect/endpoint-protection-windows-10.md) > Microsoft Defender Antivírus

As definições que são suportadas com Intune não estão a mudar. Esta é apenas uma atualização para o texto UI no Microsoft Endpoint Management Admin Center. 


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Veja também
Para mais detalhes sobre os recentes desenvolvimentos, consulte [o que há de novo no Microsoft Intune](whats-new.md).



