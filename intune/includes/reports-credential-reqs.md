---
ms.openlocfilehash: 015e50d24149a6b6242eda86d5f3d62489e9955d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511346"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciais do Azure AD e do Intune

A autenticação e a autorização são baseadas nas credenciais do Azure AD e no controlo de acesso baseado em funções (RBAC) do Intune. Todos os administradores globais e administradores de serviço do Intune do seu inquilino têm acesso ao armazém de dados por predefinição. Utilize as funções do Intune para fornecer acesso a mais utilizadores ao dar-lhes acesso ao recurso **armazém de dados do Intune**.

Os requisitos de acesso ao Armazém de Dados do Intune (incluindo a API) são:

  -  O utilizador tem de ser um dos seguintes:
      -  Administrador global do Azure AD
      -  Um administrador de serviços do Intune
      -  Utilizador com acesso baseado em funções ao recurso **armazém de dados do Intune**
      -  Autenticação sem utilizador com [autenticação apenas com a aplicação](../data-warehouse-app-only-auth.md) 
