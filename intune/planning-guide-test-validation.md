---
title: "Teste e validação do Intune"
description: "Os detalhes que precisa de ter em conta quando estiver a testar e validar uma solução do Intune apenas na cloud no seu ambiente."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.openlocfilehash: ddeb71c6a678ff42b5075d65c2bb4e0d89ae47f1
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/11/2017
---
# <a name="intune-testing-and-validation"></a>Teste e validação do Intune

A fase de teste ocorre durante e após a fase de implementação. Precisa de contas de teste, grupos e dispositivos para testar todos os cenários de TI (administrador) e de utilizador final (casos de utilização) necessários que identificou anteriormente.

Recomendamos que incorpore a sua equipa de suporte de TI e de suporte técnico na fase de teste para que seja criada a documentação de suporte e para que a equipa de suporte de TI e de suporte técnico se familiarize com a prestação de suporte do produto. Se um componente ou cenário não funcionar com base nos casos de utilização, certifique-se de que documenta as alterações necessárias e inclui o motivo de uma determinada alteração.

## <a name="before-you-begin"></a>Antes de começar

Recomendamos que documente o seguinte:

-   **Critérios de teste:** identifica os testes de avaliação.

-   **Componentes de estrutura:** estes componentes têm de existir em, pelo menos, um critério de teste.

Se não existir um componente de estrutura em, pelo menos, um critério de teste ajustado a um requisito ou cenário, pondere se o componente de estrutura é necessário ou não. Além disso, certifique-se de que tem os seguintes itens:

-   **Contas:** contas de teste com licenças do EMS e do Office 365 para testar todos os cenários de casos de utilização.

-   **Dispositivos:** dispositivos de teste que podem ser apagados ou repostos para as predefinições de fábrica.

-   **Componentes de integração:** todos os componentes de integração (Certificate Connector, conector de serviços do Intune para o Exchange alojado e conector do Exchange no local do Intune) devem ser instalados e configurados, se necessário.

Poderá ser necessário fazer alterações de estrutura para ultrapassar dificuldades imprevistas. Além disso, todas as alterações de estrutura devem ser documentadas com o motivo de cada alteração. Segue-se um exemplo para ilustrar o que poderá ser uma alteração:

<blockquote>Pode aperceber-se de que não cumpre os requisitos do Serviço de Inscrição de Dispositivos de Rede (NDES) e que os perfis de VPN e Wi-Fi podem ser configurados com uma AC de raiz que satisfaça os mesmos requisitos sem uma implementação do NDES.</blockquote>

Podem ocorrer problemas que necessitem de orientação técnica ou resolução de problemas especializada durante o processo de teste e validação. Recomendamos que contacte a assistência através dos canais de suporte da Microsoft.

-   [Como obter suporte do Intune](get-support.md)

-   [Contactar o suporte assistido por telefone do Microsoft Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>Teste de validação funcional

A validação funcional consiste no teste de cada componente e configuração para determinar se está a funcionar corretamente. Segue-se um exemplo de teste de validação na tabela abaixo.

![Tabela 1, secção 9](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Testes de validação de casos de utilização

Efetue testes de validação de casos de utilização para verificar se os cenários estão completos e funcionais. Existem dois tipos de cenários de casos de utilização: administrador de TI e utilizador final.

### <a name="it-admin"></a>Administrador de TI

Efetue testes de validação de administrador de TI para verificar se as ações administrativas efetuadas num dispositivo ou utilizador funcionam corretamente. Segue-se um exemplo de um cenário de administrador de IT para validação final.

![Tabela 2, secção 9](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>Utilizador final

Efetue testes de validação do utilizador final para verificar se a experiência do utilizador final é a esperada e se é apresentada corretamente em todas as comunicações ao utilizador. É importante verificar se a experiência do utilizador final está correta. Se a validação falhar, pode originar taxas de adoção mais baixas e um maior número de chamadas de suporte técnico.

![Tabela 3, secção 9](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Passos seguintes

Agora que testou e validou os cenários funcionais e de casos de utilização do Intune, está pronto para a [implementação de produção do Intune](planning-guide-rollout-plan.md).

Consulte [recursos adicionais](planning-guide-resources.md) para obter mais informações e modelos de plano.
