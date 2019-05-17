---
title: No desenvolvimento – Microsoft Intune
titleSuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 3645d07fe9a703f182e05bc9a7f9fbb93c413ddc
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816248"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>No desenvolvimento do Microsoft Intune – Maio de 2019

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


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Suporte de linha de base para a palavra-chave de pesquisa  <!-- 3082036         -->
Ao criar ou editar um perfil de linha de base de segurança, em breve será capaz de usar *pesquisa* para filtrar as definições que são apresentados na consola do.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Repor e apagar dispositivos em massa ao utilizar a Graph API <!-- 3295288 -->
Poderá repor e a eliminação de até 100 dispositivos em massa com a Graph API.

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Os utilizadores de dispositivos, podem ver todas as aplicações geridas que tenham instalado ou tentou instalar <!-- 2352913 -->
Portal da empresa para Windows irá listar todas as aplicações geridas&ndash; tanto necessária quanto disponível&ndash; que estão instaladas no dispositivo de um utilizador. Os utilizadores serão capazes de vista de tentativa e pendentes instalações de aplicações e respetivos Estados atuais. Se sua organização não torne as aplicações necessárias ou disponíveis, os utilizadores verão uma mensagem que explica que não existem aplicações da empresa foram instaladas. Os utilizadores também serão capazes de classificar ou filtrar as suas aplicações por Estado da instalação.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilize "regras de aplicabilidade" quando criar perfis de configuração de dispositivo Windows 10 <!-- 2549910 -->
Criar perfis de configuração de dispositivo Windows 10 (**configuração do dispositivo** > **perfis** > **criar perfil**  >  **Windows 10** para a plataforma). Poderá criar uma **regra de aplicabilidade** para que o perfil apenas se aplica a uma edição específica ou uma versão específica. Por exemplo, criar um perfil que permite que algumas configurações de disco BitLocker. Depois de adicionar o perfil, utilize uma regra de aplicabilidade para que o perfil apenas se aplica a dispositivos com o Windows 10 Enterprise.

Aplica-se a: 
- Windows 10 e posterior



## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.


