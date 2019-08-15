---
title: Gestão de dispositivos no Microsoft 365
description: O Microsoft 365 Enterprise inclui o Microsoft Intune. Veja como o Intune fornece gerenciamento de dispositivos móveis e gerenciamento de aplicativos móveis para sua organização. Leia cenários comuns e use o Intune para implantar Microsoft 365 em seu ambiente.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 37a1c9fad9b77e39145f1b4183b8176fb1677613
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/14/2019
ms.locfileid: "69022872"
---
# <a name="what-is-device-management"></a>O que é a gestão de dispositivos? 

Uma das principais tarefas dos administradores consiste na proteção dos recursos e dados da organização. Essa tarefa é o *Gerenciamento de dispositivo*. Os usuários têm muitos dispositivos onde abrem e compartilham arquivos pessoais, visitam sites e instalam aplicativos e jogos. Esses mesmos usuários também são funcionários e alunos. Eles desejam usar seus dispositivos para acessar os recursos corporativos e de estudante, como email e OneNote. O gerenciamento de dispositivos permite que as organizações protejam e protejam seus recursos e dados. 

Usando um provedor de gerenciamento de dispositivos, a organização pode garantir que apenas pessoas e dispositivos autorizados obtenham acesso a informações proprietárias. Da mesma forma, os usuários do dispositivo podem sentir a facilidade de acessar dados de trabalho de seu telefone, pois sabem que seus dispositivos atendem aos requisitos de segurança de sua organização. Enquanto organização, poderá perguntar "**o que devemos utilizar para proteger nossos recursos?"** .

A resposta é [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune). O Intune oferece gestão de dispositivos móveis (MDM) e gestão de aplicações móveis (MAM). Algumas das principais tarefas das soluções de MDM ou MAM consistem em:

- Dê suporte a um ambiente móvel diversificado e gerencie dispositivos iOS, Android, Windows e macOS com segurança.
- Verifique se os dispositivos e aplicativos estão em conformidade com os requisitos de segurança da sua organização.
- Crie políticas que ajudem a manter os dados da sua organização seguros em dispositivos pessoais e de propriedade da empresa.
- Utilizar uma solução móvel única e unificada para impor estas políticas e ajudar a gerir dispositivos, aplicações, utilizadores e grupos.

O Intune está incluído no Microsoft 365 e integra-se no Azure Active Directory (Azure AD). O Azure AD ajuda a controlar quem tem acesso e ao que têm acesso.

## <a name="hello-intune"></a>Olá, Intune!
Muitas organizações, tais como a Microsoft, utilizam o Intune para os proteger dados proprietários aos quais os utilizadores acedem a partir de dispositivos móveis pessoais e pertencentes à empresa. O Intune inclui políticas de configuração de dispositivo e aplicativo, políticas de atualização de software e status de instalação (gráficos, tabelas e relatórios) para ajudá-lo a proteger e monitorar o acesso a dados.

Normalmente, as pessoas têm múltiplos dispositivos que utilizam plataformas diferentes. Por exemplo, um colaborador poderá utilizar um Surface Pro em contexto laboral e um dispositivo móvel Android em casa. Também é normal que uma pessoa aceda a recursos organizacionais, tais como o Microsoft Outlook e o SharePoint, a partir desses dispositivos diferentes.

Com o Intune, pode gerir múltiplos dispositivos por pessoa, bem como as diferentes plataformas que são executadas em cada dispositivo, incluindo iOS, macOS, Android e Windows. O Intune separa políticas e configurações pela plataforma do dispositivo. Portanto, é fácil gerenciar e exibir dispositivos de uma plataforma específica.

