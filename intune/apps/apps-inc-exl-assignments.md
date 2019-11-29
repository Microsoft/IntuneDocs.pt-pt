---
title: Incluir e excluir atribuições de aplicações no Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Microsoft Intune para incluir e excluir atribuições de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 40cbb62a620d6e174ab8acb76798ba53080b78cf
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563983"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Incluir e excluir atribuições de aplicações no Microsoft Intune

No Intune, pode determinar quem tem acesso a uma aplicação ao atribuir os grupos de utilizadores a incluir e a excluir. Antes de atribuir grupos à aplicação, tem de definir o tipo de atribuição de uma aplicação. O tipo de atribuição faz com que a aplicação fique disponível, seja necessária ou desinstala a aplicação. 

Para definir a disponibilidade de uma aplicação, pode incluir e excluir atribuições de aplicações para um grupo de utilizadores ou dispositivos ao utilizar uma combinação de inclusão e exclusão de atribuições de grupo. Esta funcionalidade pode ser útil quando disponibiliza a aplicação ao incluir um grande grupo e, em seguida, limita os utilizadores selecionados ao excluir um grupo mais pequeno. O grupo mais pequeno pode ser um grupo de teste ou grupo executivo. 

Como prática recomendada, crie e atribua aplicativos especificamente para seus grupos de usuários e separadamente para seus grupos de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar usuários e dispositivos](~/fundamentals/groups-add.md).  

Existem cenários importantes ao incluir ou excluir atribuições de aplicativo:

- A exclusão tem precedência sobre a inclusão nos seguintes cenários de tipo de Grupo:
    - Incluindo grupos de usuários e excluindo grupos de usuários ao atribuir aplicativos
    - Incluindo grupos de dispositivos e excluindo o grupo de dispositivos ao atribuir aplicativos

    Por exemplo, se você atribuir um grupo de dispositivos ao grupo de usuários **todos os usuários corporativos** , mas excluir Membros no grupo de usuários da **equipe de gerenciamento sênior** , **todos os usuários corporativos** , exceto a **equipe de gerenciamento sênior** , obterão a atribuição, pois ambos os grupos são grupos de usuários.
- O Intune não avalia as relações de grupo de usuário para dispositivo. Se você atribuir aplicativos a grupos mistos, os resultados poderão não ser o que você deseja ou esperar.

    Por exemplo, se você atribuir um grupo de dispositivos ao grupo de usuários **todos os usuários** , mas excluirá um grupo de dispositivos de **todos os dispositivos pessoais** . Nesta atribuição de aplicativo de grupo misto, **todos os usuários** obtêm o aplicativo. A exclusão não se aplica.

Como resultado, não é recomendável atribuir aplicativos a grupos mistos.

> [!NOTE]
> Ao definir uma atribuição de grupo para uma aplicação, o tipo **Não Aplicável** é preterido e substituído pela exclusão de funcionalidades de grupo. 
>
> O Intune disponibiliza os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola. Os grupos têm otimizações incorporadas para sua comodidade. Recomendamos vivamente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos “todos os utilizadores” ou “todos os dispositivos” que possa criar.  
>
> O Android Enterprise suporta a inclusão e exclusão de grupos. Pode tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações Android Enterprise. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Incluir e excluir grupos ao atribuir aplicações 
Para atribuir uma aplicação aos grupos através da atribuição de inclusão e exclusão:
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **todos os aplicativos**. É apresentada a lista de aplicações adicionadas.
3. Selecione a aplicação que pretende atribuir. Um dashboard apresenta informações sobre a aplicação. 
4. Na secção **Gerir** do menu, selecione **Atribuições**. 

    ![Incluir atribuições de aplicativo ao atribuir aplicativos](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)

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
