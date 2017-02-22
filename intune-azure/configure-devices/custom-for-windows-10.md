---
title: "Definições personalizadas do Intune para dispositivos Windows 10 | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba quais são as definições que pode utilizar num perfil personalizado do Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0da8c0fe399f76f43439cc66eaecd12bb454f9a6
ms.openlocfilehash: 05856480f8bb76e561f2b459d4ab800f9909a40a


---

# <a name="custom-device-settings-for-windows-10-devices-in-intune-azure-preview"></a>Definições personalizadas para dispositivos Windows 10 na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 Utilize o perfil **personalizado** do Microsoft Intune para Windows 10 e Windows 10 Mobile para implementar definições OMA-URI (Open Mobile Alliance Uniform Resource Identifier) que podem ser utilizadas para controlar as funcionalidades nos dispositivos. O Windows 10 disponibiliza várias definições através de [Fornecedor do Serviço de Configuração da Política (CSP de política)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

1. Utilize as instruções em [Como configurar definições personalizadas dos dispositivos no Microsoft Intune](how-to-configure-custom-settings.md) para começar.
2. No painel **Criar Perfil**, escolha **Definições** para adicionar uma ou mais definições OMA-URI.
3. No painel **Definições de OMA-URI Personalizadas**, clique em **Adicionar** para adicionar um novo valor. Também pode clicar em **Exportar** para criar uma lista de todos os valores que configurou num ficheiro de valores separados por vírgulas (.csv).
4. Para cada definição OMA-URI que pretende adicionar, introduza as informações seguintes. Utilize a lista neste tópico para saber mais sobre as definições que pode utilizar:
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
5. Quando tiver terminado, volte ao painel **Criar Perfil** e clique em **Criar**.
O perfil será criado e é apresentado no painel da lista de perfis.

## <a name="example"></a>Exemplo
Na captura de ecrã abaixo, a definição **Connectivity/AllowVPNOverCellular** foi ativada. Isto permite que um dispositivo Windows 10 abra uma ligação VPN quando estiver numa rede celular.

> ![Exemplo de uma política personalizada que contém as definições de VPN](./media/custom-policy-example.png)


## <a name="policy-settings"></a>Definições de política

