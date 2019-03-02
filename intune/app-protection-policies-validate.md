---
title: Validar a sua configuração das políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como testar se a sua política de proteção de aplicações está configurada e a funcionar corretamente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2018
ms.prod: ''
ms.service: microsoft-intune
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2156dc466fa1b49c9bb3886af596b8a2cb0ccc2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57234329"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Como validar a configuração das políticas de proteção de aplicações

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verificar que a sua política de proteção de aplicações está configurada e a funcionar corretamente. Esta orientação aplica-se às políticas de proteção de aplicações no portal do Azure.

## <a name="checking-for-symptoms"></a>Procurar sintomas
É pouco provável que os utilizadores comuniquem problemas, uma vez que a proteção de aplicações é uma ferramenta de proteção de dados. Se houver um problema com a configuração de proteção de aplicações do utilizador tem acesso sem restrições, tal como teria sem a proteção de aplicações e não sabe que existe um problema. Por esse motivo, recomendamos que valide a configuração de proteção de aplicações ao controlar as políticas de proteção de aplicações com um pequeno grupo de utilizadores que pode testar deliberadamente as restrições da proteção de aplicações.


## <a name="what-to-check"></a>O que verificar

Se os testes mostrarem que o comportamento de política de proteção de aplicações não está conforme esperado, verifique os seguintes itens:

- Os utilizadores estão licenciados para a proteção de aplicações?
- Os utilizadores estão licenciados para O365?
- O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**.

### <a name="user-app-protection-status"></a>Estado da proteção de aplicações do utilizador
1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **aplicações de cliente** > **Monitor** >  **estado de proteção de aplicações**e, em seguida, selecione o **utilizadoresatribuídos**mosaico. 
4. Sobre o **relatório da aplicação** página, selecione **selecionar utilizador** para abrir uma lista de utilizadores e grupos. 
5. Procure e selecione um utilizador na lista, em seguida, escolha **selecionar utilizador**. Na parte superior a **relatório da aplicação** painel, pode ver se o utilizador está licenciado para proteção de aplicações. Também pode ver se o usuário tem uma licença para o Office 365 e o estado da aplicação para todos os dispositivos do utilizador.



## <a name="what-to-do"></a>O que fazer
Eis as ações a efetuar com base no estado de utilizador:

- Se o utilizador não está licenciado para proteção de aplicações, atribua uma licença do Intune ao utilizador.
- Se o utilizador não está licenciado para O365, obtenha uma licença do utilizador.
- Se a aplicação de um utilizador estiver listada com o estado **Sem verificação**, verifique se configurou corretamente uma política de proteção de aplicações para a mesma.
- Certifique-se de que estas condições aplicam-se em todos os utilizadores aos quais pretende que as políticas de proteção de aplicações a aplicar.

## <a name="see-also"></a>Consulte também

[O que é uma política de proteção de aplicações do Intune?](app-protection-policies.md)
