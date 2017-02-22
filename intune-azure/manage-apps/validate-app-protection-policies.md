---
title: "Validar as políticas de proteção de aplicações | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: este tópico descreve como pode testar e confirmar se a sua política de proteção de aplicações está corretamente definida e a funcionar conforme esperado."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: e0d5b4b0c3557c1d8158f9e0ea6e33c426dba925


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>Como validar a configuração das políticas de proteção de aplicações

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Este tópico disponibiliza informações sobre como verificar a existência de problemas depois de configurar uma política de proteção de aplicações. Esta orientação aplica-se às políticas de proteção de aplicações na **pré-visualização** do portal do Azure.

### <a name="checking-for-symptoms"></a>Procurar sintomas
É pouco provável que os utilizadores comuniquem problemas, uma vez que a proteção de aplicações é uma ferramenta de proteção de dados. Se existir um problema com a configuração da proteção de aplicações, o utilizador terá acesso sem restrições, tal como teria sem a proteção de aplicações, e não teria conhecimento do problema. Por este motivo, recomendamos que valide a configuração da proteção de aplicações ao controlar as políticas de proteção de aplicações junto de um pequeno grupo de utilizadores que pode testar deliberadamente as restrições da proteção de aplicações.


### <a name="what-to-check"></a>O que verificar

Se os testes mostrarem que o comportamento da política de proteção de aplicações não funciona como previsto, recomendamos que verifique o seguinte:

- Os utilizadores estão licenciados para a proteção de aplicações?
- Os utilizadores estão licenciados para O365?
- O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**.

#### <a name="user-app-protection-status"></a>Estado da proteção de aplicações do utilizador
1. No portal do Azure selecione **Gerir aplicações** > **Monitorizar** >  **Estado dos utilizadores da proteção de aplicações** > **utilizadores**.

2. Selecione um utilizador da lista ou procure e escolha um utilizador e, em seguida, escolha **Selecionar utilizador**. No topo da coluna **Relatórios de aplicação**, verá se o utilizador está licenciado para proteção de aplicações. Abaixo, irá ver se o utilizador está licenciado para O365 e o estado da aplicação para todos os dispositivos do utilizador.



### <a name="what-to-do"></a>O que fazer
Eis as ações a efetuar com base no estado de utilizador:

- Se o utilizador não estiver licenciado para a proteção de aplicações, atribua-lhe uma licença do Intune.
- Se o utilizador não estiver licenciado para O365, obtenha uma licença para o utilizador.
- Se a aplicação de um utilizador estiver listada como **Sem verificação**, confirme que configurou corretamente uma política de proteção de aplicações para essa aplicação.
- Confirme que estas condições são aplicadas em todos os utilizadores aos quais quer aplicar as políticas de proteção de aplicações.

### <a name="see-also"></a>Consulte também

[O que é uma política de proteção de aplicações do Intune?](app-protection-policies.md)



<!--HONumber=Feb17_HO1-->


