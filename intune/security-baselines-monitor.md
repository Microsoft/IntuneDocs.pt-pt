---
title: Verificar o êxito ou falha de linhas de base de segurança no Microsoft Intune – Azure | Documentos da Microsoft
description: Verificar o estado de erro, o conflito e o sucesso ao implementar linhas de base de segurança a utilizadores e dispositivos no Microsoft Intune MDM. Veja como resolver problemas com registos de cliente e as funcionalidades de relatório no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfbdad6d98065a691528d4cdada0b6f9377e1109
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848241"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>Monitorizar a base de segurança e o perfil no Microsoft Intune

Existem diferentes opções de monitorização, ao utilizar linhas de base de segurança. Pode monitorizar o perfil de linhas de base de segurança que se aplica aos seus utilizadores e dispositivos. Também pode monitorizar a linha de base real e todos os dispositivos que corresponde ao (ou não correspondem) os valores recomendados.

Este artigo orienta-o por meio de ambas as opções de monitorização.

[Linhas de base de segurança no Intune](security-baselines.md) fornece mais detalhes sobre a funcionalidade de linhas de base de segurança no Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Monitorizar a linha de base e seus dispositivos

Ao monitorar a linha de base, obtenha informações sobre o estado de segurança dos seus dispositivos com base nas recomendações da Microsoft.

> [!NOTE]
> Depois do primeiro é atribuída uma linha de base, relatórios podem demorar até 24 horas para atualizar. Depois disso, podem demorar até seis horas para atualizar.

1. Na [portal do Azure](https://portal.azure.com/), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.
2. Selecione **linhas de base de segurança (pré-visualização)** > Selecione uma linha de base.
3. Na **descrição geral**, o gráfico mostra o número de dispositivos é afetado pela linha de base que escolheu e os diferentes Estados:

    ![Verificar o estado dos dispositivos](./media/security-baselines-monitor/overview.png)

    Os seguintes Estados estão disponíveis:

    - **Linha de base de correspondências**: Todas as definições na linha de base correspondem as definições recomendadas.
    - **Não corresponde à linha de base**: Pelo menos uma definição na linha de base não corresponde as definições recomendadas.
    - **Configurado incorretamente**: Pelo menos uma definição não está corretamente configurada. Este estado significa que a definição está num conflito, erro ou o estado pendente.
    - **Não aplicável**: Pelo menos uma definição não é aplicável e não é aplicada.

4. Selecione um dos Estados de que tem dispositivos. Por exemplo, selecione o **Misconfigured** estado.

5. É apresentada uma lista de todos os dispositivos com esse Estado. Selecione um dispositivo específico para obter mais detalhes. 

    No exemplo seguinte, selecione **configuração do dispositivo** > selecione o perfil com um Estado de erro:

    ![Verificar o estado dos dispositivos](./media/security-baselines-monitor/device-configuration-profile-list.png)

    Selecione o perfil de erro. É apresentada uma lista de todas as definições no perfil de e o respetivo estado. Agora, pode rolar para encontrar a definição causando o erro:

    ![Ver a definição causando o erro](./media/security-baselines-monitor/profile-with-error-status.png)

Utilize este relatório para ver todas as definições num perfil que estão a causar um problema. Também obter mais detalhes sobre as políticas e perfis de implementação em dispositivos.

> [!NOTE]
> Quando uma propriedade está definida como **não configurado** na linha de base, a definição é ignorada e sem restrições são impostas. A propriedade não é mostrada em qualquer relatório.

## <a name="monitor-the-profile"></a>Monitorizar o perfil

O perfil de monitorização dá-lhe informações sobre o estado de implementação dos seus dispositivos, mas não o estado de segurança com base nas recomendações da linha de base.

1. No Intune, selecione **linhas de base de segurança** > Selecione uma linha de base > **perfis criados**.

2. Selecione um perfil. Na **descrição geral**, a imagem mostra o número de dispositivos e os utilizadores têm este perfil atribuído:

    ![Veja quantos dispositivos e utilizadores são atribuídos do perfil de linhas de base de segurança](./media/security-baselines-monitor/existing-profile-overview.png)

3. Sob **Manage** > **propriedades**, uma lista de todas as definições na linha de base são mostradas. Também pode alterar qualquer uma destas definições:

    ![Ver e atualizar as definições do perfil de linhas de base de segurança](./media/security-baselines-monitor/manage-settings.png)

4. Na **Monitor**, pode ver o estado de implementação do perfil de dispositivos individuais, o estado de cada utilizador e o estado para cada definição na linha de base:

    ![Ver as opções de monitor diferente para um perfil de linhas de base de segurança](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Resolver problemas com o estado por definição

Implementou uma linha de base de segurança, mas o estado de implementação é apresentado um erro. Os passos seguintes dão-lhe algumas orientações sobre como resolver o erro.

1. No Intune, selecione **linhas de base de segurança** > Selecione uma linha de base > **perfis criados**.
2. Selecione um perfil > sob **Monitor** > **estado por definição**.
3. A tabela mostra todas as definições e o estado de cada configuração. Selecione o **erro** coluna ou o **conflito** coluna para ver a definição causando o erro.

### <a name="mdm-diagnostic-information"></a>Informações de diagnóstico do MDM

Agora, sabe a definição problemática. A próxima etapa é descobrir por que esta definição está a causar um conflito ou erro. 

Em dispositivos Windows 10, existe um relatório de informações de diagnóstico interno do MDM. Este relatório inclui valores predefinidos, valores atuais, apresenta uma lista da política, mostra se for implementada para o dispositivo ou utilizador e muito mais. Utilize este relatório para ajudar a determinar por que a configuração está a causar um conflito ou erro.

1. No dispositivo, aceda a **configurações** > **contas** > **acesso profissional ou escolar**.
2. Selecione a conta > **Info** > **relatório de diagnóstico avançadas** > **criar relatório**.
3. Escolher **exportar**e abra o arquivo gerado.
4. No relatório, procure o erro ou a definição de conflito em diferentes seções do relatório.

  Por exemplo, procure na **inscritos origens de configuração e de recursos de destino** secção ou o **não gerido políticas** secção. Pode ter uma idéia de por que motivo que esteja a causar um conflito ou erro.

[Diagnosticar falhas MDM no Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) fornece mais informações sobre este relatório incorporado.

> [!TIP]
> - Algumas definições também listam o GUID. Pode procurar este GUID no registo (regedit) local para qualquer conjunto de valores.
> - Os registos do Visualizador de eventos também podem incluir algumas informações de erro sobre a definição de problemática (**Visualizador de eventos** > **registos de serviços e aplicações**  >   **Microsoft** > **Windows** > **DeviceManagement Enterprise-diagnóstico fornecedor** > **Admin** ).

## <a name="next-steps"></a>Passos Seguintes

[Monitorizar perfis de dispositivos](device-profile-monitor.md) e [Consulte alguns problemas comuns e as resoluções](device-profile-troubleshoot.md).
