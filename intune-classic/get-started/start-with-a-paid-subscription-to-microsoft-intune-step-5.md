---
title: Criar grupos para organizar utilizadores e dispositivos | Documentos da Microsoft
description: "Criar utilizadores e grupos para a sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 058006b2356d62c77c3a5a6ee0f4c8ed74ed4a50
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---


# <a name="create-groups-to-organize-users-and-devices"></a>Criar grupos para organizar utilizadores e dispositivos

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tópico informa os administradores sobre como podem criar grupos de utilizadores no Intune.

Os Grupos no Intune dão-lhe uma grande flexibilidade na gestão dos seus dispositivos e utilizadores. Pode configurar grupos conforme as necessidades da sua organização (por exemplo, por localização geográfica, por departamento ou por características de hardware) e utilizá-los para efetuar uma grande variedade de tarefas administrativas, desde implementar políticas para um conjunto de utilizadores a implementar aplicações num conjunto de dispositivos.

## <a name="group-management-moving-to-azure-ad"></a>Gestão de grupo em transferência para o Azure AD

**A partir de novembro de 2016**, as novas contas irão gerir grupos de utilizadores e dispositivos no portal Azure Active Directory (AD). Em dezembro de 2016, a equipa do produto do Intune iniciará a migração de clientes existentes para a nova experiência de gestão de grupos com base no Azure AD. Todos os grupos de utilizadores e dispositivos do Intune serão migrados para os grupos de segurança do Azure AD. Não iniciaremos as migrações enquanto não conseguirmos minimizar qualquer impacto no seu trabalho diário e enquanto não previrmos que estas não afetarão os seus utilizadores. Também enviaremos um aviso antes da migração da sua conta.


>[!IMPORTANT]
>
>Se abrir a área de trabalho Grupos no portal do Intune e vir **Os grupos de utilizadores do Intune são agora geridos como grupos no Active Directory do Azure** com uma ligação para o portal Azure Active Directory, tal significa que já está a utilizar a *nova* abordagem dos grupos de segurança do Azure AD à gestão de grupos no Intune. Para saber como criar grupos, veja [Gerir grupos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
>
>Caso não veja a ligação para o portal do Azure AD, ainda está a utilizar o portal do Intune para gestão de grupos.

## <a name="group-management-in-the-intune-portal"></a>Gestão de grupos no portal do Intune

Os grupos de dispositivos e utilizadores são criados na área de trabalho GRUPOS da consola de administração do Intune.

![Área de trabalho de grupos de consola de administração](./media/groups.png)


> [!TIP]
> Para saber mais sobre como utilizar grupos, veja [Utilizar grupos para gerir utilizadores e dispositivos com o Microsoft Intune](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## <a name="create-a-device-group"></a>Criar um grupo de dispositivos
Utilize grupos de dispositivos para implementar aplicações e atualizações e para configurar outras funcionalidades. Por exemplo, configure um grupo "Os Meus Dispositivos" através dos seguintes passos:

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione **Grupos** > **Descrição Geral** > **Criar Grupo**.

2.  No **Nome do grupo**, introduza "Os Meus Dispositivos" e, na lista de grupos principais, selecione **Todos os Dispositivos** e, em seguida, escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação**, selecione **Todos os dispositivos** para indicar se o grupo inclui dispositivos móveis e computadores.

4.  Na página **Definir Associação Direta**, escolha **Seguinte**. Se tiver criado anteriormente um grupo que não incluía todos os dispositivos e quer adicionar dispositivos específicos ao seu grupo novo, pode fazê-lo aqui.

5.  Na página **Resumo**, reveja as ações que serão efetuadas e escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos**, na área de trabalho **Grupos**, em **Todos os Dispositivos**. Aqui, também pode editar ou eliminar o grupo.

## <a name="create-a-user-group"></a>Criar um grupo de utilizadores
Utilize grupos de utilizadores para implementar políticas de software e de dispositivos. Por exemplo, configure o grupo "Utilizadores do Intune" através dos seguintes passos:

1.  Na [consola de administração do Intune](https://manage.microsoft.com/), selecione **Grupos** > **Descrição Geral** > **Criar Grupo**.

2.  No **Nome do grupo**, escreva "Utilizadores do Intune" e, na lista do grupo principal, selecione **Todos os Utilizadores** e, em seguida, escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação**, defina **Iniciar associação ao grupo com** como **Todos os utilizadores no grupo Principal**.

4.  Junto a **Excluir membros destes grupos de segurança**, escolha **Procurar** e, em seguida, selecione **Administrador da Empresa**. Esta exclusão permite-lhe gerir o grupo Utilizadores do Intune sem afetar a conta do Administrador da Empresa (também conhecido como administrador de inquilino).

5.  Na página **Definir Associação Direta**, escolha **Seguinte**. Aqui, não precisa de fazer nada, uma vez que pretende que o grupo Utilizadores do Intune inclua todos os utilizadores, exceto o Administrador da Empresa.

6.  Na página **Resumo**, reveja as ações que serão efetuadas e escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos**, na área de trabalho **Grupos**, em **Todos os Utilizadores**. Aqui, também pode editar ou eliminar o grupo.

>[!div class="step-by-step"]

>[&larr; **Gerir licenças do Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**Criar políticas e aplicações** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  
