---
title: Verificar o êxito ou a falha das linhas de base de segurança no Microsoft Intune-Azure | Microsoft Docs
description: Verifique o status de erro, conflito e êxito ao implantar linhas de base de segurança para usuários e dispositivos no Microsoft Intune MDM. Consulte Como solucionar problemas usando logs do cliente e os recursos de relatório no Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
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
ms.openlocfilehash: cbf82c0bef88e4a6d0e790f4b0ecdf73d2731d5d
ms.sourcegitcommit: 9bb1bcd9f1bdd53b470073da956bbd8b0935dfbc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556407"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Monitorar a linha de base e os perfis de segurança no Microsoft Intune

O Intune fornece várias opções para monitorar suas linhas de base de segurança. Você pode monitorar o perfil de linhas de base de segurança que se aplica a seus usuários e dispositivos. Você também pode monitorar a linha de base real e todos os dispositivos que correspondam (ou não correspondam) os valores recomendados.

Este artigo orienta você pelas duas opções de monitoramento.

As [linhas de base de segurança no Intune](../security-baselines.md) fornecem mais detalhes sobre o recurso de linhas de base de segurança no Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Monitorar a linha de base e seus dispositivos

Ao monitorar uma linha de base, você obtém informações sobre o estado de segurança de seus dispositivos com base nas recomendações da Microsoft. Você pode exibir essas informações no painel Visão geral da linha de base de segurança no console do Intune.  Leva até 24 horas para que os dados apareçam depois que você atribui uma linha de base pela primeira vez. As alterações posteriores levam até seis horas para serem exibidas.

