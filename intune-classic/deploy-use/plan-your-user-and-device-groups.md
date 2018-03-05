---
title: Planear os grupos de utilizadores e de dispositivos
description: "Planeie grupos para corresponder às suas necessidades organizacionais."
keywords: 
author: sanchusa
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5c1f06cc59ff81483d9e54b23435af720d919155
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="plan-your-user-and-device-groups"></a>Planear os grupos de utilizadores e de dispositivos

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Os Grupos no Intune dão-lhe uma grande flexibilidade quando estiver as gerir os seus dispositivos e utilizadores. Pode configurar grupos para se adaptarem às suas necessidades organizacionais de acordo com:

- localização geográfica
- departamento
- características de hardware
- sistema operativo
- o facto de o dispositivo ser propriedade do utilizador ou propriedade da empresa


## <a name="how-intune-groups-work"></a>Como funcionam os grupos do Intune


Esta é a vista predefinida do nó **Grupos** na consola de administração do Intune:

![Captura de ecrã da vista predefinida do nó Grupos na consola do Intune](../media/Intune_Planning_Groups_Default_small.png)

As políticas são implementadas em grupos, pelo que a hierarquia de grupos é uma das principais considerações de estrutura. Não pode alterar o grupo principal de um grupo depois de este ser criado. A forma como estrutura os seus grupos é de importância fundamental a partir do momento em que começa a utilizar o serviço Intune. São descritas aqui algumas das práticas recomendadas para criar uma hierarquia de grupos com base nas suas necessidades organizacionais.

## <a name="group-membership-rules"></a>Regras de associação a grupos

- Um grupo pode conter utilizadores ou dispositivos, mas não ambos.

    * **Grupos de dispositivos**. Inclui os computadores e os dispositivos móveis. Antes de poder adicionar um computador a um grupo, este tem de ser inscrito. Antes de poder adicionar um dispositivo móvel a um grupo, o seu ambiente tem de ser configurado para suportar dispositivos móveis e os dispositivos têm de ser inscritos ou detetados no Exchange ActiveSync.

    * **Grupos de utilizadores**. Um grupo pode ter utilizadores de grupos de segurança. Os grupos de segurança são sincronizados com a instância do Active Directory. Se não sincronizar com o Active Directory, pode criar estes grupos manualmente.

- Um dispositivo ou um utilizador pode pertencer a mais do que um grupo.

- Um grupo pode incluir e excluir membros com base nas seguintes regras de associação:

    * **Associação por Critérios**. Estes são regras dinâmicas que o Intune executa para incluir ou excluir membros. Estes critérios utilizam grupos de segurança e outras informações sincronizadas com a sua instância local do Active Directory. Quando o grupo de segurança ou os dados mudam, a associação ao grupo muda quando sincroniza com o Active Directory.

    * **Associação Direta**. estas são regras estáticas que adicionam ou excluem explicitamente membros. A lista de membros é estática.

-   Os Serviços de Domínio do Active Directory (AD DS) não são necessários quando cria grupos de utilizadores ou de dispositivos que incluem utilizadores ou computadores. No entanto, para os grupos de dispositivos incluírem dispositivos móveis, o seu ambiente tem de ser configurado para suportar dispositivos móveis.

    Além disso, os dispositivos têm de ser detetados e adicionados ao Intune.

## <a name="group-relationship-rules"></a>Regras de relação do grupo

- Cada grupo que criar tem de ter um grupo principal. É importante saber que não pode alterar o grupo principal de um grupo depois de este ser criado.

- Quando adiciona utilizadores ou dispositivos a um grupo subordinado:

    * O grupo subordinado é sempre um subconjunto do grupo principal.

    * Os novos membros que adicionar a um grupo subordinado são automaticamente adicionados ao grupo principal desse grupo.

    * Não pode adicionar um membro a um grupo subordinado quando esse membro está excluído do grupo principal.

- A associação de um grupo principal define a associação disponível para o grupo subordinado.

- Ao eliminar um grupo principal, todos os grupos subordinados são eliminados.

- Pode implementar conteúdo e políticas num grupo principal, mas excluir a implementação nos grupos subordinados.

- Pode adicionar um utilizador ou dispositivo específico a um grupo subordinado se o utilizador ou dispositivo não for já um membro do grupo principal. Se o fizer, o novo membro do grupo subordinado será adicionado ao grupo principal.

    No entanto, não pode adicionar um membro a um grupo subordinado se o membro estiver excluído do grupo principal.

- A associação a grupos é recursiva. Por exemplo:

    * a**Teresa** é um membro de apenas um grupo, o grupo de segurança **Utilizadores de Portáteis**.

    * O grupo **Utilizadores de Portáteis** é um membro do grupo de segurança **Utilizadores Aprovados**.

    * O utilizador cria um grupo no Intune que utiliza uma consulta de associação dinâmica que inclui os membros do grupo **Utilizadores Aprovados**. O resultado é que o seu grupo de utilizadores do Intune inclui a **Teresa**.

