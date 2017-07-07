---
title: "Inscrever-se para uma avaliação gratuita de 30 dias do Microsoft Intune"
description: "Inscrever-se e configurar uma avaliação gratuita de 30 dias do Microsoft Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ffa07d5e36abc8686cedd600123494180c286011
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este artigo explica os passos da inscrição para uma versão de avaliação do Intune e prepara a sua versão de avaliação com alguns utilizadores para que, em seguida, possa seguir o guia de avaliação associado para ver como o Intune gere dispositivos móveis. <!---or app data when devices are not enrolled in Intune.--->

>[!Note]
> A partir de dezembro de 2016, o Microsoft Intune será transferido para o portal do Azure, pelo que algumas inscrições de avaliação gratuita estarão no Intune no portal do Azure e algumas estarão no Intune clássico. Se a sua avaliação estiver no portal do Azure, o [conteúdo de pré-visualização do Intune no Azure](/intune/what-is-intune) ser-lhe-á mais útil depois de concluir os passos contidos neste artigo.

## <a name="assumptions"></a>Pressupostos
Este artigo de inscrição e o guia de avaliação assumem que está a utilizar a versão de avaliação apenas para o fim destinado e pretende começar com um ambiente limpo na altura da subscrição.

Para facilitar a introdução à utilização da versão de avaliação, estamos a configurar um ambiente muito simples que utiliza apenas o Intune e assume que este será o único método de gestão de dispositivos (conhecido como a autoridade de gestão de dispositivos móveis). No entanto, no decorrer do guia, iremos destacar conteúdo técnico mais aprofundado, se pretender explorar mais.

A versão de avaliação permite-lhe fazer tudo o que normalmente faria numa versão de subscrição, a única diferença é que a versão de avaliação está limitada a 100 contas de utilizador.

## <a name="sign-up-for-your-trial"></a>Inscrever-se para a versão de avaliação
Visite a página [Inscrição no Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) e preencha o formulário para se inscrever para uma subscrição de avaliação.

Se tiver uma conta profissional ou escolar e pretende utilizá-la para a sua versão de avaliação do Intune, siga antes [estas instruções de início de sessão](/intune/account-sign-up). Contudo, este artigo e os guias de avaliação assumem que não está a utilizar tal conta.

> [!TIP]
> Se a maioria das suas operações de TI e dos seus utilizadores estiverem numa região diferente da sua, pode querer definir essa mesma região para que a sua versão de avaliação possa testar o desempenho.

### <a name="post-sign-up-considerations"></a>Considerações de pós-inscrição
Quando se inscreve para uma versão avaliação, receberá uma mensagem de e-mail com as informações da sua conta para o endereço de e-mail que indicou durante o processo de inscrição. Este e-mail confirma que a sua versão de avaliação está ativa.

