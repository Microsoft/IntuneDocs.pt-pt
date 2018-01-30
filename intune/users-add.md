---
title: "Adicionar utilizadores e conceder permissões"
description: "Sincronizar utilizadores no local com o Azure AD e conceder permissões de administrador para a sua subscrição do Intune"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 45e1b3747b4c1b74401fc1ce73716abe5e06110d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="add-users-and-give-administrative-permission-to-intune"></a>Adicionar utilizadores e conceder permissões administrativas no Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Este tópico informa os administradores sobre como podem adicionar utilizadores ao Intune e que permissões administrativas estão disponíveis no serviço do Intune.

Como administrador, pode adicionar utilizadores diretamente ou sincronizar utilizadores do Active Directory no local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Também pode conceder permissões adicionais aos utilizadores, incluindo permissões de *administrador global* e de *administrador de serviços*.

## <a name="add-users-to-intune"></a>Adicionar utilizadores ao Intune
Pode adicionar utilizadores à sua subscrição do Intune manualmente através do [portal do Office 365](https://www.office.com/signin) ou do [portal do Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Um administrador pode editar contas de utilizador para atribuir licenças do Intune. Pode atribuir licenças no portal do Office 365 ou no portal do Intune no Azure. Para obter mais informações sobre como utilizar o portal do Office 365, veja [Add users individually or in bulk to the Office 365 portal (Adicionar utilizadores individualmente ou em volume ao portal do Office 365)](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Adicionar utilizadores do Intune no Centro de Administração do Office 365
1. Inicie sessão no [portal do Office 365](https://www.office.com/signin) com uma conta de administrador de gestão de utilizadores ou conta de administrador global.
2. No menu do Office 365, selecione **Administrador**.
3. No Centro de administração, selecione **Adicionar um utilizador**.

  ![Captura de ecrã do Centro de administração do Office 365](media/office-add-user.png)

4. Especifique os seguintes detalhes de utilizador:
  - **Nome próprio**
  - **Apelido**
  - **Nome a apresentar**
  - **Nome de utilizador** – nome principal de utilizador (UPN) armazenado no Azure Active Directory utilizado para aceder ao serviço
  - **Localização**
  - **Informações de contacto** (opcional)
  - **Palavra-passe** – pode gerar automaticamente ou especificar

     ![Captura de ecrã do Centro de administração do Office 365](media/office-add-user-details.png)

5. Atribua uma licença do Intune. Selecione **Licenças de produtos** e escolha a licença de produto. É necessária uma licença que inclua o Intune.
6. Selecione **Adicionar** para criar um novo utilizador.

### <a name="add-intune-users-in-the-azure-portal"></a>Adicionar utilizadores do Intune no portal do Azure
1. Inicie sessão no [portal do Azure](https://portal.azure.com) e aceda a **Mais serviços** > **Monitorização + Gestão** > **Intune**. Também pode *procurar recursos* para o **Intune**.
2. Selecione **Utilizadores**.
3. No Centro de administração, selecione **Novo utilizador**.
  ![Captura de ecrã do Centro de Administração do Office 365](media/intune-add-user.png)
4. Especifique os seguintes detalhes de utilizador:
  - **Nome**
  - **Nome de utilizador** – o novo nome no portal do Azure Active Directory ![Captura de ecrã do Centro de administração do Office 365](media/intune-add-user-info.png) Selecione **OK** para continuar.
5. Opcionalmente, pode especificar as seguintes propriedades de utilizador:
  - **Perfil** – informações de trabalho, incluindo o **Cargo** e o **Departamento**
  -  **Grupos** – selecione grupos para o utilizador
  - **Função de diretório** – conceda ao utilizador permissões administrativas, incluindo uma função de administrador de serviço do Intune.

  Selecione **Criar** para adicionar o novo utilizador ao Intune.
6. Selecione **Perfil** e, em seguida, selecione uma **Localização de utilização** para o novo utilizador. É necessário indicar a localização de utilização antes de poder atribuir uma licença do Intune ao novo utilizador. Selecione **Guardar** para continuar.
    ![Captura de ecrã do Centro de Administração do Office 365](media/intune-add-user-loc.png)
7. Selecione **Licenças** e, em seguida, selecione **Atribuir** para atribuir uma licença do Intune a este utilizador. É necessária uma licença do Intune para inscrever dispositivos ou aceder aos recursos da empresa. Selecione **Produtos**, selecione o tipo de licença, selecione **Selecionar** e, em seguida, selecione **Atribuir**.

## <a name="grant-admin-permissions"></a>Conceder permissões de administrador

Depois de adicionar utilizadores à sua subscrição do Intune, recomendamos que conceda permissões administrativas a alguns utilizadores.  Para conceder permissões de administrador, siga estes passos:

### <a name="give-admin-permissions-in-office-365"></a>Conceder permissões de administrador no Office 365
1. Inicie sessão no [portal do Office 365](https://www.office.com/signin) com uma conta de administrador global.
2. No menu do Office 365, selecione **Administrador**.
3. No Centro de Administração, selecione **Utilizadores ativos** e, em seguida, selecione o utilizador ao qual pretende conceder permissões de administrador.
4. Na coluna **Funções**, selecione **Editar**.
  ![Captura de ecrã a mostrar o ecrã Atribuir funções no Office 365](./media/office-assign-roles-open.png)
5. Selecione a permissão de administrador que pretende conceder a partir da lista de funções disponíveis.
![Imagem da atribuição de Funções no portal do Office 365.](./media/office-assign-roles.png)
6. Escolha **Guardar**.

### <a name="give-admin-permissions-in-the-azure-portal"></a>Conceder permissões de administrador no portal do Azure
1. Inicie sessão no [portal do Azure](https://www.office.com/signin) com uma conta de administrador global.
2. No portal do Azure, escolha **Utilizador** e, em seguida, escolha o utilizador ao qual pretende conceder permissões de administrador.
3. Selecione **Função de diretório** e, em seguida, selecione a permissão.
  ![Captura de ecrã](./media/add-intune-directory-role.png)
4. Escolha **Guardar**.

### <a name="types-of-administrators"></a>Tipos de administradores

Atribua uma ou mais permissões de administrador aos utilizadores. Estas permissões definem o âmbito administrativo dos utilizadores e as tarefas que estes podem gerir. As permissões de administrador são comuns entre os diferentes serviços cloud da Microsoft, embora alguns serviços possam não suportar determinadas permissões. O portal do Azure e o portal do Office 365 apresentam funções de administrador limitadas que não são utilizadas pelo Intune. As permissões de administrador do Intune incluem as seguintes opções:

- **Administrador global** (Office 365 e Intune) – acede a todas as funcionalidades administrativas no Intune. Por predefinição, a pessoa que se inscreve no Intune torna-se um Administrador global. Os administradores globais são os únicos que podem atribuir outras funções de administrador. Pode ter mais do que um administrador global na sua organização. Como melhor prática, recomendamos que apenas algumas pessoas na sua empresa tenham esta função para reduzir os riscos para o seu negócio.
- **Administrador de palavras-passe** (Office 365 e Intune) – repõe palavras-passe, faz a gestão de pedidos de serviço e monitoriza o estado de funcionamento do serviço. Os administradores de palavras-passe estão limitados à reposição de palavras-passe para os utilizadores.
- **Administrador de serviços** (Office 365 e Intune) – abre pedidos de suporte com a Microsoft e vê o dashboard do serviço e o centro de mensagens. Tem permissões de "visualizar apenas" exceto para a abertura e leitura de pedidos de suporte.
- **Administrador de faturação** (Office 365 e Intune) – efetua compras, faz a gestão de subscrições e pedidos de suporte e monitoriza o estado de funcionamento do serviço.
- **Administrador de utilizadores** (Office 365 e Intune) – repõe palavras-passe, monitoriza o estado de funcionamento do serviço, adiciona e elimina contas de utilizador e faz a gestão de pedidos de serviço. O administrador da gestão de utilizadores não pode eliminar um administrador global, criar outras funções de administrador ou repor palavras-passe para outros administradores.
- **Administrador do Serviço Intune** – todas as permissões de Administrador Global do Intune, exceto a permissão para criar utilizadores com opções de **Função de Diretório**.

A conta que utilizar para criar a sua subscrição do Microsoft Intune é um administrador global. Como melhor prática, não utilize um administrador global para tarefas de gestão diárias. Um administrador não necessita de uma licença do Intune para aceder ao portal do Azure. 

Para aceder ao portal do Office 365, a sua conta tem de ter a opção **Início de sessão permitido** definida. No portal do Azure, em **Perfil**, defina **Bloquear início de sessão** como **Não** para permitir o acesso. Este estado é diferente de ter uma licença para a subscrição. Por predefinição, todas as contas de utilizador têm o estado **Permitido**. Os utilizadores sem permissões de administrador podem utilizar o portal do Office 365 para repor palavras-passe do Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar o Active Directory e adicionar utilizadores ao Intune
Pode configurar a sincronização de diretórios para importar contas de utilizador do Active Directory no local para o Microsoft Azure Active Directory (Azure AD) que inclui utilizadores do Intune. Ligar o serviço do Active Directory no local a todos os serviços baseados no Azure Active Directory simplifica bastante a gestão da identidade de utilizadores. Também pode configurar funcionalidades de início de sessão único para tornar a experiência de autenticação dos utilizadores familiar e fácil. Ao ligar o mesmo [inquilino do Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) com múltiplos serviços, as contas de utilizador que anteriormente foram sincronizados estão disponíveis para todos os serviços baseados na cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Como sincronizar os utilizadores no local com o Azure AD
A única ferramenta de que precisa para sincronizar as contas de utilizador com o Azure AD é o [Assistente do Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). O Assistente do Azure AD Connect proporciona uma experiência orientada e simplificada para ligar a sua infraestrutura de identidade no local à cloud.  Escolha a sua topologia e as suas necessidades (apenas um ou múltiplos diretórios, sincronização de palavras-passe ou federação). O assistente implementa e configura todos os componentes necessários para que a sua ligação funcione corretamente. incluindo serviços de sincronização, Serviços de Federação do Active Directory (AD FS) e o módulo Azure AD PowerShell.

> [!TIP]
> O Azure AD Connect engloba capacidades que foram anteriormente lançadas como Dirsync e Azure AD Sync. Saiba mais sobre a [integração de diretórios](http://technet.microsoft.com/library/jj573653.aspx). Para saber mais sobre a sincronização de contas de utilizador de um diretório local com o Azure AD, veja [Similarities between Active Directory and Azure AD (Semelhanças entre o Active Directory e o Azure AD)](http://technet.microsoft.com/library/dn518177.aspx).
