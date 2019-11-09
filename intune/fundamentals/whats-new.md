---
title: Novidades no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Descobrir as novidades do Intune no portal do Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 37ed7bfd204289c963b8134252d9d76f2379ecba
ms.sourcegitcommit: 768d581cb8bcc5fdcb8ade95d402b11223ab226c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2019
ms.locfileid: "73882499"
---
# <a name="whats-new-in-microsoft-intune"></a>Novidades do Microsoft Intune

Saiba mais sobre as novidades todas as semanas no Microsoft Intune. Você também pode encontrar [avisos importantes](#notices), [versões anteriores](whats-new-archive.md)e informações sobre [como as atualizações de serviço do Intune são lançadas](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> Cada [atualização mensal](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) pode levar até três dias para ser imdistribuição e estará na seguinte ordem:
>
> - Dia 1: Pacífico Asiático (na Pacífico)
> - Dia 2: Europa, Oriente Médio, África (EMEA)
> - Dia 3: América do Norte
>
> É possível que algumas funcionalidades sejam implementadas durante várias semanas e que não estejam disponíveis para todos os clientes na primeira semana.
>
> Confira a [página em desenvolvimento](in-development.md) para obter uma lista de recursos futuros em uma versão.

**RSS feed**: seja notificado quando esta página for atualizada copiando e colando a seguinte URL em seu leitor de feed: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

## <a name="week-of-november-4-2019"></a>Semana de 4 de novembro de 2019

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>As linhas de base de segurança têm suporte no Microsoft Azure Governamental<!-- 4062552 -->

As instâncias do Intune hospedadas no *Microsoft Azure governamental* agora podem usar [linhas de base de segurança](../protect/security-baselines.md) para ajudá-lo a proteger e proteger seus usuários e dispositivos.

## <a name="week-of-october-28-2019"></a>Semana de 28 de outubro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Design de lista de verificação aprimorado no aplicativo Portal da Empresa para Android<!-- 5550857 -->  
A lista de verificação de configuração no aplicativo Portal da Empresa para Android foi atualizada com um design leve e novos ícones. As alterações se alinham com as atualizações recentes feitas no aplicativo Portal da Empresa para iOS. Para uma comparação lado a lado das alterações, consulte [novidades na interface do usuário do aplicativo](whats-new-app-ui.md). Para ver as etapas de registro atualizadas, consulte [registrar com o perfil de trabalho do Android](/intune-user-help/enroll-device-android-work-profile) e [registrar seu dispositivo Android](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Aplicativos Win32 em dispositivos do modo Windows 10 S<!-- 3747604 --> 
Você pode instalar e executar aplicativos Win32 em dispositivos gerenciados do modo Windows 10 S. Para fazer isso, você pode criar uma ou mais políticas complementares para o modo S usando as ferramentas do PowerShell do Windows Defender Application Control (WDAC). Assine as políticas complementares com o portal de assinatura do Device Guard e, em seguida, carregue e distribua as políticas por meio do Intune. No Intune, você encontrará esse recurso selecionando **aplicativos cliente** > **as políticas complementares do Windows 10 S**. Para obter mais informações, consulte [habilitar aplicativos Win32 em dispositivos em modo S](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Definir a disponibilidade do aplicativo Win32 com base em uma data e hora<!-- 3510685 -->
Como administrador, você pode configurar a hora de início e a hora do prazo para um aplicativo Win32 necessário. Na hora de início, a extensão de gerenciamento do Intune iniciará o download do conteúdo do aplicativo e o armazenará em cache. O aplicativo será instalado na hora do prazo. Para aplicativos disponíveis, a hora de início será ditada quando o aplicativo estiver visível no Portal da Empresa. Para obter mais informações, consulte [Gerenciamento de aplicativos Win32 do Intune](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Exigir reinicialização do dispositivo com base no período de carência após a instalação do aplicativo Win32<!-- 3136567 -->
Você pode exigir que um dispositivo seja reiniciado depois que um aplicativo Win32 for instalado com êxito. Para obter mais informações, consulte [Gerenciamento de aplicativo Win32-configurar detalhes de instalação do aplicativo](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Modo escuro para iOS Portal da Empresa<!-- 4911422 -->
O modo escuro está disponível para o Portal da Empresa do iOS. Os usuários podem baixar aplicativos da empresa, gerenciar seus dispositivos e obter suporte de ti no esquema de cores de sua escolha com base nas configurações do dispositivo. O Portal da Empresa do iOS corresponderá automaticamente às configurações do dispositivo do usuário final para o modo escuro ou leve. Para obter mais informações, consulte [introdução ao modo escuro no Microsoft Intune portal da empresa para IOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Para obter mais informações sobre o Portal da Empresa do iOS, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>O Android Portal da Empresa a versão mínima do aplicativo imposta<!-- 2378776 -->
Usando a configuração de **versão mín portal da empresa** de uma política de proteção de aplicativo, você pode especificar uma versão específica mínima definida do portal da empresa que é imposta em um dispositivo de usuário final. Essa configuração de inicialização condicional permite **bloquear o acesso**, **apagar dados**ou **avisar** como ações possíveis quando o valor não é atendido. Os formatos possíveis para esse valor seguem o padrão *[Major]. [ Minor]* , *[principal]. [ Secundária]. [Build]* ou *[Major]. [ Secundária]. [Build]. [Revisão]* .

A configuração de **versão mín portal da empresa** , se configurada, afetará qualquer usuário final que obtém a versão 5.0.4560.0 do portal da empresa e quaisquer versões futuras do portal da empresa. Essa configuração não terá nenhum efeito sobre os usuários que usam uma versão do Portal da Empresa mais antiga do que a versão com a qual esse recurso é lançado. Os usuários finais que usam as atualizações automáticas do aplicativo em seu dispositivo provavelmente não verão nenhuma caixa de diálogo desse recurso, Considerando que eles provavelmente estarão na versão mais recente do Portal da Empresa. Essa configuração é Android somente com proteção de aplicativo para dispositivos registrados e não registrados. Para obter mais informações, consulte [configurações de política de proteção de aplicativo Android – inicialização condicional](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Gerenciamento de dispositivos Microsoft 365

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introdução ao nó do Endpoint Security no gerenciamento de dispositivos Microsoft 365<!-- 5630102 -->

O nó do **Endpoint Security** agora está disponível em Microsoft 365 espaço de trabalho especialista em gerenciamento de dispositivos em https://devicemanagement.microsoft.com, que agrupa os recursos para proteger pontos de extremidade, como:

- Linhas de base de segurança: grupo pré-configurado de configurações que ajudam a aplicar um grupo conhecido de configurações e valores padrão que são recomendados pela Microsoft.

- Tarefas de segurança: Tire proveito do TVM (gerenciamento de ameaças e vulnerabilidades) do Microsoft defender ATPs e use o Intune para corrigir os pontos fracos do ponto de extremidade.

- Microsoft defender ATP: proteção de ameaças avançadas (ATP) integrada do Microsoft defender para ajudar a evitar violações de segurança.

Essas configurações continuarão a ser acessadas de outros nós aplicáveis, como dispositivos, e o estado atual configurado será o mesmo, independentemente de onde você acessar e habilitar esses recursos.

Para obter mais informações sobre esses aprimoramentos, consulte a [postagem do blog de sucesso do cliente do Intune](https://aka.ms/Endpoint_security_node) no site da comunidade de tecnologia da Microsoft.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>O Intune dá suporte ao iOS 11 e posterior<!-- 4665324  -->

O registro e o Portal da Empresa do Intune agora dão suporte ao iOS versões 11 e posteriores. Não há suporte para versões mais antigas.

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Linha de base do Microsoft Edge (versão prévia)<!--  3787164  -->

Adicionamos uma visualização de linha de base de segurança para [as configurações do Microsoft Edge](../protect/security-baseline-settings-edge.md). 

<!-- ########################## -->
## <a name="week-of-october-21-2019"></a>Semana de 21 de outubro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Gerenciamento de dispositivos Microsoft 365

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Experiência de administração aprimorada no gerenciamento de dispositivos Microsoft 365<!-- 5551239 -->

Uma experiência de administração atualizada e simplificada já está disponível no espaço de trabalho de especialista em gerenciamento de dispositivos Microsoft 365 em [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com), incluindo:

- **Navegação atualizada**: você encontrará uma navegação simplificada de 1º nível que agrupa logicamente os recursos.
- **Novos filtros de plataforma**: você pode selecionar uma única plataforma, que mostra apenas as políticas e os aplicativos para a plataforma selecionada, nas páginas dispositivos e aplicativos.
- **Um novo Home Page**: consulte rapidamente a integridade do serviço, o estado do seu locatário, notícias, etc. no novo Home Page.

Para obter mais informações sobre esses aprimoramentos, consulte a [postagem no blog Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) no site da comunidade de tecnologia da Microsoft.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Adicionar aplicativos de defesa contra ameaças móveis a dispositivos não registrados<!-- 3005337 -->
Você pode criar uma política de proteção de aplicativo do Intune que pode bloquear ou Apagar seletivamente os dados corporativos dos usuários com base na integridade de um dispositivo. A integridade do dispositivo é determinada usando sua solução de MTD (defesa contra ameaças móveis) escolhida. Essa funcionalidade existe hoje com dispositivos registrados no Intune como uma configuração de conformidade do dispositivo. Com esse novo recurso, ampliamos a detecção de ameaças de um fornecedor de defesa contra ameaças móveis para funcionar em dispositivos não registrados. No Android, esse recurso requer as Portal da Empresa mais recentes no dispositivo. No iOS, esse recurso estará disponível para uso quando os aplicativos integrarem o SDK do Intune mais recente (v 12.0.15 +). Atualizaremos o tópico What ' s New quando o primeiro aplicativo adotar o SDK mais recente do Intune. Os aplicativos restantes ficarão disponíveis em uma base contínua. Para obter mais informações, consulte [criar política de proteção de aplicativo de defesa contra ameaças móveis com o Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices---2266073----"></a>Novo perfil de interface de configuração de firmware de dispositivo para dispositivos Windows 10 e posteriores<!-- 2266073  -->

No Windows 10 e posterior, você pode criar um perfil de configuração de dispositivo para controlar as configurações e os recursos (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma). Nesta atualização, há um novo tipo de perfil de interface de configuração de firmware de dispositivo que permite ao Intune gerenciar configurações de UEFI (BIOS).

Para obter mais informações sobre esse recurso, consulte [usar perfis de DFCI em dispositivos Windows em Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Aplica-se a:
- Windows 10 RS5 (1809) e mais recente em firmware com suporte

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Alternar para mostrar apenas a página de status de registro em dispositivos provisionados pela experiência inicial (OOBE)<!--3959566-->
Agora você pode optar por mostrar apenas a página de status de registro em dispositivos provisionados pelo OOBE do AutoPilot.

Para ver a nova alternância, escolha **Intune** > **registro de dispositivo** > **registro do Windows** > **página status do registro** > **Criar perfil** > **configurações** > **apenas mostrar a página para dispositivos provisionados pela experiência inicial (OOBE)** .


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Semana de 14 de outubro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android<!-- 3041956   -->
Para instalações de aplicativos disponíveis em dispositivos Android Enterprise Work Profile, dedicados e totalmente gerenciados, você pode exibir o status de instalação do aplicativo, bem como a versão instalada dos aplicativos gerenciados do Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](~/apps/app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](~/enrollment/android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge versão 77 e posterior para Windows 10 e macOS (visualização pública)<!-- 3872025, 4678761  -->
O Microsoft Edge versão 77 e posterior estará disponível para implantação em computadores que executam o Windows 10 e o macOS. 

A visualização pública oferece canais de **desenvolvimento** e **beta** para o Windows 10 e um canal **beta** para MacOS. A implantação está em inglês (apenas EN), mas os usuários finais podem alterar o idioma de exibição no navegador em **configurações**  > **idiomas**. O Microsoft Edge é um aplicativo Win32 instalado no contexto do sistema e em arquiteturas semelhantes (aplicativo x86 no sistema operacional x86 e aplicativo x64 no sistema operacional x64). Além disso, as atualizações automáticas do navegador estão **ativadas** por padrão e o Microsoft Edge não pode ser desinstalado. Para obter mais informações, consulte [Adicionar o Microsoft Edge para Windows 10 a](~/apps/apps-windows-edge.md) documentação do Microsoft Intune e [do Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Atualizar para interface do usuário de proteção de aplicativo e interface do usuário de provisionamento de aplicativo iOS<!-- 4102027, 4102029   -->
A interface do usuário para criar e editar políticas de proteção de aplicativo e perfis de provisionamento de aplicativo iOS no Intune foi atualizada. As alterações da interface do usuário incluem:
- Uma experiência simplificada usando um formato de estilo de assistente condensado dentro de uma folha. 
- Uma atualização para o fluxo de criação para incluir atribuições.
- Uma página resumida de todas as coisas definidas ao exibir as propriedades, antes de criar uma nova política ou ao editar uma propriedade. Além disso, ao editar propriedades, o resumo mostrará apenas uma lista de itens da categoria de propriedades que está sendo editada.

Para obter mais informações, consulte [como criar e atribuir políticas de proteção de aplicativo](~/apps/app-protection-policies.md) e [usar perfis de provisionamento de aplicativo IOS](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Cenários guiados pelo Intune<!-- 4850318, 4831296, 3610611  -->
O Intune agora fornece cenários orientados para ajudá-lo a concluir uma tarefa específica ou um conjunto de tarefas no Intune. Um cenário guiado é uma série personalizada de etapas (fluxo de trabalho) centrada em um caso de uso de ponta a ponta. Cenários comuns são definidos com base na função que um administrador, um usuário ou um dispositivo desempenha em sua organização. Esses fluxos de trabalho normalmente exigem uma coleção de perfis, configurações, aplicativos e controles de segurança com cuidado, a fim de fornecer a melhor experiência do usuário e a segurança. Os novos cenários orientados incluem:
- [Implantar o Microsoft Edge para dispositivos móveis](~/fundamentals/guided-scenarios-edge.md)
- [Proteger Microsoft Office aplicativos móveis](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Área de trabalho moderna gerenciada pela nuvem](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Para obter mais informações, consulte [visão geral dos cenários guiados do Intune](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Variável de configuração de aplicativo adicional disponível<!-- 4969237   -->
Ao criar uma política de configuração de aplicativo, você pode incluir a variável de configuração `AAD Device ID` como parte de suas definições de configuração. No Intune, selecione **aplicativos cliente** > **políticas de configuração de aplicativo** > **Adicionar**. Insira os detalhes da política de configuração e selecione **definições de configuração** para exibir a folha de **definições de configuração** . Para obter mais informações, consulte [políticas de configuração de aplicativo para dispositivos Android Enterprise gerenciados – use o designer de configuração](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Criar grupos de objetos de gerenciamento chamados de conjuntos de políticas<!-- 3762880  -->
Os conjuntos de políticas permitem que você crie um pacote de referências a entidades de gerenciamento já existentes que precisam ser identificadas, direcionadas e monitoradas como uma única unidade conceitual. Os conjuntos de políticas não substituem os conceitos ou objetos existentes. Você pode continuar a atribuir objetos individuais no Intune e pode fazer referência a objetos individuais como parte de um conjunto de políticas. Portanto, qualquer alteração nesses objetos individuais será refletida no conjunto de políticas.  No Intune, você selecionará os **conjuntos de políticas**  > **criar** para criar um novo conjunto de políticas. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Atualização da interface do usuário para criar e editar anéis de atualização do Windows 10<!-- 4099089         -->
Atualizamos a experiência de interface do usuário para [criar e editar anéis de atualização do Windows 10](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) para o Intune. As alterações na interface do usuário incluem:  
- Um formato de estilo de assistente condensado em uma única folha de console, que se afasta da disposição da folha vista anteriormente enquanto você configura os anéis de atualização.   
- O fluxo de trabalho revisado inclui atribuições, antes de concluir a configuração inicial do anel.
- Uma página de resumo que você pode usar para examinar todas as configurações feitas, antes de salvar e implantar um novo anel de atualização. Ao editar um anel de atualização, o resumo mostra apenas a lista de itens definidos na categoria de propriedades que você editou.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Atualização da interface do usuário para criar e editar a política de atualização de software do iOS<!-- 4099090       --> 
Atualizamos a experiência de interface do usuário para [criar](../protect/software-updates-ios.md#configure-the-policy) e [Editar](../protect/software-updates-ios.md#edit-a-policy) as políticas de atualização de software do IOS para o Intune.  As alterações na interface do usuário incluem:  
- Um formato de estilo de assistente condensado em uma única folha de console, que se afasta da distribuição de folha vista anteriormente enquanto você configura as políticas de atualização.   
- O fluxo de trabalho revisado inclui atribuições, antes de concluir a configuração inicial da política.
- Uma página de resumo que você pode usar para examinar todas as configurações feitas, antes de salvar e implantar uma nova política. Ao editar uma política, o resumo mostra apenas a lista de itens definidos na categoria de propriedades que você editou.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>As configurações de reinicialização envolvidas são removidas dos anéis Windows Update<!--  4464404   WNReady   -->
Conforme anunciado anteriormente, os anéis de atualização do Windows 10 do Intune agora [dão suporte a configurações para prazos finais](../protect/windows-update-settings.md) e não oferecem mais suporte ao *reinício envolvido*. As configurações para *reinicialização iniciada* não estão mais disponíveis quando você configura ou gerencia anéis de atualização no Intune.  

Essa alteração se alinha com [as alterações de serviço do Windows](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) recentes e em dispositivos que executam o Windows 10 1903 ou posterior, os *prazos* substituem as configurações para *reinicialização*ativada.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Impedir a instalação de aplicativos de fontes desconhecidas em dispositivos Android Enterprise de perfil de trabalho<!-- 4760025   -->
Em dispositivos Android Enterprise de perfil de trabalho, os usuários não podem nunca instalar aplicativos de aplicativos de fontes desconhecidas. Nessa atualização, há uma nova configuração – **impedir instalações de aplicativos de fontes desconhecidas no perfil pessoal**. Por padrão, essa configuração impede que os usuários façam o Sideload de aplicativos de fontes desconhecidas no perfil pessoal do dispositivo.

Para ver a configuração que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Criar um proxy HTTP global em dispositivos Android Enterprise do proprietário do dispositivo<!-- 4816339   -->
Em dispositivos Android Enterprise, você pode configurar um proxy HTTP global para atender aos padrões de navegação na Web de sua organização (**configuração de dispositivos**  > **perfis**  > **Criar perfil**  > **Android Enterprise** para plataforma > **proprietário do dispositivo > restrições de dispositivo** para o tipo de perfil > **conectividade**). Uma vez configurado, todo o tráfego HTTP usará esse proxy.

Para configurar esse recurso e ver todas as configurações definidas, vá para configurações de [dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Proprietário do dispositivo corporativo Android

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>A configuração conectar automaticamente é removida nos perfis Wi-Fi no administrador do dispositivo Android e no Android Enterprise<!-- 5021055   -->
No Android Device Administrator e em dispositivos Android Enterprise, você pode criar um perfil de Wi-Fi para definir configurações diferentes (**configuração do dispositivo**  > **perfis**  > **Criar perfil**  > **dispositivo Android administrador** ou **Android Enterprise** para plataforma > **Wi-Fi** para tipo de perfil). Nessa atualização, a configuração **conectar automaticamente** é removida, pois não há [suporte para o Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Se você usar essa configuração em um perfil de Wi-Fi, talvez tenha notado que o Connect não funcionará **automaticamente** . Você não precisa realizar nenhuma ação, mas lembre-se de que essa configuração é removida na interface do usuário do Intune.

Para ver as configurações atuais, vá para [configurações de Wi-Fi do Android](../configuration/wi-fi-settings-android.md) ou [configurações de Wi-Fi para Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Aplica-se a:
- Administrador do dispositivo Android 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Novas definições de configuração de dispositivo para dispositivos iOS e iPadOS supervisionados<!-- 5199328   -->
Em dispositivos iOS e iPadOS, você pode criar um perfil para restringir recursos e configurações em dispositivos (**configuração de dispositivo**  > **perfis**  > **Criar perfil**  > **Ios/iPadOS** para o dispositivo > de plataforma  **restrições** para o tipo de perfil). Nessa atualização, há novas configurações que você pode controlar: 
- Acesso à unidade de rede no aplicativo de arquivos  
- Acesso à unidade USB no aplicativo de arquivos 
- Wi-Fi sempre ativado 

Para ver essas configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:
- iOS 13,0 e mais recente
- iPadOS 13,0 e mais recente

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Especificar quais versões do sistema operacional do dispositivo Android registrar com o perfil de trabalho ou o registro de administrador do dispositivo<!-- 4350697   -->
Usando as restrições de tipo de dispositivo do Intune, você pode usar a versão do sistema operacional do dispositivo para especificar quais dispositivos de usuário usarão o registro de perfil de trabalho do Android Enterprise ou o registro de administrador do dispositivo Android.  Para obter mais informações, consulte [definir restrições de registro](../enrollment/enrollment-restrictions-set.md).

#### <a name="windows-autopilot-deployment-reports---3856172---"></a>Relatórios de implantação do Windows AutoPilot<!-- 3856172 -->
Um novo relatório detalha cada dispositivo implantado por meio do piloto automático do Windows. Para obter mais informações, consulte [relatório de implantação do AutoPilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report). Estamos no processo de distribuir esse recurso para todos os clientes e esperar que seja concluído até o final da próxima semana.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Novas restrições para renomeação de dispositivos Windows<!-- 3478938  -->
Ao renomear um dispositivo Windows, você deve seguir as novas regras:
- 15 caracteres ou menos (deve ser menor ou igual a 63 bytes, não incluindo nulo à direita)
- Não nulo ou uma cadeia de caracteres vazia
- ASCII permitido: letras (a-z, A-Z), números (0-9) e hifens
- Unicode permitidos: caracteres > = 0x80, deve ser um UTF8 válido, deve ser IDN-mapeável (ou seja, RtlIdnToNameprepUnicode tem sucesso; consulte RFC 3492)
- Os nomes não devem conter apenas números
- Nenhum espaço no nome
- Caracteres não permitidos: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

 Para obter mais informações, consulte [renomear um dispositivo no Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Página Visão geral de novos relatórios do Android em dispositivos<!-- 4924364 -->
Um novo relatório para a página Visão geral de dispositivos exibe quantos dispositivos Android foram registrados em cada solução de gerenciamento de dispositivo. Este gráfico mostra o perfil de trabalho, as contagens de dispositivos registrados, totalmente gerenciados, dedicados e de administrador de dispositivo. Para ver o relatório, escolha o **Intune** > **dispositivos** > **visão geral**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>Certificados PKCS para macOS<!-- 1333650       -->
Agora você pode [usar certificados PKCS com MacOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Você pode selecionar o certificado PKCS como um tipo de perfil para macOS e implantar certificados de usuário e de dispositivo que tenham [campos personalizados de entidade e nome alternativo da entidade](../protect/certficates-pfx-configure.md#subject-name-format-for-macos).  

O certificado PKCS para macOS também oferece suporte a uma nova configuração, _permitir acesso a todos os aplicativos_. Com essa configuração, você pode habilitar todos os aplicativos associados ao acesso à chave privada do certificado.  Para obter mais informações sobre essa configuração, consulte a documentação da Apple em https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Credenciais derivadas para provisionar dispositivos móveis iOS com certificados<!--  1736036, 1736037, 1772050, 2777333         -->  
O Intune dá suporte ao uso de [credenciais derivadas](../protect/derived-credentials.md) como um método de autenticação e à assinatura e criptografia S/MIME para dispositivos IOS. As credenciais derivadas são uma implementação do padrão *NIST (National Institute of Standards and Technology) 800-157* para a implantação de certificados em dispositivos.  

As credenciais derivadas dependem do uso de um cartão de verificação de identidade pessoal (PIV) ou cartão de acesso comum (CAC), como um cartão inteligente. Para obter uma credencial derivada para seu dispositivo móvel, os usuários iniciam no aplicativo Portal da Empresa e seguem um fluxo de trabalho de registro que é exclusivo para o provedor que você usa.  Comum a todos os provedores é a necessidade de usar um cartão inteligente em um computador para se autenticar no provedor de credenciais derivado. Esse provedor emite um certificado para o dispositivo que é derivado do cartão inteligente do usuário.  

O Intune dá suporte aos seguintes provedores de credenciais derivados:
- DISA purebred
- Entrust Datacard
- Intercedam

Você usa credenciais derivadas como o método de autenticação para perfis de configuração de dispositivo para VPN, Wi-Fi e email. Você também pode usá-los para autenticação de aplicativo e assinatura e criptografia S/MIME.  

Para obter mais informações sobre o padrão, consulte [credenciais de PIV derivadas](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) em www.nccoe.NIST.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Use API do Graph para especificar um nome principal de usuário local como uma variável para certificados SCEP<!--  5437939        -->  
Ao usar o [API do Graph do Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0), você pode especificar onPremisesUserPrincipalName como uma variável para o San (nome alternativo da entidade) para certificados SCEP.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Semana de 23 de setembro de 2019

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Registro de usuário do iOS em versão prévia<!-- 4817900 -->
A versão iOS 13,1 da Apple inclui o registro de usuário, uma nova forma de gerenciamento leve para dispositivos iOS. Ele pode ser usado no lugar do registro de dispositivo ou do registro de dispositivo automatizado (anteriormente Programa de registro de dispositivos) para dispositivos de propriedade pessoal. A versão prévia do Intune oferece suporte a esse conjunto de recursos, permitindo que você:

- Direcionar o registro de usuário para grupos de usuários.
- Dê aos usuários finais a capacidade de selecionar entre o registro mais leve do usuário ou o registro de dispositivo mais forte quando registrarem seus dispositivos.

A partir do 9/24/2019 com o lançamento do iOS 13,1, estamos no processo de distribuir essas atualizações para todos os clientes e esperar que sejam concluídas até o final da próxima semana.
Aplica-se a:

iOS 13,1 e posterior

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Suporte do Intune para dispositivos iPadOS e iOS 13,1<!--5439574-->
O Intune agora dá suporte ao gerenciamento de dispositivos iPadOS e iOS 13,1. Para obter mais informações, veja [esta mensagem do blogue](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Semana de 16 de setembro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Aplicativos LOB privados Google Play gerenciados<!-- 1464182  -->
O Intune agora permite que os administradores de ti publiquem aplicativos LOB Android privados em Google Play gerenciados por meio de um iframe inserido no console do Intune.  Anteriormente, os administradores de ti precisavam publicar aplicativos LOB diretamente no console de publicação de reprodução do Google, que exigia várias etapas e estava demorando. Esse novo recurso permite a publicação fácil de aplicativos LOB com um conjunto mínimo de etapas, sem a necessidade de sair do console do Intune.  Os administradores não precisarão registrar-se manualmente como desenvolvedor com o Google e não precisarão mais pagar a taxa de registro do Google $25.  Qualquer um dos cenários de gerenciamento do Android Enterprise que usam Google Play gerenciados pode aproveitar esse recurso (perfil de trabalho, dispositivos dedicados, totalmente gerenciados e não registrados). No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. Em seguida, selecione **Google Play gerenciado** na lista **tipo de aplicativo** . Para obter mais informações sobre aplicativos Google Play gerenciados, consulte [adicionar aplicativos gerenciados de Google Play a dispositivos Android Enterprise com o Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Experiência do Windows Portal da Empresa<!-- 1473353, 3598357 -->
A Portal da Empresa do Windows está sendo atualizada. Você poderá usar vários filtros na página de aplicativos dentro do Portal da Empresa do Windows. A página de detalhes do dispositivo também está sendo atualizada com uma experiência de usuário aprimorada. Estamos no processo de distribuir essas atualizações para todos os clientes e esperar que sejam concluídas até o final da próxima semana.

#### <a name="macos-support-for-web-apps---3174427---"></a>suporte para macOS para aplicativos Web<!-- 3174427 -->
Os aplicativos Web, que permitem adicionar um atalho a uma URL na Web, podem ser instalados no Dock usando o Portal da Empresa macOS. Os usuários finais podem acessar a ação de **instalação** na página de detalhes do aplicativo para um aplicativo Web no MacOS portal da empresa. Para obter mais informações sobre o tipo de aplicativo de **link da Web** , consulte [adicionar aplicativos ao Microsoft Intune](../apps/apps-add.md) e [adicionar aplicativos Web ao Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>suporte do macOS para aplicativos VPP<!-- 3173501  -->
aplicativos macOS, adquiridos usando o Apple Business Manager, são exibidos no console do quando os tokens de VPP da Apple são sincronizados no Intune. Você pode atribuir, revogar e reatribuir licenças baseadas no usuário e no dispositivo para grupos usando o console do Intune. Microsoft Intune ajuda a gerenciar aplicativos VPP adquiridos para uso em sua empresa:

- Comunicar informações sobre a licença a partir da App Store.
- Controlar o número de licenças que utilizou.
- Ajudando você a impedir a instalação de mais cópias do aplicativo do que você possui.

Para obter mais informações sobre o Intune e o VPP, consulte [gerenciar aplicativos e livros adquiridos por volume com o Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>Suporte a Google Play iframe gerenciado<!-- 2871756  -->
O Intune agora oferece suporte para adicionar e gerenciar links da Web diretamente no console do Intune por meio do iframe Google Playdor gerenciado.  Isso permite que os administradores de ti enviem um gráfico de URL e ícone e, em seguida, implantem esses links em dispositivos como aplicativos Android regulares. Qualquer um dos cenários de gerenciamento do Android Enterprise que usam Google Play gerenciados pode aproveitar esse recurso (perfil de trabalho, dispositivos dedicados, totalmente gerenciados e não registrados). No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. Em seguida, selecione **Google Play gerenciado** na lista **tipo de aplicativo** . Para obter mais informações sobre aplicativos Google Play gerenciados, consulte [adicionar aplicativos gerenciados de Google Play a dispositivos Android Enterprise com o Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Instalar silenciosamente aplicativos LOB Android em dispositivos pretas<!-- 4252734  -->
Ao instalar aplicativos de LOB (linha de negócios) do Android em [dispositivos pretas](../configuration/android-zebra-mx-overview.md), em vez de ser solicitado a baixar e instalar o aplicativo LOB, você poderá instalar o aplicativo silenciosamente. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. No painel **Adicionar aplicação**, selecione **Aplicação de linha de negócio**. Para obter mais informações, consulte [Adicionar um aplicativo de linha de negócios Android a Microsoft Intune](../apps/lob-apps-android.md).

No momento, depois que o aplicativo de LOB for baixado, uma notificação de **êxito no download** será exibida no dispositivo do usuário. A notificação só pode ser descartada tocando em **limpar tudo** na sombra da notificação. Esse problema de notificação será corrigido em uma versão futura e a instalação será completamente silenciosa sem nenhum indicador visual.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Ler e gravar API do Graph operações para aplicativos do Intune<!-- 5031704  -->
Os aplicativos podem chamar o API do Graph do Intune com operações de leitura e gravação usando a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Compartilhamento e criptografia de dados protegidos para o SDK de aplicativos do Intune para iOS<!-- 3586942  -->
O SDK de aplicativo do Intune para iOS usará chaves de criptografia de 256 bits quando a criptografia for habilitada pelas políticas de proteção de aplicativo. Todos os aplicativos precisarão ter uma versão 8.1.1 do SDK para permitir o compartilhamento de dados protegidos.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Suporte para perfis VPN IKEv2 para iOS<!-- 1943438   -->
Nessa atualização, você pode criar perfis de VPN para o cliente VPN nativo do iOS usando o protocolo IKEv2. IKEv2 é um novo tipo de conexão na **configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **VPN** para tipo de perfil > **tipo de conexão**.

Esses perfis de VPN configuram o cliente VPN nativo, portanto, nenhum aplicativo cliente VPN é instalado ou enviado por push para dispositivos gerenciados. Esse recurso requer que os dispositivos sejam registrados no Intune (registro de MDM).

Para ver as configurações de VPN atuais que você pode configurar, vá para [definir configurações de VPN em dispositivos IOS](../configuration/vpn-settings-ios.md).

Aplica-se a:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Os recursos do dispositivo, as restrições de dispositivo e os perfis de extensão para as configurações do iOS e do macOS são mostrados pelo tipo de registro<!-- 4886161   -->

No Intune, você cria perfis para dispositivos iOS e macOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios** ou **MacOS** para plataforma > **recursos de dispositivo**, **dispositivo restrições**ou **extensões** para o tipo de perfil). 

Nessa atualização, as configurações disponíveis no portal do Intune são categorizadas pelo tipo de registro ao qual se aplicam:

- iOS
  - Registro de usuário
  - Inscrição de dispositivos
  - Registro de dispositivo automatizado (supervisionado)
  - Todos os tipos de registro

- macOS
  - Usuário aprovado
  - Inscrição de dispositivos
  - Registro de dispositivo automatizado
  - Todos os tipos de registro

Aplica-se a:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Novas configurações de controle de voz para dispositivos iOS supervisionados em execução no modo de quiosque<!-- 4892835   -->
No Intune, você pode criar políticas para executar dispositivos iOS supervisionados como um quiosque ou dispositivo dedicado (**configuração de dispositivo**  > **perfis**  > **Criar perfil**  > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **quiosque**).

Nessa atualização, há novas configurações que você pode controlar:
- **Controle de voz**: habilita o controle de voz no dispositivo no modo de quiosque.
- **Modificação do controle de voz**: permite que os usuários alterem a configuração de controle de voz no dispositivo no modo de quiosque.

Para ver as configurações atuais, vá para [configurações de quiosque do IOS](../configuration/device-restrictions-ios.md#kiosk).

Aplica-se a:
- iOS 13,0 e posterior

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Usar o logon único para aplicativos e sites em seus dispositivos iOS e macOS<!-- 4893175   -->
Nesta atualização, há algumas novas configurações de logon único para dispositivos iOS e macOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **iOS** ou **MacOS** para recursos de dispositivo > de plataformapara tipo de perfil).

Use essas configurações para configurar uma experiência de logon único, especialmente para aplicativos e sites que usam a autenticação Kerberos. Você pode escolher entre uma extensão de aplicativo de logon único de credencial genérica e a extensão Kerberos interna da Apple.

Para ver os recursos atuais do dispositivo que você pode configurar, vá para [recursos do dispositivo IOS](../configuration/ios-device-features-settings.md) e [recursos do dispositivo MacOS](../configuration/macos-device-features-settings.md).

Aplica-se a:
- iOS 13,0 e mais recente
- macOS 10,15 e mais recente

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associar domínios a aplicativos em dispositivos macOS 10.15 +<!-- 4898079   -->
Em dispositivos macOS, você pode configurar recursos diferentes e enviar por push esses recursos para seus dispositivos usando uma política (**configuração de dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **dispositivo recursos** para tipo de perfil). Nessa atualização, você pode associar domínios a seus aplicativos. Esse recurso ajuda a compartilhar credenciais com sites relacionados ao seu aplicativo e pode ser usado com a extensão de logon único da Apple, links universais e preenchimento de senha. 

Para ver os recursos atuais que você pode configurar, vá para [configurações de recurso de dispositivo MacOS no Intune](../configuration/macos-device-features-settings.md).

Aplica-se a:
- macOS 10,15 e mais recente

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Use "iTunes" e "apps" na URL da iTunes App Store ao mostrar ou ocultar aplicativos em dispositivos supervisionados do iOS<!-- 4928474   --> 
No Intune, você pode criar políticas para mostrar ou ocultar aplicativos em seus dispositivos iOS supervisionados (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > restrições de **dispositivo** para tipo de perfil > **Mostrar ou ocultar aplicativos**). 

Você pode inserir a URL da iTunes App Store, como `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. Nessa atualização, `apps` e `itunes` podem ser usados na URL, como:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Para obter mais informações sobre essas configurações, consulte [Mostrar ou ocultar aplicativos](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Aplica-se a:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Os valores do tipo de senha da política de conformidade do Windows 10 são mais claros e correspondem ao CSP<!-- 5138985 -->
Em dispositivos Windows 10, você pode criar uma política de conformidade que exige recursos de senha específicos (**conformidade do dispositivo** > **políticas** > **criar política** > **Windows 10 e posterior** para plataforma > **sistema Segurança**). Nesta atualização:
- Os valores de **tipo de senha** são mais claros e atualizados para corresponder ao [CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- A configuração **expiração da senha (dias)** é atualizada para permitir valores de 1-730 dias. 

Para obter mais informações sobre as configurações de conformidade do Windows 10, consulte [configurações do Windows 10 e posteriores para marcar dispositivos como em conformidade ou sem conformidade](../protect/compliance-policy-create-windows.md). 

Aplica-se a:
- Windows 10 e posterior

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Interface do usuário atualizada para configurar o acesso no local do Microsoft Exchange<!-- 4092920 -->  
Atualizamos o console do onde você configura o acesso do [Microsoft Exchange no local](../protect/conditional-access-exchange-create.md). Todas as configurações para o acesso ao Exchange local agora estão disponíveis no mesmo painel do console em que você habilita o *controle de acesso local do Exchange*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Permitir ou restringir a adição de widgets de aplicativo à tela inicial em dispositivos Android Enterprise Work Profile<!-- 1109650  --> 
Em dispositivos Android Enterprise, você pode configurar recursos no perfil de trabalho (**configuração** do dispositivo**perfis** de  >   > **Criar perfil**  > **Android Enterprise** para plataforma > **perfil de trabalho apenas > Restrições de dispositivo** para o tipo de perfil). Nessa atualização, você pode permitir que os usuários adicionem widgets expostos por aplicativos de perfil de trabalho à tela inicial do dispositivo.

Para ver as configurações que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Novos locatários ficarão desaparecendo do gerenciamento de administrador de dispositivos Android<!-- 4869790   -->
Os recursos de administrador do dispositivo do Android foram substituídos pelo Android Enterprise. Portanto, é recomendável usar Android Enterprise para novos registros em vez disso. Em uma atualização futura, novos locatários precisarão concluir as seguintes etapas de pré-requisito no registro do Android para usar o gerenciamento de administrador do dispositivo: Vá para **Intune** > **registro de dispositivo** > **registro Android** >  **Dispositivos pessoais e corporativos com privilégios de administração de dispositivo** > **usam o administrador do dispositivo para gerenciar dispositivos**.

Os locatários existentes não sofrerão alteração em seus ambientes.

Para obter mais informações sobre o administrador do dispositivo Android no Intune, consulte [registro do administrador do dispositivo Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>Lista de dispositivos DEP associados a um perfil<!-- 5012045 idmiss -->
Agora você pode ver uma lista paginável de dispositivos DEP (Automated Programa de registro de dispositivos) que estão associados a um perfil. Você pode pesquisar a lista em qualquer página da lista. Para ver a lista, acesse **Intune** > **registro de dispositivo** > **registro da Apple** > **tokens do programa de registro** > escolha um token > **perfis** > escolha um perfil > **dispositivos atribuídos** ( em **Monitor**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Mais suporte totalmente gerenciado do Android<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Adicionamos o seguinte suporte para dispositivos Android totalmente gerenciados:

- Os certificados SCEP para Android totalmente gerenciado estão disponíveis para autenticação de certificado em dispositivos gerenciados como proprietário do dispositivo. Os certificados SCEP já têm suporte em dispositivos de perfil de trabalho.  Com certificados SCEP para o proprietário do dispositivo, você poderá: <!-- 5227935 -->
    - Criar perfil SCEP sob a seção do Android Enterprise
    - vincular certificados SCEP para fazer o perfil de Wi-Fi para autenticação
    - vincular certificados SCEP a perfis de VPN para autenticação
    - vincular certificados SCEP para os perfis de email para autenticação (via AppConfig)
- Os aplicativos do sistema têm suporte em dispositivos Android Enterprise. No Intune, adicione um aplicativo Android Enterprise System selecionando **aplicativos cliente** > **aplicativos** > **Adicionar**. Na lista **tipo de aplicativo** , selecione **aplicativo Android Enterprise System**. Para obter mais informações, consulte [adicionar aplicativos do Android Enterprise System a Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- Em **conformidade do dispositivo** > **Android Enterprise** > **proprietário do dispositivo**, você pode criar uma política de conformidade que define o nível de atestado do Google SafetyNet.   <!-- 4631425 -->
- Em dispositivos Android Enterprise totalmente gerenciados, há suporte para os provedores de defesa contra ameaças móveis. Em **conformidade do dispositivo** > **Android Enterprise** > **proprietário do dispositivo**, você pode escolher um nível de ameaça aceitável. <!-- 4631440 --> [As configurações do Android Enterprise para marcar dispositivos como compatíveis ou não compatíveis usando o Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) listam as configurações atuais.
- Em dispositivos Android Enterprise totalmente gerenciados, o aplicativo Microsoft Launcher agora pode ser configurado por meio de políticas de configuração de aplicativo para permitir uma experiência de usuário final padronizada no dispositivo totalmente gerenciado. O aplicativo Microsoft Launcher pode ser usado para personalizar seu dispositivo Android. Usando o aplicativo junto com uma conta de conta Microsoft ou de trabalho/escola, você pode acessar seu calendário, documentos e atividades recentes em seu feed personalizado. <!-- 5334044 -->

Com essa atualização, estamos felizes em anunciar que o suporte do Intune para Android Enterprise totalmente gerenciado já está disponível para o público geral.

Aplica-se a:

- Dispositivos Android Enterprise totalmente gerenciados

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Enviar notificações personalizadas para um único dispositivo<!-- 4928910 -->
Agora você pode selecionar um único dispositivo e, em seguida, usar uma ação de dispositivo remoto para [Enviar uma notificação personalizada somente para esse dispositivo](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>As ações de limpeza e redefinição de senha não estão disponíveis para dispositivos iOS registrados usando o registro de usuário<!-- 4950491 -->
O registro de usuário é um novo tipo de registro de dispositivo da Apple. Quando você registra dispositivos usando o registro de usuário, as ações remotas de limpeza e redefinição de senha não estarão disponíveis para esses dispositivos.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Suporte do Intune para dispositivos do Catalina para iOS 13 e macOS<!-- 4665317 -->
O Intune agora dá suporte ao gerenciamento de dispositivos do iOS 13 e do macOS.
Para obter mais informações, consulte a [postagem de blog do suporte a Microsoft Intune para IOS 13 e iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>Suporte BitLocker para rotação de senha de recuperação controlada pelo cliente<!--  3444125 -->
Use as configurações do Intune Endpoint Protection para configurar a [rotação de senha de recuperação controlada pelo cliente](../protect/endpoint-protection-windows-10.md#windows-encryption) para o BitLocker em dispositivos que executam o Windows versão 1909 ou posterior.

Essa configuração inicia uma atualização de senha de recuperação controlada pelo cliente após uma recuperação de unidade do sistema operacional (usando o bootmgr ou WinRE) e o desbloqueio de senha de recuperação em uma unidade de dados fixa. Essa configuração atualiza a senha de recuperação específica que foi usada e outras senhas não utilizadas no volume permanecem inalteradas. Para obter mais informações, consulte a documentação do CSP do BitLocker para [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Proteção contra violação para o Windows Defender antivírus<!-- 4705448        -->
Use o Intune para gerenciar a *proteção contra adulterações* para o Windows Defender antivírus. Você encontrará a [configuração de proteção contra violações](../protect/endpoint-protection-windows-10.md#windows-defender-security-center) no grupo da central de segurança do Microsoft defender quando usar perfis de configuração do dispositivo para o Windows 10 Endpoint Protection. Você pode definir a proteção de violação como *habilitada* para ativar as restrições de proteção do Temper, definir *desabilitado* para desativá-las ou definir*não configurado* para deixar a configuração atual de dispositivos em vigor.  

Para obter mais informações sobre a proteção contra violações, consulte [impedir alterações de configurações de segurança com a proteção contra violações](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) na documentação do Windows.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>As configurações avançadas para o Windows Defender firewall já estão disponíveis para o público geral<!--  5317392       -->  
As [regras de firewall personalizadas do Windows Defender para o Endpoint Protection](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), que você configura como parte de um perfil de configuração de dispositivo, estão fora da visualização pública e estão disponíveis para o público geral (GA).  Você pode usar essas regras para especificar o comportamento de entrada e saída para aplicativos, endereços de rede e portas. Essas regras foram lançadas em julho como uma visualização pública. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>As marcas de escopo agora dão suporte a políticas de termos de uso<!-- 2358863 idmiss -->
Agora você pode atribuir [marcas de escopo](scope-tags.md) a políticas de termos de uso. Para fazer isso, acesse **Intune**  > **registro de dispositivo**  > **termos e condições** > escolha um item na lista > **Propriedades**  > **marcas de escopo** > escolha uma marca de escopo.

## <a name="week-of-september-9-2019"></a>Semana de 9 de setembro de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Atualizações para Microsoft Intune aplicativo<!-- 4997846 -->
O aplicativo Microsoft Intune para Android foi atualizado com os seguintes aprimoramentos:
- Atualizado e aprimorado o layout para incluir a navegação inferior para as ações mais importantes.
- Adicionada uma página adicional que mostra o perfil do usuário.
- Adicionada a exibição de notificações acionáveis no aplicativo para o usuário, como a necessidade de atualizar suas configurações de dispositivo.
- Adicionada a exibição de notificações por push personalizadas, alinhando o aplicativo com o suporte adicionado recentemente no aplicativo Portal da Empresa para iOS e Android. Para obter mais informações, consulte [enviar notificações personalizadas no Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa<!-- 4394993 -->
Usando a redução, você pode personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo. Para obter mais informações, consulte [como configurar o aplicativo portal da empresa do Intune](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Semana de 2 de setembro de 2019

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Atualização da interface do usuário do Intune – painel de status do locatário<!-- 5273210  -->
A interface do usuário para o painel de status do locatário foi atualizada para se alinhar com os estilos de interface do usuário do Azure. Para obter mais informações, consulte [status do locatário](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Semana de 26 de agosto de 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Definir configurações do Microsoft Edge usando modelos administrativos para Windows 10 e mais recente<!-- 5228061 -->

No Windows 10 e dispositivos mais recentes, você pode criar modelos administrativos para definir configurações de política de grupo no Intune. Nesta atualização, você pode definir as configurações que se aplicam ao Microsoft Edge versão 77 e mais recentes.

Para saber mais sobre modelos administrativos, confira [usar modelos do Windows 10 para definir configurações de política de grupo no Intune](../configuration/administrative-templates-windows.md).

Aplica-se a:

- Windows 10 e mais recente (Windows RS4 +)

## <a name="week-of-august-12-2019"></a>Semana de 12 de agosto de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Controlar o comportamento de desinstalação do aplicativo iOS no cancelamento do registro do dispositivo<!-- 3504144   -->
Os administradores podem gerenciar se um aplicativo é removido ou mantido em um dispositivo quando o registro do dispositivo é cancelado no nível de um usuário ou de um grupo de dispositivos. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Categorizar Microsoft Store para aplicativos de negócios<!-- 3926922 -->
Você pode categorizar Microsoft Store para aplicativos de negócios. Para fazer isso, escolha **Intune**  > **aplicativos cliente**  > **aplicativos** > selecione um aplicativo Microsoft Store for Business > **informações do aplicativo**  > **categoria**. No menu suspenso, atribua uma categoria.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Notificações personalizadas para usuários do Microsoft Intune app<!-- 4843354  -->
O aplicativo Microsoft Intune para Android agora dá suporte à exibição de notificações por push personalizadas, alinhando-a com o suporte adicionado recentemente nos aplicativos Portal da Empresa para iOS e Android. Para obter mais informações, consulte [enviar notificações personalizadas no Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Novos recursos para dispositivos Android Enterprise dedicados no modo de vários aplicativos<!-- 3755304 3041943 3041946   -->

No Intune, você pode controlar os recursos e as configurações em uma experiência de estilo de quiosque em seus dispositivos Android Enterprise dedicados (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **somente proprietário do dispositivo, restrições de dispositivo** para o tipo de perfil).

Nesta atualização, os seguintes recursos estão sendo adicionados:

- **Dispositivos dedicados** > **vários aplicativos**: o **botão Home virtual** pode ser mostrado passando o dedo para cima no dispositivo ou flutuando na tela para que os usuários possam movê-lo.
- **Dispositivos dedicados** > **vários aplicativos**: o **acesso à lanterna** permite que os usuários usem a lanterna. 
- **Dispositivos dedicados** > **vários aplicativos**: o **controle de volume de mídia** permite que os usuários controlem o volume de mídia do dispositivo usando um controle deslizante. 
- **Dispositivos dedicados** > **vários aplicativos**: **habilitar uma proteção de tela**, carregar uma imagem personalizada e controlar quando a proteção de tela é mostrada.

Para ver as configurações atuais, vá para [configurações do dispositivo Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:

- Dispositivos Android Enterprise dedicados

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Novos perfis de aplicativo e configuração para dispositivos Android Enterprise totalmente gerenciados<!-- 3574215 3574238 3574235 3574232   -->
Usando perfis, você pode definir configurações que aplicam configurações de VPN, email e Wi-Fi aos dispositivos do proprietário do seu dispositivo Android Enterprise (totalmente gerenciado). Nesta atualização, você pode:

- Use [as políticas de configuração de aplicativo](../apps/app-configuration-policies-use-android.md) para implantar as configurações de email do Outlook, do Gmail e noves.
- Use perfis de configuração de dispositivo para implantar [configurações de certificado raiz confiável](../protect/certificates-configure.md).
- Use perfis de configuração de dispositivo para implantar configurações de [VPN](../configuration/vpn-settings-android-enterprise.md) e [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) .

> [!IMPORTANT]
> Com esse recurso, os usuários se autenticam com seu nome de usuário e senha para perfis de VPN, Wi-Fi e de email. Atualmente, a autenticação baseada em certificado não está disponível.

Aplica-se a:  
- Proprietário do dispositivo Android Enterprise (totalmente gerenciado)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Controlar os aplicativos, arquivos, documentos e pastas que são abertos quando os usuários entram em dispositivos macOS<!--3914202   -->
Você pode habilitar e configurar recursos em dispositivos macOS (**configuração do dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > recursos do **dispositivo** para o tipo de perfil). 

Nessa atualização, há uma nova configuração de itens de logon para controlar quais aplicativos, arquivos, documentos e pastas são abertos quando um usuário entra no dispositivo registrado. 

Para ver as configurações atuais, vá para [configurações de recurso de dispositivo MacOS no Intune](../configuration/macos-device-features-settings.md).

Aplica-se a:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Os prazos substituem as configurações de reinicialização envolvidas para Windows Update anéis<!-- 4464404        -->
Para alinhar [as alterações de serviço do Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)recentes, os anéis de atualização do Windows 10 do Intune agora [dão suporte a configurações para prazos](../protect/windows-update-settings.md). Os *prazos* determinam quando um dispositivo instala atualizações de segurança e recursos.  Em dispositivos que executam o Windows 10 1903 ou posterior, os *prazos* substituem as configurações para *reinicialização envolvida*.  No futuro, os *prazos* também substituirão a *reinicialização envolvida* em versões anteriores do Windows 10.  

Quando você não configura os *prazos*, os dispositivos continuam a usar suas configurações de *reinicialização envolvidas* , no entanto, o Intune preterirá o suporte para configurações de reinicialização envolvidas em uma atualização futura.  

Planeje o uso de *prazos* para todos os seus dispositivos Windows 10. Depois que as configurações dos *prazos* estiverem em vigor, você poderá alterar as configurações do Intune para *reinicialização iniciada* para não ser configurada. Quando definido como não configurado, o Intune para de gerenciar essas configurações em dispositivos, mas não remove as últimas configurações da configuração do dispositivo. Portanto, as últimas configurações definidas para *reinicialização iniciada* permanecem ativas e em uso nos dispositivos até que essas configurações sejam modificadas por um método diferente do Intune. Posteriormente, quando a versão dos dispositivos do Windows mudar ou quando o suporte do Intune para *prazos* se expandir para a versão dos dispositivos do Windows, o dispositivo começará a usar as novas configurações, que já estão em vigor.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Suporte para vários conectores de certificado Microsoft Intune<!--   4704642      -->
O Intune agora dá suporte à instalação e ao uso de vários [conectores de certificado Microsoft Intune para operações PKCS](../protect/certficates-pfx-configure.md). Essa alteração dá suporte ao balanceamento de carga e alta disponibilidade do conector. Cada instância de conector pode processar solicitações de certificado do Intune.  Se um conector não estiver disponível, outros conectores continuarão processando solicitações.

Para usar vários conectores, você não precisa atualizar para a versão mais recente do software do conector.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Novas configurações e alterações nas configurações existentes para restringir recursos em dispositivos iOS e macOS<!-- 4867699 4867709   -->
Você pode criar perfis para restringir as configurações em dispositivos que executam iOS e macOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **iOS** ou **MacOS** para tipo de plataforma > **dispositivo restrições**). Essa atualização inclui os seguintes recursos:

- No **macOS** > **restrições de dispositivo** > **nuvem e armazenamento**, use a nova configuração de **entrega** para impedir que os usuários iniciem o trabalho em um dispositivo macOS e continuem trabalhando em outro dispositivo MacOS ou Ios.

  Para ver as configurações atuais, vá para [configurações do dispositivo MacOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-macos.md).

- Em**restrições de dispositivo** >  do **Ios**, há algumas alterações:

  - **Aplicativos internos** > **localizar meu iPhone (somente supervisionado)** : nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - Os **aplicativos internos** > **encontram meus amigos (somente supervisionado)** : nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - **Sem fio** > **modificação do estado de Wi-Fi (somente supervisionado)** : nova configuração que impede que os usuários ativem ou desativem o Wi-Fi no dispositivo.
  - **Teclado e dicionário** > **QuickPath (somente supervisionado)** : nova configuração que bloqueia o recurso QuickPath.
  - **Nuvem e armazenamento**: a **continuação da atividade** é renomeada para **entrega**.

  Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:  
- macOS 10,15 e mais recente
- iOS 13 e mais recente

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Algumas restrições de dispositivo iOS não supervisionadas ficarão supervisionadas somente com a versão iOS 13,0<!-- 4867809   -->
Nessa atualização, algumas configurações se aplicam a dispositivos supervisionados com a versão 13,0 do iOS. Se essas configurações forem configuradas e atribuídas a dispositivos não supervisionados antes da versão 13,0 do iOS, as configurações ainda serão aplicadas a esses dispositivos não supervisionados. Eles ainda se aplicam após a atualização dos dispositivos para iOS 13,0. Essas restrições são removidas em dispositivos não supervisionados que são armazenados em backup e restaurados.

Essas configurações incluem:

- App Store, Visualização de Documentos, Jogos
  - Loja de aplicações
  - Conteúdo explícito do iTunes, música, podcast ou notícias
  - Adicionando Game Center amigos
  - Jogos para vários jogadores
- Aplicações Incorporadas
  - Câmara
    - FaceTime
  - Safari
    - Preenchimento automático
- Cloud e Armazenamento
  - Backup no iCloud
  - Bloquear a sincronização de documentos do iCloud
  - Bloquear sincronização de cadeia de chaves do iCloud

Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:  
- iOS 13,0 e mais recente

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Status do dispositivo melhorado para criptografia macOS FileVault<!-- 4944983         -->
Atualizamos várias das mensagens de [status do dispositivo](../protect/encryption-monitor.md#device-encryption-status) para a criptografia FileVault em dispositivos MacOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Algumas configurações de verificação do Windows Defender antivírus no relatório mostram um status de falha<!-- 5119229 -->
No Intune, você pode criar políticas para usar o Windows Defender antivírus para verificar seus dispositivos Windows 10 **(configuração de dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma >  **Restrições de dispositivo** para o tipo de perfil > **Windows Defender antivírus**). O **tempo para executar uma verificação rápida diária e o** **tipo de verificação do sistema para executar** relatórios mostra um status de falha, quando é, na verdade, um status de êxito. 

Nessa atualização, esse comportamento é fixo. Portanto, o **tempo para executar uma verificação rápida diária** e o **tipo de verificação do sistema para executar** configurações mostra um status de êxito quando as verificações são concluídas com êxito e mostram um status de falha quando as configurações falham ao serem aplicadas.

Para obter mais informações sobre as configurações do Windows Defender antivírus, consulte [configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="default-scope-tags---3702875----"></a>Marcas de escopo padrão<!-- 3702875  -->
Uma nova marca de escopo padrão interna agora está disponível. Todos os objetos do Intune não marcados que dão suporte a marcas de escopo são automaticamente atribuídos à marca de escopo padrão. A marca de escopo **padrão** é adicionada a todas as atribuições de função existentes para manter a paridade com a experiência de administração hoje. Se você não quiser que um administrador Veja objetos do Intune com a marca de escopo padrão, remova a marca de escopo padrão da atribuição de função. Esse recurso é semelhante ao recurso de escopos de segurança no System Center Configuration Manager. Para obter mais informações, consulte [usar o RBAC e marcas de escopo para para distribuí-lo](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Suporte ao administrador do dispositivo de registro do Android<!-- 4869749   -->
A opção de registro de administrador de dispositivo Android foi adicionada à página de registro do Android (**Intune** > **registro de dispositivo** > **registro do Android**). O administrador do dispositivo Android ainda estará habilitado por padrão para todos os locatários.  Para obter mais informações, consulte [registro de administrador do dispositivo Android](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Ignorar mais telas no assistente de configuração <!--4877451  -->
Você pode definir perfis de Programa de registro de dispositivos para ignorar as seguintes telas do assistente de configuração:
- Para iOS
    - Aparência
    - Idioma Express
    - Idioma preferencial
    - Migração de dispositivo para dispositivo
- Para macOS
    - Hora da tela
    - Configuração do touch ID

Para obter mais informações sobre a personalização do assistente de configuração, consulte [criar um perfil de registro da Apple para IOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) e [criar um perfil de registro da Apple para MacOS ](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Adicionar uma coluna de usuário ao processo de carregamento de CSV de dispositivo do AutoPilot<!-- 3823054 -->
Agora você pode adicionar uma coluna de usuário ao upload de CSV para dispositivos do AutoPilot. Isso permite que você atribua usuários em massa no momento em que importar o CSV. Para obter mais informações, consulte [registrar dispositivos Windows no Intune usando o piloto automático do Windows](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Configurar o limite de tempo de limpeza de dispositivo automático para 30 dias<!--4231059  -->
Você pode definir o limite de tempo de limpeza do dispositivo automático como 30 dias (em vez do limite anterior de 90 dias) após a última entrada. Para fazer isso, acesse **Intune** > **dispositivos** > **instalação** > **regras de limpeza de dispositivo**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Número de Build incluído na página de hardware do dispositivo Android<!-- 4461910   -->
Uma nova entrada na página hardware para cada dispositivo Android inclui o número de Build do sistema operacional do dispositivo. Para obter mais informações, consulte [Exibir detalhes do dispositivo no Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Semana de 5 de agosto de 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Pretas Technologies é um OEM com suporte para o OEMConfig em dispositivos Android Enterprise<!-- 4843713 -->

No Intune, você pode criar perfis de configuração de dispositivo e aplicar configurações a dispositivos Android Enterprise usando OEMConfig **(configuração de dispositivo** > **perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **OEMConfig** para o tipo de perfil).

Nessa atualização, o pretas Technologies é um fabricante de equipamento original (OEM) com suporte para o OEMConfig. Para obter mais informações sobre o OEMConfig, consulte [usar e gerenciar dispositivos Android Enterprise com o OEMConfig](../configuration/android-oem-configuration-overview.md).

Aplica-se a:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Semana de 22 de julho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Notificações personalizadas para usuários e grupos<!-- 16766574          -->
Envie notificações por push personalizadas do aplicativo Portal da Empresa para os usuários em dispositivos Android e iOS que você gerencia com o Intune. Essas notificações por push móveis são altamente personalizáveis com texto livre e podem ser usadas para qualquer finalidade. Você pode direcioná-los para grupos de usuários diferentes em sua organização. Para obter mais informações, consulte [notificações personalizadas](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Aplicativo do controlador de política de dispositivo do Google<!-- 3041950  -->
O aplicativo de tela inicial gerenciado agora fornece acesso ao aplicativo de política de dispositivo Android do Google. O aplicativo de tela inicial gerenciado é um iniciador personalizado usado para dispositivos registrados no Intune como dispositivos do Android Enterprise (AE) dedicados usando o modo de quiosque de vários aplicativos. Você pode acessar o aplicativo de política de dispositivo Android ou orientar os usuários para o aplicativo de política de dispositivo Android, para fins de suporte e depuração. Esse recurso de inicialização está disponível no momento em que o dispositivo é registrado e bloqueado na tela inicial gerenciada. Nenhuma instalação adicional é necessária para usar essa funcionalidade.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Configurações de proteção do Outlook para dispositivos iOS e Android<!-- 3212619 -->
Agora você pode definir definições gerais de configuração de aplicativo e de proteção de dados para o Outlook para iOS e Android usando controles simples de administrador do Intune sem registro de dispositivo. As definições gerais de configuração de aplicativo fornecem paridade com as configurações que os administradores podem habilitar ao gerenciar o Outlook para iOS e Android em dispositivos registrados. Para obter mais informações sobre as configurações do Outlook, consulte [implantando definições de configuração de aplicativo do Outlook para IOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Use "regras de aplicabilidade" ao criar perfis de configuração de dispositivo do Windows 10 <!-- 2549910 eeready   idstaged -->

Você cria perfis de configuração de dispositivo do Windows 10 (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Windows 10** para **regras de aplicabilidade**de > de plataforma). Nessa atualização, você pode criar uma **regra de aplicabilidade** para que o perfil se aplique somente a uma edição específica ou a uma versão específica. Por exemplo, você cria um perfil que habilita algumas configurações do BitLocker. Depois de adicionar o perfil, use uma regra de aplicabilidade para que o perfil se aplique somente a dispositivos que executam o Windows 10 Enterprise.

Para adicionar uma regra de aplicabilidade, consulte [regras de aplicabilidade](../configuration/device-profile-create.md#applicability-rules).

Aplica-se a: Windows 10 e posterior

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Usar tokens para adicionar informações específicas do dispositivo em perfis personalizados para dispositivos iOS e macOS<!-- 3330008  -->
Você pode usar perfis personalizados em dispositivos iOS e macOS para definir configurações e recursos não internos no Intune (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** ou **MacOS** para plataforma > **Personalizado** para o tipo de perfil). Nessa atualização, você pode adicionar tokens aos arquivos `.mobileconfig` para adicionar informações específicas do dispositivo. Por exemplo, você pode adicionar `Serial Number: {{serialnumber}}` ao arquivo de configuração para mostrar o número de série do dispositivo.

Para criar um perfil personalizado, consulte [configurações](../configuration/custom-settings-ios.md) personalizadas do Ios ou [configurações personalizadas do MacOS](../configuration/custom-settings-macos.md).

Aplica-se a:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Novo designer de configuração ao criar um perfil de OEMConfig para Android Enterprise<!-- 3712769   -->
No Intune, você pode criar um perfil de configuração de dispositivo que usa um aplicativo OEMConfig (configuração de dispositivo > perfis > Criar perfil > Android Enterprise para plataforma > OEMConfig para o tipo de perfil). Quando você faz isso, um editor de JSON é aberto com um modelo e valores para que você altere. 

Essa atualização inclui um designer de configuração com uma experiência de usuário aprimorada que mostra detalhes inseridos no aplicativo, incluindo títulos, descrições e muito mais. O editor de JSON ainda está disponível e mostra as alterações feitas no designer de configuração.

Para ver as configurações atuais, vá para [usar e gerenciar dispositivos Android Enterprise com o OEMConfig](../configuration/android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Interface do usuário atualizada para configurar o Windows Hello<!-- 4089576            -->
Atualizamos o console do onde você [configura o Intune para usar o Windows Hello para empresas](../protect/windows-hello.md). Agora, todos os parâmetros de configuração estão disponíveis no mesmo painel do console em que você habilita o suporte para o Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>SDK do Intune PowerShell<!-- 4924113 --> 
O SDK do PowerShell do Intune, que fornece suporte para a API do Intune por meio do Microsoft Graph, foi atualizado para a versão 6.1907.1.0. O SDK agora dá suporte ao seguinte:
- Funciona com a automação do Azure.
- Dá suporte a operações de leitura de autenticação somente de aplicativo. 
- Dá suporte a nomes abreviados amigáveis como aliases.
- Está em conformidade com as convenções de nomenclatura do PowerShell. Especificamente, o parâmetro `PSCredential` (no cmdlet `Connect-MSGraph`) foi renomeado para `Credential`.
- Dá suporte à especificação manual do valor do cabeçalho `Content-Type` ao usar o cmdlet `Invoke-MSGraphRequest`.

Para obter mais informações, consulte [SDK do PowerShell para Microsoft Intune API do Graph](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Atualizações para restrições de registro<!-- 2871968 -->
As restrições de registro para novos locatários foram atualizadas para que os perfis de trabalho do Android Enterprise sejam permitidos por padrão. Os locatários existentes não sofrerão alteração. Para usar perfis de trabalho do Android Enterprise, você ainda precisa [conectar sua conta do Intune à sua conta de Google Play gerenciada](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Atualizações de interface do usuário para registro da Apple e restrições de registro<!--4089575, 4089579  -->
Ambos os processos a seguir usam uma interface do usuário de estilo de assistente:
- Registro de dispositivo da Apple. Para obter mais informações, consulte [registrar automaticamente dispositivos IOS com o programa de registro de dispositivos da Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Criação de restrição de registro. Para obter mais informações, consulte [definir restrições de registro](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Manipulando a pré-configuração de identificadores de dispositivos corporativos para dispositivos Android Q<!-- 4711509  idmiss -->
No Android Q (V10), o Google removerá a capacidade de agentes de MDM em dispositivos Android gerenciados por legado (administrador do dispositivo) para coletar informações de identificador de dispositivo.  O Intune tem um recurso que permite que os administradores de ti [configurem previamente uma lista de números de série de dispositivos ou IMEIs](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) para marcar automaticamente esses dispositivos como corporativos. Esse recurso não funcionará para dispositivos Android Q gerenciados pelo administrador do dispositivo.  Independentemente de o número de série ou IMEI do dispositivo ser carregado, ele sempre será considerado pessoal durante o registro do Intune.  Você pode alternar manualmente a propriedade para o corporativo após o registro.  Isso afeta apenas os novos registros e os dispositivos registrados existentes não são afetados.  Dispositivos Android gerenciados com perfis de trabalho não são afetados por essa alteração e continuarão funcionando como fazem hoje.  Além disso, os dispositivos Android Q registrados como administrador do dispositivo não poderão mais reportar o número de série ou IMEI no console do Intune como propriedades do dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Os ícones foram alterados para registros corporativos do Android (perfil de trabalho, dispositivos dedicados e dispositivos totalmente gerenciados)<!-- 4977730 -->
Os ícones para perfis de registro do Android Enterprise foram alterados. Para ver os novos ícones, vá para **Intune** > **registro** > **registro do Android** > Procure em **perfis de registro**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Alteração de coleta de dados de diagnóstico do Windows<!-- 4113859 -->
O valor padrão para coleta de dados de diagnóstico foi alterado para dispositivos que executam o Windows 10, versão 1903 e posterior. A partir do Windows 10 1903, a coleta de dados de diagnóstico é habilitada por padrão. Os dados de diagnóstico do Windows são dados técnicos vitais de dispositivos Windows sobre o dispositivo e como o Windows e o software relacionado estão sendo executados. Para obter mais informações, consulte [configurar dados de diagnóstico do Windows em sua organização](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Os dispositivos de piloto automático também são aceitos na telemetria "completa", a menos que definido de outra forma no perfil do AutoPilot com [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="improve-device-location---3855417----"></a>Melhorar o local do dispositivo<!-- 3855417  -->
Você pode ampliar as coordenadas exatas de um dispositivo usando a ação **Localizar dispositivo** . Para obter mais informações sobre como localizar dispositivos iOS perdidos, consulte [localizar dispositivos IOS perdidos](../remote-actions/device-locate.md).

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Configurações avançadas do Windows Defender firewall (visualização pública)<!--  1311949     -->  
Use o Intune para gerenciar [regras de firewall personalizadas como parte de um perfil de configuração de dispositivo para o](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) Endpoint Protection no Windows 10. As regras podem especificar o comportamento de entrada e saída para aplicativos, endereços de rede e portas. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Interface do usuário atualizada para gerenciar linhas de base de segurança<!-- 4091125     -->
Atualizamos a [experiência de criação e edição](../protect/security-baselines.md#create-the-profile) no console do Intune para nossas linhas de base de segurança. As alterações incluem:

Um formato de estilo de assistente mais simples, que é condensado para uma única folha. dentro de uma folha. Esse novo design desaparece com a expansão da folha que exige que os profissionais de ti se aprofundem em vários painéis separados.  
Agora você pode criar atribuições como parte da experiência de criação e edição, em vez de ter que retornar posteriormente para atribuir linhas de base. Adicionamos um resumo das configurações que você pode exibir antes de criar uma nova linha de base e ao editar uma existente. Ao editar, o resumo mostra apenas a lista de itens definidos dentro de uma categoria de propriedades que estão sendo editadas.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Semana de 15 de julho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Tela inicial gerenciada e ícones de configurações gerenciadas<!-- 4918107 -->
O ícone do aplicativo de tela inicial gerenciado e o ícone de **configurações gerenciadas** foram atualizados. O aplicativo de tela inicial gerenciado só é usado por dispositivos registrados no Intune como dispositivos dedicados do Android Enterprise (AE) e executados em modo de quiosque com vários aplicativos. Para obter mais informações sobre o aplicativo de tela inicial gerenciado, consulte [Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Política de dispositivo Android em dispositivos Android Enterprise dedicados<!-- 4918136 -->
Você pode acessar o aplicativo de política de dispositivo Android na tela de depuração do aplicativo de tela inicial gerenciada. O aplicativo de tela inicial gerenciado só é usado por dispositivos registrados no Intune como dispositivos dedicados do Android Enterprise (AE) e executados em modo de quiosque com vários aplicativos. Para obter mais informações, consulte [Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>atualizações de Portal da Empresa do iOS<!-- 3902931 -->
O nome da sua empresa nos prompts de gerenciamento de aplicativo iOS substituirá o texto atual "i.manage.microsoft.com". Por exemplo, os usuários verão o nome da empresa em vez de "i.manage.microsoft.com" quando os usuários tentarem instalar um aplicativo iOS do Portal da Empresa ou quando os usuários permitirem o gerenciamento do aplicativo. Isso será distribuído para todos os clientes durante os próximos dias.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Gerenciar FileVault para macOS<!--  3858502 + 4557986 + 1210104  -->
Você pode usar o Intune para [gerenciar a criptografia de chave FileVault para dispositivos MacOS](../protect/encrypt-devices.md). Para criptografar dispositivos, use um perfil de configuração de dispositivo do Endpoint Protection.

Nosso suporte para FileVault inclui criptografia de dispositivos não criptografados, caução de uma chave de recuperação pessoal de dispositivos, rotação automática ou manual de chaves de criptografia pessoais e recuperação de chave para seus dispositivos corporativos. Os usuários finais também podem usar o site Portal da Empresa para obter a chave de recuperação pessoal para seus dispositivos criptografados.

Também expandimos o relatório de criptografia para incluir [informações sobre](../protect/encryption-monitor.md) as informações no lado do FileVault para o BitLocker, para que você possa exibir todos os detalhes de criptografia do dispositivo em um único lugar.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>A redefinição do Windows AutoPilot remove o usuário principal do dispositivo<!-- 4156123 -->
Quando a redefinição do AutoPilot é usada em um dispositivo, o usuário primário do dispositivo será removido. O próximo usuário que entrar após a redefinição será definido como o usuário primário. Este recurso será distribuído para todos os clientes durante os próximos dias.

## <a name="week-of-july-8-2019"></a>Semana de 8 de julho de 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Novas configurações do Office, do Windows e do OneDrive nos modelos administrativos do Windows 10 <!-- 3510695 -->

Você pode criar modelos administrativos no Intune que imitam o gerenciamento de política de grupo local (**Gerenciamento de dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma >  **Modelo administrativo** para tipo de perfil).

Essa atualização inclui mais configurações do Office, do Windows e do OneDrive que você pode adicionar aos seus modelos. Com essas novas configurações, agora você pode definir mais de 2500 configurações que são 100% baseadas em nuvem.

Para saber mais sobre esse recurso, consulte [usar modelos do Windows 10 para definir configurações de política de grupo no Intune](../configuration/administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

## <a name="week-of-july-1-2019"></a>Semana de 1º de julho de 2019 

### <a name="app-management"></a>Gestão de aplicações

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD e aplicativo em dispositivos Android Enterprise<!-- 3574267 -->
Ao integrar dispositivos Android Enterprise totalmente gerenciados, os usuários agora serão registrados com o Azure Active Directory (AAD) durante a configuração inicial de seu dispositivo novo ou de redefinição de fábrica. Anteriormente para um dispositivo totalmente gerenciado, após a conclusão da instalação, o usuário precisava iniciar manualmente o aplicativo Microsoft Intune para iniciar o registro do AAD. Agora, quando o usuário chega no dispositivo home page após a configuração inicial, o dispositivo é registrado e inscrito.

Além das atualizações do AAD, as políticas de proteção de aplicativo do Intune (aplicativo) agora têm suporte em dispositivos Android Enterprise totalmente gerenciados. Essa funcionalidade ficará disponível à medida que for distribuída. Para obter mais informações, consulte [adicionar aplicativos gerenciados Google Play a dispositivos Android Enterprise com o Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Semana de 24 de junho de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Configurar qual navegador tem permissão para vincular aos dados da organização<!-- 3145939 -->
As políticas de Proteção de Aplicativo do Intune (aplicativo) em dispositivos Android e iOS agora permitem transferir links da Web da organização para um navegador específico além do Intune Managed Browser ou do Microsoft Edge.  Para obter mais informações sobre o aplicativo, consulte [o que são políticas de proteção de aplicativo?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>A página todos os aplicativos identifica Microsoft Store online/offline para aplicativos de negócios<!--4089647 -->
A página **todos os aplicativos** agora inclui rótulos para identificar aplicativos Microsoft Store for Business (MSFB) como aplicativos online ou offline. Cada aplicativo MSFB agora inclui um sufixo para **online** ou **offline**. A página de detalhes do aplicativo também inclui o **tipo de licença** e **dá suporte** a informações de instalação de contexto de dispositivo (somente aplicativos licenciados offline).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Portal da Empresa aplicativo em dispositivos compartilhados do Windows<!--4393553 -->
Agora, os usuários podem acessar o aplicativo Portal da Empresa em dispositivos compartilhados do Windows. Os usuários finais verão um rótulo **compartilhado** no bloco do dispositivo. Isso se aplica ao aplicativo Windows Portal da Empresa versão 10.3.45609.0 e posterior.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Exibir todos os aplicativos instalados da página da Web do New Portal da Empresa<!-- 4224326 -->
A página novos **aplicativos instalados** do portal da empresa site lista todos os aplicativos gerenciados (necessários e disponíveis) que estão instalados nos dispositivos de um usuário. Além do tipo de atribuição, os usuários podem ver o editor do aplicativo, a data de publicação e o status da instalação atual. Se você não tiver feito aplicativos necessários ou disponíveis para seus usuários, eles verão uma mensagem explicando que nenhum aplicativo da empresa foi instalado. Para ver a nova página na Web, acesse o [site do portal da empresa](https://portal.manage.microsoft.com) e clique em **aplicativos instalados**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>Nova exibição permite que os usuários do aplicativo vejam todos os aplicativos gerenciados instalados no dispositivo<!-- 2352913 -->  
O aplicativo Portal da Empresa para Windows agora lista todos os aplicativos gerenciados (necessários e disponíveis) que estão instalados no dispositivo de um usuário. Os usuários também podem ver tentativas e instalações de Aplicativos pendentes e seus status atuais. Se você não tiver feito aplicativos necessários ou disponíveis para seus usuários, eles verão uma mensagem explicando que nenhum aplicativo da empresa foi instalado. Para ver a nova exibição, vá para o painel de navegação Portal da Empresa e selecione **aplicativos** > **aplicativos instalados**.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Definir configurações para extensões de kernel em dispositivos macOS<!-- 2043024 -->
Em dispositivos macOS, você pode criar um perfil de configuração de dispositivo (**configuração do dispositivo** > **perfis** > **Criar perfil** > escolher **MacOS** para plataforma). Essa atualização inclui um novo grupo de configurações que permitem configurar e usar extensões de kernel em seus dispositivos. Você pode adicionar extensões específicas ou permitir todas as extensões de um parceiro ou desenvolvedor específico.

Para saber mais sobre esse recurso, consulte [visão geral das extensões do kernel](../configuration/kernel-extensions-overview-macos.md) e [configurações de extensão do kernel](../configuration/kernel-extensions-settings-macos.md).

Aplica-se a: macOS 10.13.2 e posterior

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Os aplicativos da configuração armazenar somente para dispositivos Windows 10 incluem mais opções de configuração<!-- 2697002 -->
Ao criar um perfil de restrições de dispositivo para dispositivos Windows, você pode usar os **aplicativos da configuração armazenar somente** para que os usuários instalem apenas os aplicativos da Windows Store (**configuração do dispositivo** > **perfis** > **criar Perfil** > **Windows 10 e posterior** para plataforma > **restrições de dispositivo** para o tipo de perfil). Nessa atualização, essa configuração é expandida para dar suporte a mais opções.

Para ver a nova configuração, vá para [configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos](../configuration/device-restrictions-windows-10.md#app-store).

Aplica-se a: Windows 10 e posterior

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Implantar vários perfis de dispositivo do pretas Mobility Extensions em um dispositivo, mesmo grupo de usuários ou no mesmo grupo de dispositivos<!-- 4089955 -->
No Intune, você pode usar o MX (pretas Mobility Extensions) em um perfil de configuração de dispositivo para personalizar as configurações de dispositivos pretas que não são internos no Intune. No momento, você pode implantar um perfil em um único dispositivo. Nesta atualização, você pode implantar vários perfis para:
- O mesmo grupo de usuários
- O mesmo grupo de dispositivos
- Um único dispositivo

[Use e gerencie dispositivos pretas com as extensões de mobilidade do pretas no Microsoft Intune](../configuration/android-zebra-mx-overview.md) mostra como usar o MX no Intune.

Aplica-se a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Algumas configurações de quiosque em dispositivos iOS são definidas usando "bloquear", substituindo "permitir"<!-- 4404075  -->
Quando você cria um perfil de restrições de dispositivo em dispositivos iOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **quiosque** ), você define o **bloqueio automático**, o **comutador de toque**, a **rotação de tela**, o botão de suspensão da **tela**e os **botões de volume**.

Nessa atualização, os valores são **Block** (bloqueia o recurso) e **não configurados** (permite o recurso). Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos](../configuration/device-restrictions-ios.md#kiosk).

Aplica-se a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Usar ID facial para autenticação de senha em dispositivos iOS<!-- 4490704 -->
Ao criar um perfil de restrições de dispositivo para dispositivos iOS, você pode usar uma impressão digital para uma senha. Nessa atualização, as configurações de senha de impressão digital também permitem o reconhecimento facial (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o perfil Digite > **senha**). Como resultado, as seguintes configurações foram alteradas:

- O **desbloqueio de impressão digital** agora é **ID de toque e desbloqueio de ID facial**.
- A **modificação de impressão digital (somente supervisionado)** agora é a **ID de toque e a modificação da ID de face (somente supervisionado)** .

A ID de face está disponível no iOS 11,0 e posterior. Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md#password).

Aplica-se a: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Restringir os recursos de jogos e da loja de aplicativos em dispositivos iOS agora depende da região de classificações<!-- 4593948 -->
Em dispositivos iOS, você pode permitir ou restringir recursos relacionados a jogos, à loja de aplicativos e à exibição de documentos (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios** para o dispositivo > de plataforma  **restrições** para o tipo de perfil > **loja de aplicativos, exibição de documento, jogos**). Você também pode escolher a região de classificações, como a Estados Unidos.

Nessa atualização, o recurso de **aplicativos** é movido para ser um filho para a **região de classificações**e depende da **região de classificações**. Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Suporte do Windows AutoPilot para ingresso híbrido no Azure AD<!-- 4809146-->
O Windows AutoPilot para dispositivos existentes agora dá suporte à junção híbrida do Azure AD (além do suporte existente para ingresso no Azure AD). Aplica-se aos dispositivos Windows 10 versão 1809 e acima. Para obter mais informações, consulte [Windows AutoPilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Consulte o nível de patch de segurança para dispositivos Android<!-- 4461911 -->
Agora você pode ver o nível de patch de segurança para dispositivos Android. Para fazer isso, escolha o **Intune** > **dispositivos** > **todos os dispositivos** > escolha um dispositivo > **hardware**.
O nível do patch está listado na seção **sistema operacional** .

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Atribuir marcas de escopo a todos os dispositivos gerenciados em um grupo de segurança<!-- 3173810 -->
Agora você pode atribuir marcas de escopo a um grupo de segurança e todos os dispositivos no grupo de segurança também serão associados a essas marcas de escopo. Todos os dispositivos nesses grupos também serão atribuídos à marca de escopo. As marcas de escopo definidas com esse recurso substituirão as marcas de escopo definidas com o fluxo atual de marcas de escopo do dispositivo. Para obter mais informações, consulte [usar RBAC e marcas de escopo para distribuí-lo](scope-tags.md).

### <a name="device-security"></a>Segurança do dispositivo

#### <a name="use-keyword-search-with-security-baselines------"></a>Usar pesquisa de palavra-chave com linhas de base de segurança<!--  -->
Ao criar ou editar [perfis de linha de base de segurança](../protect/security-baselines.md#create-the-profile), você pode especificar palavras-chave na nova barra de *pesquisa* para filtrar os grupos de configurações disponíveis para aqueles que contêm seus critérios de pesquisa.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>O recurso de linhas de base de segurança agora está disponível para o público geral<!-- 3785395 -->
O recurso de **linhas de base de segurança** está fora de visualização e agora está disponível para o público geral (GA).  Isso significa que o recurso está pronto para uso na produção. No entanto, os modelos de linha de base individuais podem permanecer na versão prévia e serem avaliados e liberados para GA em suas próprias agendas.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>O modelo de linha de base de segurança do MDM já está disponível ao público geral<!-- 3794072, 4217151,  3534649 -->
O modelo de linha de base de segurança do MDM foi removido da visualização e agora está disponível para o público geral (GA). O modelo GA é identificado como a **linha de base de segurança do MDM para maio de 2019**.  Esse é um novo modelo e não uma atualização da versão de visualização.  Como um novo modelo, você precisará examinar as [configurações que ele contém](../protect/security-baseline-settings-mdm.md)e, em seguida, criar novos perfis para implantar o modelo em seu dispositivo. Outros modelos de linha de base de segurança podem permanecer em versão prévia. Para obter uma lista de linhas de base disponíveis, consulte [linhas de base de segurança disponíveis](../protect/security-baselines.md#available-security-baselines).  

Além de ser um novo modelo, a *linha de base de segurança do MDM para o modelo de maio de 2019* inclui as duas configurações que anunciamos recentemente em nosso artigo em desenvolvimento:  
- Bloqueio acima: Ativar voz de aplicativos de uma tela bloqueada  
- DeviceGuard: usar a VBS (segurança baseada em virtualização) na próxima reinicialização dos dispositivos.  

A *linha de base de segurança do MDM para maio de 2019* também inclui a adição de várias novas configurações, a remoção de outras e uma revisão do valor padrão de uma configuração. Para obter uma lista detalhada das alterações de visualização para GA, consulte **o que mudou no novo modelo**.

#### <a name="security-baseline-versioning---3194322---"></a>Controle de versão de linha de base de segurança<!-- 3194322 -->
Linhas de base de segurança para o suporte do Intune controle de versão. Com esse suporte, à medida que novas versões de cada linha de base de segurança são liberadas, você pode atualizar seus perfis de linha de base de segurança existentes para usar a versão de linha de base mais recente sem precisar recriar e implantar uma nova linha de base do zero. Além disso, no console do Intune, você pode exibir informações sobre cada linha de base, como o número de perfis individuais que usa a linha de base, quantas versões de linha de base são usadas por seus perfis e quando a versão mais recente de uma segurança específica a linha de base foi.  Para obter mais informações, consulte **linhas de base de segurança**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>A configuração usar chaves de segurança para entrada foi movida<!-- 4501151 -->
A definição de configuração do dispositivo para a proteção de identidade chamada **usar chaves de segurança para entrar** não é mais encontrada como uma subconfiguração de *Configurar o Windows Hello para empresas*. Agora é uma configuração de nível superior que está sempre disponível, mesmo quando você não habilita o uso do Windows Hello para empresas. Para obter mais informações, consulte [proteção de identidade](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Novas permissões para administradores de grupo atribuídos<!-- 4504437   -->
A função interna de administrador da escola do Intune agora tem permissões CRUD (criar, ler, atualizar e excluir) para aplicativos gerenciados. Essa atualização significa que, se você estiver atribuído como um administrador de grupo no Intune para Educação, agora poderá criar, exibir, atualizar e excluir os MDM Push Certificate do iOS, tokens de servidor MDM do iOS e tokens VPP do iOS, juntamente com [todas as permissões existentes que você tem](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Para executar qualquer uma dessas ações, vá para **configurações de locatário** > **Gerenciamento de dispositivo IOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Os aplicativos podem usar o API do Graph para chamar operações de leitura sem credenciais de usuário<!-- 4655885 -->
Os aplicativos podem chamar o Intune API do Graph operações de leitura com a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Aplicar marcas de escopo a Microsoft Store para aplicativos de negócios<!-- 4392555 -->
Agora você pode aplicar marcas de escopo a Microsoft Store para aplicativos de negócios. Para obter mais informações sobre marcas de escopo, consulte [usar o controle de acesso baseado em função (RBAC) e marcas de escopo para distribuí-lo](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Semana de 17 de junho de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-features-in-microsoft-intune-app"></a>Novos recursos no aplicativo Microsoft Intune
Adicionamos novos recursos ao aplicativo Microsoft Intune (versão prévia) para Android. Os usuários em dispositivos Android totalmente gerenciados agora podem:  

* Exiba e gerencie os dispositivos registrados por meio do Portal da Empresa do Intune ou Microsoft Intune aplicativo.
* Entre em contato com a organização para obter suporte.
* Envie seus comentários para a Microsoft.
* Exiba os termos e condições, se definido por sua organização.

## <a name="week-of-june-10-2019"></a>Semana de 10 de junho de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Novos aplicativos de exemplo mostrando a integração do SDK do Intune disponível no GitHub<!-- 2653471 -->
A conta do GitHub msintuneappsdk adicionou novos aplicativos de exemplo para iOS (Swift), Android, Xamarin. iOS, Xamarin Forms e Xamarin. Android. Esses aplicativos destinam-se a complementar nossa documentação existente e fornecem demonstrações de como integrar o SDK de aplicativos do Intune em seus próprios aplicativos móveis. Se você for um desenvolvedor de aplicativos que precisa de diretrizes adicionais do SDK do Intune, consulte os seguintes exemplos vinculados:
- [Chat](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) -um aplicativo de mensagens instantâneas Ios (Swift) nativo que usa a Adal (biblioteca de autenticação Azure Active Directory) para autenticação orientada.
- [Tasker](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) -um aplicativo de lista de tarefas do Android nativo que usa a Adal para autenticação orientada.
- [Tasker](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) -um aplicativo de lista de tarefas do Xamarin. Android que usa a Adal para autenticação orientada, esse repositório também tem o aplicativo Xamarin. Forms.
- [Aplicativo de exemplo do xamarin. Ios](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – um aplicativo de exemplo básicas Xamarin. Ios.

## <a name="week-of-may-27-2019"></a>Semana de 27 de maio de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Relatórios de aplicativos potencialmente prejudiciais em dispositivos Android<!-- 4223162 -->
O Intune agora fornece informações de relatório adicionais sobre aplicativos potencialmente prejudiciais em dispositivos Android. 

## <a name="week-of-may-20-2019"></a>Semana de 20 de maio de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="windows-company-portal-app---3316993---"></a>Aplicação do Portal da Empresa do Windows<!-- 3316993 -->
O aplicativo Windows Portal da Empresa agora terá uma nova página rotulada **dispositivos**. A página **dispositivos** mostrará os usuários finais todos os seus dispositivos registrados. Os usuários verão essa alteração na Portal da Empresa quando usarem a versão 10.3.4291.0 e posterior. Para obter informações sobre como configurar o Portal da Empresa, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nome do atributo NúmeroDoPedido do dispositivo AutoPilot alterado para a marca de grupo <!-- 4659453 -->

Para torná-lo mais intuitivo, o nome do atributo **NúmeroDoPedido** em dispositivos AutoPilot foi alterado para a **marca de grupo**. Ao usar o CSVs para carregar as informações do dispositivo AutoPilot, você deve usar a marca Group como o cabeçalho da coluna, não OrderID.  

## <a name="week-of-may-13-2019"></a>Semana de 13 de maio de 2019

### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>As políticas do Intune atualizam o método de autenticação e Portal da Empresa instalação do aplicativo<!-- 1927359  -->
Em dispositivos já registrados por meio do assistente de configuração por meio de um dos métodos de registro de dispositivo corporativo da Apple, o Intune não dará mais suporte ao Portal da Empresa quando ele é instalado manualmente pelos usuários finais da loja de aplicativos. Essa alteração só é relevante quando você se autentica com o assistente de configuração da Apple durante o registro. Essa alteração também afeta apenas os dispositivos iOS registrados por meio de:  
* Configurador da Apple

* Gerente de negócios da Apple

* Gestor Escolar da Apple

* Apple Programa de registro de dispositivos (DEP)

Se os usuários instalarem o aplicativo Portal da Empresa da App Store e tentarem registrar esses dispositivos por meio dele, eles receberão um erro. Esses dispositivos deverão usar apenas o Portal da Empresa quando ele for enviado por push, automaticamente, pelo Intune durante o registro. Os perfis de registro no Intune no portal do Azure serão atualizados para que você possa especificar como os dispositivos são autenticados e se eles receberão o aplicativo Portal da Empresa. Se você quiser que os usuários do dispositivo DEP tenham o Portal da Empresa, será necessário especificar suas preferências em um perfil de registro. 

Além disso, a tela **identificar seu dispositivo** no portal da empresa do IOS está sendo removida. Portanto, os administradores que desejam habilitar o acesso condicional ou implantar aplicativos da empresa devem atualizar o perfil de registro do DEP. Esse requisito só se aplicará se o registro de DEP for autenticado com o assistente de configuração. Nesse caso, você deve enviar o Portal da Empresa para o dispositivo. Para fazer isso, escolha **Intune**  > **registro de dispositivo**  > **registro da Apple**  > **tokens do programa de registro** > escolha um token > **perfis** > escolha um perfil > **Propriedades** > conjunto  **Instale Portal da Empresa** em **Sim**.

Para instalar o Portal da Empresa em dispositivos DEP já registrados, você precisará acessar os aplicativos cliente do Intune > e enviá-los como um aplicativo gerenciado com as políticas de configuração de aplicativo. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Configurar como os usuários finais atualizam um aplicativo de linha de negócios (LOB) usando uma política de proteção de aplicativo<!-- 3568384 -->
Agora você pode configurar onde os usuários finais podem obter uma versão atualizada de um aplicativo de linha de negócios (LOB). Os usuários finais verão esse recurso na caixa de diálogo de inicialização condicional **versão do aplicativo mín** , que solicitará que os usuários finais atualizem para uma versão mínima do aplicativo LOB. Você deve fornecer esses detalhes de atualização como parte de sua política de proteção de aplicativo LOB (aplicativo). Esse recurso está disponível no iOS e no Android. No iOS, esse recurso requer que o aplicativo seja integrado (ou encapsulado usando a ferramenta de encapsulamento) com o SDK do Intune para iOS v. 10.0.7 ou superior. No Android, esse recurso exigiria a Portal da Empresa mais recente. Para configurar como um usuário final atualiza um aplicativo LOB, o aplicativo precisa de uma política de configuração de aplicativo gerenciado enviada a ele com a chave, `com.microsoft.intune.myappstore`. O valor enviado definirá a qual armazenamento o usuário final fará o download do aplicativo. Se o aplicativo for implantado por meio do Portal da Empresa, o valor deverá ser `CompanyPortal`. Para qualquer outro armazenamento, você deve inserir uma URL completa.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Scripts do PowerShell de extensão de gerenciamento do Intune<!-- 3734186  -->
Você pode configurar scripts do PowerShell para serem executados com os privilégios de administrador do usuário no dispositivo. Para obter mais informações, consulte [usar scripts do PowerShell em dispositivos Windows 10 no Intune](../apps/intune-management-extension.md) e gerenciamento de aplicativos do [Win32](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Gerenciamento de aplicativo empresarial do Android<!-- 4459905 -->
Para facilitar para os administradores de ti configurar e usar o gerenciamento do Android Enterprise, o Intune adicionará automaticamente quatro aplicativos comuns do Android Enterprise ao console de administração do Intune. Os quatro aplicativos do Android Enterprise são os seguintes aplicativos:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** -usados para cenários totalmente gerenciados do Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -ajuda você a entrar em suas contas se usar a verificação de dois fatores.
- **[Portal da empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** -usado para as políticas de proteção de aplicativo (aplicativo) e cenários de perfil de trabalho do Android Enterprise.
- [Tela inicial gerenciada](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -usada para cenários do Android Enterprise dedicado/quiosque.

Anteriormente, os administradores de ti precisariam localizar e aprovar manualmente esses aplicativos no [repositório de Google Play gerenciado](https://play.google.com/store/apps) como parte da instalação. Essa alteração remove as etapas manuais anteriores para tornar mais fácil e rápido para os clientes usarem o gerenciamento do Android Enterprise.

Os administradores verão esses quatro aplicativos automaticamente adicionados à lista de aplicativos do Intune no momento em que eles conectam seu locatário do Intune pela primeira vez a Google Play gerenciadas. Para obter mais informações, consulte [conectar sua conta do Intune à sua conta do Google Play gerenciado](../enrollment/connect-intune-android-enterprise.md). Para locatários que já conectaram seu locatário ou que já usam o Android Enterprise, não há nada que os administradores precisem fazer. Esses quatro aplicativos aparecerão automaticamente dentro de 7 dias após a conclusão da distribuição do serviço de maio de 2019.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Conector de certificado PFX atualizado para Microsoft Intune<!-- 1533038 -->
Lançamos uma atualização para o [conector de certificado pfx para Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) que aborda um problema em que os certificados PFX existentes continuam a ser reprocessados, o que faz com que o conector pare de processar novas solicitações.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Tarefas de segurança do Intune para o defender ATP (em visualização pública)<!-- 3208597 -->
Na visualização pública, você pode usar o Intune para gerenciar [tarefas de segurança para a ATP (proteção avançada contra ameaças) do Microsoft defender](../protect/atp-manage-vulnerabilities.md). Essa integração com ATP e adiciona uma abordagem baseada em risco para descobrir, priorizar e corrigir vulnerabilidades de ponto de extremidade e configurações incorretas, reduzindo o tempo entre a descoberta e a mitigação.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Verificar um chipset TPM em uma política de conformidade de dispositivo do Windows 10<!-- 3617671   idstaged-->
Muitos dispositivos Windows 10 e posteriores têm chipsets Trusted Platform Module (TPM). Essa atualização inclui uma nova configuração de conformidade que verifica a versão do chip do TPM no dispositivo.

[As configurações de política de conformidade do Windows 10 e posteriores](../protect/compliance-policy-create-windows.md#device-security) descrevem essa configuração.

Aplica-se a: Windows 10 e posterior

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Impedir que os usuários finais modifiquem seus HotSpots pessoais e desabilitem o log do servidor Siri em dispositivos iOS<!-- 4097904   -->  
Você cria um perfil de restrições de dispositivo no dispositivo iOS (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil). Essa atualização inclui novas configurações que você pode configurar:

- **Aplicativos internos**: log do lado do servidor para comandos Siri
- **Sem fio**: modificação do usuário de hotspot pessoal (somente supervisionado)

Para ver essas configurações, vá para [configurações de aplicativo interno para IOS](../configuration/device-restrictions-ios.md#built-in-apps) e [configurações sem fio para IOS](../configuration/device-restrictions-ios.md#wireless).

Aplica-se a: iOS 12,2 e mais recente

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Novas configurações de restrição de dispositivo de aplicativo de sala de aula para dispositivos macOS<!-- 4097905   --> 
Você pode criar perfis de configuração de dispositivo para dispositivos macOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **restrições de dispositivo** para o tipo de perfil). Essa atualização inclui novas configurações de aplicativo de sala de aula, a opção de bloquear capturas de tela e a opção de desabilitar a biblioteca de fotos do iCloud.

Para ver as configurações atuais, vá para [configurações do dispositivo MacOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-macos.md).

Aplica-se a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>A configuração de senha do iOS para acessar a loja de aplicativos foi renomeada<!-- 4557891  -->
A configuração **senha para acessar a loja de aplicativos** é renomeada para exigir a **senha da iTunes Store para todas as compras** (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **Restrições de dispositivo** para o tipo de perfil > **loja de aplicativos, exibição de documento e jogos**).

Para ver as configurações disponíveis, vá para [loja de aplicativos, exibição de documento, configurações de jogos do IOS](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Linha de base da proteção avançada contra ameaças do Microsoft defender (versão prévia)<!--  3754134 -->
Adicionamos uma visualização de linha de base de segurança para as configurações de [proteção avançada contra ameaças do Microsoft defender](../protect/security-baseline-settings-defender-atp.md) . Essa linha de base está disponível quando seu ambiente atende aos pré-requisitos para usar a [proteção avançada contra ameaças do Microsoft defender](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>A página de status de registro do Windows (ESP) já está disponível para o público geral<!-- 3605348 -->
A página de status de registro agora está fora de visualização. Para obter mais informações, consulte [Configurar uma página de status de registro](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Atualização da interface do usuário do Intune-criação do perfil de registro do AutoPilot<!-- 4593669 -->
A interface do usuário para criar um perfil de registro do AutoPilot foi atualizada para se alinhar com os estilos de interface do usuário do Azure. Para obter mais informações, consulte [criar um perfil de registro do AutoPilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Avançando, os cenários adicionais do Intune serão atualizados para esse novo estilo de interface do usuário.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Habilitar a redefinição do AutoPilot para todos os dispositivos Windows<!-- 4225665 -->
A redefinição do AutoPilot agora funciona para todos os dispositivos Windows, mesmo aqueles não configurados para usar a página status do registro. Se uma página de status de registro não tiver sido configurada para o dispositivo durante o registro inicial do dispositivo, o dispositivo passará diretamente para a área de trabalho após a entrada. Pode levar até oito horas para sincronizar e aparecer em conformidade no Intune. Para obter mais informações, consulte [Redefinir dispositivos com a redefinição remota do piloto automático do Windows](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Formato IMEI exato não necessário ao pesquisar todos os dispositivos<!--30407680 -->
Você não precisará incluir espaços em números IMEI ao pesquisar **todos os dispositivos**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>A exclusão de um dispositivo no portal da Apple será refletida no portal do Intune<!--2489996 -->
Se um dispositivo for excluído dos portais da Apple Programa de registro de dispositivos ou do Apple Business Manager, o dispositivo será excluído automaticamente do Intune durante a próxima sincronização.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>A página de status de registro agora rastreia aplicativos Win32<!-- 2714451 -->
Isso se aplica somente a dispositivos que executam o Windows 10 versão 1903 e posterior. Para obter mais informações, consulte [Configurar uma página de status de registro](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Redefinir e apagar dispositivos em massa usando o API do Graph<!-- 3295288 -->
Agora você pode redefinir e apagar até 100 dispositivos em massa usando o API do Graph.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>O relatório de criptografia está fora de visualização pública<!-- 4587546      -->
O [relatório para BitLocker e criptografia de dispositivo](../protect/encryption-monitor.md) agora está disponível para o público geral e não faz mais parte da visualização pública.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Assinatura do Outlook e configurações biométricas para dispositivos iOS e Android<!-- 4050557 -->
Agora você pode especificar se a assinatura padrão está habilitada no Outlook em dispositivos iOS e Android. Além disso, você pode optar por permitir que os usuários alterem a configuração biométrica no Outlook no iOS.

## <a name="week-of-may-6-2019"></a>Semana de 6 de maio de 2019

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Suporte ao controle de acesso à rede (NAC) para acesso de F5 para dispositivos iOS<!-- 4500808 -->

F5 lançou uma atualização para BIG-IP 13 que permite a funcionalidade de NAC para acesso F5 no iOS no Intune. Para usar esse recurso:

- Atualize BIG-IP para 13.1.1.5 Refresh. Não há suporte para BIG-IP 14.
- Integre BIG-IP ao Intune para NAC. Etapas na [visão geral: configurar o APM para verificações de postura de dispositivo com sistemas de gerenciamento de ponto de extremidade](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Marque a configuração **habilitar o controle de acesso à rede (NAC)** no perfil VPN no Intune.

Para ver a configuração disponível, vá para [definir configurações de VPN em dispositivos IOS](../configuration/vpn-settings-ios.md).

Aplica-se a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Conector de certificado PFX atualizado para Microsoft Intune<!-- doc-vso 1521237  -->  
Lançamos uma atualização para o [conector de certificado pfx para Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) que descarta o intervalo de sondagem de 5 minutos a 30 segundos.




## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