Para exibir dados de monitoramento para a linha de base e os dispositivos, entre no [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Em seguida, selecione **Endpoint security** > **linhas de base de segurança**, selecione uma linha de base e exiba o painel **visão geral** .

O painel **visão geral** fornece dois métodos para monitorar o status:

- **Exibição de dispositivo** – um resumo de quantos dispositivos estão em cada categoria de status para a linha de base.
- **Por categoria** -uma exibição que exibe cada categoria na linha de base e inclui a porcentagem de dispositivos para cada grupo de status para cada categoria de linha de base.

Cada dispositivo é representado por um dos seguintes status (usado na exibição do *dispositivo* e também nas exibições *por categoria* ):

- **Corresponde à linha de base** -todas as configurações na linha de base correspondem às configurações recomendadas.
- Não **corresponde à linha de base** -pelo menos uma configuração na linha de base não corresponde à configuração recomendada.

  > [!NOTE]
  > Quando você cria ou edita um perfil de linha de base, qualquer alteração feita em um valor padrão ou definição de configuração faz com que o status "não corresponda à linha de base" ocorra. Para obter ajuda para determinar as configurações que foram alteradas, entre em contato com Suporte da Microsoft. 

- **Mal** configurado – pelo menos uma configuração não está configurada corretamente. Esse status significa que a configuração está em um estado de conflito, erro ou pendente.
- **Não aplicável** -pelo menos uma configuração não é aplicável e não é aplicada.

### <a name="device-view"></a>Exibição do dispositivo

O painel Visão geral exibe um resumo baseado em gráfico de quantos dispositivos têm um status específico para a linha de base; **Postura de linha de base de segurança para dispositivos Windows 10 atribuídos**.

![Verificar o status dos dispositivos](./media/security-baselines-monitor/overview.png)

Quando um dispositivo tem status diferente de diferentes categorias na linha de base, o dispositivo é representado por um único status. O status que representa o dispositivo é obtido da seguinte ordem de precedência: **configurado incorretamente**, não **corresponde à linha de base**, **não aplicável**, **corresponde à linha de base**.

Por exemplo, se um dispositivo tiver uma configuração classificada como *configurada incorretamente* e uma ou mais configurações classificadas como não *corresponderem à linha de base*, o dispositivo será classificado como *configurado incorretamente*.

Você pode clicar no gráfico para fazer drill-through e exibir uma lista de dispositivos com vários status. Em seguida, você pode selecionar dispositivos individuais nessa lista para exibir detalhes sobre dispositivos individuais. Por exemplo:

- Selecione **configuração do dispositivo** > selecione o perfil com um estado de erro:

  ![Exibir o status de um perfil](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Selecione o perfil de erro. Uma lista de todas as configurações no perfil e seu estado é mostrado. Agora, você pode rolar para encontrar a configuração causando o erro:

  ![Veja a configuração que está causando o erro](./media/security-baselines-monitor/profile-with-error-status.png)

Use este relatório para ver as configurações em um perfil que estão causando um problema. Obtenha também mais detalhes de políticas e perfis implantados em dispositivos.

> [!NOTE]
> Quando uma propriedade é definida como **não configurada** na linha de base, a configuração é ignorada e nenhuma restrição é imposta. A propriedade não é mostrada em nenhum relatório.

### <a name="per-category-view"></a>Exibição por categoria

O painel Visão geral exibe um gráfico por categoria para a linha de base; **Postura de linha de base de segurança por categoria**.  Essa exibição mostra cada categoria da linha de base e identifica a porcentagem de dispositivos que se enquadram em uma classificação de status para cada uma dessas categorias.

![Exibição por categoria do status](./media/security-baselines-monitor/monitor-baseline-per-category.png)

O status de **correspondências de linha de base** não é exibido até 100% dos dispositivos relatar esse status para a categoria.

Você pode classificar a exibição por categoria por cada coluna selecionando o ícone de seta para cima na parte superior da coluna.

## <a name="monitor-the-profile"></a>Monitorar o perfil

O monitoramento do perfil fornece informações sobre o estado de implantação de seus dispositivos, mas não o estado de segurança com base nas recomendações de linha de base.

1. No Intune, selecione **linhas de base de segurança** > selecione uma linha de base > **perfis criados**.

2. Selecione um perfil. Em **visão geral**, a imagem mostra quantos dispositivos e usuários têm esse perfil atribuído:

   ![Ver quantos dispositivos e usuários recebem o perfil de linhas de base de segurança](./media/security-baselines-monitor/existing-profile-overview.png)

3. Em **gerenciar** **Propriedades**de > , uma lista de todas as configurações na linha de base é mostrada. Você também pode alterar qualquer uma dessas configurações:

   ![Consulte e atualize as configurações no perfil de linhas de base de segurança](./media/security-baselines-monitor/manage-settings.png)

4. No **Monitor**, você pode ver o status da implantação do perfil em dispositivos individuais, o status de cada usuário e o status de cada configuração na linha de base:

   ![Consulte as diferentes opções de monitor para um perfil de linhas de base de segurança](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Solucionar problemas usando o status por configuração

Você implantou uma linha de base de segurança, mas o status da implantação mostra um erro. As etapas a seguir fornecem algumas diretrizes sobre como solucionar o erro.

1. No Intune, selecione **linhas de base de segurança** > selecione uma linha de base > **perfis criados**.

2. Selecione um perfil > em **monitorar** > **status por configuração**.

3. A tabela mostra todas as configurações e o status de cada configuração. Selecione a coluna **erro** ou a coluna **conflito** para ver a configuração que está causando o erro.

### <a name="mdm-diagnostic-information"></a>Informações de diagnóstico do MDM

Agora você sabe a configuração problemática. A próxima etapa é descobrir por que essa configuração está causando um erro ou conflito.

Em dispositivos Windows 10, há um relatório interno de informações de diagnóstico do MDM. Este relatório inclui valores padrão, valores atuais, lista a política, mostra se ele está implantado no dispositivo ou no usuário e muito mais. Use este relatório para ajudar a determinar por que a configuração está causando um conflito ou erro.

1. No dispositivo, vá para **configurações** > **contas** > **acessar trabalho ou escola**.

2. Selecione a conta > **informações** > **relatório de diagnóstico avançado** > **criar relatório**.

3. Escolha **Exportar**e abra o arquivo gerado.

4. No relatório, procure o erro ou a configuração de conflito nas seções diferentes do relatório.

  Por exemplo, examine a seção **fontes de configuração e recursos de destino registrados** ou a seção **políticas não gerenciadas** . Você pode ter uma ideia de por que está causando um erro ou conflito.

[Diagnosticar falhas de MDM no Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) fornece mais informações sobre esse relatório interno.

> [!TIP]
> - Algumas configurações também listam o GUID. Você pode pesquisar esse GUID no registro local (regedit) para qualquer valor definido.
> - Os logs de Visualizador de Eventos também podem incluir algumas informações de erro sobre a configuração problemática (**Visualizar eventos** > **logs de aplicativos e serviços** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **admin**).

## <a name="next-steps"></a>Próximos passos

[Monitore perfis de dispositivo](../configuration/device-profile-monitor.md) e [Veja alguns problemas comuns e resoluções](../configuration/device-profile-troubleshoot.md).