Depois de concluir o processo de inscrição, será direcionado para uma página utilizada para adicionar utilizadores e atribuir-lhes licenças com o Centro de administração do Office 365. Da próxima vez que iniciar sessão no **Intune clássico** (https://manage.microsoft.com), será redirecionado automaticamente para a consola de administração do Intune.

Se a sua avaliação estiver no **portal do Azure**, aceda a https://portal.azure.com e inicie sessão com as credenciais da sua avaliação do Intune.

## <a name="add-users"></a>Adicionar utilizadores
Antes de sair do Centro de administração do Office 365 para o Intune, precisa de adicionar alguns utilizadores à conta de avaliação.

No Centro de administração do Office 365, pode adicionar utilizadores individualmente ou em massa ao carregar um ficheiro .csv. Serão realizados ambos para configurar a sua versão de avaliação. No entanto, no ambiente de produção, é provável que pretenda tirar partido das suas contas de utilizador do Azure Active Directory, que pode saber mais no nosso [Guia de introdução](/intune/users-permissions-add) e na secção [Passos seguintes ](#next-steps) deste artigo.

### <a name="add-an-individual-user"></a>Adicionar um utilizador individual
1. Escolha uma das opções para adicionar um utilizador para abrir um formulário que lhe permite criar um utilizador. Apenas os itens que começam por um asterisco (\*) são precisos.
![Imagem de opções de botão de adicionar utilizador](./media/sign-up/add-user.png)


2.  Quando adiciona o utilizador, o passo final será o envio de um e-mail para esse utilizador com a palavra-passe temporária do Intune. Para efeitos desta avaliação, utilize o seu próprio endereço de e-mail profissional para receber as informações de início de sessão e ver o e-mail que os seus utilizadores receberão. Em seguida, pode utilizar estas identidades de utilizador para inscrever os dispositivos de teste.<br/>

 ![Imagem de adicionar o passo final do utilizador](./media/sign-up/new-user-2.png)

3. Se pretender atribuir uma função de administrador a um utilizador depois de o criar, pode editar a função no Centro de administração do Office 365 ao selecionar o nome de utilizador na lista de utilizadores e, em seguida, escolher **Editar** na linha Função para ver a lista de funções de utilizador que pode selecionar e atribuir a esse utilizador.

 ![Imagem das opções de função de utilizador](./media/sign-up/change-user-role.png)

### <a name="import-multiple-users"></a>Importar múltiplos utilizadores
1. Encontrará o assistente para importar vários utilizadores na lista **Mais**.

 ![Imagem da opção para adicionar vários utilizadores](./media/sign-up/add-multiple-users.png)

2. Para o ajudar a configurar corretamente o ficheiro. csv, pode transferir um ficheiro de modelo para preencher com os seus dados de utilizador. Transfira o ficheiro. csv com os cabeçalhos e as informações de utilizadores de exemplo para ver exatamente o tipo de dados necessários para cada campo.

 ![Imagem do primeiro passo no assistente de inscrição em volume](./media/sign-up/bulk-enroll-step-1.png)


3. Depois de ter criado e guardado o ficheiro. csv, escolha **Procurar** para selecionar o ficheiro. Verifique e escolha **Seguinte**. Os seus utilizadores serão carregados e adicionados à lista de utilizadores ativos.

> [!NOTE]
> Os utilizadores não aparecerão no Intune até que tenham inscrito um dispositivo a gerir.

Agora está na altura de seguir para o Intune para começar a gerir os utilizadores, bem como os respetivos dispositivos e aplicações.

## <a name="keeping-the-admin-experiences-straight"></a>Distinguir as experiências do administrador
### <a name="classic-intune"></a>Intune clássico
Há dois portais que utilizará para o Intune clássico:
- O centro de administração do Office 365 ([portal.office.com](https://portal.office.com))
- A consola de administração do Intune ([manage.microsoft.com](https://manage.microsoft.com))

Normalmente, irá realizar o seu trabalho na consola de administração do Intune, como se mostra abaixo. Este é o site onde configura e gere os grupos, as políticas, os dispositivos e as aplicações.

![Imagem da consola de administração do Intune](./media/sign-up/intune-admin-console.png)

No entanto, irá utilizar o Centro de administração do Office 365, conforme mostrado abaixo, para adicionar e gerir os seus utilizadores e outros aspetos da sua conta, incluindo a faturação e o suporte.

![Imagem do Centro de administração do Office 365](./media/sign-up/office-admin-center.png)

Pode navegar do Centro de administração do Office 365 para a consola de administração do Intune. Os centros de administração estão no último item no painel de navegação à esquerda. Escolha **Intune** para abrir a consola de administração do Intune num novo separador.

![Imagem da ligação para a consola de administração do Intune](./media/sign-up/link-to-intune.png)

Para passar do Intune para o Centro de administração do Office 365, escolha a tarefa **Adicionar Utilizadores** na página Descrição Geral dos Grupos.

![Imagem da ligação para o Centro de administração do Office 365](./media/sign-up/task-add-users.png)

### <a name="intune-on-azure"></a>Intune no Azure
Há três portais que utilizará para o Intune no Azure:
- O centro de administração do Office 365 ([portal.office.com](https://portal.office.com))
- O dashboard do Intune no Azure ([portal.azure.com](https://portal.azure.com))
- A consola de administração do Intune clássico ([manage.microsoft.com](https://manage.microsoft.com))

A primeira vez que iniciar sessão no Intune no Azure, poderá não o ver no seu dashboard do Azure. Para adicionar o serviço do Intune ao seu dashboard do Azure:
1. Selecione **Mais serviços >** na lista de serviços do Azure que se encontra à esquerda do dashboard e introduza a palavra "Intune" na caixa de pesquisa.
2. Selecione **Intune** na lista e, em seguida, selecione a estrela para adicionar o serviço à lista de serviços.<br/> ![Imagem a apresentar a seleção do Intune a partir da lista de serviços](./media/sign-up/azure-add-intune1.png)
3. Selecione **Intune** na lista de serviços para abrir o dashboard do Intune.

Normalmente, irá realizar o seu trabalho no dashboard do Intune, conforme mostrado abaixo. Este é o site onde configura e gere os grupos, as políticas, os dispositivos e as aplicações. Pode aceder à consola de administração do Intune clássico a partir do dashboard. Para tal, selecione o mosaico **Abrir o portal do Intune clássico**. Para voltar para a pré-visualização do Intune no Azure, introduza https://portal.azure.com na barra de endereço do seu browser e, em seguida, selecione novamente **Intune** a partir da lista de serviços.

 ![Imagem do dashboard do Intune](./media/sign-up/intune-azure-dashboard.png)


No entanto, irá utilizar o Centro de administração do Office 365, conforme mostrado abaixo, para adicionar e gerir os seus utilizadores e outros aspetos da sua conta, incluindo a faturação e o suporte.

![Imagem do Centro de administração do Office 365](./media/sign-up/office-admin-center.png)

Para aceder ao dashboard do Intune a partir do centro de administração do Office 365, introduza https://portal.azure.com na barra de endereço do seu browser. Selecione **Intune** na lista de serviços.

Para voltar para o centro de administração do Office 365 a partir do Intune, introduza https://portal.office.com na barra de endereço do seu browser. Se já iniciou sessão no Intune, será diretamente reencaminhado para o centro de administração do Office 365.

## <a name="next-steps"></a>Passos seguintes
### <a name="classic-intune"></a>Intune clássico
Cenário de avaliação: [Avaliar a gestão de dispositivos móveis no Microsoft Intune](mobile-device-management-trial-guide-microsoft-intune.md)

### <a name="intune-on-azure"></a>Intune no Azure
Saiba mais sobre o [Intune no Azure](/intune/what-is-intune)

### <a name="integration-with-other-products"></a>Integração com outros produtos
Saiba mais sobre a utilização das suas contas de utilizador do Azure Active Directory com o Intune:
- [Requisitos de identidade](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Requisitos da sincronização de diretórios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Requisitos de autenticação multifator](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Saiba mais sobre a utilização do [Intune com o System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
