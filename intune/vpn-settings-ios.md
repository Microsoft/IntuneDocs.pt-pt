---
title: Definições de VPN para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja as definições de configuração de VPN (rede privada virtual) disponíveis, incluindo os detalhes da ligação, os métodos de autenticação e a divisão de túnel nas definições base; as definições de VPN personalizadas com o identificador e os pares de valor e chave; as definições de VPN por aplicação que incluem URLs do Safari e VPNs a pedido com SSIDs ou domínios de pesquisa DNS; e as definições de proxy para incluir um script de configuração, endereço IP ou FQDN e porta TCP no Microsoft Intune em dispositivos iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d35c9e32b7a0720d5d84a93a7edde6f2bd51911f
ms.sourcegitcommit: 08e1b0d45c84eb9525a0a59f5540d41434da2814
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39146633"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Configurar definições de VPN no Microsoft Intune para dispositivos com iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com iOS.

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem uma lista de ligações VPN disponíveis no dispositivo.
- **Endereço IP ou FQDN**: introduza o endereço IP ou nome de domínio completamente qualificado (FQDN) do servidor VPN ao qual os dispositivos são ligados. Por exemplo, introduza **192.168.1.1** ou **vpn.contoso.com**.
- **Método de autenticação**: escolha como os dispositivos serão autenticados no servidor VPN em:
  - **Certificados**: em **Certificado de autenticação**, selecione um perfil de certificado SCEP ou PKCS existente para autenticar a ligação. O tópico [Configurar certificados](certificates-configure.md) fornece algumas orientações sobre perfis de certificado.
  - **Nome de utilizador e palavra-passe**: os utilizadores finais têm de introduzir um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.

    > [!NOTE]
    > Se o nome de utilizador e a palavra-passe forem utilizados como o método de autenticação do Cisco IPsec VPN, os primeiros têm de enviar o parâmetro SharedSecret através de um perfil personalizado do Apple Configurator.
  
- **Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco Legacy AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Palo Alto Networks GlobalProtect**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **VPN Personalizada**

    > [!NOTE]
    > - Os perfis de **VPN Cisco Legacy AnyConnect** destinam-se à versão da aplicação 4.0.5x e versões mais antigas do [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)
    > - Os perfis de **VPN Cisco Legacy AnyConnect** destinam-se à versão da aplicação 4.0.7x e versões mais antigas do [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)

- **Dividir túnel**: **ative** ou **desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada** como o tipo de ligação, configure também as seguintes definições:

- **Identificador VPN**: um identificador da aplicação VPN que está a utilizar e é disponibilizado pelo seu fornecedor de VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados**: adicione ou importe **Chaves** e **Valores** para personalizar a sua ligação VPN. Mais uma vez, estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.

## <a name="automatic-vpn-settings"></a>Definições Automáticas de VPN

- **VPN por aplicação**: selecionar esta opção ativa a VPN por aplicação, que permite que a ligação VPN seja acionada automaticamente quando determinadas aplicações são abertas. Além de selecionar esta opção, também precisa de associar as aplicações a este perfil VPN. Veja as [instruções para configurar a VPN por aplicação para iOS](vpn-setting-configure-per-app.md) para obter mais detalhes. 
  - **URLs do Safari que irão acionar esta VPN**: selecione esta opção para adicionar um ou mais URLs de sites. Quando estes URLs são visitados através do browser Safari no dispositivo, a ligação VPN é estabelecida automaticamente.

- **VPN a pedido**: configure regras condicionais que controlam quando a ligação VPN é iniciada. Por exemplo, crie uma condição na qual a ligação VPN só é utilizada quando um dispositivo não estiver ligado a uma rede Wi-Fi da sua empresa. Em alternativa, crie uma condição na qual, se um dispositivo não puder aceder a um domínio de pesquisa DNS que especificar, a ligação VPN não é iniciada.

  - **SSIDs ou domínios de pesquisa DNS**: selecione se esta condição utiliza **SSIDs** de rede sem fios ou **domínios de pesquisa DNS**. Selecione **Adicionar** para configurar um ou mais SSIDs ou domínios de pesquisa.
  - **Pesquisa de cadeia de URL**: opcional. Introduza um URL para a regra utilizar como um teste. Se o dispositivo no qual está instalado este perfil conseguir aceder a este URL sem redirecionamento, a ligação VPN será iniciada e o dispositivo será ligado ao URL de destino. O utilizador não vê o site de pesquisa de cadeia de URL. Um exemplo de uma pesquisa de cadeia de URL é o endereço de um servidor Web de auditoria que verifica a conformidade do dispositivo antes de ligar a VPN. Outra possibilidade é a de o URL testar a capacidade de a VPN estabelecer ligação a um site, antes de ligar o dispositivo ao URL de destino através da VPN.
  - **Ação de domínio**: selecione um dos seguintes itens:
    - Ligar se necessário
    - Nunca ligar
  - **Ação**: selecione um dos seguintes itens:
    - Ligar
    - Avaliar a ligação
    - Ignorar
    - Desligar

## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Endereço**: introduza o endereço IP do nome do anfitrião totalmente qualificado do servidor proxy.
- **Número de porta**: introduza o número de porta associado ao servidor proxy.

## <a name="next-step"></a>Passo seguinte
[Criar perfis VPN no Intune](vpn-settings-configure.md)
