---
title: Definições personalizadas para dispositivos com o Windows Holographic for Business no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil personalizado para utilizar as definições de OMA-URI para dispositivos com o Windows Holographic for Business no Microsoft Intune. Pode configurar definições de fornecedor de serviços de configuração da política (CSP) AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates e ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7272e8e088ae2c2ecad1756233281c42a80a279b
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "32328083"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Definições personalizadas para dispositivos com o Windows Holographic for Business no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Utilize o perfil **personalizado** do Microsoft Intune para Windows Holographic for Business para implementar definições de OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos. O Windows Holographic for Business disponibiliza várias definições de fornecedores de serviços de configuração (CSPs). Para obter uma descrição geral do CSP, veja [Introdução a fornecedores de serviços de configuração (CSPs) para profissionais de TI](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Para obter CSPs específicos suportados pelo Windows Holographic, veja [CSPs suportados no Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Se estiver à procura de uma determinada definição, lembre-se de que o [perfil de restrição de dispositivos do Windows Holographic for Business](device-restrictions-windows-holographic.md) contém muitas definições incorporadas e não necessita que especifique valores personalizados.

## <a name="create-the-custom-oma-uri-profile"></a>Criar um perfil de OMA-URI personalizado

1. Utilize as instruções em [Configurar definições personalizadas dos dispositivos no Microsoft Intune](custom-settings-configure.md) para começar.
2. Em **Criar Perfil**, selecione **Definições** para adicionar uma ou mais definições OMA-URI.
3. Em **Definições de OMA-URI Personalizadas**, clique em **Adicionar** para adicionar um novo valor. Também pode clicar em **Exportar** para criar uma lista de todos os valores que configurou num ficheiro de valores separados por vírgulas (.csv).
4. Para cada definição OMA-URI que pretende adicionar, introduza as informações seguintes:
  - **Nome da definição**: introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
  - **Descrição da definição**: opcionalmente, introduza uma descrição para a definição.
  - **Tipo de dados**: escolha entre:
    - **Cadeia**
    - **Cadeia (XML)**
    - **Data e hora**
    - **Número inteiro**
    - **Vírgula flutuante**
    - **Booleano**
  - **OMA-URI (sensível às maiúsculas e minúsculas)**: introduza o OMA-URI para o qual pretende proporcionar uma definição.
  - **Valor**: introduza o valor a associar ao OMA-URI que introduziu.
5. Quando tiver terminado, volte a **Criar Perfil** e clique em **Criar**. O perfil é criado e apresentado na lista de perfis.

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

Pode consultar a lista completa de todos os fornecedores de serviços de configuração (CSPs) que o Windows Holographic suporta em [CSPs suportados no Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nem todas as definições são compatíveis com todas as versões do Windows Holographic. A tabela no artigo Windows indica quais as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições listadas no artigo. Para saber se o Intune suporta a definição que pretende, abra o artigo referente a essa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.
