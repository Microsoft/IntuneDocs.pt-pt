---
title: Verifique o sucesso ou falha das linhas de segurança no Microsoft Intune - Azure  Microsoft Docs
description: Verifique o estado de erro, conflito e estado de sucesso ao implementar linhas de segurança para utilizadores e dispositivos no Microsoft Intune MDM. Veja como resolver problemas usando registos de clientes, e o relatório apresenta-se em Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d8ee4ec6a5bcb29a51b68cff7b840823b678636
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569290"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Monitorize a linha de base de segurança e os perfis no Microsoft Intune

Intune fornece várias opções para monitorizar as suas linhas de segurança. Pode monitorizar o perfil de base de segurança que se aplica aos seus utilizadores e dispositivos. Também pode monitorizar a linha de base real, e quaisquer dispositivos que correspondam (ou não correspondam) aos valores recomendados.

Este artigo acompanha-o através de ambas as opções de monitorização.

As linhas de base de [segurança em Intune](../security-baselines.md) fornecem mais detalhes sobre a funcionalidade de base de segurança no Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Monitorize a linha de base e os seus dispositivos

Quando monitoriza uma linha de base, obtém-se informações sobre o estado de segurança dos seus dispositivos com base nas recomendações da Microsoft. Pode visualizar estas informações a partir do painel de visão geral da linha de base de segurança na consola Intune.  Leva até 24 horas para que os dados apareçam depois de atribuir uma linha de base. As alterações posteriores demoram até seis horas a aparecer.

Para visualizar os dados de monitorização da linha de base e dispositivos, inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431). Em seguida, selecione **a segurança endpoint** > **Security Baselines**, selecione uma linha de base e veja o painel de **visão geral.**

O painel **de visão geral** fornece dois métodos para monitorizar o estado:

- **Vista do dispositivo** – Um resumo de quantos dispositivos estão em cada categoria de estado para a linha de base.
- **Por categoria** - Uma vista que apresenta cada categoria na linha de base e inclui a percentagem de dispositivos para cada grupo de estatuto para cada categoria de base.

Cada dispositivo é representado por um dos seguintes estados (utilizados na vista do *dispositivo* e também pelas vistas *por categoria):*

- **Corresponde à linha** de base - Todas as definições da linha de base correspondem às definições recomendadas.
- **Não corresponde à linha** de base - Pelo menos uma definição na linha de base não corresponde à definição recomendada.

  > [!NOTE]
  > Quando cria ou edita um perfil de base, qualquer alteração que seja feita a um valor padrão ou definição de configuração faz com que ocorra um estado de base "Não corresponde à linha de base". Para obter ajuda para determinar as definições que foram alteradas, contacte o Microsoft Support. 

- **Configurado mal** - Pelo menos uma definição não está corretamente configurada. Este estado significa que a definição está num estado de conflito, erro ou pendente.
- **Não aplicável** - Pelo menos uma definição não é aplicável e não é aplicada.

### <a name="device-view"></a>Vista do dispositivo

O painel de visão geral apresenta um resumo baseado em gráficos de quantos dispositivos têm um estatuto específico para a linha de base; Postura de base de **segurança para dispositivos windows 10 atribuídos**.

![Verifique o estado dos dispositivos](./media/security-baselines-monitor/overview.png)

Quando um dispositivo tem um estatuto diferente de diferentes categorias na linha de base, o dispositivo é representado por um único estado. O estado que representa o dispositivo é retirado da seguinte ordem de precedência: **Misconfigurado**, **Não corresponde**à linha de base , Não **aplicável,** **Corresponde à linha**de base .

Por exemplo, se um dispositivo tiver uma definição classificada como *mal configurada* e uma ou mais definições classificadas como Não corresponde à linha de *base,* o dispositivo é classificado como *Misconfigurado*.

Pode clicar na tabela para perfurar e ver uma lista de dispositivos com vários estados. Em seguida, pode selecionar dispositivos individuais a partir dessa lista para visualizar detalhes sobre dispositivos individuais. Por exemplo:

- Selecione **configuração** do dispositivo > Selecione o perfil com uma posição error:

  ![Ver o estado de um perfil](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Selecione o perfil Error. Uma lista de todas as configurações no perfil, e o seu estado é mostrado. Agora, pode deslocar-se para encontrar a definição que causa o erro:

  ![Veja a definição que causa o erro](./media/security-baselines-monitor/profile-with-error-status.png)

Utilize este relatório para ver quaisquer definições num perfil que estejam a causar um problema. Obtenha também mais detalhes sobre políticas e perfis implementados para dispositivos.

> [!NOTE]
> Quando uma propriedade está definida para **Não configurada** na linha de base, a definição é ignorada, e nenhuma restrição é aplicada. A propriedade não é mostrada em nenhum relatório.

### <a name="per-category-view"></a>Por vista de categoria

O painel de visão geral apresenta um gráfico por categoria para a linha de base; **Postura de base de segurança por categoria**.  Esta visão apresenta cada categoria a partir da linha de base e identifica a percentagem de dispositivos que se enquadram numa classificação de estado para cada uma dessas categorias.

![Visão por categoria do estado](./media/security-baselines-monitor/monitor-baseline-per-category.png)

O estado da linha de **base de Fósforos** só é apresentado a 100% dos dispositivos que reportem esse estado para a categoria.

Pode classificar a vista por categoria por cada coluna, selecionando o ícone de seta para cima na parte superior da coluna.

## <a name="monitor-the-profile"></a>Monitorize o perfil

Monitorizar o perfil dá-lhe uma visão do estado de implantação dos seus dispositivos, mas não do estado de segurança com base nas recomendações de base.

1. Intune, selecione **Security Baselines** > selecione uma linha de base > **Perfis criados**.

2. Selecione um perfil. Em **resumo,** a imagem mostra quantos dispositivos e utilizadores têm este perfil atribuído:

   ![Veja quantos dispositivos e utilizadores são atribuídos ao perfil de base de segurança](./media/security-baselines-monitor/existing-profile-overview.png)

3. No âmbito **da Manage** > **Properties,** é apresentada uma lista de todas as definições da linha de base. Também pode alterar qualquer uma destas definições:

   ![Ver e atualizar definições no perfil de base de segurança](./media/security-baselines-monitor/manage-settings.png)

4. No **Monitor,** pode ver o estado de implementação do perfil em dispositivos individuais, o estado de cada utilizador e o estado de cada definição na linha de base:

   ![Consulte as diferentes opções de monitor para um perfil de base de segurança](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="view-endpoint-security-configurations-per-device"></a>Ver configurações de segurança endpoint por dispositivo

Consulte detalhes sobre as configurações de segurança que se aplicam a um dispositivo individual, o que pode ajudá-lo a isolar as definições que estão mal configuradas.

1. Inscreva-se no signine no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Vá ao **Dispositivo > ** Todos **os dispositivos** e selecione o dispositivo que pretende visualizar.

3. Na categoria *Monitor,* selecione a configuração de **segurança endpoint** para visualizar a lista de configurações de segurança que se aplicam a esse dispositivo.

4. Pode selecionar uma configuração de segurança endpoint para perfurar e ver detalhes adicionais sobre a avaliação dessa configuração de segurança no dispositivo.

## <a name="troubleshoot-using-per-setting-status"></a>Resolução de problemas utilizando o estado por definição

Implementou uma linha de base de segurança, mas o estado de implantação mostra um erro. Os seguintes passos dão-lhe alguma orientação sobre a resolução de problemas do erro.

1. Intune, selecione **Security Baselines** > selecione uma linha de base > **Perfis criados**.

2. Selecione um perfil > Sob **o monitor** > estado **de definição por definição**.

3. A tabela mostra todas as definições e o estado de cada definição. Selecione a coluna **Error** ou a coluna **Conflito** para ver a definição que causa o erro.

### <a name="mdm-diagnostic-information"></a>Informação de diagnóstico do MDM

Agora já conhece o cenário problemático. O próximo passo é descobrir por que esta configuração está a causar um erro ou conflito.

Nos dispositivos windows 10, há um relatório de diagnóstico de MDM incorporado. Este relatório inclui valores predefinidos, valores atuais, lista a política, mostra se está implantado no dispositivo ou no utilizador, e muito mais. Utilize este relatório para ajudar a determinar por que razão a definição está a causar um conflito ou erro.

1. No dispositivo, aceda a **Definições** > **Contas** > Trabalho de **Acesso ou escola**.

2. Selecione a conta > **Info** > **Relatório Avançado** de Diagnóstico > **Criar relatório**.

3. Escolha **exportação**e abra o ficheiro gerado.

4. No relatório, procure o erro ou a definição de conflito sintetizador nas diferentes secções do relatório.

  Por exemplo, procure nas fontes de **configuração inscritas e** na secção de recursos-alvo ou na secção **políticas não geridas.** Podes ter uma ideia do porquê de estar a causar um erro ou um conflito.

[Diagnosticar falhas de MDM no Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) fornece mais informações sobre este relatório incorporado.

> [!TIP]
>
> - Algumas configurações também listam o GUID. Pode pesquisar este GUID no registo local (regedita) por quaisquer valores definidos.
> - Os registos do Espectador de Eventos também podem incluir algumas informações de erro sobre a definição problemática ( Registos de > de**visualização** de **eventos > ** **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin).**

## <a name="next-steps"></a>Próximos passos

[Monitorize os perfis do dispositivo](../configuration/device-profile-monitor.md) e veja [algumas questões e resoluções comuns.](../configuration/device-profile-troubleshoot.md)
