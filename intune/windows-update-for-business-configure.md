---
title: Configurar o Windows Update para Empresas no Microsoft Intune – Azure | Microsoft Docs
description: Atualize as definições de Atualização de Software num perfil para criar uma cadência de atualização, analise a conformidade e coloque atualizações em pausa nas definições do Windows Update para Empresas através do Microsoft Intune em dispositivos com o Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 184f70aefbdc90c301ef2f97c5a3abb5ac49a4a8
ms.sourcegitcommit: 12f8b7f0bca1baa2c1f68dd6af4f16a4814daa11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737490"
---
# <a name="manage-software-updates-in-intune"></a>Gerir atualizações de software no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Windows como um Serviço é a maneira ideal de atualizar dispositivos com Windows 10. Com o Windows 10, as novas Atualizações de Funcionalidades e Atualizações de Qualidade incluem os conteúdos de todas as atualizações anteriores. Desde que instale a atualização mais recente, pode ter a certeza de que os seus dispositivos com o Windows 10 estão atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações. Não precisa de aprovar atualizações individuais de grupos de dispositivos. Pode gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações. Já o Windows Update certifica-se de que as atualizações são instaladas no momento adequado. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem diretamente ao Windows Update para obter as atualizações. Utilize o Intune para configurar e gerir **cadências de atualização do Windows 10**. Uma cadência de atualização inclui um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Por exemplo, pode configurar as seguintes definições:

- **Canal de manutenção do Windows 10**: Escolha o canal de serviço a partir do qual pretende que os grupos de dispositivos recebam atualizações. Estão disponíveis os seguintes canais: 
  - Via de Atualizações Semianuais
  - Via de Atualizações Semianuais (Direcionada)
  - Windows Insider Fast
  - Windows Insider Slow
  - Versão do Windows Insider 
      
  Para obter detalhes sobre os canais de serviço disponíveis, veja [Overview for Windows as a Service](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels) (Descrição Geral do Windows como um Serviço).
- **Definições de suspensão**: Configure definições de diferimento da atualização para atrasar as instalações de atualização para grupos de dispositivos. Utilize estas definições para testar a sua implementação de atualizações faseada para que possa consultar o progresso ao longo do processo.
- **Colocar em pausa**: Se houver um problema durante a implementação de atualização, é possível adiar a instalação da atualização. 
- **Janela de manutenção**: Configure as horas em que as atualizações podem ser instaladas.
- **Tipo de atualização**: Escolha os tipos de atualizações que são instaladas. Por exemplo, Atualizações de Qualidade, Atualizações de Funcionalidades ou controladores.
- **Comportamento de instalação**: Configura a forma como a atualização é instalada. Por exemplo, o dispositivo reinicia automaticamente após a instalação?
- **Transferência ponto a ponto**: Optar por configurar a transferência ponto a ponto. Se estiver configurada, quando um dispositivo concluir a transferência de uma atualização, os outros dispositivos poderão transferir a atualização a partir desse dispositivo. Esta definição acelera o processo de transferência.

