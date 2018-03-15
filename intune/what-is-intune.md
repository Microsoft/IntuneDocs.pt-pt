---
title: "Introdução ao Intune no portal do Azure"
titlesuffix: 
description: "O Microsoft Intune está disponível no portal do Azure. Conheça os princípios básicos do Intune no portal do Azure."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: c9c8485a3ab68be745c8903659df0fd35af2a644
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introdução ao Microsoft Intune no portal do Azure


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Tal como outros serviços do Azure, o Microsoft Intune está disponível no portal do Azure. Ao selecionar **Intune** no portal do Azure, poderá gerir os dispositivos móveis, os computadores e as aplicações da sua organização.

>[!NOTE] 
> Se tiver utilizado uma versão anterior do Microsoft Intune, poderá considerar úteis as seguintes informações:
    * O artigo [Onde estão as minhas funcionalidades no Azure?](ui-changes.md) é uma referência que lhe mostra as IUs e fluxos de trabalho específicos que foram alterados com a mudança para o Azure.
    * O artigo [Grupos clássicos do Intune no portal do Azure](groups-get-started.md) explica as implicações da transição para grupos de segurança do Azure Active Directory relativamente à gestão de grupos.

Os destaques da experiência do Microsoft Intune no portal do Azure incluem:

- Uma consola integrada para todos os componentes do Enterprise Mobility + Security (EMS)
- Uma consola baseada em HTML baseada em normas da Web
- Suporte do Microsoft Graph API para automatizar várias ações
- Grupos do Azure Active Directory (AD) para proporcionar compatibilidade em todas as suas aplicações do Azure
- Suporte para os browsers mais modernos

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

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune no portal do Azure

Pode encontrar o serviço Microsoft Intune no [portal do Azure](https://portal.azure.com). Existem vários serviços no Azure, mas poderá não utilizar todos regularmente. Para obter um guia rápido sobre como personalizar a sua experiência no portal, veja [Começar a utilizar o Intune no portal do Azure](get-started-azure.md).

## <a name="the-microsoft-intune-documentation"></a>A documentação do Microsoft Intune

Este tópico está em constante atualização, bem como todo o conjunto de documentação sobre o Microsoft Intune. Se tiver sugestões que gostaria de ver, deixe a sua opinião nos comentários do tópico. Gostaríamos de saber a sua opinião.

A documentação reflete o esquema do Microsoft Intune no portal do Azure (apresentado abaixo) para que seja mais fácil encontrar as informações de que precisa.

![Cargas de trabalho do portal do Azure](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>Guia de documentação

Utilize a tabela seguinte para localizar e compreender rapidamente as áreas principais do Microsoft Intune.

| Secção                                                      | Descrição                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Introdução](introduction-intune.md)       | Compreenda as noções básicas do Intune, incluindo:<br /> – Soluções comuns<br /> – Como funciona o Microsoft Intune<br /> – A gestão de dispositivos no Intune<br /> – A gestão de aplicações no Intune<br /> – A Gestão de Mobilidade Empresarial (EMM) com e sem inscrição de dispositivos                                                         |
| [Planear e estruturar](planning-guide.md)                         | Orientações para o ajudar a planear e estruturar com êxito o ambiente do seu Microsoft Intune.                                                                                                                                                                                                             |
| [Inscrição de dispositivos](device-enrollment.md)                    | Compreenda como o Microsoft Intune o ajuda a gerir os dispositivos da sua força de trabalho ao inscrever os dispositivos no serviço Intune. Existem vários métodos para inscrever os dispositivos da força de trabalho.                                                                                                         |
| [Conformidade do dispositivo](device-compliance.md)                    | As políticas de conformidade de dispositivos do Intune definem as regras e as definições que um dispositivo tem de cumprir para ser considerado conforme pelo Microsoft Intune. Por exemplo, exigir uma palavra-passe para o acesso ao dispositivo, a encriptação de dispositivos e exigir uma versão mínima de SO. |
| [Configuração do dispositivo](device-profiles.md)                   | Configure as definições e as funcionalidades em todos os dispositivos que gere com o Microsoft Intune ao criar perfis de dispositivos. Por exemplo, pode configurar funcionalidades como notificações, partilha de dados, suporte por e-mail, ligação Wi-Fi, certificados e proteção de pontos finais.              |
| [Dispositivos](device-management.md)                              | Certifique-se de que os dispositivos que gere estão a disponibilizar os recursos de que os seus utilizadores finais necessitam para trabalhar ao proteger os dados da sua empresa contra riscos. Faça a gestão de dispositivos ao rever o inventário de dispositivos da força de trabalho e efetuar ações remotas nos dispositivos.                                                      |
| [Aplicações móveis](app-management.md)                             | Saiba como adicionar, implementar, monitorizar, configurar e proteger aplicações.                                                                                                                                                                                                                             |
| [Acesso condicional](conditional-access.md)                  | Defina condições com base em aplicações e dispositivos que impeçam o acesso aos dados da sua empresa.                                                                                                                                                                                                            |
| [Utilizadores](users-add.md)                                        | Saiba como adicionar utilizadores aos dispositivos e aplicações que gere.                                                                                                                                                                                                                                           |
| [Grupos](groups-get-started.md)                              | Saiba como criar e gerir grupos com o Intune. Pode tirar partido dos grupos para atribuir rapidamente políticas de configuração e de proteção a dispositivos e aplicações.                                                                                                                                             |
| [Funções do Intune](role-based-access-control.md)                 | Saiba como controlar quem pode realizar várias ações do Intune e como são aplicadas as mesmas. Pode utilizar as funções incorporadas que abrangem alguns cenários comuns do Intune ou pode criar as suas próprias funções.                                                                                 |
| [Atualizações de software](windows-update-for-business-configure.md) | Saiba como configurar as atualizações de software para dispositivos Windows 10.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>Novidades?

Para saber mais sobre as mais recentes funcionalidades do Microsoft Intune, veja as [Novidades](whats-new.md).
