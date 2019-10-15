---
title: Gerenciamento de dispositivos no Microsoft 365
description: Microsoft 365 Enterprise inclui Microsoft Intune. Veja como o Intune fornece gerenciamento de dispositivos móveis e gerenciamento de aplicativos móveis para sua organização. Leia cenários comuns e use o Intune para implantar Microsoft 365 em seu ambiente.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93d8107d235d9f13af487bba4cbf6a71fc92eeab
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314546"
---
# <a name="device-management-overview"></a>Visão geral do gerenciamento de dispositivos

Uma tarefa importante de qualquer administrador é proteger e proteger os recursos e os dados de uma organização. Essa tarefa é o *Gerenciamento de dispositivo*. Os usuários têm muitos dispositivos onde abrem e compartilham arquivos pessoais, visitam sites e instalam aplicativos e jogos. Esses mesmos usuários também são funcionários e alunos. Eles desejam usar seus dispositivos para acessar os recursos corporativos e de estudante, como email e OneNote.

O gerenciamento de dispositivos permite que as organizações protejam e protejam seus recursos e dados e de diferentes dispositivos.

Usando um provedor de gerenciamento de dispositivos, a organização pode garantir que apenas pessoas e dispositivos autorizados obtenham acesso a informações proprietárias. Da mesma forma, os usuários do dispositivo podem sentir a facilidade de acessar dados de trabalho de seu telefone, pois sabem que seus dispositivos atendem aos requisitos de segurança de sua organização. Como uma organização, você pode perguntar- **o que devemos usar para proteger nossos recursos?**

A resposta é [Microsoft Intune](what-is-intune.md). O Intune oferece MDM (gerenciamento de dispositivo móvel) e MAM (gerenciamento de aplicativo móvel). Algumas tarefas importantes de qualquer solução de MDM ou MAM são:

- Dê suporte a um ambiente móvel diversificado e gerencie dispositivos iOS, Android, Windows e macOS com segurança.
- Verifique se os dispositivos e aplicativos estão em conformidade com os requisitos de segurança da sua organização.
- Crie políticas que ajudem a manter os dados da sua organização seguros em dispositivos pessoais e de propriedade da organização.
- Use uma solução móvel única e unificada para impor essas políticas e ajudar a gerenciar dispositivos, aplicativos, usuários e grupos.
- Proteja as informações da sua empresa ajudando a controlar a maneira como sua força de equipe acessa e compartilha seus dados.

O Intune está incluído com Microsoft Azure, Microsoft 365 e integra-se ao Azure Active Directory Azure AD). O Azure AD ajuda a controlar quem tem acesso e o que eles têm acesso.

## <a name="microsoft-intune"></a>Microsoft Intune

Muitas organizações, como a Microsoft, usam o Intune para proteger dados proprietários que os usuários acessam de seus dispositivos móveis pessoais e de propriedade da empresa. O Intune inclui políticas de configuração de dispositivo e aplicativo, políticas de atualização de software e status de instalação (gráficos, tabelas e relatórios) para ajudá-lo a proteger e monitorar o acesso a dados.

É comum que as pessoas tenham vários dispositivos que usam diferentes plataformas. Por exemplo, um funcionário pode usar o Surface Pro for Work e um dispositivo móvel Android em sua vida pessoal. E é comum que uma pessoa acesse recursos organizacionais, como o Microsoft Outlook e o SharePoint, desses vários dispositivos.

Com o Intune, você pode gerenciar vários dispositivos por pessoa e as diferentes plataformas que são executadas em cada dispositivo, incluindo iOS, macOS, Android e Windows. O Intune separa políticas e configurações pela plataforma do dispositivo. Portanto, é fácil gerenciar e exibir dispositivos de uma plataforma específica.

**[Cenários comuns](common-scenarios.md)** é um ótimo recurso para ver como o Intune responde a perguntas comuns ao trabalhar com dispositivos móveis. Você encontrará cenários sobre:  

- Protegendo email com o Exchange local
- Acessando o Office 365 com segurança e segurança
- Usando dispositivos pessoais para acessar recursos organizacionais

Para obter mais informações sobre o Intune, consulte [o que é o Intune](what-is-intune.md).

## <a name="integration-with-secure-and-protect-services"></a>Integração com serviços seguros e protegidos

Uma tarefa importante de qualquer solução de gerenciamento de dispositivos é fornecer segurança e proteção. O Intune faz um ótimo trabalho de integração com outros serviços para realizar essa tarefa. Por exemplo:

- **Microsoft 365** é um componente fundamental para simplificar tarefas comuns de ti. No centro de administração Microsoft 365, você cria usuários e gerencia grupos. Você também obtém acesso a outros serviços, como Intune, Azure AD e muito mais.

  Por exemplo, crie um grupo de dispositivos iOS no Microsoft 365. Em seguida, use o Intune para enviar políticas por push para o grupo de dispositivos iOS que se concentram em recursos do iOS, como o acesso à loja de aplicativos, usando o essoltar, fazendo backup no iCloud, usando o filtro da Web da Apple e muito mais.

- O **Windows Defender** inclui muitos recursos de segurança para ajudar a proteger dispositivos Windows 10. Por exemplo, usando o Intune e o Windows Defender juntos, você pode:

  - Habilite o [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md) para procurar atividades suspeitas em arquivos e aplicativos em dispositivos móveis.
  - Use a [ATP (proteção avançada contra ameaças) do Microsoft defender](../protect/advanced-threat-protection.md) para ajudar a evitar violações de segurança em dispositivos móveis. Além de ajudar a limitar o impacto de uma violação de segurança, bloqueando um usuário dos recursos corporativos.

- O **acesso condicional** é um recurso do Azure Active Directory e se integra perfeitamente com o Intune. Usando o [acesso condicional](../protect/conditional-access.md), verifique se somente dispositivos em conformidade têm permissão de acesso a email, SharePoint e outros aplicativos.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Escolha a solução de gerenciamento de dispositivo ideal para você

Há duas maneiras de abordar o gerenciamento de dispositivos. Primeiro, você pode gerenciar diferentes aspectos dos dispositivos usando os recursos internos do Intune. Essa abordagem é chamada **de MDM (gerenciamento de dispositivo móvel)** . Os usuários "registram" seus dispositivos e usam certificados para se comunicar com o Intune. Como um administrador de ti, você envia aplicativos por push a dispositivos, restringe dispositivos a um sistema operacional específico, bloqueie dispositivos pessoais e muito mais. Se um dispositivo for perdido ou roubado, você também poderá remover todos os dados do dispositivo.

Na segunda abordagem, você gerencia aplicativos em dispositivos. Essa abordagem é chamada **de MAM (gerenciamento de aplicativo móvel)** . Os usuários podem usar seus dispositivos pessoais para acessar recursos organizacionais. Ao abrir um aplicativo, como email ou SharePoint, os usuários são solicitados a fornecer autenticação adicional. Se um dispositivo for perdido ou roubado, você poderá remover todos os dados da organização do dispositivo.

Você também pode usar uma combinação de [MDM e MAM](byod-technology-decisions.md) juntos.

Ao configurar o Intune, você também opta por trabalhar somente no portal do Azure para gerenciar dispositivos ou usar o Intune e Microsoft 365 juntos para gerenciar dispositivos. [Migrar o gerenciamento de dispositivos móveis para o Intune no portal do Azure](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) é um estudo de caso de ti da Microsoft. Nesse estudo de caso, veja como a ti da Microsoft escolheu uma abordagem moderna de gerenciamento de dispositivos e leia as lições aprendidas.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Simplificar tarefas de ti usando o centro de administração do gerenciamento de dispositivos

O [centro de administração do gerenciamento de dispositivos](https://devicemanagement.microsoft.com/) é uma loja única para gerenciar e concluir tarefas para seus dispositivos móveis. Esse espaço de trabalho inclui os serviços usados para o gerenciamento de dispositivos, incluindo o Intune e o Azure Active Directory, e também para gerenciar aplicativos cliente.

No centro de administração do gerenciamento de dispositivos, você pode:

- [Registrar dispositivos](../enrollment/device-enrollment.md)
- [Definir conformidade do dispositivo](../protect/device-compliance-get-started.md)
- [Gerenciar dispositivos](../remote-actions/device-management.md)
- [Gerenciar aplicativos](../apps/app-management.md)  
- [Livros eletrônicos do iOS](../apps/vpp-ebooks-ios.md)  
- [Instalar o Exchange local Connector](../protect/exchange-connector-install.md)  
- [Gerenciar funções](role-based-access-control.md)  
- Gerenciar atualizações de software
  - [Gerenciar atualizações do Windows 10](../protect/windows-update-for-business-configure.md)  
  - [Gerenciar atualizações do iOS](../protect/software-updates-ios.md)  
- [Active Directory do Azure](https://docs.microsoft.com/azure/active-directory)  
- [Gerir utilizadores](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Gerir grupos e membros](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Resolução de problemas](help-desk-operators.md)

## <a name="next-steps"></a>Passos seguintes

Quando você estiver pronto para começar a usar uma solução de MDM ou MAM, percorra as diferentes etapas para configurar o Intune, registrar dispositivos e começar a criar políticas. O [Gerenciamento de dispositivos móveis para Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) também é um ótimo recurso.
