---
# required metadata

title: Planear os grupos de utilizadores e de dispositivos | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Planear os grupos de utilizadores e de dispositivos
Os grupos no Intune proporcionam uma enorme flexibilidade para gerir os seus dispositivos e utilizadores. Pode configurar grupos para se adaptarem às suas necessidades organizacionais de acordo com:

- localização geográfica
- departamento
- características de hardware
- sistema operativo
- o facto de o dispositivo ser propriedade do utilizador ou propriedade da empresa


## Como funcionam os grupos do Intune


A vista predefinida do nó Grupos na consola de administração do Intune é:

![Captura de ecrã da vista predefinida do nó Grupos na consola do Intune](/intune/media/Intune_Planning_Groups_Default_small.png)

As políticas são implementadas em grupos, pelo que a hierarquia do grupo é uma das principais considerações de design. Também é importante saber que o grupo principal de um grupo não pode ser alterado depois de este ser criado, pelo que o design dos grupos é fundamental a partir do momento em que começa a utilizar o serviço Intune. São descritas aqui algumas das práticas recomendadas para criar uma hierarquia de grupo com base nas suas necessidades organizacionais.

## Regras de associação a grupos

1. Um grupo pode conter utilizadores ou dispositivos, mas não ambos.

    * **Grupos de dispositivos** : inclui os computadores e os dispositivos móveis. Antes de poder adicionar um computador a um grupo, este tem de ser inscrito. Antes de poder adicionar um dispositivo móvel a um grupo, o seu ambiente tem de ser configurado para suportar dispositivos móveis e os dispositivos têm de ser inscritos ou detetados a partir do Exchange ActiveSync.

    * **Grupos de utilizadores** : um grupo pode conter utilizadores de grupos de segurança, que são os grupos que se sincronizam a partir do seu Active Directory. Se não utilizar a sincronização do Active Directory, pode criar estes grupos manualmente.

2. Um dispositivo ou um utilizador pode pertencer a mais do que um grupo.

3. Um grupo pode incluir e excluir membros com base nas seguintes regras de associação:

    * **Critérios de Associação:** são regras dinâmicas que o Intune executa para incluir ou excluir membros. Estes critérios utilizam **grupos de segurança** e outras informações sincronizadas a partir do seu Active Directory (AD) local. Quando o grupo de segurança ou os dados mudam, a associação ao grupo muda quando sincroniza com o AD.

    * **Associação Direta** : são regras estáticas que adicionam ou excluem explicitamente membros. A lista de membros é estática.

4. Os Serviços de Domínio do Active Directory (AD DS) não são necessários para criar grupos de utilizadores ou grupos de dispositivos que incluem utilizadores ou computadores, mas para os grupos de dispositivos incluírem dispositivos móveis, o seu ambiente tem de ser configurado para suportar dispositivos móveis.

    Além disso, os dispositivos têm de ser detetados e adicionados ao Intune.

## Regras de relação do grupo

1. Todos os grupos que criar têm de ter um grupo principal e, depois de o grupo ser criado, o grupo principal desse grupo não pode ser alterado.

2. Quando adiciona utilizadores ou dispositivos a um grupo subordinado:

    * Os grupos subordinados são sempre subconjuntos de um grupo principal.

    * Os novos membros que adicionar a um grupo subordinado são automaticamente adicionados ao grupo principal desse grupo.

    * Não pode adicionar um membro a um grupo subordinado quando esse membro está excluído do grupo principal.

3. A associação de um grupo principal define a associação disponível para o grupo subordinado.

4. Ao eliminar um grupo principal, todos os grupos subordinados são eliminados.

5. Pode implementar conteúdo e políticas num grupo principal enquanto exclui a implementação nos grupos subordinados.

6. Pode adicionar um utilizador ou dispositivo específico a um grupo subordinado que não é um membro do grupo principal. Se o fizer, o novo membro do grupo será adicionado ao grupo principal.

    No entanto, não pode adicionar um membro a um grupo subordinado que esteja excluído do grupo principal.

7. A associação a grupos é recursiva. Por exemplo:

    * a**Teresa** é um membro de apenas um grupo, o grupo de segurança **Utilizadores de Portáteis** .

    * O grupo **Utilizadores de Portáteis** é um membro do grupo de segurança **Utilizadores Aprovados** .

    * O utilizador cria um grupo no Intune que utiliza uma consulta de associação dinâmica que inclui os membros do grupo **Utilizadores Aprovados**. O resultado é que o seu grupo de utilizadores do Intune inclui a **Teresa**.

