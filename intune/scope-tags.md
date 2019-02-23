---
title: Filtrar políticas com etiquetas de âmbito no Microsoft Intune – Azure | Microsoft Docs
description: Utilize etiquetas de âmbito para filtrar perfis de configuração para funções específicas.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2536a5978bc9af99053e4513f4ceea8c0a40e633
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742266"
---
# <a name="use-scope-tags-to-filter-policies"></a>Utilizar etiquetas de âmbito para filtrar políticas

As etiquetas de âmbito permitem-lhe filtrar políticas com as etiquetas personalizadas que criar. Pode aplicar etiquetas de âmbito para aplicações e funções.

Quando um administrador cria um recurso no Intune, quaisquer etiquetas de âmbito atribuídas para cada administrador serão automaticamente atribuídas para o novo recurso.

Por exemplo, crie uma etiqueta de âmbito chamada "Departamento de Engenharia" e atribua-a a perfis de configuração relacionados com o departamento de engenharia. Atribua essa mesma etiqueta à função "Administradores de Engenharia". Apenas serão apresentadas as políticas com a etiqueta "Departamento de Engenharia".

## <a name="to-create-a-scope-tag"></a>Para criar uma etiqueta de âmbito

Selecione **Funções** > **Âmbito (Etiquetas)** > **Criar**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para adicionar uma etiqueta de âmbito a um perfil de configuração

Selecione **Configuração do dispositivo** > **Perfis** > selecione um perfil > **Propriedades** > **Âmbito (Etiquetas)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para atribuir uma etiqueta de âmbito a uma função

Selecione **Funções** > **Todas as funções** > **Gestor de Políticas e Perfis** > **Atribuições**  >  **Âmbito (Etiquetas)**.

## <a name="to-assign-a-scope-tag-to-an-app"></a>Para atribuir uma etiqueta de âmbito a uma aplicação

Escolher **aplicações de cliente** > **aplicações** > Escolha uma aplicação > **propriedades** > **âmbito (etiquetas)**  >  **Add** > Selecione as etiquetas > **selecione** > **OK** > **guardar**.


## <a name="next-steps"></a>Passos Seguintes

Efetue a gestão das suas [funções](role-based-access-control.md) e [perfis](device-profile-assign.md).

