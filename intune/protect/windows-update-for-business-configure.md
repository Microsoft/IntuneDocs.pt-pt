---
title: Configurar o Windows Update para Empresas no Microsoft Intune – Azure | Microsoft Docs
description: Gerencie as Atualizações de Software do Windows 10 utilizando os anéis de atualização e a política de atualizações de funcionalidades. Pode rever a conformidade e interromper a instalação da atualização com as definições do Windows Update para as definições de Negócios utilizando o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9245ca028bdb5589df8c76b10560d9130a1108c
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369920"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Gerir atualizações de software do Windows 10 em Intune

Utilize o Intune para gerir a instalação de atualizações de software do Windows 10 a partir do Windows Update for Business.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações. Não precisa de aprovar atualizações individuais de grupos de dispositivos. Pode gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações. Intune fornece a capacidade de [configurar as definições](windows-update-settings.md) de atualização nos dispositivos e dá-lhe a capacidade de adiar a instalação da atualização. Também pode impedir que os dispositivos instalem funcionalidades a partir de novas versões do Windows para ajudar a mantê-las estáveis, permitindo que esses dispositivos continuem a instalar atualizações de qualidade e segurança.

Intune armazena apenas as atribuições políticas de atualização, não as próprias atualizações. Os dispositivos acedem diretamente ao Windows Update para obter as atualizações.

Intune fornece os seguintes tipos de políticas para gerir atualizações:

- Anel de **atualização do Windows 10**: Esta política é uma coleção de definições que configura quando as atualizações do Windows 10 são instaladas.

- **Atualizações de funcionalidades do Windows 10 (pré-visualização pública)** : Esta política traz dispositivos para a versão Windows que especifica e congela a funcionalidade definida nesses dispositivos até optar por atualizá-los para uma versão posterior do Windows.  Embora a versão da funcionalidade permaneça estática, os dispositivos podem continuar a instalar atualizações de qualidade e segurança que estão disponíveis para a sua versão de funcionalidade.

Atribui políticas para os anéis de atualização do Windows 10 e atualizações de funcionalidades do Windows 10 para grupos de dispositivos. Pode utilizar ambos os tipos de políticas no mesmo ambiente Intune para gerir atualizações de software para os seus dispositivos Windows 10 e criar uma estratégia de atualização que espelha as suas necessidades empresariais.

