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
ms.openlocfilehash: 6e3219e32ef9bea838f0c19258d0b22a99083a12
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74261581"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Adicionar grupos para organizar utilizadores e dispositivos

O Intune usa grupos Azure Active Directory (Azure AD) para gerenciar dispositivos e usuários. Como administrador do Intune, pode configurar grupos para se adaptarem às suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, você pode definir políticas para muitos usuários ou implantar aplicativos em um conjunto de dispositivos.

Pode adicionar os seguintes tipos de grupos:

- **Grupos atribuídos** – adicione manualmente usuários ou dispositivos a um grupo estático. 
- **Grupos dinâmicos** (requer Azure ad Premium) – adicione automaticamente usuários ou dispositivos a grupos de usuários ou grupos de dispositivos com base em uma expressão que você criar.

  Por exemplo, quando um usuário é adicionado com o título do gerente, ele é automaticamente adicionado a um grupo **todos os gerentes** usuários. Ou, quando um dispositivo tem o tipo de so do dispositivo iOS, o dispositivo é adicionado automaticamente a um grupo **todos os dispositivos IOS dispositivos** .

## <a name="add-a-new-group"></a>Adicionar um novo grupo

Utilize os seguintes passos para criar um novo grupo.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **grupos** > **novo grupo**:

   ![Captura de tela da portal do Azure com o novo grupo selecionado](./media/groups-add/groups-add-new.png)

3. Em **tipo de grupo**, escolha uma das seguintes opções:

    - **Segurança**: os grupos de segurança definem quem pode acessar recursos e são recomendados para seus grupos no Intune. Por exemplo, você pode criar grupos para usuários, como **todos os funcionários de Charlotte** ou **todas as mulheres na contoso**. Ou crie grupos para dispositivos, como **todos os dispositivos IOS** ou **todos os dispositivos de aluno com Windows 10**.

        > [!TIP]
        > Os usuários e grupos criados também podem ser vistos no [centro de administração do Microsoft 365](https://admin.microsoft.com), no centro de administração do Azure Active Directory e [no Microsoft Intune no portal do Azure](https://go.microsoft.com/fwlink/?linkid=2090973). No locatário da sua organização, você pode criar e gerenciar grupos em todas essas áreas.
        >
        > Se sua função principal for gerenciamento de dispositivos, recomendamos que você use o [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365**: esses grupos foram projetados para controlar o acesso e compartilhar recursos do Office 365. Por exemplo, você pode criar um grupo do Office 365 para compartilhar uma caixa de entrada ou calendário do Outlook. Para obter mais informações, consulte [saiba mais sobre grupos do Office 365](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Insira um **nome de grupo** e uma **Descrição de grupo** para o novo grupo. Seja específico e inclua informações para que outras pessoas saibam o que é o grupo.

    Por exemplo, insira **todos os dispositivos de aluno do Windows 10** para o nome do grupo e **todos os dispositivos Windows 10 usados por alunos na contoso high School notas 9-12** para a descrição do grupo.

5. Insira o **tipo de associação**. As opções são:

    - **Atribuído**: os administradores atribuem usuários ou dispositivos manualmente a esse grupo e removem manualmente usuários ou dispositivos.
    - **Usuário dinâmico**: os administradores criam regras de associação para adicionar e remover membros automaticamente.
    - **Dispositivo dinâmico**: os administradores criam regras de grupo dinâmico para adicionar e remover dispositivos automaticamente.

        ![Captura de ecrã das propriedades de grupos do Intune](./media/groups-add/groups-add-properties.png)

    Para obter mais informações sobre esses tipos de associação e criar expressões dinâmicas, consulte:

    - [Criar um grupo básico e adicionar membros usando o Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Regras de associação dinâmica para grupos no Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > Nesse centro de administração, quando você cria usuários ou grupos, talvez não veja a marca de **Azure Active Directory** . Mas é isso o que você está usando.

6. Selecione **Criar** para adicionar o novo grupo. Seu grupo é mostrado na lista.

> [!TIP]
> Considere alguns dos outros grupos de usuários e dispositivos dinâmicos que você pode criar, como:
>
> - Todos os alunos da Contoso na escola alta
> - Todos os dispositivos Android Enterprise
> - Todos os dispositivos iOS 11 e mais antigos
> - Marketing
> - Recursos Humanos
> - Todos os funcionários do Charlotte
> - Todos os funcionários do WA

## <a name="groups-and-policies"></a>Grupos e políticas

O acesso aos recursos de sua organização é controlado por usuários e grupos que você cria.

Ao criar grupos, considere como você aplicará [políticas de conformidade](../protect/device-compliance-get-started.md) e [perfis de configuração](../configuration/device-profiles.md). Por exemplo, você pode ter:

- Políticas específicas para um sistema operacional do dispositivo.
- Políticas específicas para funções diferentes em sua organização.
- Políticas específicas para unidades organizacionais que você definiu em Active Directory.

Para criar os requisitos de conformidade básicos da sua organização, você pode criar uma política padrão que se aplica a todos os grupos e dispositivos. Em seguida, crie políticas mais específicas para as categorias mais amplas de usuários e dispositivos. Por exemplo, pode criar políticas de e-mail para cada um dos sistemas operativos do dispositivo.

Para obter recomendações e diretrizes do perfil de configuração, consulte [atribuir políticas a grupos de usuários ou grupos de dispositivos](../configuration/device-profile-assign.md#user-groups-vs-device-groups) e [recomendações de perfil](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>Consulte também

- [RBAC (controle de acesso baseado em função) com Microsoft Intune](role-based-access-control.md)
- [Gerenciar o acesso a recursos com grupos do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