Os **[cenários comuns](https://docs.microsoft.com/intune/common-scenarios)** são um ótimo recurso para ver a forma como o Intune responde a perguntas comuns quando trabalha com dispositivos móveis. Encontrará cenários sobre:  
- A proteção de e-mails com o Exchange no local
- O acesso ao Office 365 de forma segura e protegida
- A utilização de dispositivos pessoais para aceder a recursos organizacionais

## <a name="integration-with-secure-and-protect-services"></a>A integração com serviços de proteção
Uma das principais tarefas das soluções de gestão de dispositivos consiste em proporcionar segurança e proteção. O Intune integra-se muito bem com outros serviços para realizar esta tarefa. Por exemplo:

- O **Microsoft 365** é um componente-chave para simplificar tarefas comuns de TI. No centro de administração Microsoft 365, você cria usuários e gerencia grupos. Você também obtém acesso a outros serviços, como Intune, Azure AD e muito mais. 

  Por exemplo, crie um grupo de dispositivos iOS no Microsoft 365. Em seguida, utilize o Intune para enviar políticas para o grupo de dispositivos iOS que incidem em funcionalidades iOS, tais como o acesso à App Store, ao utilizar o AirDrop, fazer cópias de segurança em iCloud, utilizar o filtro Web da Apple e mais.

- O **Windows Defender** inclui muitas funcionalidades de segurança para ajudar a proteger dispositivos com o Windows 10. A utilização conjunta do Intune e do Windows Defender permite, por exemplo: 

  - Ativar o [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) para procurar atividades suspeitas em ficheiros e aplicações em dispositivos móveis 
  - Use a [ATP (proteção avançada contra ameaças) do Microsoft defender](https://docs.microsoft.com/intune/advanced-threat-protection) para ajudar a evitar violações de segurança em dispositivos móveis. Além de ajudar a limitar o impacto de uma violação de segurança, bloqueando um usuário dos recursos corporativos.

- O **acesso condicional** é um recurso do Azure Active Directory e se integra perfeitamente com o Intune. Usando o [acesso condicional](https://docs.microsoft.com/intune/conditional-access), verifique se somente dispositivos em conformidade têm permissão de acesso a email, SharePoint e outros aplicativos. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Optar pela solução de gestão de dispositivos que mais se adequa à sua situação

Existem duas formas de abordar a gestão de dispositivos. Primeiro, você pode gerenciar diferentes aspectos dos dispositivos usando os recursos internos do Intune. Essa abordagem é chamada **de MDM (gerenciamento de dispositivo móvel)** . Os usuários "registram" seus dispositivos e usam certificados para se comunicar com o Intune. Como um administrador de ti, você envia aplicativos por push a dispositivos, restringe dispositivos a um sistema operacional específico, bloqueie dispositivos pessoais e muito mais. Na eventualidade de perda ou roubo de um dispositivo, também pode remover todos os dados do mesmo. 

Na segunda abordagem, gere as aplicações em dispositivos. Essa abordagem é chamada **de MAM (gerenciamento de aplicativo móvel)** . Os usuários podem usar seus dispositivos pessoais para acessar recursos organizacionais. Ao abrir uma aplicação, tal como o e-mail ou o SharePoint, é pedida autenticação adicional aos utilizadores. Na eventualidade de perda ou roubo de um dispositivo, pode remover todos os dados organizacionais do mesmo. 

Também pode utilizar uma combinação de [MDM e MAM](https://docs.microsoft.com/intune/byod-technology-decisions).

Quando configurar o Intune, também poderá optar por trabalhar exclusivamente no portal do Azure ou por utilizar o Intune e o Microsoft 365 em conjunto para gerir dispositivos. [Migrar o gerenciamento de dispositivos móveis para o Intune no portal do Azure](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) é um estudo de caso de ti da Microsoft. Nesse estudo de caso, veja como a ti da Microsoft escolheu uma abordagem moderna de gerenciamento de dispositivos e leia as lições aprendidas.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Simplificar tarefas de ti usando o centro de administração do gerenciamento de dispositivos

O [centro de administração do gerenciamento de dispositivos](https://devicemanagement.microsoft.com/) é uma loja única para gerenciar e concluir tarefas para seus dispositivos móveis. Esse espaço de trabalho inclui os serviços usados para o gerenciamento de dispositivos, incluindo o Intune e o Azure Active Directory, e também para gerenciar aplicativos cliente. 

No centro de administração do gerenciamento de dispositivos, você pode:

- [Inscrever dispositivos](https://docs.microsoft.com/intune/device-enrollment)
- [Definir a conformidade do dispositivo](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Gerir dispositivos](https://docs.microsoft.com/intune/device-management)
- [Gerir aplicações](https://docs.microsoft.com/intune/app-management)  
- [ iOS](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Instalar o conector do Exchange no local](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Gerir funções](https://docs.microsoft.com/intune/role-based-access-control)  
- Gerenciar atualizações de software
  - [Gerir atualizações do Windows 10](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Gerir atualizações do iOS](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Gerir utilizadores](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Gerir grupos e membros](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Resolver problemas](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Passo seguinte
Quando você estiver pronto para começar a usar uma solução de MDM ou MAM, percorra as diferentes etapas para configurar o Intune, registrar dispositivos e começar a criar políticas. O [Gerenciamento de dispositivos móveis para Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) também é um ótimo recurso.
