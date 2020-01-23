---
title: Início Rápido – criar um grupo para gerir utilizadores
titleSuffix: Microsoft Intune
description: Neste início rápido, utilizará o Microsoft Intune para criar um grupo com base em utilizadores já existentes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
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
ms.openlocfilehash: d9b06043dd10f92b6176d4b2e9f90f1b7c87aac9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540962"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Início Rápido: criar um grupo para gerir utilizadores

Neste início rápido, utilizará o Intune para criar um grupo com base num utilizador existente. Os grupos são utilizados para gerir os utilizadores e controlar o acesso dos seus funcionários aos recursos da sua empresa. Estes recursos podem fazer parte da intranet da sua empresa ou podem ser recursos externos, tais como sites do SharePoint, aplicações SaaS ou aplicações Web.

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

>[!NOTE]
>O Intune fornece os grupos **Todos os Utilizadores** e **Todos os Dispositivos** pré-criados na consola com otimizações incorporadas para sua comodidade.

## <a name="prerequisites"></a>Pré-requisitos

- Subscrição do Microsoft Intune – [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).
- Para concluir este início rápido, terá de [criar um utilizador](quickstart-create-user.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Entrar no Intune no Microsoft Endpoint Manager

Entre no [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) como um [administrador global ou um administrador de serviços do Intune](users-add.md#types-of-administrators). Se criou uma Subscrição de Avaliação do Intune, a conta com a qual criou a subscrição é de Administrador global.

## <a name="create-a-group"></a>Criar um grupo

Irá criar um grupo que será utilizado mais tarde nesta série de início rápido. Para criar um grupo:

1. Depois de abrir o **Gerenciador de pontos de extremidade da Microsoft**, selecione **grupos** > **novo grupo**.
2. Na caixa pendente **Tipo de grupo**, selecione **Segurança**.
3. No campo **nome do grupo** , insira o nome do novo grupo (por exemplo, **testadores contoso**).
4. Adicione uma **Descrição de grupo** para o grupo.
5. Defina o **Tipo de associação** para **Atribuído**. 
6. Em **Membros**, selecione o link e adicione um ou mais membros para o grupo na lista.

    ![Captura de ecrã da criação de um grupo no Microsoft Intune](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. Clique em **Selecionar** > **Criar**.

Assim que tiver criado o grupo com êxito, este será apresentado na lista **Todos os grupos**. 

## <a name="next-steps"></a>Próximos passos

Neste início rápido, utilizou o Intune para criar um grupo com base num utilizador existente. Para obter mais informações sobre como adicionar grupos ao Intune, veja [Adicionar grupos para organizar utilizadores e dispositivos](../groups-add.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: configurar a inscrição automática para dispositivos com o Windows 10](../enrollment/quickstart-setup-auto-enrollment.md)
