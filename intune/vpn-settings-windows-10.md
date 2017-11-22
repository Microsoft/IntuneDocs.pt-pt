---
title: "Definições de VPN do Intune para dispositivos com o Windows 10"
titlesuffix: Azure portal
description: "Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos Windows 10.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6de18a341f684730c74aa824c0ae8f7bdca1a4f8
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/02/2017
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Definições de VPN para dispositivos com o Windows 10 no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Consoante as definições que escolher, nem todos os valores na lista abaixo serão configuráveis.


## <a name="base-vpn-settings"></a>Definições de VPN Base


- **Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores** – Adicione um ou mais servidores VPN aos quais os dispositivos serão ligados.
    - **Adicionar** – Abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
        - **Descrição** – Especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
        - **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predefinido** – Ativa este servidor como o servidor predefinido que os dispositivos vão utilizar para estabelecer a ligação. Confirme que predefine apenas um servidor.
    - **Importar** – Navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
    - **Exportar** – Exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

**Tipo de ligação** – Selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
- **Automático**
- **Check Point Capsule VPN**
- **VPN do Citrix**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**


**Grupo ou domínio de início de sessão** (apenas no Dell SonicWALL Mobile Connect) – Especifique o nome do grupo ou domínio de início de sessão ao qual se pretende ligar.

**XML personalizado**/**XML de EAP** – Especifique quaisquer comandos XML personalizados que configuram a ligação VPN.

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

Consulte a documentação de cada fabricante relativa à VPN para obter mais informações sobre como escrever comandos XML personalizados.

**Divisão de túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utilizará a ligação VPN para aceder aos ficheiros de trabalho, mas utilizará a rede padrão do hotel para a navegação normal na Internet.
- **Dividir rotas de túnel para esta ligação VPN** – Adicione rotas opcionais para fornecedores de VPN de terceiros. Especifique um prefixo de destino e um tamanho de prefixo para cada um.

## <a name="apps-and-traffic-rules"></a>Regras de Aplicações e Tráfego

**Restringir a ligação VPN a estas aplicações** – Ative esta opção se quiser que apenas as aplicações especificadas utilizem a ligação VPN.
**Aplicações Associadas** – Indique uma lista de aplicações que vão utilizar automaticamente a ligação VPN. O tipo de aplicação irá determinar o identificador de aplicações. Para uma aplicação universal, forneça o nome de família do pacote. Para uma aplicação de ambiente de trabalho, forneça o caminho do ficheiro da aplicação.

>[!IMPORTANT]
>Recomendamos a proteção de todas as listas de aplicações que compilar para utilização na configuração da VPN por aplicação. Se um utilizador não autorizado modificar a sua lista e importá-la para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN para aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

**Regras de tráfego de rede para esta ligação VPN** – Selecione os protocolos, as portas locais e remotas e os intervalos de endereços que vão estar ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utilizará os protocolos, portas e intervalos de endereços que especificar nessa regra.


## <a name="conditional-access"></a>Acesso Condicional

**Acesso condicional nesta ligação VPN** – ativa o fluxo de conformidade de dispositivo do cliente. Quando estiver ativado, o cliente de VPN tentará comunicar com o Azure Active Directory para obter um certificado para utilizar para autenticação. O VPN deve estar configurado para utilizar a autenticação de certificado e o servidor VPN tem de confiar no servidor devolvido pelo Azure Active Directory.

**Início de sessão único (SSO) com certificado alternativo** – para a conformidade do dispositivo, utilize um certificado diferente do certificado de autenticação do VPN para a autenticação Kerberos. Especifique o certificado com as seguintes definições: 

- **Utilização de chave avançada** – nome da utilização de chave avançada (EKU).
- **Identificador de Objeto** – identificador de objeto do EKU.
- **Hash do emissor** – thumbprint do certificado SSO.

## <a name="dns-settings"></a>Definições de DNS

**Nomes e servidores DNS para esta ligação VPN** – Selecione os servidores DNS que a ligação VPN utilizará depois de a ligação ser estabelecida.
Para cada servidor. especifique:
- **Nome DNS**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, consulte a documentação do Windows Server.
- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Utilizar um servidor proxy** – Ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
    - **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
    - **Número de porta** – Introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, consulte a documentação do Windows Server.
