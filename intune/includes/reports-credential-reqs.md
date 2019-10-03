---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830516"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciais do Azure AD e do Intune

A autenticação e a autorização são baseadas nas credenciais do Azure AD e no controlo de acesso baseado em funções (RBAC) do Intune. Todos os administradores globais e administradores de serviço do Intune do seu inquilino têm acesso ao armazém de dados por predefinição. Utilize as funções do Intune para fornecer acesso a mais utilizadores ao dar-lhes acesso ao recurso **armazém de dados do Intune**.

Os requisitos de acesso ao Armazém de Dados do Intune (incluindo a API) são:

- O utilizador tem de ser um dos seguintes:
  - Administrador global do Azure AD
  - Um administrador de serviços do Intune
  - Utilizador com acesso baseado em funções ao recurso **armazém de dados do Intune**
  - Autenticação sem utilizador com [autenticação apenas com a aplicação](../developer/data-warehouse-app-only-auth.md) 
