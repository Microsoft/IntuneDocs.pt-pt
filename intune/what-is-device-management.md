---
title: Gestão de dispositivos no Microsoft 365
description: O Microsoft 365 Enterprise inclui o Microsoft Intune. Veja como o Intune proporciona a gestão de dispositivos móveis e gestão de aplicações móveis para a sua organização. Cenários comuns de ler e utilizar o Intune para implementar o Microsoft 365 no seu ambiente.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
audience: ITPro
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 452cb8e4163b82d699347a33fd8dfda9c792b6fc
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050263"
---
# <a name="what-is-device-management"></a>O que é a gestão de dispositivos? 

Uma das principais tarefas dos administradores consiste na proteção dos recursos e dados da organização. Esta tarefa é *gestão de dispositivos*. Os utilizadores têm o número de dispositivos em que são abertos e partilham ficheiros pessoais, visite o Web sites e instalar aplicações e jogos. Esses mesmos usuários também são os funcionários e estudantes. Eles querem utilizar os seus dispositivos para aceder ao trabalho e escolares recursos, como o e-mail e OneNote. Gestão de dispositivos permite às organizações a proteger e proteger seus dados e recursos. 

Utilizar um fornecedor de gestão do dispositivo, organização pode tornar-se de que apenas as pessoas autorizadas e dispositivos obtém acesso às informações proprietárias. Da mesma forma, os utilizadores de dispositivos podem sentir-se em facilidade de acesso a dados de trabalho no respetivo telemóvel, pois sabem que o respetivo dispositivo cumprem os requisitos de segurança da sua organização. Enquanto organização, poderá perguntar "**o que devemos utilizar para proteger nossos recursos?"**.

A resposta é [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune). O Intune oferece gestão de dispositivos móveis (MDM) e gestão de aplicações móveis (MAM). Algumas das principais tarefas das soluções de MDM ou MAM consistem em:

- Suportar um ambiente móvel variado e gerir dispositivos iOS, Android, Windows e macOS com segurança.
- Certifique-se de dispositivos e aplicações estão em conformidade com requisitos de segurança da sua organização.
- Crie políticas que ajudam a manter os dados da organização seguros nos dispositivos pertencentes à empresa e pessoais.
- Utilizar uma solução móvel única e unificada para impor estas políticas e ajudar a gerir dispositivos, aplicações, utilizadores e grupos.

O Intune está incluído no Microsoft 365 e integra-se no Azure Active Directory (Azure AD). O Azure AD ajuda a controlar quem tem acesso e ao que têm acesso.

## <a name="hello-intune"></a>Olá, Intune!
Muitas organizações, tais como a Microsoft, utilizam o Intune para os proteger dados proprietários aos quais os utilizadores acedem a partir de dispositivos móveis pessoais e pertencentes à empresa. O Intune inclui políticas de configuração de aplicações e dispositivos, as políticas de atualização de software e os Estados de instalação (gráficos, tabelas e relatórios) para o ajudar a proteger e monitorizar o acesso a dados.

Normalmente, as pessoas têm múltiplos dispositivos que utilizam plataformas diferentes. Por exemplo, um colaborador poderá utilizar um Surface Pro em contexto laboral e um dispositivo móvel Android em casa. Também é normal que uma pessoa aceda a recursos organizacionais, tais como o Microsoft Outlook e o SharePoint, a partir desses dispositivos diferentes.

Com o Intune, pode gerir múltiplos dispositivos por pessoa, bem como as diferentes plataformas que são executadas em cada dispositivo, incluindo iOS, macOS, Android e Windows. Intune separa as diretivas e configurações pela plataforma do dispositivo. Portanto, é fácil de gerenciar e ver os dispositivos de uma plataforma específica.

