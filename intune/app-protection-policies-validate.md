---
title: Validar a sua configuração das políticas de proteção de aplicações
titleSuffix: Microsoft Intune
description: Saiba como configurar a política de proteção de aplicações de teste e a funcionar corretamente no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 760ff85bc31cf66e66a3bf98f7da22d5ce48eee0
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292235"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Como validar a configuração de política de proteção de aplicações no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verificar que a sua política de proteção de aplicações está configurada e a funcionar corretamente. Esta orientação aplica-se às políticas de proteção de aplicações no portal do Azure.

## <a name="checking-for-symptoms"></a>Procurar sintomas
É pouco provável que os utilizadores comuniquem problemas, uma vez que a proteção de aplicações é uma ferramenta de proteção de dados. Se houver um problema com a configuração de proteção de aplicações, o utilizador irá ter acesso sem restrições, à medida que teria sem a proteção de aplicações, e eles não sabem o que problema. Por esse motivo, recomendamos que valide a configuração de proteção de aplicações ao controlar as políticas de proteção de aplicações com um pequeno grupo de utilizadores que pode testar deliberadamente as restrições da proteção de aplicações.

## <a name="what-to-check"></a>O que verificar

Se os testes mostrarem que o comportamento de política de proteção de aplicações não está a funcionar conforme esperado, verifique os seguintes itens:

- Os utilizadores estão licenciados para a proteção de aplicações?
- Os utilizadores estão licenciados para O365?
- É o estado de cada aplicação dos utilizadores da proteção de aplicações, conforme o esperado. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**.

### <a name="user-app-protection-status"></a>Estado da proteção de aplicações do utilizador
1. Inicie sessão no [Portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Selecione **aplicações de cliente** >  **estado de proteção de aplicações**e, em seguida, selecione o **utilizadores atribuídos** mosaico. 
4. Sobre o **relatório da aplicação** página, selecione **selecionar utilizador** para abrir uma lista de utilizadores e grupos. 
5. Procure e selecione um utilizador na lista, em seguida, escolha **selecionar utilizador**. Na parte superior a **relatório da aplicação** painel, pode ver se o utilizador está licenciado para proteção de aplicações. Também pode ver se o usuário tem uma licença para o Office 365 e o estado da aplicação para todos os dispositivos do utilizador.

## <a name="what-to-do"></a>O que fazer
Eis as ações a efetuar com base no estado de utilizador:

- Se o utilizador não está licenciado para proteção de aplicações, atribuir um [licença do Intune](licenses.md) ao usuário.
- Se o utilizador não está licenciado para o Office 365, obter um [licença](licenses.md) para o utilizador.
- Se a aplicação de um utilizador estiver listada como **não verificado**, verifique se configurou corretamente uma [política de proteção de aplicações](app-protection-policies-validate.md) para essa aplicação.
- Certifique-se de que estas condições aplicam-se em todos os utilizadores aos quais pretende [políticas de proteção de aplicações](app-protection-policies-monitor.md) a aplicar.

## <a name="see-also"></a>Consulte também

- [O que é uma política de proteção de aplicações do Intune?](app-protection-policies.md)
- [Licenças que incluem o Intune](licenses.md)
- [Atribuir licenças aos utilizadores para que eles possam inscrever dispositivos no Intune](licenses-assign.md)
- [Como validar a configuração de política de proteção de aplicações](app-protection-policies-validate.md)
- [Como monitorizar as políticas de proteção de aplicações](app-protection-policies-monitor.md)

