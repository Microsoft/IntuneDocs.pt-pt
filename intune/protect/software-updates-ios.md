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
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5313cae6aa903af910471cb79f021e30a3263dd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503722"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Adicionar políticas de atualização de software do iOS no Intune

As políticas de atualização de software permitem-lhe forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de SO disponíveis mais recentes. Ao configurar uma política, pode adicionar os dias e as horas em que não quer que os dispositivos instalem uma atualização.

Esta funcionalidade aplica-se a:

- iOS 10,3 e posterior (supervisionado)

O dispositivo comunica com o Intune aproximadamente de 8 em 8 horas. Se uma atualização estiver disponível num período de tempo não restringido, o dispositivo irá transferir e instalar a atualização de SO mais recente. Não é necessária nenhuma interação do utilizador para atualizar o dispositivo. A política não impede um utilizador de atualizar manualmente o SO.

## <a name="configure-the-policy"></a>Configurar a política

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Atualizações de Software** > **Atualizar políticas para iOS** > **Criar**.
3. Introduza as seguintes definições:

    - **Nome**: Insira um nome para a política de atualizações de software. Por exemplo, introduza `iOS restricted update times`.
    - **Descrição**: Insira uma descrição para a política. Esta definição é opcional, mas recomendada.

4. Selecione **configurações > configurar**. Introduza as seguintes definições:

    - **Selecionar horários para evitar instalações de atualização**: especifique um período de tempo restrito quando as atualizações não forem instaladas de modo forçado.
      - Blocos noturnos não têm suporte e podem não funcionar. Por exemplo, não configure uma política com uma *hora de início* de 8 p.m. e uma *hora de término* de 18:00.
      - Uma política que começa às 12 AM e termina às 12 horas é avaliada como 0 hora e não 24 horas, o que resulta em nenhuma restrição.

      Ao definir o período de tempo restrito, insira os seguintes detalhes:

      - **Dias**: escolha os dias da semana em que as atualizações não estão instaladas. Por exemplo, verifique segunda-feira, quarta-feira e sexta-feira para impedir que as atualizações sejam instaladas nestes dias.
      - **Fuso horário**: escolha um fuso horário.
      - **Hora de início**: escolha a hora de início do período de tempo restrito. Por exemplo, digite 5 para que as atualizações não sejam instaladas a partir das 17:00.
      - **Hora de término**: escolha a hora de término do período de tempo restrito. Por exemplo, digite 1. portanto, as atualizações podem ser instaladas a partir de 1 A.M.

    - **Atrasar a visibilidade das atualizações de software para os usuários finais sem alterar as atualizações agendadas na política de atualização de software (dias)** : 

      \* * Se você quiser atrasar a visibilidade de atualizações de software por um período específico em seus dispositivos iOS supervisionados, defina essas configurações em restrições de [dispositivo](../configuration/device-restrictions-ios.md#general). As políticas de atualização de software substituem quaisquer restrições de dispositivo. Se você tiver ambos definido, a política de atualização de software virá primeiro a cada vez.

      > [!IMPORTANT]  
      > Uma política que tem uma *hora de início* e *hora de término* definida como 12 am é avaliada como 0 hora e não 24 horas. Isso resulta em nenhuma restrição.  

5. Selecione **OK** > **criar** para salvar as alterações e criar a política.

O perfil é criado e apresentado na lista de políticas.

Para obter diretrizes da equipe de suporte do Intune, consulte [atrasar a visibilidade das atualizações de software no Intune para dispositivos supervisionados](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

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
    > Se a **hora de início** e a **hora de término** forem definidas como 12AM, o Intune não verificará se há restrições de quando instalar atualizações. Isso significa que as configurações que você tem para **selecionar os horários para evitar que as instalações de atualização** sejam ignoradas e as atualizações podem ser instaladas a qualquer momento.  

## <a name="assign-the-policy-to-users"></a>Atribuir uma política de atualização de iOS a utilizadores

As políticas existentes são atribuídas a grupos, utilizadores ou dispositivos. A política é aplicada quando é atribuída.

1. Em **Atualizações de Software**, selecione **Atualizar políticas para iOS**.
2. Selecione uma política existente > **Atribuições**.
3. Selecione os grupos, utilizadores ou dispositivos do Azure Active Directory a excluir ou incluir nesta política.
4. Selecione **Guardar** para implementar a política aos seus grupos.

Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

## <a name="monitor-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos
<!-- 1352223 -->
**As atualizações de Software** > **falhas de instalação para dispositivos IOS** mostram uma lista de dispositivos IOS supervisionados direcionados por uma política de atualização, tentou uma atualização e não puderam ser atualizadas. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não são apresentados na lista. Os dispositivos atualizados incluem as atualizações mais recentes suportadas pelos mesmos.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../configuration/device-profile-assign.md) e [monitorize o respetivo estado](../configuration/device-profile-monitor.md).
