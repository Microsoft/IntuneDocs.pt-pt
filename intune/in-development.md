---
title: No desenvolvimento – Microsoft Intune
titleSuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e9a640a343efd4ad786d7697439531de3cd4ed3
ms.sourcegitcommit: 2f32f6d2129bc10cc4a02115732e995edceb37d6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66828959"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>No desenvolvimento do Microsoft Intune – Junho de 2019

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
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- ***********************************************-->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Os utilizadores de dispositivos, podem ver todas as aplicações geridas que tenham instalado ou tentou instalar <!-- 2352913 -->
Portal da empresa para Windows listará todas as aplicações geridas (tanto necessárias quanto disponíveis) que estão instaladas no dispositivo de um utilizador. Os utilizadores serão capazes de vista de tentativa e pendentes instalações de aplicações e respetivos Estados atuais. Se sua organização não torne as aplicações necessárias ou disponíveis, os utilizadores verão uma mensagem que explica que não existem aplicações da empresa foram instaladas. Os utilizadores também serão capazes de classificar ou filtrar as suas aplicações por Estado da instalação.

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configurar o browser tem permissão para ligar aos dados da organização <!-- 3145939 -->
Intune App Protection políticas (aplicação) em dispositivos Android e iOS permitirá a transferência Org ligações da web para um determinado navegador, além do Browser gerido do Intune ou do Microsoft Edge.  Para obter mais informações sobre a aplicação, consulte [quais são as políticas de proteção de aplicações?](app-protection-policy.md).

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>Instalado a página de aplicações no site do Portal da empresa  <!-- 4224326 -->
O [site do Portal da empresa](https://portal.manage.microsoft.com/) incluirá uma nova página para mostrar os utilizadores todas as aplicações que tenham sido instaladas no respetivo dispositivo. Esta lista inclui as aplicações disponíveis e as aplicações necessárias pela sua organização. Nesta página, os utilizadores serão capazes de ver os Estados de instalação e requisitos das aplicações nos respetivos dispositivos. Para obter mais informações sobre o site do Portal da empresa, consulte [através do site do Portal da empresa do Intune](/intune-user-help/using-the-intune-company-portal-website.md) e [como configurar a aplicação Portal da empresa do Microsoft Intune](company-portal-app.md).

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>Chamar operações de leitura a partir de uma aplicação sem credenciais de utilizador do Graph API <!-- 4655885 -->
Aplicações poderão chamar operações com a identidade da aplicação sem credenciais de utilizador de leitura Graph API do Intune. Para obter mais informações, consulte [obter acesso sem um utilizador](https://docs.microsoft.com/graph/auth-v2-service).

<!-- ***********************************************-->
### <a name="device-configuration"></a>Configuração do dispositivo


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Suporte para perfis de IKEv2 VPN para iOS <!-- 1943438 -->
Poderá criar perfis VPN para o cliente VPN nativo iOS utilizando o protocolo IKEv2. IKEv2 é um novo tipo de ligação no **configuração do dispositivo** > **perfis** > **criar perfil** > **iOS**  para a plataforma > **VPN** para o tipo de perfil > **definições**.

Estes perfis VPN configurar o cliente VPN nativo. Portanto, não existem aplicações de cliente VPN forem instaladas ou enviada por push para dispositivos geridos. Esta funcionalidade requer a dispositivos inscritos no Intune (inscrição de MDM).

Para ver as definições atuais do VPN, pode configurar, aceda à [definições de VPN configurar em dispositivos iOS no Microsoft Intune](vpn-settings-ios.md).

Aplica-se a: iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>Configurar definições para extensões de kernel em dispositivos macOS <!-- 20430240 -->
Em dispositivos macOS, pode criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > escolher **macOS** para a plataforma). Uma atualização futura irá incluir um novo grupo de definições que permitem configurar e utilizar extensões de kernel nos seus dispositivos.

Aplica-se a: macOS 10.13.2 e posterior

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Suporte de linha de base para a palavra-chave de pesquisa  <!-- 3082036         -->
Ao criar ou editar um perfil de linha de base de segurança, em breve será capaz de usar *pesquisa* para filtrar as definições que são apresentados na consola do.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilize "regras de aplicabilidade" quando criar perfis de configuração de dispositivo Windows 10 <!-- 2549910 -->
Criar perfis de configuração de dispositivo Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma). Poderá criar uma **regra de aplicabilidade** para que o perfil apenas se aplica a uma edição específica ou uma versão específica. Por exemplo, criar um perfil que permite que algumas configurações de disco BitLocker. Depois de adicionar o perfil, utilize uma regra de aplicabilidade para que o perfil apenas se aplica a dispositivos com o Windows 10 Enterprise.

