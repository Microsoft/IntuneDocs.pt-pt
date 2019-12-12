---
title: Configurações de VPN do Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Aprenda e leia sobre todas as configurações de VPN disponíveis no Microsoft Intune, para que elas são usadas e o que elas fazem, incluindo regras de tráfego, acesso condicional e configurações de DNS e proxy para dispositivos Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122872eff92a37c8724fd4a853091e51a0a54c66
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506524"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Configurações do dispositivo Windows 10 e Windows Holographic para adicionar conexões VPN usando o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Você pode adicionar e configurar conexões VPN para dispositivos usando Microsoft Intune. Este artigo lista e descreve as configurações e recursos comumente usados ao criar VPNs (redes virtuais privadas). Essas configurações e recursos de VPN são usados em perfis de configuração de dispositivo no Intune que são enviados por Push ou implantados em dispositivos.

Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, incluindo o uso de um fornecedor de VPN, a habilitação do AlwaysOn, o uso de DNS, a adição de um proxy e muito mais.

Essas configurações se aplicam a dispositivos que executam:

- Windows 10
- Windows Holographic for Business

Consoante as definições que escolher, nem todos os valores são configuráveis.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo VPN](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores**: adicione um ou mais servidores VPN aos quais os dispositivos são ligados. Ao adicionar um servidor, introduza as seguintes informações:
  - **Descrição**: introduza um nome descritivo para o servidor, como **Servidor VPN Contoso**.
  - **Endereço IP ou FQDN**: Insira o endereço IP ou o FQDN (nome de domínio totalmente qualificado) do servidor VPN ao qual os dispositivos se conectam, como **192.168.1.1** ou **VPN.contoso.com**
  - **Servidor predefinido**: define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Defina apenas um servidor como o predefinido.
  - **Importar**: navegue até um ficheiro separado por vírgulas que inclua uma lista de servidores no formato: descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importar estes servidores para a lista **Servidores**.
  - **Exportar**: exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv)

- **Registar endereços IP com DNS interno**: selecione **Ativar** para configurar o perfil VPN do Windows 10 para registar de forma dinâmica os endereços IP atribuídos à interface de VPN com o DNS interno. Selecione **Desativar** para não registar endereços IP de forma dinâmica.

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
  - **Always on**: escolha **habilitar** para se conectar automaticamente à conexão VPN quando os seguintes eventos ocorrerem: 
    - Os utilizadores iniciarem sessão nos respetivos dispositivos
    - A rede no dispositivo for alterada
    - O ecrã do dispositivo se ligar novamente após o ter desligado 

  - **Método de autenticação**: selecione como os utilizadores serão autenticados no servidor VPN. A utilização de **certificados** disponibiliza funcionalidades avançadas, como a experiência sem contacto, VPN a pedido e VPN por aplicação.
  - **Memorizar as credenciais sempre que iniciar sessão**: opte por colocar em cache as credenciais de autenticação.
  - **XML personalizado**: introduza todos os comandos XML personalizados que configuram a ligação VPN.
  - **XML de EAP**: introduza quaisquer comandos XML de EAP que configuram a ligação VPN

### <a name="pulse-secure-example"></a>Exemplo de Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>Exemplo de F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>Exemplo de SonicWALL Mobile Connect
**Grupo ou domínio de início de sessão**: não pode definir esta propriedade no perfil da VPN. Em vez disso, o Mobile Connect analisa este valor quando o nome de utilizador e o domínio são introduzidos no formato `username@domain` ou `DOMAIN\username`.

Exemplo:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>Exemplo de CheckPoint Mobile VPN

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>Escrever o XML personalizado
Para obter mais informações sobre como escrever comandos XML personalizados, veja a documentação de cada fabricante relativa à VPN.

