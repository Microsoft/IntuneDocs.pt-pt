---
title: Início Rápido – criar um grupo para gerir utilizadores
titlesuffix: Microsoft Intune
description: Neste início rápido, utilizará o Microsoft Intune para criar um grupo com base em utilizadores já existentes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581795"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Início Rápido: criar um grupo para gerir utilizadores

Neste início rápido, utilizará o Intune para criar um grupo com base num utilizador existente. Os grupos são utilizados para gerir os utilizadores e controlar o acesso dos seus funcionários aos recursos da sua empresa. Estes recursos podem fazer parte da intranet da sua empresa ou podem ser recursos externos, tais como sites do SharePoint, aplicações SaaS ou aplicações Web.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

>[!NOTE]
>O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade.

## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este início rápido, terá de [criar um utilizador](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Iniciar sessão no Intune

Inicie sessão no [Intune](https://aka.ms/intuneportal) enquanto Administrador Global ou Administrador de Serviços do Intune. O Intune encontra-se no portal do Azure. Para aceder ao Intune, selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.

## <a name="create-a-group"></a>Criar um grupo
1. Após abrir o painel **Microsoft Intune**, selecione **Grupos** > **Novo grupo**.
2. No painel **Grupo**, selecione **Tipo de grupo** > **Segurança**.
3. Defina o **Nome** para "Técnicos de Teste da Contoso" e adicione uma **Descrição** do grupo.
4. Defina o **Tipo de associação** como **Atribuído**. 
5. Clique em **Membros** e selecione **Membros** para o grupo da lista existente.

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Clique em **Selecionar**.
7. Clique em **Criar**.

Se tiver criado o grupo com êxito, este será apresentado na lista **Todos os grupos**. 

## <a name="next-steps"></a>Próximos passos

Neste início rápido, utilizou o Intune para criar um grupo com base num utilizador existente.

> [!div class="nextstepaction"]
> [Criar uma política de conformidade de dispositivo](quickstart-create-policy.md)
