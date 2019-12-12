---
title: Início Rápido – criar um grupo para gerir utilizadores
titleSuffix: Microsoft Intune
description: Neste início rápido, utilizará o Microsoft Intune para criar um grupo com base em utilizadores já existentes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d73cc367e6c3308b34c2d2dd14c9fed94d80ba74
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813403"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Início Rápido: criar um grupo para gerir utilizadores

Neste início rápido, utilizará o Intune para criar um grupo com base num utilizador existente. Os grupos são utilizados para gerir os utilizadores e controlar o acesso dos seus funcionários aos recursos da sua empresa. Estes recursos podem fazer parte da intranet da sua empresa ou podem ser recursos externos, tais como sites do SharePoint, aplicações SaaS ou aplicações Web.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

>[!NOTE]
>O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade.

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este início rápido, terá de [criar um utilizador](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Entre no portal do [Intune](https://aka.ms/intuneportal) como um [administrador global ou um administrador de serviços do Intune](users-add.md#types-of-administrators). Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-a-group"></a>Criar um grupo

Irá criar um grupo que será utilizado mais tarde nesta série de início rápido. Para criar um grupo:

1. Após abrir o painel **Microsoft Intune**, selecione **Grupos** > **Novo grupo**.
2. Na caixa pendente **Tipo de grupo**, selecione **Segurança**.
3. No campo **nome do grupo** , insira o nome do novo grupo (por exemplo, **testadores contoso**).
4. Adicione uma **Descrição** para o grupo.
5. Defina o **Tipo de associação** para **Atribuído**. 
6. Clique em **Membros** e selecione um ou mais membros para o grupo na lista.

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. Clique em **Selecionar** > **Criar**.

Assim que tiver criado o grupo com êxito, este será apresentado na lista **Todos os grupos**. 

## <a name="next-steps"></a>Próximos passos

Neste início rápido, utilizou o Intune para criar um grupo com base num utilizador existente. Para obter mais informações sobre como adicionar grupos ao Intune, veja [Adicionar grupos para organizar utilizadores e dispositivos](../groups-add.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: configurar a inscrição automática para dispositivos com o Windows 10](../enrollment/quickstart-setup-auto-enrollment.md)
