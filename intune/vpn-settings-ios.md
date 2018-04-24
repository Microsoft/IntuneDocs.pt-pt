---
title: Definições de VPN para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja as definições de configuração de VPN (rede privada virtual) disponíveis, incluindo os detalhes da ligação, os métodos de autenticação e a divisão de túnel nas definições base; as definições de VPN personalizadas com o identificador e os pares de valor e chave; as definições de VPN por aplicação que incluem URLs do Safari e VPNs a pedido com SSIDs ou domínios de pesquisa DNS; e as definições de proxy para incluir um script de configuração, endereço IP ou FQDN e porta TCP no Microsoft Intune em dispositivos iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ce970f942d8ea20eb9ea593c23160757122926e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
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
- **Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **VPN Personalizada**

- **Dividir túnel**: **ative** ou **desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada** como o tipo de ligação, configure também as seguintes definições:

- **Identificador VPN**: um identificador da aplicação VPN que está a utilizar e é disponibilizado pelo seu fornecedor de VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados**: adicione ou importe **Chaves** e **Valores** para personalizar a sua ligação VPN. Mais uma vez, estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.

## <a name="apps-per-app-vpn-settings"></a>Definições de aplicações (VPN por aplicação)

- **VPN por aplicação**: ative esta opção para utilizar URLs que ativem a ligação VPN quando são visitados a partir do browser Safari. Para configurar a VPN por aplicação, tem de selecionar **Certificados** como método de autenticação nas definições de VPN Base.
  - **URLs do Safari que irão acionar esta VPN**: selecione esta opção para adicionar um ou mais URLs de sites. Quando estes URLs são visitados, a ligação VPN é ativada.

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
