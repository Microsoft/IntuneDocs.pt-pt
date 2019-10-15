---
title: Configurar Windows Update para negócios no Microsoft Intune-Azure | Microsoft Docs
description: Atualize as configurações de atualização de software em um perfil para criar um anel de atualização, examinar a conformidade e pausar atualizações em Windows Update para configurações de negócios usando Microsoft Intune em dispositivos Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa8cc396c05150006799c1e9b86ecb63351cdb36
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314712"
---
# <a name="manage-software-updates-in-intune"></a>Gerenciar atualizações de software no Intune

Use o Intune para definir os anéis de atualização que especificam como e quando o Windows como um serviço atualiza seus dispositivos Windows 10. Os anéis de atualização são as políticas que você atribui a grupos de dispositivos. Usando anéis de atualização, você pode criar uma estratégia de atualização que espelhe suas necessidades de negócios. Para obter mais informações, consulte [gerenciar atualizações usando o Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

Com o Windows 10, novas atualizações de recursos e atualizações de qualidade incluem o conteúdo de todas as atualizações anteriores. Contanto que tenha instalado a atualização mais recente, você sabe que seus dispositivos Windows 10 estão atualizados. Ao contrário das versões anteriores do Windows, agora você deve instalar toda a atualização em vez de fazer parte de uma atualização.


Usando o Windows Update for Business, você simplifica a experiência de gerenciamento de atualizações. Você não precisa aprovar atualizações individuais para grupos de dispositivos. Você pode gerenciar riscos em seus ambientes Configurando uma estratégia de distribuição de atualização. O Intune fornece a capacidade de [definir configurações de atualização](../windows-update-settings.md) em dispositivos e oferece a capacidade de adiar a instalação da atualização. O Intune não armazena as atualizações, mas apenas a atribuição de política de atualização. Os dispositivos acessam Windows Update diretamente para as atualizações. Essa coleção de configurações que define quando as atualizações do Windows 10 são instaladas é chamada de um *anel de atualização do Windows 10*.

Os anéis de atualização do Windows 10 dão suporte a [marcas de escopo](../fundamentals/scope-tags.md). Você pode usar marcas de escopo com anéis de atualização para ajudá-lo a filtrar e gerenciar conjuntos de configurações que você usa.

## <a name="prerequisites"></a>Pré-requisitos  

Os pré-requisitos a seguir devem ser atendidos para usar as atualizações do Windows para dispositivos Windows 10 no Intune.  

- Os PCs com Windows 10 devem executar pelo menos o Windows 10 pro com a atualização de aniversário do Windows ou posterior (versão 1607 ou posterior)
- O Windows Update dá suporte às seguintes edições do Windows 10:
  - Windows 10
  - Windows 10 Team (para dispositivos Surface Hub)
  - Windows Holographic para empresas  

    O Windows Holographic for Business dá suporte a um subconjunto de configurações para atualizações do Windows, incluindo:
    - **Comportamento de atualização automática**
    - **Atualizações de produtos da Microsoft**
    - **Canal de manutenção**: oferece suporte a opções de canal **semestral** e **canal semianual (direcionado)** . Para obter mais informações, consulte [gerenciar o Windows Holographic](../fundamentals/windows-holographic-for-business.md).  

    > [!NOTE]  
    > **Versões e edições sem suporte**:
    > - Windows 10 Mobile  
    > - Windows 10 Enterprise LTSC. O Windows Update for Business (WUfB) atualmente não dá suporte a versões de *canal de serviço de longo prazo* . Planeje usar métodos alternativos de aplicação de patches, como o WSUS ou o Configuration Manager.  

- Em dispositivos Windows, **comentários & diagnósticos** > **os dados de uso e diagnóstico** devem ser definidos como **básico**, **avançado**ou **completo**.  

  Você pode definir a configuração de *dados de diagnóstico e de uso* para dispositivos Windows 10 manualmente ou usar um perfil de restrição de dispositivo do Intune para Windows 10 e posterior. Se você usar um perfil de restrição de dispositivo, defina a [configuração de restrição de dispositivo](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) de **compartilhar dados de uso** para pelo menos **básico**. Essa configuração é encontrada na categoria **relatórios e telemetria** quando você configura uma política de restrição de dispositivo para o Windows 10 ou posterior.

  Para obter mais informações sobre perfis de dispositivo, consulte [definir configurações de restrição de dispositivo](../configuration/device-restrictions-configure.md).  

- Se você usar o portal clássico do Azure, [migre suas configurações para o portal do Azure](#migrate-update-settings-to-the-azure-portal).  


## <a name="create-and-assign-update-rings"></a>Criar e atribuir anéis de atualização

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Selecione **atualizações de Software** > **anéis de atualização do Windows 10** > **criar**.
4. Insira um nome, uma descrição (opcional) e, em seguida, escolha **Configurar**.
5. Em **configurações**, defina as configurações para suas necessidades de negócios. Para obter informações sobre as configurações disponíveis, consulte [configurações do Windows Update](../windows-update-settings.md).  
6. Quando terminar, selecione **OK**. Em **Criar Cadência de Atualizações**, selecione **Criar**. O novo anel de atualização é exibido na lista de anéis de atualização.
7. Para atribuir o anel, na lista de anéis de atualização, selecione um anel e, na guia nome do \<ring >, escolha **atribuições**.
8. Use as guias **incluir** e **excluir** para definir a quais grupos este anel será atribuído e, em seguida, selecione **salvar** para concluir a atribuição.

## <a name="manage-your-windows-10-update-rings"></a>Gerenciar seus anéis de atualização do Windows 10
No portal, você pode selecionar um anel de atualização do Windows 10 para abrir seu painel de **visão geral** . Nesse painel, você pode exibir o status de atribuição de anéis e executar ações adicionais para gerenciar o anel. 
### <a name="to-view-an-updates-rings-overview-pane"></a>Para exibir um painel de visão geral dos anéis de atualizações: 
1. Inicie sessão no Portal do Azure.
2. Navegue até **Intune** > **atualizações de software** > **anéis de atualização do Windows 10**.
3. Selecione o anel de atualização que você deseja exibir ou gerenciar.  

Além de exibir o status de atribuição, você pode selecionar as seguintes ações na parte superior do painel Visão geral para gerenciar o anel de atualização:  
- [Eliminar](#delete)  
- [Temporariamente](#pause)  
- [Volte](#resume)  
- [Estender](#extend)  
- [Desinstalar](#uninstall)  

![Ações disponíveis](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Eliminar  
Selecione **excluir** para parar de impor as configurações do anel de atualização do Windows 10 selecionado. A exclusão de um anel remove sua configuração do Intune para que o Intune não se aplique mais e aplique essas configurações.  

A exclusão de um anel do Intune não modifica as configurações em dispositivos aos quais foi atribuído o anel de atualização.  Em vez disso, o dispositivo mantém suas configurações atuais. Os dispositivos não mantêm um registro histórico de quais configurações foram mantidas anteriormente. Os dispositivos também podem receber configurações de anéis de atualização adicionais que permanecem ativos.  

#### <a name="to-delete-a-ring"></a>Para excluir um anel  
1. Ao exibir a página Visão geral de um anel de atualização, selecione **excluir**.  
2. Selecione **OK**.  

### <a name="pause"></a>Pausa  
Selecione **Pausar** para impedir que os dispositivos atribuídos recebam atualizações de recursos ou atualizações de qualidade por até 35 dias a partir do momento em que você pausar o anel. Depois que o máximo de dias tiver passado, a funcionalidade de pausa expira automaticamente e o dispositivo verifica as atualizações aplicáveis do Windows. Após essa verificação, você pode pausar as atualizações novamente. Se você retomar um anel de atualização em pausa e, em seguida, pausar esse anel novamente, o período de pausa será redefinido para 35 dias.  

#### <a name="to-pause-a-ring"></a>Para pausar um anel  
1. Ao exibir a página Visão geral de um anel de atualização, selecione **Pausar**.  
2. Selecione **recurso** ou **qualidade** para pausar o tipo de atualização e, em seguida, selecione **OK**.  
3. Depois de pausar um tipo de atualização, você pode selecionar pausar novamente para pausar o outro tipo de atualização.  

Quando um tipo de atualização é pausado, o painel de visão geral desse anel exibe o número de dias restantes antes que o tipo de atualização seja retomado.

> [!IMPORTANT]  
> Depois de emitir um comando Pause, os dispositivos receberão esse comando na próxima vez que fizerem check-in no serviço. É possível que, antes de fazer check-in, eles possam instalar uma atualização agendada. Além disso, se um dispositivo de destino for desativado quando você emitir o comando Pause, quando você ativá-lo, ele poderá baixar e instalar as atualizações agendadas antes de fazer check-in no Intune.

### <a name="resume"></a>Retomar  
Enquanto um anel de atualização é pausado, você pode selecionar **retomar** para restaurar as atualizações de recursos e qualidade desse anel para a operação ativa. Depois de retomar um anel de atualização, você pode pausar o anel novamente.  

#### <a name="to-resume-a-ring"></a>Para retomar um anel  
1. Ao exibir a página Visão geral de um anel de atualização em pausa, selecione **retomar**.  
2. Selecione entre as opções disponíveis para retomar as atualizações de **recurso** ou **qualidade** e, em seguida, selecione **OK**.  
3. Depois de retomar um tipo de atualização, você pode selecionar retomar novamente para retomar o outro tipo de atualização.  

### <a name="extend"></a>Expansão  
Enquanto um anel de atualização é pausado, você pode selecionar **estender** para redefinir o período de pausa para as atualizações de recurso e qualidade desse anel de atualização para 35 dias.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>Para estender o período de pausa para um anel  
1. Ao exibir a página Visão geral de um anel de atualização em pausa, selecione **estender**. 
2. Selecione entre as opções disponíveis para retomar as atualizações de **recurso** ou **qualidade** e, em seguida, selecione **OK**.  
3. Depois de estender a pausa para um tipo de atualização, você pode selecionar estender novamente para estender o outro tipo de atualização.  

### <a name="uninstall"></a>Desinstalar  
Um administrador do Intune pode usar a **desinstalação** para desinstalar (reverter) a atualização de *recursos* mais recente ou a atualização de *qualidade* mais recente para um anel de atualização ativo ou em pausa. Após a desinstalação de um tipo, você pode desinstalar o outro tipo. O Intune não dá suporte ou gerencia a capacidade dos usuários de desinstalar atualizações.  

> [!IMPORTANT] 
> Quando você usa a opção de *desinstalação* , o Intune passa a solicitação de desinstalação para os dispositivos imediatamente. 
> - Os dispositivos Windows iniciam a remoção das atualizações assim que recebem a alteração na política do Intune. A remoção da atualização não está limitada a agendamentos de manutenção, mesmo quando elas são configuradas como parte do anel de atualização. 
> - Se a remoção da atualização exigir uma reinicialização do dispositivo, o dispositivo será reiniciado sem oferecer aos usuários do dispositivo uma opção para atrasar.


Para que a desinstalação seja bem-sucedida:  
- Um dispositivo deve executar a atualização do Windows 10 de abril de 2018 (versão 1803) ou posterior.  

Um dispositivo deve ter instalado a atualização mais recente. Como as atualizações são cumulativas, os dispositivos que instalam a atualização mais recente terão o recurso e a atualização de qualidade mais recentes. Um exemplo de quando você pode usar essa opção é reverter a última atualização caso você descubra um problema de interrupção em suas máquinas com Windows 10.  

Ao usar a desinstalação, considere o seguinte:  
- A desinstalação de um recurso ou atualização de qualidade só está disponível para o canal de manutenção no qual o dispositivo está.  

- Usar a desinstalação para atualizações de recursos ou de qualidade dispara uma política para restaurar a atualização anterior em seus computadores com Windows 10.  

- Em um dispositivo Windows 10, depois que uma atualização de qualidade for revertida com êxito, os usuários finais continuarão vendo a atualização listada nas **configurações do Windows** > **atualiza**o**histórico de atualização** > .  

- Para atualizações de recursos especificamente, o tempo que você pode desinstalar a atualização de recurso é limitado de 2-60 dias, conforme configurado pela configuração de atualização de anéis de atualização **definir o período de desinstalação da atualização de recurso (2 a 60 dias)** . Não é possível reverter uma atualização de recurso que foi instalada em um dispositivo após a instalação da atualização do recurso por mais tempo do que o período de desinstalação configurado.  

  Por exemplo, considere um anel de atualização com um período de desinstalação de atualização de recurso de 20 dias. Depois de 25 dias, você decide reverter a atualização de recursos mais recente e usar a opção de desinstalação.  Os dispositivos que instalaram a atualização de recursos há mais de 20 dias não podem desinstalá-lo, pois eles removeram os bits necessários como parte de sua manutenção. No entanto, os dispositivos que instalaram apenas a atualização de recursos até 19 dias atrás poderão desinstalar a atualização se eles fizerem check-in com êxito para receber o comando de desinstalação antes de exceder o período de desinstalação de 20 dias.  

Para obter mais informações sobre políticas de Windows Update, consulte [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) na documentação de gerenciamento de cliente do Windows.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>Para desinstalar a atualização mais recente do Windows 10  
1. Ao exibir a página Visão geral de um anel de atualização em pausa, selecione **desinstalar**.  
2. Selecione entre as opções disponíveis para desinstalar as atualizações de **recurso** ou **qualidade** e, em seguida, selecione **OK**.  
3. Depois de disparar a desinstalação para um tipo de atualização, você pode selecionar desinstalar novamente para desinstalar o tipo de atualização restante.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migrar configurações de atualização para o portal do Azure  
O portal clássico do Azure também tem um número limitado de outras configurações de atualizações do Windows 10 no perfil de configuração do dispositivo. Se você tiver uma dessas configurações configuradas ao migrar para o portal do Azure, é altamente recomendável que você faça as seguintes ações:  

1. Crie anéis de atualização do Windows 10 no portal do Azure com as configurações necessárias. A configuração **permitir recursos de pré-lançamento** não tem suporte no portal do Azure porque ele não é mais aplicável às mais recentes compilações do Windows 10. Você pode definir as outras três configurações, bem como outras configurações de atualizações do Windows 10, ao criar anéis de atualização.  

   > [!NOTE]  
   > As configurações de atualizações do Windows 10 criadas no portal clássico não são exibidas no portal do Azure após a migração. No entanto, essas configurações são aplicadas. Se você migrar qualquer uma dessas configurações e editar a política migrada do portal do Azure, essas configurações serão removidas da política.  

2. Exclua as configurações de atualização no portal clássico. Depois de migrar para o portal do Azure e adicionar as mesmas configurações a um anel de atualização, você deve excluir as configurações no portal clássico para evitar possíveis conflitos de política. Por exemplo, quando a mesma configuração é configurada com valores diferentes, há um conflito. Não há uma maneira fácil de saber porque a configuração configurada no portal clássico não é exibida na portal do Azure.  

## <a name="next-steps"></a>Passos seguintes
[Configurações do Windows Update com suporte pelo Intune](../windows-update-settings.md)  

[Relatórios de conformidade do Intune para atualizações](../windows-update-compliance-reports.md)

[Solução de problemas de anéis de atualização do Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

