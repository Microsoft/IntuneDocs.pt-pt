---
title: Início Rápido – criar um grupo para gerir utilizadores
titlesuffix: Microsoft Intune
description: Neste início rápido, utilizará o Microsoft Intune para criar um grupo com base em utilizadores já existentes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/11/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6f7d7ccb4c94300d00f02dcace5c3a089cd9f2a2
ms.sourcegitcommit: d54a12a836503f7e8b90346f16b7ad2d83b710dc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270576"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Início rápido: Criar um grupo para gerir utilizadores

Neste início rápido, utilizará o Intune para criar um grupo com base num utilizador existente. Os grupos são utilizados para gerir os utilizadores e controlar o acesso dos seus funcionários aos recursos da sua empresa. Estes recursos podem fazer parte da intranet da sua empresa ou podem ser recursos externos, tais como sites do SharePoint, aplicações SaaS ou aplicações Web.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

>[!NOTE]
>O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade.

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este início rápido, terá de [criar um utilizador](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão para o [portal do Intune](https://aka.ms/intuneportal) como um [Administrador Global ou um administrador de serviço do Intune](users-add.md#types-of-administrators). Se criou uma Subscrição de avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-a-group"></a>Criar um grupo

Irá criar um grupo que será utilizado mais tarde nesta série de início rápido.

1. Após abrir o painel **Microsoft Intune**, selecione **Grupos** > **Novo grupo**.
2. Na caixa pendente **Tipo de grupo**, selecione **Segurança**.
3. Defina o **Nome** para "Técnicos de Teste da Contoso" e adicione uma **Descrição** do grupo.
4. Defina o **Tipo de associação** para **Atribuído**. 
5. Clique em **Membros** e selecione um ou mais membros para o grupo na lista existente.

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Clique em **Selecionar** > **Criar**.

Assim que tiver criado o grupo com êxito, este será apresentado na lista **Todos os grupos**. 

## <a name="next-steps"></a>Passos Seguintes

Neste início rápido, utilizou o Intune para criar um grupo com base num utilizador existente. Para obter mais informações sobre como adicionar grupos ao Intune, veja [Adicionar grupos para organizar utilizadores e dispositivos](groups-add.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Configurar a inscrição automática para dispositivos Windows 10](quickstart-setup-auto-enrollment.md)
