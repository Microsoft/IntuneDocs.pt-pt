---
title: Validar a sua configuração das políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como testar se a sua política de proteção de aplicações está configurada e a funcionar corretamente no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9c3e775773ab08721cb3a65858f3d8c8402104f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74563743"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Como validar a configuração das políticas de proteção de aplicações no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Verificar que a sua política de proteção de aplicações está configurada e a funcionar corretamente. Esta orientação aplica-se às políticas de proteção de aplicações no portal do Azure.

## <a name="checking-for-symptoms"></a>Procurar sintomas
É pouco provável que os utilizadores comuniquem problemas, uma vez que a proteção de aplicações é uma ferramenta de proteção de dados. Se existir um problema com a configuração da proteção de aplicações, o utilizador terá acesso sem restrições, tal como teria sem a proteção de aplicações, e não saberia do problema. Por este motivo, recomendamos que valide a configuração da proteção de aplicações ao controlar as políticas de proteção de aplicações junto de um pequeno grupo de utilizadores que pode testar deliberadamente as restrições da proteção de aplicações.

## <a name="what-to-check"></a>O que verificar

Se os testes mostrarem que o comportamento da política de proteção de aplicações não funciona como previsto, verifique os seguintes itens:

- Os utilizadores estão licenciados para a proteção de aplicações?
- Os utilizadores estão licenciados para O365?
- O estado de cada uma das aplicações de proteção dos utilizadores é o previsto? Os estados possíveis para as aplicações são **Verificado** e **Não verificado**.

### <a name="user-app-protection-status"></a>Estado da proteção de aplicações do utilizador
1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **aplicativos** >  **status de proteção do aplicativo**e, em seguida, selecione o bloco **usuários atribuídos** . 
4. Na página **Relatório da aplicação**, selecione **Selecionar utilizador** para abrir uma lista de utilizadores e grupos. 
5. Procure e selecione um utilizador na lista e, em seguida, escolha **Selecionar utilizador**. No parte superior do painel **Relatório da aplicação**, pode ver se o utilizador tem uma licença a proteção de aplicações. Também pode ver se o utilizador tem uma licença do Office 365 e o estado da aplicação de todos os dispositivos do utilizador.

## <a name="what-to-do"></a>O que fazer
Eis as ações a efetuar com base no estado de utilizador:

- Se o utilizador não possuir uma licença para a proteção de aplicações, atribua-lhe uma [licença do Intune](../fundamentals/licenses.md).
- Se o utilizador não possuir uma licença do Office 365, obtenha uma [licença](../fundamentals/licenses.md) para o utilizador.
- Se a aplicação de um utilizador estiver listada com o estado **Sem verificação**, verifique se configurou corretamente uma [política de proteção de aplicações](app-protection-policies-validate.md) para a mesma.
- Confirme que estas condições se aplicam a todos os utilizadores aos quais quer aplicar as [políticas de proteção de aplicações](app-protection-policies-monitor.md).

## <a name="see-also"></a>Consulte também

- [O que é uma política de proteção de aplicações do Intune?](app-protection-policies.md)
- [Licenças que incluem o Intune](../fundamentals/licenses.md)
- [Atribuir licenças aos utilizadores para que estes possam inscrever dispositivos no Intune](../fundamentals/licenses-assign.md)
- [Como validar a configuração das políticas de proteção de aplicações](app-protection-policies-validate.md)
- [Como monitorizar as políticas de proteção de aplicações](app-protection-policies-monitor.md)

