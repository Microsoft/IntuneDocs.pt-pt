---
title: Políticas de proteção de aplicativo para extensões
titleSuffix: Microsoft Intune
description: Este tópico descreve a política de proteção de aplicativo (aplicativo) para extensões do.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a94f3d175fe5c036c5e90635a66467263b23122
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499125"
---
# <a name="protecting-application-extensions"></a>Protegendo extensões de aplicativo

Este artigo descreve as políticas de proteção de aplicativo para extensões no Microsoft Intune.

## <a name="add-ins-for-outlook-app"></a>Suplementos para a aplicação Outlook

Os suplementos do Outlook permitem integrar aplicativos populares ao cliente de email. Os suplementos para Outlook estão disponíveis na Web, Windows, Mac e Outlook para Android e iOS. As políticas do SDK de aplicativo do Intune e da proteção de aplicativo do Intune não incluem suporte para o gerenciamento de suplementos para o Outlook, mas há outras maneiras de limitar seu uso. Uma vez que os suplementos são geridos através do Microsoft Exchange, os utilizadores serão capazes de partilhar dados e mensagens no Outlook e em aplicações de suplementos não geridas, exceto se os suplementos forem desativados para o utilizador pelo Exchange deles.

Se quiser impedir que os seus utilizadores finais acedam e instalem suplementos do Outlook (afeta todos os clientes do Outlook), confirme que tem as seguintes alterações das funções no Centro de administração do Exchange:

- Para impedir que os utilizadores instalem suplementos da Loja Office, remova a função O Meu Mercado desses utilizadores.
- Para impedir que os utilizadores realizem sideloading de suplementos, remova a função As Minhas Aplicações Personalizadas desses utilizadores.
- Para impedir que os utilizadores instalem todos os suplementos, remova as funções As Minhas Aplicações Personalizadas e O Meu Mercado.

Estas instruções aplicam-se ao Office 365, ao Exchange 2016, ao Exchange 2013 no Outlook na Web, ao Windows, ao Mac e aos dispositivos móveis.

- Saiba mais sobre os [suplementos para o Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Saiba mais sobre os [como especificar os administradores e utilizadores que podem instalar e gerir suplementos para a aplicação Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Ligações de conta do LinkedIn em aplicações da Microsoft

As ligações de conta do LinkedIn permitem aos utilizadores ver informações de perfis públicos do LinkedIn em determinadas aplicações da Microsoft. Por predefinição, os utilizadores podem optar por ligar as respetivas contas escolares ou profissionais Microsoft e as contas do LinkedIn para ver informações adicionais de perfis do LinkedIn. 

> [!NOTE]
> Atualmente, a integração do LinkedIn não está disponível para clientes do Governo dos Estados Unidos nem para organizações com caixas de correio do Exchange Online alojadas na África do Sul, Alemanha, Austrália, Canadá, China, Coreia do Sul, França, Índia, Japão e Reino Unido.

As políticas de proteção da aplicação Intune e do SDK do Intune não incluem suporte para a gestão de ligações de conta do LinkedIn, mas existem outras formas de as gerir. Pode desativar as ligações de conta do LinkedIn para toda a sua organização ou ativar estas ligações para grupos de utilizadores específicos na sua organização. Estas definições afetam as ligações do LinkedIn em todas as aplicações do Office 365 em todas as plataformas (Web, móveis e de ambiente de trabalho). É possível:

- Ativar ou desativar as ligações de conta do LinkedIn para o seu inquilino no portal do Azure. 
- Ativar ou desativar as ligações de conta do LinkedIn para as aplicações do Office 2016 da sua organização que utilizem a Política de Grupo.

Se a integração do LinkedIn estiver ativada para o seu inquilino, os utilizadores da sua organização terão duas opções quando ligarem as suas contas escolares ou profissionais Microsoft às contas do LinkedIn: 

- Podem dar permissão para partilhar dados entre ambas as contas. Isto significa que dão permissão para que a conta do LinkedIn partilhe dados com a conta escolar ou profissional Microsoft e vice-versa. Os dados que são partilhados com o LinkedIn saem dos serviços online. 
- Os utilizadores podem dar permissão para partilhar dados apenas da conta do LinkedIn para a conta escolar ou profissional Microsoft

Se um utilizador consentir partilhar dados entre as contas, tal como os suplementos do Office, a integração do LinkedIn utilizará as APIs do Microsoft Graph existentes. A integração do LinkedIn só utiliza um subconjunto de APIs disponível aos suplementos do Office e suporta várias exclusões.


|Permissões do Microsoft Graph  |Description  |
|---------|---------|
|Permissões de leitura para [Pessoas](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)     |Permite que a aplicação leia uma lista com classificações de pessoas relevantes para o utilizador com sessão iniciada. A lista pode incluir contactos locais, contactos de redes sociais ou do diretório da sua organização e pessoas de comunicações recentes (como e-mail e Skype).         |
|Permissões de leitura para [Calendários](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)     |Permite que a aplicação leia eventos nos calendários dos utilizadores. Inclui as reuniões nos calendários de utilizadores com sessão iniciada, as respetivas horas, localizações e participantes.         |
|Permissões de leitura para [Perfil de Utilizador](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)     |Permite que os utilizadores iniciem sessão na aplicação e permite que a aplicação leia o perfil dos utilizadores com sessão iniciada. Também permite que a aplicação leia informações básicas sobre a empresa dos utilizadores com sessão iniciada.         |
|Subscriptions     |Este âmbito não está disponível e ainda não está em utilização. Inclui subscrições de aplicações e serviços Microsoft, como o Office 365, fornecidas pela organização do utilizador.         |
|Informações     |Este âmbito não está disponível e ainda não está em utilização. Inclui os interesses associados à conta do utilizador com sessão iniciada, com base na respetiva utilização dos serviços Microsoft.         |

### <a name="learn-more"></a>Saiba mais

- Saiba mais sobre [Informações e funcionalidades do LinkedIn nas suas aplicações da Microsoft](https://go.microsoft.com/fwlink/?linkid=850740).
- Saiba mais sobre o lançamento das ligações de conta do LinkedIn na [página do Plano do Office 365](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Saiba mais sobre [Configuring LinkedIn account connections](https://docs.microsoft.com/azure/active-directory/linkedin-integration) (Configurar as ligações de conta do LinkedIn).
- Para obter mais informações sobre os dados que são partilhados entre as contas escolares ou profissionais Microsoft e as contas do LinkedIn dos utilizadores, veja [LinkedIn in Microsoft applications at your work or school](https://www.linkedin.com/help/linkedin/answer/84077) (O LinkedIn em aplicações da Microsoft na sua escola ou trabalho).

