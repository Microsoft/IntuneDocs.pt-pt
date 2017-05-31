---
title: "Configurar as definições do Windows Update para Empresas – Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como configurar as definições do Windows Update para Empresas no Intune para controlar as atualizações para dispositivos Windows 10."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08f659cf-715e-4e10-9ab2-1bac3c6f2366
ms.reviewer: coryfe
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: b0bc3e557f303cd80c780634ba47b24405c327e1
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-windows-update-for-business-settings-with-microsoft-intune"></a>Como configurar as definições do Windows Update para Empresas com o Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="introduction"></a>Introdução
O Windows como um Serviço é a nova forma de disponibilizar atualizações para o Windows 10. A partir do Windows 10, todas as novas Atualizações de Funcionalidades e Atualizações de Qualidade irão conter o conteúdo de todas as atualizações anteriores. Tal significa que, desde que instale a atualização mais recente, sabe que os dispositivos Windows 10 estão completamente atualizados. Ao contrário das versões anteriores do Windows, agora tem de instalar toda a atualização em vez de parte de uma atualização.

Ao utilizar o Windows Update para Empresas, pode simplificar a experiência de gestão de atualizações para não ter de aprovar atualizações individuais para grupos de dispositivos. Pode continuar a gerir o risco nos seus ambientes ao configurar uma estratégia de implementação de atualizações e o Windows Update irá garantir que as atualizações são instaladas no momento certo. O Microsoft Intune permite configurar definições de atualizações nos dispositivos e dá-lhe a capacidade de diferir a instalação de atualizações. O Intune não armazena as atualizações, mas apenas a atribuição da política de atualização. Os dispositivos acedem ao Windows Update diretamente para obterem as atualizações. Utilize o Intune para configurar e gerir **anéis de atualização do Windows 10**. Um anel de atualização contém um grupo de definições que configuram quando e como as atualizações do Windows 10 são instaladas. Por exemplo, pode configurar o seguinte:

- **Servicing Branch do Windows 10**: escolha se pretende que grupos de dispositivos recebam atualizações a partir do Current Branch ou do Current Branch for Business.  
- **Definições de Diferimento**: configure as definições de diferimento das atualizações para atrasar as instalações de atualizações para grupos de dispositivos. Em seguida, terá uma implementação de atualização faseada para que possa rever o progresso ao longo do processo.
- **Colocar em pausa**: adie a instalação de atualizações se detetar um problema em qualquer momento durante a implementação das atualizações.
- **Janela de manutenção**: configure as horas nas quais as atualizações possam ser instaladas.
- **Tipo de atualização**: escolha os tipos de atualizações que são instaladas. Por exemplo, Atualizações de Qualidade, Atualizações de Funcionalidades ou controladores.
- **Comportamento da instalação**: esta opção configura a forma como a atualização é instalada. Por exemplo, o dispositivo reinicia automaticamente após a instalação?
- **Transferência ponto a ponto**: pode especificar se pretende configurar a transferência ponto a ponto. Se estiver configurada, quando um dispositivo concluir a transferência de uma atualização, os outros dispositivos poderão transferir a atualização a partir desse dispositivo. Deste modo, acelera o processo de transferência.

