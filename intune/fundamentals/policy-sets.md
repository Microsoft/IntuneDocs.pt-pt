---
title: Conjuntos de políticas
titleSuffix: Microsoft Intune
description: Use conjuntos de políticas para agrupar coleções de objetos de gerenciamento no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2019
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
ms.openlocfilehash: e539f44fc9c9b4e7382368c0f3ad9f79bb1c98b1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585877"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Usar conjuntos de políticas para agrupar coleções de objetos de gerenciamento

Os conjuntos de políticas permitem que você crie um pacote de referências a entidades de gerenciamento já existentes que precisam ser identificadas, direcionadas e monitoradas como uma única unidade conceitual. Um conjunto de políticas é uma coleção atribuível de aplicativos, políticas e outros objetos de gerenciamento que você criou. A criação de um conjunto de políticas permite que você selecione vários objetos diferentes ao mesmo tempo e atribua-os de um único lugar. À medida que sua organização for alterada, você poderá revisitar um conjunto de políticas para adicionar ou remover seus objetos e atribuições. Você pode usar uma política definida para associar e atribuir objetos existentes, como aplicativos, políticas e VPNs em um único pacote. 

> [!IMPORTANT]
> Para obter uma lista de problemas conhecidos relacionados a conjuntos de políticas, a [política define problemas conhecidos](~/fundamentals/policy-sets.md#policy-sets-known-issues).

Os conjuntos de políticas não substituem os conceitos ou objetos existentes. Você pode continuar a atribuir objetos individuais e também pode fazer referência a objetos individuais como parte de um conjunto de políticas. Portanto, qualquer alteração nesses objetos individuais será refletida no conjunto de políticas. 

Você pode usar conjuntos de políticas para:

- Agrupar objetos que precisam ser atribuídos juntos
- Atribua os requisitos mínimos de configuração da sua organização em todos os dispositivos gerenciados
- Atribuir aplicativos mais usados ou relevantes a todos os usuários

Você pode incluir os seguintes objetos de gerenciamento em um conjunto de políticas:
- Apps
- Políticas de configuração de aplicações
- Políticas de proteção de aplicações
- Perfis de configuração de dispositivos
- Políticas de conformidade de dispositivo
- Restrições de tipo de dispositivo
- Perfis de implantação do Windows AutoPilot
- Enrollment status page (Página do estado de inscrição)

Ao criar um conjunto de políticas, você cria uma única unidade de atribuição e gerencia associações entre objetos diferentes. Um conjunto de políticas será uma referência a objetos externos a ele. Todas as alterações nos objetos incluídos também afetarão o conjunto de políticas. Depois de criar um conjunto de políticas, você pode exibir e editar seus objetos e atribuições repetidamente. 

> [!NOTE]
> Os conjuntos de políticas dão suporte às configurações do Windows, do Android, do macOS e do iOS e podem ser atribuídas a várias plataformas.

## <a name="how-to-create-a-policy-set"></a>Como criar um conjunto de políticas

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Na folha **Intune** , escolha **conjuntos de políticas** > **conjuntos de políticas** > **criar**.
3. Na página **noções básicas** , adicione os seguintes valores:
    - **Nome do conjunto de políticas** – forneça um nome para esse conjunto de políticas.
    - **Descrição** – opcionalmente, forneça uma descrição para o conjunto de políticas.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Clique em **Avançar: gerenciamento de aplicativos**.<br>
   Na página **Gerenciamento de aplicativos** , opcionalmente, você pode [adicionar aplicativos](~/apps/apps-add.md), [políticas de configuração de aplicativo](~/apps/app-configuration-policies-overview.md)e políticas de proteção de [aplicativo](~/apps/app-protection-policy.md) ao conjunto de políticas. Para obter informações sobre o gerenciamento de aplicativos, consulte [o que é o gerenciamento de aplicativos Microsoft Intune?](~/apps/app-management.md). 
5. Clique em **Avançar: gerenciamento de dispositivo**.<br>
   A página **Gerenciamento de dispositivos** permite adicionar objetos de gerenciamento de dispositivos ao conjunto de políticas, como [perfis de configuração de dispositivo](~/configuration/device-profiles.md) e políticas de conformidade do [dispositivo](~/protect/device-compliance-get-started.md). Certifique-se de incluir todos os objetos associados, como outras políticas, certificados e perfis de linha de base de segurança.
6. Clique em **Avançar: registro de dispositivo**.<br>
   A página de **registro de dispositivo** permite adicionar objetos de registro de dispositivo ao conjunto de políticas, como restrições de [tipo de dispositivo](~/enrollment/enrollment-restrictions-set.md), perfis de [implantação do Windows AutoPilot](~/enrollment/enrollment-autopilot.md)e [perfis de página de status de registro](~/enrollment/windows-enrollment-status.md).
7. Clique em **Avançar: atribuições**.<br>
   A página **atribuições** permite que você atribua a política definida a usuários e dispositivos. É importante observar que você pode atribuir uma política definida a um dispositivo, independentemente de o dispositivo ser gerenciado pelo Intune ou não.
8. Clique em **Avançar: examinar + criar** para examinar os valores inseridos para o perfil.
9. Quando terminar, clique em **criar** para criar a política definida no Intune. 

## <a name="policy-sets-known-issues"></a>Política define problemas conhecidos

Os conjuntos de políticas, novos no 1910, têm os seguintes problemas conhecidos.

- Ao criar um conjunto de políticas, se um administrador com escopo tentar criar um conjunto de políticas sem nenhuma marca de escopo selecionada, ao chegar à página **revisar + criar** , a validação falhará e um erro será exibido na barra de status. O administrador deve alternar para uma página diferente no processo e, em seguida, retornar para a página **revisar + criar** . Isso habilitará a opção **criar** .  
 
- Os seguintes tipos de aplicativo têm suporte atualmente por conjuntos de políticas:
    - Aplicação da loja iOS
    - aplicativo de linha de negócios do iOS
    - Aplicativo de linha de negócios iOS gerenciado
    - Aplicação da loja Android
    - Aplicativo de linha de negócios do Android
    - Aplicativo de linha de negócios Android gerenciado
    - Pacote do Office 365 ProPlus (Windows 10)
    - Link da Web
    - Aplicação iOS incorporada
    - Aplicação Android incorporada

- Não há suporte para a definição de uma atribuição de conjunto de políticas de **todos os usuários** para o **perfil do AutoPilot** .

- Os conjuntos de políticas têm as seguintes restrições de registro e problemas de página de status de registro (ESP):
    - As restrições e o ESP não dão suporte a atribuições de grupo virtual.
    - As restrições e o ESP não dão suporte estritamente a atribuições de grupo de exclusão. 
    - Restrições e ESP usam resolução de conflitos com base em prioridade. As restrições e o ESP podem não ser aplicados aos mesmos usuários que o restante de um conjunto de políticas, se as restrições e o ESP também forem direcionados por uma restrição de prioridade mais alta e ESP.
    - As restrições padrão e a ESP não podem ser adicionadas a um conjunto de políticas.

- Os tipos de política de MAM que dão suporte a conjuntos de políticas incluem o seguinte: 
    - Proteção de aplicativo gerenciado direcionado ao MDM do MAM (Windows) 
    - Proteção de aplicativo gerenciado direcionado para iOS de MAM
    - Proteção de aplicativo gerenciado direcionado para Android do MAM
    - Configuração de aplicativo gerenciado direcionado para iOS de MAM
    - Configuração de aplicativo gerenciado direcionado para Android do MAM

- Os tipos de política de MAM que não dão suporte a conjuntos de políticas incluem o seguinte: 
    - Proteção de aplicativo gerenciado de WIP (Windows) de MAM

- Os processos de MAM definem as atribuições de política como atribuições diretas para os seguintes tipos de política:
    - Proteção de aplicativo gerenciado direcionado para iOS de MAM
    - Proteção de aplicativo gerenciado direcionado para Android do MAM
    - Configuração de aplicativo gerenciado direcionado para iOS de MAM
    - Configuração de aplicativo gerenciado direcionado para Android do MAM

    Se uma política for adicionada a um conjunto de políticas implantado em um grupo, o grupo será exibido como atribuído diretamente na carga de trabalho, não "atribuído por meio do conjunto de políticas". Como resultado disso, o MAM não processa exclusões de atribuição de grupo provenientes de conjuntos de políticas.

- O MAM não oferece suporte à implantação para **todos os usuários** e **todos os** grupos virtuais de dispositivos para qualquer tipo de política.

## <a name="next-steps"></a>Próximos passos

- [Registrar dispositivos no Microsoft Intune](~/enrollment/index.yml).