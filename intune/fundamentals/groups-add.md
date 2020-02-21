---
title: Adicionar grupos para organizar utilizadores e dispositivos
titleSuffix: Microsoft Intune
description: Adicione grupos para organizar utilizadores e dispositivos por geografia, departamento ou hardware específico.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183e8cc5924f6ce1f002225150d808841924e20c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514647"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Adicionar grupos para organizar utilizadores e dispositivos

Intune utiliza grupos de Diretório Ativo Azure (Azure AD) para gerir dispositivos e utilizadores. Como administrador do Intune, pode configurar grupos para se adaptarem às suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, pode definir políticas para muitos utilizadores ou implementar aplicações para um conjunto de dispositivos.

Pode adicionar os seguintes tipos de grupos:

- **Grupos atribuídos** - Adicione manualmente utilizadores ou dispositivos num grupo estático. 
- **Grupos dinâmicos** (Requer Azure AD Premium) - Adicione automaticamente utilizadores ou dispositivos a grupos de utilizadores ou grupos de dispositivos com base numa expressão que cria.

  Por exemplo, quando um utilizador é adicionado com o título de gestor, o utilizador é adicionado automaticamente a um grupo de utilizadores **de Todos os gestores.** Ou, quando um dispositivo tem o tipo OS do dispositivo iOS/iPadOS, o dispositivo é automaticamente adicionado a um grupo de **dispositivos all iOS/iPadOS.**

## <a name="add-a-new-group"></a>Adicionar um novo grupo

Utilize os seguintes passos para criar um novo grupo.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Grupos** > **Novo grupo:**

   ![Screenshot do portal Azure com novo grupo selecionado](./media/groups-add/groups-add-new.png)

3. No **tipo de Grupo,** escolha uma das seguintes opções:

    - **Segurança**: Os grupos de segurança definem quem pode aceder aos recursos e são recomendados para os seus grupos em Intune. Por exemplo, pode criar grupos para utilizadores, como **todos os funcionários da Charlotte** ou **trabalhadores remotos.** Ou criar grupos para dispositivos, como **todos os dispositivos iOS/iPadOS** ou **todos os dispositivos estudantis do Windows 10.**

        > [!TIP]
        > Os utilizadores e grupos criados também podem ser vistos no centro de administração da [Microsoft 365,](https://admin.microsoft.com)no Centro de Administração do Azure Ative Directory e [no Microsoft Intune no portal Azure.](https://go.microsoft.com/fwlink/?linkid=2090973) Na sua organização inquilino, você pode criar e gerir grupos em todas estas áreas.
        >
        > Se a sua função principal é a gestão do dispositivo, recomendamos que utilize o [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365**: Proporciona oportunidades de colaboração dando aos membros acesso a uma caixa de correio partilhada, calendário, ficheiros, site SharePoint, e muito mais. Esta opção também lhe permite conceder às pessoas fora da organização acesso ao grupo. Para mais informações, consulte [O Office 365 Groups](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Insira um nome de **grupo** e **descrição** do grupo para o novo grupo. Seja específico e inclua informações para que outros saibam para que é o grupo.

    Por exemplo, introduza **todos os dispositivos estudantis do Windows 10** para nome de grupo, e **todos os dispositivos Windows 10 usados por alunos do liceu de Contoso 9-12** para descrição do grupo.

5. Introduza o **tipo de Membro**. As opções são:

    - **Atribuído**: Os administradores atribuem manualmente utilizadores ou dispositivos a este grupo e removam manualmente utilizadores ou dispositivos.
    - **Utilizador Dinâmico**: Os administradores criam regras de adesão para adicionar e remover automaticamente os membros.
    - **Dispositivo Dinâmico**: Os administradores criam regras dinâmicas de grupo para adicionar e remover automaticamente os dispositivos.

        ![Captura de ecrã das propriedades de grupos do Intune](./media/groups-add/groups-add-properties.png)

    Para obter mais informações sobre estes tipos de membros e criar expressões dinâmicas, consulte:

    - [Crie um grupo básico e adicione membros usando AD Azure](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Regras dinâmicas de adesão para grupos em Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > Neste centro de administração, quando cria utilizadores ou grupos, pode não ver a marca **Azure Ative Directory.** Mas é isso que estás a usar.

6. Selecione **Criar** para adicionar o novo grupo. O seu grupo está na lista.

> [!TIP]
> Considere alguns dos outros grupos dinâmicos de utilizador e dispositivo que pode criar, tais como:
>
> - Todos os alunos da escola de Contoso
> - Todos os dispositivos Android Enterprise
> - Todos os dispositivos iOS 11 e mais antigos
> - Marketing
> - Recursos Humanos
> - Todos os empregados da Charlotte
> - Todos os funcionários da WA

## <a name="groups-and-policies"></a>Grupos e políticas

O acesso aos recursos da sua organização é controlado por utilizadores e grupos que cria.

Quando criar grupos, considere como irá aplicar políticas de [conformidade](../protect/device-compliance-get-started.md) e perfis de [configuração](../configuration/device-profiles.md). Por exemplo, pode ter:

- Políticas específicas para um sistema operativo de dispositivos.
- Políticas específicas para diferentes papéis na sua organização.
- Políticas específicas para unidades organizacionais que definiu no Diretório Ativo.

Para criar os requisitos básicos de conformidade da sua organização, pode criar uma política padrão que se aplica a todos os grupos e dispositivos. Em seguida, crie políticas mais específicas para as categorias mais amplas de utilizadores e dispositivos. Por exemplo, pode criar políticas de e-mail para cada um dos sistemas operativos do dispositivo.

Para recomendações e orientações de perfil de configuração, consulte [as políticas de atribuição a grupos de utilizadores ou grupos](../configuration/device-profile-assign.md#user-groups-vs-device-groups) de dispositivos e [recomendações](../configuration/device-profile-create.md#recommendations)de perfil .

## <a name="see-also"></a>Veja também

- [Controlo de acesso baseado em funções (RBAC) com microsoft Intune](role-based-access-control.md)
- [Gerir o acesso a recursos com grupos DaD Azure](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
