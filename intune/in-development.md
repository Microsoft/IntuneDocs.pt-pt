---
title: No desenvolvimento – Microsoft Intune
titleSuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910317"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>No desenvolvimento do Microsoft Intune – Maio de 2019

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>A eliminar um dispositivo no portal da Apple será refletida no portal do Intune <!--2489996 -->
Se um dispositivo é eliminado do programa de inscrição de dispositivos da Apple ou a portais de gerente de negócios da Apple, o dispositivo será eliminado automaticamente do Intune durante a sincronização seguinte.

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Suporte de linha de base para a palavra-chave de pesquisa  <!-- 3082036         -->
Ao criar ou editar um perfil de linha de base de segurança, em breve será capaz de usar *pesquisa* para filtrar as definições que são apresentados na consola do.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Repor e apagar dispositivos em massa ao utilizar a Graph API <!-- 3295288 -->
Poderá repor e a eliminação de até 100 dispositivos em massa com a Graph API.

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verifique a existência de um chipset TPM numa política de conformidade de dispositivos Windows 10 <!-- 3617671 -->
Muitos Windows 10 e dispositivos posteriores têm chipsets Trusted Platform Module (TPM). Esta atualização inclui uma nova definição de conformidade que verifica a versão de chip do TPM no dispositivo. 

[Windows 10 e posteriores definições de política de conformidade](compliance-policy-create-windows.md#device-security) descreve esta definição.

Aplica-se a: Windows 10 e posterior

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Scripts de PowerShell de extensão de gestão do Intune  <!-- 3734186    -->
Será capaz de configurar os scripts do PowerShell para executar com privilégios de administrador do utilizador no dispositivo. Para obter mais informações, consulte [scripts do PowerShell de utilização em dispositivos Windows 10 no Intune](intune-management-extension.md).

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>Impedir que os utilizadores finais modificar seus HotSpot pessoal e desativar o registo no iOS dispositivos supervisionados de servidor de Siri <!-- 4097904  --> 
Criar um perfil de restrições de dispositivo no dispositivo iOS (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **iOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização inclui novas definições que pode configurar:

- HotSpot pessoal
- Registo de servidor da Siri

Para ver as definições atuais, aceda à [definições de dispositivos iOS para permitir ou restringir funcionalidades](device-restrictions-ios.md). 

Aplica-se a: iOS 12.2 e mais recentes

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>Nova sala de aula aplicação restrição de dispositivos para dispositivos macOS inscritos em DEP <!-- 4097905  --> 
Pode criar perfis de configuração para dispositivos macOS de dispositivos (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **macOS** para a plataforma > **restrições de dispositivos** para tipo de perfil). Esta atualização inclui novas definições de aplicação de sala de aula para dispositivos inscritos em DEP e a opção para desativar o biblioteca de fotografias do iCloud.

Para ver as definições atuais, aceda à [definições de dispositivos macOS para permitir ou restringir funcionalidades com o Intune](device-restrictions-macos.md).

Aplica-se a: macOS 10.14.4 e mais recentes

### <a name="android-enterprise-app-management----4459905-idready---"></a>Gestão de aplicações do Android Enterprise <!-- 4459905 idready -->
Para tornar mais fácil para os administradores de TI configurar e utilizar a gestão de Android Enterprise, Intune adiciona automaticamente os quatro comuns Android Enterprise relacionadas com aplicações para a consola de administração do Intune. As aplicações do Android Enterprise quatro são os seguintes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)**  - utilizado para cenários do Android Enterprise totalmente gerido.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**  -ajuda a que iniciar sessão para as suas contas se usar a verificação de dois fatores.
- **[Portal da empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)**  - utilizado para as políticas de proteção de aplicações (aplicação) e cenários de perfil de trabalho do Android Enterprise.
- [Gerido home page de tela](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - utilizado para cenários de dedicado/quiosque do Android Enterprise.

Anteriormente, os administradores de TI precisaria manualmente localize e aprove destas aplicações na [loja Google Play gerido](https://play.google.com/store/apps) como parte da configuração. Esta alteração remove esses passos anteriormente manuais para torná-lo mais fácil e rápida para os clientes utilizar a gestão do Android Enterprise.

Os administradores vão ver estas quatro aplicações automaticamente adicionadas à sua lista de aplicações do Intune, no momento que eles ligam pela primeira vez o inquilino do Intune para o Google Play gerido. Para obter mais informações, consulte [ligar a sua conta do Intune à sua conta do Google Play gerido](connect-intune-android-enterprise.md). Para inquilinos que já ligou respetivo inquilino ou que já usam o Android Enterprise, não há nada os administradores precisam de fazer. Essas quatro aplicações aparecerá automaticamente dentro de 7 dias após a conclusão da implementação do serviço de Maio de 2019 horizontalmente.

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Definições avançadas do Firewall do Windows Defender <!-- 1311949 -->
Em breve poderá utilizar o Intune para gerir as regras de firewall personalizadas nos clientes para o Windows Defender. Regras podem especificar o comportamento de entrada e saído para aplicações, endereços de rede e portas. 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Os utilizadores de dispositivos, podem ver todas as aplicações geridas que tenham instalado ou tentou instalar <!-- 2352913 -->
Portal da empresa para Windows irá listar todas as aplicações geridas&ndash; tanto necessária quanto disponível&ndash; que estão instaladas no dispositivo de um utilizador. Os utilizadores serão capazes de vista de tentativa e pendentes instalações de aplicações e respetivos Estados atuais. Se sua organização não torne as aplicações necessárias ou disponíveis, os utilizadores verão uma mensagem que explica que não existem aplicações da empresa foram instaladas. Os utilizadores também serão capazes de classificar ou filtrar as suas aplicações por Estado da instalação.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilize "regras de aplicabilidade" quando criar perfis de configuração de dispositivo Windows 10 <!-- 2549910 -->
Criar perfis de configuração de dispositivo Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma). Poderá criar uma **regra de aplicabilidade** para que o perfil apenas se aplica a uma edição específica ou uma versão específica. Por exemplo, criar um perfil que permite que algumas configurações de disco BitLocker. Depois de adicionar o perfil, utilize uma regra de aplicabilidade para que o perfil apenas se aplica a dispositivos com o Windows 10 Enterprise.

Aplica-se a: 
- Windows 10 e posterior

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tarefas de segurança do Intune para Defender ATP (em pré-visualização pública) <!-- 3208597 -->
Disponível como pré-visualização pública, o Intune em breve adicionará tarefas de segurança para o recentemente anunciado Defender ameaças da Microsoft e gestão de vulnerabilidades.  Com esta integração, os administradores de operações de segurança no ATP do Windows Defender (WDATP) com mais eficiência podem comunicar as remediações recomendadas ameaças emergentes para os administradores do Intune. A adição de tarefas de segurança Adiciona uma abordagem com base no risco para o descobrir, priorizar e remediar vulnerabilidades do ponto final e configurações incorretas.

Para saber mais sobre as tarefas de segurança no Intune, consulte o mensagem de blogue sobre [usar tarefas de segurança do Intune para estender a gestão de vulnerabilidades e ameaças Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Linha de base de proteção de ameaças avançada do Windows Defender <!-- 3754134 -->
Vamos adicionar a nova linha de base para o ajudar a configurar as definições de proteção de ameaças avançada do Windows Defender.



## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