> [!TIP]
> Quando estiver a criar grupos, pense como irá aplicar a política. Por exemplo, pode ter políticas específicas para sistemas operativos de dispositivos e políticas específicas para diferentes funções na sua organização ou para Unidades Organizacionais que já definiu no Active Directory. Alguns utilizadores consideram útil ter grupos de dispositivos específicos para iOS, Android e Windows, bem como grupos de utilizadores para cada função organizacional.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Grupos incorporados
O Intune disponibiliza nove grupos incorporados que não pode editar nem eliminar: <!--maybe a screen shot would be best?-->

-   **Todos os Utilizadores**
    -   Utilizadores Sem Grupo
-   **Todos os Dispositivos**
    -   Todos os Computadores
    -   Todos os Dispositivos Móveis
        -   Todos os Dispositivos Geridos Diretamente
        -   Todos os Dispositivos Geridos pelo Exchange ActiveSync
    -   Todos os Dispositivos Pertencentes à Empresa
    -   Dispositivos Sem Grupo

> [!NOTE]
> Adote o lema: *manter as coisas simples*. Se a sua organização não tiver necessidades específicas, como as descritas abaixo, mantenha as coisas simples e opte pela estrutura e pelas políticas de grupo predefinidas para tornar o serviço mais fácil de gerir a longo prazo. A manutenção será mais fácil se for possível tratar os utilizadores da mesma forma, com poucas diferenças por grupo, o que faz com que tenha de manter menos políticas.


### Todos os utilizadores e dispositivos da organização
Defina um grupo principal para todos os utilizadores e dispositivos da organização , uma vez que é provável que tenha políticas que se apliquem a todos. Pode utilizar os grupos **Todos os Utilizadores** e **Todos os dispositivos** no Intune para este fim. Os subgrupos que organizam os dispositivos por especificações, como um grupo para dispositivos BYOD (Bring Your Own Device) e um grupo para dispositivos pertencentes à empresa (CO), podem ser os subordinados dos grupos principais **Todos os Utilizadores** e **Todos os dispositivos**.

## Personalizar grupos para a sua organização

### Dispositivos BYOD e pertencentes à empresa
Se a sua organização permitir que os funcionários utilizem os seus próprios dispositivos no local de trabalho (BYOD), fornecer dispositivos pertencentes à empresa (CO), ou uma combinação de ambos, recomendamos que aplique políticas com base nessas duas categorias de dispositivos.

No caso de BYOD ou de uma combinação, tenha o cuidado de planear políticas que não interfiram nas regulamentações de privacidade locais. Crie um grupo principal para todos os utilizadores que vão trazer os dispositivos deles. Este grupo pode, posteriormente, ser utilizado para aplicar as políticas que são aplicáveis a todos os utilizadores nesta categoria.

![Captura de ecrã da criação de um grupo principal BYOD](/intune/media/Intune_Planning_Groups_BYOD_small.png)

Da mesma forma, pode criar um grupo para os utilizadores de CO na sua organização:

