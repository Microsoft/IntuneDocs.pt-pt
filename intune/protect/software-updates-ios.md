---
title: Configure iOS software update policies in Microsoft Intune (Configurar as políticas de atualização de software iOS no Microsoft Intune) – Azure | Microsoft Docs
description: No Microsoft Intune, crie ou adicione uma política de configuração para restringir quando as atualizações de software são instaladas automaticamente em dispositivos iOS. Pode selecionar as datas e as horas em que as atualizações não serão instaladas. Também pode atribuir esta política a grupos, utilizadores ou dispositivos e verificar a existência de falhas de instalação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f9750603d19d9b19697c7d2660351c4586432f6
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984184"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Adicionar políticas de atualização de software do iOS no Intune

As políticas de atualização de software permitem-lhe forçar os dispositivos iOS supervisionados a instalarem automaticamente as atualizações de SO disponíveis mais recentes. Ao configurar uma política, pode adicionar os dias e as horas em que não quer que os dispositivos instalem uma atualização.

Esta funcionalidade aplica-se a:

- iOS 10,3 e posterior (supervisionado)

O dispositivo comunica com o Intune aproximadamente de 8 em 8 horas. Se uma atualização estiver disponível, o dispositivo baixará e instalará, exceto durante os horários restritos. Embora o processo de atualização normalmente não envolva nenhuma interação do usuário, se o dispositivo tiver uma senha, o usuário será solicitado a inseri-lo para iniciar uma atualização de software. Isso se aplica ao iOS 10,3 e às versões posteriores. A política não impede um utilizador de atualizar manualmente o SO.

## <a name="configure-the-policy"></a>Configurar a política

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Atualizações de Software** > **Atualizar políticas para iOS** > **Criar**.
3. Na guia **noções básicas** , especifique um nome para essa política, especifique uma descrição (opcional) e, em seguida, selecione **Avançar**.

   ![Guia básico](./media/software-updates-ios/basics-tab.png) 

4. Na guia **Atualizar configurações de política** , especifique um período de tempo restrito quando as atualizações não forem instaladas de modo forçado.  
   - Blocos noturnos não têm suporte e podem não funcionar. Por exemplo, não configure uma política com uma *hora de início* de 8 p.m. e uma *hora de término* de 18:00.
   - Uma política que começa às 12 AM e termina às 12 horas é avaliada como 0 hora e não 24 horas. Essa configuração resulta em nenhuma restrição.

   Ao definir o período de tempo restrito, insira os seguintes detalhes:

   - **Dias**: escolha os dias da semana em que as atualizações não estão instaladas. Por exemplo, verifique segunda-feira, quarta-feira e sexta-feira para impedir que as atualizações sejam instaladas nestes dias.
   - **Fuso horário**: escolha um fuso horário.
   - **Hora de início**: escolha a hora de início do período de tempo restrito. Por exemplo, digite 5 para que as atualizações não sejam instaladas a partir das 17:00.
   - **Hora de término**: escolha a hora de término do período de tempo restrito. Por exemplo, digite 1. portanto, as atualizações podem ser instaladas a partir de 1 A.M.
  
   > [!IMPORTANT]  
   > Uma política que tem uma *hora de início* e *hora de término* definida como 12 am é avaliada como 0 hora e não 24 horas. Isso resulta em nenhuma restrição.  
    
   Para atrasar a visibilidade das atualizações de software por um período específico de tempo em seus dispositivos iOS supervisionados, defina essas configurações em [restrições de dispositivo](../configuration/device-restrictions-ios.md#general). As políticas de atualização de software substituem quaisquer restrições de dispositivo. Quando você define uma política de atualização de software e uma restrição para atrasar a visibilidade das atualizações de software, o dispositivo força uma atualização de software de acordo com a política. A restrição se aplica para que os usuários não vejam a opção de atualizar o próprio dispositivo e a atualização seja enviada por push na primeira janela de tempo, conforme definido pela política de atualização do iOS.

   Depois de definir *as configurações de política de atualização*, selecione **Avançar**. 

5. Na guia **marcas de escopo** , selecione **+ selecionar marcas de escopo** para abrir o painel *selecionar marcas* se desejar aplicá-las à política de atualização.
   
   - No painel **selecionar marcas** , escolha uma ou mais marcas e, em seguida, clique em **selecionar** para adicioná-las à política e retornar ao painel de *marcas de escopo* .  

   Quando estiver pronto, selecione **Avançar** para continuar com as *atribuições*.

6. Na guia **atribuições** , escolha **+ Selecionar grupos para incluir** e, em seguida, atribua a política de atualização a um ou mais grupos. Use **+ selecione grupos para excluir** para ajustar a atribuição. Quando estiver pronto, selecione **Avançar** para continuar. 

   Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

7. Na guia **revisar + criar** , examine as configurações e, em seguida, selecione **criar** quando estiver pronto para salvar a política de atualização do Ios. Sua nova política é exibida na lista de políticas de atualização para iOS.


Para obter diretrizes da equipe de suporte do Intune, consulte [atrasar a visibilidade das atualizações de software no Intune para dispositivos supervisionados](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> A MDM da Apple não lhe permite forçar um dispositivo a instalar atualizações numa determinada hora ou data.

## <a name="edit-a-policy"></a>Editar uma política
Você pode editar uma política existente, incluindo a alteração dos horários restritos:

1. Em **atualizações de software**, selecione **Atualizar políticas para IOS** e, em seguida, selecione a política que você deseja editar.

2. Ao exibir as **Propriedades**de políticas, selecione **Editar** para a página de política que você deseja modificar.  
   ![editar uma](./media/software-updates-ios/edit-policy.png) de vigilância   

3. Depois de introduzir uma alteração, selecione **revisar + salvar**  > **salvar** para salvar as edições e retornar às *Propriedades*das políticas.  
 
> [!NOTE]
> Se a **hora de início** e a **hora de término** estiverem definidas como 12 am, o Intune não verificará se há restrições de quando instalar atualizações. Isso significa que as configurações que você tem para **selecionar os horários para evitar que as instalações de atualização** sejam ignoradas e as atualizações podem ser instaladas a qualquer momento.  


## <a name="monitor-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos
<!-- 1352223 -->
**As atualizações de Software** > **falhas de instalação para dispositivos IOS** mostram uma lista de dispositivos IOS supervisionados direcionados por uma política de atualização, tentou uma atualização e não puderam ser atualizadas. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não são apresentados na lista. Os dispositivos atualizados incluem as atualizações mais recentes suportadas pelos mesmos.

## <a name="next-steps"></a>Próximos passos

[Monitore seu status](../configuration/device-profile-monitor.md).
