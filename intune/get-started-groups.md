---
title: "Introdução aos grupos"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>Introdução aos grupos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

O Microsoft Intune utiliza o Azure Active Directory (Azure AD) para [gerir o acesso aos recursos empresariais](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups). Este acesso é controlado através das funções contidas no diretório. Em seguida, o Intune faz a gestão deste acesso para dispositivos móveis, o que permite aos membros desse grupo acederem aos recursos.

__Como posso criar um grupo?__

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Através da opção **Procurar recursos**, procure **Utilizadores e grupos**.
3. Assim que tiver aberto o painel **Utilizadores e grupos**, selecione **Todos os grupos**.
4. No painel **Utilizadores e grupos – Todos os grupos**, selecione o comando **Novo grupo**.
5. No painel **Grupo**, adicione um **Nome** e **Descrição** ao grupo.
6. Defina o **Tipo de associação** como **Atribuído**. Não selecione a opção **Ativar funcionalidades do Office** para o grupo de teste.
7. Clique em **Criar**.

Se tiver criado um grupo com êxito, o mesmo deverá ser apresentado na lista de **Todos os grupos**. Se o grupo não aparecer na lista, experimente criar outro grupo.
