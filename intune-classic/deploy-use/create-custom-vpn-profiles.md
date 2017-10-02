---
title: "Configurações personalizadas para perfis VPN do Microsoft Intune"
description: "Utilize configurações personalizadas para criar perfis de VPN no Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
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
ms.openlocfilehash: d640dd9e80965561e5ddf24c42b5ba4278e49892
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
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

Em seguida, [implemente a política](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy) como habitualmente.

## <a name="example-uri-settings"></a>Exemplo de definições de URI

Estas definições podem ser utilizadas para criar uma configuração personalizada para uma VPN numa empresa fictícia denominada Contoso.
Para obter mais informações sobre todas as definições que pode utilizar, consulte [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx).

**VPN nativa da Contoso (IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
   <EapMethod>
      <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
      <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
      <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
      <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
   </EapMethod>
   <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
      <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
         <Type>13</Type>
         <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
            <CredentialsSource>
               <CertificateStore>
                  <SimpleCertSelection>true</SimpleCertSelection>
               </CertificateStore>
            </CredentialsSource>
            <ServerValidation>
               <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
               <ServerNames></ServerNames>
            </ServerValidation>
            <DifferentUsername>false</DifferentUsername>
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
Verdadeiro

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Para quaisquer perguntas sobre a forma como estas definições devem ser utilizadas ou para obter mais detalhes sobre o que fazem, os clientes devem consultar a [documentação do fornecedor de serviços de configuração (CSP)](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx).

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
