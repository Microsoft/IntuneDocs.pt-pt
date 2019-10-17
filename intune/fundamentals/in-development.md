---
title: Em desenvolvimento-Microsoft Intune
titleSuffix: ''
description: Recursos de Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa3309cc1aad3f82499e37cf0d009da336b15cca
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502770"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Em desenvolvimento para Microsoft Intune-outubro de 2019

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

### <a name="include-another-app-configuration-variable----4969237----"></a>Incluir outra variável de configuração de aplicativo <!-- 4969237  -->
Ao criar uma política de configuração de aplicativo, você poderá incluir a variável de configuração `AAD Device ID` como parte de suas definições de configuração. 

Para adicionar a variável de configuração `AAD Device ID`:
1. No Intune, selecione **aplicativos cliente** > **políticas de configuração de aplicativo** > **Adicionar**. 
1. Insira os detalhes da política de configuração.
1. Para exibir a folha **definições de configuração** , selecione definições de **configuração**.

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Aplicar modo escuro no Portal da Empresa do iOS <!-- 4911422  -->
O modo escuro está planejado para Portal da Empresa do iOS. Você poderá baixar aplicativos da empresa, gerenciar seus dispositivos e obter suporte de ti no esquema de cores de sua escolha. Para obter mais informações sobre Portal da Empresa do iOS, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Impedir a instalação de aplicativos de fontes desconhecidas em dispositivos Android Enterprise <!-- 4760025  -->
Em dispositivos Android Enterprise de perfil de trabalho, os usuários finais nunca podem instalar aplicativos de fontes desconhecidas no perfil de trabalho. Você poderá optar por estender essa restrição para o perfil pessoal também. Se você habilitar essa restrição, os usuários finais em dispositivos Android Enterprise de perfil de trabalho não poderão carregar aplicativos de fontes desconhecidas no lado pessoal do dispositivo. 

### <a name="use-an-updated-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Usar uma interface do usuário de proteção de aplicativo atualizada e a interface do usuário de provisionamento de aplicativo iOS <!-- 4102027, 4102029  -->
Atualizaremos a interface do usuário para criar e editar políticas de proteção de aplicativo (aplicativo) e perfis de provisionamento de aplicativo iOS no Intune. As alterações da interface do usuário incluem:
- Uma experiência simplificada que usa um formato de estilo de assistente em uma folha. 
- Uma atualização para o fluxo de criação para incluir atribuições.
- Um resumo. Ao exibir as propriedades antes de criar uma nova política ou ao editar uma propriedade, você verá uma página de Resumo de todas as configurações. Além disso, quando você edita Propriedades, o resumo listará apenas os itens da categoria de propriedades que você está editando.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Criar grupos de objetos de gerenciamento chamados de conjuntos de políticas <!-- 3762880  -->
Você poderá usar *conjuntos de políticas* para criar um pacote de referências a entidades de gerenciamento existentes que precisam ser identificadas, direcionadas e monitoradas como uma única unidade conceitual. Os conjuntos de políticas não substituem os conceitos ou objetos existentes. Os administradores podem continuar a atribuir objetos individuais como fazem hoje. Os conjuntos de políticas fazem referência a objetos individuais. Portanto, qualquer alteração nesses objetos individuais será refletida no conjunto de políticas. 

Para criar uma política definida no Intune, você selecionará os **conjuntos de políticas** > **criar**. 

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Executar aplicativos Win32 em dispositivos de modo S do Windows 10 <!-- 3747604  --> 
Você poderá instalar e executar aplicativos Win32 em dispositivos que são gerenciados no modo Windows 10 S. Crie uma ou mais políticas complementares para o modo S usando as ferramentas do PowerShell do Windows Defender Application Control (WDAC). Use o portal de assinatura do Device Guard para assinar as políticas complementares. Em seguida, carregue e distribua as políticas por meio do Intune. 

No Intune, você encontrará esse recurso selecionando **aplicativos cliente** > **políticas complementares do Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Definir a disponibilidade do aplicativo com base em uma data e hora <!-- 3510685  -->
Como administrador, você poderá configurar a hora de início e a data limite para um aplicativo necessário. Na hora de início, a extensão de gerenciamento do Intune baixará o conteúdo do aplicativo e irá armazená-lo em cache. O aplicativo será instalado na hora do prazo. Para aplicativos disponíveis, a hora de início determinará quando o aplicativo estiver visível no Portal da Empresa. 

Para definir a disponibilidade do aplicativo com base na data e hora:

