---
title: Configure as políticas de atualização de software iOS/iPadOS no Microsoft Intune - Azure Microsoft Docs
description: No Microsoft Intune, crie ou adicione uma política de configuração para restringir quando as atualizações de software se instalarem automaticamente em dispositivos iOS/iPadOS. Pode selecionar as datas e as horas em que as atualizações não serão instaladas. Também pode atribuir esta política a grupos, utilizadores ou dispositivos e verificar a existência de falhas de instalação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576147"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Adicione políticas de atualização de software iOS/iPadOS em Intune

As políticas de atualização de software permitem-lhe forçar dispositivos iOS/iPadOS supervisionados a instalar automaticamente as atualizações do OS. Os dispositivos supervisionados são aqueles que se matricularam usando o Apple Business Manager ou apple school manager. Ao configurar uma política para implementar atualizações, pode:

- Opte por implementar a *mais recente atualização* que está disponível ou opte por implementar uma atualização mais antiga pelo número da versão de atualização se não quiser implementar a última atualização. Se optar por implementar uma atualização mais antiga, também deve definir uma política de Configuração do Dispositivo para restringir a visibilidade das atualizações de software.
- Especifique um horário que determina quando a atualização se instala. Os horários podem ser tão simples como instalar atualizações da próxima vez que o dispositivo entrar ou criar intervalos de data e hora durante os quais as atualizações podem instalar ou estar bloqueadas de instalação.

Esta funcionalidade aplica-se a:

- iOS 10.3 e posteriormente (supervisionado)

Por predefinição, os dispositivos check-in com Intune a cada 8 horas. Se uma atualização estiver disponível através de uma política de atualização, o dispositivo descarrega a atualização. Em seguida, o dispositivo instala a atualização após o check-in seguinte dentro da configuração de horário. Embora o processo de atualização não envolva normalmente qualquer interação do utilizador, se o dispositivo tiver uma senha, o utilizador deve inseri-lo para iniciar uma atualização de software. Os perfis não impedem os utilizadores de atualizar manualmente o SO. Os utilizadores podem ser impedidos de atualizar manualmente o S com uma política de configuração de dispositivos para restringir a visibilidade das atualizações de software.

## <a name="configure-the-policy"></a>Configurar a política

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Atualizar as políticas para iOS/iPadOS** > Criar **perfil**.
3. No separador **Basics,** especifique um nome para esta política, especifique uma descrição (opcional) e, em seguida, selecione **Next**.

   ![Separador básico](./media/software-updates-ios/basics-tab.png)

