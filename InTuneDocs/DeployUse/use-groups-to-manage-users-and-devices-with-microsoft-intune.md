---
title: Utilizar grupos para gerir utilizadores e dispositivos | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cc64e51499908d08823429871cda91dfb0078b1e
ms.openlocfilehash: a1f6dfc7629481403c40a1ce927b588f67e5fa74


---

# Criar grupos para gerir utilizadores e dispositivos com o Microsoft Intune

Para criar e gerir grupos, utilize a área de trabalho **Grupos** na consola de administração do Microsoft Intune. A página **Descrição Geral dos Grupos** contém resumos do estado que o ajudam a identificar e a atribuir prioridades a problemas que necessitam da sua atenção para:

-   Alertas
-   Atualizações de software
-   Endpoint Protection
-   Política
-   Gestão de software

Além disso, a hierarquia de grupo é apresentada com resumos de estado para ajudar a identificar e resolver problemas de membros de um grupo selecionado.


> [!TIP]
> Ao criar os grupos, tenha em consideração a forma como irá aplicar a política. Por exemplo, pode ter políticas específicas para sistemas operativos de dispositivos e políticas específicas para diferentes funções na sua organização ou para Unidades Organizacionais que já definiu no Active Directory. Alguns utilizadores consideram útil ter grupos de dispositivos específicos para iOS, Android e Windows, bem como grupos de utilizadores para cada função organizacional.
>
> Provavelmente, será útil criar uma política padrão que se aplique a todos os grupos e dispositivos, para estabelecer os requisitos de conformidade básicos da sua empresa. Depois, crie políticas mais específicas para as categorias mais amplas de utilizadores e dispositivos, como, por exemplo, políticas de e-mail para cada um dos sistemas operativos dos dispositivos.
>
> Seja cuidadoso ao atribuir os nomes às políticas, para que as possa identificar facilmente mais tarde. Por exemplo, um nome bom e descritivo para uma política é **Política de E-mail para WP para Toda a Empresa**.
>
> Sempre que criar uma política restritiva, deverá comunicá-la aos utilizadores, pelo que, depois de criar os grupos e as políticas mais gerais, tenha atenção a como criar grupos mais pequenos, para que possa reduzir a comunicação desnecessária.


## Criar um grupo de dispositivos

1.  Na consola de administração do Intune, selecione **Grupos** &gt; **Descrição Geral** &gt; **Criar Grupo**.

2.  Forneça um nome e uma descrição opcional para o grupo e selecione um grupo de dispositivos como o grupo principal. Escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação** , selecione o tipo de dispositivos que o grupo irá incluir. Opções adicionais para configurar o grupo dependendo do tipo de dispositivos que selecionar:

    -   **Computador**: especifique se inclui todos os membros do grupo principal, as Unidades Organizacionais (UO) que pretende incluir ou excluir e os domínios que pretende incluir ou excluir. As informações da UO e de domínio de um computador são obtidas a partir do inventário.

    -   **Dispositivos Móveis**: especifique se inclui apenas os dispositivos móveis que são geridos pelo Intune, os que são geridos pelo Exchange ActiveSync ou ambos.

    -   **Todos os dispositivos** : esta opção inclui todos os dispositivos sem exclusões com base nos critérios.

4.  Na página **Definir Associação Direta** , inclua ou exclua os dispositivos individuais que especificar ao clicar em **Procurar**. Se utilizar a opção para selecionar dispositivos que não se encontram no grupo principal que especificou, esses dispositivos são adicionados automaticamente ao grupo principal.


5.  Na página **Resumo**, reveja as ações que serão efetuadas. Escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos**, na área de trabalho **Grupos**, no grupo principal. Aqui, também pode editar ou eliminar o grupo.

## Criar um grupo de utilizadores

1.  Na consola de administração do Intune, selecione **Grupos** &gt; **Descrição Geral** &gt; **Criar Grupo**.

2.  Forneça um nome e uma descrição opcional para o grupo e selecione um grupo de utilizadores como o grupo principal. Escolha **Seguinte**.