![Captura de ecrã de grupos de utilizadores colaterais para BYOD e CO](/intune/media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Grupos para regiões geográficas
Se a sua organização precisar de políticas para regiões específicas, pode criar grupos com base na região geográfica. Pode baseá-los em grupos regionais que possa já ter criado no Active Directory (AD) e sincronizá-los com o Azure AD. Também pode criá-los diretamente no Azure AD.

Estas capturas de ecrã mostram como criar grupos do Intune com base em grupos sincronizados a partir do AD no local. Este exemplo parte do princípio de que tem um grupo de segurança do AD com o nome **Grupo de Utilizadores dos EUA**.

1. Em primeiro lugar, forneça as informações gerais.

![Captura de ecrã da área Editar Grupo](/intune/media/Intune_Planning_Groups_AD_General_small.png)

Nos Critérios de associação, selecione **Grupo de Utilizadores dos EUA**, sincronizado a partir do AD, como o grupo de segurança a utilizar nas Regras de associação.

![Caixa de diálogo Editar Grupo](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

Reveja e, em seguida, escolha **Concluir** para concluir a criação do grupo.

![Caixa de diálogo Editar Grupo](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

No nosso exemplo, também criámos um grupo Médio Oriente e Ásia, MEA.

> [!NOTE] Se a associação ao grupo não for preenchida com base na associação ao grupo de segurança, verifique se atribuiu licenças do Intune a esses membros.

### Grupos para hardware específico
Se a sua organização precisar de políticas que se apliquem a tipos específicos de hardware, pode criar grupos com base neste requisito. Pode baseá-los em grupos específicos que já tenha criado no AD no local e sincronizá-los com o Azure AD. Também pode criá-los diretamente no Azure AD. Neste exemplo, utilizamos o **Grupo de Utilizadores dos EUA** como o principal do grupo **Utilizadores de portáteis**.

![Caixa de diálogo Selecionar Grupo de Segurança](/intune/media/Intune_Planning_Groups_Laptop_small.png)

Nesta fase, a hierarquia do grupo deverá aparecer da seguinte forma: Como pode ver, existem agora membros no grupo do Intune **Utilizadores de portáteis**. Todas as políticas aplicadas a este grupo serão agora aplicadas aos utilizadores de portáteis BYOD da região dos EUA.

![Apresentação do grupo de utilizadores de portáteis](/intune/media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Grupos para sistemas operativos específicos
Se a sua organização precisar de políticas que se apliquem a sistemas operativos específicos, como Android, iOS ou Windows, pode criar grupos com base neste requisito. Tal como nos exemplos anteriores, pode baseá-los em grupos específicos de sistema operativo que já tenha criado no AD no local e sincronizá-los com o Azure AD. Também pode criá-los diretamente no Azure AD.

Seguindo o mesmo método dos exemplos anteriores, podemos criar grupos com base em utilizadores <!--devices?--> que utilizem plataformas de SO específicas.

> [!NOTE] Se tiver utilizadores que utilizem várias plataformas/sistemas operativos móveis e não dispuser de uma forma de categorizar automaticamente esses utilizadores como utilizadores de Android, iOS ou Windows, considere aplicar políticas ao nível do dispositivo, o que lhe garantirá mais flexibilidade na aplicação de políticas específicas de SO.
>
> Não pode aprovisionar grupos dinamicamente com base no SO do dispositivo. Para tal, utilize grupos de Segurança do AD ou do AAD.

![Apresentação do grupo de utilizadores de portáteis](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

Depois de todos os Grupos de utilizadores estarem preenchidos com base nestes requisitos organizacionais, a hierarquia de grupo deverá ter um aspeto parecido com o seguinte:

![Vista de hierarquia de grupos](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Esta hierarquia pode ser utilizada para aplicar as políticas da organização adequadamente.

### Grupos de dispositivos
Também pode criar grupos semelhantes para dispositivos, conforme apresentado abaixo, começando com um grupo abrangente que inclua todos os dispositivos propriedade dos empregados, para o cenário BYOD:

![Caixa de diálogo Criar Grupo](/intune/media/Intune_Planning_Groups_Device_General_small.png)

Certifique-se de que seleciona **Todos os dispositivos (computadores e dispositivos móveis)**, para que o grupo inclua todos os dispositivos BYO:

![Página de definição de critérios de associação](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

Reveja e escolha **Concluir** para criar o grupo BYOD.

![Caixa de diálogo Criar grupo](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

Continue a criar grupos de dispositivos, até ter uma hierarquia de grupo de dispositivos semelhante à hierarquia de grupo de utilizadores. Depois, o nó do grupo na consola do Intune deverá ter um aspeto semelhante a:

![Vista de hierarquia de grupos do Intune](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## Hierarquias de grupos e convenções de nomenclatura
Para facilitar a gestão de políticas, recomendamos que atribua um nome a cada política de acordo com o objetivo, a plataforma e o âmbito com que é aplicada. Este padrão de nomenclatura deve seguir a estrutura do grupo que criou durante a preparação da aplicação das políticas.

Por exemplo, para uma política do Android que seja aplicada a todos os dispositivos móveis Android da empresa, ao nível regional dos EUA, o nome da política pode ser **CO_US_Mob_Android_General**.

![Criar política para Android](/intune/media/Intune_planning_policy_android_small.png)

Ao denominar as políticas desta forma, poderá identificar as políticas rapidamente, bem como a sua utilização prevista e âmbito, a partir do nó de políticas da consola, conforme apresentado:

![Lista de políticas do Intune](/intune/media/Intune_planning_policy_view_small.png)

## Passos seguintes
[Criar grupos](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=Jun16_HO3-->


