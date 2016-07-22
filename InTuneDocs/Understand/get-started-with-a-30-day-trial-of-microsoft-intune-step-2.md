---
title: "Adicionar utilizadores à avaliação de 30 dias do Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cb729533107d511fa0cc863ec6ab842e7624982
ms.openlocfilehash: 15e641f4f5f60c4a3eb3a7b09cab8cb9ef788cba


---

# Adicionar utilizadores à avaliação de 30 dias do Microsoft Intune
Agora que configurou a sua conta, irá utilizar o assistente **Novos Utilizadores** para adicionar contas de utilizador individuais ao Intune ou o assistente **Adição de utilizadores em volume** para adicionar utilizadores em volume (consulte as instruções nesta secção).  Antes de começar, é importante que compreenda a forma como o Intune processa as contas de administrador.

Um administrador inquilino utiliza o centro de administração do Office 365 para adicionar utilizadores ao **Grupo de Utilizadores** do Microsoft Intune. A adição de utilizadores ao  **Grupo de Utilizadores** permite atribuir licenças de subscrição do Intune aos utilizadores, sendo igualmente o meio utilizado para apresentar esses utilizadores na consola de administração do Microsoft Intune.

Ao contrário das contas de utilizador normais, as contas de administrador para o Intune não são criadas no centro de administração do Office 365. Em vez disso, os direitos administrativos de acesso só de leitura ou de acesso total são atribuídos aos utilizadores através da consola de administração na área de trabalho **Administração** em **Gestão da Administração**. Os administradores de serviço aos quais é atribuído acesso só de leitura não podem alterar as definições do Intune, mas podem ver dados e executar relatórios. Os administradores de serviço com acesso total têm todos os direitos administrativos disponíveis.

Pode ver as informações do administrador de inquilinos através da consola de administração do Intune, mas não pode criar administradores de inquilinos nessa consola. Por predefinição, o proprietário da subscrição torna-se no administrador inquilino do seu serviço Microsoft Intune e tem acesso total tanto ao centro de administração do Office 365 como à consola de administração do Intune. Recomendamos que crie, pelo menos, uma conta de administrador inquilino adicional através do centro de administração do Office 365 para ajudar a delegar tarefas e garantir que não fica com o acesso à sua conta de administrador do serviço Intune bloqueado se se esquecer da sua palavra-passe.

## Adicionar contas de utilizador individuais
Utilize os seguintes passos para criar contas de utilizador adicionais no inquilino da sua avaliação. Lembre-se, cada conta de utilizador que adicionar é contabilizada como uma das 100 licenças obtidas como parte da avaliação gratuita do Intune.

1.  No [centro de administração do Office 365](http://go.microsoft.com/fwlink/?LinkID=787455), escolha **Adicionar Utilizadores** &gt; **Novo** &gt; **Utilizador** para iniciar o assistente **Novos utilizadores**.

2.  Na página **Detalhes** , preencha os campos obrigatórios.

3.  Na página **Definições** , defina a **localização** do utilizador.

4.  Na página **Grupo**, escolha **Seguinte** para aceitar a predefinição e atribuir uma licença do Intune à conta do utilizador.

5.  Na página **E-mail** , especifique até cinco endereços de e-mail que receberão uma notificação relativamente ao nome de utilizador e à palavra-passe temporária da conta. Separe múltiplos endereços de e-mail com um ponto e vírgula (;). Quando tiver terminado, escolha **Criar** para adicionar o utilizador à sua subscrição.

6.  Na página **Resultados** , pode ver o novo nome da conta e a respetiva palavra-passe temporária. O Intune cria automaticamente a palavra-passe temporária.

7.  Quando o utilizador novo aparecer no centro de administração do Office 365, certifique-se de que foi criado com êxito:

    1.  Na [consola de administração do Intune](https://manage.microsoft.com/), escolha **Administração** &gt; **Portal da Empresa** e, em seguida, desloque-se para a parte inferior do ecrã. Copie o URL apresentado em **Portal da Empresa do Intune**.

    2.  Abra uma nova janela do browser no "modo de privacidade" (no Internet Explorer, escolha **Ferramentas** &gt; **Navegação InPrivate**) ou abra uma nova janela do browser noutro dispositivo e, em seguida, navegue para o URL que copiou no passo anterior. Quando os utilizadores iniciarem sessão pela primeira vez, têm de fornecer uma nova palavra-passe para a conta.

## Adicionar utilizadores em volume
Para adicionar utilizadores em volume ao Intune, utilize o assistente **Adição de utilizadores em volume** para carregar um ficheiro de valores separados por vírgulas (CSV) que contenha os dados dos utilizadores. As ligações presentes no assistente permitem-lhe transferir um modelo em branco e um ficheiro CSV de exemplo. A primeira linha do ficheiro CSV tem de conter, pela ordem correta, cada uma das etiquetas de coluna de dados dos utilizadores. Em seguida, para cada utilizador no ficheiro CSV, tem de incluir o **nome de utilizador** (como **miguel@contoso.com**) e um **nome a apresentar** (como **Miguel Cardoso**).

1.  No [centro de administração do Office 365](http://go.microsoft.com/fwlink/?LinkID=787455), escolha **Utilizadores** &gt; **Novo**.

2.  Escolha **Adicionar em volume** para iniciar o assistente Adicionar utilizadores em volume.

3.  Na página **Selecionar ficheiro** , escolha **Procurar** para especificar e carregar um ficheiro CSV existente a partir do computador. Também pode transferir um ficheiro CSV de exemplo ou o ficheiro de modelo em branco utilizando as ligações presentes no assistente.

4.  Na página **Verificação**, consulte os resultados e, em seguida, escolha **Ver** para obter mais detalhes.

5.  Na página **Definições**, confirme se o estado de início de sessão está definido como **Permitido** e defina a **localização**. Estas definições aplicam-se a todas as contas de utilizador adicionadas pelo ficheiro CSV.

6.  Na página **Grupo**, escolha **Seguinte** para aceitar a predefinição e atribuir uma licença do Intune a todas as contas de utilizador adicionadas pelo ficheiro CSV. Por predefinição, a caixa de verificação está selecionada, o que atribui uma licença do Intune a cada conta.

7.  Na página **E-mail**, especifique até cinco endereços de e-mail para receber a notificação relativamente aos nomes de utilizador e às palavras-passe temporárias que o Intune cria para cada conta. Separe os vários endereços de e-mail com ponto e vírgula (;). Escolha **Criar** para adicionar os utilizadores à subscrição.

8.  Na página **Resultados** , pode ver os nomes das contas e palavra-passe temporária de cada conta de utilizador.

Cada conta de utilizador adicionada através da importação é agora apresentada no nó **Utilizadores** do centro de administração do Office 365. Quando os novos utilizadores iniciarem sessão pela primeira vez, têm de especificar uma nova palavra-passe para a conta de utilizador correspondente.

### Passos seguintes
Parabéns! Acabou de concluir o passo 2 das instruções da *avaliação do Microsoft Intune*.

>[!div class="step-by-step"]

>[&larr; **Inscrever-se para uma avaliação**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**Criar grupos** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  



<!--HONumber=Jun16_HO4-->


