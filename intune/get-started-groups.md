---
title: "Introdução aos grupos"
titleSuffix: Azure portal
description: "Organize os utilizadores em grupos para ser mais fácil gerir as políticas e aplicações a que podem aceder."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 964732be680273c62f341086ce23f0e40d981479
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2017
---
# <a name="get-started-with-groups"></a>Introdução aos grupos

Os grupos são utilizados para gerir os utilizadores e controlar o acesso dos seus funcionários aos recursos da sua empresa. Estes recursos podem fazer parte do seu diretório ou podem ser externos, como as aplicações SaaS ou os sites do SharePoint.

O Microsoft Intune utiliza o Azure Active Directory (Azure AD) para gerir o acesso aos recursos da empresa. Este acesso é controlado através das funções contidas no diretório. Em seguida, o Intune faz a gestão deste acesso para dispositivos móveis, o que permite aos membros desse grupo acederem aos recursos.

## <a name="how-do-i-create-a-group"></a>Como posso criar um grupo?

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Utilize a opção **Procurar recursos**, procure o **Intune**.
3. Após abrir o painel **Microsoft Intune**, selecione **Grupos**.
4. No painel **Utilizadores e grupos – Todos os grupos**, selecione o comando **Novo grupo**.
5. No painel **Grupo**, adicione um **Nome** e **Descrição** ao grupo.
6. Defina o **Tipo de associação** como **Atribuído**. Não selecione a opção **Ativar funcionalidades do Office** para o grupo de teste.
7. Clique em **Criar**.

Se tiver criado um grupo com êxito, o mesmo deverá ser apresentado na lista de **Todos os grupos**. Se o grupo não aparecer na lista, experimente criar outro grupo.

## <a name="next-steps"></a>Próximos passos

[Introdução às políticas](get-started-policies.md) – crie políticas para impedir que os utilizadores realizem ações não autorizadas com os dispositivos.

## <a name="learn-more"></a>Saiba mais

* [Definir restrições de inscrição através de grupos no Intune](groups-add.md)
* [Gerir o acesso aos recursos da empresa através de grupos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
