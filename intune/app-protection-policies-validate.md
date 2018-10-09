---
title: Validar a sua configuração das políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como testar se a sua política de proteção de aplicações está configurada e a funcionar corretamente.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cac03f35cdec3c1a4815559abc83108bd27d3472
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231144"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Como validar a configuração das políticas de proteção de aplicações

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verificar que a sua política de proteção de aplicações está configurada e a funcionar corretamente. Esta orientação aplica-se às políticas de proteção de aplicações no portal do Azure.

### <a name="checking-for-symptoms"></a>Procurar sintomas
É pouco provável que os utilizadores comuniquem problemas, uma vez que a proteção de aplicações é uma ferramenta de proteção de dados. Se existir um problema com a configuração da proteção de aplicações, o utilizador terá acesso ilimitado, tal como teria sem a proteção de aplicações, e não saberá que existe um problema. Por este motivo, recomendamos que valide a configuração da proteção de aplicações ao controlar as políticas de proteção de aplicações junto de um pequeno grupo de utilizadores que pode testar deliberadamente as restrições da proteção de aplicações.


### <a name="what-to-check"></a>O que verificar

Se os testes mostrarem que o comportamento da política de proteção de aplicações não funciona como previsto, recomendamos que verifique os seguintes itens:

- Os utilizadores estão licenciados para a proteção de aplicações?
- Os utilizadores estão licenciados para O365?
- O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**.

#### <a name="user-app-protection-status"></a>Estado da proteção de aplicações do utilizador
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
1. Selecione **Gerir aplicações** > **Monitorização** >  **Estado da proteção de aplicações** > **Utilizadores atribuídos**.

2. Selecione um utilizador da lista ou procure e selecione um utilizador. Em seguida, selecione **Selecionar utilizador**. No topo da coluna **Relatório da aplicação**, pode ver se o utilizador está licenciado para proteção de aplicações. Também pode ver se o utilizador está licenciado para o Office 365 e o estado da aplicação para todos os dispositivos do utilizador.



### <a name="what-to-do"></a>O que fazer
Eis as ações a efetuar com base no estado de utilizador:

- Se o utilizador não estiver licenciado para a proteção de aplicações, atribua-lhe uma licença do Intune.
- Se o utilizador não estiver licenciado para O365, obtenha uma licença para o utilizador.
- Se a aplicação de um utilizador estiver listada com o estado **Sem verificação**, verifique se configurou corretamente uma política de proteção de aplicações para a mesma.
- Confirme que estas condições são aplicadas em todos os utilizadores aos quais quer aplicar as políticas de proteção de aplicações.

### <a name="see-also"></a>Consulte também

[O que é uma política de proteção de aplicações do Intune?](app-protection-policies.md)
