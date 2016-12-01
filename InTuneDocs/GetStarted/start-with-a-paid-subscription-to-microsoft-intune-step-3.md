---
title: Sincronizar o Active Directory e adicionar utilizadores ao Intune | Microsoft Intune
description: "Sincronizar utilizadores no local com o Azure AD e conceder permissões de administrador para a sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar o Active Directory e adicionar utilizadores ao Intune
Pode configurar a sincronização de diretórios para importar contas de utilizador do Active Directory no local para o Microsoft Azure Active Directory (Azure AD). Ligar o serviço do Active Directory no local a todos os serviços baseados no Azure Active Directory simplifica bastante a gestão da identidade de utilizadores. Também pode configurar funcionalidades de início de sessão único para tornar a experiência de autenticação dos utilizadores familiar e fácil.

Para tornar as coisas ainda mais fáceis, se utilizar vários serviços com o mesmo [inquilino do Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/), as contas de utilizador que tiver sincronizado anteriormente estão disponíveis em todos os serviços baseados na nuvem que partilhem a mesma subscrição do inquilino do Azure AD.

## <a name="synchronize-on-premises-users-with-azure-ad"></a>Sincronizar os utilizadores no local com o Azure AD
A única ferramenta de que precisa para sincronizar as contas de utilizador com o Azure AD é o [Assistente do Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). O Assistente do Azure AD Connect proporciona uma experiência orientada e simplificada para ligar a sua infraestrutura de identidade no local à nuvem.  Escolha a sua topologia e as suas necessidades (um ou vários diretórios, sincronização de palavras-passe ou federação) e o assistente implementará e configurará todos os componentes necessários para ter a sua ligação pronta, incluindo serviços de sincronização, Serviços de Federação do Active Directory (AD FS) e o módulo Azure AD PowerShell.

> [!TIP]
> O Azure AD Connect engloba capacidades que foram anteriormente lançadas como Dirsync e Azure AD Sync. Saiba mais sobre a [integração de diretórios](http://technet.microsoft.com/library/jj573653.aspx). Para saber quais são as vantagens de sincronizar as contas de utilizador do diretório no local com o Azure AD, veja [Semelhanças entre o Active Directory e o Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-administrator-permissions"></a>Conceder permissões de administrador

Para administrar o Intune, irá utilizar:
- Dois tipos de contas de administrador
- Contas de utilizador com permissões adicionais
- Duas consolas/portais de administração baseadas na Web para conceder aos seus administradores acesso ao conteúdo que devem gerir.

Depois de acrescentar utilizadores à sua subscrição do Intune, recomendamos que conceda credenciais administrativas a algumas contas de utilizador. A consola utilizada para atribuir credenciais administrativas depende do tipo de administrador que pretende atribuir:

-   **Administrador inquilino**: utilize o **portal de contas do Microsoft Intune** para atribuir este tipo de administrador para gerir a sua subscrição, incluindo faturação, armazenamento na cloud e gestão dos utilizadores que podem utilizar o Intune.

-   **Administrador do serviço**: utilize a **Consola do administrador do Microsoft Intune** para atribuir este tipo de administrador a tarefas quotidianas, incluindo gestão de dispositivos móveis ou de computadores, implementação de políticas ou de software e execução de relatórios.

As seguintes secções explicam estas contas e portais.

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>Contas de administrador e de utilizador com permissões especiais

Seguem-se as contas e as permissões que irá utilizar para o Intune.

### <a name="tenant-administrator"></a>Administrador inquilino
|Níveis de permissão|Mais informações|
|--------------------------|-------------------------|
|Aos administradores inquilinos é atribuída uma função de administrador que define o âmbito de administração desse utilizador e as tarefas que o mesmo pode gerir.<br /><br />As funções de administrador são comuns entre os diferentes serviços em nuvem da Microsoft, embora alguns serviços não suportem determinadas funções.<br /><br /> O Microsoft Intune utiliza as seguintes funções:<br /><br />– Administrador global<br />– Administrador de faturação<br />– Administrador de palavras-passe<br />– Administrador de suporte de serviços<br />– Administrador de gestão de utilizadores|Por predefinição, a conta que utilizar para criar a sua subscrição do Microsoft Intune será um administrador inquilino com a função de administrador global.<br /></br>  Enquanto administrador inquilino, utiliza o [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] para gerir a sua subscrição do Intune e atribuir administradores inquilinos a partir do [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Utilize um administrador inquilino com função de administrador global para aceder à [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] e designar o seu primeiro administrador de serviços. Como melhor prática, não utilize um administrador inquilino em tarefas de gestão diárias. Um administrador inquilino não precisa de uma licença do Intune para aceder ao [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />O administrador inquilino é um conceito comum nos serviços em nuvem da Microsoft. Quando subscreve o Intune, o seu serviço é um inquilino do Microsoft Azure AD. Consulte a secção de inquilino do Azure AD em [O que é um diretório do Azure AD?](http://technet.microsoft.com/library/jj573650.aspx).|


### <a name="service-administrator"></a>Administrador de serviços
|Níveis de permissão|Mais informações|
|--------------------------|-------------------------|
|Aos administradores de serviços é atribuída uma das seguintes permissões:<br /><br />**Acesso total**: concede acesso a todas as áreas da [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], sem restrições. Também pode adicionar e gerir outros administradores de serviços.<br /><br />**Acesso só de leitura**: concede permissão de leitura a todas as áreas da [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. Um administrador de serviços só de leitura não pode modificar dados, mas pode executar relatórios.<br /><br />**Suporte técnico - Nó de Grupos**: concede permissões que permitem ao administrador do serviço executar apenas um conjunto de tarefas normalmente associadas a cenários de suporte técnico. Para obter mais informações sobre este conjunto de permissões, consulte [Personalizar as vistas de consola do Intune de acordo com as funções de administrador](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|Por predefinição, o Intune não designa um administrador de serviços. Em vez disso, tem de utilizar um administrador inquilino com a função de administrador global para designar o primeiro administrador de serviços da sua subscrição. </br></br> Enquanto administrador de serviços, utiliza a [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] para gerir as tarefas diárias do Intune.<br /><br />Pode designar administradores de serviços a partir da consola do administrador. Um administrador de serviços necessita de uma licença do Intune para que a conta possa aceder à consola de administração.|



### <a name="device-enrollment-managers"></a>Gestores de inscrição de dispositivos
|Níveis de permissão|Mais informações|
|--------------------------|-------------------------|
|Os gestores de inscrição de dispositivos são contas de utilizador padrão com uma permissão adicional para inscrever mais do que cinco dispositivos.|Por predefinição, cada utilizador do [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] pode inscrever até cinco dispositivos. No entanto, pode conceder a permissão de gestor de inscrição de dispositivos a uma conta de utilizador e, em seguida, utilizar essa conta para inscrever grandes grupos de dispositivos pertencentes à empresa. Esta funcionalidade é útil se os dispositivos forem atribuídos aos utilizadores de forma temporária ou se forem utilizados no modo de local público, em que não é necessária a associação dos utilizadores aos dispositivos.|




>[!div class="step-by-step"]

>[&larr; **Definições de domínio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Gerir licenças do Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->


