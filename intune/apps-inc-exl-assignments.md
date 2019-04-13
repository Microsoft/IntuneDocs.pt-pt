---
title: Incluir e excluir atribuições de aplicações no Microsoft Intune
titleSuffix: ''
description: Saiba como pode utilizar o Microsoft Intune para incluir e excluir atribuições de aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48ec49b0539711fa50083850ea394a369a3c65b9
ms.sourcegitcommit: af2512a1342d8037a96a61c8cc2c63e107913733
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59533524"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Incluir e excluir atribuições de aplicações no Microsoft Intune

No Intune, pode determinar quem tem acesso a uma aplicação ao atribuir os grupos de utilizadores a incluir e a excluir. Antes de atribuir grupos à aplicação, tem de definir o tipo de atribuição de uma aplicação. O tipo de atribuição faz com que a aplicação fique disponível, seja necessária ou desinstala a aplicação. 

Para definir a disponibilidade de uma aplicação, pode incluir e excluir atribuições de aplicações para um grupo de utilizadores ou dispositivos ao utilizar uma combinação de inclusão e exclusão de atribuições de grupo. Esta funcionalidade pode ser útil quando disponibiliza a aplicação ao incluir um grande grupo e, em seguida, limita os utilizadores selecionados ao excluir um grupo mais pequeno. O grupo mais pequeno pode ser um grupo de teste ou grupo executivo. 

Ao excluir grupos de uma atribuição de aplicações, tem de excluir apenas grupos de utilizadores ou apenas grupos de dispositivo. Não pode excluir uma combinação de grupos de utilizadores e grupos de dispositivos. 

O Intune não tem em consideração a associação de utilizadores a dispositivos ao excluir grupos. Incluir grupos de utilizadores e excluir grupos de dispositivos provavelmente não produzirá os resultados de que precisa. A inclusão tem precedência sobre a exclusão. Por exemplo, se direcionar uma aplicação iOS para **Todos os Utilizadores** e excluir **Todos os iPads**, o resultado será que qualquer utilizador que utilize um iPad continuará a obter a aplicação. No entanto, se direcionar a aplicação iOS para **Todos os Dispositivos** e excluir **Todos os iPads**, a implementação ocorrerá com êxito.  

> [!NOTE]
> Ao definir uma atribuição de grupo para uma aplicação, o tipo **Não Aplicável** é preterido e substituído pela exclusão de funcionalidades de grupo. 
>
> O Intune disponibiliza os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola. Os grupos têm otimizações incorporadas para sua comodidade. Recomendamos vivamente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos “todos os utilizadores” ou “todos os dispositivos” que possa criar.  
>
> O Android Enterprise suporta a inclusão e exclusão de grupos. Pode tirar partido dos grupos incorporados **Todos os Utilizadores** e **Todos os Dispositivos** para a atribuição de aplicações Android Enterprise. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>Incluir e excluir grupos ao atribuir aplicações 
Para atribuir uma aplicação aos grupos através da atribuição de inclusão e exclusão:
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No menu **Intune**, selecione **Aplicações do cliente**.
4. No painel **Aplicações do cliente**, selecione **Aplicações**. É apresentada a lista de aplicações adicionadas.
5. Selecione a aplicação que pretende atribuir. Um dashboard apresenta informações sobre a aplicação. 
6. Na secção **Gerir** do menu, selecione **Atribuições**. 

    ![Incluir atribuições de aplicações, ao atribuir aplicações](./media/apps-inc-exl-01.png)
7. Selecione **Adicionar grupo** para adicionar os grupos de utilizadores que estão atribuídos à aplicação. 
8. No painel **Adicionar grupo**, selecione um **Tipo de atribuição** nos tipos de atribuição disponíveis.
9. Para o tipo de atribuição, selecione **Disponível com ou sem inscrição**.

    ![Atribuições de aplicações do Intune – adicionar grupo](./media/apps-inc-exl-02.png)
10. Selecione **Grupos Incluídos** para selecionar o grupo de utilizadores para o qual quer disponibilizar esta aplicação.

    > [!NOTE]
    > Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, a aplicação estará pré-selecionada e inalterável para outros tipos de atribuição de inclusão. O grupo que foi utilizado não poderá ser utilizado como um grupo incluído.

11. Selecione **Sim** para disponibilizar esta aplicação para todos os utilizadores.

    ![Atribuições de aplicações do Intune – incluir grupos](./media/apps-inc-exl-03.png)
12. Selecione **OK** para definir o grupo a incluir.
13. Selecione **Grupos Excluídos** para selecionar os grupos de utilizadores para os quais não quer disponibilizar esta aplicação. 
14. Selecione os grupos a excluir. Esta ação faz com que esta aplicação fique indisponível para esses grupos.

    ![Atribuições de aplicações do Intune – excluir grupos](./media/apps-inc-exl-04.png)
15. Selecione **Selecionar** para concluir a seleção de grupos.
16. No painel **Adicionar grupo**, selecione **OK**. É apresentada a lista de **Atribuições** de aplicações.
17. Clique em **Guardar** para aplicar as suas atribuições de grupo à aplicação.

Quando realizar atribuições de grupo, os grupos que já tiverem sido atribuídos não estarão disponíveis para serem modificados. Se quiser selecionar um grupo que esteja atualmente indisponível, primeiro remova a aplicação da lista de atribuições. 

Pode editar atribuições, na lista de **Atribuições** da aplicação, selecione a linha que contém a atribuição específica que quer alterar. Além disso, pode remover uma atribuição ao selecionar as reticências (**…**) no final da linha e ao selecionar **Remover**. Para alterar a vista da lista de **Atribuições**, agrupe por **Tipo de atribuição** ou por **Incluído/Excluído**.

![Atribuições de aplicações do Intune – concluir](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Passos Seguintes

- Para obter mais informações sobre como incluir e excluir atribuições de grupo para aplicações, veja o [Blogue do Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Saiba como [monitorizar informações e atribuições da aplicação](apps-monitor.md).
