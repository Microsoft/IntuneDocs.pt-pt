---
ms.openlocfilehash: 6ec8f8a613d3b0a0b17f2615de634e70fa282fd7
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "68229262"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciais do Azure AD e do Intune

A autenticação e a autorização são baseadas nas credenciais do Azure AD e no controlo de acesso baseado em funções (RBAC) do Intune. Todos os administradores globais e administradores de serviço do Intune do seu inquilino têm acesso ao armazém de dados por predefinição. Utilize as funções do Intune para fornecer acesso a mais utilizadores ao dar-lhes acesso ao recurso **armazém de dados do Intune**.

Os requisitos de acesso ao Armazém de Dados do Intune (incluindo a API) são:

- O utilizador tem de ser um dos seguintes:
  - Administrador global do Azure AD
  - Um administrador de serviços do Intune
  - Utilizador com acesso baseado em funções ao recurso **armazém de dados do Intune**
  - Autenticação sem utilizador com [autenticação apenas com a aplicação](../data-warehouse-app-only-auth.md) 
