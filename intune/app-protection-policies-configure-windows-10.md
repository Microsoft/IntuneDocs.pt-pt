---
title: Configurar políticas de proteção de aplicações para Windows 10
titleSuffix: Microsoft Intune
description: Este tópico descreve como configurar políticas de proteção de aplicações (aplicação) para dispositivos Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8ea91d037cce88f98850c3220b9856e7231fa0b
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57389320"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Preparar-se para configurar políticas de proteção de aplicações para o Windows 10 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ative a gestão de aplicações móveis (MAM) para o Windows 10 ao definir o fornecedor de MAM no Azure AD. Definir um fornecedor de MAM no Azure AD permite-lhe definir o estado de inscrição ao criar uma nova política do Windows Information Protection (WIP) com o Intune. O estado de inscrição pode ser MAM ou gestão de dispositivos móveis (MDM).

## <a name="to-configure-the-mam-provider"></a>Para configurar o fornecedor de MAM

1. Inicie sessão no portal do Azure e selecione **Azure Active Directory.**

2. Selecione **Mobilidade (MDM e MAM)** no grupo **Gerir**.

3. Clique em **Microsoft Intune**.

4. Configure as definições no grupo **Restaurar URLs MAM predefinidos** no painel **Configurar**.

   **Âmbito de utilizador MAM**  
   Utilize a inscrição automática MAM para gerir dados empresariais nos dispositivos Windows dos seus funcionários. A inscrição automática MAM será configurada para cenários de Bring Your Own Device.<ul><li>**Nenhum**<br>Selecione se nenhum utilizador pode ser inscrito na MAM.</li><li>**Alguns**<br>Selecione grupos do Azure AD que contenham utilizadores que serão inscritos na MAM.</li><li>**Todos**<br>Selecione se todos os utilizadores podem ser inscritos na MAM.</li></ul>

   **URL dos termos de utilização da MAM**  
   O URL dos termos de utilização da MAM não é suportado no Microsoft Intune. Esta caixa de introdução tem de ser deixada em branco para aplicar políticas de proteção.

   **URL de deteção da MAM**  
   O URL do ponto final de inscrição da MAM. O ponto final de inscrição é utilizado para inscrever dispositivos para gestão com a MAM.

   **URL de conformidade da MAM**  
   O URL de conformidade da MAM não é suportado no Microsoft Intune. Esta caixa de introdução tem de ser deixada em branco para aplicar políticas de proteção. 

5.  Clique em **Guardar**.

## <a name="next-steps"></a>Passos Seguintes

[Criar uma política de proteção de aplicações WIP](windows-information-protection-policy-create.md)
