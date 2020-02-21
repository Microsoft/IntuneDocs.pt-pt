---
title: Gestão de dispositivos no Microsoft 365
description: O Microsoft 365 Enterprise inclui o Microsoft Intune. Veja como a Intune fornece gestão de dispositivos móveis e gestão de aplicações móveis para a sua organização. Leia cenários comuns e use O Intune para implementar o Microsoft 365 no seu ambiente.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a15bf0bd8ed0a46f330b159e45d0a5d5a4c7059
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510389"
---
# <a name="device-management-overview"></a>Device management overview (Descrição geral da gestão de dispositivos)

Uma das principais tarefas dos administradores consiste na proteção dos recursos e dados da organização. Esta tarefa é *a gestão do dispositivo.* Os utilizadores têm muitos dispositivos onde abrem e partilham ficheiros pessoais, visitam websites e instalam apps e jogos. Estes mesmos utilizadores são também funcionários e alunos. Pretendem utilizar os seus dispositivos para aceder ao trabalho e aos recursos escolares, como o email e o OneNote.

A gestão de dispositivos permite que as organizações protejam e protejam os seus recursos e dados, e de diferentes dispositivos.

Utilizando um fornecedor de gestão de dispositivos, a organização pode certificar-se de que apenas pessoas e dispositivos autorizados têm acesso a informações próprias. Da mesma forma, os utilizadores de dispositivos podem sentir-se facilitados a aceder aos dados de trabalho a partir do seu telemóvel, uma vez que sabem que o seu dispositivo cumpre os requisitos de segurança da sua organização. Enquanto organização, poderá perguntar "**o que devemos utilizar para proteger nossos recursos?"** .

A resposta é [Microsoft Intune](what-is-intune.md). O Intune oferece gestão de dispositivos móveis (MDM) e gestão de aplicações móveis (MAM). Algumas das principais tarefas das soluções de MDM ou MAM consistem em:

- Suporte um ambiente móvel diversificado e gerencie os dispositivos iOS/iPadOS, Android, Windows e macOS de forma segura.
- Certifique-se de que os dispositivos e aplicações estão em conformidade com os requisitos de segurança da sua organização.
- Crie políticas que ajudem a manter os dados da sua organização seguros em dispositivos pessoais e propriedade da organização.
- Utilizar uma solução móvel única e unificada para impor estas políticas e ajudar a gerir dispositivos, aplicações, utilizadores e grupos.
- Proteja as informações da sua empresa ajudando a controlar a forma como a sua força de trabalho acede e partilha os seus dados.

Intune está incluído com o Microsoft Azure, Microsoft 365, e integra-se com o Azure Ative Directory (Azure AD). O Azure AD ajuda a controlar quem tem acesso e ao que têm acesso.

## <a name="microsoft-intune"></a>Microsoft Intune

Muitas organizações, tais como a Microsoft, utilizam o Intune para os proteger dados proprietários aos quais os utilizadores acedem a partir de dispositivos móveis pessoais e pertencentes à empresa. Intune inclui políticas de configuração de dispositivos e aplicações, políticas de atualização de software e estados de instalação (gráficos, tabelas e relatórios) para ajudá-lo a garantir e monitorizar o acesso aos dados.

Normalmente, as pessoas têm múltiplos dispositivos que utilizam plataformas diferentes. Por exemplo, um colaborador poderá utilizar um Surface Pro em contexto laboral e um dispositivo móvel Android em casa. Também é normal que uma pessoa aceda a recursos organizacionais, tais como o Microsoft Outlook e o SharePoint, a partir desses dispositivos diferentes.

Com o Intune, pode gerir vários dispositivos por pessoa, e as diferentes plataformas que funcionam em cada dispositivo, incluindo iOS/iPadOS, macOS, Android e Windows. Intune separa políticas e configurações por plataforma de dispositivos. Portanto, é fácil gerir e ver dispositivos de uma plataforma específica.

Os **[cenários comuns](common-scenarios.md)** são um ótimo recurso para ver a forma como o Intune responde a perguntas comuns quando trabalha com dispositivos móveis. Encontrará cenários sobre:  

- A proteção de e-mails com o Exchange no local
- O acesso ao Office 365 de forma segura e protegida
- A utilização de dispositivos pessoais para aceder a recursos organizacionais

Para mais informações sobre Intune, consulte [o que é Intune](what-is-intune.md).

## <a name="integration-with-secure-and-protect-services"></a>A integração com serviços de proteção

Uma das principais tarefas das soluções de gestão de dispositivos consiste em proporcionar segurança e proteção. O Intune integra-se muito bem com outros serviços para realizar esta tarefa. Por exemplo:

