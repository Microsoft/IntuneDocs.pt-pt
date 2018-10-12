---
title: Gestão de dispositivos no Microsoft 365
description: O Microsoft 365 Enterprise inclui o Microsoft Intune. Veja como o Intune permite que a sua organização faça a gestão de dispositivos móveis e a gestão de aplicações móveis, inclusive cenários comuns, e como pode utilizar o Intune para implementar o Microsoft 365 no seu ambiente.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: microsoft-intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.openlocfilehash: 153f49ce0799ed181c9cb904c7c8ed88509805cc
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581840"
---
# <a name="what-is-device-management"></a>O que é a gestão de dispositivos? 

Uma das principais tarefas dos administradores consiste na proteção dos recursos e dados da organização. Esta tarefa é a gestão de dispositivos. Os utilizadores têm muitos dispositivos a partir dos quais abrem e partilham ficheiros pessoais, acedem a sites e instalam aplicações e jogos. Estes utilizadores também são colaboradores e estudantes, pelo que pretendem utilizar os dispositivos para acederem a recursos profissionais e escolares, tais como o e-mail e o OneNote. A *gestão de dispositivos* permite que as organizações protejam os respetivos recursos e dados. 

As organizações podem recorrer a um fornecedor de gestão de dispositivos para garantir que só as pessoas e os dispositivos autorizados podem aceder às informações proprietárias. Da mesma forma, os utilizadores dos dispositivos podem sentir-se à vontade para aceder aos dados de trabalho a partir do telemóvel porque sabem que o dispositivo cumpre os requisitos de segurança da organização. Enquanto organização, poderá perguntar "**o que devemos utilizar para proteger nossos recursos?"**.

É aí que o [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) entra em ação. O Intune oferece gestão de dispositivos móveis (MDM) e gestão de aplicações móveis (MAM). Algumas das principais tarefas das soluções de MDM ou MAM consistem em:

- Suportar um ambiente móvel diverso &mdash; gestão segura de dispositivos iOS, Android, Windows, e macOS
- Garantir que os dispositivos e as aplicações estão em conformidade com os requisitos de segurança da organização
- Criar políticas que ajudem a manter os dados da organização seguros em dispositivos pessoais e pertencentes à empresa
- Utilizar uma solução móvel única e unificada para impor estas políticas e ajudar a gerir dispositivos, aplicações, utilizadores e grupos.

O Intune está incluído no Microsoft 365 e integra-se no Azure Active Directory (Azure AD). O Azure AD ajuda a controlar quem tem acesso e ao que têm acesso.

## <a name="hello-intune"></a>Olá, Intune!
Muitas organizações, tais como a Microsoft, utilizam o Intune para os proteger dados proprietários aos quais os utilizadores acedem a partir de dispositivos móveis pessoais e pertencentes à empresa. O Intune inclui funcionalidades, tais como políticas de configuração de dispositivos e aplicações, políticas de atualização de software e estados de instalação (bem como gráficos, tabelas e relatórios) para ajudar a proteger e monitorizar o acesso aos dados.

Normalmente, as pessoas têm múltiplos dispositivos que utilizam plataformas diferentes. Por exemplo, um colaborador poderá utilizar um Surface Pro em contexto laboral e um dispositivo móvel Android em casa. Também é normal que uma pessoa aceda a recursos organizacionais, tais como o Microsoft Outlook e o SharePoint, a partir desses dispositivos diferentes.

Com o Intune, pode gerir múltiplos dispositivos por pessoa, bem como as diferentes plataformas que são executadas em cada dispositivo, incluindo iOS, macOS, Android e Windows. O Intune separa as políticas e definições por plataforma de dispositivo, pelo que é fácil gerir e ver dispositivos de uma plataforma específica.

