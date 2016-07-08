---
title: Criar grupos para organizar utilizadores e dispositivos | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: 00ac59ffe219109dd48c47e59de9ecf588f07344


---


# Criar grupos para organizar utilizadores e dispositivos
Os Grupos no Intune dão-lhe uma grande flexibilidade na gestão dos seus dispositivos e utilizadores. Pode configurar grupos conforme as necessidades da sua organização (por exemplo, por localização geográfica, por departamento ou por características de hardware) e utilizá-los para efetuar uma grande variedade de tarefas administrativas, desde implementar políticas para um conjunto de utilizadores a implementar aplicações num conjunto de dispositivos.

Os grupos de dispositivos e utilizadores são criados na área de trabalho GRUPOS da consola de administração do Intune.

![Área de trabalho de grupos de consola de administração](./media/groups.png)


> [!TIP]
> Para saber mais sobre como utilizar grupos, veja [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## Criar um grupo de dispositivos
Utilize grupos de dispositivos para implementar aplicações e atualizações e para configurar outras funcionalidades. Por exemplo, configure um grupo "Os Meus Dispositivos" através dos seguintes passos:

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione **Grupos** > **Descrição Geral** > **Criar Grupo**.

2.  No **Nome do grupo**, introduza "Os Meus Dispositivos" e, na lista de grupos principais, selecione **Todos os Dispositivos** e, em seguida, escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação** , selecione **Todos os dispositivos** para indicar se o grupo inclui dispositivos móveis e computadores.

4.  Na página **Definir Associação Direta**, escolha **Seguinte**. Se tiver criado anteriormente um grupo que não incluía todos os dispositivos e quer adicionar dispositivos específicos ao seu grupo novo, pode fazê-lo aqui.

5.  Na página **Resumo**, reveja as ações que serão efetuadas e escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos** , na área de trabalho **Grupos**, em **Todos os Dispositivos**. Aqui, também pode editar ou eliminar o grupo.

## Criar um grupo de utilizadores
Utilize grupos de utilizadores para implementar políticas de software e de dispositivos. Por exemplo, configure o grupo "Utilizadores do Intune" através dos seguintes passos:

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione **Grupos** > **Descrição Geral** > **Criar Grupo**.

2.  No **Nome do grupo**, escreva "Utilizadores do Intune" e, na lista do grupo principal, selecione **Todos os Utilizadores** e, em seguida, escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação** , defina **Iniciar associação ao grupo com** como **Todos os utilizadores no grupo Principal**.

4.  Junto a **Excluir membros destes grupos de segurança**, escolha **Procurar** e, em seguida, selecione **Administrador da Empresa**. Esta exclusão permite-lhe gerir o grupo Utilizadores do Intune sem afetar a conta do Administrador da Empresa (também conhecido como administrador de inquilino).

5.  Na página **Definir Associação Direta**, escolha **Seguinte**. Aqui, não precisa de fazer nada, uma vez que pretende que o grupo Utilizadores do Intune inclua todos os utilizadores, exceto o Administrador da Empresa.

6.  Na página **Resumo**, reveja as ações que serão efetuadas e escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos**, na área de trabalho **Grupos**, em **Todos os Utilizadores**. Aqui, também pode editar ou eliminar o grupo.



### Passos seguintes
Parabéns! Acabou de concluir o passo 5 do *Guia de introdução do Intune*.

>[!div class="step-by-step"]

>[&larr; **Gerir licenças do Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**Criar políticas e aplicações** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Jun16_HO4-->


