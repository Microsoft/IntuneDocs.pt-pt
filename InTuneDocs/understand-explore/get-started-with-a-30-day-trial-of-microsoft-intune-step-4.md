﻿---
title: "Criar políticas e publicar uma aplicação para os utilizadores | Documentos da Microsoft"
description: "Como criar políticas e publicar uma aplicação quando se inscreve numa avaliação gratuita de 30 dias do Intune"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 21d1e624069117d905dc7aced33b70abeb0e1109
ms.lasthandoff: 04/14/2017


---


# <a name="create-policies-and-publish-an-app-to-evaluation-users"></a>Criar políticas e publicar uma aplicação para utilizadores de avaliação

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As políticas do Intune disponibilizam definições que o ajudam a controlar as definições de segurança nos dispositivos móveis, a gerir as definições de Endpoint Protection e Firewall do Windows de computadores e a implementar aplicações. Se estiver a planear utilizar o Intune para os dispositivos que configurou para utilização de produção após a avaliação, é absolutamente essencial que siga as instruções em [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) e [Ajudar a proteger os PC Windows com o Endpoint Protection para o Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Pode executar dois tipos de instalações de aplicações com o Intune. O primeiro é uma **instalação necessária**, que implementa automaticamente as aplicações nos dispositivos geridos. O segundo tipo é uma **instalação disponível**, que implementa as aplicações, ou ligações para as mesmas, no Portal da Empresa do Intune, para que os utilizadores possam optar por instalá-las nos computadores ou dispositivos móveis deles.

Antes de utilizar o Intune para implementar aplicações, confirme que tem as licenças adequadas para as publicar, distribuir e utilizar. A área de trabalho **Licenças** permite-lhe adicionar e gerir informações de contratos de licença de aplicações ou software comprados através de contratos de Licenciamento em Volume da Microsoft, bem como de aplicações ou software da Microsoft ou sem ser da Microsoft comprados por outros meios. Em seguida, pode criar relatórios de licenças, que apresentam informações de utilização das licenças geridas de toda a empresa, para se manter a par da atividade em torno da utilização das licenças.

Nestes passos, vai ser configurada uma política de configuração de dispositivos móveis e uma política de firewall de computador do Windows e ainda o Skype como instalação disponível para dispositivos móveis depois de serem inscritos Depois de adicionar e implementar uma política nova, todos os utilizadores ou grupos nos quais tiver implementado a política herdam as definições como a respetiva política de linha de base. Pode sempre rever e editar os detalhes destas políticas mais tarde, a partir da área de trabalho **Política** na consola de administração.

## <a name="create-and-deploy-a-mobile-device-configuration-policy"></a>Criar e implementar políticas de configuração de dispositivos móveis

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com/).

2.  No painel esquerdo, escolha o ícone **Política**.

3.  Na lista **Tarefas**, na página **Descrição Geral da Política**, escolha **Adicionar Política**.

4.  Na lista de políticas, expanda a plataforma para a qual quer criar uma política, selecione **Configuração Geral**, selecione **Criar e Implementar uma Política Personalizada** e, em seguida, selecione **Criar Política**.

5.  Quando lhe for solicitado para **Selecionar os grupos nos quais pretende implementar esta política**, selecione **Os Utilizadores da Minha Versão de Avaliação** na lista e escolha **Adicionar** &gt; **OK**.

A sua política é apresentada na lista de políticas de configuração e foi implementada no grupo **Os Utilizadores da Minha Versão de Avaliação** . Faça duplo clique na política para ver as respetivas definições.

## <a name="publish-the-skype-app-for-mobile-devices"></a>Publicar a aplicação Skype em dispositivos móveis

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione o ícone **Aplicações** e, em seguida, selecione **Aplicações** &gt; **Adicionar Aplicação**. Introduza as suas credenciais do Intune, caso pedido.

    > [!NOTE]
    > Quando inicia o **Intune Software Publisher** pela primeira vez, ocorre um pequeno atraso durante a instalação da aplicação.

2.  Leia o aviso de segurança e escolha **Executar**.

3.  Na página **Antes de começar**, escolha **Seguinte**.

4.  Na página **Configuração do software**, em **Selecione de que forma este software é disponibilizado nos dispositivos**, selecione **Ligação externa**.

5.  Introduza uma ligação externa para o software em **Especificar o URL** e, em seguida, escolha **Seguinte** Certifique-se de que precede o URL com **https://**. Para a aplicação Skype, utilize a ligação abaixo que corresponda à plataforma de dispositivos móveis que está a utilizar:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **No Windows Phone 8.1:** [http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Na página **Descrição do software**, indique as informações que pretende que os utilizadores vejam no Portal da Empresa relativamente ao software e, em seguida, escolha **Seguinte**. Estão disponíveis as seguintes definições (este exemplo é relativo ao Skype):

    -   **Publicador:** introduza o nome do publicador, **Microsoft**

    -   **Nome:** introduza **Skype**

    -   **Descrição:** introduza uma descrição para o software, como **aplicação de comunicação Skype**

    -   **Categoria:** selecione a categoria que melhor se adequa a este software, como **Colaboração**

    -   **Apresentar esta aplicação como uma aplicação em destaque e destacá-la no portal da empresa:** selecione esta opção para apresentar a aplicação de forma destacada no Portal da Empresa nos dispositivos móveis.

    -   **Ícone:**  (opcional) escolha se quer associar um ícone ao software. O tamanho de ícone máximo é 250 x 250 pixéis, mas o tamanho de ícone recomendado é 32 x 32 pixéis.

7.  Na página **Resumo**, verifique as informações do software e, em seguida, escolha **Carregar**. Escolha **Fechar** para sair do assistente.

8.  Na [consola de administração do Intune](https://manage.microsoft.com/), escolha **Apps** &gt; **Apps** &gt; **Skype** &gt; **Manage Deployment**.

9. Na página **Selecionar Grupos**, selecione **Os Utilizadores da Minha Versão de Avaliação** para implementar o software nesse grupo de utilizadores e, em seguida, escolha **Adicionar** &gt; **Seguinte**.

10. Na página **Ação de Implementação**, selecione **Instalação Disponível** na coluna **Aprovação** do seu grupo.

11. Escolha **Concluir**.

## <a name="install-the-skype-app"></a>Instalar a aplicação Skype
Abra o Portal da Empresa no dispositivo móvel, selecione **Aplicações** e, em seguida, instale o Microsoft Skype.

Este passo conclui o guia de gestão de dispositivos móveis do Intune, mas pode saber mais sobre o Intune ao seguir as ligações na secção Passos seguintes.
## <a name="next-steps"></a>Passos seguintes
Saber mais sobre outras [funcionalidades do Intune](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)

Ler sobre as [formas comuns de utilizar o Intune](common-ways-to-use-intune.md)

Converter numa [subscrição paga](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)
