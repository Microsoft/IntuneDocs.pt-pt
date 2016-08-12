---
title: "Criar políticas e publicar uma aplicação para os utilizadores | Microsoft Intune"
description: "Como criar políticas e publicar uma aplicação quando se inscreve numa avaliação gratuita de 30 dias do Intune"
keywords: 
author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3a17884-442a-44f5-bc81-4589e823f65e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 51fba2b01d8978bc062c50c4388714609be0fdf0
ms.openlocfilehash: 1a41bfd926b1dac88ca8c8cd33483955f1150e34


---


# Criar políticas e publicar uma aplicação para utilizadores de avaliação
As políticas do Intune disponibilizam definições que o ajudam a controlar as definições de segurança nos dispositivos móveis, a gerir as definições de Endpoint Protection e Firewall do Windows de computadores e a implementar aplicações. Se estiver a planear utilizar o Intune para os dispositivos que configurou para utilização de produção após a avaliação, é absolutamente essencial que siga as instruções em [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) e [Ajudar a proteger os PC Windows com o Endpoint Protection para o Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).

Pode executar dois tipos de instalações de aplicações com o Intune. O primeiro é uma **instalação necessária**, que implementa automaticamente as aplicações nos computadores geridos. O segundo tipo é uma **instalação disponível**, que implementa as aplicações, ou ligações para as mesmas, no Portal da Empresa do Intune, para que os utilizadores possam optar por instalá-las nos computadores ou dispositivos móveis deles.

Antes de utilizar o Intune para implementar aplicações, confirme que tem as licenças adequadas para as publicar, distribuir e utilizar. A área de trabalho **Licenças** permite-lhe adicionar e gerir informações de contratos de licença de aplicações ou software comprados através de contratos de Licenciamento em Volume da Microsoft, bem como de aplicações ou software da Microsoft ou sem ser da Microsoft comprados por outros meios. Em seguida, pode criar relatórios de licenças, que apresentam informações de utilização das licenças geridas de toda a empresa, para se manter a par da atividade em torno da utilização das licenças.

Nestes passos, vai ser configurada uma política de configuração de dispositivos móveis e uma política de firewall de computador do Windows e ainda o Skype como instalação disponível para dispositivos móveis depois de serem inscritos Depois de adicionar e implementar uma política nova, todos os utilizadores ou grupos nos quais tiver implementado a política herdam as definições como a respetiva política de linha de base. Pode sempre rever e editar os detalhes destas políticas mais tarde, a partir da área de trabalho **Política** na consola de administração.

## Criar e implementar políticas de configuração de dispositivos móveis

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com/).

2.  No painel esquerdo, escolha o ícone **Política**.

3.  Na lista **Tarefas**, na página **Descrição Geral da Política**, escolha **Adicionar Política**.

4.  Na lista de políticas, expanda a plataforma para a qual pretende criar uma política, selecione **Configuração Geral**, escolha **Criar e Implementar uma Política com as Definições Recomendadas** e, em seguida, escolha **Criar Política**.

5.  Quando lhe for solicitado para **Selecionar os grupos nos quais pretende implementar esta política**, selecione **Os Utilizadores da Minha Versão de Avaliação** na lista e escolha **Adicionar** &gt; **OK**.

A sua política é apresentada na lista de políticas de configuração e foi implementada no grupo **Os Utilizadores da Minha Versão de Avaliação** . Faça duplo clique na política para ver as respetivas definições.

## Publicar a aplicação Skype em dispositivos móveis

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione o ícone **Aplicações** e, em seguida, selecione **Aplicações** &gt; **Adicionar Aplicação**. Introduza as suas credenciais do Intune, caso pedido.

    > [!NOTE]
    > Quando inicia o **Intune Software Publisher** pela primeira vez, ocorre um pequeno atraso durante a instalação da aplicação.

2.  Leia o aviso de segurança e escolha **Executar**.

3.  Na página **Antes de começar**, escolha **Seguinte**.

4.  Na página **Configuração do software** , em **Selecione de que forma este software é disponibilizado nos dispositivos**, selecione **Ligação externa**.

5.  Introduza uma ligação externa para o software em **Especificar o URL** e, em seguida, escolha **Seguinte** Certifique-se de que precede o URL com **https://**. Para a aplicação Skype, utilize a ligação abaixo que corresponda à plataforma de dispositivos móveis que está a utilizar:

    -   **iOS:** [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:** [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 ou Windows Phone 8.1:** [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Na página **Descrição do software** , indique as informações que pretende que os utilizadores vejam no Portal da Empresa relativamente ao software e, em seguida, escolha **Seguinte**. Estão disponíveis as seguintes definições (este exemplo é relativo ao Skype):

    -   **Publicador:** introduza o nome do publicador, **Microsoft**

    -   **Nome:** introduza **Skype**

    -   **Descrição:** introduza uma descrição para o software, como **aplicação de comunicação Skype**

    -   **Categoria:** selecione a categoria que melhor se adequa a este software, como **Colaboração**

    -   **Apresentar esta aplicação como uma aplicação em destaque e destacá-la no portal da empresa:** selecione esta opção para apresentar a aplicação de forma destacada no Portal da Empresa nos dispositivos móveis.

    -   **Ícone:**  (opcional) escolha se quer associar um ícone ao software. O tamanho de ícone máximo é 250 x 250 pixéis, mas o tamanho de ícone recomendado é 32 x 32 pixéis.

7.  Na página **Resumo**, verifique as informações do software e, em seguida, escolha **Carregar**. Escolha **Fechar** para sair do assistente.

8.  Na [consola de administração do Intune](https://manage.microsoft.com/), escolha **Aplicações** &gt; **Aplicações** &gt; **Skype** &gt; **Gerir Implementação**.

9. Na página **Selecionar Grupos**, selecione **Os Utilizadores da Minha Versão de Avaliação** para implementar o software nesse grupo de utilizadores e, em seguida, escolha **Adicionar** &gt; **Seguinte**.

10. Na página **Ação de Implementação** , selecione **Instalação Disponível** na coluna **Aprovação** do seu grupo.

11. Escolha **Concluir**.

A aplicação Skype está agora disponível para instalação em dispositivos móveis a partir do Portal da Empresa, mas tem de, em primeiro lugar, instalar o software do Intune nos PCs e nos dispositivos móveis.

### Passos seguintes
Parabéns! Acabou de concluir o passo 4 das instruções da *avaliação do Microsoft Intune*.

>[!div class="step-by-step"]

>[&larr; **Criar Grupos**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)     [**Inscrever Dispositivos** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)  



<!--HONumber=Aug16_HO2-->


