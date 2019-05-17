---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o portal do Azure para atribuir políticas e perfis de dispositivo a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c950efdd95fd8d856ec677385712a022dead870
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59898739"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Criou um perfil que inclui todas as definições que introduziu. O passo seguinte é implementar ou “atribuir” o perfil aos grupos de utilizadores ou dispositivos do Microsoft Azure Active Directory (Microsoft Azure AD). Quando for atribuído, os utilizadores e os dispositivos recebem o perfil e as definições que introduziu são aplicadas.

O artigo mostra como atribuir um perfil, inclui também alguma informação sobre a utilização de etiquetas de âmbito nos perfis.

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** > filtre o **Intune** > selecione  **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis**. Todos os perfis são apresentados.
3. Selecione o perfil que quer atribuir > **Atribuições**.
4. Escolha **Incluir** ou **Excluir** grupos e, em seguida, selecione os grupos. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar vários grupos, mantenha premida a tecla **Ctrl** e selecione os grupos.

    ![Captura de ecrã das opções para incluir ou excluir grupos de uma atribuição de perfis](./media/group-include-exclude.png)

5. **Guarde** as suas alterações.

### <a name="evaluate-how-many-users-are-targeted"></a>Avaliar a quantidade de utilizadores visados

Quando atribui o perfil, também pode **Avaliar** quantos utilizadores são afetados. Esta funcionalidade calcula os utilizadores, mas não calcula os dispositivos.

1. No Intune, selecione **Configuração do dispositivo** > **Perfis**.
2. Selecione um perfil > **Atribuições** > **Avaliar**. É apresentada uma mensagem que mostra a quantidade de utilizadores visados por este perfil.

Se o botão **Avaliar** ficar cinzento, verifique se o perfil foi atribuído a um ou mais grupos.


## <a name="use-scope-tags"></a>Utilizar etiquetas de âmbito

Quando criar ou atualizar um perfil, também pode adicionar etiquetas de âmbito ao perfil.

As **etiquetas de âmbito** são uma ótima forma de atribuir e filtrar políticas para grupos específicos, tais como Recursos Humanos ou Todos os funcionários dos EUA. Para obter mais informações, veja [Utilizar o RBAC e etiquetas de âmbito para TI distribuídas](scope-tags.md).

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfis

Os perfis de configuração de dispositivos do Intune permitem-lhe excluir grupos da atribuição de políticas. Por exemplo, pode atribuir um perfil de dispositivo ao grupo **Todos os utilizadores da empresa** e excluir membros do grupo **Equipa de Direção**.

Ao excluir grupos, exclua apenas utilizadores ou grupos de dispositivos (e não uma mistura de grupos) de uma atribuição, dado que o Intune não contempla relações entre utilizador e dispositivo. Incluir grupos de utilizadores e excluir grupos de dispositivos poderá não gerar os resultados esperados. Ao utilizar grupos misturados ou se existirem outros conflitos, a inclusão terá prioridade sobre a exclusão.

Por exemplo, suponha que pretende atribuir um perfil do dispositivo a todos os dispositivos na sua organização, exceto a dispositivos de local público. Deve incluir o grupo **Todos os Utilizadores** e excluir o grupo **Todos os Dispositivos**. Neste caso, a política será aplicada a todos os utilizadores e aos dispositivos deles, mesmo que esses dispositivos façam parte do grupo **Todos os Dispositivos**.

A exclusão contempla apenas os membros diretos do grupo. Não inclui dispositivos associados a um utilizador. No entanto, os dispositivos que não estiverem associados a um utilizador não receberão a política. Tal acontece porque esses dispositivos não têm qualquer relação com o grupo **Todos os Utilizadores**.

Se incluir o grupo **Todos os Dispositivos** e excluir **Todos os Utilizadores**, todos os dispositivos irão receber a política. Neste cenário, o objetivo é excluir desta política os dispositivos que tiverem um utilizador associado. No entanto, isto não exclui os dispositivos porque a exclusão só compara membros diretos do grupo.

## <a name="next-steps"></a>Próximos passos

Veja [monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como monitorizar os perfis e os dispositivos que executam os seus perfis.