4. No separador de definições de definições de **atualização,** configure o seguinte:

   1. **Selecione versão para instalar**. Pode escolher entre:

      - *Última atualização*: Isto implementa a atualização mais recente mente lançada para iOS/iPadOS.
      - Qualquer versão anterior que esteja disponível na caixa de dropdown. Se selecionar uma versão anterior, também deve implementar uma política de configuração do dispositivo para atrasar a visibilidade das atualizações de software.

   2. **Tipo**de horário : Configure o calendário para esta política:

      - *Atualização no próximo check-in*: A atualização instala-se no dispositivo da próxima vez que verificar com o Intune. Esta é a opção mais simples e não tem configurações adicionais.
      - *Atualização durante o tempo programado*: Configura rumia uma ou mais janelas de tempo durante as quais a atualização será instalada no momento do check-in.
      - *Atualização fora do horário programado*: Configura rumiuma ou mais janelas de tempo durante as quais as atualizações não serão instaladas no momento do check-in.

   3. **Horário semanal**: Se escolher um tipo de horário diferente da *atualização no próximo check-in,* configure as seguintes opções:

      ![Exemplo de seleção para atualizar durante o tempo programado](./media/software-updates-ios/scheduled-time.png)

      - **Fuso**horário : Escolha um fuso horário.
      - **Janela de tempo**: Defina um ou mais blocos de tempo que restringem quando as atualizações instalam. O efeito das seguintes opções depende do tipo 'Agendar' selecionado. Ao usar um dia de início e fim de dia, os blocos noturnos são suportados. As opções incluem:

        - **Dia de início**: Escolha o dia em que começa a janela de horários.
        - **Hora de início**: Escolha o dia da hora quando a janela de horários começar. Por exemplo, se selecionar 5 AM e tiver um tipo de Atualização de Agenda durante o *tempo programado,* 5 AM será o momento em que as atualizações podem começar a instalar. Se escolheu um tipo de Atualização de Agenda *fora de um horário programado,* 5 AM será o início de um período de tempo que as atualizações não podem instalar.
        - **Fim do dia**: Escolha o dia em que termina a janela de horários.
        - **Hora final**: Escolha a hora do dia quando a janela de horário parar. Por exemplo, se selecionar 1 AM e tiver um tipo de Atualização de Agenda durante o *tempo programado,* 1 AM será o momento em que as atualizações já não podem instalar. Se escolheu um tipo de Atualização de Agenda *fora de um horário programado,* 1 AM será o início de um período de tempo que as atualizações podem instalar.

       Se não configurar os horários para iniciar ou terminar, a configuração não resulta em restrições e as atualizações podem ser instaladas a qualquer momento.  

       > [!NOTE]
       > Para atrasar a visibilidade das atualizações de software durante um período específico de tempo nos seus dispositivos iOS/iPadOS supervisionados, configure essas definições nas [Restrições](../configuration/device-restrictions-ios.md#general)do Dispositivo . As políticas de atualização de software sobrepõem-se a quaisquer restrições ao dispositivo. Quando definiu uma política de atualização de software e restrição para atrasar a visibilidade das atualizações de software, o dispositivo força uma atualização de software de acordo com a política. A restrição aplica-se para que os utilizadores não vejam a opção de atualizar o dispositivo em si, e a atualização é impulsionada conforme definido pela sua política de atualização iOS.

   Depois de configurar as definições da *política de atualização,* selecione **Next**.

5. No separador **'Etiquetas Scope',** selecione **+ Selecione etiquetas** de âmbito para abrir o painel *De etiquetas Select* se quiser aplicá-las na política de atualização.

   - No painel **Select tags,** escolha uma ou mais tags e, em seguida, clique **em Selecionar** para adicioná-las à apólice e voltar ao painel de *etiquetas Scope.*

   Quando estiver pronto, selecione **Next** para continuar a *ser atribuições*.

6. No separador **De missões,** escolha **+ Selecione grupos para incluir** e, em seguida, atribuir a política de atualização a um ou mais grupos. Utilizar **+ Selecione grupos para excluir** afinar a atribuição. Quando estiver pronto, selecione **Next** para continuar.

   Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade das atualizações. Esta política também suporta dispositivos sem utilizador.

7. No **separador Review + criar,** reveja as definições e, em seguida, selecione **Criar** quando estiver pronto para guardar a sua política de atualização iOS/iPadOS. A sua nova política encontra-se na lista de políticas de atualização para iOS/iPadOS.

Para obter orientações da equipa de suporte Intune, consulte [A visibilidade do Atraso das atualizações de software em Intune para dispositivos supervisionados](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> A MDM da Apple não lhe permite forçar um dispositivo a instalar atualizações numa determinada hora ou data. Não pode utilizar políticas de atualização de software Intune para desvalorizar a versão S num dispositivo.

## <a name="edit-a-policy"></a>Editar uma política

Pode editar uma política existente, incluindo alterar os tempos restritos:

1. Selecione **Dispositivos** > **Atualizar as políticas para iOS**. Selecione a política que pretende editar.

2. Ao visualizar as políticas **Propriedades**, selecione **Editar** para a página de política que pretende modificar.

   ![Editar uma política](./media/software-updates-ios/edit-policy.png)

3. Depois de introduzir uma alteração, selecione **Review + guarde** > **Guarde** para salvar as suas edificações e volte às políticas *Propriedades*.

> [!NOTE]
> Se o tempo de **início** e **o tempo** de fim estiverem definidos para as 12 da manhã, o Intune não verifica as restrições sobre quando instalar atualizações. Isto significa que quaisquer configurações que tenha para **Tempos Select para evitar** que as instalações da atualização sejam ignoradas, e as atualizações podem ser instaladas a qualquer momento.

## <a name="monitor-device-installation-failures"></a>Monitorizar as falhas de instalação em dispositivos

<!-- 1352223 -->
**As atualizações** de software > Falhas de **instalação para dispositivos iOS** mostram uma lista de dispositivos iOS/iPadOS supervisionados visados por uma política de atualização, tentaram uma atualização e não puderam ser atualizados. Pode ver o estado com o motivo pelo qual cada um dos dispositivos não foi atualizado automaticamente. Os dispositivos atualizados e em bom estado de funcionamento não são apresentados na lista. Os dispositivos atualizados incluem as atualizações mais recentes suportadas pelos mesmos.

## <a name="next-steps"></a>Próximos passos

[Monitorize o seu estado](../configuration/device-profile-monitor.md).
