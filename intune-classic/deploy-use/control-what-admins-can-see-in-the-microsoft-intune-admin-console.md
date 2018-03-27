---
title: Personalizar vistas da consola para funções de administrador
description: Utilize este tópico para obter ajuda para filtrar a vista da consola de administração do Intune de modo a permitir aos administradores verem apenas os itens de que precisam no âmbito das funções deles.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9baa0325a90e152ffd6cf6a31cdd0a458588758a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="customize-intune-console-views-according-to-admin-roles"></a>Personalizar vistas da consola do Intune de acordo com funções de administrador

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pode filtrar a vista da consola de administração do Microsoft Intune para permitir que os seus administradores vejam apenas os itens que precisam de ver para desempenharem a sua função. Por exemplo, pode permitir que apenas os operadores da consola de administração atualizem definições de software maligno ou redefinam o código de acesso nos dispositivos. Esta filtragem é executada através de **designações** predefinidas que são atribuídas a utilizadores específicos. Quando estes utilizadores acedem à consola de administração, apenas podem ver os itens específicos para as suas designações.

## <a name="to-create-a-custom-view"></a>Para criar uma vista personalizada

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Admin** &gt; **Administradores do Serviço**.

2.  Na lista de administradores do serviço, escolha o utilizador cuja designação pretende alterar e, em seguida, escolha **Gerir Acesso**.

3.  Na caixa de diálogo **Gerir Acesso**, escolha o nível de acesso que pretende dar ao utilizador selecionado. Pode escolher entre:

    -   **Acesso total**
    -   **Acesso só de leitura**
    -   **Suporte técnico – nó Grupos**

    O acesso total e o acesso só de leitura são facilmente compreensíveis. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the Intune admin console:--->

    **Suporte técnico - nó Grupos** restringe o que o administrador pode ver e fazer ao seguinte:

    -   Ver listas de utilizadores e dispositivos. O administrador não pode utilizar filtros para modificar a vista. No entanto, pode utilizar a filtragem de grupos para modificar o que ele conseguirá ver. Para obter mais informações, consulte [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Imprimir a lista de utilizadores e dispositivos

    -   Exportar a lista de utilizadores e dispositivos

    -   Ver as propriedades de um utilizador ou dispositivo

    -   Efetuar as seguintes tarefas remotas:

        -   Executar uma análise completa de malware

        -   Executar uma análise rápida de malware

        -   Reiniciar um computador

        -   Atualizar definições de software maligno

        -   Atualizar políticas

        -   Atualizar inventário

        -   Bloquear remotamente um dispositivo

        -   Repor um código de acesso

Da próxima vez que o administrador configurado abrir a consola de administração do Intune, ser-lhe-á concedido o nível de acesso que lhe tiver designado.
