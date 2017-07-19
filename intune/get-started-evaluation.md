---
title: "Introdução ao Intune"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>O que é o Microsoft Intune?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Microsoft Intune no portal do Azure](./media/generic-intune-azure.png)

O Microsoft Intune é um dos serviços mais recentes do Azure. O Intune oferece ferramentas que lhe permitem gerir os dispositivos móveis, PCs e aplicações da sua organização que recebem [atualizações regularmente](whats-new.md). Além de conter a consola moderna do Azure, o Intune também lhe permite utilizar a Consola Clássica. A Consola Clássica é a primeira versão do Intune e o local a que ainda deve aceder para [gerir PCs Windows com o cliente de software do Intune](/intune-classic/deploy-use/pc-management-comparison.md). O Portal Clássico, incorporado no Silverlight, é utilizado para uma pequena quantidade de tarefas. Tudo o resto, incluindo a gestão de dispositivos móveis e aplicações, é efetuada no portal do Azure. O guia de introdução irá orientá-lo ao longo das tarefas básicas que precisa de efetuar para utilizar o Intune no portal do Azure de forma bem-sucedida.

![O painel de ajuda e suporte, disponível na parte inferior da lista de ações na barra lateral esquerda do Intune.](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>O que é que o Intune no portal do Azure fornece?

O Intune no portal do Azure fornece-lhe:

* Uma consola integrada para todos os [componentes do Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security)
* Uma consola baseada em HTML e em normas da Web que suporta [browsers modernos](supported-devices-browsers.md)
* [Grupos do Azure Active Directory](groups-get-started.md) para proporcionar compatibilidade em todas as suas aplicações do Azure
* Automatização através da [Microsoft Graph API](intune-graph-apis.md)

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, tem de ter uma conta de administrador e de inquilino do Intune ativada. Pode inscrever-se nessas contas [aqui](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20). Os subscritores atuais também podem concluir estas atividades no seu inquilino dinâmico. Certifique-se de que está a trabalhar apenas em dispositivos de teste!

Também deverá garantir que é o administrador global da sua organização para poder concluir todas as tarefas descritas no guia.
