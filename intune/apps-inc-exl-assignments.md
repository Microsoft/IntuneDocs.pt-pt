---
title: "Incluir e excluir atribuições de aplicações no Microsoft Intune"
titlesuffix: 
description: "Saiba como pode utilizar o Microsoft Intune para incluir e excluir atribuições de aplicações."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dbe8669dc2bf448e0738147758d90ba6d2d69b06
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Incluir e excluir atribuições de aplicações no Microsoft Intune

Com o Intune, pode determinar quem tem acesso a uma aplicação ao indicar os grupos a incluir e a excluir. No entanto, antes de atribuir grupos à aplicação, tem de definir o tipo de atribuição de uma aplicação. O tipo de atribuição faz com que a aplicação fique disponível, seja necessária ou desinstala a aplicação. 

Relativamente à disponibilidade de uma aplicação, pode incluir e excluir atribuições de aplicações para um grupo de utilizadores ou dispositivos ao utilizar uma combinação de inclusão e exclusão de atribuições de grupo. Esta funcionalidade pode ser útil quando disponibiliza a aplicação ao incluir um grande grupo e, em seguida, limita os utilizadores selecionados ao excluir um grupo mais pequeno. O grupo mais pequeno pode ser um grupo de teste ou grupo executivo. 

Ao excluir grupos de uma aplicação, tem de excluir apenas grupos de utilizadores ou apenas grupos de dispositivos, não uma mistura de grupos. O Intune não tem em consideração a associação de utilizadores a dispositivos ao excluir grupos. Incluir grupos de utilizadores e excluir grupos de dispositivos provavelmente não produzirá os resultados de que precisa, pois a inclusão terá precedência sobre a exclusão. Por exemplo, se direcionar uma aplicação iOS para **Todos os Utilizadores** e excluir **Todos os iPads**, o resultado será que qualquer utilizador que utilize um iPad continuará a obter a aplicação. No entanto, se direcionar a aplicação iOS para **Todos os Dispositivos** e excluir **Todos os iPads**, a implementação ocorrerá com êxito.  

>[!NOTE]
>Ao definir uma atribuição de grupo para uma aplicação, o tipo **Não Aplicável** é preterido e substituído pela exclusão de funcionalidades de grupo. 
>
>O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade. Recomendamos fortemente que utilize estes grupos para abranger todos os utilizadores e todos os dispositivos em vez dos grupos "Todos os utilizadores" ou "Todos os dispositivos" que possa ter criado.  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>Incluir e excluir grupos ao atribuir aplicações 
Para atribuir uma aplicação a grupos ao utilizar a atribuição de inclusão e exclusão:
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **Aplicações móveis** no painel do Microsoft Intune.
4. Selecione **Aplicações** no painel **Aplicações móveis**. É apresentada a lista de aplicações adicionadas.
5. Selecione a aplicação que pretende atribuir. É apresentado um dashboard relacionado com a aplicação. 
6. Selecione **Atribuições** na secção **Gerir**. 

    ![Atribuições de aplicações do Intune](./media/apps-inc-exl-01.png)
7. Selecione **Adicionar grupo** para adicionar os grupos de utilizadores que estão atribuídos à aplicação. 
8. Selecione um **Tipo de atribuição** a partir dos tipos de atribuição disponíveis no painel **Adicionar grupo**.
9. Selecione **Disponível com ou sem inscrição** como o tipo de atribuição.

    ![Atribuições de aplicações do Intune – adicionar grupo](./media/apps-inc-exl-02.png)
10. Selecione **Grupos Incluídos** para selecionar o grupo de utilizadores para o qual pretende disponibilizar esta aplicação.

    >[!NOTE]
    >Ao adicionar um grupo, se outro grupo já tiver sido incluído num determinado tipo de atribuição, o mesmo estará pré-selecionado e inalterável para outras atribuições de inclusão. Por conseguinte, esse grupo que foi utilizado não poderá ser utilizado como um grupo incluído.

11. Selecione **Sim** para disponibilizar esta aplicação para todos os utilizadores.

    ![Atribuições de aplicações do Intune – incluir grupos](./media/apps-inc-exl-03.png)
12. Clique em **OK** para definir o grupo a incluir.
13. Selecione **Grupos Excluídos** para selecionar os grupos de utilizadores para os quais não pretende disponibilizar esta aplicação. 
14. Selecione os grupos a excluir, o que torna esta aplicação indisponível para os mesmos.

    ![Atribuições de aplicações do Intune – excluir grupos](./media/apps-inc-exl-04.png)
15. Clique em **Selecionar** para concluir a sua seleção de grupos.
16. Clique em **OK** no painel **Adicionar grupo**. É apresentada a lista de **Atribuições** de aplicações.
17. Clique em **Guardar** para aplicar as suas atribuições de grupo à aplicação.

Ao criar atribuições de grupo, os grupos que já foram atribuídos ou selecionados são desativados. Se quiser selecionar um grupo que está atualmente desativado, remova-o da lista de atribuições da aplicação. Pode editar atribuições a partir da lista de **Atribuições** de aplicações ao selecionar a linha que contém a atribuição específica que pretende alterar. Além disso, pode remover uma atribuição ao clicar nas reticências (...) no final da linha e ao selecionar **Remover**. Pode alterar a vista da lista de **atribuições** ao optar por agrupar por **Tipo de atribuição** ou por **Incluído/Excluído**.

![Atribuições de aplicações do Intune – concluir](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre como incluir e excluir atribuições de grupo para aplicações, veja o [Blogue do Microsoft Intune](https://aka.ms/new_app_assignment_process).
- [Como monitorizar informações e atribuições da aplicação](apps-monitor.md)