---
title: "Definições de VPN do Intune para dispositivos com o Windows 10"
titlesuffix: Azure portal
description: "Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos Windows 10."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d126853051bb4a6c2f1ea6fbd54195ae06254b51
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2018
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Definições de VPN para dispositivos com o Windows 10 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

> [!NOTE]
> Estas definições também se aplicam a dispositivos com o Windows Holographic for Business.


## <a name="base-vpn-settings"></a>Definições de VPN Base


- **Nome da ligação** – introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores** – adicione um ou mais servidores VPN aos quais os dispositivos são ligados.
    - **Adicionar** – abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
        - **Descrição** – especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
        - **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predefinido** – define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Certifique-se de que predefine apenas um servidor.
    - **Importar** – navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
    - **Exportar** – exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

**Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
- **Automático**
- **Check Point Capsule VPN**
- **VPN do Citrix**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**


**Grupo ou domínio de início de sessão** (apenas no Dell SonicWALL Mobile Connect) – especifique o nome do grupo ou domínio de início de sessão ao qual se pretende ligar.

**XML personalizado**/**XML de EAP** – especifique quaisquer comandos XML personalizados que configuram a ligação VPN.

**Exemplo para o Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exemplo para o CheckPoint Mobile VPN:**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exemplo para o Dell SonicWALL Mobile Connect:**

```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exemplo para o F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Para obter mais informações sobre como escrever comandos XML personalizados, veja a documentação de cada fabricante relativa à VPN.

Para obter mais informações sobre a criação de XML de EAP, veja [Configuração de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

**Divisão de túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utilizará a ligação VPN para aceder aos ficheiros de trabalho, mas utilizará a rede padrão do hotel para a navegação normal na Internet.
- **Dividir rotas de túnel para esta ligação VPN** – adicione rotas opcionais para fornecedores de VPN de terceiros. Especifique um prefixo de destino e um tamanho de prefixo para cada um.

## <a name="apps-and-traffic-rules"></a>Regras de Aplicações e Tráfego

**Restringir a ligação VPN a estas aplicações** – ative esta opção se quiser que apenas as aplicações especificadas utilizem a ligação VPN.
**Aplicações Associadas** – forneça uma lista de aplicações que utilizam automaticamente a ligação VPN. O tipo de aplicação determina o identificador de aplicação. Para uma aplicação universal, forneça o nome de família do pacote. Para uma aplicação de ambiente de trabalho, forneça o caminho do ficheiro da aplicação.

>[!IMPORTANT]
>Recomendamos a proteção de todas as listas de aplicações que compilar para utilização na configuração da VPN por aplicação. Se um utilizador não autorizado modificar a sua lista e importá-la para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN para aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

**Regras de tráfego de rede para esta ligação VPN** – selecione os protocolos, as portas locais e remotas e os intervalos de endereços que estão ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utilizará os protocolos, portas e intervalos de endereços que especificar nessa regra.


## <a name="conditional-access"></a>Acesso Condicional

**Acesso condicional nesta ligação VPN** – ativa o fluxo de conformidade de dispositivo do cliente. Quando estiver ativado, o cliente VPN tenta comunicar com o Azure Active Directory para obter um certificado para utilizar para autenticação. O VPN deve estar configurado para utilizar a autenticação de certificado e o servidor VPN tem de confiar no servidor devolvido pelo Azure Active Directory.

**Início de sessão único (SSO) com certificado alternativo** – para a conformidade do dispositivo, utilize um certificado diferente do certificado de autenticação do VPN para a autenticação Kerberos. Especifique o certificado com as seguintes definições: 

- **Utilização de chave avançada** – nome da utilização de chave avançada (EKU).
- **Identificador de Objeto** – identificador de objeto do EKU.
- **Hash do emissor** – thumbprint do certificado SSO.

## <a name="dns-settings"></a>Definições de DNS

**Nomes e servidores DNS para esta ligação VPN** – selecione os servidores DNS que a ligação VPN utilizará depois de a ligação ser estabelecida.
Para cada servidor. especifique:
- **Nome DNS**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, veja a documentação do Windows Server.
- **Script de configuração automática** – utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com) que contém o ficheiro de configuração.
- **Utilizar um servidor proxy** – ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
    - **Endereço** – introduza o endereço do servidor proxy (como um endereço IP).
    - **Número de porta** – introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, veja a documentação do Windows Server.
