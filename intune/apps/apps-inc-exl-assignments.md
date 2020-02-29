---
title: Incluir e excluir atribuições de aplicações no Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Microsoft Intune para incluir e excluir atribuições de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efc712840a75e533e85ea8c930e2b2ac5aaf119e
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181743"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Incluir e excluir atribuições de aplicações no Microsoft Intune

No Intune, pode determinar quem tem acesso a uma aplicação ao atribuir os grupos de utilizadores a incluir e a excluir. Antes de atribuir grupos à aplicação, tem de definir o tipo de atribuição de uma aplicação. O tipo de atribuição faz com que a aplicação fique disponível, seja necessária ou desinstala a aplicação. 

Para definir a disponibilidade de uma aplicação, pode incluir e excluir atribuições de aplicações para um grupo de utilizadores ou dispositivos ao utilizar uma combinação de inclusão e exclusão de atribuições de grupo. Esta funcionalidade pode ser útil quando disponibiliza a aplicação ao incluir um grande grupo e, em seguida, limita os utilizadores selecionados ao excluir um grupo mais pequeno. O grupo mais pequeno pode ser um grupo de teste ou grupo executivo. 

Como uma boa prática, crie e atribua aplicações especificamente para os seus grupos de utilizadores e separadamente para os grupos de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar utilizadores e dispositivos](~/fundamentals/groups-add.md).  

Existem cenários importantes ao incluir ou excluir atribuições de aplicações:

- A exclusão prevalece sobre a inclusão nos seguintes cenários de grupo:
    - Incluir grupos de utilizadores e excluir grupos de utilizadores ao atribuir aplicações
    - Incluindo grupos de dispositivos e excluindo grupo de dispositivos ao atribuir aplicações

    Por exemplo, se atribuir um grupo de dispositivos ao grupo de utilizadores de **todos os utilizadores corporativos,** mas excluir membros do grupo de utilizadores do Staff de **Gestão Sénior,** **todos os utilizadores corporativos,** exceto o pessoal de **Gestão Sénior,** obtêm a atribuição, porque ambos os grupos são grupos de utilizadores.
- Intune não avalia as relações de grupo de utilizador para dispositivo. Se atribuir aplicações a grupos mistos, os resultados podem não ser o que pretende ou espera.

    Por exemplo, se atribuir um grupo de dispositivos ao grupo de utilizadores todos os **utilizadores,** mas excluir um grupo de **dispositivos todos os dispositivos pessoais.** Nesta atribuição de aplicativos de grupo misto, **todos os utilizadores** recebem a app. A exclusão não se aplica.

Como resultado, não é recomendado atribuir apps a grupos mistos.

> [!NOTE]
> Ao definir uma atribuição de grupo para uma aplicação, o tipo **Não Aplicável** é preterido e substituído pela exclusão de funcionalidades de grupo. 
>
> O Intune disponibiliza os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola. Os grupos têm otimizações incorporadas para sua comodidade. Recomendamos vivamente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos “todos os utilizadores” ou “todos os dispositivos” que possa criar.  
>
> O Android Enterprise suporta a inclusão e exclusão de grupos. Pode tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações Android Enterprise. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Incluir e excluir grupos ao atribuir aplicações 
Para atribuir uma aplicação aos grupos através da atribuição de inclusão e exclusão:
1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações.** É apresentada a lista de aplicações adicionadas.
3. Selecione a aplicação que pretende atribuir. Um dashboard apresenta informações sobre a aplicação. 
4. Na secção **Gerir** do menu, selecione **Atribuições**. 

    ![Incluir atribuições de aplicativos ao atribuir apps](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)

5. Selecione **Adicionar grupo** para adicionar os grupos de utilizadores que estão atribuídos à aplicação. 
6. No painel **Adicionar grupo**, selecione um **Tipo de atribuição** nos tipos de atribuição disponíveis.
7. Para o tipo de atribuição, selecione **Disponível com ou sem inscrição**.

    ![Atribuições de aplicações do Intune – adicionar grupo](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
8. Selecione **Grupos Incluídos** para selecionar o grupo de utilizadores para o qual quer disponibilizar esta aplicação.

    > [!NOTE]
    > Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, a aplicação estará pré-selecionada e inalterável para outros tipos de atribuição de inclusão. O grupo que foi utilizado não poderá ser utilizado como um grupo incluído.

9. Selecione **Sim** para disponibilizar esta aplicação para todos os utilizadores.

    ![Atribuições de aplicações do Intune – incluir grupos](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
10. Selecione **OK** para definir o grupo a incluir.
11. Selecione **Grupos Excluídos** para selecionar os grupos de utilizadores para os quais não quer disponibilizar esta aplicação. 
12. Selecione os grupos a excluir. Esta ação faz com que esta aplicação fique indisponível para esses grupos.

    ![Atribuições de aplicações do Intune – excluir grupos](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
13. Selecione **Selecionar** para concluir a seleção de grupos.
14. No painel **Adicionar grupo**, selecione **OK**. É apresentada a lista de **Atribuições** de aplicações.
15. Clique em **Guardar** para aplicar as suas atribuições de grupo à aplicação.

Quando realizar atribuições de grupo, os grupos que já tiverem sido atribuídos não estarão disponíveis para serem modificados. Se quiser selecionar um grupo que esteja atualmente indisponível, primeiro remova a aplicação da lista de atribuições. 

Pode editar atribuições, na lista de **Atribuições** da aplicação, selecione a linha que contém a atribuição específica que quer alterar. Além disso, pode remover uma atribuição ao selecionar as reticências ( **…** ) no final da linha e ao selecionar **Remover**. Para alterar a vista da lista de **Atribuições**, agrupe por **Tipo de atribuição** ou por **Incluído/Excluído**.

![Atribuições de aplicações do Intune – concluir](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como incluir e excluir atribuições de grupo para aplicações, veja o [Blogue do Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Saiba como [monitorizar informações e atribuições da aplicação](apps-monitor.md).
