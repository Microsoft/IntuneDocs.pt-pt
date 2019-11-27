---
title: Atualizar o Office 365 usando modelos administrativos no Microsoft Intune-Azure | Microsoft Docs
description: Use modelos administrativos no Microsoft Intune para atualizar os aplicativos do Office 365 para a versão mais recente e escolha a frequência com que o Office verifica se há atualizações. Consulte as chaves do registro do dispositivo que são atualizadas quando uma política do Intune para atualização do Office é aplicada.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf872387d6e6f4f91af9f074f54695b081b79119
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549537"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>Use as configurações de canal de atualização e versão de destino para atualizar o Office 365 com Microsoft Intune Modelos Administrativos

No Intune, você pode usar [modelos do Windows 10 para definir configurações de política de grupo](administrative-templates-windows.md). Este artigo mostra como atualizar o Office 365 usando um modelo administrativo no Intune. Ele também fornece orientação sobre como confirmar se as políticas se aplicam com êxito. Essas informações também ajudam na solução de problemas.

Nesse cenário, você cria um modelo administrativo no Intune que atualiza o Office 365 em seus dispositivos.

Para obter mais informações sobre modelos administrativos, consulte [modelos do Windows 10 para definir configurações de política de grupo](administrative-templates-windows.md).

Aplica-se a:

- Windows 10 e posterior
- Office 365

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de [habilitar o Office365 ProPlus atualizações automáticas](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) para seus aplicativos do Office. Você pode fazer isso usando a política de grupo ou o modelo de ADMX do Intune Office 2016:

