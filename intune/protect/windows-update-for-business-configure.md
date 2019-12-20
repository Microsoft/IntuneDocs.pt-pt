---
title: Configurar o Windows Update para Empresas no Microsoft Intune – Azure | Microsoft Docs
description: Gerencie as atualizações de software do Windows 10 usando a política de anéis de atualização e atualizações de recursos. Você pode examinar a conformidade e pausar a instalação da atualização com Windows Update para configurações de negócios usando Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ad630eb34b296d7ab77081a1e3063db8dffc64f9
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207456"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Gerenciar atualizações de software do Windows 10 no Intune

Use o Intune para gerenciar a instalação de atualizações de software do Windows 10 do Windows Update for Business.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações. Não precisa de aprovar atualizações individuais de grupos de dispositivos. Pode gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações. O Intune fornece a capacidade de [definir configurações de atualização](windows-update-settings.md) em dispositivos e oferece a capacidade de adiar a instalação da atualização. Você também pode impedir que os dispositivos instalem recursos de novas versões do Windows para ajudar a mantê-los estáveis e, ao mesmo tempo, permitir que esses dispositivos continuem instalando atualizações para qualidade e segurança.

O Intune armazena apenas as atribuições de política de atualização, não as próprias atualizações. Os dispositivos acedem diretamente ao Windows Update para obter as atualizações.

O Intune fornece os seguintes tipos de política para gerenciar atualizações:

- **Anel de atualização do Windows 10**: essa política é uma coleção de configurações que é configurada quando as atualizações do Windows 10 são instaladas.

- **Atualizações de recursos do Windows 10 (visualização pública)**: essa política traz os dispositivos para a versão do Windows que você especifica e congela o conjunto de recursos nesses dispositivos até que você opte por atualizá-los para uma versão posterior do Windows.  Embora a versão do recurso permaneça estática, os dispositivos podem continuar a instalar as atualizações de qualidade e segurança disponíveis para a versão do recurso.

Você atribui políticas para anéis de atualização do Windows 10 e atualizações de recurso do Windows 10 a grupos de dispositivos. Você pode usar ambos os tipos de política no mesmo ambiente do Intune para gerenciar atualizações de software para seus dispositivos Windows 10 e para criar uma estratégia de atualização que espelhe suas necessidades de negócios.

