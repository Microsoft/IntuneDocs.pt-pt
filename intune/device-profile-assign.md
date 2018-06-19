---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o portal do Azure para atribuir políticas e perfis de dispositivo a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft InTune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fa1a1b1085d196411a03a6228eefa808399397ea
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024809"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

Depois de criar um perfil, pode atribuí-lo a grupos do Azure Active Directory (Azure AD).

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** e procure **Microsoft Intune**.
2. No **Microsoft Intune**, selecione **Configuração do dispositivo** e selecione **Perfis**.
3. Na lista de perfis, selecione o perfil que pretende atribuir e, em seguida, selecione **Atribuições**.
4. Opte por **Incluir** ou **Excluir** grupos e, em seguida, selecione os grupos.  

    ![Captura de ecrã das opções para incluir ou excluir grupos de uma atribuição de perfis](./media/group-include-exclude.png)

5. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar múltiplos grupos, mantenha a tecla **Ctrl** premida.
6. Quando tiver terminado, selecione **Guardar**.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfis

Os perfis de configuração de dispositivos do Intune permitem-lhe excluir grupos da atribuição de políticas. Por exemplo, pode atribuir um perfil de dispositivo ao grupo **Todos os utilizadores da empresa**e excluir membros do grupo **Equipa de Direção**.

Ao excluir grupos de uma atribuição, exclua apenas utilizadores ou grupos de dispositivos (e não uma mistura de grupos), dado que o Intune não considera relações entre utilizador e dispositivo. Incluir grupos de utilizadores e excluir grupos de dispositivos poderá não gerar os resultados esperados. Ao utilizar grupos misturados ou se existirem outros conflitos, a inclusão terá prioridade sobre a exclusão.

Por exemplo, suponha que pretende atribuir um perfil do dispositivo a todos os dispositivos na sua organização, exceto a dispositivos de local público. Deve incluir o grupo **Todos os Utilizadores** e excluir o grupo **Todos os Dispositivos**. Neste caso, a política será aplicada a todos os utilizadores e aos respetivos dispositivos, mesmo que esses dispositivos façam parte do grupo **Todos os Dispositivos**.

A exclusão só contempla os membros diretos dos grupos e não inclui os dispositivos associados a um utilizador. No entanto, os dispositivos que não estiverem associados a um utilizador não receberão a política. Isto acontece porque esses dispositivos não têm qualquer relação com o grupo **Todos os Utilizadores**.

Se incluir o grupo **Todos os Dispositivos** e excluir **Todos os Utilizadores**, todos os dispositivos irão receber a política. Neste cenário, o objetivo é excluir desta política os dispositivos que tiverem um utilizador associado. No entanto, isto não exclui os dispositivos porque a exclusão só compara membros diretos do grupo.

>[!TIP]
>As exclusões não estão disponíveis para políticas de conformidade ou atribuições da aplicação. Para excluir membros de uma atribuição, pode utilizar as atribuições **Disponível** e **Não aplicável**. Por exemplo, pode atribuir uma aplicação ao grupo **Todos os utilizadores da empresa** com o objetivo **Disponível** e atribuir a mesma ao grupo **Equipa de Direção** com o objetivo **Não aplicável**. A aplicação é atribuída a todos os utilizadores, *exceto* aos utilizadores no grupo **Equipa de Direção**. Se atribuir a aplicação ao grupo **Todos os utilizadores da empresa** com o objetivo **Necessário**, os utilizadores no grupo **Equipa de Direção** também serão incluídos.

## <a name="next-steps"></a>Próximos passos
Veja [Como monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como controlar as atribuições de perfis de dispositivos.