Aplica-se a: 
- Windows 10 e posterior

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>As aplicações da loja definição apenas para dispositivos Windows 10 inclui mais opções de configuração <!-- 2697002  -->

Quando cria um perfil de restrições de dispositivos para dispositivos Windows, pode utilizar o **aplicações da loja só** definição para que os utilizadores instalarem apenas aplicações da Store de aplicação do Windows (**configuração do dispositivo**  >  **Perfis** > **criar perfil** > **Windows 10 e posterior** para a plataforma > **dispositivo restrições** para tipo de perfil). Numa atualização futura, esta definição será expandida para suportar mais opções. 

Para ver as definições atuais, aceda à [definições de dispositivos de 10 (e versões posteriores) do Windows para permitir ou restringir funcionalidades com o Intune](device-restrictions-windows-10.md#app-store).

Aplica-se a: Windows 10 e posterior

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Implementar vários perfis de dispositivo de extensões das riscas das mobilidade num dispositivo, o mesmo grupo de utilizadores ou o mesmo grupo de dispositivos <!-- 4089955 -->
No Intune, pode utilizar extensões de mobilidade as riscas das (MX) num perfil de configuração do dispositivo para personalizar as definições ou adicionar as definições não incorporadas ao Intune. Atualmente, pode implementar um perfil para um único dispositivo. Numa atualização futura, poderá implementar vários perfis para:

- O mesmo grupo de utilizadores
- O mesmo grupo de dispositivos
- Um único dispositivo

[Utilizar e gerir as riscas das dispositivos com as riscas das extensões de mobilidade no Microsoft Intune](android-zebra-mx-overview.md) mostra como utilizar MX no Intune.

Aplica-se a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Algumas definições de local público em dispositivos iOS são definidas utilizando um "Bloco" substituir "Permitir" <!-- 4404075  -->
Quando cria um perfil de restrições de dispositivos em dispositivos iOS (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **quiosque**), define o **bloqueio automático**, **Comutador do toque**, **rotação do ecrã**, **botão de suspensão do ecrã**, e **botões de Volume**. 

Atualmente, estas definições são configuradas usando **permitir** (bloqueia a funcionalidade) ou **não configurada** (permite que o recurso). Numa atualização futura, os valores serão **bloco** (bloqueia a funcionalidade) ou **não configurada** (permite que o recurso).

Para ver as definições atuais, aceda à [definições de dispositivos iOS para permitir ou restringir funcionalidades](device-restrictions-ios.md). 

Aplica-se a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>Utilize o Face ID para a autenticação de palavra-passe em dispositivos iOS <!-- 4490704  -->
Quando cria um perfil de restrições de dispositivos para dispositivos iOS, pode utilizar uma impressão digital para uma palavra-passe. Numa atualização futura, as definições de palavra-passe de impressão digital também irão permitir reconhecimento facial (**configuração do dispositivo** > **perfis** > **criar perfil**   >  **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **palavra-passe**). Como resultado, as seguintes definições estão mudando:

- **Desbloqueio por impressão digital** agora é **Touch ID e Face ID desbloquear**.
- **(Apenas supervisionada) de modificação de impressão digital** agora é **Touch ID e Face ID modificação (apenas supervisionada)** .

Face ID está disponível no iOS 11.0 e posterior. Para ver as definições atuais, aceda à [definições de dispositivos iOS para permitir ou restringir funcionalidades com o Intune](device-restrictions-ios.md#password).

Aplica-se a: iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>Funcionalidade de aplicações está dependente de região das classificações quando a restrição de jogos e aplicações armazenam funcionalidades em dispositivos iOS <!-- 4593948  -->
Em dispositivos iOS, pode permitir ou restringir funcionalidades relacionadas com a jogos, da app store e visualização de documentos (**configuração do dispositivo** > **perfis**  >   **Criar perfil** > **iOS** para a plataforma > **restrições de dispositivos** para o tipo de perfil > **App Store, visualização de documentos, jogos**). Também pode escolher a região das classificações como, por exemplo, Estados Unidos. Numa atualização futura, o **aplicações** funcionalidade irá mudar para o possível filho **região das classificações**e é dependente **região das classificações**.

Para ver as definições atuais, aceda à [definições de dispositivos iOS para permitir ou restringir funcionalidades com o Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>Modelos administrativos de política de grupo     <!--  3510695 -->
Para ajudar a melhorar a segurança para dispositivos na cloud, vamos lançar modelos administrativos que lhe permitirá utilizar o Intune para configurar as definições de política de grupo selecionadas para Windows PCs.  Estes modelos de utilizam o fornecedor de serviços de configuração de política (CSP) para fornecer até 2500 definições adicionais do Office, o Windows e o OneDrive.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Novas definições para a linha de base de segurança do Windows  <!-- 3534649, 4217151          -->
Estamos a adicionar novas definições para a linha de base de segurança do Windows. A primeira definição destina-se a segurança baseada em virtualização, que requer o arranque seguro. A segunda definição permitirá que gerenciar a ativação de voz de aplicações do Windows, quando o ecrã ser bloqueado.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>Linhas de base de segurança estará disponíveis em geral  <!--  3785395       -->
A funcionalidade de linhas de base de segurança estarão em breve do modo de pré-visualização e em disponibilidade geral. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>O modelo de base de segurança do Windows estará disponível em geral   <!--  3794072       -->
O modelo de base de segurança do Windows em breve estará do modo de pré-visualização e em disponibilidade geral. A versão de pré-visualização do modelo vai ser descontinuada e um novo modelo estará disponível.

<!-- ***********************************************-->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Atribuir etiquetas de âmbito para todos os dispositivos geridos num grupo de segurança <!-- 3173810 -->
Atualmente, pode atribuir uma etiqueta de âmbito para um dispositivo, entrar em cada dispositivo individual **propriedades** página e selecionar as etiquetas de âmbito. Numa atualização futura, poderá atribuir etiquetas de âmbito para um grupo de segurança e todos os dispositivos no grupo de segurança também será associados essas etiquetas de âmbito. Para tal, escolha **Intune** > **funções** > **âmbito (etiquetas)**  > **criar**  >  **Âmbito (etiquetas)** > Escolha os grupos que pretende atribuir a etiqueta de âmbito para. Todos os dispositivos nestes grupos também serão atribuídos a etiqueta de âmbito. As etiquetas de âmbito definido com esta funcionalidade irão substituir as etiquetas de âmbito definido com o fluxo de etiquetas de âmbito atual do dispositivo. (Numa atualização futura, o fluxo atual para atribuir etiquetas de âmbito para dispositivos será feito só de leitura.)

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Consulte o nível de patch de segurança para dispositivos Android <!-- 4461911  -->
Será capaz de ver o nível de patch de segurança para dispositivos Android. Para tal, escolha **Intune** > **dispositivos** > **todos os dispositivos** > Escolha um dispositivo > **Monitor**  >  **Hardware**.


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