> [!TIP]
> Quando criar grupos, pense como irá aplicar a política. Por exemplo, pode ter políticas específicas para sistemas operativos de dispositivos ou políticas específicas para diferentes funções ou unidades organizacionais que já definiu no seu serviço Active Directory. Alguns administradores consideram útil criar grupos de dispositivos específicos para iOS, Android e Windows. Isto, para além da criação de grupos de utilizadores para cada função organizacional.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## <a name="built-in-groups"></a>Grupos incorporados
O Intune disponibiliza nove grupos incorporados que não pode editar ou eliminar: <!--maybe a screen shot would be best?-->

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
> Adote o lema: *manter as coisas simples*. Se a sua organização não tiver necessidades específicas, como as descritas nas secções seguintes, mantenha as coisas simples e opte pela estrutura e pelas políticas de grupo predefinidas. Desta forma, o serviço torna-se mais fácil de gerir a longo prazo. A manutenção será mais fácil se conseguir tratar os seus utilizadores de modo uniforme. Com uma pequena diferenciação por grupo, terá menos políticas para manter.


### <a name="all-users-and-devices-in-your-organization"></a>Todos os utilizadores e dispositivos da organização
Defina um grupo principal para todos os utilizadores e dispositivos da sua organização. É provável que tenha políticas que serão aplicadas a todos. Pode utilizar os grupos predefinidos do Intune **Todos os Utilizadores** e **Todos os dispositivos** para este fim. Os subgrupos que organizam os dispositivos por especificações, como um grupo para dispositivos BYOD (Bring Your Own Device) e um grupo para dispositivos pertencentes à empresa (CO), podem ser os subordinados dos grupos principais **Todos os Utilizadores** e **Todos os dispositivos**.

## <a name="customize-groups-for-your-organization"></a>Personalizar grupos para a sua organização

### <a name="byod-and-corporate-owned-devices"></a>Dispositivos BYOD e pertencentes à empresa
Se a sua organização permitir que os empregados utilizem os seus próprios dispositivos, fornecer dispositivos pertencentes à empresa, ou uma combinação de ambos, recomendamos que aplique políticas separadas com base nestas categorias de dispositivos.

No caso de BYOD ou de uma combinação, tenha o cuidado de planear políticas que não interfiram nas regulamentações de privacidade locais. Crie um grupo principal para todos os utilizadores que vão trazer os dispositivos deles. Pode utilizar este grupo para aplicar as políticas que são aplicáveis a todos os utilizadores nesta categoria.

![Criar um grupo principal BYOD](../media/Intune_Planning_Groups_BYOD_small.png)

Da mesma forma, pode criar um grupo para os utilizadores de dispositivos CO na sua organização:

