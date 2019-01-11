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
ms.openlocfilehash: 0da6861b6c49fc37691b8c6e464a506670643fa3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203336"
---
# <a name="use-scope-tags-to-filter-policies"></a>Utilizar etiquetas de âmbito para filtrar políticas

As etiquetas de âmbito permitem-lhe filtrar políticas com as etiquetas personalizadas que criar. Pode aplicar etiquetas de âmbito para aplicações e funções.

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

