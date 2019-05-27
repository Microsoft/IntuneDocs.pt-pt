---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 044ced57d9dd2e3e4b86548540090de35b88a6b0
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197084"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Também pode encontrar [alterações futuras](in-development.md), [avisos importantes](#notices)e informações sobre [versões anteriores](whats-new-archive.md). 

> [!Note]
> É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.

**RSS feed**: Seja notificado quando esta página é atualizada ao copiar e colar o URL seguinte no seu leitor de feeds: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-may-20-2019"></a>Semana de 20 de Maio de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="windows-company-portal-app----3316993---"></a>Aplicação do Portal da Empresa do Windows <!-- 3316993 -->
A aplicação Portal da empresa de Windows terá agora uma nova página rotulada **dispositivos**. O **dispositivos** página irá mostrar os utilizadores finais todos os respetivos dispositivos inscritos. Os utilizadores irão ver esta alteração no Portal da empresa quando utilizam a versão 10.3.4291.0 e mais tarde. Para obter informações sobre a configuração do Portal da empresa, consulte [como configurar a aplicação Portal da empresa do Microsoft Intune](company-portal-app.md).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot OrderID atributo nome do dispositivo foi alterado para a etiqueta de grupo <!-- 4659453 -->

Para torná-lo mais intuitivo, o **OrderID** nome de atributo em dispositivos Autopilot foi alterada para **etiqueta de grupo**. Quando utilizar CSVs para carregar as informações de dispositivo do Autopilot, tem de utilizar a etiqueta de grupo como no cabeçalho da coluna, não OrderID. Caso contrário, o carregamento falhará. OrderID será novamente introduzida para acomodar os clientes herdados ou scripts. No entanto, a etiqueta de grupo será o padrão mais adiante.

## <a name="week-of-may-13-2019"></a>Semana de 13 de Maio de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>As políticas do Intune atualizar o método de autenticação e a instalação da aplicação Portal da empresa  <!-- 1927359 idready wnready-->
Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, o Intune suportará já não é o Portal da empresa quando é instalado manualmente pelos usuários finais da loja de aplicações. Esta alteração é relevante apenas quando se autenticar com o Assistente de configuração da Apple durante a inscrição. Esta alteração afeta também apenas dispositivos iOS inscritos através de:  
* Do Apple configurator

* Gerente de negócios da Apple

* Gestor Escolar da Apple

* Programa de inscrição de dispositivos Apple (DEP)

Se os utilizadores instalarem a aplicação Portal da empresa a partir da App store e, em seguida, tentar inscrever estes dispositivos através do mesmo, receberá um erro. Estes dispositivos serão esperados para utilizar apenas o Portal da empresa quando foi enviado, automaticamente, pelo Intune durante a inscrição. Perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Se pretender que os utilizadores de dispositivos do DEP para o portal da empresa, terá de especificar as suas preferências num perfil de inscrição. 

Além disso, o **identificar o seu dispositivo** ecrã no Portal da empresa iOS está a ser removido. Por conseguinte, os administradores que pretendem ativar o acesso condicional ou implementar aplicações da empresa tem de atualizar o perfil de inscrição de DEP. Este requisito aplica-se apenas se a inscrição de DEP é autenticada com o Assistente de configuração. Nesse caso, deve enviar por push o Portal da empresa no dispositivo. Para tal, escolha **Intune** > **inscrição de dispositivos** > **inscrição da Apple** > **programa de inscrição tokens** > Escolha um token > **perfis** > Escolha um perfil > **propriedades** > definir **instalar o Portal da empresa** para **Sim**.

