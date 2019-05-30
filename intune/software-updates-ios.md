---
title: Configure iOS software update policies in Microsoft Intune (Configurar as políticas de atualização de software iOS no Microsoft Intune) – Azure | Microsoft Docs
description: Crie ou adicione uma política de configuração no Microsoft Intune para restringir a instalação automática de atualizações de software em dispositivos iOS geridos ou supervisionados pelo Intune. Pode selecionar as datas e as horas em que as atualizações não serão instaladas. Também pode atribuir esta política a grupos, utilizadores ou dispositivos e verificar a existência de falhas de instalação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a5c9dea847ace51c7d6f06cfa43c44beead18f8
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373423"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Adicionar políticas de atualização de software iOS no Intune

As políticas de atualização de software permitem-lhe forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de SO disponíveis mais recentes. Ao configurar uma política, pode adicionar os dias e as horas em que não quer que os dispositivos instalem uma atualização. 

Esta funcionalidade aplica-se a:

- iOS 10.3 ou posterior (supervisionado)

O dispositivo comunica com o Intune aproximadamente de 8 em 8 horas. Se uma atualização estiver disponível num período de tempo não restringido, o dispositivo irá transferir e instalar a atualização de SO mais recente. Não é necessária nenhuma interação do utilizador para atualizar o dispositivo. A política não impede um utilizador de atualizar manualmente o SO.

## <a name="configure-the-policy"></a>Configurar a política

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Atualizações de Software** > **Atualizar políticas para iOS** > **Criar**.
3. Introduza as seguintes definições:

    - **Nome**: Introduza um nome para a política de atualizações de software. Por exemplo, introduza `iOS restricted update times`.
    - **Descrição**: Introduza uma descrição para a sua política. Esta definição é opcional, mas recomendada.

4. Selecione **definições > configurar**. Introduza as seguintes definições:

    - **Selecionar horas para impedir instalações de atualização**: Especifique um intervalo de tempo limitado quando as atualizações a forçar não estão instaladas. 
      - Blocos de dia não são suportados e poderão não funcionar. Por exemplo, não configure uma política com uma *hora de início* de 8 PM e um *hora de fim* de 6 da Manhã.
      - Uma política que começa em 12 AM e termina às 12h, mas é avaliada como 0 horas e não de 24 horas, que resulta em nenhuma restrição.

      Ao definir o período de tempo limitado, introduza os seguintes detalhes:

      - **Dias**: Escolha o dia da semana, quando as atualizações não estiverem instaladas (s). Por exemplo, confira segunda-feira, quarta-feira e sexta-feira para impedir que as atualizações sejam instalados no hoje em dia.
      - **Fuso horário**: Escolha um fuso horário.
      - **Hora de início**: Escolha a hora de início do intervalo de tempo limitado. Por exemplo, introduza 5 AM, para que as atualizações não são instaladas a partir de às 05:00.
      - **Hora de fim**: Escolha a hora de fim do período de tempo limitado. Por exemplo, introduza 1 AM, para que as atualizações podem ser instaladas a partir de 1 AM.

    - **Atrasar a visibilidade das atualizações de software para os usuários finais sem alterações atualizações agendadas (dias)** : 

      **Esta definição movida para [restrições de dispositivos](device-restrictions-ios.md#general). Esta será removida a partir desta localização no portal do**. Para um curto período de tempo, as políticas existentes podem ser alteradas aqui. Depois de sobre um mês, esta definição será removida das políticas existentes.

      Para limitar o impacto, recomendamos:
        - Remova a política existente a partir desta localização no portal.
        - Criar uma nova [política de restrição de dispositivos](device-restrictions-ios.md#general).
        - Segmenta os mesmos utilizadores como a política original.

      Se houver um conflito, esta definição não faz nada *, a menos que* os dois valores são idênticos. Para evitar um conflito, certifique-se de que alterar ou remover a política existente a partir desta localização no portal.
      > [! Importante]  
      > Uma política que tem um *hora de início* e *hora de fim* conjunto até as 12:00 é avaliado como 0 horas e não de 24 horas. Isso resulta em nenhuma restrição.  

5. Selecione **OK** > **criar** para guardar as alterações e criar a política.

O perfil é criado e apresentado na lista de políticas.

Para obter orientações da equipa de suporte do Intune, veja [atrasar a visibilidade das atualizações de software no Intune para dispositivos supervisionados](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> A MDM da Apple não lhe permite forçar um dispositivo a instalar atualizações numa determinada hora ou data.

## <a name="change-the-restricted-times-for-the-policy"></a>Alterar as horas restritas da política

1. Em **Atualizações de Software**, selecione **Atualizar políticas para iOS**.
2. Selecione uma política existente > **Propriedades**.
3. Atualize a hora restrita:

    1. Selecione os dias da semana
    2. Selecione o fuso horário em que esta política é aplicada
    3. Introduza a hora de início e a hora de fim das horas bloqueadas

    > [!NOTE]
    > Se o **hora de início** e **hora de fim** estão ambas definidas como 12h, mas, em seguida, o Intune não verifica para restrições sobre o quando instalar atualizações. Isso significa que quaisquer configurações que tem para **selecione vezes para impedir instalações de atualização** são ignoradas, e as atualizações podem instalar em qualquer altura.  

## <a name="assign-the-policy-to-users"></a>Atribuir uma política de atualização de iOS a utilizadores

As políticas existentes são atribuídas a grupos, utilizadores ou dispositivos. A política é aplicada quando é atribuída.

1. Em **Atualizações de Software**, selecione **Atualizar políticas para iOS**.
2. Selecione uma política existente > **Atribuições**. 
3. Selecione os grupos, utilizadores ou dispositivos do Azure Active Directory a excluir ou incluir nesta política.
4. Selecione **Guardar** para implementar a política aos seus grupos.

Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

## <a name="monitor-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos
<!-- 1352223 -->
**Atualizações de software** > **falhas de instalação para dispositivos iOS** mostra uma lista de iOS supervisionados dispositivos visado por uma política de atualização, tentaram uma atualização e não foi possível atualizar. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não são apresentados na lista. Os dispositivos atualizados incluem as atualizações mais recentes suportadas pelos mesmos.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
