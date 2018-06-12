---
title: Configurar as definições de VPN no Windows 10 – Azure | Microsoft Docs
description: Conheça e leia sobre as definições de VPN disponíveis no Microsoft Intune, para que são utilizadas e o que fazem, incluindo as regras de tráfego, acesso condicional e as definições de DNS e proxy para dispositivos Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 61310f5baa64c43d2e818df6c61a36d232922c1c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744742"
---
# <a name="windows-10-vpn-settings-in-intune"></a>Definições de VPN do Windows 10 no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode configurar as ligações VPN com o Intune. Este artigo descreve estas definições, as regras de tráfego, o acesso condicional e as definições de DNS e proxy.

Estas definições aplicam-se a:

- Dispositivos com o Windows 10
- Dispositivos com o Windows Holographic for Business

Consoante as definições que escolher, nem todos os valores são configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores**: adicione um ou mais servidores VPN aos quais os dispositivos são ligados. Ao adicionar um servidor, introduza as seguintes informações:
  - **Descrição**: introduza um nome descritivo para o servidor, como **Servidor VPN Contoso**.
  - **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados, tal como **192.168.1.1** ou **vpn.contoso.com**.
  - **Servidor predefinido**: define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Defina apenas um servidor como o predefinido.
  - **Importar**: navegue até um ficheiro separado por vírgulas que contenha uma lista de servidores no formato: descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importar estes servidores para a lista **Servidores**.
  - **Exportar**: exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv)

- **Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automático**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Ao escolher um tipo de ligação de VPN, também poderão ser pedidas as seguintes definições:  
    - **AlwaysOn**: ative-a para ligar automaticamente à ligação VPN quando: 
      - Os utilizadores iniciarem sessão nos respetivos dispositivos
      - A rede no dispositivo for alterada
      - O ecrã do dispositivo se ligar novamente após o ter desligado 

    - **Método de autenticação**: selecione como os utilizadores serão autenticados no servidor VPN. A utilização de **certificados** disponibiliza funcionalidades avançadas, como a experiência sem contacto, VPN a pedido e VPN por aplicação.
    - **Memorizar as credenciais sempre que iniciar sessão**: opte por colocar em cache as credenciais de autenticação.
    - **XML personalizado**: introduza todos os comandos XML personalizados que configuram a ligação VPN.
    - **XML de EAP**: introduza quaisquer comandos XML de EAP que configuram a ligação VPN

#### <a name="pulse-secure-example"></a>Exemplo de Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Exemplo de F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Exemplo de SonicWALL Mobile Connect
**Grupo ou domínio de início de sessão**: não pode definir esta propriedade no perfil da VPN. Em vez disso, o Mobile Connect analisa este valor quando o nome de utilizador e o domínio são introduzidos no formato `username@domain` ou `DOMAIN\username`.

Exemplo:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>Exemplo de CheckPoint Mobile VPN

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Escrever o XML personalizado
Para obter mais informações sobre como escrever comandos XML personalizados, veja a documentação de cada fabricante relativa à VPN.

Para obter mais informações sobre a criação de XML de EAP, veja [Configuração de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Regras de Aplicações e Tráfego

- **Associar o WIP ou as aplicações a esta VPN**: ative esta definição se quiser que apenas algumas aplicações utilizem a ligação VPN. As opções são:

  - **Associar um WIP a esta ligação**: introduza um **domínio WIP para esta ligação**
  - **Associar aplicações a esta ligação**: pode **Restringir a ligação VPN a estas aplicações** e, em seguida, adicionar **Aplicações Associadas**. As aplicações que introduzir automaticamente utilizam a ligação VPN. O tipo de aplicação determina o identificador de aplicação. Para uma aplicação universal, introduza o nome de família do pacote. Para uma aplicação de ambiente de trabalho, introduza o caminho do ficheiro da aplicação.
  >[!IMPORTANT]
  >Recomendamos a proteção de todas as listas de aplicação criadas para as VPN por aplicação. Se um utilizador não autorizado alterar esta lista e se esta lista for importada por si para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN a aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

- **Regras de tráfego de rede para esta ligação VPN**: selecione os protocolos, as portas locais e remotas e os intervalos de endereços que estão ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utiliza os protocolos, portas e intervalos de endereços que introduzir nessa regra.

## <a name="conditional-access"></a>Acesso Condicional

- **Acesso condicional nesta ligação VPN**: ativa o fluxo de conformidade do dispositivo do cliente. Quando estiver ativado, o cliente VPN tenta comunicar com o Azure Active Directory (AD) para obter um certificado para utilizar na autenticação. A VPN deve estar configurado para utilizar a autenticação de certificado e o servidor VPN tem de confiar no servidor devolvido pelo Azure AD.

- **Início de sessão único (SSO) com certificado alternativo**: para a conformidade do dispositivo, utilize um certificado diferente do certificado de autenticação da VPN para a autenticação Kerberos. Introduza o certificado com as seguintes definições:

  - **Nome**: o nome para a utilização alargada da chave (EKU)
  - **Identificador de Objeto**: identificador de objeto da EKU.
  - **Hash do emissor**: thumbprint do certificado SSO

## <a name="dns-settings"></a>Definições de DNS

**Domínio e servidores desta ligação VPN**: adicione o domínio e o servidor DNS para a VPN a utilizar. Pode escolher os servidores DNS que a ligação VPN utilizará depois de a ligação ser estabelecida. Para cada servidor, introduza:
- **Domínio**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, tal como `http://proxy.contoso.com`, que contém o ficheiro de configuração.
- **Endereço**: introduza o endereço do servidor proxy, como um endereço IP ou `vpn.contoso.com`
- **Número de porta**: introduza o número de porta TCP utilizada pelo servidor proxy
- **Ignorar o proxy para endereços locais**: se não quiser utilizar um servidor proxy para endereços locais, escolha Ativar. Esta definição aplica-se se o seu servidor VPN precisar de um servidor proxy para a ligação.

## <a name="split-tunneling"></a>Dividir Túnel

- **Dividir túnel**: **ative** ou **desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.
- **Dividir rotas de túnel para esta ligação VPN**: adicione rotas opcionais para fornecedores de VPN de terceiros. Introduza um prefixo de destino e um tamanho de prefixo para cada ligação.