Depois de criar anéis de atualização, atribua-os a grupos de dispositivos. Ao utilizar anéis de atualização, pode criar uma estratégia de atualização que reflete as necessidades da sua empresa. Para obter mais informações, veja [Manage updates using Windows Update for Business (Gerir atualizações através do Windows Update para Empresas)](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Antes de começar

- Para atualizar os PCs com o Windows 10, estes têm de ter, pelo menos, o Windows 10 Pro com a atualização de Aniversário do Windows.

- O Windows Update suporta as seguintes versões do Windows 10:
  - Windows 10
  - Windows 10 Team (para dispositivos Surface Hub)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  Os dispositivos com o Windows 10 Mobile não são suportados.

- Nos dispositivos Windows, a definição **Comentários e diagnósticos** > **Dados de diagnóstico e utilização** tem de ser definida, pelo menos, para **Básico**.

    ![Definição do Windows para os dados de diagnóstico e utilização](./media/telemetry-basic.png)

    Pode configurar esta definição manualmente ou utilizar um perfil do Intune para Windows 10 e posterior (**Restrições do dispositivo** > **Relatórios e Telemetria** > Definir **Partilhar dados de utilização** para, pelo menos, **Básica**). Para obter mais informações sobre os perfis de dispositivo, veja [Configurar definições de restrições de dispositivos](device-restrictions-configure.md).

- O portal clássico do Azure também tem um número limitado de outras definições de atualizações do Windows 10 no perfil de configuração do dispositivo. Se alguma destas definições estiverem configuradas quando migrar para o portal do Azure, recomendamos vivamente que:

  1. No portal do Azure, crie anéis de atualização do Windows 10 com as definições de que precisa. A definição **Permitir funcionalidades de pré-lançamento** não é suportada no portal do Azure, porque já não é aplicável às compilações do Windows 10 mais recentes. Pode configurar as outras definições, bem como outras definições de atualizações do Windows 10, quando cria cadências de atualizações.

   > [!NOTE]
   > As definições das atualizações do Windows 10 criadas no portal clássico não são apresentadas no portal do Azure após a migração. No entanto, estas definições são aplicadas. Se migrar qualquer uma destas definições e editar a política migrada a partir do portal do Azure, estas definições serão removidas da política.

  2. Elimine as definições de atualização no portal clássico. Depois de migrar para o portal do Azure e adicionar as mesmas definições a uma cadência de atualizações, elimine as definições no portal clássico para evitar potenciais conflitos de políticas. Por exemplo, quando a mesma definição está configurada com valores diferentes, não existe um conflito. Não existe uma forma fácil de saber porque é que a definição configurada no portal clássico não está no portal do Azure.

## <a name="create-and-assign-update-rings"></a>Criar e atribuir cadências de atualização

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e, em seguida, selecione **Microsoft Intune**.
2. Selecione **Atualizações de software** > **Cadências de Atualização do Windows 10** > **Criar**.
3. Introduza um nome, uma descrição (opcional) e, em seguida, selecione **Configurar**.
4. Em **Definições**, introduza as seguintes informações:  

   **Definições de atualização**  
   - **Canal de serviço**: Defina o canal a partir do qual o dispositivo recebe atualizações do Windows.
   - **Atualizações de produtos Microsoft**: Opte por verificar a existência de atualizações de aplicações do Microsoft Update.
   - **Controladores do Windows**: Opte por excluir controladores do Windows Update durante as atualizações.
   - **Período de diferimento da atualização de qualidade (dias)**: Introduza o número de dias de diferimento das atualizações de qualidade. Pode diferir a receção destas Atualizações de Qualidade durante um período de 30 dias a partir do seu lançamento.

     Normalmente, as Atualizações de Qualidade são correções e melhorias às funcionalidades do Windows existentes e são publicadas na segunda terça-feira de cada mês. As Atualizações de Qualidade disponíveis através do Windows Update para Empresas só recebem estas atualizações (a versão "beta"), mas há outras atualizações que poderão ser lançadas pela Microsoft em qualquer altura. Pode definir se quer diferir e durante quanto tempo quer diferir a receção de Atualizações de Qualidade depois de estarem disponíveis no Windows Update. Para obter mais informações, veja [Deploy updates using Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb) (Implementar atualizações através do Windows Update para Empresas).

   - **Período de diferimento da atualização de funcionalidades (dias)**: Introduza o número de dias de diferimento das atualizações de funcionalidades. Pode diferir a receção destas Atualizações de Funcionalidades durante um período de 180 dias a partir do seu lançamento.

     Normalmente, as Atualizações de Funcionalidades são novas funcionalidades do Windows. Depois de configurar a definição **Canal de serviço**, pode definir se quer diferir e durante quanto tempo quer diferir a receção de Atualizações de Funcionalidades depois de estarem disponíveis no Windows Update.

     Por exemplo: **Se o canal de manutenção estiver definido para via de atualizações Semianuais (direcionada) e o período de diferimento for 30 dias**: Digamos que atualização de funcionalidades X fica disponível pela primeira publicamente no Windows Update como um canal Semianual (direcionada) em Janeiro. O dispositivo não recebe a atualização até fevereiro – 30 dias mais tarde.

     **Se o canal de manutenção estiver definido para via de atualizações Semianuais e o período de diferimento for 30 dias**: Digamos que a atualização de funcionalidades X fica disponível pela primeira publicamente no Windows Update como um canal Semianual (direcionada) em Janeiro. Quatro meses mais tarde, em abril, a Atualização de Funcionalidades X é lançada na Via de Atualizações Semianuais. O dispositivo recebe a Atualização de Funcionalidades 30 dias após o lançamento na Via de Atualizações Semianuais e é atualizado em maio.  

   **Definições de experiência do utilizador**
   
   - **Comportamento de atualização automática**: Escolha como são instaladas as atualizações automáticas, quando a reiniciar. Para obter mais detalhes, veja [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).

     Uma definição de *repor para predefinição* restaurará as definições de atualização automática original em máquinas do Windows 10 que executam o *atualização de Outubro de 2018* ou posterior.  

     - **Frequência de comportamento automático**: Se selecionou **instalar automaticamente e reiniciar na hora agendada** para o comportamento de atualização, esta definição é apresentada. Utilize esta definição para agendar quando as atualizações são instaladas, incluindo a semana, o dia e a hora.

   - **Verificações de reinício**: Ativado por predefinição. Quando reinicia um dispositivo, existem algumas verificações que ocorrem, incluindo a verificação de utilizadores ativos, níveis de bateria, jogos em execução e mais. Para ignorar estas verificações ao reiniciar um dispositivo, selecione **Ignorar**.

   - **Impedir o utilizador da colocar em pausa atualizações de Windows**: Permitido por predefinição. Utilize esta definição para bloquear ou permitir que os utilizadores para a instalação da atualização de colocar em pausa a *definições* das suas máquinas. 
      
   - **Modo de transferência de otimização de entrega**: Otimização da entrega já não está configurada como parte de uma cadência de atualização do Windows 10 em atualizações de Software. Otimização da entrega está agora definida por meio da configuração do dispositivo. No entanto, as configurações anteriores permanecem disponíveis na consola. Pode remover estas configurações anteriores ao editar que sejam *não configurado*, mas caso contrário, não pode ser modificados. Para evitar conflitos entre políticas novas e antigas, consulte [mover de cadências de atualização existente para a Otimização da entrega](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) e, em seguida, mova as suas definições para um perfil de otimização de entrega. 

5. Quando terminar, selecione **OK**. Em **Criar Cadência de Atualização**, selecione **Criar**.

O novo anel de atualização é apresentado na lista de anéis de atualização.

1. Para atribuir o anel, na lista de anéis de atualização, selecione um anel e, em seguida, no separador <*nome do anel*>, escolha **Atribuições**.
2. No separador seguinte, selecione **Selecionar grupos a incluir** e, em seguida, selecione os grupos para os quais pretende atribuir este anel.
3. Quando tiver terminado, selecione **Selecionar** para concluir a atribuição.

## <a name="update-compliance-reporting"></a>Relatórios de conformidade de atualização
Pode ver a conformidade de atualizações no Intune ou através de uma solução gratuita denominada Conformidade de Atualizações.

### <a name="review-update-compliance-in-intune"></a>Rever a conformidade de atualizações no Intune 
<!-- 1352223 --> Reveja um relatório das políticas para ver o estado de implementação das cadências de atualização do Windows 10 que configurou.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e, em seguida, selecione **Microsoft Intune**.
2. Selecione **Atualizações de software** > **Descrição Geral**. Poderá ver informações gerais sobre o estado de qualquer cadência de atualizações que tenha atribuído.
3. Abra um dos seguintes relatórios:

   **Para todas as cadências de implementação**:  
   1. Em **Atualizações de software** > **Cadências de Atualização do Windows 10**
   2. Na secção **Monitorizar**, selecione **Por estado de implementação da cadência de atualização**.

   **Para cadências de implementação específicas**:  
   1. Em **Atualizações de software** > **Cadências de Atualização do Windows 10**, selecione a cadência de implementação a analisar.
   2. Na secção **Monitorizar**, selecione um dos seguintes relatórios para ver informações mais detalhadas sobre a cadência de atualização:
      - **Estado do dispositivo**
      - **Estado de utilizador**

### <a name="review-update-compliance-using-oms"></a>Rever a conformidade de atualizações com o OMS
Pode monitorizar as implementações de atualizações do Windows 10 através de uma solução gratuita denominada Conformidade de Atualizações. Para obter mais detalhes, veja [Monitor Windows Updates with Update Compliance (Monitorizar Atualizações do Windows com a Compatibilidade da Atualização)](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). Quando utiliza esta solução, pode implementar um ID comercial em qualquer um dos seus dispositivos com o Windows 10 geridos pelo Intune para os quais pretende gerar relatórios sobre a compatibilidade da atualização.

No Intune, pode utilizar as definições de OMA-URI de uma política personalizada para configurar o ID comercial. Para obter mais detalhes, veja [Definições de política do Intune para dispositivos com o Windows 10 no Microsoft Intune](custom-settings-windows-10.md).   

O caminho do OMA-URI (sensível às maiúsculas e minúsculas) para configurar o ID comercial é: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:

- **Nome da definição**: ID comercial do Windows Analytics
- **Descrição da definição**: Configurar soluções comerciais de ID para o Windows Analytics
- **OMA-URI** (sensível às maiúsculas e minúsculas): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Tipo de dados**: Cadeia
- **Valor**: <*utilizar o GUID apresentado no separador Telemetria do Windows na sua área de trabalho OMS*>

![Definição de OMA-URI – Editar Linha](./media/commID-edit.png)

> [!NOTE]
> Para obter mais informações sobre o servidor de DM MS, veja [Fornecedor de serviço de configuração (CSP) do DMClient](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="pause-updates"></a>Colocar atualizações em pausa
Pode colocar em pausa a receção de Atualizações de Funcionalidades ou Atualizações de Qualidade num dispositivo durante um período máximo de 35 dias desde o momento em que colocou as atualizações em pausa. Após ter decorrido o número máximo de dias, a funcionalidade de pausa expira automaticamente e o dispositivo procura atualizações aplicáveis nas Atualizações do Windows. Após esta procura, pode colocar as atualizações em pausa novamente.

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e, em seguida, selecione **Microsoft Intune**.
2. Selecione **Atualizações de software** > **Cadências de Atualização do Windows 10**.
3. Na lista de cadências de atualização, selecione a cadência que pretende colocar em pausa e, em seguida, selecione **...**  > **Colocar Atualização de Qualidade em Pausa** ou **Colocar Atualização de Funcionalidades em Pausa**, dependendo do tipo de atualizações que pretende colocar em pausa.

> [!IMPORTANT]
> Quando emitir um comando de pausa, os dispositivos receberão este comando da próxima vez que se registarem no serviço. É possível que instalem uma atualização agendada antes do registo.
> Além disso, se um dispositivo de destino for desativado quando emitir o comando de pausa, ao desativá-lo, este poderá transferir e instalar atualizações agendadas antes do registo no Intune.

## <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Desinstalar as atualizações de software mais recentes do Windows 10 
Se ocorrer um problema de interrupção em computadores com o Windows 10, pode optar por desinstalar (reverter) a atualização mais recente da funcionalidade ou a atualização de qualidade mais recente. A desinstalação de uma atualização da funcionalidade ou qualidade só está disponível para o canal de serviço onde o dispositivo está ativado. A desinstalação aciona uma política para restaurar a atualização anterior em computadores com Windows 10. Especificamente para atualizações da funcionalidade, pode limitar o tempo de 2 a 60 dias em que pode ser aplicada uma desinstalação da versão mais recente. Para definir opções de desinstalação de atualizações de software:

1. No Intune, selecione **Atualizações de software**.
2. Selecione **Cadências de Atualização do Windows 10** > selecione uma cadência de atualização existente > **Desinstalar**.

> [!NOTE]
> Em computadores com o Windows 10, após a atualização de qualidade ser revertida com êxito, os utilizadores finais continuam a ver a atualização listada em **Definições do Windows** > **Atualizações** > **Histórico de Atualizações**.

## <a name="windows-holographic-for-business-support"></a>Suporte do Windows Holographic for Business

O Windows Holographic for Business suporta as seguintes definições:

- **Comportamento de atualização automática**
- **Atualizações de produtos da Microsoft**
- **Canal de serviço**: Suporta **canal semianual** e **canal semianual (direcionada)** opções