Para instalar o Portal da empresa em dispositivos DEP já inscrito, terá de ir para o Intune > aplicações de cliente e enviá-los como uma aplicação gerida com as políticas de configuração de aplicações. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurar como os utilizadores finais atualizar uma aplicação de (LOB) de linha de negócio com uma política de proteção de aplicações <!-- 3568384 -->
Agora, pode configurar onde os utilizadores finais podem obter uma versão atualizada de uma aplicação de linha de negócio (LOB). Os utilizadores finais irão ver esta funcionalidade no **versão mínima da aplicação** caixa de diálogo de início condicional, que irá solicitar-os utilizadores finais para atualizar para uma versão mínima da aplicação LOB. Tem de fornecer que esses detalhes de atualização como parte da sua política de proteção de aplicações LOB (aplicação). Esta funcionalidade está disponível em iOS e Android. No iOS, esta funcionalidade requer que a aplicação para ser integrado (ou encapsuladas com a ferramenta de encapsulamento de aplicações) com o SDK do Intune para iOS v. 10.0.7 ou superior. No Android, esta funcionalidade requer que o Portal da empresa mais recente. Para configurar como um utilizador final atualiza uma aplicação LOB, a aplicação tem uma política de configuração de aplicação gerida enviada para o mesmo com a chave, `com.microsoft.intune.myappstore`. O valor enviado irá definir o arquivo do utilizador final irá transferir a aplicação a partir. Se a aplicação é implementada através do Portal da empresa, o valor tem de ser `CompanyPortal`. Para qualquer outro arquivo, tem de introduzir um URL completo.

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Scripts de PowerShell de extensão de gestão do Intune  <!-- 3734186 idready -->
Pode configurar os scripts do PowerShell para executar com privilégios de administrador do utilizador no dispositivo. Para obter mais informações, consulte [scripts do PowerShell de utilização em dispositivos Windows 10 no Intune](intune-management-extension.md) e [gestão de aplicações de Win32](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Gestão de aplicações do Android Enterprise <!-- 4459905 -->
Para tornar mais fácil para os administradores de TI configurar e utilizar a gestão de Android Enterprise, Intune adiciona automaticamente os quatro comuns Android Enterprise relacionadas com aplicações para a consola de administração do Intune. As aplicações do Android Enterprise quatro são os seguintes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)**  - utilizado para cenários do Android Enterprise totalmente gerido.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**  -ajuda a que iniciar sessão para as suas contas se usar a verificação de dois fatores.
- **[Portal da empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)**  - utilizado para as políticas de proteção de aplicações (aplicação) e cenários de perfil de trabalho do Android Enterprise.
- [Gerido home page de tela](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - utilizado para cenários de dedicado/quiosque do Android Enterprise.

Anteriormente, os administradores de TI precisaria manualmente localize e aprove destas aplicações na [loja Google Play gerido](https://play.google.com/store/apps) como parte da configuração. Esta alteração remove esses passos anteriormente manuais para torná-lo mais fácil e rápida para os clientes utilizar a gestão do Android Enterprise.

Os administradores vão ver estas quatro aplicações automaticamente adicionadas à sua lista de aplicações do Intune, no momento que eles ligam pela primeira vez o inquilino do Intune para o Google Play gerido. Para obter mais informações, consulte [ligar a sua conta do Intune à sua conta do Google Play gerido](connect-intune-android-enterprise.md). Para inquilinos que já ligou respetivo inquilino ou que já usam o Android Enterprise, não há nada os administradores precisam de fazer. Essas quatro aplicações aparecerá automaticamente dentro de 7 dias após a conclusão da implementação do serviço de Maio de 2019 horizontalmente.

### <a name="device-configuration"></a>Configuração do dispositivo

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Tarefas de segurança do Intune para Defender ATP (em pré-visualização pública)     <!-- 3208597 -->
Em pré-visualização pública, pode utilizar o Intune para gerir as tarefas de segurança para a Microsoft Defender avançadas de proteção contra ameaças (ATP). Esta integração com o ATP e adiciona uma abordagem com base no risco para detetar, priorizar e remediar vulnerabilidades de ponto final e configurações incorretas, reduzindo o tempo entre a deteção de atenuação.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Verifique a existência de um chipset TPM numa política de conformidade de dispositivos Windows 10 <!-- 3617671   idstaged-->
Muitos Windows 10 e dispositivos posteriores têm chipsets Trusted Platform Module (TPM). Esta atualização inclui uma nova definição de conformidade que verifica a versão de chip do TPM no dispositivo. 

[Windows 10 e posteriores definições de política de conformidade](compliance-policy-create-windows.md#device-security) descreve esta definição.

Aplica-se a: Windows 10 e posterior

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Impedir que os utilizadores finais modificar seus HotSpot pessoal e desativar o registo no iOS, dispositivos de servidor de Siri <!-- 4097904   --> 
Criar um perfil de restrições de dispositivo no dispositivo iOS (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **iOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização inclui novas definições que pode configurar:

- **Aplicações incorporadas**: Registo do lado do servidor para os comandos da Siri
- **Sem fios**: Modificação de utilizador de Hotspot pessoal (apenas supervisionado)

Para ver estas definições, aceda à [definições de aplicação incorporada para iOS](device-restrictions-ios.md#built-in-apps) e [sem fios definições para dispositivos iOS](device-restrictions-ios.md#wireless).

Aplica-se a: iOS 12.2 e mais recentes

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nova sala de aula aplicação restrição de dispositivos para dispositivos macOS <!-- 4097905   --> 
Pode criar perfis de configuração para dispositivos macOS de dispositivos (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **macOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização inclui novas definições de aplicação de sala de aula, a opção para bloquear as capturas de ecrã e a opção para desativar o biblioteca de fotografias do iCloud.

Para ver as definições atuais, aceda à [definições de dispositivos macOS para permitir ou restringir funcionalidades com o Intune](device-restrictions-macos.md).

Aplica-se a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>O palavra-passe para aceder à loja de aplicações, a definição do iOS foi mudado<!-- 4557891  -->
O **palavra-passe para aceder à loja de aplicações** definição foi mudada para **exigir iTunes Store palavra-passe para todas as compras** (**configuração do dispositivo**  >  **Perfis** > **criar perfil** > **iOS** para a plataforma > **restrições de dispositivos** para tipo de perfil > **loja de aplicações, Doc, visualização e jogos**).

Para ver as definições disponíveis, aceda à [Store de aplicação, visualizar o documento, as definições do iOS de jogos](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Linha de base de proteção do Microsoft Defender avançada contra ameaças (pré-visualização)  <!--  3754134 -->
Adicionámos uma linha de base de segurança pré-visualização para [a proteção de ameaças avançada do Microsoft Defender](security-baseline-settings-defender-atp.md) definições.  

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Página de estado de inscrição do Windows (ESP) agora está disponível em geral <!-- 3605348 -->
A página de estado de inscrição está agora do modo de pré-visualização. Para obter mais informações, consulte [configurar uma página de estado de inscrição](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Atualização de interface de utilizador do Intune - criação de perfil de inscrição de Autopilot  <!-- 4593669 -->
A interface de utilizador para criar um perfil de inscrição de Autopilot foi atualizada para alinhar com estilos de interface de utilizador do Azure. Para obter mais informações, consulte [criar um perfil de inscrição do Autopilot](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Mais adiante, cenários adicionais do Intune serão atualizados para esse novo estilo de interface do Usuário.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Ativar a reposição do Autopilot para todos os dispositivos Windows <!-- 4225665 -->
Reposição de autopilot agora funciona para todos os dispositivos Windows, mesmo aqueles não configurado para utilizar a página de estado de inscrição. Se uma página de estado de inscrição não foi configurada para o dispositivo durante a inscrição de dispositivos inicial, o dispositivo será vá diretamente para a área de trabalho após o início de sessão. Poderá demorar até oito horas a sincronizar e aparecem em conformidade no Intune. Para obter mais informações, consulte [repor os dispositivos com obter reposição remota do Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Formato exato do IMEI não é necessário quando pesquisar todos os dispositivos <!--30407680 -->
Não precisa incluir espaços em números IMEI, quando pesquisa **todos os dispositivos**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>A eliminar um dispositivo no portal da Apple será refletida no portal do Intune <!--2489996 -->
Se um dispositivo é eliminado do programa de inscrição de dispositivos da Apple ou a portais de gerente de negócios da Apple, o dispositivo será eliminado automaticamente do Intune durante a sincronização seguinte.


### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>O relatório de encriptação está fora do pré-visualização pública   <!-- 4587546      -->
O [relatório para a encriptação BitLocker e o dispositivo](encryption-monitor.md) está agora disponível em geral e já não faz parte da pré-visualização pública. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Assinatura do Outlook e definições biométricas para dispositivos iOS e Android <!-- 4050557 -->
Agora pode especificar se a assinatura de predefinição está ativada no Outlook para dispositivos iOS e Android. Além disso, pode optar por permitir que os utilizadores alterar a definição biométrica no Outlook para iOS.

## <a name="week-of-may-6-2019"></a>Semana de 6 de Maio de 2019 

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Suporte de Access Control (NAC) para acesso de F5 para dispositivos iOS de rede <!-- 4500808 -->

F5 lançou uma atualização para BIG-IP 13, que permite a funcionalidade NAC F5 acesso em dispositivos iOS no Intune. Para utilizar esta funcionalidade:

- Atualizar o BIG-IP para 13.1.1.5 atualizar. 14 de BIG-IP não é suportada.
- Integre o BIG-IP com o Intune para NAC. Os passos em [descrição geral: Configuração de APM para uma postura de dispositivo verifica com sistemas de gestão do ponto de extremidade](https://support.f5.com/kb/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89).
- Verifique os **ativar o controlo de acesso de rede (NAC)** definição no perfil da VPN no Intune.

Para ver a definição disponível, aceda a [definições de VPN configurar em dispositivos iOS](vpn-settings-ios.md).

Aplica-se a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Conector do certificado PFX atualizado para o Microsoft Intune <!-- doc-vso 1521237  -->  
Lançámos uma atualização para o [PFX Certificate Connector para o Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) que ignora o intervalo de consulta provenientes de 5 minutos para 30 segundos.

## <a name="week-of-april-22-2019"></a>Semana de 22 de Abril de 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Utilize o Gestor de conformidade para criar avaliações para o Microsoft Intune<!-- 4404750 -->

[Gestor de conformidade](https://servicetrust.microsoft.com/ComplianceManager) (abre o outro site da Microsoft) é uma ferramenta de avaliação de riscos baseada em fluxo de trabalho no Portal de confiança de serviço para Microsoft. Permite-lhe controlar, atribuir e verificar suas atividades da organização a conformidade a normas relacionadas a serviços da Microsoft. Pode criar sua própria avaliação de conformidade com o Office 365, Azure, Dynamics, serviços profissionais e Intune. O Intune tem duas avaliações está disponíveis – FFIEC e GDPR.

Gestor de conformidade ajuda-o a concentrar seus esforços dividindo controles – controles de gerida pela Microsoft e geridos pela sua organização. Pode concluir as avaliações e, em seguida, exportar e imprimir as avaliações.

[Federal financeiros instituições exame Council (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (abre o outro site da Microsoft) a conformidade é um conjunto de padrões para a banca online emitido por FFIEC. É a avaliação mais pedida para instituições financeiras que utilizar o Intune. Ele interpreta como o Intune ajuda a atender às cargas de trabalho do FFIEC cibersegurança diretrizes em nuvem relacionados ao público. Avaliação de FFIEC do Intune é a avaliação de FFIEC segundo no Gestor de conformidade.

No exemplo a seguir, pode ver a divisão de FFIEC controles. Microsoft abrange 64 controles. É responsável para os controles de 12 restantes.

![Veja uma avaliação do Intune de exemplo para FFIEC, incluindo as ações de cliente e ações da Microsoft](./media/intune-ffiec-assessment-status.png)

[Regulamento geral de proteção de dados (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (abre o outro site da Microsoft) é uma lei da União Europeia (UE) que ajuda a proteger os direitos de indivíduos e respetivos dados. Com o GDPR é a avaliação mais pedida para ajudar a cumprir as normas de privacidade. 

No exemplo seguinte, verá a divisão de controles GDPR. Microsoft abrange 49 controles. É responsável para os controles de 66 restantes.

![Veja uma avaliação do Intune de exemplo para o GDPR, incluindo as ações de cliente e ações da Microsoft](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Semana de 15 de Abril de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Encriptação de OpenSSL para políticas de proteção de aplicações para Android <!-- 3747362 -->
Agora, o Intune políticas de proteção (aplicação) em dispositivos Android utiliza uma biblioteca de encriptação OpenSSL que tem certificação FIPS 140-2 em conformidade. Para obter mais informações, consulte a [encryption](app-protection-policy-settings-android.md#encryption) secção de [definições de política de proteção de aplicações Android no Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Ativar dependências de aplicações do Win32 <!-- 2617348  -->
Como administrador, pode exigir que as outras aplicações são instaladas como dependências antes de instalar a aplicação de Win32. Especificamente, o dispositivo tem de instalar a aplicação dependente (ões) antes de instalar a aplicação de Win32. No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar** para apresentar o **Adicionar aplicação** painel. Selecione **aplicação do Windows (Win32)** como o **tipo de aplicação**. Depois de ter adicionado a aplicação, pode selecionar **dependências** para adicionar as aplicações dependentes que devem ser instaladas antes de pode instalar a aplicação de Win32. Para obter mais informações, consulte [Intune autónomo - gestão de aplicações de Win32](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Informações de instalação de versão do aplicativo do Microsoft Store para aplicações empresariais <!-- 3537391   -->
Relatórios de instalação de aplicações incluem informações de versão de aplicação do Microsoft Store para aplicações de negócio. No Intune, selecione **aplicações de cliente** > **aplicações**. Selecione um **Microsoft Store para a aplicação de negócio** e, em seguida, selecione **estado de instalação de dispositivo** sob o **Monitor** secção.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Adições às regras de requisitos de aplicações do Win32 <!-- 3676883   -->
Pode criar requisito regras com base nos scripts do PowerShell, valores do Registro e informações do sistema de ficheiros. No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar**. Em seguida, selecione **aplicação do Windows (Win32)** como o **tipo de aplicação** no **Adicionar aplicação** painel.  Selecione **requisitos** > **Add** para configurar regras de requisitos adicionais. Em seguida, selecione **tipo de ficheiro**, **Registro**, ou **Script** como o **tipo de requisito**. Para obter mais informações, consulte [gestão de aplicações de Win32](apps-win32-app-management.md).

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurar as suas aplicações de Win32 a serem instalados nos inscritos no Intune dispositivos associados ao Azure AD <!-- 3695227  -->
Pode atribuir as aplicações de Win32 a serem instalados nos inscritos no Intune dispositivos associados ao Azure AD. Para obter mais informações sobre as aplicações de Win32 no Intune, consulte [gestão de aplicações de Win32](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---794259----"></a>Descrição geral do dispositivo mostra o utilizador primário <!--794259  -->
A página de descrição geral do dispositivo irá mostrar o utilizador primário, também chamado do utilizador de afinidade de dispositivo de utilizador (UDA). Para ver o utilizador primário para um dispositivo, escolha **Intune** > **dispositivos** > **todos os dispositivos** > Escolha um dispositivo. O utilizador primário aparecerá junto à parte superior do **descrição geral** página.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Relatórios adicionais da aplicação do Managed Google Play para dispositivos de perfil de trabalho do Android Enterprise <!-- 4105925  -->
Para as aplicações do Managed Google Play implementadas para dispositivos de perfil de trabalho do Android Enterprise, pode ver o número de versão específica da aplicação instalada num dispositivo. Tal só se aplica às aplicações obrigatórias. A mesma funcionalidade para aplicações disponíveis será habilitada numa versão futura. 

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS teclados de terceiros <!-- 4111843   -->
O suporte de política (aplicação) do Intune app protection para o **teclados de terceiros** configuração para iOS já não é suportado devido a uma alteração de plataforma iOS. Não será capaz de configurar esta definição na consola de administração do Intune e não serão imposto no cliente no SDK da aplicação Intune.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Configurar definições de início de sessão e controlar as opções de reinício em dispositivos macOS <!-- 1210083  -->
Em dispositivos macOS, pode criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > escolher **macOS** para a plataforma > **funcionalidades do dispositivo** para tipo de perfil). Esta atualização inclui novas definições de janela de início de sessão, por exemplo, que mostra uma faixa personalizada, escolha como os utilizadores iniciarem sessão, mostram ou ocultar as definições de energia e muito mais.

Para ver estas definições, aceda à [definições de funcionalidade do dispositivo macOS](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurar Wi-Fi no Android Enterprise, os dispositivos de proprietário do dispositivo dedicado em execução no modo de local público de várias aplicações <!--3041940  -->
Pode ativar as definições no Android Enterprise, o proprietário do dispositivo durante a execução como um dispositivo dedicado no modo de quiosque de várias aplicações. Nesta atualização, poderá habilitá-los configurar e ligar a redes Wi-Fi (**Intune** > **configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Android Enterprise** para a plataforma > **apenas proprietário do dispositivo, restrições de dispositivos** para tipo de perfil >  **Dispositivos dedicados** > **modo de local público**: **Multi-App** > **configuração de Wi-Fi**). 

Para ver todas as definições que pode configurar, aceda à [definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md).

Aplica-se a: Dispositivos Android da empresa dedicado em execução no modo de local público de várias aplicações


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurar o Bluetooth e emparelhamento no Android Enterprise, o proprietário do dispositivo dispositivos dedicados em execução no modo de local público de várias aplicações <!-- 3041941  -->
Pode ativar as definições no Android Enterprise, o proprietário do dispositivo durante a execução como um dispositivo dedicado no modo de quiosque de várias aplicações. Nesta atualização, pode permitir que os utilizadores finais permitir Bluetooth e emparelhe os dispositivos via Bluetooth (**Intune** > **configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Android Enterprise** para a plataforma > **apenas proprietário do dispositivo, restrições de dispositivos** do perfil tipo > **dispositivos dedicados** > **modo de local público**: **Multi-App** > **configuração de Bluetooth**). 

Para ver todas as definições que pode configurar, aceda à [definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md).

Aplica-se a: Dispositivos Android da empresa dedicado em execução no modo de local público de várias aplicações

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Criar e utilizar perfis de configuração de dispositivos de OEMConfig no Intune <!-- 3305883  -->
Esta atualização, o Intune suporta a configuração de dispositivos Android Enterprise com OEMConfig. Especificamente, pode criar um perfil de configuração do dispositivo e aplicar as definições para dispositivos Android Enterprise com OEMConfig (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Android enterprise** para a plataforma).

Suporte para OEMs encontra-se numa base por OEM. Se uma aplicação de OEMConfig pretende não estiver disponível na lista de aplicações de OEMConfig, entre em contato com `IntuneOEMConfig@microsoft.com`.

Para saber mais sobre esta funcionalidade, aceda à [utilizar e gerir dispositivos Android Enterprise com OEMConfig no Microsoft Intune](android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notificações de atualização do Windows  <!-- 3316758, 3316782  -->
Adicionámos dois *definições de experiência do usuário* à atualização do Windows em anel configurações que pode gerir a partir da consola do Intune. Agora, pode:
- Bloquear ou permitir que os usuários [procurar as atualizações do Windows](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- Gerir o [nível de notificação de atualização do Windows](windows-update-settings.md#windows-update-notification-level) que os utilizadores veem.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Novas definições de restrição de dispositivos do Android Enterprise, o proprietário do dispositivo <!-- 3574254  -->
Em dispositivos Android Enterprise, pode criar um perfil de restrição de dispositivos para permitir ou restringir funcionalidades, o conjunto de regras de palavra-passe e muito mais (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **Android Enterprise** para a plataforma > **apenas proprietário do dispositivo > restrições de dispositivos** para tipo de perfil). 

Esta atualização inclui novas definições de palavra-passe, permite o acesso total às aplicações do Google Play Store para dispositivos totalmente geridos e muito mais. Para ver a lista atual de definições, aceda à [definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md). 

Aplica-se a: Android Enterprise dispositivos totalmente geridos

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verifique a existência de um chipset TPM numa política de conformidade de dispositivos Windows 10 <!-- 3617671 -->

Esta funcionalidade é atrasada e deve ser incluída numa versão futura.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Alterações de interface do Usuário atualizadas para o Browser do Microsoft Edge no Windows 10 e dispositivos posteriores <!-- 3775833   -->
Quando cria um perfil de configuração do dispositivo, pode permitir ou restringir funcionalidades do Microsoft Edge no Windows 10 e dispositivos posteriores (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Windows 10 e posterior** para a plataforma, > **restrições de dispositivos** para o tipo de perfil >  **Browser Microsoft Edge**). Nesta atualização, as definições do Microsoft Edge são mais descritivo e mais fácil de entender. 

Para ver esses recursos, aceda a [definições de restrição de dispositivos de Browser do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

Aplica-se a: Windows 10 e posterior

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Suporte expandido para dispositivos Android Enterprise totalmente gerida (pré-visualização)  <!--   3903241, 3903244, 3903246   -->
Ainda na pré-visualização pública, Expandimos o nosso suporte de dispositivos empresariais Android totalmente gerido ([anunciada pela primeira vez em Janeiro de 2019](whats-new.md#week-of-january-14-2019) para incluir o seguinte: 

- Em dispositivos totalmente geridos e dedicados, pode criar [políticas de conformidade](compliance-policy-create-android-for-work.md) para incluir regras de palavra-passe e requisitos do sistema operativo (**conformidade do dispositivo**  >   **As políticas** > **criar política** > **Android Enterprise** para a plataforma > **proprietário do dispositivo** para tipo de perfil). 

  Em dispositivos dedicados, o dispositivo pode mostrar como **não conformes**. Acesso condicional não está disponível nos dispositivos dedicados. Realize algumas tarefas ou ações para que os dispositivos dedicados fiquem em conformidade com as políticas atribuídas.

- [Acesso condicional](conditional-access.md) -dispositivos geridos pelo acesso condicional, as políticas que se aplicam ao Android também se aplicam ao Android Enterprise totalmente. Os utilizadores podem agora registar o respetivo dispositivo completamente gerido no Azure Active Directory com o **da aplicação Microsoft Intune**. Em seguida, ver e resolver quaisquer problemas de conformidade para aceder a recursos organizacionais.

- Nova aplicação de utilizador final (Microsoft da aplicação Intune) – há uma nova aplicação de utilizador final para Android totalmente geridos chamados **Microsoft Intune**. Esta nova aplicação é leves e modernos e fornece semelhante funcionalmente como a aplicação Portal da empresa, mas para dispositivos totalmente gerenciados. Para obter mais informações, consulte [da aplicação Microsoft Intune no Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Para configurar o Android totalmente geridos os dispositivos, aceda a **inscrição de dispositivos** > **inscrição de dispositivos Android** > **dispositivos de utilizador de propriedade da empresa, totalmente gerido**. Suporte para dispositivos Android geridos totalmente permanece em pré-visualização e algumas funcionalidades do Intune poderão não estar totalmente funcionais.  

Para saber mais sobre esta pré-visualização, veja o nosso blogue [Preview 2 para dispositivos Android Enterprise totalmente gerido do Microsoft Intune –](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>Configurar o perfil para ignorar algumas telas durante o Assistente de configuração <!-- 2276470  wnstaged-->
Quando cria um macOS perfil de inscrição, pode configurar para ignorar qualquer um dos ecrãs seguintes quando um utilizador executa o Assistente de configuração:
- Aparência
- Sinal de Exibição
- iCloudStorage se criar um novo perfil ou editar um perfil, selecionado ignorar ecrãs necessidade para sincronizar com o servidor de MDM da Apple.  Os utilizadores podem emitir uma sincronização manual dos dispositivos, para que haja um atraso de escolher as alterações de perfil.
Para obter mais informações, consulte [inscrever automaticamente dispositivos macOS com o programa de inscrição de dispositivos ou do Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Em massa de dispositivos de nomenclatura quando inscrever dispositivos iOS empresariais<!--3566569  -->
Quando utilizar um dos métodos de inscrição da empresa da Apple (DEP/ABM/ASM), pode definir um formato de nome de dispositivo para automaticamente nome entrada dispositivos iOS. Pode especificar um formato que inclui o tipo de dispositivo e o número de série do seu modelo. Para tal, escolha **Intune** > **inscrição de dispositivos** > **inscrição da Apple** > **programa de inscrição tokens** > **selecione um token** >**criar perfil** > **formato de nomenclatura de dispositivo**. Pode editar perfis existentes, mas apenas os dispositivos recentemente sincronizados terá o nome aplicado.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Mensagem de tempo limite padrão atualizada na página de estado de inscrição <!-- 3959331 -->
Atualizámos a mensagem de tempo limite predefinido, os utilizadores veem quando a página de estado de inscrição (ESP) excede o valor de tempo limite especificado no perfil do ESP. A nova mensagem predefinido é o que os utilizadores veem e ajuda a entender as ações de seguintes com a implantação do ESP.  

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Extinguir dispositivos não conformes  <!-- 1827291   -->
Esta funcionalidade foi adiada e será fornecido numa versão futura.


### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Alterações de V1.0 de armazém de dados do Intune refletindo para o beta <!-- 4403765 -->
Quando a versão 1.0 foi introduzida inicialmente no 1808, eram diferentes quanto de algumas maneiras significativas da versão beta API. No 1903 essas alterações serão refletidas novamente para a versão de API do beta. Se tiver relatórios importantes que utilizem a versão de API do beta, é altamente recomendável mudar esses relatórios para a versão 1.0 para evitar alterações significativas. Para obter mais informações, consulte [registo de alterações para a API do armazém de dados do Intune](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorizar o estado de linha de base de segurança (pré-visualização pública) <!-- 3082047 --> 
Adicionámos uma [vista por categoria](security-baselines-monitor.md#per-category-view) para a monitorização de linhas de base de segurança. (Linhas de base de segurança permanecem na pré-visualização). O modo de exibição por categoria apresenta cada categoria da linha de base juntamente com a percentagem de dispositivos que pertencem a cada grupo de estado para essa categoria. Agora, pode ver o número de dispositivos não corresponde as categorias individuais, é configurado incorretamente ou não se aplicam.

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Etiquetas de âmbito para tokens VPP da Apple <!--2371886  -->
Agora pode adicionar etiquetas de âmbito para tokens VPP da Apple. Apenas os utilizadores com a mesma etiqueta de âmbito têm acesso para o token de Apple VPP com a mesma. As aplicações VPP e ebooks adquirido com esse token herdam suas etiquetas de âmbito. Para obter mais informações sobre etiquetas de âmbito, veja [marcas RBAC de utilização e âmbito](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Semana de 1 de Abril de 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Conectores de certificado atualizado  <!-- ICM 113304612 -->
Lançámos atualizações para ambos os [Intune Certificate Connector e o conector do certificado PFX para o Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors). As novas versões resolver vários problemas conhecidos.  

### <a name="app-management"></a>Gestão de aplicações

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS <!-- 2536024 -->
Foi reestruturada a home page da aplicação Portal da empresa para dispositivos iOS. Com esta alteração, a home page será melhor siga os padrões de interface do Usuário do iOS e também fornecem a capacidade de deteção melhorada para aplicações e e-Books.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Alterações para a inscrição no Portal da empresa para os utilizadores de dispositivos iOS 12 <!--3448635 -->  
O Portal da empresa para ecrãs de inscrição de iOS e os passos foram atualizadas para alinhar com as alterações de inscrição de MDM lançadas no Apple iOS 12.2. O fluxo de trabalho atualizado solicita aos usuários para:  

* Permita o Safari abrir o site do Portal da empresa e transferir o perfil de gestão antes de retornar para a aplicação Portal da empresa.  
* Abra a aplicação de definições para instalar o perfil de gestão no respetivo dispositivo.
* Regressar à aplicação Portal da empresa que conclua a inscrição.  

Para obter os passos de inscrição atualizadas e telas, veja [inscrever o dispositivo de iOS no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Semana de 25 de Março de 2019

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Suporte para a aplicação de conformidade do Power BI a partir do painel do armazém de dados no Microsoft Intune <!-- 4260871 -->
Anteriormente, o **ficheiros de transferir o Power BI** ligação na **armazém de dados do Intune** painel transferido um relatório de armazém de dados do Intune (ficheiro. pbix). Este relatório foi substituído com a aplicação de conformidade do Power BI. A aplicação de conformidade do Power BI não precisará de configuração ou de carregamento especial. Ele irá abrir diretamente no portal online do Power BI e exibir dados especificamente para o seu inquilino do Intune com base nas suas credenciais. No Intune, selecione o **definir o armazém de dados do Intune** ligação no lado direito do painel do Intune. Em seguida, clique em **obter a aplicação do Power BI**. Para obter mais informações, consulte [ligar ao armazém de dados com o Power BI](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Semana de 18 de Março de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Implantar o Microsoft Visio e o Microsoft Project <!-- 3725386  -->
Agora pode implementar Microsoft Visio Pro para Office 365 e o cliente de ambiente de trabalho do Microsoft Project Online independente das aplicações para dispositivos Windows 10 com o Microsoft Intune, se tiver licenças para estas aplicações. A partir do Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar** para apresentar o **Adicionar aplicação** painel. Sobre o **Adicionar aplicação** painel, selecione **com o Windows 10** como o **tipo de aplicação**. Em seguida, selecione **configurar o conjunto de aplicações** para selecionar os aplicativos sejam instalados. Para obter mais informações sobre aplicações do Office 365 para dispositivos Windows 10, consulte [aplicações de atribuir o Office 365 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro para alteração de nome de produto do Office 365 <!-- 3593653  -->
**Microsoft Visio Pro para Office 365** será agora conhecido como **Microsoft Visio Online plano 2**.  Para obter mais informações sobre o Microsoft Visio, consulte [Visio Online plano 2](https://products.office.com/visio/visio-online-plan-2). Para obter mais informações sobre aplicações do Office 365 para dispositivos Windows 10, consulte [aplicações de atribuir o Office 365 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune app protection política (aplicação) caráter configuração do limite <!-- 3291302  -->
Os administradores do Intune, podem especificar uma exceção para a aplicação do Intune **restringir operações cortar, copiar e colar com outras aplicações** definição de política.  Como administrador, pode especificar o número de carateres que podem ser cortados ou copiados de uma aplicação gerida. Esta definição irá permitir a partilha do número especificado de carateres a todas as aplicações, independentemente do "restringir operações cortar, copiar e colar com outras aplicações" definição. Observe que a versão da aplicação Portal da empresa do Intune para Android requer a versão 5.0.4364.0 ou posterior. Para obter mais informações, consulte [proteção de dados de iOS](app-protection-policy-settings-ios.md#data-protection), [proteção de dados em dispositivos Android](app-protection-policy-settings-android.md#data-protection), e [rever registos de proteção de aplicações de cliente](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Ferramenta de implementação do Office (ODT) XML para a implementação do Office ProPlus <!-- 3192477   -->
Será capaz de fornecer a ferramenta de implementação do Office (ODT) XML ao criar uma instância do Office Pro Plus na consola de administração do Intune. Isso permitirá que a maior capacidade de personalização se as opções de interface do Usuário do Intune existentes não atenderem às suas necessidades. Para obter mais informações, consulte [aplicações de atribuir o Office 365 a dispositivos Windows 10 com o Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) e [opções de configuração para a ferramenta de implementação do Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Os ícones da aplicação serão agora apresentados com um fundo gerado automaticamente <!-- 1429026  -->
Na aplicação Portal da empresa de Windows, os ícones da aplicação serão agora apresentados com um fundo gerado automaticamente com base na cor dominante do ícone (caso seja possível detetar uma). Quando aplicável, este plano de fundo substituirá o limite cinzento que era visível anteriormente nos mosaicos das aplicações. Os utilizadores irão ver esta alteração nas versões mais tarde do que 10.3.3451.0 do Portal da empresa.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Instalar as aplicações disponíveis com a aplicação Portal da empresa após a inscrição em massa do Windows <!-- 2751523   -->
Dispositivos Windows inscritos no Intune, utilizando [inscrição em massa de Windows](windows-bulk-enroll.md) (pacotes de aprovisionamento) será possível utilizar a aplicação do Portal da empresa para instalar as aplicações disponíveis. Para obter mais informações sobre a aplicação Portal da empresa, consulte [adicionar manualmente o Portal da empresa do Windows 10](store-apps-company-portal-app.md) e [como configurar a aplicação Portal da empresa do Microsoft Intune](company-portal-app.md).

> [!Note]
> Esta funcionalidade ainda não totalmente foi implementada para todos os clientes. Se não é possível utilizar o Portal da empresa em dispositivos em massa inscritos, poderá ter de aguardar até que esta alteração for implementada para a sua conta.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>A aplicação Microsoft Teams pode ser selecionada como parte do pacote de aplicação do Office <!-- 3828932  -->
A aplicação Microsoft Teams pode ser incluída ou excluída como parte da instalação do pacote de aplicação Office Pro Plus. Esta funcionalidade funciona para Office Pro Plus 16.0.11328.20116+ de número de compilação. O utilizador tem de terminar sessão e, em seguida, inicie sessão no dispositivo para a conclusão da instalação. No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar**. Selecione uma da **Office 365 Suite** tipos de aplicações e selecione **configurar conjunto de aplicações**.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Iniciar automaticamente uma aplicação ao executar várias aplicações no modo de local público no Windows 10 e dispositivos posteriores <!-- 2351390 -->

No Windows 10 e dispositivos posteriores, pode executar um dispositivo no modo de quiosque e executar muitos aplicativos. Nesta atualização, há uma **AutoLaunch** definição (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** para a plataforma > **quiosque** para o tipo de perfil > **quiosque de várias aplicações**). Utilize esta definição para iniciar automaticamente uma aplicação quando o utilizador inicia sessão no dispositivo.

Para ver uma lista e a descrição de todas as definições de local público, consulte [Windows 10 e posteriores definições do dispositivo para ser executado como um quiosque no Intune](kiosk-settings-windows.md).

Aplica-se a: Windows 10 e posterior

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Registos operacionais também mostram detalhes em dispositivos não conformes <!-- 4063755  -->
Quando inicia sessão Intune encaminhamento recursos do Azure monitor, também pode encaminhar registos operacionais. Nesta atualização, o registos operacionais também fornecem informações sobre dispositivos não conformes. 

Para obter mais informações sobre esta funcionalidade, consulte [enviar dados de registo para armazenamento, os hubs de eventos ou do log analytics no Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Registos de rota para o Azure Monitor em mais cargas de trabalho do Intune <!-- 3804627 -->
No Intune, pode encaminhar a auditoria e registos operacionais para os hubs de eventos, armazenamento e do log analytics no Azure Monitor (**Intune** > **monitorização** > **diagnóstico definições**). Nesta atualização, pode encaminhar esses logs em mais Intune cargas de trabalho, incluindo a conformidade, configurações, aplicações de cliente e muito mais. 

Para saber mais sobre os registos de encaminhamento para o Azure Monitor, consulte [enviar dados de registo para o armazenamento, os hubs de eventos ou do log analytics](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Criar e utilizar extensões de mobilidade em dispositivos das riscas das Android no Intune <!-- 3305880   -->
Esta atualização, o Intune suporta a configuração de dispositivos das riscas das Android. Especificamente, pode criar um perfil de configuração do dispositivo e aplicar as definições para dispositivos as riscas das Android através de perfis de extensões de mobilidade (MX) gerados pelo StageNow (**configuração do dispositivo**  >   **Perfis** > **criar perfil** > **Android** para a plataforma > **perfil de MX (apenas as riscas das)** do perfil tipo).

Para obter mais informações sobre esta funcionalidade, consulte [utilizar e gerir os dispositivos as riscas com extensões de mobilidade no Intune](android-zebra-mx-overview.md).

Aplica-se a: Android

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Relatório de encriptação para dispositivos do Windows 10 (em pré-visualização pública)<!-- 2351538 -->  
Utilizar a nova [relatório de encriptação (pré-visualização)](encryption-monitor.md) para ver detalhes sobre o estado de encriptação dos seus dispositivos Windows 10. Detalhes disponíveis incluem uma versão do TPM de dispositivos, preparação de encriptação e o estado, o relatório de erros e mais.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Aceder a chaves de recuperação do BitLocker a partir do portal do Intune (em pré-visualização pública) <!-- 2351547   -->  
Agora pode utilizar o Intune para [ver detalhes](encryption-monitor.md) sobre o ID da chave do BitLocker e chaves de recuperação do BitLocker, do Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Suporte do Microsoft Edge para cenários do Intune em dispositivos iOS e Android <!-- 3411007 -->
Microsoft Edge irá suportar todos os cenários de gestão mesmo como o Intune Managed Browser com a adição de melhorias na experiência de utilizador final. As funcionalidades de enterprise do Microsoft Edge que estão ativadas por políticas do Intune incluem dual-Identity, integração de política de proteção de aplicações, integração de proxy de aplicações do Azure e gerenciados de Favoritos e os atalhos de página inicial. Para obter mais informações, consulte [suporte do Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Conector do Exchange Online/Intune Preterir o suporte para apenas os dispositivos EAS <!--3105122  -->
A consola do Intune já não suporta a visualização e gestão de dispositivos só de EAS ligados ao Exchange Online com o conector do Intune. Em vez disso, tem as seguintes opções:
- Inscrever dispositivos na gestão de dispositivos móveis (MDM)
- Utilizar políticas de proteção de aplicações do Intune para gerir os seus dispositivos
- Utilizar controlos de Exchange, conforme descrito na [clientes e dispositivos móveis no Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Procure página todos os dispositivos de um dispositivo exata, utilizando [nome] <!--4254930 -->
Agora pode procurar um nome de dispositivo exato. Aceda a **Intune** > **dispositivos** > **todos os dispositivos** > na caixa de pesquisa, coloque o nome do dispositivo com {} para procurar um correspondência exata. Por exemplo, **{Device12345}** .

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Suporte para conectores adicionais na página de estado do inquilino <!-- 3617202  -->
O [página de estado do inquilino](tenant-status.md) agora mostra informações de estado de conectores adicionais, incluindo *proteção de ameaças avançada do Windows Defender* (ATP) e outros conectores de defesa contra ameaças móveis.

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Intune a conceder acesso de leitura apenas ao algumas funções do Azure Active Directory <!-- 3637917  -->
Intune ler apenas o acesso foi concedido para as seguintes funções do Azure AD. Permissões concedidas com funções do Azure AD substituem as permissões concedidas com controlo de acesso baseado em funções (RBAC) do Intune.

Ler apenas o acesso aos dados de auditoria do Intune:

- Administrador de conformidade
- Administrador de dados de conformidade

Acesso só de leitura a todos os dados do Intune:

- Administrador de Segurança
- Operador de segurança
- Leitor de segurança

Para obter mais informações, consulte [controlo de acesso baseado em funções](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Etiquetas de âmbito para perfis de aprovisionamento de aplicações iOS <!--2934430   -->
Pode adicionar uma etiqueta de âmbito para um perfil de aprovisionamento de aplicações iOS, para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso para o perfil de aprovisionamento de aplicações iOS. Para obter mais informações, consulte [marcas RBAC de utilização e âmbito](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Etiquetas de âmbito para políticas de configuração de aplicações <!--2371891   -->
Pode adicionar uma etiqueta de âmbito para uma política de configuração de aplicação para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso para a política de configuração de aplicação. A política de configuração de aplicação só pode ser direcionada para ou associada a aplicações atribuídas a mesma etiqueta de âmbito. Para obter mais informações, consulte [marcas RBAC de utilização e âmbito](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Suporte do Microsoft Edge para cenários do Intune em dispositivos iOS e Android <!-- 3411007 -->
Microsoft Edge irá suportar todos os cenários de gestão mesmo como o Intune Managed Browser com a adição de melhorias à experiência de utilizador final. As funcionalidades de enterprise do Microsoft Edge que estão ativadas por políticas do Intune incluem dual-Identity, integração de política de proteção de aplicações, integração de proxy de aplicações do Azure e gerenciados de Favoritos e os atalhos de página inicial. Para obter mais informações, consulte [suporte do Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Semana de 25 de Fevereiro de 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="intune-powershell-module----951068----"></a>Módulo do PowerShell do Intune <!-- 951068  -->
O módulo PowerShell do Intune, que fornece suporte para a API do Intune através do Microsoft Graph, está agora disponível na [Gallery do PowerShell Microsoft](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Detalhes sobre como utilizam este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemplos de cenário com este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Suporte aprimorado para otimização de entrega  <!--3183757  -->
Expandimos o suporte do Intune para configurar a otimização de entrega. Agora, pode configurar uma lista expandida de [as definições de otimização de entrega](delivery-optimization-settings.md) e aplicá-lo para os seus dispositivos diretamente a partir do consola do Intune.


## <a name="week-of-february-18-2019"></a>Semana de 18 de Fevereiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune será tiram partido das APIs de proteger reproduzir da Google em dispositivos Android <!-- 2577355   -->
Alguns administradores de TI enfrentam um cenário BYOD onde os utilizadores finais podem acabar embota ou jailbreaking o celular. Este comportamento, embora às vezes, não mal-bem-intencionado, resulta numa omissão de muitas das políticas do Intune que estão definidas para proteger os dados da organização nos dispositivos do utilizador final. Assim, o Intune fornece deteção de raiz e jailbreak para dispositivos inscritos e não inscritos. Com esta versão, o Intune irá agora tirar Google Play proteger APIs para adicionar à nossa verificações existentes para a deteção de raiz para dispositivos não inscritos. Embora a Google não partilha a totalidade das verificações de deteção de raiz que ocorrem, esperamos que essas APIs para detetar os utilizadores que têm Root seus dispositivos por qualquer motivo de personalização do dispositivo para a capacidade de obter as atualizações de SO mais recente nos dispositivos mais antigos. Estes utilizadores, em seguida, podem ser impedidos de aceder a dados empresariais ou suas contas empresariais poderão ser eliminadas a partir das suas aplicações de política ativada. Para o valor adicional, o administrador de TI agora têm várias atualizações de geração de relatórios no painel de proteção de aplicações do Intune – o relatório de "Utilizadores sinalizados" irá mostrar os utilizadores que são detetados através do análise de SafetyNet API da Google Play Protect, o "potencialmente prejudicial aplicações" relatório irá mostre as aplicações são detetadas através verificar aplicações API da Google de verificação. Esta funcionalidade está disponível no Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informações da aplicação Win32 disponíveis no painel de resolução de problemas <!-- 2617342   -->
Agora pode recolher ficheiros de registo de falha para uma instalação de aplicações de Win32 a partir da aplicação Intune **resolução de problemas** painel. Para obter mais informações sobre resolução de problemas de instalação de aplicação, consulte [resolver problemas de instalação de aplicações](troubleshoot-app-install.md) e [problemas de aplicações de Win32 de resolução de problemas](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Detalhes do Estado da aplicação para aplicações iOS <!-- 3761235   -->
Existem mensagens de erro de instalação de aplicação nova relacionadas ao seguinte:
- Falha de aplicações VPP durante a instalação num iPad partilhado
- Falha quando a loja de aplicações está desativada
- Falha ao localizar a licença do VPP para aplicação
- Falha ao instalar aplicações de sistemas com o fornecedor de MDM
- Falha ao instalar aplicações quando o dispositivo estiver no modo perdido ou o modo de local público
- Falha ao instalar a aplicação quando o utilizador não tem sessão iniciado na App Store

No Intune, selecione **aplicações de cliente** > **aplicações** > "Nome da aplicação" > **estado de instalação de dispositivo**. Novas mensagens de erro estará disponíveis na **detalhes do estado** coluna.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Novo ecrã de categorias de aplicação na aplicação Portal da empresa para Windows 10<!-- 3834780  -->
Um ecrã novo chamado **categorias de aplicações** foi adicionado para melhorar a experiência de navegação e a seleção de aplicação no Portal da empresa para Windows 10. Os utilizadores irão ver agora as aplicações ordenadas em categorias, como **em destaque**, **educação**, e **produtividade**. Esta alteração apareça em versões do Portal da empresa 10.3.3451.0 e mais tarde. Para ver o novo ecrã, consulte [quais são as novidades na IU da aplicação](https://docs.microsoft.com/intune/whats-new-app-ui). Para obter mais informações sobre as aplicações no Portal da empresa, consulte [instalar e partilhar aplicações no seu dispositivo](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Aplicação de conformidade do Power BI <!-- 1455231 doc-work-item -->
Aceder ao seu armazém de dados do Intune no Power BI Online com o [conformidade do Intune (armazém de dados)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) aplicação. Com esta aplicação do Power BI, pode agora aceder e partilhar relatórios previamente criados sem qualquer configuração e sem sair do seu navegador da web. Para obter mais informações, consulte [registo de alterações - aplicação de conformidade do Power BI](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Scripts do PowerShell podem ser executado num host de 64 bits em dispositivos de 64 bits <!-- 1862675   -->
Quando adiciona um script do PowerShell para um perfil de configuração do dispositivo, o script é executado sempre de 32 bits, mesmo em sistemas de operativos de 64 bits. Com esta atualização, um administrador pode executar o script num host do PowerShell de 64 bits em dispositivos de 64 bits (**configuração do dispositivo** > **scripts do PowerShell**  >   **Adicione** > **configurar** > **executar script num anfitrião do PowerShell de 64 bits**).

Para obter mais detalhes sobre como utilizar o PowerShell, consulte [scripts do PowerShell no Intune](intune-management-extension.md).

Aplica-se a: Windows 10 e posterior

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>utilizadores do macOS-lhe pedidos para atualizar a palavra-passe <!-- 1873216 -->
Intune é aplicar a **ChangeAtNextAuth** definição em dispositivos macOS. Esta definição irá afetar os utilizadores finais e dispositivos que têm políticas de conformidade de palavra-passe ou perfis de palavra-passe de restrição de dispositivos. Os utilizadores finais for pedidos, uma vez, para atualizar a palavra-passe. Este pedido acontece sempre que um utilizador primeiro executa uma tarefa que exige autenticação, como iniciar sessão no dispositivo. Também podem ser pedido aos utilizadores para atualizar a palavra-passe quando fazer nada que requer privilégios administrativos, como pedir acesso de keychain. 

Quaisquer alterações de política de palavra-passe nova ou existente pelo administrador pede-lhe os utilizadores finais novamente para atualizar a palavra-passe.

Aplica-se a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>Atribuir certificados SCEP para um dispositivo macOS sem utilizador  <!-- 2340521  -->
Pode atribuir certificados Simple Certificate Enrollment Protocol (SCEP), usando atributos de dispositivo para dispositivos macOS, incluindo os dispositivos sem afinidade do utilizador e associar o perfil de certificado, Wi-Fi ou perfis VPN. Isso expande o suporte já temos a [atribuir certificados SCEP para dispositivos com e sem afinidade do utilizador](certificates-scep-configure.md#create-a-scep-certificate-profile) que executam o Windows, iOS e Android.  Esta atualização adiciona a opção de selecionar um tipo de certificado de *dispositivo* ao configurar um perfil de certificado SCEP para o macOS.

Aplica-se a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Atualização de interface do Usuário de acesso condicional do Intune   <!-- 2432313   -->
Fizemos melhorias na interface do usuário para o acesso condicional na consola do Intune. Estas incluem:
-  Substituído do Intune *acesso condicional* painel com o painel do Azure Active Directory. Isto garante que terá acesso a uma gama completa de definições e configurações para [acesso condicional](conditional-access.md) (que continua sendo uma tecnologia do Azure AD), do Intune consola. 
- Mudamos o nome da *acesso no local* painel para *acesso ao Exchange*e realocada o *conector de serviço do Exchange* configuração deste painel nome mudado.  Esta alteração consolida onde [configurar e monitorizar detalhes relacionados com o Exchange online e no local](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Aplicações de Browser de local público e o Browser do Microsoft Edge podem ser executadas em dispositivos Windows 10 no modo de local público <!-- 2935135   -->
Pode utilizar dispositivos Windows 10 no modo de local público para executar uma aplicação ou muitas aplicações. Esta atualização inclui várias alterações para utilizar aplicações de browser no modo de local público, incluindo:

- Adicionar o Browser do Microsoft Edge ou o Browser de local público para ser executado como aplicações no dispositivo local público (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **Windows 10 e posterior** para a plataforma > **quiosque** para tipo de perfil).
- Novos recursos e as definições estão disponíveis para permitir ou restringir (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **Windows 10 e posterior** para a plataforma > **restrições de dispositivos** para tipo de perfil), incluindo:

  - Microsoft Edge Browser:
  - Utilizar o modo de local público do Microsoft Edge
  - Atualize o browser após o tempo de inatividade

 - Favoritos e pesquisar:
  - Permitir alterações para o mecanismo de pesquisa

Para obter uma lista destas definições, consulte:

- [Windows 10 e posteriores definições do dispositivo para ser executado como um quiosque](kiosk-settings-windows.md)
- [Restrições de dispositivos de Browser do Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Favoritos e restrições de dispositivos de pesquisa](device-restrictions-windows-10.md##favorites-and-search)

Aplica-se a: Windows 10 e posterior

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Novas definições de restrição de dispositivos para dispositivos iOS e macOS <!-- 3448774   -->
Pode restringir algumas definições e funcionalidades nos dispositivos que executam o iOS e macOS (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **iOS** ou **macOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização adiciona mais funcionalidades e as definições que pode controlar, incluindo o tempo de ecrã de configuração, alterar definições de eSIM e planos de celular e muito mais em dispositivos iOS. Além disso, atrasando a visibilidade do usuário de atualizações de software e a bloquear a colocação em cache conteúdo em dispositivos macOS. 

Para ver os recursos e configurações que pode restringir, consulte:

- [definições de restrição de dispositivos iOS](device-restrictions-ios.md)
- [definições de restrição de dispositivos macOS](device-restrictions-macos.md)

Aplica-se a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Dispositivos de "local público" são agora denominados "Dispositivos dedicados" em dispositivos Android Enterprise <!-- 3598402   -->
Para se alinhar a terminologia do Android, **quiosque** é alterado para **dispositivos dedicados** para dispositivos Android enterprise (**configuração do dispositivo**  >  **Perfis** > **criar perfil** > * * Android enterprise para a plataforma > **dispositivo proprietário apenas** > **dispositivo Restrições** > **dispositivos dedicados**).

Para ver as definições disponíveis, aceda à [definições do dispositivo para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari e Delaying utilizador atualização de software iOS visibilidade definições estão a ser movidos na IU do Intune <!-- 3640850, 3803313   -->
Para dispositivos iOS, pode configurar as definições do Safari e configurar atualizações de Software. Nesta atualização, estas definições estão a ser movidos para diferentes partes da IU do Intune:

- As definições do Safari movidas de **Safari** (**configuração do dispositivo** > **perfis** > **novo perfil**  >  **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil) para  **[aplicações incorporadas](device-restrictions-ios.md#built-in-apps)**.
- O **atrasar a visibilidade de atualização de software de utilizador para supervisionado dispositivos iOS** definição (**atualizações de Software** > **atualizar políticas para iOS**) está a mudar para  **Restrições de dispositivos** > **[geral](device-restrictions-ios.md#general)**.  Para obter detalhes sobre o impacto para as políticas existentes, consulte [atualizações de software iOS](software-updates-ios.md#configure-the-policy). 

Para obter uma lista das definições, consulte:

- [restrições de dispositivos iOS](device-restrictions-ios.md) 
- [atualizações de software do iOS](software-updates-ios.md)

Esta funcionalidade aplica-se a: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Ativar restrições nas definições do dispositivo foi mudado para o tempo de tela em dispositivos iOS <!-- 3699164   -->
Pode configurar o **ativar restrições nas definições do dispositivo** no supervisionado dispositivos iOS (**configuração do dispositivo** > **perfis**  >  **Novo perfil** > **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **geral**). Nesta atualização, esta definição foi mudada para **tempo de ecrã (apenas supervisionado)** . 

O comportamento é o mesmo. Especificamente: 

- iOS 11.4.1 e anterior: **Bloquear** impede que os utilizadores finais definam as suas próprias restrições nas definições do dispositivo. 
- iOS 12.0 e posterior: **Bloco** impede que os utilizadores finais definir seus próprios **ecrã tempo** nas definições do dispositivo, incluindo restrições de privacidade & de conteúdo. Dispositivos atualizados para o iOS 12.0 não verão a guia restrições nas definições do dispositivo deixa de poder. Estas definições estão em **Tempo do Ecrã**. 

Para obter uma lista das definições, consulte [restrições de dispositivos iOS](device-restrictions-ios.md#general).

Aplica-se a: 
- iOS


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Mudar o nome de um dispositivo Windows inscrito <!-- 1911112  -->
Agora pode renomear um dispositivo Windows 10 inscrito (RS4 ou posterior). Para fazer, escolha **Intune** > **dispositivos** > **todos os dispositivos** > Escolha um dispositivo > **mudança de nome de dispositivo**. Esta funcionalidade não suporta atualmente a mudança de nome dispositivos de Windows do Azure AD híbrido.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Atribuir automaticamente etiquetas de âmbito para recursos criados por um administrador com esse âmbito <!-- 3173823  -->
Quando um administrador cria um recurso, quaisquer etiquetas de âmbito atribuídas para o administrador serão automaticamente atribuídas a esses novos recursos.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Relatório de inscrição falha se move para o painel de inscrição de dispositivos <!-- 3560202  -->
O **falha inscrições** relatório foi movido para o **Monitor** seção o **inscrição de dispositivos** painel. Foram adicionadas duas novas colunas (método de inscrição e versão do SO).

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Relatório de abandonment de Portal da empresa foi mudado para inscrições de utilizador incompleto <!--3815076 eemiss -->
O **abandonment do Portal da empresa** relatório foi renomeado para **inscrições de utilizador incompleta**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Semana de 4 de Fevereiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>No modo escuro do Portal da empresa do Intune macOS <!-- 3300524  -->
O Portal da empresa do macOS do Intune agora suporta o modo escuro para macOS. Quando ativar o modo escuro num dispositivo macOS 10.14 +, o Portal da empresa irá ajustar sua aparência para as cores que refletem esse modo.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Semana de 21 de Janeiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notificações de alerta para aplicações de Win32 <!-- 3136566   -->
É possível suprimir notificações de alerta do utilizador final que mostra por atribuição de aplicações. A partir do Intune, selecione **aplicações de cliente** > **aplicações** > selecione a aplicação > **atribuições** > **grupos incluem**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Atualização de interface do Usuário de políticas de proteção de aplicação de Intune <!-- 3251427  -->
Alterámos as etiquetas para as definições e botões para proteção de aplicações do Intune para que cada mais fácil de compreender. Algumas das alterações incluem:  
- Controles são alterados de **Sim** / **nenhum** controla principalmente para **bloco** / **permitir** e **desativar** / **ativar** controles. As etiquetas também são atualizadas.  
- As definições são reformatadas, portanto, a definição e a etiqueta são lado a lado no controle, para fornecer uma navegação melhor.   

As predefinições e diversas configurações permanecem os mesmos, mas esta alteração permite ao utilizador entender, navegar e utilizar as definições mais facilmente para aplicar políticas de proteção da aplicação selecionada. Para obter informações, consulte [definições do iOS](app-protection-policy-settings-ios.md) e [definições do Android](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Definições adicionais para o Outlook <!-- 3301182  -->
Agora pode configurar as seguintes definições adicionais para o Outlook para iOS e Android com o Intune:

- Permitir apenas contas escolares ou profissionais a ser utilizado no Outlook no iOS e Android
- Implementar a autenticação moderna do Office 365 e a autenticação moderna híbrida contas no local
- Utilize `SAMAccountName` para o campo de nome de utilizador no perfil de e-mail quando a autenticação básica é seleccionada
- Permitir que os contactos sejam guardados
- Configurar destinatários externos dicas de email
- Configurar **caixa de entrada destaques**
- Exigir biometria para acessar o Outlook para iOS
- Bloquear a imagens externas

> [!NOTE]
> Se estiver a utilizar políticas de proteção de aplicações do Intune para gerir o acesso de identidades empresariais, deve considerar a ativação não **requerem biometria**. Para obter mais informações, consulte **requerer credenciais empresariais de acesso** para [iOS as definições de acesso](app-protection-policy-settings-ios.md#access-requirements) e [definições de acesso para Android](app-protection-policy-settings-android.md#access-requirements).

Para obter mais informações, consulte [definições de configuração do Microsoft Outlook](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminar as aplicações do Android Enterprise <!-- 1352553 -->
Pode eliminar as aplicações geridas do Google Play do Microsoft Intune. Para eliminar uma aplicação do Managed Google Play, abra o Microsoft Intune no portal do Azure e selecione **Aplicações cliente** > **Aplicações**. Na lista de aplicações, selecione as reticências (...) à direita da aplicação do Managed Google Play e, em seguida, selecione **Eliminar** na lista apresentada. Quando elimina uma aplicação do Managed Google Play da lista de aplicações, essa aplicação passa automaticamente a não aprovada.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo de aplicações do Managed Google Play <!-- 1352580 -->
O **managed Google Play** tipo de aplicação permite-lhe adicionar especificamente [Google Play aplicações geridas](https://play.google.com/work/search?q=microsoft&c=apps) ao Intune. Como o administrador do Intune, pode agora navegar, procurar, aprovar, sincronizar e atribuir aprovados Google Play gerido aplicações no Intune.  Já não precisa de procurar na consola do Managed Google Play separadamente e já não tem de se autenticar novamente.  No Intune, selecione **aplicações de cliente** > **aplicações** > **adicionar**. Na **tipo de aplicação** lista, selecione **Google Play gerido** como o tipo de aplicação.

### <a name="default-android-pin-keyboard----3802457---"></a>Teclado de Android PIN predefinido <!-- 3802457 -->
Para os utilizadores finais que definiu uma aplicação de proteção de política (PIN da aplicação Intune) nos respetivos dispositivos Android com o tipo PIN de "Numérica", irão ver agora o teclado de Android padrão em vez de teclado Android fixo da interface do Usuário que foi criado anteriormente. Esta alteração foi feita para ser consistente ao utilizar o teclados padrão no Android e iOS, para os dois tipos PIN de "Numérica" e/ou de "Código de acesso". Para obter mais informações sobre as definições de acesso do utilizador final no Android, por exemplo, o PIN da aplicação, consulte [requisitos de acesso para Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Utilizar definições recomendadas pela Microsoft com linhas de base de segurança (pré-visualização pública) <!-- 2055484   -->

O Intune tem integração com outros serviços centrados na segurança, incluindo o Windows Defender ATP e o Office 365 ATP. Os clientes estão a pedir uma estratégia comum e um conjunto coeso de fluxos de trabalho de segurança de ponto a ponto em todos os serviços do Microsoft 365. O nosso objetivo é alinhar estratégias para desenvolver soluções que criem uma ponte entre operações de segurança e tarefas de administrador comuns. No Intune, pretendemos cumprir este objetivo através da publicação de um conjunto de "Linhas de base de segurança" recomendadas pela Microsoft (**Intune** > **Linhas de base de segurança**).  Um administrador pode criar políticas de segurança diretamente a partir dessas linhas de base e, em seguida, implementá-las aos respetivos utilizadores. Também pode personalizar as recomendações de melhores práticas para satisfazer as necessidades da sua organização. O Intune assegura que os dispositivos permanecem em conformidade com estas linhas de base e notifica os administradores de utilizadores ou dispositivos que não estejam em conformidade.

Esta funcionalidade está em pré-visualização pública, para que quaisquer perfis criados agora não serão movida aos modelos de linhas de base de segurança que estão em disponibilidade geral (GA). Não deve planeia utilizar estes modelos de pré-visualização no seu ambiente de produção.

Para saber mais sobre as linhas de base de segurança, veja [criar uma linha de base de segurança do Windows 10 no Intune](security-baselines-monitor.md).

Esta funcionalidade aplica-se a: Windows 10 e posterior

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Os não administradores podem ativar o BitLocker em dispositivos Windows 10 associados ao Azure AD<!-- 2147379   -->
Quando ativa as definições do BitLocker em dispositivos Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** para a plataforma > **proteção de ponto final** para o tipo de perfil > **encriptação Windows**), adicionar as definições do BitLocker. 

Esta atualização inclui uma nova definição de disco BitLocker para permitir que os usuários padrão (não-administradores) ativar a encriptação. 

Para ver as definições, aceda à [definições do Endpoint protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Verificar a conformidade do Configuration Manager <!-- 2192052  eepublished  -->
Esta atualização inclui uma nova definição de conformidade do System Center Configuration Manager (**conformidade do dispositivo** > **políticas** > **criar política**  >  **Windows 10 e posterior** > **compatibilidade do Configuration Manager**). O Configuration Manager envia sinais de conformidade ao Intune. Com esta definição, pode exigir a todos os sinais de Configuration Manager para retornar "em conformidade".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se todos os programas no dispositivo estão num Estado desconhecido, em seguida, o dispositivo está em conformidade no Intune.

[Compatibilidade do Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance) descreve esta definição.

Aplica-se a: Windows 10 e posterior

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalizar a imagem de fundo em dispositivos iOS supervisionados a utilizar um perfil de configuração do dispositivo <!-- 2809324   -->
Quando cria um perfil de configuração do dispositivo para dispositivos iOS, pode personalizar algumas funcionalidades (**configuração do dispositivo** > **perfis** > **Create perfil** > **iOS** para a plataforma > **funcionalidades do dispositivo** para tipo de perfil). Esta atualização inclui novos **papel de parede** definições que permitem que um administrador utilizar uma imagem de formato. png,. jpg ou. JPEG na tela inicial ou no ecrã de bloqueio. Estas definições de imagem de fundo aplicam-se apenas a dispositivos supervisionados. 

Para obter uma lista destas definições, consulte [definições de funcionalidade do dispositivo iOS](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Quiosque do Windows 10 está disponível em geral <!-- 3594661  -->
Nesta atualização, a funcionalidade de local público no Windows 10 e dispositivos posteriores está disponível em geral (GA). Para ver todas as definições que pode adicionar e configurar, consulte [definições de local público para o Windows 10 (e versões posteriores)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Partilha de contactos através de Bluetooth for removido no restrições de dispositivos > proprietário do dispositivo do Android Enterprise <!-- 3598396   -->
Quando cria um perfil de restrições de dispositivos para dispositivos Android Enterprise, há uma **contacto partilha através de Bluetooth** definição. Nesta atualização, o **contacto partilha através de Bluetooth** configuração seja removida (**configuração do dispositivo** > **perfis**  >   **Criar perfil** > **Android Enterprise** para a plataforma > **restrições de dispositivos > proprietário do dispositivo** para o tipo de perfil > **geral** ). 

O **contacto partilha através de Bluetooth** definição não é suportada para a gestão de proprietário do dispositivo do Android Enterprise. Quando esta definição for removida, não afeta quaisquer dispositivos ou inquilinos, mesmo que esta definição está ativada e configurada no seu ambiente.

Para ver a lista atual de definições, aceda à [definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades](device-restrictions-android-for-work.md).

Aplica-se a: Proprietário do dispositivo Android Enterprise

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Suporte de eliminação seletiva para WIP sem inscrição de dispositivos <!-- 1434452 -->
Windows Information Protection sem inscrição (WIP-PODEMOS) permite que os clientes proteger os dados empresariais em dispositivos Windows 10, sem a necessidade de inscrição de MDM completa. Assim que os documentos estão protegidos com um WIP-política de nós, os dados protegidos que podem ser apagados seletivamente por um administrador do Intune. Ao selecionar o utilizador e dispositivo e enviar um pedido de eliminação de dados, todos os dados que foi protegido por meio do WIP-política irá tornar-se inutilizável. No Intune, no portal do Azure, selecione **Aplicação móvel** > **Eliminação seletiva da aplicação**.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Novos registos operacionais e capacidade para enviar registos para serviços do Azure Monitor <!-- 3762211  -->
O Intune tem o log de auditoria interno que regista os eventos são feitas alterações. Esta atualização inclui novos recursos de Registro em log, incluindo: 
- Registos operacionais (pré-visualização) que mostram detalhes sobre os utilizadores e dispositivos inscritos, incluindo o êxito e tentativas falhadas.
- Os registos de auditoria e registos operacionais podem ser enviados para o Azure Monitor, incluindo contas de armazenamento, os hubs de eventos e do log analytics. Estes serviços permitem-lhe armazenar, utilizar a análise de como Splunk e QRadar e obtenha visualizações dos seus dados de registo.

[Enviar dados de registo para o armazenamento, os hubs de eventos ou do log analytics no Intune](review-logs-using-azure-monitor.md) fornece mais informações sobre esta funcionalidade.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorar mais ecrãs do Assistente de configuração num dispositivo DEP iOS <!-- 2687509  -->
Além dos ecrãs que atualmente pode ignorar, pode definir iOS dispositivos DEP para ignorar os ecrãs seguintes no Assistente de configuração, quando um utilizador inscreve o dispositivo: Apresenta tom, privacidade, migração Android, botão Home page, iMessage & FaceTime, integração, migração de Watch, aparência, tempo de tela, atualização de Software, a configuração SIM.
Para escolher que telas para ignorar, aceda a **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token > **Perfis** > Escolha um perfil > **propriedades** > **personalização do Assistente de configuração** > Escolha **ocultar**  para qualquer telas que pretende ignorar > **OK**.
Se criar um novo perfil ou editar um perfil, selecionado ignorar a necessidade de telas para sincronizar com o servidor de MDM da Apple. Os utilizadores podem emitir uma sincronização manual dos dispositivos, para que haja um atraso de escolher as alterações de perfil.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Aplicação do Android Enterprise-implementação de aplicações, <!-- 1171203 -->
Para dispositivos Android num não inscritos proteção política sem inscrição de aplicações (APP-PODEMOS) cenário de implementação, pode agora utilizar geridos Google Play para implementar aplicações da loja e aplicações aos utilizadores LOB. Especificamente, pode fornecer aos utilizadores finais uma experiência de instalação e de catálogo de aplicações que já não necessita que os utilizadores finais flexibilize as a postura de segurança dos seus dispositivos ao permitir que as instalações de origens desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Semana de 14 de Janeiro de 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Pré-visualização do suporte para dispositivos Android de empresa, totalmente geridos <!-- 1574342  -->
Intune agora suporta totalmente geridos os dispositivos Android, uma empresa cenário de "proprietário do dispositivo" em que dispositivos totalmente geridos pelo IT e são associados aos utilizadores individuais. Isto permite aos administradores gerir todo o dispositivo, aplicar um conjunto expandido de controlos de política indisponíveis para perfis de trabalho e restringe os utilizadores a instalar aplicações da Google Play gerido apenas. Para obter mais informações, consulte [configurar o Intune inscrição do Android totalmente dispositivos geridos](android-fully-managed-enroll.md) e [inscrever o seu dispositivos dedicados ou dispositivos totalmente gerenciados](android-dedicated-devices-fully-managed-enroll.md).  Tenha em atenção que esta funcionalidade está em pré-visualização. Algumas funcionalidades do Intune, tais como certificados, conformidade e acesso condicional, não estão atualmente disponíveis com o Android totalmente geridos os dispositivos dos utilizadores.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Semana de 7 de Janeiro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-app-pin----2298397---"></a>PIN da aplicação Intune <!-- 2298397 -->
O administrador de TI, pode agora configurar o número de dias que um utilizador final pode aguardar até ser preciso Alterar PIN da aplicação Intune. É a nova definição *reposição após número de dias do PIN* e está disponível no portal do Azure ao selecionar **Intune** > **aplicações de cliente**  >   **Políticas de proteção de aplicações** > **criar política** > **definições** > **aceder aos requisitos de**. Disponível para [iOS](app-protection-policy-settings-ios.md) e [Android](app-protection-policy-settings-android.md) dispositivos, esse recurso oferece suporte a um valor de número inteiro positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campos de relatórios de dispositivos do Intune <!-- 2748738 -->
O Intune fornece relatórios campos, incluindo o ID de registo de aplicação, fabricante do Android, modelo e versão de patch de segurança, bem como o modelo de iOS adicionais do dispositivo. No Intune, estes campos estão disponíveis, selecionando **aplicações de cliente** > **estado de proteção de aplicações** e escolha **relatório de proteção de aplicações: iOS, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão. 


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Modelos administrativos estão em pré-visualização pública e movido para o seu próprio perfil de configuração <!-- 3322847 -->

Modelos administrativos no Intune (**configuração do dispositivo** > **modelos administrativos**) estão atualmente em pré-visualização pública. Com esta atualização:

- Modelos administrativos incluem aproximadamente 300 definições que podem ser geridas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
- Modelos administrativos estão disponíveis em pré-visualização pública.
- Estiver a mover de modelos administrativos **configuração do dispositivo** > **modelos administrativos** para **configuração do dispositivo**  >   **Perfis** > **criar perfil** > no **plataforma**, selecione **Windows 10 e posterior** > no **perfil tipo**, escolha **modelos administrativos**.
- O relatório está ativado

Para ler mais sobre esta funcionalidade, aceda a [modelos do Windows 10 para configurar as definições de política de grupo](administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Utilizar S/MIME para encriptar e assinar vários dispositivos para um utilizador  <!-- 1333642 -->
Esta atualização inclui a encriptação de e-mails com S/MIME através de um novo perfil de certificado importado (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > selecione a plataforma > tipo de perfil **Certificados PKCS importados**). No Intune, pode importar certificados no formato PFX. O Intune pode enviar esses mesmos certificados para múltiplos dispositivos inscritos por um único utilizador. Isto também inclui:
- O perfil de e-mail nativo do iOS suporta a ativação da encriptação S/MIME através de certificados importados no formato PFX.
- A aplicação de e-mail nativa dos dispositivos Windows Phone 10 utiliza automaticamente o certificado S/MIME.
- Os certificados privados podem ser fornecidos a várias plataformas. No entanto, nem todas as aplicações de e-mail suportam S/MIME.
- Noutras plataformas, talvez seja necessário configurar manualmente a aplicação de e-mail para permitir o S/MIME.  
- As aplicações de e-mail que suportam a encriptação S/MIME conseguem obter certificados para a encriptação S/MIME de e-mails de uma forma que não é suportada por MDM, como a leitura a partir do arquivo de certificados do respetivo publicador.
Para obter mais informações sobre esta funcionalidade, consulte [descrição geral de S/MIME para assinar e encriptar e-mail](certificates-s-mime-encryption-sign.md).
Suportado no: Windows Phone 10, Windows, iOS, Android e macOS

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Novas opções para automaticamente se ligar e manter regras ao utilizar as definições de DNS no Windows 10 e dispositivos posteriores <!-- 1333665, 2999078 -->
No Windows 10 e dispositivos posteriores, pode criar um perfil de configuração de VPN que inclui uma lista de servidores DNS para resolver domínios, tal como contoso.com. Esta atualização inclui novas definições para resolução de nomes (**configuração do dispositivo** > **perfis** > **criar perfil** > Escolha  **Windows 10 e posterior** para a plataforma > Escolha **VPN** para o tipo de perfil > **definições de DNS** >**adicionar**): 
- **Ligar automaticamente**: Quando **ativado**, o dispositivo estabelece ligação automaticamente para a VPN quando um dispositivo entra em contacto com um domínio, introduza, por exemplo, contoso.com.
- **Persistente**: Por predefinição, todas as regras de tabela (NRPT) de política de resolução de nome estão ativas, desde que o dispositivo estiver conectado com este perfil VPN. Quando esta definição for **ativado** numa regra NRPT, a regra permanece ativa no dispositivo, mesmo quando desliga a VPN. A regra permanece até que o perfil VPN é removido ou até que a regra é manualmente removida, que pode ser feito com o PowerShell.
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) descreve as definições. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utilizar a deteção de rede fidedigna para perfis VPN em dispositivos Windows 10 <!-- 1500165 -->
Ao utilizar a deteção de rede fidedigna, pode impedir que os perfis VPN crie automaticamente uma ligação VPN quando o utilizador já se encontra numa rede fidedigna. Com esta atualização, pode adicionar sufixos DNS para ativar a deteção de rede fidedigna em dispositivos com Windows 10 e posterior (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Windows 10 e posterior** para a plataforma > **VPN** para tipo de perfil).
[Definições de VPN do Windows 10](vpn-settings-windows-10.md) lista as definições de VPN atuais.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gerir Windows Holographic for Business dispositivos usados por vários utilizadores <!-- 1907917, 1063203 -->
Atualmente, pode configurar definições do PC compartilhadas no Windows 10 e Windows Holographic for Business dispositivos com uma definição de OMA-URI personalizada. Com esta atualização, é adicionado um novo perfil para configurar definições de dispositivos partilhados (**configuração do dispositivo** > **perfis** > **criar perfil do**  >  **Windows 10 e posterior** > **dispositivos de vários utilizadores partilhado**).
Para saber mais sobre esta funcionalidade, aceda à [definições do Intune para gerir dispositivos partilhados](shared-user-device-settings.md).
Aplica-se a: Windows 10 e posterior, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Novas definições de atualização do Windows 10 <!--2626030  2512994  -->
Para sua [Cadências de atualização do Windows 10](windows-update-for-business-configure.md), pode configurar:
- **Comportamento de atualização automática** -utilize uma nova opção *repor para predefinição* para restaurar as definições de atualização automática original numa máquina de Windows 10 em computadores que executam o *atualização de Outubro de 2018*
- **Impedir o utilizador de atualizações do Windows a colocar em pausa** -configurar um novo Software de atualizações de definição que permite-lhe bloquear ou permitir que os utilizadores para a instalação da atualização de colocar em pausa a *definições* das suas máquinas. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>perfis de e-mail do iOS podem utilizar a encriptação e assinatura S/MIME <!-- 2662949 -->
Pode criar um perfil de e-mail que inclui definições diferentes. Esta atualização inclui definições de S/MIME que podem ser utilizadas para assinar e criptografar as comunicações por e-mail em dispositivos iOS (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > **E-Mail** para tipo de perfil).
[definições de configuração de e-mail do iOS](email-settings-ios.md) lista as definições.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algumas definições de BitLocker suportam a edição Windows 10 Pro<!-- 2727036 -->
Pode criar um perfil de configuração que define as definições do endpoint protection em dispositivos Windows 10, inclusive BitLocker. Esta atualização adiciona suporte para a edição Windows 10 Professional para algumas configurações de disco BitLocker. Para ver estas definições de proteção, aceda à [definições do Endpoint protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Configuração de dispositivos partilhados foi mudada para mensagem de ecrã de bloqueio para dispositivos iOS no portal do Azure<!-- 2809362 -->
Quando cria um perfil de configuração para dispositivos iOS, pode adicionar **configuração de dispositivos partilhados** definições para mostrar o texto específico no ecrã de bloqueio. Esta atualização inclui as seguintes alterações: 
- O **configuração de dispositivos partilhados** definições no portal do Azure são o nome mudadas para "Mensagem de ecrã de bloqueio (apenas supervisionada)" (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > Escolha **funcionalidades do dispositivo** para o tipo de perfil > **bloqueio Mensagem de ecrã**).
- Ao adicionar mensagens de ecrã de bloqueio, pode inserir um número de série, um nome de dispositivo ou outro valor específicos do dispositivo como uma variável no **informações da etiqueta de recursos** e **nota de rodapé de ecrã de bloqueio**. Por exemplo, pode introduzir `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` usando chaves de saída. [iOS tokens](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) apresenta uma lista de tokens disponíveis que podem ser utilizados.
[Definições para apresentar mensagens no ecrã de bloqueio](shared-device-settings-ios.md) lista as definições.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Novo App Store, visualização de documentos, definições de restrição de dispositivos de jogos adicionadas para dispositivos iOS <!-- 2827760-->
Na **configuração do dispositivo** > **perfis** > **criar perfil** > **iOS** para Plataforma > **restrições de dispositivos** para o tipo de perfil > **App Store, visualização de documentos, jogos**, são adicionadas as seguintes definições: Permitir que aplicações geridas escrever contactos para contas de não-gerenciado contactos aplicações permitir não gerido para ler contactos geridos de contas para ver estas definições, vá para de [restrições de dispositivos iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Novas definições de notificação, sugestões e keyguard para dispositivos de proprietário do dispositivo Android Enterprise <!-- 3201839 3201843 -->
Esta atualização inclui várias novas funcionalidades em dispositivos Android Enterprise quando em execução como proprietário do dispositivo. Para utilizar estas funcionalidades, aceda a **configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma**, escolha **Android Enterprise** > no **tipo de perfil**, escolha **proprietário do dispositivo só** > **dispositivo Restrições**.

Os novos recursos incluem: 

- Desative notificações de sistema do que mostra, incluindo a entrada chamadas, alertas do sistema, erros de sistema e muito mais.
- Sugere a ignorar a partir de tutoriais e dicas para aplicações que são abertas pela primeira vez.
- Desative keyguard avançada desbloquear as definições, tais como a câmara, notificações, impressão digital e muito mais.


Para ver as definições, aceda à [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Dispositivos de proprietário de dispositivos empresariais Android podem utilizar ligações de VPN AlwaysOn <!-- 3202194 -->
Nesta atualização, pode utilizar ligações VPN sempre ativada nos dispositivos de proprietário do dispositivo Android empresarial. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN sempre ativada no **configuração do dispositivo** > **perfis** > **criar perfil**  >   **Android enterprise** para a plataforma > **restrições de dispositivos** para o proprietário do dispositivo só > **conectividade** definições. Para ver as definições, aceda à [definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nova definição para processos de fim no Gerenciador de tarefas em dispositivos Windows 10 <!-- 3285177 --> 
Esta atualização inclui uma nova definição para terminar a processos usando o Gerenciador de tarefas em dispositivos Windows 10. Utilizar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma** , escolha **Windows 10** > no **tipo de perfil**, escolha **restrições de dispositivos** > **geral** definições), optar por permitir ou impedir que esta definição.
Para ver estas definições, aceda à [definições de restrição de dispositivos Windows 10](device-restrictions-windows-10.md).
Aplica-se a: Windows 10 e posterior


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mais mensagens de falha de restrição de inscrição <!-- 3111564 -->
Mensagens de erro mais detalhadas estão disponíveis quando restrições de inscrição não forem cumpridas. Para ver estas mensagens, aceda à **Intune** > **resolução de problemas** > e consulte a tabela de falhas de inscrição. Para obter mais informações, consulte a [lista de falhas de inscrição](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard de estado do inquilino  <!-- 1124854 -->
A nova [página de estado do inquilino](tenant-status.md) fornece um único local onde pode ver o estado e os detalhes relacionados para o seu inquilino.  O dashboard está dividido em quatro áreas:
- **Detalhes de inquilino** -apresenta informações que inclui o nome de inquilino e a localização, a autoridade de MDM, o total nos dispositivos inscritos no seu inquilino e a conta de sua licença. Esta secção também apresenta a versão atual do serviço para o seu inquilino.
- **Estado do conector** -apresenta informações sobre conectores disponíveis que configurou e também pode listar os que ainda não tiver ativado.  
   Com base no estado atual de cada conector, eles são sinalizados como bom estado de funcionamento, aviso ou mau estado de funcionamento. Selecione um conector para explorar e ver detalhes ou configurar as informações adicionais para o mesmo.
-  **Estado de funcionamento do serviço Intune** -apresenta detalhes sobre incidentes activos ou falhas para o seu inquilino. As informações nesta secção são obtidas diretamente a partir do Centro de mensagens do Office.
-  **Notícias do Intune** -exibe mensagens de Active Directory para o seu inquilino. As mensagens incluem opções como notificações quando o seu inquilino recebe as mais recentes funcionalidades do Intune.  As informações nesta secção são obtidas diretamente a partir do Centro de mensagens do Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Novo ajuda e suporte de experiência no Portal da empresa para Windows 10 <!-- 1488939-->
A nova página de ajuda de Portal da empresa e suporte ajuda os utilizadores a resolver problemas e pedir ajuda para problemas de acesso e aplicação. Na página nova, podem enviar por e-mail os detalhes de registo de diagnóstico e de erro e encontrar os detalhes de suporte técnico da sua organização. Eles também encontrará uma secção de FAQ com ligações para documentação relevante do Intune. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Ajuda e suporte da nova experiência para o Intune   <!-- #3307080 -->
Estamos a implementar a nova experiência de ajuda e suporte para todos os inquilinos ao longo do daqui a alguns dias. Esta nova experiência está disponível para o Intune e podem ser acessada ao utilizar os painéis do Intune no [portal do Azure](https://portal.azure.com/).
A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Estas soluções são oferecidas por meio de uma máquina com base na regra de algoritmo, orientado por utilizador de aprendizagem consultas. Além das orientações específicas do problema, utilize o novo fluxo de trabalho de criação de casos para abrir um incidente de suporte por e-mail ou telefone. Esta nova experiência substitui a experiência de ajuda e suporte anterior de um conjunto estático de opções previamente selecionadas que são baseiam-se a área da consola que estiver ao abrir a ajuda e suporte. Para obter mais informações, consulte [como obter suporte para o Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apps----1081941---"></a>Etiquetas de âmbito para aplicações <!-- 1081941 -->
Pode criar etiquetas de âmbito para limitar o acesso para aplicações e funções. Pode adicionar uma etiqueta de âmbito a uma aplicação para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso à aplicação. Atualmente, aplicações que adicionar ao Intune a partir do Google Play gerido ou aplicações adquiridas através do Apple Volume Purchase Program (VPP) não não possível atribuir etiquetas de âmbito (mas suporte virão no futuro). Para obter mais informações, consulte [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>Semana de 10 de Dezembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="updates-for-application-transport-security----748318---"></a>Atualizações de segurança de transporte de aplicações <!-- 748318 -->

O Microsoft Intune suporta Transport Layer Security (TLS) 1.2 + para fornecer encriptação de melhor em classe, para garantir que o Intune é mais seguro por padrão e para se alinhar com outros serviços Microsoft como o Microsoft Office 365. Para cumprir este requisito, portais de empresa do iOS e macOS irão impor requisitos de segurança de transporte de aplicações (ATS) atualizados da Apple, que também necessitam de TLS 1.2 +. A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Esta alteração irá afetar os clientes do Intune a utilizar as aplicações de Portal da empresa iOS e macOS. Para obter mais informações, consulte a [blogue de suporte do Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>O SDK da aplicação Intune irá suportar as chaves de encriptação de 256 bits <!-- 1832174 -->
O SDK da aplicação Intune para Android utiliza agora as chaves de encriptação de 256 bits quando a encriptação está ativada por políticas de proteção de aplicações. O SDK irá continuar a fornecer suporte de chaves de 128 bits para compatibilidade com o conteúdo e aplicações que utilizam versões mais antigas do SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Versão de atualização automática de Microsoft 4.5.0 necessária para dispositivos macOS <!-- 3503442 -->
Para continuar a receber atualizações para o Portal da empresa e outros aplicativos do Office, dispositivos macOS geridos pelo Intune tem de atualizar para a atualização automática do Microsoft 4.5.0. Os utilizadores poderão já ter esta versão para seus aplicativos do Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>O Intune necessita de macOS 10.12 ou posterior <!-- 2827778 -->
O Intune requer agora macOS versão 10.12 ou posterior. Dispositivos com versões anteriores do macOS não é possível utilizar o Portal da empresa para inscrição no Intune. Para receber suporte e novos recursos, os utilizadores tem de atualizar o dispositivo para macOS 10.12 ou posterior e atualize o Portal da empresa para a versão mais recente.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Semana de 26 de Novembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Desinstalar aplicações em dispositivos iOS supervisionados pertencente à empresa <!-- 1281677 -->

Pode remover todas as aplicações em dispositivos iOS supervisionados pertencente à empresa. Pode remover qualquer aplicação ao visar os grupos de utilizadores ou dispositivos com um tipo de atribuição **Desinstalar**. Para dispositivos iOS pessoais ou não supervisionados, continuará a poder remover apenas as aplicações que foram instaladas com o Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Transferir o conteúdo da aplicação Intune Win32 <!-- 2617320 -->
Windows 10 RS3 e aos clientes acima irá transferir o conteúdo da aplicação Intune Win32 usando um componente de Otimização da entrega no cliente Windows 10. Otimização da entrega fornece uma funcionalidade de ponto-a-ponto que ele está ativado por predefinição. Otimização da entrega pode ser configurada pela política de grupo e no futuro através de MDM do Intune. Para obter mais informações, consulte [otimização de entrega para o Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu de conteúdo dispositivos e aplicações utilizador final <!-- 2771453 -->
Os usuários finais agora pode utilizar o menu de contexto em aplicações e dispositivos para acionar ações comuns, como mudar o nome de um dispositivo ou a verificação de conformidade.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Definir o plano de fundo personalizado na aplicação Managed tela home page  <!-- 3041945 -->
Estamos a adicionar uma definição que permite-lhe personalizar a aparência de plano de fundo da aplicação gerida tela home page no Android Enterprise, várias aplicações, dispositivos de modo de local público.  Para configurar o **Fundo do URL personalizado**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.
Para ver as definições de local público, consulte [restrições de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Atribuição de política de proteção de aplicações, guardar e aplicar <!-- 3104570 -->
Agora tem um melhor controle sobre sua [atribuições de política de proteção de aplicações](app-protection-policies.md#deploy-a-policy-to-users). Quando seleciona *atribuições* para definir ou editar as atribuições de uma política, deve **guardar** sua configuração antes da alteração aplica-se. Uso **descartar** para limpar todas as alterações fizer sem guardar as alterações para a inclusão ou exclusão apresenta uma lista.  Ao exigir que guarde ou rejeição, apenas os utilizadores que pretende são atribuídos uma política de proteção de aplicações.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Novas definições do browser Microsoft Edge para Windows 10 e posterior <!-- 3174639 -->
Esta atualização inclui novas definições para ajudar a controlar e gerir o browser Microsoft Edge nos seus dispositivos. Para obter uma lista destas definições, consulte [restrição de dispositivos para Windows 10 (e versões posteriores)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Suportam a novas aplicações com políticas de proteção de aplicações <!-- 3330037 -->
Agora pode gerir as seguintes aplicações com [políticas de proteção de aplicações do Intune](app-protection-policies.md):
- Stream (iOS)
- Para fazer (Android, iOS)
- PowerApps (Android, iOS)
- Fluxo (Android, iOS)

Utilize políticas de proteção de aplicações para proteger a empresa transferência de dados e controle de dados para estas aplicações, como outra aplicações geridas por políticas do Intune. Nota: Se o fluxo ainda não estiver visível na consola, adicionar fluxo quando criar ou editar e políticas de proteção de aplicações. Para tal, utilize o **+ mais aplicações** opção e, em seguida, especifique a *ID de aplicação* do Flow no campo de entrada. Para Android utilizam *com.microsoft.flow*, e para iOS utilize *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>números de versão do iOS e macOS e números de compilação são mostrados <!-- 1892471 -->
Em **Conformidade do dispositivo** > **Conformidade do dispositivo**, são apresentadas as versões dos sistemas operativos iOS e macOS. Estas versões estão disponíveis para serem utilizadas nas políticas de conformidade. Esta atualização inclui o número de compilação, o que é configurável para ambas as plataformas.
Quando as atualizações de segurança são lançadas, normalmente, a Apple não altera o número da versão, mas atualiza o número de compilação. Ao utilizar o número de compilação numa política de conformidade, pode verificar facilmente se foi instalada uma atualização da vulnerabilidade.
Para utilizar esta funcionalidade, consulte [iOS](compliance-policy-create-ios.md#device-health) e [macOS](compliance-policy-create-mac-os.md#device-properties) políticas de conformidade.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Cadências de atualização estão a ser substituídas com as definições de otimização de entrega para o Windows 10 e posterior <!-- 2753807 -->
Otimização da entrega é um novo perfil de configuração para Windows 10 e posterior. Esta funcionalidade fornece uma experiência mais simplificada para fornecer atualizações de software para dispositivos na sua organização. Esta atualização também ajuda a fornecer as definições de cadências de atualização de novas e existentes com um perfil de configuração.
Para configurar um perfil de configuração de otimização de entrega, consulte [as definições de otimização do Windows 10 (e mais recente) entrega](delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Novas definições de restrição de dispositivos adicionadas a dispositivos iOS e macOS <!-- 2827760 -->
Esta atualização inclui novas definições para os seus dispositivos iOS e macOS que são lançadas com o iOS 12:

**definições do iOS**: 
- Gerais: Remoção de aplicações de bloco (apenas supervisionada)
- Gerais: Modo de bloco USB restrito (apenas supervisionado)
- Gerais: Forçar automática data e hora (apenas supervisionado)
- Palavra-passe: Bloquear a palavra-passe de preenchimento automático (apenas supervisionado)
- Palavra-passe: Bloquear pedidos de proximidade de palavra-passe (apenas supervisionados)
- Palavra-passe: Bloquear a partilha de palavra-passe (apenas supervisionado)

**definições do macOS**: 
- Palavra-passe: Bloquear o preenchimento automático de palavra-passe
- Palavra-passe: Bloquear pedidos de proximidade de palavra-passe
- Palavra-passe: Bloquear a partilha de palavra-passe

Para saber mais sobre estas definições, consulte [iOS](device-restrictions-ios.md) e [macOS](device-restrictions-macos.md) definições de restrição de dispositivos.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selecionadas aplicações registadas na página de estado de inscrição<!-- 2531007 -->
Pode escolher as aplicações que são controladas na página de estado de inscrição. Até que estas aplicações são instaladas, o utilizador não é possível utilizar o dispositivo. Para obter mais informações, consulte [configurar uma página de estado de inscrição](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Procurar dispositivos Autopilot por número de série <!--2595788 -->
Agora pode procurar por dispositivos Autopilot por número de série. Para tal, escolha **inscrição de dispositivos** > **inscrição Windows** > **dispositivos** > Escreva um número de série no **pesquisar por número de série** caixa > prima Enter.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Controlar a instalação do Office ProPlus <!--2620217 -->
Os usuários podem controlar o progresso da instalação [Office ProPlus](apps-add-office365.md) utilizando o [página de estado de inscrição](windows-enrollment-status.md). Para obter mais informações, consulte [configurar uma página de estado de inscrição](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Baixa em execução de licença de alertas para o VPP token expirar ou de Portal da empresa <!-- 2237572 -->
Se estiver a utilizar o Volume Purchase Program (VPP) para pré-aprovisionar o Portal da empresa durante a inscrição de DEP, o Intune irá alertá-lo quando o token VPP está prestes a expirar e quando há pouca as licenças para o Portal da empresa.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Programa de inscrição de macOS suporte para contas de Gestor de escola da Apple <!--3006133 -->
Intune agora suporta através do programa de inscrição de dispositivos em dispositivos macOS para contas de Gestor de escola da Apple.  Para obter mais informações, consulte [inscrever automaticamente dispositivos macOS com o Apple School Manager ou o programa de inscrição de dispositivos](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nova subscrição de dispositivo do Intune SKU <!--3312071-->
Para ajudar a reduzir o custo associado à gestão de dispositivos nas empresas, está agora disponível um novo SKU de subscrição baseado em dispositivos. Este SKU de dispositivos do Intune possui uma licença mensal por dispositivo. Os preços variam em função do programa de licenciamento. Está disponível diretamente por meio de centro de administração do Microsoft 365 e o [contrato Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Products da Microsoft e o contrato de serviços](https://www.microsoft.com/licensing/mpsa/default) (MPSA), [Microsoft Open Contratos](https://partner.microsoft.com/licensing/licensing-agreements), e [fornecedor de solução de Cloud](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Interromper temporariamente o modo de local público em dispositivos Android para efetuar alterações <!-- 3041935 -->
Ao utilizar dispositivos Android no modo de quiosque de múltiplas aplicações, um administrador de TI poderá ter de fazer alterações ao dispositivo. Esta atualização inclui novas definições de local público de várias aplicações que permite que um administrador de TI temporariamente a colocar em pausa a utilização de um PIN de modo de local público e obtenha acesso a todo o dispositivo.
Para ver as definições de local público, consulte [restrições de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Ativar o botão início virtual em dispositivos de local público do Android Enterprise  <!-- 3042021 -->
Uma nova definição permitirá que os utilizadores toquem num botão de tecla de função no respetivo dispositivo para alternar entre a aplicação Ecrã Inicial Gerido e outras aplicações atribuídas no respetivo dispositivo de quiosque de múltiplas aplicações. Esta definição é particularmente útil em cenários onde a aplicação de quiosque do utilizador não responde adequadamente ao botão "retroceder". Poderá configurar esta definição para dispositivos Android de utilização única, pertencentes à empresa. Para ativar ou desativar o **botão Home virtual**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.
Para ver as definições de local público, consulte [restrições de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Semana de 12 de Novembro de 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Suporte de Access Control (NAC) para Citrix SSO para iOS de rede <!-- 3259404 -->

Citrix lançou uma atualização para o Gateway da Citrix para permitir o controlo de acesso de rede (NAC) para Citrix SSO para iOS no Intune. Pode optar por incluir um ID de dispositivo de um perfil VPN no Intune e, em seguida, enviar este perfil para seus dispositivos iOS. Terá de instalar a atualização mais recente para o Gateway da Citrix para utilizar esta funcionalidade.

[Configurar definições de VPN em dispositivos iOS](vpn-settings-ios.md#base-vpn-settings) fornece mais informações sobre como usar o NAC, incluindo alguns requisitos adicionais. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Semana de 5 de novembro de 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Suporte para iOS 12 OAuth nos perfis de e-mail do iOS <!--2155106 -->

Os perfis de e-mail iOS do Intune suportam o Open Authorization (OAuth) do iOS 12. Para ver esta funcionalidade, crie um novo perfil (**Configuração do Dispositivo** > **Perfis** > **Criar perfil**  >  **iOS** para a plataforma > **E-mail** para o tipo de perfil) ou atualize um perfil de e-mail iOS existente. Se ativar o OAuth num perfil que já foi implementado para utilizadores, será pedido aos utilizadores que autentiquem e transfiram novamente o respetivo e-mail.

Pode obter mais informações sobre como utilizar o OAuth num perfil de e-mail em [iOS email profiles](email-settings-ios.md) (Perfis de e-mail iOS).

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Autopilot suporte híbrido do Azure Active Directory dispositivos associados (pré-visualização) <!-- 1048100-->
Agora pode configurar dispositivos associados ao Azure Active Directory híbrido com o Autopilot. Os dispositivos têm de ser associados à rede da sua organização para utilizar a funcionalidade Autopilot híbrida. Para obter mais informações, veja [Implementar dispositivos associados ao Azure Active Directory híbrido com o Intune e o Windows Autopilot](windows-autopilot-hybrid.md).
Esta funcionalidade será implementada para a base de utilizadores nos próximos dias. Assim, poderá não conseguir seguir estes passos até que a mesma seja implementada na sua conta.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Semana de 29 de outubro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Exigir PIN não biométrica após um tempo limite especificado <!-- 1506985 -->
Ao exigir um PIN não biométrico após um tempo limite especificado pelo administrador, o Intune fornece segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições afetam os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições permitem que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, ao eliminar os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações do cliente** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas. Para obter informações sobre as definições de acesso, veja as [definições do iOS](app-protection-policy-settings-ios.md#access-requirements) e as [definições do Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Definições de transferência de dados de aplicação do Intune no iOS MDM nos dispositivos inscritos <!-- 2244713 -->
Pode separar o controlo das definições de transferência de dados de aplicações do Intune em dispositivos iOS inscritos na MDM da especificação da identidade do utilizador inscrito, também conhecida como Nome Principal de Utilizador (UPN). Os administradores que não utilizarem o IntuneMAMUPN não notarão a existência de uma alteração de comportamento. Quando esta funcionalidade estiver disponível, os administradores que utilizam o IntuneMAMUPN para controlar o comportamento de transferência de dados em dispositivos inscritos devem rever as novas definições e atualizar as respetivas definições das aplicações conforme necessário.

#### <a name="windows-10-win32-apps----2617325---"></a>Aplicações de Win32 do Windows 10 <!-- 2617325 -->
Pode configurar as suas aplicações Win32 para que sejam instaladas no contexto de utilizador para utilizadores individuais ou para todos os utilizadores do dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Aplicações Windows Win32 e scripts do PowerShell <!-- 2617330 -->
Os utilizadores finais já não necessitam de ter sessão iniciada no dispositivo para instalarem aplicações Win32 ou executarem scripts do PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Resolução de problemas de instalação da aplicação de cliente <!-- 1363711 -->
Pode resolver problemas relativos ao sucesso da instalação de aplicações cliente ao rever a coluna intitulada **Instalação da aplicação** e o painel **Resolução de Problemas**. Para ver o painel **Resolução de Problemas**, selecione **Resolução de Problemas** em **Ajuda e suporte**, no portal do Intune.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Suporte de controlo de acesso de rede em clientes VPN de iOS <!-- 1333693 -->
Com esta atualização, há uma nova definição para ativar o Controlo de Acesso à Rede (NAC) quando criar um perfil de configuração de VPN para Cisco AnyConnect, F5 Access e Citrix SSO para iOS. Esta definição permite que o ID do NAC do dispositivo seja incluído no perfil de VPN. Atualmente, não existem clientes VPN nem soluções de parceiro de NAC que suportem este novo ID do NAC, mas iremos mantê-lo informado através da nossa [mensagem de blogue de suporte](ttps://aka.ms/iOS12_and_vpn) quando existirem.

Para utilizar o NAC, precisará de:
1. Optar ativamente por permitir que o Intune inclua IDs de dispositivos em perfis de VPN
2. Atualizar o software/firmware do seu fornecedor de NAC através da orientação fornecida diretamente pelo seu fornecedor de NAC

Para obter informações sobre esta definição num perfil de VPN do iOS, veja [Adicionar definições de VPN em dispositivos iOS no Microsoft Intune](vpn-settings-ios.md). Para obter mais informações sobre o controlo de acesso à rede, veja [Integração de controlo de acesso à rede (NAC) com o Intune](network-access-control-integrate.md). 

Aplica-se a: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Remover um perfil de e-mail de um dispositivo, mesmo quando o perfil tem apenas um e-mail <!-- 1818139 -->
Anteriormente, não podia remover um perfil de e-mail de um dispositivo *se* fosse o único perfil de e-mail. Com esta atualização, este comportamento muda. Agora pode remover um perfil de e-mail, mesmo que seja o único perfil de e-mail no dispositivo. Para obter detalhes, veja [Adicionar definições de e-mail a dispositivos com o Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts do PowerShell e AAD <!-- 2309469 -->
Os scripts do PowerShell no Intune podem ser direcionados a grupos de segurança de dispositivo do AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Novo "tipo obrigatório de palavra-passe" a configuração padrão para Android, Android enterprise<!-- 2649963 -->
Ao criar uma nova política de conformidade (**Intune** > **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android** ou **Android Enterprise** para a Plataforma > Segurança do Sistema), o valor predefinido para **Tipo de palavra-passe necessária** muda:

De: Predefinição do dispositivo para: Pelo menos numérica

Aplica-se a: Android, Android Enterprise

Para ver estas definições, aceda a [Android](compliance-policy-create-android.md) e [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utilizar uma chave pré-partilhada num perfil de Wi-Fi do Windows 10 <!-- 2662938 -->
Com esta atualização, poderá utilizar uma chave pré-partilhada (PSK) com o protocolo de segurança WPA/WPA2-Pessoal para autenticar um perfil de configuração de Wi-Fi para o Windows 10. Na atualização de outubro de 2018 para dispositivos com o Windows 10, também pode especificar a configuração de custos para uma rede com tráfego limitado.

Atualmente, tem de importar um perfil de Wi-Fi ou criar um perfil personalizado para utilizar uma chave pré-partilhada. O artigo [Definições de Wi-Fi para o Windows 10](wi-fi-settings-windows.md) indica as definições atuais. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Remover certificados PKCS e SCEP dos seus dispositivos <!-- 3218390 -->
Em alguns cenários, houve certificados PKCS e SCEP que permaneceram em dispositivos, mesmo quando se procedeu à remoção de uma política de um grupo ou à eliminação de uma implementação de configuração ou de conformidade, ou quando um administrador atualizou um perfil SCEP ou PKCS existente. Esta atualização altera o comportamento. Há alguns cenários onde os certificados PKCS e SCEP são removidos de dispositivos e outros cenários em que estes certificados permanecem no dispositivo. Para obter informações sobre estes cenários, veja [Remover certificados SCEP e PKCS no Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Utilizar o controlador de chamadas em dispositivos macOS para conformidade <!-- 2504381 -->
Esta atualização inclui o controlador de chamadas para macOS para avaliar dispositivos quanto à conformidade. Para definir o Controlador de Chamadas, tem de [Adicionar uma política de conformidade para dispositivos macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="enrollment-abandonment-report----1382924---"></a>Relatório de abandonment de inscrição <!-- 1382924 -->
Um novo relatório que fornece detalhes sobre inscrições abandonadas está disponível em **Inscrição de dispositivos** > **Monitorização**. Para obter mais informações, veja [Relatório de abandono do Portal da Empresa](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Novos termos do Azure Active Directory da funcionalidade de utilização <!-- 2870393 -->
O Azure Active Directory tem uma funcionalidade de termos de utilização que pode utilizar em vez dos termos e condições do Intune existentes. A funcionalidade de termos de utilização do Azure AD proporciona mais flexibilidade relativamente aos termos a apresentar e a quando o fazer, melhor suporte para a localização, mais controlo sobre a forma como os termos são compostos e relatórios melhorados. A funcionalidade de termos de utilização do Azure AD necessita do Azure Active Directory Premium P1, que também faz parte do conjunto Enterprise Mobility + Security E3. Para saber mais, veja o artigo [Gerir os termos e condições da sua empresa para o acesso dos utilizadores](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Suporte ao modo do proprietário do dispositivo Android <!--3188762-->
Para o Knox Mobile Enrollment da Samsung, o Intune suporta agora inscrição de dispositivos para o modo de gestão Proprietário de Dispositivo Android. Os utilizadores em redes Wi-Fi ou redes móveis podem inscrever com apenas alguns toques os respetivos dispositivos quando os ligarem pela primeira vez. Para obter mais informações, consulte [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscrever automaticamente dispositivos Android através do Knox Mobile Enrollment da Samsung).

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="new-settings-for-software-updates------1907869---"></a>Novas definições de atualizações de Software   <!-- 1907869 -->  
- Agora, pode configurar algumas notificações aos utilizadores finais alerta sobre reinícios necessários para concluir a instalação das atualizações de software mais recente.   
- Agora, pode configurar uma mensagem de aviso de reinício para reinícios do que acontecer fora do horário de trabalho, que oferece suporte a cenários BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Grupo de dispositivos inscritos pelo Windows Autopilot por ID do correlacionador <!-- 2075110 -->
O Intune suporta agora o agrupamento de dispositivos Windows por um ID de correlacionador se os mesmos forem inscritos com o [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), através do Configuration Manager. O ID de correlacionador é um parâmetro do ficheiro de configuração do Autopilot. O Intune irá definir automaticamente o [atributo enrollmentProfileName de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) para que seja igual a "OfflineAutopilotprofile-<correlator ID>". Isto permite que sejam criados grupos dinâmicos do Azure AD arbitrários com base no ID de correlacionador, através do atributo enrollmentprofileName para inscrições do Autopilot offline. Para obter mais informações, veja [Windows Autopilot for existing devices](enrollment-autopilot.md#windows-autopilot-for-existing-devices) (Windows Autopilot para dispositivos existentes).

#### <a name="intune-app-protection-policies----2984657---"></a>Políticas de proteção de aplicações do Intune <!-- 2984657 -->
As políticas de proteção de aplicações do Intune permitem-lhe configurar várias definições de proteção de dados para aplicações protegidas pelo Intune, como o Microsoft Outlook e o Microsoft Word. Alterámos o aspeto e funcionalidade destas definições tanto para [iOS](app-protection-policy-settings-ios.md) como para [Android](app-protection-policy-settings-android.md), de modo a facilitar a localização de definições individuais. Existem três categorias de definições de política:
- **Reposicionamento de dados**: este grupo inclui os controlos de prevenção de perda de dados (DLP), como as restrições das operações de cortar, copiar, colar e guardar como. Estas definições determinam como os utilizadores interagem com os dados nas aplicações.
- **Requisitos de acesso**: este grupo contém as opções de PIN por aplicação que determinam como o utilizador final utiliza as aplicações num contexto de trabalho.  
- **Iniciação condicional**: este grupo guarda definições como as definições de SO mínimo, de deteção de dispositivos desbloqueados por jailbreak ou rooting e de períodos de tolerância offline.  
  
A funcionalidade das definições não muda, mas será mais fácil encontrá-las quando trabalhar no fluxo de autoria de política.

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>O Intune suportará um tamanho de pacote máximo de 8 GB para aplicações LOB <!-- 1727158 -->
O Intune aumentou a dimensão máxima dos pacotes para 8 GB para as aplicações de linha de negócio (LOB). Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Adicionar imagem de marca personalizada para a aplicação Portal da empresa <!-- 1916266 -->
Enquanto administrador do Microsoft Intune, pode carregar uma imagem de marca personalizada que será apresentada como uma imagem de fundo na página de perfil do utilizador, na aplicação Portal da Empresa para iOS. Para obter mais informações sobre como configurar a aplicação Portal da Empresa, veja [Como configurar a aplicação Portal da Empresa do Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune manterá o idioma localizado do Office, ao atualizar o Office em máquinas dos utilizadores finais <!-- 2971030 -->
Quando o Intune instalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI. Para obter mais informações, veja [Atribuir aplicações do Office 365 a dispositivos Windows 10 com o Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nova experiência de suporte do Intune no portal de gestão de dispositivos do Microsoft 365 <!-- 3076965 -->
Estamos a implementar uma nova experiência de Ajuda e Suporte para o Intune no [portal de Gestão de Dispositivos do Microsoft 365]( http://devicemanagement.microsoft.com). A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Estas soluções são disponibilizadas através de um algoritmo de aprendizagem automática baseado em regras, alimentado pelas perguntas dos utilizadores.  

Para além das orientações específicas de problemas, pode utilizar o novo fluxo de trabalho de criação de processos para abrir um processo de suporte por e-mail ou telefone.  

Para os clientes que fazem parte da implementação, esta nova experiência substitui a experiência atual de Ajuda e Suporte de um conjunto estático de opções previamente selecionadas que se baseiam na área da consola que é apresentada ao abrir a Ajuda e Suporte.  

*Esta nova experiência de Ajuda e Suporte está a ser implementada apenas para alguns inquilinos e está disponível no portal de Gestão de Dispositivos. Os participantes desta nova experiência são selecionados aleatoriamente a partir dos inquilinos do Intune disponíveis. Serão adicionados novos inquilinos à medida que expandimos a implementação.*  

Para obter mais informações, consulte [ajuda e suporte a experiência](get-support.md#help-and-support-experience) em como obter suporte para o Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Módulo do PowerShell para o Intune – pré-visualização disponível <!-- 951068 -->
Está agora disponível para pré-visualização no [GitHub]( https://aka.ms/intunepowershell) um novo módulo do PowerShell que fornece suporte para a API do Intune através do Microsoft Graph. Para obter mais informações sobre como utilizar este módulo, veja o ficheiro LEIA-ME nessa localização. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Semana de 15 de outubro de 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Pedido de PIN quando alterar as impressões digitais ou ID se deparam num dispositivo iOS  <!-- 2637704  -->
Agora é pedido um PIN aos utilizadores após fazerem alterações biométricas no respetivo dispositivo iOS. Isto inclui alterações ao nível de impressões digitais ou do Face ID registados. A altura em que o pedido é apresentado depende da configuração do tempo limite *Verificar novamente os requisitos de acesso após (minutos)* .  Quando não está definido nenhum PIN, é pedido ao utilizador para configurar um. 
 
Esta funcionalidade só está disponível para iOS e requer a participação de aplicações que integrem o SDK da aplicação Intune para iOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>Semana de 1 de outubro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Acesso às propriedades de perfil de chave a utilizar a aplicação portal da empresa <!-- 772203 -->
Os utilizadores finais podem agora aceder a ações e propriedades de conta fundamentais, tais como a reposição de palavra-passe, a partir da aplicação Portal da Empresa. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>teclados 3rd party podem estar bloqueados por definições de aplicações no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune podem bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, estão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Acesso de conta de utilizador de aplicações do Intune em dispositivos Android e iOS geridos <!-- 1248496 -->
Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>IOS do Outlook e política de configuração de aplicação Android <!--1828527 -->
Agora pode criar uma política de configuração da aplicação Outlook para iOS e Android para os utilizadores no local que tiram partido da autenticação Básica com o protocolo ActiveSync. Serão adicionadas outras definições de configuração à medida que forem ativadas para o Outlook para iOS e Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensões de ficheiros de aplicações de linha de negócio (LOB) Windows <!-- 1884873 -->
As extensões de ficheiro para aplicações LOB para Windows agora incluirão *. msi*, *. AppX*, *. appxbundle*, *.msix*, e *. msixbundle*. Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações do cliente** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** é apresentado, o qual lhe permite selecionar o **Tipo de aplicação**. Para aplicações LOB do Windows, selecione o tipo de aplicação **Linha de negócio**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação com a extensão adequada.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Implementação de aplicações do Windows 10 com o Intune <!-- 2309001 -->
Com base no suporte existente para aplicações de linha de negócio (LOB) e aplicações da Microsoft Store para Empresas, os administradores podem utilizar o Intune para implementar a maioria das aplicações existentes da respetiva organização nos utilizadores finais em dispositivos com o Windows 10. Os administradores podem adicionar, instalar e desinstalar aplicações para utilizadores do Windows 10 numa variedade de formatos, como MSIs, Setup.exe ou MSP. O Intune irá avaliar as regras de requisitos antes de transferir e instalar, e irá notificar os utilizadores finais sobre o estado ou os requisitos de reinício através do Centro de Ação do Windows 10. Esta funcionalidade irá efetivamente ajudar as organizações interessadas em mudar esta carga de trabalho para o Intune e a cloud. Esta funcionalidade está atualmente em pré-visualização pública e esperamos acrescentar-lhe novas funcionalidades relevantes durante os próximos meses. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Definições de política de proteção (aplicação) para dados da web da aplicação <!-- 2662995 -->
As definições da política APP para conteúdos da Web em dispositivos Android e iOS serão atualizadas para processar melhor ligações Web HTTP e HTTPS, bem como a transferência de dados através de Ligações Universais do iOS e Ligações de Aplicações do Android. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu de conteúdo dispositivos e aplicações utilizador final <!-- 2771453 -->
Os utilizadores finais podem agora utilizar o menu de contexto em aplicações e dispositivos para acionar ações comuns, tais como mudar o nome de um dispositivo ou realizar verificações de conformidade. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Atalhos de teclado do Portal da Empresa do Windows <!-- 2771518 -->
Os utilizadores finais poderão agora ativar ações de aplicação e de dispositivo no Portal da Empresa do Windows com atalhos de teclado (aceleradores).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Criar os sufixos DNS nos perfis de configuração de VPN em dispositivos com Windows 10<!-- 1333668 -->
Quando criar um perfil de configuração de um dispositivo VPN (**Configuração do dispositivo** > **Perfis** > **Criar perfil** >  plataforma **Windows 10 e versões posteriores** > tipo de perfil **VPN**), terá de introduzir algumas definições de DNS. Com esta atualização, também pode introduzir múltiplos **sufixos DNS** no Intune. Quando utilizar sufixos DNS, pode procurar um recurso de rede através do respetivo nome abreviado, em vez do nome de domínio completamente qualificado (FQDN). Esta atualização também permite alterar a ordem dos sufixos DNS no Intune.
O artigo [Definições de VPN do Windows 10](vpn-settings-windows-10.md#dns-settings) indica as definições de DNS atuais.
Aplica-se a: Dispositivos com o Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Suporte para VPN sempre ativa para perfis de trabalho do Android enterprise <!-- 1333705 -->
Nesta atualização, pode utilizar ligações VPN Sempre Ativada em dispositivos Android Enterprise com perfis de trabalho geridos. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN Sempre Ativada nas definições **Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Android Enterprise** para a plataforma > **Restrições do dispositivo** > **Conectividade**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emitir certificados SCEP para dispositivos sem utilizador <!-- 1744554 -->
De momento, os certificados são emitidos para utilizadores. Com esta atualização, é possível emitir certificados SCEP para dispositivos, incluindo para dispositivos sem utilizador, tais como quiosques (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Certificado SCEP** para o perfil). Outras atualizações incluem o seguinte:
- A propriedade **Requerente** nos perfis SCEP é agora uma caixa de texto personalizada e pode incluir novas variáveis. 
- A propriedade **Nome alternativo do requerente (SAN)** nos perfis SCEP tem agora um formato de tabela e pode incluir novas variáveis. Na tabela, os administradores podem adicionar um atributo e preencher o valor numa caixa de texto personalizada. O SAN suportará os seguintes atributos: 
  - DNS
  - Endereço de e-mail
  - UPN

  Estas variáveis novas podem ser adicionadas com texto estático numa caixa de texto de valor personalizado. Por exemplo, o atributo de DNS pode ser adicionado como `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > As chavetas, os pontos e vírgulas e as barras verticais " { } ; | " não funcionarão no texto estático do SAN. As chavetas só podem delimitar uma das novas variáveis de certificado de dispositivo para que sejam aceites em `Subject` ou `Subject alternative name`. 

Variáveis de certificado de dispositivo novas:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` só funciona em dispositivos com Windows e dispositivos associados a um domínio. 
>  -  Quando especificar as propriedades do dispositivo, tais como o IMEI, o Número de Série e o Nome de Domínio Completamente Qualificado, no requerente ou no SAN de um certificado de dispositivo, tenha em atenção que estas propriedades podem ser falsificadas por uma pessoa que tenha acesso ao dispositivo. 

O artigo [Criar um perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) indica as variáveis atuais durante a criação de um perfil de configuração SCEP. 

Aplica-se a: Windows 10 e posterior e iOS, suportado para Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloquear remotamente dispositivos uncompliant <!-- 2064495 -->
Quando um dispositivo não estiver em conformidade, poderá criar uma ação na política de conformidade que bloqueie remotamente o dispositivo. No Intune > **Conformidade do dispositivo**, crie uma nova política ou selecione uma política existente > **Propriedades**. Selecione **Ações para não conformidade** > **Adicionar** e selecione a opção para bloquear remotamente o dispositivo.
Suportado no: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e posterior 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Windows 10 e posteriores aperfeiçoamentos de perfil de local público no portal do Azure <!-- 2748224 -->
Esta atualização inclui as seguintes melhorias no perfil de configuração de dispositivos de Quiosque do Windows 10 (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Pré-visualização de quiosque** para o tipo de perfil): 
- Atualmente, pode criar múltiplos perfis de quiosque no mesmo dispositivo. Com esta atualização, o Intune suportará apenas um perfil de quiosque por dispositivo. Se continuar a necessitar de múltiplos perfis de quiosque num só dispositivo, pode utilizar um URL personalizado.
- Num perfil **Quiosque de várias aplicações**, pode selecionar o tamanho e a ordem dos mosaicos das aplicações para o **Esquema do menu Iniciar** na grelha das aplicações. Se preferir um nível superior de personalização, pode avançar para carregar um ficheiro XML.
- As definições do Browser de Quiosque estão a passar para as definições de **Quiosque**. Neste momento, as definições do **browser de Quiosque** têm a sua própria categoria no portal do Azure.
Aplica-se a: Windows 10 e posterior




### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Aplicar Autopilot inscritos de perfil para dispositivos Windows 10, não se cadastrou para Autopilot <!-- 1558983 -->
Pode aplicar um perfil do Autopilot a dispositivos com o Windows 10 inscritos e que ainda não tenham sido registados no Autopilot. No perfil do Autopilot, selecione a opção **Converter todos os dispositivos visados para o Autopilot** para registar automaticamente dispositivos não Autopilot com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot aprovisioná-lo-á.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Criar e atribuir vários perfis de página de estado de inscrição a grupos do Azure AD <!-- 2526564 -->
Agora, pode [criar e atribuir](windows-enrollment-status.md) múltiplos perfis de Página de Estado de Inscrição a grupos do Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migração a partir do registo de aparelho da Apple o gerente de negócios no Intune <!--2748613-->
O Apple Business Manager (ABM) funciona no Intune, pelo que pode atualizar versão do software da sua conta do Programa de Registo de Aparelho (DEP) para o ABM. No Intune, o processo é o mesmo. Para atualizar a versão do software da sua conta Apple do DEP para o ABM, aceda a [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Separadores de estado de alerta e a inscrição na página de descrição geral de inscrição do dispositivo <!--2748656-->
Os alertas e os erros ao nível das inscrições aparecem agora em separadores diferentes da página Descrição geral de inscrições de dispositivos.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restringe a aplicações e bloquear o acesso aos recursos da empresa em dispositivos Android <!-- 2451462  -->  
Em **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android**  > **Segurança do Sistema**, há uma nova definição na secção *Segurança do Dispositivo* chamada **Aplicações restritas**. A definição **Aplicações restritas** utiliza uma política de conformidade para bloquear o acesso aos recursos da empresa, caso determinadas aplicações estejam instaladas no dispositivo. O dispositivo é considerado não compatíveis até que as aplicações restritas sejam removidas do dispositivo.
Aplica-se a: 
- Android

<!-- ########################### -->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