|Nome da política e URI|Detalhes|
|---------------|------------|-----------|
|**Permitir Atualização Automática**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Apenas ambiente de trabalho<br>**Tipo de dados:** Número inteiro<br />**Valores:** **0** - **5** (predefinição: **1**)|
|**Agendar Dia da Instalação**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Apenas dispositivos móveis<br>**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – Todos os dias (predefinição)<br>**1** – Domingo<br>**2** – Segunda-feira<br>**3** – Terça-feira<br>**4** – Quarta-feira<br>**5** – Quinta-feira<br>**6** – Sexta-feira<br>**7** – Sábado|
|**Agendar Hora da Instalação**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – **23** horas (**0** é meia-noite) (predefinição: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** - o utilizador não pode definir o temporizador do período de tolerância da palavra-passe; o valor está definido como “sempre”<br>**1** - o utilizador pode definir o temporizador do período de tolerância da palavra-passe (predefinição)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não permitir a **utilização de ligação Wi-Fi**.<br>**1** –** permitir a utilização de ligação Wi-Fi** (predefinição)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Ambiente de trabalho e dispositivos móveis<br>**Tipo de dados:** Número inteiro<br />**Valores:** **0** – Não permitir Partilha da Internet, **1** – Permitir Partilha da Internet (predefinição)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não é permitida uma ligação Wi-Fi fora da MDM aprovisionada.<br>**1** – é permitido adicionar novos SSIDs de rede para além dos que já são aprovisionados pelo MDM (predefinição)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Ambiente de trabalho e dispositivos móveis<br>**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não permitido (definição apenas para empresas)<br>**1** – limitado<br>**2** – completo (predefinição)<br>**3** – completo e informações de diagnóstico|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não permitido<br>**1**- apenas definições (predefinição)<br>**2**- definições e experimentação|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** - não permitir modo Anti Roubo<br>**1** – preferência do utilizador (predefinição)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não é permitida VPN por rede móvel<br>**1** – a VPN pode utilizar qualquer ligação, incluindo rede móvel (predefinição)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não permitir que o utilizador ligue o Bluetooth.<br>**1** – reservado. O utilizador pode ligar e configurar o Bluetooth (não suportado no Windows Phone 8.1 para MDM, EAS, ambiente de trabalho do Windows 10 ou Windows 10 Mobile)<br>**2** - permitido. O utilizador pode ligar e configurar o Bluetooth (predefinição)|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – Não permitir roaming, **1** – Permitir roaming (predefinição)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** (predefinição), **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0**, **1** (predefinição)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** (predefinição), **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** (predefinição), **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** (predefinição), **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0**, **1** (predefinição)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** (predefinição), **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** (predefinição), **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não permitir<br>O Dicionário Expandido Aberto está desativado.<br>O utilizador não pode:<br>- Adicionar um novo Dicionário Expandido Aberto<br />- Adicionar um novo ficheiro de configuração de integração de pesquisa<br>- Utilizar a funcionalidade de candidato na nuvem<br>- Enviar palavras registadas pelo utilizador.<br>**1** - permitir<br>É possível adicionar e utilizar um Dicionário Expandido Aberto como predefinição. Além disso, a função de integração de pesquisas pode ser utilizada como predefinição.<br>O utilizador pode:<br>Utilizar a funcionalidade de candidato na nuvem.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** - registo de conversões incorretas desativado.<br>**1** – registo de conversões incorretas ativado (predefinição)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não é filtrado nenhum caráter (predefinição)<br>**1** – são filtrados todos os carateres, exceto os Shift JIS|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br />**0** – não é filtrado nenhum caráter (predefinição)<br>**1** – são filtrados todos os carateres, exceto os JIS0208|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não é filtrado nenhum caráter (predefinição)<br>**1** – são filtrados todos os carateres, exceto os JIS0208 ou os EUDC|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – rígida, filtragem mais estrita de conteúdos para adultos<br>**1** – moderada, filtragem moderada de conteúdos para adultos (os resultados de pesquisa válidos não serão filtrados - predefinição)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**Forçar Tamanho Inicial**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** - permitir que o utilizador altere o tamanho (predefinição)<br>**1** - forçar não utilização do ecrã inteiro<br>**2** - forçar ecrã inteiro|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0**: não difere da atualização (mantenha-se no ramo atual, CB - predefinição)<br>**1**: permite que as atualizações sejam adiadas (o dispositivo segue o ramo atual para empresa, CBB, regras)<br />Para mais detalhes, consulte:<br>[Introdução à manutenção do Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Ambiente de trabalho e dispositivos móveis<br>**Descrição:** política para diferir atualizações de software para até quatro semanas<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br> **0**: aplicar atualizações imediatamente (predefinição)<br>**1**-**4**: número de semanas para diferir atualizações de software.<br />Para mais detalhes, consulte:<br>[Introdução à manutenção do Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Ambiente de trabalho e dispositivos móveis<br>**Descrição:** política para diferir atualizações de funcionalidade para até oito meses<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0**: aplicar atualizações imediatamente (predefinição)<br>**1**-**8**: número de meses para diferir atualizações de funcionalidade.<br />Para mais detalhes, consulte:<br>[Introdução à manutenção do Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plano de implementação do Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Ambiente de trabalho e dispositivos móveis<br>**Descrição:** permite que um dispositivo deixe de receber atualizações durante cinco semanas.<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0**: aplicar atualizações imediatamente (predefinição)<br>**1**: colocar atualizações em pausa (expira após cinco semanas)|

## <a name="windows-defender-settings"></a>Definições do Windows Defender

|Nome da política e URI|Detalhes|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – monitorizar todos os ficheiros (predefinição)<br>**1** – monitorizar ficheiros recebidos<br>**2** – monitorizar ficheiros enviados|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** - **90** – representa o período de retenção do software maligno<br>**Predefinição:** **0** – mantém na pasta de quarentena indefinidamente e não remove automaticamente|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**1** – análise rápida (predefinição)<br>**2** – análise completa|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – todos os dias (predefinição)<br>**1** – Segunda-feira<br>**2** – Terça-feira<br>**3** – Quarta-feira<br>**4** – Quinta-feira<br>**5** – Sexta-feira<br>**6** – Sábado<br>**7** – Domingo<br>**8** – nenhuma análise agendada|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – 24:00<br>**60** – 01:00<br>**120** – 2:00 (predefinição)<br>**180** – 03:00<br>**240** – 04:00<br>**300** – 05:00<br>**360** – 06:00<br>**420** – 07:00<br>**480** – 08:00<br>**540** – 09:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1381** – janela de manutenção|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Apenas ambiente de trabalho<br>**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – 24:00<br>**60** – 01:00<br>**120** – 2:00 (predefinição)<br>**180** – 03:00<br>**240** – 04:00<br>**300** – 05:00<br>**360** – 06:00<br>**420** – 07:00<br>**480** – 08:00<br>**540** – 09:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1380** – 23:00|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** - **100** (predefinição: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br>**Valores:** **0** – não permitido (predefinição), **1** – permitido|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido (predefinição), **1** – permitido|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido, **1** – permitido (predefinição) – também é executada quando o RTP está definido como permitido|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – não verificar assinaturas num intervalo<br>**1** - verificar assinaturas a cada hora<br>**2** – verificar a cada duas horas, etc.<br>**24** - verificar todos os dias<br>**Valor predefinido:** 8 – verificar a cada oito horas|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitido **1** – permitido (predefinição)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – perguntar sempre (predefinição)<br>**1** – enviar automaticamente amostras seguras<br>**2** – nunca enviar<br>**1** – enviar automaticamente todas as amostras|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Apenas ambiente de trabalho<br />**Tipo de dados:** Cadeia<br />**Valores:**<br>*&lt;lista de extensões separadas por ponto e vírgula&gt;* Por exemplo, **obj;lib**<br>**Predefinição**: não é excluída nenhuma extensão|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Apenas ambiente de trabalho<br />**Tipo de dados:** Cadeia<br />**Valores:**<br />*&lt;lista de caminhos separados por ponto e vírgula&gt;*<br />Exemplo: **c:\test;c:\test1.exe**<br />**Valor predefinido:** Não são excluídos caminhos|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Apenas ambiente de trabalho<br />**Tipo de dados:** Cadeia<br />**Valores:**<br>*&lt;lista de caminhos separados por ponto e vírgula&gt;*<br>Exemplo: **c:\test.exe;c:\test1.exe**<br>**Valor predefinido:** Não são excluídos processos|

## <a name="edge-browser-settings"></a>Definições do browser Edge

|Nome da política e URI|Detalhes|
|---------------|------------|-----------|
|**Permitir Browser**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Apenas dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0**: navegação desativada, **1**: navegação ativada (predefinição)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0**: não mostrar sugestões, **1**: mostrar sugestões (predefinição)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0**: desativado (abrir sites da intranet no browser Edge - predefinição)<br>**1** - ativado (abrir sites da intranet no Internet Explorer).|
|**Permitir Do Not Track**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Ambiente de trabalho e dispositivos móveis)<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – desativado (DNT não enviado – predefinição), **1** – ativado (enviar DNT)|
|**Configurar SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – não permitir, **1** – permitir (predefinição)|
|**Permitir Pop-ups**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – bloquear janelas de pop-up (predefinição), **1** – permitir janelas de pop-up|
|**Permitir Cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – permitir cookies de todos os sites (predefinição)<br>**1** – bloquear apenas cookies de terceiros<br>**2** – bloquear todos os cookies|
|**Permitir Guardar Palavra-passe**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Ambiente de trabalho e dispositivos móveis<br />**Tipo de dados:** Número inteiro<br />**Valores:**<br>**0** – o gestor de palavras-passe está desativado; <br>**1** – o gestor de palavras-passe está ativado (predefinição)|
|**Permitir Preenchimento Automático**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Apenas ambiente de trabalho<br />**Tipo de dados:** Número inteiro<br />**Valores:** **0** – desativado (predefinição), **1** – ativado|
|**Configurar a Lista de Sites da Empresa**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Apenas ambiente de trabalho<br />**Tipo de dados:** Cadeia<br />**Valores:<br>**0** – Não configurado<br>**1** – Utilizar a localização da lista de sites do modo empresarial do IE, se estiver configurada (predefinição)<br>**2** – Especificar a localização da lista de sites da empresa|



<!--HONumber=Feb17_HO1-->