Os **[cenários comuns](https://docs.microsoft.com/intune/common-scenarios)** são um ótimo recurso para ver a forma como o Intune responde a perguntas comuns quando trabalha com dispositivos móveis. Encontrará cenários sobre:  
- A proteção de e-mails com o Exchange no local
- O acesso ao Office 365 de forma segura e protegida
- A utilização de dispositivos pessoais para aceder a recursos organizacionais

## <a name="integration-with-secure-and-protect-services"></a>A integração com serviços de proteção
Uma das principais tarefas das soluções de gestão de dispositivos consiste em proporcionar segurança e proteção. O Intune integra-se muito bem com outros serviços para realizar esta tarefa. Por exemplo:

- O **Microsoft 365** é um componente-chave para simplificar tarefas comuns de TI. Se utilizar o Centro de Administração do Microsoft 365, pode criar utilizadores, gerir grupos e obter acesso a outros serviços, tais como o Intune, o Azure Active Directory e mais. Pode, por exemplo, criar um grupo de dispositivos iOS no Microsoft 365. Em seguida, utilize o Intune para enviar políticas para o grupo de dispositivos iOS que incidem em funcionalidades iOS, tais como o acesso à App Store, ao utilizar o AirDrop, fazer cópias de segurança em iCloud, utilizar o filtro Web da Apple e mais.

- O **Windows Defender** inclui muitas funcionalidades de segurança para ajudar a proteger dispositivos com o Windows 10. A utilização conjunta do Intune e do Windows Defender permite, por exemplo: 

    - Ativar o [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) para procurar atividades suspeitas em ficheiros e aplicações em dispositivos móveis 
    - Utilizar a [Proteção Avançada Contra Ameaças do Windows Defender (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) para ajudar a impedir falhas de segurança em dispositivos móveis e a limitar o impacto de uma falha de segurança ao bloquear o acesso de um utilizador aos recursos da empresa.

- O **acesso condicional** é um recurso do Azure Active Directory que se integra muito bem com o Intune. A utilização do [acesso condicional](https://docs.microsoft.com/intune/conditional-access) permite garantir que apenas os dispositivos em conformidade podem aceder ao e-mail, ao SharePoint e a outras aplicações. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Optar pela solução de gestão de dispositivos que mais se adequa à sua situação

Existem duas formas de abordar a gestão de dispositivos. A primeira abordagem consiste na gestão de todos os aspetos dos dispositivos através de todas as funcionalidades incorporadas no Intune. Esta abordagem chama-se **Gestão de dispositivos móveis (MDM)**. Nesta abordagem, os utilizadores "inscrevem" os respetivos dispositivos e utilizam certificados para comunicar com o Intune. Enquanto administrador de TI, pode enviar aplicações em dispositivos, restringir dispositivos a um sistema operativo específico, bloquear dispositivos pessoais e mais. Na eventualidade de perda ou roubo de um dispositivo, também pode remover todos os dados do mesmo. 

Na segunda abordagem, gere as aplicações em dispositivos. Esta abordagem chama-se **Gestão de aplicações móveis (MAM)**. Nesta abordagem, os utilizadores podem utilizar os dispositivos pessoais para acederem a recursos organizacionais. Ao abrir uma aplicação, tal como o e-mail ou o SharePoint, é pedida autenticação adicional aos utilizadores. Na eventualidade de perda ou roubo de um dispositivo, pode remover todos os dados organizacionais do mesmo. 

Também pode utilizar uma combinação de [MDM e MAM](https://docs.microsoft.com/intune/byod-technology-decisions).

Quando configurar o Intune, também poderá optar por trabalhar exclusivamente no portal do Azure ou por utilizar o Intune e o Microsoft 365 em conjunto para gerir dispositivos. Veja como o departamento de TI da Microsoft optou por uma abordagem de gestão de dispositivos moderna e as lições aprendidas no estudo de caso [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) (Migrar a gestão de dispositivos móveis para o Intune no portal do Azure) do departamento de TI da Microsoft. 

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>Simplifique as tarefas TI com o dashboard de Gestão de Dispositivos

O [dashboard de Gestão de Dispositivos](https://devicemanagement.portal.azure.com/) inclui tudo o que precisa para gerir e concluir tarefas para os seus dispositivos móveis. Este dashboard contém os serviços utilizados para a gestão de dispositivos, incluindo o Intune e o Azure Active Directory, bem como para gerir aplicações cliente. 

No dashboard de Gestão de Dispositivos, pode:

- [Inscrever dispositivos](https://docs.microsoft.com/intune/device-enrollment)
- [Definir a conformidade do dispositivo](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Gerir dispositivos](https://docs.microsoft.com/intune/device-management)
- [Gerir aplicações](https://docs.microsoft.com/intune/app-management)  
- [ iOS](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Instalar o conector do Exchange no local](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Gerir funções](https://docs.microsoft.com/intune/role-based-access-control)  
- Gerir atualizações de software
  - [Gerir atualizações do Windows 10](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Gerir atualizações do iOS](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Gerir utilizadores](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Gerir grupos e membros](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Resolver problemas](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Passo seguinte
Quando estiver pronto para começar a utilizar uma solução MDM ou MAM e seguir os diferentes passos para configurar o Intune, inscrever dispositivos e começar a criar políticas, veja [Mobile device management for Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) (Gestão de dispositivos móveis para o Microsoft 365). 
