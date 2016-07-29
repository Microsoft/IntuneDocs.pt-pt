---
title: "Configurações personalizadas para perfis VPN | Microsoft Intune"
description: "Utilize configurações personalizadas para criar perfis de VPN no Intune."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9a124663a80bb477d0312faa0fb43e4457ba8246
ms.openlocfilehash: ae5ac5c697195f8b45f500cfa9d0de24953f8cb0


---

# Configurações personalizadas para perfis VPN

## Criar uma configuração personalizada
Pode utilizar configurações personalizadas para criar perfis VPN no Intune. Para criar uma configuração personalizada:

   1. Na consola de administração do Intune, **Política** -> **Adicionar Política** -> *<Expand platform>* -> **Configuração personalizada** -> **Criar Política**.
   2. Forneça um nome para a política.
   3. Para cada definição de URI, clique em **Adicionar** e forneça as informações pedidas. Segue-se um exemplo:

   ![Caixa de diálogo de configuração personalizada de perfil VPN](./media/Intune_Add_VPN_URI.png)

   4.  Após introduzir todas as definições de URI, clique em **Guardar política** e, em seguida, implemente a política.

## Implementar uma política de configuração

1.  Na área de trabalho **Política** , selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Fechar a caixa de diálogo sem implementar a política** - clique em **Cancelar**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

##Exemplo de definições de URI para uma configuração de perfil VPN personalizada
Seguem-se entradas de exemplo para valores URI para criar uma configuração personalizada para uma VPN numa empresa fictícia denominada Contoso. Para obter mais informações, como o tipo de dados para cada entrada, consulte [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)

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

Para quaisquer perguntas sobre a forma como estas definições devem ser utilizadas ou para obter mais detalhes sobre o que fazem, os clientes devem consultar a documentação do CSP: https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx

## Definições de URI para VPN por aplicação Android no PulseSecure
### URI PERSONALIZADO PARA LISTA DE PACOTES
-  Tipo de dados = Cadeia
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList
-  Valor = Lista de pacotes separada por delimitadores.
   - Delimitadores: ponto e vírgula (;), dois pontos (:), vírgula (,), barra (|)

Exemplos:
- com.android.chrome
- com.android.chrome;com.android.browser

### URI PERSONALIZADO PARA MODO (OPCIONAL)
- Tipo de Dados = Cadeia
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Notas
> - Utilize o mesmo *nome* que atribuiu ao perfil personalizado
> - Valores possíveis: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - Assume a predefinição *GLOBAL* se não for fornecido nenhum PackageList (retrocompatibilidade com perfis ao nível do sistema)
> - Assume a predefinição *WHITELIST* se for fornecido um PackageList


### Consulte também
(Ligações VPN no Microsoft Intune)[vpn-connections-in-microsoft-intune.md]



<!--HONumber=Jul16_HO4-->


