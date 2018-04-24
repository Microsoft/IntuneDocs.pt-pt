---
title: Definições personalizadas para dispositivos com o Windows Holographic for Business no Microsoft Intune – Azure | Microsoft Docs
description: Crie um perfil personalizado para utilizar as definições de OMA-URI para dispositivos com o Windows Holographic for Business no Microsoft Intune. Pode configurar definições de fornecedor de serviços de configuração da política (CSP) AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates e ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b349a61d61288f700294e04d029d825afba13445
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
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
    - **Nome da definição** – introduza um nome exclusivo para a definição OMA-URI para o ajudar a identificá-la na lista de definições.
    - **Descrição da definição** – opcionalmente, introduza uma descrição para a definição.
    - **Tipo de dados** – escolha entre:
        - **Cadeia**
        - **Cadeia (XML)**
        - **Data e hora**
        - **Número inteiro**
        - **Vírgula flutuante**
        - **Booleano**
    - **OMA-URI (sensível às maiúsculas e minúsculas)** – especifique o OMA-URI para o qual pretende fornecer uma definição.
    - **Valor** - indique o valor a associar ao OMA-URI que introduziu.
1. Quando tiver terminado, volte a **Criar Perfil** e clique em **Criar**.
O perfil é criado e apresentado na lista de perfis.

## <a name="recommended-custom-settings"></a>Definições personalizadas recomendadas

As seguintes definições são úteis para dispositivos com o Windows Holographic for Business:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Número inteiro<br>0 – não permitido<br>1 – permitido (predefinição)|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Número inteiro<br>0 – não permitido<br>1 – permitido (predefinição)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Número inteiro<br>0 – o serviço de atualização não é permitido. <br>1 – o serviço de atualização é permitido (predefinição).|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Cadeia<br>URL – o dispositivo procura atualizações do servidor WSUS no URL especificado.<br>Não configurado – o dispositivo procura atualizações do Microsoft Update.|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Número inteiro<br>0 – não configurado. O dispositivo instala todas as atualizações aplicáveis.<br>1 – o dispositivo instala apenas as atualizações que são aplicáveis e estão na lista de Atualizações Aprovadas. Defina esta política para 1 se a equipa de TI quiser controlar a implementação das atualizações nos dispositivos, como quando é pedido um teste antes da implementação.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**Importante**<br>Tem de ler e aceitar os EULAs de atualização em nome dos seus utilizadores finais. Caso contrário, ocorrerá uma falha de segurança nas obrigações contratuais e legais.|O nó para as aprovações de atualizações e a aceitação do EULA em nome do utilizador final.|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

---
|OMA-URI|Tipo de dados  |
|---------|---------|
|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**Importante**<br>O artigo AppLocker CSP utiliza exemplos de XML de escape. Para configurar as definições com os perfis personalizados do Intune, tem de utilizar XML simples.|Cadeia<br>Para obter mais informações, veja [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp).|

## <a name="find-the-policies-you-can-configure"></a>Encontrar as políticas que pode configurar

Pode consultar a lista completa de todos os fornecedores de serviços de configuração (CSPs) que o Windows Holographic suporta em [CSPs suportados no Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nem todas as definições são compatíveis com todas as versões do Windows Holographic. A tabela no artigo Windows indica quais as versões suportadas para cada CSP.

Além disso, o Intune não suporta todas as definições listadas no artigo. Para saber se o Intune suporta a definição que pretende, abra o artigo referente a essa definição. Cada página de definição mostra a sua operação suportada. Para trabalhar com o Intune, a definição tem de suportar as operações **Adicionar** ou **Substituir**.
