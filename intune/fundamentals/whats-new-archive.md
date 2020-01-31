---
title: Novidades nos meses anteriores do Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Veja os anúncios mais antigos na página Novidades do Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/28/2020
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 313d9f470e9467cc80bae9c2400d4cc64aacc7ea
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886772"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novidades do Microsoft Intune – meses anteriores

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


<!-- ########################## -->
## <a name="october-2019"></a>outubro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Design de lista de verificação aprimorado no aplicativo Portal da Empresa para Android<!-- 5550857 -->  
A lista de verificação de configuração no aplicativo Portal da Empresa para Android foi atualizada com um design leve e novos ícones. As alterações se alinham com as atualizações recentes feitas no aplicativo Portal da Empresa para iOS. Para uma comparação lado a lado das alterações, consulte [novidades na interface do usuário do aplicativo](whats-new-app-ui.md). Para ver as etapas de registro atualizadas, consulte [registrar com o perfil de trabalho do Android](/intune-user-help/enroll-device-android-work-profile) e [registrar seu dispositivo Android](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Aplicativos Win32 em dispositivos do modo Windows 10 S<!-- 3747604 --> 
Você pode instalar e executar aplicativos Win32 em dispositivos gerenciados do modo Windows 10 S. Para fazer isso, você pode criar uma ou mais políticas complementares para o modo S usando as ferramentas do PowerShell do Windows Defender Application Control (WDAC). Assine as políticas complementares com o portal de assinatura do Device Guard e, em seguida, carregue e distribua as políticas por meio do Intune. No Intune, você encontrará esse recurso selecionando **aplicativos cliente** > **as políticas complementares do Windows 10 S**. Para obter mais informações, consulte [habilitar aplicativos Win32 em dispositivos em modo S](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Definir a disponibilidade do aplicativo Win32 com base em uma data e hora<!-- 3510685 -->
Como administrador, você pode configurar a hora de início e a hora do prazo para um aplicativo Win32 necessário. Na hora de início, a extensão de gerenciamento do Intune iniciará o download do conteúdo do aplicativo e o armazenará em cache. O aplicativo será instalado na hora do prazo. Para aplicativos disponíveis, a hora de início será ditada quando o aplicativo estiver visível no Portal da Empresa. Para obter mais informações, consulte [Gerenciamento de aplicativos Win32 do Intune](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Exigir reinicialização do dispositivo com base no período de carência após a instalação do aplicativo Win32<!-- 3136567 -->
Você pode exigir que um dispositivo seja reiniciado depois que um aplicativo Win32 for instalado com êxito. Para mais informações, consulte a gestão de [aplicações Win32.](~/apps/apps-win32-app-management.md)

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Modo escuro para iOS Portal da Empresa<!-- 4911422 -->
O modo escuro está disponível para o Portal da Empresa do iOS. Os usuários podem baixar aplicativos da empresa, gerenciar seus dispositivos e obter suporte de ti no esquema de cores de sua escolha com base nas configurações do dispositivo. O Portal da Empresa do iOS corresponderá automaticamente às configurações do dispositivo do usuário final para o modo escuro ou leve. Para obter mais informações, consulte [introdução ao modo escuro no Microsoft Intune portal da empresa para IOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Para obter mais informações sobre o Portal da Empresa do iOS, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>O Android Portal da Empresa a versão mínima do aplicativo imposta<!-- 2378776 -->
Usando a configuração de **versão mín portal da empresa** de uma política de proteção de aplicativo, você pode especificar uma versão específica mínima definida do portal da empresa que é imposta em um dispositivo de usuário final. Essa configuração de inicialização condicional permite **bloquear o acesso**, **apagar dados**ou **avisar** como ações possíveis quando o valor não é atendido. Os possíveis formatos para este valor seguem o padrão *[Major]. Menor,* *[Major].[ Menor]. [Construir]* ou *[Major].[ Menor]. [Construir]. [Revisão]* .

A configuração de **versão mín portal da empresa** , se configurada, afetará qualquer usuário final que obtém a versão 5.0.4560.0 do portal da empresa e quaisquer versões futuras do portal da empresa. Essa configuração não terá nenhum efeito sobre os usuários que usam uma versão do Portal da Empresa mais antiga do que a versão com a qual esse recurso é lançado. Os usuários finais que usam as atualizações automáticas do aplicativo em seu dispositivo provavelmente não verão nenhuma caixa de diálogo desse recurso, Considerando que eles provavelmente estarão na versão mais recente do Portal da Empresa. Essa configuração é Android somente com proteção de aplicativo para dispositivos registrados e não registrados. Para obter mais informações, consulte [configurações de política de proteção de aplicativo Android – inicialização condicional](~/apps/app-protection-policy-settings-android.md#conditional-launch).

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Adicionar aplicativos de defesa contra ameaças móveis a dispositivos não registrados<!-- 3005337 -->
Você pode criar uma política de proteção de aplicativo do Intune que pode bloquear ou Apagar seletivamente os dados corporativos dos usuários com base na integridade de um dispositivo. A integridade do dispositivo é determinada usando sua solução de MTD (defesa contra ameaças móveis) escolhida. Essa funcionalidade existe hoje com dispositivos registrados no Intune como uma configuração de conformidade do dispositivo. Com esse novo recurso, ampliamos a detecção de ameaças de um fornecedor de defesa contra ameaças móveis para funcionar em dispositivos não registrados. No Android, esse recurso requer as Portal da Empresa mais recentes no dispositivo. No iOS, esse recurso estará disponível para uso quando os aplicativos integrarem o SDK do Intune mais recente (v 12.0.15 +). Atualizaremos o tópico What ' s New quando o primeiro aplicativo adotar o SDK mais recente do Intune. Os aplicativos restantes ficarão disponíveis em uma base contínua. Para obter mais informações, consulte [criar política de proteção de aplicativo de defesa contra ameaças móveis com o Intune](~/protect/mtd-app-protection-policy.md).

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Relatórios de aplicativos Google Play disponíveis para perfis de trabalho do Android<!-- 3041956   -->
Para instalações de aplicativos disponíveis em dispositivos Android Enterprise Work Profile, dedicados e totalmente gerenciados, você pode exibir o status de instalação do aplicativo, bem como a versão instalada dos aplicativos gerenciados do Google Play. Para obter mais informações, consulte [como monitorar políticas de proteção de aplicativo](~/apps/app-protection-policies-monitor.md), [gerenciar dispositivos de perfil de trabalho Android com o Intune](~/enrollment/android-enterprise-overview.md) e o tipo de [aplicativo Google Play gerenciado](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge versão 77 e posterior para Windows 10 e macOS (visualização pública)<!-- 3872025, 4678761  -->
O Microsoft Edge versão 77 e posterior estará disponível para implantação em computadores que executam o Windows 10 e o macOS. 

A visualização pública oferece canais de **desenvolvimento** e **beta** para o Windows 10 e um canal **beta** para MacOS. A implantação está em inglês (apenas EN), mas os usuários finais podem alterar o idioma de exibição no navegador em **configurações** > **idiomas**. O Microsoft Edge é um aplicativo Win32 instalado no contexto do sistema e em arquiteturas semelhantes (aplicativo x86 no sistema operacional x86 e aplicativo x64 no sistema operacional x64). Além disso, as atualizações automáticas do navegador estão **ativadas** por padrão e o Microsoft Edge não pode ser desinstalado. Para obter mais informações, consulte [Adicionar o Microsoft Edge para Windows 10 a](~/apps/apps-windows-edge.md) documentação do Microsoft Intune e [do Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2103823).

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
Os conjuntos de políticas permitem que você crie um pacote de referências a entidades de gerenciamento já existentes que precisam ser identificadas, direcionadas e monitoradas como uma única unidade conceitual. Os conjuntos de políticas não substituem os conceitos ou objetos existentes. Você pode continuar a atribuir objetos individuais no Intune e pode fazer referência a objetos individuais como parte de um conjunto de políticas. Portanto, qualquer alteração nesses objetos individuais será refletida no conjunto de políticas.  No Intune, você selecionará os **conjuntos de políticas** > **criar** para criar um novo conjunto de políticas. 


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Novo perfil de interface de configuração de firmware de dispositivo para dispositivos Windows 10 e posteriores (visualização pública)<!-- 2266073  -->
No Windows 10 e posterior, você pode criar um perfil de configuração de dispositivo para controlar as configurações e os recursos (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma). Nesta atualização, há um novo tipo de perfil de interface de configuração de firmware de dispositivo que permite ao Intune gerenciar configurações de UEFI (BIOS).

Para obter mais informações sobre esse recurso, consulte [usar perfis de DFCI em dispositivos Windows em Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Aplica-se a:

- Windows 10 RS5 (1809) e mais recente em firmware com suporte

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

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404--------"></a>As configurações de reinicialização envolvidas são removidas dos anéis Windows Update<!--  4464404      -->
Conforme anunciado anteriormente, os anéis de atualização do Windows 10 do Intune agora [dão suporte a configurações para prazos finais](../protect/windows-update-settings.md) e não oferecem mais suporte ao *reinício envolvido*. As configurações para *reinicialização iniciada* não estão mais disponíveis quando você configura ou gerencia anéis de atualização no Intune.  

Essa alteração se alinha com [as alterações de serviço do Windows](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) recentes e em dispositivos que executam o Windows 10 1903 ou posterior, os *prazos* substituem as configurações para *reinicialização*ativada.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Impedir a instalação de aplicativos de fontes desconhecidas em dispositivos Android Enterprise de perfil de trabalho<!-- 4760025   -->
Em dispositivos Android Enterprise de perfil de trabalho, os usuários não podem nunca instalar aplicativos de aplicativos de fontes desconhecidas. Nessa atualização, há uma nova configuração – **impedir instalações de aplicativos de fontes desconhecidas no perfil pessoal**. Por padrão, essa configuração impede que os usuários façam o Sideload de aplicativos de fontes desconhecidas no perfil pessoal do dispositivo.

Para ver a configuração que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:

- Perfil de trabalho do Android Enterprise

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Criar um proxy HTTP global em dispositivos Android Enterprise do proprietário do dispositivo<!-- 4816339   -->
Em dispositivos Android Enterprise, você pode configurar um proxy HTTP global para atender aos padrões de navegação na Web de sua organização (**configuração de dispositivos** > **perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **proprietário do dispositivo > restrições de dispositivo** para o tipo de perfil > **conectividade**). Uma vez configurado, todo o tráfego HTTP usará esse proxy.

Para configurar esse recurso e ver todas as configurações definidas, vá para configurações de [dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:

- Proprietário do dispositivo corporativo Android

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>A configuração conectar automaticamente é removida nos perfis Wi-Fi no administrador do dispositivo Android e no Android Enterprise<!-- 5021055   -->
No Android Device Administrator e em dispositivos Android Enterprise, você pode criar um perfil de Wi-Fi para definir configurações diferentes (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Android Device administrator** ou **Android Enterprise** for Platform > **Wi-Fi** para o tipo de perfil). Nessa atualização, a configuração **conectar automaticamente** é removida, pois não há [suporte para o Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Se você usar essa configuração em um perfil de Wi-Fi, talvez tenha notado que o Connect não funcionará **automaticamente** . Você não precisa realizar nenhuma ação, mas lembre-se de que essa configuração é removida na interface do usuário do Intune.

Para ver as configurações atuais, vá para [configurações de Wi-Fi do Android](../configuration/wi-fi-settings-android.md) ou [configurações de Wi-Fi para Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Aplica-se a:

- Administrador do dispositivo Android 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Novas definições de configuração de dispositivo para dispositivos iOS e iPadOS supervisionados<!-- 5199328   -->
Em dispositivos iOS e iPadOS, você pode criar um perfil para restringir recursos e configurações em dispositivos (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios/iPadOS** para plataforma > **restrições de dispositivo** para o tipo de perfil). Nessa atualização, há novas configurações que você pode controlar: 
- Acesso à unidade de rede no aplicativo de arquivos  
- Acesso à unidade USB no aplicativo de arquivos 
- Wi-Fi sempre ativado 

Para ver essas configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:

- iOS 13,0 e mais recente
- iPadOS 13,0 e mais recente

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Alternar para mostrar apenas a página de status de registro em dispositivos provisionados pela experiência inicial (OOBE)<!--3959566-->
Agora você pode optar por mostrar apenas a página de status de registro em dispositivos provisionados pelo OOBE do AutoPilot.

Para ver a nova alternância, escolha **Intune** > **registro de dispositivo** > **registro do Windows** > **página status do registro** > **Criar perfil** > **configurações** > **apenas mostrar a página para dispositivos provisionados pela OOBE (configuração inicial do box)** .

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Especificar quais versões do sistema operacional do dispositivo Android registrar com o perfil de trabalho ou o registro de administrador do dispositivo<!-- 4350697   -->
Usando as restrições de tipo de dispositivo do Intune, você pode usar a versão do sistema operacional do dispositivo para especificar quais dispositivos de usuário usarão o registro de perfil de trabalho do Android Enterprise ou o registro de administrador do dispositivo Android.  Para obter mais informações, consulte [definir restrições de registro](../enrollment/enrollment-restrictions-set.md).



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>O Intune dá suporte ao iOS 11 e posterior<!-- 4665324  -->
O registro e o Portal da Empresa do Intune agora dão suporte ao iOS versões 11 e posteriores. Não há suporte para versões mais antigas.

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Novas restrições para renomeação de dispositivos Windows<!-- 3478938  -->
Ao renomear um dispositivo Windows, você deve seguir as novas regras:
- 15 caracteres ou menos (deve ser menor ou igual a 63 bytes, não incluindo nulo à direita)
- Não nulo ou uma cadeia de caracteres vazia
- ASCII permitido: letras (a-z, A-Z), números (0-9) e hifens
- Unicode permitidos: caracteres > = 0x80, deve ser um UTF8 válido, deve ser IDN-mapeável (ou seja, RtlIdnToNameprepUnicode tem sucesso; consulte RFC 3492)
- Os nomes não devem conter apenas números
- Nenhum espaço no nome
- Caracteres proibidos: { ~ ~ [ ] [ ] [ ] < = > & @! " # $ % ` ( ) + / , . _ *)

 Para obter mais informações, consulte [renomear um dispositivo no Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Página Visão geral de novos relatórios do Android em dispositivos<!-- 4924364 -->
Um novo relatório para a página Visão geral de dispositivos exibe quantos dispositivos Android foram registrados em cada solução de gerenciamento de dispositivo. Este gráfico mostra o perfil de trabalho, as contagens de dispositivos registrados, totalmente gerenciados, dedicados e de administrador de dispositivo. Para ver o relatório, escolha **Intune** > **dispositivos** > **visão geral**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Linha de base do Microsoft Edge (versão prévia)<!--  3787164  -->
Adicionamos uma visualização de linha de base de segurança para [as configurações do Microsoft Edge](../protect/security-baseline-settings-edge.md). 

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>Certificados PKCS para macOS<!-- 1333650       -->
Agora você pode [usar certificados PKCS com MacOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Você pode selecionar o certificado PKCS como um tipo de perfil para macOS e implantar certificados de usuário e de dispositivo que tenham [campos personalizados de entidade e nome alternativo da entidade](../protect/certficates-pfx-configure.md#subject-name-format).  

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

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Gerenciamento de dispositivos Microsoft 365

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Experiência de administração aprimorada no gerenciamento de dispositivos Microsoft 365<!-- 5551239 -->
Uma experiência de administração atualizada e simplificada já está disponível no espaço de trabalho de especialista em gerenciamento de dispositivos Microsoft 365 em [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com), incluindo:

- **Navegação atualizada**: você encontrará uma navegação simplificada de 1º nível que agrupa logicamente os recursos.
- **Novos filtros de plataforma**: você pode selecionar uma única plataforma, que mostra apenas as políticas e os aplicativos para a plataforma selecionada, nas páginas dispositivos e aplicativos.
- **Um novo Home Page**: consulte rapidamente a integridade do serviço, o estado do seu locatário, notícias, etc. no novo Home Page.

Para obter mais informações sobre esses aprimoramentos, consulte a [postagem no blog Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) no site da comunidade de tecnologia da Microsoft.

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introdução ao nó do Endpoint Security no gerenciamento de dispositivos Microsoft 365<!-- 5630102 -->

O nó do **Endpoint Security** agora está disponível em Microsoft 365 espaço de trabalho especialista em gerenciamento de dispositivos em https://devicemanagement.microsoft.com, que agrupa os recursos para proteger pontos de extremidade, como:

- Linhas de base de segurança: grupo pré-configurado de configurações que ajudam a aplicar um grupo conhecido de configurações e valores padrão que são recomendados pela Microsoft.
- Tarefas de segurança: Tire proveito do TVM (gerenciamento de ameaças e vulnerabilidades) do Microsoft defender ATPs e use o Intune para corrigir os pontos fracos do ponto de extremidade.
- Microsoft defender ATP: proteção de ameaças avançadas (ATP) integrada do Microsoft defender para ajudar a evitar violações de segurança.

Essas configurações continuarão a ser acessadas de outros nós aplicáveis, como dispositivos, e o estado atual configurado será o mesmo, independentemente de onde você acessar e habilitar esses recursos.

Para obter mais informações sobre esses aprimoramentos, consulte a [postagem do blog de sucesso do cliente do Intune](https://aka.ms/Endpoint_security_node) no site da comunidade de tecnologia da Microsoft.

<!-- ########################## -->
## <a name="september-2019"></a>setembro de 2019

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
Ao instalar aplicativos de LOB (linha de negócios) do Android em [dispositivos pretas](../configuration/android-zebra-mx-overview.md), em vez de ser solicitado a baixar e instalar o aplicativo LOB, você poderá instalar o aplicativo silenciosamente. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. No painel do **tipo de aplicação Select,** selecione **app Line-of-business**. Para obter mais informações, consulte [Adicionar um aplicativo de linha de negócios Android a Microsoft Intune](../apps/lob-apps-android.md).

No momento, depois que o aplicativo de LOB for baixado, uma notificação de **êxito no download** será exibida no dispositivo do usuário. A notificação só pode ser descartada tocando em **limpar tudo** na sombra da notificação. Esse problema de notificação será corrigido em uma versão futura e a instalação será completamente silenciosa sem nenhum indicador visual.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Ler e gravar API do Graph operações para aplicativos do Intune<!-- 5031704  -->
Os aplicativos podem chamar o API do Graph do Intune com operações de leitura e gravação usando a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Compartilhamento e criptografia de dados protegidos para o SDK de aplicativos do Intune para iOS<!-- 3586942  -->
Quando a encriptação está ativada por políticas de proteção de aplicações, o SDK da aplicação Intune para iOS utilizará as chaves de encriptação de 256 bits. Todos os aplicativos precisarão ter uma versão 8.1.1 do SDK para permitir o compartilhamento de dados protegidos.

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Atualizações para Microsoft Intune aplicativo<!-- 4997846 -->
O aplicativo Microsoft Intune para Android foi atualizado com os seguintes aprimoramentos:
- Atualizado e aprimorado o layout para incluir a navegação inferior para as ações mais importantes.
- Adicionada uma página adicional que mostra o perfil do usuário.
- Adicionada a exibição de notificações acionáveis no aplicativo para o usuário, como a necessidade de atualizar suas configurações de dispositivo.
- Adicionada a exibição de notificações por push personalizadas, alinhando o aplicativo com o suporte adicionado recentemente no aplicativo Portal da Empresa para iOS e Android. Para obter mais informações, consulte [enviar notificações personalizadas no Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>Para dispositivos iOS, personalize a tela de privacidade do processo de registro do Portal da Empresa<!-- 4394993 -->
Usando a redução, você pode personalizar a tela de privacidade do Portal da Empresa que os usuários finais veem durante o registro do iOS. Especificamente, você poderá personalizar a lista de coisas que sua organização não pode ver ou fazer no dispositivo. Para obter mais informações, consulte [como configurar o aplicativo portal da empresa do Intune](../apps/company-portal-app.md#privacy-statement-customization).



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Suporte para perfis VPN IKEv2 para iOS<!-- 1943438   -->
Nessa atualização, você pode criar perfis de VPN para o cliente VPN nativo do iOS usando o protocolo IKEv2. IKEv2 é um novo tipo de conexão na **configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **VPN** para tipo de perfil > **tipo de conexão**.

Esses perfis de VPN configuram o cliente VPN nativo, portanto, nenhum aplicativo cliente VPN é instalado ou enviado por push para dispositivos gerenciados. Esse recurso requer que os dispositivos sejam registrados no Intune (registro de MDM).

Para ver as configurações de VPN atuais que você pode configurar, vá para [definir configurações de VPN em dispositivos IOS](../configuration/vpn-settings-ios.md).

Aplica-se a:

- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Os recursos do dispositivo, as restrições de dispositivo e os perfis de extensão para as configurações do iOS e do macOS são mostrados pelo tipo de registro<!-- 4886161   -->

No Intune, você cria perfis para dispositivos iOS e macOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios** ou **MacOS** para plataforma > **recursos de dispositivo**, **restrições de dispositivo**ou **extensões** para o tipo de perfil). 

Nessa atualização, as configurações disponíveis no portal do Intune são categorizadas pelo tipo de registro ao qual se aplicam:

- iOS
  - Inscrição do utilizador
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
No Intune, você pode criar políticas para executar dispositivos iOS supervisionados como um quiosque ou dispositivo dedicado (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **quiosque**).

Nessa atualização, há novas configurações que você pode controlar:
- **Controle de voz**: habilita o controle de voz no dispositivo no modo de quiosque.
- **Modificação do controle de voz**: permite que os usuários alterem a configuração de controle de voz no dispositivo no modo de quiosque.

Para ver as configurações atuais, vá para [configurações de quiosque do IOS](../configuration/device-restrictions-ios.md#kiosk).

Aplica-se a:

- iOS 13,0 e posterior

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Usar o logon único para aplicativos e sites em seus dispositivos iOS e macOS<!-- 4893175   -->
Nesta atualização, há algumas novas configurações de logon único para dispositivos iOS e macOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **iOS** ou **MacOS** para recursos de plataforma > do **dispositivo** para o tipo de perfil).

Use essas configurações para configurar uma experiência de logon único, especialmente para aplicativos e sites que usam a autenticação Kerberos. Você pode escolher entre uma extensão de aplicativo de logon único de credencial genérica e a extensão Kerberos interna da Apple.

Para ver os recursos atuais do dispositivo que você pode configurar, vá para [recursos do dispositivo IOS](../configuration/ios-device-features-settings.md) e [recursos do dispositivo MacOS](../configuration/macos-device-features-settings.md).

Aplica-se a:

- iOS 13,0 e mais recente
- macOS 10,15 e mais recente

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associar domínios a aplicativos em dispositivos macOS 10.15 +<!-- 4898079   -->
Em dispositivos macOS, você pode configurar diferentes recursos e enviar esses recursos por push para seus dispositivos usando uma política **(configuração de dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **recursos de dispositivo** para o tipo de perfil). Nessa atualização, você pode associar domínios a seus aplicativos. Esse recurso ajuda a compartilhar credenciais com sites relacionados ao seu aplicativo e pode ser usado com a extensão de logon único da Apple, links universais e preenchimento de senha. 

Para ver os recursos atuais que você pode configurar, vá para [configurações de recurso de dispositivo MacOS no Intune](../configuration/macos-device-features-settings.md).

Aplica-se a:

- macOS 10,15 e mais recente

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Use "iTunes" e "apps" na URL da iTunes App Store ao mostrar ou ocultar aplicativos em dispositivos supervisionados do iOS<!-- 4928474   --> 
No Intune, você pode criar políticas para mostrar ou ocultar aplicativos em seus dispositivos iOS supervisionados (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **Mostrar ou ocultar aplicativos**). 

Você pode inserir a URL da iTunes App Store, como `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. Nessa atualização, `apps` e `itunes` podem ser usados na URL, como:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Para obter mais informações sobre essas configurações, consulte [Mostrar ou ocultar aplicativos](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Aplica-se a:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Os valores do tipo de senha da política de conformidade do Windows 10 são mais claros e correspondem ao CSP<!-- 5138985 -->
Em dispositivos Windows 10, você pode criar uma política de conformidade que exige recursos de senha específicos ( **políticas** de > de**conformidade do dispositivo** > **criar política** > **Windows 10 e posterior** para plataforma > **sistema de segurança**). Nesta atualização:
- Os valores de **tipo de senha** são mais claros e atualizados para corresponder ao [CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- A configuração **expiração da senha (dias)** é atualizada para permitir valores de 1-730 dias. 

Para obter mais informações sobre as configurações de conformidade do Windows 10, consulte [configurações do Windows 10 e posteriores para marcar dispositivos como em conformidade ou sem conformidade](../protect/compliance-policy-create-windows.md). 

Aplica-se a:
- Windows 10 e posterior

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Interface do usuário atualizada para configurar o acesso no local do Microsoft Exchange<!-- 4092920 -->  
Atualizamos o console do onde você configura o acesso do [Microsoft Exchange no local](../protect/conditional-access-exchange-create.md). Todas as configurações para o acesso ao Exchange local agora estão disponíveis no mesmo painel do console em que você habilita o *controle de acesso local do Exchange*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Permitir ou restringir a adição de widgets de aplicativo à tela inicial em dispositivos Android Enterprise Work Profile<!-- 1109650  --> 
Em dispositivos Android Enterprise, você pode configurar recursos no perfil de trabalho (**configuração** do dispositivo **perfis** de >  > **Criar perfil** > **Android Enterprise** para plataforma > **perfil de trabalho apenas > restrições de dispositivo** para o tipo de perfil). Nessa atualização, você pode permitir que os usuários adicionem widgets expostos por aplicativos de perfil de trabalho à tela inicial do dispositivo.

Para ver as configurações que você pode definir, vá para [configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-android-for-work.md).

Aplica-se a:
- Perfil de trabalho do Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Novos locatários ficarão desaparecendo do gerenciamento de administrador de dispositivos Android<!-- 4869790   -->
Os recursos de administrador do dispositivo do Android foram substituídos pelo Android Enterprise. Portanto, é recomendável usar Android Enterprise para novos registros em vez disso. Em uma atualização futura, novos locatários precisarão concluir as seguintes etapas de pré-requisito no registro do Android para usar o gerenciamento de administrador do dispositivo: Vá para **Intune** > **registro de dispositivo** > **registro do Android** > **dispositivos pessoais e corporativos com privilégios de administração de dispositivo** > use o administrador do **dispositivo para gerenciar dispositivos**.

Os locatários existentes não sofrerão alteração em seus ambientes.

Para obter mais informações sobre o administrador do dispositivo Android no Intune, consulte [registro do administrador do dispositivo Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045----"></a>Lista de dispositivos DEP associados a um perfil<!-- 5012045  -->
Agora você pode ver uma lista paginável de dispositivos DEP (Automated Programa de registro de dispositivos) que estão associados a um perfil. Você pode pesquisar a lista em qualquer página da lista. Para ver a lista, acesse **Intune** > **registro de dispositivo** > **registro da Apple** > **tokens do programa de registro** > escolha um token > **perfis** > escolha um perfil > **dispositivos atribuídos** (em **Monitor**).

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Registro de usuário do iOS em versão prévia<!-- 4817900 -->
A versão iOS 13,1 da Apple inclui o registro de usuário, uma nova forma de gerenciamento leve para dispositivos iOS. Ele pode ser usado no lugar do registro de dispositivo ou do registro de dispositivo automatizado (anteriormente Programa de registro de dispositivos) para dispositivos de propriedade pessoal. A versão prévia do Intune oferece suporte a esse conjunto de recursos, permitindo que você:

- Direcionar o registro de usuário para grupos de usuários.
- Dê aos usuários finais a capacidade de selecionar entre o registro mais leve do usuário ou o registro de dispositivo mais forte quando registrarem seus dispositivos.

A partir do 9/24/2019 com o lançamento do iOS 13,1, estamos no processo de distribuir essas atualizações para todos os clientes e esperar que sejam concluídas até o final da próxima semana.

Aplica-se a:

- iOS 13,1 e posterior

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
- Em **conformidade do dispositivo** > **Android Enterprise** > **proprietário do dispositivo**, você pode criar uma política de conformidade que defina o nível de atestado do Google SafetyNet.   <!-- 4631425 -->
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

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Suporte do Intune para dispositivos iPadOS e iOS 13,1<!--5439574-->
O Intune agora dá suporte ao gerenciamento de dispositivos iPadOS e iOS 13,1. Para mais informações, consulte [esta mensagem no blogue](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>Suporte BitLocker para rotação de senha de recuperação controlada pelo cliente<!--  3444125 -->
Use as configurações do Intune Endpoint Protection para configurar a [rotação de senha de recuperação controlada pelo cliente](../protect/endpoint-protection-windows-10.md#windows-encryption) para o BitLocker em dispositivos que executam o Windows versão 1909 ou posterior.

Essa configuração inicia uma atualização de senha de recuperação controlada pelo cliente após uma recuperação de unidade do sistema operacional (usando o bootmgr ou WinRE) e o desbloqueio de senha de recuperação em uma unidade de dados fixa. Essa configuração atualiza a senha de recuperação específica que foi usada e outras senhas não utilizadas no volume permanecem inalteradas. Para obter mais informações, consulte a documentação do CSP do BitLocker para [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Proteção contra violação para o Windows Defender antivírus<!-- 4705448        -->
Use o Intune para gerenciar a *proteção contra adulterações* para o Windows Defender antivírus. Você encontrará a [configuração de proteção contra violações](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) no grupo da central de segurança do Microsoft defender quando usar perfis de configuração do dispositivo para o Windows 10 Endpoint Protection. Você pode definir a proteção de violação como *habilitada* para ativar as restrições de proteção do Temper, definir *desabilitado* para desativá-las ou definir*não configurado* para deixar a configuração atual de dispositivos em vigor.  

Para obter mais informações sobre a proteção contra violações, consulte [impedir alterações de configurações de segurança com a proteção contra violações](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) na documentação do Windows.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>As configurações avançadas para o Windows Defender firewall já estão disponíveis para o público geral<!--  5317392       -->  
As [regras de firewall personalizadas do Windows Defender para o Endpoint Protection](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), que você configura como parte de um perfil de configuração de dispositivo, estão fora da visualização pública e estão disponíveis para o público geral (GA).  Você pode usar essas regras para especificar o comportamento de entrada e saída para aplicativos, endereços de rede e portas. Essas regras foram lançadas em julho como uma visualização pública. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Atualização da interface do usuário do Intune – painel de status do locatário<!-- 5273210  -->
A interface do usuário para o painel de status do locatário foi atualizada para se alinhar com os estilos de interface do usuário do Azure. Para obter mais informações, consulte [status do locatário](../tenant-status.md).


### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863----"></a>As marcas de escopo agora dão suporte a políticas de termos de uso<!-- 2358863  -->
Agora você pode atribuir [marcas de escopo](scope-tags.md) a políticas de termos de uso. Para fazer isso, acesse **Intune** > **registro de dispositivo** > **termos e condições** > escolha um item na lista > **Propriedades** > **marcas de escopo** > escolha uma marca de escopo.

<!-- ########################## -->
## <a name="august-2019"></a>agosto de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Controlar o comportamento de desinstalação do aplicativo iOS no cancelamento do registro do dispositivo<!-- 3504144   -->
Os administradores podem gerenciar se um aplicativo é removido ou mantido em um dispositivo quando o registro do dispositivo é cancelado no nível de um usuário ou de um grupo de dispositivos. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Categorizar Microsoft Store para aplicativos de negócios<!-- 3926922 -->
Você pode categorizar Microsoft Store para aplicativos de negócios. Para fazer isso, escolha **Intune** > **aplicativos cliente** > **aplicativos** > selecione um aplicativo Microsoft Store for Business > **informações do aplicativo** > **categoria**. No menu suspenso, atribua uma categoria.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Notificações personalizadas para usuários do Microsoft Intune app<!-- 4843354  -->
O aplicativo Microsoft Intune para Android agora dá suporte à exibição de notificações por push personalizadas, alinhando-a com o suporte adicionado recentemente nos aplicativos Portal da Empresa para iOS e Android. Para obter mais informações, consulte [enviar notificações personalizadas no Intune](../remote-actions/custom-notifications.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Definir configurações do Microsoft Edge usando modelos administrativos para Windows 10 e mais recente<!-- 5228061 -->
No Windows 10 e dispositivos mais recentes, você pode criar modelos administrativos para definir configurações de política de grupo no Intune. Nesta atualização, você pode definir as configurações que se aplicam ao Microsoft Edge versão 77 e mais recentes.

Para saber mais sobre modelos administrativos, confira [usar modelos do Windows 10 para definir configurações de política de grupo no Intune](../configuration/administrative-templates-windows.md).

Aplica-se a:

- Windows 10 e mais recente (Windows RS4 +)

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
Você pode habilitar e configurar recursos em dispositivos macOS (**configuração do dispositivo** > **perfis** > **Criar perfil** > **MacOS** para plataforma > **recursos do dispositivo** para o tipo de perfil). 

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
Você pode criar perfis para restringir as configurações em dispositivos que executam o iOS e o macOS ( **perfis** de > de**configuração de dispositivo** > **Criar perfil** > **ios** ou **MacOS** para tipo de plataforma > **restrições de dispositivo**). Essa atualização inclui os seguintes recursos:

- No **macOS** > **restrições de dispositivo** > **nuvem e armazenamento**, use a nova configuração de **entrega** para impedir que os usuários iniciem o trabalho em um dispositivo macOS e continuem trabalhando em outro dispositivo MacOS ou Ios.

  Para ver as configurações atuais, vá para [configurações do dispositivo MacOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-macos.md).

- No **iOS** > **restrições de dispositivo**, há algumas alterações:

  - **Aplicativos internos** > **localizar meu iPhone (somente supervisionado)** : nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  - **Aplicativos internos** > **encontrar meus amigos (somente supervisionado)** : nova configuração que bloqueia esse recurso no recurso Localizar meu aplicativo. 
  -  > **sem fio** **de modificação do estado de Wi-Fi (somente supervisionado)** : nova configuração que impede que os usuários ativem ou desativem o Wi-Fi no dispositivo.
  - **Teclado e dicionário** > **QuickPath (somente supervisionado)** : nova configuração que bloqueia o recurso QuickPath.
  - **Nuvem e armazenamento**: a **continuação da atividade** é renomeada para **entrega**.

  Para ver as configurações atuais, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md).

Aplica-se a:  
- macOS 10,15 e mais recente
- iOS 13 e mais recente

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Algumas restrições de dispositivo iOS não supervisionadas ficarão supervisionadas somente com a versão iOS 13,0<!-- 4867809   -->
Nessa atualização, algumas configurações se aplicam a dispositivos supervisionados com a versão 13,0 do iOS. Se essas configurações forem configuradas e atribuídas a dispositivos não supervisionados antes da versão 13,0 do iOS, as configurações ainda serão aplicadas a esses dispositivos não supervisionados. Eles ainda se aplicam após a atualização dos dispositivos para iOS 13,0. Essas restrições são removidas em dispositivos não supervisionados que são armazenados em backup e restaurados.

Estas definições incluem:

- App Store, Visualização de Documentos, Jogos
  - Loja de aplicações
  - Conteúdo explícito do iTunes, música, podcast ou notícias
  - Adicionando Game Center amigos
  - Jogos de vários jogadores
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
No Intune, você pode criar políticas para usar o Windows Defender antivírus para verificar seus dispositivos Windows 10 (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma > **restrições de dispositivo** para o tipo de perfil > **Windows Defender antivírus**). O **tempo para executar uma verificação rápida diária e o** **tipo de verificação do sistema para executar** relatórios mostra um status de falha, quando é, na verdade, um status de êxito. 

Nessa atualização, esse comportamento é fixo. Portanto, o **tempo para executar uma verificação rápida diária** e o **tipo de verificação do sistema para executar** configurações mostra um status de êxito quando as verificações são concluídas com êxito e mostram um status de falha quando as configurações falham ao serem aplicadas.

Para obter mais informações sobre as configurações do Windows Defender antivírus, consulte [configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Pretas Technologies é um OEM com suporte para o OEMConfig em dispositivos Android Enterprise<!-- 4843713 -->
No Intune, você pode criar perfis de configuração de dispositivo e aplicar configurações a dispositivos Android Enterprise usando OEMConfig (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Android Enterprise** para plataforma > **OEMConfig** para o tipo de perfil).

Nessa atualização, o pretas Technologies é um fabricante de equipamento original (OEM) com suporte para o OEMConfig. Para obter mais informações sobre o OEMConfig, consulte [usar e gerenciar dispositivos Android Enterprise com o OEMConfig](../configuration/android-oem-configuration-overview.md).

Aplica-se a:  
- Android Enterprise


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="default-scope-tags---3702875----"></a>Marcas de escopo padrão<!-- 3702875  -->
Uma nova marca de escopo padrão interna agora está disponível. Todos os objetos do Intune não marcados que dão suporte a marcas de escopo são automaticamente atribuídos à marca de escopo padrão. A marca de escopo **padrão** é adicionada a todas as atribuições de função existentes para manter a paridade com a experiência de administração hoje. Se você não quiser que um administrador Veja objetos do Intune com a marca de escopo padrão, remova a marca de escopo padrão da atribuição de função. Esse recurso é semelhante ao recurso de escopos de segurança no Configuration Manager. Para obter mais informações, consulte [usar o RBAC e marcas de escopo para para distribuí-lo](scope-tags.md).

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

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Configurar o limite de tempo de limpeza de dispositivo automático para 30 dias<!--4231059  -->
Você pode definir o limite de tempo de limpeza do dispositivo automático como 30 dias (em vez do limite anterior de 90 dias) após a última entrada. Para fazer isso, vá para **Intune** > **dispositivos** > **configuração** > **regras de limpeza do dispositivo**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Número de Build incluído na página de hardware do dispositivo Android<!-- 4461910   -->
Uma nova entrada na página hardware para cada dispositivo Android inclui o número de Build do sistema operacional do dispositivo. Para obter mais informações, consulte [Exibir detalhes do dispositivo no Intune](../remote-actions/device-inventory.md).

<!-- ########################## -->
## <a name="july-2019"></a>julho de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Notificações personalizadas para usuários e grupos<!-- 16766574          -->
Envie notificações por push personalizadas do aplicativo Portal da Empresa para os usuários em dispositivos Android e iOS que você gerencia com o Intune. Essas notificações por push móveis são altamente personalizáveis com texto livre e podem ser usadas para qualquer finalidade. Você pode direcioná-los para grupos de usuários diferentes em sua organização. Para obter mais informações, consulte [notificações personalizadas](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Aplicativo do controlador de política de dispositivo do Google<!-- 3041950  -->
O aplicativo de tela inicial gerenciado agora fornece acesso ao aplicativo de política de dispositivo Android do Google. O aplicativo de tela inicial gerenciado é um iniciador personalizado usado para dispositivos registrados no Intune como dispositivos do Android Enterprise (AE) dedicados usando o modo de quiosque de vários aplicativos. Você pode acessar o aplicativo de política de dispositivo Android ou orientar os usuários para o aplicativo de política de dispositivo Android, para fins de suporte e depuração. Esse recurso de inicialização está disponível no momento em que o dispositivo é registrado e bloqueado na tela inicial gerenciada. Nenhuma instalação adicional é necessária para usar essa funcionalidade.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Configurações de proteção do Outlook para dispositivos iOS e Android<!-- 3212619 -->
Agora você pode definir definições gerais de configuração de aplicativo e de proteção de dados para o Outlook para iOS e Android usando controles simples de administrador do Intune sem registro de dispositivo. As definições gerais de configuração de aplicativo fornecem paridade com as configurações que os administradores podem habilitar ao gerenciar o Outlook para iOS e Android em dispositivos registrados. Para obter mais informações sobre as configurações do Outlook, consulte [implantando definições de configuração de aplicativo do Outlook para IOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).


#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Tela inicial gerenciada e ícones de configurações gerenciadas<!-- 4918107 -->
O ícone do aplicativo de tela inicial gerenciado e o ícone de **configurações gerenciadas** foram atualizados. O aplicativo de tela inicial gerenciado só é usado por dispositivos registrados no Intune como dispositivos dedicados do Android Enterprise (AE) e executados em modo de quiosque com vários aplicativos. Para obter mais informações sobre o aplicativo de tela inicial gerenciado, consulte [Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Política de dispositivo Android em dispositivos Android Enterprise dedicados<!-- 4918136 -->
Você pode acessar o aplicativo de política de dispositivo Android na tela de depuração do aplicativo de tela inicial gerenciada. O aplicativo de tela inicial gerenciado só é usado por dispositivos registrados no Intune como dispositivos dedicados do Android Enterprise (AE) e executados em modo de quiosque com vários aplicativos. Para obter mais informações, consulte [Configurar o aplicativo de tela inicial gerenciado pela Microsoft para Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>atualizações de Portal da Empresa do iOS<!-- 3902931 -->
O nome da sua empresa nos prompts de gerenciamento de aplicativo iOS substituirá o texto atual "i.manage.microsoft.com". Por exemplo, os usuários verão o nome da empresa em vez de "i.manage.microsoft.com" quando os usuários tentarem instalar um aplicativo iOS do Portal da Empresa ou quando os usuários permitirem o gerenciamento do aplicativo. Isso será distribuído para todos os clientes durante os próximos dias.

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD e aplicativo em dispositivos Android Enterprise<!-- 3574267 -->
Ao integrar dispositivos Android Enterprise totalmente gerenciados, os usuários agora serão registrados com o Azure Active Directory (AAD) durante a configuração inicial de seu dispositivo novo ou de redefinição de fábrica. Anteriormente para um dispositivo totalmente gerenciado, após a conclusão da instalação, o usuário precisava iniciar manualmente o aplicativo Microsoft Intune para iniciar o registro do AAD. Agora, quando o usuário chega no dispositivo home page após a configuração inicial, o dispositivo é registrado e inscrito.

Além das atualizações do AAD, as políticas de proteção de aplicativo do Intune (aplicativo) agora têm suporte em dispositivos Android Enterprise totalmente gerenciados. Essa funcionalidade ficará disponível à medida que for distribuída. Para obter mais informações, consulte [adicionar aplicativos gerenciados Google Play a dispositivos Android Enterprise com o Intune](../apps/apps-add-android-for-work.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready------"></a>Use "regras de aplicabilidade" ao criar perfis de configuração de dispositivo do Windows 10 <!-- 2549910 eeready    -->

Você cria perfis de configuração de dispositivo do Windows 10 (**configuração de dispositivos** > **perfis** > **Criar perfil** > **Windows 10** para **regras de aplicabilidade**de > de plataforma). Nessa atualização, você pode criar uma **regra de aplicabilidade** para que o perfil se aplique somente a uma edição específica ou a uma versão específica. Por exemplo, você cria um perfil que habilita algumas configurações do BitLocker. Depois de adicionar o perfil, use uma regra de aplicabilidade para que o perfil se aplique somente a dispositivos que executam o Windows 10 Enterprise.

Para adicionar uma regra de aplicabilidade, consulte [regras de aplicabilidade](../configuration/device-profile-create.md#applicability-rules).

Aplica-se a: Windows 10 e posterior

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Usar tokens para adicionar informações específicas do dispositivo em perfis personalizados para dispositivos iOS e macOS<!-- 3330008  -->
Você pode usar perfis personalizados em dispositivos iOS e macOS para definir configurações e recursos não integrados ao Intune (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** ou **MacOS** para plataforma > **personalizado** para o tipo de perfil). Nessa atualização, você pode adicionar tokens aos arquivos de `.mobileconfig` para adicionar informações específicas do dispositivo. Por exemplo, você pode adicionar `Serial Number: {{serialnumber}}` ao arquivo de configuração para mostrar o número de série do dispositivo.

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
- Dá suporte à especificação manual do valor do cabeçalho de `Content-Type` ao usar o cmdlet `Invoke-MSGraphRequest`.

Para obter mais informações, consulte [SDK do PowerShell para Microsoft Intune API do Graph](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Gerenciar FileVault para macOS<!--  3858502 + 4557986 + 1210104  -->
Você pode usar o Intune para [gerenciar a criptografia de chave FileVault para dispositivos MacOS](../protect/encrypt-devices.md). Para criptografar dispositivos, use um perfil de configuração de dispositivo do Endpoint Protection.

Nosso suporte para FileVault inclui criptografia de dispositivos não criptografados, caução de uma chave de recuperação pessoal de dispositivos, rotação automática ou manual de chaves de criptografia pessoais e recuperação de chave para seus dispositivos corporativos. Os usuários finais também podem usar o site Portal da Empresa para obter a chave de recuperação pessoal para seus dispositivos criptografados.

Também expandimos o relatório de criptografia para incluir [informações sobre](../protect/encryption-monitor.md) as informações no lado do FileVault para o BitLocker, para que você possa exibir todos os detalhes de criptografia do dispositivo em um único lugar.

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Novas configurações do Office, do Windows e do OneDrive nos modelos administrativos do Windows 10 <!-- 3510695 -->

Você pode criar modelos administrativos no Intune que imitam o gerenciamento de política de grupo local (**Gerenciamento de dispositivos** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma > **modelo administrativo** para tipo de perfil).

Essa atualização inclui mais configurações do Office, do Windows e do OneDrive que você pode adicionar aos seus modelos. Com estas novas definições, agora pode configurar mais de 2500 configurações que são 100% baseadas em nuvem.

Para saber mais sobre esse recurso, consulte [usar modelos do Windows 10 para definir configurações de política de grupo no Intune](../configuration/administrative-templates-windows.md).

Aplica-se a: Windows 10 e posterior

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Atualizações para restrições de registro<!-- 2871968 -->
As restrições de registro para novos locatários foram atualizadas para que os perfis de trabalho do Android Enterprise sejam permitidos por padrão. Os locatários existentes não sofrerão alteração. Para usar perfis de trabalho do Android Enterprise, você ainda precisa [conectar sua conta do Intune à sua conta de Google Play gerenciada](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Atualizações de interface do usuário para registro da Apple e restrições de registro<!--4089575, 4089579  -->
Ambos os processos a seguir usam uma interface do usuário de estilo de assistente:
- Registro de dispositivo da Apple. Para obter mais informações, consulte [registrar automaticamente dispositivos IOS com o programa de registro de dispositivos da Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Criação de restrição de registro. Para obter mais informações, consulte [definir restrições de registro](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509-----"></a>Manipulando a pré-configuração de identificadores de dispositivos corporativos para dispositivos Android Q<!-- 4711509   -->
No Android Q (V10), o Google removerá a capacidade de agentes de MDM em dispositivos Android gerenciados por legado (administrador do dispositivo) para coletar informações de identificador de dispositivo.  O Intune tem um recurso que permite que os administradores de ti [configurem previamente uma lista de números de série de dispositivos ou IMEIs](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) para marcar automaticamente esses dispositivos como corporativos. Esse recurso não funcionará para dispositivos Android Q gerenciados pelo administrador do dispositivo.  Independentemente de o número de série ou IMEI do dispositivo ser carregado, ele sempre será considerado pessoal durante o registro do Intune.  Você pode alternar manualmente a propriedade para o corporativo após o registro.  Isso afeta apenas os novos registros e os dispositivos registrados existentes não são afetados.  Dispositivos Android gerenciados com perfis de trabalho não são afetados por essa alteração e continuarão funcionando como fazem hoje.  Além disso, os dispositivos Android Q registrados como administrador do dispositivo não poderão mais reportar o número de série ou IMEI no console do Intune como propriedades do dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Os ícones foram alterados para registros corporativos do Android (perfil de trabalho, dispositivos dedicados e dispositivos totalmente gerenciados)<!-- 4977730 -->
Os ícones para perfis de registro do Android Enterprise foram alterados. Para ver os novos ícones, acesse **Intune** > **registro** > **registro do Android** > examinar **perfis de registro**.

#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Alteração de coleta de dados de diagnóstico do Windows<!-- 4113859 -->
O valor padrão para coleta de dados de diagnóstico foi alterado para dispositivos que executam o Windows 10, versão 1903 e posterior. A partir do Windows 10 1903, a coleta de dados de diagnóstico é habilitada por padrão. Os dados de diagnóstico do Windows são dados técnicos vitais de dispositivos Windows sobre o dispositivo e como o Windows e o software relacionado estão sendo executados. Para obter mais informações, consulte [configurar dados de diagnóstico do Windows em sua organização](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Os dispositivos de piloto automático também são aceitos na telemetria "completa", a menos que definido de outra forma no perfil do AutoPilot com [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>A redefinição do Windows AutoPilot remove o usuário principal do dispositivo<!-- 4156123 -->
Quando a redefinição do AutoPilot é usada em um dispositivo, o usuário primário do dispositivo será removido. O próximo usuário que entrar após a redefinição será definido como o usuário primário. Este recurso será distribuído para todos os clientes durante os próximos dias.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="improve-device-location---3855417----"></a>Melhorar o local do dispositivo<!-- 3855417  -->
Você pode ampliar as coordenadas exatas de um dispositivo usando a ação **Localizar dispositivo** . Para obter mais informações sobre como localizar dispositivos iOS perdidos, consulte [localizar dispositivos IOS perdidos](../remote-actions/device-locate.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Segurança do dispositivo

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Configurações avançadas do Windows Defender firewall (visualização pública)<!--  1311949     -->  
Use o Intune para gerenciar [regras de firewall personalizadas como parte de um perfil de configuração de dispositivo para o](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) Endpoint Protection no Windows 10. As regras podem especificar o comportamento de entrada e saída para aplicativos, endereços de rede e portas. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Interface do usuário atualizada para gerenciar linhas de base de segurança<!-- 4091125     -->
Atualizamos a [experiência de criação e edição](../protect/security-baselines.md#create-the-profile) no console do Intune para nossas linhas de base de segurança. As alterações incluem:

Um formato de estilo de assistente mais simples, que é condensado para uma única folha. dentro de uma folha. Esse novo design desaparece com a expansão da folha que exige que os profissionais de ti se aprofundem em vários painéis separados.  
Agora você pode criar atribuições como parte da experiência de criação e edição, em vez de ter que retornar posteriormente para atribuir linhas de base. Adicionamos um resumo das configurações que você pode exibir antes de criar uma nova linha de base e ao editar uma existente. Ao editar, o resumo mostra apenas a lista de itens definidos dentro de uma categoria de propriedades que estão sendo editadas.

<!-- ########################## -->
## <a name="june-2019"></a>junho de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
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

#### <a name="new-features-in-microsoft-intune-app"></a>Novos recursos no aplicativo Microsoft Intune
Adicionamos novos recursos ao aplicativo Microsoft Intune (versão prévia) para Android. Os usuários em dispositivos Android totalmente gerenciados agora podem:  

* Exiba e gerencie os dispositivos registrados por meio do Portal da Empresa do Intune ou Microsoft Intune aplicativo.
* Entre em contato com a organização para obter suporte.
* Envie seus comentários para a Microsoft.
* Exiba os termos e condições, se definido por sua organização.

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Novos aplicativos de exemplo mostrando a integração do SDK do Intune disponível no GitHub<!-- 2653471 -->
A conta do GitHub msintuneappsdk adicionou novos aplicativos de exemplo para iOS (Swift), Android, Xamarin. iOS, Xamarin Forms e Xamarin. Android. Esses aplicativos destinam-se a complementar nossa documentação existente e fornecem demonstrações de como integrar o SDK de aplicativos do Intune em seus próprios aplicativos móveis. Se você for um desenvolvedor de aplicativos que precisa de diretrizes adicionais do SDK do Intune, consulte os seguintes exemplos vinculados:
- [Chat](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) -um aplicativo de mensagens instantâneas Ios (Swift) nativo que usa a Adal (biblioteca de autenticação Azure Active Directory) para autenticação orientada.
- [Tasker](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) -um aplicativo de lista de tarefas do Android nativo que usa a Adal para autenticação orientada.
- [Tasker](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) -um aplicativo de lista de tarefas do Xamarin. Android que usa a Adal para autenticação orientada, esse repositório também tem o aplicativo Xamarin. Forms.
- [Aplicativo de exemplo do xamarin. Ios](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) – um aplicativo de exemplo básicas Xamarin. Ios.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Definir configurações para extensões de kernel em dispositivos macOS<!-- 2043024 -->
Em dispositivos macOS, você pode criar um perfil de configuração de dispositivo (**configuração de dispositivo** > **perfis** > **Criar perfil** > escolher **MacOS** para plataforma). Essa atualização inclui um novo grupo de configurações que permitem configurar e usar extensões de kernel em seus dispositivos. Você pode adicionar extensões específicas ou permitir todas as extensões de um parceiro ou desenvolvedor específico.

Para saber mais sobre esse recurso, consulte [visão geral das extensões do kernel](../configuration/kernel-extensions-overview-macos.md) e [configurações de extensão do kernel](../configuration/kernel-extensions-settings-macos.md).

Aplica-se a: macOS 10.13.2 e posterior

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Os aplicativos da configuração armazenar somente para dispositivos Windows 10 incluem mais opções de configuração<!-- 2697002 -->
Ao criar um perfil de restrições de dispositivo para dispositivos Windows, você pode usar os **aplicativos da configuração armazenar somente** para que os usuários instalem apenas os aplicativos da Windows Store (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Windows 10 e posterior** para plataforma > **restrições de dispositivo** para o tipo de perfil). Nessa atualização, essa configuração é expandida para dar suporte a mais opções.

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
Quando você cria um perfil de restrições de dispositivo em dispositivos iOS (**configuração de dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **quiosque**), você define o **bloqueio automático**, o **comutador de toque**, a rotação de **tela**, o botão de **suspensão da tela**e os botões de **volume**.

Nessa atualização, os valores são **Block** (bloqueia o recurso) e **não configurados** (permite o recurso). Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos](../configuration/device-restrictions-ios.md#kiosk).

Aplica-se a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Usar ID facial para autenticação de senha em dispositivos iOS<!-- 4490704 -->
Ao criar um perfil de restrições de dispositivo para dispositivos iOS, você pode usar uma impressão digital para uma senha. Nessa atualização, as configurações de senha de impressão digital também permitem o reconhecimento facial (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **senha**). Como resultado, as seguintes configurações foram alteradas:

- O **desbloqueio de impressão digital** agora é **ID de toque e desbloqueio de ID facial**.
- A **modificação de impressão digital (somente supervisionado)** agora é a **ID de toque e a modificação da ID de face (somente supervisionado)** .

A ID de face está disponível no iOS 11,0 e posterior. Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md#password).

Aplica-se a: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Restringir os recursos de jogos e da loja de aplicativos em dispositivos iOS agora depende da região de classificações<!-- 4593948 -->
Em dispositivos iOS, você pode permitir ou restringir recursos relacionados a jogos, a loja de aplicativos e a exibição de documentos (**configuração de dispositivos** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > **App Store, exibição de documento, jogos**). Você também pode escolher a região de classificações, como a Estados Unidos.

Nessa atualização, o recurso de **aplicativos** é movido para ser um filho para a **região de classificações**e depende da **região de classificações**. Para ver as configurações, vá para [configurações do dispositivo IOS para permitir ou restringir recursos usando o Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Suporte do Windows AutoPilot para ingresso híbrido no Azure AD<!-- 4809146-->
O Windows AutoPilot para dispositivos existentes agora dá suporte à junção híbrida do Azure AD (além do suporte existente para ingresso no Azure AD). Aplica-se aos dispositivos Windows 10 versão 1809 e acima. Para obter mais informações, consulte [Windows AutoPilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Consulte o nível de patch de segurança para dispositivos Android<!-- 4461911 -->
Agora você pode ver o nível de patch de segurança para dispositivos Android. Para fazer isso, escolha **dispositivos** > do **Intune** > **todos os dispositivos** > escolha um dispositivo > **hardware**.
O nível do patch está listado na seção **sistema operacional** .

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Atribuir marcas de escopo a todos os dispositivos gerenciados em um grupo de segurança<!-- 3173810 -->
Agora você pode atribuir marcas de escopo a um grupo de segurança e todos os dispositivos no grupo de segurança também serão associados a essas marcas de escopo. Todos os dispositivos nesses grupos também serão atribuídos à marca de escopo. As marcas de escopo definidas com esse recurso substituirão as marcas de escopo definidas com o fluxo atual de marcas de escopo do dispositivo. Para obter mais informações, consulte [usar RBAC e marcas de escopo para distribuí-lo](scope-tags.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
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

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Novas permissões para administradores de grupo atribuídos<!-- 4504437   -->
A função interna de administrador da escola do Intune agora tem permissões CRUD (criar, ler, atualizar e excluir) para aplicativos gerenciados. Essa atualização significa que, se você estiver atribuído como um administrador de grupo no Intune para Educação, agora poderá criar, exibir, atualizar e excluir os MDM Push Certificate do iOS, tokens de servidor MDM do iOS e tokens VPP do iOS, juntamente com [todas as permissões existentes que você tem](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Para executar qualquer uma dessas ações, vá para **configurações de locatário** > **Gerenciamento de dispositivo IOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Os aplicativos podem usar o API do Graph para chamar operações de leitura sem credenciais de usuário<!-- 4655885 -->
Os aplicativos podem chamar o Intune API do Graph operações de leitura com a identidade do aplicativo sem credenciais do usuário. Para obter mais informações sobre como acessar a API de Microsoft Graph para o Intune, consulte [trabalhando com o Intune no Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Aplicar marcas de escopo a Microsoft Store para aplicativos de negócios<!-- 4392555 -->
Agora você pode aplicar marcas de escopo a Microsoft Store para aplicativos de negócios. Para obter mais informações sobre marcas de escopo, consulte [usar o controle de acesso baseado em função (RBAC) e marcas de escopo para distribuí-lo](scope-tags.md).

<!-- ########################## -->
## <a name="may-2019"></a>maio de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Relatórios de aplicativos potencialmente prejudiciais em dispositivos Android<!-- 4223162 -->
O Intune agora fornece informações de relatório adicionais sobre aplicativos potencialmente prejudiciais em dispositivos Android. 

#### <a name="windows-company-portal-app---3316993---"></a>Aplicação do Portal da Empresa do Windows<!-- 3316993 -->
O aplicativo Windows Portal da Empresa agora terá uma nova página rotulada **dispositivos**. A página **dispositivos** mostrará os usuários finais todos os seus dispositivos registrados. Os usuários verão essa alteração na Portal da Empresa quando usarem a versão 10.3.4291.0 e posterior. Para obter informações sobre como configurar o Portal da Empresa, consulte [como configurar o aplicativo de portal da empresa de Microsoft Intune](../apps/company-portal-app.md).

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>As políticas do Intune atualizam o método de autenticação e Portal da Empresa instalação do aplicativo<!-- 1927359  -->
Em dispositivos já registrados por meio do assistente de configuração por meio de um dos métodos de registro de dispositivo corporativo da Apple, o Intune não dará mais suporte ao Portal da Empresa quando ele é instalado manualmente pelos usuários finais da loja de aplicativos. Esta alteração é relevante apenas quando se autenticar com o Assistente de configuração da Apple durante a inscrição. Esta alteração afeta também apenas dispositivos iOS inscritos através de:  
* Do Apple configurator
* Gerente de negócios da Apple
* Gestor Escolar da Apple
* Programa de inscrição de dispositivos Apple (DEP)

Se os utilizadores instalarem a aplicação Portal da empresa a partir da App store e, em seguida, tentar inscrever estes dispositivos através do mesmo, receberá um erro. Esses dispositivos deverão usar apenas o Portal da Empresa quando ele for enviado por push, automaticamente, pelo Intune durante o registro. Perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Se pretender que os utilizadores de dispositivos do DEP para o portal da empresa, terá de especificar as suas preferências num perfil de inscrição. 

Além disso, a tela **identificar seu dispositivo** no portal da empresa do IOS está sendo removida. Portanto, os administradores que desejam habilitar o acesso condicional ou implantar aplicativos da empresa devem atualizar o perfil de registro do DEP. Esse requisito só se aplicará se o registro de DEP for autenticado com o assistente de configuração. Nesse caso, você deve enviar o Portal da Empresa para o dispositivo. Para fazer isso, escolha **Intune** > **registro de dispositivo** > **registro da Apple** > **tokens do programa de registro** > escolha um token > **perfis** > escolha um perfil > **Propriedades** > defina **instalar portal da empresa** como **Sim**.

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

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Conector de certificado PFX atualizado para Microsoft Intune<!-- 1533038 -->
Lançamos uma atualização para o [conector de certificado pfx para Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) que aborda um problema em que os certificados PFX existentes continuam a ser reprocessados, o que faz com que o conector pare de processar novas solicitações.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Tarefas de segurança do Intune para o defender ATP (em visualização pública)<!-- 3208597 -->
Na visualização pública, você pode usar o Intune para gerenciar [tarefas de segurança para a ATP (proteção avançada contra ameaças) do Microsoft defender](../protect/atp-manage-vulnerabilities.md). Essa integração com ATP e adiciona uma abordagem baseada em risco para descobrir, priorizar e corrigir vulnerabilidades de ponto de extremidade e configurações incorretas, reduzindo o tempo entre a descoberta e a mitigação.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671-----"></a>Verificar um chipset TPM em uma política de conformidade de dispositivo do Windows 10<!-- 3617671   -->
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
A configuração **senha para acessar a loja de aplicativos** é renomeada para exigir a **senha da iTunes Store para todas as compras** (**configuração do dispositivo** > **perfis** > **Criar perfil** > **Ios** para plataforma > **restrições de dispositivo** para o tipo de perfil > loja de **aplicativos, exibição de documento e jogos**).

Para ver as configurações disponíveis, vá para [loja de aplicativos, exibição de documento, configurações de jogos do IOS](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Aplica-se a: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Linha de base da proteção avançada contra ameaças do Microsoft defender (versão prévia)<!--  3754134 -->
Adicionamos uma visualização de linha de base de segurança para as configurações de [proteção avançada contra ameaças do Microsoft defender](../protect/security-baseline-settings-defender-atp.md) . Essa linha de base está disponível quando seu ambiente atende aos pré-requisitos para usar a [proteção avançada contra ameaças do Microsoft defender](../protect/advanced-threat-protection.md#prerequisites).

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Assinatura do Outlook e configurações biométricas para dispositivos iOS e Android<!-- 4050557 -->
Agora você pode especificar se a assinatura padrão está habilitada no Outlook em dispositivos iOS e Android. Além disso, você pode optar por permitir que os usuários alterem a configuração biométrica no Outlook no iOS.

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Suporte ao controle de acesso à rede (NAC) para acesso de F5 para dispositivos iOS<!-- 4500808 -->
F5 lançou uma atualização para BIG-IP 13 que permite a funcionalidade de NAC para acesso F5 no iOS no Intune. Para usar esse recurso:

- Atualize BIG-IP para 13.1.1.5 Refresh. Não há suporte para BIG-IP 14.
- Integre BIG-IP ao Intune para NAC. Etapas na [visão geral: configurar o APM para verificações de postura de dispositivo com sistemas de gerenciamento de ponto de extremidade](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Marque a configuração **habilitar o controle de acesso à rede (NAC)** no perfil VPN no Intune.

Para ver a configuração disponível, vá para [definir configurações de VPN em dispositivos IOS](../configuration/vpn-settings-ios.md).

Aplica-se a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Conector de certificado PFX atualizado para Microsoft Intune<!-- doc-vso 1521237  -->  
Lançamos uma atualização para o [conector de certificado pfx para Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) que descarta o intervalo de sondagem de 5 minutos a 30 segundos.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nome do atributo NúmeroDoPedido do dispositivo AutoPilot alterado para a marca de grupo <!-- 4659453 -->

Para torná-lo mais intuitivo, o nome do atributo **NúmeroDoPedido** em dispositivos AutoPilot foi alterado para a **marca de grupo**. Ao usar o CSVs para carregar as informações do dispositivo AutoPilot, você deve usar a marca Group como o cabeçalho da coluna, não OrderID.  

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

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Redefinir e apagar dispositivos em massa usando o API do Graph<!-- 3295288 -->
Agora você pode redefinir e apagar até 100 dispositivos em massa usando o API do Graph.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>O relatório de criptografia está fora de visualização pública<!-- 4587546      -->
O [relatório para BitLocker e criptografia de dispositivo](../protect/encryption-monitor.md) agora está disponível para o público geral e não faz mais parte da visualização pública.


<!-- ########################## -->
## <a name="april-2019"></a>abril de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações
#### <a name="user-experience-update-for-the-company-portal-app-for-ios---2536024---"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS<!-- 2536024 -->
O home page do aplicativo Portal da Empresa para dispositivos iOS foi reprojetado. Com essa alteração, a home page seguirá melhor os padrões da interface do usuário do iOS e também proporcionará uma capacidade de descoberta aprimorada para aplicativos e livros eletrônicos.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users--3448635---"></a>Alterações no registro de Portal da Empresa para usuários do dispositivo iOS 12<!--3448635 -->
As Portal da Empresa para as telas e etapas de registro do iOS foram atualizadas para alinhar com as alterações de registro do MDM lançadas no Apple iOS 12,2. O fluxo de trabalho atualizado solicita que os usuários:  

* Permita que o Safari Abra o site Portal da Empresa e baixe o perfil de gerenciamento antes de retornar ao aplicativo Portal da Empresa.  
* Abra o aplicativo configurações para instalar o perfil de gerenciamento em seu dispositivo.
* Retorne ao aplicativo Portal da Empresa para concluir o registro.  

Para ver etapas e ecrãs de inscrição atualizados, consulte [O dispositivo 'Inscrever o iOS' no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).

#### <a name="openssl-encryption-for-android-app-protection-policies---3747362---"></a>Criptografia OpenSSL para políticas de proteção de aplicativo Android<!-- 3747362 -->
As políticas de proteção de aplicativo do Intune (aplicativo) em dispositivos Android agora usam uma biblioteca de criptografia OpenSSL que é compatível com FIPS 140-2. Para mais informações, consulte a secção de [encriptação](../apps/app-protection-policy-settings-android.md#encryption) das definições de política de proteção de [aplicações Android no Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies---2617348----"></a>Habilitar dependências de aplicativo Win32<!-- 2617348  -->
Como administrador, você pode exigir que outros aplicativos sejam instalados como dependências antes de instalar seu aplicativo Win32. Especificamente, o dispositivo deve instalar os aplicativos dependentes antes de instalar o aplicativo Win32. Intune, selecione **aplicações do Cliente** > **Apps** > **Adicionar** para exibir a lâmina da **aplicação Add.** Selecione **a aplicação Windows (Win32)** como o tipo de **App**. Depois de ter adicionado a aplicação, pode selecionar **Dependências** para adicionar as aplicações dependentes que devem ser instaladas antes de a aplicação Win32 poder ser instalada. Para mais informações, consulte [Intune Autónomo - Gestão de aplicações Win32.](./../apps/app-management.md) 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps---3537391-----"></a>Informações de instalação de versão do aplicativo para Microsoft Store para aplicativos de negócios<!-- 3537391   -->
Os relatórios de instalação do aplicativo incluem informações de versão do aplicativo para Microsoft Store para aplicativos de negócios. Intune, selecione **aplicações do Cliente** > **Apps**. Selecione uma **aplicação Microsoft Store for Business** e, em seguida, selecione o estado de **instalação do Dispositivo** na secção **Monitor.**

#### <a name="additions-to-win32-apps-requirement-rules---3676883-----"></a>Adições a regras de requisito de aplicativos Win32<!-- 3676883   -->
Você pode criar regras de requisitos com base em scripts do PowerShell, valores de registro e informações do sistema de arquivos. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. Em seguida, selecione a **aplicação Windows (Win32)** como o tipo de **App** na lâmina de **aplicação Adicionar.**  Selecione **Requisitos** > **Adicionar** para configurar regras de requisitos adicionais. Em seguida, selecione o tipo de **ficheiro,** **o registo,** ou o **Script** como o **tipo Deexigência**. Para mais informações, consulte a gestão de [aplicações Win32.](./../apps/app-management.md)

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices---3695227----"></a>Configurar seus aplicativos Win32 para serem instalados em dispositivos adicionados ao Azure AD registrados no Intune<!-- 3695227  -->
Você pode atribuir seus aplicativos Win32 para serem instalados em dispositivos ingressados no Azure AD registrados no Intune. Para mais informações sobre as aplicações Win32 em Intune, consulte a gestão de [aplicações Win32.](./../apps/app-management.md)

#### <a name="device-overview-shows-primary-user--3794259----"></a>Visão geral do dispositivo mostra o usuário principal<!--3794259  -->
A página Visão geral do dispositivo mostrará o usuário primário, também chamado de usuário de afinidade de dispositivo de usuário (UDA). Para ver o Utilizador Primário para um dispositivo, escolha **Intune** > **Devices** > **Todos os dispositivos** > escolha um dispositivo. O Utilizador Primário aparecerá perto do topo da página **'Visão Geral'.**

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices---4105925----"></a>Relatórios adicionais da aplicação do Managed Google Play para dispositivos de perfil de trabalho do Android Enterprise<!-- 4105925  -->
Para as aplicações do Managed Google Play implementadas para dispositivos de perfil de trabalho do Android Enterprise, pode ver o número de versão específica da aplicação instalada num dispositivo. Tal só se aplica às aplicações obrigatórias.  

#### <a name="ios-third-party-keyboards---4111843-----"></a>teclados de terceiros do iOS<!-- 4111843   -->
O suporte à política de proteção de aplicações (APP) para a definição de **Teclados de Terceiros** para iOS já não é suportado devido a uma mudança de plataforma iOS. Você não poderá definir essa configuração no console de administração do Intune e ela não será imposta no cliente no SDK do aplicativo do Intune.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="updated-certificate-connectors---icm-113304612---"></a>Conectores de certificado atualizados<!-- ICM 113304612 -->
Lançámos atualizações tanto para o [Conector de Certificado Intune como para o Conector de Certificado PFX para o Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors). As novas versões corrigem vários problemas conhecidos.

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices---1210083----"></a>Definir configurações de logon e opções de reinicialização de controle em dispositivos macOS<!-- 1210083  -->
Nos dispositivos macOS, pode criar um perfil de configuração do dispositivo (**configuração** do dispositivo > **Perfis** > **Criar perfil** > escolher **macOS** para **funcionalidades** de plataforma > dispositivo para tipo de perfil). Essa atualização inclui novas configurações de janela de logon, como mostrar uma faixa personalizada, escolher como os usuários entram, mostrar ou ocultar as configurações de energia e muito mais.

Para ver estas definições, vá às definições de funcionalidades do [dispositivo macOS](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode--3041940----"></a>Configurar o WiFi no Android Enterprise, dispositivos dedicados de proprietário do dispositivo em execução no modo de quiosque de vários aplicativos<!--3041940  -->
Você pode habilitar as configurações no Android Enterprise, o proprietário do dispositivo ao executar como um dispositivo dedicado no modo de quiosque de vários aplicativos. Nesta atualização, pode permitir aos utilizadores configurar e conectar-se às redes WiFi (**Configuração intune** > **Dispositivo** > **Perfis** > **Criar perfil** > Android **Enterprise** apenas para plataforma > Proprietário do **dispositivo, restrições** de dispositivos para o tipo de perfil > **Dispositivos dedicados** > **modo quiosque**: **Configuração Wi-Fi** ** > multi-app).**

Para ver todas as definições que pode configurar, vá às definições do [dispositivo Android Enterprise para permitir ou restringir funcionalidades](../configuration/device-restrictions-android-for-work.md).

Aplica-se a: dispositivos Android Enterprise dedicados em execução no modo de quiosque de vários aplicativos

#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041941----"></a>Configurar o Bluetooth e o emparelhamento no Android Enterprise, dispositivos dedicados de proprietário do dispositivo em execução no modo de quiosque de vários aplicativos<!-- 3041941  -->
Você pode habilitar as configurações no Android Enterprise, o proprietário do dispositivo ao executar como um dispositivo dedicado no modo de quiosque de vários aplicativos. Nesta atualização, pode permitir que os utilizadores finais ativem bluetooth e emparelhem dispositivos através de Bluetooth – **Configuração** de > **De perfil** do dispositivo**Intune** > Perfis > **Criar perfil** > **Android Enterprise** apenas para a plataforma > Proprietário do **dispositivo, restrições** de dispositivos para o tipo de perfil > **Dispositivos dedicados** > **modo Quiosque**: **Configuração Multi-app** > **Bluetooth).**

Para ver todas as definições que pode configurar, vá às definições do [dispositivo Android Enterprise para permitir ou restringir funcionalidades](../configuration/device-restrictions-android-for-work.md).

Aplica-se a: dispositivos Android Enterprise dedicados em execução no modo de quiosque de vários aplicativos

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune---3305883----"></a>Criar e usar perfis de configuração de dispositivo OEMConfig no Intune<!-- 3305883  -->
Nesta atualização, o Intune dá suporte à configuração de dispositivos Android Enterprise com OEMConfig. Especificamente, pode criar um perfil de configuração de dispositivos e aplicar configurações em dispositivos Android Enterprise utilizando o OEMConfig (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **empresa Android** para plataforma).

O suporte para OEMs está atualmente em uma base por OEM. Se uma aplicação OEMConfig que deseja não estiver disponível na lista de aplicações OEMConfig, contacte `IntuneOEMConfig@microsoft.com`.

Para saber mais sobre esta funcionalidade, vá utilizar [e gerir dispositivos Android Enterprise com o OEMConfig no Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Aplica-se a: Android Enterprise

#### <a name="windows-update-notifications---3316758-3316782----"></a>Notificações de Windows Update<!-- 3316758, 3316782  -->
Adicionámos duas *definições* de experiência do Utilizador às configurações do anel de Atualização do Windows que podes gerir dentro da consola Intune. Agora pode:
- Bloqueie ou permita que os utilizadores [responsalhem as atualizações do Windows](../protect/windows-update-settings.md).
- Gerencie o nível de [notificação do Windows Update](../protect/windows-update-settings.md) que os utilizadores vêem.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner---3574254----"></a>Novas configurações de restrição de dispositivo para Android Enterprise, proprietário do dispositivo<!-- 3574254  -->
Nos dispositivos Android Enterprise, pode criar um perfil de restrição de dispositivos para permitir ou restringir funcionalidades, definir regras de palavra-passe e muito mais (**Configuração** de **dispositivo > Perfis** > **Criar perfil** > escolher **Android Enterprise** para plataforma > **Dispositivo apenas > Restrições** de dispositivos para tipo de perfil). 

Essa atualização inclui novas configurações de senha, permite acesso completo a aplicativos em Google Play Store para dispositivos totalmente gerenciados e muito mais. Para ver a lista atual de configurações, vá às definições do [dispositivo Android Enterprise para permitir ou restringir funcionalidades](../configuration/device-restrictions-android-for-work.md). 

Aplica-se a: dispositivos Android Enterprise totalmente gerenciados

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---"></a>Verificar um chipset TPM em uma política de conformidade de dispositivo do Windows 10<!-- 3617671 -->

Esse recurso está atrasado e está planejado para ser lançado posteriormente.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices---3775833-----"></a>Alterações de interface do usuário atualizadas para o navegador Microsoft Edge em dispositivos Windows 10 e posteriores<!-- 3775833   -->
Quando cria um perfil de configuração do dispositivo, pode permitir ou restringir as funcionalidades do Microsoft Edge no Windows 10 e dispositivos posteriores **(configuração** do dispositivo > **Perfis** > **Criar perfil** > **Windows 10 e posteriormente** para **restrições** de plataforma, > Dispositivo para o tipo de perfil > **Microsoft Edge Browser).** Nessa atualização, as configurações do Microsoft Edge são mais descritivas e mais fáceis de entender.

Para ver estas funcionalidades, vá às definições de [restrição](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)do dispositivo do Microsoft Edge Browser .

Aplica-se a: Windows 10 e posterior

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-----3903241-3903244-3903246-----"></a>Suporte expandido para dispositivos Android Enterprise totalmente gerenciados (versão prévia)<!--   3903241, 3903244, 3903246   -->
Ainda numa pré-visualização pública, expandimos o nosso suporte aos dispositivos geridos totalmente android Enterprise, anunciados pela primeira vez em janeiro de 2019, para incluir o seguinte:

- Em dispositivos totalmente geridos e dedicados, pode criar políticas de [conformidade](../protect/compliance-policy-create-android-for-work.md) para incluir regras de senha e requisitos do sistema operativo (**Conformidade com dispositivos** > **Políticas** > **Criar política** > Android **Enterprise** para o tipo de plataforma > **Dispositivo** para tipo de perfil).

  Em dispositivos dedicados, o dispositivo pode apresentar-se como **não conforme**. O acesso condicional não está disponível em dispositivos dedicados. Realize algumas tarefas ou ações para que os dispositivos dedicados fiquem em conformidade com as políticas atribuídas.

- [Acesso Condicional](../protect/conditional-access.md) - As políticas de acesso condicional aplicáveis ao Android também se aplicam a dispositivos geridos por Android Enterprise. Os utilizadores podem agora registar o seu dispositivo totalmente gerido no Diretório Ativo do Azure utilizando a **aplicação Microsoft Intune**. Em seguida, consulte e resolva quaisquer problemas de conformidade para acessar recursos organizacionais.

- Nova aplicação de utilizador final (aplicação Microsoft Intune) - Existe uma nova aplicação de utilizador final para dispositivos geridos totalmente pelo Android chamado **Microsoft Intune**. Esse novo aplicativo é leve e moderno e fornece uma funcionalidade semelhante à do Portal da Empresa aplicativo, mas para dispositivos totalmente gerenciados. Para mais informações, consulte a [aplicação Microsoft Intune no Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Para configurar dispositivos totalmente geridos pelo Android, vá para a **inscrição do Dispositivo** > **inscrição android** > dispositivos de utilizador totalmente geridos pela **Empresa.** O suporte para dispositivos Android totalmente gerenciados permanece em versão prévia, e alguns recursos do Intune podem não estar totalmente funcionais.  

Para saber mais sobre esta pré-visualização, consulte o nosso blog, [Microsoft Intune - Preview 2 para dispositivos Totalmente Geridos](https://aka.ms/preview2_AE_fullymanaged)para Android Enterprise .

#### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Use o Compliance Manager para criar Avaliações para Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (abre outro site da Microsoft) é uma ferramenta de avaliação de risco baseada no fluxo de trabalho no Portal microsoft Service Trust. Ele permite que você controle, atribua e verifique as atividades de conformidade regulatória de sua organização relacionadas aos serviços da Microsoft. Você pode criar sua própria avaliação de conformidade com o Office 365, o Azure, o Dynamics, os serviços profissionais e o Intune. O Intune tem duas avaliações disponíveis – FFIEC e GDPR.

O Compliance Manager ajuda você a concentrar seus esforços dividindo controles – controles gerenciados pela Microsoft e controles gerenciados por sua organização. Você pode concluir as avaliações e, em seguida, exportar e imprimir as avaliações.

O Conselho Federal de [Exame de Instituições Financeiras (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (abre outro site da Microsoft) é um conjunto de normas para a banca online emitidas pela FFIEC. É a avaliação mais solicitada para instituições financeiras que usam o Intune. Ele interpreta como o Intune ajuda a atender às diretrizes do FFIEC segurança cibernética relacionadas a cargas de trabalho de nuvem pública. A avaliação do FFIEC do Intune é a segunda avaliação do FFIEC no Compliance Manager.

No exemplo a seguir, você pode ver a divisão dos controles do FFIEC. A Microsoft abrange 64 controles. Você é responsável pelos 12 controles restantes.

![Consulte uma avaliação do Intune de exemplo para o FFIEC, incluindo as ações do cliente e as ações da Microsoft](./media/whats-new/intune-ffiec-assessment-status.png)

O Regulamento Geral de Proteção de [Dados (RGPD)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (abre outro site da Microsoft) é uma lei da União Europeia (UE) que ajuda a proteger os direitos das pessoas e dos seus dados. O GDPR é a avaliação mais solicitada para ajudar a cumprir os regulamentos de privacidade. 

No exemplo a seguir, você verá a divisão dos controles GDPR. A Microsoft abrange 49 controles. Você é responsável pelos demais controles 66.

![Consulte uma avaliação do Intune de exemplo para GDPR, incluindo as ações do cliente e as ações da Microsoft](./media/whats-new/intune-assessment-status.png)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant---2276470----"></a>Configurar o perfil para ignorar algumas telas durante o assistente de configuração<!-- 2276470  -->
Ao criar um perfil de registro do macOS, você pode configurá-lo para ignorar qualquer uma das telas a seguir quando um usuário passar pelo assistente de configuração:
- Aparência
- Sinal de Exibição
- iCloudStorage se você criar um novo perfil ou editar um perfil, as telas ignorar selecionadas precisarão ser sincronizadas com o servidor MDM da Apple.  Os usuários podem emitir uma sincronização manual dos dispositivos para que não haja atraso na separação das alterações de perfil.
Para mais informações, consulte [Automaticamente inscrever dispositivos macOS com o Programa de Inscrição de Dispositivos ou O Gestor da Apple School](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Nomeação de dispositivo em massa ao registrar dispositivos iOS corporativos<!--3566569  -->
Ao usar um dos métodos de registro corporativo da Apple (DEP/ABM/ASM), você pode definir um formato de nome de dispositivo para nomear automaticamente dispositivos iOS de entrada. Você pode especificar um formato que inclua o tipo de dispositivo e o número de série em seu modelo. Para tal, escolha **intune** > **dispositivo de inscrição** > apple matricula do programa de **inscrição** > **Matricula tokens** > **Selecione um token** >Criar o **formato** de **nomeação**do dispositivo > dispositivo . Você pode editar perfis existentes, mas somente os dispositivos recém sincronizados terão o nome aplicado.

#### <a name="updated-default-timeout-message-on-enrollment-status-page---3959331---"></a>Mensagem de tempo limite padrão atualizada na página de status do registro<!-- 3959331 -->
Atualizamos a mensagem de tempo limite padrão que os usuários veem quando a página de status de registro (ESP) excede o valor de tempo limite especificado no perfil ESP. A nova mensagem padrão é o que os usuários veem e os ajuda a entender as próximas ações a serem executadas com a implantação do ESP.  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="retire-noncompliant-devices---1827291-----"></a>Desativar dispositivos não compatíveis<!-- 1827291   -->
Esse recurso foi atrasado e está planejado para uma versão futura.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta---4403765---"></a>Alterações do Intune data warehouse V 1.0 refletindo de volta para a versão beta<!-- 4403765 -->
Quando o V 1.0 foi introduzido pela primeira vez em 1808, ele difere de algumas maneiras significativas da API beta. Em 1903, essas alterações serão refletidas de volta para a versão da API beta. Se você tiver relatórios importantes que usam a versão da API beta, é altamente recomendável trocar esses relatórios para V 1.0 para evitar alterações significativas. Para mais informações, consulte o [registo de alteração para a API](../developer/reports-changelog.md#1903-part-2)do Armazém de Dados Intune .

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorar o status da linha de base de segurança (visualização pública) <!-- 3082047 --> 
Adicionámos uma [visão por categoria](../protect/security-baselines-monitor.md#per-category-view) à monitorização das linhas de base de segurança. (As linhas de base de segurança permanecem na versão prévia). A exibição por categoria exibe cada categoria da linha de base junto com a porcentagem de dispositivos que se enquadram em cada grupo de status dessa categoria. Agora você pode ver quantos dispositivos não correspondem às categorias individuais, estão configurados incorretamente ou não são aplicáveis.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apple-vpp-tokens--2371886----"></a>Marcas de escopo para tokens de VPP da Apple<!--2371886  -->
Agora você pode adicionar marcas de escopo a tokens de VPP da Apple. Somente os usuários atribuídos com a mesma marca de escopo terão acesso ao token do Apple VPP com essa marca. Os aplicativos VPP e os livros eletrônicos adquiridos com esse token herdam suas marcas de escopo. Para mais informações sobre etiquetas de âmbito, consulte [Use RBAC e etiquetas](scope-tags.md)de mira .

<!-- ########################## -->
## <a name="march-2019"></a>março de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações
#### <a name="deploy-microsoft-visio-and-microsoft-project---3725386----"></a>Implantar o Microsoft Visio e o Microsoft Project<!-- 3725386  -->
Agora você pode implantar o Microsoft Visio pro para Office 365 e o cliente de área de trabalho do Microsoft Project online como aplicativos independentes em dispositivos Windows 10 usando Microsoft Intune, se você tiver licenças para esses aplicativos. A partir de Intune, selecione **aplicações do Cliente** > **Apps** > **Adicionar** para exibir a lâmina da **aplicação Add.** Na lâmina da **aplicação Adicionar,** selecione **o Windows 10** como o tipo de **App**. Em seguida, **selecione Configure App Suite** para selecionar aplicações para instalar. Para obter mais informações sobre as aplicações do Office 365 para dispositivos Windows 10, consulte [as aplicações do Assign Office 365 para dispositivos Windows 10 com](../apps/apps-add-office365.md)o Microsoft Intune .

#### <a name="microsoft-visio-pro-for-office-365-product-name-change---3593653----"></a>Alteração do nome do produto Microsoft Visio pro para Office 365<!-- 3593653  -->
**O Microsoft Visio Pro para o Office 365** passará a ser conhecido como **Microsoft Visio Online Plan 2**.  Para mais informações sobre o Microsoft Visio, consulte o [Visio Online Plan 2](https://products.office.com/visio/visio-online-plan-2). Para obter mais informações sobre as aplicações do Office 365 para dispositivos Windows 10, consulte [as aplicações do Assign Office 365 para dispositivos Windows 10 com](../apps/apps-add-office365.md)o Microsoft Intune .

#### <a name="intune-app-protection-policy-app-character-limit-setting---3291302----"></a>Configuração de limite de caracteres da política de proteção de aplicativo do Intune (aplicativo)<!-- 3291302  -->
Os administradores intune podem especificar uma exceção ao corte, cópia e cola intune APP **Restrict com outras definições** de política de aplicações.  Como administrador, você pode especificar o número de caracteres que podem ser recortados ou copiados de um aplicativo gerenciado. Essa configuração permitirá o compartilhamento do número especificado de caracteres para qualquer aplicativo, independentemente da configuração "restringir recortar, copiar e colar com outros aplicativos". Observe que a versão do aplicativo Portal da Empresa do Intune para Android requer a versão 5.0.4364.0 ou posterior. Para mais informações, consulte a proteção de [dados iOS](../apps/app-protection-policy-settings-ios.md#data-protection), [a proteção de dados Android](../apps/app-protection-policy-settings-android.md#data-protection)e reveja os registos de proteção de [aplicações dos clientes.](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings)

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment---3192477-----"></a>Ferramenta de implantação do Office (ODT) XML para implantação do Office ProPlus<!-- 3192477   -->
Você poderá fornecer o XML da ferramenta de implantação do Office (ODT) ao criar uma instância do Office Pro Plus no console de administração do Intune. Isso permitirá maior personalização se as opções de interface do usuário do Intune existentes não atenderem às suas necessidades. Para mais informações, consulte [as aplicações do Office 365 para dispositivos Windows 10 com](../apps/apps-add-office365.md) opções de Intune e Configuração microsoft [para a Ferramenta de Implementação do Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background---1429026----"></a>Os ícones de aplicativo agora serão exibidos com um plano de fundo gerado automaticamente<!-- 1429026  -->
No aplicativo Windows Portal da Empresa, os ícones de aplicativo agora serão exibidos com um plano de fundo gerado automaticamente com base na cor dominante do ícone (se puder ser detectado). Quando aplicável, esse plano de fundo substituirá a borda cinza que estava visível anteriormente nos blocos do aplicativo. Os usuários verão essa alteração nas versões do Portal da Empresa posteriores a 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment---2751523-----"></a>Instalar aplicativos disponíveis usando o aplicativo Portal da Empresa após o registro em massa do Windows<!-- 2751523   -->
Os dispositivos Windows registrados no Intune usando o [registro em massa do Windows](../enrollment/windows-bulk-enroll.md) (pacotes de provisionamento) poderão usar o aplicativo portal da empresa para instalar os aplicativos disponíveis. Para obter mais informações sobre o aplicativo Portal da Empresa, consulte [adicionar manualmente o portal da empresa do Windows 10](../apps/store-apps-company-portal-app.md) e [como configurar o aplicativo Microsoft Intune portal da empresa](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite---3828932----"></a>O aplicativo Microsoft Teams pode ser selecionado como parte do pacote de aplicativos do Office<!-- 3828932  -->
O aplicativo Microsoft Teams pode ser incluído ou excluído como parte da instalação do Office Pro Plus app Suite. Esse recurso funciona para o Office Pro Plus número de Build 16.0.11328.20116 +. O usuário deve sair e, em seguida, entrar no dispositivo para que a instalação seja concluída. No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. Selecione um dos tipos de aplicativos **Office 365 Suite** e, em seguida, selecione **Configure App Suite**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices---2351390---"></a>Iniciar automaticamente um aplicativo ao executar vários aplicativos no modo de quiosque em dispositivos Windows 10 e posteriores<!-- 2351390 -->

No Windows 10 e em dispositivos posteriores, você pode executar um dispositivo no modo de quiosque e executar muitos aplicativos. Nesta atualização, existe uma definição **de AutoLaunch** (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **Windows 10 e, mais tarde,** para plataforma > **Quiosque** para o tipo de perfil > **quiosque multi-app).** Use essa configuração para iniciar automaticamente um aplicativo quando o usuário entrar no dispositivo.

Para ver uma lista e descrição de todas as definições do quiosque, consulte as [definições do Windows 10 e posteriormente](../configuration/kiosk-settings-windows.md)do dispositivo para funcionar como um quiosque em Intune .

Aplica-se a: Windows 10 e posterior

#### <a name="operational-logs-also-show-details-on-non-compliant-devices---4063755----"></a>Os logs operacionais também mostram detalhes sobre dispositivos não compatíveis<!-- 4063755  -->
Ao rotear logs do Intune para recursos do Azure monitor, você também pode rotear os logs operacionais. Nessa atualização, os logs operacionais também fornecem informações sobre dispositivos sem conformidade.

Para obter mais informações sobre esta funcionalidade, consulte Enviar dados de registo para armazenamento, centros de [eventos ou análisede log em Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads---3804627---"></a>Rotear logs para Azure Monitor em mais cargas de trabalho do Intune<!-- 3804627 -->
Em Intune, pode encaminhar registos de auditoria e operacionais para centros de eventos, armazenamento e análise de registo**sintetizadores** em **Definições**de Diagnóstico de > De monitorização ( Intune > **Monitoring** ). Nessa atualização, você pode rotear esses logs em mais cargas de trabalho do Intune, incluindo conformidade, configurações, aplicativos cliente e muito mais.

Para saber mais sobre o encaminhamento de registos para o Monitor Azure, consulte enviar dados de [registo para armazenamento, centros](../review-logs-using-azure-monitor.md)de eventos ou análise de registo .

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune---3305880-----"></a>Criar e usar extensões de mobilidade em dispositivos Android pretas no Intune<!-- 3305880   -->
Nesta atualização, o Intune dá suporte à configuração de dispositivos Android pretas. Especificamente, pode criar um perfil de configuração do dispositivo e aplicar configurações para dispositivos Android Zebra utilizando perfis de Extensões de Mobilidade (MX) gerados pelo StageNow –**Configuração** do dispositivo > **Perfis** > **Criar perfil** > **Android** para o perfil da plataforma > **MX (apenas zebra)** para o tipo de perfil).

Para obter mais informações sobre esta funcionalidade, consulte [Utilize e gerencie dispositivos Zebra com extensões de mobilidade em Intune](../configuration/android-zebra-mx-overview.md).

Aplica-se a: Android

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos
#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Relatório de criptografia para dispositivos Windows 10 (em visualização pública)<!-- 2351538 -->
Utilize o novo relatório de [encriptação (Pré-visualização)](../protect/encryption-monitor.md) para visualizar detalhes sobre o estado de encriptação dos seus dispositivos Windows 10. Os detalhes disponíveis incluem uma versão do TPM de dispositivos, prontidão de criptografia e status, relatório de erros e muito mais.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview---2351547-----"></a>Acessar chaves de recuperação do BitLocker no portal do Intune (em visualização pública)<!-- 2351547   -->
Agora pode utilizar o Intune para [ver detalhes](../protect/encryption-monitor.md) sobre as chaves de id de chave BitLocker e bitLocker, a partir do Diretório Ativo Azure.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Suporte do Microsoft Edge para cenários do Intune em dispositivos iOS e Android<!-- 3411007 -->
O Microsoft Edge dará suporte a todos os mesmos cenários de gerenciamento que o Intune Managed Browser com a adição de melhorias à experiência do usuário final. Os recursos do Microsoft Edge Enterprise habilitados pelas políticas do Intune incluem identidade dupla, integração de política de proteção de aplicativo, integração de proxy de aplicativo do Azure e atalhos de home page e favoritos gerenciados. Para mais informações, consulte o [suporte do Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices--3105122----"></a>O conector do Exchange Online/Intune preteri o suporte para dispositivos EAS somente<!--3105122  -->
O console do Intune não dá mais suporte à exibição e ao gerenciamento de dispositivos somente EAS conectados ao Exchange Online com o conector do Intune. Em vez disso, você tem as seguintes opções:
- Registrar dispositivos no MDM (gerenciamento de dispositivo móvel)
- Usar políticas de Proteção de Aplicativo do Intune para gerenciar seus dispositivos
- Utilize os [controlos](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) de troca conforme delineado em Clientes e mobile em Exchange Online

#### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name--4254930---"></a>Procure na página Todos os dispositivos um dispositivo exato utilizando [nome]<!--4254930 -->
Agora você pode pesquisar um nome de dispositivo exato. Vá a **Intune** > **Devices** > **Todos os dispositivos** > na caixa de pesquisa, rodeie o nome do dispositivo com {} para procurar uma correspondência exata. Por exemplo, **{Dispositivo12345}** .

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="support-for-additional-connectors-on-the-tenant-status-page---3617202----"></a>Suporte para conectores adicionais na página de status do locatário<!-- 3617202  -->
A [página 'Status'](../tenant-status.md) do Inquilino apresenta agora informações sobre o estado dos conectores adicionais, incluindo a Proteção avançada de Ameaças (ATP) do *Windows Defender* e outros conectores de Defesa de Ameaças Móveis.

#### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune---4260871---"></a>Suporte para o aplicativo de conformidade de Power BI da folha de data warehouse no Microsoft Intune<!-- 4260871 -->
Anteriormente, o link de **ficheiro sonuque Power BI** na lâmina **intune Data Warehouse** descarregou um relatório intune Data Warehouse (ficheiro.pbix). Este relatório foi substituído pelo aplicativo de conformidade Power BI. O aplicativo de conformidade Power BI não exigirá carregamento ou configuração especial. Ele será aberto diretamente no portal do Power BI online e exibirá dados especificamente para seu locatário do Intune com base em suas credenciais. Em Intune, selecione a ligação **'Intune Data Warehouse'** no lado direito da lâmina Intune. Em seguida, clique em **Obter Power BI App**. Para mais informações, consulte [Connect to the Data Warehouse with Power BI](../developer/reports-proc-get-a-link-powerbi.md).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles---3637917----"></a>Concedendo acesso somente leitura do Intune a algumas funções de Azure Active Directory<!-- 3637917  -->
O acesso somente leitura do Intune foi concedido às seguintes funções do Azure AD. As permissões concedidas com as funções do Azure AD substituem as permissões concedidas com o RBAC (controle de acesso baseado em função) do Intune.

Acesso somente leitura aos dados de auditoria do Intune:

- Administrador de conformidade
- Administrador de dados de conformidade

Acesso somente leitura a todos os dados do Intune:

- Administrador de Segurança
- Operador de segurança
- Leitor de Segurança

Para mais informações, consulte [o controlo de acesso baseado em funções.](role-based-access-control.md)

#### <a name="scope-tags-for-ios-app-provisioning-profiles--2934430-----"></a>Marcas de escopo para perfis de provisionamento de aplicativo iOS<!--2934430   -->
Você pode adicionar uma marca de escopo a um perfil de provisionamento de aplicativo iOS para que somente as pessoas com funções também atribuídas a essa marca de escopo tenham acesso ao perfil de provisionamento de aplicativo iOS. Para mais informações, consulte [Use RBAC e etiquetas de mira.](scope-tags.md)

#### <a name="scope-tags-for-app-configuration-policies--2371891-----"></a>Marcas de escopo para políticas de configuração de aplicativo<!--2371891   -->
Você pode adicionar uma marca de escopo a uma política de configuração de aplicativo para que somente as pessoas com funções também atribuídas a essa marca de escopo tenham acesso à política de configuração de aplicativo. A política de configuração de aplicativo só pode ser destinada ou associada a aplicativos atribuídos à mesma marca de escopo. Para mais informações, consulte [Use RBAC e etiquetas de mira.](scope-tags.md)

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Suporte do Microsoft Edge para cenários do Intune em dispositivos iOS e Android<!-- 3411007 -->
O Microsoft Edge dará suporte a todos os mesmos cenários de gerenciamento que o Intune Managed Browser com a adição de melhorias à experiência do usuário final. Os recursos do Microsoft Edge Enterprise habilitados pelas políticas do Intune incluem identidade dupla, integração de política de proteção de aplicativo, integração de proxy de aplicativo do Azure e atalhos de home page e favoritos gerenciados. Para mais informações, consulte o [suporte do Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).




<!-- ########################## -->
## <a name="february-2019"></a>fevereiro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações
#### <a name="intune-macos-company-portal-dark-mode---3300524----"></a>Modo escuro do Intune macOS Portal da Empresa<!-- 3300524  -->
O Portal da Empresa do Intune no macOS agora dá suporte ao modo escuro para macOS. Quando você habilita o modo escuro em um dispositivo macOS 10.14 +, o Portal da Empresa ajustará sua aparência às cores que refletem esse modo.

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices---2577355-----"></a>O Intune aproveitará Google Play proteger APIs em dispositivos Android<!-- 2577355   -->
Alguns administradores de ti enfrentam um cenário de BYOD em que os usuários finais podem acabar com a raiz ou jailbreakingr seus celulares. Esse comportamento, embora às vezes não seja mal intencional, resulta em um bypass de muitas políticas do Intune que são definidas para proteger os dados da organização em dispositivos de usuário final. Portanto, o Intune fornece detecção de raiz e jailbreak para dispositivos registrados e não registrados. Com esta versão, o Intune agora aproveitará Google Play proteger APIs para adicionar às nossas verificações de detecção de raiz existentes para dispositivos não registrados. Embora o Google não compartilhe integralmente as verificações de detecção de raiz que ocorrem, esperamos que essas APIs detectem usuários que fizeram a raiz de seus dispositivos por qualquer motivo, desde a personalização do dispositivo até a capacidade de obter atualizações mais recentes do sistema operacional em dispositivos mais antigos. Esses usuários podem então ser impedidos de acessar dados corporativos ou suas contas corporativas podem ser apagadas de seus aplicativos habilitados para políticas. Para um valor adicional, o administrador de ti agora terá várias atualizações de relatório na folha Proteção de Aplicativo do Intune-o relatório "usuários sinalizados" mostrará quais usuários são detectados por meio da verificação de API SafetyNet do Google Play Protect, o relatório "aplicativos potencialmente prejudiciais" Mostre quais aplicativos são detectados por meio da verificação da API de aplicativos de verificação do Google. Esse recurso está disponível no Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade---2617342-----"></a>Informações do aplicativo Win32 disponíveis na folha de solução de problemas<!-- 2617342   -->
Agora pode recolher ficheiros de registo de falhas para uma instalação de aplicação Win32 a partir da lâmina de resolução de **problemas** da aplicação Intune. Para obter mais informações sobre a resolução de problemas de instalação de aplicações, consulte problemas de instalação de [aplicações Troubleshoot](./../apps/troubleshoot-app-install.md) e [problemas com aplicações Troubleshoot Win32.](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting)

#### <a name="app-status-details-for-ios-apps---3761235-----"></a>Detalhes de status do aplicativo para aplicativos iOS<!-- 3761235   -->
Há novas mensagens de erro de instalação de aplicativo relacionadas ao seguinte:
- Falha para aplicativos VPP ao instalar em iPad compartilhado
- Falha quando a loja de aplicativos está desabilitada
- Falha ao localizar a licença do VPP para o aplicativo
- Falha ao instalar aplicativos de sistema com o provedor de MDM
- Falha ao instalar aplicativos quando o dispositivo está no modo perdido ou no modo de quiosque
- Falha ao instalar o aplicativo quando o usuário não está conectado à loja de aplicativos

Intune, selecione **Aplicações cliente** > **Apps** > "Nome de aplicação" > Estado de **instalação do dispositivo.** Novas mensagens de erro estarão disponíveis na coluna de detalhes do **Estado.**

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Tela de novas categorias de aplicativo no aplicativo Portal da Empresa para Windows 10<!-- 3834780  -->
Foi adicionado um novo ecrã chamado **Categorias app** para melhorar a experiência de navegação e seleção de aplicações no Portal da Empresa para o Windows 10. Os utilizadores verão agora as suas aplicações classificadas em categorias como **Featured**, **Education**e **Productivity**. Essa alteração aparece em Portal da Empresa versões 10.3.3451.0 e posteriores. Para exibir a nova tela, consulte [o que há de novo na interface do usuário do aplicativo](whats-new-app-ui.md). Para obter mais informações sobre aplicativos no Portal da Empresa, consulte [instalar e compartilhar aplicativos em seu dispositivo](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app---1455231-doc-work-item---"></a>Aplicativo de conformidade Power BI<!-- 1455231 doc-work-item -->
Aceda ao seu Intune Data Warehouse em Power BI Online utilizando a aplicação [Intune Compliance (Data Warehouse).](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) Com este Power BI aplicativo, agora você pode acessar e compartilhar relatórios pré-criados sem nenhuma configuração e sem sair do navegador da Web. Para obter informações adicionais, consulte [alterar o registo - aplicação de conformidade do Power BI](../developer/reports-changelog.md#power-bi-compliance-app).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices---1862675-----"></a>Os scripts do PowerShell podem ser executados em um host de 64 bits em dispositivos de 64 bits<!-- 1862675   -->
Quando você adiciona um script do PowerShell a um perfil de configuração do dispositivo, o script sempre é executado no 32-bit, mesmo em sistemas operacionais de 64 bits. Com esta atualização, um administrador pode executar o script num anfitrião powerShell de 64 bits em dispositivos de 64 bits (**configuração** do dispositivo > **scripts PowerShell** > **Adicionar** > **Configure** > **Executar script em PowerShell Host de 64 bits**).

Para mais detalhes sobre a utilização do PowerShell, consulte [os scripts PowerShell em Intune](../apps/intune-management-extension.md).

Aplica-se a: Windows 10 e posterior

#### <a name="macos-users-are-prompted-to-update-their-password---1873216---"></a>os usuários do macOS são solicitados a atualizar sua senha<!-- 1873216 -->
A Intune está a impor a definição **ChangeAtNextAuth** nos dispositivos macOS. Essa configuração afeta os usuários finais e os dispositivos que têm políticas de senha de conformidade ou perfis de senha de restrição de dispositivo. Os usuários finais são solicitados uma vez para atualizar sua senha. Esse prompt ocorre sempre que um usuário executa pela primeira vez uma tarefa que requer autenticação, como entrar no dispositivo. Os usuários também podem ser solicitados a atualizar sua senha ao fazer qualquer coisa que exija privilégios administrativos, como solicitar o acesso ao conjunto de chaves.

Qualquer política de senha nova ou existente é alterada pelo administrador solicitando os usuários finais novamente para atualizar sua senha.

Aplica-se a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device---2340521------"></a>Atribuir certificados SCEP a um dispositivo macOS-não-usuário<!-- 2340521    -->
Você pode atribuir certificados de protocolo SCEP (SCEP) usando atributos de dispositivo para dispositivos macOS, incluindo dispositivos sem afinidade de usuário, e associar o perfil de certificado a perfis Wi-Fi ou VPN. Isto expande o suporte que já temos de [atribuir certificados SCEP a dispositivos com e sem afinidade](../protect/certificates-profile-scep.md) de utilizadores que executam Windows, iOS e Android.  Esta atualização adiciona a opção de selecionar um tipo de *Dispositivo* de Certificado quando configurar um perfil de certificado SCEP para o macOS.

Aplica-se a:
- macOS

#### <a name="intune-conditional-access-ui-update---2432313-----"></a>Atualização da interface do usuário de acesso condicional do Intune<!-- 2432313   -->
Fizemos melhorias na interface do usuário para acesso condicional no console do Intune. Estas atualizações incluem:
- Substituiu a lâmina de *acesso condicional* Intune pela lâmina do Diretório Ativo Azure. Isto garante que terá acesso a toda a gama de configurações e configurações para [acesso condicional](../protect/conditional-access.md) (que continua a ser uma tecnologia Azure AD), a partir da consola Intune. 
- Rebatizamos a lâmina *de acesso on-premida* para *o acesso*ao Exchange e deslocámos a configuração do *conector* de serviço exchange para esta lâmina renomeada.  Esta alteração consolida-se onde [configura e monitoriza detalhes relacionados com o Exchange online e no local.](../protect/exchange-connector-install.md)  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode---2935135-----"></a>Os aplicativos navegador de quiosque e navegador Microsoft Edge podem ser executados em dispositivos Windows 10 no modo de quiosque<!-- 2935135   -->
Você pode usar dispositivos Windows 10 no modo de quiosque para executar um aplicativo ou muitos aplicativos. Essa atualização inclui várias alterações no uso de aplicativos de navegador no modo de quiosque, incluindo:

- Adicione o Navegador Microsoft Edge ou o Navegador Kiosk para executar como aplicações no dispositivo de quiosque (**configuração** do dispositivo > **Perfis** > **Novo perfil** > **Windows 10 e mais tarde** para plataforma > **Quiosque** para tipo de perfil).
- Novas funcionalidades e configurações estão disponíveis para permitir ou restringir (**configuração do dispositivo** **perfis** > perfis > **Novo perfil** > **Windows 10 e posteriormente** para **restrições** de plataforma > dispositivo para tipo de perfil), incluindo:

- Navegador Microsoft Edge:
  - Usar o modo de quiosque do Microsoft Edge
  - Atualizar o navegador após o tempo ocioso

- Favoritos e pesquisa:
  - Permitir alterações no mecanismo de pesquisa

Para obter uma lista dessas configurações, consulte:

- [Windows 10 e posteriores configurações do dispositivo para funcionar como um quiosque](../configuration/kiosk-settings-windows.md)
- [Restrições ao dispositivo do Microsoft Edge Browser](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Restrições de dispositivos favoritos e de pesquisa](../configuration/device-restrictions-windows-10.md##favorites-and-search)

Aplica-se a: Windows 10 e posterior

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices---3448774-----"></a>Novas configurações de restrição de dispositivo para dispositivos iOS e macOS<!-- 3448774   -->
Pode restringir algumas definições e funcionalidades em dispositivos que executam iOS e macOS (**configuração** do dispositivo > **Perfis** > **Novo perfil** > iOS ou **macOS** para **restrições** de plataforma > Dispositivo para tipo de perfil). Esta atualização adiciona mais recursos e configurações que você pode controlar, incluindo a configuração de tempo da tela, alteração das configurações do eSIM e planos de celular e muito mais em dispositivos iOS. Além disso, atrasar a visibilidade do usuário de atualizações de software e bloquear o cache de conteúdo em dispositivos macOS.

Para ver os recursos e as configurações que você pode restringir, consulte:

- [Definições de restrição de dispositivos iOS](../configuration/device-restrictions-ios.md)
- [Definições de restrição do dispositivo macOS](../configuration/device-restrictions-macos.md)

Aplica-se a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices---3598402-----"></a>Os dispositivos "quiosque" agora são chamados de "dispositivos dedicados" em dispositivos Android Enterprise<!-- 3598402   -->
Para alinhar com a terminologia Android, o **quiosque** é alterado para **dispositivos dedicados** para dispositivos empresariais Android (**Configuração de dispositivos** > **Perfis** > **Criar perfil** > **Android enterprise para plataforma > Dispositivo **Proprietário Apenas** > Restrições de **Dispositivo s > ** **dispositivos dedicados).**

Para ver as definições disponíveis, vá às definições do [Dispositivo para permitir ou restringir as funcionalidades](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Aplica-se a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui---3640850-3803313-----"></a>O Safari e atrasando as configurações do iOS de visibilidade da atualização de software do usuário estão se movendo na interface do usuário do Intune<!-- 3640850, 3803313   -->
Para dispositivos iOS, você pode definir as configurações do Safari e configurar as atualizações de software. Nesta atualização, essas configurações estão mudando para diferentes partes da interface do usuário do Intune:

- As definições do Safari passaram do **Safari** –**Configuração** do dispositivo > Perfis > **Novo perfil** > **iOS** para **restrições** de plataforma > dispositivo para tipo de perfil) para **[Aplicações](../configuration/device-restrictions-ios.md#built-in-apps)** **Incorporadas.**
- A visibilidade da atualização de software do utilizador para a definição **de dispositivos iOS supervisionados** (**atualizações** de software > **Atualizações de tecnologia para iOS**) está a mover-se para **restrições** de dispositivos >  **[Geral](../configuration/device-restrictions-ios.md#general)** .  Para mais detalhes sobre o impacto nas políticas existentes, consulte as atualizações de [software do iOS.](../protect/software-updates-ios.md#configure-the-policy)

Para obter uma lista das configurações, consulte:

- [Restrições de dispositivos iOS](../configuration/device-restrictions-ios.md) 
- [atualizações de software iOS](../protect/software-updates-ios.md)

Esta funcionalidade aplica-se a:

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices---3699164-----"></a>Habilitar restrições nas configurações do dispositivo é renomeado para tempo de tela em dispositivos iOS<!-- 3699164   -->
Pode configurar as **restrições de habilitação nas definições do dispositivo** em dispositivos iOS supervisionados (**configuração** do dispositivo > **Perfis** > **Novo perfil** > **iOS** para as **restrições** do tipo de perfil > **Geral).** Nesta atualização, esta definição é renomeada para Tempo de **Ecrã (apenas supervisionado)** .

O comportamento é o mesmo. Especificamente:

- iOS 11.4.1 e anterior: **Bloquear** impede que os usuários finais definam suas próprias restrições nas configurações do dispositivo. 
- iOS 12.0 e posteriormente: **O bloco** impede que os utilizadores finais definam o seu próprio Tempo de **Ecrã** nas definições do dispositivo, incluindo restrições de conteúdo e privacidade. Os dispositivos atualizados para iOS 12,0 não verão mais a guia restrições nas configurações do dispositivo. Estas definições estão em **Tempo do Ecrã**. 

Para obter uma lista das definições, consulte as restrições do [dispositivo iOS](../configuration/device-restrictions-ios.md#general).

Aplica-se a:
- iOS


#### <a name="intune-powershell-module---951068----"></a>Módulo do Intune PowerShell<!-- 951068  -->
O módulo Intune PowerShell, que fornece suporte para o Intune API através do Microsoft Graph, está agora disponível na [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Detalhes sobre como usar este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemplos de cenário usando este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization--3183757----"></a>Suporte aprimorado para otimização de entrega<!--3183757  -->
Expandimos o suporte no Intune para configurar a otimização de entrega. Agora pode configurar uma lista expandida de definições de [Otimização](../configuration/delivery-optimization-settings.md) de Entrega e direcioná-la para os seus dispositivos diretamente da consola Intune.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de dispositivos

#### <a name="rename-an-enrolled-windows-device---1911112----"></a>Renomear um dispositivo Windows registrado<!-- 1911112  -->
Agora você pode renomear um dispositivo Windows 10 registrado (RS4 ou posterior). Para fazer, escolha **Dispositivos** **Intune** >  > **Todos os dispositivos** > escolha um dispositivo > **Rename**. Atualmente, esse recurso não dá suporte à renomeação de dispositivos Windows do Azure AD híbridos.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope---3173823----"></a>Atribuir automaticamente marcas de escopo a recursos criados por um administrador com esse escopo<!-- 3173823  -->
Quando um administrador cria um recurso, todas as marcas de escopo atribuídas ao administrador serão automaticamente atribuídas a esses novos recursos.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade---3560202----"></a>O relatório de registro com falha se move para a folha de registro do dispositivo<!-- 3560202  -->
O relatório **de matrículas falhada** foi transferido para a secção **monitora** da lâmina de matrícula do **Dispositivo.** Duas novas colunas (método de registro e versão do sistema operacional) foram adicionadas.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments--3815076-eemiss---"></a>Portal da Empresa relatório de abandono renomeado para inscrições incompletas do usuário<!--3815076 eemiss -->
O relatório de abandono do **Portal da Empresa** foi renomeado para **inscrições incompletas de utilizadores.**






<!-- ########################## -->
## <a name="january-2019"></a>janeiro de 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestão de aplicações

#### <a name="intune-app-pin---2298397---"></a>PIN do aplicativo do Intune<!-- 2298397 -->
Como administrador de ti, agora você pode configurar o número de dias que um usuário final pode esperar até que o PIN do seu aplicativo do Intune seja alterado. A nova definição é *redefinida pin após o número de dias* e está disponível no portal Azure selecionando **aplicações** **intune** > Cliente > políticas de **proteção** de aplicações > Criar **Definições** **políticas** >  > requisitos de **acesso.** Disponível para dispositivos [iOS](../apps/app-protection-policy-settings-ios.md) e [Android,](../apps/app-protection-policy-settings-android.md) esta funcionalidade suporta um valor inteiro positivo.

#### <a name="intune-device-reporting-fields---2748738---"></a>Campos de relatório de dispositivo do Intune<!-- 2748738 -->
O Intune fornece campos de relatório de dispositivo adicionais, incluindo ID de registro do aplicativo, fabricante do Android, modelo e versão do patch de segurança, bem como o modelo do iOS. No Intune, estes campos estão disponíveis selecionando **aplicações do Cliente** > estado de **proteção** de aplicações e escolhendo o Relatório de Proteção de **Aplicações: iOS, Android**. Além disso, esses parâmetros irão ajudá-lo a configurar o **permitir** lista para o fabricante do dispositivo (Android), o **permitir** lista para o modelo do dispositivo (Android e iOS) e o patch de segurança mínima para Android definição de versão.

#### <a name="toast-notifications-for-win32-apps---3136566-----"></a>Notificações do sistema para aplicativos Win32<!-- 3136566   -->
Você pode suprimir a exibição de notificações do sistema de usuário final por atribuição de aplicativo. A partir de Intune, selecione **aplicações do Cliente** > **Apps** > selecione a app > **Atribuições** > **Incluir Grupos.**

#### <a name="intune-app-protection-policies-ui-update---3251427----"></a>Atualização da interface do usuário das políticas de proteção de aplicativo<!-- 3251427  -->
Alteramos os rótulos de configurações e botões para a proteção de aplicativo do Intune para facilitar a compreensão. Algumas das alterações incluem:  
- Os controles são alterados de **sim** / **nenhum** controle para **Bloquear** principalmente / **permitir** e **desabilitar** / **habilitar** controles. Os rótulos também são atualizados.  
- As configurações são reformatadas, portanto, a configuração e seu rótulo são lado a lado no controle, para fornecer melhor navegação.

As configurações padrão e o número de configurações permanecem os mesmos, mas essa alteração permite que o usuário entenda, navegue e utilize as configurações mais facilmente para aplicar as políticas de proteção de aplicativo selecionadas. Para obter informações, consulte [as definições do iOS](../apps/app-protection-policy-settings-ios.md) e [as definições do Android.](../apps/app-protection-policy-settings-android.md)

#### <a name="additional-settings-for-outlook---3301182----"></a>Configurações adicionais para o Outlook<!-- 3301182  -->
Agora você pode definir as seguintes configurações adicionais para o Outlook para iOS e Android usando o Intune:

- Permitir que apenas contas corporativas ou de estudante sejam usadas no Outlook no iOS e no Android
- Implantar a autenticação moderna para o Office 365 e contas locais de autenticação moderna híbrida
- Utilize `SAMAccountName` para o campo username no perfil de e-mail quando a autenticação básica for selecionada
- Permitir que os contatos sejam salvos
- Configurar os destinatários externos dicas de Recipient
- Configure **caixa de entrada focada**
- Exigir biometria para acessar o Outlook para iOS
- Bloquear imagens externas

> [!NOTE]
> Se estiver a utilizar políticas de Proteção de Aplicações Intune para gerir o acesso a identidades corporativas, deve considerar não permitir a **necessidade de biometria.** Para mais informações, consulte **Requerer credenciais corporativas para acesso** a definições de [acesso iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) e [Definições](../apps/app-protection-policy-settings-android.md#access-requirements)de Acesso Android .

Para obter mais informações, consulte [definições de configuração do Microsoft Outlook](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps---1352553---"></a>Excluir aplicativos corporativos do Android<!-- 1352553 -->
Você pode excluir aplicativos Google Play gerenciados do Microsoft Intune. Para eliminar uma aplicação do Managed Google Play, abra o Microsoft Intune no portal do Azure e selecione **Aplicações cliente** > **Aplicações**. Na lista de aplicações, selecione as reticências (...) à direita da aplicação do Managed Google Play e, em seguida, selecione **Eliminar** na lista apresentada. Quando elimina uma aplicação do Managed Google Play da lista de aplicações, essa aplicação passa automaticamente a não aprovada.

#### <a name="managed-google-play-app-type---1352580---"></a>Tipo de aplicações do Managed Google Play<!-- 1352580 -->
O tipo de aplicação gerida do **Google Play** permitir-lhe-á adicionar especificamente [aplicações geridas](https://play.google.com/work/search?q=microsoft&c=apps) do Google Play ao Intune. Como administrador do Intune, agora você pode procurar, Pesquisar, aprovar, sincronizar e atribuir aplicativos de Google Play gerenciados aprovados no Intune.  Já não precisa de procurar na consola do Managed Google Play separadamente e já não tem de se autenticar novamente.  No Intune, selecione **aplicativos cliente** > **aplicativos** > **Adicionar**. Na lista do **tipo App,** selecione **Managed Google Play** como o tipo de aplicação.

#### <a name="default-android-pin-keyboard---3802457---"></a>Teclado padrão de PIN do Android<!-- 3802457 -->
Para os usuários finais que definiram um PIN de política de Proteção de Aplicativo do Intune (aplicativo) em seus dispositivos Android com o tipo de PIN ' numeric ', eles agora verão o teclado Android padrão em vez da interface do usuário do teclado do Android fixa que foi previamente projetada. Essa alteração foi feita para ser consistente ao usar teclados padrão no Android e no iOS, para ambos os tipos de PIN de ' numeric ' e/ou ' senha '. Para obter mais informações sobre as definições de acesso ao utilizador final no Android, como o APP PIN, consulte [os requisitos de acesso ao Android.](../apps/app-protection-policy-settings-android.md#access-requirements)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Os modelos administrativos estão em visualização pública e movidos para seu próprio perfil de configuração <!-- 3322847 -->

Os modelos administrativos em Intune (**configuração** do dispositivo > **modelos administrativos)** estão atualmente em pré-visualização pública. Com esta atualização:

- Os modelos administrativos incluem as configurações de 300 que podem ser gerenciadas no Intune. Anteriormente, estas definições só existiam no editor de políticas de grupo.
- Os modelos administrativos estão disponíveis em visualização pública.
- Os modelos administrativos estão a mover-se da **configuração** do Dispositivo > **modelos administrativos** para a **configuração** do dispositivo > **Perfis** > **Criar perfil** > na **Plataforma,** escolha **o Windows 10 e mais tarde** > no tipo de **perfil,** escolha **modelos administrativos.**
- O relatório está habilitado

Para ler mais sobre esta funcionalidade, vá aos [modelos do Windows 10 para configurar as definições](../configuration/administrative-templates-windows.md)de política do grupo .

Aplica-se a: Windows 10 e posterior

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user---1333642---"></a>Usar S/MIME para criptografar e assinar vários dispositivos para um usuário<!-- 1333642 -->
Esta atualização inclui a encriptação de e-mails com S/MIME através de um novo perfil de certificado importado (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > selecione a plataforma > tipo de perfil **Certificados PKCS importados**). No Intune, pode importar certificados no formato PFX. O Intune pode enviar esses mesmos certificados para múltiplos dispositivos inscritos por um único utilizador. Isto também inclui:
- O perfil de e-mail nativo do iOS suporta a ativação da encriptação S/MIME através de certificados importados no formato PFX.
- O aplicativo de email nativo em Windows Phone 10 dispositivos usa automaticamente o certificado S/MIME.
- Os certificados privados podem ser fornecidos a várias plataformas. No entanto, nem todas as aplicações de e-mail suportam S/MIME.
- Noutras plataformas, talvez seja necessário configurar manualmente a aplicação de e-mail para permitir o S/MIME.  
- As aplicações de e-mail que suportam a encriptação S/MIME conseguem obter certificados para a encriptação S/MIME de e-mails de uma forma que não é suportada por MDM, como a leitura a partir do arquivo de certificados do respetivo publicador.
Para mais informações sobre esta funcionalidade, consulte a [visão geral da S/MIME para assinar e encriptar e-mails](../protect/certificates-s-mime-encryption-sign.md).
Suportado no: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices---1333665-2999078---"></a>Novas opções para se conectar e manter as regras automaticamente ao usar as configurações de DNS no Windows 10 e em dispositivos posteriores<!-- 1333665, 2999078 -->
No Windows 10 e em dispositivos posteriores, você pode criar um perfil de configuração de VPN que inclui uma lista de servidores DNS para resolver domínios, como contoso.com. Esta atualização inclui novas definições para resolução de **nomes** (**configuração** do dispositivo > Perfis > **Criar perfil** > Escolha **o Windows 10 e, mais tarde,** para plataforma > Escolha **VPN** para definições de perfil > **DNS** >**Adicionar**): 
- **Ligar automaticamente**: quando **ativado**, o dispositivo estabelece ligação automaticamente para a VPN quando um dispositivo entra em contacto com um domínio, introduza, por exemplo, contoso.com.
- **Persistente**: por predefinição, todas as regras de tabela (NRPT) de política de resolução de nome estão ativas, desde que o dispositivo estiver conectado com este perfil VPN. Quando esta definição é **ativada** numa regra NRPT, a regra permanece ativa no dispositivo, mesmo quando a VPN se desliga. A regra permanece até que o perfil VPN seja removido ou até que a regra seja manualmente removida, o que pode ser feito usando o PowerShell.
[As definições VPN do Windows 10](../configuration/vpn-settings-windows-10.md) descrevem as definições.

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices---1500165---"></a>Usar detecção de rede confiável para perfis VPN em dispositivos Windows 10<!-- 1500165 -->
Ao usar a detecção de rede confiável, você pode impedir que perfis VPN criem automaticamente uma conexão VPN quando o usuário já estiver em uma rede confiável. Com esta atualização, pode adicionar sufixos DNS para permitir a deteção fidedigna de rede em dispositivos que executam o Windows 10 e posteriormente **(Configuração** do dispositivo > **Perfis** > **Criar perfil** > **Windows 10 e mais tarde** para plataforma > **VPN** para o tipo de perfil).
[Definições de VPN do Windows 10](../configuration/vpn-settings-windows-10.md) lista as definições de VPN atuais.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users---1907917-1063203---"></a>Gerenciar dispositivos Windows Holographic for Business usados por vários usuários<!-- 1907917, 1063203 -->
No momento, você pode definir configurações de computador compartilhado em dispositivos Windows 10 e Windows Holographic for Business usando uma configuração de OMA-URI personalizada. Com esta atualização, é adicionado um novo perfil para configurar as definições de dispositivos **partilhados** (**configuração** do dispositivo > Perfis > **Criar perfil** > **Windows 10 e, posteriormente,**  > **dispositivo multiutilizador partilhado).**
Para saber mais sobre esta funcionalidade, vá a [configurações Intune para gerir dispositivos partilhados](../configuration/shared-user-device-settings.md).
Aplica-se a: Windows 10 e posterior, o Windows Holographic for Business

#### <a name="new-windows-10-update-settings--2626030--2512994----"></a>Novas configurações de atualização do Windows 10<!--2626030  2512994  -->
Para os seus Anéis de [Atualização do Windows 10,](../protect/windows-update-for-business-configure.md)pode configurar:
- **Comportamento de atualização automática** - Utilize uma nova opção, *Reset para o padrão* para restaurar as definições originais de atualização automática numa máquina do Windows 10 em máquinas que executam a Atualização de outubro de *2018*
- **Bloqueie o utilizador a partir de uma pausa nas atualizações do Windows** - Configure uma nova definição de atualizações de Software que lhe permite bloquear ou permitir que os seus utilizadores façam uma pausa na instalação da atualização a partir das *Definições* das suas máquinas.

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption---2662949---"></a>os perfis de email do iOS podem usar assinatura e criptografia S/MIME<!-- 2662949 -->
Você pode criar um perfil de email que inclui configurações diferentes. Esta atualização inclui definições de S/MIME que podem ser usadas para assinar e encriptar comunicações de e-mail em dispositivos iOS **(configuração do dispositivo** > **Perfis** > **Criar perfil** > Escolha **o iOS** para plataforma > **E-mail** para o tipo de perfil).
As definições de configuração de [e-mail iOS](../configuration/email-settings-ios.md) listam as definições.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algumas configurações do BitLocker dão suporte ao Windows 10 Pro Edition<!-- 2727036 -->
Você pode criar um perfil de configuração que define as configurações do Endpoint Protection em dispositivos Windows 10, incluindo o BitLocker. Esta atualização adiciona suporte para o Windows 10 Professional Edition para algumas configurações do BitLocker.
Para ver estas definições de proteção, vá às definições de [proteção de Endpoint para o Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>A configuração de dispositivo compartilhado foi renomeada para bloquear a mensagem da tela para dispositivos iOS no portal do Azure<!-- 2809362 -->
Quando criar um perfil de configuração para dispositivos iOS, pode adicionar definições de Configuração de **Dispositivos Partilhados** para mostrar texto específico no ecrã de bloqueio. Essa atualização inclui as seguintes alterações: 
- O **configuração de dispositivos partilhados** definições no portal do Azure são o nome mudadas para "Mensagem de ecrã de bloqueio (apenas supervisionada)" (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > Escolha **iOS** para a plataforma > Escolha **funcionalidades do dispositivo** para o tipo de perfil > **bloqueio Mensagem de ecrã**).
- Ao adicionar mensagens de ecrã de bloqueio, pode inserir um número de série, um nome de dispositivo ou outro valor específico do dispositivo como variável na **informação** de etiqueta de Ativo e **nota**de rodapé do ecrã de bloqueio . Por exemplo, pode introduzir `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` usando chaves de saída. [iOS tokens](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) apresenta uma lista de tokens disponíveis que podem ser utilizados.
[As definições para visualizar mensagens no ecrã de bloqueio](../configuration/ios-device-features-settings.md#lock-screen-message) listam as definições.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices---2827760--"></a>Nova loja de aplicativos, exibição de documento, configurações de restrição de dispositivo de jogos adicionadas a dispositivos iOS<!-- 2827760-->
Na **Configuração** do Dispositivo > **Perfis** > **Criar perfis** > **iOS** para as **restrições** de plataforma > Dispositivo para o tipo de perfil > **App Store, Doc Viewing, Gaming**, são adicionadas as seguintes definições: Permitir que as aplicações geridas escrevam contactos em contas de contactos não geridos Permitam que as aplicações não geridas leiam a partir de contas de contactos geridos Para ver estas definições, vá para as restrições do dispositivo [iOS.](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices---3201839-3201843---"></a>Novas notificações, dicas e configurações de keyguard para dispositivos Android Enterprise do proprietário do dispositivo<!-- 3201839 3201843 -->
Esta atualização inclui várias novas funcionalidades em dispositivos Android Enterprise quando em execução como proprietário do dispositivo. Para utilizar estas funcionalidades, aceda a **configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma**, escolha **Android Enterprise** > no **tipo de perfil**, escolha **proprietário do dispositivo só** > **dispositivo Restrições**.

Os novos recursos incluem:

- Desabilite as notificações do sistema de mostrar, incluindo chamadas de entrada, alertas do sistema, erros do sistema e muito mais.
- Sugere ignorar tutoriais e dicas iniciais para aplicativos que são abertos na primeira vez.
- Desabilite as configurações avançadas do keyguard, como a câmera, as notificações, o desbloqueio de impressão digital e muito mais.

Para ver as definições, vá às definições de [restrição](../configuration/device-restrictions-android-for-work.md)do dispositivo Android Enterprise .

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections---3202194---"></a>Dispositivos Android Enterprise do proprietário do dispositivo podem usar Always On conexões VPN<!-- 3202194 -->
Nesta atualização, pode utilizar ligações VPN sempre ativada nos dispositivos de proprietário do dispositivo Android empresarial. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN sempre ativada no **configuração do dispositivo** > **perfis** > **criar perfil**  >   **Android enterprise** para a plataforma > **restrições de dispositivos** para o proprietário do dispositivo só > **conectividade** definições. Para ver as definições, vá às definições de [restrição](../configuration/device-restrictions-android-for-work.md)do dispositivo Android Enterprise .

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices---3285177---"></a>Nova configuração para encerrar processos no Gerenciador de tarefas em dispositivos Windows 10<!-- 3285177 --> 
Esta atualização inclui uma nova definição para terminar a processos usando o Gerenciador de tarefas em dispositivos Windows 10. Utilizar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > no **plataforma** , escolha **Windows 10** > no **tipo de perfil**, escolha **restrições de dispositivos** > **geral** definições), optar por permitir ou impedir que esta definição.
Para ver estas definições, vá às definições de restrição do [dispositivo Windows 10](../configuration/device-restrictions-windows-10.md).
Aplica-se a: Windows 10 e posterior

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview---2055484-----"></a>Usar as configurações recomendadas pela Microsoft com linhas de base de segurança (visualização pública)<!-- 2055484   -->

O Intune tem integração com outros serviços centrados na segurança, incluindo o Windows Defender ATP e o Office 365 ATP. Os clientes estão a pedir uma estratégia comum e um conjunto coeso de fluxos de trabalho de segurança de ponto a ponto em todos os serviços do Microsoft 365. O nosso objetivo é alinhar estratégias para desenvolver soluções que criem uma ponte entre operações de segurança e tarefas de administrador comuns. No Intune, pretendemos cumprir este objetivo através da publicação de um conjunto de "Linhas de base de segurança" recomendadas pela Microsoft (**Intune** > **Linhas de base de segurança**).  Um administrador pode criar políticas de segurança diretamente dessas linhas de base e, em seguida, implantá-las em seus usuários. Você também pode personalizar as recomendações de práticas recomendadas para atender às necessidades da sua organização. O Intune assegura que os dispositivos permanecem em conformidade com estas linhas de base e notifica os administradores de utilizadores ou dispositivos que não estejam em conformidade.

Esse recurso está em visualização pública, de modo que qualquer perfil criado agora não passará para os modelos de linhas de base de segurança que estão geralmente disponíveis (GA). Você não deve planejar usar esses modelos de visualização em seu ambiente de produção.

Para saber mais sobre as linhas de segurança, consulte Criar uma linha de [segurança do Windows 10 em Intune](../protect/security-baselines-monitor.md).

Este recurso se aplica a: Windows 10 e posterior

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Não administradores podem habilitar o BitLocker em dispositivos Windows 10 ingressados no Azure AD<!-- 2147379   -->
Quando ativa as definições do BitLocker em dispositivos Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10 e posterior** para a plataforma > **proteção de ponto final** para o tipo de perfil > **encriptação Windows**), adicionar as definições do BitLocker.

Esta atualização inclui uma nova definição de disco BitLocker para permitir que os usuários padrão (não-administradores) ativar a encriptação.

Para ver as definições, vá às definições de [proteção do Ponto Final para o Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance---2192052--eepublished----"></a>Verificar a conformidade de Configuration Manager<!-- 2192052  eepublished  -->
Essa atualização inclui uma nova configuração de conformidade Configuration Manager ( **políticas** de > de**conformidade do dispositivo** > **criar política** > **Windows 10 e posterior** > **conformidade Configuration Manager**). O Configuration Manager envia sinais de conformidade ao Intune. Usando essa configuração, você pode exigir que todos os sinais de Configuration Manager retornem "em conformidade".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se algum programa no dispositivo estiver em um estado desconhecido, o dispositivo não será compatível no Intune.

[Configuração Manager Compliance](../protect/compliance-policy-create-windows.md#configuration-manager-compliance) descreve esta definição.

Aplica-se a: Windows 10 e posterior

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile---2809324-----"></a>Personalizar o papel de parede em dispositivos iOS supervisionados usando um perfil de configuração de dispositivo<!-- 2809324   -->
Quando cria um perfil de configuração de dispositivos para dispositivos iOS, pode personalizar algumas funcionalidades **(configuração** do dispositivo > **Perfis** > **Criar perfil** > **iOS** para **funcionalidades** de plataforma > Dispositivo para o tipo de perfil). Esta atualização inclui novas definições de **Papel de Parede** que permitem a um Administrador utilizar uma imagem .png, .jpg ou .jpeg no ecrã principal ou ecrã de bloqueio. Essas configurações de papel de parede se aplicam somente a dispositivos supervisionados. 

Para obter uma lista destas definições, consulte as definições de funcionalidades do [dispositivo iOS](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available---3594661----"></a>O quiosque do Windows 10 está disponível para o público geral<!-- 3594661  -->
Nessa atualização, o recurso de quiosque no Windows 10 e em dispositivos posteriores está geralmente disponível (GA). Para ver todas as definições que pode adicionar e configurar, consulte as definições do [Quiosque para o Windows 10 (e mais tarde)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise---3598396-----"></a>O compartilhamento de contatos via Bluetooth é removido nas restrições de dispositivo > proprietário do dispositivo para Android Enterprise<!-- 3598396   -->
Ao criar um perfil de restrições de dispositivos para dispositivos Android Enterprise, existe uma partilha de contactos através da definição **Bluetooth.** Nesta atualização, a partilha de contactos através da definição **Bluetooth** é removida (**configuração** do dispositivo > **Perfis** > **Criar perfil** > **Android Enterprise** para plataforma > Restrições de **dispositivos > Proprietário** do dispositivo para o tipo de perfil > **Geral).**

A partilha de contactos através da definição **Bluetooth** não é suportada para a gestão do Android Enterprise Device Owner. Assim, quando essa configuração é removida, ela não afetará nenhum dispositivo ou locatários, mesmo que essa configuração esteja habilitada e configurada em seu ambiente.

Para ver a lista atual de configurações, vá às definições do [dispositivo Android Enterprise para permitir ou restringir funcionalidades](../configuration/device-restrictions-android-for-work.md).

Aplica-se a: proprietário do dispositivo Android Enterprise


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="more-detailed-enrollment-restriction-failure-messaging---3111564---"></a>Mensagens de falha de restrição de registro mais detalhadas<!-- 3111564 -->
Mensagens de erro mais detalhadas estão disponíveis quando as restrições de registro não são atendidas. Para ver estas mensagens, aceda à **Intune** > **resolução de problemas** > e consulte a tabela de falhas de inscrição. Para mais informações, consulte a lista de falhas de [inscrição.](help-desk-operators.md#enrollment-failure-reference)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestão de Dispositivos
#### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices---1574342----"></a>Visualização do suporte para dispositivos Android de propriedade corporativa e totalmente gerenciado<!-- 1574342  -->
O Intune agora dá suporte a dispositivos Android totalmente gerenciados, um cenário de "proprietário do dispositivo" de propriedade da empresa, em que os dispositivos são totalmente gerenciados por ele e são afiliados a usuários individuais. Isso permite que os administradores gerenciem todo o dispositivo, imponham um intervalo estendido de controles de política indisponíveis para perfis de trabalho e restringe os usuários a instalarem aplicativos somente de Google Play gerenciados. Para mais informações, consulte [Configurar a inscrição intune de dispositivos totalmente geridos](../enrollment/android-fully-managed-enroll.md) pelo Android e [inscrever os seus dispositivos dedicados ou dispositivos totalmente geridos](../enrollment/android-dedicated-devices-fully-managed-enroll.md).  Observe que esse recurso está em versão prévia. Alguns recursos do Intune, como certificados, conformidade e acesso condicional, não estão disponíveis no momento com dispositivos de usuário totalmente gerenciados do Android.

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices---1434452---"></a>Suporte de apagamento seletivo para WIP sem dispositivos de registro<!-- 1434452 -->
A proteção de informações do Windows sem registro (WIP-WE) permite que os clientes protejam seus dados corporativos em dispositivos Windows 10 sem a necessidade de registro completo de MDM. Depois que os documentos são protegidos com uma política WIP-nós, os dados protegidos podem ser apagados seletivamente por um administrador do Intune. Ao selecionar o usuário e o dispositivo e enviar uma solicitação de apagamento, todos os dados que foram protegidos por meio da política WIP-WE se tornarão inutilizáveis. No Intune, no portal do Azure, selecione **Aplicação móvel** > **Eliminação seletiva da aplicação**.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="tenant-status-dashboard---1124854---"></a>Painel de status do locatário<!-- 1124854 -->
A [página novo status do locatário](tenant-status.md) fornece um único local onde você pode exibir o status e os detalhes relacionados para seu locatário.  O painel é dividido em quatro áreas:
- **Detalhes do Inquilino** - Exibe informações que incluem o nome e localização do seu Inquilino, a sua Autoridade de MDM, o total de dispositivos matriculados no seu inquilino, e a sua licença conta. Esta seção também lista a versão de serviço atual para seu locatário.
- **Estado do Conector** - Exibe informações sobre conectores disponíveis configurados e também pode listar aqueles que ainda não ativou.  
   Com base no estado atual de cada conector, eles são sinalizados como íntegros, de aviso ou não íntegros. Selecione um conector para detalhar e exibir detalhes ou configurar informações adicionais para ele.
- **Intune Service Health** - Exibe detalhes sobre incidentes ativos ou interrupções para o seu inquilino. As informações nesta seção são recuperadas diretamente do centro de mensagens do Office.
- **Notícias Intune** - Exibe mensagens ativas para o seu inquilino. As mensagens incluem itens como notificações quando seu locatário recebe os recursos mais recentes do Intune.  As informações nesta seção são recuperadas diretamente do centro de mensagens do Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10---1488939--"></a>Nova experiência de ajuda e suporte no Portal da Empresa para Windows 10<!-- 1488939-->
O novo Portal da Empresa ajuda & página de suporte ajuda os usuários a solucionar problemas e solicitar ajuda para problemas de aplicativo e acesso. Na nova página, eles podem enviar detalhes de erro de email e log de diagnóstico e encontrar os detalhes da assistência técnica de sua organização. Eles também encontrarão uma seção de perguntas frequentes com links para a documentação relevante do Intune.

#### <a name="new-help-and-support-experience-for-intune---3307080---"></a>Nova experiência de ajuda e suporte para o Intune<!-- #3307080 -->
Estamos distribuindo a nova experiência de ajuda e suporte para todos os locatários nos próximos dias. Esta nova experiência está disponível para Intune e pode ser acedida quando utilizar as lâminas Intune no [portal Azure](https://portal.azure.com/).
A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Essas soluções são oferecidas por meio de um algoritmo de aprendizado de máquina baseado em regra, orientado pelas consultas do usuário. Além das diretrizes específicas do problema, você usa o novo fluxo de trabalho de criação de caso para abrir um caso de suporte por email ou telefone. Essa nova experiência substitui a ajuda anterior e a experiência de suporte de um conjunto estático de opções pré-selecionadas que se baseiam na área do console em que você está ao abrir a ajuda e o suporte.
Para mais informações, consulte [Como obter suporte para o Microsoft Intune](get-support.md).

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services---3762211----"></a>Novos logs operacionais e capacidade de enviar logs para serviços de Azure Monitor<!-- 3762211  -->
O Intune tem log de auditoria interno que rastreia eventos conforme são feitas alterações. Essa atualização inclui novos recursos de log, incluindo: 
- Logs operacionais (versão prévia) que mostram detalhes sobre usuários e dispositivos registrados, incluindo êxito e tentativas com falha.
- Os logs de auditoria e os logs operacionais podem ser enviados para Azure Monitor, incluindo contas de armazenamento, hubs de eventos e log Analytics. Esses serviços permitem que você armazene, use análises como Splunk e QRadar e obtenha visualizações de seus dados de registro em log.

[Enviar dados de registo para armazenamento, centros de eventos ou análises](../review-logs-using-azure-monitor.md) de registo em Intune fornece mais informações sobre esta funcionalidade.

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device---2687509----"></a>Ignorar mais telas do assistente de configuração em um dispositivo de DEP do iOS<!-- 2687509  -->
Além das telas que você pode ignorar no momento, você pode definir dispositivos do iOS DEP para ignorar as seguintes telas no assistente de configuração quando um usuário registra o dispositivo: Tom de exibição, privacidade, migração do Android, botão página inicial, iMessage & FaceTime, integração, inspeção Migração, aparência, hora da tela, atualização de software, instalação do SIM.
Para escolher que telas para ignorar, aceda a **inscrição de dispositivos** > **inscrição da Apple** > **tokens do programa de inscrição** > Escolha um token > **Perfis** > Escolha um perfil > **propriedades** > **personalização do Assistente de configuração** > Escolha **ocultar**  para qualquer telas que pretende ignorar > **OK**.
Se você criar um novo perfil ou editar um perfil, as telas ignorar selecionadas precisarão ser sincronizadas com o servidor MDM da Apple. Os usuários podem emitir uma sincronização manual dos dispositivos para que não haja atraso na separação das alterações de perfil.

#### <a name="android-enterprise-app-we-app-deployment---1171203---"></a>APLICATIVO Android Enterprise – implantação de aplicativo<!-- 1171203 -->
Para dispositivos Android em uma política de proteção de aplicativo não registrada sem registro (APP-WE), agora você pode usar o Google Play gerenciado para implantar aplicativos de armazenamento e aplicativos LOB para os usuários. Especificamente, você pode fornecer aos usuários finais um catálogo de aplicativos e uma experiência de instalação que não exige mais que os usuários finais afrouxem a postura de segurança de seus dispositivos, permitindo instalações de fontes desconhecidas. Além disso, neste cenário de implementação irá fornecer uma experiência de usuário aprimorada do fim.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-apps---1081941---"></a>Marcas de escopo para aplicativos<!-- 1081941 -->
Você pode criar marcas de escopo para limitar o acesso a funções e aplicativos. Você pode adicionar uma marca de escopo a um aplicativo para que somente as pessoas com funções também atribuídas a essa marca de escopo tenham acesso ao aplicativo. Atualmente, os aplicativos adicionados ao Intune a partir de Google Play gerenciados ou aplicativos adquiridos usando Apple Volume Purchase Program (VPP) não podem ser atribuídos a marcas de escopo (o suporte futuro é planejado). Para mais informações, consulte [Utilize etiquetas de mira para filtrar as políticas](scope-tags.md).




<!-- ########################## -->
## <a name="december-2018"></a>dezembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="updates-for-application-transport-security---748318---"></a>Atualizações para segurança de transporte de aplicativo<!-- 748318 -->

O Microsoft Intune dá suporte ao protocolo TLS 1.2 + para fornecer a melhor criptografia de classe, para garantir que o Intune seja mais seguro por padrão e se alinhe com outros serviços da Microsoft, como o Microsoft Office 365. Para atender a esse requisito, os portais da empresa para iOS e macOS impedirão os requisitos de ATS (segurança de transporte de aplicativos) atualizados da Apple, que também exigem o TLS 1.2 +. A ATS é utilizada para impor medidas de segurança mais rigorosas em todas as comunicações feitas por aplicações através de HTTPS. Essa alteração afeta os clientes do Intune usando os aplicativos iOS e macOS Portal da Empresa. Para mais informações, consulte o blog de [suporte Intune.](https://aka.ms/compportalats)

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys---1832174---"></a>O SDK de aplicativos do Intune dará suporte a chaves de criptografia de 256 bits<!-- 1832174 -->
O SDK de aplicativo do Intune para Android agora usa chaves de criptografia de 256 bits quando a criptografia é habilitada pelas políticas de proteção de aplicativo. O SDK irá continuar a fornecer suporte de chaves de 128 bits para compatibilidade com o conteúdo e aplicações que utilizam versões mais antigas do SDK.

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices---3503442---"></a>Microsoft Auto Update versão 4.5.0 necessário para dispositivos macOS<!-- 3503442 -->
Para continuar recebendo atualizações para o Portal da Empresa e outros aplicativos do Office, os dispositivos macOS gerenciados pelo Intune devem ser atualizados para a atualização automática da Microsoft 4.5.0. Os usuários já podem ter essa versão para seus aplicativos do Office.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="intune-requires-macos-1012-or-later---2827778---"></a>O Intune requer macOS 10,12 ou posterior<!-- 2827778 -->
Agora, o Intune requer o macOS versão 10,12 ou posterior. Os dispositivos que usam versões anteriores do macOS não podem usar o Portal da Empresa para se registrar no Intune. Para receber assistência de suporte e novos recursos, os usuários devem atualizar seus dispositivos para macOS 10,12 ou posterior e atualizar o Portal da Empresa para a versão mais recente.

<!-- ########################## -->
## <a name="november-2018"></a>novembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices---1281677---"></a>Desinstalando aplicativos em dispositivos iOS supervisionados de propriedade corporativa<!-- 1281677 -->
Você pode remover qualquer aplicativo em dispositivos iOS supervisionados de propriedade corporativa. Pode remover qualquer aplicação ao visar os grupos de utilizadores ou dispositivos com um tipo de atribuição **Desinstalar**. Para dispositivos iOS pessoais ou não supervisionados, continuará a poder remover apenas as aplicações que foram instaladas com o Intune.

#### <a name="downloading-intune-win32-app-content---2617320---"></a>Baixando o conteúdo do aplicativo Win32 do Intune<!-- 2617320 -->
Os clientes do Windows 10 RS3 e posteriores baixarão o conteúdo do aplicativo Win32 do Intune usando um componente de otimização de entrega no cliente do Windows 10. A otimização de entrega fornece a funcionalidade ponto a ponto que está ativada por padrão. Atualmente, a otimização de entrega pode ser configurada pela diretiva de grupo. Para obter mais informações, consulte [otimização de entrega para Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Menu de conteúdo do dispositivo e aplicativo do usuário final<!-- 2771453 -->
Os usuários finais agora podem usar o menu de contexto em dispositivos e aplicativos para disparar ações comuns, como renomear um dispositivo ou verificar a conformidade.

#### <a name="set-custom-background-in-managed-home-screen-app----3041945---"></a>Definir plano de fundo personalizado no aplicativo de tela inicial gerenciado <!-- 3041945 -->
Estamos adicionando uma configuração que permite que você personalize a aparência em segundo plano do aplicativo de tela inicial gerenciado no Android Enterprise, vários aplicativos, dispositivos de modo de quiosque.  Para configurar o **Fundo do URL personalizado**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.
Para ver as definições do quiosque, consulte [as restrições](../configuration/device-restrictions-android-for-work.md)do dispositivo Android Enterprise .

#### <a name="app-protection-policy-assignment-save-and-apply---3104570---"></a>Salvar e aplicar atribuição de política de proteção de aplicativo<!-- 3104570 -->
Agora tem um melhor controlo sobre as atribuições de políticas de proteção de [aplicações.](../apps/app-protection-policies.md) Quando selecionar *Atribuições* para definir ou editar as atribuições de uma apólice, tem de **guardar** a sua configuração antes da alteração se aplicar. Use **O Discard** para limpar todas as alterações que fizer sem guardar quaisquer alterações nas listas incluir ou excluir.  Ao exigir salvar ou descartar, somente os usuários aos quais você pretende receberão uma política de proteção de aplicativo.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later---3174639---"></a>Novas configurações do navegador Microsoft Edge para Windows 10 e posterior<!-- 3174639 -->
Essa atualização inclui novas configurações para ajudar a controlar e gerenciar o navegador Microsoft Edge em seus dispositivos. Para obter uma lista destas definições, consulte [a restrição do Dispositivo para o Windows 10 (e mais recente)](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies---3330037---"></a>Suporte a novos aplicativos com políticas de proteção de aplicativo<!-- 3330037 -->
Agora você pode gerenciar os seguintes aplicativos com [as políticas de proteção de aplicativo do Intune](../apps/app-protection-policies.md):
- Fluxo (iOS)
- Para fazer (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Use as políticas de proteção de aplicativo para proteger dados corporativos e controlar a transferência de dados para esses aplicativos, como outros aplicativos gerenciados pela política do Intune. Observação: se o fluxo ainda não estiver visível no console, você adicionará o Flow ao criar ou editar as políticas de proteção do aplicativo. Para isso, utilize a opção **+ Mais aplicações** e, em seguida, especifique o ID da *Aplicação* para o Fluxo no campo de entrada. Para Android use *com.microsoft.flow*, e para iOS use *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles--2155106---"></a>Suporte para OAuth do iOS 12 em perfis de email do iOS<!--2155106 -->
Os perfis de e-mail iOS do Intune suportam o Open Authorization (OAuth) do iOS 12. Para ver esta funcionalidade, crie um novo perfil (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **iOS** para a plataforma > **E-mail** para o tipo de perfil) ou atualize um perfil de e-mail iOS existente. Se ativar o OAuth num perfil que já foi implementado para utilizadores, será pedido aos utilizadores que autentiquem e transfiram novamente o respetivo e-mail.

Pode obter mais informações sobre como utilizar o OAuth num perfil de e-mail em [iOS email profiles](../configuration/email-settings-ios.md) (Perfis de e-mail iOS).

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios---3259404---"></a>Suporte ao controle de acesso à rede (NAC) para Citrix SSO para iOS<!-- 3259404 -->
A Citrix lançou uma atualização para o gateway Citrix para permitir o NAC (controle de acesso à rede) para o Citrix SSO para iOS no Intune. Você pode optar por incluir uma ID de dispositivo em um perfil VPN no Intune e, em seguida, enviar esse perfil por push para seus dispositivos iOS. Você precisará instalar a atualização mais recente para o gateway Citrix para usar essa funcionalidade.

[Configurar as definições de VPN nos dispositivos iOS](../configuration/vpn-settings-ios.md#base-vpn-settings) fornece mais informações sobre a utilização do NAC, incluindo alguns requisitos adicionais. 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown---1892471---"></a>os números de versão do iOS e do macOS e os números de Build são mostrados<!-- 1892471 -->
Em **Conformidade do dispositivo** > **Conformidade do dispositivo**, são apresentadas as versões dos sistemas operativos iOS e macOS. Estas versões estão disponíveis para serem utilizadas nas políticas de conformidade. Essa atualização inclui o número da compilação, que é configurável para ambas as plataformas.
Quando as atualizações de segurança são lançadas, normalmente, a Apple não altera o número da versão, mas atualiza o número de compilação. Ao utilizar o número de compilação numa política de conformidade, pode verificar facilmente se foi instalada uma atualização da vulnerabilidade.
Para utilizar esta funcionalidade, consulte as políticas de conformidade [iOS](../protect/compliance-policy-create-ios.md#device-health) e [macOS.](../protect/compliance-policy-create-mac-os.md#device-properties)

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later---2753807---"></a>Os anéis de atualização estão sendo substituídos pelas configurações de otimização de entrega para Windows 10 e posterior<!-- 2753807 -->
A otimização de entrega é um novo perfil de configuração para Windows 10 e posterior. Esse recurso fornece uma experiência mais simplificada para fornecer atualizações de software aos dispositivos em sua organização. Essa atualização também ajuda a fornecer as configurações em anéis de atualização novos e existentes usando um perfil de configuração.
Para configurar um perfil de configuração de otimização de entrega, consulte as definições de otimização de entrega do [Windows 10 (e mais recentes).](../configuration/delivery-optimization-windows.md)

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices---2827760---"></a>Novas configurações de restrição de dispositivo adicionadas a dispositivos iOS e macOS<!-- 2827760 -->
Essa atualização inclui novas configurações para seus dispositivos iOS e macOS que são lançadas com o iOS 12:

**Definições iOS:** 
- Geral: bloquear a remoção do aplicativo (somente supervisionado)
- Geral: bloquear o modo restrito por USB (somente supervisionado)
- Geral: forçar data e hora automáticas (somente supervisionado)
- Senha: bloquear o preenchimento automático de senha (apenas no modo supervisionado)
- Senha: bloquear solicitações de proximidade de senha (somente supervisionado)
- Senha: bloquear o compartilhamento de senha (somente supervisionado)

**definições de macOS:** 
- Senha: bloquear AutoPreenchimento de senha
- Senha: bloquear solicitações de proximidade de senha
- Senha: bloquear compartilhamento de senha

Para saber mais sobre estas definições, consulte as definições de restrição do [iOS](../configuration/device-restrictions-ios.md) e [do dispositivo macOS.](../configuration/device-restrictions-macos.md)

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview---1048100--"></a>Suporte ao piloto automático para dispositivos ingressados no Azure Active Directory híbrido (versão prévia)<!-- 1048100-->
Agora pode configurar dispositivos associados ao Azure Active Directory híbrido com o Autopilot. Os dispositivos têm de ser associados à rede da sua organização para utilizar a funcionalidade Autopilot híbrida. Para obter mais informações, veja [Implementar dispositivos associados ao Azure Active Directory híbrido com o Intune e o Windows Autopilot](../enrollment/windows-autopilot-hybrid.md).
Esta funcionalidade será implementada na base de utilizadores nos próximos dias. Assim, poderá não conseguir seguir estes passos até que a mesma seja implementada na sua conta.

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selecionar aplicativos acompanhados na página de status de registro<!-- 2531007 -->
Você pode escolher quais aplicativos são acompanhados na página status do registro. Até que esses aplicativos sejam instalados, o usuário não poderá usar o dispositivo. Para obter mais informações, consulte [Configurar uma página de status de registro](../enrollment/windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number--2595788---"></a>Pesquisar por um dispositivo AutoPilot por número de série<!--2595788 -->
Agora você pode pesquisar por um número de série de dispositivos AutoPilot. Para tal, escolha a **inscrição do Dispositivo** > **inscrição do Windows** > **Dispositivos** > escreva um número de série na caixa de **números de série** > prima Enter.

#### <a name="track-installation-of-office-proplus--2620217---"></a>Acompanhar a instalação do Office ProPlus<!--2620217 -->
Os utilizadores podem acompanhar o progresso da instalação do [Office ProPlus](../apps/apps-add-office365.md) utilizando a Página de Estado de [Inscrição](../enrollment/windows-enrollment-status.md). Para obter mais informações, consulte [Configurar uma página de status de registro](../enrollment/windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low---2237572---"></a>Alertas para expiração do token VPP ou licença de Portal da Empresa em execução baixa<!-- 2237572 -->
Se você estiver usando o VPP (programa de compra de volume) para pré-configurar o Portal da Empresa durante o registro de DEP, o Intune o alertará quando o token de VPP estiver prestes a expirar e quando as licenças do Portal da Empresa estiverem em execução baixa.

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts--3006133---"></a>suporte ao macOS Programa de registro de dispositivos para contas do Apple School Manager<!--3006133 -->
O Intune agora dá suporte ao uso do Programa de registro de dispositivos em dispositivos macOS para contas do Apple School Manager.  Para mais informações, consulte [Automaticamente inscrever dispositivos macOS com](../enrollment/device-enrollment-program-enroll-macos.md)o Apple School Manager ou o Programa de Inscrição de Dispositivos .

#### <a name="new-intune-device-subscription-sku--3312071--"></a>Novo SKU de assinatura de dispositivo do Intune<!--3312071-->
Para ajudar a reduzir o custo associado à gestão de dispositivos nas empresas, está agora disponível um novo SKU de subscrição baseado em dispositivos. Este SKU de dispositivos do Intune possui uma licença mensal por dispositivo. Os preços variam em função do programa de licenciamento. Está disponível diretamente através do centro de administração da Microsoft 365, e através do [Acordo de Empresa](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), Microsoft Products and Services [Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA), Microsoft [Open Agreements](https://partner.microsoft.com/licensing/licensing-agreements)e [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes---3041935---"></a>Pausar temporariamente o modo de quiosque em dispositivos Android para fazer alterações<!-- 3041935 -->
Ao utilizar dispositivos Android no modo de quiosque de múltiplas aplicações, um administrador de TI poderá ter de fazer alterações ao dispositivo. Essa atualização inclui novas configurações de quiosque de vários aplicativos que permitem que um administrador de ti Pause temporariamente o modo de quiosque usando um PIN e obtenha acesso a todo o dispositivo.
Para ver as definições do quiosque, consulte [as restrições](../configuration/device-restrictions-android-for-work.md)do dispositivo Android Enterprise .

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices----3042021---"></a>Habilitar o botão Home virtual em dispositivos Android Enterprise quiosque <!-- 3042021 -->
Uma nova definição permitirá que os utilizadores toquem num botão de tecla de função no respetivo dispositivo para alternar entre a aplicação Ecrã Inicial Gerido e outras aplicações atribuídas no respetivo dispositivo de quiosque de múltiplas aplicações. Esta definição é particularmente útil em cenários onde a aplicação de quiosque do utilizador não responde adequadamente ao botão "retroceder". Poderá configurar esta definição para dispositivos Android de utilização única, pertencentes à empresa. Para ativar ou desativar o **botão Home virtual**, aceda ao Intune no portal do Azure > Configuração do dispositivo. Selecione um perfil de configuração de dispositivo atual ou crie um novo para editar as respetivas definições de quiosque.
Para ver as definições do quiosque, consulte [as restrições](../configuration/device-restrictions-android-for-work.md)do dispositivo Android Enterprise .




<!-- ########################## -->
## <a name="october-2018"></a>Outubro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="access-to-key-profile-properties-using-the-company-portal-app---772203---"></a>Acesso às propriedades do perfil de chave usando o aplicativo do portal da empresa<!-- 772203 -->
Os utilizadores finais podem agora aceder a ações e propriedades de conta fundamentais, tais como a reposição de palavra-passe, a partir da aplicação Portal da Empresa. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios---1248481---"></a>os teclados de terceiros podem ser bloqueados pelas configurações do aplicativo no iOS<!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune podem bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, estão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices---1248496---"></a>Acesso de conta de usuário de aplicativos do Intune em dispositivos Android e iOS gerenciados<!-- 1248496 -->
Enquanto administrador do Microsoft Intune, pode controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Pode limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. 

#### <a name="outlook-ios-and-android-app-configuration-policy--1828527---"></a>Política de configuração de aplicativo Android e iOS do Outlook<!--1828527 -->
Agora pode criar uma política de configuração da aplicação Outlook para iOS e Android para os utilizadores no local que tiram partido da autenticação Básica com o protocolo ActiveSync. Serão adicionadas outras definições de configuração à medida que forem ativadas para o Outlook para iOS e Android.

#### <a name="office-365-pro-plus-language-packs---1833450---"></a>Pacotes de idiomas do Office 365 Pro Plus<!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

#### <a name="windows-line-of-business-lob-apps-file-extensions---1884873---"></a>Extensões de arquivo de aplicativos LOB (linha de negócios) do Windows<!-- 1884873 -->
As extensões de ficheiros para aplicações do Windows LOB passarão a incluir *.msi*, *.appx,* *.appxbundle*, *.msix*, e *.msixbundle*. Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações do cliente** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** é apresentado, o qual lhe permite selecionar o **Tipo de aplicação**. Para aplicações LOB do Windows, selecione o tipo de aplicação **Linha de negócio**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação com a extensão adequada.

#### <a name="windows-10-app-deployment-using-intune---2309001---"></a>Implantação de aplicativo do Windows 10 usando o Intune<!-- 2309001 -->
Com base no suporte existente para aplicações de linha de negócio (LOB) e aplicações da Microsoft Store para Empresas, os administradores podem utilizar o Intune para implementar a maioria das aplicações existentes da respetiva organização nos utilizadores finais em dispositivos com o Windows 10. Os administradores podem adicionar, instalar e desinstalar aplicações para utilizadores do Windows 10 numa variedade de formatos, como MSIs, Setup.exe ou MSP. O Intune irá avaliar as regras de requisitos antes de transferir e instalar, e irá notificar os utilizadores finais sobre o estado ou os requisitos de reinício através do Centro de Ação do Windows 10. Esta funcionalidade irá efetivamente ajudar as organizações interessadas em mudar esta carga de trabalho para o Intune e a cloud. Esta funcionalidade está atualmente em pré-visualização pública e esperamos acrescentar-lhe novas funcionalidades relevantes durante os próximos meses. 

#### <a name="app-protection-policy-app-settings-for-web-data---2662995---"></a>Configurações de política de proteção de aplicativo (aplicativo) para dados da Web<!-- 2662995 -->
As definições da política APP para conteúdos da Web em dispositivos Android e iOS serão atualizadas para processar melhor ligações Web HTTP e HTTPS, bem como a transferência de dados através de Ligações Universais do iOS e Ligações de Aplicações do Android. 

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Menu de conteúdo do dispositivo e aplicativo do usuário final<!-- 2771453 -->
Os utilizadores finais podem agora utilizar o menu de contexto em aplicações e dispositivos para acionar ações comuns, tais como mudar o nome de um dispositivo ou realizar verificações de conformidade. 

#### <a name="windows-company-portal-keyboard-shortcuts---2771518---"></a>Atalhos de teclado do Portal da Empresa do Windows<!-- 2771518 -->
Os utilizadores finais poderão agora ativar ações de aplicação e de dispositivo no Portal da Empresa do Windows com atalhos de teclado (aceleradores).

#### <a name="require-non-biometric-pin-after-a-specified-timeout---1506985---"></a>Exigir PIN não biométrico após um tempo limite especificado<!-- 1506985 -->
Ao exigir um PIN não biométrico após um tempo limite especificado pelo administrador, o Intune fornece segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições afetam os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições permitem que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, ao eliminar os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações do cliente** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas. Para obter informações sobre as definições de acesso, veja as [definições do iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) e as [definições do Android](../apps/app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices---2244713---"></a>Configurações de transferência de dados de aplicativo do Intune em dispositivos iOS MDM registrados<!-- 2244713 -->
Pode separar o controlo das definições de transferência de dados de aplicações do Intune em dispositivos iOS inscritos na MDM da especificação da identidade do utilizador inscrito, também conhecida como Nome Principal de Utilizador (UPN). Os administradores que não utilizarem o IntuneMAMUPN não notarão a existência de uma alteração de comportamento. Quando esta funcionalidade estiver disponível, os administradores que utilizam o IntuneMAMUPN para controlar o comportamento de transferência de dados em dispositivos inscritos devem rever as novas definições e atualizar as respetivas definições das aplicações conforme necessário.

#### <a name="windows-10-win32-apps---2617325---"></a>Aplicativos do Windows 10 Win32<!-- 2617325 -->
Pode configurar as suas aplicações Win32 para que sejam instaladas no contexto de utilizador para utilizadores individuais ou para todos os utilizadores do dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts---2617330---"></a>Aplicativos do Windows Win32 e scripts do PowerShell<!-- 2617330 -->
Os utilizadores finais já não necessitam de ter sessão iniciada no dispositivo para instalarem aplicações Win32 ou executarem scripts do PowerShell. 

#### <a name="troubleshooting-client-app-installation---1363711---"></a>Solucionando problemas de instalação do aplicativo cliente<!-- 1363711 -->
Pode resolver problemas relativos ao sucesso da instalação de aplicações cliente ao rever a coluna intitulada **Instalação da aplicação** e o painel **Resolução de Problemas**. Para ver o painel **Resolução de Problemas**, selecione **Resolução de Problemas** em **Ajuda e suporte**, no portal do Intune.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Criar sufixos DNS em perfis de configuração de VPN em dispositivos que executam o Windows 10<!-- 1333668 -->
Quando criar um perfil de configuração de um dispositivo VPN (**Configuração do dispositivo** > **Perfis** > **Criar perfil** >  plataforma **Windows 10 e versões posteriores** > tipo de perfil **VPN**), terá de introduzir algumas definições de DNS. Com esta atualização, também pode introduzir múltiplos **sufixos DNS** no Intune. Quando utilizar sufixos DNS, pode procurar um recurso de rede através do respetivo nome abreviado, em vez do nome de domínio completamente qualificado (FQDN). Esta atualização também permite alterar a ordem dos sufixos DNS no Intune.
O artigo [Definições de VPN do Windows 10](../configuration/vpn-settings-windows-10.md#dns-settings) indica as definições de DNS atuais.
Aplica-se a: dispositivos com o Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles---1333705---"></a>Suporte para VPN Always on para perfis de trabalho do Android Enterprise<!-- 1333705 -->
Nesta atualização, pode utilizar ligações VPN Sempre Ativada em dispositivos Android Enterprise com perfis de trabalho geridos. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
Pode ativar a VPN Sempre Ativada nas definições **Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Android Enterprise** para a plataforma > **Restrições do dispositivo** > **Conectividade**.

#### <a name="issue-scep-certificates-to-user-less-devices---1744554---"></a>Emitir certificados SCEP para dispositivos sem usuário<!-- 1744554 -->
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
> - `{{FullyQualifiedDomainName}}` só funciona em dispositivos com Windows e dispositivos associados a um domínio. 
> - Quando especificar as propriedades do dispositivo, tais como o IMEI, o Número de Série e o Nome de Domínio Completamente Qualificado, no requerente ou no SAN de um certificado de dispositivo, tenha em atenção que estas propriedades podem ser falsificadas por uma pessoa que tenha acesso ao dispositivo. 

O artigo [Criar um perfil de certificado SCEP](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile) indica as variáveis atuais durante a criação de um perfil de configuração SCEP. 

Aplica-se a: Windows 10 e versões posteriores e ao iOS, com suporte para Wi-Fi

#### <a name="remotely-lock-uncompliant-devices---2064495---"></a>Bloquear dispositivos sem conformidade remotamente<!-- 2064495 -->
Quando um dispositivo não estiver em conformidade, poderá criar uma ação na política de conformidade que bloqueie remotamente o dispositivo. No Intune > **Conformidade do dispositivo**, crie uma nova política ou selecione uma política existente > **Propriedades**. Selecione **Ações para não conformidade** > **Adicionar** e selecione a opção para bloquear remotamente o dispositivo.
Suportado em: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e posterior 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal---2748224---"></a>Aprimoramentos no perfil de quiosque do Windows 10 e posterior no portal do Azure<!-- 2748224 -->
Esta atualização inclui as seguintes melhorias no perfil de configuração de dispositivos de Quiosque do Windows 10 (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Pré-visualização de quiosque** para o tipo de perfil): 
- Atualmente, pode criar múltiplos perfis de quiosque no mesmo dispositivo. Com esta atualização, o Intune suportará apenas um perfil de quiosque por dispositivo. Se continuar a necessitar de múltiplos perfis de quiosque num só dispositivo, pode utilizar um URL personalizado.
- Num perfil **Quiosque de várias aplicações**, pode selecionar o tamanho e a ordem dos mosaicos das aplicações para o **Esquema do menu Iniciar** na grelha das aplicações. Se preferir um nível superior de personalização, pode avançar para carregar um ficheiro XML.
- As definições do Browser de Quiosque estão a passar para as definições de **Quiosque**. Neste momento, as definições do **browser de Quiosque** têm a sua própria categoria no portal do Azure.
Aplica-se a: Windows 10 e posterior

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device----2637704----"></a>Solicitação de PIN quando você altera as impressões digitais ou a ID de face em um dispositivo iOS <!-- 2637704  -->
Agora é pedido um PIN aos utilizadores após fazerem alterações biométricas no respetivo dispositivo iOS. Isto inclui alterações ao nível de impressões digitais ou do Face ID registados. A altura em que o pedido é apresentado depende da configuração do tempo limite *Verificar novamente os requisitos de acesso após (minutos)* .  Quando não está definido nenhum PIN, é pedido ao utilizador para configurar um. 
 
Esta funcionalidade só está disponível para iOS e requer a participação de aplicações que integrem o SDK da aplicação Intune para iOS, versão 9.0.1 ou posterior. Precisa da integração do SDK para que o comportamento possa ser imposto nas aplicações de destino. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. Algumas aplicações participantes incluem: WXP, Outlook, Managed Browser e Yammer.

#### <a name="network-access-control-support-on-ios-vpn-clients---1333693---"></a>Suporte ao controle de acesso à rede em clientes VPN iOS<!-- 1333693 -->
Com esta atualização, há uma nova definição para ativar o Controlo de Acesso à Rede (NAC) quando criar um perfil de configuração de VPN para Cisco AnyConnect, F5 Access e Citrix SSO para iOS. Esta definição permite que o ID do NAC do dispositivo seja incluído no perfil de VPN. Atualmente, não existem clientes VPN nem soluções de parceiro de NAC que suportem este novo ID do NAC, mas iremos mantê-lo informado através da nossa [mensagem de blogue de suporte](ttps://aka.ms/iOS12_and_vpn) quando existirem.

Para utilizar o NAC, precisará de:
1. Optar ativamente por permitir que o Intune inclua IDs de dispositivos em perfis de VPN
2. Atualizar o software/firmware do seu fornecedor de NAC através da orientação fornecida diretamente pelo seu fornecedor de NAC

Para obter informações sobre esta definição num perfil de VPN do iOS, veja [Adicionar definições de VPN em dispositivos iOS no Microsoft Intune](../configuration/vpn-settings-ios.md). Para obter mais informações sobre o controlo de acesso à rede, veja [Integração de controlo de acesso à rede (NAC) com o Intune](../protect/network-access-control-integrate.md). 

Aplica-se a: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile---1818139---"></a>Remover um perfil de email de um dispositivo, mesmo quando há apenas um perfil de email<!-- 1818139 -->
Anteriormente, não podia remover um perfil de e-mail de um dispositivo *se* fosse o único perfil de e-mail. Com esta atualização, este comportamento muda. Agora pode remover um perfil de e-mail, mesmo que seja o único perfil de e-mail no dispositivo. Para obter detalhes, veja [Adicionar definições de e-mail a dispositivos com o Intune](../configuration/email-settings-configure.md).

#### <a name="powershell-scripts-and-aad---2309469---"></a>Scripts do PowerShell e AAD<!-- 2309469 -->
Os scripts do PowerShell no Intune podem ser direcionados a grupos de segurança de dispositivo do AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nova configuração padrão "tipo de senha necessária" para Android, Android Enterprise<!-- 2649963 -->
Ao criar uma nova política de conformidade (**Intune** > **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android** ou **Android Enterprise** para a Plataforma > Segurança do Sistema), o valor predefinido para **Tipo de palavra-passe necessária** muda:

De: Predefinição do dispositivo; Para: Pelo menos, numérico

Aplicável ao: Android, Android Enterprise

Para ver estas definições, aceda a [Android](../protect/compliance-policy-create-android.md) e [Android Enterprise](../protect/compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile---2662938---"></a>Usar uma chave pré-compartilhada em um perfil de Wi-Fi do Windows 10<!-- 2662938 -->
Com esta atualização, poderá utilizar uma chave pré-partilhada (PSK) com o protocolo de segurança WPA/WPA2-Pessoal para autenticar um perfil de configuração de Wi-Fi para o Windows 10. Na atualização de outubro de 2018 para dispositivos com o Windows 10, também pode especificar a configuração de custos para uma rede com tráfego limitado.

Atualmente, tem de importar um perfil de Wi-Fi ou criar um perfil personalizado para utilizar uma chave pré-partilhada. O artigo [Definições de Wi-Fi para o Windows 10](../configuration/wi-fi-settings-windows.md) indica as definições atuais. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices---3218390---"></a>Remover Certificados PKCS e SCEP de seus dispositivos<!-- 3218390 -->
Em alguns cenários, houve certificados PKCS e SCEP que permaneceram em dispositivos, mesmo quando se procedeu à remoção de uma política de um grupo ou à eliminação de uma implementação de configuração ou de conformidade, ou quando um administrador atualizou um perfil SCEP ou PKCS existente. Esta atualização altera o comportamento. Há alguns cenários onde os certificados PKCS e SCEP são removidos de dispositivos e outros cenários em que estes certificados permanecem no dispositivo. Para obter informações sobre estes cenários, veja [Remover certificados SCEP e PKCS no Microsoft Intune](../protect/remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance---2504381---"></a>Usar o gatekeeper em dispositivos macOS para conformidade<!-- 2504381 -->
Esta atualização inclui o controlador de chamadas para macOS para avaliar dispositivos quanto à conformidade. Para definir o Controlador de Chamadas, tem de [Adicionar uma política de conformidade para dispositivos macOS](../protect/compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot---1558983---"></a>Aplicar o perfil do AutoPilot a dispositivos Win 10 registrados que ainda não estão registrado para o piloto automático<!-- 1558983 -->
Pode aplicar um perfil do Autopilot a dispositivos com o Windows 10 inscritos e que ainda não tenham sido registados no Autopilot. No perfil do Autopilot, selecione a opção **Converter todos os dispositivos visados para o Autopilot** para registar automaticamente dispositivos não Autopilot com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot aprovisioná-lo-á.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups---2526564---"></a>Criar e atribuir vários perfis de página de status de registro aos grupos do Azure AD<!-- 2526564 -->
Agora, pode [criar e atribuir](../enrollment/windows-enrollment-status.md) múltiplos perfis de Página de Estado de Inscrição a grupos do Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune--2748613--"></a>Migração de Programa de registro de dispositivos para o Apple Business Manager no Intune<!--2748613-->
O Apple Business Manager (ABM) funciona no Intune, pelo que pode atualizar versão do software da sua conta do Programa de Registo de Aparelho (DEP) para o ABM. No Intune, o processo é o mesmo. Para atualizar a versão do software da sua conta Apple do DEP para o ABM, aceda a [https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page--2748656--"></a>Guias de status de alerta e registro na página Visão geral do registro do dispositivo<!--2748656-->
Os alertas e os erros ao nível das inscrições aparecem agora em separadores diferentes da página Descrição geral de inscrições de dispositivos.

#### <a name="enrollment-abandonment-report---1382924---"></a>Relatório de abandono de registro<!-- 1382924 -->
Um novo relatório que fornece detalhes sobre inscrições abandonadas está disponível em **Inscrição de dispositivos** > **Monitorização**. Para obter mais informações, veja [Relatório de abandono do Portal da Empresa](../enrollment/enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature---2870393---"></a>Novo Azure Active Directory recurso de termos de uso<!-- 2870393 -->
O Azure Active Directory tem uma funcionalidade de termos de utilização que pode utilizar em vez dos termos e condições do Intune existentes. A funcionalidade de termos de utilização do Azure AD proporciona mais flexibilidade relativamente aos termos a apresentar e a quando o fazer, melhor suporte para a localização, mais controlo sobre a forma como os termos são compostos e relatórios melhorados. A funcionalidade de termos de utilização do Azure AD necessita do Azure Active Directory Premium P1, que também faz parte do conjunto Enterprise Mobility + Security E3. Para saber mais, veja o artigo [Gerir os termos e condições da sua empresa para o acesso dos utilizadores](../enrollment/terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support--3188762--"></a>Suporte ao modo do proprietário do dispositivo Android<!--3188762-->
Para o Knox Mobile Enrollment da Samsung, o Intune suporta agora inscrição de dispositivos para o modo de gestão Proprietário de Dispositivo Android. Os utilizadores em redes Wi-Fi ou redes móveis podem inscrever com apenas alguns toques os respetivos dispositivos quando os ligarem pela primeira vez. Para obter mais informações, consulte [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](../enrollment/android-samsung-knox-mobile-enroll.md) (Inscrever automaticamente dispositivos Android através do Knox Mobile Enrollment da Samsung).

### <a name="device-management"></a>Gestão de dispositivos
#### <a name="new-settings-for-software-updates-----1907869---"></a>Novas configurações para atualizações de software  <!-- 1907869 -->  
- Agora você pode configurar algumas notificações para alertar os usuários finais sobre reinicializações que são necessárias para concluir a instalação das atualizações de software mais recentes.   
- Agora você pode configurar um prompt de aviso de reinicialização para reinicializações que ocorrem fora do horário de trabalho, que dá suporte a cenários BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id---2075110---"></a>Agrupar dispositivos do Windows AutoPilot-registrados por ID do correlator<!-- 2075110 -->
O Intune suporta agora o agrupamento de dispositivos Windows por um ID de correlacionador se os mesmos forem inscritos com o [Autopilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), através do Configuration Manager. O ID de correlacionador é um parâmetro do ficheiro de configuração do Autopilot. O Intune irá definir automaticamente o [atributo enrollmentProfileName de dispositivos do Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) para que seja igual a "OfflineAutopilotprofile-<correlator ID>". Isto permite que sejam criados grupos dinâmicos do Azure AD arbitrários com base no ID de correlacionador, através do atributo enrollmentprofileName para inscrições do Autopilot offline. Para obter mais informações, veja [Windows Autopilot for existing devices](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices) (Windows Autopilot para dispositivos existentes).

#### <a name="intune-app-protection-policies---2984657---"></a>Políticas de proteção de aplicativo do Intune<!-- 2984657 -->
As políticas de proteção de aplicações do Intune permitem-lhe configurar várias definições de proteção de dados para aplicações protegidas pelo Intune, como o Microsoft Outlook e o Microsoft Word. Alterámos o aspeto e funcionalidade destas definições tanto para [iOS](../apps/app-protection-policy-settings-ios.md) como para [Android](../apps/app-protection-policy-settings-android.md), de modo a facilitar a localização de definições individuais. Existem três categorias de definições de política:
- **Reposicionamento de dados**: este grupo inclui os controlos de prevenção de perda de dados (DLP), como as restrições das operações de cortar, copiar, colar e guardar como. Estas definições determinam como os utilizadores interagem com os dados nas aplicações.
- **Requisitos de acesso**: este grupo contém as opções de PIN por aplicação que determinam como o utilizador final utiliza as aplicações num contexto de trabalho.  
- **Iniciação condicional**: este grupo guarda definições como as definições de SO mínimo, de deteção de dispositivos desbloqueados por jailbreak ou rooting e de períodos de tolerância offline.  
  
A funcionalidade das definições não muda, mas será mais fácil encontrá-las quando trabalhar no fluxo de autoria de política.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices---2451462----"></a>Restringe os aplicativos e bloqueie o acesso aos recursos da empresa em dispositivos Android<!-- 2451462  -->  
Em **Conformidade do dispositivo** > **Políticas** > **Criar política** > **Android** > **Segurança do Sistema**, há uma nova definição na secção *Segurança do Dispositivo* chamada **Aplicações restritas**. A definição **Aplicações restritas** utiliza uma política de conformidade para bloquear o acesso aos recursos da empresa, caso determinadas aplicações estejam instaladas no dispositivo. O dispositivo é considerado não compatíveis até que as aplicações restritas sejam removidas do dispositivo.
Aplica-se a: 
- Android

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps---1727158---"></a>O Intune dará suporte a um tamanho de pacote máximo de 8 GB para aplicativos LOB<!-- 1727158 -->
O Intune aumentou a dimensão máxima dos pacotes para 8 GB para as aplicações de linha de negócio (LOB). Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](../apps/apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app---1916266---"></a>Adicionar imagem de marca personalizada para o aplicativo Portal da Empresa<!-- 1916266 -->
Enquanto administrador do Microsoft Intune, pode carregar uma imagem de marca personalizada que será apresentada como uma imagem de fundo na página de perfil do utilizador, na aplicação Portal da Empresa para iOS. Para obter mais informações sobre como configurar a aplicação Portal da Empresa, veja [Como configurar a aplicação Portal da Empresa do Microsoft Intune](../apps/company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines---2971030---"></a>O Intune manterá o idioma traduzido do Office ao atualizar o Office em computadores dos usuários finais<!-- 2971030 -->
Quando o Intune instalar o Office nos computadores dos seus utilizadores finais, estes terão automaticamente os mesmos pacotes de idiomas de que dispunham com instalações anteriores do Office .MSI. Para obter mais informações, veja [Atribuir aplicações do Office 365 a dispositivos Windows 10 com o Microsoft Intune](../apps/apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal---3076965---"></a>Nova experiência de suporte do Intune no portal de gerenciamento de dispositivos Microsoft 365<!-- 3076965 -->
Estamos a implementar uma nova experiência de Ajuda e Suporte para o Intune no [portal de Gestão de Dispositivos do Microsoft 365]( https://devicemanagement.microsoft.com). A nova experiência permite-lhe descrever o seu problema pelas suas próprias palavras e receber informações de resolução de problemas e conteúdos de remediação baseados na Web. Estas soluções são disponibilizadas através de um algoritmo de aprendizagem automática baseado em regras, alimentado pelas perguntas dos utilizadores.  

Para além das orientações específicas de problemas, pode utilizar o novo fluxo de trabalho de criação de processos para abrir um processo de suporte por e-mail ou telefone.  

Para os clientes que fazem parte da implementação, esta nova experiência substitui a experiência atual de Ajuda e Suporte de um conjunto estático de opções previamente selecionadas que se baseiam na área da consola que é apresentada ao abrir a Ajuda e Suporte.  

*Esta nova experiência de Ajuda e Suporte está a ser lançada para alguns, mas não para todos os inquilinos e está disponível no portal de Gestão de Dispositivos. Os participantes desta nova experiência são selecionados aleatoriamente entre os inquilinos intune disponíveis. Novos inquilinos serão adicionados à medida que expandirmos o lançamento.*  

Para mais informações, consulte [a experiência de Ajuda e Suporte](get-support.md#help-and-support-experience) em Como obter suporte para o Microsoft Intune.  

#### <a name="powershell-module-for-intune--preview-available---951068---"></a>Módulo do PowerShell para Intune – versão prévia disponível<!-- 951068 -->
Está agora disponível para pré-visualização no [GitHub](https://aka.ms/intunepowershell) um novo módulo do PowerShell que fornece suporte para a API do Intune através do Microsoft Graph. Para obter mais informações sobre como utilizar este módulo, veja o ficheiro LEIA-ME nessa localização.

<!-- ########################## -->
## <a name="september-2018"></a>Setembro de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="remove-duplication-of-app-protection-status-tiles---3083391---"></a>Remover a duplicação dos mosaicos de estado da proteção da aplicação<!-- 3083391 -->
Os mosaicos **Estado do utilizador para iOS** e **Estado do utilizador para Android** eram apresentados nas páginas **Aplicações do Cliente – Descrição Geral** e **Aplicações do Cliente – Estado de proteção de aplicação**. Os mosaicos de estado foram removidos da página **Aplicações do Cliente – Descrição Geral** para evitar a duplicação. 

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="support-for-more-third-party-certification-authorities-ca---3093107---"></a>Suporte para mais autoridades de certificação (AC) de terceiros<!-- 3093107 -->
Ao utilizar o protocolo SCEP (Simple Certificate Enrollment Protocol), agora pode emitir novos certificados e renovar certificados em dispositivos móveis com o Windows, iOS, Android e macOS.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-moves-to-support-ios-10-and-later---2454656---"></a>O Intune suporta agora o iOS 10 e posterior<!-- 2454656 -->  
A inscrição do Intune, o Portal da Empresa e o browser gerido agora suportam apenas dispositivos iOS com o iOS 10 e versões posteriores. Para verificar que dispositivos ou utilizadores são afetados na sua organização, aceda ao Intune no portal do Azure > **Dispositivos** > **Todos os dispositivos**. Filtre por SO e, em seguida, clique em **Colunas** para ver os detalhes da versão do SO. Peça a esses utilizadores para atualizarem os respetivos dispositivos para uma versão suportada do SO.  

Se tiver um dos dispositivos listados abaixo ou quiser inscrever um deles, tenha em atenção que só suportam o iOS 9 e versões anteriores.  Para continuar a aceder ao Portal da Empresa do Intune, tem de fazer a atualização para dispositivos que suportem o iOS 10 ou versões posteriores:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ª Geração) 
* iPad Mini (1ª Geração)  

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="microsoft-365-device-management-administration-center---3078424---"></a>Centro de administração da Gestão de Dispositivos do Microsoft 365<!-- 3078424 -->
Uma das promessas de Microsoft 365 é a administração simplificada e, ao longo dos anos, integramos os serviços de Microsoft 365 de back-end para fornecer cenários de ponta a ponta, como o Intune e o acesso condicional do Azure AD. O novo [Centro de administração do Microsoft 365](https://devicemanagement.microsoft.com) é o lugar certo para consolidar, simplificar e integrar a experiência de administração. A área de trabalho de especialista para a Gestão de Dispositivos fornece acesso fácil a todas as informações e tarefas de gestão de dispositivos e aplicações de que a sua organização precisa. Esperamos que esta se torne na principal área de trabalho da cloud das equipas de informática de utilizador final empresarial.


<!-- ########################## -->
## <a name="august-2018"></a>Agosto de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types---1520957---"></a>Suporte de túnel de pacotes para perfis VPN por aplicação iOS para tipos de ligações personalizadas e Pulse Secure<!-- 1520957 -->
Ao utilizar perfis VPN por aplicação iOS, pode optar por utilizar o túnel de camada de aplicação (proxy-de-aplicação) ou o túnel de nível do pacote (pacote-túnel). Estas opções estão disponíveis com os seguintes tipos de ligação:
- VPN Personalizada
- Pulse Secure, se não tiver a certeza sobre o valor a utilizar, consulte a documentação do seu fornecedor de VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device---1949583---"></a>Adiar quando as atualizações de software iOS são apresentadas no dispositivo<!-- 1949583 -->
Em Intune > **Atualizações de Software** > **Atualizar políticas para iOS**, pode configurar os dias e as horas em que não pretende que os dispositivos instalem as atualizações. Numa atualização futura, poderá atrasar a apresentação de uma atualização de software no dispositivo, entre 1 a 90 dias. 
[Configurar as políticas de atualização de iOS no Microsoft Intune](../protect/software-updates-ios.md) lista as definições atuais.

#### <a name="office-365-proplus-version---2213968---"></a>Office 365 versão ProPlus<!-- 2213968 -->
Ao atribuir as aplicações do Office 365 ProPlus a dispositivos com o Windows 10 com o Intune, poderá selecionar a versão do Office. No portal do Azure, selecione **Microsoft Intune** > **Aplicações** > **Adicionar Aplicações**. Em seguida, selecione **Conjunto de Aplicações Office 365 ProPlus (Windows 10)** na lista suspensa **Tipo**. Selecione **Definições do conjunto de aplicações** para apresentar o painel associado. Defina **Atualizar Canal** para um valor, como **Mensal**. Opcionalmente, remova a outra versão do Office (msi) dos dispositivos de utilizador final ao selecionar **Sim**. Selecione **Específico** para instalar uma versão específica do Office no canal selecionado em dispositivos de utilizador final. Agora, pode selecionar a **Versão específica** do Office a utilizar. As versões disponíveis serão alteradas ao longo do tempo. Por conseguinte, ao criar uma nova implementação, as versões disponíveis podem ser mais recentes e não ter determinadas versões mais antigas disponíveis. As implementações atuais continuarão a implementar a versão mais antiga, mas a lista de versões será constantemente atualizada por canal. Para obter mais informações, veja [Overview of update channels for Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) (Descrição geral dos canais de atualização do Office 365 ProPlus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn---2282852---"></a>Suporte para a definição do Registo de DNS para a VPN do Windows 10<!-- 2282852 -->
Com esta atualização, pode configurar perfis VPN do Windows 10 para registar dinamicamente os endereços IP atribuídos à interface de VPN com o DNS interno, sem a necessidade de utilizar perfis personalizados.
Para obter informações sobre as definições de perfis VPN atualmente disponíveis, veja [Windows 10 VPN settings](../configuration/vpn-settings-windows-10.md) (Definições de VPN do Windows 10).

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name--2652728--"></a>O instalador do Portal da Empresa para macOS inclui agora o número da versão no nome de ficheiro do instalador<!--2652728-->

#### <a name="ios-automatic-app-updates---2729759---"></a>Atualizações automáticas da aplicação do iOS<!-- 2729759 -->
As atualizações automáticas da aplicação funcionam em aplicações licenciadas para o dispositivo e o utilizador para o iOS Versão 11.0 e versões superiores.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="windows-hello-will-target-users-and-devices---1106609---"></a>O Windows Hello destina-se a utilizadores e dispositivos<!-- 1106609 -->
Quando cria uma política [Windows Hello para Empresas](../protect/windows-hello.md), esta aplica-se a todos os utilizadores numa organização (ao nível dos inquilinos). Com esta atualização, a política também pode ser aplicada a utilizadores ou dispositivos específicos através de uma política de configuração de dispositivos (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Identity Protection** > **Windows Hello para Empresas**).
No Intune no portal do Azure, a configuração e as definições do Windows Hello estão agora presentes tanto na **Inscrição de dispositivos** como na **Configuração do dispositivo**. A **Inscrição de dispositivos** destina-se a toda a organização (ao nível dos inquilinos) e suporta o Windows AutoPilot (OOBE). A **Configuração do dispositivo** destina-se a dispositivos e utilizadores através de uma política aplicada durante o registo.
Esta funcionalidade aplica-se a:  
- Windows 10 e posterior
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios---1769858---"></a>Zscaler é uma ligação disponível para perfis VPN no iOS<!-- 1769858 -->
Quando cria um perfil de configuração de dispositivo VPN de iOS (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **iOS** plataforma > **VPN** tipo de perfil), existem vários tipos de ligação, incluindo Cisco, Citrix e muito mais. Esta atualização adiciona o Zscaler como um tipo de ligação. 
A página [Definições de VPN para dispositivos com iOS](../configuration/vpn-settings-ios.md) lista os tipos de ligação disponíveis.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10---1879077---"></a>Modo FIPS para perfis de Wi-Fi de Empresas para o Windows 10<!-- 1879077 -->
Agora pode ativar o modo FIPS (Federal Information Processing Standards) para perfis de Wi-Fi de Empresas para o Windows 10 no Intune no portal do Azure. Certifique-se de que o modo FIPS está ativado na sua infraestrutura de Wi-Fi se o ativar nos seus perfis de Wi-Fi.
O artigo [Definições de Wi-Fi para dispositivos com o Windows 10 ou posterior no Intune](../configuration/wi-fi-settings-windows.md) mostra-lhe como pode criar um perfil de Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview---1958649---"></a>Controlar o modo S nos dispositivos Windows 10 e posteriores – pré-visualização pública<!-- 1958649 -->
Com a atualização desta funcionalidade, poderá criar um perfil de configuração de dispositivos que retire um dispositivo com o Windows 10 do modo S ou que impeça os utilizadores de retirarem o dispositivo do modo S. Esta funcionalidade está em Intune > **Configuração do dispositivo** > **Perfis** >  **Windows 10 e versões posteriores** > **Atualização da edição e alteração de modo**.
[Introdução ao Windows 10 no modo S](https://www.microsoft.com/windows/s-mode) fornece mais informações sobre o modo S.
Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile---2144658---"></a>Pacote de configuração do Windows Defender ATP adicionado automaticamente ao perfil de configuração<!-- 2144658 -->
Ao utilizar dispositivos de [Proteção Avançada Contra Ameaças e integração](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile) no Intune, tinha de transferir um pacote de configuração e adicioná-lo ao seu perfil de configuração. Com esta atualização, o Intune obtém automaticamente o pacote a partir do Centro de Segurança do Windows Defender e adiciona-o ao seu perfil.
Aplica-se ao Windows 10 e posterior.

#### <a name="require-users-to-connect-during-device-setup--2311457--"></a>Exigir que os utilizadores estabeleçam ligação durante a configuração do dispositivo<!--2311457-->
Agora pode definir perfis de dispositivos de modo a exigir que o dispositivo esteja ligado a uma rede antes de avançar para além da página Rede durante a configuração do Windows 10. Enquanto esta funcionalidade estiver em pré-visualização, é necessário que tenha a versão 1809 ou versões posteriores do Windows Insider para utilizar esta definição.
Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices---2451462---"></a>Restringir aplicações e bloquear o acesso aos recursos da empresa em dispositivos iOS e Android Enterprise<!-- 2451462 -->
Em **Conformidade do dispositivo** > **Políticas** > **Criar política** > **iOS** > **Segurança do Sistema**, há uma nova definição de **Aplicações restritas**. Esta nova definição utiliza uma política de conformidade para bloquear o acesso aos recursos da empresa, caso determinadas aplicações estejam instaladas no dispositivo. O dispositivo é considerado não compatíveis até que as aplicações restritas sejam removidas do dispositivo.
Aplica-se a: iOS

#### <a name="modern-vpn-support-updates-for-ios---2459928-1819876-and-2650856---"></a>A VPN moderna suporta atualizações para iOS<!-- 2459928, 1819876, and 2650856 -->
Esta atualização adiciona suporte para os seguintes clientes VPN do iOS:
- F5 Access (versão 3.0.1 e superior)
- Citrix SSO
- Palo Alto Networks GlobalProtect (versão 5.0 e superior). Também nesta atualização:
- O nome do tipo de ligação **F5 Access** foi alterado para **F5 Access Legacy** para o iOS.
- O nome do tipo de ligação **Palo Alto Networks GlobalProtect** foi alterado para **Palo Alto Networks GlobalProtect (legacy)** para o iOS.
Os perfis existentes com estes tipos de ligação continuam a funcionar com o respetivo cliente VPN legado. Se estiver a utilizar o Cisco Legacy AnyConnect, F5 Access Legacy, VPN do Citrix ou Palo Alto Networks GlobalProtect (versão 4.1 ou anterior) com o iOS, deve mudar para as novas aplicações. Faça-o assim que possível para garantir que o acesso VPN está disponível para dispositivos iOS, conforme os mesmos são atualizados para iOS 12.
Para obter mais informações sobre o iOS 12 e os perfis VPN, veja o [Blogue da Equipa de Suporte do Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal---2469637---"></a>Exportar políticas de conformidade do portal clássico do Azure para recriar estas políticas no Intune no portal do Azure<!-- 2469637 -->
As políticas de conformidade que criou no portal clássico do Azure serão preteridas. Pode rever e eliminar quaisquer políticas de conformidade existentes, mas não pode atualizá-las. Se precisar de migrar políticas de conformidade para o Intune no portal do Azure atual, pode exportar as políticas sob a forma de um ficheiro separado por vírgulas (ficheiro *.csv*). Em seguida, utilize os detalhes no ficheiro para recriar estas políticas no Intune no portal do Azure.

> [!IMPORTANT]
> Quando o portal clássico do Azure for descontinuado, deixará de conseguir aceder ou ver as suas políticas de conformidade. Por isso, não se esqueça de as exportar e recriar no portal do Azure antes de o portal clássico do Azure ser descontinuado.

#### <a name="better-mobile---new-mobile-threat-defense-partner---22662717---"></a>Better Mobile – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis<!-- 22662717 -->
Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada por um melhor Mobile, uma solução de defesa contra ameaças móveis que se integra ao Microsoft Intune.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in--1067692---"></a>Bloquear o Portal da Empresa no modo de aplicação única até o utilizador iniciar sessão<!--1067692 --> 
Agora pode optar por executar o Portal da Empresa no modo de Aplicação Única se autenticar um utilizador através do Portal da Empresa em vez do Assistente de Configuração durante a inscrição de DEP. Esta opção bloqueia o dispositivo imediatamente após a conclusão do Assistente de Configuração, para que um utilizador tenha de iniciar sessão para aceder ao dispositivo. Este processo assegura que o dispositivo conclui a inclusão e não fica órfão num estado sem qualquer utilizador ligado.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device--1346521---"></a>Atribuir um utilizador e um nome amigável a um dispositivo do Autopilot<!--1346521 -->
Agora pode [atribuir um utilizador a um único dispositivo do Autopilot](../enrollment/enrollment-autopilot.md). Os administradores também serão capazes de atribuir nomes amigáveis para dar as boas-vindas ao utilizador quando estão a configurar o dispositivo com o Autopilot.
Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment---1608345---"></a>Utilizar licenças de dispositivos VPP para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP<!-- 1608345 -->
Agora pode utilizar licenças de dispositivos do Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante as inscrições do Programa de Registo de Aparelho (DEP). Para tal, ao [criar ou editar um perfil de inscrição](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), especifique o token VPP que pretende utilizar para instalar o Portal da Empresa. Certifique-se de que o token não expira e que tem licenças suficientes para a aplicação Portal da Empresa. Nos casos em que o token expirar ou esgotar as licenças, o Intune irá iniciar o Portal da Empresa a partir da App Store (esta ação irá exigir um ID Apple).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning---2237634---"></a>Confirmação necessária para eliminar o token VPP que está a ser utilizado para aprovisionar previamente o Portal da Empresa<!-- 2237634 -->
É necessária uma confirmação para eliminar um token VPP (Volume Purchase Program) se o mesmo estiver a ser utilizado para aprovisionar previamente o Portal da Empresa durante a inscrição no DEP.

#### <a name="block-windows-personal-device-enrollments---1849498---"></a>Bloquear inscrições de dispositivos pessoais do Windows<!-- 1849498 -->
Pode [impedir que os dispositivos pessoais do Windows](../enrollment/enrollment-restrictions-set.md) se inscrevam com a [gestão de dispositivos móveis](../enrollment/windows-enroll.md) no Intune. A inscrição de dispositivos com o [agente de PC do Intune](../manage-windows-pcs-with-microsoft-intune.md) não pode ser bloqueada com esta funcionalidade. Esta funcionalidade será implementada durante as próximas semanas, pelo que poderá não a ver imediatamente na interface de utilizador.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile--1849855--"></a>Especificar os padrões de nome de computador num perfil do Autopilot<!--1849855-->
Pode [especificar um modelo de nome do computador](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) para gerar e definir o [nome do computador](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante a inscrição do Autopilot. Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page--1901669---"></a>Nos perfis do Windows Autopilot, ocultar as opções de alteração da conta na página de início de sessão da empresa e na página de erro do domínio<!--1901669 -->
Existem [novas opções de perfil do Windows Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) para os administradores ocultarem as opções de alteração de conta nas páginas de início de sessão da empresa e de erro no domínio. Para ocultar essas opções, é preciso configurar a Imagem Corporativa da Empresa no Azure Active Directory. Aplica-se a: à versão mais recente do [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (período de pré-visualização).

### <a name="macos-support-for-apple-device-enrollment-program---747651---"></a>Suporte do macOS para o Programa de Registo de Aparelho da Apple<!-- 747651 -->
Agora, o Intune suporta a inscrição de dispositivos macOS no Programa de Registo de Aparelho da Apple (DEP). Para obter mais informações, veja [Inscrever automaticamente dispositivos macOS com o Programa de Registo de Aparelho da Apple](../enrollment/device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="delete-jamf-devices---2653306--"></a>Eliminar dispositivos Jamf<!-- 2653306-->
Pode eliminar dispositivos geridos pelo JAMF ao aceder a **Dispositivos** > selecionar o dispositivo Jamf > **Eliminar**.

#### <a name="change-terminology-to-retire-and-wipe---2175759---"></a>Alterar a terminologia para “extinguir” e “eliminar”<!-- 2175759 -->
Para ser consistente com o Graph API, os seguintes termos foram alterados na documentação e na interface de utilizador do Intune:
- **Remover dados da empresa** será alterado para "extinguir"
- **Reposição de fábrica** será alterado para **eliminar**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate---297909500--"></a>Caixa de diálogo de confirmação apresentada se o administrador tentar eliminar o Certificado Push de MDM<!-- 297909500-->
Se alguém tentar eliminar um Certificado Push de MDM da Apple, uma caixa de diálogo de confirmação apresenta o número de dispositivos iOS e macOS associados. Se o certificado for eliminado, será necessário inscrever novamente estes dispositivos.

#### <a name="additional-security-settings-for-windows-installer---2282430---"></a>Definições de segurança adicionais para o Windows installer<!-- 2282430 -->
Pode permitir que os utilizadores controlem a instalação de aplicações. Se estiver ativada, esta definição permite continuar as instalações que, caso contrário, seriam interrompidas devido a uma violação de segurança. Pode configurar o Windows Installer para utilizar permissões elevadas ao instalar programas num sistema. Além disso, pode ativar os itens do Windows Information Protection (WIP) para serem indexados e os metadados acerca dos mesmos para serem armazenados numa localização não encriptada. Quando a política está desativada, os itens protegidos pelo WIP não são indexados e não são apresentados nos resultados na Cortana ou no explorador de ficheiros. A funcionalidade destas opções está desativada por predefinição. 

#### <a name="new-user-experience-update-for-the-company-portal-website--2000968---"></a>Nova atualização da experiência de utilizador no site do Portal da Empresa<!--2000968 -->
Adicionámos novas funcionalidades ao site do Portal da Empresa com base no feedback dos clientes. Irá ver uma melhoria significativa na facilidade de utilização e nas funcionalidades existentes nos seus dispositivos. Algumas áreas do site &ndash; tais como detalhes do dispositivo, feedback e suporte e descrição geral do dispositivo &ndash; receberam uma nova estrutura moderna e reativa. A atualização inclui ainda:

- Fluxos de trabalho simplificados em todas as plataformas de dispositivos
- Fluxos de inscrição e identificação de dispositivos melhorados
- Mensagens de erro mais úteis
- Linguagem mais simples, menos termos técnicos
- Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações
- Acessibilidade melhorada para todos os utilizadores  

A [documentação do site do Portal da Empresa do Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) foi atualizada para refletir estas alterações. Para ver um exemplo das melhorias ao nível das aplicações, veja [Atualização da IU para aplicações de utilizadores finais do Intune](../whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Deteção de jailbreak melhorada no relatório de conformidade<!-- 2198738 -->
Os estados da definição de deteção de jailbreak avançada são agora apresentados em todos os relatórios de conformidade na consola de administração.

### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="scope-tags-for-policies--1081974---"></a>Etiquetas de âmbito para políticas<!--1081974 -->
Pode [criar etiquetas de âmbito](scope-tags.md) para restringir o acesso aos recursos do Intune. Adicione uma etiqueta de âmbito a uma atribuição de função e, em seguida, adicione a etiqueta de âmbito a um perfil de configuração. A função apenas terá acesso aos recursos com perfis de configuração com etiquetas de âmbito correspondentes (ou nenhuma etiqueta de âmbito).





<!-- ########################## -->
## <a name="july-2018"></a>Julho de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="line-of-business-lob-app-support-for-macos---1895847---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS<!-- 1895847 -->
O Microsoft Intune permite que as aplicações LOB para macOS sejam implementadas como **Necessário** ou **Disponível com inscrição**. Os utilizadores finais podem implementar as aplicações como **Disponível** com o Portal da Empresa para macOS ou com o [site do Portal da Empresa](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode---2051098---"></a>Suporte de aplicações integradas para iOS para o modo de quiosque<!-- 2051098 -->
Para além das Aplicações da Loja e das Aplicações Geridas, pode selecionar uma Aplicação Integrada (como o Safari) que executa em modo de quiosque num dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments---2150145---"></a>Editar as implementações de aplicações do Office 365 Pro Plus<!-- 2150145 -->
Enquanto administrador do Microsoft Intune, tem maior capacidade de editar as suas implementações de aplicações do Office 365 Pro Plus. Adicionalmente, já não precisa de eliminar as suas implementações para alterar qualquer uma das propriedades do conjunto. No portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Aplicações**. A partir da lista de aplicações, selecione o Office 365 Pro Plus Suite.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available---2744271--"></a>O SDK da Aplicação do Intune para Android atualizado já está disponível<!-- 2744271-->
Uma versão atualizada do SDK da Aplicação do Intune para Android está disponível para suportar o lançamento do Android P. Se é um programador de aplicações e utiliza o SDK do Intune para Android, tem de instalar a versão atualizada do SDK da aplicação do Intune para garantir que a funcionalidade do Intune nas suas aplicações Android continuam a funcionar conforme esperado nos dispositivos Android P. Esta versão do SDK da Aplicação do Intune fornece um plug-in integrado que efetua as atualizações do SDK. Não precisa de reescrever o código existente que estiver integrado. Para obter mais detalhes, veja [SDK do Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Se estiver a utilizar o estilo de criação de distintivos antigo do Intune, recomendamos que utilize o ícone de porta-documentos. Para obter informações corporativas, veja [este repositório do GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Mais oportunidades de sincronização na aplicação Portal da Empresa para Windows  
Agora a aplicação Portal da Empresa para Windows permite-lhe iniciar uma sincronização a partir do menu Iniciar e da barra de tarefas do Windows. Esta funcionalidade é especialmente útil se a sua tarefa for sincronizar dispositivos e obter acesso a recursos da empresa. Para aceder à nova funcionalidade, clique com o botão direito do rato no ícone do Portal da Empresa que está afixado à barra de tarefas ou menu Iniciar. Nas opções do menu (também conhecido como lista de atalhos), selecione **Sincronizar este dispositivo**. O Portal da Empresa abrirá para a página **Definições** e iniciará a sua sincronização. Para ver a nova funcionalidade veja [o que há de novo na UI.](../whats-new-app-ui.md)   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Novas experiências de navegação na aplicação Portal da Empresa para Windows  
Ao navegar ou procurar aplicações na aplicação Portal da Empresa para Windows, pode alternar entre a vista **Mosaicos** existente e a vista **Detalhes** recentemente adicionada. A nova vista apresenta os detalhes das aplicações, como o nome, o publicador, a data de publicação e o estado da instalação.  

A vista **Instalado** da página **Aplicações** permite-lhe ver detalhes sobre as instalações de aplicações concluídas e em curso. Para ver o aspeto da nova vista, veja [Novidades na IU](../whats-new-app-ui.md).  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Experiência da aplicação Portal da Empresa melhorada para gestores de inscrições de dispositivos  
Quando um gestor de inscrições de dispositivos (DEM) iniciar sessão na aplicação Portal da Empresa para Windows, agora a aplicação só apresentará o dispositivo atual do DEM. Esta melhoria irá reduzir os erros de tempo limite que ocorriam quando a aplicação tentava mostrar todos os dispositivos inscritos pelo DEM.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models----1425689----"></a>Bloquear o acesso a aplicações baseado em fornecedores e modelos de dispositivos não aprovados <!-- 1425689 ! -->
O administrador de TI do Intune pode impor uma lista específica de fabricantes Android e/ou de modelos iOS nas Políticas de Proteção de Aplicações do Intune. O administrador de TI pode fornecer uma lista separada por ponto e vírgula de fabricantes para políticas para Android e de modelos de dispositivos para políticas iOS. As Políticas de Proteção de Aplicações do Intune destinam-se apenas a Android e iOS. Existem duas ações separadas que podem ser realizadas na lista especificada:
- O bloqueio do acesso a aplicações em dispositivos não especificados.
- Uma eliminação seletiva de dados empresariais em dispositivos não especificados. 

O utilizador não conseguirá aceder à aplicação visada se os requisitos da política não forem cumpridos. Com base nas definições escolhidas, os dados empresariais do utilizador podem ser bloqueados ou eliminados seletivamente da aplicação. Nos dispositivos iOS, esta funcionalidade requer que a participação de aplicações (tais como o WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune para que a funcionalidade seja imposta nas aplicações visadas. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. No Android, esta funcionalidade necessita da versão mais recente do Portal da Empresa. 

Nos dispositivos dos utilizadores finais, o cliente do Intune tomará medidas com base numa única correspondência das cadeias especificadas no painel Intune das Políticas de Proteção de Aplicações. Isto depende inteiramente do valor comunicado pelo dispositivo. Como tal, recomendamos que o administrador de TI se certifique de que o comportamento pretendido é preciso. Pode fazê-lo ao testar esta definição com base em vários fabricantes e modelos de dispositivos direcionados para um grupo de utilizadores pequeno. No Microsoft Intune, selecione **Aplicações do cliente** > **Políticas de proteção de aplicações** para ver e adicionar políticas de proteção de aplicações. Para obter mais informações sobre as políticas de proteção de aplicações, veja [O que são as políticas de proteção de aplicações?](../apps/app-protection-policy.md) e [Eliminação seletiva de dados através de ações de acesso das políticas de proteção de aplicações no Intune](../apps/app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build---1734766---"></a>Acesso à compilação de pré-lançamento do Portal da Empresa do macOS<!-- 1734766 -->
Com o Microsoft AutoUpdate, pode inscrever-se para receber compilações antecipadamente ao aderir ao programa Insider. A inscrição permitir-lhe-á utilizar o Portal da Empresa atualizado antes de este ser disponibilizado aos seus utilizadores finais. Para obter mais informações, veja o [blogue do Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices---1497640---"></a>Criar política de conformidade de dispositivos com as Definições de firewall em dispositivos macOS<!-- 1497640 -->
Quando criar uma nova política de conformidade do macOS (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: macOS** > **Segurança do sistema**), estarão disponíveis algumas definições de **Firewall** novas: 

- **Firewall**: configure a forma como as ligações de entrada são processadas no seu ambiente.
- **Ligações de entrada**: **bloqueia** todas as ligações de entrada, exceto as ligações necessárias para serviços básicos de Internet, tal como o DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha.
- **Modo invisível**: **ative** o modo invisível para impedir que o dispositivo responda aos pedidos de pesquisa. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas.

Aplica-se a: macOS 10.12 e posterior

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later---1879077---"></a>Novo perfil de configuração de dispositivos Wi-Fi para Windows 10 e posterior<!-- 1879077 -->
Atualmente, pode importar e exportar perfis Wi-Fi através de ficheiros XML. Com esta atualização, pode criar um perfil de configuração de dispositivos Wi-Fi diretamente no Intune, tal como o faria em algumas outras plataformas.

Para criar o perfil, abra o menu **Configuração do dispositivo** > **Perfis** > **Criar Perfil** > **Windows 10 e versões posteriores** > **Wi-Fi**. 

Aplica-se ao Windows 10 e posterior.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed---2149998---"></a>A funcionalidade Quiosque (obsoleta) foi desativada e não pode ser alterada<!-- 2149998 -->
A funcionalidade Quiosque (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e posterior** > **Restrições do dispositivo**) está obsoleta e foi substituída pelas [definições do Quiosque para Windows 10 e posterior](../configuration/kiosk-settings.md). Com esta atualização, a funcionalidade **Quiosque – Obsoleto** foi desativada e a interface de utilizador não pode ser alterada nem atualizada. 

Para ativar o modo de quiosque, veja [Definições de quiosque para Windows 10 e posterior](../configuration/kiosk-settings.md).

Aplica-se ao Windows 10 e posterior e ao Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities---2184013---"></a>APIs para utilização de autoridades de certificação de terceiros<!-- 2184013 -->
Nesta atualização, foi disponibilizada uma API Java que permite a integração de autoridades de certificação externas no Intune e no SCEP. A partir daí, os utilizadores podem adicionar o certificado SCEP a um perfil e aplicá-lo aos dispositivos com MDM.

Atualmente, o Intune suporta [pedidos de SCEP que utilizam os Serviços de Certificados do Active Directory](../protect/certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser---2455253---"></a>Alternar entre mostrar ou não mostrar o botão Terminar Sessão num browser de Quiosque<!-- 2455253 -->
Agora pode configurar as opções para determinar se os browsers do Quiosque devem ou não mostrar o botão Terminar Sessão. Pode ver o controlo em **Configuração do dispositivo** > **Quiosque (pré-visualização)**  > **Browser da Web do Quiosque**. Se o botão estiver ativado e quando o utilizador clicar no mesmo, a aplicação pede confirmação para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação e regressa ao URL predefinido.

#### <a name="create-an-esim-cellular-configuration-profile---2564077---"></a>Criar um perfil de configuração de rede móvel eSIM<!-- 2564077 -->
Em **Configuração do dispositivo**, pode criar um perfil celular eSIM. Pode importar um ficheiro com códigos de ativação de rede móvel fornecidos pela sua operadora móvel. Em seguida, poderá implementar estes perfis nos seus dispositivos Windows 10 compatíveis com eSIM LTE, como o Surface Pro LTE e outros dispositivos compatíveis com eSIM.

Verifique se os seus [dispositivos suportam perfis eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Aplica-se ao Windows 10 e posterior.

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings---1058963-eenotready---"></a>Selecionar as categorias de dispositivos através das definições de Acesso Profissional ou Escolar<!-- 1058963 eenotready --> 
Se tiver ativado o [mapeamento do grupo de dispositivos](../enrollment/device-group-mapping.md), agora será pedido aos utilizadores no Windows 10 que selecionem uma categoria de dispositivos após a inscrição através do botão **Ligar** em **Definições** > **Contas** > **Acesso profissional ou escolar**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles---1500307---"></a>Utilizar sAMAccountName como o nome de utilizador da conta para perfis de e-mail<!-- 1500307 -->
Pode utilizar **sAMAccountName** no local como o nome de utilizador da conta para perfis de e-mail para Android, iOS e Windows 10. Também pode obter o domínio do atributo `domain` ou `ntdomain` no Azure Active Directory (Azure AD). Em alternativa, introduza um domínio estático personalizado.

Para utilizar esta funcionalidade, tem de sincronizar o atributo `sAMAccountName` do seu ambiente do Active Directory no local com o Azure AD.

Aplica-se ao [Android](../configuration/email-settings-android.md), [iOS](../configuration/email-settings-ios.md), [Windows 10 e posterior](../configuration/email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict---1556983---"></a>Ver perfis de configuração de dispositivos em conflito<!-- 1556983 -->
Em **Configuração do Dispositivo**, é apresentada uma lista dos perfis existentes. Com esta atualização, é adicionada uma nova coluna que fornece detalhes sobre os perfis que apresentam conflitos. Pode selecionar uma linha de conflito para ver a definição e o perfil que está em conflito. 

Saiba mais sobre como [gerir perfis de configuração](../configuration/device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance---2308882---"></a>Novo estado dos dispositivos em Conformidade do dispositivo<!-- 2308882 -->
Em **Conformidade do dispositivo** > **Políticas** > selecione uma política > **Descrição geral**, são adicionados os novos estados que se seguem:
- com êxito
- erro
- conflito
- pendente
- não aplicável Também é apresentada uma imagem que mostra a contagem de dispositivos de uma plataforma diferente. Por exemplo, se observar um perfil iOS, o novo mosaico mostra a contagem de dispositivos não iOS atribuídos a este perfil. Veja [Políticas de conformidade do dispositivo](../protect/compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions---2325484---"></a>A conformidade do dispositivo suporta soluções de antivírus de terceiros<!-- 2325484 -->
Ao criar uma política de conformidade do dispositivo (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: Windows 10 e posterior** > **Definições** > **Segurança do sistema**), estão disponíveis novas opções de **[Segurança do Dispositivo](../protect/compliance-policy-create-windows.md)** : 
- **Antivírus**: quando estiver definido como **Exigir**, pode verificar a conformidade com soluções de antivírus registadas com o Centro de Segurança do Windows, tal como Symantec e o Windows Defender. 
- **AntiSpyware**: quando estiver definido como **Exigir**, pode verificar a conformidade com soluções de antispyware registadas com o Centro de Segurança do Windows, tal como Symantec e o Windows Defender. 

Aplica-se a: Windows 10 e posterior 

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate---2404851---"></a>Marcar automaticamente dispositivos Android inscritos através do Samsung Knox Mobile Enrollment como "empresarial".<!-- 2404851 -->
Por predefinição, os dispositivos Android inscritos através do Samsung Knox Mobile Enrollment são marcados como **empresarial** em **Propriedade do Dispositivo**. Não tem de identificar manualmente os dispositivos empresariais através dos números de série ou do IMEI antes da inscrição com o Knox Mobile Enrollment.

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens---1853904---"></a>Coluna Dispositivos sem perfis na lista de tokens do programa de inscrição<!-- 1853904 -->
Na lista de tokens do programa de inscrição, existe uma nova coluna que apresenta o número de dispositivos sem um perfil atribuído. Isto ajuda os administradores a atribuírem perfis a estes dispositivos antes de os distribuírem pelos utilizadores. Para ver a nova coluna, aceda a **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="bulk-delete-devices-on-devices-blade---1793693---"></a>Eliminar dispositivos em massa no painel Dispositivos<!-- 1793693 -->
Agora pode eliminar múltiplos dispositivos de uma só vez no painel Dispositivos. Selecione **Dispositivos** > **Todos os dispositivos** > selecione os dispositivos que pretende eliminar > **Eliminar**. Será apresentado um alerta para os dispositivos que não puderem ser eliminados.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work--842873---"></a>Alterações de nome da Google para Android for Work e Play for Work<!--842873 -->
O Intune atualizou a terminologia do "Android for Work" para refletir as alterações de imagem corporativa da Google. Os termos "Android for Work" e "Play for Work" já não são utilizados. É utilizada terminologia diferente consoante o contexto:
- "Android Enterprise" refere-se à pilha de gestão de Android global e moderna.
- "Perfil profissional" ou "Proprietário do Perfil" refere-se a dispositivos BYOD geridos com perfis profissionais.
- "Google Play Gerido" refere-se à loja de aplicações da Google.

#### <a name="rules-for-removing-devices---1609459---"></a>Regras para remover dispositivos<!-- 1609459 -->
Estão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não tenham sido registados durante o número de dias definido. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de limpeza do dispositivo**.

#### <a name="corporate-owned-single-use-support-for-android-devices---1630973---"></a>Suporte de utilização única pertencente à empresa para dispositivos Android<!-- 1630973 -->

O Intune agora suporta dispositivos Android ao estilo de quiosque, bloqueados e altamente geridos. Isto permite que os administradores bloqueiem a utilização de um dispositivo para uma única aplicação ou pequeno conjunto de aplicações e impede que os utilizadores ativem outras aplicações ou efetuem outras ações no dispositivo. Para configurar o quiosque Android, aceda a Intune > **Inscrição de dispositivos** > **Inscrição Android** > **Inscrição de quiosque e dispositivos de tarefas**. Para obter mais informações, veja [Set up enrollment of Android enterprise kiosk devices](../enrollment/android-kiosk-enroll.md) (Configurar a inscrição de dispositivos de quiosque do Android Enterprise).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded---2203794--"></a>Revisão por linha de identificadores de dispositivos da empresa duplicados carregados<!-- 2203794-->
Ao carregar IDs empresariais, o Intune agora fornece uma lista de duplicados e dá-lhe a opção de substituir ou manter as informações existentes. O relatório será apresentado se existirem duplicados após selecionar **Inscrição do dispositivo** > **Identificadores de Dispositivo da Empresa** > **Adicionar Identificadores**. 

#### <a name="manually-add-corporate-device-identifiers---2203803---"></a>Adicionar manualmente identificadores de dispositivos da empresa<!-- 2203803 -->
Agora pode adicionar manualmente IDs de dispositivos da empresa. Selecione **Inscrição de dispositivos** > **Identificadores de Dispositivo da Empresa** > **Adicionar**. 


<!-- ########################## -->
## <a name="june-2018"></a>Junho de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies---1817882---"></a>Suporte móvel de políticas de proteção de aplicações do Intune no Microsoft Edge<!-- 1817882 -->
O browser Microsoft Edge para dispositivos móveis agora suporta as políticas de proteção de aplicações definidas no Intune.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode---1560077----"></a>Obter o ID de modelo de utilizador da aplicação (AUMID) associado para aplicações da Microsoft Store para Empresas no modo de quiosque<!-- 1560077 ! -->
O Intune pode agora obter os IDs de modelo de utilizador da aplicação (AUMIDs) para aplicações da Microsoft Store para Empresas (WSfB) para proporcionar uma configuração melhorada do perfil de quiosque.

Para obter mais informações sobre aplicações da Microsoft Store para Empresas, veja [Gerir aplicações a partir da Microsoft Store para Empresas](../apps/windows-store-for-business.md).

#### <a name="new-company-portal-branding-page---1916370---"></a>Nova página de imagem corporativa do Portal da Empresa<!-- 1916370 -->
A página de imagem corporativa do Portal da Empresa tem um novo esquema, mensagens e descrições.


### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="pradeo---new-mobile-threat-defense-partner---1169249---"></a>Pradeo – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis<!-- 1169249 -->
Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Pradeo, uma solução de defesa contra ameaças móveis que se integra ao Microsoft Intune.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector---1333688---"></a>Utilizar o modo FIPS com o conector do Certificado NDES<!-- 1333688 -->
Ao instalar o conector do Certificado NDES num computador com o modo FIPS (Federal Information Processing Standard) ativado, a emissão e a revogação de certificados não funcionaram como esperado. Com esta atualização, é incluído suporte para FIPS com o conector do Certificado NDES. 

Esta atualização também inclui:

- O conector do Certificado NDES precisa do .NET 4.5 Framework, que é incluído automaticamente com o Windows Server 2016 e o Windows Server 2012 R2. Anteriormente, a versão mínima necessária era o .NET 3.5 Framework.
- É incluído suporte para o TLS 1.2 com o Certificate Connector do NDES. Assim, se o servidor com o Certificate Connector do NDES instalado suportar o TLS 1.2, será utilizado o TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

Para obter mais informações, veja [Configurar e utilizar certificados SCEP](../protect/certificates-scep-configure.md) e [Configurar e utilizar certificados PKCS](../protect/certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles---1333680----"></a>Suporte para perfis de VPN do GlobalProtect da Palo Alto Networks<!-- 1333680 ! -->
Com esta atualização, pode escolher o GlobalProtect da Palo Alto Networks como um tipo de ligação VPN para perfis de VPN no Intune (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Tipo de perfil** > **VPN**). Neste lançamento, são suportadas as seguintes plataformas: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings---1403702---"></a>Adições às definições de Opções de Segurança do Dispositivo Local<!-- 1403702 -->
Agora é possível configurar definições adicionais de Opções de Segurança do Dispositivo Local para dispositivos com o Windows 10. As definições adicionais estão disponíveis nas áreas do Cliente de Rede da Microsoft, Servidor de Rede da Microsoft, Segurança e acesso à rede e Início de sessão interativo. Estas definições encontram-se na categoria Endpoint Protection durante a criação de uma política de configuração de dispositivo Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices---1560072----"></a>Ativar o modo quiosque em dispositivos com o Windows 10<!-- 1560072 ! -->
Nos dispositivos com o Windows 10, pode criar um perfil de configuração e ativar o modo de quiosque (**Configuração do Dispositivo** > **Perfis** > **Criar perfil** > **Windows 10** > **Restrições do Dispositivo** > **Quiosque**). Nesta atualização, o nome da definição **Quiosque (pré-visualização)** irá mudar para **Quiosque (obsoleto)** . A utilização da definição **Quiosque (obsoleto)** deixará de ser recomendada, embora continue a estar funcional até à atualização de julho. A definição **Quiosque (obsoleto)** será substituída pelo novo tipo de perfil de **Quiosque** (**Criar perfil** > **Windows 10** > **Quiosque (pré-visualização)** ), que incluirá as definições para configurar Quiosques no Windows 10 RS4 e posterior.

Aplica-se ao Windows 10 e posterior.

#### <a name="device-profile-graphical-user-chart-is-back---2160133---"></a>O gráfico de utilizadores do perfil do dispositivo está de volta<!-- 2160133 -->
Durante a melhoria das contagens apresentadas no gráfico de utilizadores do perfil do dispositivo (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição geral**), este gráfico foi removido temporariamente.

Com esta atualização, o gráfico de utilizadores está de volta e é apresentado no portal do Azure.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication---1165118---"></a>Suporte para a inscrição do Windows Autopilot sem autenticação do utilizador<!-- 1165118 -->
O Intune suporta a inscrição do Windows Autopilot sem autenticação de utilizador. Esta é uma opção nova no perfil de implementação do Windows Autopilot "Modo de implementação do Autopilot" definido para "Implementação Automática".  O dispositivo tem de estar a executar a Versão 17672 do Windows 10 Insider Preview ou posterior e ter um chip do TPM 2.0 para concluir este tipo de inscrição com êxito. Uma vez que não é necessária a autenticação de utilizador, só deve atribuir esta opção a dispositivos sobre os quais tenha o controlo físico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot---1821766---"></a>Nova definição de idioma/região ao configurar o OOBE para o AutoPilot<!-- 1821766 -->
É disponibilizada uma nova configuração para definir o idioma e a região de perfis AutoPilot durante a experiência OOBE (Out of Box Experience). Para ver a nova definição, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de implementação** > **Criar perfil** > **Modo de implementação** = **Implementação automática** > **Predefinições configuradas**.

#### <a name="new-setting-for-configuring-device-keyboard---1821768---"></a>Nova definição para configurar o teclado do dispositivo<!-- 1821768 -->
Será disponibilizada uma nova definição para configurar o teclado de perfis AutoPilot durante a experiência OOBE (Out of Box Experience). Para ver a nova definição, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de implementação** > **Criar perfil** > **Modo de implementação** = **Implementação automática** > **Predefinições configuradas**.

#### <a name="autopilot-profiles-moving-to-group-targeting---1877935---"></a>Mudança dos perfis do Autopilot para a filtragem de grupo<!-- 1877935 -->
Os perfis de implementação AutoPilot podem ser atribuídos a grupos do Azure AD com contenham dispositivos AutoPilot.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="set-compliance-by-device-location---851881----"></a>Definir a conformidade pela localização do dispositivo<!-- 851881 ! -->
Em algumas situações, pode ser útil restringir o acesso a recursos empresariais para uma localização específica, definida por uma ligação de rede. Pode criar uma política de conformidade (**Conformidade do dispositivo** > **Localizações**) baseada no endereço IP do dispositivo. Se o dispositivo estiver fora do intervalo de IP, não conseguirá aceder a recursos empresariais.

Aplica-se a: dispositivos com o Android 6.0 e superior, com a aplicação Portal da Empresa atualizada

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Impedir as experiências e aplicações de consumidor em dispositivos AutoPilot com o Windows 10 Enterprise RS4<!-- 1621980 -->
Poderá impedir a instalação de experiências e aplicações de consumidor nos seus dispositivos AutoPilot com o Windows 10 Enterprise RS4. Para ver esta funcionalidade, aceda a **Intune** > **Configuração de dispositivos** > **Perfis** > **Criar perfil** > **Plataforma** = **Windows 10 ou posterior** > **Tipo de perfil** = **Restrições de dispositivos** > **Configurar** > **Windows Spotlight** > **Funcionalidades do consumidor**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates---1732948---"></a>Desinstalar as atualizações de software mais recentes do Windows 10<!-- 1732948 -->
Se detetar um problema de interrupção em computadores com Windows 10, pode optar por desinstalar (reverter) a atualização mais recente da funcionalidade ou a atualização mais recente de qualidade. A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado. A desinstalação irá acionar uma política para restaurar a atualização anterior em computadores com Windows 10. Especificamente para atualizações da funcionalidade, pode limitar o tempo de 2 a 60 dias em que pode ser aplicada uma desinstalação da versão mais recente. Para definir as opções de desinstalação da atualização do software, selecione **Atualizações do software** do painel **Microsoft Intune** no portal do Azure. Em seguida, selecione **Anéis de Atualização do Windows 10**, a partir do painel **Atualizações do software**. Em seguida, pode selecionar a opção **Desinstalar** na secção **Descrição geral**.

#### <a name="search-all-devices-for-imei-and-serial-number---1793685---"></a>Procurar o IMEI e o número de série em todos os dispositivos<!-- 1793685 -->
Pode procurar por IMEI e números de série no painel Todos os dispositivos (e-mail, UPN, nome do dispositivo e nome de gestão ainda estão disponíveis). No Intune, selecione **Dispositivos** > **Todos os dispositivos** > introduza a sua pesquisa na caixa de pesquisa.

#### <a name="management-name-field-will-be-editable---1875989---"></a>O campo Nome de gestão passará a ser editável<!-- 1875989 -->
Pode editar o campo Nome de gestão no painel **Propriedades** de um dispositivo. Para editar este campo, selecione **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Propriedades**. Pode utilizar o campo Nome de gestão para identificar um dispositivo de forma exclusiva.

#### <a name="new-all-devices-filter-device-category---1878520---"></a>Novo filtro de todos os dispositivos: categoria de dispositivo<!-- 1878520 -->
Pode filtrar a lista **Todos os dispositivos** por categoria de dispositivo. Para tal, selecione **Dispositivos** > **Todos os dispositivos** > **Filtro** > **Categoria de dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices---1985547---"></a>Utilizar o TeamViewer para partilhar ecrãs de dispositivos iOS e MacOS<!-- 1985547 -->
Os administradores podem estabelecer ligação ao [TeamViewer](../remote-actions/teamviewer-support.md) e iniciar uma sessão de partilha de ecrã com dispositivos iOS e macOS. Os utilizadores de dispositivos iPhone, iPad e macOS podem partilhar os seus ecrãs em direto com qualquer outro computador ou dispositivo. 

#### <a name="multiple-exchange-connector-support---2070451---"></a>Suporte múltiplo do Exchange Connector<!-- 2070451 -->
Deixará de ficar limitado a um Microsoft Intune Exchange Connector por inquilino. O Intune agora dá suporte a vários conectores do Exchange para que você possa configurar o acesso condicional do Intune com várias organizações locais do Exchange.

Com um Exchange Connector no local do Intune, pode gerir o acesso de dispositivos a caixas de correio do Exchange no local com base no facto de um dispositivo estar ou não inscrito no Intune e estar ou não em conformidade com as políticas de conformidade de dispositivos do Intune. Para configurar um conector, transfira o Exchange Connector no local do Intune a partir do portal do Azure e instale-o num servidor na sua organização do Exchange. No dashboard do Microsoft Intune, selecione **Acesso no local** e, em **Configuração**, selecione **Conector do Exchange ActiveSync**. Transfira o Exchange Connector no local e instale-o num servidor na sua organização do Exchange. Como deixou de estar limitado a um Exchange Connector por inquilino, se tiver mais organizações do Exchange, pode seguir este processo para transferir e instalar um conector para cada organização do Exchange adicional.

#### <a name="new-device-hardware-detail-ccid---2156657---"></a>Detalhes do novo hardware do dispositivo: CCID<!-- 2156657 -->
As informações de Dispositivo de Interface de Cartão de Circuito Integrado (CCID) estão agora incluídas para cada dispositivo. Para vê-las, selecione **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Hardware**> verifique em **Detalhes da rede**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups---2196803---"></a>Atribuir todos os utilizadores e dispositivos como grupos de âmbito<!-- 2196803 -->
Pode agora atribuir todos os utilizadores, todos os dispositivos e todos os utilizadores e dispositivos em grupos de âmbito. Para o fazer, selecione **Funções do Intune** > **Todas as funções** > **Gestor de políticas e perfis** > **Atribuições** > selecione uma atribuição > **Âmbito (grupos)** .

#### <a name="udid-information-now-included-for-ios-and-macos-devices---2219806---"></a>Informações de UDID agora incluídas para dispositivos iOS e macOS<!-- 2219806 -->
Para ver o Identificador Único do Dispositivo (UDID) para dispositivos iOS e macOS, aceda a **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Hardware**. O UDID só está disponível para dispositivos empresariais (como definido em **Dispositivos** > **Todos os dispositivos** > selecione um dispositivo > **Propriedades** > **Propriedade do dispositivo**).

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="improved-troubleshooting-for-app-installation---928990---"></a>Melhorias na resolução de problemas de instalação de aplicações<!-- 928990 -->
Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. Vamos lançar uma Pré-visualização Pública das nossas funcionalidades de Resolução de Problemas de Aplicações. Verá um novo nó em cada dispositivo denominado **Aplicações Geridas**. Este nó apresenta as aplicações que foram enviadas através do Intune MDM. Dentro do nó, verá uma lista de estados de instalação das aplicações. Se selecionar uma única aplicação, ser-lhe-á apresentada a vista de resolução de problemas dessa aplicação específica. Na vista de resolução de problemas, verá o ciclo de vida ponto a ponto da aplicação, por exemplo quando é que a aplicação foi criada, modificada, visada e enviada para um dispositivo. Além disso, se a instalação da aplicação não tiver sido concluída com êxito, ser-lhe-á apresentado o código de erro e uma mensagem útil sobre a causa do erro. 

#### <a name="intune-app-protection-policies-and-microsoft-edge---1818968---"></a>Políticas de proteção de aplicações do Intune e Microsoft Edge<!-- 1818968 -->
Agora o browser Microsoft Edge para dispositivos móveis (iOS e Android) suporta as políticas de proteção de aplicações do Microsoft Intune. Os utilizadores de dispositivos iOS e Android que iniciarem sessão com as contas empresariais do Microsoft Azure AD na aplicação Microsoft Edge passarão a ser protegidos pelo Intune. Em dispositivos iOS, a política **Exigir browser gerido para conteúdo Web** permitirá aos utilizadores abrir ligações no Microsoft Edge quando é gerido.

<!-- ########################## -->
## <a name="may-2018"></a>Maio de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="configuring-your-app-protection-policies---2144597-part-2---"></a>Configurar as políticas de proteção de aplicações<!-- 2144597 Part 2 -->

Agora, no portal do Azure, em vez de aceder ao painel do serviço de Proteção de Aplicações do Intune, acede diretamente ao Intune. Só existe uma localização para as políticas de proteção de aplicações no Intune. Tenha em atenção que todas as suas políticas de proteção de aplicações se encontram no painel **Aplicação móvel** no Intune, em **Políticas de proteção de aplicações**. Esta integração ajuda a simplificar a sua administração da gestão da cloud. Tenha em atenção que todas as políticas de proteção de aplicações já se encontram no Intune e pode modificar as suas políticas configuradas anteriormente. As políticas de proteção da política de aplicações intonou (APP) e as políticas de Acesso Condicional (CA) estão agora no **Acesso Condicional**, que pode ser encontrada na secção **Gerir** na lâmina **Microsoft Intune** ou sob a secção **de Segurança** na lâmina **do Diretório Ativo Azure.** Para obter mais informações sobre a modificação das políticas de acesso condicional, consulte [acesso condicional no Diretório Ativo do Azure.](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) Para obter informações adicionais, veja [O que são as políticas de proteção de aplicações?](../apps/app-protection-policy.md)

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles---1553555---"></a>Exigir a instalação de políticas, aplicações, perfis de certificado e de rede<!-- 1553555 -->
Os administradores podem impedir os utilizadores finais de acederem ao ambiente de trabalho do Windows 10 RS4 até que o Intune instale as políticas, as aplicações e os perfis de certificado e de rede durante o aprovisionamento de dispositivos do AutoPilot. Para obter mais informações, veja [Configurar uma página de estado de inscrição](../enrollment/windows-enrollment-status.md).

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="samsung-knox-mobile-enrollment-support--1112863--"></a>Suporte do Knox Mobile Enrollment da Samsung<!--1112863-->
Ao utilizar o Intune com o Knox Mobile Enrollment (KME) da Samsung, pode inscrever um grande número de dispositivos Android da empresa. Os utilizadores em redes Wi-Fi ou redes móveis podem inscrever com apenas alguns toques os respetivos dispositivos quando os ligarem pela primeira vez. Ao utilizarem a Aplicação Knox Deployment, os dispositivos podem ser inscritos através de Bluetooth ou NFC. Para obter mais informações, consulte [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](../enrollment/android-samsung-knox-mobile-enroll.md) (Inscrever automaticamente dispositivos Android através do Knox Mobile Enrollment da Samsung).

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas 

#### <a name="requesting-help-in-the-company-portal-for-windows-10---1874137---"></a>Pedir ajuda no Portal da Empresa para o Windows 10<!-- 1874137 -->
O Portal da Empresa para Windows 10 irá agora enviar registos de aplicações diretamente para a Microsoft quando o utilizador iniciar o fluxo de trabalho para obter ajuda com um problema. Isto facilitará a resolução dos problemas colocados à Microsoft.

<!-- ########################## -->
## <a name="april-2018"></a>Abril de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Suporte de código de acesso para o PIN de MAM no Android<!-- 1438086 -->

Os administradores do Intune podem definir um requisito de execução da aplicação para impor um código de acesso em vez de um PIN numérico de MAM. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. O Intune suporta um código de acesso de forma semelhante ao PIN numérico existente, sendo capaz de definir um comprimento mínimo e de permitir sequências e carateres repetidos através da consola de administrador. Esta funcionalidade necessita da versão mais recente do Portal da Empresa no Android. Esta funcionalidade já se encontra disponível para iOS.

#### <a name="line-of-business-lob-app-support-for-macos---1473977---"></a>Suporte de aplicações de linha de negócio (LOB) para macOS<!-- 1473977 -->
O Microsoft Intune irá oferecer a capacidade de instalar aplicações LOB para macOS a partir do portal do Azure. Poderá adicionar uma aplicação LOB para macOS ao Intune depois de a mesma ter sido previamente processada pela ferramenta disponível no GitHub. No portal do Azure, selecione **Aplicações do cliente** no painel **Intune**. No painel **Aplicações do cliente**, selecione **Aplicações** > **Adicionar**. No painel **Adicionar Aplicação**, selecione **Aplicação de linha de negócio**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment---1813073---"></a>Grupos Todos os Utilizadores e Todos os Dispositivos incorporados para a atribuição de aplicações do perfil de trabalho do Android Enterprise<!-- 1813073 -->
Pode tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações de perfil de trabalho do Android Enterprise. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](../apps/apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users---1947010---"></a>O Intune reinstalará as aplicações exigidas que foram desinstaladas pelos utilizadores<!-- 1947010 -->
Se um utilizador final desinstalar uma aplicação necessária, o Intune reinstalará automaticamente a aplicação no prazo de 24 horas em vez de aguardar o ciclo de reavaliação de 7 dias.

#### <a name="update-where-to-configure-your-app-protection-policies---2144597---"></a>Atualização do local de configuração das políticas de proteção de aplicações<!-- 2144597 -->

No portal do Azure no serviço do Microsoft Intune, iremos redirecioná-lo temporariamente do painel do serviço **Proteção de Aplicações do Intune** para o painel **Aplicação móvel**. Tenha em atenção que todas as suas políticas de proteção de aplicações já se encontram no painel **Aplicação móvel** no Intune, em Configuração da aplicação. Em vez de aceder à Proteção de Aplicações do Intune, acederá simplesmente ao Intune. Em abril de 2018, iremos interromper o redirecionamento e remover completamente o painel do serviço **Proteção de Aplicações do Intune**, de modo a que só exista uma única localização para políticas de proteção de aplicações no Intune. 

**Como é que isto me afeta?**
Esta alteração afetará os clientes autónomos e os clientes híbridos (Intune com o Configuration Manager) do Intune. Esta integração irá ajudar a simplificar a sua administração da gestão da cloud.

**O que preciso de fazer para me preparar para esta alteração?**
Adicione o **Intune** como um favorito em vez do painel do serviço **Proteção de Aplicações do Intune** e certifique-se de que está familiarizado com o fluxo de trabalho da Política de proteção de aplicações no painel **Aplicação móvel** no Intune. Iremos redirecionar os utilizadores durante um breve período de tempo e, em seguida, remover o painel **Proteção de Aplicações**. Lembre-se de que todas as políticas de proteção de aplicativo já estão no Intune e você pode modificar qualquer uma das políticas de acesso condicional. Para obter mais informações sobre a modificação das políticas de acesso condicional, consulte [acesso condicional no Diretório Ativo do Azure.](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) Para obter informações adicionais, veja [O que são as políticas de proteção de aplicações?](../apps/app-protection-policy.md) 

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group---1449153---"></a>O gráfico do perfil de dispositivos e a lista de estados mostra todos os dispositivos num grupo<!-- 1449153 -->
Quando configurar um perfil de dispositivo (**Configuração do dispositivo** > **Perfis**), selecione o perfil de dispositivo que pretende, como iOS. Atribua este perfil a um grupo que inclua dispositivos iOS e dispositivos não iOS. A contagem do gráfico mostra que o perfil é aplicado a dispositivos iOS *e* não iOS (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**). Quando seleciona o gráfico no separador **Descrição Geral**, o **Estado do dispositivo** apresenta uma lista de todos os dispositivos no grupo, em vez de mostrar apenas os dispositivos iOS. 

Com esta atualização, o gráfico (**Configuração do dispositivo** > **Perfis** > selecione um perfil existente > **Descrição Geral**) mostra apenas a contagem do perfil do dispositivo específico. Por exemplo, se o perfil de configuração do dispositivo se aplicar a dispositivos iOS, o gráfico só apresentará a contagem de dispositivos iOS. Ao selecionar o gráfico e abrir o **Estado do dispositivo** só serão apresentados os dispositivos iOS.

Enquanto esta atualização estiver a ser efetuada, o gráfico de utilizadores será temporariamente removido. 

#### <a name="always-on-vpn-for-windows-10--1333666---"></a>Funcionalidade AlwaysOn através de VPN no Windows 10<!--1333666 -->

Atualmente, a funcionalidade [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) pode ser utilizada em dispositivos com o Windows 10 através da utilização de um perfil de rede privada virtual (VPN) personalizada criada com o OMA-URI.

Com esta atualização, os administradores podem ativar a funcionalidade AlwaysOn para perfis VPN do Windows 10 diretamente no Intune, no portal do Azure. Os perfis VPN AlwaysOn irão ligar automaticamente quando:

- Os utilizadores iniciarem sessão nos respetivos dispositivos
- A rede no dispositivo for alterada
- O ecrã do dispositivo se ligar novamente após o ter desligado

#### <a name="new-printer-settings-for-education-profiles---1308900---"></a>Novas definições de impressora para perfis de educação<!-- 1308900 -->

Para os perfis de educação, as novas definições estão disponíveis na categoria **Impressoras**: **Impressoras**, **Impressora predefinida**, **Adicionar novas impressoras**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile--1098984---"></a>Mostrar o ID do chamador no perfil pessoal – perfil de trabalho do Android Enterprise<!--1098984 -->
Quando utiliza um perfil pessoal num dispositivo, os utilizadores finais podem não ver os detalhes do ID do autor da chamada de um contacto de trabalho. 

Com esta atualização, existe uma nova definição em **Android Enterprise** > **Restrições do dispositivo** > **Definições do perfil de trabalho**:
- Apresentar o ID do autor da chamada do contacto de trabalho no perfil pessoal

Quando a opção está ativada (não configurada), os detalhes do autor da chamada do contacto de trabalho são apresentados no perfil pessoal. Quando a opção está bloqueada, o número do autor da chamada do contacto de trabalho não é apresentado no perfil pessoal. 

Aplica-se a: dispositivos de perfil de trabalho Android em Android OS v6.0 e mais recentes

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings--1102252-----from-1802-and-1804--"></a>Foram adicionadas novas definições do Windows Defender Credential Guard às definições de proteção de ponto final<!--1102252 --><!--from 1802 and 1804-->

Com esta atualização, o [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuração do dispositivo** > **Perfis** > **Proteção de ponto final**) inclui as seguintes definições: 

- **Windows Defender Credential Guard**: ativa o Credential Guard com a segurança baseada em virtualização. Se ativar esta funcionalidade, ajudará a proteger as credenciais no próximo reinício quando o **Nível de Segurança da Plataforma com o Arranque Seguro** e a **Segurança Baseada em Virtualização** estiverem ativados. As opções incluem:
  - **Desativado**: se o Credential Guard tiver sido ativado anteriormente com a opção “**Ativada sem bloqueio**”, desativa o Credential Guard remotamente.

  - **Ativada com bloqueio UEFI**: garante que o Credential Guard não pode ser desativado com a chave de registo ou através da utilização da Política de Grupo. Para desativar o Credential Guard depois de utilizar esta definição, tem de definir a Política de Grupo como “Desativada”. Em seguida, remova a funcionalidade de segurança de cada computador, com um utilizador fisicamente presente. Estes passos limpam a configuração persistente na UEFI. Enquanto a configuração da UEFI persistir, o Credential Guard estará ativado.

  - **Ativada sem bloqueio**: permite que o Credential Guard seja desativado remotamente através da utilização da Política de Grupo. Os dispositivos que utilizam esta definição têm de ter, pelo menos, o Windows 10 (Versão 1511).

As seguintes tecnologias dependentes são ativadas automaticamente ao configurar o Credential Guard: 

- **Ativar a Segurança baseada na Virtualização (VBS)** : ativa a segurança baseada na virtualização (VBS) no próximo reinício. A segurança baseada na virtualização utiliza o Windows Hypervisor para dar suporte aos serviços de segurança e requer o Arranque Seguro.
- **Reinício Seguro com o Acesso Direto à Memória (DMA)** : ativa a VBS com o Arranque Seguro e o acesso direto à memória. As proteções de DMA precisam de suporte de hardware e serão ativadas apenas em dispositivos configurados corretamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate---2064190---"></a>Utilizar um nome de requerente personalizado no certificado SCEP<!-- 2064190 -->
Poderá utilizar o nome comum **OnPremisesSamAccountName** num requerente personalizado num perfil de certificado SCEP. Por exemplo, pode utilizar `CN={OnPremisesSamAccountName})`.

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles---1098977---"></a>Bloquear a câmara e as capturas de ecrã em perfis de trabalho do Android Enterprise<!-- 1098977 -->
Estão disponíveis duas propriedades novas para o bloqueio ao configurar as restrições dos dispositivos Android: 
- Câmara: bloqueia o acesso a todas as câmaras do dispositivo
- Captura de ecrã: bloqueia a captura de ecrã e também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura

Aplica-se a perfis de trabalho do Android Enterprise.

#### <a name="use-cisco-anyconnect-client-for-ios---1333708---"></a>Utilizar o cliente Cisco AnyConnect para iOS<!-- 1333708 -->

Quando cria um novo perfil VPN para iOS, existem agora duas opções: **Cisco AnyConnect** e **Cisco Legacy AnyConnect**. Os perfis do Cisco AnyConnect suportam a versão 4.0.7x e versões mais recentes. Os perfis VPN existentes do Cisco AnyConnect para iOS são identificados como **Cisco Legacy AnyConnect** e continuarão a funcionar com a versão 4.0.5x e mais antigas do Cisco AnyConnect, tal como atualmente.

> [!NOTE]
> Esta alteração só se aplica ao iOS. Continua a existir apenas uma opção Cisco AnyConnect para as plataformas Android, perfis de trabalho do Android Enterprise e macOS.


### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132--1734567---"></a>Novos passos de inscrição para os utilizadores em dispositivos com o macOS High Sierra 10.13.2 ou superior<!--1734567 -->
O macOS High Sierra 10.13.2 introduziu um conceito de inscrição "Aprovado Pelo Utilizador" na MDM. As inscrições aprovadas permitem que o Intune faça a gestão de algumas definições relacionadas com a segurança. Para obter mais informações, veja a documentação de suporte da Apple aqui: https://support.apple.com/HT208019.

Os dispositivos inscritos através do Portal da Empresa do macOS são considerados “Não Aprovados Pelo Utilizador”, a menos que o utilizador final abra as Preferências do Sistema e conceda a aprovação manualmente. Para tal, o Portal da Empresa do macOS agora direciona os utilizadores no macOS 10.13.2 e superior para que acedam e aprovem manualmente a inscrição no final do processo de inscrição. A consola de administrador do Intune irá indicar se um dispositivo inscrito for aprovado pelo utilizador.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune---2370684---"></a>Os dispositivos macOS inscritos com Jamf podem agora registar-se no Intune<!-- 2370684 -->
As versões 1.3 e 1.4 do portal da empresa do macOS não conseguiam registar dispositivos com Jamf com o Intune. A versão 1.4.2 do portal do macOS corrige este problema.

#### <a name="updated-help-experience-in-company-portal-app-for-android---1631531---"></a>Experiência de ajuda atualizada na aplicação Portal da Empresa para Android<!-- 1631531 -->
Atualizámos a experiência de ajuda na aplicação Portal da Empresa para Android para estarmos alinhados com as melhores práticas para a plataforma Android. Agora, quando os utilizadores detetarem um problema na aplicação, podem tocar em **Menu** > **Ajuda** e:
- Carregar registos de diagnóstico para a Microsoft.
- Enviar um e-mail a descrever o problema e o ID do incidente para um membro da equipa de suporte da empresa.  

Para experimentar a experiência de ajuda atualizada, aceda a [Enviar registos por e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) e [Enviar erros para a Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table---1471783---"></a>Novo gráfico de tendências de falhas e tabela de motivos de falhas em inscrições<!-- 1471783 -->
Na página Descrição Geral de Inscrições, pode ver as tendências de falhas de inscrições e as cinco principais causas de falhas. Ao clicar no gráfico ou na tabela, pode pormenorizar os detalhes para encontrar conselhos de resolução de problemas e sugestões de remediação.


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated---1629303---"></a>A Advanced Threat Protection (ATP) e o Intune estão totalmente integrados<!-- 1629303 -->

A [Proteção Avançada Contra Ameaças (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) mostra o nível de risco dos dispositivos com o Windows 10. No Centro de Segurança do Windows Defender (portal ATP), pode criar uma ligação para o Microsoft Intune. Depois de a criar, uma política de conformidade do Intune serve para determinar um nível de ameaça aceitável. Se o nível de ameaça for excedido, uma política de acesso condicional Azure Active Directory (AD) poderá bloquear o acesso a diferentes aplicativos em sua organização.

Esta funcionalidade permite ao ATP analisar ficheiros, detetar ameaças e reportar qualquer risco nos dispositivos Windows 10.

Consulte [o ATP habilitar com acesso condicional em Intune](../protect/advanced-threat-protection.md).

#### <a name="support-for-user-less-devices---1637553---"></a>Suporte para dispositivos sem utilizador<!-- 1637553 -->
O Intune permite avaliar a conformidade num dispositivo sem utilizadores, tal como o Microsoft Surface Hub. A política de conformidade pode ser aplicada a dispositivos específicos. Portanto, a conformidade e não conformidade podem ser determinadas para dispositivos que não tenham um utilizador associado.

#### <a name="delete-autopilot-devices---1713650---"></a>Eliminar dispositivos Autopilot<!-- 1713650 -->
Os administradores do Intune podem [eliminar dispositivos Autopilot](../enrollment/enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience--1832333---"></a>Experiência de eliminação de dispositivos melhorada<!--1832333 -->
Já não será obrigado a remover os dados da empresa ou a fazer uma reposição de fábrica do dispositivo antes de [eliminar um dispositivo do Intune](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal).

Para ver a nova experiência, inicie sessão no Intune e selecione **Dispositivos** > **Todos os Dispositivos** > o nome do dispositivo > **Eliminar**.

Se quiser continuar com a confirmação de eliminação/extinção, pode utilizar a rota de ciclo de vida do dispositivo padrão ao executar a opção **Remover dados da empresa** e **Reposição de Fábrica** antes de **Eliminar**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode---1947769---"></a>Reproduzir sons no iOS quando está no Modo perdido<!-- 1947769 -->
Quando os dispositivos iOS supervisionados estiverem no [Modo perdido](../remote-actions/device-lost-mode.md) na Gestão de Dispositivos Móveis (MDM), poderá [reproduzir um som](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivos** > **Todos os Dispositivos** > selecione um dispositivo iOS > **Descrição Geral** > **Mais**). O som continuará a ser reproduzido até que o dispositivo seja removido do Modo perdido ou que um utilizador desative o som no dispositivo. Aplica-se aos dispositivos iOS 9.3 e mais recentes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device--1972804--"></a>Bloquear ou permitir resultados da Web em pesquisas realizadas num dispositivo Intune<!--1972804-->

Os administradores podem agora bloquear resultados da Web em pesquisas realizadas num dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure---2172331---"></a>Mensagens de erro melhoradas para a falha de carregamento do Certificado Push de MDM da Apple<!-- 2172331 -->

A mensagem de erro explica que tem de utilizar o mesmo ID Apple ao renovar um certificado de MDM existente.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines---2216679---"></a>Testar o Portal da Empresa para macOS em máquinas virtuais<!-- 2216679 -->

Publicamos orientações para ajudar os administradores de TI a testar a aplicação Portal da Empresa para macOS em máquinas virtuais no Parallels Desktop e na VMware Fusion. Saiba mais em [Inscrever máquinas virtuais macOS para teste](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios--1412866---"></a>Atualização da experiência de utilizador da aplicação Portal da Empresa para iOS<!--1412866 -->
Lançámos uma atualização importante da experiência de utilizador para a aplicação Portal da Empresa para iOS. A atualização consiste numa reestruturação visual completa que inclui um aspeto e funcionalidade mais modernos. Mantivemos a funcionalidade da aplicação, mas aumentámos a facilidade de utilização e acessibilidade da mesma.  

A atualização inclui ainda:
- Suporte para iPhone X.
- Respostas de início e carregamento de aplicações mais rápidas, que poupam tempo aos utilizadores.
- Barras de progresso adicionais que mostram as informações de estado mais recentes aos utilizadores.
- Melhorias à forma como os utilizadores carregam os registos, para facilitar o envio de relatórios em caso de falha.  

Para ver a versão atualizada, aceda a [Novidades na IU da aplicação](../whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca---1056954---"></a>Proteger dados do Exchange no local com a APP e o AC do Intune<!-- 1056954 -->
Agora pode utilizar a Política de Proteção de Aplicações (APP) e o Acesso Condicional (AC) do Intune para proteger o acesso a dados do Exchange no local com o Outlook Mobile. Para adicionar ou modificar uma política de proteção de aplicações no portal do Azure, selecione **Microsoft Intune** > **Aplicações do cliente** > **Políticas de proteção de aplicações**. Antes de utilizar esta funcionalidade, certifique-se de que cumpre os [requisitos do Outlook para iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx).


### <a name="user-interface"></a>Interface de utilizador

#### <a name="improved-device-tiles-in-the-windows-10-company-portal--2213364---"></a>Mosaicos de dispositivos melhorados no Portal da Empresa do Windows 10<!--2213364 -->

Os mosaicos foram atualizados para serem mais acessíveis a utilizadores de visão reduzida e para terem um melhor desempenho nas ferramentas de leitura de ecrãs.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos---2216677---"></a>Enviar relatórios de diagnóstico na aplicação Portal da Empresa para macOS<!-- 2216677 -->
A aplicação do Portal da Empresa para dispositivos macOS foi atualizada para melhorar a forma como os utilizadores comunicam erros relacionados com o Intune. Na aplicação Portal da Empresa, os funcionários podem:

- Carregar os relatórios de diagnóstico diretamente para a equipa de programadores da Microsoft.
- Enviar o ID do incidente por e-mail para a equipa de suporte de TI da sua empresa.

Para obter mais informações, veja [Enviar erros do macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10---1195010---"></a>O Intune adapta-se ao Fluent Design System na aplicação Portal da Empresa para Windows 10<!-- 1195010 -->
A aplicação Portal da Empresa do Intune para Windows 10 foi atualizada com a [vista de navegação do Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Na parte lateral da aplicação, verá uma lista vertical estática de todas as páginas de nível superior. Clique em qualquer ligação para ver e alternar entre páginas rapidamente. Esta é a primeira de várias atualizações que verá como parte do nosso esforço contínuo para criar uma experiência mais adaptável, agradável e familiar no Intune. Para ver a versão atualizada, aceda a [Novidades na IU da aplicação](../whats-new-app-ui.md).

<!-- ########################## -->
## <a name="march-2018"></a>Março de 2018

### <a name="app-management"></a>Gestão de aplicações

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune---748789---"></a>Alertas de aplicações de linha de negócio (LOB) de iOS prestes a expirar no Microsoft Intune<!-- 748789 -->

No portal do Azure, o Intune irá alertá-lo para as aplicações de linha de negócio do iOS que estão prestes a expirar. Após o carregamento de uma nova versão da aplicação de linha de negócio do iOS, o Intune remove a notificação de expiração da lista de aplicações. Esta notificação de expiração só estará ativa para as aplicações de linha de negócio do iOS carregadas recentemente. Será apresentado um aviso 30 dias antes de o perfil de aprovisionamento de aplicações LOB do iOS expirar. Quando o perfil expirar, o estado do alerta será alterado para Expirado.

#### <a name="customize-your-company-portal-themes-with-hex-codes--1049561---"></a>Personalizar os temas do Portal da Empresa com códigos hexadecimais<!--1049561 -->

Pode personalizar a cor do tema nas aplicações do Portal da Empresa com códigos hexadecimais. Ao introduzir o seu código hexadecimal, o Intune determina a cor do texto que fornece o maior nível de contraste entre a cor do texto e a cor de fundo. Pode pré-visualizar a cor do texto e o logótipo da empresa relativamente à cor em **Aplicações do cliente** > **Portal da Empresa**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise---1813081---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos do Android Enterprise<!-- 1813081 -->

O Android Enterprise (anteriormente conhecido como Android for Work) suporta incluir e excluir grupos, mas não suporta os grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados. Para obter mais informações, veja [Incluir e excluir atribuições de aplicações no Microsoft Intune](../apps/apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestão de dispositivos

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome---2258071---"></a>Exportar todos os dispositivos para ficheiros CSV no IE, Microsoft Edge ou Chrome<!-- 2258071 -->
Em **Dispositivos** > **Todos os dispositivos**, pode **Exportar** os dispositivos para uma lista com formatação CSV. Os utilizadores do Internet Explorer (IE) com mais de 10 000 dispositivos podem exportar os seus dispositivos com êxito para múltiplos ficheiros. Cada ficheiro contém um máximo de 10 000 dispositivos.

Os utilizadores do Microsoft Edge e do Chrome com mais de 30 000 dispositivos podem exportar os dispositivos com êxito para vários ficheiros. Cada ficheiro contém um máximo de 30 000 dispositivos.

O artigo [Gerir dispositivos](../remote-actions/device-management.md) fornece mais detalhes sobre o que pode fazer com os dispositivos que gere.

#### <a name="new-security-enhancements-in-the-intune-service----1637539---"></a>Novas melhorias de segurança no serviço do Intune <!-- 1637539 -->   

Introduzimos um botão no Intune no Azure que os clientes do Intune autónomo podem utilizar para marcar dispositivos sem qualquer política atribuída como **Compatível** (a funcionalidade de segurança fica desativada) ou como **Não compatível** (a funcionalidade de segurança fica ativada). Isto garante que os recursos só podem ser acedidos após a avaliação da conformidade do dispositivo.

A forma como esta funcionalidade o afeta varia consoante existam ou não políticas de conformidade atribuídas.

- Se tiver uma conta nova ou existente e não tiver políticas de conformidade atribuídas aos seus dispositivos, o botão estará automaticamente definido para **Compatível**. A funcionalidade está desativada por predefinição na consola. O utilizador final não é afetado.
- Se tiver uma conta existente e tiver dispositivos com políticas de conformidade atribuídas, o botão estará automaticamente definido para **Não compatível**. A funcionalidade estará ativada por predefinição quando a atualização de março for implementada.

Se utilizar políticas de conformidade com Acesso Condicional (AC) e tiver a funcionalidade ativada, os dispositivos sem pelo menos uma política de conformidade atribuída serão bloqueados pela AC. Os utilizadores finais associados a estes dispositivos, que tinham anteriormente permissão de acesso ao e-mail, perderão o acesso a menos que atribua pelo menos uma política de conformidade a todos os dispositivos.   

Tenha em atenção que, embora o estado predefinido do botão seja logo apresentado na IU com as atualizações do serviço do Intune de março, este estado não será imposto de imediato. As alterações que fizer ao botão não afetarão a conformidade do dispositivo até que implementemos um botão funcional na sua conta. Informá-lo-emos através do Centro de Mensagens quando terminarmos a implementação na sua conta. Este processo poderá demorar alguns dias após as atualizações de março terem sido aplicadas ao seu serviço do Intune.

**Informações Adicionais**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection---846515---"></a>Deteção de jailbreak melhorada<!-- 846515 -->

A deteção de jailbreak avançada é uma nova definição de conformidade que melhora a forma como o Intune avalia os dispositivos com jailbreak. A definição faz com que o dispositivo se ligue ao Intune com mais frequência, o que resulta na utilização dos serviços de localização e afeta a duração da bateria.

#### <a name="reset-passwords-for-android-o-devices---1238299---"></a>Repor palavras-passe de dispositivos Android O<!-- 1238299 -->
Poderá repor as palavras-passe de dispositivos com o Android 8.0 inscritos com perfis de trabalho. Quando envia um pedido "Repor palavra-passe" para um dispositivo com o Android 8.0, este define uma nova palavra-passe de desbloqueio de dispositivo ou um desafio de perfil gerido para o utilizador atual. A palavra-passe ou desafio é enviado e entra imediatamente em vigor.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups--1307012---"></a>Filtrar políticas de conformidade para os dispositivos nos grupos de dispositivos<!--1307012 -->

Pode direcionar as políticas de conformidade de destino para utilizadores em grupos de utilizadores. Com esta atualização, pode filtrar políticas de conformidade para os dispositivos nos grupos de dispositivos. Os dispositivos filtrados como parte de grupos de dispositivos não serão contemplados por ações de conformidade.

#### <a name="new-management-name-column---1333586---"></a>Nova coluna Nome de gestão<!-- 1333586 -->
 Está disponível uma nova coluna denominada **Nome de gestão** no painel de dispositivos. Trata-se de um nome gerado automaticamente, não editável e atribuído por dispositivo com base na seguinte fórmula:
- Nome predefinido para todos os dispositivos: <username><em><devicetype></em><enrollmenttimestamp>
- Para dispositivos adicionados em massa: <IDDoPacote/IDDoPerfil><em><DeviceType></em><EnrollmentTime>

Esta é uma coluna opcional no painel de dispositivos. Esta não está disponível por predefinição e só pode aceder-lhe através do seletor de colunas. O nome do dispositivo não é afetado por esta nova coluna.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes--1550837---"></a>Os dispositivos iOS recebem um pedido de PIN a cada 15 minutos<!--1550837 -->
Após ser aplicada uma política de conformidade ou de configuração para um dispositivo iOS, os utilizadores recebem um pedido de PIN a cada 15 minutos. Os utilizadores continuam a receber pedidos até que seja definido um PIN.

#### <a name="schedule-your-automatic-updates--1805514---"></a>Agendar as atualizações automáticas<!--1805514 -->
O Intune dá-lhe controlo sobre quando instalar as atualizações automáticas com as [definições da Cadência de Atualizações do Windows](../protect/windows-update-for-business-configure.md). Com esta atualização, pode agendar atualizações recorrentes, incluindo a semana, o dia e a hora das mesmas.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate--2221763---"></a>Utilizar um nome único completo como nome do requerente num certificado SCEP<!--2221763 -->
Quando cria um perfil de certificado SCEP, tem de introduzir um Nome do Requerente. Com esta atualização, pode utilizar um nome único completo como nome do requerente. Para **Nome do Requerente**, selecione **Personalizado** e, em seguida, escreva `CN={{OnPrem_Distinguished_Name}}`. Para utilizar a variável `{{OnPrem_Distinguished_Name}}`, certifique-se de que sincroniza o atributo de utilizador `onpremisesdistingishedname` com o [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) com o seu Azure AD.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="enable-bluetooth-contact-sharing---android-for-work--1098983---"></a>Permitir a partilha de contactos através de Bluetooth – Android for Work<!--1098983 -->
Por predefinição, o Android impede que os contactos do perfil de trabalho sincronizem com dispositivos Bluetooth. Como resultado, os contactos do perfil de trabalho não são apresentados no ID do autor da chamada em dispositivos Bluetooth.

Com esta atualização, existe uma nova definição em **Android for Work** > **Restrições do dispositivo** > **Definições do perfil de trabalho**:
- Partilha de contactos através de Bluetooth

O administrador do Intune pode configurar estas definições para permitir a partilha. É um procedimento útil para emparelhar um dispositivo com outro dispositivo Bluetooth utilizado em automóveis que apresente o ID do autor da chamada e permita uma utilização mãos-livres. Quando ativada, os contactos do perfil de trabalho são apresentados. Quando desativada, os contactos do perfil de trabalho não são apresentados.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source---1690459---"></a>Configurar o Controlador de Chamadas para controlar a origem de transferência da aplicação para macOS<!-- 1690459 -->

Pode configurar o Controlador de Chamadas para proteger os seus dispositivos das aplicações ao controlar os locais donde as aplicações podem ser transferidas. Pode configurar as seguintes origens de transferência: **Mac App Store**, **Mac App Store e programadores identificados** ou **Em qualquer lado**. Pode configurar a possibilidade de os utilizadores instalarem uma aplicação ao manterem a tecla Ctrl premida e clicarem para ignorar estes controlos do Controlador de Chamadas.

Estas definições podem ser encontradas em **Configuração do dispositivo** -> **Criar perfil** -> **macOS** -> **Proteção de ponto final**.

#### <a name="configure-the-mac-application-firewall---1690461---"></a>Configurar a firewall da aplicação para Mac<!-- 1690461 -->

Pode configurar a firewall da aplicação para Mac. Pode utilizar esta opção para controlar as ligações por aplicação em vez de por porta. Desta forma, é mais fácil beneficiar da proteção da firewall e contribuir para impedir que aplicações indesejáveis controlem portas de rede abertas para aplicações legítimas.

Esta funcionalidade encontra-se em **Configuração do dispositivo** -> **Criar perfil** -> **macOS** -> **Proteção de ponto final**.

Depois de ativar a definição da Firewall, pode configurar a firewall através de duas estratégias:

- Bloquear todas as ligações a receber

   Pode bloquear todas as ligações a receber para os dispositivos direcionados. Se optar por fazê-lo, as ligações a receber serão bloqueadas para todas as aplicações.

- Permitir ou bloquear aplicações específicas

   Pode permitir ou bloquear a receção de ligações a receber provenientes de aplicações específicas. Também pode ativar o modo furtivo para impedir respostas a pedidos de pesquisa.

#### <a name="detailed-error-codes-and-messages---1376342---"></a>Mensagens e códigos de erro detalhados<!-- 1376342 -->

Na Configuração do Dispositivo, poderá ver mensagens e códigos de erro mais detalhados. Este relatório melhorado mostra as definições, o estado destas definições e os detalhes sobre como resolver problemas.

##### <a name="more-information"></a>Mais informações

- Bloquear todas as ligações a receber

   Permite bloquear a receção de ligações a receber por parte de todos os serviços de partilha (tal como a Partilha de Ficheiros e a Partilha de Ecrãs). Os serviços do sistema que continuam a ter permissão para a receção de ligações a receber são:
  - configd – implementa o protocolo DHCP e outros serviços de configuração de rede
  - mDNSResponder – implementa Bonjour
  - Racoon-implementa IPSec

    Para utilizar os serviços de partilha, certifique-se de que a opção **Ligações a receber** está definida como **Não configurada** (e não como **Bloquear**).

- Modo furtivo

   Ative esta opção para impedir que o computador responda aos pedidos de pesquisa. O computador continua a responder a pedidos recebidos de aplicações autorizadas. São ignorados pedidos inesperados, tais como o protocolo ICMP (ping).

#### <a name="disable-checks-on-device-restart--1805490---"></a>Desativar as verificações no reinício do dispositivo<!--1805490 -->
O Intune dá-lhe o controlo para [gerir as atualizações de software](../protect/windows-update-for-business-configure.md). Com esta atualização, a propriedade <strong>Verificações de reinício</strong> está disponível e ativada por predefinição. Para ignorar as verificações habituais que ocorrem ao reiniciar um dispositivo (como as verificações de utilizadores ativos, níveis de bateria, entre outras), selecione <strong>Ignorar</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings---1746293---"></a>Novos canais do Windows 10 Insider Preview disponíveis para cadências de implementação<!-- 1746293 -->
Agora pode selecionar os seguintes canais de serviço do Windows 10 Insider Preview ao criar uma cadência de implementação do Windows 10:
- Compilação do Windows Insider - Rápida
- Compilação do Windows Insider - Lenta
- Versão da compilação do Windows Insider 

Para obter mais informações sobre estes canais, veja [Manage Insider Preview Builds](https://insider.windows.com/for-business-organization-admin/) (Gerir Compilações do Insider Preview).   
Para obter mais informações sobre a criação de canais de implementação no Intune, veja [Gerir atualizações de software no Intune](../protect/windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings---1631893---"></a>Novas definições do Windows Defender Exploit Guard<!-- 1631893 -->

Estão agora disponíveis seis novas definições de <strong>Redução da Superfície de Ataque</strong> e funcionalidades expandidas de <strong>Acesso a pastas controladas: proteção de pastas</strong>. Estas definições encontram-se em: Configuração do dispositivo\Perfis\
Criar perfil\Proteção de ponto final\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque

|Nome da definição  |Opções da definição  |Description  |
|---------|---------|---------|
|Proteção de ransomware avançada|Ativado, Auditar, Não configurado|Utilize proteção contra ransomware intensiva.|
|Sinalizar o roubo de credenciais do subsistema de autoridade de segurança local do Windows|Ativado, Auditar, Não configurado|Sinalize o roubo de credenciais do subsistema de autoridade de segurança local do Windows (Lsass.exe).|
|Criação de processos com os comandos PsExec e WMI|Bloquear, Auditar, Não configurado|Bloqueie a criação de processos provenientes de comandos PsExec e WMI.|
|Processos não fidedignos e não assinados executados a partir de USB|Bloquear, Auditar, Não configurado|Bloqueie processos não fidedignos e não assinados executados a partir de USB.|
|Ficheiros executáveis que não cumprem uma lista de critérios de prevalência, idade ou fidedignidade|Bloquear, Auditar, Não configurado|Impeça ficheiros executáveis de serem executados a menos que cumpram uma lista de critérios de prevalência, idade ou fidedignidade.|

#### <a name="controlled-folder-access"></a>Acesso a pastas controladas

|              Nome da definição               |                                                              Opções da definição                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Proteção de pastas (já implementada) | Não configurado, Ativar, Apenas auditoria (já implementada)<br><br> <strong>Novidade</strong><br>Bloquear modificação do disco, Auditar modificação do disco |             |

Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.<br><br>**Ativar**: impede que aplicações não fidedignas modifiquem ou eliminem ficheiros em pastas protegidas e escrevam em setores do disco.<br><br>
**Bloquear apenas a modificação do disco**:<br>Impeça que aplicações não fidedignas escrevam em setores do disco. As aplicações não fidedignas continuam a poder modificar ou eliminar ficheiros em pastas protegidas.|

### <a name="intune-apps"></a>Aplicações do Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview---710595---"></a>Os sites do Azure Active Directory podem exigir a aplicação Intune Managed Browser e o suporte do Início de Sessão Único do Managed Browser (Pré-visualização Pública)<!-- 710595 -->

Com o Azure Active Directory (Azure AD), pode restringir o acesso a sites em dispositivos móveis na aplicação Intune Managed Browser. No Managed Browser, os dados dos sites permanecerão protegidos e separados dos dados pessoais dos utilizadores finais. Além disso, o Managed Browser suporta as funcionalidades de Início de Sessão Único para sites protegidos pelo Azure AD. Iniciar sessão no Managed Browser ou utilizá-lo num dispositivo com outra aplicação gerida pelo Intune permite que o Managed Browser aceda a sites empresariais protegidos pelo Azure AD sem que o utilizador tenha de introduzir as suas credenciais. Esta funcionalidade aplica-se a sites como o Outlook Web Access (OWA) e o SharePoint Online, bem como a outros sites empresariais como recursos de intranet acedidos através do Proxy de Aplicações do Azure. Para obter informações adicionais, consulte os controlos de acesso no Acesso Condicional do [Diretório Ativo azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates--976944---"></a>Atualizações visuais da aplicação Portal da Empresa para Android<!--976944 -->

Atualizámos a aplicação Portal da Empresa para Android para seguir as diretrizes de [Conceção do Material](https://material.io/) do Android. Pode ver as imagens dos novos ícones no artigo [Novidades na IU da aplicação](../whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved---1874230-eeready--"></a>Registo no Portal da Empresa melhorado<!-- 1874230 eeready-->
Os utilizadores que inscreverem um dispositivo através do Portal da Empresa com a compilação 1703 e posteriores do Windows 10 poderão concluir o primeiro passo de inscrição sem sair da aplicação.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists--1725868---"></a>O HoloLens e o Surface Hub são agora apresentados nas listas de dispositivos<!--1725868 -->
Incluímos suporte adicional para mostrar dispositivos HoloLens e SurfaceHub inscritos no Intune na aplicação Portal da Empresa para Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks---1488911---"></a>Personalizar as categorias Livros para eBooks do Volume Purchase Program (VPP)<!-- 1488911 -->
Pode criar categorias de eBook personalizadas e depois atribuir eBooks do VPP a essas categorias. Os utilizadores finais podem depois ver as categorias de eBook recentemente criadas e os livros atribuídos às categorias. Para obter mais informações, veja [Gerir aplicações e livros comprados em grandes volumes com o Microsoft Intune](../apps/vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option---2070166---"></a>Alterações ao suporte da opção Enviar Feedback na aplicação Portal da Empresa para Windows<!-- 2070166 -->
A partir de 30 de abril de 2018, a opção **Enviar Feedback** na aplicação Portal da Empresa para Windows funcionará apenas em dispositivos com a Atualização de Aniversário do Windows 10 (1607) e versões posteriores. A opção para enviar feedback já não é suportada ao utilizar a aplicação Portal da Empresa para Windows com a:  
- Versão 1507 do Windows 10  
- Versão 1511 do Windows 10  
- Wnodows Phone 8.1 

Se o seu dispositivo estiver a executar o Windows 10 RS1 ou posterior, transfira a versão mais recente da aplicação Portal da Empresa para Windows a partir da Store. Se estiver a executar uma versão não suportada, continue a enviar feedback através dos seguintes canais: 
- Aplicação Hub de Comentários no Windows 10
- E-mail (WinCPfeedback@microsoft.com)  

#### <a name="new-windows-defender-application-guard-settings---1631890---"></a>Novas definições do Windows Defender Application Guard<!-- 1631890 -->

- **Ativar a aceleração de gráficos**: os administradores podem ativar um processador de gráficos virtual para o Windows Defender Application Guard. Esta definição permite que o CPU descarregue a composição dos gráficos para o vGPU. Isto pode melhorar o desempenho ao trabalhar com sites de gráficos intensos ou ao ver um vídeo no contentor.

- **SaveFilestoHost**: os administradores podem permitir que os ficheiros passem do Microsoft Edge a ser executado no contentor para o sistema de ficheiros anfitrião. Ativar esta definição permite que os utilizadores transfiram ficheiros do Microsoft Edge no contentor para o sistema de ficheiros anfitrião.

#### <a name="mam-protection-policies-targeted-based-on-management-state---1665993---"></a>Políticas de proteção MAM filtradas com base no estado de gestão<!-- 1665993 -->
Pode direcionar políticas MAM com base no estado de gestão do dispositivo:
- **Dispositivos Android** – pode abranger dispositivos não geridos, dispositivos geridos pelo Intune e perfis do Android Enterprise (anteriormente Android for Work) geridos pelo Intune.
- **Dispositivos iOS** – pode abranger dispositivos não geridos (apenas MAM) ou dispositivos geridos pelo Intune.

    > [!NOTE]
    > - O suporte para esta funcionalidade em dispositivos iOS será implementado ao longo de abril de 2018.

Para obter mais informações, veja [Direcionar políticas de proteção de aplicações com base no estado de gestão do dispositivo](../apps/app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows---1683758---"></a>Melhorias à linguagem na aplicação Portal da Empresa para Windows<!-- 1683758 -->
Melhorámos a linguagem no Portal da Empresa para Windows 10 de forma a torná-lo mais fácil de utilizar e adequado à sua empresa. Para ver algumas imagens de exemplo das alterações que fizemos, veja as [novidades na IU da aplicação](../whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy---1440709---"></a>Novas adições aos nossos documentos sobre a privacidade dos utilizadores<!-- 1440709 -->
Como parte do nosso compromisso em dar maior controlo aos utilizadores finais sobre os respetivos dados e privacidade, publicámos atualizações nos nossos documentos que explicam como ver e remover dados armazenados localmente pelas aplicações do Portal da Empresa. Pode encontrar estas atualizações em:

- **Android**: [How to remove your Android device from Intune (Como remover o seu dispositivo Android do Intune)](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, se o utilizador tiver recusado os termos de utilização**: [Remove your device management if you declined "Terms of Use" (Remover a sua gestão de dispositivos se tiver rejeitado os "Termos de Utilização")](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [Remove your iOS device from Intune (Remover o seu dispositivo iOS do Intune)](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Remove your Windows device from Intune (Remover o seu dispositivo Windows do Intune)](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>Fevereiro de 2018

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager<!-- 747685 -->

O Intune agora suporta a inscrição de dispositivos com até 100 contas diferentes do [Programa de Inscrição de Dispositivos (DEP) da Apple](../enrollment/device-enrollment-program-enroll-ios.md) ou do [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md). Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

#### <a name="see-enrollment-restrictions-per-user---1634444-eeready-wnready---"></a>Ver restrições de inscrição por utilizador<!-- 1634444 eeready wnready -->
No painel **Resolução de problemas**, pode agora ver as [restrições de inscrição](../enrollment/enrollment-restrictions-set.md) de cada utilizador ao selecionar **Restrições de inscrição** na lista **Atribuições**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment---747625-eeready---"></a>Nova opção para a autenticação do utilizador na inscrição em massa da Apple<!-- 747625 eeready -->

> [!NOTE]
> Os novos inquilinos veem esta opção de imediato. Para inquilinos existentes, esta funcionalidade será implementada durante o mês de abril. Até esta implementação estar concluída, poderá não ter acesso a estas novas funcionalidades.

O Intune agora dá-lhe a opção de autenticar dispositivos através da aplicação Portal da Empresa para os seguintes métodos de inscrição:

- Programa de Inscrição de Dispositivos Apple
- Gestor Escolar da Apple
- Inscrição no Apple Configurator

Ao utilizar a opção do Portal da Empresa, a autenticação multifator do Azure Active Directory pode ser imposta sem bloquear estes métodos de inscrição.

Quando utilizar a opção do Portal da empresa, o Intune ignora a autenticação do utilizador no Assistente de Configuração iOS para a inscrição de afinidade do utilizador. Tal significa que o dispositivo está inscrito inicialmente como um dispositivo sem utilizador e, como tal, não receberá configurações ou políticas de grupos de utilizadores. Só recebe configurações e políticas de grupos de dispositivos. No entanto, o Intune instalará automaticamente a aplicação Portal da Empresa no Dispositivo. O primeiro utilizador a abrir e a iniciar sessão na aplicação Portal da Empresa será associado ao dispositivo no Intune. Neste momento, o utilizador receberá configurações e políticas dos grupos de utilizadores. A associação do utilizador não pode ser alterada sem a reinscrição.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685-eeready---"></a>Suporte do Intune para várias contas do DEP da Apple/Apple School Manager<!-- 747685 eeready -->

O Intune agora suporta a inscrição de dispositivos com até 100 contas diferentes do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple School Manager. Cada token carregado pode ser gerido separadamente para dispositivos e perfis de inscrição. Um perfil de inscrição diferente pode ser automaticamente atribuído por token do DEP/School Manager carregado. Se forem carregados vários tokens do School Manager, só um poderá ser partilhado com a School Data Sync da Microsoft de cada vez.

Após a migração, as Graph APIs beta e os scripts publicados para gerir o DEP da Apple ou o ASM através do Graph deixarão de funcionar. Estão em desenvolvimento novas Graph APIs beta e serão lançadas após a migração.

### <a name="remote-printing-over-a-secure-network---1709994----"></a>Impressão remota através de uma rede segura<!-- 1709994  -->
As soluções de impressão móveis sem fios da PrinterOn irão permitir aos utilizadores imprimir remotamente a partir de qualquer lugar e em qualquer altura através de uma rede segura. A PrinterOn será integrada com o SDK da Aplicação Intune para iOS e Android. Conseguirá filtrar políticas de proteção de aplicações para esta aplicação através do painel **Políticas de proteção de aplicações** do Intune na consola de administração. Os utilizadores finais conseguirão transferir a aplicação “PrinterOn para Microsoft” através da Play Store ou do iTunes para utilizar no seu ecossistema do Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager---1352411---"></a>Suporte do Portal da Empresa do macOS para inscrições que utilizam o Gestor de Inscrições de Dispositivos<!-- 1352411 -->

Os utilizadores agora podem utilizar o Gestor de Inscrições de Dispositivos ao inscrever-se no Portal da Empresa do macOS.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="windows-defender-health-status-and-threat-status-reports--854704---"></a>Relatórios de estado da ameaça e estado de funcionamento do Windows Defender<!--854704 -->

Compreender o funcionamento e o estado do Windows Defender é fundamental para gerir PCs Windows.  Com esta atualização, o Intune adiciona novos relatórios e ações ao estado e estado de funcionamento do agente Windows Defender. Através de um relatório geral do estado na [carga de trabalho de Conformidade do Dispositivo](../protect/compliance-policy-monitor.md), pode ver os dispositivos que necessitam de:
- atualização de assinatura
- Reiniciar
- intervenção manual
- análise completa
- outros estados de agente a precisar de intervenção

Um relatório de agregação para cada categoria de estado indica os PCs individuais que precisam de atenção ou os que estão registados como **Limpar**.

#### <a name="new-privacy-settings-for-device-restrictions--1308926---"></a>Novas definições de privacidade para as restrições do dispositivo<!--1308926 -->
Estão agora disponíveis [duas novas definições de privacidade](../configuration/device-restrictions-windows-10.md#privacy) para os dispositivos:
- **Publicar as atividades do utilizador**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas.
- **Apenas atividades locais**: defina esta opção para **Bloquear** para impedir que as experiências e a deteção de recursos utilizados recentemente sejam partilhadas no comutador de tarefas com base na atividade local.

#### <a name="new-settings-for-the-microsoft-edge-browser--1469166---"></a>Novas definições no browser Microsoft Edge<!--1469166 -->
Estão agora disponíveis [duas novas definições](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser) de privacidade para os dispositivos com o browser Microsoft Edge: **Caminho para o ficheiro de favoritos** e **Alterações aos Favoritos**.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="protocol-exceptions-for-applications--1035509---"></a>Exceções do protocolo para determinadas aplicações<!--1035509 -->

Agora pode criar exceções para a política de transferência de dados da Gestão de Aplicações Móveis (MAM) do Intune para abrir determinadas aplicações não geridas. Estas aplicações têm de ser consideradas fidedignas pelas TI. Além das exceções que criar, a transferência de dados ainda será restrita a aplicações geridas pelo Intune quando a sua política de transferência de dados estiver definida para **apenas aplicações geridas**. Pode criar as restrições ao utilizar protocolos (iOS) ou pacotes (Android).

Por exemplo, pode adicionar o pacote WebEx como uma exceção à política de transferência de dados da MAM. Isto permite que as ligações WebEx numa mensagem de e-mail do Outlook gerido sejam abertas diretamente na aplicação WebEx. A transferência de dados será restrita noutras aplicações não geridas. Para obter mais informações, veja [Data transfer policy exceptions for apps](../apps/app-protection-policies-exception.md) (Exceções da política de transferência de dados).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results---1469193---"></a>Dados encriptados da Windows Information Protection (WIP) nos resultados da pesquisa do Windows<!-- 1469193 -->
Uma definição na política do Windows Information Protection (WIP) agora permite-lhe controlar se os dados encriptados pelo WIP são incluídos nos resultados da pesquisa do Windows. Pode definir esta opção de política de proteção de aplicações ao selecionar **Permitir que o Indexador do Windows Search procure itens encriptados** nas **Definições avançadas** da política do Windows Information Protection. A política de proteção de aplicações tem de ser definida para a plataforma do *Windows 10* e a política de aplicação **Estado da inscrição** tem de ser definida para **Com inscrição**. Para obter mais informações, veja [Permitir que o Indexador do Windows Search procure itens encriptados](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app---1740840---"></a>Configurar uma aplicação móvel MSI de atualização automática<!-- 1740840 -->
Pode configurar uma aplicação MSI móvel de atualização automática conhecida para ignorar o processo de verificação da versão. Esta funcionalidade é útil para evitar que ocorra uma condição race. Por exemplo, este tipo de condição race poderia ocorrer quando a aplicação de atualização automática por parte do programador também é atualizada pelo Intune. Ambos podem tentar impor uma versão da aplicação no cliente Windows, o que pode criar um conflito. Para estas aplicações MSI atualizadas automaticamente, pode configurar a definição **Ignorar versão da aplicação** no painel **Informações da aplicação**. Quando esta opção está definida para **Sim**, o Microsoft Intune irá ignorar a versão da aplicação instalada no cliente Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune---1864117---"></a>Conjuntos relacionados de licenças de aplicações suportadas no Intune<!-- 1864117 -->
O Intune no portal do Azure agora suporta conjuntos relacionados de licenças de aplicações como um único item de aplicação na IU. Além disso, todas as aplicações com Licença Offline sincronizadas a partir da Microsoft Store para Empresas serão consolidadas numa única entrada de aplicação e todos os detalhes de implementação dos pacotes individuais serão migrados para uma única entrada. Para ver conjuntos relacionados de licenças de aplicações no portal do Azure, selecione **Licenças de aplicação** no painel **Aplicações do cliente**.

### <a name="device-configuration"></a>Configuração do dispositivo
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption---1463582---"></a>Extensões de ficheiros do Windows Information Protection (WIP) para encriptação automática<!-- 1463582 -->
Uma definição na política do Windows Information Protection (WIP) agora permite-lhe especificar que extensões de ficheiros são automaticamente encriptadas ao copiar de uma partilha do Server Message Block (SMB) no vínculo empresarial, conforme definido na política do WIP.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurar definições de contas de recurso para Surface Hubs

Agora pode configurar definições de contas de recurso para Surface Hubs remotamente.

A conta de recurso é utilizada por um Surface Hub para efetuar a autenticação com o Skype/Exchange para que possa participar numa reunião.
Poderá querer criar uma conta de recurso exclusiva para que o Surface Hub seja apresentado na reunião como a sala de conferência.
Por exemplo, uma conta de recurso como **Sala de Conferência B41/6233**.

> [!NOTE]
> - Se deixar campos em branco, irá substituir atributos configurados anteriormente no dispositivo.
>
> - As propriedades da Conta de Recurso podem ser alteradas de forma dinâmica no Surface Hub. Por exemplo, caso a rotação da palavra-passe esteja ativada. Por isso, é possível que os valores na consola do Azure demorem algum tempo a refletir a realidade no dispositivo.
>
>   Para perceber o que está configurado atualmente no Surface Hub, as informações da Conta de Recurso podem ser incluídas no inventário de hardware (que já tem um intervalo de 7 dias) ou como propriedades só de leitura. Para melhorar a precisão após ser efetuada uma ação remota, pode obter o estado dos parâmetros imediatamente após a execução da ação para atualizar a conta/os parâmetros no Surface Hub.

##### <a name="attack-surface-reduction"></a>Redução da Superfície de Ataque

|Nome da definição  |Opções da definição  |Description  |
|---------|---------|---------|
|Execução de conteúdos executáveis protegidos por palavra-passe a partir do e-mail|Bloquear, Auditar, Não configurado|Impeça a execução de ficheiros executáveis protegidos por palavra-passe transferidos do e-mail.|
|Proteção de ransomware avançada|Ativado, Auditar, Não configurado|Utilize proteção contra ransomware intensiva.|
|Sinalizar o roubo de credenciais do subsistema de autoridade de segurança local do Windows|Ativado, Auditar, Não configurado|Sinalize o roubo de credenciais do subsistema de autoridade de segurança local do Windows (Lsass.exe).|
|Criação de processos com os comandos PsExec e WMI|Bloquear, Auditar, Não configurado|Bloqueie a criação de processos provenientes de comandos PsExec e WMI.|
|Processos não fidedignos e não assinados executados a partir de USB|Bloquear, Auditar, Não configurado|Bloqueie processos não fidedignos e não assinados executados a partir de USB.|
|Ficheiros executáveis que não cumprem uma lista de critérios de prevalência, idade ou fidedignidade|Bloquear, Auditar, Não configurado|Impeça ficheiros executáveis de serem executados a menos que cumpram uma lista de critérios de prevalência, idade ou fidedignidade.|

##### <a name="controlled-folder-access"></a>Acesso a pastas controladas

|              Nome da definição               |                                                              Opções da definição                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Proteção de pastas (já implementada) | Não configurado, Ativar, Apenas auditoria (já implementada)<br><br> <strong>Novidade</strong><br>Bloquear modificação do disco, Auditar modificação do disco |             |

Proteja ficheiros e pastas contra alterações não autorizadas por aplicações não fidedignas.<br><br>**Ativar**: impede que aplicações não fidedignas modifiquem ou eliminem ficheiros em pastas protegidas e escrevam em setores do disco.<br><br>
**Bloquear apenas a modificação do disco**:<br>Impeça que aplicações não fidedignas escrevam em setores do disco. As aplicações não fidedignas continuam a poder modificar ou eliminar ficheiros em pastas protegidas.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies--1704133--"></a>Adições às definições de políticas de conformidade da Segurança do Sistema do Windows 10 e posterior<!--1704133-->

Estão agora disponíveis adições às definições de conformidade do Windows 10, incluindo a obrigatoriedade da Firewall e do Antivírus do Windows Defender.

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business--1222672--"></a>Suporte para aplicações offline na Loja Microsoft para Empresas<!--1222672-->
As aplicações offline que comprou na Microsoft Store para Empresas são agora sincronizadas com o portal do Azure. Pode implementar estas aplicações em grupos de dispositivos ou de utilizadores. As aplicações offline são instaladas pelo Intune, não pela loja.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile---1728700---"></a>Impedir os utilizadores de adicionarem ou removerem contas manualmente no perfil de trabalho<!-- 1728700 -->

Ao implementar a aplicação Gmail num perfil do Android for Work, agora pode impedir os utilizadores finais de adicionarem ou removerem contas manualmente no perfil de trabalho através da definição **Adicionar e remover contas** no perfil Restrições do dispositivo Android for Work.

<!-- ########################## -->
## <a name="january-2018"></a>Janeiro de 2018

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire---1639263---"></a>Alertas para tokens expirados e tokens que expiram em breve<!-- 1639263 -->
A página de descrição geral agora mostra alertas sobre tokens expirados e tokens prestes a expirar. Ao clicar num alerta com um único token, acederá à página de detalhes do token.  Se clicar num alerta com vários tokens, acederá a uma lista de todos os tokens com o estado deles. Os administradores devem renovar os tokens antes da data de expiração.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="remote-erase-command-support-for-macos-devices---1438084---"></a>Suporte para o comando “Apagar” remoto em dispositivos macOS<!-- 1438084 -->

Os administradores podem executar um comando Apagar remotamente para dispositivos macOS.

> [!IMPORTANT]
> O comando apagar não pode ser invertido e deve ser utilizado com cuidado.

O comando apagar remove todos os dados, incluindo o sistema operativo, de um dispositivo. Esta operação também remove o dispositivo da gestão do Intune. Nenhum aviso é apresentado ao utilizador e a eliminação ocorre imediatamente após a emissão do comando.

Tem de configurar um PIN de recuperação de seis dígitos. Este PIN pode servir para desbloquear o dispositivo apagado, altura em que irá iniciar a reinstalação do sistema operativo. Depois de a eliminação começar, o PIN é apresentado numa barra de estado no painel de descrição geral do dispositivo no Intune. O PIN será mantido enquanto a eliminação estiver em curso. Depois de concluída a eliminação, o dispositivo desaparece totalmente da gestão do Intune. Não se esqueça de registar o PIN de recuperação para que quem estiver a restaurar o dispositivo o possa utilizar.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token---820870---"></a>Revogar licenças para um token do Volume Purchase Program para iOS<!-- 820870 -->
Pode revogar a licença de todas as aplicações VPP (Volume Purchase Program) para iOS para um Token VPP específico.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="revoking-ios-volume-purchase-program-apps----820863---"></a>Revogar aplicações do Volume Purchase Program para iOS <!-- 820863 -->
Para um dispositivo específico com uma ou mais aplicações VPP (Volume Purchase Program) para iOS, pode revogar a licença da aplicação baseada em dispositivos associada do dispositivo. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. Para obter mais informações, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune](../apps/vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type---1332318---"></a>Atribuir aplicações móveis do Office 365 a dispositivos iOS e Android ao utilizar o tipo de aplicação incorporada<!-- 1332318 -->
O tipo de aplicação **Incorporada** torna mais fácil criar e atribuir aplicações do Office 365 nos dispositivos iOS e Android que gere. Estas aplicações incluem aplicações do O365, tais como o Word, Excel, PowerPoint e OneDrive. Pode atribuir aplicações específicas ao tipo de aplicação e editar a configuração de informações da aplicação.

#### <a name="including-and-excluding-app-assignment-based-on-groups---1406920---"></a>Incluir e excluir a atribuição de aplicações com base nos grupos<!-- 1406920 -->

Durante a atribuição de aplicações e após selecionar um tipo de atribuição, pode selecionar os grupos a incluir e os grupos a excluir.

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments----1480316---"></a>Pode atribuir uma política de configuração de aplicações a grupos ao incluir e excluir atribuições <!-- 1480316 -->

Pode atribuir uma política de configuração de aplicações a um grupo de utilizadores e dispositivos ao incluir e excluir atribuições. As atribuições podem ser seleções personalizadas de grupos ou um grupo virtual. Um grupo virtual pode incluir **Todos os utilizadores**, **Todos os Dispositivos** ou **Todos os Utilizadores e Todos os Dispositivos**.

#### <a name="support-for-windows-10-edition-upgrade-policy-----903672archived-1119689---"></a>Suporte para a política de atualização da edição do Windows 10  <!-- 903672(archived), 1119689 -->  
Pode criar uma política de atualização da edição do Windows 10 que atualize os dispositivos com o Windows 10 para o Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Para obter detalhes sobre as atualizações da edição do Windows 10, veja [Como configurar atualizações da edição do Windows 10](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal----1737088-1634311---"></a>As políticas de Acesso Condicional do Intune só estão disponíveis no portal do Azure <!-- 1737088 1634311 -->

A partir desta versão, tem de configurar e gerir as políticas de Acesso Condicional no [portal do Azure](https://portal.azure.com) a partir de **Azure Active Directory** > **Acesso Condicional**. Para a sua comodidade, também pode aceder a este painel a partir do Intune no portal do Azure em **Intune** > **Acesso Condicional**.

#### <a name="updates-to-compliance-emails--1637547---"></a>Atualizações em e-mails de conformidade<!--1637547 -->

Quando é enviado um e-mail para comunicar um dispositivo não conforme, são incluídos detalhes sobre o mesmo.

### <a name="intune-apps"></a>Aplicações do Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices--1583480--"></a>Nova funcionalidade para a ação “Resolver” em dispositivos Android<!--1583480-->

A aplicação Portal da Empresa para Android irá expandir a ação "Resolver" de **Atualizar definições do dispositivo** para também resolver [problemas de encriptação de dispositivos](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10--676506--"></a>Bloqueio remoto disponível na aplicação Portal da Empresa para Windows 10<!--676506-->
Agora os utilizadores finais podem bloquear remotamente os seus dispositivos a partir da aplicação Portal da Empresa para Windows 10. Isto não será apresentado no dispositivo local que estejam a utilizar atualmente.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10--676546--"></a>Resolução de problemas de conformidade mais fácil na aplicação do Portal da Empresa para Windows 10<!--676546-->
Os utilizadores finais com dispositivos Windows poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema.

<!-- ########################## -->
## <a name="december-2017"></a>Dezembro de 2017

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="new-automatic-redeployment-setting---1469168---"></a>Nova definição de reimplementação automática<!-- 1469168 -->
A definição **Reimplementação automática** permite aos utilizadores com direitos administrativos eliminar todos os dados do utilizador e as definições através de **CTRL + Win + R** no ecrã de bloqueio do dispositivo. O dispositivo é automaticamente reconfigurado e reinscrito na gestão. Esta definição encontra-se em Windows 10 > Restrições do dispositivo > Geral > Reimplementação automática. Para obter mais detalhes, veja [Definições de restrição de dispositivos Windows 10 no Intune](../configuration/device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy----903672--1119689---"></a>Suporte para edições de origem adicionais na política de atualização de edição do Windows 10 <!-- 903672,  1119689 -->
Agora, pode utilizar a política de atualização de edição do Windows 10 para atualizar a partir de edições do Windows 10 adicionais (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud e etc.). Antes desta versão, os caminhos de atualização de edição suportados eram mais limitados. Para obter detalhes, veja [Como configurar atualizações de edição do Windows 10](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings---1335507---"></a>Novas definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender (WDSC)<!-- 1335507 -->

O Intune adiciona uma nova secção de definições do perfil de configuração do dispositivo na Endpoint Protection com o nome **Centro de Segurança do Windows Defender**. Os administradores de TI podem configurar quais os pilares do Centro de Segurança do Windows Defender a que os utilizadores finais podem aceder. Se um administrador de TI ocultar um pilar na aplicação do Centro de Segurança do Windows Defender, nenhuma das notificações relacionadas com o pilar oculto serão apresentadas no dispositivo do utilizador.

Estes são os pilares que os administradores podem ocultar das definições do perfil de configuração do dispositivo do Centro de Segurança do Windows Defender:
- Proteção contra vírus e ameaças
- Desempenho e funcionamento do dispositivo
- Proteções de rede e de firewall
- Controlo de aplicações e browsers
- Opções de famílias

Os administradores de TI também podem personalizar as notificações que os utilizadores recebem. Por exemplo, pode configurar se os utilizadores recebem todas as notificações geradas por pilares visíveis no WDSC ou apenas as notificações críticas. As notificações não críticas incluem resumos periódicos da atividade e das notificações do Antivírus do Windows Defender quando as análises estiverem concluídas. Todas as outras notificações são consideradas críticas. Além disso, também pode personalizar o próprio conteúdo da notificação, por exemplo, pode proporcionar as informações de contacto de TI para incorporar nas notificações que são apresentadas nos dispositivos dos utilizadores.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling---1361755---"></a>Suporte para vários conectores para o processamento de certificados PFX e SCEP<!-- 1361755 -->

Os clientes que utilizam o conector do NDES no local para entregar certificados aos dispositivos podem agora configurar múltiplos conectores num único inquilino.

Esta nova capacidade suporta o seguinte cenário:

- **Elevada disponibilidade**

Cada conector do NDES obtém os pedidos de certificados do Intune.  Se um conector do NDES ficar offline, o outro conector poderá continuar a processar pedidos.

#### <a name="customer-subject-name-can-use-aad_device_id-variable----1468599---"></a>Nome do requerente do cliente pode utilizar a variável AAD_DEVICE_ID <!-- 1468599 -->

Quando cria um perfil de certificado SCEP no Intune, agora, pode utilizar a variável AAD_DEVICE_ID ao criar o nome do requerente personalizado.   Quando o certificado é solicitado através deste perfil SCEP, a variável é substituída pelo ID de dispositivo do AAD do dispositivo que faz o pedido de certificado.


### <a name="device-management"></a>Gestão de dispositivos

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747---"></a>Gerir dispositivos macOS inscritos com Jamf através do motor de conformidade de dispositivos do Intune<!-- 1592747 -->
Agora, pode utilizar o Jamf para enviar informações sobre o estado do dispositivo macOS ao Intune que, em seguida, avaliará a conformidade com as políticas definidas na consola do Intune. Com base no estado de conformidade do dispositivo, bem como em outras condições (como local, risco do usuário, etc.), o acesso condicional impedirá a conformidade para dispositivos macOS que acessam aplicativos locais e de nuvem conectados ao Azure AD, incluindo o Office 365. Saiba mais sobre como [configurar a integração do Jamf](../protect/conditional-access-integrate-jamf.md) e [impor a conformidade para dispositivos geridos pelo Jamf](../protect/conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action-----1424701---"></a>Nova ação do dispositivo iOS  <!-- 1424701 -->

Agora, pode encerrar os dispositivos iOS 10.3 supervisionados. Esta ação encerra o dispositivo imediatamente sem avisar o utilizador final. A ação **Encerrar (apenas os supervisionados)** encontra-se nas propriedades do dispositivo ao selecionar um dispositivo na carga de trabalho **Dispositivo**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices---1468103---"></a>Não permitir alterações de data/hora em dispositivos Samsung Knox<!-- 1468103 -->

Adicionamos uma nova funcionalidade que lhe permite bloquear alterações de data e hora em dispositivos Samsung Knox. Pode encontrá-la em **Perfis de configuração de dispositivos** > **Restrições de dispositivos (Android)**  > **Geral**.

#### <a name="surface-hub-resource-account-supported---1566442----"></a>Conta de recurso Surface Hub suportada<!-- 1566442  -->

Foi adicionada uma nova ação do dispositivo para que os administradores possam definir e atualizar a conta de recurso associada a um Surface Hub.

A conta de recurso é utilizada por um Surface Hub para se autenticar com o Skype/Exchange para que possa participar numa reunião. Pode criar uma conta de recurso exclusiva para que o Surface Hub apareça na reunião como a sala de conferência. Por exemplo, a conta de recursos pode aparecer como a *Sala de Conferência B41/6233*. Normalmente, a conta de recurso (conhecida como a conta do dispositivo) do Surface Hub tem de ser configurada para a localização da sala de conferência e sempre que outros parâmetros da conta de recurso precisarem ser alterados.

Quando os administradores querem atualizar a conta de recurso num dispositivo, têm de indicar as credenciais do Active Directory/Azure Active Directory atuais associadas ao dispositivo. Se a rotação da palavra-passe estiver ativada no dispositivo, os administradores terão de aceder ao Azure Active Directory para localizar a palavra-passe.

> [!NOTE]
> Todos os campos são enviados para baixo num pacote e substituem todos os campos que foram anteriormente configurados. Os campos vazios também substituem os campos existentes.

Seguem-se as definições que os administradores podem configurar:

- **Conta de recurso**
  - **Utilizador do Active Directory**

    Nomedomínio\nomeutilizador ou Nome Principal de Utilizador (UPN): user@domainname.com

  - **Palavra-passe**

- **Parâmetros da conta de recurso opcionais** (têm de ser definidos com a conta de recurso especificada)

  - **Período de rotação da palavra-passe**

    Garante que a palavra-passe da conta é atualizada automaticamente pelo Surface Hub todas as semanas por motivos de segurança. Para configurar quaisquer parâmetros depois de ativar esta opção, terá primeiro de repor a palavra-passe na conta no Azure Active Directory.

  - **Endereço do protocolo SIP (Session Initiation Protocol)**

    Usado apenas quando a autodiscovery falhar.

  - **E-mail**

    Endereço de e-mail da conta de recurso/dispositivo.

  - **Exchange Server**

    Só é preciso quando a autodiscovery falhar.

  - **Sincronização do calendário**

    Especifica se a sincronização do calendário e outros serviços do Exchange Server estão ativados. Por exemplo: reunião de sincronização.

#### <a name="install-office-apps-on-macos-devices---1494311---"></a>Instalar aplicações do Office em dispositivos macOS<!-- 1494311 -->
A partir de agora, vai poder instalar aplicações do Office em dispositivos macOS. Este novo tipo de aplicação permitirá a instalação do Word, Excel, PowerPoint, Outlook e OneNote. Estas aplicações também vêm com o Microsoft AutoUpdate (MAU) para ajudar a manter as aplicações protegidas e atualizadas.

### <a name="app-management"></a>Gestão de aplicações

#### <a name="delete-an-ios--volume-purchasing-program-token---820879---"></a>Eliminar um token do Volume Purchase Program para iOS<!-- 820879 -->
Poderá eliminar o token VPP (Volume Purchasing Program) para iOS através da consola. Tal poderá ser preciso quando tiver ocorrências duplicadas de um token de VPP.

### <a name="intune-apps"></a>Aplicações do Intune


### <a name="role-based-access-control"></a>Controlo de acesso baseado em funções

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data---1667026---"></a>A nova coleção de entidades denominada Utilizador Atual está limitada aos dados dos utilizadores atualmente ativos<!-- 1667026 -->

A coleção de entidades **Utilizadores** contém todos os utilizadores do Azure Active Directory (Azure AD) com licenças atribuídas na empresa. Por exemplo, um utilizador pode ser adicionado ao Intune e, em seguida, removido no decorrer do mês anterior. Apesar de este utilizador não estar presente no momento do relatório, o utilizador e o estado estão presentes nos dados. Pode criar um relatório que mostrará a duração da presença no histórico do utilizador nos seus dados.

Em contrapartida, a nova coleção de entidades **Utilizador Atual** contém apenas os utilizadores que não foram removidos. A coleção de entidades **Utilizador Atual** contém apenas os utilizadores atualmente ativos. Para obter informações sobre a coleção de entidades **Utilizador Atual**, veja [Reference for current user entity (Referência para a entidade utilizador atual)](../developer/reports-ref-data-model.md).

### <a name="updated-graph-apis---1736360---"></a>Graph APIs atualizadas<!-- 1736360 -->

Nesta versão, atualizamos algumas das Graph APIs do Intune que estão na versão beta. Veja o [registo de alterações da Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) mensal para obter mais informações.

### <a name="monitor-and-troubleshoot"></a>Monitorizar e resolver problemas

#### <a name="intune-supports-windows-information-protection-wip-denied-apps---1479103---"></a>O Intune suporta as aplicações negadas do Windows Information Protection (WIP)<!-- 1479103 -->
Pode especificar aplicações negadas no Intune. Se uma aplicação for negada, não poderá aceder a informações empresariais, ao contrário do que acontece com a lista de aplicações permitidas. Para obter mais informações, veja [Recommended deny list for Windows Information Protection (Lista de negações recomendadas para o Windows Information Protection)](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).

<!-- ########################## -->
## <a name="november-2017"></a>Novembro de 2017

### <a name="troubleshoot-enrollment-issues----746324---"></a>Resolução de problemas de inscrição <!-- 746324 -->

A área de trabalho **Resolução de Problemas** agora apresenta os problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.

### <a name="group-assigned-enrollment-restrictions---747598---"></a>Restrições de inscrição atribuídas a grupos<!-- 747598 -->

Enquanto administrador do Intune, agora pode [criar restrições de inscrição personalizadas de Tipo de Dispositivo e Limite de Dispositivo para grupos de utilizadores](../enrollment/enrollment-restrictions-set.md).

O portal do Azure do Intune permite-lhe criar até 25 instâncias de cada tipo de restrição, que podem depois ser atribuídas a grupos de utilizadores. As restrições atribuídas a grupos substituem as restrições predefinidas.

Todas as instâncias de um tipo de restrição são mantidas numa lista estritamente ordenada. Esta ordem define um valor de prioridade para a resolução do conflito. Um utilizador afetado por mais do que uma instância de restrição só é restringido pela instância com o valor de prioridade mais elevada. Pode alterar a prioridade de uma determinada instância ao arrastá-la para uma posição diferente na lista.

Esta funcionalidade será lançada com a migração das definições do Android for Work do menu de inscrição do Android for Work para o menu Restrições de Inscrição. Como esta migração pode demorar vários dias, poderão ser atualizadas outras partes da sua conta no lançamento de novembro antes da ativação da atribuição de grupos nas Restrições de Inscrição.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors---1528104---"></a>Suporte para múltiplos conectores do Serviço de Inscrição de Dispositivos de Rede (NDES)<!-- 1528104 -->

O NDES permite a execução de dispositivos móveis sem credenciais de domínio para obter certificados com base no protocolo SCEP (Simple Certificate Enrollment Protocol).
Com esta atualização, são suportados múltiplos conectores do NDES.

### <a name="manage-android-for-work-devices-independently-from-android-devices---1490731-eeready--"></a>Gerir dispositivos Android for Work de forma independente dos dispositivos Android<!-- 1490731 EEready-->

O Intune suporta a gestão de inscrição de dispositivos Android for Work de forma independente da plataforma Android. Estas definições são geridas em **Inscrição de Dispositivos** > **Restrições de inscrição** > **Restrições de Tipos de Dispositivos**. (Estavam anteriormente localizadas em **Inscrição de Dispositivos** > **Inscrição do Android for Work** > **Definições de Inscrição do Android for Work**.)

Por predefinição, as definições dos dispositivos Android for Work são as mesmas que as definições dos seus dispositivos Android. No entanto, depois de alterar as definições do Android for Work, este já não será o caso.

Se bloquear a inscrição pessoal do Android for Work, só será possível inscrever dispositivos Android empresariais como Android for Work.

Ao trabalhar com as novas definições, tenha em conta o seguinte:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se nunca tiver integrado a inscrição do Android for Work

A nova plataforma do Android for Work está bloqueada nas Restrições de Tipos de Dispositivos predefinidas. Depois de integrar a funcionalidade, pode permitir que os dispositivos sejam inscritos com o Android for Work. Para tal, altere a predefinição ou crie uma nova Restrição de Tipo de Dispositivo para substituir a Restrição de Tipo de Dispositivo predefinida.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se já tiver integrado a inscrição do Android for Work

Se já a tiver integrado, a sua situação depende da definição que escolher:

| Definição | Estado do Android for Work em Restrição de Tipo de Dispositivo predefinida | Notas |
| --- | --- | --- |
| **Gerir todos os dispositivos como Android** | Bloqueado | Todos os dispositivos Android têm de ser inscritos sem o Android for Work. |
| **Gerir dispositivos suportados como Android for Work** | Permitido | Todos os dispositivos Android que suportam o Android for Work têm de ser inscritos com o Android for Work. |
| **Gerir dispositivos suportados para utilizadores apenas nestes grupos como Android for Work** | Bloqueado | Foi criada uma política de Restrição de Tipo de Dispositivo separada para substituir a predefinição. Esta política define os grupos que selecionou anteriormente para permitir a inscrição do Android for Work. Os utilizadores nos grupos selecionados continuarão a poder inscrever os seus dispositivos Android for Work. Todos os outros utilizadores não efetuam a inscrição com o Android for Work. |

Em todos os casos, mantém-se o seu regulamento pretendido. Não é necessária nenhuma ação da sua parte para manter a permissão global ou por grupo do Android for Work no seu ambiente.

### <a name="google-play-protect-support-on-android---908720---"></a>Suporte ao Google Play Protect no Android<!-- 908720 -->

Com o lançamento do Android Oreo, a Google apresenta um conjunto de funcionalidades de segurança chamado Google Play Protect, que permite que os utilizadores e as organizações executem imagens Android e aplicações seguras. O Intune agora suporta funcionalidades do Google Play Protect, incluindo o atestado remoto SafetyNet. Os administradores podem definir os requisitos da política de conformidade que são necessários para o Google Play Protect ser configurado e funcionar corretamente.
A definição **Atestado do dispositivo SafetyNet** requer que o dispositivo para estabelecer ligação com um serviço do Google verifique se o dispositivo está a funcionar e se não está comprometido. Os administradores também podem especificar uma definição de perfil de configuração do Android For Work que exija que as aplicações instaladas sejam verificadas pelos serviços do Google Play. Se um dispositivo não estiver em conformidade com os requisitos de proteção de Google Play, o acesso condicional poderá impedir que os usuários acessem recursos corporativos.

- Saiba [Como criar uma política de conformidade de dispositivos para ativar o Google Play Protect](../protect/compliance-policy-create-android.md).

### <a name="text-protocol-allowed-from-managed-apps---1414050----"></a>Protocolo de texto autorizado a partir de Aplicações geridas<!-- 1414050  -->

As aplicações geridas pelo SDK da Aplicação Intune podem enviar mensagens SMS.


### <a name="app-install-report-updated-to-include-install-pending-status---1249446---"></a>O relatório de instalação da aplicação foi atualizado para incluir o estado Instalação Pendente<!-- 1249446 -->  

O relatório **Estado de instalação de aplicação** acessível para cada aplicação através da lista **Aplicação** na carga de trabalho **Aplicações do cliente** contém uma contagem de **Instalações Pendentes** para Utilizadores e Dispositivos.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection---1391759---"></a>API do inventário de aplicações do iOS 11 para a Deteção de Ameaças para Dispositivos Móveis<!-- 1391759 -->

O Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Deteção de Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Pode recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS 11 ou uma versão superior.

**Inventário de aplicações**  
Os inventários de dispositivos iOS pessoais ou empresariais com o iOS 11 ou uma versão superior são enviados para o seu fornecedor de serviços de MTD. Os dados no inventário de aplicações incluem:

- ID da Aplicação
- Versão da Aplicação
- Versão Abreviada da Aplicação
- Nome da Aplicação
- Tamanho da Coleção de Pacotes de Aplicação
- Tamanho Dinâmico da Aplicação
- A aplicação é ou não validada
- A aplicação é ou não gerida

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone---1463747-wnready---"></a>Migrar os utilizadores e dispositivos da MDM híbrida para o Intune autónomo<!-- 1463747 wnready -->
Estão agora disponíveis novos processos e ferramentas para migrar utilizadores e os respetivos dispositivos da MDM híbrida para o Intune no portal do Azure, que lhe permitem efetuar as seguintes tarefas:
- Copiar políticas e perfis da consola do Configuration Manager para o Intune no portal do Azure
- Mover um subconjunto de utilizadores para o Intune no portal do Azure enquanto mantém os restantes na MDM híbrida
- Migrar dispositivos para o Intune no portal do Azure sem precisar de voltar a inscrevê-los

### <a name="on-premises-exchange-connector-high-availability-support----676614---"></a>Suporte de elevada disponibilidade do Exchange Connector no local <!-- 676614 -->
Depois que o Exchange Connector cria uma conexão com o Exchange usando o servidor de acesso para cliente (CAS) especificado, o conector agora tem a capacidade de descobrir outros CASs. Se a CAS principal ficar indisponível, o conector realizará a ativação pós-falha de outra CAS, se disponível, até a CAS principal ficar disponível. Para obter mais informações, veja [Suporte de elevada disponibilidade do conector do Exchange no local](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only---1424595---"></a>Reiniciar dispositivos iOS remotamente (apenas supervisionado)<!-- 1424595 -->

Agora pode acionar o reinício de um dispositivo supervisionado com o iOS 10.3 ou superior ao utilizar uma ação de dispositivo. Para obter mais informações sobre como utilizar a ação de reinício de dispositivos, veja [Reiniciar remotamente dispositivos com o Intune](../remote-actions/device-restart.md).

> [!Note]
> Este comando necessita de um dispositivo supervisionado e do direito de acesso **Bloqueio do Dispositivo**. O dispositivo é reiniciado imediatamente. Os dispositivos iOS bloqueados por código de acesso não voltarão a ligar-se a uma rede Wi-Fi após o reinício. Após o reinício, estes dispositivos poderão não conseguir comunicar com o servidor.

### <a name="single-sign-on-support-for-ios---1333645---"></a>Suporte de Início de Sessão Único para iOS<!-- 1333645 -->  

Pode utilizar o Início de Sessão Único para utilizadores do iOS. As aplicações iOS que estão codificadas para procurar as credenciais dos utilizadores no payload de Início de Sessão Único são compatíveis com esta atualização de configuração do payload. Também pode utilizar o UPN e o ID de Dispositivo do Intune para configurar o Nome Principal e o Realm. Para obter detalhes, veja [Configure Intune for iOS device single sign-on (Configurar o Intune para o início de sessão único em dispositivos iOS)](../configuration/ios-device-features-settings.md#single-sign-on).

### <a name="add-find-my-iphone-for-personal-devices--1427287--"></a>Adicionar “Encontrar o meu iPhone” para dispositivos pessoais<!--1427287-->
Agora pode ver se os dispositivos iOS têm o Bloqueio de Ativação ativado. Esta funcionalidade estava anteriormente disponível no portal clássico do Intune.

### <a name="remotely-lock-managed-macos-device-with-intune---1437691---"></a>Bloquear remotamente dispositivos macOS geridos com o Intune<!-- 1437691 -->

Pode bloquear um dispositivo macOS perdido e definir um PIN de recuperação de 6 dígitos. Se estiver bloqueado, o painel **Descrição geral do dispositivos** apresenta o PIN até que seja enviada outra ação de dispositivo.

Para obter mais informações, veja [Bloquear remotamente dispositivos geridos com o Intune](../remote-actions/device-remote-lock.md).

### <a name="new-scep-profile-details-supported---1559808---"></a>Suporte para novos detalhes do perfil SCEP<!-- 1559808 -->

Agora, os administradores podem configurar definições adicionais ao criar um perfil SCEP em plataformas Windows, iOS, macOS e Android.  Os administradores podem definir o IMEI, o número de série ou o nome comum, incluindo o e-mail, no formato do nome do requerente.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset---1588489---"></a>Reter dados durante uma reposição de fábrica <!--1588489 -->
Quando repõe uma versão 1709 ou posterior do Windows 10 para as definições de fábrica, fica disponível uma nova capacidade. Os administradores podem especificar se a inscrição de dispositivos e outros dados aprovisionados são retidos num dispositivo através de uma reposição de fábrica.

Os seguintes dados são retidos através de uma reposição de fábrica:
- Contas de utilizador associadas ao dispositivo
- Estado da máquina (associação a um domínio, associado ao Azure Active Directory)
- Inscrição na MDM
- Aplicações OEM instaladas (aplicações Win32 e da loja)
- Perfil de utilizador
- Dados de utilizador fora do perfil de utilizador
- Início de sessão automático de utilizador

Os seguintes dados não são retidos:
- Ficheiros do utilizador
- Aplicações instaladas pelo utilizador (aplicações Win32 e da loja)
- Definições do dispositivo não predefinidas


### <a name="window-10-update-ring-assignments-are-displayed---1621837---"></a>Atribuições da cadência de atualizações do Windows 10 apresentadas<!-- 1621837 -->
Durante a **Resolução de problemas** do utilizador que está a ver, pode ver todas as atribuições de cadências de atualização do Windows 10.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings----1455974----"></a>Definições da frequência dos relatórios do Advanced Threat Protection do Windows Defender <!-- 1455974  -->
O serviço de Proteção Avançada Contra Ameaças do Windows Defender (WDATP) permite aos administradores gerir a frequência de relatórios dos dispositivos geridos. Com a nova opção **Acelerar a frequência do relatório de telemetria**, o WDATP recolhe os dados e avalia os riscos com mais frequência. A predefinição dos relatórios otimiza a velocidade e o desempenho. O aumento da frequência de relatórios pode ser útil para dispositivos de alto risco. Poderá encontrar esta definição no perfil **Windows Defender ATP** nas **Configurações do dispositivo**.

### <a name="audit-updates---1412961---"></a>Atualizações de auditoria<!-- 1412961 -->  
A auditoria do Intune fornece um registo das operações de alteração relacionadas com o Intune.  Todas as operações de criação, atualização, eliminação e realização de tarefas remotas são registadas e retidas durante um ano.  O portal do Azure fornece uma vista dos dados de auditoria dos últimos 30 dias em cada carga de trabalho e podem ser filtrados.  A Graph API correspondente permite a obtenção dos dados de auditoria armazenados do último ano.

A Auditoria está localizada no grupo **MONITORIZAÇÃO**. Existe um item de menu **Registos de Auditoria** para cada carga de trabalho.

### <a name="company-portal-app-for-macos-is-available--1541700--"></a>A aplicação Portal da Empresa para macOS está disponível<!--1541700-->
O Portal da Empresa do Intune no macOS tem uma experiência atualizada, a qual foi otimizada para apresentar corretamente todas as informações e notificações de conformidade que os utilizadores precisam para todos os dispositivos inscritos. Além disso, após implementar o Portal da Empresa do Intune num dispositivo, o Microsoft AutoUpdate para macOS fornecerá as atualizações. Pode transferir o novo Portal da Empresa do Intune para macOS ao iniciar sessão no site do Portal da Empresa do Intune a partir de um dispositivo macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps----1248473---"></a>O Microsoft Planner faz agora parte da lista de aplicações aprovadas da gestão de aplicações móveis (MAM) <!-- 1248473 -->
A aplicação Microsoft Planner para iOS e Android faz agora parte das aplicações aprovadas para a gestão de aplicações móveis (MAM). A aplicação pode ser configurada através do painel Proteção de Aplicações do Intune no portal do Azure para todos os inquilinos.
- Saiba mais sobre a [Lista MAM de aplicações aprovadas](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices-----1547061---"></a>Frequência de atualização dos requisitos de VPN por Aplicação em dispositivos iOS  <!-- 1547061 -->  
Os administradores podem agora remover os requisitos de VPN por Aplicação para as aplicações em dispositivos iOS; os dispositivos afetados serão removidos após a próxima entrada do Intune, o que geralmente ocorre num espaço de 15 minutos.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector---885457---"></a>Suporte para o pacote de gestão do System Center Operations Manager do conector do Exchange<!-- 885457 -->
O pacote de gestão do System Center Operations Manager do conector do Exchange está agora disponível para ajudar a analisar os registos do conector do Exchange. Esta funcionalidade disponibiliza maneiras diferentes de monitorizar o serviço quando precisar de resolver problemas.

### <a name="co-management-for-windows-10-devices----1243445---"></a>Cogestão para os dispositivos com Windows 10 <!-- 1243445 -->
A cogestão é uma solução que proporciona a transição de uma gestão tradicional para uma moderna, além de permitir que faça essa transição de forma faseada. Na sua génese, a cogestão é uma solução em que os dispositivos Windows 10 são geridos simultaneamente pelo Configuration Manager e pelo Microsoft Intune, além de estar associada ao Active Directory (AD) e ao Azure Active Directory (Azure AD).  Esta configuração proporciona-lhe uma forma de modernizar a gestão com ao longo do tempo e ao ritmo mais adequado para a sua organização, caso não consiga efetuar a mudança de uma só vez.  

### <a name="restrict-windows-enrollment-by-os-version---245498---"></a>Restringir a Inscrição do Windows por versão do SO<!-- 245498 -->
Enquanto administrador do Intune, pode especificar uma versão mínima e máxima do Windows 10 para a inscrição de dispositivos. Pode definir estas restrições no painel **Configurações da Plataforma**.

O Intune irá continuar a suportar a inscrição de telemóveis e PCs com o Windows 8.1. No entanto, apenas as versões do Windows 10 podem ser definidas com os limites mínimo e máximo. Para permitir a inscrição de dispositivos com o Windows 8.1, deixe o limite mínimo em branco.

### <a name="alerts-for-windows-autopilot-unassigned-devices----1631236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos <!-- 1631236 -->
Está disponível um novo alerta para dispositivos Windows AutoPilot não atribuídos na página **Microsoft Intune** > **Inscrição de dispositivos** > **Descrição geral**. Este alerta mostra o número de dispositivos do programa AutoPilot que não têm perfis de implementação do AutoPilot atribuídos. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows AutoPilot e informações detalhadas sobre os mesmos. Para obter mais informações, veja [Inscrever dispositivos Windows com o programa de implementação do Windows AutoPilot](../enrollment/enrollment-autopilot.md).


### <a name="refresh-button-for-devices-list------1333581---"></a>Botão Atualizar da Lista de dispositivos   <!-- 1333581 -->
Como a lista Dispositivos não atualiza automaticamente, pode utilizar o novo botão Atualizar para atualizar os dispositivos que são apresentados na lista.

### <a name="support-for-symantec-cloud-certification-authority-ca----1333638---"></a>Suporte para a Autoridade de Certificação (AC) do Symantec Cloud <!-- 1333638 -->    
O Intune agora suporta a AC da Symantec Cloud, que permite ao Intune Certificate Connector emitir certificados PKCS a partir da AC da Symantec Cloud para os dispositivos geridos pelo Intune. Se já estiver a utilizar o Intune Certificate Connector com a Autoridade de Certificação (AC) da Microsoft, pode utilizar a configuração existente do Intune Certificate Connector para incluir o suporte à AC da Symantec.

### <a name="new-items-added-to-device-inventory----1404455---"></a>Novos itens adicionados ao inventário de dispositivos  <!--1404455 -->
Estão agora disponíveis os seguintes novos itens no [inventário de dispositivos inscritos](../remote-actions/device-inventory.md):

- Endereço MAC Wi-Fi
- Espaço de armazenamento total
- Espaço livre total
- MEID
- Operadora subscritora

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Definir o acesso a aplicações através de uma atualização de segurança mínima para Android no dispositivo<!-- 1278463 -->   
Um administrador pode definir a atualização de segurança mínima para Android que tem de ser instalada no dispositivo, de modo a obter acesso a uma aplicação gerida numa conta gerida.

> [!Note]  
> Esta funcionalidade apenas restringe atualizações de segurança lançadas pela Google em dispositivos Android 6.0+.

### <a name="app-conditional-launch-support---1193313---"></a>Suporte para execução condicional de aplicações<!-- 1193313 -->
Os administradores de TI já podem definir um requisito através do portal de administração do Azure para impor um código de acesso em vez de um PIN numérico através da gestão de aplicações móveis (MAM) quando a aplicações é executada. Caso esteja configurado, é pedido ao utilizador que defina e utilize um código de acesso antes de poder aceder a aplicações otimizadas para a MAM. Os código de acesso são definidos como um PIN numérico com, pelo menos, um caráter especial ou letras em maiúsculas/minúsculas. Esta versão do Intune irá ativar esta funcionalidade **apenas no iOS**. O Intune suporta um código de acesso de forma semelhante a um PIN numérico: a aplicação define um comprimento mínimo e permite sequências e carateres repetidos. Esta funcionalidade requer que a participação de aplicações (por exemplo, WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune com o código desta funcionalidade para que as definições do código de acesso sejam impostas nas aplicações visadas.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report---1233999---"></a>Número da versão para aplicações de linha de negócio no relatório de estado de instalação do dispositivo<!-- 1233999 -->
Com esta versão, o relatório de estado de instalação do Dispositivo apresenta o número da versão de aplicação das aplicações de linha de negócio para iOS e Android. Pode utilizar estas informações para resolver problemas nas suas aplicações ou localizar dispositivos que estão a ser executados com versões desatualizadas da aplicação.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile---951708---"></a>Agora, os administradores podem configurar as Definições de firewall num dispositivo através de um perfil de configuração de dispositivo<!-- 951708 -->   
Os administradores podem ativar a firewall para os dispositivos, bem como configurar vários protocolos para redes de domínio privadas e públicas.  Poderá encontrar estas definições de firewall no perfil "Proteção de ponto final".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization---958257---"></a>O Windows Defender Application Guard ajuda a proteger os dispositivos de sites não fidedignos, consoante as definições da sua organização<!-- 958257 -->   
Os administradores podem definir sites como "fidedigno" ou "empresarial" através de um fluxo do Windows Information Protection ou do novo perfil "Limite de rede" nas configurações dos dispositivos. Se forem acedidos com o Microsoft Edge, todos os sites que não estiverem indicados no limite de rede fidedigno de um dispositivo com o Windows 10 de 64 bits serão abertos num browser num computador virtual Hyper-V.

Poderá encontrar o Application Guard nos perfis de configuração de dispositivos, no perfil "Proteção de ponto final". A partir daí, os administradores podem configurar a interação entre o browser virtualizado e o computador anfitrião, sites fidedignos e não fidedignos e os dados de armazenamento gerados no browser virtualizado. Para utilizar o Application Guard num dispositivo, é necessário configurar primeiro um limite de rede. É importante definir apenas um limite de rede para um dispositivo.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps---1031096---"></a>O Controlo de Aplicações do Windows Defender no Windows 10 Enterprise fornece um modo para confiar apenas em aplicações autorizadas<!-- 1031096 -->    
Com milhares de novos ficheiros maliciosos a serem criados todos os dias, a deteção com base em assinatura de antivírus para combater software maligno poderá deixar de ser uma defesa adequada contra novos ataques. Com o Controlo de Aplicações do Windows Defender no Windows 10 Enterprise, pode alterar a configuração do dispositivo de um modo em que as aplicações são fidedignas, a menos que sejam bloqueadas por um antivírus ou por outra solução de segurança, para um modo em que o sistema operativo confia apenas nas aplicações autorizadas pela sua empresa. A atribuição de fidedignidade a aplicações é feita no Controlo de Aplicações do Windows Defender.

Com o Intune, pode configurar as políticas de controlo de aplicações no modo "apenas auditoria" ou no modo de imposição. As aplicações não são bloqueadas ao serem executadas no modo "apenas auditoria". O modo "apenas auditoria" regista todos os eventos nos registos do cliente local. Também pode configurar se pretende que apenas os componentes Windows e as aplicações da Microsoft Store tenham permissão para serem executados ou se pretende permitir a execução de aplicações adicionais com boa reputação, conforme definido pelo Gráfico de Segurança Inteligente.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10---1063615---"></a>O Windows Defender Exploit Guard é um novo conjunto de funcionalidades de prevenção de intrusões para o Windows 10<!-- 1063615 -->   
O Windows Defender Exploit Guard inclui regras personalizadas para reduzir a exploração de aplicações, impede ameaças de macros e scripts, bloqueia automaticamente ligações de rede a endereço IP com baixa reputação e ajuda a proteger os dados de ransomware e ameaças desconhecidas. O Windows Defender Exploit Guard consiste nos seguintes componentes:

- A **Redução da Superfície de Ataque** fornece regras que lhe permitem impedir ameaças de macros, scripts e e-mail.
- O **Acesso a Pastas Controladas** bloqueia automaticamente o acesso a conteúdos de pastas protegidas.
- O **Filtro de Rede** bloqueia a ligação de saída de qualquer aplicação para um IP/domínio com baixa reputação
- A **Exploit Protection** fornece restrições de memória, fluxo de controlos e de políticas que podem ser utilizadas para proteger um aplicação de exploits.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices---790537---"></a>Gerir scripts do PowerShell no Intune para dispositivos Windows 10<!-- 790537 -->

A extensão de gestão do Intune permite-lhe carregar scripts do PowerShell no Intune para executar em dispositivos Windows 10. A extensão complementa as funcionalidades de gestão de dispositivos móveis (MDM) do Windows 10 e facilita a sua transição para a gestão moderna. Para obter detalhes, veja [Manage PowerShell scripts in Intune for Windows 10 devices (Gerir scripts do PowerShell no Intune para dispositivos Windows 10)](../apps/intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10--------1308850---"></a>Novas definições de restrição de dispositivos para Windows 10     <!-- 1308850 -->
- Mensagens (apenas para telemóveis) – desativar mensagens de teste ou MMS
- Palavra-passe – definições para ativar o sistema FIPS e utilizar dispositivos secundários Windows Hello para efeitos de autenticação 
- Apresentação – definições para ativar ou desativar o Dimensionamento de GDI para aplicações legadas

### <a name="windows-10-kiosk-mode-device-restrictions---1308872---"></a>Restrições de dispositivos Windows 10 no modo de quiosque<!-- 1308872 -->   
Pode restringir os utilizadores de dispositivos Windows 10 ao modo de local público, que os limita a um conjunto de aplicações predefinidas.  Para fazê-lo, crie um perfil de restrição de dispositivos Windows 10 e configure as definições do modo de local público.

O modo de local público suporta dois modos: **quiosque de uma aplicação** (permite que um utilizador execute apenas uma aplicação) ou **quiosque de várias aplicações** (concede acesso a um conjunto de aplicações).  Defina a conta de utilizador e o nome do dispositivo, o qual determina as aplicações suportadas).  Quando o utilizador tiver sessão iniciada, este será limitado às aplicações definidas.  Para saber mais, veja [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

O modo de local público necessita que:

- O Intune seja a autoridade MDM.
- As aplicações já estejam instaladas no dispositivo alvo.
- O dispositivo esteja [devidamente aprovisionado](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries---1311967---"></a>Novo perfil de configuração de dispositivos para a criação de limites de rede<!-- 1311967 -->   
Está agora disponível um novo perfil de configuração de dispositivos denominado **Limite de rede** nos perfis de configuração de dispositivos. Utilize este perfil para definir os recursos online que pretende que sejam considerados como empresariais e fidedignos. Tem de definir um limite de rede para um dispositivo *antes* de as funcionalidades como o Windows Defender Application Guard e o Windows Information Protection poderem ser utilizadas no dispositivo. É importante definir apenas um limite de rede para cada dispositivo.

Pode definir os recursos do Enterprise Cloud, intervalos de endereços IP e servidores proxy internos que pretende que sejam considerados fidedignos. Assim que o definir, o limite de rede pode ser utilizado por outras funcionalidades, tais como o Windows Defender Application Guard e o Windows Information Protection.

### <a name="two-additional-settings-for-windows-defender-antivirus---1338409---"></a>Duas definições adicionais do Antivírus do Windows Defender<!-- 1338409 -->  
**Nível de bloqueio de ficheiros**

| | |
|---|---|
| Não Configurado | A definição **Não Configurado** utiliza o nível de bloqueio predefinido do Antivírus do Windows Defender e oferece um sistema de deteção avançado sem aumentar o risco de detetar ficheiros legítimos. |
| Alto | A opção**Alto** aplica um nível de deteção elevado.
| Alto +  | A opção **Alto +** proporciona o nível de deteção Alto com medidas adicionais de proteção que podem afetar o desempenho do cliente.
| Tolerância zero  | A opção **Tolerância zero** bloqueia todos os executáveis desconhecidos. |

Embora seja pouco provável, mudar para o nível **Alto** pode fazer com que alguns ficheiros legítimos sejam detetados.
Recomendamos que mude o Nível de bloqueio de ficheiros para o valor predefinido **Não configurado**.

**Prolongamento do tempo limite para a análise de ficheiros pela cloud**  

| | |
|--|--|
| Número de segundos (0-50) | Especifique o período de tempo máximo em que o Antivírus do Windows Defender deve bloquear um ficheiro enquanto aguarda por um resultado da cloud. O período predefinido é de 10 segundos: o tempo adicional que for especificado aqui (até um máximo de 50 segundos) será adicionado a esses 10 segundos. Na maioria dos casos, a pesquisa demora muito menos tempo do que o tempo máximo permitido. Alargar o período de tempo permite que a cloud investigue ficheiros suspeitos de forma mais minuciosa. Recomendamos que ative esta definição e especifique, no mínimo, um aumento de 20 segundos adicionais. |

### <a name="citrix-vpn-added-for-windows-10-devices---1512457---"></a>Adição da VPN do Citrix para dispositivos Windows 10<!-- 1512457 -->  
Pode configurar a VPN do Citrix nos respetivos dispositivos Windows 10. Pode selecionar a VPN do Citrix na lista *Selecione um tipo de ligação* no painel **VPN Base** ao configurar uma VPN para o Windows 10 e posterior.

> [!Note]
> A configuração do Citrix existia para os sistemas iOS e Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios---1550823---"></a>As ligações Wi-Fi suportam chaves pré-partilhadas no iOS<!-- 1550823 -->
Os clientes podem configurar perfis de Wi-Fi para utilizar chaves pré-partilhadas (PSK) para ligações Pessoais WPA/WPA2 em dispositivos iOS. Estes perfis são enviados via push para o dispositivo do utilizador quando o dispositivo está inscrito no Intune.

Quando o perfil tiver sido enviado para o dispositivo, o passo seguinte depende da configuração do perfil.  Se estiver definido para ligar automaticamente, assim o faz quando a rede se tornar necessária.  Quando o perfil está definido para ligar manualmente, o utilizador tem de ativar a ligação manualmente.  

### <a name="access-to-managed-app-logs-for-ios---1469920---"></a>Acesso a registos de aplicações geridas para iOS<!-- 1469920 -->
Agora, os utilizadores finais com o Managed Browser instalado podem ver o estado da gestão de todas as aplicações publicadas da Microsoft e enviar registos para resolver os problemas das respetivas aplicações iOS geridas.

Para saber como ativar o modo de resolução de problemas num Managed Browser num dispositivo iOS, veja [How to access to managed app logs using the Managed Browser on iOS (Como aceder a registos de aplicações geridas com o Managed Browser no iOS)](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290---1417174---"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa para iOS na versão 2.9.0<!-- 1417174 -->

O fluxo de trabalho da configuração de dispositivos foi melhorado na aplicação Portal da Empresa para iOS. O tipo de linguagem é mais simples. Além disso, combinámos os ecrãs sempre que possível. A linguagem é agora mais adaptada à sua empresa, ao utilizar o nome da sua empresa no texto de configuração. Pode ver este fluxo de trabalho atualizado em  [novidades na página da IU para aplicações](../whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model---1544273---"></a>A entidade User contém dados de utilizador no modelo de dados Data Warehouse<!-- 1544273 -->
A primeira versão do modelo de dados do Armazém de Dados do Intune continha apenas dados de histórico recentes do Intune. Os criadores de relatórios não conseguiam capturar o estado atual de um utilizador. Nesta atualização, a **entidade User** é preenchida com os dados de utilizador mais recentes.

<!-- ########################## -->
## <a name="october-2017"></a>Outubro de 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible---1380712---"></a>O número da versão da aplicação de linha de negócio para iOS e Android está visível<!-- 1380712 -->

As aplicações no Intune apresentam agora o número da versão de aplicações de linha de negócio para iOS e Android. O número é apresentado no portal do Azure na lista de aplicações e no painel de descrição geral da aplicação. Os utilizadores finais podem ver o número da aplicação na aplicação Portal da Empresa e no portal Web.

__Número da versão completo__ – O número da versão completo identifica uma versão específica da aplicação. O número é apresentado como _Versão_(_Compilação_), por exemplo, 2.2(2.2.17560800).

O número da versão completo tem dois componentes:

- **Versão**  
  O número da versão é o número da versão legível por humanos da aplicação. Este número é utilizado pelos utilizadores finais para identificar diferentes versões da aplicação.

- **Número de Compilação**  
  O número de compilação é um número interno que pode ser utilizado para detetar aplicações e gerir a aplicação de forma programática. O número de compilação refere-se a uma iteração da aplicação que faz referência a alterações no código.

Saiba mais sobre os números de versão e o desenvolvimento de aplicações de linha de negócio em [Introdução ao SDK da Aplicação Microsoft Intune](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration---677972---"></a>Integração da gestão de dispositivos e aplicações<!-- 677972 -->   
Agora que tanto a gestão de dispositivos móveis (MDM) do Intune como a gestão de aplicações móveis (MAM) se encontram acessíveis no portal do Azure, o Intune iniciou a integração da experiência de administradores de TI em torno da gestão de aplicações e dispositivos. Estas alterações foram concebidas de modo a simplificar a sua experiência de gestão de dispositivos e aplicações.

Saiba mais sobre as alterações de MDM e MAM anunciadas no [blogue da equipa de suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices---1471790---"></a>Novos alertas de inscrição para dispositivos da Apple<!-- 1471790 -->
A página de descrição geral para inscrição apresentará alertas úteis para os administradores de TI sobre a gestão de dispositivos da Apple. Os alertas serão apresentados na página Descrição Geral quando o certificado push de MDM da Apple estiver prestes a expirar ou já tiver expirado, quando o token do Programa de Registo de Aparelho estiver prestes a expirar ou já tiver expirado e quando existirem dispositivos não atribuídos no Programa de Registo de Aparelho.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment---1080364---"></a>Suporte à substituição de tokens para a configuração de aplicações sem inscrição de dispositivos<!-- 1080364 -->

Pode utilizar tokens para valores dinâmicos em configurações da aplicação para aplicações em dispositivos que não estejam inscritos. Para obter mais informações, veja [Adicionar políticas de configuração da aplicação para aplicações geridas sem inscrição de dispositivos](../apps/app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10--1299474--"></a>Atualizações à aplicação Portal da Empresa para Windows 10<!--1299474-->
A página Definições na aplicação Portal da Empresa para Windows 10 foi atualizada para tornar as definições e as ações do utilizador em causa mais consistentes em todas as definições. Também foi atualizada para corresponder ao esquema de outras aplicações do Windows. Pode encontrar imagens antes/depois na página [novidades na página da IU para aplicações](../whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices--1337920--"></a>Informar os utilizadores finais acerca das informações do dispositivo que podem ser vistas nos dispositivos Windows 10<!--1337920-->
Adicionámos o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para Windows 10. Isto permitirá que os utilizadores descubram mais sobre privacidade diretamente a partir desta página a partir dos docs finais do utilizador intune. Também poderão localizar esta informação no ecrã **Sobre.**

### <a name="feedback-prompts-for-the-company-portal-app-for-android--1165249--"></a>Pedidos de comentários sobre a aplicação Portal da Empresa para Android<!--1165249-->
A aplicação Portal da Empresa para Android solicita agora comentários aos utilizadores finais. Este feedback é enviado diretamente para a Microsoft e proporciona aos utilizadores finais a oportunidade de reverem a aplicação na Google Play Store pública. Os comentários não são obrigatórios e podem ser dispensados facilmente para os utilizadores poderem continuar a utilizar a aplicação.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android---1573324-1573150-1558616-1564878---"></a>Ajudar os utilizadores a resolver problemas com a aplicação Portal da Empresa para Android<!-- 1573324, 1573150, 1558616, 1564878 -->

A aplicação Portal da Empresa para Android adicionou instruções para ajudar os utilizadores finais a compreender e, sempre que possível, a resolver autonomamente novos casos de utilização.
- Os utilizadores finais serão encaminhados para o [portal do Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) para remover um dispositivo se tiverem atingido o número máximo de dispositivos que estão autorizados a adicionar.
- Os utilizadores finais recebem uma lista de passos a seguir para os ajudar a [corrigir erros de ativação em dispositivos Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) ou a [desativar o modo de poupança de energia](/intune-user-help/power-saving-mode-android). Se nenhuma dessas soluções resolver o problema, forneceremos uma explicação sobre como [enviar registos para a Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices---1583480---"></a>Nova ação “Resolver” disponível para dispositivos Android<!-- 1583480 -->

A aplicação Portal da Empresa para Android está a introduzir a ação "Resolver" na página _Atualizar definições do dispositivo_. A seleção desta opção levará o utilizador diretamente para a definição que está a fazer com que o dispositivo não esteja em conformidade. A aplicação Portal da Empresa para Android suporta atualmente esta ação para as definições de [código de acesso do dispositivo](/intune-user-help/set-your-pin-or-password-android), [depuração de USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [Origens Desconhecidas](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal---1565657---"></a>Indicador de progresso da configuração do dispositivo no Portal da Empresa para Android<!-- 1565657 -->
A aplicação Portal da Empresa para Android mostra um indicador de progresso da configuração do dispositivo quando um utilizador está a inscrever o dispositivo. O indicador mostra novos estados, a começar por “A configurar o dispositivo…”, seguido de “A registar o dispositivo…”, “A concluir o registo do dispositivo...” e “A concluir a configuração do dispositivo...”.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios--1029830--"></a>Suporte para a autenticação baseada em certificados no Portal da Empresa para iOS<!--1029830-->
Adicionámos o suporte para a autenticação baseada em certificados (CBA) na aplicação Portal da Empresa para iOS. Os utilizadores com CBA devem introduzir o seu nome de utilizador e, em seguida, tocar na ligação "Iniciar sessão com um certificado". A CBA já é suportada na aplicação Portal da Empresa para Android e Windows. Pode obter mais informações na página [Iniciar sessão na aplicação Portal da Empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment---1334712---"></a>As aplicações que estão disponíveis com ou sem inscrição podem agora ser instaladas sem qualquer pedido de inscrição.<!-- 1334712 -->

As aplicações da empresa que foram disponibilizadas com ou sem inscrição na aplicação Portal da Empresa para Android já podem ser instaladas sem qualquer pedido de inscrição.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617----"></a>Suporte do Programa Windows AutoPilot Deployment no Microsoft Intune <!-- 747617  -->
Agora pode utilizar o Microsoft Intune com o Programa Windows AutoPilot Deployment para permitir que os utilizadores aprovisionem os respetivos dispositivos da empresa sem envolver o departamento de TI. Pode personalizar a configuração inicial (OOBE) e guiar os utilizadores para associarem os respetivos dispositivos ao Azure AD e inscrevê-los no Intune. Ao trabalharem em conjunto, o Microsoft Intune e o Windows AutoPilot eliminam a necessidade de implementar, manter e gerir imagens de sistema operativo. Para obter detalhes, veja [Enroll Windows devices using Windows AutoPilot Deployment Program (Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment)](../enrollment/enrollment-autopilot.md).

### <a name="quickstart-for-device-enrollment----1425655---"></a>Guia de introdução da inscrição de dispositivos <!-- 1425655 --> 
O guia de introdução está agora disponível em **Inscrição de dispositivos** e fornece uma tabela de referência para gerir plataformas e configurar o processo de inscrição. Uma breve descrição de cada item e as ligações para documentos com instruções passo a passo fornecem documentos úteis para simplificar a introdução.

### <a name="device-categorization---1427491---"></a>Categorização de dispositivos<!-- 1427491 -->
O gráfico da plataforma de dispositivos inscritos do painel **Dispositivos > Descrição Geral** organiza os dispositivos por plataforma, incluindo Android, iOS, macOS, Windows e Windows Mobile.  Os dispositivos com outros sistemas operativos são agrupados em "Outro".  Isto inclui dispositivos fabricados pela Blackberry, NOKIA, entre outros.  

Para saber quais são os dispositivos afetados no seu inquilino, selecione **Gerir > Todos os dispositivos** e, em seguida, utilize o **Filtro** para limitar o campo **SO**.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis  <!-- 954681 -->  
Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Zimperium, uma solução de defesa contra ameaças móveis que se integra ao Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune
O risco é avaliado com base na telemetria recolhida dos dispositivos a executar o Zimperium. Você pode configurar políticas de acesso condicional do EMS com base na avaliação de risco do Zimperium habilitada por meio das políticas de conformidade do dispositivo do Intune, que você pode usar para permitir ou bloquear dispositivos sem conformidade para acessar recursos corporativos com base em ameaças detectadas.

### <a name="new-settings-for-windows-10-device-restriction-profile-----978575-1308849---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 <!--- 978575, 1308849, -->  
Estamos a adicionar novas definições ao perfil de restrição de dispositivos com o Windows 10 na categoria Windows Defender SmartScreen.

Para obter detalhes sobre o perfil de restrição de dispositivos com o Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos com o Windows 10 e posterior)](../configuration/device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Suporte remoto para dispositivos Windows e Windows Mobile  <!-- 1070473 -->  
O Intune pode utilizar o software [TeamViewer](https://www.teamviewer.com), comprado separadamente, para lhe permitir disponibilizar assistência remota aos utilizadores com o Windows e dispositivos Windows Mobile.

### <a name="scan-devices-with-windows-defender---1280988--1280990-----"></a>Analisar dispositivos com o Windows Defender<!-- 1280988  1280990   -->
Pode executar uma **Análise rápida**, **Análise completa** e **Atualizar assinaturas** com o Antivírus do Windows Defender em dispositivos Windows 10 geridos. No painel de descrição geral do dispositivo, escolha a ação a executar no dispositivo. Ser-lhe-á pedido para confirmar a ação antes do comando ser enviado para o dispositivo. 

**Análise rápida**: uma análise rápida analisa as localizações onde se inicia o registo do software maligno, tais como chaves do registo e pastas de arranque conhecidas do Windows. Uma análise rápida demora cerca de cinco minutos. Combinada com a definição **Proteção em tempo real sempre ativada**, que analisa os ficheiros quando são abertos, quando são fechados e sempre que um utilizador navega para uma pasta, a análise rápida ajuda a fornecer proteção contra software maligno que poderá estar no sistema ou no kernel. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Análise completa**: pode ser útil uma análise completa em dispositivos que encontraram uma ameaça de software maligno para identificar se existem componentes inativos que requerem uma limpeza mais detalhada- É também útil para executar análises a pedido. Uma análise completa pode demorar cerca de uma hora. Os utilizadores veem os resultados da análise nos dispositivos ao terminar. 

**Atualizar assinaturas**: o comando de atualização de assinaturas atualiza as definições e as assinaturas do software maligno do Windows Defender Antivirus. Este comando ajuda a garantir que o Windows Defender Antivirus é eficaz na deteção de software maligno. Esta funcionalidade destina-se apenas a dispositivos Windows 10, com ligação à Internet dos dispositivos pendente. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal----1400455---"></a>O botão Ativar/Desativar removido da página Autoridade de Certificação do Intune do portal do Azure no Intune <!-- 1400455 -->
 Vamos eliminar um passo extra na configuração do Certificate Connector no Intune. Neste momento, pode transferir o Certificate Connector e, em seguida, ativá-lo na consola do Intune. No entanto, se desativar o conector na consola do Intune, este continuará a emitir certificados.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
A partir de outubro, o botão Ativar/Desativar deixará de ser apresentado na página Autoridade de Certificação no portal do Azure. A funcionalidade do conector permanece igual. Os certificados continuam a ser implementados nos dispositivos inscritos no Intune. Pode continuar a transferir e instalar o Certificate Connector. Para interromper a emissão de certificados, desinstale o Certificate Connector em vez de o desativar.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se tiver o Certificate Connector desativado, deve desinstalá-lo.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838---"></a>Novas definições para o perfil de restrição de dispositivos Windows 10 Team  <!--- 1308838 -->
Nesta versão, adicionámos muitas definições novas ao perfil de restrição de dispositivos Windows 10 Team para ajudar a controlar os dispositivos Surface Hub.

Para obter mais informações sobre este perfil, veja [Definições de restrição de dispositivos Windows 10 Team](../configuration/device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Impedir que os utilizadores de dispositivos Android alterem a data e a hora dos dispositivos <!-- 1333292 -->
Pode utilizar uma [política de dispositivo personalizada do Android](../configuration/custom-settings-android.md) para impedir que os utilizadores de dispositivos Android alterem a data e a hora do dispositivo.

Para tal, configure uma política personalizada do Android com a definição URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Defina esta opção como **TRUE**e, em seguida, atribua-a aos grupos necessários.

### <a name="bitlocker-device-configuration---1397398---"></a>Configuração do dispositivo BitLocker<!-- 1397398 -->
A opção **Encriptação Windows > Definições Base** inclui uma nova definição **Aviso para a encriptação de outro disco**, que permitirá desativar o [pedido de aviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption) para a encriptação de outro disco que poderá estar em utilização no dispositivo do utilizador.  A mensagem de aviso necessita de consentimento do utilizador final para configurar o BitLocker no dispositivo e bloqueia a configuração do BitLocker até confirmação do utilizador final.  A nova definição desativa o aviso do utilizador final.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant---800882---"></a>As aplicações do Volume Purchase Program for Business serão agora sincronizadas com o Inquilino do Intune<!-- 800882 -->  
Os programadores de terceiros podem distribuir em privado aplicações aos membros autorizados do Volume Purchase Program (VPP) for Business especificados no iTunes Connect. Estes membros do VPP for Business podem iniciar sessão na Loja de Aplicações do Volume Purchase Program e comprar as suas aplicações.

Com esta versão, as aplicações do VPP for Business compradas pelo utilizador final começarão a sincronizar com os respetivos inquilinos do Intune.

### <a name="select-apple-countryregion-store-to-sync-vpp-apps----1332311---"></a>Selecione o repositório de país/região da Apple para sincronizar aplicativos VPP <!-- 1332311 -->  
Você pode configurar o repositório de país/região do VPP (Volume Purchase Program) ao carregar seu token de VPP. O Intune sincroniza aplicativos VPP para todas as localidades do repositório de país/região do VPP especificado.

> [!NOTE]  
> Hoje, o Intune sincroniza apenas os aplicativos VPP do repositório de país/região VPP que correspondem à localidade do Intune na qual o locatário do Intune foi criado.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work---1098994---"></a>Bloquear ações “copiar e colar” entre perfis de trabalho e pessoais no Android for Work<!-- 1098994 -->
Com esta versão, pode configurar o perfil de trabalho do Android for Work para bloquear as ações de copiar e colar entre aplicações pessoais e de trabalho. Pode encontrar esta nova definição no perfil **Restrições do dispositivo** da Plataforma **Android for Work** em **Definições do perfil de trabalho**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores---1281692---"></a>Criar aplicações iOS limitadas a Lojas de Aplicações da Apple regionais específicas<!-- 1281692 -->
Você poderá especificar a localidade do país/região durante a criação de um aplicativo gerenciado da Apple App Store.

> [!Note]  
> No momento, você só pode criar aplicativos gerenciados da Apple App Store que estejam presentes no armazenamento de país/região dos EUA.

### <a name="update-ios-vpp-user-and-device-licensed-apps----1305564---"></a>Atualizar as aplicações licenciadas de dispositivos e o utilizador do VPP para iOS <!-- 1305564 -->  
Poderá configurar o token VPP para iOS para atualizar todas as aplicações compradas para esse token através do serviço Intune. O Intune vai detetar as atualizações de aplicações VPP no interior da loja de aplicações e emiti-las automaticamente para o dispositivo quando este entra.

Para obter passos para configurar um token VPP e ativar as atualizações automáticas, veja [Como gerir aplicações iOS compradas através de um programa de compra em grandes volumes com o Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model---1187917---"></a>Coleção de entidades de associação de dispositivos do utilizador adicionada ao modelo de dados Data Warehouse do Intune<!-- 1187917 -->
Agora pode criar relatórios e visualizações de dados com as informações de associação de dispositivos do utilizador que associam o utilizador às coleções de dispositivos de entidades. Pode aceder ao modelo de dados através do ficheiro do Power BI (PBIX) obtido na página do Intune do Armazém de Dados, através do ponto final do OData ou ao desenvolver um cliente personalizado.

### <a name="review-policy-compliance-for-windows-10-update-rings---1067886---"></a>Rever a conformidade das políticas das cadências de atualizações do Windows 10<!-- 1067886 -->
Poderá rever um relatório das políticas das cadências de atualização do Windows 10 em Atualizações de software > Por estado de implementação da cadência de atualização. O relatório das políticas inclui o estado de implementação das cadências de atualização configuradas. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions-----1352223---"></a>Novo relatório que indica os dispositivos iOS com versões mais antigas do iOS  <!-- 1352223 -->
O relatório **Dispositivos iOS desatualizados** está disponível na área de trabalho **Atualizações de software**. No relatório, poderá ver uma lista dos dispositivos iOS supervisionados que foram abrangidos por uma política de atualização iOS com atualizações disponíveis. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Ver as atribuições de políticas de proteção de aplicações para resolução de problemas<!--  1475003 -->
Nesta versão futura, a opção **Política de proteção de aplicações** será adicionada a **Atribuições**, na lista pendente disponível no painel de resolução de problemas. Agora, pode selecionar as políticas de proteção de aplicações para ver as políticas de proteção de aplicações que foram atribuídas aos utilizadores selecionados.



### <a name="improvements-to-device-setup-workflow-in-company-portal--1490692--"></a>Melhorias no fluxo de trabalho da configuração de dispositivos no Portal da Empresa<!--1490692-->
Melhorámos o fluxo de trabalho da configuração de dispositivos na aplicação Portal da Empresa para Android. O tipo de linguagem é mais simples e específico para a sua empresa. Além disso, combinámos os ecrãs sempre que possível. Pode ver estas melhorias na página [Novidades na IU da aplicação](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices--1484985--"></a>Orientação melhorada no pedido de acesso aos contactos em dispositivos Android<!--1484985-->

A aplicação Portal da Empresa para Android exige frequentemente que o utilizador final aceite as permissões de Contactos. Se um usuário final recusar esse acesso, ele agora verá uma notificação no aplicativo que o alertará para conceder a ele o acesso condicional. 

### <a name="secure-startup-remediation-for-android--1490712--"></a>Remediação de arranque seguro para Android<!--1490712-->

Os utilizadores finais com dispositivos Android poderão tocar no motivo de não conformidade na aplicação Portal da Empresa. Sempre que possível, esta ação irá reencaminhá-lo para a localização correta na aplicação de definições para resolver o problema. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo--1475932--"></a>Notificações push adicionais para utilizadores finais na aplicação Portal da Empresa para Android Oreo<!--1475932-->

Os utilizadores finais receberão notificações adicionais a indicar quando a aplicação Portal da Empresa para Android Oreo está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune. Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas nos respetivos dispositivos. Isto faz parte da [otimização geral da IU do Portal da Empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) para a aplicação Portal da Empresa para Android Oreo. 

Existem mais otimizações para novos elementos da IU que estão ativadas no Android Oreo.  Os utilizadores finais receberão notificações adicionais a indicar quando o Portal da Empresa está a efetuar tarefas em segundo plano, como a obtenção de políticas do serviço do Intune.  Isto aumenta a transparência para os utilizadores finais sobre quando o Portal da Empresa está a efetuar tarefas administrativas no dispositivo.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles---1485783---"></a>Novos comportamentos para a aplicação Portal da Empresa para Android com perfis de trabalho<!-- 1485783 -->

Quando inscreve um dispositivo Android for Work num perfil de trabalho, é a aplicação Portal da Empresa no perfil de trabalho que executa as tarefas de gestão no dispositivo. 

Se estiver a utilizar uma aplicação ativada para MAM no perfil pessoal, a aplicação Portal da Empresa para Android já não terá qualquer utilidade. Para melhorar a experiência do perfil de trabalho, o Intune ocultará automaticamente a aplicação Portal da Empresa depois de inscrever com sucesso o perfil de trabalho.

A aplicação Portal da Empresa para Android pode ser ativada em qualquer altura no perfil pessoal. para tal, navegue para o [Portal da Empresa na Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e toque em **Ativar**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode--1428681--"></a>Mudança do Portal da Empresa para Windows 8.1 e do Windows Phone 8.1 para o modo de suporte<!--1428681-->

A partir de outubro de 2017, as aplicações Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 irão passar para o modo de suporte, o que significa que as aplicações e os cenários existentes, tais como inscrição e conformidade, continuarão a ter suporte nestas plataformas. Estas aplicações continuarão a estar disponíveis para transferência através dos canais de lançamento existentes, tais como a Loja Microsoft. 

Quando estiverem no modo de suporte, estas aplicações receberão apenas atualizações de segurança críticas. Não haverá quaisquer atualizações ou funcionalidades adicionais para estas aplicações. Para obter novas funcionalidades, recomendamos que atualize os dispositivos para Windows 10 ou Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Bloquear a inscrição de dispositivos Samsung Knox não suportados <!-- 1490695 -->

A aplicação Portal da Empresa apenas tenta inscrever dispositivos Samsung Knox suportados. Para evitar erros de ativação Knox que impeçam a inscrição MDM, a tentativa de inscrição do dispositivo só será realizada se o dispositivo aparecer na [lista de dispositivos publicados pela Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Os dispositivos Samsung poderão ter números de modelo compatíveis ou não com o Knox. Verifique a compatibilidade com o Knox junto do revendedor do seu dispositivo antes da compra e implementação. Poderá encontrar a lista completa de dispositivos verificados nas [Definições da política para Android e Samsung Knox Standard](supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower---1171126-1326920---"></a>Fim do suporte para Android 4.3 e anterior<!-- 1171126, 1326920 -->
As aplicações geridas e a aplicação Portal da Empresa para Android precisarão do Android 4.4 e superior para aceder a recursos empresariais. Até dezembro, todos os dispositivos inscritos serão retirados à força, resultando na perda do acesso aos recursos empresariais. Se estiver a utilizar políticas de proteção de aplicações sem MDM, as aplicações não receberão atualizações e a qualidade da experiência irá diminuir ao longo do tempo.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices--1165314--"></a>Informar os utilizadores finais acerca das informações do dispositivo que podem ser vistas nos dispositivos inscritos<!--1165314-->
Iremos adicionar o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo em todas as aplicações Portal da Empresa. Isto permitirá aos utilizadores saber mais sobre a privacidade diretamente a partir do artigo [Que informações pode a sua empresa ver?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Isto será implementado em todas as aplicações Portal da Empresa brevemente. Anunciámos esta funcionalidade para iOS em [setembro](#september-2017).

<!-- ########################## -->
## <a name="september-2017"></a>Setembro de 2017

### <a name="intune-supports-ios-11--1428975--"></a>O Intune suporta o iOS 11<!--1428975-->
O Intune suporta o iOS 11. Isto foi anteriormente anunciado no [blogue de Suporte do Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80---1164477---"></a>Fim do suporte para iOS 8.0<!-- 1164477 -->
As aplicações geridas e a aplicação Portal da Empresa para iOS precisarão do iOS 9.0 e superior para aceder aos recursos empresariais. Os dispositivos que não forem atualizados antes de setembro deixarão de poder aceder ao Portal da Empresa ou a essas aplicações. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10--1132468--"></a>Ação “atualizar” adicionada à aplicação Portal da Empresa para Windows 10<!--1132468-->
A aplicação Portal da Empresa para Windows 10 permite aos utilizadores atualizar os dados na aplicação, ao pedir para atualizar ou, em computadores, ao premir F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios--739894--"></a>Informar os utilizadores finais acerca das informações do dispositivo que podem ser vistas no iOS<!--739894-->

Adicionámos o **Tipo de Propriedade** ao ecrã Detalhes do Dispositivo na aplicação Portal da Empresa para iOS. Isso permitirá que os usuários obtenham mais informações sobre privacidade diretamente desta página nos documentos do usuário final do Intune. Eles também poderão localizar essas informações na tela sobre.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment---1169910---"></a>Permitir que os utilizadores finais acedam à aplicação Portal da Empresa para Android sem inscrição<!---1169910--->

Em breve, os utilizadores finais não terão de inscrever os dispositivos para aceder à aplicação Portal da Empresa para Android. Os utilizadores finais em organizações que utilizam Políticas de Proteção de Aplicações deixarão de receber pedidos para inscrever os dispositivos quando abrem a aplicação Portal da Empresa. Os utilizadores finais também poderão instalar aplicações a partir do Portal da Empresa sem inscrever o dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android---1396349---"></a>Linguagem de compreensão mais fácil na aplicação Portal da Empresa para Android<!---1396349--->  

O texto do processo de inscrição da aplicação Portal da Empresa para Android foi simplificado para facilitar a inscrição dos utilizadores finais. Se tiver documentação de inscrição personalizada, deve atualizá-la para refletir os novos ecrãs. Poderá encontrar imagens de exemplo na nossa página de [Atualização da IU para aplicações de utilizadores finais do Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy---677129---"></a>Aplicação Portal da Empresa do Windows 10 adicionada à política de permissão do Windows Information Protection<!-- 677129 -->

A aplicação Portal da Empresa do Windows 10 foi atualizada para suportar o Windows Information Protection (WIP). A aplicação pode ser adicionada à política de permissão do WIP. Com esta alteração, a aplicação já não tem de ser adicionada à lista **Excluídas**.


<!-- ########################## -->
## <a name="august-2017"></a>Agosto de 2017

### <a name="improvements-to-device-overview---1404453---"></a>Melhorias na descrição geral do dispositivo<!-- 1404453 -->  
As melhorias na descrição geral do dispositivo apresentam agora os dispositivos inscritos, mas excluem os dispositivos geridos pelo Exchange ActiveSync. Os dispositivos do Exchange ActiveSync não têm as mesmas opções de gestão que os dispositivos inscritos. Para ver o número de dispositivos inscritos e o número de dispositivos inscritos por plataforma, no Intune, no portal do Azure, aceda a **Dispositivos** > **Descrição Geral**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Melhorias no inventário de dispositivos recolhido pelo Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
Neste lançamento, fizemos as seguintes melhorias às informações do inventário recolhido pelos dispositivos que gere:
 
- Em dispositivos Android, pode agora adicionar uma coluna ao inventário do dispositivo que mostra o nível de atualização mais recente para cada dispositivo. Adicione a coluna **Nível de atualização de segurança** à sua lista de dispositivos para ver isto.
- Quando filtrar a vista do dispositivo, agora pode filtrar dispositivos pela sua data de inscrição. Por exemplo, pode apresentar apenas dispositivos que foram inscritos após uma data especificada por si.
- Melhorámos o filtro utilizado pelo item **Data do Último Registo**.
- Na lista de dispositivos, agora pode ver o número de telemóvel dos dispositivos pertencentes à empresa.
Além disso, pode utilizar o painel de filtros para procurar dispositivos por número de telemóvel.

Para obter mais detalhes sobre o inventário de dispositivos, veja [Como ver o inventário de dispositivos do Intune](../remote-actions/device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Suporte a acesso condicional para dispositivos macOS 
<!-- 720172 -->
Agora você pode definir uma política de acesso condicional que exige que dispositivos Mac sejam registrados no Intune e estejam em conformidade com suas políticas de conformidade do dispositivo. Por exemplo, os utilizadores podem transferir a aplicação Portal da Empresa do Intune para macOS e inscrever os dispositivos Mac no Intune. O Intune avalia se o dispositivo Mac está ou não em conformidade com os requisitos, tal como o PIN, versão do SO e Integridade do Sistema.

- Saiba mais sobre o suporte de [Acesso Condicional para dispositivos macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview---1484796---"></a>A aplicação Portal da Empresa para macOS está em pré-visualização pública<!---1484796--->
O aplicativo Portal da Empresa para macOS agora está disponível como parte da visualização pública para acesso condicional no Enterprise Mobility + Security. Esta versão suporta o macOS 10.11 e posterior. Obtenha-a em [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Novas definições de restrição de dispositivos para Windows 10    
<!--1063965, 1308850  -->
Nesta versão, adicionámos novas definições ao [perfil de restrição de dispositivos Windows 10](/intune/device-restrictions-windows-10) nas seguintes categorias:

- Windows Defender SmartScreen
- Loja de aplicações

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Atualizações ao perfil de dispositivo de proteção de ponto final do Windows 10 para as definições do BitLocker
<!--1459533 -->    
Neste lançamento, fizemos as seguintes melhorias à forma como as definições do BitLocker funcionam num perfil de dispositivo de proteção de ponto final do Windows 10:
 
- Sob as definições de **unidade BitLocker OS**, para a definição **BitLocker com chip TPM não compatível**, quando selecionar O **Bloco**, anteriormente, isso faria com que o BitLocker fosse realmente permitido. Corrigimos isto para que o BitLocker seja bloqueado quando a opção é selecionada.
- No âmbito das definições de **unidade BitLocker OS,** para o agente de **recuperação de dados baseado em Certificados,** pode agora bloquear explicitamente o agente de recuperação de dados baseado em certificados. No entanto, por predefinição, o agente é permitido.
- Em **Definições de unidades de dados fixas do BitLocker**, na definição **Agente de recuperação de dados**, pode agora bloquear explicitamente o agente de recuperação de dados.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](../protect/endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users---621669---"></a>Nova experiência de início de sessão para utilizadores do Portal da Empresa para Android e das Políticas de Proteção de Aplicações<!-- 621669 -->
Os utilizadores finais podem agora procurar aplicações, gerir dispositivos e ver informações de contacto de TI com a aplicação Portal da Empresa para Android sem inscrever os respetivos dispositivos Android. Além disso, se um utilizador final já utilizar uma aplicação protegida por Políticas de Proteção de Aplicações do Intune e iniciar o Portal da Empresa para Android, deixará de receber um pedido para inscrever o dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization--1405990--"></a>Nova definição para ativar e desativar a otimização da bateria na aplicação Portal da Empresa para Android<!--1405990-->
A página **Definições** na aplicação Portal da Empresa para Android tem uma nova definição para permitir aos utilizadores desativar facilmente a otimização da bateria para as aplicações Microsoft Authenticator e Portal da Empresa. O nome da aplicação apresentado na definição irá variar consoante a aplicação que gere a conta profissional. Recomendamos que os utilizadores desativem a otimização da bateria para melhorar o desempenho das aplicações de trabalho que sincronizam e-mails e dados. 

### <a name="multi-identity-support-for-onenote-for-ios--------1234281---"></a>Suporte de várias identidades do OneNote para iOS     <!-- 1234281 -->
Os utilizadores finais podem agora utilizar contas diferentes (profissionais e pessoais) com o Microsoft OneNote para iOS. As políticas de proteção de aplicações podem ser aplicadas a dados empresariais em blocos de notas de trabalho sem afetar os blocos de notas pessoais. Por exemplo, uma política pode permitir que um utilizador encontre informações em blocos de notas de trabalho, mas impedir que o utilizador copie e cole dados empresariais do bloco de notas de trabalho num bloco de notas pessoal.
 
- Saiba mais sobre as aplicações que suportam a [proteção de aplicações e várias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) com o Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Novas definições para permitir e bloquear aplicações em dispositivos Samsung Knox Standard
<!-- 1305423 822899-->  
Neste lançamento, estamos a adicionar novas [definições de restrição de dispositivos](../configuration/device-restrictions-android.md) que lhe permitem especificar as seguintes listas de aplicações:
 
- Aplicações que os utilizadores têm permissão para instalar
- Aplicações que os utilizadores não têm permissão para executar
- Aplicações que estão ocultas do utilizador no dispositivo
 
Pode especificar a aplicação pelo URL, nome do pacote ou da lista de aplicações que gere.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Novo link de interface do usuário da política de acesso condicional com base no aplicativo do Azure AD do Intune
<!-- 1016201 -->
Agora, os administradores de ti podem definir políticas condicionais baseadas em aplicativo por meio da nova interface de acesso condicional na carga de trabalho do Azure AD. O acesso condicional com base no aplicativo que está na seção Proteção de Aplicativo do Intune na portal do Azure permanecerá lá por enquanto e será imposto lado a lado). Também há um link de conveniência para a nova interface de usuário da política de acesso condicional na carga de trabalho do Intune.

- Saiba mais sobre [o acesso condicional baseado em aplicativos em Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

<!-- ########################## -->
## <a name="july-2017"></a>Julho de 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256--1245463----"></a>Restringir a inscrição de dispositivos Android e iOS pela versão do SO <!--- 1333256,  1245463 --->
O Intune suporta agora a restrição da inscrição do iOS e Android pelo número da versão do sistema operativo. Em **Restrição do Tipo de Dispositivo**, o administrador de TI poderá definir uma configuração de plataforma para restringir a inscrição entre o valor do sistema operativo mínimo e o máximo. As versões do sistema operativo Android têm de ser especificadas como Major.Minor.Build.Rev, em que Minor, Build e Rev são opcionais. As versões iOS têm de ser especificadas como Major.Minor.Build em que Minor e Build são opcionais. Saiba mais sobre as [restrições de inscrição de dispositivos](../enrollment/enrollment-restrictions-set.md).

>[!NOTE]
>Não restringe a inscrição através dos programas de inscrição da Apple ou do Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272--1333275-1245709----"></a>Restringir a inscrição de dispositivos pessoais Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
O Intune pode restringir a inscrição de dispositivos pessoais ao criar uma lista de permissões de números IMEI de dispositivos empresariais. O Intune expandiu esta funcionalidade para iOS, Android e macOS através de números de série de dispositivos. Ao carregar os números de série para o Intune, pode pré-declarar os dispositivos como pertencentes à empresa. Através das restrições de inscrição, pode bloquear dispositivos pessoais (BYOD), permitindo a inscrição apenas para dispositivos pertencentes à empresa. Saiba mais sobre as [restrições de inscrição de dispositivos](../enrollment/enrollment-restrictions-set.md).

Para importar números de série, aceda a **Inscrição de dispositivos** > **Identificadores de dispositivo da empresa** e clique em **Adicionar**. Em seguida, carregue um ficheiro .CSV (nenhum cabeçalho, duas colunas para o número de série e detalhes como números IMEI). Para restringir dispositivos pessoais, aceda a **Inscrição do dispositivo** > **Restrições de inscrição**. Em **Restrições de Tipos de Dispositivos**, selecione **Predefinição** e, em seguida, selecione **Configurações de Plataformas**. Pode **Permitir** ou **Bloquear** dispositivos pessoais para iOS, Android e macOS.


### <a name="new-device-action-to-force-devices-to-sync-with-intune---711369---"></a>Nova ação de dispositivo para forçar os dispositivos a sincronizar com o Intune<!-- 711369 -->
Nesta versão, adicionámos uma nova ação de dispositivo que força o dispositivo selecionado a dar entrada imediatamente no Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo.  Esta ação pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.
Para obter detalhes, veja [Sincronizar dispositivos](../remote-actions/device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update---777100---"></a>Forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes<!-- 777100 -->
Encontra-se disponível uma nova política a partir da área de trabalho Atualizações de software, onde pode forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de software disponíveis mais recentes. Para obter mais detalhes, veja [Configurar as políticas de atualização do iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile – novo parceiro de Defesa Contra Ameaças para Dispositivos Móveis <!-- 954651, 1172027 -->
Você pode controlar o acesso de dispositivos móveis a recursos corporativos usando o acesso condicional com base na avaliação de risco realizada pelo Checkpoint SandBlast Mobile, uma solução de defesa contra ameaças móveis que se integra ao Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Como funciona a integração com o Intune?
O risco é avaliado com base na telemetria recolhida dos dispositivos que executam o CheckPoint SandBlast Mobile. Você pode configurar políticas de acesso condicional do EMS com base no ponto de verificação SandBlast Mobile Risk Assessment habilitado por meio das políticas de conformidade do dispositivo do Intune. Pode permitir ou bloquear o acesso dos dispositivos que não estejam em conformidade aos recursos empresariais, com base nas ameaças detetadas.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business---748101---"></a>Implementar uma aplicação como disponível na Loja Microsoft para Empresas<!-- 748101 -->
Com esta versão, os administradores podem atribuir a Loja Microsoft para Empresas como disponível. Quando é definida como disponível, os utilizadores finais podem instalar a aplicação a partir da aplicação ou site do Portal da Empresa sem serem redirecionados para a Loja Microsoft.

### <a name="ui-updates-to-the-company-portal-website--1313244-part-1--"></a>Atualização da IU do site do Portal da Empresa<!--1313244 part 1-->
Fizemos várias alterações à IU do [site do Portal da Empresa](https://portal.manage.microsoft.com) para melhorar a experiência do utilizador final.

- __Melhorias aos mosaicos das aplicações__: os ícones das aplicações são agora apresentados com um fundo gerado automaticamente com base na cor dominante do ícone (caso seja possível detetar uma). Quando aplicável, este fundo vem substituir o limite cinzento que era apresentado nos mosaicos das aplicações.

    O site do Portal da Empresa apresentará ícones grandes sempre que possível numa próxima versão. Recomendamos que os administradores de TI publiquem aplicações com ícones de alta resolução com o tamanho mínimo de 120 x 120 píxeis. 

- __Alterações de navegação__: os itens da barra de navegação foram movidos para o menu de opções no canto superior esquerdo. A página Categorias foi removida. Os utilizadores podem agora filtrar conteúdos por categoria enquanto navegam.

- __Atualização das Aplicações em Destaque:__ adicionámos ao site uma página dedicada em que os utilizadores podem procurar aplicações que optou por destacar e otimizámos a IU da secção Destaques na home page.

### <a name="ibooks-support-for-the-company-portal-website--1231841--"></a>Suporte para iBooks no site do Portal da Empresa<!--1231841-->
Adicionámos uma página dedicada ao site do Portal da Empresa que permite aos utilizadores procurar e transferir iBooks. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Detalhes adicionais sobre a resolução de problemas do suporte técnico<!---  Applies to 1263399, 1326964, 1341642 --->
O Intune atualizou o ecrã de resolução de problemas e acrescentou mais informações para a equipa de administradores e suporte técnico. Agora pode ver uma tabela **Atribuições**, que resume todas as atribuições do utilizador com base na associação a grupos. Esta lista inclui:
- Aplicações móveis
- Compliance políticas
- Perfis de configuração

Para além disso, a tabela **Dispositivos** agora inclui as colunas **Tipo de associação Azure AD** e **Em conformidade com o Azure AD**. Para obter mais informações, veja [Ajudar os utilizadores na resolução de problemas](../help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Armazém de Dados do Intune (Pré-visualização Pública)
O Armazém de Dados do Intune copia dados diariamente para fornecer uma apresentação do histórico do seu inquilino. Pode aceder a dados através de um ficheiro do Power BI (PBIX), de uma ligação OData compatível com várias ferramentas de análise ou ao interagir com a API REST. Para obter mais informações, veja [Utilizar o Armazém de Dados do Intune](../developer/reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10---676547---"></a>Modos claro e escuro disponíveis para a aplicação Portal da Empresa para Windows 10<!---676547--->
Os utilizadores finais poderão personalizar o modo de cor da aplicação Portal da Empresa para Windows 10. O utilizador pode fazer a alteração na secção Definições da aplicação Portal da Empresa. A alteração será apresentada após o utilizador reiniciar a aplicação. Para a versão 1607 e posterior do Windows 10, o modo de aplicação será predefinido para a definição do sistema. Para a versão 1511 e anterior do Windows 10, o modo de aplicação será predefinido para o modo claro.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10---807046--"></a>Permitir que os utilizadores finais marquem o grupo de dispositivos na aplicação Portal da Empresa para Windows 10<!---807046-->
Os utilizadores finais podem agora selecionar o grupo a que o dispositivo pertence ao marcá-lo diretamente na aplicação Portal da Empresa para Windows 10.

<!-- ########################## -->
## <a name="june-2017"></a>Junho de 2017

### <a name="new-role-based-administration-access-for-intune-admins-----1099990---"></a>Novo acesso de administração baseado em funções para administradores do Intune  <!-- 1099990 -->  
Uma nova função de administrador de acesso condicional está sendo adicionada para exibir, criar, modificar e excluir políticas de acesso condicional do Azure AD. Anteriormente, apenas os administradores globais e os administradores de segurança tinham essa permissão. Os administradores do Intune podem ser concedidos com essa permissão de função para que eles tenham acesso às políticas de acesso condicional.


### <a name="tag-corporate-owned-devices-with-serial-number---1215070---"></a>Marcar dispositivos da empresa com um número de série<!-- 1215070 -->  
Agora, o Intune suporta o carregamento de números de série Android, Mac OS e iOS como Identificadores de Dispositivo da Empresa. Neste momento, não pode utilizar números de série para bloquear a inscrição de dispositivos pessoais, porque os números de série não são verificados durante a inscrição. O bloqueio de dispositivos pessoais pelo número de série será lançado em breve.


### <a name="new-remote-actions-for-ios-devices---854689---"></a>Novas ações remotas para dispositivos iOS<!-- 854689 -->
Nesta versão, adicionámos duas novas ações de dispositivo remoto para dispositivos iPad partilhados que fazem a gestão da aplicação Sala de Aula da Apple:

- [Terminar a sessão do utilizador atual](../remote-actions/device-logout-user.md) – termina a sessão do utilizador atual do dispositivo iOS escolhido.
- [Remover utilizador](../remote-actions/device-remove-user.md) – elimina o utilizador que selecionar da cache local num dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app---1044681---"></a>Suporte para iPads partilhados com a aplicação Classroom para iOS<!-- 1044681 -->
Nesta versão, expandimos o suporte da gestão da aplicação Sala de Aula para iOS para incluir alunos que iniciem sessão em iPads partilhados com o respetivo ID Apple gerido.


### <a name="changes-to-intune-built-in-apps---1332306---"></a>Alterações às aplicações incorporadas do Intune<!-- 1332306 -->
Anteriormente, o Intune continha várias aplicações incorporadas que podia atribuir rapidamente. Com base no seu feedback, removemos esta lista e já não verá as aplicações incorporadas.
No entanto, se já tiver atribuído aplicações incorporadas, as mesmas continuarão visíveis na lista de aplicações. Pode continuar a atribuir estas aplicações conforme necessário.
Numa versão posterior, planeamos adicionar um método mais simples para selecionar e atribuir aplicações incorporadas a partir do portal do Azure.

### <a name="easier-installation-of-office-365-apps----1121362----"></a>Instalação mais fácil das aplicações do Office 365<!--- 1121362 --->
O novo tipo de aplicação do **Office 365 ProPlus** faz com que seja mais fácil atribuir aplicações do Office 365 ProPlus 2016 aos dispositivos que está a gerir que executem a versão mais recente do Windows 10. Além disso, também pode instalar o Microsoft Project e o Microsoft Visio, se tiver licenças dos mesmos. As aplicações que pretende são agrupadas e apresentadas como uma aplicação na lista de aplicações na consola do Intune.
Para obter mais informações, veja [Como adicionar aplicações do Office 365 para Windows 10](../apps/apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business----777044----"></a>Suporte para aplicações offline na Loja Microsoft para Empresas<!--- 777044 --->
As aplicações offline compradas na Loja Microsoft para Empresas serão agora sincronizadas com o portal do Azure. Poderá então implementar essas aplicações para grupos de dispositivos ou grupos de utilizadores. As aplicações offline são instaladas pelo Intune e não pela loja.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps-----1257019---"></a>O Microsoft Teams faz agora parte da lista de aplicações aprovadas para acesso condicional baseado em aplicações  <!-- 1257019 -->
O aplicativo Microsoft Teams para iOS e Android agora faz parte dos aplicativos aprovados para políticas de acesso condicional com base no aplicativo para o Exchange e o SharePoint Online. O aplicativo pode ser configurado por meio da folha Proteção de Aplicativo do Intune na portal do Azure para todos os locatários que estão usando o acesso condicional baseado no aplicativo.

### <a name="managed-browser-and-app-proxy-integration---1287310---"></a>Managed Browser e integração do proxy de aplicações<!-- 1287310 -->
O Intune Managed Browser pode agora ser integrado com o serviço do Proxy de Aplicações do Azure AD para permitir aos utilizadores acederem a sites internos mesmo quando trabalham remotamente. Basta que os utilizadores do browser entrem no URL do site como fariam normalmente e o Managed Browser encaminha o pedido através do gateway Web do proxy de aplicações. Para obter mais informações, veja [Manage Internet access using managed browser policies (Gerir o acesso à Internet através de políticas de browser gerido)](../apps/app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser---682951---"></a>Novas definições de configuração de aplicações para o Intune Managed Browser<!-- 682951 -->
Nesta versão, adicionámos mais configurações à aplicação Intune Managed Browser para iOS e Android. Agora, pode utilizar uma política de configuração de aplicações para configurar a página inicial predefinida e os marcadores para o browser.
Para obter mais informações, veja [Manage Internet access using managed browser policies (Gerir o acesso à Internet através de políticas de browser gerido)](../apps/app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10----951707---"></a>Definições do BitLocker para Windows 10 <!-- 951707 -->
Agora, pode configurar as definições do BitLocker para dispositivos Windows 10 com um novo perfil de dispositivo do Intune. Por exemplo, pode exigir que os dispositivos sejam encriptados e também pode configurar definições adicionais que são aplicadas quando o BitLocker está ativado.
Para obter mais informações, veja [Endpoint protection settings for Windows 10 and later (Definições de proteção de ponto final para o Windows 10 e versões posteriores)](../protect/endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile----978527--978550-978569-1050031-1058611-----"></a>Novas definições para o perfil de restrição de dispositivos Windows 10<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
Nesta versão, adicionámos novas definições ao perfil de restrição de dispositivos Windows 10 nas seguintes categorias:

- Windows Defender
- Rede móvel e conectividade
- Experiência de ecrã bloqueado
- Privacidade
- Procura
- Destaque do Windows
- Browser Microsoft Edge

Para obter mais informações sobre as definições do Windows 10, veja [Windows 10 and later device restriction settings (Definições de restrição de dispositivos Windows 10)](../configuration/device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies--1305217--"></a>A aplicação Portal da Empresa para Android tem agora uma nova experiência de utilizador final para Políticas de Proteção de Aplicações<!--1305217-->
Com base no feedback dos clientes, modificámos a aplicação Portal da Empresa para Android para apresentar o botão **Aceder a Conteúdos da Empresa**. O objetivo é evitar que os utilizadores finais passem desnecessariamente pelo processo de inscrição quando apenas precisarem de acesso a aplicações que suportem Políticas de Proteção de Aplicações, uma funcionalidade da gestão de aplicações móveis do Intune. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal--1164569--"></a>Nova ação de menu para remover facilmente o Portal da Empresa<!--1164569-->
Com base nos comentários dos utilizadores, a aplicação Portal da Empresa para Android adicionou uma nova ação de menu para iniciar a remoção do Portal da Empresa do seu dispositivo. Esta ação remove o dispositivo da gestão do Intune para que a aplicação possa ser removida do dispositivo pelo utilizador. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md) e na [Documentação do utilizador final do Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update--676505--"></a>Melhorias na sincronização da aplicação com a Atualização para Criativos do Windows 10<!--676505-->
A aplicação Portal da Empresa para Windows 10 iniciará agora automaticamente uma sincronização para pedidos de instalação de aplicações para dispositivos com a Atualização para Criativos do Windows 10 (versão 1703). Tal reduzirá o problema da interrupção da instalação de aplicações durante o estado “Sincronização Pendente”. Além disso, os utilizadores poderão iniciar manualmente uma sincronização a partir da própria aplicação. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal---1058938---"></a>Nova experiência orientada para o Portal da Empresa do Windows 10<!---1058938--->
A aplicação Portal da Empresa para Windows 10 vai incluir uma experiência de instruções orientada do Intune para dispositivos que não foram identificados ou inscritos. A nova experiência disponibiliza instruções passo a passo que orientam o utilizador no registo do Azure Active Directory (obrigatório para as funcionalidades de Acesso Condicional) e na inscrição MDM (obrigatória para as funcionalidades de gestão de dispositivos). A experiência guiada estará acessível na página inicial do Portal da Empresa. Os utilizadores podem continuar a utilizar a aplicação se não concluírem o registo e a inscrição, mas terão funcionalidades limitadas.

Esta atualização só é visível em dispositivos com a Atualização de Aniversário do Windows 10 (compilação 1607) ou superior. Pode ver estas alterações na página [Novidades na IU da aplicação](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>As consolas de administração do Microsoft Intune e do Acesso Condicional estão geralmente disponíveis
Estamos a anunciar a disponibilidade geral do novo Intune na consola de administração do portal do Azure e na consola de administração do Acesso Condicional. Através do Intune no portal do Azure, agora pode gerir todas as capacidades de MAM e MDM do Intune numa experiência de administração consolidada e tirar partido do agrupamento e do direcionamento do Azure AD. O acesso condicional no Azure traz recursos avançados entre o Azure AD e o Intune juntos em um console unificado. E, a partir de uma experiência administrativa, a migração para a plataforma do Azure permite que utilize browsers modernos.

O Intune agora está visível sem a etiqueta **pré-visualização** no portal do Azure em portal.azure.com.

Não é necessária nenhuma ação para os clientes existentes no momento, exceto se tiver recebido uma de várias mensagens no centro de mensagens a pedir para tomar uma ação para que possamos migrar os seus grupos. Também pode ter recebido um aviso do centro de mensagens a informar que a migração está a demorar mais tempo devido a erros do nosso lado. Continuaremos a trabalhar diligentemente para migrar qualquer cliente afetado.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Melhorias dos mosaicos de aplicação na aplicação Portal da Empresa para iOS
Atualizamos a estrutura dos mosaicos de aplicação na home page para refletir a cor corporativa que definiu para o Portal da Empresa. Para mais obter informações, veja [Novidades na IU da aplicação](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Seletor de conta agora disponível para a aplicação Portal da Empresa para iOS
Os utilizadores de dispositivos iOS podem ver o nosso novo seletor de conta ao iniciar sessão no Portal da Empresa se utilizarem a conta profissional ou escolar para iniciar sessão noutras aplicações da Microsoft. Para mais obter informações, veja [Novidades na IU da aplicação](whats-new-app-ui.md).

<!-- ########################## -->
## <a name="may-2017"></a>Maio de 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices--1103950--"></a>Alterar a autoridade MDM sem anular a inscrição dos dispositivos geridos<!--1103950-->
Pode agora alterar a autoridade MDM sem ter de contactar o Suporte da Microsoft e sem ter de anular a inscrição e inscrever novamente os seus dispositivos geridos existentes. Na consola do Gestor de Configuração, pode alterar a sua autoridade MDM a partir da opção Definir para o Gestor de Configuração (híbrido) para o Microsoft Intune (autónomo) ou vice-versa.


### <a name="improved-notification-for-samsung-knox-startup-pins--1087143--"></a>Notificação melhorada para os PINs de arranque do Samsung Knox<!--1087143-->
Quando os utilizadores finais têm de definir um PIN de arranque em dispositivos Samsung Knox para ficarem em conformidade com a encriptação, a notificação apresentada aos utilizadores finais vai colocá-los no local exato na aplicação Definições quando toca na notificação.  Anteriormente, a notificação enviava o utilizador final para o ecrã de alteração da palavra-passe.

### <a name="device-enrollment"></a>Inscrição de dispositivos

#### <a name="apple-school-manager-asm-support-with-shared-ipad---748864-770395--"></a>Suporte do Gestor Escolar da Apple (ASM) com iPad partilhado<!-- 748864, 770395-->

O Intune suporta agora a utilização do Gestor de Escola da Apple (ASM) em vez do Programa de Inscrição de Dispositivos Apple para fornecer uma inscrição inicial de dispositivos iOS. A integração do ASM é necessária para utilizar a aplicação Sala de Aula para iPads Partilhados e para ativar a sincronização de dados do ASM no Azure Active Directory através da School Data Sync (SDS) da Microsoft. Para obter mais informações, veja [Ativar a inscrição do dispositivo iOS com o Gestor de Escola da Apple](../enrollment/apple-school-manager-set-up-ios.md).

> [!NOTE]
> A configuração de iPads Partilhados para trabalhar com a aplicação Sala de Aula requer configurações do iOS Education no Azure que ainda não estão disponíveis.  Esta funcionalidade será adicionada em breve.

### <a name="device-management"></a>Gestão de dispositivos

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer---675418---"></a>Fornecer assistência remota em dispositivos Android através do TeamViewer<!-- 675418 -->

O Intune pode agora utilizar o software [TeamViewer](https://www.teamviewer.com), adquirido separadamente, para lhe permitir disponibilizar assistência remota aos seus utilizadores com dispositivos Android. Para obter mais informações, veja [Fornecer assistência remota em dispositivos Android geridos no Intune](../remote-actions/teamviewer-support.md).

### <a name="app-management"></a>Gestão de aplicações

#### <a name="new-app-protection-policies-conditions-for-mam---679864---"></a>Novas condições de políticas de proteção de aplicações para MAM<!-- 679864 -->

Agora pode definir um requisito para a MAM sem utilizadores de inscrição que impõe as seguintes políticas:

- Versão mínima da aplicação
- Versão mínima do sistema operativo
- Versão mínima do SDK da Aplicação Intune da aplicação de destino (apenas iOS)

Esta funcionalidade está disponível no Android e no iOS. O Intune suporta a imposição da versão mínima para versões de plataformas de SO, versões de aplicações e SDK da Aplicação Intune. No iOS, as aplicações com o SDK integrado podem também definir a imposição de uma versão mínima ao nível do SDK. O utilizador não poderá aceder à aplicação de destino se não forem cumpridos os requisitos mínimos através da política de proteção de aplicações nos três níveis diferentes mencionados acima. Neste momento, o utilizador pode remover a conta (para aplicações de várias identidades), fechar a aplicação ou atualizar a versão do SO ou da aplicação.

Também pode configurar definições adicionais para fornecer uma notificação sem bloqueios que recomenda uma atualização da versão do SO ou da aplicação. Esta notificação pode ser fechada e a aplicação pode ser utilizada normalmente.

Para obter mais informações, veja [Definições de políticas de proteção de aplicações iOS](../apps/app-protection-policy-settings-ios.md) e [Definições de políticas de proteção de aplicações Android](../apps/app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work---621621---"></a>Configurar as configurações de aplicações para Android for Work<!-- 621621 -->
Algumas aplicações Android da loja suportam opções de configuração geridas que permitem a um administrador de TI controlar o modo como uma aplicação é executada no perfil de trabalho. Com o Intune, agora pode ver as configurações suportadas por uma aplicação e configurá-las a partir do portal do Azure com um estruturador de configuração ou um editor de JSON. Para obter mais informações, veja [Use app configurations for Android for Work (Utilizar configurações de aplicações para Android for Work)](../apps/app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment---677969---"></a>Nova capacidade de configuração de aplicações para MAM sem inscrição<!-- 677969 -->
Agora pode criar políticas de configuração de aplicações através do MAM sem canal de inscrição. Esta funcionalidade é equivalente às políticas de configuração de aplicações disponíveis na configuração de aplicações de gestão de dispositivos móveis (MDM). Para obter um exemplo de configuração de aplicações através do MAM sem inscrição, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser---682960---"></a>Configurar listas de URLs permitidos e bloqueados para o Managed Browser<!-- 682960 -->
Agora pode configurar uma lista de domínios e URLs permitidos e bloqueados para o Intune Managed Browser utilizando definições de configuração de aplicações no portal do Azure. Estas definições podem ser configuradas independentemente de estarem a ser utilizadas num dispositivo gerido ou não gerido. Para obter mais informações, veja [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view---1069473---"></a>Vista do suporte técnico da política de proteção de aplicações<!-- 1069473 -->
Os utilizadores do Suporte Técnico de TI agora podem verificar o estado da licença do utilizador e o estado da política de proteção de aplicações atribuído aos utilizadores no painel Resolução de Problemas. Para obter detalhes, veja [Resolução de Problemas](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuração do dispositivo

#### <a name="control-website-visits-on-ios-devices---723832---"></a>Controlar as visitas a sites em dispositivos iOS<!-- 723832 -->
Agora pode controlar os sites que os utilizadores dos dispositivos iOS podem visitar através de um destes métodos:

- Adicionar URLs permitidos e bloqueados através do filtro de conteúdo Web incorporado da Apple.

- Permitir o acesso apenas a sites específicos no browser Safari. São criados marcadores no Safari para cada site que especificar.

Para obter mais informações, veja [Definições de filtros de conteúdo Web para dispositivos iOS](../configuration/ios-device-features-settings.md#web-content-filter).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps---621614---"></a>Permissões pré-configuradas de dispositivos para aplicações Android for Work<!-- 621614 -->
Para aplicações implementadas para perfis de trabalho de dispositivos Android for Work, pode agora configurar o estado das permissões para aplicações individuais.  Por predefinição, as aplicações Android que requerem permissões de dispositivos, tal como o acesso à localização ou à câmara do dispositivo, solicitarão aos utilizadores que aceitem ou recusem as permissões.  Por exemplo, se uma aplicação utilizar o microfone do dispositivo, o utilizador final ser solicitado a conceder permissão à aplicação para utilizar o microfone. Esta funcionalidade permite-lhe definir permissões em nome do utilizador final.  Pode configurar permissões para a) recusar automaticamente sem notificar o utilizador, b) aprovar automaticamente sem notificar o utilizador ou c) avisar o utilizador para aceitar ou recusar. Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](../configuration/device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices---728976-1102534---"></a>Definir um PIN específico da aplicação para dispositivos Android for Work<!-- 728976, 1102534 -->
Os dispositivos Android 7.0 e superior com um perfil de trabalho gerido como um dispositivo Android for Work permitem ao administrador definir uma política de código de acesso aplicada apenas a aplicações no perfil de trabalho.  As opções incluem:

- Definir apenas uma política de código de acesso para todos os dispositivos – este é o código de acesso que o utilizador tem de utilizar para desbloquear os dispositivos completos.
- Definir apenas uma política de código de acesso do perfil de trabalho – será pedido aos utilizadores que introduzam um código de acesso sempre que qualquer aplicação no perfil de trabalho for aberta.
- Definir uma política de perfil de trabalho e de dispositivo – o administrador de TI tem a opção de definir uma política de código de acesso do dispositivo e uma política de código de acesso do perfil de trabalho com diferentes níveis de segurança (por exemplo, um PIN de quatro dígitos para desbloquear o dispositivo, mas um PIN de seis dígitos para abrir qualquer aplicação de trabalho).

Para obter mais informações, veja [Definições de restrição de dispositivos Android for Work no Microsoft Intune](../configuration/device-restrictions-android-for-work.md).

> [!NOTE]
> Esta opção só está disponível para o Android 7.0 e superior.  Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os dois PINs definidos no mais forte dos dois.

#### <a name="new-settings-for-windows-10-devices---978585---"></a>Novas definições para dispositivos Windows 10<!-- 978585 -->
Adicionámos novas [Definições de restrição de dispositivos Windows](../configuration/device-restrictions-windows-10.md) que controlam funcionalidades como ligação sem fios, deteção de dispositivos, mudança de tarefas e mensagens de erro do cartão SIM.

#### <a name="updates-to-certificate-configuration---918991-and-823198---"></a>Atualizações à configuração do certificado<!-- 918991 and 823198 -->
Ao criar um perfil de certificado SCEP, para <strong>Formato de nome do requerente</strong>, a opção <strong>Personalizado</strong> está disponível para dispositivos iOS, Android e Windows. Antes desta atualização, o campo <strong>Personalizado</strong> estava disponível apenas para dispositivos iOS. Para obter mais informações, veja [Criar um perfil de certificado SCEP](../protect/certificates-profile-scep.md).

Ao criar um perfil de certificado PKCS, para **Nome alternativo do requerente**, o **atributo Personalizado do Azure AD** está disponível. A opção **Departamento** está disponível quando seleciona o **atributo Personalizado do Azure AD**. Para obter mais informações, veja [criar um perfil de certificado PKCS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode---662059---"></a>Configurar várias aplicações que podem ser executadas quando um dispositivo Android está no modo de quiosque<!-- 662059 -->
Quando um dispositivo Android estava no modo de quiosque, podia apenas configurar anteriormente uma aplicação com permissão para ser executada. Agora pode configurar várias aplicações ao utilizar a ID da aplicação, o URL da loja ou ao selecionar uma aplicação Android que já gere. Para obter mais informações, veja [Definições do modo de quiosque](../configuration/device-restrictions-android.md#kiosk).

<!-- ########################## -->
## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Suporte para gerir a aplicação Sala de Aula da Apple
Já pode gerir a aplicação Sala de Aula do iOS nos dispositivos iPad. Configure a aplicação Sala de Aula no iPad dos professores com os dados corretos da turma e dos estudantes e, em seguida, configure os iPads dos estudantes registados numa turma para que possa controlá-los através da aplicação.
Para obter detalhes, veja [Configure iOS education settings (Configurar as definições de educação do iOS)](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps---621621---"></a>Suporte para opções de configuração gerida em aplicações Android<!-- 621621 -->
As aplicações Android na Play Store que suportam opções de configuração gerida podem agora ser configuradas pelo Intune.  Esta funcionalidade permite às TI ver a lista de valores de configuração suportados por uma aplicação e disponibiliza IU de primeira classe assistida para lhes permitir configurar os valores.

### <a name="new-android-policy-for-complex-pins---722069---"></a>Nova política para PINs complexos do Android<!-- 722069 -->
Pode agora definir um tipo de [palavra-passe](../configuration/device-restrictions-android.md#password) obrigatório de Numérica complexa num perfil de dispositivo Android para dispositivos com o Android 5.0 e superior.  Utilize esta definição para impedir que os utilizadores dos dispositivos criem um PIN que contenha números repetidos ou consecutivos, como 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Suporte adicional para dispositivos Android for Work
- **Gerir definições de palavra-passe e perfil de trabalho**<!-- 612808 -->

  Esta nova política de restrição para dispositivos Android for Work permite-lhe agora gerir as definições de palavra-passe e perfil de trabalho em dispositivos Android for Work geridos por si.

- **Permitir a partilha de dados entre perfis de trabalho e pessoais**<!-- 1045102 -->

Este perfil de restrição para dispositivos Android for Work tem agora novas opções para o ajudar a configurar a partilha de dados entre perfis de trabalho e perfis pessoais.

- **Restringir as ações “copiar e colar” entre perfis de trabalho e pessoais**<!-- 1046094 -->

  Um novo perfil de dispositivo personalizado para dispositivos Android for Work permite-lhe agora decidir se as ações de copiar e colar entre aplicações de trabalho e pessoais são permitidas.

Para obter mais informações, veja [Restrições de dispositivos para Android for Work](../configuration/device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices---1057568---"></a>Atribuir aplicações LOB a dispositivos iOS e Android<!-- 1057568 -->
Agora pode atribuir aplicações de linha de negócio (LOB) para [iOS](../apps/lob-apps-ios.md) (ficheiros .ipa) e [Android](../apps/lob-apps-android.md) (ficheiros .apk) a utilizadores ou dispositivos.


### <a name="new-device-policies-for-ios---723774-723815-723826-723830---"></a>Novas políticas de dispositivos para iOS<!-- 723774, 723815, 723826, 723830 -->
- **Aplicações no Ecrã principal** – controla as aplicações que os utilizadores veem no [Ecrã principal do dispositivo iOS](../configuration/ios-device-features-settings.md#home-screen-layout). Esta política altera o esquema do ecrã principal, mas não implementa aplicações.

- **Ligações a dispositivos AirPrint** – controla os [dispositivos AirPrint](../configuration/ios-device-features-settings.md#airprint) (impressoras de rede) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Ligações a dispositivos AirPlay** – controla os [dispositivos AirPlay](../configuration/ios-device-features-settings.md) (como a Apple TV) aos quais os utilizadores finais do dispositivo iOS se podem ligar.

- **Mensagem de ecrã de bloqueio personalizada** – configura uma mensagem personalizada que os utilizadores verão no ecrã de bloqueio do dispositivo iOS, que substitui a mensagem de ecrã de bloqueio predefinida. Para mais informações, veja [Ativar o modo perdido em dispositivos iOS](../remote-actions/device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps---723767---"></a>Restringir notificações push para aplicações iOS<!-- 723767 -->
Num perfil de restrição para dispositivos do Intune, pode agora configurar as seguintes [definições de notificação](../configuration/ios-device-features-settings.md#app-notifications) para dispositivos iOS:

- Ativar ou desativar notificações por completo para uma aplicação específica.
- Ativar ou desativar notificações para uma aplicação específica na central de notificações.
- Especificar o tipo de alerta: **Nenhum**, **Faixa** ou **Aviso Modal**.
- Especificar se são permitidos emblemas para esta aplicação.
- Especificar se são permitidos sons de notificação.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously---737837---"></a>Configurar que aplicações iOS são executadas no modo de aplicação única autónomo<!-- 737837 -->
Pode agora utilizar um perfil de dispositivo do Intune para configurar os dispositivos iOS para executar aplicações específicas no [modo de aplicação única autónomo](../configuration/device-restrictions-ios.md#autonomous-single-app-mode). Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado para que possa apenas executar essa aplicação. Um exemplo desta funcionalidade é quando configura uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações da aplicação forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices---723765---"></a>Configurar domínios de confiança para navegação Web e de e-mail em dispositivos iOS<!-- 723765 -->
Para um perfil de restrição para dispositivos iOS, pode agora configurar as seguintes [definições de domínio](../configuration/device-restrictions-ios.md#domains):

- **Domínios de e-mail não marcados** – e-mails que o utilizador envia ou recebe que não correspondam aos domínios que especifica aqui serão marcados como não sendo de confiança.

- **Domínios Web geridos** – os documentos transferidos a partir dos URLs que especificar aqui serão considerados como geridos (apenas para Safari).  

- **Domínios de preenchimento automático da palavra-passe do Safari** – os utilizadores podem guardar palavras-passe no Safari apenas de URLs que correspondam aos padrões que especificar aqui. Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado e não configurado para múltiplos utilizadores. (iOS 9.3 e superior)


### <a name="vpp-apps-available-in-ios-company-portal---748782---"></a>Aplicações do VPP disponíveis no Portal da Empresa para iOS<!-- 748782 -->
Pode agora atribuir aos utilizadores finais aplicações iOS compradas em grandes volumes (VPP) como instalações no modo **Disponível**. Os utilizadores finais precisarão de uma conta da Apple Store para instalar a aplicação.

### <a name="synchronize-ebooks-from-apple-vpp-store---800878---"></a>Sincronizar eBooks a partir da Apple VPP Store<!-- 800878 -->
Agora pode [sincronizar livros](../apps/vpp-apps-ios.md) que tenha comprado na loja do Apple Volume Purchase Program com o Intune e atribuí-los aos utilizadores.

### <a name="multi-user-management-for-samsung-knox-standard-devices---971988---"></a>Gestão de vários utilizadores em dispositivos Samsung Knox Standard<!-- 971988 -->
Os dispositivos com o Samsung Knox Standard agora suportam a [gestão de vários utilizadores](../enrollment/android-enroll.md) do Intune. Isto significa que os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure Active Directory e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não.  Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

### <a name="additional-windows-device-restriction-settings---818566---"></a>Mais definições de restrição de dispositivos Windows<!-- 818566 -->
Adicionámos suporte para mais [definições de restrição de dispositivos Windows](../configuration/device-restrictions-windows-10.md), tais como suporte adicional para o browser Microsoft Edge, personalização do ecrã de bloqueio de dispositivos, personalizações do menu Iniciar, imagens de fundo definidas para pesquisas do Destaque do Windows e definição de proxy.

### <a name="multi-user-support-for-windows-10-creators-update---822547---"></a>Suporte para múltiplos utilizadores da Atualização para Criativos do Windows 10<!-- 822547 -->
Adicionamos suporte para a [gestão de vários utilizadores](../enrollment/windows-enroll.md) para dispositivos a executar a Atualização para Criativos do Windows 10 e que estejam associados ao domínio do Azure Active Directory. Tal significa que, quando outros utilizadores padrão iniciarem sessão no dispositivo com as credenciais do Azure AD, receberão as aplicações e as políticas atribuídas aos seus nomes de utilizador. Atualmente, os utilizadores não podem utilizar o Portal da Empresa para cenários de self-service, tais como instalar aplicações.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Funcionalidade Começar do Zero para PCs com Windows 10<!-- 1004830 -->
Está agora disponível uma [ação de dispositivo Fresh Start](../remote-actions/device-fresh-start.md) para PCs com Windows 10.  Ao executar esta ação, as aplicações instaladas no PC são removidas e o PC é automaticamente atualizado para a versão mais recente do Windows. Esta ação pode ajudar a remover aplicações OEM que vêm frequentemente pré-instaladas num PC novo. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação.

### <a name="additional-windows-10-upgrade-paths---903672---"></a>Mais caminhos de atualização do Windows 10<!-- 903672 -->
Agora, pode criar uma [política de atualização de edição para atualizar os dispositivos](../configuration/edition-upgrade-configure-windows-10.md) para as seguintes edições do Windows 10 adicionais:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices---747607---"></a>Inscrever dispositivos Windows 10 em massa<!-- 747607 -->
Agora, pode juntar-se a um grande número de dispositivos que executam a atualização para Criativos do Windows 10 para o Azure Active Directory e o Intune com o Windows Configuration Designer (WCD). Para ativar a [inscrição na MDM em massa](../enrollment/windows-bulk-enroll.md) para o seu inquilino do Azure AD, crie um pacote de aprovisionamento que associe dispositivos ao seu inquilino do Azure AD através do Windows Configuration Designer e aplique o pacote aos dispositivos pertencentes à empresa que pretende inscrever e gerir em massa. Assim que o pacote for aplicado aos dispositivos, estes são associados ao Microsoft Azure AD, inscritos no Intune e estarão prontos para os seus utilizadores do Microsoft Azure AD iniciarem sessão.  Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as políticas atribuídas e as aplicações necessárias. Os cenários Self-service e Portal da Empresa não são atualmente suportados.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations---581122-736644---"></a>Novas definições de MAM para PIN e localizações de armazenamento gerido<!-- 581122, 736644 -->
Estão agora disponíveis duas novas definições de aplicações para o ajudar em cenários de MAM (gestão de aplicações móveis):

- **Desativar o PIN da aplicação quando o PIN do dispositivo for gerido** – deteta se está presente um PIN no dispositivo inscrito e, caso esteja, ignora o PIN da aplicação acionado pelas políticas de proteção da aplicação. Esta definição permitirá reduzir o número de pedidos de PIN quando os utilizadores abrirem uma aplicação com MAM ativada num dispositivo inscrito. Esta funcionalidade está disponível para Android e iOS.

- **Selecionar em que serviços de armazenamento podem ser guardados os dados empresariais** – permite-lhe especificar as localizações de armazenamento onde podem ser guardados dados empresariais. Os utilizadores podem guardar nos serviços de localização de armazenamento selecionados, o que significa que todos os que não estiverem listados serão bloqueados.

  Lista dos serviços de localização de armazenamento:

  - OneDrive para Empresas
  - SharePoint Online
  - Armazenamento local

### <a name="help-desk-troubleshooting-portal---907448---"></a>Portal de resolução de problemas de suporte técnico<!-- 907448 -->
O novo [portal de resolução de problemas](../help-desk-operators.md) permite aos operadores de suporte técnico e aos administradores do Intune verem os utilizadores e os seus dispositivos e executar tarefas para resolver problemas técnicos do Intune.

<!-- ########################## -->
## <a name="march-2017"></a>Março de 2017

### <a name="support-for-ios-lost-mode--431695--"></a>Suporte para o Modo Perdido no iOS<!--431695-->
Para os dispositivos iOS 9.3 e posteriores, o Intune adicionou o suporte para o **Modo Perdido**. Agora, pode bloquear um dispositivo para impedir toda a utilização e apresentar um número de telefone de contacto e uma mensagem no ecrã de bloqueio do dispositivo.

O utilizador final só poderá desbloquear o dispositivo quando um administrador desativar o Modo Perdido. Quando o Modo Perdido está ativado, pode utilizar a ação **Localizar dispositivo** para apresentar a localização geográfica do dispositivo num mapa na consola do Intune.

O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado.

Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](../remote-actions/device-management.md)?

### <a name="improvements-to-device-actions-report--677150--"></a>Melhorias ao relatório Ações de Dispositivos<!--677150-->
Melhoramos o relatório de Ações de Dispositivos para um melhor desempenho. Além disso, agora pode filtrar o relatório por estado. Por exemplo, pode filtrar o relatório para mostrar apenas as ações de dispositivo que foram concluídas.

### <a name="custom-app-categories--748805--"></a>Categorias de aplicações personalizadas<!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](../apps/apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices--748823--"></a>Atribuir aplicações LOB a utilizadores com dispositivos não inscritos<!--748823-->
Agora pode atribuir aplicações de linha de negócio da loja aos utilizadores, quer os respetivos dispositivos estejam ou não inscritos no Intune. Se o dispositivo do utilizador não estiver inscrito no Intune, o utilizador terá de aceder ao site do Portal da Empresa para o instalar, em vez da aplicação Portal da Empresa.

### <a name="new-compliance-reports--846671--"></a>Novos relatórios de conformidade<!--846671-->
Tem agora relatórios de conformidade que lhe dão a postura de conformidade dos dispositivos na sua empresa e lhe permitem rapidamente resolver problemas relacionados com a conformidade encontrados pelos utilizadores. Pode ver informações sobre o

- Estado de conformidade geral dos dispositivos
- Estado de conformidade de uma definição individual
- Estado de conformidade de uma política individual

Também pode utilizar estes relatórios para desagregar um dispositivo individual e ver as definições e políticas específicas que afetam esse dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios--951869--"></a>Acesso direto aos cenários de inscrição da Apple<!--951869-->
Para as contas do Intune criadas depois de janeiro de 2017, o Intune ativou o acesso direto aos cenários de inscrição da Apple através da carga de trabalho Inscrever Dispositivos no portal do Azure. Anteriormente, a pré-visualização da inscrição da Apple apenas estava acessível a partir de ligações no portal do Azure. As contas do Intune criadas antes de Janeiro de 2017 precisam de uma única migração antes de estas funcionalidades ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.


<!-- ########################## -->
## <a name="february-2017"></a>Fevereiro de 2017

### <a name="ability-to-restrict-mobile-device-enrollment--747600-795782--"></a>Capacidade para restringir a inscrição de dispositivos móveis<!--747600, 795782-->
O Intune está a adicionar novas restrições de inscrição que controlam as plataformas de dispositivos móveis autorizadas a inscrever. O Intune separa plataformas de dispositivos móveis como iOS, macOS, Android, Windows e Windows Mobile.

- A restrição da inscrição de dispositivos móveis não restringe a inscrição do cliente de PC.  
- Existe uma opção adicional para bloquear a inscrição de dispositivos pessoais apenas para iOS e Android.

O Intune marca todos os novos dispositivos como pessoais, a menos que o administrador de TI os marque como pertencentes à empresa, conforme explicado [neste artigo](../enrollment/device-enrollment.md).

### <a name="view-all-actions-on-managed-devices--677150--"></a>Ver todas as ações em dispositivos geridos<!--677150-->
Um novo relatório __Ações de Dispositivos__ mostra quem efetuou ações remotas como a reposição de dados de fábrica em dispositivos e o estado dessas ações. Veja [O que é a gestão de dispositivos?](../remote-actions/device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps--664691--"></a>Os dispositivos não geridos podem aceder a aplicações atribuídas<!--664691-->
Como parte das alterações de estrutura no site do Portal da Empresa, os utilizadores de iOS e Android poderão instalar aplicações atribuídas a eles próprios como "disponíveis sem inscrição" nos seus dispositivos não geridos. Com as suas credenciais do Intune, os utilizadores poderão iniciar sessão no site do Portal da Empresa e ver as listas de aplicações atribuídas a eles próprios. Os pacotes de aplicações das aplicações "disponíveis sem inscrição" estão disponíveis para transferência através do site do Portal da Empresa. As aplicações que requerem inscrição para instalação não são afetadas por esta alteração, uma vez que será solicitado aos utilizadores que inscrevam o seu dispositivo se quiserem instalar essas aplicações.

### <a name="custom-app-categories--748805--"></a>Categorias de aplicações personalizadas<!--748805-->
Agora pode criar, editar e atribuir categorias às aplicações que adicionar ao Intune. Atualmente, as categorias só podem ser especificadas em inglês.
Veja [Como adicionar uma aplicação ao Intune](../apps/apps-add.md).

### <a name="display-device-categories--814654--"></a>Mostrar categorias dos dispositivos<!--814654-->
Agora pode ver a categoria do dispositivo como uma coluna na lista de dispositivos. Também pode editar a categoria a partir da secção de propriedades do painel de propriedades do dispositivo. Veja [Como adicionar uma aplicação ao Intune](../apps/apps-add.md).

### <a name="configure-windows-update-for-business-settings--776716--"></a>Configurar definições do Windows Update para Empresas<!--776716-->

O Windows como um Serviço é a nova forma de disponibilizar atualizações para o Windows 10. A partir do Windows 10, todas as novas Atualizações de Funcionalidades e Atualizações de Qualidade irão conter o conteúdo de todas as atualizações anteriores. Tal significa que, desde que instale a atualização mais recente, sabe que os dispositivos Windows 10 estão completamente atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações para não ter de aprovar atualizações individuais para grupos de dispositivos. Pode continuar a gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações e o Windows Update irá garantir que as atualizações são instaladas no momento certo. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem ao Windows Update diretamente para obterem as atualizações. Utilize o Intune para configurar e gerir **anéis de atualização do Windows 10**. Um anel de atualização contém um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Para obter detalhes, veja [Configure Windows Update for Business settings (Configurar definições do Windows Update para Empresas)](../protect/windows-update-for-business-configure.md).
