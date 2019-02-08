---
title: Página de estado do inquilino do Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize a página de estado do inquilino do Intune para ver os detalhes de inquilino importante sem sair do portal do Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8bdb74c19e6b996bafc9284bfedaf0608fdf8fb
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834624"
---
# <a name="intune-tenant-status-page"></a>Página de estado do inquilino do Intune
Utilize a página de estado do inquilino como um concentrador centralizado para se manter atualizado sobre a detalhes importantes sobre o seu inquilino, disponibilidade de licença e utilização, estado do conector e as comunicações importantes sobre o serviço Intune.  

Para ver o dashboard, no portal do Azure, aceda a **Intune > Estado do inquilino**.  Estado do inquilino é apresentado no **ajudar e o grupo de suporte**.  

A página é dividida em quatro áreas:

## <a name="tenant-details"></a>Detalhes do inquilino
Detalhes de inquilino fornecer em rapidamente informações sobre o seu inquilino. Ver detalhes como nome do seu inquilino e localização, a autoridade de MDM e o número de versão do serviço de inquilinos. O número de versão do serviço é uma ligação que abre o *o que há de novo no Intune* artigo nos documentos da Microsoft, onde pode ler sobre as mais recentes funcionalidades e atualizações para o serviço do Intune.  

Esta secção também fornece informações básicas sobre as licenças disponíveis e quantas estão atribuídas a utilizadores. Licenças para dispositivos não são apresentadas.

## <a name="connector-status"></a>Estado do conector
Estado do conector é um local de um único local para rever o estado de todos os conectores disponíveis para o Intune.  

Os conectores são:
- **Ligações que configurar para serviços externos**. Por exemplo, o *Apple Volume Purchase Program* serviço ou o *Windows Autopilot* serviço.  Estado para este tipo de conector baseia-se a hora da última sincronização efetuada com êxito.
- **Certificados ou as credenciais que são necessárias para ligar a um serviço externo de não-gerenciado**, como *Apple Push Notification Services* certificados (APNS). Estado para este tipo de conector baseia-se o carimbo de hora de expiração do certificado ou credenciais.  

Por predefinição, apenas cinco conectores apresentam. Pode selecionar **ver todos os conectores** expandir essa lista para ver todos os conectores disponíveis, incluindo os conectores que ainda não configurou para utilização.  

Quando existe mais do que um único conector de qualquer tipo, o estado é um resumo de todos os conectores do mesmo. O estado de bom estado de funcionamento, pelo menos, de qualquer conector único é utilizado como o estado de funcionamento para o grupo.  

Conectores de mau estado de funcionamento apresentam sempre na parte superior da lista. Em seguida, estão conectores com avisos e, em seguida, a lista de conectores em bom estado. Os conectores que ainda não configurou aparecem em último lugar.

**Estado do conector:**
- **Unhealthy:**
    - O certificado ou a credencial expirou
    - A última sincronização foi três ou mais dias atrás
- **Aviso:**
    - O certificado ou a credencial expira dentro de sete dias
    - A última sincronização foi há mais de um dia
- **Bom estado de funcionamento:**
    - O certificado ou a credencial não expira nos próximos sete dias
    - A última sincronização foi há menos de um dia  

Quando seleciona um conector na lista, o portal apresenta a página de portal que é relevante para criar ou configurar esse conector.  Por exemplo, quando seleciona a **data de expiração de VPP** conector, o **iOS compradas em volume Tokens do programa** onde pode ver mais detalhes sobre esse conector de é aberta a página. Em seguida, pode criar uma nova configuração ou editar e corrigir problemas com um já existente.  

## <a name="intune-service-health"></a>Estado de funcionamento do serviço do Intune  
Pode ver os detalhes para incidentes activos e consultorias sem ter de navegar para o Dashboard de estado de funcionamento de serviço do Microsoft 365 ou o Centro de mensagens, localizados no Centro de administração do Microsoft 365 em https://portal.office.com. Apenas os incidentes onde impacto tem sido observado para afetar o seu inquilino são apresentados.  

Quando seleciona um incidente, são apresentados os detalhes do incidente diretamente na página de estado do inquilino. Para ver os passados consultorias e incidentes, selecione **Consulte anteriores incidentes/Consultorias**. Abre o Centro de administração do Microsoft 365 e, em seguida, pode ver as consultorias e incidentes dos últimos 30 dias para o seu inquilino.  

Para ver as informações de *Intune Service Health*, a conta tem de ter o **Administrador Global** ou **administrador de serviços** função no Azure Active Directory ou o Portal de administração do Office. Para atribuir estas permissões, inicie sessão para o [Centro de administração do Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) com permissões de Administrador Global. Selecione **utilizadores > utilizadores ativos**e, em seguida, selecione a conta que precisa de acesso. Selecione **edite** para funções, selecione *administrador de serviços* ou *Administrador Global*e, em seguida **guardar** sua edição para atribuir a permissões.  

Só pode configurar suas preferências de comunicação para o estado de funcionamento do serviço Intune através do Centro de administração do Microsoft 365.

## <a name="intune-news"></a>Notícias do Intune  
Ver informativas comunicações da equipa do serviço Intune sem ter de navegar para o Centro de mensagens do Office. Comunicações incluem mensagens sobre as alterações que ocorreram recentemente para o serviço do Intune ou que estão a caminho para o seu inquilino.  

Por predefinição, apresentam as últimas 10 mensagens de Active Directory. Para ver mensagens mais antigas, selecione **ver últimas mensagens** para abrir o *Centro de mensagens* no portal do Centro de administração do Microsoft 365.  

Para ver as informações de notícias do Intune, sua conta tem de ter o **Administrador Global** ou **administrador de serviço** função no Azure Active Directory, ou estar atribuído a **leitor do Centro de mensagens**  função no portal de administração do Office.  Para atribuir esta permissão, inicie sessão para o [Centro de administração do Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) com permissões de administrador. Selecione **utilizadores > utilizadores ativos**e, em seguida, selecione a conta que precisa de acesso. Selecione **editar** para *funções*, selecione *Equipes comunicações administrador*e, em seguida **guardar** sua edição para atribuir as permissões.  

Só pode configurar suas preferências de comunicação de notícias do Intune através do Centro de administração do Microsoft 365.
