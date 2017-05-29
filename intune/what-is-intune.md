---
title: "Introdução ao Intune na pré-visualização no portal do Azure"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: conheça os princípios básicos sobre o Intune na pré-visualização do portal do Azure e como o pode ajudar a gerir os seus dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 04/24/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 16d7ff50eb821e0927c3c6ea21f3cdb1257762a0
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Introdução ao Microsoft Intune na pré-visualização do portal do Azure


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

O Microsoft Intune vai mudar para o portal do Azure, o que significa que as funcionalidades e os fluxos de trabalho a que está habituado vão mudar.
O novo portal oferece-lhe uma pré-visualização das funcionalidades novas e atualizadas no portal do Azure, onde pode gerir os dispositivos móveis, os PCs e as aplicações da sua organização.
Todas as funcionalidades do Intune vão acabar por passar para o Azure, mas pode realizar muitas tarefas do Intune no portal do Azure atualmente. Uma vez que esta nova experiência está em pré-visualização, algumas funcionalidades podem ainda não estar presentes no portal. Reveja a secção [Novidades](#whats-new) para obter detalhes.

> [!IMPORTANT]
> **Ainda não vê o novo portal?**<br>
> Já começamos a implementar a pré-visualização em inquilinos selecionados. Os inquilinos existentes serão migrados para a nova experiência que começa no início do ano de calendário de 2017. Vai receber uma notificação no Centro de Mensagens do Office antes da migração do seu inquilino.
>
> As contas do Intune criadas antes de janeiro de 2017 precisam de uma única migração antes dos fluxos de trabalho da Inscrição da Apple ficarem disponíveis no Azure. A agenda para a migração ainda não foi anunciada, mas os detalhes serão disponibilizados logo que possível. Recomendamos vivamente a criação de uma conta de avaliação para testar a nova experiência se a conta existente não conseguir aceder à pré-visualização.


Nesta biblioteca, encontrará documentação sobre novos produtos e será constantemente atualizada durante a pré-visualização. Se tiver sugestões que gostaria de ver, deixe a sua opinião nos comentários do tópico. Gostaríamos de saber a sua opinião.

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

Os destaques da nova experiência incluem:

- Uma consola integrada para todos os componentes do Enterprise Mobility + Security (EMS)
- Uma consola baseada em HTML baseada em normas da Web
- Suporte do Microsoft Graph API para automatizar várias ações
- Grupos do Azure Active Directory (AD) para proporcionar compatibilidade em todas as suas aplicações do Azure
- Suporte para os browsers mais modernos

Se estiver à procura de documentação da consola clássica do Intune, veja a [biblioteca de documentação do Intune](https://docs.microsoft.com/intune-classic/).

## <a name="before-you-start"></a>Antes de começar

Para utilizar o Intune no portal do Azure, tem de ter uma conta de administrador e de inquilino do Intune. Caso ainda não o tenha feito, [inscreva-se numa conta](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

## <a name="supported-web-browsers-for-the-azure-portal"></a>Browsers suportados para o portal do Azure

O portal do Azure funciona na maior parte dos PCs, Macs e tablets mais recentes. Os telemóveis não são suportados.
Atualmente, são suportados os seguintes browsers:

- Microsoft Edge (versão mais recente)
- Microsoft Internet Explorer 11
- Safari (versão mais recente, apenas Mac)
- Chrome (versão mais recente)
- Firefox (versão mais recente)

Consulte o [portal do Azure](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices) para obter as informações mais recentes sobre browsers suportados.

## <a name="whats-in-this-library"></a>O que existe nesta biblioteca?

A documentação reflete o esquema do portal do Intune para que seja mais fácil encontrar as informações de que precisa.

![Cargas de trabalho do portal do Azure](./media/azure-portal-workloads.png)

### <a name="introduction-and-get-started"></a>Introdução
Esta secção contém informações sobre as [novidades](whats-new.md), os [problemas conhecidos](known-issues.md), [como obter suporte](get-support.md) e [como começar a utilizar uma versão de avaliação gratuita](free-trial-sign-up.md) do Intune.
### <a name="plan-and-design"></a>Planear e estruturar
Informações para o ajudar a [planear e estruturar](/intune-classic/plan-and-design/introduction) o ambiente do Intune.
### <a name="device-enrollment"></a>Inscrição de dispositivos
[Como fazer com que os seus dispositivos sejam geridos pelo Intune](device-enrollment.md).
### <a name="device-compliance"></a>Conformidade do dispositivo
[Defina um nível de conformidade para os seus dispositivos e, em seguida, comunique caso existam dispositivos que não sejam compatíveis](device-compliance.md).
### <a name="device-configuration"></a>Configuração do dispositivo
[Compreenda os perfis que pode utilizar para configurar definições e funcionalidades nos dispositivos que gere](device-profiles.md).
### <a name="devices"></a>Dispositivos
[Conheça os dispositivos que gere através do inventário e dos relatórios](device-management.md).
### <a name="mobile-apps"></a>Aplicações móveis
[Como publicar, gerir, configurar e proteger aplicações](app-management.md).
### <a name="conditional-access"></a>Acesso condicional
[Restrinja o acesso aos serviços Exchange consoante as condições que especificar](conditional-access.md).
### <a name="on-premises-access"></a>Acesso no local
[Configurar o acesso ao Exchange ActiveSync e ao Exchange no local](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Users
[Saiba mais sobre os utilizadores de dispositivos que gere e ordene recursos em grupos](user-management.md).
### <a name="groups"></a>Grupos
[Saiba mais sobre como pode utilizar os grupos do Azure Active Directory com o Intune](groups-get-started.md)
### <a name="intune-roles"></a>Funções do Intune
[Controle quem pode realizar várias ações do Intune e a quem se aplicam essas ações](role-based-access-control.md). Pode utilizar as funções incorporadas que abrangem alguns cenários comuns do Intune ou pode criar as suas próprias funções.
### <a name="software-updates"></a>Atualizações de software
[Saiba mais sobre como configurar as atualizações de software para dispositivos Windows 10](windows-update-for-business-configure.md).



## <a name="whats-new"></a>Novidades?

[Conheça as novidades da versão de pré-visualização](whats-new.md).

