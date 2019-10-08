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
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999320"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Em desenvolvimento para Microsoft Intune-outubro de 2019

Para ajudá-lo em sua preparação e planejamento, esta página lista as atualizações da interface do usuário do Intune e os recursos que estão em desenvolvimento, mas ainda não foram lançados. Além disso:

- Se prevemos que você precisará tomar medidas antes de uma alteração, publicaremos uma postagem complementar do centro de mensagens do Office.
- Quando um recurso é iniciado na produção, como uma visualização ou disponível para o público geral, a descrição do recurso será movida para fora desta página e para a [página o que há de novo](whats-new.md).
- Esta página e a [página novidades](whats-new.md) são atualizadas periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte o [roteiro do M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e cronogramas.

> [!Note]
> Esses itens refletem as expectativas atuais da Microsoft sobre os recursos do Intune que estão chegando em uma versão futura. As datas e os recursos individuais podem mudar. Nem todos os itens no desenvolvimento têm uma descrição de recurso nesta página.

**RSS feed**: Seja notificado quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="additional-app-configuration-variable-available----4969237----"></a>Variável de configuração de aplicativo adicional disponível <!-- 4969237  -->
Ao criar uma política de configuração de aplicativo, você poderá incluir a variável de configuração `AAD Device ID` como parte de suas definições de configuração. No Intune, selecione **aplicativos cliente** > **políticas de configuração de aplicativo** > **Adicionar**. Insira os detalhes da política de configuração e selecione **definições de configuração** para exibir a folha de **definições de configuração** .

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Modo escuro para iOS Portal da Empresa <!-- 4911422  -->
O modo escuro está planejado para o Portal da Empresa do iOS. Baixe os aplicativos da empresa, gerencie seus dispositivos e obtenha suporte no esquema de cores de sua escolha. Para obter mais informações sobre o Portal da Empresa do iOS, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Impedir a instalação de aplicativos de fontes desconhecidas em dispositivos Android Enterprise <!-- 4760025  -->
Para um dispositivo de perfil de trabalho do Android Enterprise, nunca é possível que os usuários finais instalem aplicativos de fontes desconhecidas no perfil de trabalho. Opcionalmente, você poderá estender essa restrição para o perfil pessoal também. Se você habilitar essa restrição, os usuários finais em dispositivos Android Enterprise Work Profile também serão impedidos de aplicativos de carregamento lado de fontes desconhecidas no lado pessoal do dispositivo. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Atualizar para interface do usuário de proteção de aplicativo e interface do usuário de provisionamento de aplicativo iOS <!-- 4102027, 4102029  -->
A interface do usuário para criar e editar políticas de proteção de aplicativo e perfis de provisionamento de aplicativo iOS no Intune será atualizada. As alterações da interface do usuário incluem:
- Uma experiência simplificada usando um formato de estilo de assistente condensado dentro de uma folha. 
- Uma atualização para o fluxo de criação para incluir atribuições.
- Uma página resumida de todas as coisas definidas ao exibir as propriedades, antes de criar uma nova política ou ao editar uma propriedade. Além disso, ao editar propriedades, o resumo mostrará apenas uma lista de itens da categoria de propriedades que está sendo editada.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Criar grupos de objetos de gerenciamento chamados de conjuntos de políticas <!-- 3762880  -->
Os conjuntos de políticas permitem que você crie um pacote de referências a entidades de gerenciamento já existentes que precisam ser identificadas, direcionadas e monitoradas como uma única unidade conceitual. Os conjuntos de políticas não substituem os conceitos ou objetos existentes. Um administrador pode continuar a atribuir objetos individuais como eles fazem hoje. Os objetos individuais são referenciados por um conjunto de políticas. Portanto, qualquer alteração nesses objetos individuais será refletida no conjunto de políticas.  No Intune, você selecionará os **conjuntos de políticas** > **criar** para criar um novo conjunto de políticas. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Aplicativos Win32 em dispositivos do modo Windows 10 S <!-- 3747604  --> 
Você poderá instalar e executar aplicativos Win32 em dispositivos gerenciados por modo do Windows 10 S. Você poderá criar uma ou mais políticas complementares para o modo S usando as ferramentas do PowerShell do Windows Defender Application Control (WDAC). Assine as políticas complementares com o portal de assinatura do Device Guard e, em seguida, carregue e distribua as políticas por meio do Intune. No Intune, você encontrará esse recurso selecionando **aplicativos cliente** > **políticas complementares do Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Definir a disponibilidade do aplicativo com base em uma data e hora <!-- 3510685  -->
Como administrador, você poderá configurar a hora de início e a hora do prazo para um aplicativo necessário. Na hora de início, a extensão de gerenciamento do Intune iniciará o download do conteúdo do aplicativo e o armazenará em cache. O aplicativo será instalado na hora do prazo. Para aplicativos disponíveis, a hora de início será ditada quando o aplicativo estiver visível no Portal da Empresa. No Intune, selecione **aplicativos cliente** > **aplicativos**. Em seguida, selecione um aplicativo específico na lista ou selecione **Adicionar** para adicionar um novo aplicativo. Na folha do aplicativo, selecione **atribuições** > **Adicionar grupo**. Defina o **tipo de atribuição** como **obrigatório** e, em seguida, selecione **grupos incluídos**. Defina **tornar este aplicativo necessário para todos os usuários** para **Sim** e selecione **Editar** para modificar as opções de **experiência do usuário final** . Na folha **experiência do usuário final** , defina o **tempo disponível do software** conforme necessário. Para obter mais informações sobre como adicionar aplicativos, consulte [adicionar aplicativos ao Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Exigir que aplicativos Win32 reiniciem <!-- 3136567  -->
Você poderá exigir que um aplicativo Win32 precise ser reiniciado após uma instalação bem-sucedida. Além disso, você poderá escolher a quantidade de tempo (o período de carência) antes que a reinicialização deva ocorrer.

### <a name="company-portal-app-on-windows----1808082----"></a>Portal da Empresa aplicativo no Windows <!-- 1808082  -->
O aplicativo Portal da Empresa em dispositivos Windows será atualizado para exibir notificações do sistema para os usuários, mesmo quando o aplicativo for fechado. A atualização só mostrará notificações para aplicativos disponíveis quando o status de instalação for concluído ou com falha. O aplicativo Portal da Empresa não mostrará notificações para os aplicativos necessários.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portal da Empresa mensagens de status de instalação do aplicativo <!-- 2514416  -->
O aplicativo Portal da Empresa mostrará mensagens de status de instalação de aplicativo adicionais aos usuários finais. As seguintes condições serão aplicadas a novos recursos de dependência do Win32:
- Falha ao instalar o aplicativo. As dependências definidas pelo administrador não foram atendidas.
- O aplicativo foi instalado com êxito, mas requer uma reinicialização.
- O aplicativo está no processo de instalação, mas requer uma reinicialização para continuar.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Atribuir o Microsoft Edge beta para macOS <!-- 4678761  -->
Você poderá adicionar e atribuir a versão mais recente do Microsoft Edge beta ao Intune para dispositivos macOS. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar aplicativo** > **Microsoft Edge-MacOS**. Em seguida, atribua o Microsoft Edge beta aos grupos pretendidos. O Microsoft AutoUpdate (MAU) mantém o Microsoft Edge atualizado. Para obter mais informações sobre o Microsoft Edge, consulte [gerenciar o acesso via Web usando o Microsoft Edge com o Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar conteúdo de notificação do aplicativo para contas da organização <!-- 2576686 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android e iOS permitirão que você controle o conteúdo de notificação do aplicativo para contas da organização. Este recurso exigirá suporte de aplicativos e pode não estar disponível para todos os aplicativos habilitados para aplicativo. Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](../apps/app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android <!-- 3041956  -->
Para instalações de aplicativos disponíveis em dispositivos Android de perfil de trabalho, você pode exibir o status de instalação do aplicativo e a versão instalada dos aplicativos gerenciados Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](../apps/app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](../enrollment/android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuração do dispositivo


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Novas definições de configuração de dispositivo para dispositivos iOS e iPadOS supervisionados <!-- 5199328  -->
Em dispositivos iOS e iPadOS, você pode criar um perfil para restringir recursos e configurações em dispositivos (**configuração de dispositivo**@no__t-**1 perfis** > **Criar perfil** > **Ios/iPadOS** para o **dispositivo > de plataforma restrições** para o tipo de perfil). Haverá novas configurações que você pode controlar: 
- Acesso à unidade de rede no aplicativo de arquivos  
- Acesso à unidade USB no aplicativo de arquivos 
- Wi-Fi sempre ativado 

Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:
- iOS 13,0 e mais recente
- iPadOS 13,0 e mais recente

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>A configuração conectar automaticamente é removida em perfis Wi-Fi no Android e Android Enterprise <!-- 5021055  -->
Em dispositivos Android e Android Enterprise, você pode criar um perfil de Wi-Fi para definir configurações diferentes (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Android** ou **Android Enterprise** para plataforma > **Wi-Fi** para tipo de perfil). A configuração **conectar automaticamente** será removida, pois não há [suporte para o Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Se você usar essa configuração em um perfil de Wi-Fi, talvez perceba que o Connect não funcionará **automaticamente** . Você não precisa realizar nenhuma ação, mas lembre-se de que essa configuração é removida na interface do usuário do Intune.

Para ver as configurações atuais, vá para [configurações de Wi-Fi do Android](../configuration/wi-fi-settings-android.md) ou [configurações de Wi-Fi para Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Aplica-se a:
- Android
- Android Enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Criar um proxy HTTP global em dispositivos Android Enterprise do proprietário do dispositivo <!-- 4816339  -->
Em dispositivos Android Enterprise, você pode configurar um proxy HTTP global para atender aos padrões de navegação na Web de sua organização (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **proprietário do dispositivo > restrições de dispositivo** para o tipo de perfil > **conectividade**). Uma vez configurado, todo o tráfego HTTP usará esse proxy.

Aplica-se a:
- Proprietário do dispositivo corporativo Android

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Novo perfil de interface de configuração de firmware de dispositivo para dispositivos Windows 10 e posteriores <!-- 2266073  -->
No Windows 10 e posterior, você pode criar um perfil de configuração de dispositivo para controlar as configurações e os recursos (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma). Haverá um novo tipo de perfil de interface de configuração de firmware de dispositivo que permite ao Intune gerenciar configurações de UEFI (BIOS).

Para ver uma visão geral de todas as configurações atuais que você pode configurar, consulte [aplicar recursos e configurações em seus dispositivos usando perfis de dispositivo no Microsoft Intune](../configuration/device-profiles.md).

Aplica-se a:
- Windows 10 RS5 (1809) e mais recente em dispositivos selecionados

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>Certificados PKCS para macOS  <!-- 1333650                -->
Adicionaremos suporte completo para certificados PKCS em dispositivos que executam o macOS. Os usuários poderão implantar certificados de usuário e de dispositivo com os campos de entidade de personalização e nome alternativo da entidade. Também teremos uma nova configuração permitir acesso de todos os aplicativos, que habilitando o acesso à chave privada a todos os aplicativos associados. Para obter mais detalhes sobre essa configuração, visite a seguinte documentação da Apple: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Credenciais derivadas para provisionar dispositivos móveis com certificados      <!--  1736036, 1736037, 1772050      --> 
Vamos adicionar suporte para credenciais derivadas, que dão suporte ao *National Institute of Standards and Technology (NIST) 800-157* Standard para implantar certificados em dispositivos.  As credenciais derivadas dependem do uso de um cartão de verificação de identidade pessoal (PIV) ou cartão de acesso comum (CAC), como um cartão inteligente. Os usuários se autenticam com seu cartão inteligente em um computador e enviam uma solicitação de um certificado para o dispositivo gerenciado após o processo exigido pelo provedor de credenciais derivado.   

O processo para usar credenciais derivadas para obter um certificado é diferente de usar perfis de certificado SCEP ou PKCS, mas o resultado final é o mesmo – dispositivos móveis com certificados para autenticação que podem ser usados para autenticação de aplicativo, VPN, Wi-Fi ou email perfis.   

Para obter mais informações, consulte [derivadas PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) em www.nccoe.NIST.gov.

A versão inicial das credenciais derivadas dará suporte a Entrust Datacard, intercedam e DISA purebred no iOS. Plataformas adicionais e provedores de credenciais derivados terão suporte em versões posteriores.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscrição de dispositivos

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Especificar quais versões do sistema operacional do dispositivo Android registrar com o perfil de trabalho ou o registro de administrador do dispositivo <!-- 4350697 -->
Usando as restrições de tipo de dispositivo do Intune, você poderá usar a versão do sistema operacional do dispositivo para especificar quais dispositivos de usuário usarão o registro de perfil de trabalho do Android Enterprise ou o registro de administrador do dispositivo Android. Para fazer isso, acesse **Intune** > **registro de dispositivo**@no__t-**3 restrições de registro** > **criar restrição** > **restrição de tipo de dispositivo** >  configurações de**plataforma**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Editar o valor do nome do dispositivo para dispositivos de piloto automático <!-- 4816775 -->
Você poderá editar o valor do nome do dispositivo para dispositivos de piloto automático ingressados no Azure AD. Para fazer isso, vá para **Intune** > **registro de dispositivo**@no__t-**3 registro do Windows** > **dispositivos** **Windows autopilot** >  > escolha o dispositivo > alterar o valor do nome do dispositivo no painel direito > **salvar** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa <!-- 4394993  -->
Usando a redução, você poderá personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestão de dispositivos


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Editar o valor da marca do grupo para dispositivos de piloto automático<!-- 4816775 -->
Você poderá editar o valor da marca de grupo para dispositivos de piloto automático. Para fazer isso, vá para **Intune** > **registro de dispositivo**@no__t-**3 registro do Windows** > **dispositivos** **Windows autopilot** >  > escolha o dispositivo > alterar o valor da marca de grupo no painel direito > **salvar** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Atualização da interface do usuário para criar e editar anéis de atualização do Windows 10  <!-- 4099089          -->   
Vamos distribuir uma experiência de criação e edição de interface do usuário para anéis de atualização do Windows 10 para o Intune.  As alterações na interface do usuário incluirão:  
- Simplifique a experiência existente usando um formato de estilo de assistente condensado dentro de uma folha. Essa atualização da interface do usuário será desfeita com a redução da folha que exige que os profissionais de ti realizem uma busca detalhada em jornadas de folha profundas.   
- Revisar o fluxo de criação para incluir atribuições.  
- A adição de uma página resumida de todas as coisas definidas ao exibir as propriedades, antes de criar um novo anel de atualização e ao editar uma propriedade. Ao editar, o resumo mostrará apenas a lista de itens definidos dentro de uma categoria de propriedades que estão sendo editadas.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Atualização da interface do usuário para criar e editar atualizações de software iOS  <!-- 4099090        -->   
Lançaremos uma experiência de criação e edição de interface do usuário atualizada para atualizações de software do iOS no Intune. As alterações na interface do usuário incluirão:
- Simplifique a experiência existente usando um formato de estilo de assistente condensado dentro de uma folha. Essa atualização da interface do usuário será desfeita com a redução da folha que exige que os profissionais de ti realizem uma busca detalhada em jornadas de folha profundas.  
- O fluxo de criação da política de atualização de software do iOS será atualizado para incluir atribuições 
- A política de atualização de software do iOS incluirá uma página resumida de todas as coisas definidas ao exibir as propriedades, antes de criar uma nova política e ao editar uma propriedade. Ao editar, o resumo mostrará apenas a lista de itens definidos dentro de uma categoria de propriedades que estão sendo editadas.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Direcione os grupos de usuários do macOS para exigir o gerenciamento de JAMF <!-- 4061739 -->
Você poderá direcionar grupos específicos de usuários para exigir que seus dispositivos macOS sejam gerenciados pelo JAMF. Esse direcionamento permitirá que você aplique a integração de conformidade do JAMF a um subconjunto de dispositivos macOS enquanto outros dispositivos continuam a ser gerenciados pelo Intune. Ele também permitirá que você migre gradualmente os dispositivos dos usuários de um MDM para outro.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Novas restrições para renomeação de dispositivos Windows <!-- 3478938 -->
Os nomes de dispositivo terão que seguir estas regras:
- 15 caracteres ou menos (deve ser menor ou igual a 63 bytes, não incluindo nulo à direita)
- Cadeia de caracteres não nula ou vazia
- ASCII permitido: Letras (a-z, A-Z), números (0-9) e hifens
- Unicode permitidos: caracteres > = 0x80, deve ser um UTF8 válido, deve ser IDN-mapeável (RtlIdnToNameprepUnicode tem sucesso; consulte RFC 3492)
- Os nomes não devem conter apenas números ou começar com um número
- Nenhum espaço no nome
- Caracteres não permitidos: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implantar atualizações de software em dispositivos macOS <!-- 3194876 -->
Você poderá implantar atualizações de software em grupos de dispositivos macOS. Esse recurso inclui o arquivo crítico, firmware, configuração e outras atualizações. Você poderá enviar atualizações no próximo check-in do dispositivo ou selecionar uma agenda semanal para implantar atualizações dentro ou fora do tempo que você definir. Esse recurso ajuda quando você deseja atualizar dispositivos fora do horário de trabalho padrão ou quando o suporte técnico está totalmente na equipe. Você também obterá um relatório detalhado de todos os dispositivos macOS com atualizações implantadas. Você pode analisar o relatório de acordo com o dispositivo para ver os status de atualizações específicas.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Página Visão geral de novos relatórios do Android em dispositivos <!-- 2984353  -->
Vamos adicionar um novo relatório à página Visão geral de dispositivos que exibe quantos dispositivos Android foram registrados em cada solução de gerenciamento de dispositivo. Este gráfico mostrará o perfil de trabalho, as contagens de dispositivos registrados, totalmente gerenciadas, dedicadas e de administrador de dispositivo. Para ver o relatório, escolha o **Intune** > **dispositivos** > **visão geral**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Relatórios de implantação do Windows AutoPilot <!-- 3856172  -->
Um novo relatório detalhará cada dispositivo implantado por meio do piloto automático do Windows. Esses dados estarão disponíveis por 30 dias após a implantação. Para ver o relatório, acesse **Intune** > **registro de dispositivo** > **Monitor** > **implantações de piloto automático**.

### <a name="updated-support-experience-------5012398------"></a>Experiência de suporte atualizada   <!--  5012398    -->
Como parte dos aprimoramentos contínuos, atualizaremos a experiência de suporte no console do Intune.  Vamos melhorar a pesquisa no console e os comentários para problemas comuns e simplificar o fluxo de trabalho para entrar em contato com o suporte.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.




