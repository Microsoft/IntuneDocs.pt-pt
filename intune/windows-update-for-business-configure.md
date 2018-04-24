---
title: Configurar o Windows Update para Empresas no Microsoft Intune – Azure | Microsoft Docs
description: Atualize as definições de Atualização de Software num perfil para criar uma cadência de atualização, analise a conformidade e coloque atualizações em pausa nas definições do Windows Update para Empresas através do Microsoft Intune em dispositivos com o Windows 10.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: 58a55c9162076af1e2e763a9799c7c1f756d80ce
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="manage-software-updates-in-intune"></a>Gerir atualizações de software no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Windows como um Serviço é a maneira ideal de atualizar dispositivos com o Windows 10. Com o Windows 10, as novas Atualizações de Funcionalidades e Atualizações de Qualidade incluem os conteúdos de todas as atualizações anteriores. Desde que instale a atualização mais recente, pode ter a certeza de que os seus dispositivos com o Windows 10 estão atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações. Não precisa de aprovar atualizações individuais de grupos de dispositivos. Pode gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações. Já o Windows Update certifica-se de que as atualizações são instaladas no momento adequado. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem diretamente ao Windows Update para obter as atualizações. Utilize o Intune para configurar e gerir **cadências de atualização do Windows 10**. Uma cadência de atualização inclui um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Por exemplo, pode configurar as seguintes definições:

