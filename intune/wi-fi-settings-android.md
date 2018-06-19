---
title: Configurar as definições de Wi-Fi do Microsoft Intune para dispositivos Android
titleSuffix: ''
description: Saiba como configurar no Intune as definições da ligação Wi-Fi em dispositivos Android e Android for Work.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ee82da997a794bb2f65929a6fd9e0de0cc776a6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831066"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Configurar definições de Wi-Fi no Microsoft Intune para dispositivos Android e Android for Work  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições de Wi-Fi que pode configurar no Microsoft Intune para os dispositivos Android e Android for Work.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Definições de Wi-Fi para perfis básicos e empresariais

As seguintes definições de Wi-Fi estão disponíveis para dispositivos Android e Android para Work:

- **Nome da rede** – Introduza um nome para esta ligação Wi-Fi. Este é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos respetivos dispositivos.
- **SSID** – Sigla de Service Set Identifier (identificador do conjunto de serviço). Este é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Ligar automaticamente** – Faz com que o dispositivo se ligue sempre que estiver ao alcance desta rede.
- **Rede oculta** – Impede que esta rede seja apresentada na lista de redes disponíveis no dispositivo.


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Definições de Wi-Fi apenas para perfis empresariais

- **Tipo de EAP** – Selecione o tipo Protocolo EAP (Extensible authentication protocol) que serve para autenticar as ligações sem fios protegidas entre:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Outras opções ao selecionar um tipo de EAP

#### <a name="server-trust"></a>Fidedignidade do Servidor



|Nome da definição|Mais informações|Utilizar quando|
|-------------|---------------|-----------|
|**Nomes de servidores de certificados**|Especifique um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Se fornecer estas informações, pode ignorar a caixa de diálogo de confiança dinâmica que é apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.|O tipo de EAP é **EAP-TLS** ou **EAP-TTLS**|
|**Certificado de raiz para a validação do servidor**|Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação. |O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**|
|**Privacidade de identidade (identidade externa)**|Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|O tipo de EAP é **PEAP**|


#### <a name="client-authentication"></a>Autenticação de Cliente


|                                     Nome da definição                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Mais informações                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Utilizar quando                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Certificado de cliente para autenticação de cliente (Certificado de identidade)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Escolha o perfil de certificado SCEP ou PKCS que serve para autenticar a ligação.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              O tipo de EAP é <strong>EAP-TLS</strong>              |
|                        <strong>Método de autenticação</strong>                        | Selecione o método de autenticação da ligação:<br>- <strong>Certificados</strong> para selecionar a SCEP ou PKCS do certificado de cliente que é o certificado de identidade apresentado para o servidor.<br><br>- <strong>Nome de utilizador e Palavra-passe</strong> para especificar um método de autenticação diferente. <br><br>Se tiver selecionado <strong>Nome de utilizador e Palavra-passe</strong>, configure:<br><br>-  <strong>Método não EAP (identidade interna)</strong> e, em seguida, selecione a forma como autentica a ligação entre:<br>- <strong>Nenhum</strong><br>- <strong>Palavra-passe não encriptada (PAP)</strong><br>- <strong>Protocolo CHAP (Challenge Handshake Authentication Protocol)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP Versão 2 (MS-CHAP v2)</strong><br>As opções disponíveis dependerão do tipo EAP que selecionou.<br><br><strong>e</strong><br><br>- <strong>Privacidade de identidade (identidade externa)</strong> – Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro. | O tipo de EAP é <strong>EAP-TTLS</strong> ou <strong>PEAP</strong> |