![No modelo administrativo do Intune, defina a configuração Habilitar Atualizações Automáticas para o Office](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Definir o canal de atualização no modelo administrativo do Intune

1. No [modelo administrativo do Intune](administrative-templates-windows.md#create-a-template), vá para a configuração **Atualizar canal** e insira o canal desejado. Por exemplo, escolha `Semi-Annual Channel`:

    ![No modelo administrativo do Intune, defina a configuração de canal de atualização para o Office](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > É recomendável atualizar com mais frequência. Semestral é usado apenas como um exemplo.

2. Certifique-se de [atribuir a política](device-profile-assign.md) a seus dispositivos Windows 10. Para testar sua política mais cedo, você também pode sincronizar a política:

    - [Sincronizar a política no Intune](../remote-actions/device-sync.md)
    - [Sincronizar manualmente a política no dispositivo](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Verificar as chaves do registro do Intune

Depois de atribuir a política e as sincronizações de dispositivo, você pode confirmar se a política foi aplicada:

1. No dispositivo, abra o aplicativo **Editor do registro** .
2. Vá para o caminho de política do Intune: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > O `<Provider ID>` na chave do registro é alterado. Para localizar a ID do provedor do seu dispositivo, abra o aplicativo **Editor do registro** e vá para `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. A ID do provedor é mostrada.

    Quando a política for aplicada, você verá as seguintes chaves do registro:

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    Observando o exemplo a seguir, você verá `L_UpdateBranch` tem um valor semelhante a `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`. Esse valor significa que ele está definido como canal semianual:

    ![Modelo administrativo L_Updatebranch exemplo de chave do registro](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [Gerenciar o Office 365 ProPlus com Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) lista os valores e o que eles significam. Os valores do registro se baseiam no canal de distribuição selecionado:
    >
    >- Canal-valor mensal = "atual"
    >- Canal mensal (direcionado)-valor = "atual"
    >- Canal semianual-valor = "atual"
    >- Canal semianual (direcionado)-valor = "FirstReleaseDeferred"
    >- Insider rápido-valor = "InsiderFast"

Neste ponto, a política do Intune é aplicada com êxito ao dispositivo.

## <a name="check-the-office-registry-keys"></a>Verificar as chaves do registro do Office

1. No dispositivo, abra o aplicativo **Editor do registro** .
2. Vá para o caminho de política do Office: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    Você verá as seguintes chaves do registro:

    - `UpdateChannel`: uma chave dinâmica que é alterada, dependendo das configurações definidas.
    - `CDNBaseUrl`: defina quando o Office 365 é instalado no dispositivo.

3. Examine o valor `UpdateChannel`. O valor informa com que frequência o Office é atualizado. [Gerencie o Office 365 ProPlus com Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) lista os valores e o que eles estão definidos como.

    Observando o exemplo a seguir, você verá `UpdateChannel` está definido como `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`, o que é **mensal**:

    ![Modelo administrativo do Office UpdateChannel exemplo de chave do registro](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Este exemplo significa que a política ainda não foi aplicada, pois ela ainda está definida como **mensal**, em vez de **semianual**.

Essa chave do registro é atualizada quando o **Agendador de Tarefas** > **Office atualizações automáticas 2,0** é executado ou quando um usuário entra no dispositivo. Para confirmar, abra a tarefa do **Office Atualizações Automáticas 2,0** > **gatilhos**. Dependendo de seus gatilhos, pode levar pelo menos um dia e mais antes de a chave do registro `UpdateChannel` ser atualizada.

## <a name="force-office-automatic-updates-to-run"></a>Forçar a execução de atualizações automáticas do Office

Para testar sua política, você pode forçar as configurações de política no dispositivo. As etapas a seguir atualizam o registro. Como sempre, tenha cuidado ao atualizar o registro.

1. Limpe a chave do registro:

    1. Aceda a `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Selecione a chave de `UpdateDetectionLastRunTime` e exclua os dados do valor > **OK**.

2. Execute a tarefa de Atualizações Automáticas do Office:

    1. Abra o aplicativo **Agendador de tarefas** no dispositivo.
    2. Expanda **Agendador de tarefas biblioteca** > **Microsoft** > **Office**.
    3. Selecione **Office Atualizações Automáticas 2,0** > **executar**:

        ![Abra o agendamento de tarefas e execute o Office Atualizações Automáticas](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Aguarde a conclusão da tarefa, o que pode levar vários minutos.

3. No aplicativo **Editor do registro** , vá para `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Verifique o valor de `UpdateChannel`.

    Ele deve ser atualizado com o valor definido na política. Em nosso exemplo, o valor deve ser definido como `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`.

Neste ponto, o canal de atualização do Office é alterado com êxito no dispositivo. Você pode abrir um aplicativo do Office 365 para um usuário que recebe essa atualização para verificar o status.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Forçar a sincronização do Office para atualizar as informações da conta  

Se você quiser fazer mais, você pode forçar o Office a obter a atualização da versão mais recente. As etapas a seguir só devem ser feitas como uma confirmação, ou se você precisar dos dispositivos para obter a atualização da versão mais recente desse canal rapidamente. Caso contrário, deixe o Office fazer seu trabalho e atualizar automaticamente.

### <a name="step-1-force-the-office-version-to-update"></a>Etapa 1: forçar a atualização da versão do Office

1. Confirme se a versão do Office dá suporte ao canal de atualização que você está escolhendo. O [histórico de atualizações do Office 365 ProPlus](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) lista os números de compilação que dão suporte aos diferentes canais de atualização.

2. No [modelo administrativo do Intune](administrative-templates-windows.md#create-a-template), vá para a configuração de **versão de destino** e insira a versão desejada.

    Sua configuração de **versão de destino** é semelhante à seguinte configuração:

    ![No modelo administrativo do Intune, defina a configuração de versão de destino para o Office](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Certifique-se de atribuir a política.
> - Se você alterar uma política existente, suas alterações afetarão todos os usuários atribuídos.
> - Se você estiver testando esse recurso, é recomendável criar uma política de teste e atribuir a política a um grupo de teste de usuários.

### <a name="step-2-check-the-office-version"></a>Etapa 2: verificar a versão do Office

Considere o uso dessas etapas para testar sua política antes de implantar a política para todos os usuários.

1. No aplicativo **Editor do registro** , vá para `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. Examine o valor `L_UpdateTargetVersion`. Depois que a política se aplica, o valor é definido para a versão que você inseriu, como `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    Neste ponto, a política do Intune é aplicada com êxito ao dispositivo.

3. Em seguida, você pode forçar o Office a atualizar. Abra um aplicativo do Office, como o Excel. Escolha Atualizar agora (possivelmente no menu **conta** ).

    A atualização leva vários minutos. Você pode confirmar se o Office está tentando obter a versão que você digitou:

      1. No dispositivo, vá para `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
      2. Abra o arquivo `VersionDescriptor.xml` e vá para a seção `<Version>`. A versão disponível deve ser a mesma versão que você inseriu na política do Intune, como:

          ![Verifique a seção versão no arquivo XML do Office descritor de versão](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. Depois que a atualização for instalada, o aplicativo do Office deverá mostrar a nova versão (por exemplo, no menu **conta** )

## <a name="next-steps"></a>Próximos passos

[Atualizar valores de canal para clientes do Office 365](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)

[Visão geral do serviço de política de nuvem do Office para Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Use modelos do Windows 10 para definir configurações de política de grupo (modelos ADMX) no Microsoft Intune](administrative-templates-windows.md)
