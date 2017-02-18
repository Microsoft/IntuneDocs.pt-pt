---
title: "Configurações personalizadas para perfis VPN do Microsoft Intune | Documentos da Microsoft"
description: "Utilize configurações personalizadas para criar perfis de VPN no Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f2b364b2c57adab33df2a8e6b34c1f30c02988d3
ms.openlocfilehash: 9dbb44981c1525e6137dd8a469b1582731ee9719


---

# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Configurações personalizadas para perfis VPN do Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>Criar uma configuração personalizada
Pode utilizar políticas de configuração personalizada do Intune para criar perfis VPN para:

* Dispositivos a executar o Android 4 e posterior
* Dispositivos Android for Work
* Dispositivos inscritos com Windows 8.1 e posterior
* Dispositivos a executar o Windows Phone 8.1 e posterior
* Computadores inscritos com o Windows 10 
* Dispositivo com o Windows 10 Mobile

Este tipo de política pode ser útil quando as políticas de VPN do Intune padrão não contêm as definições que pretende utilizar.

## <a name="to-create-a-custom-configuration-policy"></a>Para criar uma política de configuração personalizada:

   1. Na [consola de administração do Intune](https://manage.microsoft.com), selecione **Política** > **Adicionar Política** > *Expandir plataforma* > **Configuração personalizada** > **Criar Política**.
   2. Introduza um nome para a política.
   3. Para cada definição de URI que pretende especificar, selecione **Adicionar** e forneça as informações pedidas. Segue-se um exemplo:

   ![Caixa de diálogo de configuração personalizada de perfil VPN](./media/Intune_Add_VPN_URI.png)

   4.  Após introduzir todas as definições de URI, escolha **Save policy** e, em seguida, implemente a política.

Em seguida, [implemente a política](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) como habitualmente.

## <a name="example-uri-settings"></a>Exemplo de definições de URI

Estas definições podem ser utilizadas para criar uma configuração personalizada para uma VPN numa empresa fictícia denominada Contoso.
Para obter mais informações sobre todas as definições que pode utilizar, consulte [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx).

VPN nativa da Contoso (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Para quaisquer perguntas sobre a forma como estas definições devem ser utilizadas ou para obter mais detalhes sobre o que fazem, os clientes devem consultar a documentação do fornecedor de serviços de configuração (CSP): https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx.

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>Definições de URI para VPN por aplicação Android no PulseSecure
### <a name="custom-uri-for-package-list"></a>URI PERSONALIZADO PARA LISTA DE PACOTES
-  Tipo de dados = Cadeia
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  Valor = Lista de pacotes separada por delimitadores.
   - Delimitadores: ponto e vírgula (;), dois pontos (:), vírgula (,), barra (|)

Exemplos:
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>URI PERSONALIZADO PARA MODO (OPCIONAL)
- Tipo de Dados = Cadeia
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Notas
> - Utilize o mesmo *nome* que atribuiu ao perfil personalizado
> - Valores possíveis: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - Assume a predefinição *GLOBAL* se não for fornecido nenhum PackageList (retrocompatibilidade com perfis ao nível do sistema)
> - Assume a predefinição *WHITELIST* se for fornecido um PackageList


### <a name="see-also"></a>Consulte também
[Ligações VPN no Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


