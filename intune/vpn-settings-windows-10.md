---
title: Definições de VPN do Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Conheça e leia sobre a VPN disponível definições no Microsoft Intune, o que são utilizadas e o que fazem, incluindo as regras de tráfego, acesso condicional e definições de DNS e proxy do Windows 10 e Windows Holographic for Business dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b71bc2ea893199b83de5fd1480dae5630c3edfd
ms.sourcegitcommit: 9a4c5b6c2ce511edaeace25426a23f180cb71e15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57565671"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Definições de dispositivos Windows 10 e Windows Holographic para adicionar conexões VPN com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode adicionar e configurar ligações de VPN para dispositivos com o Microsoft Intune. Este artigo apresenta uma lista e descreve funcionalidades e definições comummente utilizadas durante a criação de redes privadas virtuais (VPNs). Estas definições de VPN e funcionalidades são utilizadas nos perfis de configuração do dispositivo no Intune, que são emitidos via push ou implementadas nos dispositivos. 

Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, incluindo através de um fornecedor VPN, permitindo sempre no, através de DNS, adição de um proxy e muito mais.

Estas definições aplicam-se a dispositivos que executam:

- Windows 10
- Windows Holographic for Business

Consoante as definições que escolher, nem todos os valores são configuráveis.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivos VPN](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Nome da ligação**: Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores**: Adicione um ou mais servidores VPN aos quais dispositivos são ligados. Ao adicionar um servidor, introduza as seguintes informações:
  - **Descrição**: Introduza um nome descritivo para o servidor, como **servidor VPN da Contoso**
  - **IP ou FQDN do endereço**: Introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos ligados, tal como **192.168.1.1** ou **vpn.contoso.com**
  - **Servidor predefinido**: Ativa este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Defina apenas um servidor como o predefinido.
  - **Importar**: Procure um ficheiro separado por vírgulas que inclui uma lista de servidores no formato: descrição, endereço IP ou FQDN, servidor predefinido. Escolha **OK** para importar estes servidores para a lista **Servidores**.
  - **Exportar**: Exporta a lista de servidores para um ficheiro de vírgula separados-valores (csv)

- **Registar os endereços IP com o DNS interno**: Selecione **ativar** para configurar o perfil de VPN do Windows 10 para registar dinamicamente os endereços IP atribuídos à interface de VPN com o DNS interno. Selecione **Desativar** para não registar endereços IP de forma dinâmica.

- **Tipo de ligação**: Selecione o tipo de ligação de VPN da seguinte lista de fornecedores:

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
    - **Always On**: Escolher **ativar** para ligar automaticamente a ligação VPN quando ocorrem os seguintes eventos: 
      - Os utilizadores iniciarem sessão nos respetivos dispositivos
      - A rede no dispositivo for alterada
      - O ecrã do dispositivo se ligar novamente após o ter desligado 

    - **Método de autenticação**: Selecione como pretende que os utilizadores sejam autenticados no servidor VPN. A utilização de **certificados** disponibiliza funcionalidades avançadas, como a experiência sem contacto, VPN a pedido e VPN por aplicação.
    - **Lembre-se as credenciais sempre que iniciarem sessão**: Opte por colocar em cache as credenciais de autenticação.
    - **XML personalizado**: Introduza quaisquer comandos XML personalizados que configuram a ligação VPN.
    - **EAP Xml**: Introduza quaisquer comandos XML de EAP que configuram a ligação VPN

#### <a name="pulse-secure-example"></a>Exemplo de Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Exemplo de F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Exemplo de SonicWALL Mobile Connect
**Grupo de início de sessão ou domínio**: Esta propriedade não pode ser definida no perfil da VPN. Em vez disso, o Mobile Connect analisa este valor quando o nome de utilizador e o domínio são introduzidos no formato `username@domain` ou `DOMAIN\username`.

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

- **Associar WIP ou aplicações a esta VPN**: Ative esta definição se quiser que apenas algumas aplicações utilizem a ligação VPN. As opções são:

  - **Associar um WIP esta ligação**: Introduza um **domínio WIP para esta ligação**
  - **Associar aplicações esta ligação**: Pode **ligação de VPN de restringir a estas aplicações**e, em seguida, adicione **associados aplicações**. As aplicações que introduzir automaticamente utilizam a ligação VPN. O tipo de aplicação determina o identificador de aplicação. Para uma aplicação universal, introduza o nome de família do pacote. Para uma aplicação de ambiente de trabalho, introduza o caminho do ficheiro da aplicação.
  >[!IMPORTANT]
  >Recomendamos a proteção de todas as listas de aplicação criadas para as VPN por aplicação. Se um utilizador não autorizado alterar esta lista e se esta lista for importada por si para a lista de aplicações VPN por aplicação, irá autorizar potencialmente o acesso VPN a aplicações que não devem ter acesso. Uma forma de proteger as listas de aplicação é utilizar uma lista de controlo de acesso (ACL).

- **Regras de tráfego para esta ligação VPN de rede**: Selecione os protocolos, as portas locais e remotas e os intervalos de endereços que estão ativados para a ligação VPN. Se não criar uma regra de tráfego de rede, todos os protocolos, portas e intervalos de endereços estarão ativados. Depois de criar uma regra, a ligação VPN apenas utiliza os protocolos, portas e intervalos de endereços que introduzir nessa regra.

## <a name="conditional-access"></a>Acesso Condicional

- **Acesso condicional para esta ligação VPN**: Ativa o fluxo de conformidade de dispositivo do cliente. Quando estiver ativado, o cliente VPN comunica com o Azure Active Directory (AD) para obter um certificado para utilizar na autenticação. A VPN deve estar configurado para utilizar a autenticação de certificado e o servidor VPN tem de confiar no servidor devolvido pelo Azure AD.

- **Início de sessão único (SSO) com certificado alternativo**: Para a conformidade do dispositivo, utilize um certificado diferente do certificado de autenticação do VPN para a autenticação Kerberos. Introduza o certificado com as seguintes definições:

  - **Nome**: Nome para utilização alargada da chave (EKU)
  - **Identificador de objeto**: Identificador de objeto para EKU
  - **Hash de emissor**: Thumbprint do certificado SSO

## <a name="dns-settings"></a>Definições de DNS

- **Lista de pesquisa de sufixos DNS**: Na **sufixos DNS**, introduza um sufixo DNS, e **Add**. Pode adicionar vários sufixos.

  Quando utilizar sufixos DNS, pode procurar um recurso de rede através do respetivo nome abreviado, em vez do nome de domínio completamente qualificado (FQDN). Quando pesquisar com o nome abreviado, o sufixo é determinado automaticamente pelo servidor DNS. Por exemplo, `utah.contoso.com` está na lista de sufixos DNS. Deve enviar o ping para `DEV-comp`. Neste cenário, é resolvido para `DEV-comp.utah.contoso.com`.

  Os sufixos DNS são resolvidos pela ordem listada e a mesma pode ser alterada. Por exemplo, `colorado.contoso.com` e `utah.contoso.com` estão na lista de sufixos DNS e ambos têm um recurso denominado `DEV-comp`. Uma vez que `colorado.contoso.com` é o primeiro da lista, é resolvido como `DEV-comp.colorado.contoso.com`.
  
  Para alterar a ordem, clique nos pontos à esquerda do sufixo DNS e, em seguida, arraste o sufixo para a parte superior:

  ![Selecione os três pontos e clique e arraste para mover o sufixo DNS](./media/vpn-settings-windows10-move-dns-suffix.png)

- **Nome de regras de política de resolução de tabela (NRPT)**: Regras de tabela (NRPT) de política de resolução de nomes definem como o DNS resolve nomes quando estiver ligado à VPN. Depois da ligação VPN é estabelecida, pode escolher os servidores DNS que utiliza a ligação VPN.

  Pode adicionar regras para a tabela que incluem o domínio, DNS server, proxy e outros detalhes para resolver o domínio que introduzir. A ligação VPN utiliza estas regras quando os utilizadores ligam-se para os domínios que introduzir.

  Selecione **adicionar** para adicionar uma nova regra. Para cada servidor, introduza:

  - **Domínio**: Introduza o nome de domínio completamente qualificado (FQDN) ou um sufixo DNS para aplicar a regra. Também pode introduzir um ponto (.) no início com um sufixo de DNS. Por exemplo, introduza: `contoso.com` ou `.allcontososubdomains.com`.
  - **Servidores DNS**: Introduza o endereço IP ou o servidor DNS que resolve o domínio. Por exemplo, introduza: `10.0.0.3` ou `vpn.contoso.com`.
  - **Proxy**: Introduza o servidor de proxy web que resolve o domínio. Por exemplo, introduza `http://proxy.com`.
  - **Ligar automaticamente**: Quando **Enabled**, o dispositivo estabelece ligação automaticamente para a VPN quando um dispositivo se liga a um domínio introduzir, tais como `contoso.com`. Quando **não configurado** (predefinição), o dispositivo não ligar automaticamente à VPN
  - **Persistente**: Quando definido como **ativado**, a regra mantém-se na tabela de política de resolução de nome (NRPT) até que a regra é manualmente removida do dispositivo, desliga, mesmo depois que a VPN. Quando definido como **não configurado** (predefinição), as regras NRPT no perfil da VPN são removidas do dispositivo quando o VPN se desliga.

## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática**: Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, tal como `http://proxy.contoso.com`, que contém o ficheiro de configuração.
- **Endereço**: Introduza o endereço do servidor proxy, por exemplo, um endereço IP ou `vpn.contoso.com`
- **Número de porta**: Introduza o número da porta TCP utilizado pelo seu servidor proxy
- **Ignorar o proxy para endereços locais**: Se não pretender utilizar um servidor proxy para endereços locais, em seguida, selecione Enable. Esta definição aplica-se se o seu servidor VPN precisar de um servidor proxy para a ligação.

## <a name="split-tunneling"></a>Dividir Túnel

- **Divisão do túnel**: **Ativar** ou **desativar** para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.
- **Dividir rotas de túnel para esta ligação VPN**: Adicione rotas opcionais para fornecedores VPN de terceiros. Introduza um prefixo de destino e um tamanho de prefixo para cada ligação.

## <a name="trusted-network-detection"></a>Deteção de rede fidedigna

**Trusted sufixos DNS de rede**: Quando os utilizadores já estão ligados a uma rede fidedigna, pode impedir que os dispositivos automaticamente se a outras ligações VPN.

Na **sufixos DNS**, introduza um sufixo DNS que pretende confia, tal como contoso.com e selecione **Add**. Pode adicionar sufixos de tantas quanto quiser.

Se um utilizador estiver ligado a um sufixo DNS na lista, em seguida, o utilizador não ligar automaticamente a outra ligação VPN. O utilizador continua a utilizar a lista fidedigna de sufixos DNS que introduzir. A rede fidedigna ainda é utilizada, mesmo que qualquer autotriggers são definidos.

Por exemplo, se o utilizador já está ligado a um sufixo DNS fidedigno, em seguida, os autotriggers seguintes são ignorados. Especificamente, os sufixos DNS na lista de cancelar todas as outras autotriggers de ligação, incluindo:

- Sempre ativo
- Acionador com base na aplicação
- Autotrigger DNS

## <a name="next-steps"></a>Passos Seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribuir o perfil](device-profile-assign.md), e [monitorizar o estado](device-profile-monitor.md).

Configurar definições de VPN nas [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md), e [macOS](vpn-settings-macos.md) dispositivos.
