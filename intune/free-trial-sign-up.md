---
title: "Inscrever-se para uma avaliação gratuita de 30 dias do Microsoft Intune"
titleSuffix: Azure portal
description: "Como inscrever-se numa avaliação gratuita de 30 dias do Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 3b4d6528acd42a84c7d87968874d36199b661a90
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune


Este artigo explica-lhe como se inscrever numa versão de avaliação do Intune autónomo para o portal do Azure.

1. Visite a página [Inscrição no Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) e preencha o formulário para se inscrever para uma subscrição de avaliação.
* Se tiver uma conta profissional ou escolar e pretende utilizá-la para a sua versão de avaliação do Intune, siga antes [estas instruções de início de sessão](/intune/account-sign-up).

* Se a maioria das suas operações de TI e dos seus utilizadores estiverem numa região diferente da sua, pode querer selecionar essa região em **Onde está situada a sua empresa?**.

2. No final do processo de inscrição, recebe uma mensagem com as informações da sua conta nova. <br/> ![Imagem das informações da conta](./media/2-end-of-sign-up-process.png) <br/>Nesta fase, se clicar em **Está pronto para começar**, é direcionado para o Centro de Administração do Office 365, onde pode adicionar utilizadores ao seu ambiente de teste. <br/><br/>No entanto, se desejar ir diretamente para o Intune no portal do Azure, abra uma nova janela do browser e introduza **https://portal.azure.com** na barra de endereço. É direcionado para a página de início de sessão do Azure, onde poderá utilizar as credenciais que lhe foram dadas para iniciar sessão. Utilize este endereço sempre que quiser iniciar sessão na versão de avaliação do Intune. <br/> ![Imagem da página de início de sessão do portal do Azure](./media/azure-portal-signin.png)

Na primeira vez que iniciar sessão no Intune no portal do Azure, poderá não ver o Intune no dashboard do Azure. Para adicionar o serviço do Intune ao seu dashboard do Azure:
1. Selecione **Mais serviços >** na lista de serviços do Azure que se encontra à esquerda do dashboard e introduza a palavra **Intune** na caixa de pesquisa.
2. Selecione **Intune** na lista e, em seguida, selecione a estrela para adicionar o serviço à lista de serviços.<br/> ![Imagem a apresentar a seleção do Intune a partir da lista de serviços](./media/azure-add-intune1.png)
3. Em seguida, selecione **Intune** na lista de serviços para abrir o dashboard do Intune.

Quando se inscreve para uma versão avaliação, também receberá uma mensagem de e-mail com as informações da sua conta para o endereço de e-mail que indicou durante o processo de inscrição. Este e-mail confirma que a sua versão de avaliação está ativa.



## <a name="keeping-the-admin-experiences-straight"></a>Distinguir as experiências do administrador


Existem três portais que pode utilizar para o Intune no portal do Azure:
- O dashboard do Intune no Azure ([portal.azure.com](https://portal.azure.com)), onde poderá explorar as [funcionalidades do Intune no portal do Azure](what-is-intune.md).
- O Centro de administração do Office 365 ([portal.office.com](https://portal.office.com)), onde poderá adicionar e gerir utilizadores se não estiver a utilizar o Azure Active Directory para o fazer. Também pode gerir outros aspetos da sua conta, incluindo faturação e suporte.
- A consola de administração do Intune ([manage.microsoft.com](https://manage.microsoft.com)), onde poderá explorar as funcionalidades que ainda não foram adicionadas ao Azure.

Normalmente, irá realizar o seu trabalho no dashboard do Intune, conforme mostrado abaixo. Este é o site onde configura e gere os grupos, as políticas, os dispositivos e as aplicações.

Pode aceder à consola de administração do Intune a partir do dashboard. Para tal, escolha **Portal clássico** na parte superior do dashboard.

Para voltar para o Intune no portal do Azure, introduza https://portal.azure.com na barra de endereço do browser e, em seguida, selecione novamente **Intune** na lista de serviços.

 ![Imagem do dashboard do Intune](./media/intune-azure-dashboard.png)


Pode utilizar o Centro de Administração do Office 365, conforme mostrado abaixo, para adicionar e gerir os seus utilizadores e outros aspetos da sua conta, incluindo a faturação e o suporte.

![Imagem do Centro de administração do Office 365](./media/office-admin-center.png)

Para aceder ao dashboard do Intune a partir do centro de administração do Office 365, introduza https://portal.azure.com na barra de endereço do seu browser. Selecione **Intune** na lista de serviços.

Para voltar para o centro de administração do Office 365 a partir do Intune, introduza https://portal.office.com na barra de endereço do seu browser. Se já iniciou sessão no Intune, será diretamente reencaminhado para o centro de administração do Office 365.

## <a name="next-steps"></a>Próximos passos

### <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure
Saiba mais sobre o [Intune no portal do Azure](what-is-intune.md)

### <a name="integration-with-other-products"></a>Integração com outros produtos
Saiba mais sobre a utilização das suas contas de utilizador do Azure Active Directory com o Intune:
- [Requisitos de identidade](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Requisitos da sincronização de diretórios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Requisitos de autenticação multifator](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Saiba mais sobre a utilização do [Intune com o System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