1. No Intune, selecione **aplicativos cliente** > **aplicativos**. 
1. Selecione um aplicativo na lista ou adicione um novo selecionando **Adicionar**. 
1. Na folha do aplicativo, selecione **atribuições** > **Adicionar grupo**. 
1. Defina o **tipo de atribuição** como **obrigatório** e, em seguida, selecione **grupos incluídos**. 
1. Defina **tornar este aplicativo necessário para que todos os usuários** sejam **Sim**. 
1. Selecione **Editar** para modificar as opções de **experiência do usuário final** . 
1. Na folha **experiência do usuário final** , defina o **tempo disponível do software** conforme necessário. 

Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Exigir que aplicativos Win32 reiniciem <!-- 3136567  -->
Você poderá exigir que um aplicativo Win32 seja reiniciado após uma instalação bem-sucedida. Você pode escolher a quantidade de tempo (o período de carência) antes da reinicialização.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Exibir notificações para o aplicativo Portal da Empresa no Windows <!-- 1808082  -->
Atualizaremos o aplicativo Portal da Empresa em dispositivos Windows para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização mostrará notificações para aplicativos disponíveis somente quando o status da instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Exibir mensagens de status de instalação para o aplicativo Portal da Empresa <!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.
- O aplicativo foi instalado com êxito, mas requer uma reinicialização.
- O aplicativo está no processo de instalação, mas requer uma reinicialização para continuar.

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Atribuir o Microsoft Edge beta para macOS <!-- 4678761  -->
Você poderá adicionar e atribuir a versão mais recente do Microsoft Edge beta ao Intune para dispositivos macOS. 

Para atribuir o Microsoft Edge beta para dispositivos macOS:
1. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar aplicativo** > **Microsoft Edge-MacOS**. 
1. Atribua o Microsoft Edge beta aos grupos pretendidos. O Microsoft AutoUpdate (MAU) mantém o Microsoft Edge atualizado. 
 
