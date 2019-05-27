---
title: Configurar definições de proxy para o conector do Intune para o Active Directory
description: Explica como configurar o conector do Intune para o Active Directory trabalhar com servidores de proxy no local existentes.
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c47a7413d98467fffc26dee098a64cfeac770e4
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043548"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Trabalhar com servidores de proxy no local existentes

Este artigo explica como configurar o conector do Intune para o Active Directory trabalhar com servidores de proxy de saída. Destina-se para os clientes com ambientes de rede que tenham proxies existentes.

Para obter mais informações sobre como funcionam os conectores, consulte [conectores de Proxy de aplicações do AD Azure compreender](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Proxies de saída de omissão

Conectores têm componentes do sistema operacional subjacentes que efetuam pedidos de saída. Esses componentes automaticamente tentarem localizar um servidor proxy na rede usando o Proxy Auto-Discovery WPAD (Web).

Os componentes do SO tentam localizar um servidor proxy ao realizar uma pesquisa de DNS para wpad.domainsuffix. Se a pesquisa é resolvido no DNS, um pedido HTTP, em seguida, é feito para o endereço IP para wpad.dat. Este pedido torna-se o script de configuração de proxy no seu ambiente. O conector utiliza este script para selecionar um servidor de proxy de saída. No entanto, o tráfego de conector poderá ainda não passar por, devido às definições de configuração adicionais necessárias no proxy.

Pode configurar o conector para ignorar o proxy no local para se certificar de que utiliza conectividade direta aos serviços do Azure. Recomendamos esta abordagem, enquanto permite que a política de rede, porque significa que tenha uma menor configuração para manter.

Para desativar a utilização de proxy de saída para o conector, edite o: \Programas\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config de ficheiros e adicionar o endereço de proxy e a porta de proxy na seção mostrada neste exemplo de código:

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
Para garantir que o serviço Atualizador do Conetor também ignora o proxy, fazer uma alteração similar C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

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

Certifique-se de que fazer cópias dos arquivos originais, caso seja necessário reverter para os arquivos. config do padrão.

Assim que os ficheiros de configuração foram modificados, terá de reiniciar o serviço do conector do Intune. 

1. Open **Services. msc**.
2. Localize e selecione o **serviço do Intune ODJConnector**.
3. Selecione **reiniciar**.

![Captura de ecrã do reinício do serviço](media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Passos Seguintes

[Gerir os seus dispositivos](device-management.md)