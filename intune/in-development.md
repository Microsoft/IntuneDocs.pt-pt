---
title: No desenvolvimento – Microsoft Intune
titleSuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
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
ms.openlocfilehash: 004ebad5276575fe9f5b580d13db188f297424fb
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513689"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>No desenvolvimento do Microsoft Intune – Abril de 2019

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

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Definições avançadas do Firewall do Windows Defender <!-- 1311949 -->
Em breve poderá utilizar o Intune para gerir as regras de firewall personalizadas nos clientes para o Windows Defender. Regras podem especificar o comportamento de entrada e saído para aplicações, endereços de rede e portas. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Necessitam de acesso condicional de proteção de aplicações  <!--1634317 -->
Poderá usar *política de proteção de aplicações requerem*, confirma que a política é aplicada a aplicação de um utilizador antes de início de sessão estiver concluída, para impedir que os utilizadores acedam a dados a proteger com o acesso condicional. Enquanto a garantia de política pode retardar a primeira experiência de utilização, ele ajuda a proteger contra problemas de rede, configurações incorretas administrativas ou intencionais esforços para permitem despistar políticas de proteção de aplicações. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurar definições para extensões de kernel em dispositivos macOS <!-- 2043024 -->
Em dispositivos macOS, pode criar um perfil de configuração do dispositivo (**configuração do dispositivo** > **perfis** > **criar perfil** > escolher **macOS** para a plataforma). Um novo grupo de definições permitirá configurar e utilizar extensões de kernel nos seus dispositivos.

Aplica-se a: macOS 10.13.2 e posterior

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


### <a name="ios-third-party-keyboards----4111843---"></a>iOS teclados de terceiros <!-- 4111843 -->
Suporte para a política de proteção de aplicações do Intune (aplicação) para o **teclados de terceiros** definição vai terminar devido a uma alteração de plataforma iOS. Não será capaz de configurar esta definição na consola de administração do Intune e não serão imposto no cliente no SDK da aplicação Intune.

<!-- 1903 start-->

### <a name="windows-update-notifications----3316782---"></a>Notificações de atualização do Windows <!-- 3316782 -->
Estamos a adicionar suporte para as configurações de anel de atualização do Windows para que possa configurar as notificações de atualização do Windows, que os seus utilizadores verão. Esta definição não estará disponível a partir do portal, mas pode ser configurada utilizando a Graph API do Intune.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Facilitar o acesso às definições de diagnóstico <!-- 3804627 -->
Estamos a adicionar uma nova opção para o **registos de auditoria** painel em cada carga de trabalho do Log de auditoria na consola do Intune que pode utilizar para abrir diretamente a *das definições de diagnóstico* página.

## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


