---
title: Exibir e corrigir dados pessoais
titleSuffix: Microsoft Intune
description: Saiba como exibir e corrigir dados pessoais.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b6ca291f55511be9e88b0ff898d9383691542bf
ms.sourcegitcommit: a2654f3642b43b29ab0e1cbb2dfa2b56aae18d0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72310897"
---
# <a name="view-and-correct-personal-data"></a>Exibir e corrigir dados pessoais

Os administradores do Intune podem exibir alguns dados pessoais com base em suas permissões de acesso, mas somente os usuários finais podem alterar os dados pessoais do dispositivo.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>Exibir dados pessoais

Os administradores podem ver informações pessoais do usuário final em várias folhas na interface do usuário do Intune. Os artigos a seguir explicam quais administradores de informações fazem e não têm acesso:
- [Consulte detalhes do dispositivo](../remote-actions/device-inventory.md) no Intune explica como você pode examinar os detalhes sobre o dispositivo de um usuário final.
- [Monitorar informações e atribuições de aplicativo](../apps/apps-monitor.md) explica como ver detalhes sobre os aplicativos instalados no dispositivo do usuário final.
- O [artigo quais informações minha empresa pode ver quando eu registro meu dispositivo?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) fornece aos usuários finais uma lista de dados que sua empresa pode e não consegue ver. É melhor informar claramente aos usuários que tipo de dados você está coletando e por que está coletando. Este artigo pode ser a primeira etapa dessa transparência.

### <a name="who-can-view-the-data"></a>Quem pode exibir os dados?

A Microsoft usa controles estritos para controlar o acesso aos dados do cliente, concedendo o menor nível de acesso necessário para concluir as tarefas principais e revogar o acesso quando ele não for mais necessário. 

Você pode proteger e controlar o acesso aos dados pessoais do usuário final usando o controle de administração baseado em função (RBAC). Para obter mais informações, consulte [RBAC com Microsoft Intune](../fundamentals/role-based-access-control.md).

Você pode aprender mais sobre as práticas de dados da Microsoft lendo os termos de serviços online e a [política de privacidade do Microsoft Online Services](https://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409). 

## <a name="correct-end-user-personal-data"></a>Corrigir dados pessoais do usuário final

Os administradores não podem atualizar informações específicas do dispositivo ou do aplicativo. Se um usuário final quiser corrigir quaisquer dados pessoais (como o nome do dispositivo), eles deverão fazê-lo diretamente em seu dispositivo. Essas alterações são sincronizadas na próxima vez que se conectarem ao Intune.


## <a name="next-steps"></a>Passos seguintes

Descubra como [auditar, exportar ou excluir](privacy-data-audit-export-delete.md) dados pessoais no Intune.