Os **[cenários comuns](https://docs.microsoft.com/intune/common-scenarios)** são um ótimo recurso para ver a forma como o Intune responde a perguntas comuns quando trabalha com dispositivos móveis. Encontrará cenários sobre:  
- A proteção de e-mails com o Exchange no local
- O acesso ao Office 365 de forma segura e protegida
- A utilização de dispositivos pessoais para aceder a recursos organizacionais

## <a name="integration-with-secure-and-protect-services"></a>A integração com serviços de proteção
Uma das principais tarefas das soluções de gestão de dispositivos consiste em proporcionar segurança e proteção. O Intune integra-se muito bem com outros serviços para realizar esta tarefa. Por exemplo:

- O **Microsoft 365** é um componente-chave para simplificar tarefas comuns de TI. No Centro de administração do Microsoft 365, pode criar utilizadores e gerir grupos. Também obtém acesso a outros serviços, como o Intune, do Azure AD e muito mais. 

  Por exemplo, crie um grupo de dispositivos iOS no Microsoft 365. Em seguida, utilize o Intune para enviar políticas para o grupo de dispositivos iOS que incidem em funcionalidades iOS, tais como o acesso à App Store, ao utilizar o AirDrop, fazer cópias de segurança em iCloud, utilizar o filtro Web da Apple e mais.

- O **Windows Defender** inclui muitas funcionalidades de segurança para ajudar a proteger dispositivos com o Windows 10. A utilização conjunta do Intune e do Windows Defender permite, por exemplo: 

    - Ativar o [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) para procurar atividades suspeitas em ficheiros e aplicações em dispositivos móveis 
    - Uso [proteção de ameaças avançada do Windows Defender (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) para ajudar a evitar falhas de segurança em dispositivos móveis. Além disso, ajudar a limitar o impacto de uma violação de segurança ao bloquear um utilizador a partir de recursos da empresa.

- O **acesso condicional** é um recurso do Azure Active Directory que se integra muito bem com o Intune. Usando [acesso condicional](https://docs.microsoft.com/intune/conditional-access), certifique-se de que apenas os dispositivos compatíveis têm acesso ao e-mail, o SharePoint e outras aplicações. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Optar pela solução de gestão de dispositivos que mais se adequa à sua situação

Existem duas formas de abordar a gestão de dispositivos. Em primeiro lugar, pode gerenciar diferentes aspectos de dispositivos com as funcionalidades incorporadas no Intune. Essa abordagem é chamada **gestão de dispositivos móveis (MDM)**. Os utilizadores "inscreverem" os respetivos dispositivos e utilizam certificados para comunicar com o Intune. Como um administrador de TI, emitir aplicações em dispositivos, restringir dispositivos para um sistema operativo específico, impedir que os dispositivos pessoais e muito mais. Na eventualidade de perda ou roubo de um dispositivo, também pode remover todos os dados do mesmo. 

Na segunda abordagem, gere as aplicações em dispositivos. Essa abordagem é chamada **gestão de aplicações móveis (MAM)**. Os utilizadores podem utilizar os seus dispositivos pessoais para aceder a recursos organizacionais. Ao abrir uma aplicação, tal como o e-mail ou o SharePoint, é pedida autenticação adicional aos utilizadores. Na eventualidade de perda ou roubo de um dispositivo, pode remover todos os dados organizacionais do mesmo. 

Também pode utilizar uma combinação de [MDM e MAM](https://docs.microsoft.com/intune/byod-technology-decisions).

Quando configurar o Intune, também poderá optar por trabalhar exclusivamente no portal do Azure ou por utilizar o Intune e o Microsoft 365 em conjunto para gerir dispositivos. [Gestão de dispositivos móveis migrando para o Intune no portal do Azure](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) é um estudo de caso do Microsoft IT. Nesse caso, estudar, veja como o Microsoft IT optou por uma abordagem de gestão de dispositivos modernos e leia as lições aprenderam.

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
Quando estiver pronto para começar a trabalhar com uma solução MDM ou MAM, siga os passos diferentes para configurar o Intune, inscrever os dispositivos e iniciar a criação de políticas. [Gestão de dispositivos móveis para o Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) também é um ótimo recurso.
