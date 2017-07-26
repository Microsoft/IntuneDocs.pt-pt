---
title: "Adicionar utilizadores e conceder permissões"
description: "Sincronizar utilizadores no local com o Azure AD e conceder permissões de administrador para a sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4289fdbdadbef34f06514b62722f84354534ae65
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2017
---
# <a name="add-users-and-give-administrative-permission-to-intune"></a>Adicionar utilizadores e conceder permissões administrativas no Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Este tópico informa os administradores sobre como podem adicionar utilizadores ao Intune e que permissões administrativas estão disponíveis no serviço do Intune.

Como administrador, pode adicionar utilizadores diretamente ou sincronizar utilizadores do Active Directory no local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Também pode conceder permissões adicionais aos utilizadores, incluindo permissões de *administrador global* e de *administrador de serviços*.

## <a name="add-users-to-intune"></a>Adicionar utilizadores ao Intune
Pode adicionar utilizadores à sua subscrição do Intune manualmente através do [portal do Office 365](https://www.office.com/signin) ou do [portal do Intune no Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Um administrador pode editar contas de utilizador para atribuir licenças do Intune. Pode atribuir licenças no portal do Office 365 ou no portal do Intune no Azure. Para obter mais informações sobre como utilizar o portal do Office 365, veja [Add users individually or in bulk to the Office 365 portal (Adicionar utilizadores individualmente ou em volume ao portal do Office 365)](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Adicionar utilizadores do Intune no Centro de Administração do Office 365
1. Inicie sessão no [portal do Office 365](https://www.office.com/signin).
2. No menu do Office 365, selecione **Administrador**.
3. No Centro de administração, selecione **Adicionar um utilizador**.

  ![Captura de ecrã do Centro de administração do Office 365](media/office-add-user.png)

4. Especifique os seguintes detalhes de utilizador:
  - **Nome próprio**
  - **Apelido**
  - **Nome a apresentar** – apresentado no portal do Intune
  - **Nome de utilizador** – nome UPN no portal do Intune
  - **Localização**
  - **Informações de contacto** (opcional)
  - **Palavra-passe** – pode gerar automaticamente ou especificar

     ![Captura de ecrã do Centro de administração do Office 365](media/office-add-user-details.png)

5. Atribua uma licença do Intune. Selecione **Licenças de produtos** e escolha a licença de produto.
6. Selecione **Adicionar** para criar um novo utilizador.

### <a name="add-intune-users-in-the-azure-intune-portal"></a>Adicionar utilizadores do Intune no portal do Intune no Azure
1. Inicie sessão no [portal do Azure](https://portal.azure.com). Aceda a **Monitorização + Gestão** > **Intune**. Também pode *procurar recursos* para o **Intune**.
2. Selecione **Utilizadores**.
3. No Centro de administração, selecione **Adicionar um utilizador**.
  ![Captura de ecrã do Centro de administração do Office 365](media/intune-add-user.png)
4. Especifique os seguintes detalhes de utilizador:
  - **Nome**
  - **Nome de utilizador** – o novo nome no portal do Azure Active Directory ![Captura de ecrã do Centro de administração do Office 365](media/intune-add-user-info.png) Selecione **OK** para continuar.
5. Opcionalmente, pode especificar as seguintes propriedades de utilizador:
  - **Perfil** – informações de trabalho, incluindo o **Cargo** e o **Departamento**
  -  **Grupos** – selecione grupos para o utilizador
  - **Função de diretório** – conceda ao utilizador permissões administrativas para o Intune

  Selecione **Criar** para adicionar o novo utilizador ao Intune.
6. Selecione **Perfil** e, em seguida, selecione uma **Localização de utilização** para o novo utilizador. É necessário indicar a localização de utilização antes de poder atribuir uma licença do Intune ao novo utilizador. Selecione **Guardar** para continuar.
    ![Captura de ecrã do Centro de administração do Office 365](media/intune-add-user-loc.png)
7. Selecione **Licenças** e, em seguida, selecione **Atribuir** para atribuir uma licença do Intune a este utilizador. É necessária uma licença do Intune para inscrever dispositivos ou aceder aos recursos da empresa. Selecione **Produtos**, escolha o tipo de licença, selecione **Selecionar** e, em seguida, selecione **Atribuir**.

## <a name="grant-admin-permissions"></a>Conceder permissões de administrador

Depois de adicionar utilizadores à sua subscrição do Intune, recomendamos que conceda permissões administrativas a alguns utilizadores:
-   [Administrador global](#tenant-administrator): utilize o portal do Office 365 para atribuir este tipo de administrador. O administrador global pode gerir a sua subscrição, incluindo a faturação, o armazenamento na cloud e a gestão dos utilizadores que podem utilizar o Intune.
-   [Administrador limitado ou personalizado](#service-administrator): utilize o Office 365 ou a consola do Intune no Azure para atribuir este tipo de administrador a tarefas quotidianas, incluindo gestão de dispositivos móveis e de computadores, implementação de políticas e de aplicações e execução de relatórios.

![Imagem da atribuição de Funções no portal do Office 365.](./media/office-assign-roles.png)

### <a name="types-of-administrators"></a>Tipos de administradores

Atribua uma ou mais permissões de administrador aos utilizadores. Estas permissões definem o âmbito administrativo dos utilizadores e as tarefas que estes podem gerir. As permissões de administrador são comuns entre os diferentes serviços cloud da Microsoft, embora alguns serviços possam não suportar determinadas permissões. O Intune utiliza as seguintes permissões de administrador:

- **Administrador global** (Office 365 e Intune) – acede a todas as funcionalidades administrativas no Intune. Por predefinição, a pessoa que se inscreve no Intune torna-se um Administrador global. Os administradores globais são os únicos que podem atribuir outras funções de administrador. Pode ter mais do que um administrador global na sua organização. Como melhor prática, recomendamos que apenas algumas pessoas na sua empresa tenham esta função para reduzir os riscos para o seu negócio.
- **Administrador de faturação** (Office 365 e Intune) – efetua compras, faz a gestão de subscrições e pedidos de suporte e monitoriza o estado de funcionamento do serviço.
- **Administrador de palavras-passe** (Office 365 e Intune) – repõe palavras-passe, faz a gestão de pedidos de serviço e monitoriza o estado de funcionamento do serviço. Os administradores de palavras-passe estão limitados à reposição de palavras-passe para os utilizadores.
- **Administrador de serviços** (Office 365) – abre pedidos de suporte com a Microsoft e vê o dashboard do serviço e o centro de mensagens. Tem permissões de "visualizar apenas" exceto para a abertura e leitura de pedidos de suporte.
- **Administrador da gestão de utilizadores** (Office 365 e Intune) – repõe palavras-passe, monitoriza o estado de funcionamento do serviço, adiciona e elimina contas de utilizador e faz a gestão de pedidos de serviço. O administrador da gestão de utilizadores não pode eliminar um administrador global, criar outras funções de administrador ou repor palavras-passe para outros administradores.

Por predefinição, a conta que utiliza para criar a sua subscrição do Microsoft Intune é de um administrador global. Como melhor prática, não utilize um administrador global para tarefas de gestão diárias. Um administrador não precisa de uma licença para o Intune para aceder à consola do administrador do Intune. Veja a secção de inquilino do Azure AD em [O que é um diretório do Azure AD?](http://technet.microsoft.com/library/jj573650.aspx) para obter mais informações.

Para aceder ao portal do Office 365, a sua conta tem de ter a opção **Início de sessão permitido** definida. No portal do Intune, em **Perfil**, defina **Bloquear o início de sessão** para **Não** para permitir o acesso. Este estado é diferente de ter uma licença para a subscrição. Por predefinição, todas as contas de utilizador têm o estado **Permitido**. Os utilizadores sem permissões de administrador podem utilizar o portal do Office 365 para repor palavras-passe do Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar o Active Directory e adicionar utilizadores ao Intune
Pode configurar a sincronização de diretórios para importar contas de utilizador do Active Directory no local para o Microsoft Azure Active Directory (Azure AD) que inclui utilizadores do Intune. Ligar o serviço do Active Directory no local a todos os serviços baseados no Azure Active Directory simplifica bastante a gestão da identidade de utilizadores. Também pode configurar funcionalidades de início de sessão único para tornar a experiência de autenticação dos utilizadores familiar e fácil. Ao ligar o mesmo [inquilino do Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) com múltiplos serviços, as contas de utilizador que anteriormente foram sincronizados estão disponíveis para todos os serviços baseados na cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Como sincronizar os utilizadores no local com o Azure AD
A única ferramenta de que precisa para sincronizar as contas de utilizador com o Azure AD é o [Assistente do Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). O Assistente do Azure AD Connect proporciona uma experiência orientada e simplificada para ligar a sua infraestrutura de identidade no local à cloud.  Escolha a sua topologia e as suas necessidades (apenas um ou múltiplos diretórios, sincronização de palavras-passe ou federação). O assistente implementa e configura todos os componentes necessários para que a sua ligação funcione corretamente. incluindo serviços de sincronização, Serviços de Federação do Active Directory (AD FS) e o módulo Azure AD PowerShell.

> [!TIP]
> O Azure AD Connect engloba capacidades que foram anteriormente lançadas como Dirsync e Azure AD Sync. Saiba mais sobre a [integração de diretórios](http://technet.microsoft.com/library/jj573653.aspx). Para saber mais sobre a sincronização de contas de utilizador de um diretório local com o Azure AD, veja [Similarities between Active Directory and Azure AD (Semelhanças entre o Active Directory e o Azure AD)](http://technet.microsoft.com/library/dn518177.aspx).