![Grupos de utilizadores colaterais para dispositivos BYOD e CO](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### <a name="groups-for-geographic-regions"></a>Grupos para regiões geográficas
Se a sua organização precisar de políticas para regiões específicas, pode criar grupos com base na região geográfica. Pode baseá-los em grupos regionais que pode já ter criado na sua instância do Active Directory e sincronizá-los com o seu serviço Azure Active Directory. Também pode criar grupos regionais diretamente no Azure Active Directory.

As capturas de ecrã seguintes mostram-lhe como criar grupos do Intune com base nos grupos sincronizados com a instância do Active Directory no local. Estes exemplos partem do princípio de que tem um grupo de segurança do Active Directory denominado **Grupo de Utilizadores dos EUA**.

Em primeiro lugar, forneça as informações gerais.

![Captura de ecrã da área Editar Grupo](../media/Intune_Planning_Groups_AD_General_small.png)

Em **Critérios de associação**, selecione **Grupo de Utilizadores dos EUA**, sincronizado com o Active Directory, como o grupo de segurança a utilizar nas regras de associação.

![Captura de ecrã da caixa de diálogo Editar Grupo](../media/Intune_Planning_Groups_AD_Criteria_small.png)

Reveja as entradas e, em seguida, escolha **Concluir** para criar o grupo.

![Captura de ecrã da caixa de diálogo Editar Grupo](../media/Intune_Planning_Groups_AD_Summary_small.png)

No nosso exemplo, também criámos um grupo com o nome **MEA**, para o Médio Oriente e a Ásia.

> [!NOTE]
> Se a associação ao grupo não for preenchida com base na associação de grupo de segurança, certifique-se de que atribuiu licenças do Intune aos membros do grupo.

### <a name="groups-for-specific-hardware"></a>Grupos para hardware específico
Se a sua organização precisar de políticas que se apliquem a tipos específicos de hardware, pode criar grupos com base neste requisito. Pode basear as políticas em grupos específicos que pode já ter criado na sua instância do Active Directory no local e, em seguida, sincronizá-los com o Azure Active Directory. Também pode criar grupos diretamente no Azure Active Directory. Neste exemplo, utilizamos o **Grupo de Utilizadores dos EUA** como grupo principal do grupo **Utilizadores de Portáteis**.

![Caixa de diálogo Selecionar Grupo de Segurança](../media/Intune_Planning_Groups_Laptop_small.png)

Neste momento, a hierarquia de grupos deve ser semelhante à captura de ecrã seguinte. Pode ver que existem agora membros no grupo do Intune **Utilizadores de Portáteis**. Todas as políticas aplicadas a este grupo serão aplicadas aos utilizadores de portáteis BYOD da região dos EUA.

![Apresentação do grupo de utilizadores de portáteis](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### <a name="groups-for-specific-operating-systems"></a>Grupos para sistemas operativos específicos
Se a sua organização precisar de políticas que se apliquem a sistemas operativos específicos, como Android, iOS ou Windows, pode criar grupos com base neste requisito. Tal como nos exemplos anteriores, pode basear as políticas em grupos específicos do SO que pode já ter criado na sua instância do Active Directory no local e sincronizá-los com o Azure Active Directory. Também pode criá-los diretamente na sua instância do Azure Active Directory.

Ao utilizar o mesmo método dos exemplos anteriores, pode criar grupos com base nos utilizadores <!--devices?--> que utilizam plataformas de sistema operativo específicas.

> [!NOTE]
> Se tiver utilizadores que utilizem várias plataformas ou sistemas operativos móveis e não dispuser de uma forma de categorizar automaticamente esses utilizadores como utilizadores de Android, iOS ou Windows, considere aplicar políticas ao nível do dispositivo. Isto irá proporcionar-lhe mais flexibilidade na aplicação de políticas específicas de um sistema operativo.
>
> Não pode aprovisionar grupos dinamicamente com base no sistema operativo do dispositivo. Em vez disso, faça-o com grupos de segurança do Active Directory ou do Azure Active Directory.

![Grupo de utilizadores de portáteis](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

Depois de todos os grupos de utilizadores estarem preenchidos com base nos requisitos organizacionais, a hierarquia de grupos deverá ter um aspeto parecido com o seguinte:

![Vista da hierarquia de grupos](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Pode utilizar esta hierarquia para aplicar as políticas da organização.

### <a name="device-groups"></a>Grupos de dispositivos
Também pode criar grupos semelhantes para dispositivos, conforme apresentado aqui, começando com um grupo abrangente que inclua todos os dispositivos propriedade dos empregados, para o cenário BYOD.

![Caixa de diálogo Criar Grupo](../media/Intune_Planning_Groups_Device_General_small.png)

Certifique-se de que seleciona **Todos os dispositivos (computadores e dispositivos móveis)**, para que o grupo inclua todos os dispositivos BYO:

![Página de definição de critérios de associação](../media/Intune_Planning_Groups_Device_Criteria_small.png)

Reveja as entradas e, em seguida, escolha **Concluir** para criar o grupo BYOD.

![Caixa de diálogo Criar Grupo](../media/Intune_Planning_Groups_Device_Summary_small.png)

Continue a criar grupos de dispositivos, até ter uma hierarquia de grupos de dispositivos semelhante à hierarquia de grupos de utilizadores. O nó do grupo na consola do Intune deverá ter um aspeto semelhante ao seguinte:

![Vista de hierarquia de grupos do Intune](../media/Intune_Groups_Hierarchy_Final_Small.png)

## <a name="group-hierarchies-and-naming-conventions"></a>Hierarquias de grupos e convenções de nomenclatura
Para facilitar a gestão de políticas, recomendamos que atribua um nome a cada política de acordo com o objetivo, a plataforma e o âmbito com que é aplicada. Utilize um padrão de nomenclatura que siga a estrutura de grupos que criou quando se preparou para aplicar as políticas.

Por exemplo, para uma política do Android que seja aplicada a todos os dispositivos móveis Android da empresa, ao nível regional dos EUA, o nome da política pode ser **CO_EUA_Móv_Android_Geral**.

![Criar política para Android](../media/Intune_planning_policy_android_small.png)

Ao atribuir um nome às políticas desta forma, poderá identificar as políticas rapidamente, bem como a respetiva utilização e âmbito previstos no nó **Políticas**, deste modo:

![Lista de políticas do Intune](../media/Intune_planning_policy_view_small.png)

## <a name="next-steps"></a>Passos seguintes
[Criar grupos](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
