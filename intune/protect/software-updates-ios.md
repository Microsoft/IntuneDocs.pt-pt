---
title: Configure as políticas de atualização de software iOS/iPadOS no Microsoft Intune - Azure Microsoft Docs
description: No Microsoft Intune, crie ou adicione uma política de configuração para restringir quando as atualizações de software se instalarem automaticamente em dispositivos iOS/iPadOS. Pode selecionar as datas e as horas em que as atualizações não serão instaladas. Também pode atribuir esta política a grupos, utilizadores ou dispositivos e verificar a existência de falhas de instalação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f977e449bc38aee84262a401b4b238505aa5b8b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514800"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Adicione políticas de atualização de software iOS/iPadOS em Intune

As políticas de atualização de software permitem-lhe forçar os dispositivos iOS/iPadOS supervisionados a instalarem automaticamente a mais recente atualização do OS disponível. Ao configurar uma política, pode adicionar os dias e as horas em que não quer que os dispositivos instalem uma atualização.

Esta funcionalidade aplica-se a:

- iOS 10.3 e posteriormente (supervisionado)

O dispositivo comunica com o Intune aproximadamente de 8 em 8 horas. Se estiver disponível uma atualização, o dispositivo descarrega-a e instala-a, exceto em tempos restritos. Embora o processo de atualização não envolva normalmente qualquer interação do utilizador, se o dispositivo tiver uma senha, o utilizador será obrigado a introduzi-lo para iniciar uma atualização de software. Isto aplica-se às versões iOS 10.3 e posteriores. A política não impede um utilizador de atualizar manualmente o SO.

## <a name="configure-the-policy"></a>Configurar a política

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Atualizar as políticas para o iOS** > **Criar**.
3. No separador **Basics,** especifique um nome para esta política, especifique uma descrição (opcional) e, em seguida, selecione **Next**.

   ![Guia básico](./media/software-updates-ios/basics-tab.png) 

4. No separador de definições de definições de **atualização,** especifique um prazo restrito quando as atualizações não forem instaladas à força.  
   - Os blocos noturnos não são suportados e podem não funcionar. Por exemplo, não configure uma política com um tempo de *início* de 20:00 e um tempo de *fim* de 6 da manhã.
   - Uma política que começa às 12:00 e termina às 12:00 é avaliada como 0 horas e não 24 horas. Esta configuração não resulta em restrições.

   Ao definir o prazo restrito, introduza os seguintes detalhes:

   - **Dias**: Escolha o dia(s) da semana quando as atualizações não estiverem instaladas. Por exemplo, consulte segunda, quarta e sexta-feira para evitar que as atualizações sejam instaladas nestes dias.
   - **Fuso**horário : Escolha um fuso horário.
   - **Início**: Escolha o tempo de início do prazo restrito. Por exemplo, insira 5 AM para que as atualizações não sejam instaladas a partir das 5 da manhã.
   - **Tempo final**: Escolha o tempo final do prazo restrito. Por exemplo, introduza 1 AM para que as atualizações possam ser instaladas a partir da 1 da manhã.
  
   > [!IMPORTANT]  
   > Uma política que tem um tempo de *início* e *fim* definido para 12 horas é avaliada como 0 horas, e não 24 horas. Isto não resulta em restrições.  
    
   Para atrasar a visibilidade das atualizações de software durante um período específico de tempo nos seus dispositivos iOS/iPadOS supervisionados, configure essas definições nas [Restrições](../configuration/device-restrictions-ios.md#general)do Dispositivo . As políticas de atualização de software sobrepõem-se a quaisquer restrições ao dispositivo. Quando definiu uma política de atualização de software e restrição para atrasar a visibilidade das atualizações de software, o dispositivo força uma atualização de software de acordo com a política. A restrição aplica-se para que os utilizadores não vejam a opção de atualizar o dispositivo em si, e a atualização é empurrada no primeiro período, tal como definida pela sua política de atualização do iOS.

   Depois de configurar as definições da *política de atualização,* selecione **Next**. 

5. No separador **'Etiquetas Scope',** selecione **+ Selecione etiquetas** de âmbito para abrir o painel *De etiquetas Select* se quiser aplicá-las na política de atualização.
   
   - No painel **Select tags,** escolha uma ou mais tags e, em seguida, clique **em Selecionar** para adicioná-las à apólice e voltar ao painel de *etiquetas Scope.*  

   Quando estiver pronto, selecione **Next** para continuar a *ser atribuições*.

6. No separador **De missões,** escolha **+ Selecione grupos para incluir** e, em seguida, atribuir a política de atualização a um ou mais grupos. Utilizar **+ Selecione grupos para excluir** afinar a atribuição. Quando estiver pronto, selecione **Next** para continuar. 

   Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

7. No **separador Review + criar,** reveja as definições e, em seguida, selecione **Criar** quando estiver pronto para guardar a sua política de atualização iOS/iPadOS. A sua nova política encontra-se na lista de políticas de atualização para iOS.


Para obter orientações da equipa de suporte Intune, consulte [A visibilidade do Atraso das atualizações de software em Intune para dispositivos supervisionados](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> A MDM da Apple não lhe permite forçar um dispositivo a instalar atualizações numa determinada hora ou data.

## <a name="edit-a-policy"></a>Editar uma política
Pode editar uma política existente, incluindo alterar os tempos restritos:

1. Selecione **Dispositivos** > **Atualizar as políticas para iOS**. Selecione a política que pretende editar.

2. Ao visualizar as políticas **Propriedades**, selecione **Editar** para a página de política que pretende modificar.  
   ![Editar uma](./media/software-updates-ios/edit-policy.png) política   

3. Depois de introduzir uma alteração, selecione **Review + guarde** > **Guarde** para salvar as suas edificações e volte às políticas *Propriedades*.  
 
> [!NOTE]
> Se o tempo de **início** e **o tempo** de fim estiverem definidos para as 12 da manhã, o Intune não verifica as restrições sobre quando instalar atualizações. Isto significa que quaisquer configurações que tenha para **Tempos Select para evitar** que as instalações da atualização sejam ignoradas, e as atualizações podem ser instaladas a qualquer momento.  


## <a name="monitor-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos
<!-- 1352223 -->
**As atualizações** de software > Falhas de **instalação para dispositivos iOS** mostram uma lista de dispositivos iOS/iPadOS supervisionados visados por uma política de atualização, tentaram uma atualização e não puderam ser atualizados. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não são apresentados na lista. Os dispositivos atualizados incluem as atualizações mais recentes suportadas pelos mesmos.

## <a name="next-steps"></a>Próximos passos

[Monitorize o seu estado](../configuration/device-profile-monitor.md).
