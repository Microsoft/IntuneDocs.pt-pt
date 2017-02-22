---
title: "Definições de VPN do Intune para dispositivos iOS | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cd3069a63bd657d1c9f5e33b96db39a3b3f98d2
ms.openlocfilehash: 23322313bfedb089f2665f53795996a26efe40e0


---

# <a name="vpn-settings-for-ios-devices-in-intune-azure-preview"></a>Definições de VPN para dispositivos iOS na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Consoante as definições que escolher, nem todos os valores na lista abaixo serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base


**Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticação** – Escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Em **Certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](how-to-configure-certificates.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Tipo de ligação** – Selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Cisco (IPSec)**
    - **Citrix**
    - **VPN Personalizada**
- **Divisão de túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utilizará a ligação VPN para aceder aos ficheiros de trabalho, mas utilizará a rede padrão do hotel para a navegação normal na Internet.


## <a name="custom-vpn-settings"></a>Definições de VPN Personalizada

Se tiver selecionado **VPN Personalizada** como o tipo de ligação, configure estas definições adicionais:

- **Identificador VPN** – É o identificador da aplicação VPN que está a utilizar e é disponibilizado pelo seu fornecedor de VPN.
- **Introduzir pares de chave e valor para os atributos de VPN personalizados** – Adicione ou importe **Chaves** e **Valores** para personalizar a ligação VPN. Mais uma vez, estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.

## <a name="apps-per-app-vpn-settings"></a>Definições de aplicações (VPN por aplicação)

- **VPN por aplicação** – Ative esta opção se quiser URLs que ativem a ligação VPN quando são visitados a partir do browser Safari. Para configurar esta opção, tem de ter selecionado **Certificados** como método de autenticação nas definições de VPN Base.
- **URLs que vão ativar a ligação VPN durante a utilização do browser Safari** – Clique em Adicionar para adicionar um ou mais URLs de sites. Quando estes URLs são visitados, a ligação VPN é ativada.

- **Regras a pedido** – Esta opção permite-lhe configurar regras condicionais que controlam quando a ligação VPN é iniciada. Por exemplo, pode criar uma condição na qual a ligação VPN só é utilizada quando um dispositivo não está ligado a uma das redes Wi-Fi da sua empresa. Em alternativa, pode criar uma condição na qual, se um dispositivo não puder aceder a um domínio de pesquisa DNS que especificar, a ligação VPN não é iniciada.

    - **SSIDs ou domínios de pesquisa DNS** – Selecione se esta condição utilizará **SSIDs** de rede sem fios ou **Domínios de pesquisa DNS**. Escolha Adicionar para configurar um ou mais SSIDs ou domínios de pesquisa.
    - **Pesquisa de cadeia de URL** – Opcionalmente, indique um URL para a regra utilizar como um teste. Se o dispositivo no qual está instalado este perfil for capaz de aceder a este URL sem redirecionamento, a ligação VPN será iniciada e o dispositivo será ligado ao URL de destino. O utilizador não verá o site de pesquisa de cadeia de URL. Um exemplo de uma pesquisa de cadeia de URL é o endereço de um servidor Web de auditoria que verifica a conformidade do dispositivo antes de ligar a VPN. Outra possibilidade é a de o URL testar a capacidade de a VPN estabelecer ligação a um site, antes de ligar o dispositivo ao URL de destino através da VPN.
    - **Ação de domínio** – Escolha uma das seguintes opções:
        - Ligar caso seja preciso – 
        - Nunca ligar – 
    - **Ação** – Escolha uma das seguintes opções:
        - Ligar – 
        - Avaliar ligação – 
        - Ignorar – 
        - Desligar – 


## <a name="proxy-settings"></a>Definições de proxy

- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
- **Número de porta** – Introduza o número de porta associado ao servidor proxy.



<!--HONumber=Feb17_HO2-->


