---
title: Criar um grupo no Microsoft Intune
titleSuffix: ''
description: Organize os utilizadores em grupos para ser mais fácil gerir as políticas e aplicações a que podem aceder.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fcf6f3071e50304216a182a21dd542cace1b6390
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186465"
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>Criar um grupo para gerir o acesso aos seus utilizadores e dados

Os grupos são utilizados para gerir os utilizadores e controlar o acesso dos seus funcionários aos recursos da sua empresa. Estes recursos podem fazer parte do seu diretório ou podem ser externos, como as aplicações SaaS ou os sites do SharePoint.

O Microsoft Intune utiliza o Azure Active Directory (Azure AD) para gerir o acesso aos recursos da empresa. Este acesso é controlado através das funções contidas no diretório. Em seguida, o Intune faz a gestão deste acesso para dispositivos móveis, o que permite aos membros desse grupo acederem aos recursos.

## <a name="how-do-i-create-a-group"></a>Como posso criar um grupo?

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Após abrir o painel **Microsoft Intune**, selecione **Grupos**.
4. No painel **Utilizadores e grupos – Todos os grupos**, selecione o comando **Novo grupo**.
5. No painel **Grupo**, selecione um **Tipo de grupo**.
5. Adicione um **Nome** e **Descrição** para o grupo.
6. Defina o **Tipo de associação** como **Atribuído**. Não selecione a opção **Ativar funcionalidades do Office** para o grupo de teste.
7. Selecione os **Membros** do grupo.
7. Clique em **Criar**.

Se tiver criado um grupo com êxito, o mesmo deverá ser apresentado na lista de **Todos os grupos**. Se o grupo não aparecer na lista, experimente criar outro grupo.

## <a name="next-steps"></a>Passos Seguintes

[Introdução às políticas](get-started-policies.md) – crie políticas para impedir que os utilizadores realizem ações não autorizadas com os dispositivos.

## <a name="learn-more"></a>Saiba mais

* [Definir restrições de inscrição através de grupos no Intune](groups-add.md)
* [Gerir o acesso aos recursos da empresa através de grupos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
