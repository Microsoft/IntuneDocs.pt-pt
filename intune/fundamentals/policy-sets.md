---
title: Conjuntos de políticas
titleSuffix: Microsoft Intune
description: Utilize conjuntos de políticas para agrupar coleções de objetos de gestão no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48bfe727615f5165fc70ed2e08f98f01203dc895
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514834"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Use conjuntos de políticas para agrupar coleções de objetos de gestão

Os conjuntos de políticas permitem criar um conjunto de referências a entidades de gestão já existentes que precisam de ser identificadas, direcionadas e monitorizadas como uma única unidade conceptual. Um conjunto de políticas é uma coleção atribuível de apps, políticas e outros objetos de gestão que criou. A criação de um conjunto de políticas permite-lhe selecionar muitos objetos diferentes ao mesmo tempo e atribuí-los a partir de um único local. À medida que a sua organização muda, pode revisitar um conjunto de políticas para adicionar ou remover os seus objetos e atribuições. Pode utilizar um conjunto de políticas para associar e atribuir objetos existentes, tais como apps, políticas e VPNs num único pacote. 

> [!IMPORTANT]
> Para uma lista de questões conhecidas relacionadas com conjuntos de políticas, [a Política define questões conhecidas.](~/fundamentals/policy-sets.md#policy-sets-known-issues)

Os conjuntos de políticas não substituem os conceitos ou objetos existentes. Pode continuar a atribuir objetos individuais e também pode fazer referência a objetos individuais como parte de um conjunto de políticas. Por conseguinte, quaisquer alterações a esses objetos individuais refletir-se-ão no conjunto de políticas. 

Pode utilizar conjuntos de políticas para:

- Objetos de grupo que precisam ser atribuídos juntos
- Atribuir os requisitos mínimos de configuração da sua organização em todos os dispositivos geridos
- Atribuir aplicações geralmente utilizadas ou relevantes a todos os utilizadores

Pode incluir os seguintes objetos de gestão num conjunto de políticas:
- Aplicações
- Políticas de configuração de aplicações
- Políticas de proteção de aplicações
- Perfis de configuração de dispositivos
- Políticas de conformidade do dispositivo
- Restrições ao tipo de dispositivo
- Perfis de implementação do piloto automático do Windows
- Enrollment status page (Página do estado de inscrição)

Quando se cria um conjunto de políticas, cria-se uma única unidade de atribuição e gere-se associações entre diferentes objetos. Um conjunto de políticas será uma referência a objetos externos a ele. Quaisquer alterações nos objetos incluídos afetarão também o conjunto de políticas. Depois de criar um conjunto de políticas, pode visualizar e editar repetidamente os seus objetos e atribuições. 

> [!NOTE]
> As definições de definições de definições de suporte de definições de suporte Windows, Android, macOS e iOS/iPadOS podem ser atribuídas com plataforma cruzada.

## <a name="how-to-create-a-policy-set"></a>Como criar um conjunto de políticas

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **definições** de política > **conjuntos** de políticas > **criar**.
3. Na página Basics, adicione os **seguintes valores:**
    - **Nome definido pela política** - Forneça um nome para este conjunto de políticas.
    - **Descrição** - Opcionalmente, forneça uma descrição para o conjunto de políticas.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Clique **em Seguir: Gestão de aplicações**.<br>
   Na página de gestão de **aplicações** pode [opcionalmente adicionar aplicações,](~/apps/apps-add.md)políticas de configuração de [aplicações](~/apps/app-configuration-policies-overview.md)e políticas de proteção de [aplicações](~/apps/app-protection-policy.md) ao seu conjunto de políticas. Para obter informações sobre a gestão de apps, consulte o que é a gestão de [aplicações microsoft Intune?](~/apps/app-management.md) 
5. Clique **em Seguir: Gestão do dispositivo**.<br>
   A página de **gestão** do Dispositivo permite-lhe adicionar objetos de gestão de dispositivos ao seu conjunto de políticas, tais como perfis de [configuração](~/configuration/device-profiles.md) do dispositivo e políticas de [conformidade do dispositivo.](~/protect/device-compliance-get-started.md) Certifique-se de incluir todos os objetos associados, tais como outras políticas, certificados e perfis de base de segurança.
6. Clique **em Seguir: Inscrição do dispositivo**.<br>
   A página de **inscrição** do Dispositivo permite-lhe adicionar objetos de inscrição de dispositivos ao seu conjunto de políticas, tais como restrições de [tipo de dispositivo,](~/enrollment/enrollment-restrictions-set.md)perfis de [implementação do Windows Autopilot](~/enrollment/enrollment-autopilot.md)e perfis de página de estado de [inscrição](~/enrollment/windows-enrollment-status.md).
7. Clique **em seguir: Atribuições**.<br>
   A página **De Missões** permite-lhe atribuir o conjunto de políticas aos utilizadores e dispositivos. É importante notar que pode atribuir uma definição de política a um dispositivo, quer o dispositivo seja ou não gerido pela Intune.
8. Clique **em Seguir: Rever + criar** para rever os valores introduzidos para o perfil.
9. Quando terminar, clique em **Criar** a política definida no Intune. 

## <a name="policy-sets-known-issues"></a>Definições políticas questões conhecidas

Os conjuntos políticos, novos para 1910, têm as seguintes questões conhecidas.

- Ao criar um conjunto de políticas, se um administrador de âmbito de aplicação tentar criar um conjunto de políticas sem qualquer etiqueta de âmbito selecionada, ao chegar à página **Review + Criar,** a validação falhará e será apresentado um erro na barra de estado. O administrador deve mudar para uma página diferente no processo e, em seguida, voltar à página **Review + Criar.** Isto permitirá a opção **Criar.**  
 
- Os seguintes tipos de aplicações são atualmente suportados por conjuntos de políticas:
    - aplicação de loja iOS/iPadOS
    - aplicação iOS/iPadOS line-of-business
    - Aplicação de linha de negócios gerida iOS/iPadOS
    - Aplicação da loja Android
    - Aplicativo android line-of-business
    - Aplicativo de linha de negócios gerido android
    - Office 365 ProPlus Suite (Windows 10)
    - Ligação web
    - Aplicativo iOS/iPadOS incorporado
    - Aplicação Android incorporada

- A definição de uma definição de definição de política de **Todos os Utilizadores** para o Perfil **autopiloto** não é suportada.

- Os conjuntos de políticas têm as seguintes restrições de inscrição e questões de Status Page (ESP):
    - As restrições e a ESP não suportam atribuições de grupos virtuais.
    - As restrições e a ESP não apoiam rigorosamente as atribuições de grupos de exclusão. 
    - As restrições e a ESP utilizam uma resolução de conflitos baseada em prioridades. As restrições e a ESP podem não ser aplicadas aos mesmos utilizadores que o resto das cargas de um conjunto de políticas se as restrições e o ESP também forem alvo de restrições prioritárias e de ESP.
    - As restrições por defeito e a ESP não podem ser adicionadas a um conjunto de políticas.

- Os tipos de política do MAM que apoiam os conjuntos de políticas incluem os seguintes: 
    - MAM WIP (Windows) MDM direcionado para a proteção de aplicações geridas 
    - MAM iiOS/iPadOSOS direcionada para a proteção de aplicações geridas
    - MAM Android direcionado para a proteção de aplicações geridas
    - Configuração de aplicações geridas mAM iOS/iPadOS
    - MAM Android direcionado para configuração de aplicativo gerido

- Os tipos de política do MAM que não apoiam os conjuntos de políticas incluem o seguinte: 
    - MAM WIP (Windows) direcionado para a proteção de aplicações geridas

- MAM processa atribuições de definição de políticas como atribuições diretas para os seguintes tipos de políticas:
    - MAM iOS/iPadOS direcionado para a proteção de aplicações geridas
    - MAM Android direcionado para a proteção de aplicações geridas
    - Configuração de aplicações geridas mAM iOS/iPadOS
    - MAM Android direcionado para configuração de aplicativo gerido

    Se uma política for adicionada a um conjunto de políticas que é implementado para um grupo, o grupo mostrar-se-ia diretamente atribuído na carga de trabalho, e não "atribuído através do conjunto de políticas". Como resultado disso, a MAM não processa as supressões de atribuição de grupos provenientes de conjuntos de políticas.

- A MAM não suporta a implementação de **todos os** grupos virtuais de Utilizadores e Todos os **Dispositivos** para quaisquer tipos de políticas.

## <a name="next-steps"></a>Próximos passos

- [Inscreva dispositivos no Microsoft Intune](~/enrollment/index.yml).