---
title: Considerações sobre quando gerir dispositivos Windows com o Intune no Azure
description: Considerações sobre quando utilizar o Intune no Azure para gerir os dispositivos Windows da sua organização.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 71effb587bfb82ecae18afda67b05fffd2127052
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
ms.locfileid: "30015264"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune na consola do Azure e Cliente de PC do Intune legado

O Intune foi recentemente movido para uma arquitetura de serviço de aplicações SaaS baseado no Azure. O Azure oferece melhorias significativas ao nível da escala, capacidade e desempenho. Esta transição também oferece experiências do administrador do Intune melhoradas e fluxos de trabalho otimizados no portal do Azure. 

Quando utilizar o Intune no Azure para gerir os dispositivos Windows da sua organização, tenha em consideração os seguintes aspetos:

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>As funcionalidades do Cliente de PC legadas só estão disponíveis na consola do Silverlight

Os fluxos de trabalho de gestão do Cliente de PC do Intune utilizam a [Consola de Administração do Intune baseada no Silverlight](https://manage.microsoft.com/), que tem as seguintes consequências:

- Para todas as tarefas de gestão não agrupadas que utilizam o Cliente de PC do Intune, tem de utilizar a consola do Silverlight.
- Quando gerir grupos, tem de utilizar o [Intune no portal do Azure](https://portal.azure.com/). Este requisito existe porque o Intune agora utiliza Grupos do Azure AD, em vez de Grupos do Intune legados. 

Devido à mudança para os Grupos do Azure AD, a filtragem “baseada nos grupos” nas vistas do dashboard da consola do Silverlight mudou ligeiramente. Para filtrar na UI do Silverlight atualizada, siga estes passos:

1. Selecione uma vista.
2. Na caixa **Filtros**, introduza o nome do grupo pelo qual quer filtrar e prima Enter. Deste modo, vai filtrar a vista de lista dos dispositivos nesse grupo específico.

   ![](media/intune_on_azure/image01.png)

## <a name="manage-windows-10-devices-by-using-mdm"></a>Gerir dispositivos Windows 10 com a MDM

Recomendamos que utilize a [Gestão de Dispositivos Móveis (MDM) para gerir os dispositivos Windows 10](https://docs.microsoft.com/intune/device-restrictions-windows-10), em vez de utilizar o cliente de PC do Intune legado. A capacidade para gerir o Windows 10 com a MDM está disponível no Intune no portal do Azure. A MDM do Windows 10 proporciona muitas capacidades de segurança e gestão novas que não estão disponíveis através do cliente de PC do Intune legado.

## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Continuar a gerir o Windows 7 com o Cliente de PC do Intune

Para o Windows 7, que não pode ser gerido através da MDM, vamos continuar a suportar as capacidades do Cliente de PC do Intune existentes apenas na consola do Silverlight. Considere migrar para a gestão MDM quando atualizar para o Windows 10.

## <a name="mdm-capabilities"></a>Capacidades da MDM

Para ver uma comparação detalhada entre as capacidades da MDM e do Cliente de PC, veja [Comparar a gestão de PCs Windows como computadores ou dispositivos móveis](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison). As atualizações da MDM continuarão a proporcionar novas capacidades de gestão aos dispositivos Windows 10 inscritos na MDM, incluindo opções de avaliação para aplicações do Win32. Veja as [Novidades](https://docs.microsoft.com/intune/whats-new) para estar a par de tudo o que foi adicionado ao serviço nas versões mais recentes.

## <a name="switch-from-pc-client-to-mdm"></a>Mudar do Cliente de PC para a MDM

Para mudar da gestão de dispositivos Windows 10 com o Cliente de PC do Intune para a gestão com a MDM, siga estes passos:

1. Na consola do Silverlight, execute uma **Eliminação seletiva** para anular a inscrição do dispositivo do Cliente de PC.
  ![](media/intune_on_azure/image02.png)
2. Volte a inscrever o dispositivo através da [MDM (e/ou Associação Azure AD)](https://docs.microsoft.com/intune/windows-enroll). 

## <a name="next-steps"></a>Próximos passos
[Inscrever dispositivos Windows](https://docs.microsoft.com/intune/windows-enroll)

 
