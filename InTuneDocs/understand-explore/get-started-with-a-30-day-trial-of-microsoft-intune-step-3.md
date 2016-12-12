---
title: Criar grupos para organizar utilizadores e dispositivos | Microsoft Intune
description: "Como criar grupos de dispositivos e grupos de utilizadores quando se inscreve numa avaliação gratuita de 30 dias do Microsoft Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: ab451a1213923ecd27dfc0b8ca353041e70435ed


---

# <a name="create-groups-to-organize-evaluation-subscription-users-and-devices"></a>Criar grupos para organizar utilizadores e dispositivos de subscrições de avaliação
Os Grupos no Intune dão-lhe uma grande flexibilidade na gestão dos seus dispositivos e utilizadores. Pode configurar os grupos conforme as suas necessidades organizacionais (por exemplo, por localização geográfica, por departamento ou por características de hardware) e utilizá-los para efetuar uma variedade de tarefas administrativas em escala, desde definir políticas para um conjunto de utilizadores a implementar aplicações num conjunto de dispositivos.

## <a name="create-a-device-group"></a>Criar um grupo de dispositivos
Utilize grupos de dispositivos para implementar software e atualizações, e configurar as políticas Definições do Agente do Microsoft Intune e Definições da Firewall do Windows. Por exemplo, configure um grupo "Dispositivos da Minha Versão de Avaliação" através dos seguintes passos:

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Descrição Geral** &gt; **Criar Grupo**.

2.  No **Nome do grupo**, escreva "Dispositivos da Minha Versão de Avaliação" e, na lista do grupo principal, selecione **Todos os Dispositivos**. Em seguida, escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação** , selecione **Todos os dispositivos** para indicar se o grupo inclui dispositivos móveis e computadores.

4.  Na página **Definir Associação Direta**, escolha **Seguinte**. Se criou anteriormente um grupo que não inclui todos os dispositivos e quer adicionar dispositivos específicos ao seu grupo novo, pode fazê-lo aqui.

5.  Na página **Resumo**, reveja as ações que serão efetuadas e escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos** , na área de trabalho **Grupos** , em **Todos os Dispositivos**. Aqui, também pode editar ou eliminar o grupo.

## <a name="create-a-user-group"></a>Criar um grupo de utilizadores
Utilize grupos de utilizadores para implementar políticas de software e de dispositivos. Por exemplo, configure um grupo "Utilizadores da Minha Versão de Avaliação" através dos seguintes passos:

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione **Grupos** &gt; **Descrição Geral** &gt; **Criar Grupo**.

2.  No **Nome do grupo**, escreva "Utilizadores da Minha Versão de Avaliação" e, na lista do grupo principal, selecione **Todos os Utilizadores**. Em seguida, escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação** , defina **Iniciar associação ao grupo com** como **Todos os utilizadores no grupo Principal**.

4.  Junto a **Excluir membros destes grupos de segurança**, escolha **Procurar** e, em seguida, selecione **Administrador da Empresa**. Esta exclusão permite-lhe gerir o grupo Utilizadores da Minha Versão de Avaliação sem afetar a conta de Administrador da Empresa (também conhecido como administrador de inquilinos).

5.  Na página **Definir Associação Direta**, escolha **Seguinte**. Aqui não precisa de fazer nada, uma vez que pretende que o grupo Os Utilizadores da Minha Versão de Avaliação inclua todos os utilizadores, exceto o Administrador da Empresa.

6.  Na página **Resumo**, reveja as ações que serão efetuadas e escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos** , na área de trabalho **Grupos** , em **Todos os Utilizadores**. Aqui, também pode editar ou eliminar o grupo.

Para saber mais sobre como utilizar grupos, veja [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="next-steps"></a>Passos seguintes
[Criar políticas](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO5-->