Depois de criar anéis de atualização, atribua-os a grupos de dispositivos. Ao utilizar anéis de atualização, pode criar uma estratégia de atualização que reflete as necessidades da sua empresa. Para obter mais informações, veja [Manage updates using Windows Update for Business (Gerir atualizações através do Windows Update para Empresas)](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Antes de começar

- Para atualizar os PCs com o Windows 10, estes têm de ter, pelo menos, o Windows 10 Pro com a atualização de Aniversário do Windows.

- O Windows Update suporta as seguintes versões do Windows 10:
    - Windows 10
    - Windows 10 Team (para dispositivos Surface Hub)

 Os dispositivos que executam o Windows 10 Mobile e Windows 10 Holographic não são suportados.

- Nos dispositivos Windows, a definição **Comentários e diagnósticos** > **Dados de diagnóstico e utilização** tem de ser definida, pelo menos, para **Básico**.

    ![Definição do Windows para os dados de diagnóstico e utilização](./media/telemetry-basic.png)

    Pode configurar esta definição manualmente ou utilizar um perfil de restrição de dispositivos do Intune para o Windows 10 e posterior. Para o fazer, configure a definição **Geral** > **Submissão de dados de diagnóstico**, pelo menos, para **Básico**. Para obter mais informações sobre os perfis de dispositivo, veja [Como configurar definições de restrições de dispositivos](device-restrictions-configure.md).

- Na consola clássica de administração do Intune, existem quatro definições que controlam o comportamento das atualizações do software. Estas definições fazem parte da política de configuração geral dos dispositivos móveis e computadores com o Windows 10:
    - **Permitir atualizações automáticas**
    - **Permitir funcionalidades de pré-lançamento**
    - **Agendar Dia da Instalação**
    - **Agendar Hora da Instalação**

  A consola clássica também tem um número limitado de outras definições de atualizações do Windows 10 no perfil de configuração do dispositivo. Se tiver qualquer uma destas definições configuradas na consola clássica de administração do Intune quando migra para o portal do Azure, recomendamos vivamente que realize o seguinte procedimento:

1. No portal do Azure, crie anéis de atualização do Windows 10 com as definições de que precisa. A definição **Permitir funcionalidades de pré-lançamento** não é suportada no portal do Azure, porque já não é aplicável às compilações do Windows 10 mais recentes. Pode configurar as outras três definições, bem como outras definições de atualizações do Windows 10, quando cria os anéis de atualização.

  > [!NOTE]
  > As definições das atualizações do Windows 10 criadas na consola clássica não são apresentadas no portal do Azure após a migração. No entanto, estas definições continuam a ser aplicadas. Se tiver migrado qualquer uma destas definições e editar a política migrada a partir do portal do Azure, estas definições serão removidas da política.

2. Elimine as definições de atualização na consola clássica. Depois de migrar para o portal do Azure e adicionar as mesmas definições a um anel de atualização, terá de eliminar as definições no portal clássico para evitar potenciais conflitos de políticas. Por exemplo, quando a mesma definição está configurada com valores diferentes, existirá um conflito e não haverá uma forma fácil de saber porque a definição configurada na consola clássica não é apresentada no portal do Azure.

## <a name="how-to-create-and-assign-update-rings"></a>Como criar e atribuir anéis de atualização

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Atualizações de Software**.
4. No painel **Atualizações de Software**, escolha **Gerir** > **Anéis de Atualização do Windows 10**.
5. No painel que apresenta a lista de anéis de atualização, escolha **Criar**.
6. No painel **Criar Anel de Atualização**, indique um nome e uma descrição opcional para o anel de atualização e, em seguida, escolha **Definições**.
7. No painel **Definições**, configure as informações seguintes:
    - **Servicing branch**: defina o ramo para o qual o dispositivo irá receber atualizações do Windows (Current Branch ou Current Branch for Business).
    - **Atualizações da Microsoft**: escolha se pretende procurar atualizações da aplicação no Microsoft Update.
    - **Controladores do Windows**: escolha se pretende excluir controladores do Windows Update durante as atualizações.
    - **Comportamento da atualização automática**: escolha como pretende gerir o comportamento da atualização automática para procurar, transferir e instalar atualizações. Para obter mais detalhes, veja [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Período de diferimento da atualização de qualidade (dias)** – especifique o número de dias de diferimento das atualizações de qualidade. Pode diferir a receção destas Atualizações de Qualidade durante um período máximo de 30 dias a partir do seu lançamento.  

      Geralmente, as Atualizações de Qualidade são correções e melhorias às funcionalidades do Windows existentes e, normalmente, são publicadas na primeira terça-feira de cada mês, embora possam ser lançadas em qualquer altura pela Microsoft. Pode definir se, e durante quanto tempo, gostaria de diferir a receção das Atualizações de Qualidade, após a sua disponibilidade.
    - **Período de diferimento da atualização de funcionalidades (dias)** – especifique o número de dias de diferimento das Atualizações de Funcionalidades. Pode diferir a receção destas Atualizações de Funcionalidades durante um período máximo de 180 dias após o seu lançamento.

    Geralmente, as Atualizações de Funcionalidades são novas funcionalidades do Windows. Depois de configurar a definição **Servicing branch** (**CB** ou **CBB**), pode definir se, e durante quanto tempo, gostaria de diferir a receção das Atualizações de Funcionalidades, após a sua disponibilidade da Microsoft no Windows Update.

    Por exemplo:  
    **Se o Servicing branch estiver definido como CB e o período de diferimento for de 30 dias**: vamos supor que a Atualização de Funcionalidades X está disponível publicamente pela primeira vez no Windows Update como um CB em janeiro. O dispositivo só irá receber a atualização em fevereiro – 30 dias mais tarde.

    **Se o Servicing branch estiver definido como CBB e o período de diferimento for de 30 dias**: vamos supor que a Atualização de Funcionalidades X está disponível publicamente pela primeira vez no Windows Update como um CB em janeiro. Quatro meses mais tarde, em abril, a Atualização de Funcionalidades X é lançada para o CBB. O dispositivo irá receber a Atualização de Funcionalidades 30 dias após o lançamento deste CBB e será atualizado na maio.

    - **Otimização da entrega** – escolha o método para o qual os dispositivos irão transferir as atualizações do Windows. Para obter mais detalhes, veja [DeliveryOptimization/DODownloadMode](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#deliveryoptimization-dodownloadmode).
8. Quando tiver terminado, clique em **OK** e, no painel **Criar Anel de Atualização**, clique em **Criar**.

O novo anel de atualização é apresentado na lista de anéis de atualização.

1. Para atribuir o anel, na lista de anéis de atualização, selecione um anel e, em seguida, no separador <*nome do anel*>, escolha **Atribuições**.
2. No separador seguinte, escolha **Selecionar grupos** e, em seguida, selecione os grupos para os quais pretende atribuir este anel.
3. Quando tiver terminado, selecione **Selecionar** para concluir a atribuição.



## <a name="update-compliance-reporting"></a>Relatórios de conformidade de atualização
Pode monitorizar as implementações de atualizações do Windows 10 através de uma solução gratuita no Operations Management Suite (OMS) denominada Compatibilidade da Atualização. Para obter mais detalhes, veja [Monitor Windows Updates with Update Compliance (Monitorizar Atualizações do Windows com a Compatibilidade da Atualização)](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). Quando utiliza esta solução, pode implementar um ID comercial em qualquer um dos seus dispositivos com o Windows 10 geridos pelo Intune para os quais pretende gerar relatórios sobre a compatibilidade da atualização.

Na consola do Intune, pode utilizar as definições de OMA-URI de uma política personalizada para configurar o ID comercial. Para obter mais detalhes, veja [Definições de política do Intune para dispositivos com o Windows 10 no Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

O caminho do OMA-URI (sensível às maiúsculas e minúsculas) para configurar o ID comercial é: ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:

- **Nome da Definição**: ID Comercial do Windows Analytics
- **Descrição da Definição**: configurar o ID comercial para soluções do Windows Analytics
- **Tipo de Dados:** cadeia
- **OMA-URI** (sensível às maiúsculas e minúsculas): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Valor**: <*utilizar o GUID apresentado no separador Telemetria do Windows na sua área de trabalho OMS*>

![Definição do Windows para os dados de diagnóstico e utilização](./media/commID.png)

<!--
1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Software Updates**.
4. On the **Software Updates** blade, choose **Overview**. From here you can see general information about the status of any update rings you assigned.
4. On the **Windows 10 Updates** blade, choose **Monitor** > **Update ring deployment for devices**, **Update ring deployment for users**, or **Per-setting deployment state** to view more detailed information about update ring assignments.
-->





## <a name="how-to-pause-updates"></a>Como colocar atualizações em pausa
Pode colocar em pausa a receção de Atualizações de Funcionalidades ou Atualizações de Qualidade num dispositivo durante um período máximo de 35 dias desde o momento em que colocou as atualizações em pausa. Após ter decorrido o número máximo de dias, a funcionalidade de pausa irá automaticamente expirar e o dispositivo irá procurar atualizações aplicáveis nas Atualizações do Windows. Após esta procura, pode colocar as atualizações em pausa novamente.
1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Atualizações de Software**.
4. No painel **Atualizações de Software**, escolha **Gerir** > **Anéis de Atualização do Windows 10**.
5. No painel que mostra a lista de anéis de atualização, escolha o anel que quer colocar em pausa e, em seguida, escolha **...**  > **Colocar em Pausa Atualizações de Qualidade** > ou **Colocar em Pausa Atualizações de Funcionalidades**, dependendo do tipo de atualizações que quer colocar em pausa.

> [!IMPORTANT]
> Quando emitir um comando de pausa, os dispositivos receberão este comando da próxima vez que se registarem no serviço. É possível que instalem uma atualização agendada antes do registo.
> Além disso, se um dispositivo de destino for desativado quando emitir o comando de pausa, ao desativá-lo, este poderá transferir e instalar atualizações agendadas antes do registo no Intune.

