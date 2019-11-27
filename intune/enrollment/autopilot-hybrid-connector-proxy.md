---
title: Definir configurações de proxy para o conector do Intune para Active Directory
description: Aborda como configurar o conector do Intune para Active Directory para trabalhar com servidores proxy locais existentes.
keywords: ''
author: master11218
ms.author: erikje
manager: dougeby
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a1af2e7c8aff281e04e92344b3e2c762bb23e0a
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465756"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Trabalhar com servidores proxy locais existentes

Este artigo explica como configurar o conector do Intune para Active Directory para trabalhar com servidores proxy de saída. Ele destina-se a clientes com ambientes de rede que têm proxies existentes.

Para obter mais informações sobre como os conectores funcionam, consulte [entender os conectores de proxy de aplicativo do AD do Azure](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Ignorar proxies de saída

OS conectores têm componentes de sistema operacional subjacentes que fazem solicitações de saída. Esses componentes tentam automaticamente localizar um servidor proxy na rede usando a descoberta automática de proxy da Web (WPAD).

Os componentes do sistema operacional tentam localizar um servidor proxy executando uma pesquisa de DNS para WPAD. domainsuffix. Se a pesquisa for resolvida no DNS, uma solicitação HTTP será feita para o endereço IP para WPAD. dat. Essa solicitação se torna o script de configuração de proxy em seu ambiente. O conector usa esse script para selecionar um servidor proxy de saída. No entanto, o tráfego do conector ainda pode não passar, devido às definições de configuração adicionais necessárias no proxy.

Você pode configurar o conector para ignorar o proxy local para garantir que ele use conectividade direta com os serviços do Azure. Recomendamos essa abordagem, desde que sua política de rede permita isso, porque significa que você tem uma menos configuração para manter.

Para desabilitar o uso do proxy de saída para o conector, edite o arquivo: \Arquivos de Programas\microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config e adicione o endereço de proxy e a porta do proxy na seção mostrada neste exemplo de código:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Para garantir que o serviço de Atualizador do Conector também ignore o proxy, faça uma alteração semelhante em C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Certifique-se de fazer cópias dos arquivos originais, caso precise reverter para os arquivos. config padrão.

Depois que os arquivos de configuração tiverem sido modificados, será necessário reiniciar o serviço do conector do Intune. 

1. Abra **Services. msc**.
2. Localize e selecione o **serviço ODJConnector do Intune**.
3. Selecione **reiniciar**.

![Captura de tela da reinicialização do serviço](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Passos Seguintes

[Gerenciar seus dispositivos](../remote-actions/device-management.md)
