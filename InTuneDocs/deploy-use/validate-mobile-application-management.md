---
title: "Validar a configuração de MAM | Documentos da Microsoft"
description: "Este tópico descreve como pode testar e confirmar se a sua política de MAM está corretamente definida e a funcionar conforme esperado."
keywords: 
author: andredm7
ms.author: andredm
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
translationtype: Human Translation
ms.sourcegitcommit: d6ff74f0b46baf384dbdedf13ad75538dd33a089
ms.openlocfilehash: 080d8f4fd4b6e1b53df860f4319b1c199d504c06


---

# <a name="validating-your-mobile-application-management-setup"></a>Validar a configuração de gestão de aplicações móveis

Este tópico fornece informações sobre como verificar a existência de problemas depois de configurar a gestão de aplicações móveis (MAM). Esta orientação aplica-se às políticas de MAM no portal do Azure.

### <a name="checking-for-symptoms"></a>Procurar sintomas
É pouco provável que os utilizadores comuniquem problemas, uma vez que o MAM é uma ferramenta de proteção de dados. Se existir um problema com a configuração de MAM, o utilizador irá ter acesso sem restrições, tal como teria sem MAM, e não teria conhecimento do problema. Por este motivo, recomendamos que valide a configuração de MAM, controlando as políticas de MAM com um pequeno grupo de utilizadores que pode testar deliberadamente as restrições de MAM.


### <a name="what-to-check"></a>O que verificar

Se os testes mostrarem que o comportamento da política de MAM não funciona como previsto, recomendamos que verifique o seguinte:

- Os utilizadores estão licenciados para MAM?
- Os utilizadores estão licenciados para O365?
- O estado de cada uma das aplicações MAM dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**.

#### <a name="user-mam-status"></a>Estado do utilizador de MAM
1. No portal do Azure, escolha **Gestão de aplicações móveis do Intune** > **definições** > **gestão de aplicações** > **Todas as definições** > **Relatórios de aplicação por utilizador** > **utilizadores**.

2. Selecione um utilizador da lista ou procure e escolha um utilizador e, em seguida, escolha **Selecionar utilizador**. No topo da coluna **Relatórios de aplicação**, irá ver se o utilizador está licenciado para MAM. Abaixo, irá ver se o utilizador está licenciado para O365 e o estado da aplicação para todos os dispositivos do utilizador.

![Estado da aplicação para MAM](..\media\ts-mam-user-apps.png)

### <a name="what-to-do"></a>O que fazer
Eis as ações a efetuar com base no estado de utilizador:

- Se o utilizador não estiver licenciado para MAM, atribua uma licença do Intune ao utilizador, conforme descrito em [Gerir licenças do Intune](..\get-started\start-with-a-paid-subscription-to-microsoft-intune.md).
- Se o utilizador não estiver licenciado para O365, obtenha uma licença para o utilizador.
- Se a aplicação de um utilizador estiver listada como **Não verificado**, certifique-se de que configurou corretamente uma política de MAM para essa aplicação.
- Certifique-se de que estas condições são aplicadas em todos os utilizadores aos quais pretende aplicar as políticas de MAM.

### <a name="see-also"></a>Consulte também
[Configurar políticas de gestão de aplicações móveis com o Microsoft Intune](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