- **Canal de Serviço do Windows 10**: selecione o canal de serviço a partir do qual pretende que os grupos de dispositivos recebam as atualizações. Estão disponíveis os seguintes canais: 
  - Via de Atualizações Semianuais
  - Via de Atualizações Semianuais (Direcionada)
  - Windows Insider Fast
  - Windows Insider Slow
  - Versão do Windows Insider 
      
  Para obter detalhes sobre os canais de serviço disponíveis, veja [Overview for Windows as a Service](https://docs.microsoft.com/en-us/windows/deployment/update/waas-overview#servicing-channels) (Descrição Geral do Windows como um Serviço).
- **Definições de Diferimento**: configure as definições de diferimento das atualizações para atrasar as instalações de atualizações para grupos de dispositivos. Utilize estas definições para testar a sua implementação de atualizações faseada para que possa consultar o progresso ao longo do processo.
- **Colocar em pausa**: adie a instalação de atualizações se detetar um problema em qualquer momento durante a implementação das atualizações.
- **Janela de manutenção**: configure as horas nas quais as atualizações possam ser instaladas.
- **Tipo de atualização**: escolha os tipos de atualizações que são instaladas. Por exemplo, Atualizações de Qualidade, Atualizações de Funcionalidades ou controladores.
- **Comportamento da instalação**: esta opção configura a forma como a atualização é instalada. Por exemplo, o dispositivo reinicia automaticamente após a instalação?
- **Transferência ponto a ponto**: pode optar por configurar a transferência ponto a ponto. Se estiver configurada, quando um dispositivo concluir a transferência de uma atualização, os outros dispositivos poderão transferir a atualização a partir desse dispositivo. Esta definição acelera o processo de transferência.

Depois de criar cadências de atualização, atribua-os a grupos de dispositivos. Ao utilizar cadências de atualização, pode criar uma estratégia de atualização que reflete as necessidades da sua empresa. Para obter mais informações, veja [Manage updates using Windows Update for Business (Gerir atualizações através do Windows Update para Empresas)](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Antes de começar

- Para atualizar os PCs com o Windows 10, estes têm de ter, pelo menos, o Windows 10 Pro com a atualização de Aniversário do Windows.

- O Windows Update suporta as seguintes versões do Windows 10:
  - Windows 10
  - Windows 10 Team (para dispositivos Surface Hub)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  Os dispositivos com o Windows 10 Mobile não são suportados.

- Nos dispositivos Windows, a definição **Comentários e diagnósticos** > **Dados de diagnóstico e utilização** tem de ser definida, pelo menos, para **Básico**.

    ![Definição do Windows para os dados de diagnóstico e utilização](./media/telemetry-basic.png)

    Pode configurar esta definição manualmente ou utilizar um perfil de restrição de dispositivos do Intune para o Windows 10 e posterior. Para o fazer, configure a definição **Geral** > **Submissão de dados de diagnóstico**, pelo menos, para **Básico**. Para obter mais informações sobre os perfis de dispositivo, veja [Configurar definições de restrições de dispositivos](device-restrictions-configure.md).

- Na consola de administração do Intune, existem quatro definições que controlam o comportamento das atualizações do software. Estas definições fazem parte da política de configuração geral dos dispositivos móveis e computadores com o Windows 10:
  - **Permitir atualizações automáticas**
  - **Permitir funcionalidades de pré-lançamento**
  - **Agendar Dia da Instalação**
  - **Agendar Hora da Instalação**

  O portal clássico do Azure também tem um número limitado de outras definições de atualizações do Windows 10 no perfil de configuração do dispositivo. Se tiver qualquer uma destas definições configuradas quando migrar para o portal do Azure, recomendamos vivamente que siga o seguinte procedimento:

1. No portal do Azure, crie cadências de atualização do Windows 10 com as definições de que precisa. A definição **Permitir funcionalidades de pré-lançamento** não é suportada no portal do Azure, porque já não é aplicável às compilações do Windows 10 mais recentes. Pode configurar as outras três definições, bem como outras definições de atualizações do Windows 10, quando cria as cadências de atualização.

   > [!NOTE]
   > As definições das atualizações do Windows 10 criadas no portal clássico não são apresentadas no portal do Azure após a migração. No entanto, estas definições são aplicadas. Se migrar qualquer uma destas definições e editar a política migrada a partir do portal do Azure, estas definições serão removidas da política.

2. Elimine as definições de atualização no portal clássico. Depois de migrar para o portal do Azure e adicionar as mesmas definições a uma cadência de atualização, terá de eliminar as definições no portal clássico para evitar potenciais conflitos de políticas. Por exemplo, quando a mesma definição está configurada com valores diferentes, não existe um conflito. Não existe uma forma fácil de saber porque é que a definição configurada no portal clássico não é apresentada no portal do Azure.

## <a name="create-and-assign-update-rings"></a>Criar e atribuir cadências de atualização

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**.
3. Selecione **Atualizações de software** > **Cadências de Atualização do Windows 10** > **Criar**.
4. Introduza um nome, uma descrição (opcional) e, em seguida, selecione **Configurar**.
5. Em **Definições**, introduza as seguintes informações:

   - **Canal de serviço**: defina o canal a partir do qual o dispositivo receberá as atualizações do Windows.
   - **Atualizações de produtos da Microsoft**: selecione a opção para procurar atualizações da aplicação no Microsoft Update.
   - **Controladores do Windows**: opte por excluir os controladores do Windows Update durante as atualizações.
   - **Comportamento da atualização automática**: selecione a forma como são instaladas as atualizações automáticas e quando reiniciar. Para obter mais detalhes, veja [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).
     - **Frequência de comportamento automático**: se selecionar a opção **Instalar automaticamente e reiniciar à hora agendada** para o comportamento da atualização, esta definição é apresentada. Utilize esta definição para agendar quando as atualizações são instaladas, incluindo a semana, o dia e a hora.

   - **Verificações de reinício**: ativado por predefinição. Quando reinicia um dispositivo, existem algumas verificações que ocorrem, incluindo a verificação de utilizadores ativos, níveis de bateria, jogos em execução e mais. Para ignorar estas verificações ao reiniciar um dispositivo, selecione **Ignorar**.

   - **Período de diferimento da atualização de qualidade (dias)**: introduza o número de dias de diferimento das atualizações de qualidade. Pode diferir a receção destas Atualizações de Qualidade durante um período de 30 dias a partir do seu lançamento.

     Normalmente, as Atualizações de Qualidade são correções e melhorias às funcionalidades do Windows existentes e são publicadas na primeira terça-feira de cada mês. No entanto, podem ser lançadas em qualquer altura pela Microsoft. Pode definir se pretende e quanto tempo tem para diferir a receção de Atualizações de Qualidade depois de estarem disponíveis no Windows Update.

   - **Período de diferimento da atualização de funcionalidades (dias)**: introduza o número de dias de diferimento das Atualizações de Funcionalidades. Pode diferir a receção destas Atualizações de Funcionalidades durante um período de 180 dias a partir do seu lançamento.

     Normalmente, as Atualizações de Funcionalidades são novas funcionalidades do Windows. Depois de configurar a definição **Canal de serviço**, pode definir se pretende e quanto tempo tem para diferir a receção de Atualizações de Funcionalidades depois de estarem disponíveis no Windows Update.

     Por exemplo, **se o Canal de serviço estiver definido para Via de Atualizações Semianuais (Direcionada) e o período de diferimento for de 30 dias**: digamos que a Atualização de Funcionalidades X fica disponível ao público pela primeira vez no Windows Update através da Via de Atualizações Semianuais (Direcionada) em janeiro. O dispositivo não irá receber a atualização até fevereiro – 30 dias mais tarde.

     **Se o canal de Manutenção estiver definido para Via de Atualizações Semianuais e o período de diferimento for 30 dias**: digamos que a Atualização de Funcionalidades X fica disponível ao público pela primeira vez no Windows Update através da Via de Atualizações Semianuais (Direcionada) em janeiro. Quatro meses mais tarde, em abril, a Atualização de Funcionalidades X é lançada na Via de Atualizações Semianuais. O dispositivo recebe a Atualização de Funcionalidades 30 dias após o lançamento na Via de Atualizações Semianuais e é atualizado em maio.

   - **Modo de transferência de otimização da entrega**: selecione o método para o qual os dispositivos transferem as atualizações do Windows. Para obter mais detalhes, veja [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).

6. Quando terminar, selecione **OK**. Em **Criar Cadência de Atualização**, selecione **Criar**.

A nova cadência de atualização é apresentada na lista de cadências de atualização.

1. Para atribuir a cadência, na lista de cadências de atualização, selecione uma cadência e, em seguida, no separador <*nome da cadência*>, escolha **Atribuições**.
2. No separador seguinte, selecione **Selecionar grupos a incluir** e, em seguida, selecione os grupos para os quais pretende atribuir esta cadência.
3. Quando tiver terminado, selecione **Selecionar** para concluir a atribuição.

## <a name="update-compliance-reporting"></a>Relatórios de conformidade de atualização
Pode ver a conformidade de atualizações no Intune ou através de uma solução gratuita no Operations Management Suite (OMS) denominada Conformidade de Atualizações.

### <a name="review-update-compliance-in-intune"></a>Rever a conformidade de atualizações no Intune 
<!-- 1352223 -->
Reveja um relatório das políticas para ver o estado de implementação das cadências de atualização do Windows 10 que configurou.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Atualizações de software** > **Descrição Geral**. Poderá ver informações gerais sobre o estado de qualquer cadência de atualizações que tenha atribuído.
4. Abra um dos seguintes relatórios:

   **Para todas as cadências de implementação**:  
   1. Em **Atualizações de software** > **Cadências de Atualização do Windows 10**
   2. Na secção **Monitorizar**, selecione **Por estado de implementação da cadência de atualização**.

   **Para cadências de implementação específicas**:  
   1. Em **Atualizações de software** > **Cadências de Atualização do Windows 10**, selecione a cadência de implementação a analisar.
   2. Na secção **Monitorizar**, selecione um dos seguintes relatórios para ver informações mais detalhadas sobre a cadência de atualização:
      - **Estado do dispositivo**
      - **Estado de utilizador**

### <a name="review-update-compliance-using-oms"></a>Rever a conformidade de atualizações com o OMS
Pode monitorizar as implementações de atualizações do Windows 10 através de uma solução gratuita no Operations Management Suite (OMS) denominada Compatibilidade da Atualização. Para obter mais detalhes, veja [Monitor Windows Updates with Update Compliance (Monitorizar Atualizações do Windows com a Compatibilidade da Atualização)](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). Quando utiliza esta solução, pode implementar um ID comercial em qualquer um dos seus dispositivos com o Windows 10 geridos pelo Intune para os quais pretende gerar relatórios sobre a compatibilidade da atualização.

Na consola do Intune, pode utilizar as definições de OMA-URI de uma política personalizada para configurar o ID comercial. Para obter mais detalhes, veja [Definições de política do Intune para dispositivos com o Windows 10 no Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

O caminho do OMA-URI (sensível às maiúsculas e minúsculas) para configurar o ID comercial é: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:

- **Nome da Definição**: ID Comercial do Windows Analytics
- **Descrição da Definição**: configurar o ID comercial para soluções do Windows Analytics
- **OMA-URI** (sensível às maiúsculas e minúsculas): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Tipo de Dados:** cadeia
- **Valor**: <*utilizar o GUID apresentado no separador Telemetria do Windows na sua área de trabalho OMS*>

![Definição de OMA-URI – Editar Linha](./media/commID-edit.png)

> [!NOTE]
> Para obter mais informações sobre o servidor de DM MS, veja [Fornecedor de serviço de configuração (CSP) do DMClient](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="pause-updates"></a>Colocar atualizações em pausa
Pode colocar em pausa a receção de Atualizações de Funcionalidades ou Atualizações de Qualidade num dispositivo durante um período máximo de 35 dias desde o momento em que colocou as atualizações em pausa. Após ter decorrido o número máximo de dias, a funcionalidade de pausa irá automaticamente expirar e o dispositivo irá procurar atualizações aplicáveis nas Atualizações do Windows. Após esta procura, pode colocar as atualizações em pausa novamente.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Atualizações de software** > **Cadências de Atualização do Windows 10**.
4. Na lista de cadências de atualização, selecione a cadência que pretende colocar em pausa e, em seguida, selecione **...**  > **Colocar Atualização de Qualidade em Pausa** ou **Colocar Atualização de Funcionalidades em Pausa**, dependendo do tipo de atualizações que pretende colocar em pausa.

> [!IMPORTANT]
> Quando emitir um comando de pausa, os dispositivos receberão este comando da próxima vez que se registarem no serviço. É possível que instalem uma atualização agendada antes do registo.
> Além disso, se um dispositivo de destino for desativado quando emitir o comando de pausa, ao desativá-lo, este poderá transferir e instalar atualizações agendadas antes do registo no Intune.

## <a name="windows-holographic-for-business-support"></a>Suporte do Windows Holographic for Business

O Windows Holographic for Business suporta as seguintes definições:

- **Comportamento de atualização automática**
- **Atualizações de produtos da Microsoft**
- **Canal de serviço**