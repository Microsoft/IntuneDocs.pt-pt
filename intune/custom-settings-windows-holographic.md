---
title: Definições personalizadas – Windows Holographic for Business dispositivos – Microsoft Intune
description: Adicione ou crie um perfil personalizado para utilizar as definições OMA-URI para dispositivos com o Windows Holographic for Business no Microsoft Intune, incluindo o Microsoft Hololens. Pode configurar definições de fornecedor de serviços de configuração da política (CSP) AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates e ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: reference
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee2084cd7b5ba2d51311b675c3f31c41cc83fc4f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490064"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>Utilizar definições personalizadas para dispositivos com o Windows Holographic for Business no Intune

Ao utilizar o Microsoft Intune, pode adicionar ou criar definições personalizadas para os seus dispositivos com o Windows Holographic for Business, com "perfis personalizados". Os perfis personalizados são uma funcionalidade do Intune. Foram concebidos para adicionar definições e funcionalidades de dispositivos que não estão incorporadas Intune.

Os perfis personalizados do Windows Holographic for Business utilizam as definições Open Mobile Alliance Uniform Resource Identifier (OMA-URI) para configurar diferentes funcionalidades. Estas definições são normalmente utilizadas por fabricantes de dispositivos móveis para controlar as funcionalidades no dispositivo.

O Windows Holographic for Business disponibiliza várias definições de fornecedores de serviços de configuração (CSPs). Para obter uma descrição geral do CSP, veja [Introdução a fornecedores de serviços de configuração (CSPs) para profissionais de TI](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Para obter CSPs específicos suportados pelo Windows Holographic, veja [CSPs suportados no Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Se estiver à procura de uma definição específica, lembre-se de que o [perfil de restrição de dispositivos com o Windows Holographic for Business](device-restrictions-windows-holographic.md) inclui várias definições incorporadas. Por isso, poderá não ter de introduzir valores personalizados.

Este artigo mostra-lhe como criar um perfil personalizado para dispositivos com o Windows Holographic for Business. Inclui também uma lista de definições OMA-URI recomendadas.

## <a name="create-the-profile"></a>Criar o perfil

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: Introduza um nome para o perfil, como `hololens custom profile`.
    - **Descrição**: Introduza uma descrição para o perfil.
    - **Plataforma**: Escolher **Windows 10 e posterior**.
    - **Tipo de perfil**: Escolher **personalizado**.

4. Em **Definições OMA-URI Personalizadas**, selecione **Adicionar**. Introduza as seguintes definições:

    - **Nome**: Introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição**: Introduza uma descrição que proporcione uma descrição geral da definição e outros detalhes importantes.
    - **OMA-URI** (sensível a maiúsculas e minúsculas): Introduza o OMA-URI que pretende utilizar como uma definição.
    - **Tipo de dados**: Escolha o tipo de dados que irá utilizar para esta definição de OMA-URI. As opções são:

        - Cadeia
        - Cadeia (ficheiro XML)
        - Data e Hora
        - Número inteiro
        - Vírgula flutuante
        - Booleano
        - Base64 (ficheiro)

    - **Valor**: Introduza o valor de dados que pretende associar ao OMA-URI que introduziu. O valor depende do tipo de dados que selecionou. Por exemplo, se optar por **Data e hora**, selecione o valor num seletor de datas.

    Depois de adicionar algumas definições, pode selecionar **Exportar**. A opção **Exportar** cria uma lista de todos os valores que adicionou num ficheiro de valores separados por vírgulas (.csv).

5. Selecione **OK** para guardar as alterações. Continue a adicionar mais definições conforme necessário.
6. Quanto terminar, selecione **OK** > **Criar** para criar o perfil do Intune. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**.

## <a name="recommended-custom-settings"></a>Definições personalizadas recomendadas

As seguintes definições são úteis para dispositivos com o Windows Holographic for Business:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Número inteiro<br/>0 – não permitido<br/>1 – permitido (predefinição)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Número inteiro<br/>0 – o serviço de atualização não é permitido. <br/>1 – o serviço de atualização é permitido (predefinição).|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Número inteiro<br/>0 – não permitido<br/>1 – permitido (predefinição)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Número inteiro<br/>0 – não configurado. O dispositivo instala todas as atualizações aplicáveis.<br/>1 – o dispositivo instala apenas as atualizações que são aplicáveis e estão na lista de Atualizações Aprovadas. Defina esta política para 1 se a equipa de TI quiser controlar a implementação das atualizações nos dispositivos, como quando é pedido um teste antes da implementação.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Número inteiro entre 0 e 23, em que 0=00:00 e 23=23:00<br/>O valor predefinido é 3.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Cadeia<br/>URL – o dispositivo procura atualizações do servidor WSUS no URL especificado.<br/>Não configurado – o dispositivo procura atualizações do Microsoft Update.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**Importante**<br/>Tem de ler e aceitar os EULAs de atualização em nome dos seus utilizadores finais. Caso contrário, ocorrerá uma falha de segurança nas obrigações contratuais e legais.|O nó para as aprovações de atualizações e a aceitação do EULA em nome do utilizador final.<br/><br/>Para mais informações, veja [Atualizar CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**Importante**<br/>O artigo AppLocker CSP utiliza exemplos de XML de escape. Para configurar as definições com os perfis personalizados do Intune, tem de utilizar XML simples.|Cadeia<br/>Para mais informações, veja [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp).|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Número inteiro<br/>0 – eliminar imediatamente quando o dispositivo voltar a um estado sem utilizadores atualmente ativos<br/>1 – eliminar quanto for atingido o limiar de capacidade de armazenamento (predefinição)<br/>2 – eliminar quando for atingido o limiar de capacidade de armazenamento e o limiar de inatividade do perfil|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|Booleano<br/>Verdadeiro – ativar<br/>Falso – desativar (predefinição)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Número inteiro<br/>O valor predefinido é 30.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Número inteiro<br/>O valor predefinido é 25.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Tipo de dados|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Número inteiro<br/>O valor predefinido é 50.|

## <a name="find-the-policies-you-can-configure"></a>Encontrar as políticas que pode configurar

Pode consultar a lista completa de todos os fornecedores de serviços de configuração (CSPs) que o Windows Holographic suporta em [CSPs suportados no Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nem todas as definições são compatíveis com todas as versões do Windows Holographic. A tabela em [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSPs suportados no Windows Holographic) apresenta as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições apresentadas em [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSPs suportados no Windows Holographic). Para saber se o Intune suporta a definição que pretende, abra o artigo referente a essa definição. Cada página de definição mostra a respetiva operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md).

Saiba como criar um perfil personalizado em [dispositivos Windows 10](custom-settings-windows-10.md).
