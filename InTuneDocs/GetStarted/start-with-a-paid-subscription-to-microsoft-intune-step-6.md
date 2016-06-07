---
# required metadata

title: Criar políticas e publicar aplicações | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Criar políticas e publicar aplicações
As políticas do Intune disponibilizam definições que o ajudam a controlar as definições de segurança nos dispositivos móveis, a gerir as definições de Endpoint Protection e Firewall do Windows de computadores e a implementar aplicações. Pode saber mais em [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](/Intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) e [Ajudar a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](/Intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

Pode executar dois tipos de instalações de aplicações com o Intune. O primeiro é uma **instalação necessária**, que implementa automaticamente as aplicações nos computadores geridos. O segundo tipo é uma **instalação disponível**, que implementa as aplicações, ou ligações para as mesmas, no portal da empresa do Intune, para que os utilizadores possam optar por instalá-las nos computadores ou dispositivos móveis deles.

<!-- this section really isn't necessary and confuses a lot of people because most mobile device apps aren't licensed this way (and our licensing/reporting features aren't super helpful). I think it's best to avoid this during a quick start guide.

Before using Intune to deploy apps, make sure that you have the appropriate licenses to publish, distribute, and use the app. The Licenses workspace lets you add and manage license agreement information for apps or software purchased through Microsoft Volume Licensing agreements, and for Microsoft or non-Microsoft software that was purchased by other means. You can then create license reports that display managed license usage information throughout your company to stay informed of license usage activity.
-->

Os passos seguintes ajudá-lo-ão a configurar uma política de configuração de dispositivos móveis, uma política de firewall de PC Windows e ainda o Skype como instalação disponível para dispositivos móveis depois de serem inscritos.

> [!TIP]
> Depois de adicionar e implementar uma política nova, todos os utilizadores ou grupos nos quais tiver implementado a política herdam as definições como a respetiva política de linha de base. Pode sempre rever e editar os detalhes destas políticas mais tarde, a partir da Área de trabalho de política.


## Criar e implementar políticas de configuração de dispositivos móveis

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com/)

2.  No painel esquerdo, escolha o ícone **Política**.

    ![admin-console-policy-workspace](./media/policy.png)

3.  Na lista **Tarefas** na página **Descrição Geral da Política**, escolha **Adicionar Política**

4.  Na lista de políticas, expanda a plataforma para a qual quer criar uma política, em seguida, escolha **Configuração Geral** > **Criar e Implementar uma Política com as Definições Recomendadas** > **Criar Política**

5.  Quando lhe for pedido para **Selecionar os grupos aos quais pretende aplicar esta política**, escolha **Utilizadores do Intune** (o grupo criado durante o passo anterior) a partir da lista de grupos disponíveis, e escolha **Adicionar** > **OK**

A sua política é apresentada na lista de políticas de configuração e foi implementada no grupo **Utilizadores do Intune**. Faça duplo clique na política para ver as respetivas definições.

## Publicar a aplicação Skype em dispositivos móveis

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), escolha o ícone **Aplicações** e, em seguida, escolha **Aplicações** > **Adicionar Aplicação**. Introduza as suas credenciais do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], caso pedido.

    ![admin-console-apps-workspace](./media/apps.png)

    > Quando inicia o **Intune Software Publisher** pela primeira vez, ocorre um pequeno atraso durante a instalação da aplicação.

2.  Consulte o aviso de segurança e escolha **Executar**

3.  Na página **Antes de começar**, escolha **Seguinte**

4.  Na página **Configuração do software**, em **Selecione de que forma este software é disponibilizado nos dispositivos**, escolha **Ligação externa**

5.  Introduza uma ligação externa para o software em **Especificar o URL** e, em seguida, escolha **Seguinte** Certifique-se de que precede o URL com **http://**. Para a aplicação Skype, utilize a ligação abaixo que corresponda à plataforma de dispositivos móveis que está a utilizar:

    -   **iOS:**   [https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8](https://itunes.apple.com/us/app/skype-for-iphone/id304878510?mt%3D8)

    -   **Android:**  [https://play.google.com/store/apps/details?id=com.skype.raider](https://play.google.com/store/apps/details?id=com.skype.raider)

    -   **Windows Phone 8 ou Windows Phone 8.1:**  [http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51](http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51)

6.  Na página **Descrição do software**, indique as informações que pretende que os utilizadores vejam no portal da empresa relativamente ao software e, em seguida, escolha **Seguinte**. Estão disponíveis as seguintes definições (este exemplo é relativo ao Skype):

    -   **Editor:** introduza o nome do editor, "Microsoft"

    -   **Nome:** introduza **Skype**

    -   **Descrição:** introduza uma descrição para o software, como **aplicação de comunicação Skype**

    -   **Categoria:** selecione a categoria que melhor se adequa a este software, como **Colaboração**

    -   **Apresentar esta aplicação como uma aplicação em destaque e destacá-la no portal da empresa:** Selecione esta opção para apresentar a aplicação de forma destacada no portal da empresa nos dispositivos móveis.

    -   **Ícone:** selecione se pretende associar um ícone ao software. O tamanho máximo do ícone opcional é de 250 x 250 pixels e o tamanho recomendado é de 32 x 32 pixels.

7.  Na página **Resumo**, verifique as informações do software e, em seguida, escolha **Carregar**. Escolha **Fechar** para sair do assistente.

8.  Na [consola de administração do Intune](https://manage.microsoft.com/), escolha **Aplicações** > **Aplicações** > **Skype** > **Gerir Implementação**

9. Na página **Selecionar Grupos**, escolha **Utilizadores do Intune** para implementar o software nesse grupo de utilizadores e, em seguida, escolha **Adicionar** > **Seguinte**

10. Na página **Ação de Implementação** , selecione **Instalação Disponível** na coluna **Aprovação** do seu grupo.

11. Escolha **Concluir**

A aplicação Skype está agora disponível para instalação em dispositivos móveis a partir do portal da empresa, mas tem primeiro de instalar o software do [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] nos computadores e nos dispositivos móveis.


### Passos seguintes
Parabéns! Acabou de concluir o passo 6 do *Guia de introdução do Intune*

>[!div class="step-by-step"]

>[&larr; **Organizar utilizadores e dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)       [**Personalizar o Portal da Empresa** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  


<!--HONumber=May16_HO2-->