Para obter mais informações, veja [Manage updates using Windows Update for Business (Gerir atualizações através do Windows Update para Empresas)](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Pré-requisitos

Os pré-requisitos a seguir devem ser atendidos para usar as atualizações do Windows para dispositivos Windows 10 no Intune.

- Os PCs com Windows 10 devem executar as seguintes versões do Windows 10:
  - **Anéis de atualização do Windows 10**: versão 1607 ou posterior
  - **Atualizações de recursos do Windows 10**: versão 1703 ou posterior

- O Windows Update dá suporte às seguintes edições do Windows 10:
  - Windows 10
  - Windows 10 Team – para dispositivos Surface Hub (não dá suporte a *atualizações de recurso do Windows 10*)
  - Windows Holographic for Business

    O Windows Holographic for Business dá suporte a um subconjunto de configurações para atualizações do Windows, incluindo:
    - **Comportamento de atualização automática**
    - **Atualizações de produtos da Microsoft**
    - **Canal de manutenção**: oferece suporte a opções de canal **semestral** e **canal semianual (direcionado)** . Para obter mais informações, consulte [gerenciar o Windows Holographic](../fundamentals/windows-holographic-for-business.md).

  > [!NOTE]
  > **Versões e edições sem suporte**:
  > - Windows 10 Mobile  
  > - Windows 10 Enterprise LTSC. O Windows Update for Business (WUfB) atualmente não dá suporte a versões de *canal de serviço de longo prazo* . Planeje usar métodos alternativos de aplicação de patches, como o WSUS ou o Configuration Manager.

- Em dispositivos Windows, os **comentários & diagnósticos** > **dados de diagnóstico e de uso** devem ser definidos como **básico**, **avançado**ou **completo**.  

  Você pode definir a configuração de *dados de diagnóstico e de uso* para dispositivos Windows 10 manualmente ou usar um perfil de restrição de dispositivo do Intune para Windows 10 e posterior. Se você usar um perfil de restrição de dispositivo, defina a [configuração de restrição de dispositivo](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) de **compartilhar dados de uso** para pelo menos **básico**. Essa configuração é encontrada na categoria **relatórios e telemetria** quando você configura uma política de restrição de dispositivo para o Windows 10 ou posterior.

  Para obter mais informações sobre os perfis de dispositivo, veja [Configurar definições de restrições de dispositivos](../configuration/device-restrictions-configure.md).

## <a name="windows-10-update-rings"></a>Anéis de atualização do Windows 10

Crie anéis de atualização que especificam como e quando o Windows como um serviço atualiza seus dispositivos Windows 10 com atualizações de recursos e qualidade. Com o Windows 10, as novas Atualizações de Funcionalidades e Atualizações de Qualidade incluem os conteúdos de todas as atualizações anteriores. Desde que instale a atualização mais recente, pode ter a certeza de que os seus dispositivos com o Windows 10 estão atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Os anéis de atualização do Windows 10 dão suporte a [marcas de escopo](../fundamentals/scope-tags.md). Você pode usar marcas de escopo com anéis de atualização para ajudá-lo a filtrar e gerenciar conjuntos de configurações que você usa.

### <a name="create-and-assign-update-rings"></a>Criar e atribuir cadências de atualização

1. Entre no centro de [Administração do Microsoft Endpoint Manager]( https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > os anéis de atualização **do Windows > ** **Windows 10** > **criar**.

3. Em *noções básicas*, especifique um nome, uma descrição (opcional) e, em seguida, selecione **Avançar**.
  ![criar um anel de atualização]( ./media/windows-update-for-business-configure/basics-tab.png)
  
4. Em **Atualizar configurações de anel**, defina as configurações para suas necessidades de negócios. Para obter informações sobre as configurações disponíveis, consulte Configurações do Windows Update. Depois de definir as configurações *de atualização e experiência do usuário* , selecione **Avançar**.

5. Em **marcas de escopo**, selecione **+ selecionar marcas de escopo** para abrir o painel *selecionar marcas* se desejar aplicá-las ao anel de atualização. Escolha uma ou mais marcas e, em seguida, clique em **selecionar** para adicioná-las ao anel de atualização e retornar à página da *marca de escopo*s.

   Quando estiver pronto, selecione **Avançar** para continuar com as *atribuições*.

6. Em **atribuições**, escolha **+ Selecionar grupos para incluir** e, em seguida, atribua o anel de atualização a um ou mais grupos. Use **+ selecione grupos para excluir** para ajustar a atribuição. Selecione **Avançar** para continuar.

7. Em**revisão + criar**, examine as configurações e, em seguida, selecione **criar** quando estiver pronto para salvar o anel de atualização do Windows 10. O novo anel de atualização é exibido na lista de anéis de atualização.

### <a name="manage-your-windows-10-update-rings"></a>Gerenciar seus anéis de atualização do Windows 10

No portal, navegue até **dispositivos** > os anéis de atualização **do Windows > ** **Windows 10** e selecione a política que você deseja gerenciar.  A política é aberta para sua página de **visão geral** .

Nessa página, você pode exibir o status de atribuição de anéis e selecionar as seguintes ações na parte superior do painel de visão geral para gerenciar o anel de atualização:

- [Eliminar](#delete)
- [Temporariamente](#pause)
- [Volte](#resume)
- [Estender](#extend)
- [Desinstalar](#uninstall)

![Ações disponíveis](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Eliminar

Selecione **excluir** para parar de impor as configurações do anel de atualização do Windows 10 selecionado. A exclusão de um anel remove sua configuração do Intune para que o Intune não se aplique mais e aplique essas configurações.

A exclusão de um anel do Intune não modifica as configurações em dispositivos aos quais foi atribuído o anel de atualização.  Em vez disso, o dispositivo mantém suas configurações atuais. Os dispositivos não mantêm um registro histórico de quais configurações foram mantidas anteriormente. Os dispositivos também podem receber configurações de anéis de atualização adicionais que permanecem ativos.

##### <a name="to-delete-a-ring"></a>Para excluir um anel

1. Ao exibir a página Visão geral de um anel de atualização, selecione **excluir**.
2. Selecione **OK**.

#### <a name="pause"></a>Colocar em pausa

Selecione **Pausar** para impedir que os dispositivos atribuídos recebam atualizações de recursos ou atualizações de qualidade por até 35 dias a partir do momento em que você pausar o anel. Após ter decorrido o número máximo de dias, a funcionalidade de pausa expira automaticamente e o dispositivo procura atualizações aplicáveis nas Atualizações do Windows. Após esta procura, pode colocar as atualizações em pausa novamente.
Se você retomar um anel de atualização em pausa e, em seguida, pausar esse anel novamente, o período de pausa será redefinido para 35 dias.

##### <a name="to-pause-a-ring"></a>Para pausar um anel

1. Ao exibir a página Visão geral de um anel de atualização, selecione **Pausar**.
2. Selecione **recurso** ou **qualidade** para pausar o tipo de atualização e, em seguida, selecione **OK**.
3. Depois de pausar um tipo de atualização, você pode selecionar pausar novamente para pausar o outro tipo de atualização.

Quando um tipo de atualização é pausado, o painel de visão geral desse anel exibe o número de dias restantes antes que o tipo de atualização seja retomado.

> [!IMPORTANT]
> Depois de emitir um comando Pause, os dispositivos receberão esse comando na próxima vez que fizerem check-in no serviço. É possível que instalem uma atualização agendada antes do registo. Além disso, se um dispositivo de destino for desativado quando emitir o comando de pausa, ao desativá-lo, este poderá transferir e instalar atualizações agendadas antes do registo no Intune.

#### <a name="resume"></a>Retomar

Enquanto um anel de atualização é pausado, você pode selecionar **retomar** para restaurar as atualizações de recursos e qualidade desse anel para a operação ativa. Depois de retomar um anel de atualização, você pode pausar o anel novamente.

##### <a name="to-resume-a-ring"></a>Para retomar um anel

1. Ao exibir a página Visão geral de um anel de atualização em pausa, selecione **retomar**.
2. Selecione entre as opções disponíveis para retomar as atualizações de **recurso** ou **qualidade** e, em seguida, selecione **OK**.
3. Depois de retomar um tipo de atualização, você pode selecionar retomar novamente para retomar o outro tipo de atualização.

#### <a name="extend"></a>Estender  

Enquanto um anel de atualização é pausado, você pode selecionar **estender** para redefinir o período de pausa para as atualizações de recurso e qualidade desse anel de atualização para 35 dias.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>Para estender o período de pausa para um anel

1. Ao exibir a página Visão geral de um anel de atualização em pausa, selecione **estender**.
2. Selecione entre as opções disponíveis para retomar as atualizações de **recurso** ou **qualidade** e, em seguida, selecione **OK**.
3. Depois de estender a pausa para um tipo de atualização, você pode selecionar estender novamente para estender o outro tipo de atualização.

#### <a name="uninstall"></a>Desinstalar  

Um administrador do Intune pode usar a **desinstalação** para desinstalar (reverter) a atualização de *recursos* mais recente ou a atualização de *qualidade* mais recente para um anel de atualização ativo ou em pausa. Após a desinstalação de um tipo, você pode desinstalar o outro tipo. O Intune não dá suporte ou gerencia a capacidade dos usuários de desinstalar atualizações.  

> [!IMPORTANT]
> Quando você usa a opção de *desinstalação* , o Intune passa a solicitação de desinstalação para os dispositivos imediatamente.
>
> - Os dispositivos Windows iniciam a remoção das atualizações assim que recebem a alteração na política do Intune. A remoção da atualização não está limitada a agendamentos de manutenção, mesmo quando elas são configuradas como parte do anel de atualização.
> - Se a remoção da atualização exigir uma reinicialização do dispositivo, o dispositivo será reiniciado sem oferecer aos usuários do dispositivo uma opção para atrasar.

Para que a desinstalação seja bem-sucedida:

- Um dispositivo deve executar a atualização do Windows 10 de abril de 2018 (versão 1803) ou posterior.

Um dispositivo deve ter instalado a atualização mais recente. Como as atualizações são cumulativas, os dispositivos que instalam a atualização mais recente terão o recurso e a atualização de qualidade mais recentes. Um exemplo de quando você pode usar essa opção é reverter a última atualização caso você descubra um problema de interrupção em suas máquinas com Windows 10.

Ao usar a desinstalação, considere o seguinte:

- A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado.

- Usar a desinstalação para atualizações de recursos ou de qualidade dispara uma política para restaurar a atualização anterior em seus computadores com Windows 10.

- Em um dispositivo Windows 10, depois que uma atualização de qualidade for revertida com êxito, os usuários do dispositivo continuarão vendo a atualização listada nas **configurações do Windows** > **atualizações** > **histórico de atualizações**.

- Para atualizações de recursos especificamente, o tempo que você pode desinstalar a atualização é limitado de 2-60 dias. Esse período é configurado pela configuração de atualização de anéis de atualização **definir período de desinstalação de atualização de recurso (2 a 60 dias)**. Não é possível reverter uma atualização de recurso que foi instalada em um dispositivo depois que a atualização tiver sido instalada por mais tempo do que o período de desinstalação configurado.

  Por exemplo, considere um anel de atualização com um período de desinstalação de atualização de recurso de 20 dias. Depois de 25 dias, você decide reverter a atualização de recursos mais recente e usar a opção de desinstalação.  Os dispositivos que instalaram a atualização de recursos há mais de 20 dias não podem desinstalá-lo, pois eles removeram os bits necessários como parte de sua manutenção. No entanto, os dispositivos que instalaram apenas a atualização de recursos até 19 dias atrás poderão desinstalar a atualização se eles fizerem check-in com êxito para receber o comando de desinstalação antes de exceder o período de desinstalação de 20 dias.

Para obter mais informações sobre políticas de Windows Update, consulte [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) na documentação de gerenciamento de cliente do Windows.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>Para desinstalar a atualização mais recente do Windows 10

1. Ao exibir a página Visão geral de um anel de atualização em pausa, selecione **desinstalar**.
2. Selecione entre as opções disponíveis para desinstalar as atualizações de **recurso** ou **qualidade** e, em seguida, selecione **OK**.
3. Depois de disparar a desinstalação para um tipo de atualização, você pode selecionar desinstalar novamente para desinstalar o tipo de atualização restante.

## <a name="windows-10-feature-updates"></a>Atualizações de recursos do Windows 10

*Este recurso está em visualização pública.*

Com *as atualizações de recursos do Windows 10*, você seleciona a versão do recurso do Windows na qual deseja que os dispositivos permaneçam, como o Windows 10 versão 1803 ou 1809. Você pode definir um nível de recurso de 1803 ou posterior.

Quando um dispositivo recebe uma política de atualizações de recursos do Windows 10:

- O dispositivo será atualizado para a versão do Windows especificada na política. Um dispositivo que já executa uma versão posterior do Windows permanece em sua versão atual. Ao congelar a versão, o conjunto de recursos de dispositivos permanece estável durante a política.

- Embora a versão instalada do Windows permaneça definida, os dispositivos ainda podem receber e instalar atualizações de qualidade e segurança para a versão do Windows durante o suporte para essa versão, o que ajuda a manter os dispositivos atuais e seguros.

- Ao contrário do uso de *Pause* com um anel de atualização, que expira após 35 dias, a política de atualizações de recursos do Windows 10 permanece em vigor. Os dispositivos não instalarão uma nova versão do Windows até que você modifique ou remova a política de atualizações de recursos do Windows 10. Se você editar a política para especificar uma versão mais recente, os dispositivos poderão instalar os recursos dessa versão do Windows.

### <a name="limitations-for-windows-10-feature-updates"></a>Limitações para atualizações de recursos do Windows 10

- Quando você implanta uma política de *atualização de recursos do Windows 10* em um dispositivo que também recebe uma política de *anel de atualização do Windows 10* , examine o anel de atualização para as seguintes configurações:
  - O **período de adiamento da atualização do recurso (dias)** deve ser definido como **0**.
  - As atualizações de recurso para o anel de atualização devem estar *em execução*. Eles não devem estar em pausa.

- As políticas de atualização de recursos do Windows 10 não podem ser aplicadas durante a OOBE (configuração inicial pelo uso) e serão aplicadas somente na primeira verificação de Windows Update depois que um dispositivo tiver concluído o provisionamento (que normalmente é um dia). Além disso, os dispositivos que foram provisionados com o piloto automático não receberão a política.

  Essa limitação está sendo examinada para ver se ele pode ter suporte no futuro.


### <a name="create-and-assign-windows-10-feature-updates"></a>Criar e atribuir atualizações de recursos do Windows 10

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > atualizações de recurso **do Windows > ** **Windows 10** > **criar**.

3. Em **noções básicas**, especifique um nome, uma descrição (opcional) e para **a atualização do recurso a ser implantada**, selecione a versão do Windows com o conjunto de recursos desejado e, em seguida, selecione **Avançar**.

4. Em **atribuições**, escolha **+ Selecionar grupos para incluir** e, em seguida, atribua a implantação de atualização de recurso a um ou mais grupos. Selecione **Avançar** para continuar.

5. Em **revisão + criar**, examine as configurações e selecione **criar** quando estiver pronto para salvar a política de atualizações de recursos do Windows 10.  

### <a name="manage-windows-10-feature-updates"></a>Gerenciar atualizações de recursos do Windows 10

No centro de administração, vá para **dispositivos** > atualizações de recursos **do Windows > ** **Windows 10** e selecione a política que você deseja gerenciar. A política é aberta para seu painel de **visão geral** .

Nesse painel, você pode:

- Selecione **excluir** para excluir a política do Intune e removê-la dos dispositivos.
- Selecione **Propriedades** para modificar a implantação.  No painel *Propriedades* , selecione **Editar** para abrir as *configurações ou atribuições de implantação*, onde você pode modificar a implantação.
- Selecione **status de atualização do usuário final** para exibir informações sobre a política.

## <a name="next-steps"></a>Próximos passos

[Configurações do Windows Update com suporte pelo Intune](../windows-update-settings.md)

[Relatórios de conformidade do Intune para atualizações](../windows-update-compliance-reports.md)

[Solução de problemas de anéis de atualização do Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

