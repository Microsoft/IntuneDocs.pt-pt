---
# required metadata

title: Contas administrativas, sites e permissões no Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Contas administrativas, sites e permissões no Microsoft Intune

Antes de configurar o Microsoft Intune, reveja este tópico e outros requisitos listados em [O que deve saber antes de iniciar o Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)

Para administrar o Intune, irá utilizar:
- Dois tipos de contas de administrador
- Contas de utilizador com permissões adicionais
- Duas consolas/portais de administração baseadas na Web para conceder aos seus administradores acesso ao conteúdo que devem gerir.

As seguintes secções explicam estas contas e portais.

## Contas de administrador e de utilizador com permissões especiais

Seguem-se as contas e as permissões que irá utilizar para o Intune.

### Administrador inquilino
|Níveis de permissão|Mais informações|
|--------------------------|-------------------------|
|Aos administradores inquilinos é atribuída uma função de administrador que define o âmbito de administração desse utilizador e as tarefas que o mesmo pode gerir.<br /><br />As funções de administrador são comuns entre os diferentes serviços em nuvem da Microsoft, embora alguns serviços não suportem determinadas funções.<br /><br /> O Microsoft Intune utiliza as seguintes funções:<br /><br />- Administrador global<br />- Administrador de faturação<br />- Administrador de palavras-passe<br />- Administrador de suporte de serviços<br />- Administrador de gestão de utilizadores|Por predefinição, a conta que utilizar para criar a sua subscrição do Microsoft Intune será um administrador inquilino com a função de administrador global.<br /></br>  Enquanto administrador inquilinos, utiliza o [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] para gerir a sua subscrição do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e atribuir administradores inquilino a partir do<br /><br />Utilize um administrador inquilino com função de administrador global para aceder à [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] e designar o seu primeiro administrador de serviços. Como melhor prática, não utilize um administrador inquilino em tarefas de gestão diárias. Um administrador inquilino não necessita de uma licença do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para aceder ao<br /><br />O administrador inquilino é um conceito comum nos serviços em nuvem da Microsoft. Quando subscreve o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], o seu serviço é um inquilino do Microsoft Azure AD. Consulte a secção de inquilino do Azure AD [O que é um diretório do Azure AD?](http://technet.microsoft.com/library/jj573650.aspx)|


### Administrador de serviços
|Níveis de permissão|Mais informações|
|--------------------------|-------------------------|
|Aos administradores de serviços é atribuída uma das seguintes permissões:<br /><br />**Acesso total**: concede acesso a todas as áreas da [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], sem restrições. Também pode adicionar e gerir outros administradores de serviços.<br /><br />**Acesso só de leitura**: concede permissão de leitura a todas as áreas da [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. Um administrador de serviços só de leitura não pode modificar dados, mas pode executar relatórios.<br /><br />**Suporte técnico - Nó de Grupos**: concede permissões que permitem ao administrador do serviço executar apenas um conjunto de tarefas normalmente associadas a cenários de suporte técnico. Para obter informações sobre este conjunto de permissões, consulte [Personalizar as vistas de consola do Intune de acordo com as funções de administrador](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)|Por predefinição, o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] não designa um administrador de serviços. Em vez disso, tem de utilizar um administrador inquilino com a função de administrador global para designar o primeiro administrador de serviços da sua subscrição. </br></br> Enquanto administrador de serviços, utiliza a [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] para gerir as tarefas diárias do<br /><br />Pode designar administradores de serviços a partir da consola do administrador. Um administrador de serviços necessita de uma licença do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para que a conta possa aceder à consola de administração.|



### Gestores de inscrição de dispositivos
|Níveis de permissão|Mais informações|
|--------------------------|-------------------------|
|Os gestores de inscrição de dispositivos são contas de utilizador padrão com uma permissão adicional para inscrever mais do que cinco dispositivos.|Por predefinição, cada utilizador do [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] pode inscrever até cinco dispositivos. No entanto, pode conceder a permissão de gestor de inscrição de dispositivos a uma conta de utilizador e, em seguida, utilizar essa conta para inscrever grandes grupos de dispositivos pertencentes à empresa. Esta funcionalidade é útil se os dispositivos forem atribuídos aos utilizadores de forma temporária ou se forem utilizados no modo de local público, em que não é necessária a associação dos utilizadores aos dispositivos.|


## Sites administrativos para o Intune
 As diferentes tarefas administrativas exigem que utilize um dos seguintes sites administrativos, ao qual pode aceder através de um [browser suportado](supported-web-browsers.md)

- [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Consola do administrador do Microsoft Intune](https://admin.manage.microsoft.com/)

### [Portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Enquanto administrador inquilino, utilize este portal para gerir a sua subscrição**, incluindo as seguintes tarefas, se a sua função de administrador o permitir:

- Gerir as contas de utilizador da subscrição e configurar a sincronização de diretórios a partir do seu Active Directory no local.
- Gerir grupos de utilizadores denominados grupos de segurança.
- Atribuir licenças aos utilizadores para utilizar o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Configurar o nome de domínio que utiliza com a sua subscrição. O nome de domínio define a conta com a qual os utilizadores iniciam sessão.
- Gerir os detalhes de compra e faturação da sua subscrição, incluindo o número de licenças que possui ou a quantidade de espaço de armazenamento em nuvem que pode utilizar.
- Localizar ligações para ver o estado de funcionamento do serviço do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Enquanto administrador inquilino, pode iniciar sessão no portal do Office 365 para gerir a subscrição, mesmo que a sua conta não tenha nenhuma licença atribuída para utilizar
- Qualquer utilizador que tenha uma licença do Intune, mas que não seja administrador, pode utilizar este portal para repor a palavra-passe da conta e editar o respetivo perfil.
- Para aceder ao portal do Office 365, a sua conta tem de ter o estado de início de sessão definido como **Permitido**. Este estado é diferente de ter uma licença para a subscrição. Por predefinição, todas as contas de utilizador têm o estado **Permitido**


### [Consola do administrador do Microsoft Intune](https://admin.manage.microsoft.com/)

**Enquanto administrador de serviços, utilize este portal para gerir operações diárias,** incluindo:

- Definir políticas para computadores e dispositivos móveis.
- Carregar e implementar software, tal como atualizações de software e aplicações.
- Gerir o Endpoint Protection do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] nos computadores.
- Ver o estado dos dispositivos e executar relatórios.
- Inicie sessão neste portal. Tem de ter permissões de administrador de serviços ou ser um administrador inquilino com a função de administrador global para iniciar sessão neste portal.


Apenas os utilizadores com permissões de administrador de serviços ou administradores inquilinos com a função de administrador global podem iniciar sessão neste portal. Para aceder à consola de administração, a sua conta tem de ter uma licença para utilizar o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e o estado de início de sessão definido como **Permitido**

Saiba mais sobre como [adicionar utilizadores para a sua subscrição](start-with-a-paid-subscription-to-microsoft-intune-step-3.md) e [atribuir licenças para a sua subscrição](start-with-a-paid-subscription-to-microsoft-intune-step-4.md)

 ### Consulte também
 [What to know before you start Microsoft Intune (O que deve saber antes de iniciar o Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->

