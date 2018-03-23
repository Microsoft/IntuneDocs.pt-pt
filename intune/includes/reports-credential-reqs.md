<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciais do Azure AD e do Intune

A autenticação e a autorização são baseadas nas credenciais do Azure AD e no controlo de acesso baseado em funções (RBAC) do Intune. Todos os administradores globais e administradores de serviço do Intune do seu inquilino têm acesso ao armazém de dados por predefinição. Utilize as funções do Intune para fornecer acesso a mais utilizadores ao dar-lhes acesso ao recurso **armazém de dados do Intune**.

Os requisitos de acesso ao Armazém de Dados do Intune (incluindo a API) são:

  -  O utilizador tem de ser um dos seguintes:
      -  Administrador global do Azure AD
      -  Um administrador de serviços do Intune
      -  Utilizador com acesso baseado em funções ao recurso **armazém de dados do Intune**
      -  Autenticação sem utilizador com [autenticação apenas com a aplicação](../data-warehouse-app-only-auth.md) 
