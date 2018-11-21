---
title: Adicionar definições de VPN para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de VPN com definições de rede privada virtual (VPN), incluindo os detalhes da ligação, os métodos de autenticação e a divisão de túnel nas definições base; as definições de VPN personalizadas com o identificador e os pares de valor e chave; as definições de VPN por aplicação que incluem URLs do Safari e VPNs a pedido com SSIDs ou domínios de pesquisa DNS; e as definições de proxy para incluir um script de configuração, endereço IP ou FQDN e porta TCP no Microsoft Intune em dispositivos iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ea127fb72a2e24343185d06e26d883e1183e7c2b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185564"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Configurar definições de VPN em dispositivos iOS no Microsoft Intune

O Microsoft Intune inclui várias definições de VPN que podem ser implementadas nos seus dispositivos iOS. Estas definições são utilizadas para criar e configurar ligações VPN à rede da sua organização. Este artigo descreve estas definições. Algumas definições só estão disponíveis para alguns clientes VPN, tais como o Citrix, Zscaler, entre outros.

## <a name="connection-type"></a>Tipo de ligação

Selecione o tipo de ligação de VPN da seguinte lista de fornecedores:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**: aplicável à versão 4.0.5x e versões anteriores da aplicação [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924).
- **Cisco AnyConnect**: aplicável à versão 4.0.7x e versões posteriores da aplicação [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690).
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: aplicável a versão 2.1 e versões anteriores da aplicação F5 Access.
- **F5 Access**: aplicável a versão 3.0 e versões posteriores da aplicação F5 Access.
- **Palo Alto Networks GlobalProtect (Legacy)**: aplicável a versão 4.1 e versões anteriores da aplicação Palo Alto Networks GlobalProtect.
- **Palo Alto Networks GlobalProtect**: aplicável a versão 5.0 e versões posteriores da aplicação Palo Alto Networks GlobalProtect.
- **Pulse Secure**
- **Cisco (IPSec)**
- **VPN do Citrix**
- **Citrix SSO**
- **Zscaler**: requer que integre o Zscaler Private Access (ZPA) na sua conta do Azure AD. Para obter passos detalhados, veja a [documentação do Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
- **VPN Personalizada**

> [!NOTE]
> A Cisco, Citrix, F5 e Palo Alto anunciaram que os seus clientes legados não funcionam no iOS 12. Deverá migrar para as novas aplicações logo que possível. Para obter mais informações, veja o [Blogue da Equipa de Suporte do Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## <a name="base-vpn-settings"></a>Definições de VPN Base

As definições apresentadas na seguinte lista são determinadas pelo tipo de ligação VPN que escolher.  

- **Nome da ligação**: os utilizadores finais verão este nome quando procurarem uma lista de ligações VPN disponíveis no dispositivo.
- **Nome de domínio personalizado** (apenas Zscaler): pré-preencha o campo de início de sessão da aplicação Zscaler com o domínio ao qual os seus utilizadores pertencem. Por exemplo, se um nome de utilizador for `Joe@contoso.net`, o domínio `contoso.net` será apresentado estaticamente no campo ao abrir a aplicação. Se não introduzir um nome de domínio, será utilizada a parte do domínio do UPN no Azure Active Directory (AD).
- **Endereço IP ou FQDN**: o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza: `192.168.1.1` ou `vpn.contoso.com`.
- **Nome da cloud da organização** (apenas Zscaler): introduza o nome da cloud em que a sua organização está aprovisionada. O URL que utiliza para iniciar sessão no Zscaler contém o nome.  
- **Método de autenticação**: selecione como os dispositivos serão autenticados no servidor VPN. 
  - **Certificados**: em **Certificado de autenticação**, selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. O tópico [Configurar certificados](certificates-configure.md) fornece algumas orientações sobre perfis de certificado.
  - **Nome de utilizador e palavra-passe**: os utilizadores finais têm de introduzir um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.  

    > [!NOTE]
    > Se o nome de utilizador e a palavra-passe forem utilizados como o método de autenticação do Cisco IPsec VPN, os primeiros têm de enviar o parâmetro SharedSecret através de um perfil personalizado do Apple Configurator.

- **URLs excluídos** (apenas Zscaler): quando estiver ligado à VPN do Zscaler, os URLs apresentados estarão acessíveis fora da cloud do Zscaler. 

- **Dividir túnel**: **ative** ou **desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

- **Identificador VPN** (VPN personalizada, Zscaler e Citrix): um identificador da aplicação VPN que está a utilizar e é disponibilizado pelo seu fornecedor VPN.
  - **Introduzir pares chave/valor para os atributos de VPN personalizados da sua organização**: adicione ou importe **Chaves** e **Valores** para personalizar a sua ligação VPN. Lembre-se de que estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.

- **Ativar o controlo de acesso de rede (NAC)** (apenas no Citrix SSO): ao escolher **concordo**, o dispositivo ID está incluído no perfil da VPN. Este ID pode ser utilizado para autenticação da VPN para permitir ou impedir o acesso à rede.

  **Ao utilizar o Citrix SSO com Gateway**, não se esqueça de:

  - Confirme que está a utilizar o Gateway da Citrix 12.0.59 ou superior.
  - Certifique-se os utilizadores terem SSO de Citrix 1.1.6 ou posterior instalado nos respetivos dispositivos.
  - Integrar o Citrix Gateway com o Intune para NAC, conforme descrito no [integrar o Microsoft Intune/Enterprise Mobility Suite com NetScaler (cenário LDAP + OTP)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) guia de implementação da Citrix.
  - Ative o NAC no perfil da VPN.

  Detalhes importantes:  

  - Quando o NAC estiver ativado, a VPN estiver desligada a cada 24 horas.
  - O ID do dispositivo faz parte do perfil, mas não pode ser visto no Intune. Este ID não é armazenado nem partilhado pela Microsoft. Quando isto for suportado pelos parceiros de VPN, o cliente VPN, como o Citrix SSO, poderá obter o ID e consultar o Intune para confirmar que o dispositivo está inscrito e se o perfil VPN está ou não em conformidade.
  - Para remover esta definição, volte a criar o perfil e não selecione a opção **Concordo**. Em seguida, atribua novamente o perfil.

## <a name="automatic-vpn-settings"></a>Definições Automáticas de VPN

- **VPN por aplicação**: ativa a VPN por aplicação. Permite que a ligação VPN seja acionada automaticamente quando determinadas aplicações forem abertas. Também associa as aplicações com este perfil VPN. Para obter mais informações, veja as [instruções para configurar a VPN por aplicação para iOS](vpn-setting-configure-per-app.md).
  - **Tipo de Fornecedor**: disponível apenas para o Pulse Secure e a VPN Personalizada.
  - Ao utilizar perfis **VPN por aplicação** iOS com o Pulse Secure ou uma VPN Personalizada, selecione o túnel de camada de aplicação (proxy-de-aplicação) ou o túnel de nível do pacote (pacote-túnel). Defina o valor **ProviderType** para **proxy-da-aplicação**, para o túnel de camada de aplicação ou para **pacote-túnel**, para o túnel de camada de pacote. Se não tiver a certeza sobre o valor a utilizar, consulte a documentação do seu fornecedor de VPN.
  - **URLs do Safari que irão acionar esta VPN**: adicione um ou mais URLs de sites. Quando estes URLs são visitados através do browser Safari no dispositivo, a ligação VPN é estabelecida automaticamente.

- **VPN a pedido**: configure regras condicionais que controlam quando a ligação VPN é iniciada. Por exemplo, crie uma condição na qual a ligação VPN só é utilizada quando um dispositivo não estiver ligado a uma rede Wi-Fi da sua empresa. Em alternativa, crie uma condição na qual, se um dispositivo não puder aceder a um domínio de pesquisa DNS que introduzir, a ligação VPN não é iniciada.

  - **SSIDs ou domínios de pesquisa DNS**: selecione se esta condição utiliza **SSIDs** de rede sem fios ou **domínios de pesquisa DNS**. Selecione **Adicionar** para configurar um ou mais SSIDs ou domínios de pesquisa.
  - **Pesquisa de cadeia de URL**: opcional. Introduza um URL para a regra utilizar como um teste. Se o dispositivo que contém este perfil aceder a este URL sem redirecionamento, a ligação VPN será iniciada. Além disso, o dispositivo será ligado ao URL de destino. O utilizador não vê o site de pesquisa de cadeia de URL. Um exemplo de uma pesquisa de cadeia de URL é o endereço de um servidor Web de auditoria que verifica a conformidade do dispositivo antes de ligar a VPN. Outra possibilidade é a de o URL testar a capacidade de a VPN estabelecer ligação a um site, antes de ligar o dispositivo ao URL de destino através da VPN.
  - **Ação de domínio**: selecione um dos seguintes itens:
    - Ligar se necessário
    - Nunca ligar
  - **Ação**: selecione um dos seguintes itens:
    - Ligar
    - Avaliar a ligação
    - Ignorar
    - Desligar

## <a name="proxy-settings"></a>Definições de proxy

Se estiver a utilizar um proxy, configure as definições seguintes. As definições de proxy não estão disponíveis para ligações VPN do Zscaler.  

- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que inclui o ficheiro de configuração.
- **Endereço**: introduza o endereço IP do nome do anfitrião totalmente qualificado do servidor proxy.
- **Número de porta**: introduza o número de porta associado ao servidor proxy.

## <a name="next-step"></a>Passo seguinte
[Criar perfis VPN no Intune](vpn-settings-configure.md)  