Para obter mais informações sobre o Microsoft Edge, consulte [gerenciar o acesso via Web usando o Microsoft Edge com o Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
O aplicativo do Intune em dispositivos Android e iOS permitirá que você controle o conteúdo de notificação do aplicativo para contas da organização. Esse recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](../apps/app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android <!-- 3041956  -->
Para instalações de aplicativos disponíveis em dispositivos Android de perfil de trabalho, você pode exibir o status de instalação do aplicativo e a versão instalada dos aplicativos gerenciados Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](../apps/app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](../enrollment/android-enterprise-overview.md)e tipos de [aplicativo Google Play gerenciados](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Novas definições de configuração de dispositivo para dispositivos iOS e iPadOS supervisionados <!-- 5199328  -->
Em dispositivos iOS e iPadOS, você pode criar um perfil para restringir recursos e configurações em dispositivos:

1. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
1. Para a plataforma, selecione **Ios/iPadOS**.
1. Para o tipo de perfil, selecione **restrições de dispositivo**.

Você poderá controlar as novas configurações: 
- Acesse a unidade de rede no aplicativo arquivos.  
- Acesse a unidade USB no aplicativo arquivos. 
- Mantenha o Wi-Fi ligado. 

Para obter informações sobre as configurações atuais, consulte [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

As novas configurações se aplicam a:
- iOS 13,0 e mais recente.
- iPadOS 13,0 e mais recente.

### <a name="removal-of-automatic-connection-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Remoção de conexão automática em perfis Wi-Fi no Android e Android Enterprise <!-- 5021055  -->
Em dispositivos Android e Android Enterprise, você pode criar um perfil de Wi-Fi para definir configurações diferentes: 

1. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
1. Para a plataforma, selecione **Android** ou **Android Enterprise**.
1. Para o tipo de perfil, selecione **Wi-Fi**. 

A configuração **conectar automaticamente** será removida porque não é [suportada pelo Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29).

Se você usar essa configuração em um perfil de Wi-Fi, talvez perceba que o Connect não funcionará **automaticamente** . Você não precisa realizar nenhuma ação, mas lembre-se de que essa configuração será removida da interface do usuário do Intune.

Para obter informações sobre as configurações atuais, vá para [configurações de Wi-Fi do Android](../configuration/wi-fi-settings-android.md) ou configurações de [Wi-Fi do Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

A remoção dessa configuração aplica-se a:
- Android.
- Android Enterprise.

### <a name="global-http-proxy-on-android-enterprise-devices----4816339----"></a>Proxy HTTP global em dispositivos Android Enterprise <!-- 4816339  -->
Em dispositivos Android Enterprise, você poderá configurar um proxy HTTP global para atender aos padrões de navegação na Web de sua organização:

1. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
1. Para a plataforma, selecione **Android Enterprise**.
1. Selecione **proprietário do dispositivo**.
1. Para o tipo de perfil, selecione **restrições de dispositivo**. 
1. Selecione **conectividade**. 
 
Depois de configurar o proxy, todo o tráfego HTTP o usará. Esse recurso se aplica a dispositivos Android Enterprise que estão no modo de proprietário do dispositivo.

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Novo perfil de interface de configuração de firmware de dispositivo para dispositivos que executam o Windows 10 e posterior <!-- 2266073  -->
No Windows 10 e posterior, você pode criar um perfil de configuração de dispositivo para controlar as configurações e os recursos: 

1. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
1. Para a plataforma, selecione **Windows 10 e posterior**. 
 
Um novo tipo de perfil de interface de configuração de firmware de dispositivo permitirá que o Intune gerencie configurações de UEFI (BIOS).

Para obter informações sobre as configurações atuais que você pode configurar, consulte [aplicar recursos e configurações em seus dispositivos usando perfis de dispositivo no Microsoft Intune](../configuration/device-profiles.md).

Esse recurso se aplica ao Windows 10 RS5 (1809) e posterior, em selecionar dispositivos.

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>Certificados PKCS para macOS  <!-- 1333650                -->
Adicionaremos suporte completo para certificados PKCS (padrões de criptografia de chave pública) em dispositivos que executam o macOS. Os usuários poderão implantar certificados de usuário e de dispositivo com campos para **entidade de personalização** e **nome alternativo da entidade**. 

Também teremos uma nova configuração chamada **permitir todos os aplicativos de acesso**. Habilite essa configuração para conceder acesso à chave privada a todos os aplicativos associados. Para obter mais informações sobre essa configuração, consulte [referência de perfil de configuração](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) em developer.Apple.com.

### <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Credenciais derivadas para provisionar dispositivos móveis com certificados      <!--  1736036, 1736037, 1772050      --> 
Adicionaremos suporte para credenciais derivadas, que dão suporte ao *National Institute of Standards and Technology (NIST) 800-157* Standard para implantar certificados em dispositivos.  As credenciais derivadas dependem do uso de uma PIV (verificação de identidade pessoal) ou do CAC (cartão de acesso comum), como um cartão inteligente. Os usuários são autenticados usando seu cartão inteligente em um computador. Em seguida, eles solicitam um certificado para seu dispositivo gerenciado seguindo o processo que o provedor de credenciais derivado exige.   

O processo para usar credenciais derivadas para obter um certificado é diferente dos processos que usam perfis de certificado SCEP ou PKCS. Mas o resultado é o mesmo: dispositivos móveis que têm certificados de autenticação que podem ser usados para autenticação de aplicativo, VPN, Wi-Fi ou perfis de email. Para obter mais informações, consulte [derivadas PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) on NCCOE. NIST.gov.

A versão inicial das credenciais derivadas dará suporte a Entrust Datacard, intercedam e DISA purebred no iOS. Plataformas adicionais e provedores de credenciais derivados terão suporte em versões posteriores.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="specify-which-android-device-os-versions-enroll-through-the-work-profile-and-which-enroll-through-the-device-administrator----4350697---"></a>Especificar quais versões do sistema operacional do dispositivo Android se registram por meio do perfil de trabalho e quais registram por meio do administrador do dispositivo <!-- 4350697 -->
Usando as restrições de tipo de dispositivo do Intune, você poderá usar a versão do sistema operacional de um dispositivo para especificar se ele usará o registro de perfil de trabalho do Android Enterprise ou o registro de administrador do dispositivo Android. Para fazer isso, no Intune, selecione **registro de dispositivo**@no__t-**1 restrições de registro** > **criar restrição** > **restrição de tipo de dispositivo** > **configurações de plataforma**.

### <a name="edit-the-device-name-value-for-autopilot-devices----4816775---"></a>Editar o valor do nome do dispositivo para dispositivos de piloto automático <!-- 4816775 -->
Você poderá editar o valor do **nome do dispositivo** para os dispositivos do piloto automático ingressado no Azure AD:

1. Selecione **Intune** > **registro de dispositivo**@no__t-**3 registro do Windows** > **dispositivos** **Windows AutoPilot** > .
1. Escolha o dispositivo.
1. No painel à direita, altere o valor do **nome do dispositivo** .
1. Selecione **Guardar**.

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>Para dispositivos iOS, personalize a janela de privacidade de registro do Portal da Empresa <!-- 4394993  -->
Ao usar a redução, você poderá personalizar a janela de privacidade de Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você pode personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Editar o valor da marca do grupo para dispositivos de piloto automático<!-- 4816775 -->
Você poderá editar o valor da **marca do grupo** para dispositivos de piloto automático:

1. Selecione **Intune** > **registro de dispositivo**@no__t-**3 registro do Windows** > **dispositivos** **Windows AutoPilot** > .
1. Escolha o dispositivo.
1. No painel à direita, altere o valor da **marca de grupo** .
1. Selecione **Guardar**.

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Atualização da interface do usuário para criar e editar anéis de atualização do Windows 10  <!-- 4099089          -->   
Vamos distribuir as experiências de criação e edição da interface do usuário para anéis de atualização do Windows 10. A nova interface do usuário irá:  
- Simplifique a experiência existente usando um formato de estilo de assistente em uma folha. Essa atualização de interface do usuário eliminará a expansão da folha que exige que os profissionais de ti tomem jornadas de folha profundas.   
- Revisar o fluxo de criação para incluir atribuições.  
- Adicione uma página de resumo. O resumo incluirá todas as configurações quando você estiver exibindo Propriedades, quando estiver se preparando para criar um anel de atualização e quando estiver editando uma propriedade. Quando você estiver editando, o resumo listará apenas os itens dentro da categoria de propriedades que você está editando.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Atualização da interface do usuário para criar e editar atualizações de software iOS  <!-- 4099090        -->   
Vamos distribuir as experiências de interface do usuário criar e editar atualizadas para atualizações de software do iOS no Intune. A nova interface do usuário irá:
- Simplifique a experiência existente usando um formato de estilo de assistente em uma folha. Essa atualização de interface do usuário eliminará a expansão da folha que exige que os profissionais de ti tomem jornadas de folha profundas.  
- Incluir atribuições no fluxo de criação da política de atualização de software do iOS. 
- Inclua uma página de resumo na política de atualização de software do iOS. O resumo incluirá todas as configurações quando você estiver exibindo Propriedades, quando estiver se preparando para criar uma política e quando estiver editando uma propriedade. Quando você estiver editando, o resumo listará apenas os itens dentro da categoria de propriedades que você está editando.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Direcione os grupos de usuários do macOS para exigir o gerenciamento de JAMF <!-- 4061739 -->
Você poderá direcionar grupos específicos de usuários para exigir que seus dispositivos macOS sejam gerenciados pelo JAMF. Esse direcionamento permitirá que você aplique a integração de conformidade do JAMF a um subconjunto de dispositivos macOS enquanto outros dispositivos continuam a ser gerenciados pelo Intune. O direcionamento também permitirá que você migre gradualmente os dispositivos dos usuários de um sistema de MDM (gerenciamento de dispositivo móvel) para o outro.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Novas restrições para renomeação de dispositivos Windows <!-- 3478938 -->
Os nomes de dispositivo terão que seguir estas regras:
- 15 caracteres ou menos (menos de ou igual a 63 bytes, sem incluir um nulo à direita)
- Nenhuma cadeia de caracteres nula ou vazia
- ASCII permitido: letras (a-z, A-Z), números (0-9) e hifens
- Unicode permitido: caracteres > = 0x80, UTF8 válido, mapeados por IDN (RtlIdnToNameprepUnicode sucede; consulte RFC 3492)
- Os nomes não devem conter apenas números ou começar com um número
- Nenhum espaço no nome
- Caracteres não permitidos: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implantar atualizações de software em dispositivos macOS <!-- 3194876 -->
Você poderá implantar atualizações de software em grupos de dispositivos macOS. Esse recurso inclui o arquivo crítico, firmware, configuração e outras atualizações. Você pode enviar atualizações no próximo check-in do dispositivo. Ou você pode selecionar uma agenda semanal para implantar atualizações dentro ou fora dos períodos que você definiu. 

Esse recurso ajuda quando você deseja atualizar dispositivos fora do horário de trabalho padrão ou fora do horário em que o suporte técnico está totalmente na equipe. Você também obterá um relatório detalhado de todos os dispositivos macOS que têm atualizações implantadas. Você pode analisar o relatório por dispositivo para ver o status de uma atualização específica.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoramento e solução de problemas

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Relatório do Android na página Visão geral de dispositivos <!-- 2984353  -->
Vamos adicionar um novo relatório à página **visão geral de dispositivos** . O relatório exibe quantos dispositivos Android foram registrados em cada solução de gerenciamento de dispositivo. O gráfico mostra as contagens de dispositivos para o perfil de trabalho, totalmente gerenciado, dedicado e de administrador de dispositivo registrado. 

Para ver o relatório, escolha o **Intune** > **dispositivos** > **visão geral**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Relatórios de implantação do Windows AutoPilot <!-- 3856172  -->
Um novo relatório detalhará cada dispositivo implantado por meio do piloto automático do Windows. Esses dados estarão disponíveis por 30 dias após a implantação. 

Para ver o relatório, acesse **Intune** > **registro de dispositivo** > **Monitor** > **implantações de piloto automático**.

### <a name="updated-support-experience-------5012398------"></a>Experiência de suporte atualizada   <!--  5012398    -->
Como parte de aprimoramentos contínuos, atualizaremos a experiência de suporte no console do Intune.  Aprimoraremos a pesquisa no console e os comentários para problemas comuns e simplificaremos o fluxo de trabalho para entrar em contato com o suporte.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Para obter detalhes sobre os desenvolvimentos recentes, consulte [What ' s New in Microsoft Intune](whats-new.md).
