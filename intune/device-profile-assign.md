---
title: Atribuir perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Utilize o portal do Azure para atribuir políticas e perfis de dispositivo a utilizadores e dispositivos. Saiba como excluir grupos de uma atribuição de perfis no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2019
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
ms.openlocfilehash: 1d77308e010b71ec076f33b669674ce1252937f9
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394846"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Atribuir perfis de utilizador e dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Criar um perfil e inclui todas as definições que introduziu. A próxima etapa é implementar ou "atribuir" o perfil aos seus grupos de utilizadores ou dispositivos do Azure Active Directory (Azure AD). Quando for atribuído, os utilizadores e dispositivos recebem o seu perfil e as definições que introduziu são aplicadas.

Este artigo mostra-lhe como atribuir um perfil e inclui algumas informações sobre como utilizar etiquetas de âmbito nos seus perfis.

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis**. São listados todos os perfis.
3. Selecione o perfil que pretende atribuir > **atribuições**.
4. Optar por **inclusão** grupos ou **excluir** agrupa e, em seguida, selecione os grupos. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar múltiplos grupos, mantenha premida a **Ctrl** da chave e selecionar os seus grupos.

    ![Captura de ecrã das opções para incluir ou excluir grupos de uma atribuição de perfis](./media/group-include-exclude.png)

5. **Guarde** as suas alterações.

## <a name="use-scope-tags"></a>Utilizar etiquetas de âmbito

Quando criar ou atualizar um perfil, também pode adicionar etiquetas de âmbito para o perfil.

**Definir o âmbito etiquetas** são uma excelente forma de atribuir e filtrar políticas a grupos específicos, como recursos humanos ou por NC dos EUA todos os funcionários. [Utilizar etiquetas de âmbito e o RBAC para distribuído IT](scope-tags.md) tem mais informações.

## <a name="exclude-groups-from-a-profile-assignment"></a>Excluir grupos de uma atribuição de perfis

Os perfis de configuração de dispositivos do Intune permitem-lhe excluir grupos da atribuição de políticas. Por exemplo, pode atribuir um perfil de dispositivo para o **todos os utilizadores empresariais** de grupo, mas excluir membros no **equipa de direção** grupo.

Ao excluir grupos, exclua apenas utilizadores ou excluir apenas grupos de dispositivos (não uma mistura de grupos) de uma atribuição, o Intune não considera qualquer relação de utilizador para o dispositivo. Incluir grupos de utilizadores e excluir grupos de dispositivos poderá não receber os resultados esperados. Quando utilizar grupos misturados ou se existirem outros conflitos, a inclusão terá prioridade sobre a exclusão.

Por exemplo, suponha que pretende atribuir um perfil do dispositivo a todos os dispositivos na sua organização, exceto a dispositivos de local público. Deve incluir o grupo **Todos os Utilizadores** e excluir o grupo **Todos os Dispositivos**. Neste caso, todos os seus utilizadores e os respetivos dispositivos obtém a política, mesmo se o dispositivo do utilizador estiver no **todos os dispositivos** grupo.

Exclusão aborda apenas os membros diretos do grupo. Ele não inclui dispositivos que estão associados um utilizador. No entanto, os dispositivos que não estiverem associados a um utilizador não receberão a política. Isto acontece porque esses dispositivos não têm qualquer relação com o **todos os utilizadores** grupo.

Se incluir o grupo **Todos os Dispositivos** e excluir **Todos os Utilizadores**, todos os dispositivos irão receber a política. Neste cenário, o objetivo é excluir desta política os dispositivos que tiverem um utilizador associado. No entanto, isto não exclui os dispositivos porque a exclusão só compara membros diretos do grupo.

## <a name="next-steps"></a>Passos Seguintes

Ver [monitorizar perfis de dispositivos](device-profile-monitor.md) para obter orientações sobre como monitorizar os seus perfis e os dispositivos que executam os seus perfis.