Para obter mais informações, veja [Manage updates using Windows Update for Business (Gerir atualizações através do Windows Update para Empresas)](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Pré-requisitos

Os seguintes pré-requisitos devem ser cumpridos para utilizar as atualizações do Windows para dispositivos Windows 10 em Intune.

- Os PCs do Windows 10 devem executar as seguintes versões do Windows 10:
  - **Os anéis de atualização do Windows 10**: versão 1607 ou posterior
  - **Atualizações de funcionalidades do Windows 10**: versão 1703 ou posterior

- O Windows Update suporta as seguintes edições do Windows 10:
  - Windows 10
  - Equipa do Windows 10 - para dispositivos Surface Hub (não suporta atualizações de *funcionalidades do Windows 10)*
  - Windows Holographic for Business

    O Windows Holographic for Business suporta um subconjunto de definições para atualizações do Windows, incluindo:
    - **Comportamento de atualização automática**
    - **Atualizações de produtos da Microsoft**
    - **Canal de manutenção**: Suporta opções **semi-anuais** de canal e **canal semi-anual (direcionado).** Para mais informações, consulte [Gerir o Windows Holographic](../fundamentals/windows-holographic-for-business.md).

  > [!NOTE]
  > **Versões e edições não suportadas:**
  > - Windows 10 Mobile  
  > - Windows 10 Enterprise LTSC. O Windows Update for Business (WUfB) não suporta atualmente lançamentos do Canal de Serviço de *Longo Prazo.* Planeie utilizar métodos alternativos de correção, como WSUS ou Gestor de Configuração.

- Nos dispositivos Windows, **feedback e diagnóstico > ** os dados de **diagnóstico e utilização** devem ser definidos para **Básico,** **Melhorado**ou **Completo**.

  Pode configurar manualmente a definição de dados de *Diagnóstico e utilização* para dispositivos Windows 10 ou utilizar um perfil de restrição de dispositivos Intune para o Windows 10 e posteriormente. Se utilizar um perfil de restrição do dispositivo, defina a definição de [restrição](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) do dispositivo dos dados de **utilização** do Share para, pelo **menos, Basic**. Esta definição encontra-se na categoria **Reporting and Telemettry** quando configura uma política de restrição de dispositivos para o Windows 10 ou mais tarde.

  Para obter mais informações sobre os perfis de dispositivo, veja [Configurar definições de restrições de dispositivos](../configuration/device-restrictions-configure.md).

## <a name="windows-10-update-rings"></a>Os anéis de atualização do Windows 10

Crie anéis de atualização que especifiquem como e quando o Windows como Serviço atualiza os seus dispositivos Windows 10 com atualizações de Funcionalidade e Qualidade. Com o Windows 10, as novas Atualizações de Funcionalidades e Atualizações de Qualidade incluem os conteúdos de todas as atualizações anteriores. Desde que tenha instalado a mais recente atualização, sabe que os dispositivos do Windows 10 estão atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Os anéis de atualização do Windows 10 suportam [etiquetas](../fundamentals/scope-tags.md)de mira . Pode utilizar etiquetas de âmbito com anéis de atualização para o ajudar a filtrar e gerir conjuntos de configurações que utiliza.

### <a name="create-and-assign-update-rings"></a>Criar e atribuir cadências de atualização

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > os anéis de atualização **do Windows** > **Windows 10** > **Criar**.

3. Em *Basics,* especifique um nome, uma descrição (opcional) e, em seguida, selecione **Next**.
  ![Criar um](./media/windows-update-for-business-configure/basics-tab.png) de anel de atualização

4. Em definições de **anel de atualização,** configure as definições para as suas necessidades de negócio. Para obter informações sobre as definições disponíveis, consulte as definições de [atualização do Windows](../protect/windows-update-settings.md). Depois de configurar as definições de *experiência de Atualização e utilizador,* selecione **Next**.

5. Em **etiquetas de âmbito,** selecione **+ Selecione etiquetas** de âmbito para abrir o painel *De etiquetas Select* se quiser aplicá-las no anel de atualização. Escolha uma ou mais tags e, em seguida, clique em **Select** para adicioná-las ao anel de atualização e voltar à página scope *tags.*

   Quando estiver pronto, selecione **Next** para continuar a *ser atribuições*.

6. Em **Atribuições,** escolha **+ Selecione grupos para incluir** e, em seguida, atribuir o anel de atualização a um ou mais grupos. Utilizar **+ Selecione grupos para excluir** afinar a atribuição. Selecione **Next** para continuar.

7. Em **Review + criar**, reveja as definições e, em seguida, selecione **Criar** quando estiver pronto para guardar o seu anel de atualização do Windows 10. O seu novo anel de atualização está apresentado na lista de anéis de atualização.

### <a name="manage-your-windows-10-update-rings"></a>Gerencie os seus anéis de atualização do Windows 10

No portal, navegue para **Dispositivos** > **Windows** > **Windows 10 Update Rings** e selecione a política que pretende gerir.  A política abre-se para a sua página **de visão geral.**

A partir desta página, pode visualizar o estado de atribuição de anéis e selecionar as seguintes ações a partir do topo do painel de visão geral para gerir o anel de atualização:

- [Eliminar](#delete)
- [Pausa](#pause)
- [Retomar](#resume)
- [Estender](#extend)
- [Desinstalar](#uninstall)

![Ações disponíveis](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Eliminar

**Selecione Eliminar** para parar de impor as definições do anel de atualização do Windows 10 selecionado. A eliminação de um anel remove a sua configuração de Intune para que Intune deixe de aplicar e aplique essas definições.

A abater um anel de Intune não modifica as definições nos dispositivos que foram atribuídos ao anel de atualização.  Em vez disso, o dispositivo mantém as definições atuais. Os dispositivos não mantêm um registo histórico das definições que mantiveram anteriormente. Os dispositivos também podem receber definições de anéis de atualização adicionais que permanecem ativos.

##### <a name="to-delete-a-ring"></a>Para apagar um anel

1. Ao visualizar a página de visão geral para um Anel de Atualização, **selecione Delete**.
2. Selecione **OK**.

#### <a name="pause"></a>Colocar em pausa

Selecione **Pausa** para evitar que os dispositivos atribuídos recebem Atualizações de Funcionalidades ou Atualizações de Qualidade durante 35 dias a partir da hora em que pausa o anel. Após ter decorrido o número máximo de dias, a funcionalidade de pausa expira automaticamente e o dispositivo procura atualizações aplicáveis nas Atualizações do Windows. Após esta procura, pode colocar as atualizações em pausa novamente.
Se retomar um anel de atualização pausado e, em seguida, interromper o anel novamente, o período de pausa repõe-se para 35 dias.

##### <a name="to-pause-a-ring"></a>Para parar um anel

1. Ao visualizar a página de visão geral para um Anel de Atualização, selecione **Pause**.
2. Selecione **funcionalidade** ou **qualidade** para interromper este tipo de atualização e, em seguida, selecione **OK**.
3. Depois de fazer uma pausa num tipo de atualização, pode selecionar pausa novamente para parar o outro tipo de atualização.

Quando um tipo de atualização é interrompido, o painel de visão geral para esse anel mostra quantos dias restam antes de o tipo de atualização recomeçar.

> [!IMPORTANT]
> Depois de emitir um comando de pausa, os dispositivos recebem este comando da próxima vez que entrarem no serviço. É possível que instalem uma atualização agendada antes do registo. Além disso, se um dispositivo de destino for desativado quando emitir o comando de pausa, ao desativá-lo, este poderá transferir e instalar atualizações agendadas antes do registo no Intune.

#### <a name="resume"></a>Retomar

Enquanto um anel de atualização é interrompido, pode selecionar **o Currículo** para restaurar as atualizações de Funcionalidade e Qualidade para esse anel funcionar ativamente. Depois de retomar um anel de atualização, pode interromper o anel novamente.

##### <a name="to-resume-a-ring"></a>Para retomar um anel

1. Ao visualizar a página de visão geral para um anel de atualização pausado, selecione **Resume**.
2. Selecione entre as opções disponíveis para retomar as atualizações **de Funcionalidade** ou **Qualidade** e, em seguida, selecione **OK**.
3. Depois de retomar um tipo de atualização, pode selecionar o Retomar novamente para retomar o outro tipo de atualização.

#### <a name="extend"></a>Estender  

Enquanto um anel de atualização estiver pausado, pode selecionar **Extend** para redefinir o período de pausa para atualizações de Funcionalidade e Qualidade para esse anel de atualização para 35 dias.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>Para prolongar o período de pausa para um anel

1. Ao visualizar a página de visão geral para um anel de atualização pausado, **selecione Extend**.
2. Selecione entre as opções disponíveis para retomar as atualizações **de Funcionalidade** ou **Qualidade** e, em seguida, selecione **OK**.
3. Depois de prolongar a pausa para um tipo de atualização, pode selecionar Extend novamente para alargar o outro tipo de atualização.

#### <a name="uninstall"></a>Desinstalar  

Um administrador intune pode utilizar **desinstalar** para desinstalar (reverter) a mais recente atualização de *funcionalidades* ou a mais recente atualização de *qualidade* para um anel de atualização ativo ou pausado. Depois de desinstalar um tipo, pode então desinstalar o outro tipo. A Intune não suporta nem gere a capacidade dos utilizadores de desinstalarem atualizações.  

> [!IMPORTANT]
> Quando utilizar a opção *Desinstalar,* intune passa imediatamente o pedido de desinstalação para os dispositivos.
>
> - Os dispositivos Windows iniciam a remoção de atualizações assim que recebem a alteração da política Intune. A remoção da atualização não se limita aos horários de manutenção, mesmo quando estão configuradas como parte do anel de atualização.
> - Se a remoção da atualização necessitar de um reinício do dispositivo, o dispositivo reinicia sem oferecer aos utilizadores do dispositivo uma opção para atrasar.

Para que a Desinstalação tenha sucesso:

- Um dispositivo deve ser executado na atualização do Windows 10 de abril de 2018 (versão 1803) ou mais tarde.

Um dispositivo deve ter instalado a última atualização. Como as atualizações são cumulativas, os dispositivos que instalarem a mais recente atualização terão a mais recente funcionalidade e atualização de qualidade. Um exemplo de quando poderá utilizar esta opção é reverter a última atualização caso descubra um problema de rutura nas suas máquinas Windows 10.

Considere o seguinte quando utilizar Desinstalar:

- A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado.

- A utilização de desinstalada para atualizações de funcionalidades ou qualidade desencadeia uma política para restaurar a atualização anterior nas suas máquinas Windows 10.

- Num dispositivo Windows 10, depois de uma atualização de qualidade ser relançada com sucesso, os utilizadores do dispositivo continuam a ver a atualização listada nas **definições do Windows** > **Atualizações** > **Update History**.

- Para atualizações de funcionalidades especificamente, o tempo que pode desinstalar a atualização é limitado de 2 a 60 dias. Este período é configurado pelos anéis de atualização Definição de definição de funcionalidades de **desinstalação (2 - 60 dias)** . Não é possível reverter uma atualização de funcionalidade seletiva que tenha sido instalada num dispositivo depois de a atualização ter sido instalada por mais tempo do que o período de desinstalação configurado.

  Por exemplo, considere um anel de atualização com um período de desinstalação de atualização de funcionalidades de 20 dias. Após 25 dias, decide reverter a última atualização de funcionalidades e utilizar a opção Desinstalar.  Os dispositivos que instalaram a atualização da funcionalidade há mais de 20 dias não podem desinstalá-la, uma vez que removeram as partes necessárias como parte da sua manutenção. No entanto, os dispositivos que apenas instalaram a atualização da funcionalidade até há 19 dias podem desinstalar a atualização se fizerem o check-in com sucesso para receberem o comando de desinstalação antes de excederem o período de desinstalação de 20 dias.

Para obter mais informações sobre as políticas do Windows Update, consulte [o Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) na documentação de gestão do cliente do Windows.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>Para desinstalar a mais recente atualização do Windows 10

1. Ao visualizar a página de visão geral para um anel de atualização pausado, **selecione Desinstalar**.
2. Selecione a partir das opções disponíveis para desinstalar as atualizações **de Funcionalidade** ou **Qualidade** e, em seguida, selecione **OK**.
3. Depois de acionar a desinstalação para um tipo de atualização, pode selecionar Desinstalar novamente para desinstalar o restante tipo de atualização.

## <a name="windows-10-feature-updates"></a>Atualizações de funcionalidades do Windows 10

*Esta funcionalidade está em pré-visualização pública.*

Com as atualizações de *funcionalidades do Windows 10,* selecione a versão de funcionalidade seletiva do Windows que pretende que os dispositivos permaneçam, como a versão 1803 do Windows 1803 ou a versão 1809. Pode definir um nível de característica de 1803 ou mais tarde.

Quando um dispositivo recebe uma política de atualizações de funcionalidades do Windows 10:

- O dispositivo irá atualizar para a versão do Windows especificada na política. Um dispositivo que já executa uma versão posterior do Windows permanece na sua versão atual. Ao congelar a versão, o conjunto de funcionalidades dos dispositivos permanece estável durante a duração da apólice.

- Embora a versão instalada do Windows permaneça definida, os dispositivos ainda podem receber e instalar atualizações de qualidade e segurança para a sua versão Windows durante a duração do suporte para essa versão, o que o ajuda a manter os dispositivos atualizados e seguros.

- Ao contrário de utilizar a *Pause* com um anel de atualização, que expira após 35 dias, a política de atualizações de funcionalidades do Windows 10 mantém-se em vigor. Os dispositivos não instalarão uma nova versão do Windows até modificarou ou remover a política de atualizações da funcionalidade Do Windows 10. Se editar a política para especificar uma versão mais recente, os dispositivos podem então instalar as funcionalidades a partir dessa versão Windows.

### <a name="prerequisites-for-windows-10-feature-updates"></a>Pré-requisitos para atualizações de funcionalidades do Windows 10

Os seguintes pré-requisitos devem ser cumpridos para utilizar as atualizações da funcionalidade do Windows 10 em Intune.

- Os dispositivos devem ser matriculados em Intune MDM e Azure AD aderiu ou Azure AD registado.
- Para utilizar a política de Atualizações de Funcionalidades com O Intune, os dispositivos devem ter telemetria ligada, com uma definição mínima de [*Basic*](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry). A telemetria está configurada no âmbito de *Reporting and Telemettry* como parte de uma política de [restrição](../configuration/device-restrictions-configure.md)de dispositivos.
  
  Os dispositivos que recebem a política de Atualizações de Funcionalidades e que tenham um conjunto de telemetria para *Não configurado*, o que significa que está desligado, poderão instalar uma versão posterior do Windows do que definida na política de Atualização de Funcionalidades. O pré-requisito para exigir telemetria está em revisão à medida que esta funcionalidade avança para a disponibilidade geral.

### <a name="limitations-for-windows-10-feature-updates"></a>Limitações para atualizações de funcionalidades do Windows 10

- Quando implementar uma política de atualização de *funcionalidades do Windows 10* para um dispositivo que também recebe uma política de anéis de *atualização do Windows 10,* reveja o anel de atualização para as seguintes configurações:
  - O período de diferimento da **atualização da funcionalidade (dias)** deve ser definido para **0**.
  - As atualizações de funcionalidades para o anel de atualização devem estar *a ser ressumadas*. Não devem ser pausados.

- As políticas de atualização de funcionalidades do Windows 10 não podem ser aplicadas durante o Autopilot fora da experiência da caixa (OOBE) e só serão aplicadas na primeira análise do Windows Update depois de um dispositivo ter terminado o fornecimento (que normalmente é um dia).

### <a name="create-and-assign-windows-10-feature-updates"></a>Criar e atribuir atualizações de funcionalidades do Windows 10

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **as** atualizações de funcionalidades do Windows > **Windows 10** > **Criar**.

3. Em **Basics,** especifique um nome, uma descrição (opcional) e para a atualização de **funcionalidades ser implementada,** selecione a versão do Windows com o conjunto de funcionalidades que deseja e, em seguida, selecione **Next**.

4. Em **Atribuições,** escolha **+ Selecione grupos para incluir** e, em seguida, atribuir a implementação da atualização de funcionalidades a um ou mais grupos. Selecione **Next** para continuar.

5. Em **Review + criar**, reveja as definições e selecione **Criar** quando estiver pronto para guardar a política de atualizações de funcionalidades do Windows 10.  

### <a name="manage-windows-10-feature-updates"></a>Gerir atualizações de funcionalidades do Windows 10

No centro de administração, vá a **Dispositivos** > **Windows** > as atualizações de **funcionalidades do Windows 10** e selecione a política que pretende gerir. A política abre-se ao seu painel **de visão geral.**

A partir deste painel, pode:

- **Selecione Eliminar** para eliminar a política de Intune e removê-la dos dispositivos.
- Selecione **Propriedades** para modificar a implementação.  No painel *Propriedades,* **selecione Editar** para abrir as *definições de implementação ou atribuições,* onde poderá modificar a implementação.
- Selecione o estado de **atualização do utilizador Final** para visualizar informações sobre a apólice.

## <a name="validation-and-reporting-for-windows-10-updates"></a>Validação e reportagens para atualizações do Windows 10

Para ambos os anéis de atualização do Windows 10 e atualizações de funcionalidades do Windows 10, utilize relatórios de [conformidade intune para atualizações](../windows-update-compliance-reports.md) para monitorizar o estado da atualização dos dispositivos. Esta solução utiliza a Conformidade da [Atualização](https://docs.microsoft.com/windows/deployment/update/update-compliance-monitor) com a sua subscrição Azure.

## <a name="next-steps"></a>Próximos passos

[Definições de atualização do Windows suportadas por Intune](../windows-update-settings.md)

[Problemas de resolução de anéis de atualização do Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)