Para obter mais informações sobre a criação de XML de EAP, veja [Configuração de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Regras de Aplicações e Tráfego

- **Associar o WIP ou as aplicações a esta VPN**: ative esta definição se quiser que apenas algumas aplicações utilizem a ligação VPN. As opções são:

  - **Associar um WIP a esta ligação**: introduza um **domínio WIP para esta ligação**
  - **Associar aplicações a esta ligação**: pode **Restringir a ligação VPN a estas aplicações** e, em seguida, adicionar **Aplicações Associadas**. As aplicações que introduzir automaticamente utilizam a ligação VPN. O tipo de aplicação determina o identificador de aplicação. Para uma aplicação universal, introduza o nome de família do pacote. Para uma aplicação de ambiente de trabalho, introduza o caminho do ficheiro da aplicação.
  >[!IMPORTANT]
  >Recomendamos a proteção de todas as listas de aplicação criadas para as VPN por aplicação. Se um utilizador não autorizado alterar esta lista e se esta lista for importada por si para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN a aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

- **Regras de tráfego de rede para esta ligação VPN**: selecione os protocolos, as portas locais e remotas e os intervalos de endereços que estão ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utiliza os protocolos, portas e intervalos de endereços que introduzir nessa regra.

## <a name="conditional-access"></a>Conditional Access

- **Acesso condicional para esta conexão VPN**: habilita o fluxo de conformidade do dispositivo do cliente. Quando estiver ativado, o cliente VPN comunica com o Azure Active Directory (AD) para obter um certificado para utilizar na autenticação. A VPN deve estar configurado para utilizar a autenticação de certificado e o servidor VPN tem de confiar no servidor devolvido pelo Azure AD.

- **Início de sessão único (SSO) com certificado alternativo**: para a conformidade do dispositivo, utilize um certificado diferente do certificado de autenticação da VPN para a autenticação Kerberos. Introduza o certificado com as seguintes definições:

  - **Nome**: o nome para a utilização alargada da chave (EKU)
  - **Identificador de Objeto**: identificador de objeto da EKU.
  - **Hash do emissor**: thumbprint do certificado SSO

## <a name="dns-settings"></a>Definições de DNS

- **Lista de pesquisa de sufixos DNS**: em **Sufixos DNS**, introduza um sufixo DNS e clique em **Adicionar**. Você pode adicionar vários sufixos.

  Quando utilizar sufixos DNS, pode procurar um recurso de rede através do respetivo nome abreviado, em vez do nome de domínio completamente qualificado (FQDN). Quando pesquisar com o nome abreviado, o sufixo é determinado automaticamente pelo servidor DNS. Por exemplo, `utah.contoso.com` está na lista de sufixos DNS. Deve enviar o ping para `DEV-comp`. Neste cenário, é resolvido para `DEV-comp.utah.contoso.com`.

  Os sufixos DNS são resolvidos pela ordem listada e a mesma pode ser alterada. Por exemplo, `colorado.contoso.com` e `utah.contoso.com` estão na lista de sufixos DNS e ambos têm um recurso denominado `DEV-comp`. Uma vez que `colorado.contoso.com` é o primeiro da lista, é resolvido como `DEV-comp.colorado.contoso.com`.
  
  Para alterar a ordem, clique nos pontos à esquerda do sufixo DNS e, em seguida, arraste o sufixo para a parte superior:

  ![Selecione os três pontos e clique e arraste para mover o sufixo DNS](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- **Regras de tabela de políticas de resolução de nomes (NRPT)** : as regras de tabela de políticas de resolução de nomes (NRPT) definem como o DNS resolve nomes quando conectados à VPN. Depois que a conexão VPN é estabelecida, você escolhe quais servidores DNS a conexão VPN usa.

  Você pode adicionar regras à tabela que incluem o domínio, o servidor DNS, o proxy e outros detalhes para resolver o domínio que você inserir. A conexão VPN usa essas regras quando os usuários se conectam aos domínios que você inserir.

  Selecione **Adicionar** para adicionar uma nova regra. Para cada servidor, introduza:

  - **Domínio**: Insira o nome de domínio totalmente qualificado (FQDN) ou um sufixo DNS para aplicar a regra. Você também pode inserir um ponto (.) no início de um sufixo DNS. Por exemplo, introduza: `contoso.com` ou `.allcontososubdomains.com`.
  - **Servidores DNS**: Insira o endereço IP ou o servidor DNS que resolve o domínio. Por exemplo, introduza: `10.0.0.3` ou `vpn.contoso.com`.
  - **Proxy**: Insira o servidor proxy da Web que resolve o domínio. Por exemplo, introduza `http://proxy.com`.
  - **Conectar automaticamente**: quando **habilitado**, o dispositivo se conecta automaticamente à VPN quando um dispositivo se conecta a um domínio que você insere, como `contoso.com`. Quando **não configurado** (padrão), o dispositivo não se conecta automaticamente à VPN
  - **Persistent**: quando definido como **habilitado**, a regra permanece na tabela de políticas de resolução de nomes (NRPT) até que a regra seja manualmente removida do dispositivo, mesmo após a desconexão da VPN. Quando definido como **não configurado** (padrão), as regras de NRPT no perfil VPN são removidas do dispositivo quando a VPN é desconectada.

## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, tal como `http://proxy.contoso.com`, que contém o ficheiro de configuração.
- **Endereço**: introduza o endereço do servidor proxy, como um endereço IP ou `vpn.contoso.com`
- **Número de porta**: introduza o número de porta TCP utilizada pelo servidor proxy
- **Ignorar o proxy para endereços locais**: se não quiser utilizar um servidor proxy para endereços locais, escolha Ativar. Esta definição aplica-se se o seu servidor VPN precisar de um servidor proxy para a ligação.

## <a name="split-tunneling"></a>Dividir Túnel

- **Dividir túnel**: **ative** ou **desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.
- **Dividir rotas de túnel para esta ligação VPN**: adicione rotas opcionais para fornecedores de VPN de terceiros. Introduza um prefixo de destino e um tamanho de prefixo para cada ligação.

## <a name="trusted-network-detection"></a>Detecção de rede confiável

**Sufixos DNS de rede confiável**: quando os usuários já estão conectados a uma rede confiável, você pode impedir que dispositivos se conectem automaticamente a outras conexões VPN.

Em **sufixos DNS**, insira um sufixo DNS que você deseja confiar, como contoso.com, e selecione **Adicionar**. Você pode adicionar quantos sufixos desejar.

Se um usuário estiver conectado a um sufixo DNS na lista, o usuário não se conectará automaticamente a outra conexão VPN. O usuário continua a usar a lista confiável de sufixos DNS que você inserir. A rede confiável ainda será usada, mesmo se algum gatilho for definido.

Por exemplo, se o usuário já estiver conectado a um sufixo DNS confiável, os seguintes gatilhos serão ignorados. Especificamente, os sufixos DNS na lista cancelam todos os outros disparadores automotivos de conexão, incluindo:

- Sempre ativado
- Gatilho baseado em aplicativo
- Gatilho de autodisparo do DNS

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md)e [monitore seu status](device-profile-monitor.md).

Defina as configurações de VPN em dispositivos [Android](vpn-settings-android.md), [Ios](vpn-settings-ios.md)e [MacOS](vpn-settings-macos.md) .
