---
title: Ver as definições de VPN no Microsoft Intune – Azure | Microsoft Docs
description: Conheça e leia sobre as definições de VPN disponíveis no Microsoft Intune, para que são utilizadas e o que fazem, incluindo as regras de tráfego, acesso condicional e as definições de DNS e proxy para dispositivos Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 787501892d0955e3396bc8f37e5da8ba0d312c74
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>Leia sobre as definições de VPN no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode configurar as ligações VPN com o Intune. Este artigo descreve estas definições, as regras de tráfego, o acesso condicional e as definições de DNS e proxy.

Estas definições aplicam-se a:

- Dispositivos com o Windows 10
- Dispositivos com o Windows Holographic for Business

Consoante as definições que escolher, nem todos os valores são configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores**: adicione um ou mais servidores VPN aos quais os dispositivos são ligados.
  - **Adicionar**: abre **Adicionar Linha**, onde pode introduzir as seguintes informações:
    - **Descrição**: introduza um nome descritivo para o servidor, como **Servidor VPN Contoso**.
    - **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados, tal como **192.168.1.1** ou **vpn.contoso.com**.
    - **Servidor predefinido**: define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Defina apenas um servidor como o predefinido.
  - **Importar**: navegue até um ficheiro separado por vírgulas que contenha uma lista de servidores no formato: descrição, endereço IP ou FQDN, Servidor predefinido. Selecione **OK** para importar estes servidores para a lista **Servidores**.
  - **Exportar**: exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv)

**Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:

- **Automático**
- **Check Point Capsule VPN**
- **VPN do Citrix**
- **SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**Grupo ou domínio de início de sessão** (apenas SonicWALL Mobile Connect): não é possível definir esta propriedade no perfil da VPN. Em vez disso, o Mobile Connect analisa este valor quando o nome de utilizador e o domínio são introduzidos no formato `username@domain` ou `DOMAIN\username`.

**XML personalizado**/**XML de EAP**: introduza quaisquer comandos XML personalizados que configuram a ligação VPN.

**Exemplo para o Pulse Secure:**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exemplo para o CheckPoint Mobile VPN:**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exemplo para o SonicWALL Mobile Connect:**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exemplo para o F5 Edge Client:**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Para obter mais informações sobre como escrever comandos XML personalizados, veja a documentação de cada fabricante relativa à VPN.

Para obter mais informações sobre a criação de XML de EAP, veja [Configuração de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

**Dividir túnel**: **ative** ou **desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.
- **Dividir rotas de túnel para esta ligação VPN**: adicione rotas opcionais para fornecedores de VPN de terceiros. Introduza um prefixo de destino e um tamanho de prefixo para cada um.

## <a name="apps-and-traffic-rules"></a>Regras de Aplicações e Tráfego

**Restringir a ligação VPN a estas aplicações**: ative esta definição se quiser que apenas algumas aplicações utilizem a ligação VPN.

**Aplicações Associadas**: introduza uma lista de aplicações que utilizam automaticamente a ligação VPN. O tipo de aplicação determina o identificador de aplicação. Para uma aplicação universal, introduza o nome de família do pacote. Para uma aplicação de ambiente de trabalho, introduza o caminho do ficheiro da aplicação.

>[!IMPORTANT]
>Recomendamos a proteção de todas as listas de aplicação criadas para as VPN por aplicação. Se um utilizador não autorizado alterar esta lista e se esta lista for importada por si para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN a aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

**Regras de tráfego de rede para esta ligação VPN**: selecione os protocolos, as portas locais e remotas e os intervalos de endereços que estão ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utiliza os protocolos, portas e intervalos de endereços que introduzir nessa regra.

## <a name="conditional-access"></a>Acesso Condicional

**Acesso condicional nesta ligação VPN**: ativa o fluxo de conformidade do dispositivo do cliente. Quando estiver ativado, o cliente VPN tenta comunicar com o Azure Active Directory para obter um certificado para utilizar para autenticação. O VPN deve estar configurado para utilizar a autenticação de certificado e o servidor VPN tem de confiar no servidor devolvido pelo Azure Active Directory.

**Início de sessão único (SSO) com certificado alternativo**: para a conformidade do dispositivo, utilize um certificado diferente do certificado de autenticação da VPN para a autenticação Kerberos. Introduza o certificado com as seguintes definições:

- **Utilização de chave avançada**: nome da utilização de chave avançada (EKU).
- **Identificador de Objeto**: identificador de objeto da EKU.
- **Hash do emissor**: thumbprint do certificado SSO

## <a name="dns-settings"></a>Definições de DNS

**Nomes e servidores DNS para esta ligação VPN**: selecione os servidores DNS que a ligação VPN utiliza depois de a ligação ser estabelecida.
Para cada servidor, introduza:
- **Nome DNS**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy**: se o seu servidor VPN precisar de um servidor proxy para a ligação, escolha se quer que os dispositivos detetem automaticamente as definições de ligação.
- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, tal como `http://proxy.contoso.com`, que contém o ficheiro de configuração.
- **Utilizar um servidor proxy**: ative esta opção para introduzir manualmente as definições do servidor proxy.
  - **Endereço**: introduza o endereço do servidor proxy (como um endereço IP).
  - **Número de porta**: introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais**: se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta definição caso não queira utilizar o servidor proxy para endereços locais introduzidos.