- O **Microsoft 365** é um componente-chave para simplificar tarefas comuns de TI. No centro de administração da Microsoft 365, cria-se utilizadores e gere grupos. Você também tem acesso a outros serviços, tais como Intune, Azure AD, e muito mais.

  Por exemplo, criar um grupo de dispositivos iOS/iPadOS na Microsoft 365. Em seguida, utilize o Intune para empurrar as políticas para o grupo de dispositivos iOS/iPadOS que se concentram nas funcionalidades do iOS/iPadOS, como o acesso à loja de aplicações, utilizando o AirDrop, o backup do iCloud, utilizando o filtro web da Apple, e muito mais.

- O **Windows Defender** inclui muitas funcionalidades de segurança para ajudar a proteger dispositivos com o Windows 10. A utilização conjunta do Intune e do Windows Defender permite, por exemplo:

  - Ativar o [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) para procurar atividades suspeitas em ficheiros e aplicações em dispositivos móveis
  - Utilize a Proteção avançada de [ameaças (ATP)](../protect/advanced-threat-protection.md) do Microsoft Defender para ajudar a evitar falhas de segurança em dispositivos móveis. E, ajudar a limitar o impacto de uma falha de segurança bloqueando um utilizador de recursos corporativos.

- **O Acesso Condicional** é uma característica do Azure Ative Directory, e integra-se bem com o Intune. Utilizando [o Acesso Condicional,](../protect/conditional-access.md)certifique-se de que apenas os dispositivos conformes têm acesso a e-mail, SharePoint e outras aplicações.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Optar pela solução de gestão de dispositivos que mais se adequa à sua situação

Existem duas formas de abordar a gestão de dispositivos. Em primeiro lugar, pode gerir diferentes aspetos dos dispositivos utilizando as funcionalidades incorporadas em Intune. Esta abordagem chama-se gestão de **dispositivos móveis (MDM)** . Os utilizadores "matriculam" os seus dispositivos e utilizam certificados para comunicar com o Intune. Como administrador de TI, pressiona aplicações em dispositivos, restringe os dispositivos a um sistema operativo específico, bloqueia dispositivos pessoais e muito mais. Na eventualidade de perda ou roubo de um dispositivo, também pode remover todos os dados do mesmo.

Na segunda abordagem, gere as aplicações em dispositivos. Esta abordagem chama-se gestão de **aplicações móveis (MAM)** . Os utilizadores podem utilizar os seus dispositivos pessoais para aceder a recursos organizacionais. Ao abrir uma aplicação, tal como o e-mail ou o SharePoint, é pedida autenticação adicional aos utilizadores. Na eventualidade de perda ou roubo de um dispositivo, pode remover todos os dados organizacionais do mesmo.

Também pode utilizar uma combinação de [MDM e MAM](byod-technology-decisions.md).

Quando configurar o Intune, também poderá optar por trabalhar exclusivamente no portal do Azure ou por utilizar o Intune e o Microsoft 365 em conjunto para gerir dispositivos. [A gestão de dispositivos móveis migratórios para Intune no portal Azure](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) é um estudo de caso da Microsoft IT. Neste estudo de caso, veja como a Microsoft IT escolheu uma abordagem moderna de gestão de dispositivos e leia as lições aprendidas.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Simplificar tarefas de TI utilizando o centro de administração de gestão de dispositivos

O [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) é uma loja de balcão único para gerir e completar tarefas para os seus dispositivos móveis. Este espaço de trabalho inclui os serviços utilizados para a gestão de dispositivos, incluindo o Intune e o Azure Ative Directory, e também para gerir aplicações de clientes.

No centro de gestão de dispositivos, pode:

- [Inscrever dispositivos](../enrollment/device-enrollment.md)
- [Definir conformidade do dispositivo](../protect/device-compliance-get-started.md)
- [Gerir dispositivos](../remote-actions/device-management.md)
- [Gerir aplicações](../apps/app-management.md)  
- [ iOS](../apps/vpp-ebooks-ios.md)  
- [Instalar o conector do Exchange no local](../protect/exchange-connector-install.md)  
- [Gerir funções](role-based-access-control.md)  
- Gerir atualizações de software
  - [Gerir atualizações do Windows 10](../protect/windows-update-for-business-configure.md)  
  - [Gerir atualizações iOS/iPadOS](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Gerir utilizadores](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Gerir grupos e membros](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Resolução de Problemas](help-desk-operators.md)

## <a name="next-steps"></a>Próximos passos

Quando estiver pronto para começar com uma solução MDM ou MAM, caminhe pelos diferentes passos para configurar Intune, matricular dispositivos e começar a criar políticas. [A gestão de dispositivos móveis para o Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) também é um grande recurso.