3.  Na página **Definir Critérios de Associação** , especifique se inclui todos os membros do grupo principal ou se começa com um grupo vazio.  Em seguida, pode incluir ou excluir membros com base nos **Grupos de segurança** dos utilizadores que configurar manualmente no [Centro de administração do Office 365](http://go.microsoft.com/fwlink/?LinkId=698854) ou que sincronizar a partir do seu Active Directory local. Se a associação de um grupo de segurança mudar, a associação dos grupos de utilizadores com base nesse grupo de segurança também podem mudar.

    > [!IMPORTANT]
    > Atualmente, se o grupo incluir os membros de grupos de segurança ou gestores específicos e também excluir membros de grupos específicos, os membros incluídos inicialmente serão removidos. Para criar um grupo que tenha membros incluídos e excluídos, recomendamos que crie primeiro um grupo principal com os membros incluídos e, em seguida, crie um subordinado a esse grupo no qual listará os membros excluídos. Em seguida, pode utilizar o grupo subordinado conforme adequado para as políticas, perfis e distribuição de aplicações do Intune.

    > [!NOTE]
    > No Portal de Gestão do Azure, pode criar um grupo com base no gestor a quem os utilizadores reportam. O grupo será dinâmico, alterando os empregados à medida que são adicionados ou removidos da equipa desse gestor no Azure Active Directory. O procedimento para criar um grupo do Azure com base num gestor está descrito em [Utilizar atributos para criar regras avançadas](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) na secção denominada **Para configurar um grupo como um grupo "Gestor"**.


4.  Na página **Definir Associação Direta** , inclua ou exclua utilizadores individuais que especificou ao clicar em **Procurar**. Se utilizar a opção para selecionar utilizadores que não se encontram no grupo principal que especificou, esses utilizadores são adicionados automaticamente ao grupo principal. Na parte inferior da caixa de diálogo **Selecionar Membros**, encontrará a opção para adicionar manualmente um utilizador. Esta ação é útil se pretender adicionar um utilizador que ainda não tem um dispositivo inscrito.


5.  Na página **Resumo**, reveja as ações que serão efetuadas. Escolha **Concluir**.

Pode encontrar o grupo recém-criado na lista **Grupos**, na área de trabalho **Grupos**, no grupo principal. Aqui, também pode editar ou eliminar o grupo.

> [!TIP]
> Os grupos de segurança são um ótimo recurso para preencher os grupos de utilizadores. Uma vez que os grupos de segurança definem quem tem acesso a quais recursos, estes podem ser bem traduzidos para grupos de utilizadores do Intune. Os grupos de segurança que são sincronizados a partir do Active Directory para o Azure Active Directory ou que são criados diretamente no Azure Active Directory através do centro de administração do Office 365 ou do portal de Administração do Azure, estão disponíveis para que possa criar grupos de utilizadores no Intune.

## Personalizar vistas de acordo com funções de administrador
As vistas de grupo filtradas permitem personalizar a vista que os administradores podem ver com base na sua função e restringir os grupos que cada administrador de TI pode gerir. Esta ação pode ser útil quando:

-   Os seus administradores de TI devem apenas poder implementar itens a utilizadores e a dispositivos específicos.

-   Pretende apresentar apenas grupos relevantes para cada administrador de TI.

Pode configurar vistas de grupo filtradas para administradores de serviço na consola do administrador do Intune. Para obter mais detalhes, veja [O que deve saber antes de iniciar o Microsoft Intune](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

Após configurar as vistas de grupo filtradas para um administrador de serviço, esse administrador:

-   Pode ver e selecionar apenas os grupos que tiver especificado ao implementar software ou políticas ou ao utilizar relatórios

-   Não recebe informações de estado nas seguintes páginas da consola de administração:

    -   **Descrição Geral do Sistema**

    -   **Descrição Geral dos Grupos**

    -   **Descrição Geral do Endpoint Protection**

    -   **Descrição Geral dos Alertas**

    -   **Descrição Geral do Software**

    -   **Descrição Geral da Política**

### Configurar vistas de grupo filtradas

1.  Na consola de administração do Intune, escolha **Admin** &gt; **Gestão de Administradores** &gt; **Administradores de Serviço**.

2.  Selecione o administrador de serviço para o qual pretende filtrar grupos e, em seguida, clique em **Gerir Grupos**.

3.  Na caixa de diálogo **Selecionar os grupos que estarão visíveis para este administrador de serviço** , adicione os grupos que o administrador de serviço selecionado poderá aceder e, em seguida, clique em **OK**.

Após configurar as vistas de grupo filtradas, o administrador de TI poderá visualizar e selecionar apenas os grupos que o utilizador selecionou.

## Gerir os grupos
Depois de criar os grupos, continuará a geri-los de acordo com as necessidades da sua organização.

Pode editar o seu grupo para alterar o nome e a descrição e quem pertence ao mesmo.

Pode eliminar um grupo que já não serve as necessidades da sua organização. Eliminar um grupo não elimina os utilizadores que pertencem a esse grupo.

## Passos seguintes

### Verificar a estrutura
Depois de configurar os grupos e as políticas, verifique as implicações práticas da estrutura em **Valor Pretendido** e **Estado**.

1. Selecione qualquer dispositivo de um grupo de dispositivos e procure as categorias de informações na parte superior do ecrã.
2. Selecione **Política** . Verá algo semelhante a esta captura de ecrã das definições de política de um dispositivo Android.

![Política de definições do iOS de exemplo](../media/Intune-Device-Policy-v.2.jpg)

Cada política tem um **Valor Pretendido** e um **Estado**. O valor pretendido é o que esperava obter com a atribuição da política. O estado é o que é realmente obtido quando todas as políticas que se aplicam ao dispositivo, bem como as restrições e os requisitos de hardware e do sistema operativo, são consideradas em conjunto.  Na captura de ecrã, verá dois exemplos claros:

-   A opção**Permitir palavras-passe simples** está definida como **Sim**, conforme apresentado na coluna **Valor Pretendido** , mas o **Estado** está definido como **Não aplicável**. Isto ocorre porque os dispositivos Android não suportam as palavras-passe simples.

-   Da mesma forma, o item de política expandida, **Definições de e-mail para dispositivos iOS**, não se aplica a este dispositivo, uma vez que é um dispositivo Android.

> [!NOTE]
> Lembre-se de que quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, na prática, é aplicada a política mais restrita.



<!--HONumber=Jun16_HO4-->


