---
title: Como atribuir perfis de dispositivos com o Intune
titlesuffix: Azure portal
description: "Assim que tiver criado um perfil de dispositivo do Intune, utilize este tópico para saber como atribuí-lo a dispositivos.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef03eeab32050559d34d3d7d580c06c21f5ffb05
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-assign-microsoft-intune-device-profiles"></a>Como atribuir perfis de dispositivo do Microsoft Intune

## <a name="assign-a-device-profile"></a>Atribuir um perfil do dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
1. No painel **Configuração do dispositivo**, escolha **Gerir** > **Perfis**.
2. No painel da lista de perfis, selecione o perfil que quer gerir e, em seguida, no painel <*nome do perfil*> **Relatórios**, selecione **Gerir** > **Atribuições**.
3. No painel seguinte, selecione **Incluir** (para incluir grupos) ou **Excluir** (para excluir os grupos) e, em seguida, selecione **Selecionar grupos**.
![Inclua e exclua grupos a partir de uma atribuição de perfis.](./media/group-include-exclude.png)
4. No painel **Selecionar grupos**, selecione os grupos do Azure AD que pretende incluir ou excluir da atribuição. Pode manter premida a tecla **Ctrl** para selecionar vários grupos.
4. Quando terminar, no painel **Selecionar grupos**, selecione **Selecionar**.



## <a name="how-to-exclude-groups-from-a-device-profile-assignment"></a>Como excluir grupos de uma atribuição de perfis de dispositivo

Os perfis de configuração de dispositivos do Intune permitem-lhe excluir grupos da atribuição de políticas. Por exemplo, pode atribuir um perfil do dispositivo ao grupo **Todos os utilizadores da empresa**e excluir membros do grupo **Equipa de Direção**.

Ao excluir grupos de uma atribuição, exclua apenas grupos de utilizadores ou apenas grupos de dispositivos, não uma mistura de grupos. O Intune não tem em consideração a associação de utilizadores a dispositivos ao excluir grupos. Incluir grupos de utilizadores e excluir grupos de dispositivos provavelmente não produzirá os resultados de que precisa. Se utilizar grupos misturados ou se existirem outros conflitos, a inclusão terá prioridade sobre a exclusão.

Por exemplo, suponha que pretende atribuir um perfil do dispositivo a todos os dispositivos na sua organização, exceto a dispositivos de local público. Deve incluir o grupo **Todos os Utilizadores** e excluir o grupo **Todos os Dispositivos**.

Neste caso, a política será aplicada a todos os utilizadores e aos respetivos dispositivos, mesmo que esses dispositivos façam parte do grupo **Todos os Dispositivos**. 

A exclusão só avalia os membros diretos dos grupos e não inclui os dispositivos associados a um utilizador. No entanto, os dispositivos que não estiverem associados a um utilizador não receberão a política, uma vez que não têm associação ao grupo **Todos os Utilizadores**. 

Se incluir o grupo **Todos os Dispositivos** e excluir **Todos os Utilizadores**, todos os dispositivos irão receber a política. Neste caso, o objetivo é excluir desta política os dispositivos que tiverem um utilizador associado. No entanto, tal não acontece porque a funcionalidade de exclusão só compara membros diretos do grupo. 

>[!Tip]
>As exclusões não estão atualmente disponíveis para políticas de conformidade ou atribuições da aplicação. Para excluir membros de uma atribuição, pode utilizar os objetivos de atribuição Disponível e Não aplicável. Por exemplo, pode atribuir uma aplicação ao grupo **Todos os utilizadores da empresa** com o objetivo **Disponível** e ao grupo **Equipa de Direção** com o objetivo **Não aplicável**. A aplicação é atribuída a todos os utilizadores, *exceto* aos utilizadores no grupo **Equipa de Direção**. Se atribuir a aplicação ao grupo **Todos os utilizadores da empresa** com o objetivo **Necessário**, os utilizadores no grupo **Equipa de Direção** não serão excluídos.
 
    
## <a name="next-steps"></a>Próximos passos
Veja [Como monitorizar perfis de dispositivos](device-profile-monitor.md) para obter informações sobre como controlar as atribuições de perfis de dispositivos.
